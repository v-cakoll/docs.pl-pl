---
title: Wprowadzenie — przykład
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- basic samples [WCF], getting started
ms.assetid: 967a3d94-0261-49ff-b85a-20bb07f1af20
ms.openlocfilehash: 12568b2bb86257ed7075f2dc83b8077714a1318e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347039"
---
# <a name="getting-started-sample"></a><span data-ttu-id="33688-102">Wprowadzenie — przykład</span><span class="sxs-lookup"><span data-stu-id="33688-102">Getting Started Sample</span></span>

<span data-ttu-id="33688-103">Przykład Wprowadzenie ilustruje sposób implementacji typowej usługi i typowego klienta przy użyciu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="33688-103">The Getting Started sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="33688-104">Ten przykład jest podstawą dla wszystkich innych podstawowych przykładów technologii.</span><span class="sxs-lookup"><span data-stu-id="33688-104">This sample is the basis for all other basic technology samples.</span></span>

> [!NOTE]
> <span data-ttu-id="33688-105">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="33688-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="33688-106">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="33688-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="33688-107">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="33688-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="33688-108">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="33688-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="33688-109">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="33688-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\GettingStarted\GettingStarted`

<span data-ttu-id="33688-110">Usługa opisuje operacje wykonywane w ramach kontraktu usługi, które ujawnia publicznie jako metadane.</span><span class="sxs-lookup"><span data-stu-id="33688-110">The service describes the operations it performs in a service contract that it exposes publicly as metadata.</span></span> <span data-ttu-id="33688-111">Usługa zawiera również kod umożliwiający zaimplementowanie operacji.</span><span class="sxs-lookup"><span data-stu-id="33688-111">The service also contains the code to implement the operations.</span></span>

<span data-ttu-id="33688-112">Klient zawiera definicję kontraktu usługi i klasy proxy w celu uzyskania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="33688-112">The client contains a definition of the service contract and a proxy class for accessing the service.</span></span> <span data-ttu-id="33688-113">Kod serwera proxy jest generowany na podstawie metadanych usługi przy użyciu [Narzędzia do obsługi metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="33688-113">The proxy code is generated from the service metadata using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>

<span data-ttu-id="33688-114">W systemie Windows Vista usługa jest hostowana w usłudze aktywacji systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="33688-114">On Windows Vista, the service is hosted in the Windows Activation Service (WAS).</span></span> <span data-ttu-id="33688-115">W systemach [!INCLUDE[wxp](../../../../includes/wxp-md.md)] i Windows Server 2003 jest on hostowany przez Internet Information Services (IIS) i ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="33688-115">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] and Windows Server 2003, it is hosted by Internet Information Services (IIS) and ASP.NET.</span></span> <span data-ttu-id="33688-116">Hostowanie usługi w usługach IIS lub zezwala na automatyczne Aktywowanie usługi przy pierwszym dostępie.</span><span class="sxs-lookup"><span data-stu-id="33688-116">Hosting a service in IIS or WAS allows the service to be activated automatically when it is accessed for the first time.</span></span>

> [!NOTE]
> <span data-ttu-id="33688-117">Jeśli wolisz rozpocząć pracę z przykładem, który hostuje usługę w aplikacji konsolowej zamiast usług IIS, [Zobacz przykład samoobsługi.](../../../../docs/framework/wcf/samples/self-host.md)</span><span class="sxs-lookup"><span data-stu-id="33688-117">If you would prefer to get started with a sample that hosts the service in a console application instead of IIS, see the [Self-Host](../../../../docs/framework/wcf/samples/self-host.md) sample.</span></span>

<span data-ttu-id="33688-118">Usługa i klient określają szczegóły dostępu w ustawieniach pliku konfiguracji, co zapewnia elastyczność w czasie wdrażania.</span><span class="sxs-lookup"><span data-stu-id="33688-118">The service and client specify access details in configuration file settings, which provide flexibility at the time of deployment.</span></span> <span data-ttu-id="33688-119">Obejmuje to definicję punktu końcowego, który określa adres, powiązanie i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="33688-119">This includes an endpoint definition that specifies an address, binding, and contract.</span></span> <span data-ttu-id="33688-120">Powiązanie określa szczegóły dotyczące transportu i zabezpieczeń dotyczące sposobu uzyskiwania dostępu do usługi.</span><span class="sxs-lookup"><span data-stu-id="33688-120">The binding specifies transport and security details for how the service is to be accessed.</span></span>

<span data-ttu-id="33688-121">Usługa konfiguruje zachowanie w czasie wykonywania w celu opublikowania jego metadanych.</span><span class="sxs-lookup"><span data-stu-id="33688-121">The service configures a run-time behavior to publish its metadata.</span></span>

