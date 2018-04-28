---
title: Używanie monikera programu WCF z klientami COM
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
caps.latest.revision: 34
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 322467510d499040c07d6e5e84842542aa325737
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="413c6-102">Używanie monikera programu WCF z klientami COM</span><span class="sxs-lookup"><span data-stu-id="413c6-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="413c6-103">W tym przykładzie przedstawiono sposób użycia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] moniker usługi do integracji usług sieci Web w środowiskach Programowanie oparte na modelu COM, na przykład Microsoft Office Visual Basic for Applications (Office VBA) lub Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="413c6-103">This sample demonstrates how to use the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="413c6-104">W tym przykładzie składa się z klienta Host skryptów systemu Windows (VBS), pomocnicze biblioteki klienta (.dll) i usługi biblioteki (.dll), obsługiwane przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="413c6-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="413c6-105">Usługa jest usługą Kalkulator i klient modelu COM wywołuje operacji matematycznych — Dodawanie, odjąć mnożenia i dzielenia — w usłudze.</span><span class="sxs-lookup"><span data-stu-id="413c6-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="413c6-106">Aktywność klienta jest widoczny w systemie windows — okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="413c6-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="413c6-107">Procedury i kompilacji instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="413c6-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="413c6-108">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="413c6-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="413c6-109">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="413c6-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="413c6-110">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="413c6-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="413c6-111">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="413c6-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="413c6-112">Implementuje usługi `ICalculator` kontrakt zdefiniowany, jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="413c6-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="413c6-113">W przykładzie pokazano trzy alternatywnych metod dla przy użyciu krótkiej nazwy:</span><span class="sxs-lookup"><span data-stu-id="413c6-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
-   <span data-ttu-id="413c6-114">Typu kontraktu — jest zarejestrowany jako typ widoczne COM na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="413c6-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
-   <span data-ttu-id="413c6-115">Kontrakt WSDL — Umowa jest dostarczany w formie dokument WSDL.</span><span class="sxs-lookup"><span data-stu-id="413c6-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="413c6-116">Wymiany metadanych kontraktu — są pobierane w czasie wykonywania z punktu końcowego metadanych programu Exchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="413c6-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="413c6-117">Typu kontraktu</span><span class="sxs-lookup"><span data-stu-id="413c6-117">Typed Contract</span></span>  
 <span data-ttu-id="413c6-118">Aby użyć monikerem przy użyciu typu kontraktu, odpowiednio oparte na atrybutach typów kontraktu usługi musi być zarejestrowana w modelu COM.</span><span class="sxs-lookup"><span data-stu-id="413c6-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="413c6-119">Po pierwsze, klient musi zostać wygenerowany przy użyciu [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="413c6-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="413c6-120">Uruchom następujące polecenie w wierszu polecenia w katalogu klienta można wygenerować typu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="413c6-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="413c6-121">Ta klasa muszą być zawarte w projekcie i projekt powinien być skonfigurowany do generowania widoczny dla modelu COM, podpisany zestaw podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="413c6-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="413c6-122">Następujące atrybut powinien być uwzględniany w pliku AssemblyInfo.cs.</span><span class="sxs-lookup"><span data-stu-id="413c6-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```  
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="413c6-123">Po utworzeniu projektu należy zarejestrować typy widoczne dla modelu COM za pomocą `regasm` jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="413c6-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="413c6-124">Zestaw, który jest tworzony powinni zostać dodani do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="413c6-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="413c6-125">Nie są ściśle wymagane, ale upraszcza proces znajdowania zestawu środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="413c6-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="413c6-126">Polecenie dodaje zestaw do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="413c6-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  <span data-ttu-id="413c6-127">Moniker usługi wymaga tylko rejestracji typu i nie używa serwera proxy do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="413c6-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="413c6-128">Aplikacja kliencka ComCalcClient.vbs używa `GetObject` funkcji, aby utworzyć serwer proxy dla usługi, określ adres, powiązanie, za pomocą składni krótkiej nazwy usługi i kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="413c6-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```  
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="413c6-129">Podaj parametry używane przez moniker:</span><span class="sxs-lookup"><span data-stu-id="413c6-129">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="413c6-130">Adres punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="413c6-130">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="413c6-131">Powiązania, które powinien używać klient do nawiązywania połączenia z tym punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="413c6-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="413c6-132">W takim przypadku wsHttpBinding zdefiniowana w systemie jest używany, chociaż można zdefiniować powiązania niestandardowe w plikach konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="413c6-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="413c6-133">Do użytku z hostem skryptów systemu Windows niestandardowego powiązania jest zdefiniowany w pliku Cscript.exe.config w tym samym katalogu co Cscript.exe.</span><span class="sxs-lookup"><span data-stu-id="413c6-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
-   <span data-ttu-id="413c6-134">Typ kontraktu, który jest obsługiwany w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="413c6-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="413c6-135">Jest to typ, który został wygenerowany i zarejestrowana powyżej.</span><span class="sxs-lookup"><span data-stu-id="413c6-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="413c6-136">Ponieważ skrypt Visual Basic nie zapewnia środowisku jednoznacznie modelu COM, należy określić identyfikator umowy.</span><span class="sxs-lookup"><span data-stu-id="413c6-136">Because Visual Basic script does not provide a strongly-typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="413c6-137">Ten identyfikator GUID jest `interfaceID` z CalcProxy.tlb, które można wyświetlić przy użyciu narzędzia COM, takie jak przeglądarka obiektów OLE/COM (OleView.exe).</span><span class="sxs-lookup"><span data-stu-id="413c6-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="413c6-138">W środowiskach jednoznacznie, takich jak Office VBA lub Visual Basic 6.0 dodanie jawnego odwołania do biblioteki typów, a następnie deklarowanie typu obiektu serwera proxy można użyć zamiast parametrów kontraktu.</span><span class="sxs-lookup"><span data-stu-id="413c6-138">For strongly-typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="413c6-139">Zapewnia również obsługę funkcji IntelliSense podczas tworzenia aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="413c6-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="413c6-140">O utworzone wystąpienie serwera proxy z monikerem usługi, aplikacji klienckiej, można wywoływać metod na serwerze proxy, co powoduje wywołanie odpowiednich operacji usługi infrastruktury moniker usługi.</span><span class="sxs-lookup"><span data-stu-id="413c6-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Po uruchomieniu próbki odpowiedzi operacji jest wyświetlany w okno komunikatu Host skryptów systemu Windows. Oznacza to, klient modelu COM wywołań obiektów COM za pomocą typu krótkiej nazwy do komunikowania się z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi. <span data-ttu-id="413c6-143">Niezależnie od stosowania modelu COM w aplikacji klienckiej komunikacja z usługą składa się tylko z wywołania usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="413c6-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="413c6-144">Kontrakt WSDL</span><span class="sxs-lookup"><span data-stu-id="413c6-144">WSDL Contract</span></span>  
 <span data-ttu-id="413c6-145">Aby użyć monikerem z kontraktem WSDL, nie klienta biblioteki jest wymagana rejestracja, ale kontrakt WSDL dla usługi musi zostać pobrane za pośrednictwem mechanizmu poza pasmem, takie jak otwieranie WSDL punktu końcowego usługi za pomocą przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="413c6-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="413c6-146">Następnie moniker mają dostęp do tego kontraktu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="413c6-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="413c6-147">Aplikacja kliencka ComCalcClient.vbs używa `FileSystemObject` dostępu lokalnie zapisanego pliku WSDL, a następnie ponownie używa `GetObject` funkcji do utworzenia serwera proxy dla usługi.</span><span class="sxs-lookup"><span data-stu-id="413c6-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```  
