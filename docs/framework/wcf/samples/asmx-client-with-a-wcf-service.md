---
title: Klient ASMX z usługą WCF
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: 3465954cc937e1611634c8cd13a9264173e71817
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507202"
---
# <a name="asmx-client-with-a-wcf-service"></a><span data-ttu-id="fde4d-102">Klient ASMX z usługą WCF</span><span class="sxs-lookup"><span data-stu-id="fde4d-102">ASMX Client with a WCF Service</span></span>
<span data-ttu-id="fde4d-103">W tym przykładzie przedstawiono sposób tworzenia usługi przy użyciu usługi Windows Communication Foundation (WCF) i następnie uzyskać dostęp do usługi z klienta inne niż WCF, takich jak klient ASMX.</span><span class="sxs-lookup"><span data-stu-id="fde4d-103">This sample demonstrates how to create a service using Windows Communication Foundation (WCF) and then access the service from a non-WCF client, such as an ASMX client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fde4d-104">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="fde4d-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="fde4d-105">W tym przykładzie składa się z konsoli programu klienckiego (.exe) i usługi biblioteki (.dll), hostowanej przez Internetowe usługi informacyjne (IIS).</span><span class="sxs-lookup"><span data-stu-id="fde4d-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="fde4d-106">Usługa implementuje kontraktu, który definiuje wzorzec komunikacji "żądanie-odpowiedź".</span><span class="sxs-lookup"><span data-stu-id="fde4d-106">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="fde4d-107">Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne (`Add`, `Subtract`, `Multiply`, i `Divide`).</span><span class="sxs-lookup"><span data-stu-id="fde4d-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="fde4d-108">Klient ASMX wysyła żądań synchronicznych operacji matematycznych i odpowiedzi usługi z wynikiem.</span><span class="sxs-lookup"><span data-stu-id="fde4d-108">The ASMX client makes synchronous requests to a math operation and the service replies with the result.</span></span>  
  
 <span data-ttu-id="fde4d-109">Implementuje usługi `ICalculator` Umowę zgodnie z definicją w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="fde4d-109">The service implements an `ICalculator` contract as defined in the following code.</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]  
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
  
 <span data-ttu-id="fde4d-110"><xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Xml.Serialization.XmlSerializer> mapowania typów CLR reprezentację XML.</span><span class="sxs-lookup"><span data-stu-id="fde4d-110">The <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Xml.Serialization.XmlSerializer> map CLR types to an XML representation.</span></span> <span data-ttu-id="fde4d-111"><xref:System.Runtime.Serialization.DataContractSerializer> Inaczej niż element XmlSerializer interpretuje niektóre reprezentacji XML.</span><span class="sxs-lookup"><span data-stu-id="fde4d-111">The <xref:System.Runtime.Serialization.DataContractSerializer> interprets some XML representations differently than XmlSerializer.</span></span> <span data-ttu-id="fde4d-112">Generatory serwera proxy spoza WCF, takich jak Wsdl.exe, generowania bardziej użyteczne interfejsu używanego elementu XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="fde4d-112">Non-WCF proxy generators, such as Wsdl.exe, generate a more usable interface when the XmlSerializer is being used.</span></span> <span data-ttu-id="fde4d-113"><xref:System.ServiceModel.XmlSerializerFormatAttribute> Jest stosowany do `ICalculator` interfejsu, aby upewnić się, że element XmlSerializer służy do mapowania typów CLR do pliku XML.</span><span class="sxs-lookup"><span data-stu-id="fde4d-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> is applied to the `ICalculator` interface, to ensure that the XmlSerializer is used for mapping CLR types to XML.</span></span> <span data-ttu-id="fde4d-114">Implementacja usługi oblicza i zwraca odpowiedni wynik.</span><span class="sxs-lookup"><span data-stu-id="fde4d-114">The service implementation calculates and returns the appropriate result.</span></span>  
  
 <span data-ttu-id="fde4d-115">Usługa udostępnia jeden punkt końcowy do komunikacji z usługą zdefiniowane przy użyciu pliku konfiguracji (Web.config).</span><span class="sxs-lookup"><span data-stu-id="fde4d-115">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="fde4d-116">Punkt końcowy składa się z adresu, powiązanie i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="fde4d-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="fde4d-117">Usługa udostępnia punkt końcowy pod podstawowym adresem udostępniane przez hosta usług Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="fde4d-117">The service exposes the endpoint at the base address provided by the Internet Information Services (IIS) host.</span></span> <span data-ttu-id="fde4d-118">`binding` Atrybut jest ustawiony na basicHttpBinding, zapewniająca komunikacji HTTP przy użyciu protokołu SOAP 1.1, który jest zgodny z protokołu WS-I BasicProfile 1.1, jak pokazano w poniższym Przykładowa konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="fde4d-118">The `binding` attribute is set to basicHttpBinding that provides HTTP communications using SOAP 1.1, which is compliant with WS-I BasicProfile 1.1 as shown in the following sample configuration.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc.  -->  
    <endpoint address=""  
              binding="basicHttpBinding"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </service>  
