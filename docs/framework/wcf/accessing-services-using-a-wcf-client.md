---
title: Uzyskiwanie dostępu do usług za pomocą klienta WCF
description: Dowiedz się, jak utworzyć serwer proxy klienta WCF dla usługi WCF. Aplikacja kliencka komunikuje się z usługą za pomocą serwera proxy klienta.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 25446a89a0b5657d32d77e2d0d57f58f36bed71b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245547"
---
# <a name="accessing-services-using-a-wcf-client"></a><span data-ttu-id="29780-104">Uzyskiwanie dostępu do usług za pomocą klienta WCF</span><span class="sxs-lookup"><span data-stu-id="29780-104">Accessing Services Using a WCF Client</span></span>

<span data-ttu-id="29780-105">Następnym krokiem po utworzeniu usługi jest utworzenie serwera proxy klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="29780-105">After you create a service, the next step is to create a WCF client proxy.</span></span> <span data-ttu-id="29780-106">Aplikacja kliencka używa serwera proxy klienta WCF do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="29780-106">A client application uses the WCF client proxy to communicate with the service.</span></span> <span data-ttu-id="29780-107">Aplikacje klienckie zazwyczaj importują metadane usługi w celu wygenerowania kodu klienta WCF, którego można użyć do wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="29780-107">Client applications usually import a service's metadata to generate WCF client code that can be used to invoke the service.</span></span>

 <span data-ttu-id="29780-108">Podstawowe kroki tworzenia klienta WCF są następujące:</span><span class="sxs-lookup"><span data-stu-id="29780-108">The basic steps for creating a WCF client include the following:</span></span>

1. <span data-ttu-id="29780-109">Skompiluj kod usługi.</span><span class="sxs-lookup"><span data-stu-id="29780-109">Compile the service code.</span></span>

2. <span data-ttu-id="29780-110">Generuj serwer proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="29780-110">Generate the WCF client proxy.</span></span>

3. <span data-ttu-id="29780-111">Tworzenie wystąpienia serwera proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="29780-111">Instantiate the WCF client proxy.</span></span>

