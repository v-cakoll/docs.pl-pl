---
title: Uzyskiwanie dostępu do usług za pomocą klienta WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clients [WCF], consuming services
ms.assetid: d780af9f-73c5-42db-9e52-077a5e4de7fe
ms.openlocfilehash: 97340f8583ef0900645f6db5c453475e85549c55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620201"
---
# <a name="accessing-services-using-a-wcf-client"></a><span data-ttu-id="9b717-102">Uzyskiwanie dostępu do usług za pomocą klienta WCF</span><span class="sxs-lookup"><span data-stu-id="9b717-102">Accessing Services Using a WCF Client</span></span>

<span data-ttu-id="9b717-103">Po utworzeniu usługi, następnym krokiem jest utworzenie serwer proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="9b717-103">After you create a service, the next step is to create a WCF client proxy.</span></span> <span data-ttu-id="9b717-104">Aplikacja kliencka używa serwera proxy klienta WCF do komunikowania się z usługą.</span><span class="sxs-lookup"><span data-stu-id="9b717-104">A client application uses the WCF client proxy to communicate with the service.</span></span> <span data-ttu-id="9b717-105">Aplikacje klienckie zwykle Importowanie metadanych usługi, aby wygenerować kod klienta WCF, który może służyć do wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="9b717-105">Client applications usually import a service's metadata to generate WCF client code that can be used to invoke the service.</span></span>

 <span data-ttu-id="9b717-106">Następujące podstawowe kroki tworzenia klienta programu WCF:</span><span class="sxs-lookup"><span data-stu-id="9b717-106">The basic steps for creating a WCF client include the following:</span></span>

1.  <span data-ttu-id="9b717-107">Kompilowanie kodu usługi.</span><span class="sxs-lookup"><span data-stu-id="9b717-107">Compile the service code.</span></span>

2.  <span data-ttu-id="9b717-108">Generuj proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="9b717-108">Generate the WCF client proxy.</span></span>

3.  <span data-ttu-id="9b717-109">Tworzy serwer proxy klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="9b717-109">Instantiate the WCF client proxy.</span></span>

