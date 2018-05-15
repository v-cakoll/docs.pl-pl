---
title: 'Instrukcje: Wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 807a34ac50ea317ace42ec12eddcd9ec7cf3736b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="d69cd-102">Instrukcje: Wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów</span><span class="sxs-lookup"><span data-stu-id="d69cd-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>
<span data-ttu-id="d69cd-103">Istniejące aplikacje usługi kolejkowania komunikatów (MSMQ) można zintegrować z aplikacji Windows Communication Foundation (WCF), za pomocą powiązania integracji usługi MSMQ do przekonwertowania wiadomości usługi MSMQ do i z wiadomości WCF.</span><span class="sxs-lookup"><span data-stu-id="d69cd-103">You can integrate existing Message Queuing (MSMQ) applications with Windows Communication Foundation (WCF) applications by using the MSMQ integration binding to convert MSMQ messages to and from WCF messages.</span></span> <span data-ttu-id="d69cd-104">Dzięki temu można wywołują aplikacji odbiornika usługi MSMQ z klientów usługi WCF, a także wywołują usługi WCF z aplikacji nadawcy usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d69cd-104">This allows you to call into MSMQ receiver applications from WCF clients as well as call into WCF services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="d69cd-105">W tej sekcji możemy opisano sposób użycia <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> umieszczonych w kolejce komunikacji między (1) klienta WCF i usługa MSMQ aplikacji napisane przy użyciu usługi WCF i System.Messaging i (2) klienta aplikacji usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d69cd-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a WCF client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a WCF service.</span></span>  
  
 <span data-ttu-id="d69cd-106">Dla kompletnego przykładu, który demonstruje sposób wywołania aplikacji odbiornika usługi MSMQ z klienta WCF, zobacz [Windows Communication Foundation, do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="d69cd-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a WCF client, see the [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="d69cd-107">Na przykład pełną, który demonstruje sposób wywoływania usługi WCF w kliencie usługi MSMQ, zobacz [usługi kolejkowania komunikatów Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="d69cd-107">For a complete sample that demonstrates how to call a WCF service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="d69cd-108">Aby utworzyć usługę WCF, która odbiera komunikaty z klienta usługi MSMQ</span><span class="sxs-lookup"><span data-stu-id="d69cd-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1.  <span data-ttu-id="d69cd-109">Zdefiniuj interfejs, który definiuje kontrakt usługi dla usługi WCF, służącą do odbierania wiadomości w kolejce z aplikacją usługi MSMQ nadawcy, jak pokazano w poniższym kodzie przykład.</span><span class="sxs-lookup"><span data-stu-id="d69cd-109">Define an interface that defines the service contract for the WCF service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  <span data-ttu-id="d69cd-110">Zaimplementuj interfejs i zastosować <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu do klasy, jak pokazano w poniższym przykładzie kodzie.</span><span class="sxs-lookup"><span data-stu-id="d69cd-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  <span data-ttu-id="d69cd-111">Utwórz plik konfiguracji, który określa <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span><span class="sxs-lookup"><span data-stu-id="d69cd-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  
  
  
  
4.  <span data-ttu-id="d69cd-112">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> obiekt, który używa skonfigurowanego powiązania.</span><span class="sxs-lookup"><span data-stu-id="d69cd-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="d69cd-113">Aby utworzyć klienta WCF, który wysyła wiadomości do aplikacji odbiornika usługi MSMQ</span><span class="sxs-lookup"><span data-stu-id="d69cd-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1.  <span data-ttu-id="d69cd-114">Zdefiniuj interfejs, który definiuje kontrakt usługi dla klienta WCF wysyła wiadomości do odbiornika usługi MSMQ w kolejce, jak pokazano w poniższym przykładzie kodzie.</span><span class="sxs-lookup"><span data-stu-id="d69cd-114">Define an interface that defines the service contract for the WCF client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  <span data-ttu-id="d69cd-115">Zdefiniuj klasę klienta używany przez klienta WCF do wywoływania odbiornika usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d69cd-115">Define a client class that the WCF client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  <span data-ttu-id="d69cd-116">Tworzenie konfiguracji, który określa użycie powiązania MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="d69cd-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  <span data-ttu-id="d69cd-117">Tworzenie wystąpienia klasy klienta i wywołaj metodę zdefiniowany przez komunikat odbieranie usługi.</span><span class="sxs-lookup"><span data-stu-id="d69cd-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="d69cd-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d69cd-118">See Also</span></span>  
 [<span data-ttu-id="d69cd-119">Omówienie kolejek</span><span class="sxs-lookup"><span data-stu-id="d69cd-119">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [<span data-ttu-id="d69cd-120">Instrukcje: wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF</span><span class="sxs-lookup"><span data-stu-id="d69cd-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [<span data-ttu-id="d69cd-121">Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="d69cd-121">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [<span data-ttu-id="d69cd-122">Instalowanie usługi kolejkowania komunikatów (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="d69cd-122">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [<span data-ttu-id="d69cd-123">Obsługa kolejek komunikatów programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d69cd-123">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [<span data-ttu-id="d69cd-124">Zabezpieczenia komunikatów w ramach kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="d69cd-124">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