<span data-ttu-id="33688-122">Usługa implementuje kontrakt definiujący wzorzec komunikacji żądanie-odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="33688-122">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="33688-123">Kontrakt jest definiowany przez interfejs `ICalculator`, który udostępnia operacje matematyczne (Dodawanie, odejmowanie, mnożenie i dzielenie).</span><span class="sxs-lookup"><span data-stu-id="33688-123">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="33688-124">Klient wysyła żądania do danej operacji matematycznej i zwraca odpowiedzi usługi z wynikiem.</span><span class="sxs-lookup"><span data-stu-id="33688-124">The client makes requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="33688-125">Usługa implementuje kontrakt `ICalculator`, który jest zdefiniowany w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="33688-125">The service implements an `ICalculator` contract that is defined in the following code.</span></span>

```vb
' Define a service contract.
    <ServiceContract(Namespace:="http://Microsoft.Samples.GettingStarted")>
     Public Interface ICalculator
        <OperationContract()>
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()>
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
```

```csharp
// Define a service contract.
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

<span data-ttu-id="33688-126">Implementacja usługi oblicza i zwraca odpowiedni wynik, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="33688-126">The service implementation calculates and returns the appropriate result, as shown in the following example code.</span></span>

```vb
' Service class which implements the service contract.
Public Class CalculatorService
Implements ICalculator
Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
Return n1 + n2
End Function

Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
Return n1 - n2
End Function

Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
Return n1 * n2
End Function

Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
Return n1 / n2
End Function
End Class
```

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="33688-127">Usługa udostępnia punkt końcowy do komunikacji z usługą, zdefiniowany przy użyciu pliku konfiguracji (Web. config), jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="33688-127">The service exposes an endpoint for communicating with the service, defined using a configuration file (Web.config), as shown in the following sample configuration.</span></span>

```xaml
<services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
        <!-- ICalculator is exposed at the base address provided by
         host: http://localhost/servicemodelsamples/service.svc.  -->
       <endpoint address=""
              binding="wsHttpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
       ...
    </service>
</services>
```

<span data-ttu-id="33688-128">Usługa uwidacznia punkt końcowy pod adresem podstawowym dostarczonym przez usługi IIS lub hosta.</span><span class="sxs-lookup"><span data-stu-id="33688-128">The service exposes the endpoint at the base address provided by the IIS or WAS host.</span></span> <span data-ttu-id="33688-129">Powiązanie jest skonfigurowane przy użyciu standardowej <xref:System.ServiceModel.WSHttpBinding>, która zapewnia komunikację HTTP i standardowe protokoły usług sieci Web do adresowania i zabezpieczenia.</span><span class="sxs-lookup"><span data-stu-id="33688-129">The binding is configured with a standard <xref:System.ServiceModel.WSHttpBinding>, which provides HTTP communication and standard Web service protocols for addressing and security.</span></span> <span data-ttu-id="33688-130">Kontrakt jest `ICalculator` zaimplementowany przez usługę.</span><span class="sxs-lookup"><span data-stu-id="33688-130">The contract is the `ICalculator` implemented by the service.</span></span>

<span data-ttu-id="33688-131">Zgodnie z konfiguracją usługa może być dostępna na `http://localhost/servicemodelsamples/service.svc` przez klienta programu na tym samym komputerze.</span><span class="sxs-lookup"><span data-stu-id="33688-131">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="33688-132">Aby klienci na komputerach zdalnych mogli uzyskać dostęp do usługi, należy określić w pełni kwalifikowaną nazwę domeny zamiast hosta lokalnego.</span><span class="sxs-lookup"><span data-stu-id="33688-132">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span>

<span data-ttu-id="33688-133">Struktura nie ujawnia domyślnie metadanych.</span><span class="sxs-lookup"><span data-stu-id="33688-133">The framework does not expose metadata by default.</span></span> <span data-ttu-id="33688-134">W związku z tym usługa włącza <xref:System.ServiceModel.Description.ServiceMetadataBehavior> i uwidacznia punkt końcowy wymiany metadanych (MEX) w `http://localhost/servicemodelsamples/service.svc/mex`.</span><span class="sxs-lookup"><span data-stu-id="33688-134">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> and exposes a metadata exchange (MEX) endpoint at `http://localhost/servicemodelsamples/service.svc/mex`.</span></span> <span data-ttu-id="33688-135">Poniżej przedstawiono konfigurację.</span><span class="sxs-lookup"><span data-stu-id="33688-135">The following configuration demonstrates this.</span></span>

```xaml
<system.serviceModel>
  <services>
    <service
        name="Microsoft.ServiceModel.Samples.CalculatorService"
        behaviorConfiguration="CalculatorServiceBehavior">
      ...
      <!-- the mex endpoint is exposed at
       http://localhost/servicemodelsamples/service.svc/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>

  <!--For debugging purposes set the includeExceptionDetailInFaults
   attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True"/>
        <serviceDebug includeExceptionDetailInFaults="False" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```

