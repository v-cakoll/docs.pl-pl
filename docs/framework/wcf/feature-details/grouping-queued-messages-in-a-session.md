---
title: Grupowanie komunikatów z obsługą kolejek w ramach sesji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 231310e5c427f507141e3c144cb02b8e848d4fbf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185158"
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="b67b1-102">Grupowanie komunikatów z obsługą kolejek w ramach sesji</span><span class="sxs-lookup"><span data-stu-id="b67b1-102">Grouping Queued Messages in a Session</span></span>
<span data-ttu-id="b67b1-103">Windows Communication Foundation (WCF) udostępnia sesję, która umożliwia grupowanie zestawu powiązanych wiadomości razem do przetwarzania przez jedną aplikację odbierającą.</span><span class="sxs-lookup"><span data-stu-id="b67b1-103">Windows Communication Foundation (WCF) provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="b67b1-104">Wiadomości, które są częścią sesji musi być częścią tej samej transakcji.</span><span class="sxs-lookup"><span data-stu-id="b67b1-104">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="b67b1-105">Ponieważ wszystkie wiadomości są częścią tej samej transakcji, jeśli jedna wiadomość nie może być przetworzona, cała sesja zostanie wycofana.</span><span class="sxs-lookup"><span data-stu-id="b67b1-105">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="b67b1-106">Sesje mają podobne zachowania w odniesieniu do kolejek utraconych wiadomości i kolejek trucizny.</span><span class="sxs-lookup"><span data-stu-id="b67b1-106">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="b67b1-107">Właściwość Czas wygaśnięcia (TTL) ustawiona na powiązanie w kolejce skonfigurowane dla sesji jest stosowana do sesji jako całości.</span><span class="sxs-lookup"><span data-stu-id="b67b1-107">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="b67b1-108">Jeśli tylko niektóre wiadomości w sesji są wysyłane przed wygaśnięciem czasu wygaśnięcia, cała sesja jest umieszczana w kolejce utraconych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b67b1-108">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="b67b1-109">Podobnie, gdy wiadomości w sesji nie mogą być wysyłane do aplikacji z kolejki aplikacji, cała sesja jest umieszczana w kolejce trucić (jeśli są dostępne).</span><span class="sxs-lookup"><span data-stu-id="b67b1-109">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="b67b1-110">Przykład grupowania wiadomości</span><span class="sxs-lookup"><span data-stu-id="b67b1-110">Message Grouping Example</span></span>  
 <span data-ttu-id="b67b1-111">Jednym z przykładów, gdzie grupowanie wiadomości jest przydatne jest podczas implementowania aplikacji przetwarzania zamówień jako usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="b67b1-111">One example where grouping messages is helpful is when implementing an order-processing application as a WCF service.</span></span> <span data-ttu-id="b67b1-112">Na przykład klient przesyła zamówienie do tej aplikacji, która zawiera wiele elementów.</span><span class="sxs-lookup"><span data-stu-id="b67b1-112">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="b67b1-113">Dla każdego elementu klient wykonuje wywołanie usługi, co powoduje wysłanie osobnej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b67b1-113">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="b67b1-114">Istnieje możliwość wyświetlania A, aby otrzymać pierwszy element, a serwer B, aby otrzymać drugi element.</span><span class="sxs-lookup"><span data-stu-id="b67b1-114">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="b67b1-115">Za każdym razem, gdy element jest dodawany, serwer przetwarzający ten element musi znaleźć odpowiednią kolejność i dodać do niego element, który jest wysoce nieefektywny.</span><span class="sxs-lookup"><span data-stu-id="b67b1-115">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="b67b1-116">Nadal można napotkać takie nieefektywności tylko z jednego serwera obsługi wszystkich żądań, ponieważ serwer musi śledzić wszystkie zamówienia obecnie przetwarzane i określić, który z nich nowy element należy do.</span><span class="sxs-lookup"><span data-stu-id="b67b1-116">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="b67b1-117">Grupowanie wszystkich żądań dla jednego zamówienia znacznie upraszcza implementację takiej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b67b1-117">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="b67b1-118">Aplikacja kliencka wysyła wszystkie elementy dla pojedynczego zamówienia w sesji, więc gdy usługa przetwarza zamówienie, przetwarza całą sesję jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="b67b1-118">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="b67b1-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="b67b1-119">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="b67b1-120">Aby skonfigurować umowę serwisową do używania sesji</span><span class="sxs-lookup"><span data-stu-id="b67b1-120">To set up a service contract to use sessions</span></span>  
  
1. <span data-ttu-id="b67b1-121">Zdefiniuj umowę serwisową, która wymaga sesji.</span><span class="sxs-lookup"><span data-stu-id="b67b1-121">Define a service contract that requires a session.</span></span> <span data-ttu-id="b67b1-122">Zrób to <xref:System.ServiceModel.ServiceContractAttribute> za pomocą atrybutu, określając:</span><span class="sxs-lookup"><span data-stu-id="b67b1-122">Do this with the <xref:System.ServiceModel.ServiceContractAttribute> attribute by specifying:</span></span>  
  
    ```csharp
    SessionMode=SessionMode.Required  
    ```  
  
