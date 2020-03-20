---
title: Używanie monikera programu WCF z klientami COM
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: d4d812c59a504f365eb3ad63ddd45ba5a66296e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183236"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="5784a-102">Używanie monikera programu WCF z klientami COM</span><span class="sxs-lookup"><span data-stu-id="5784a-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="5784a-103">W tym przykładzie pokazano, jak używać moniker usługi Windows Communication Foundation (WCF) do integracji usług sieci Web w środowiskach programistycznych opartych na komismencie, takich jak Microsoft Office Visual Basic for Applications (Office VBA) lub Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="5784a-103">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="5784a-104">Ten przykład składa się z klienta hosta skryptów systemu Windows (vbs), pomocniczej biblioteki klienta (dll) i biblioteki usług (dll) hostowanego przez internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="5784a-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="5784a-105">Usługa jest usługą kalkulatora, a klient COM wywołuje operacje matematyczne — dodawanie, odejmowanie, mnożenie i dzielenie — w usłudze.</span><span class="sxs-lookup"><span data-stu-id="5784a-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="5784a-106">Aktywność klienta jest widoczna w oknach okna okna okna komunikatu.</span><span class="sxs-lookup"><span data-stu-id="5784a-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5784a-107">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5784a-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5784a-108">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5784a-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5784a-109">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="5784a-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5784a-110">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="5784a-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5784a-111">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="5784a-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="5784a-112">Usługa implementuje `ICalculator` kontrakt zdefiniowany w sposób pokazany w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="5784a-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="5784a-113">Przykład pokazuje trzy alternatywne podejścia do korzystania z monikera:</span><span class="sxs-lookup"><span data-stu-id="5784a-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
- <span data-ttu-id="5784a-114">Typowa umowa — kontrakt jest zarejestrowany jako typ widoczny com na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="5784a-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
- <span data-ttu-id="5784a-115">Umowa WSDL — umowa jest dostarczana w formie dokumentu WSDL.</span><span class="sxs-lookup"><span data-stu-id="5784a-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
- <span data-ttu-id="5784a-116">Kontrakt wymiany metadanych — kontrakt jest pobierany w czasie wykonywania z punktu końcowego wymiany metadanych (MEX).</span><span class="sxs-lookup"><span data-stu-id="5784a-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="5784a-117">Typowa umowa</span><span class="sxs-lookup"><span data-stu-id="5784a-117">Typed Contract</span></span>  
 <span data-ttu-id="5784a-118">Aby użyć monikera z typowym użyciem umowy, odpowiednio przypisane typy dla umowy serwisowej muszą być zarejestrowane w com.</span><span class="sxs-lookup"><span data-stu-id="5784a-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="5784a-119">Po pierwsze, klient musi być generowany przy użyciu [narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5784a-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="5784a-120">Uruchom następujące polecenie z wiersza polecenia w katalogu klienta, aby wygenerować wpisany serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="5784a-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="5784a-121">Ta klasa musi być uwzględniona w projekcie, a projekt powinien być skonfigurowany do generowania zestawu widocznego dla urządzenia COM po skompilowaniu.</span><span class="sxs-lookup"><span data-stu-id="5784a-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="5784a-122">W pliku AssemblyInfo.cs należy uwzględnić następujący atrybut.</span><span class="sxs-lookup"><span data-stu-id="5784a-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="5784a-123">Po zbudowaniu projektu zarejestruj typy widoczne `regasm` w programie COM przy użyciu jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5784a-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="5784a-124">Zestaw, który jest tworzony należy dodać do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="5784a-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="5784a-125">Chociaż nie jest to ściśle wymagane, upraszcza to proces środowiska wykonawczego lokalizowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="5784a-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="5784a-126">Następujące polecenie dodaje zestaw do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="5784a-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> <span data-ttu-id="5784a-127">Moniker usługi wymaga tylko rejestracji typu i nie używa serwera proxy do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="5784a-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="5784a-128">ComCalcClient.vbs aplikacja kliencka używa `GetObject` tej funkcji do konstruowania serwera proxy dla usługi, przy użyciu składni moniker usługi, aby określić adres, powiązanie i umowy dla usługi.</span><span class="sxs-lookup"><span data-stu-id="5784a-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="5784a-129">Parametry używane przez moniker określają:</span><span class="sxs-lookup"><span data-stu-id="5784a-129">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="5784a-130">Adres punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="5784a-130">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="5784a-131">Powiązanie, które klient powinien używać do łączenia się z tym punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="5784a-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="5784a-132">W takim przypadku zdefiniowane przez system wsHttpBinding jest używane, chociaż niestandardowe powiązania mogą być definiowane w plikach konfiguracji klienta.</span><span class="sxs-lookup"><span data-stu-id="5784a-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="5784a-133">Do użytku z hostem skryptów systemu Windows powiązanie niestandardowe jest zdefiniowane w pliku Cscript.exe.config w tym samym katalogu co Cscript.exe.</span><span class="sxs-lookup"><span data-stu-id="5784a-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
