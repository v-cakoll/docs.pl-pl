---
title: "Grupowanie komunikatów z obsługą kolejek w ramach sesji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aba045456d61b5ad687f1030dca3c26b083cdb58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="77591-102">Grupowanie komunikatów z obsługą kolejek w ramach sesji</span><span class="sxs-lookup"><span data-stu-id="77591-102">Grouping Queued Messages in a Session</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="77591-103">zawiera sesję, który umożliwia grupowanie zestaw komunikatów powiązane ze sobą do przetworzenia przez aplikację odbierającą pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="77591-103"> provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="77591-104">Komunikaty, które są częścią sesji musi być częścią tej samej transakcji.</span><span class="sxs-lookup"><span data-stu-id="77591-104">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="77591-105">Ponieważ wszystkie komunikaty są częścią tej samej transakcji, jeśli jeden komunikat nie można przetworzyć całej sesji została wycofana.</span><span class="sxs-lookup"><span data-stu-id="77591-105">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="77591-106">Sesje mają podobne zachowania w odniesieniu do kolejki utraconych wiadomości i kolejki skażone.</span><span class="sxs-lookup"><span data-stu-id="77591-106">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="77591-107">Czas wygaśnięcia (TTL) ustawiona w Zakolejkowane powiązanie skonfigurowane dla sesji jest stosowany do sesji jako całość.</span><span class="sxs-lookup"><span data-stu-id="77591-107">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="77591-108">Jeśli tylko niektóre wiadomości w sesji są wysyłane przed wygaśnięciem czas TTL, całej sesji jest umieszczona w kolejce wiadomości utraconych.</span><span class="sxs-lookup"><span data-stu-id="77591-108">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="77591-109">Podobnie gdy wiadomości w sesji nie mogą być wysyłane do aplikacji z kolejki aplikacji, całej sesji jest umieszczone w kolejce skażone (jeśli jest dostępna).</span><span class="sxs-lookup"><span data-stu-id="77591-109">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="77591-110">Przykład grupowanie komunikatów</span><span class="sxs-lookup"><span data-stu-id="77591-110">Message Grouping Example</span></span>  
 <span data-ttu-id="77591-111">Jest przykładem, w których grupowanie komunikatów jest przydatne podczas wdrażania aplikacji przetwarzanie zamówień jako [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="77591-111">One example where grouping messages is helpful is when implementing an order-processing application as a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="77591-112">Na przykład klient przesyła kolejności do tej aplikacji, która zawiera liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="77591-112">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="77591-113">Dla każdego elementu klient nawiązuje połączenie z usługą, co prowadzi do osobnej wiadomości wysyłane.</span><span class="sxs-lookup"><span data-stu-id="77591-113">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="77591-114">Istnieje możliwość A służą do odebrania pierwszego elementu i serwer B, aby otrzymywał drugiego elementu.</span><span class="sxs-lookup"><span data-stu-id="77591-114">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="77591-115">Zawsze, gdy element zostanie dodany serwer przetwarzania elementu ma można znaleźć odpowiedniej kolejności i Dodaj element, który jest bardzo mało wydajne.</span><span class="sxs-lookup"><span data-stu-id="77591-115">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="77591-116">Nadal uruchamiać się do takich wydajność z tylko jednym serwerem obsługi wszystkich żądań, ponieważ serwer musi śledzić wszystkie zamówienia aktualnie przetwarzane i określić, która z nich nowy element należy do.</span><span class="sxs-lookup"><span data-stu-id="77591-116">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="77591-117">Grupowanie wszystkie żądania dotyczące pojedynczego zamówienia znacznie upraszcza implementacji takich aplikacji.</span><span class="sxs-lookup"><span data-stu-id="77591-117">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="77591-118">Aplikacja kliencka wysyła wszystkie elementy dla pojedynczego zamówienia w sesji, więc usługa przetwarza kolejności, przetwarza jednocześnie całej sesji.</span><span class="sxs-lookup"><span data-stu-id="77591-118">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="77591-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="77591-119">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="77591-120">Aby skonfigurować kontraktu usługi do użycia sesji</span><span class="sxs-lookup"><span data-stu-id="77591-120">To set up a service contract to use sessions</span></span>  
  
1.  <span data-ttu-id="77591-121">Definiowanie kontraktu usługi, która wymaga sesji.</span><span class="sxs-lookup"><span data-stu-id="77591-121">Define a service contract that requires a session.</span></span> <span data-ttu-id="77591-122">W tym z <xref:System.ServiceModel.OperationContractAttribute> atrybutu i określenie:</span><span class="sxs-lookup"><span data-stu-id="77591-122">Do this with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2.  <span data-ttu-id="77591-123">Oznacz operacji w umowie jako jednokierunkowe, ponieważ metody te nie mają żadnych czynności.</span><span class="sxs-lookup"><span data-stu-id="77591-123">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="77591-124">Jest to zrobić za pomocą <xref:System.ServiceModel.OperationContractAttribute> atrybutu i określenie:</span><span class="sxs-lookup"><span data-stu-id="77591-124">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3.  <span data-ttu-id="77591-125">Implementowanie kontraktu usługi i określ `InstanceContextMode` z `PerSession`.</span><span class="sxs-lookup"><span data-stu-id="77591-125">Implement the service contract and specify an `InstanceContextMode` of `PerSession`.</span></span> <span data-ttu-id="77591-126">Tworzy to wystąpienie usługi, tylko raz dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="77591-126">This instantiates the service only once for each session.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4.  <span data-ttu-id="77591-127">Każda operacja usługi wymaga transakcji.</span><span class="sxs-lookup"><span data-stu-id="77591-127">Each service operation requires a transaction.</span></span> <span data-ttu-id="77591-128">Określ ją z <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="77591-128">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="77591-129">Operacja, która kończy transakcji należy również ustawić `TransactionAutoComplete` do `true`.</span><span class="sxs-lookup"><span data-stu-id="77591-129">The operation that completes the transaction should also set `TransactionAutoComplete` to `true`.</span></span>  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5.  <span data-ttu-id="77591-130">Konfigurowanie punktu końcowego, który używa dostarczane przez system `NetMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="77591-130">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6.  <span data-ttu-id="77591-131">Tworzenie kolejki transakcyjnej przy użyciu <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="77591-131">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="77591-132">Można również utworzyć kolejkę, za pomocą usługi kolejkowania komunikatów (MSMQ) lub programu MMC.</span><span class="sxs-lookup"><span data-stu-id="77591-132">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="77591-133">Jeśli to zrobisz, Utwórz kolejkę transakcyjną.</span><span class="sxs-lookup"><span data-stu-id="77591-133">If you do, create a transactional queue.</span></span>  
  
7.  <span data-ttu-id="77591-134">Utwórz hosta usługi dla usługi przy użyciu <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="77591-134">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8.  <span data-ttu-id="77591-135">Otworzyć hosta usługi, aby udostępnić usługę.</span><span class="sxs-lookup"><span data-stu-id="77591-135">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="77591-136">Zamknij hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="77591-136">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="77591-137">Aby skonfigurować klienta</span><span class="sxs-lookup"><span data-stu-id="77591-137">To set up a client</span></span>  
  
1.  <span data-ttu-id="77591-138">Tworzenie zakresu transakcji do zapisu transakcyjne kolejki.</span><span class="sxs-lookup"><span data-stu-id="77591-138">Create a transaction scope to write to the transactional queue.</span></span>  
  
2.  <span data-ttu-id="77591-139">Utwórz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta przy użyciu [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia.</span><span class="sxs-lookup"><span data-stu-id="77591-139">Create the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3.  <span data-ttu-id="77591-140">Umieść kolejności.</span><span class="sxs-lookup"><span data-stu-id="77591-140">Place the order.</span></span>  
  
4.  <span data-ttu-id="77591-141">Zamknij [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta.</span><span class="sxs-lookup"><span data-stu-id="77591-141">Close the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77591-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="77591-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="77591-143">Opis</span><span class="sxs-lookup"><span data-stu-id="77591-143">Description</span></span>  
 <span data-ttu-id="77591-144">W poniższym przykładzie przedstawiono kod `IProcessOrder` usługi i dla klienta, który korzysta z tej usługi.</span><span class="sxs-lookup"><span data-stu-id="77591-144">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="77591-145">Widoczny jest sposób [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa w kolejce sesji, aby zapewnić zachowanie grupowania.</span><span class="sxs-lookup"><span data-stu-id="77591-145">It shows how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="77591-146">Kod usługi</span><span class="sxs-lookup"><span data-stu-id="77591-146">Code for the Service</span></span>  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  
  
  
  
### <a name="code-for-the-client"></a><span data-ttu-id="77591-147">Kod dla klienta</span><span class="sxs-lookup"><span data-stu-id="77591-147">Code for the Client</span></span>  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="77591-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77591-148">See Also</span></span>  
 [<span data-ttu-id="77591-149">Sesje i kolejki</span><span class="sxs-lookup"><span data-stu-id="77591-149">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [<span data-ttu-id="77591-150">Omówienie kolejek</span><span class="sxs-lookup"><span data-stu-id="77591-150">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)
