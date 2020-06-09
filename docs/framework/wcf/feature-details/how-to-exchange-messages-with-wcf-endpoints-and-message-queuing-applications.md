---
title: 'Instrukcje: Wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 0775de90903aed27a8d0006614a4b6f2d857eee3
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597101"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a><span data-ttu-id="45432-102">Instrukcje: Wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów</span><span class="sxs-lookup"><span data-stu-id="45432-102">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>
<span data-ttu-id="45432-103">Istniejące aplikacje usługi kolejkowania komunikatów (MSMQ) można zintegrować z aplikacjami Windows Communication Foundation (WCF) przy użyciu powiązania integracji usługi MSMQ w celu konwertowania komunikatów usługi MSMQ do i z komunikatów WCF.</span><span class="sxs-lookup"><span data-stu-id="45432-103">You can integrate existing Message Queuing (MSMQ) applications with Windows Communication Foundation (WCF) applications by using the MSMQ integration binding to convert MSMQ messages to and from WCF messages.</span></span> <span data-ttu-id="45432-104">Pozwala to na wywoływanie aplikacji odbiornika usługi MSMQ z klientów WCF, a także wywoływanie usług WCF z aplikacji nadawcy usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="45432-104">This allows you to call into MSMQ receiver applications from WCF clients as well as call into WCF services from MSMQ sender applications.</span></span>  
  
 <span data-ttu-id="45432-105">W tej sekcji wyjaśniono, jak używać funkcji <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> komunikacji w kolejce między (1) klientem programu WCF i usługą aplikacji MSMQ zapisaną przy użyciu funkcji system. Messaging i (2) klienta aplikacji usługi MSMQ i usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="45432-105">In this section, we explain how to use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> for queued communication between (1) a WCF client and an MSMQ application service written using System.Messaging and (2) an MSMQ application client and a WCF service.</span></span>  
  
 <span data-ttu-id="45432-106">Aby zapoznać się z kompletnym przykładem, który pokazuje, jak wywołać aplikację odbiornika usługi MSMQ z poziomu klienta WCF, zobacz [Windows Communication Foundation do usługi kolejkowania komunikatów](../samples/wcf-to-message-queuing.md) .</span><span class="sxs-lookup"><span data-stu-id="45432-106">For a complete sample that demonstrates how to call a MSMQ receiver application from a WCF client, see the [Windows Communication Foundation to Message Queuing](../samples/wcf-to-message-queuing.md) sample.</span></span>  
  
 <span data-ttu-id="45432-107">Aby zapoznać się z kompletnym przykładem, który ilustruje sposób wywoływania usługi WCF z poziomu klienta usługi MSMQ, zobacz [Usługa kolejkowania komunikatów do Windows Communication Foundation](../samples/message-queuing-to-wcf.md) przykład.</span><span class="sxs-lookup"><span data-stu-id="45432-107">For a complete sample that demonstrates how to call a WCF service from a MSMQ client, see the [Message Queuing to Windows Communication Foundation](../samples/message-queuing-to-wcf.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a><span data-ttu-id="45432-108">Aby utworzyć usługę WCF, która odbiera komunikaty z klienta MSMQ</span><span class="sxs-lookup"><span data-stu-id="45432-108">To create a WCF service that receives messages from a MSMQ client</span></span>  
  
1. <span data-ttu-id="45432-109">Zdefiniuj interfejs, który definiuje kontrakt usługi dla usługi WCF, który odbiera kolejkowane komunikaty z aplikacji nadawcy usługi MSMQ, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="45432-109">Define an interface that defines the service contract for the WCF service that receives queued messages from a MSMQ sender application, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. <span data-ttu-id="45432-110">Zaimplementuj interfejs i Zastosuj <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybut do klasy, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="45432-110">Implement the interface and apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to the class, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. <span data-ttu-id="45432-111">Utwórz plik konfiguracji, który określa <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> .</span><span class="sxs-lookup"><span data-stu-id="45432-111">Create a configuration file that specifies the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span>  

4. <span data-ttu-id="45432-112">Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> obiektu, który używa skonfigurowanego powiązania.</span><span class="sxs-lookup"><span data-stu-id="45432-112">Instantiate a <xref:System.ServiceModel.ServiceHost> object that uses the configured binding.</span></span>  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a><span data-ttu-id="45432-113">Aby utworzyć klienta WCF, który wysyła komunikaty do aplikacji odbiornika usługi MSMQ</span><span class="sxs-lookup"><span data-stu-id="45432-113">To create a WCF client that sends messages to a MSMQ receiver application</span></span>  
  
1. <span data-ttu-id="45432-114">Zdefiniuj interfejs, który definiuje kontrakt usługi dla klienta WCF, który wysyła wiadomości w kolejce do odbiornika MSMQ, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="45432-114">Define an interface that defines the service contract for the WCF client that sends queued messages to the MSMQ receiver, as shown in the following example code.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. <span data-ttu-id="45432-115">Zdefiniuj klasę klienta używaną przez klienta WCF do wywoływania odbiorcy usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="45432-115">Define a client class that the WCF client uses to call the MSMQ receiver.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. <span data-ttu-id="45432-116">Utwórz konfigurację, która określa użycie powiązania MsmqIntegrationBinding.</span><span class="sxs-lookup"><span data-stu-id="45432-116">Create a configuration that specifies use of the MsmqIntegrationBinding binding.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. <span data-ttu-id="45432-117">Utwórz wystąpienie klasy Client i Wywołaj metodę zdefiniowaną przez usługę otrzymywania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="45432-117">Create an instance of the client class and call the method defined by the message receiving service.</span></span>  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="45432-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45432-118">See also</span></span>

- [<span data-ttu-id="45432-119">Omówienie kolejek</span><span class="sxs-lookup"><span data-stu-id="45432-119">Queues Overview</span></span>](queues-overview.md)
- [<span data-ttu-id="45432-120">Instrukcje: wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF</span><span class="sxs-lookup"><span data-stu-id="45432-120">How to: Exchange Queued Messages with WCF Endpoints</span></span>](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [<span data-ttu-id="45432-121">Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="45432-121">Windows Communication Foundation to Message Queuing</span></span>](../samples/wcf-to-message-queuing.md)
- [<span data-ttu-id="45432-122">Instalowanie usługi kolejkowania komunikatów (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="45432-122">Installing Message Queuing (MSMQ)</span></span>](../samples/installing-message-queuing-msmq.md)
- [<span data-ttu-id="45432-123">Obsługa kolejek komunikatów programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="45432-123">Message Queuing to Windows Communication Foundation</span></span>](../samples/message-queuing-to-wcf.md)
- [<span data-ttu-id="45432-124">Zabezpieczenia komunikatów w ramach kolejkowania komunikatów</span><span class="sxs-lookup"><span data-stu-id="45432-124">Message Security over Message Queuing</span></span>](../samples/message-security-over-message-queuing.md)