- <span data-ttu-id="5784a-134">Typ kontraktu, który jest obsługiwany w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="5784a-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="5784a-135">Jest to typ, który został wygenerowany i zarejestrowany powyżej.</span><span class="sxs-lookup"><span data-stu-id="5784a-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="5784a-136">Ponieważ skrypt języka Visual Basic nie zapewnia silnie typizowanego środowiska COM, należy określić identyfikator kontraktu.</span><span class="sxs-lookup"><span data-stu-id="5784a-136">Because Visual Basic script does not provide a strongly-typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="5784a-137">Ten identyfikator GUID jest `interfaceID` z CalcProxy.tlb, który można przeglądać za pomocą narzędzi COM, takich jak OLE/COM Object Viewer (OleView.exe).</span><span class="sxs-lookup"><span data-stu-id="5784a-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="5784a-138">W przypadku silnie typizowanych środowisk, takich jak Office VBA lub Visual Basic 6.0, zamiast parametru kontraktu można dodać jawne odwołanie do biblioteki typów, a następnie zadeklarować typ obiektu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="5784a-138">For strongly-typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="5784a-139">Zapewnia to również obsługę IntelliSense podczas tworzenia aplikacji klienckich.</span><span class="sxs-lookup"><span data-stu-id="5784a-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="5784a-140">Po skonstruowaniu wystąpienia serwera proxy za pomocą moniker usługi, aplikacja kliencka może wywołać metody na serwerze proxy, co powoduje infrastruktury moniker usługi wywołując odpowiednie operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="5784a-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 When you run the sample, the operation response is displayed in a Windows Script Host message box window. Pokazuje to klienta COM, który wywołuje COM przy użyciu wpisanego monikera do komunikowania się z usługą WCF. <span data-ttu-id="5784a-143">Pomimo użycia com w aplikacji klienckiej, komunikacja z usługą składa się tylko z wywołań usługi sieci Web.</span><span class="sxs-lookup"><span data-stu-id="5784a-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="5784a-144">Kontrakt WSDL</span><span class="sxs-lookup"><span data-stu-id="5784a-144">WSDL Contract</span></span>  
 <span data-ttu-id="5784a-145">Aby użyć moniker z umową WSDL, nie jest wymagana rejestracja biblioteki klienta, ale kontrakt WSDL dla usługi musi być pobierany za pośrednictwem mechanizmu poza pasmem, takiego jak korzystanie z przeglądarki w celu uzyskania dostępu do punktu końcowego WSDL dla usługi.</span><span class="sxs-lookup"><span data-stu-id="5784a-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="5784a-146">Moniker może następnie uzyskać dostęp do tej umowy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5784a-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="5784a-147">ComCalcClient.vbs aplikacja kliencka `FileSystemObject` używa dostępu do lokalnie zapisanego pliku WSDL, a następnie ponownie używa `GetObject` funkcji do konstruowania serwera proxy dla usługi.</span><span class="sxs-lookup"><span data-stu-id="5784a-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
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
  
 <span data-ttu-id="5784a-148">Parametry używane przez moniker określają:</span><span class="sxs-lookup"><span data-stu-id="5784a-148">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="5784a-149">Adres punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="5784a-149">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="5784a-150">Powiązanie, które klient powinien używać do łączenia się z tym punktem końcowym i przestrzenią nazw, w której zdefiniowano to powiązanie.</span><span class="sxs-lookup"><span data-stu-id="5784a-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="5784a-151">W takim przypadku `wsHttpBinding_ICalculator` jest używany.</span><span class="sxs-lookup"><span data-stu-id="5784a-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="5784a-152">WSDL, który definiuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="5784a-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="5784a-153">W tym przypadku jest to ciąg, który został odczytany z pliku serviceWsdl.xml.</span><span class="sxs-lookup"><span data-stu-id="5784a-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
