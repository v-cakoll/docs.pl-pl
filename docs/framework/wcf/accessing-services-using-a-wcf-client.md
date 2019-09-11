---
title: Uzyskiwanie dostępu do usług za pomocą klienta WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: ae589e1c418b1cf13fe9f5b34648bdf7a2210eed
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855673"
---
# <a name="accessing-services-using-a-wcf-client"></a><span data-ttu-id="a9590-102">Uzyskiwanie dostępu do usług za pomocą klienta WCF</span><span class="sxs-lookup"><span data-stu-id="a9590-102">Accessing Services Using a WCF Client</span></span>

<span data-ttu-id="a9590-103">Następnym krokiem po utworzeniu usługi jest utworzenie serwera proxy klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="a9590-103">After you create a service, the next step is to create a WCF client proxy.</span></span> <span data-ttu-id="a9590-104">Aplikacja kliencka używa serwera proxy klienta WCF do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="a9590-104">A client application uses the WCF client proxy to communicate with the service.</span></span> <span data-ttu-id="a9590-105">Aplikacje klienckie zazwyczaj importują metadane usługi w celu wygenerowania kodu klienta WCF, którego można użyć do wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="a9590-105">Client applications usually import a service's metadata to generate WCF client code that can be used to invoke the service.</span></span>

 <span data-ttu-id="a9590-106">Podstawowe kroki tworzenia klienta WCF są następujące:</span><span class="sxs-lookup"><span data-stu-id="a9590-106">The basic steps for creating a WCF client include the following:</span></span>

1. <span data-ttu-id="a9590-107">Skompiluj kod usługi.</span><span class="sxs-lookup"><span data-stu-id="a9590-107">Compile the service code.</span></span>

2. <span data-ttu-id="a9590-108">Generuj serwer proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="a9590-108">Generate the WCF client proxy.</span></span>

3. <span data-ttu-id="a9590-109">Tworzenie wystąpienia serwera proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="a9590-109">Instantiate the WCF client proxy.</span></span>