2. <span data-ttu-id="b67b1-123">Oznacz operacje w umowie jako jednokierunkowe, ponieważ te metody nie zwracają niczego.</span><span class="sxs-lookup"><span data-stu-id="b67b1-123">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="b67b1-124">Odbywa się to <xref:System.ServiceModel.OperationContractAttribute> za pomocą atrybutu, określając:</span><span class="sxs-lookup"><span data-stu-id="b67b1-124">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute by specifying:</span></span>  
  
    ```csharp  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. <span data-ttu-id="b67b1-125">Zaimplementuj <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> umowę <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>serwisową i określ wartość .</span><span class="sxs-lookup"><span data-stu-id="b67b1-125">Implement the service contract and specify an <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b67b1-126">Spowoduje to wystąpienie usługi tylko raz dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="b67b1-126">This instantiates the service only once for each session.</span></span>  
  
    ```csharp  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. <span data-ttu-id="b67b1-127">Każda operacja usługi wymaga transakcji.</span><span class="sxs-lookup"><span data-stu-id="b67b1-127">Each service operation requires a transaction.</span></span> <span data-ttu-id="b67b1-128">Określ to <xref:System.ServiceModel.OperationBehaviorAttribute> za pomocą atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b67b1-128">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="b67b1-129">Operacja, która kończy transakcję, <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> `true`powinna również być ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="b67b1-129">The operation that completes the transaction should also set <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> to `true`.</span></span>  
  
    ```csharp  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    ```  
  
5. <span data-ttu-id="b67b1-130">Skonfiguruj punkt końcowy, który `NetMsmqBinding` używa powiązania dostarczonego przez system.</span><span class="sxs-lookup"><span data-stu-id="b67b1-130">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6. <span data-ttu-id="b67b1-131">Utwórz kolejkę <xref:System.Messaging>transakcyjną przy użyciu programu .</span><span class="sxs-lookup"><span data-stu-id="b67b1-131">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="b67b1-132">Kolejkę można również utworzyć za pomocą usługi kolejkowania wiadomości (MSMQ) lub programu MMC.</span><span class="sxs-lookup"><span data-stu-id="b67b1-132">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="b67b1-133">Jeśli to zrobisz, utwórz kolejkę transakcyjną.</span><span class="sxs-lookup"><span data-stu-id="b67b1-133">If you do, create a transactional queue.</span></span>  
  
7. <span data-ttu-id="b67b1-134">Utwórz hosta usługi dla <xref:System.ServiceModel.ServiceHost>usługi za pomocą programu .</span><span class="sxs-lookup"><span data-stu-id="b67b1-134">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8. <span data-ttu-id="b67b1-135">Otwórz hosta usługi, aby udostępnić usługę.</span><span class="sxs-lookup"><span data-stu-id="b67b1-135">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="b67b1-136">Zamknij hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="b67b1-136">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="b67b1-137">Aby skonfigurować klienta</span><span class="sxs-lookup"><span data-stu-id="b67b1-137">To set up a client</span></span>  
  
1. <span data-ttu-id="b67b1-138">Utwórz zakres transakcji do zapisu w kolejce transakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="b67b1-138">Create a transaction scope to write to the transactional queue.</span></span>  
  
2. <span data-ttu-id="b67b1-139">Utwórz klienta WCF za pomocą narzędzia [Narzędzie narzędziowe ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)</span><span class="sxs-lookup"><span data-stu-id="b67b1-139">Create the WCF client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3. <span data-ttu-id="b67b1-140">Złóż zamówienie.</span><span class="sxs-lookup"><span data-stu-id="b67b1-140">Place the order.</span></span>  
  
4. <span data-ttu-id="b67b1-141">Zamknij klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="b67b1-141">Close the WCF client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b67b1-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="b67b1-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b67b1-143">Opis</span><span class="sxs-lookup"><span data-stu-id="b67b1-143">Description</span></span>  
 <span data-ttu-id="b67b1-144">Poniższy przykład zawiera kod `IProcessOrder` dla usługi i dla klienta, który używa tej usługi.</span><span class="sxs-lookup"><span data-stu-id="b67b1-144">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="b67b1-145">Pokazuje, jak WCF używa sesji w kolejce, aby zapewnić zachowanie grupowania.</span><span class="sxs-lookup"><span data-stu-id="b67b1-145">It shows how WCF uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="b67b1-146">Kod usługi</span><span class="sxs-lookup"><span data-stu-id="b67b1-146">Code for the Service</span></span>  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a><span data-ttu-id="b67b1-147">Kod dla klienta</span><span class="sxs-lookup"><span data-stu-id="b67b1-147">Code for the Client</span></span>  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="b67b1-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b67b1-148">See also</span></span>

- [<span data-ttu-id="b67b1-149">Sesje i kolejki</span><span class="sxs-lookup"><span data-stu-id="b67b1-149">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [<span data-ttu-id="b67b1-150">Omówienie kolejek</span><span class="sxs-lookup"><span data-stu-id="b67b1-150">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)