- <span data-ttu-id="5784a-154">Nazwa i obszar nazw kontraktu.</span><span class="sxs-lookup"><span data-stu-id="5784a-154">The name and namespace of the contract.</span></span> <span data-ttu-id="5784a-155">Ta identyfikacja jest wymagana, ponieważ WSDL może zawierać więcej niż jedną umowę.</span><span class="sxs-lookup"><span data-stu-id="5784a-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5784a-156">Domyślnie usługi WCF generują oddzielne pliki WSDL dla każdego obszaru nazw, który jest używany.</span><span class="sxs-lookup"><span data-stu-id="5784a-156">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="5784a-157">Są one połączone z użyciem konstrukcji importu WSDL.</span><span class="sxs-lookup"><span data-stu-id="5784a-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="5784a-158">Ponieważ moniker oczekuje pojedynczej definicji WSDL, usługa musi używać pojedynczego obszaru nazw, jak pokazano w tym przykładzie lub oddzielne pliki muszą być scalane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="5784a-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="5784a-159">Po skonstruowaniu wystąpienia serwera proxy za pomocą moniker usługi, aplikacja kliencka może wywołać metody na serwerze proxy, co powoduje infrastruktury moniker usługi wywołując odpowiednie operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="5784a-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 When you run the sample, the operation response is displayed in a Windows Script Host message box window. <span data-ttu-id="5784a-161">Pokazuje to klienta COM wykonywanie wywołań COM przy użyciu moniker z umowy WSDL do komunikowania się z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="5784a-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="5784a-162">Kontrakt wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="5784a-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="5784a-163">Aby użyć moniker z umową MEX, tak jak w przypadku umowy WSDL, nie jest wymagana rejestracja klienta.</span><span class="sxs-lookup"><span data-stu-id="5784a-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="5784a-164">Kontrakt dla usługi jest pobierany w czasie wykonywania za pośrednictwem wewnętrznego użycia metadata Exchange.</span><span class="sxs-lookup"><span data-stu-id="5784a-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="5784a-165">ComCalcClient.vbs aplikacja kliencka `GetObject` ponownie używa funkcji do konstruowania serwera proxy dla usługi.</span><span class="sxs-lookup"><span data-stu-id="5784a-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="5784a-166">Parametry używane przez moniker określają:</span><span class="sxs-lookup"><span data-stu-id="5784a-166">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="5784a-167">Adres punktu końcowego wymiany metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="5784a-167">The address of the service metadata exchange endpoint.</span></span>  
  
