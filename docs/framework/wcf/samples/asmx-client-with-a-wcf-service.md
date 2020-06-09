---
title: Klient ASMX z usługą WCF
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: fd13d4907f1be09440387a36e14ecdc4926ba7e7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594780"
---
# <a name="asmx-client-with-a-wcf-service"></a><span data-ttu-id="582b7-102">Klient ASMX z usługą WCF</span><span class="sxs-lookup"><span data-stu-id="582b7-102">ASMX Client with a WCF Service</span></span>

<span data-ttu-id="582b7-103">W tym przykładzie pokazano, jak utworzyć usługę przy użyciu programu Windows Communication Foundation (WCF), a następnie uzyskać dostęp do usługi z poziomu klienta niepochodzącego z programu WCF, takiego jak Klient ASMX.</span><span class="sxs-lookup"><span data-stu-id="582b7-103">This sample demonstrates how to create a service using Windows Communication Foundation (WCF) and then access the service from a non-WCF client, such as an ASMX client.</span></span>

> [!NOTE]
> <span data-ttu-id="582b7-104">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="582b7-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="582b7-105">Ten przykład składa się z programu konsolowego klienta (exe) i biblioteki usług (. dll) hostowanej przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="582b7-105">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="582b7-106">Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="582b7-106">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="582b7-107">Kontrakt jest definiowany przez `ICalculator` interfejs, który udostępnia operacje matematyczne ( `Add` , `Subtract` , `Multiply` i `Divide` ).</span><span class="sxs-lookup"><span data-stu-id="582b7-107">The contract is defined by the `ICalculator` interface, which exposes math operations (`Add`, `Subtract`, `Multiply`, and `Divide`).</span></span> <span data-ttu-id="582b7-108">Klient ASMX wykonuje synchroniczne żądania do operacji matematycznej i odpowiedzi usługi z wynikiem.</span><span class="sxs-lookup"><span data-stu-id="582b7-108">The ASMX client makes synchronous requests to a math operation and the service replies with the result.</span></span>

<span data-ttu-id="582b7-109">Usługa implementuje `ICalculator` kontrakt zgodnie z definicją w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="582b7-109">The service implements an `ICalculator` contract as defined in the following code.</span></span>