<span data-ttu-id="a9590-110">Serwer proxy klienta WCF można wygenerować ręcznie przy użyciu narzędzia metadanych modelu usług (SvcUtil. exe), aby uzyskać więcej informacji, zobacz [Narzędzie narzędzia metadanych ServiceModel (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="a9590-110">The WCF client proxy can be generated manually by using the Service Model Metadata Utility Tool (SvcUtil.exe) for more information see, [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="a9590-111">Serwer proxy klienta WCF można również wygenerować w programie Visual Studio przy użyciu funkcji **Dodaj odwołanie do usługi** .</span><span class="sxs-lookup"><span data-stu-id="a9590-111">The WCF client proxy can also be generated within Visual Studio using the **Add Service Reference**  feature.</span></span> <span data-ttu-id="a9590-112">Aby wygenerować serwer proxy klienta WCF przy użyciu dowolnej metody, musi być uruchomiona usługa.</span><span class="sxs-lookup"><span data-stu-id="a9590-112">To generate the WCF client proxy using either method the service must be running.</span></span> <span data-ttu-id="a9590-113">Jeśli usługa jest samoobsługowa, należy uruchomić hosta.</span><span class="sxs-lookup"><span data-stu-id="a9590-113">If the service is self-hosted you must run the host.</span></span> <span data-ttu-id="a9590-114">Jeśli usługa jest hostowana w programie IIS/nie trzeba wykonywać żadnych innych czynności.</span><span class="sxs-lookup"><span data-stu-id="a9590-114">If the service is hosted in IIS/WAS you do not need to do anything else.</span></span>

## <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="a9590-115">Narzędzie do przesyłania metadanych ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a9590-115">ServiceModel Metadata Utility Tool</span></span>
 <span data-ttu-id="a9590-116">[Narzędzie do przesyłania metadanych modelu ServiceModel (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) jest narzędziem wiersza polecenia do generowania kodu z metadanych.</span><span class="sxs-lookup"><span data-stu-id="a9590-116">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) is a command-line tool for generating code from metadata.</span></span> <span data-ttu-id="a9590-117">Poniżej przedstawiono przykład podstawowego polecenia Svcutil. exe.</span><span class="sxs-lookup"><span data-stu-id="a9590-117">The following use is an example of a basic Svcutil.exe command.</span></span>

```console
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 <span data-ttu-id="a9590-118">Alternatywnie można użyć programu Svcutil. exe z plikami Web Services Description Language (WSDL) i XML schematu Definition Language (XSD) w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="a9590-118">Alternatively, you can use Svcutil.exe with Web Services Description Language (WSDL) and XML Schema definition language (XSD) files on the file system.</span></span>

```console
Svcutil.exe <list of WSDL and XSD files on file system>
```

 <span data-ttu-id="a9590-119">Wynikiem jest plik kodu, który zawiera kod klienta WCF, którego aplikacja kliencka może użyć do wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="a9590-119">The result is a code file that contains WCF client code that the client application can use to invoke the service.</span></span>

 <span data-ttu-id="a9590-120">Możesz również użyć narzędzia do generowania plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a9590-120">You can also use the tool to generate configuration files.</span></span>

```console
Svcutil.exe <file1 [,file2]>
```

 <span data-ttu-id="a9590-121">Jeśli podano tylko jedną nazwę pliku, która jest nazwą pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a9590-121">If only one file name is given, that is the name of the output file.</span></span> <span data-ttu-id="a9590-122">Jeśli podano dwie nazwy plików, pierwszy plik jest plikiem konfiguracji wejściowej, którego zawartość jest scalana z wygenerowaną konfiguracją i zapisywana w drugim pliku.</span><span class="sxs-lookup"><span data-stu-id="a9590-122">If two file names are given, then the first file is an input configuration file whose contents are merged with the generated configuration and written out into the second file.</span></span> <span data-ttu-id="a9590-123">Aby uzyskać więcej informacji na temat konfiguracji, zobacz [Konfigurowanie powiązań dla usług](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="a9590-123">For more information about configuration, see [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a9590-124">Niezabezpieczone żądania metadanych stanowią pewne zagrożenia w taki sam sposób, w jaki wszystkie niezabezpieczone żądania sieciowe: Jeśli nie masz pewności, że punkt końcowy, z którym nawiązujesz połączenie, jest on widoczny, a pobierane informacje mogą być metadanymi ze złośliwej usługi.</span><span class="sxs-lookup"><span data-stu-id="a9590-124">Unsecured metadata requests pose certain risks in the same way that any unsecured network request does: If you are not certain that the endpoint you are communicating with is who it says it is, the information you retrieve might be metadata from a malicious service.</span></span>

## <a name="add-service-reference-in-visual-studio"></a><span data-ttu-id="a9590-125">Dodaj odwołanie do usługi w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a9590-125">Add Service Reference in Visual Studio</span></span>

 <span data-ttu-id="a9590-126">Po uruchomieniu usługi kliknij prawym przyciskiem myszy projekt, który będzie zawierać serwer proxy klienta WCF i wybierz polecenie **Dodaj** > **odwołanie do usługi**.</span><span class="sxs-lookup"><span data-stu-id="a9590-126">With the service running, right click the project that will contain the WCF client proxy and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="a9590-127">W **oknie dialogowym Dodaj odwołanie do usługi**wpisz adres URL usługi, którą chcesz wywołać, a następnie kliknij przycisk **Przejdź** .</span><span class="sxs-lookup"><span data-stu-id="a9590-127">In the **Add Service Reference Dialog**, type in the URL to the service you want to call and click the **Go** button.</span></span> <span data-ttu-id="a9590-128">W oknie dialogowym zostanie wyświetlona lista usług dostępnych pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="a9590-128">The dialog will display a list of services available at the address you specify.</span></span> <span data-ttu-id="a9590-129">Kliknij dwukrotnie usługę, aby wyświetlić dostępne kontrakty i operacje, określ przestrzeń nazw dla wygenerowanego kodu, a następnie kliknij przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="a9590-129">Double click the service to see the contracts and operations available, specify a namespace for the generated code, and click the **OK** button.</span></span>

## <a name="example"></a><span data-ttu-id="a9590-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9590-130">Example</span></span>
 <span data-ttu-id="a9590-131">Poniższy przykład kodu przedstawia kontrakt usługi utworzony dla usługi.</span><span class="sxs-lookup"><span data-stu-id="a9590-131">The following code example shows a service contract created for a service.</span></span>

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    // Other methods are not shown here.
}
```

```vb
' Define a service contract.
<ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
Public Interface ICalculator
    <OperationContract()>  _
    Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
    ' Other methods are not shown here.
End Interface
```

 <span data-ttu-id="a9590-132">Narzędzie do przesyłania metadanych ServiceModel i **Dodaj odwołanie do usługi** w programie Visual Studio generuje następujące klasy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="a9590-132">The ServiceModel Metadata utility tool and **Add Service Reference** in Visual Studio generates the following WCF client class.</span></span> <span data-ttu-id="a9590-133">Klasa dziedziczy z klasy generycznej <xref:System.ServiceModel.ClientBase%601> i `ICalculator` implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="a9590-133">The class inherits from the generic <xref:System.ServiceModel.ClientBase%601> class and implements the `ICalculator` interface.</span></span> <span data-ttu-id="a9590-134">Narzędzie generuje `ICalculator` również interfejs (nie pokazano tutaj).</span><span class="sxs-lookup"><span data-stu-id="a9590-134">The tool also generates the `ICalculator` interface (not shown here).</span></span>

```csharp
public partial class CalculatorClient : System.ServiceModel.ClientBase<ICalculator>, ICalculator
{
    public CalculatorClient()
    {}

    public CalculatorClient(string endpointConfigurationName) :
            base(endpointConfigurationName)
    {}

    public CalculatorClient(string endpointConfigurationName, string remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(string endpointConfigurationName,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(endpointConfigurationName, remoteAddress)
    {}

    public CalculatorClient(System.ServiceModel.Channels.Binding binding,
        System.ServiceModel.EndpointAddress remoteAddress) :
            base(binding, remoteAddress)
    {}

    public double Add(double n1, double n2)
    {
        return base.Channel.Add(n1, n2);
    }
}
```

```vb
Partial Public Class CalculatorClient
    Inherits System.ServiceModel.ClientBase(Of ICalculator)
    Implements ICalculator

    Public Sub New()
        MyBase.New
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String)
        MyBase.New(endpointConfigurationName)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String, ByVal remoteAddress As String)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal endpointConfigurationName As String,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(endpointConfigurationName, remoteAddress)
    End Sub

    Public Sub New(ByVal binding As System.ServiceModel.Channels.Binding,
        ByVal remoteAddress As System.ServiceModel.EndpointAddress)
        MyBase.New(binding, remoteAddress)
    End Sub

    Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        Implements ICalculator.Add
        Return MyBase.Channel.Add(n1, n2)
    End Function
End Class
```

## <a name="using-the-wcf-client"></a><span data-ttu-id="a9590-135">Korzystanie z klienta WCF</span><span class="sxs-lookup"><span data-stu-id="a9590-135">Using the WCF Client</span></span>
 <span data-ttu-id="a9590-136">Aby użyć klienta WCF, Utwórz wystąpienie klienta WCF, a następnie Wywołaj jego metody, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a9590-136">To use the WCF client, create an instance of the WCF client, and then call its methods, as shown in the following code.</span></span>

```csharp
// Create a client object with the given client endpoint configuration.
CalculatorClient calcClient = new CalculatorClient("CalculatorEndpoint"));
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = calcClient.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

```vb
' Create a client object with the given client endpoint configuration.
Dim calcClient As CalculatorClient = _
New CalculatorClient("CalculatorEndpoint")

' Call the Add service operation.
Dim value1 As Double = 100.00D
Dim value2 As Double = 15.99D
Dim result As Double = calcClient.Add(value1, value2)
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result)
```

## <a name="debugging-exceptions-thrown-by-a-client"></a><span data-ttu-id="a9590-137">Debugowanie wyjątków zgłoszonych przez klienta</span><span class="sxs-lookup"><span data-stu-id="a9590-137">Debugging Exceptions Thrown by a Client</span></span>

<span data-ttu-id="a9590-138">Wiele wyjątków zgłoszonych przez klienta WCF jest spowodowanych przez wyjątek w usłudze.</span><span class="sxs-lookup"><span data-stu-id="a9590-138">Many exceptions thrown by a WCF client are caused by an exception on the service.</span></span> <span data-ttu-id="a9590-139">Oto kilka przykładów:</span><span class="sxs-lookup"><span data-stu-id="a9590-139">Some examples of this are:</span></span>

- <span data-ttu-id="a9590-140"><xref:System.Net.Sockets.SocketException>: Istniejące połączenie zostało wymuszone przez hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="a9590-140"><xref:System.Net.Sockets.SocketException>: An existing connection was forcibly closed by the remote host.</span></span>

- <span data-ttu-id="a9590-141"><xref:System.ServiceModel.CommunicationException>: Połączenie bazowe zostało nieoczekiwanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="a9590-141"><xref:System.ServiceModel.CommunicationException>: The underlying connection was closed unexpectedly.</span></span>

- <span data-ttu-id="a9590-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: Połączenie gniazda zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="a9590-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: The socket connection was aborted.</span></span> <span data-ttu-id="a9590-143">Może to być spowodowane błędem przetwarzania komunikatu, przekroczeniem limitu czasu odbierania przez hosta zdalnego lub problemem związanym z zasobami sieciowymi.</span><span class="sxs-lookup"><span data-stu-id="a9590-143">This could be caused by an error processing your message, a receive time-out being exceeded by the remote host, or an underlying network resource issue.</span></span>

<span data-ttu-id="a9590-144">W przypadku wystąpienia tego typu wyjątków najlepszym sposobem rozwiązania problemu jest włączenie śledzenia po stronie usługi i określenie, który wyjątek wystąpił.</span><span class="sxs-lookup"><span data-stu-id="a9590-144">When these types of exceptions occur, the best way to solve the problem is to turn on tracing on the service side and determine what exception occurred there.</span></span> <span data-ttu-id="a9590-145">Aby uzyskać więcej informacji na temat śledzenia, zobacz [śledzenie](../../../docs/framework/wcf/diagnostics/tracing/index.md) i [Używanie śledzenia w celu rozwiązywania problemów z aplikacją](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="a9590-145">For more information about tracing, see [Tracing](../../../docs/framework/wcf/diagnostics/tracing/index.md) and [Using Tracing to Troubleshoot Your Application](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a9590-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a9590-146">See also</span></span>

- [<span data-ttu-id="a9590-147">Instrukcje: Tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="a9590-147">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="a9590-148">Instrukcje: Dostęp do usług za pomocą kontraktu dupleksowego</span><span class="sxs-lookup"><span data-stu-id="a9590-148">How to: Access Services with a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="a9590-149">Instrukcje: Asynchroniczne wywoływanie operacji usługi</span><span class="sxs-lookup"><span data-stu-id="a9590-149">How to: Call Service Operations Asynchronously</span></span>](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [<span data-ttu-id="a9590-150">Instrukcje: Dostęp do usług za pomocą kontraktów jednokierunkowych i odpowiedzi na żądanie</span><span class="sxs-lookup"><span data-stu-id="a9590-150">How to: Access Services with One-Way and Request-Reply Contracts</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [<span data-ttu-id="a9590-151">Instrukcje: Dostęp do usługi WSE 3,0</span><span class="sxs-lookup"><span data-stu-id="a9590-151">How to: Access a WSE 3.0 Service</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [<span data-ttu-id="a9590-152">Opis wygenerowanego kodu klienta</span><span class="sxs-lookup"><span data-stu-id="a9590-152">Understanding Generated Client Code</span></span>](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)
- [<span data-ttu-id="a9590-153">Instrukcje: Zwiększenie czasu uruchamiania aplikacji klienckich WCF przy użyciu elementu XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="a9590-153">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [<span data-ttu-id="a9590-154">Określanie zachowania klienta w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="a9590-154">Specifying Client Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="a9590-155">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="a9590-155">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)
