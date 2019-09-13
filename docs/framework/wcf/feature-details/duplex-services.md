---
title: Usługi dwukierunkowe
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: f9e563cb87ee376e33442cdf718f70202d300f40
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895169"
---
# <a name="duplex-services"></a><span data-ttu-id="89dd8-102">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="89dd8-102">Duplex Services</span></span>

<span data-ttu-id="89dd8-103">Kontrakt usługi dupleksowej jest wzorcem wymiany komunikatów, w którym oba punkty końcowe mogą wysyłać wiadomości osobno do siebie.</span><span class="sxs-lookup"><span data-stu-id="89dd8-103">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="89dd8-104">Usługa dupleksowa, dlatego może wysyłać komunikaty z powrotem do punktu końcowego klienta, zapewniając zachowanie podobne do zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="89dd8-104">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="89dd8-105">Komunikacja dupleksowa występuje, gdy klient nawiązuje połączenie z usługą i udostępnia usługę za pomocą kanału, w którym usługa może wysyłać komunikaty z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="89dd8-105">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="89dd8-106">Należy zauważyć, że zachowanie usługi dupleksowej działa wyłącznie w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="89dd8-106">Note that the event-like behavior of duplex services only works within a session.</span></span>

<span data-ttu-id="89dd8-107">Aby utworzyć umowę dupleksową, utworzysz parę interfejsów.</span><span class="sxs-lookup"><span data-stu-id="89dd8-107">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="89dd8-108">Pierwszy to interfejs kontraktu usługi, który opisuje operacje, które mogą być wywoływane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="89dd8-108">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="89dd8-109">Ten kontrakt usługi musi określać *kontrakt wywołania zwrotnego* we <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="89dd8-109">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="89dd8-110">Kontrakt wywołania zwrotnego jest interfejsem, który definiuje operacje, które usługa może wywołać w punkcie końcowym klienta.</span><span class="sxs-lookup"><span data-stu-id="89dd8-110">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="89dd8-111">Kontrakt dupleksowy nie wymaga sesji, mimo że powiązania dupleksowe dostępne w systemie korzystają z nich.</span><span class="sxs-lookup"><span data-stu-id="89dd8-111">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>

<span data-ttu-id="89dd8-112">Poniżej znajduje się przykład kontraktu dupleksowego.</span><span class="sxs-lookup"><span data-stu-id="89dd8-112">The following is an example of a duplex contract.</span></span>

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

<span data-ttu-id="89dd8-113">Klasa implementuje interfejs podstawowy `ICalculatorDuplex`. `CalculatorService`</span><span class="sxs-lookup"><span data-stu-id="89dd8-113">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="89dd8-114">Usługa używa trybu wystąpienia <xref:System.ServiceModel.InstanceContextMode.PerSession> , aby zachować wynik dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="89dd8-114">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="89dd8-115">Właściwość prywatna o `Callback` nazwie uzyskuje dostęp do kanału wywołania zwrotnego do klienta.</span><span class="sxs-lookup"><span data-stu-id="89dd8-115">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="89dd8-116">Usługa używa wywołania zwrotnego do wysyłania komunikatów z powrotem do klienta za pośrednictwem interfejsu wywołania zwrotnego, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="89dd8-116">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

<span data-ttu-id="89dd8-117">Klient musi dostarczyć klasę, która implementuje interfejs wywołania zwrotnego kontraktu dupleksowego na potrzeby otrzymywania komunikatów z usługi.</span><span class="sxs-lookup"><span data-stu-id="89dd8-117">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="89dd8-118">Poniższy przykładowy kod przedstawia `CallbackHandler` klasę, która `ICalculatorDuplexCallback` implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="89dd8-118">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

<span data-ttu-id="89dd8-119">Klient WCF wygenerowany dla kontraktu dupleksowego wymaga, <xref:System.ServiceModel.InstanceContext> aby Klasa była dostarczana podczas konstruowania.</span><span class="sxs-lookup"><span data-stu-id="89dd8-119">The WCF client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="89dd8-120">Ta <xref:System.ServiceModel.InstanceContext> Klasa jest używana jako lokacja dla obiektu, który implementuje interfejs wywołania zwrotnego i obsługuje komunikaty wysyłane z powrotem z usługi.</span><span class="sxs-lookup"><span data-stu-id="89dd8-120">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="89dd8-121">Klasa jest zbudowana z wystąpieniem `CallbackHandler` klasy. <xref:System.ServiceModel.InstanceContext></span><span class="sxs-lookup"><span data-stu-id="89dd8-121">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="89dd8-122">Ten obiekt obsługuje komunikaty wysyłane z usługi do klienta w interfejsie wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="89dd8-122">This object handles messages sent from the service to the client on the callback interface.</span></span>

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

<span data-ttu-id="89dd8-123">Konfiguracja usługi musi być skonfigurowana w taki sposób, aby zapewnić powiązanie obsługujące komunikację między sesjami i dupleks.</span><span class="sxs-lookup"><span data-stu-id="89dd8-123">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="89dd8-124">`wsDualHttpBinding` Element obsługuje komunikację z sesją i umożliwia komunikację dwukierunkową przez dostarczanie podwójnych połączeń HTTP, po jednym dla każdego kierunku.</span><span class="sxs-lookup"><span data-stu-id="89dd8-124">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>

