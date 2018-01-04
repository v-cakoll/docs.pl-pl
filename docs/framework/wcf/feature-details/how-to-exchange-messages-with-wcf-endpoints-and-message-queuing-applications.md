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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa6f9d0b9631420013593cb44903b5451549e8c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>Instrukcje: Wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów
Możesz też zintegrować istniejące aplikacje usługi kolejkowania komunikatów (MSMQ) z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikacji za pomocą powiązania integracji usługi MSMQ do przekonwertowania wiadomości usługi MSMQ do i z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wiadomości. Dzięki temu można wywołać do aplikacji odbiornika usługi MSMQ z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientów, a także wywołanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług z aplikacji nadawcy usługi MSMQ.  
  
 W tej sekcji możemy opisano sposób użycia <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> umieszczonych w kolejce komunikacji między (1 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta i usługi MSMQ usługi aplikacji napisanych z użyciem System.Messaging i (2) klienta aplikacji usługi MSMQ i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.  
  
 Dla kompletnego przykładu, który demonstruje sposób wywoływania usługi MSMQ aplikacja odbiorcy z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, zobacz [Windows Communication Foundation, do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) próbki.  
  
 Dla kompletnego przykładu, który demonstruje sposób wywoływania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi z klienta usługi MSMQ, zobacz [usługi kolejkowania komunikatów Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) próbki.  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>Aby utworzyć usługę WCF, która odbiera komunikaty z klienta usługi MSMQ  
  
1.  Zdefiniuj interfejs, który definiuje kontrakt usługi dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, który odbiera wiadomości w kolejce z usługi MSMQ aplikacji nadawcy, jak pokazano w poniższym przykładzie kodzie.  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  Zaimplementuj interfejs i zastosować <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu do klasy, jak pokazano w poniższym przykładzie kodzie.  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  Utwórz plik konfiguracji, który określa <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
  
  
4.  Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> obiekt, który używa skonfigurowanego powiązania.  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>Aby utworzyć klienta WCF, który wysyła wiadomości do aplikacji odbiornika usługi MSMQ  
  
1.  Zdefiniuj interfejs, który definiuje kontrakt usługi dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, który wysyła umieszczonych w kolejce komunikaty odbiornik usługi MSMQ, jak pokazano w poniższym przykładzie kodzie.  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  Zdefiniuj klienta klasy, która [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient używa do wywołania odbiornika usługi MSMQ.  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3.  Tworzenie konfiguracji, który określa użycie powiązania MsmqIntegrationBinding.  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4.  Tworzenie wystąpienia klasy klienta i wywołaj metodę zdefiniowany przez komunikat odbieranie usługi.  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Instrukcje: wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Instalowanie usługi kolejkowania komunikatów (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Obsługa kolejek komunikatów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Zabezpieczenia komunikatów w ramach kolejkowania komunikatów](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