<span data-ttu-id="9b717-110">Serwer proxy klienta WCF można wygenerować ręcznie przy użyciu usługi modelu metadanych narzędzie (SvcUtil.exe) Aby uzyskać więcej informacji, zobacz [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9b717-110">The WCF client proxy can be generated manually by using the Service Model Metadata Utility Tool (SvcUtil.exe) for more information see, [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="9b717-111">Serwer proxy klienta WCF, mogą być też generowane w programie Visual Studio przy użyciu **Dodaj odwołanie do usługi** funkcji.</span><span class="sxs-lookup"><span data-stu-id="9b717-111">The WCF client proxy can also be generated within Visual Studio using the **Add Service Reference**  feature.</span></span> <span data-ttu-id="9b717-112">Aby wygenerować serwer proxy klienta WCF, za pomocą jednej z metod usługi musi być uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="9b717-112">To generate the WCF client proxy using either method the service must be running.</span></span> <span data-ttu-id="9b717-113">Jeśli usługa jest samodzielnie hostowana należy uruchomić hosta.</span><span class="sxs-lookup"><span data-stu-id="9b717-113">If the service is self-hosted you must run the host.</span></span> <span data-ttu-id="9b717-114">Jeśli usługa jest hostowana w programie IIS / WAS, nie trzeba nic robić.</span><span class="sxs-lookup"><span data-stu-id="9b717-114">If the service is hosted in IIS/WAS you do not need to do anything else.</span></span>

## <a name="servicemodel-metadata-utility-tool"></a><span data-ttu-id="9b717-115">Narzędzie do obsługi metadanych elementu ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9b717-115">ServiceModel Metadata Utility Tool</span></span>
 <span data-ttu-id="9b717-116">[Narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to narzędzie wiersza polecenia, generowanie kodu na podstawie metadanych.</span><span class="sxs-lookup"><span data-stu-id="9b717-116">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) is a command-line tool for generating code from metadata.</span></span> <span data-ttu-id="9b717-117">Użyj następujących znajduje się przykład podstawowe polecenia Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="9b717-117">The following use is an example of a basic Svcutil.exe command.</span></span>

```
Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
```

 <span data-ttu-id="9b717-118">Alternatywnie można użyć Svcutil.exe plikami Web Services Description Language (WSDL) i schemat XML definicji język (XSD) w systemie plików.</span><span class="sxs-lookup"><span data-stu-id="9b717-118">Alternatively, you can use Svcutil.exe with Web Services Description Language (WSDL) and XML Schema definition language (XSD) files on the file system.</span></span>

```
Svcutil.exe <list of WSDL and XSD files on file system>
```

 <span data-ttu-id="9b717-119">Wynik jest plik kodu, który zawiera kod klienta WCF, używanego przez aplikację klienta do wywołania usługi.</span><span class="sxs-lookup"><span data-stu-id="9b717-119">The result is a code file that contains WCF client code that the client application can use to invoke the service.</span></span>

 <span data-ttu-id="9b717-120">Umożliwia także narzędzie do generowania plików konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="9b717-120">You can also use the tool to generate configuration files.</span></span>

```
Svcutil.exe <file1 [,file2]>
```

 <span data-ttu-id="9b717-121">Jeśli tylko jedną nazwę pliku, który jest nazwa pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="9b717-121">If only one file name is given, that is the name of the output file.</span></span> <span data-ttu-id="9b717-122">Jeśli są podane dwie nazwy pliku, pierwszy plik jest plikiem konfiguracja danych wejściowych, których zawartość jest scalany z wygenerowaną konfigurację i zapisywane w pliku drugie.</span><span class="sxs-lookup"><span data-stu-id="9b717-122">If two file names are given, then the first file is an input configuration file whose contents are merged with the generated configuration and written out into the second file.</span></span> <span data-ttu-id="9b717-123">Aby uzyskać więcej informacji o konfiguracji, zobacz [konfigurowanie powiązań dla usług](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="9b717-123">For more information about configuration, see [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9b717-124">Żądania metadanych niezabezpieczony stanowić zagrożeniom w taki sam sposób, który wykonuje każde żądanie niezabezpieczonej sieci: Jeśli nie masz pewność, że punkt końcowy, które komunikują się z jest tożsamości jest, informacje, które możesz pobrać może być metadanych usługi złośliwego.</span><span class="sxs-lookup"><span data-stu-id="9b717-124">Unsecured metadata requests pose certain risks in the same way that any unsecured network request does: If you are not certain that the endpoint you are communicating with is who it says it is, the information you retrieve might be metadata from a malicious service.</span></span>

## <a name="add-service-reference-in-visual-studio"></a><span data-ttu-id="9b717-125">Dodaj odwołanie do usługi w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9b717-125">Add Service Reference in Visual Studio</span></span>

 <span data-ttu-id="9b717-126">Z uruchomioną usługę, kliknij prawym przyciskiem myszy projekt, który będzie zawierać serwer proxy klienta WCF, a następnie wybrać **Dodaj** > **odwołanie do usługi**.</span><span class="sxs-lookup"><span data-stu-id="9b717-126">With the service running, right click the project that will contain the WCF client proxy and select **Add** > **Service Reference**.</span></span> <span data-ttu-id="9b717-127">W **Dodaj odwołanie okno dialogowe usługi**, wpisz adres URL usługi, aby wywołać, a następnie kliknij przycisk **Przejdź** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9b717-127">In the **Add Service Reference Dialog**, type in the URL to the service you want to call and click the **Go** button.</span></span> <span data-ttu-id="9b717-128">Okno dialogowe wyświetli listę usług, które są dostępne pod adresem, które określisz.</span><span class="sxs-lookup"><span data-stu-id="9b717-128">The dialog will display a list of services available at the address you specify.</span></span> <span data-ttu-id="9b717-129">Kliknij dwukrotnie usługę Zobacz kontrakty i operacje dostępne, określ obszar nazw dla wygenerowanego kodu, a następnie kliknij przycisk **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9b717-129">Double click the service to see the contracts and operations available, specify a namespace for the generated code, and click the **OK** button.</span></span>

## <a name="example"></a><span data-ttu-id="9b717-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="9b717-130">Example</span></span>
 <span data-ttu-id="9b717-131">Poniższy przykład kodu pokazuje kontraktu usługi utworzonych dla usługi.</span><span class="sxs-lookup"><span data-stu-id="9b717-131">The following code example shows a service contract created for a service.</span></span>

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

 <span data-ttu-id="9b717-132">Narzędzie do obsługi metadanych elementu ServiceModel i **Dodaj odwołanie do usługi** w programie Visual Studio generuje następujące klasy klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="9b717-132">The ServiceModel Metadata utility tool and **Add Service Reference** in Visual Studio generates the following WCF client class.</span></span> <span data-ttu-id="9b717-133">Klasa dziedziczy ogólnego <xref:System.ServiceModel.ClientBase%601> klasy i implementuje `ICalculator` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9b717-133">The class inherits from the generic <xref:System.ServiceModel.ClientBase%601> class and implements the `ICalculator` interface.</span></span> <span data-ttu-id="9b717-134">Narzędzie generuje również `ICalculator` interfejsu (nie pokazane tutaj).</span><span class="sxs-lookup"><span data-stu-id="9b717-134">The tool also generates the `ICalculator` interface (not shown here).</span></span>

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

## <a name="using-the-wcf-client"></a><span data-ttu-id="9b717-135">Za pomocą klienta WCF</span><span class="sxs-lookup"><span data-stu-id="9b717-135">Using the WCF Client</span></span>
 <span data-ttu-id="9b717-136">Aby używać klienta platformy WCF, Utwórz wystąpienie obiektu klienta WCF, a następnie wywołać jego metody, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="9b717-136">To use the WCF client, create an instance of the WCF client, and then call its methods, as shown in the following code.</span></span>

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

## <a name="debugging-exceptions-thrown-by-a-client"></a><span data-ttu-id="9b717-137">Debugowanie wyjątków zgłaszanych przez klientów</span><span class="sxs-lookup"><span data-stu-id="9b717-137">Debugging Exceptions Thrown by a Client</span></span>

<span data-ttu-id="9b717-138">Wiele wyjątków wygenerowanych przez klienta programu WCF są spowodowane przez wyjątek w usłudze.</span><span class="sxs-lookup"><span data-stu-id="9b717-138">Many exceptions thrown by a WCF client are caused by an exception on the service.</span></span> <span data-ttu-id="9b717-139">Przedstawiono kilka przykładów:</span><span class="sxs-lookup"><span data-stu-id="9b717-139">Some examples of this are:</span></span>

-   <span data-ttu-id="9b717-140"><xref:System.Net.Sockets.SocketException>: Istniejące połączenie zostało zamknięte przez hosta zdalnego.</span><span class="sxs-lookup"><span data-stu-id="9b717-140"><xref:System.Net.Sockets.SocketException>: An existing connection was forcibly closed by the remote host.</span></span>

-   <span data-ttu-id="9b717-141"><xref:System.ServiceModel.CommunicationException>: Połączenie podstawowe zostało nieoczekiwanie zamknięte.</span><span class="sxs-lookup"><span data-stu-id="9b717-141"><xref:System.ServiceModel.CommunicationException>: The underlying connection was closed unexpectedly.</span></span>

-   <span data-ttu-id="9b717-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: Połączenie gniazda zostało przerwane.</span><span class="sxs-lookup"><span data-stu-id="9b717-142"><xref:System.ServiceModel.CommunicationObjectAbortedException>: The socket connection was aborted.</span></span> <span data-ttu-id="9b717-143">Może to być spowodowane błędnym przetwarzaniem komunikatu, limit czasu odbioru przekroczenia przez hosta zdalnego lub podstawowym problemem z zasobami sieciowymi.</span><span class="sxs-lookup"><span data-stu-id="9b717-143">This could be caused by an error processing your message, a receive time-out being exceeded by the remote host, or an underlying network resource issue.</span></span>

<span data-ttu-id="9b717-144">Po wystąpieniu tego rodzaju wyjątków, najlepszym sposobem rozwiązania tego problemu jest włączone jest śledzenie po stronie usługi i określić, jakie wyjątek wystąpił brak.</span><span class="sxs-lookup"><span data-stu-id="9b717-144">When these types of exceptions occur, the best way to solve the problem is to turn on tracing on the service side and determine what exception occurred there.</span></span> <span data-ttu-id="9b717-145">Aby uzyskać więcej informacji na temat śledzenia, zobacz [śledzenia](../../../docs/framework/wcf/diagnostics/tracing/index.md) i [przy użyciu śledzenia do Rozwiązywanie problemów aplikacji](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span><span class="sxs-lookup"><span data-stu-id="9b717-145">For more information about tracing, see [Tracing](../../../docs/framework/wcf/diagnostics/tracing/index.md) and [Using Tracing to Troubleshoot Your Application](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9b717-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9b717-146">See also</span></span>

- [<span data-ttu-id="9b717-147">Instrukcje: Tworzenie klienta</span><span class="sxs-lookup"><span data-stu-id="9b717-147">How to: Create a Client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [<span data-ttu-id="9b717-148">Instrukcje: Dostęp do usług za pomocą kontraktu dwukierunkowego</span><span class="sxs-lookup"><span data-stu-id="9b717-148">How to: Access Services with a Duplex Contract</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [<span data-ttu-id="9b717-149">Instrukcje: Asynchroniczne wywoływanie operacji usługi</span><span class="sxs-lookup"><span data-stu-id="9b717-149">How to: Call Service Operations Asynchronously</span></span>](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [<span data-ttu-id="9b717-150">Instrukcje: Uzyskiwanie dostępu do usług za pomocą jednokierunkowego i kontraktów "żądanie odpowiedź"</span><span class="sxs-lookup"><span data-stu-id="9b717-150">How to: Access Services with One-Way and Request-Reply Contracts</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [<span data-ttu-id="9b717-151">Instrukcje: Dostęp do programu WSE 3.0 usługi</span><span class="sxs-lookup"><span data-stu-id="9b717-151">How to: Access a WSE 3.0 Service</span></span>](../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [<span data-ttu-id="9b717-152">Opis wygenerowanego kodu klienta</span><span class="sxs-lookup"><span data-stu-id="9b717-152">Understanding Generated Client Code</span></span>](../../../docs/framework/wcf/feature-details/understanding-generated-client-code.md)
- [<span data-ttu-id="9b717-153">Instrukcje: Poprawę czasu uruchamiania programu WCF klienta aplikacji przy użyciu elementu XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="9b717-153">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
- [<span data-ttu-id="9b717-154">Określanie zachowania klienta w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="9b717-154">Specifying Client Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="9b717-155">Konfigurowanie zachowań klienta</span><span class="sxs-lookup"><span data-stu-id="9b717-155">Configuring Client Behaviors</span></span>](../../../docs/framework/wcf/configuring-client-behaviors.md)