</services>  
```  
  
 <span data-ttu-id="fde4d-119">Klient ASMX komunikuje się z usługą WCF, za pomocą typizowanego serwera proxy, który jest generowany przez narzędzie Web Services Description Language (WSDL) (Wsdl.exe).</span><span class="sxs-lookup"><span data-stu-id="fde4d-119">The ASMX client communicates with the WCF service using a typed proxy that is generated by the Web Services Description Language (WSDL) utility (Wsdl.exe).</span></span> <span data-ttu-id="fde4d-120">Typizowanego serwera proxy znajduje się w generatedClient.cs pliku.</span><span class="sxs-lookup"><span data-stu-id="fde4d-120">The typed proxy is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="fde4d-121">Narzędzie WSDL pobiera metadane dla określonej usługi i generuje typizowanego serwera proxy do użytku przez klienta do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="fde4d-121">The WSDL utility retrieves metadata for the specified service and generates a typed proxy for use by a client to communicate.</span></span> <span data-ttu-id="fde4d-122">Domyślnie struktura nie ujawnia żadnych metadanych.</span><span class="sxs-lookup"><span data-stu-id="fde4d-122">By default, the framework does not expose any metadata.</span></span> <span data-ttu-id="fde4d-123">Aby udostępnić metadane wymagane do generowania serwera proxy, należy dodać [ \<serviceMetadata w pliku >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) i ustaw jego `httpGetEnabled` atrybutu `True` jak pokazano na następującej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="fde4d-123">To expose the metadata required to generate the proxy, you must add a [\<serviceMetadata>](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) and set its `httpGetEnabled` attribute to `True` as shown in the following configuration.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- Setting httpGetEnabled to True on the serviceMetadata  
           behavior exposes the service's wsdl at <base address>?wsdl :  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="fde4d-124">Uruchom następujące polecenie w wierszu polecenia w katalogu klienta można wygenerować typizowanego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="fde4d-124">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl  
```  
  
 <span data-ttu-id="fde4d-125">Za pomocą wygenerowanego typizowanego serwera proxy, ten klient uzyskuje dostęp danego punktu końcowego, konfigurując odpowiedni adres.</span><span class="sxs-lookup"><span data-stu-id="fde4d-125">By using the generated typed proxy, the client can access a given service endpoint by configuring the appropriate address.</span></span> <span data-ttu-id="fde4d-126">Klient korzysta z do określania punktu końcowego do komunikowania się z plikiem konfiguracyjnym (App.config).</span><span class="sxs-lookup"><span data-stu-id="fde4d-126">The client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span>  
  
```xml  
<appSettings>  
  <add key="CalculatorServiceAddress"   
       value="http://localhost/ServiceModelSamples/service.svc"/>  
</appSettings>  
```  
  
 <span data-ttu-id="fde4d-127">Implementacja klienta tworzy wystąpienie klasy typizowanego serwera proxy, aby rozpocząć, komunikacji z usługą.</span><span class="sxs-lookup"><span data-stu-id="fde4d-127">The client implementation constructs an instance of the typed proxy to begin communicating with the service.</span></span>  
  
```  
// Create a client to the CalculatorService.  
using (CalculatorService client = new CalculatorService())  
{  
    // Call the Add service operation.  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation.  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Multiply service operation.  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
}  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="fde4d-128">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="fde4d-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="fde4d-129">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="fde4d-129">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fde4d-130">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="fde4d-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="fde4d-131">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fde4d-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="fde4d-132">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fde4d-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="fde4d-133">Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fde4d-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fde4d-134">Aby uzyskać więcej informacji na temat przekazywanie i zwracanie złożonych danych Zobacz typy: [powiązanie danych w kliencie Windows Forms](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [powiązanie danych w kliencie systemu Windows Presentation Foundation](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), i [danych Powiązanie w kliencie programu ASP.NET](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span><span class="sxs-lookup"><span data-stu-id="fde4d-134">For more information about passing and returning complex data types see: [Data Binding in a Windows Forms Client](../../../../docs/framework/wcf/samples/data-binding-in-a-windows-forms-client.md), [Data Binding in a Windows Presentation Foundation Client](../../../../docs/framework/wcf/samples/data-binding-in-a-wpf-client.md), and [Data Binding in an ASP.NET Client](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fde4d-135">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fde4d-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fde4d-136">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fde4d-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fde4d-137">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="fde4d-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fde4d-138">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fde4d-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`  
  
## <a name="see-also"></a><span data-ttu-id="fde4d-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fde4d-139">See Also</span></span>
