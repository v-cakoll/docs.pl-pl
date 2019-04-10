---
title: 'Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 7463f9cfc37c2bf4f271f6e59896a7d77f3f65cd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310309"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="2207c-102">Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów</span><span class="sxs-lookup"><span data-stu-id="2207c-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>
<span data-ttu-id="2207c-103">Istniejące aplikacje usługi kolejkowania komunikatów (MSMQ) można zintegrować z aplikacjami Windows Communication Foundation (WCF), przy użyciu powiązanie integracji usługi MSMQ na Konwertowanie wiadomości usługi MSMQ komunikatów WCF.</span><span class="sxs-lookup"><span data-stu-id="2207c-103">You can integrate existing Message Queuing (MSMQ) applications with Windows Communication Foundation (WCF) applications by using the MSMQ integration binding to convert MSMQ messages to and from WCF messages.</span></span> <span data-ttu-id="2207c-104">Dzięki temu można wywoływać z aplikacji odbiornika usługi MSMQ z klientów programu WCF, a także wywoływać usługi WCF z usługi MSMQ nadawcy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2207c-104">This allows you to call into MSMQ receiver applications from WCF clients as well as call into WCF services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="2207c-105">W tej sekcji, firma Microsoft wyjaśniają jak używać <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> umieszczonych w kolejce komunikacji między (1) klienta WCF, jak i usługi aplikacji MSMQ napisane przy użyciu System.Messaging i (2) klienta aplikacji usługi MSMQ i usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="2207c-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a WCF client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a WCF service.</span></span>  
  
 <span data-ttu-id="2207c-106">Aby uzyskać pełny przykład pokazuje sposób wywołania aplikacji odbiornika usługi MSMQ z klienta programu WCF, zobacz [Windows Communication Foundation do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="2207c-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a WCF client, see the [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="2207c-107">Aby uzyskać pełny przykład pokazuje sposób wywołania usługi WCF w kliencie usługi MSMQ, zobacz [usługi kolejkowania komunikatów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="2207c-107">For a complete sample that demonstrates how to call a WCF service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="2207c-108">Aby utworzyć usługę WCF, która odbiera komunikaty z klienta usługi MSMQ</span><span class="sxs-lookup"><span data-stu-id="2207c-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1. <span data-ttu-id="2207c-109">Zdefiniuj interfejs, który definiuje kontrakt usługi dla usługi WCF, która odbiera komunikaty w kolejce z usługi MSMQ aplikacji nadawcy, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2207c-109">Define an interface that defines the service contract for the WCF service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. <span data-ttu-id="2207c-110">Zaimplementuj interfejs i zastosować <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutów do klasy, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2207c-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. <span data-ttu-id="2207c-111">Utwórz plik konfiguracji, który określa <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span><span class="sxs-lookup"><span data-stu-id="2207c-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  

4. <span data-ttu-id="2207c-112">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> obiektu, który używa skonfigurowanego powiązania.</span><span class="sxs-lookup"><span data-stu-id="2207c-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="2207c-113">Aby utworzyć klienta WCF, która wysyła komunikaty do aplikacji odbiornika usługi MSMQ</span><span class="sxs-lookup"><span data-stu-id="2207c-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1. <span data-ttu-id="2207c-114">Zdefiniuj interfejs, który definiuje kontrakt usługi dla klienta WCF, wysyła wiadomości, do odbiorcy usługi MSMQ w kolejce, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2207c-114">Define an interface that defines the service contract for the WCF client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. <span data-ttu-id="2207c-115">Zdefiniuj klasę klienta używanego przez klienta programu WCF do wywoływania odbiornika usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="2207c-115">Define a client class that the WCF client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. <span data-ttu-id="2207c-116">Utwórz konfigurację, która określa użycie powiązania MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="2207c-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. <span data-ttu-id="2207c-117">Utwórz wystąpienie klasy klienta i wywołanie metody zdefiniowane za pomocą wiadomości Odbieranie usługi.</span><span class="sxs-lookup"><span data-stu-id="2207c-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="2207c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2207c-118">See also</span></span>

- [<span data-ttu-id="2207c-119">Omówienie kolejek</span><span class="sxs-lookup"><span data-stu-id="2207c-119">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [<span data-ttu-id="2207c-120">Instrukcje: wymiana zakolejkowanych komunikatów z punktami końcowymi WCF</span><span class="sxs-lookup"><span data-stu-id="2207c-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [<span data-ttu-id="2207c-121">Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="2207c-121">Windows Communication Foundation to Message Queuing</span></span>](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="2207c-122">Instalowanie usługi kolejkowania komunikatów (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="2207c-122">Installing Message Queuing (MSMQ)</span></span>](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="2207c-123">Obsługa kolejek komunikatów programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="2207c-123">Message Queuing to Windows Communication Foundation</span></span>](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="2207c-124">Zabezpieczenia komunikatów w ramach kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="2207c-124">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
