---
title: Używanie monikera programu WCF z klientami COM
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: 6e5bb35d0d1d9128ddbc5f7ab4dd81c3bc0f8fbf
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221638"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="92b33-102">Używanie monikera programu WCF z klientami COM</span><span class="sxs-lookup"><span data-stu-id="92b33-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="92b33-103">W tym przykładzie pokazano, jak użyć monikera programu Windows Communication Foundation (WCF) do integracji usług internetowych w środowiskach programistycznych opartych na modelu COM, takich jak Microsoft Office Visual Basic for Applications (VBA pakietu Office) lub Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="92b33-103">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="92b33-104">W tym przykładzie składa się z klienta Windows Script Host (VBS), obsługi klienta biblioteki (.dll) i usługi biblioteki (.dll), hostowanej przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="92b33-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="92b33-105">Usługa jest usługą Kalkulator i klient modelu COM wywołuje operacji matematycznych — dodawania, odejmowania, mnożenia i dzielenia — w usłudze.</span><span class="sxs-lookup"><span data-stu-id="92b33-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="92b33-106">Aktywność klienta jest widoczny w systemie windows okno komunikatu.</span><span class="sxs-lookup"><span data-stu-id="92b33-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92b33-107">Procedury i kompilacja instrukcje dotyczące konfiguracji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="92b33-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="92b33-108">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="92b33-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="92b33-109">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="92b33-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="92b33-110">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="92b33-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="92b33-111">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="92b33-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="92b33-112">Implementuje usługi `ICalculator` kontrakt zdefiniowany jak pokazano w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="92b33-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="92b33-113">W przykładzie pokazano trzech alternatywnych metod dla używanie monikera programu:</span><span class="sxs-lookup"><span data-stu-id="92b33-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
-   <span data-ttu-id="92b33-114">Wpisane kontraktu — jest zarejestrowany jako typ widoczne COM na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="92b33-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
-   <span data-ttu-id="92b33-115">WSDL kontraktu — jest dostarczany w formie dokumentu WSDL.</span><span class="sxs-lookup"><span data-stu-id="92b33-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="92b33-116">Wymiany metadanych kontraktu — są pobierane w czasie wykonywania z punktu końcowego metadanych programu Exchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="92b33-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="92b33-117">Wpisane kontraktu</span><span class="sxs-lookup"><span data-stu-id="92b33-117">Typed Contract</span></span>  
 <span data-ttu-id="92b33-118">Aby użyć monikera programu przy użyciu umowy wpisane, odpowiednio opartego na atrybutach typy kontraktu usługi musi być zarejestrowana w modelu COM.</span><span class="sxs-lookup"><span data-stu-id="92b33-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="92b33-119">Po pierwsze, klient musi zostać wygenerowany przy użyciu [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="92b33-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="92b33-120">Uruchom następujące polecenie w wierszu polecenia w katalogu klienta można wygenerować typizowanego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="92b33-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="92b33-121">Ta klasa muszą być zawarte w projekcie i projektu powinny być skonfigurowane do generowania modelu COM-widoczne, podpisanego zestawu podczas kompilowania.</span><span class="sxs-lookup"><span data-stu-id="92b33-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="92b33-122">Plik AssemblyInfo.cs powinny być objęte następujący atrybut.</span><span class="sxs-lookup"><span data-stu-id="92b33-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="92b33-123">Po utworzeniu projektu, należy zarejestrować typy widoczne dla modelu COM za pomocą `regasm` jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="92b33-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="92b33-124">Zestaw, który jest tworzony, należy dodać do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="92b33-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="92b33-125">Ściśle wymagane, ale upraszcza proces środowiska uruchomieniowego lokalizowanie zestawu.</span><span class="sxs-lookup"><span data-stu-id="92b33-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="92b33-126">Następujące polecenie dodaje zestaw do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="92b33-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