<span data-ttu-id="89dd8-125">Na kliencie należy skonfigurować adres używany przez serwer do łączenia się z klientem, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="89dd8-125">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="89dd8-126">Klienci niebędący w trybie dupleksu, którzy nie mogą uwierzytelnić się <xref:System.ServiceModel.Security.MessageSecurityException>przy użyciu bezpiecznej konwersacji zwykle generują.</span><span class="sxs-lookup"><span data-stu-id="89dd8-126">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="89dd8-127">Jednak jeśli uwierzytelnienie klienta dupleksowego używającego bezpiecznej konwersacji nie powiedzie się, klient otrzyma <xref:System.TimeoutException> zamiast.</span><span class="sxs-lookup"><span data-stu-id="89dd8-127">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>

<span data-ttu-id="89dd8-128">Jeśli utworzysz klienta/usługę za pomocą `WSHttpBinding` elementu, a punkt końcowy wywołania zwrotnego klienta nie zostanie uwzględniony, zostanie wyświetlony następujący błąd.</span><span class="sxs-lookup"><span data-stu-id="89dd8-128">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>

```console
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

<span data-ttu-id="89dd8-129">Poniższy przykładowy kod przedstawia sposób programowego określania adresu punktu końcowego klienta.</span><span class="sxs-lookup"><span data-stu-id="89dd8-129">The following sample code shows how to specify the client endpoint address programmatically.</span></span>

```csharp
WSDualHttpBinding binding = new WSDualHttpBinding();
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");
```

```vb
Dim binding As New WSDualHttpBinding()
Dim endptadr As New EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server")
binding.ClientBaseAddress = New Uri("http://localhost:8000/DuplexTestUsingCode/Client/")
```

<span data-ttu-id="89dd8-130">Poniższy przykładowy kod pokazuje, jak określić adres punktu końcowego klienta w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="89dd8-130">The following sample code shows how to specify the client endpoint address in configuration.</span></span>

```xml
<client>
    <endpoint name ="ServerEndpoint"
          address="http://localhost:12000/DuplexTestUsingConfig/Server"
          bindingConfiguration="WSDualHttpBinding_IDuplexTest"
            binding="wsDualHttpBinding"
           contract="IDuplexTest" />
</client>
<bindings>
    <wsDualHttpBinding>
        <binding name="WSDualHttpBinding_IDuplexTest"
          clientBaseAddress="http://localhost:8000/myClient/" >
            <security mode="None"/>
         </binding>
    </wsDualHttpBinding>
</bindings>
```

> [!WARNING]
> <span data-ttu-id="89dd8-131">Model dupleksu nie wykrywa automatycznie, gdy usługa lub klient zamknie kanał.</span><span class="sxs-lookup"><span data-stu-id="89dd8-131">The duplex model doesn't automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="89dd8-132">Jeśli więc klient nieoczekiwanie zakończy działanie, domyślnie usługa nie zostanie powiadomiona lub jeśli usługa nieoczekiwanie zakończy działanie, klient nie zostanie powiadomiony.</span><span class="sxs-lookup"><span data-stu-id="89dd8-132">So if a client unexpectedly terminates, by default the service will not be notified, or if a service unexpectedly terminates, the client will not be notified.</span></span> <span data-ttu-id="89dd8-133">Jeśli używasz usługi, która jest odłączona, <xref:System.ServiceModel.CommunicationException> wyjątek jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="89dd8-133">If you use a service that is disconnected, the <xref:System.ServiceModel.CommunicationException> exception is raised.</span></span> <span data-ttu-id="89dd8-134">Klienci i usługi mogą wdrożyć własny protokół, aby powiadomić siebie nawzajem o takim wyborze.</span><span class="sxs-lookup"><span data-stu-id="89dd8-134">Clients and services can implement their own protocol to notify each other if they so choose.</span></span> <span data-ttu-id="89dd8-135">Aby uzyskać więcej informacji na temat obsługi błędów, zobacz [Obsługa błędów WCF](../wcf-error-handling.md)</span><span class="sxs-lookup"><span data-stu-id="89dd8-135">For more information on error handling, see [WCF Error Handling](../wcf-error-handling.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="89dd8-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89dd8-136">See also</span></span>

- [<span data-ttu-id="89dd8-137">Dupleks</span><span class="sxs-lookup"><span data-stu-id="89dd8-137">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="89dd8-138">Określanie zachowania klienta w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="89dd8-138">Specifying Client Run-Time Behavior</span></span>](../specifying-client-run-time-behavior.md)
- [<span data-ttu-id="89dd8-139">Instrukcje: Tworzenie fabryki kanałów i używanie jej do tworzenia kanałów i zarządzania nimi</span><span class="sxs-lookup"><span data-stu-id="89dd8-139">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