<span data-ttu-id="29780-112">Serwer proxy klienta WCF można wygenerować ręcznie przy użyciu narzędzia metadanych modelu usługi (SvcUtil.exe), aby uzyskać więcej informacji, zobacz [Narzędzie narzędzia metadanych ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="29780-112">The WCF client proxy can be generated manually by using the Service Model Metadata Utility Tool (SvcUtil.exe) for more information see, [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="29780-113">Serwer proxy klienta WCF można również wygenerować w programie Visual Studio przy użyciu funkcji **Dodaj odwołanie do usługi** .</span><span class="sxs-lookup"><span data-stu-id="29780-113">The WCF client proxy can also be generated within Visual Studio using the **Add Service Reference**  feature.</span></span> <span data-ttu-id="29780-114">Aby wygenerować serwer proxy klienta WCF przy użyciu dowolnej metody, musi być uruchomiona usługa.</span><span class="sxs-lookup"><span data-stu-id="29780-114">To generate the WCF client proxy using either method the service must be running.</span></span> <span data-ttu-id="29780-115">Jeśli usługa jest samoobsługowa, należy uruchomić hosta.</span><span class="sxs-lookup"><span data-stu-id="29780-115">If the service is self-hosted you must run the host.</span></span> <span data-ttu-id="29780-116">Jeśli usługa jest hostowana w programie IIS/nie trzeba wykonywać żadnych innych czynności.</span><span class="sxs-lookup"><span data-stu-id="29780-116">If the service is hosted in IIS/WAS you do not need to do anything else.</span></span>

## <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="29780-117">Narzędzie do przesyłania metadanych ServiceModel</span><span class="sxs-lookup"><span data-stu-id="29780-117">ServiceModel Metadata Utility Tool</span></span>
 <span data-ttu-id="29780-118">[Narzędzie do przesyłania metadanych modelu ServiceModel (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) jest narzędziem wiersza polecenia do generowania kodu z metadanych.</span><span class="sxs-lookup"><span data-stu-id="29780-118">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) is a command-line tool for generating code from metadata.</span></span> <span data-ttu-id="29780-119">Poniżej przedstawiono przykład polecenia Basic Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="29780-119">The following use is an example of a basic Svcutil.exe command.</span></span>

```console
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 <span data-ttu-id="29780-120">Alternatywnie, można użyć Svcutil.exe z Web Services Description Language (WSDL) i plików języka definicji schematu XML (XSD) w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="29780-120">Alternatively, you can use Svcutil.exe with Web Services Description Language (WSDL) and XML Schema definition language (XSD) files on the file system.</span></span>

```console
Svcutil.exe <list of WSDL and XSD files on file system>
```

 <span data-ttu-id="29780-121">Wynikiem jest plik kodu, który zawiera kod klienta WCF, którego aplikacja kliencka może użyć do wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="29780-121">The result is a code file that contains WCF client code that the client application can use to invoke the service.</span></span>

 <span data-ttu-id="29780-122">Możesz również użyć narzędzia do generowania plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="29780-122">You can also use the tool to generate configuration files.</span></span>

```console
Svcutil.exe <file1 [,file2]>
```

 <span data-ttu-id="29780-123">Jeśli podano tylko jedną nazwę pliku, która jest nazwą pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="29780-123">If only one file name is given, that is the name of the output file.</span></span> <span data-ttu-id="29780-124">Jeśli podano dwie nazwy plików, pierwszy plik jest plikiem konfiguracji wejściowej, którego zawartość jest scalana z wygenerowaną konfiguracją i zapisywana w drugim pliku.</span><span class="sxs-lookup"><span data-stu-id="29780-124">If two file names are given, then the first file is an input configuration file whose contents are merged with the generated configuration and written out into the second file.</span></span> <span data-ttu-id="29780-125">Aby uzyskać więcej informacji na temat konfiguracji, zobacz [Konfigurowanie powiązań dla usług](configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="29780-125">For more information about configuration, see [Configuring Bindings for Services](configuring-bindings-for-wcf-services.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29780-126">Niezabezpieczone żądania metadanych stanowią pewne zagrożenia w taki sam sposób, w jaki wszystkie niezabezpieczone żądania sieciowe: Jeśli nie masz pewności, że punkt końcowy, z którym nawiązujesz połączenie, jest to, że informacje pobierane mogą być metadanymi ze złośliwej usługi.</span><span class="sxs-lookup"><span data-stu-id="29780-126">Unsecured metadata requests pose certain risks in the same way that any unsecured network request does: If you are not certain that the endpoint you are communicating with is who it says it is, the information you retrieve might be metadata from a malicious service.</span></span>

## <a name="add-service-reference-in-visual-studio"></a><span data-ttu-id="29780-127">Dodaj odwołanie do usługi w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="29780-127">Add Service Reference in Visual Studio</span></span>

 <span data-ttu-id="29780-128">Po uruchomieniu usługi kliknij prawym przyciskiem myszy projekt, który będzie zawierać serwer proxy klienta WCF i wybierz polecenie **Dodaj**  >  **odwołanie do usługi**.</span><span class="sxs-lookup"><span data-stu-id="29780-128">With the service running, right click the project that will contain the WCF client proxy and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="29780-129">W **oknie dialogowym Dodaj odwołanie do usługi**wpisz adres URL usługi, którą chcesz wywołać, a następnie kliknij przycisk **Przejdź** .</span><span class="sxs-lookup"><span data-stu-id="29780-129">In the **Add Service Reference Dialog**, type in the URL to the service you want to call and click the **Go** button.</span></span> <span data-ttu-id="29780-130">W oknie dialogowym zostanie wyświetlona lista usług dostępnych pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="29780-130">The dialog will display a list of services available at the address you specify.</span></span> <span data-ttu-id="29780-131">Kliknij dwukrotnie usługę, aby wyświetlić dostępne kontrakty i operacje, określ przestrzeń nazw dla wygenerowanego kodu, a następnie kliknij przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="29780-131">Double click the service to see the contracts and operations available, specify a namespace for the generated code, and click the **OK** button.</span></span>

## <a name="example"></a><span data-ttu-id="29780-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="29780-132">Example</span></span>
 <span data-ttu-id="29780-133">Poniższy przykład kodu przedstawia kontrakt usługi utworzony dla usługi.</span><span class="sxs-lookup"><span data-stu-id="29780-133">The following code example shows a service contract created for a service.</span></span>

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

 <span data-ttu-id="29780-134">Narzędzie do przesyłania metadanych ServiceModel i **Dodaj odwołanie do usługi** w programie Visual Studio generuje następujące klasy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="29780-134">The ServiceModel Metadata utility tool and **Add Service Reference** in Visual Studio generates the following WCF client class.</span></span> <span data-ttu-id="29780-135">Klasa dziedziczy z klasy generycznej <xref:System.ServiceModel.ClientBase%601> i implementuje `ICalculator` interfejs.</span><span class="sxs-lookup"><span data-stu-id="29780-135">The class inherits from the generic <xref:System.ServiceModel.ClientBase%601> class and implements the `ICalculator` interface.</span></span> <span data-ttu-id="29780-136">Narzędzie generuje również `ICalculator` interfejs (nie pokazano tutaj).</span><span class="sxs-lookup"><span data-stu-id="29780-136">The tool also generates the `ICalculator` interface (not shown here).</span></span>

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

## <a name="using-the-wcf-client"></a><span data-ttu-id="29780-137">Korzystanie z klienta WCF</span><span class="sxs-lookup"><span data-stu-id="29780-137">Using the WCF Client</span></span>
 <span data-ttu-id="29780-138">Aby użyć klienta WCF, Utwórz wystąpienie klienta WCF, a następnie Wywołaj jego metody, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="29780-138">To use the WCF client, create an instance of the WCF client, and then call its methods, as shown in the following code.</span></span>

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

## <a name="debugging-exceptions-thrown-by-a-client"></a><span data-ttu-id="29780-139">Debugowanie wyjątków zgłoszonych przez klienta</span><span class="sxs-lookup"><span data-stu-id="29780-139">Debugging Exceptions Thrown by a Client</span></span>

<span data-ttu-id="29780-140">Wiele wyjątków zgłoszonych przez klienta WCF jest spowodowanych przez wyjątek w usłudze.</span><span class="sxs-lookup"><span data-stu-id="29780-140">Many exceptions thrown by a WCF client are caused by an exception on the service.</span></span> <span data-ttu-id="29780-141">Oto kilka przykładów:</span><span class="sxs-lookup"><span data-stu-id="29780-141">Some examples of this are:</span></span>

- <span data-ttu-id="29780-142"><xref:System.Net.Sockets.SocketException>: Wykryto, że istniejące połączenie zostało wymuszone przez hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="29780-142"><xref:System.Net.Sockets.SocketException>: An existing connection was forcibly closed by the remote host.</span></span>

- <span data-ttu-id="29780-143"><xref:System.ServiceModel.CommunicationException>: Połączenie bazowe zostało nieoczekiwanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="29780-143"><xref:System.ServiceModel.CommunicationException>: The underlying connection was closed unexpectedly.</span></span>

- <span data-ttu-id="29780-144"><xref:System.ServiceModel.CommunicationObjectAbortedException>: Połączenie gniazda zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="29780-144"><xref:System.ServiceModel.CommunicationObjectAbortedException>: The socket connection was aborted.</span></span> <span data-ttu-id="29780-145">Może to być spowodowane błędem przetwarzania komunikatu, przekroczeniem limitu czasu odbierania przez hosta zdalnego lub problemem związanym z zasobami sieciowymi.</span><span class="sxs-lookup"><span data-stu-id="29780-145">This could be caused by an error processing your message, a receive time-out being exceeded by the remote host, or an underlying network resource issue.</span></span>

<span data-ttu-id="29780-146">W przypadku wystąpienia tego typu wyjątków najlepszym sposobem rozwiązania problemu jest włączenie śledzenia po stronie usługi i określenie, który wyjątek wystąpił.</span><span class="sxs-lookup"><span data-stu-id="29780-146">When these types of exceptions occur, the best way to solve the problem is to turn on tracing on the service side and determine what exception occurred there.</span></span> <span data-ttu-id="29780-147">Aby uzyskać więcej informacji na temat śledzenia, zobacz [śledzenie](./diagnostics/tracing/index.md) i [Używanie śledzenia w celu rozwiązywania problemów z aplikacją](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="29780-147">For more information about tracing, see [Tracing](./diagnostics/tracing/index.md) and [Using Tracing to Troubleshoot Your Application](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="29780-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29780-148">See also</span></span>

- [<span data-ttu-id="29780-149">Instrukcje: tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="29780-149">How to: Create a Client</span></span>](how-to-create-a-wcf-client.md)
- [<span data-ttu-id="29780-150">Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="29780-150">How to: Access Services with a Duplex Contract</span></span>](./feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="29780-151">Instrukcje: Asynchroniczne wywoływanie operacji usługi</span><span class="sxs-lookup"><span data-stu-id="29780-151">How to: Call Service Operations Asynchronously</span></span>](./feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [<span data-ttu-id="29780-152">Instrukcje: uzyskiwanie dostępu do usług za pomocą kontraktów jednokierunkowych i kontraktów „żądanie-odpowiedź”</span><span class="sxs-lookup"><span data-stu-id="29780-152">How to: Access Services with One-Way and Request-Reply Contracts</span></span>](./feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [<span data-ttu-id="29780-153">Instrukcje: dostęp do usługi WSE 3.0</span><span class="sxs-lookup"><span data-stu-id="29780-153">How to: Access a WSE 3.0 Service</span></span>](./feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [<span data-ttu-id="29780-154">Opis wygenerowanego kodu klienta</span><span class="sxs-lookup"><span data-stu-id="29780-154">Understanding Generated Client Code</span></span>](./feature-details/understanding-generated-client-code.md)
- [<span data-ttu-id="29780-155">Instrukcje: skracanie czasu uruchamiania aplikacji klienckich programu WCF za pomocą elementu XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="29780-155">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [<span data-ttu-id="29780-156">Określanie zachowania klienta w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="29780-156">Specifying Client Run-Time Behavior</span></span>](specifying-client-run-time-behavior.md)
- [<span data-ttu-id="29780-157">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="29780-157">Configuring Client Behaviors</span></span>](configuring-client-behaviors.md)