>  <span data-ttu-id="92b33-127">Monikera programu wymaga tylko rejestracji typu, a nie za pomocą serwera proxy do komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="92b33-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="92b33-128">Aplikacja kliencka ComCalcClient.vbs używa `GetObject` funkcję, aby utworzyć serwer proxy dla usługi przy użyciu składni moniker usługi, aby określić adres, powiązanie i kontraktu usługi.</span><span class="sxs-lookup"><span data-stu-id="92b33-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,   
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="92b33-129">Określ parametry używane przez moniker:</span><span class="sxs-lookup"><span data-stu-id="92b33-129">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="92b33-130">Adres punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="92b33-130">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="92b33-131">Wiązanie, którego powinien używać klient do łączenia z tego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="92b33-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="92b33-132">W tym przypadku wsHttpBinding zdefiniowanych w systemie jest używany, chociaż można zdefiniować powiązań niestandardowych w plikach konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="92b33-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="92b33-133">Do użytku z hostem skryptów Windows niestandardowego powiązania jest zdefiniowana w pliku Cscript.exe.config, w tym samym katalogu co Cscript.exe.</span><span class="sxs-lookup"><span data-stu-id="92b33-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
-   <span data-ttu-id="92b33-134">Typ kontraktu, który jest obsługiwany w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="92b33-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="92b33-135">Jest to typ, który został wygenerowany i zarejestrowany powyżej.</span><span class="sxs-lookup"><span data-stu-id="92b33-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="92b33-136">Ponieważ skrypt Visual Basic nie udostępnia silnie typizowane COM środowiska, należy określić identyfikator dla kontraktu.</span><span class="sxs-lookup"><span data-stu-id="92b33-136">Because Visual Basic script does not provide a strongly-typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="92b33-137">Jest to identyfikator GUID `interfaceID` z CalcProxy.tlb, które mogą być wyświetlane za pomocą narzędzi COM, takich jak OLE/COM Object Viewer (OleView.exe).</span><span class="sxs-lookup"><span data-stu-id="92b33-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="92b33-138">W środowiskach silnie typizowane, takich jak Office VBA lub Visual Basic 6.0 Dodawanie jawnego odwołania do biblioteki typów, a następnie deklarowania typu obiektu serwera proxy można zamiast parametru kontraktu.</span><span class="sxs-lookup"><span data-stu-id="92b33-138">For strongly-typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="92b33-139">To ten zapewnia obsługę technologii IntelliSense podczas tworzenia aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="92b33-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="92b33-140">Posiadanie skonstruowany wystąpienia serwera proxy przy użyciu monikera programu, aplikacja kliencka może wywoływać metody na serwerze proxy, co skutkuje infrastruktury monikera usługi wywoływania odpowiednich operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="92b33-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Po uruchomieniu przykładu, odpowiedź operacji jest wyświetlany w okno komunikatu Windows Script Host. W tym przykładzie pokazano, jak klient modelu COM, wywołań obiektów COM używanie monikera programu wpisane do komunikowania się z usługą WCF. <span data-ttu-id="92b33-143">Mimo zastosowania modelu COM w aplikacji klienckiej komunikacji z usługą składa się tylko z wywołania usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="92b33-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="92b33-144">Kontrakt WSDL</span><span class="sxs-lookup"><span data-stu-id="92b33-144">WSDL Contract</span></span>  
 <span data-ttu-id="92b33-145">Moniker za pomocą kontraktu WSDL, nie rejestracji biblioteki klienta jest wymagany, ale musi zostać pobrany kontrakt WSDL dla usługi za pośrednictwem mechanizmu poza pasmem, takich jak otwieranie WSDL punktu końcowego usługi za pomocą przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="92b33-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="92b33-146">Moniker mogą uzyskiwać dostęp do tej Umowy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="92b33-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="92b33-147">Aplikacja kliencka ComCalcClient.vbs używa `FileSystemObject` dostępu do pliku zapisanego lokalnie WSDL, a następnie ponownie używa `GetObject` funkcję, aby utworzyć serwer proxy dla usługi.</span><span class="sxs-lookup"><span data-stu-id="92b33-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
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
  
 <span data-ttu-id="92b33-148">Określ parametry używane przez moniker:</span><span class="sxs-lookup"><span data-stu-id="92b33-148">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="92b33-149">Adres punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="92b33-149">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="92b33-150">Wiązanie, którego powinien używać klient do połączenia z tego punktu końcowego i przestrzeni nazw, w którym to powiązanie jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="92b33-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="92b33-151">W tym przypadku `wsHttpBinding_ICalculator` jest używany.</span><span class="sxs-lookup"><span data-stu-id="92b33-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