- <span data-ttu-id="5784a-168">Adres punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="5784a-168">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="5784a-169">Powiązanie, które klient powinien używać do łączenia się z tym punktem końcowym i przestrzenią nazw, w której zdefiniowano to powiązanie.</span><span class="sxs-lookup"><span data-stu-id="5784a-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="5784a-170">W takim przypadku `wsHttpBinding_ICalculator` jest używany.</span><span class="sxs-lookup"><span data-stu-id="5784a-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="5784a-171">Nazwa i obszar nazw kontraktu.</span><span class="sxs-lookup"><span data-stu-id="5784a-171">The name and namespace of the contract.</span></span> <span data-ttu-id="5784a-172">Ta identyfikacja jest wymagana, ponieważ WSDL może zawierać więcej niż jedną umowę.</span><span class="sxs-lookup"><span data-stu-id="5784a-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="5784a-173">Po skonstruowaniu wystąpienia serwera proxy za pomocą moniker usługi, aplikacja kliencka może wywołać metody na serwerze proxy, co powoduje infrastruktury moniker usługi wywołując odpowiednie operacje usługi.</span><span class="sxs-lookup"><span data-stu-id="5784a-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 When you run the sample, the operation response is displayed in a Windows Script Host message box window. <span data-ttu-id="5784a-175">Pokazuje to klienta COM wykonywanie wywołań COM przy użyciu moniker z umowy MEX do komunikowania się z usługą WCF.</span><span class="sxs-lookup"><span data-stu-id="5784a-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="5784a-176">Aby skonfigurować i utworzyć próbkę</span><span class="sxs-lookup"><span data-stu-id="5784a-176">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="5784a-177">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5784a-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5784a-178">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5784a-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5784a-179">W wierszu polecenia dewelopera dla programu Visual Studio otwórz folder \client\bin w folderze specyficznym dla języka.</span><span class="sxs-lookup"><span data-stu-id="5784a-179">From a Developer Command Prompt for Visual Studio, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5784a-180">Jeśli używasz systemu Windows Vista, Windows Server 2008, Windows 7 lub Windows Server 2008 R2, upewnij się, że wiersz polecenia jest uruchamiany z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="5784a-180">If you are using Windows Vista, Windows Server 2008, Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4. <span data-ttu-id="5784a-181">Wpisz, `tlbexp.exe client.dll /out:CalcProxy.tlb` aby wyeksportować bibliotekę dll do pliku tlb.</span><span class="sxs-lookup"><span data-stu-id="5784a-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="5784a-182">Oczekiwano "Ostrzeżenia eksportera biblioteki typu", ale nie jest to problem, ponieważ typ ogólny nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="5784a-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5. <span data-ttu-id="5784a-183">Wpisz, `regasm.exe /tlb:CalcProxy.tlb client.dll` aby zarejestrować typy w COM.</span><span class="sxs-lookup"><span data-stu-id="5784a-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="5784a-184">Oczekiwano "Ostrzeżenia eksportera biblioteki typu", ale nie jest to problem, ponieważ typ ogólny nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="5784a-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6. <span data-ttu-id="5784a-185">`gacutil.exe /i client.dll` Wpisz, aby dodać zestaw do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="5784a-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="5784a-186">Aby uruchomić próbkę na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="5784a-186">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="5784a-187">Sprawdź, czy możesz uzyskać dostęp do usługi za pomocą `http://localhost/servicemodelsamples/service.svc`przeglądarki, wpisując następujący adres: .</span><span class="sxs-lookup"><span data-stu-id="5784a-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="5784a-188">W odpowiedzi powinna zostać wyświetlona strona potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="5784a-188">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="5784a-189">Uruchom comcalcclient.vbs z \client, spod folderu specyficznego dla języka.</span><span class="sxs-lookup"><span data-stu-id="5784a-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="5784a-190">Aktywność klienta jest wyświetlana w oknach okna okna komunikatu.</span><span class="sxs-lookup"><span data-stu-id="5784a-190">Client activity is displayed in message box windows.</span></span>  
  
