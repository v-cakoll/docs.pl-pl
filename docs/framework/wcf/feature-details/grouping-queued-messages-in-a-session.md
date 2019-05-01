---
title: Grupowanie komunikatów z obsługą kolejek w ramach sesji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 37f0874ea99ee928e49a54a3e6a05ea4ef06f84e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855923"
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="bd958-102">Grupowanie komunikatów z obsługą kolejek w ramach sesji</span><span class="sxs-lookup"><span data-stu-id="bd958-102">Grouping Queued Messages in a Session</span></span>
<span data-ttu-id="bd958-103">Windows Communication Foundation (WCF) zapewnia sesji, która pozwala grupować zestaw komunikatów powiązane ze sobą do przetworzenia przez aplikację odbierającą jednego.</span><span class="sxs-lookup"><span data-stu-id="bd958-103">Windows Communication Foundation (WCF) provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="bd958-104">Komunikaty, które są częścią sesji musi być częścią tej samej transakcji.</span><span class="sxs-lookup"><span data-stu-id="bd958-104">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="bd958-105">Ponieważ wszystkie komunikaty są częścią tej samej transakcji, jeśli jeden komunikat zakończy się niepowodzeniem do przetworzenia całej sesji jest wycofywana.</span><span class="sxs-lookup"><span data-stu-id="bd958-105">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="bd958-106">Sesje mają podobne zachowanie w odniesieniu do kolejki utraconych wiadomości i skażone kolejki.</span><span class="sxs-lookup"><span data-stu-id="bd958-106">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="bd958-107">Czas wygaśnięcia (TTL) ustawiona w Zakolejkowane powiązanie skonfigurowane dla sesji jest stosowana do sesji jako całości.</span><span class="sxs-lookup"><span data-stu-id="bd958-107">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="bd958-108">Jeśli tylko część wiadomości w sesji są wysyłane przed wygaśnięcia, podczas całej sesji jest umieszczana w kolejce wiadomości utraconych.</span><span class="sxs-lookup"><span data-stu-id="bd958-108">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="bd958-109">Podobnie po wiadomości w sesji nie można wysyłać do aplikacji z kolejki aplikacji, podczas całej sesji jest umieszczany w kolejce skażone (jeśli jest dostępny).</span><span class="sxs-lookup"><span data-stu-id="bd958-109">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="bd958-110">Przykład grupowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="bd958-110">Message Grouping Example</span></span>  
 <span data-ttu-id="bd958-111">Przykładem, w których grupowanie komunikatów przydaje się to podczas wdrażania aplikacji przetwarzania zamówień jako usługa WCF.</span><span class="sxs-lookup"><span data-stu-id="bd958-111">One example where grouping messages is helpful is when implementing an order-processing application as a WCF service.</span></span> <span data-ttu-id="bd958-112">Na przykład klient składa zamówienie do tej aplikacji, która zawiera wiele elementów.</span><span class="sxs-lookup"><span data-stu-id="bd958-112">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="bd958-113">Dla każdego elementu klient wysyła wywołania do usługi, co skutkuje osobnej wiadomości wysyłane.</span><span class="sxs-lookup"><span data-stu-id="bd958-113">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="bd958-114">Jest możliwe, a będzie służył do odbierania pierwszego elementu a serwer B, aby otrzymywał drugiego elementu.</span><span class="sxs-lookup"><span data-stu-id="bd958-114">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="bd958-115">Każdorazowo, gdy element zostanie dodany serwer przetwarzania tego elementu musi znaleźć właściwą kolejność i Dodaj element, który jest bardzo mało wydajne.</span><span class="sxs-lookup"><span data-stu-id="bd958-115">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="bd958-116">Nadal występują takie czynniki za pomocą tylko obsługę wszystkich żądań, ponieważ serwer musi śledzić wszystkie zamówienia w danej chwili przetwarzany i określić, której nowy element należy do jednego serwera.</span><span class="sxs-lookup"><span data-stu-id="bd958-116">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="bd958-117">Grupowanie wszystkie żądania dotyczące pojedynczego zamówienia znacznie upraszcza implementacji takich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bd958-117">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="bd958-118">Aplikacja kliencka wysyła wszystkie elementy w jednym zamówienia w sesji, dzięki czemu usługa przetworzy to zamówienie, przetwarza jednocześnie całej sesji.</span><span class="sxs-lookup"><span data-stu-id="bd958-118">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="bd958-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="bd958-119">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="bd958-120">Aby skonfigurować kontraktu usługi do użycia sesji</span><span class="sxs-lookup"><span data-stu-id="bd958-120">To set up a service contract to use sessions</span></span>  
  
