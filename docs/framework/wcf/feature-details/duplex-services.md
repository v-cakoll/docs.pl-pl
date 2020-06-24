---
title: Usługi dwukierunkowe
description: Dowiedz się, jak utworzyć kontrakt usługi dupleksowej w programie WCF, który umożliwia obu punktom końcowym wysyłanie komunikatów do siebie za pośrednictwem kanału utworzonego przez klienta.
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: a43bb63a0ccf1a34b79dce755c19f7ed4cb6c16c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247354"
---
# <a name="duplex-services"></a><span data-ttu-id="74296-103">Usługi dwukierunkowe</span><span class="sxs-lookup"><span data-stu-id="74296-103">Duplex Services</span></span>

<span data-ttu-id="74296-104">Kontrakt usługi dupleksowej jest wzorcem wymiany komunikatów, w którym oba punkty końcowe mogą wysyłać wiadomości osobno do siebie.</span><span class="sxs-lookup"><span data-stu-id="74296-104">A duplex service contract is a message exchange pattern in which both endpoints can send messages to the other independently.</span></span> <span data-ttu-id="74296-105">Usługa dupleksowa, dlatego może wysyłać komunikaty z powrotem do punktu końcowego klienta, zapewniając zachowanie podobne do zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="74296-105">A duplex service, therefore, can send messages back to the client endpoint, providing event-like behavior.</span></span> <span data-ttu-id="74296-106">Komunikacja dupleksowa występuje, gdy klient nawiązuje połączenie z usługą i udostępnia usługę za pomocą kanału, w którym usługa może wysyłać komunikaty z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="74296-106">Duplex communication occurs when a client connects to a service and provides the service with a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="74296-107">Należy zauważyć, że zachowanie usługi dupleksowej działa wyłącznie w ramach sesji.</span><span class="sxs-lookup"><span data-stu-id="74296-107">Note that the event-like behavior of duplex services only works within a session.</span></span>

<span data-ttu-id="74296-108">Aby utworzyć umowę dupleksową, utworzysz parę interfejsów.</span><span class="sxs-lookup"><span data-stu-id="74296-108">To create a duplex contract you create a pair of interfaces.</span></span> <span data-ttu-id="74296-109">Pierwszy to interfejs kontraktu usługi, który opisuje operacje, które mogą być wywoływane przez klienta.</span><span class="sxs-lookup"><span data-stu-id="74296-109">The first is the service contract interface that describes the operations that a client can invoke.</span></span> <span data-ttu-id="74296-110">Ten kontrakt usługi musi określać *kontrakt wywołania zwrotnego* we <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="74296-110">That service contract must specify a *callback contract* in the <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="74296-111">Kontrakt wywołania zwrotnego jest interfejsem, który definiuje operacje, które usługa może wywołać w punkcie końcowym klienta.</span><span class="sxs-lookup"><span data-stu-id="74296-111">The callback contract is the interface that defines the operations that the service can call on the client endpoint.</span></span> <span data-ttu-id="74296-112">Kontrakt dupleksowy nie wymaga sesji, mimo że powiązania dupleksowe dostępne w systemie korzystają z nich.</span><span class="sxs-lookup"><span data-stu-id="74296-112">A duplex contract does not require a session, although the system-provided duplex bindings make use of them.</span></span>

<span data-ttu-id="74296-113">Poniżej znajduje się przykład kontraktu dupleksowego.</span><span class="sxs-lookup"><span data-stu-id="74296-113">The following is an example of a duplex contract.</span></span>

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

<span data-ttu-id="74296-114">`CalculatorService`Klasa implementuje `ICalculatorDuplex` interfejs podstawowy.</span><span class="sxs-lookup"><span data-stu-id="74296-114">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="74296-115">Usługa używa <xref:System.ServiceModel.InstanceContextMode.PerSession> trybu wystąpienia, aby zachować wynik dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="74296-115">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="74296-116">Właściwość prywatna o nazwie `Callback` uzyskuje dostęp do kanału wywołania zwrotnego do klienta.</span><span class="sxs-lookup"><span data-stu-id="74296-116">A private property named `Callback` accesses the callback channel to the client.</span></span> <span data-ttu-id="74296-117">Usługa używa wywołania zwrotnego do wysyłania komunikatów z powrotem do klienta za pośrednictwem interfejsu wywołania zwrotnego, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="74296-117">The service uses the callback for sending messages back to the client through the callback interface, as shown in the following sample code.</span></span>

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

<span data-ttu-id="74296-118">Klient musi dostarczyć klasę, która implementuje interfejs wywołania zwrotnego kontraktu dupleksowego na potrzeby otrzymywania komunikatów z usługi.</span><span class="sxs-lookup"><span data-stu-id="74296-118">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="74296-119">Poniższy przykładowy kod przedstawia `CallbackHandler` klasę, która implementuje `ICalculatorDuplexCallback` interfejs.</span><span class="sxs-lookup"><span data-stu-id="74296-119">The following sample code shows a `CallbackHandler` class that implements the `ICalculatorDuplexCallback` interface.</span></span>

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

