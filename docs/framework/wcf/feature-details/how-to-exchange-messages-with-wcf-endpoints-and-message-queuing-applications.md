---
title: "Instrukcje: Wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów"
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
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d09b8e662b2876fa5d5c5246ea7e7a4998cde9ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="3c89f-102">Instrukcje: Wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów</span><span class="sxs-lookup"><span data-stu-id="3c89f-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>
<span data-ttu-id="3c89f-103">Możesz też zintegrować istniejące aplikacje usługi kolejkowania komunikatów (MSMQ) z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji za pomocą powiązania integracji usługi MSMQ do przekonwertowania wiadomości usługi MSMQ do i z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3c89f-103">You can integrate existing Message Queuing (MSMQ) applications with [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications by using the MSMQ integration binding to convert MSMQ messages to and from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] messages.</span></span> <span data-ttu-id="3c89f-104">Dzięki temu można wywołać do aplikacji odbiornika usługi MSMQ z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów, a także wywołanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług z aplikacji nadawcy usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3c89f-104">This allows you to call into MSMQ receiver applications from [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients as well as call into [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="3c89f-105">W tej sekcji możemy opisano sposób użycia <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> umieszczonych w kolejce komunikacji między (1 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta i usługi MSMQ usługi aplikacji napisanych z użyciem System.Messaging i (2) klienta aplikacji usługi MSMQ i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="3c89f-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="3c89f-106">Dla kompletnego przykładu, który demonstruje sposób wywoływania usługi MSMQ aplikacja odbiorcy z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, zobacz [Windows Communication Foundation, do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="3c89f-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, see the [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="3c89f-107">Dla kompletnego przykładu, który demonstruje sposób wywoływania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi z klienta usługi MSMQ, zobacz [usługi kolejkowania komunikatów Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="3c89f-107">For a complete sample that demonstrates how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="3c89f-108">Aby utworzyć usługę WCF, która odbiera komunikaty z klienta usługi MSMQ</span><span class="sxs-lookup"><span data-stu-id="3c89f-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1.  <span data-ttu-id="3c89f-109">Zdefiniuj interfejs, który definiuje kontrakt usługi dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, który odbiera wiadomości w kolejce z usługi MSMQ aplikacji nadawcy, jak pokazano w poniższym przykładzie kodzie.</span><span class="sxs-lookup"><span data-stu-id="3c89f-109">Define an interface that defines the service contract for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  <span data-ttu-id="3c89f-110">Zaimplementuj interfejs i zastosować <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu do klasy, jak pokazano w poniższym przykładzie kodzie.</span><span class="sxs-lookup"><span data-stu-id="3c89f-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  <span data-ttu-id="3c89f-111">Utwórz plik konfiguracji, który określa <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span><span class="sxs-lookup"><span data-stu-id="3c89f-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  
  
  
  
4.  <span data-ttu-id="3c89f-112">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> obiekt, który używa skonfigurowanego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3c89f-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="3c89f-113">Aby utworzyć klienta WCF, który wysyła wiadomości do aplikacji odbiornika usługi MSMQ</span><span class="sxs-lookup"><span data-stu-id="3c89f-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1.  <span data-ttu-id="3c89f-114">Zdefiniuj interfejs, który definiuje kontrakt usługi dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, który wysyła umieszczonych w kolejce komunikaty odbiornik usługi MSMQ, jak pokazano w poniższym przykładzie kodzie.</span><span class="sxs-lookup"><span data-stu-id="3c89f-114">Define an interface that defines the service contract for the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  <span data-ttu-id="3c89f-115">Zdefiniuj klienta klasy, która [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient używa do wywołania odbiornika usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="3c89f-115">Define a client class that the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  <span data-ttu-id="3c89f-116">Tworzenie konfiguracji, który określa użycie powiązania MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="3c89f-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  <span data-ttu-id="3c89f-117">Tworzenie wystąpienia klasy klienta i wywołaj metodę zdefiniowany przez komunikat odbieranie usługi.</span><span class="sxs-lookup"><span data-stu-id="3c89f-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="3c89f-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c89f-118">See Also</span></span>  
 [<span data-ttu-id="3c89f-119">Omówienie kolejek</span><span class="sxs-lookup"><span data-stu-id="3c89f-119">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [<span data-ttu-id="3c89f-120">Porady: wymiana komunikatów z punktami końcowymi WCF umieszczonych w kolejce</span><span class="sxs-lookup"><span data-stu-id="3c89f-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [<span data-ttu-id="3c89f-121">Windows Communication Foundation, do usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="3c89f-121">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [<span data-ttu-id="3c89f-122">Instalowanie usługi kolejkowania komunikatów (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="3c89f-122">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [<span data-ttu-id="3c89f-123">Obsługa kolejek komunikatów programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3c89f-123">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [<span data-ttu-id="3c89f-124">Zabezpieczenia komunikatów w ramach usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="3c89f-124">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