-   <span data-ttu-id="92b33-152">Języka WSDL, który definiuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="92b33-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="92b33-153">W tym przypadku jest to ciąg, który został odczytany z pliku serviceWsdl.xml.</span><span class="sxs-lookup"><span data-stu-id="92b33-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
-   <span data-ttu-id="92b33-154">Nazwa i przestrzeni nazw kontraktu.</span><span class="sxs-lookup"><span data-stu-id="92b33-154">The name and namespace of the contract.</span></span> <span data-ttu-id="92b33-155">Ten identyfikator jest wymagana, ponieważ WSDL może zawierać więcej niż jednego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="92b33-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="92b33-156">Domyślnie usługi WCF generować oddzielne pliki WSDL dla każdej przestrzeni nazw, użycie.</span><span class="sxs-lookup"><span data-stu-id="92b33-156">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="92b33-157">Są one połączone z użyciem konstrukcji importu WSDL.</span><span class="sxs-lookup"><span data-stu-id="92b33-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="92b33-158">Ponieważ moniker oczekuje jednej definicji WSDL, jak pokazano w tym przykładzie Usługa należy użyć jednej przestrzeni nazw lub osobne pliki muszą zostać ręcznie połączone.</span><span class="sxs-lookup"><span data-stu-id="92b33-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="92b33-159">Posiadanie skonstruowany wystąpienia serwera proxy przy użyciu monikera programu, aplikacja kliencka może wywoływać metody na serwerze proxy, co skutkuje infrastruktury monikera usługi wywoływania odpowiednich operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="92b33-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Po uruchomieniu przykładu, odpowiedź operacji jest wyświetlany w okno komunikatu Windows Script Host. <span data-ttu-id="92b33-161">W tym przykładzie pokazano, jak klient modelu COM, wywołań obiektów COM używanie monikera programu za pomocą kontraktu WSDL do komunikowania się z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="92b33-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="92b33-162">Kontrakt wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="92b33-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="92b33-163">Za pomocą moniker kontrakt MEX zgodnie z umową WSDL nie klienta jest wymagana rejestracja.</span><span class="sxs-lookup"><span data-stu-id="92b33-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="92b33-164">Kontrakt usługi są pobierane w czasie wykonywania za pomocą wewnętrznego wymiany metadanych.</span><span class="sxs-lookup"><span data-stu-id="92b33-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="92b33-165">Aplikacja kliencka ComCalcClient.vbs ponownie używa `GetObject` funkcję, aby utworzyć serwer proxy dla usługi.</span><span class="sxs-lookup"><span data-stu-id="92b33-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="92b33-166">Określ parametry używane przez moniker:</span><span class="sxs-lookup"><span data-stu-id="92b33-166">The parameters used by the moniker specify:</span></span>  
  
-   <span data-ttu-id="92b33-167">Adres punktu końcowego wymiany metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="92b33-167">The address of the service metadata exchange endpoint.</span></span>  
  
-   <span data-ttu-id="92b33-168">Adres punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="92b33-168">The address of the service endpoint.</span></span>  
  