1. <span data-ttu-id="bd958-121">Definiowanie kontraktu usługi, która wymaga sesji.</span><span class="sxs-lookup"><span data-stu-id="bd958-121">Define a service contract that requires a session.</span></span> <span data-ttu-id="bd958-122">W tym z <xref:System.ServiceModel.OperationContractAttribute> atrybutu i określenie:</span><span class="sxs-lookup"><span data-stu-id="bd958-122">Do this with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2. <span data-ttu-id="bd958-123">Oznacz operacji w umowie jako jednokierunkowe, ponieważ te metody nie zwraca niczego.</span><span class="sxs-lookup"><span data-stu-id="bd958-123">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="bd958-124">Jest to zrobić za pomocą <xref:System.ServiceModel.OperationContractAttribute> atrybutu i określenie:</span><span class="sxs-lookup"><span data-stu-id="bd958-124">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. <span data-ttu-id="bd958-125">Implementowanie kontraktu usługi i określ `InstanceContextMode` z `PerSession`.</span><span class="sxs-lookup"><span data-stu-id="bd958-125">Implement the service contract and specify an `InstanceContextMode` of `PerSession`.</span></span> <span data-ttu-id="bd958-126">Tworzy to wystąpienie usługi, tylko jeden raz dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="bd958-126">This instantiates the service only once for each session.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. <span data-ttu-id="bd958-127">Każda operacja usługi wymaga transakcji.</span><span class="sxs-lookup"><span data-stu-id="bd958-127">Each service operation requires a transaction.</span></span> <span data-ttu-id="bd958-128">Określ za pomocą <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bd958-128">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="bd958-129">Operacja, która kończy transakcji należy również ustawić `TransactionAutoComplete` do `true`.</span><span class="sxs-lookup"><span data-stu-id="bd958-129">The operation that completes the transaction should also set `TransactionAutoComplete` to `true`.</span></span>  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5. <span data-ttu-id="bd958-130">Konfigurowanie punktu końcowego, który używa dostarczane przez system `NetMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="bd958-130">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6. <span data-ttu-id="bd958-131">Utwórz kolejkę transakcyjną za pomocą <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="bd958-131">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="bd958-132">Można również utworzyć kolejkę przy użyciu usługi kolejkowania komunikatów (MSMQ) lub programu MMC.</span><span class="sxs-lookup"><span data-stu-id="bd958-132">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="bd958-133">Jeśli to zrobisz, Utwórz kolejkę transakcyjną.</span><span class="sxs-lookup"><span data-stu-id="bd958-133">If you do, create a transactional queue.</span></span>  
  
7. <span data-ttu-id="bd958-134">Tworzenie usługi hosta usługi przy użyciu <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="bd958-134">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8. <span data-ttu-id="bd958-135">Otwórz hosta usługi, aby udostępnić usługę.</span><span class="sxs-lookup"><span data-stu-id="bd958-135">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="bd958-136">Zamknij hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="bd958-136">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="bd958-137">Aby skonfigurować klienta</span><span class="sxs-lookup"><span data-stu-id="bd958-137">To set up a client</span></span>  
  
1. <span data-ttu-id="bd958-138">Tworzenie zakresu transakcji do zapisu do kolejki transakcyjne.</span><span class="sxs-lookup"><span data-stu-id="bd958-138">Create a transaction scope to write to the transactional queue.</span></span>  
  
2. <span data-ttu-id="bd958-139">Tworzenie klienta WCF, używając [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="bd958-139">Create the WCF client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3. <span data-ttu-id="bd958-140">Złóż zamówienie.</span><span class="sxs-lookup"><span data-stu-id="bd958-140">Place the order.</span></span>  
  
4. <span data-ttu-id="bd958-141">Zamknij klienta platformy WCF.</span><span class="sxs-lookup"><span data-stu-id="bd958-141">Close the WCF client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd958-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="bd958-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="bd958-143">Opis</span><span class="sxs-lookup"><span data-stu-id="bd958-143">Description</span></span>  
 <span data-ttu-id="bd958-144">W poniższym przykładzie przedstawiono kod używany w `IProcessOrder` usługi i dla klienta, który korzysta z tej usługi.</span><span class="sxs-lookup"><span data-stu-id="bd958-144">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="bd958-145">Pokazuje, jak WCF używa sesji w kolejce, aby zapewnić zachowanie grupowania.</span><span class="sxs-lookup"><span data-stu-id="bd958-145">It shows how WCF uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="bd958-146">Kod usługi</span><span class="sxs-lookup"><span data-stu-id="bd958-146">Code for the Service</span></span>  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a><span data-ttu-id="bd958-147">Kod klienta</span><span class="sxs-lookup"><span data-stu-id="bd958-147">Code for the Client</span></span>  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="bd958-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd958-148">See also</span></span>

- [<span data-ttu-id="bd958-149">Sesje i kolejki</span><span class="sxs-lookup"><span data-stu-id="bd958-149">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [<span data-ttu-id="bd958-150">Omówienie kolejek</span><span class="sxs-lookup"><span data-stu-id="bd958-150">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)