<span data-ttu-id="33688-136">Klient komunikuje się przy użyciu danego typu kontraktu przy użyciu klasy klienta, która jest generowana przez [Narzędzie narzędzia metadanych ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="33688-136">The client communicates using a given contract type by using a client class that is generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="33688-137">Ten wygenerowany klient jest zawarty w pliku generatedClient.cs lub generatedClient. vb.</span><span class="sxs-lookup"><span data-stu-id="33688-137">This generated client is contained in the file generatedClient.cs or generatedClient.vb.</span></span> <span data-ttu-id="33688-138">To narzędzie pobiera metadane dla danej usługi i generuje klienta do użytku przez aplikację kliencką w celu komunikowania się przy użyciu danego typu kontraktu.</span><span class="sxs-lookup"><span data-stu-id="33688-138">This utility retrieves metadata for a given service and generates a client for use by the client application to communicate using a given contract type.</span></span> <span data-ttu-id="33688-139">Usługa hostowana musi być dostępna do wygenerowania kodu klienta, ponieważ usługa jest używana do pobierania zaktualizowanych metadanych.</span><span class="sxs-lookup"><span data-stu-id="33688-139">The hosted service must be available to generate the client code, because the service is used to retrieve the updated metadata.</span></span>

 <span data-ttu-id="33688-140">Uruchom następujące polecenie w wierszu polecenia zestawu SDK w katalogu klienta, aby wygenerować serwer proxy z określonym typem:</span><span class="sxs-lookup"><span data-stu-id="33688-140">Run the following command from the SDK command prompt in the client directory to generate the typed proxy:</span></span>

```console
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs
```

<span data-ttu-id="33688-141">Aby wygenerować klienta w Visual Basic wpisz następujące polecenie w wierszu polecenia zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="33688-141">To generate client in Visual Basic type the following from the SDK command prompt:</span></span>

`Svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /l:vb /out:generatedClient.vb`

<span data-ttu-id="33688-142">Korzystając z wygenerowanego klienta, klient może uzyskać dostęp do danego punktu końcowego usługi przez skonfigurowanie odpowiedniego adresu i powiązania.</span><span class="sxs-lookup"><span data-stu-id="33688-142">By using the generated client, the client can access a given service endpoint by configuring the appropriate address and binding.</span></span> <span data-ttu-id="33688-143">Podobnie jak w przypadku usługi, klient używa pliku konfiguracji (App. config) do określenia punktu końcowego, z którym chce się skomunikować.</span><span class="sxs-lookup"><span data-stu-id="33688-143">Like the service, the client uses a configuration file (App.config) to specify the endpoint with which it wants to communicate.</span></span> <span data-ttu-id="33688-144">Konfiguracja punktu końcowego klienta składa się z adresu bezwzględnego dla punktu końcowego usługi, powiązania i kontraktu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="33688-144">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract, as shown in the following example.</span></span>

```xaml
<client>
     <endpoint
         address="http://localhost/servicemodelsamples/service.svc"
         binding="wsHttpBinding"
         contract=" Microsoft.ServiceModel.Samples.ICalculator" />
</client>
```

<span data-ttu-id="33688-145">Implementacja klienta tworzy wystąpienie klienta i używa określonego interfejsu do rozpoczęcia komunikacji z usługą, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="33688-145">The client implementation instantiates the client and uses the typed interface to begin communicating with the service, as shown in the following example code.</span></span>

```vb
' Create a client
Dim client As New CalculatorClient()

' Call the Add service operation.
            Dim value1 = 100.0R
            Dim value2 = 15.99R
            Dim result = client.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)

' Call the Subtract service operation.
value1 = 145.00R
value2 = 76.54R
result = client.Subtract(value1, value2)
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result)

' Call the Multiply service operation.
value1 = 9.00R
value2 = 81.25R
result = client.Multiply(value1, value2)
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result)

' Call the Divide service operation.
value1 = 22.00R
value2 = 7.00R
result = client.Divide(value1, value2)
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result)

'Closing the client gracefully closes the connection and cleans up resources
```

```csharp
// Create a client.
CalculatorClient client = new CalculatorClient();

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

//Closing the client releases all communication resources.
client.Close();
```

<span data-ttu-id="33688-146">Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="33688-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="33688-147">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="33688-147">Press ENTER in the client window to shut down the client.</span></span>

```output
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

<span data-ttu-id="33688-148">Wprowadzenie przykład pokazuje standardowy sposób tworzenia usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="33688-148">The Getting Started sample shows the standard way to create a service and client.</span></span> <span data-ttu-id="33688-149">Druga [podstawowa](../../../../docs/framework/wcf/samples/basic-sample.md) Kompilacja tego przykładu w celu przedstawienia określonych funkcji produktu.</span><span class="sxs-lookup"><span data-stu-id="33688-149">The other [Basic](../../../../docs/framework/wcf/samples/basic-sample.md) build on this sample to demonstrate specific product features.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="33688-150">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="33688-150">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="33688-151">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33688-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="33688-152">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33688-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="33688-153">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="33688-153">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="33688-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33688-154">See also</span></span>

- [<span data-ttu-id="33688-155">Instrukcje: hostowanie usługi WCF w zarządzanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="33688-155">How to: Host a WCF Service in a Managed Application</span></span>](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)
- [<span data-ttu-id="33688-156">Instrukcje: hostowanie usługi WCF w programie IIS</span><span class="sxs-lookup"><span data-stu-id="33688-156">How to: Host a WCF Service in IIS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