-   <span data-ttu-id="92b33-169">Wiązanie, którego powinien używać klient do połączenia z tego punktu końcowego i przestrzeni nazw, w którym to powiązanie jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="92b33-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="92b33-170">W tym przypadku `wsHttpBinding_ICalculator` jest używany.</span><span class="sxs-lookup"><span data-stu-id="92b33-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
-   <span data-ttu-id="92b33-171">Nazwa i przestrzeni nazw kontraktu.</span><span class="sxs-lookup"><span data-stu-id="92b33-171">The name and namespace of the contract.</span></span> <span data-ttu-id="92b33-172">Ten identyfikator jest wymagana, ponieważ WSDL może zawierać więcej niż jednego kontraktu.</span><span class="sxs-lookup"><span data-stu-id="92b33-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="92b33-173">Posiadanie skonstruowany wystąpienia serwera proxy przy użyciu monikera programu, aplikacja kliencka może wywoływać metody na serwerze proxy, co skutkuje infrastruktury monikera usługi wywoływania odpowiednich operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="92b33-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Po uruchomieniu przykładu, odpowiedź operacji jest wyświetlany w okno komunikatu Windows Script Host. <span data-ttu-id="92b33-175">W tym przykładzie pokazano, jak klient modelu COM, wywołań obiektów COM używanie monikera programu za pomocą kontraktu MEX do komunikowania się z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="92b33-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="92b33-176">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="92b33-176">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="92b33-177">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92b33-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="92b33-178">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="92b33-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="92b33-179">W wierszu polecenia dla deweloperów programu Visual Studio, otwórz folder \client\bin, w folderze specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="92b33-179">From a Developer Command Prompt for Visual Studio, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="92b33-180">Jeśli używasz [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7 lub Windows Server 2008 R2, upewnij się, uruchom wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="92b33-180">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[lserver](../../../../includes/lserver-md.md)], Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4.  <span data-ttu-id="92b33-181">Wpisz `tlbexp.exe client.dll /out:CalcProxy.tlb` można wyeksportować biblioteki dll z plikiem tlb.</span><span class="sxs-lookup"><span data-stu-id="92b33-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="92b33-182">"Ostrzeżenie eksportera biblioteki typów" oczekuje się, ale nie jest problemem, ponieważ typ ogólny nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="92b33-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5.  <span data-ttu-id="92b33-183">Wpisz `regasm.exe /tlb:CalcProxy.tlb client.dll` zarejestrować typy za pomocą modelu COM.</span><span class="sxs-lookup"><span data-stu-id="92b33-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="92b33-184">"Ostrzeżenie eksportera biblioteki typów" oczekuje się, ale nie jest problemem, ponieważ typ ogólny nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="92b33-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6.  <span data-ttu-id="92b33-185">Wpisz `gacutil.exe /i client.dll` można dodać zestawu do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="92b33-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="92b33-186">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="92b33-186">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="92b33-187">Test, który możesz uzyskać dostęp do usługi, w przeglądarce, wpisując następujący adres: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="92b33-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="92b33-188">Strona potwierdzenia powinna być wyświetlana w odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="92b33-188">A confirmation page should be displayed in response.</span></span>  
  
2.  <span data-ttu-id="92b33-189">Uruchom ComCalcClient.vbs \client jest dostępna z folderu specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="92b33-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="92b33-190">Aktywność klienta jest wyświetlana w polu wiadomości w systemie windows.</span><span class="sxs-lookup"><span data-stu-id="92b33-190">Client activity is displayed in message box windows.</span></span>  
  