3. <span data-ttu-id="5784a-191">Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5784a-191">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="5784a-192">Aby uruchomić próbkę na różnych komputerach</span><span class="sxs-lookup"><span data-stu-id="5784a-192">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="5784a-193">Na komputerze usługi utwórz katalog wirtualny o nazwie ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="5784a-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="5784a-194">Skrypt Setupvroot.bat dołączony do przykładu może służyć do tworzenia katalogu dysku i katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="5784a-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2. <span data-ttu-id="5784a-195">Skopiuj pliki programu serwisowego z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego ServiceModelSamples na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="5784a-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="5784a-196">Pamiętaj, aby dołączyć pliki do katalogu \bin.</span><span class="sxs-lookup"><span data-stu-id="5784a-196">Be sure to include the files in the \bin directory.</span></span>  
  
3. <span data-ttu-id="5784a-197">Skopiuj plik skryptu klienta z folderu \client w folderze specyficznym dla języka na komputer kliencki.</span><span class="sxs-lookup"><span data-stu-id="5784a-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4. <span data-ttu-id="5784a-198">W pliku skryptu zmień wartość adresu definicji punktu końcowego, aby dopasować go do nowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="5784a-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="5784a-199">Zastąp wszelkie odwołania do "localhost" w pełni kwalifikowaną nazwą domeny w adresie.</span><span class="sxs-lookup"><span data-stu-id="5784a-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5. <span data-ttu-id="5784a-200">Skopiuj plik WSDL na komputer kliencki.</span><span class="sxs-lookup"><span data-stu-id="5784a-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="5784a-201">W pliku WSDL, serviceWsdl.xml, zastąp wszelkie odwołania do "localhost" w pełni kwalifikowaną nazwą domeny w adresie.</span><span class="sxs-lookup"><span data-stu-id="5784a-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6. <span data-ttu-id="5784a-202">Skopiuj bibliotekę Client.dll z folderu \client\bin w folderze specyficznym dla języka do katalogu na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="5784a-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7. <span data-ttu-id="5784a-203">W wierszu polecenia przejdź do tego katalogu docelowego na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="5784a-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="5784a-204">Jeśli używasz systemu Windows Vista lub Windows Server 2008, uruchom wiersz polecenia jako administrator.</span><span class="sxs-lookup"><span data-stu-id="5784a-204">If using Windows Vista or Windows Server 2008, make sure to run the command prompt as Administrator.</span></span>  
  
8. <span data-ttu-id="5784a-205">Wpisz, `tlbexp.exe client.dll /out:CalcProxy.tlb` aby wyeksportować bibliotekę dll do pliku tlb.</span><span class="sxs-lookup"><span data-stu-id="5784a-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="5784a-206">Oczekiwano "Ostrzeżenia eksportera biblioteki typu", ale nie jest to problem, ponieważ typ ogólny nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="5784a-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="5784a-207">Wpisz, `regasm.exe /tlb:CalcProxy.tlb client.dll` aby zarejestrować typy w COM.</span><span class="sxs-lookup"><span data-stu-id="5784a-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="5784a-208">Przed uruchomieniem polecenia upewnij się, `regasm.exe` że ścieżka została ustawiona na folder, który zawiera.</span><span class="sxs-lookup"><span data-stu-id="5784a-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="5784a-209">`gacutil.exe /i client.dll` Wpisz, aby dodać zestaw do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="5784a-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="5784a-210">Przed uruchomieniem polecenia upewnij się, `gacutil.exe` że ścieżka została ustawiona na folder, który zawiera.</span><span class="sxs-lookup"><span data-stu-id="5784a-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="5784a-211">Sprawdź, czy można uzyskać dostęp do usługi z komputera klienckiego za pomocą przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="5784a-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="5784a-212">Na komputerze klienckim uruchom comcalcclient.vbs.</span><span class="sxs-lookup"><span data-stu-id="5784a-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="5784a-213">Aby oczyścić po próbce</span><span class="sxs-lookup"><span data-stu-id="5784a-213">To clean up after the sample</span></span>  
  
- <span data-ttu-id="5784a-214">Ze względów bezpieczeństwa usuń definicję katalogu wirtualnego i uprawnienia przyznane w krokach konfiguracji po zakończeniu pracy z próbkami.</span><span class="sxs-lookup"><span data-stu-id="5784a-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>  