' Open the WSDL contract file and read it all into the wsdlContract string  
Const ForReading = 1  
Set objFSO = CreateObject("Scripting.FileSystemObject")  
Set objFile = objFSO.OpenTextFile("serviceWsdl.xml", ForReading)  
wsdlContract = objFile.ReadAll  
objFile.Close  
  
' Create a string for the service moniker including the content of the WSDL contract file  
wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
```  
  
 <span data-ttu-id="413c6-148">Podaj parametry używane przez moniker:</span><span class="sxs-lookup"><span data-stu-id="413c6-148">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="413c6-149">Adres punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="413c6-149">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="413c6-150">Powiązania, które powinien używać klient do nawiązywania połączenia z określonego punktu końcowego i przestrzeni nazw, w którym jest zdefiniowany tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="413c6-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="413c6-151">W takim przypadku `wsHttpBinding_ICalculator` jest używany.</span><span class="sxs-lookup"><span data-stu-id="413c6-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
-   <span data-ttu-id="413c6-152">WSDL, który definiuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="413c6-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="413c6-153">W tym przypadku jest to ciąg, który został odczytany z pliku serviceWsdl.xml.</span><span class="sxs-lookup"><span data-stu-id="413c6-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
-   <span data-ttu-id="413c6-154">Nazwa i przestrzeń nazw kontraktu.</span><span class="sxs-lookup"><span data-stu-id="413c6-154">The name and namespace of the contract.</span></span> <span data-ttu-id="413c6-155">Ten identyfikator jest wymagana, ponieważ WSDL może zawierać więcej niż jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="413c6-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="413c6-156">Domyślnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi generować oddzielne pliki WSDL dla każdej przestrzeni nazw który użycia.</span><span class="sxs-lookup"><span data-stu-id="413c6-156">By default, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="413c6-157">Są połączone z użyciem konstrukcji importu WSDL.</span><span class="sxs-lookup"><span data-stu-id="413c6-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="413c6-158">Ponieważ moniker oczekuje jednej definicji WSDL, usługa musi użyć jedna przestrzeń nazw jak pokazano w przykładzie lub osobne pliki muszą zostać ręcznie połączone.</span><span class="sxs-lookup"><span data-stu-id="413c6-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="413c6-159">O utworzone wystąpienie serwera proxy z monikerem usługi, aplikacji klienckiej, można wywoływać metod na serwerze proxy, co powoduje wywołanie odpowiednich operacji usługi infrastruktury moniker usługi.</span><span class="sxs-lookup"><span data-stu-id="413c6-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Po uruchomieniu próbki odpowiedzi operacji jest wyświetlany w okno komunikatu Host skryptów systemu Windows. <span data-ttu-id="413c6-161">Oznacza to, klient modelu COM wywołań obiektów COM za pomocą krótkiej nazwy z kontraktem WSDL do komunikowania się z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="413c6-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="413c6-162">Kontrakt wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="413c6-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="413c6-163">Aby użyć monikerem z kontrakt MEX zgodnie z umową WSDL nie klienta jest wymagana rejestracja.</span><span class="sxs-lookup"><span data-stu-id="413c6-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="413c6-164">Kontrakt usługi są pobierane w czasie wykonywania za pomocą wewnętrznego wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="413c6-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="413c6-165">Aplikacja kliencka ComCalcClient.vbs ponownie używa `GetObject` funkcji do utworzenia serwera proxy dla usługi.</span><span class="sxs-lookup"><span data-stu-id="413c6-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="413c6-166">Podaj parametry używane przez moniker:</span><span class="sxs-lookup"><span data-stu-id="413c6-166">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="413c6-167">Adres punktu końcowego wymiany metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="413c6-167">The address of the service metadata exchange endpoint.</span></span>  
  
-   <span data-ttu-id="413c6-168">Adres punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="413c6-168">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="413c6-169">Powiązania, które powinien używać klient do nawiązywania połączenia z określonego punktu końcowego i przestrzeni nazw, w którym jest zdefiniowany tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="413c6-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="413c6-170">W takim przypadku `wsHttpBinding_ICalculator` jest używany.</span><span class="sxs-lookup"><span data-stu-id="413c6-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
-   <span data-ttu-id="413c6-171">Nazwa i przestrzeń nazw kontraktu.</span><span class="sxs-lookup"><span data-stu-id="413c6-171">The name and namespace of the contract.</span></span> <span data-ttu-id="413c6-172">Ten identyfikator jest wymagana, ponieważ WSDL może zawierać więcej niż jeden kontrakt.</span><span class="sxs-lookup"><span data-stu-id="413c6-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="413c6-173">O utworzone wystąpienie serwera proxy z monikerem usługi, aplikacji klienckiej, można wywoływać metod na serwerze proxy, co powoduje wywołanie odpowiednich operacji usługi infrastruktury moniker usługi.</span><span class="sxs-lookup"><span data-stu-id="413c6-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Po uruchomieniu próbki odpowiedzi operacji jest wyświetlany w okno komunikatu Host skryptów systemu Windows. <span data-ttu-id="413c6-175">Oznacza to, klient modelu COM wywołań obiektów COM za pomocą krótkiej nazwy z kontraktem MEX do komunikowania się z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="413c6-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="413c6-176">Aby skonfigurować i tworzyć przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="413c6-176">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="413c6-177">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="413c6-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="413c6-178">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="413c6-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="413c6-179">W wierszu polecenia programu Visual Studio Otwórz folder \client\bin, w folderze danego języka.</span><span class="sxs-lookup"><span data-stu-id="413c6-179">From a Visual Studio command prompt, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="413c6-180">Jeśli używasz [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 lub Windows Server 2008 R2, upewnij się, uruchom wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="413c6-180">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="413c6-181">Wpisz `tlbexp.exe client.dll /out:CalcProxy.tlb` można wyeksportować do pliku tlb biblioteki dll.</span><span class="sxs-lookup"><span data-stu-id="413c6-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="413c6-182">"Ostrzeżenie eksportera biblioteki typów" jest oczekiwany, ale nie stanowi to problemu, ponieważ typ ogólny nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="413c6-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5.  <span data-ttu-id="413c6-183">Wpisz `regasm.exe /tlb:CalcProxy.tlb client.dll` zarejestrować typy z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="413c6-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="413c6-184">"Ostrzeżenie eksportera biblioteki typów" jest oczekiwany, ale nie stanowi to problemu, ponieważ typ ogólny nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="413c6-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6.  <span data-ttu-id="413c6-185">Wpisz `gacutil.exe /i client.dll` można dodać zestawu do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="413c6-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="413c6-186">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="413c6-186">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="413c6-187">Test, który można uzyskać dostępu do usługi przy użyciu przeglądarki przez wpisanie następującego adresu: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="413c6-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="413c6-188">Powinna być wyświetlana strona potwierdzenia w odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="413c6-188">A confirmation page should be displayed in response.</span></span>  
  
2.  <span data-ttu-id="413c6-189">Uruchom ComCalcClient.vbs z \client z folderu specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="413c6-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="413c6-190">Aktywność klienta jest wyświetlany w systemie windows — okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="413c6-190">Client activity is displayed in message box windows.</span></span>  
  
3.  <span data-ttu-id="413c6-191">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="413c6-191">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="413c6-192">Aby uruchomić przykład na komputerach</span><span class="sxs-lookup"><span data-stu-id="413c6-192">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="413c6-193">Na komputerze, usługi należy utworzyć katalog wirtualny o nazwie ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="413c6-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="413c6-194">Skrypt Setupvroot.bat dołączony próbki mogą służyć do tworzenia katalogu na dysku i katalog wirtualny.</span><span class="sxs-lookup"><span data-stu-id="413c6-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2.  <span data-ttu-id="413c6-195">Skopiuj pliki programu usługi z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego ServiceModelSamples na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="413c6-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="413c6-196">Pamiętaj uwzględnić pliki w katalogu \bin.</span><span class="sxs-lookup"><span data-stu-id="413c6-196">Be sure to include the files in the \bin directory.</span></span>  
  
3.  <span data-ttu-id="413c6-197">Skopiuj plik skryptu klienta z folderu \client w folderze danego języka na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="413c6-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4.  <span data-ttu-id="413c6-198">W pliku skryptu zmień wartość adresu definicji punktu końcowego do dopasowania nowy adres z usługą.</span><span class="sxs-lookup"><span data-stu-id="413c6-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="413c6-199">Zamień wszystkie odwołania do "localhost" pełni kwalifikowanej nazwy domeny w adresie.</span><span class="sxs-lookup"><span data-stu-id="413c6-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5.  <span data-ttu-id="413c6-200">Skopiuj plik WSDL na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="413c6-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="413c6-201">W pliku WSDL serviceWsdl.xml, Zamień wszystkie odwołania do "localhost" pełni kwalifikowanej nazwy domeny w adresie.</span><span class="sxs-lookup"><span data-stu-id="413c6-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6.  <span data-ttu-id="413c6-202">Kopiowanie biblioteki Client.dll z folderu \client\bin w folderze danego języka do katalogu na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="413c6-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7.  <span data-ttu-id="413c6-203">W wierszu polecenia przejdź do tego katalogu docelowego na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="413c6-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="413c6-204">Jeśli przy użyciu [!INCLUDE[wv](../../../../includes/wv-md.md)] lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)], upewnij się uruchomić wiersz polecenia jako Administrator.</span><span class="sxs-lookup"><span data-stu-id="413c6-204">If using [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], make sure to run the command prompt as Administrator.</span></span>  
  
8.  <span data-ttu-id="413c6-205">Wpisz `tlbexp.exe client.dll /out:CalcProxy.tlb` można wyeksportować do pliku tlb biblioteki dll.</span><span class="sxs-lookup"><span data-stu-id="413c6-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="413c6-206">"Ostrzeżenie eksportera biblioteki typów" jest oczekiwany, ale nie stanowi to problemu, ponieważ typ ogólny nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="413c6-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="413c6-207">Wpisz `regasm.exe /tlb:CalcProxy.tlb client.dll` zarejestrować typy z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="413c6-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="413c6-208">Upewnij się, że ścieżka została ustawiona jako folder zawierający `regasm.exe` przed uruchomieniem polecenia.</span><span class="sxs-lookup"><span data-stu-id="413c6-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="413c6-209">Wpisz `gacutil.exe /i client.dll` można dodać zestawu do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="413c6-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="413c6-210">Upewnij się, że ścieżka została ustawiona jako folder zawierający `gacutil.exe` przed uruchomieniem polecenia.</span><span class="sxs-lookup"><span data-stu-id="413c6-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="413c6-211">Aby uzyskać dostęp do usługi z komputera klienckiego przy użyciu przeglądarki testu.</span><span class="sxs-lookup"><span data-stu-id="413c6-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="413c6-212">Na komputerze klienckim uruchom ComCalcClient.vbs.</span><span class="sxs-lookup"><span data-stu-id="413c6-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="413c6-213">Aby wyczyścić po próbki</span><span class="sxs-lookup"><span data-stu-id="413c6-213">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="413c6-214">Ze względów bezpieczeństwa Usuń katalog wirtualny definicji i uprawnienia przyznane w ramach kroków konfiguracji, po zakończeniu pracy z próbek.</span><span class="sxs-lookup"><span data-stu-id="413c6-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="413c6-215">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="413c6-215">See Also</span></span>