```csharp
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

<span data-ttu-id="582b7-110"><xref:System.Runtime.Serialization.DataContractSerializer>I <xref:System.Xml.Serialization.XmlSerializer> MAPUJ typy CLR na reprezentację XML.</span><span class="sxs-lookup"><span data-stu-id="582b7-110">The <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Xml.Serialization.XmlSerializer> map CLR types to an XML representation.</span></span> <span data-ttu-id="582b7-111"><xref:System.Runtime.Serialization.DataContractSerializer>Interpretuje niektóre reprezentacje XML inaczej niż XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="582b7-111">The <xref:System.Runtime.Serialization.DataContractSerializer> interprets some XML representations differently than XmlSerializer.</span></span> <span data-ttu-id="582b7-112">Generatory proxy inne niż WCF, takie jak WSDL. exe, generują interfejs bardziej użyteczny, gdy jest używany element XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="582b7-112">Non-WCF proxy generators, such as Wsdl.exe, generate a more usable interface when the XmlSerializer is being used.</span></span> <span data-ttu-id="582b7-113"><xref:System.ServiceModel.XmlSerializerFormatAttribute>Jest stosowany do `ICalculator` interfejsu, aby upewnić się, że XmlSerializer jest używany do mapowania typów CLR na XML.</span><span class="sxs-lookup"><span data-stu-id="582b7-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute> is applied to the `ICalculator` interface, to ensure that the XmlSerializer is used for mapping CLR types to XML.</span></span> <span data-ttu-id="582b7-114">Implementacja usługi oblicza i zwraca odpowiedni wynik.</span><span class="sxs-lookup"><span data-stu-id="582b7-114">The service implementation calculates and returns the appropriate result.</span></span>

<span data-ttu-id="582b7-115">Usługa udostępnia jeden punkt końcowy do komunikacji z usługą, zdefiniowany przy użyciu pliku konfiguracji (Web. config).</span><span class="sxs-lookup"><span data-stu-id="582b7-115">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="582b7-116">Punkt końcowy składa się z adresu, powiązania i kontraktu.</span><span class="sxs-lookup"><span data-stu-id="582b7-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="582b7-117">Usługa uwidacznia punkt końcowy pod adresem podstawowym dostarczonym przez hosta Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="582b7-117">The service exposes the endpoint at the base address provided by the Internet Information Services (IIS) host.</span></span> <span data-ttu-id="582b7-118">`binding`Atrybut jest ustawiany na BasicHttpBinding, który zapewnia komunikację HTTP przy użyciu protokołu SOAP 1,1, który jest zgodny z protokołem WS-I BasicProfile 1,1, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="582b7-118">The `binding` attribute is set to basicHttpBinding that provides HTTP communications using SOAP 1.1, which is compliant with WS-I BasicProfile 1.1 as shown in the following sample configuration.</span></span>

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

<span data-ttu-id="582b7-119">Klient ASMX komunikuje się z usługą WCF przy użyciu serwera proxy z określonym typem, który jest generowany przez narzędzie Web Services Description Language (WSDL) (WSDL. exe).</span><span class="sxs-lookup"><span data-stu-id="582b7-119">The ASMX client communicates with the WCF service using a typed proxy that is generated by the Web Services Description Language (WSDL) utility (Wsdl.exe).</span></span> <span data-ttu-id="582b7-120">Typ serwera proxy jest zawarty w pliku generatedClient.cs.</span><span class="sxs-lookup"><span data-stu-id="582b7-120">The typed proxy is contained in the file generatedClient.cs.</span></span> <span data-ttu-id="582b7-121">Narzędzie WSDL pobiera metadane dla określonej usługi i generuje serwer proxy z określonym typem, który będzie używany przez klienta do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="582b7-121">The WSDL utility retrieves metadata for the specified service and generates a typed proxy for use by a client to communicate.</span></span> <span data-ttu-id="582b7-122">Domyślnie platforma nie ujawnia żadnych metadanych.</span><span class="sxs-lookup"><span data-stu-id="582b7-122">By default, the framework does not expose any metadata.</span></span> <span data-ttu-id="582b7-123">Aby udostępnić metadane wymagane do wygenerowania serwera proxy, należy dodać [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) i ustawić jego atrybut, `httpGetEnabled` `True` tak jak pokazano w poniższej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="582b7-123">To expose the metadata required to generate the proxy, you must add a [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) and set its `httpGetEnabled` attribute to `True` as shown in the following configuration.</span></span>

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

<span data-ttu-id="582b7-124">Uruchom następujące polecenie w wierszu polecenia w katalogu klienta, aby wygenerować serwer proxy z określonym typem.</span><span class="sxs-lookup"><span data-stu-id="582b7-124">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>

```console
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl
```

<span data-ttu-id="582b7-125">Korzystając z wygenerowanego typu serwera proxy, klient może uzyskać dostęp do danego punktu końcowego usługi przez skonfigurowanie odpowiedniego adresu.</span><span class="sxs-lookup"><span data-stu-id="582b7-125">By using the generated typed proxy, the client can access a given service endpoint by configuring the appropriate address.</span></span> <span data-ttu-id="582b7-126">Klient używa pliku konfiguracji (App. config), aby określić punkt końcowy do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="582b7-126">The client uses a configuration file (App.config) to specify the endpoint to communicate with.</span></span>

```xml
<appSettings>
  <add key="CalculatorServiceAddress"
       value="http://localhost/ServiceModelSamples/service.svc"/>
</appSettings>
```

<span data-ttu-id="582b7-127">Implementacja klienta Konstruuje wystąpienie serwera proxy o określonym typie, aby rozpocząć komunikację z usługą.</span><span class="sxs-lookup"><span data-stu-id="582b7-127">The client implementation constructs an instance of the typed proxy to begin communicating with the service.</span></span>

```csharp
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

<span data-ttu-id="582b7-128">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="582b7-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="582b7-129">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="582b7-129">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="582b7-130">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="582b7-130">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="582b7-131">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="582b7-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="582b7-132">Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="582b7-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="582b7-133">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="582b7-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="582b7-134">Aby uzyskać więcej informacji na temat przekazywania i zwracania złożonych typów danych, zobacz: [powiązanie danych w kliencie Windows Forms](data-binding-in-a-windows-forms-client.md), [powiązanie danych w kliencie Windows Presentation Foundation](data-binding-in-a-wpf-client.md)i [powiązanie danych w kliencie ASP.NET](data-binding-in-an-aspnet-client.md)</span><span class="sxs-lookup"><span data-stu-id="582b7-134">For more information about passing and returning complex data types see: [Data Binding in a Windows Forms Client](data-binding-in-a-windows-forms-client.md), [Data Binding in a Windows Presentation Foundation Client](data-binding-in-a-wpf-client.md), and [Data Binding in an ASP.NET Client](data-binding-in-an-aspnet-client.md)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="582b7-135">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="582b7-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="582b7-136">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="582b7-136">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="582b7-137">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="582b7-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="582b7-138">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="582b7-138">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`