3.  <span data-ttu-id="92b33-191">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="92b33-191">If the client and service are not able to communicate, see [Troubleshooting Tips](https://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="92b33-192">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="92b33-192">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="92b33-193">Na komputerze usługi należy utworzyć katalog wirtualny o nazwie ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="92b33-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="92b33-194">Skrypt Setupvroot.bat dołączone do przykładu może służyć do tworzenia katalogu na dysku i katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="92b33-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2.  <span data-ttu-id="92b33-195">Skopiuj pliki programu usługi z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples katalog wirtualny ServiceModelSamples na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="92b33-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="92b33-196">Pamiętaj uwzględnić pliki w katalogu \bin.</span><span class="sxs-lookup"><span data-stu-id="92b33-196">Be sure to include the files in the \bin directory.</span></span>  
  
3.  <span data-ttu-id="92b33-197">Skopiuj plik skryptu klienta z folderu \client w folderze specyficzny dla języka na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="92b33-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4.  <span data-ttu-id="92b33-198">W pliku skryptu zmień wartość adresu definicji punktu końcowego, aby dopasować nowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="92b33-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="92b33-199">Zastąp wszystkie odwołania do "localhost" w pełni kwalifikowaną nazwę domeny w adresie.</span><span class="sxs-lookup"><span data-stu-id="92b33-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5.  <span data-ttu-id="92b33-200">Skopiuj plik WSDL na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="92b33-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="92b33-201">W pliku WSDL serviceWsdl.xml, Zamień wszystkie odwołania do "localhost" w pełni kwalifikowaną nazwę domeny w adresie.</span><span class="sxs-lookup"><span data-stu-id="92b33-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6.  <span data-ttu-id="92b33-202">Skopiuj bibliotekę Client.dll z folderu \client\bin w folderze specyficzny dla języka do katalogu na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="92b33-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7.  <span data-ttu-id="92b33-203">W wierszu polecenia przejdź do tego katalogu docelowego na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="92b33-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="92b33-204">Jeśli przy użyciu [!INCLUDE[wv](../../../../includes/wv-md.md)] lub [!INCLUDE[lserver](../../../../includes/lserver-md.md)], upewnij się uruchomić wiersz polecenia jako Administrator.</span><span class="sxs-lookup"><span data-stu-id="92b33-204">If using [!INCLUDE[wv](../../../../includes/wv-md.md)] or [!INCLUDE[lserver](../../../../includes/lserver-md.md)], make sure to run the command prompt as Administrator.</span></span>  
  
8.  <span data-ttu-id="92b33-205">Wpisz `tlbexp.exe client.dll /out:CalcProxy.tlb` można wyeksportować biblioteki dll z plikiem tlb.</span><span class="sxs-lookup"><span data-stu-id="92b33-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="92b33-206">"Ostrzeżenie eksportera biblioteki typów" oczekuje się, ale nie jest problemem, ponieważ typ ogólny nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="92b33-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="92b33-207">Wpisz `regasm.exe /tlb:CalcProxy.tlb client.dll` zarejestrować typy za pomocą modelu COM.</span><span class="sxs-lookup"><span data-stu-id="92b33-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="92b33-208">Upewnij się, ta ścieżka została ustawiona na folder, który zawiera `regasm.exe` przed uruchomieniem polecenia.</span><span class="sxs-lookup"><span data-stu-id="92b33-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="92b33-209">Wpisz `gacutil.exe /i client.dll` można dodać zestawu do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="92b33-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="92b33-210">Upewnij się, ta ścieżka została ustawiona na folder, który zawiera `gacutil.exe` przed uruchomieniem polecenia.</span><span class="sxs-lookup"><span data-stu-id="92b33-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="92b33-211">Test, aby uzyskać dostęp do usługi z poziomu komputera klienckiego za pomocą przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="92b33-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="92b33-212">Na komputerze klienckim, aby uruchomić ComCalcClient.vbs.</span><span class="sxs-lookup"><span data-stu-id="92b33-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="92b33-213">Aby wyczyścić zasoby po próbki</span><span class="sxs-lookup"><span data-stu-id="92b33-213">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="92b33-214">Ze względów bezpieczeństwa usuń definicję katalogu wirtualnego i uprawnienia udzielone w ramach kroków konfiguracji, po zakończeniu pracy z próbek.</span><span class="sxs-lookup"><span data-stu-id="92b33-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b33-215">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92b33-215">See Also</span></span>