<span data-ttu-id="74296-120">Klient WCF wygenerowany dla kontraktu dupleksowego wymaga, <xref:System.ServiceModel.InstanceContext> Aby Klasa była dostarczana podczas konstruowania.</span><span class="sxs-lookup"><span data-stu-id="74296-120">The WCF client that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> class to be provided upon construction.</span></span> <span data-ttu-id="74296-121">Ta <xref:System.ServiceModel.InstanceContext> Klasa jest używana jako lokacja dla obiektu, który implementuje interfejs wywołania zwrotnego i obsługuje komunikaty wysyłane z powrotem z usługi.</span><span class="sxs-lookup"><span data-stu-id="74296-121">This <xref:System.ServiceModel.InstanceContext> class is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="74296-122"><xref:System.ServiceModel.InstanceContext>Klasa jest zbudowana z wystąpieniem `CallbackHandler` klasy.</span><span class="sxs-lookup"><span data-stu-id="74296-122">An <xref:System.ServiceModel.InstanceContext> class is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="74296-123">Ten obiekt obsługuje komunikaty wysyłane z usługi do klienta w interfejsie wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="74296-123">This object handles messages sent from the service to the client on the callback interface.</span></span>

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

<span data-ttu-id="74296-124">Konfiguracja usługi musi być skonfigurowana w taki sposób, aby zapewnić powiązanie obsługujące komunikację między sesjami i dupleks.</span><span class="sxs-lookup"><span data-stu-id="74296-124">The configuration for the service must be set up to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="74296-125">`wsDualHttpBinding`Element obsługuje komunikację z sesją i umożliwia komunikację dwukierunkową przez dostarczanie podwójnych połączeń HTTP, po jednym dla każdego kierunku.</span><span class="sxs-lookup"><span data-stu-id="74296-125">The `wsDualHttpBinding` element supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span>

<span data-ttu-id="74296-126">Na kliencie należy skonfigurować adres używany przez serwer do łączenia się z klientem, jak pokazano w poniższej konfiguracji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="74296-126">On the client, you must configure an address that the server can use to connect to the client, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="74296-127">Klienci niebędący w trybie dupleksu, którzy nie mogą uwierzytelnić się przy użyciu bezpiecznej konwersacji zwykle generują <xref:System.ServiceModel.Security.MessageSecurityException> .</span><span class="sxs-lookup"><span data-stu-id="74296-127">Non-duplex clients that fail to authenticate using a secure conversation typically throw a <xref:System.ServiceModel.Security.MessageSecurityException>.</span></span> <span data-ttu-id="74296-128">Jednak jeśli uwierzytelnienie klienta dupleksowego używającego bezpiecznej konwersacji nie powiedzie się, klient otrzyma <xref:System.TimeoutException> zamiast.</span><span class="sxs-lookup"><span data-stu-id="74296-128">However, if a duplex client that uses a secure conversation fails to authenticate, the client receives a <xref:System.TimeoutException> instead.</span></span>

<span data-ttu-id="74296-129">Jeśli utworzysz klienta/usługę za pomocą elementu, `WSHttpBinding` a punkt końcowy wywołania zwrotnego klienta nie zostanie uwzględniony, zostanie wyświetlony następujący błąd.</span><span class="sxs-lookup"><span data-stu-id="74296-129">If you create a client/service using the `WSHttpBinding` element and you do not include the client callback endpoint, you will receive the following error.</span></span>

```console
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

<span data-ttu-id="74296-130">Poniższy przykładowy kod przedstawia sposób programowego określania adresu punktu końcowego klienta.</span><span class="sxs-lookup"><span data-stu-id="74296-130">The following sample code shows how to specify the client endpoint address programmatically.</span></span>

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

<span data-ttu-id="74296-131">Poniższy przykładowy kod pokazuje, jak określić adres punktu końcowego klienta w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="74296-131">The following sample code shows how to specify the client endpoint address in configuration.</span></span>

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
> <span data-ttu-id="74296-132">Model dupleksu nie wykrywa automatycznie, gdy usługa lub klient zamknie kanał.</span><span class="sxs-lookup"><span data-stu-id="74296-132">The duplex model doesn't automatically detect when a service or client closes its channel.</span></span> <span data-ttu-id="74296-133">Jeśli więc klient nieoczekiwanie zakończy działanie, domyślnie usługa nie zostanie powiadomiona lub jeśli usługa nieoczekiwanie zakończy działanie, klient nie zostanie powiadomiony.</span><span class="sxs-lookup"><span data-stu-id="74296-133">So if a client unexpectedly terminates, by default the service will not be notified, or if a service unexpectedly terminates, the client will not be notified.</span></span> <span data-ttu-id="74296-134">Jeśli używasz usługi, która jest odłączona, <xref:System.ServiceModel.CommunicationException> wyjątek jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="74296-134">If you use a service that is disconnected, the <xref:System.ServiceModel.CommunicationException> exception is raised.</span></span> <span data-ttu-id="74296-135">Klienci i usługi mogą wdrożyć własny protokół, aby powiadomić siebie nawzajem o takim wyborze.</span><span class="sxs-lookup"><span data-stu-id="74296-135">Clients and services can implement their own protocol to notify each other if they so choose.</span></span> <span data-ttu-id="74296-136">Aby uzyskać więcej informacji na temat obsługi błędów, zobacz [Obsługa błędów WCF](../wcf-error-handling.md).</span><span class="sxs-lookup"><span data-stu-id="74296-136">For more information on error handling, see [WCF Error Handling](../wcf-error-handling.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="74296-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74296-137">See also</span></span>

- [<span data-ttu-id="74296-138">Dupleks</span><span class="sxs-lookup"><span data-stu-id="74296-138">Duplex</span></span>](../samples/duplex.md)
- [<span data-ttu-id="74296-139">Określanie zachowania klienta w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="74296-139">Specifying Client Run-Time Behavior</span></span>](../specifying-client-run-time-behavior.md)
- [<span data-ttu-id="74296-140">Instrukcje: tworzenie fabryki kanałów i używanie jej do tworzenia kanałów oraz zarządzania nimi</span><span class="sxs-lookup"><span data-stu-id="74296-140">How to: Create a Channel Factory and Use it to Create and Manage Channels</span></span>](how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
