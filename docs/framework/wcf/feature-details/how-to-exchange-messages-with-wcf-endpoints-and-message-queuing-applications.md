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
ms.locfileid: "33491082"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>Instrukcje: Wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów
Istniejące aplikacje usługi kolejkowania komunikatów (MSMQ) można zintegrować z aplikacji Windows Communication Foundation (WCF), za pomocą powiązania integracji usługi MSMQ do przekonwertowania wiadomości usługi MSMQ do i z wiadomości WCF. Dzięki temu można wywołują aplikacji odbiornika usługi MSMQ z klientów usługi WCF, a także wywołują usługi WCF z aplikacji nadawcy usługi MSMQ.  
  
 W tej sekcji możemy opisano sposób użycia <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> umieszczonych w kolejce komunikacji między (1) klienta WCF i usługa MSMQ aplikacji napisane przy użyciu usługi WCF i System.Messaging i (2) klienta aplikacji usługi MSMQ.  
  
 Dla kompletnego przykładu, który demonstruje sposób wywołania aplikacji odbiornika usługi MSMQ z klienta WCF, zobacz [Windows Communication Foundation, do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) próbki.  
  
 Na przykład pełną, który demonstruje sposób wywoływania usługi WCF w kliencie usługi MSMQ, zobacz [usługi kolejkowania komunikatów Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) próbki.  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>Aby utworzyć usługę WCF, która odbiera komunikaty z klienta usługi MSMQ  
  
1.  Zdefiniuj interfejs, który definiuje kontrakt usługi dla usługi WCF, służącą do odbierania wiadomości w kolejce z aplikacją usługi MSMQ nadawcy, jak pokazano w poniższym kodzie przykład.  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2.  Zaimplementuj interfejs i zastosować <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutu do klasy, jak pokazano w poniższym przykładzie kodzie.  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3.  Utwórz plik konfiguracji, który określa <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  
  
  
  
4.  Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> obiekt, który używa skonfigurowanego powiązania.  
  
  
  
### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>Aby utworzyć klienta WCF, który wysyła wiadomości do aplikacji odbiornika usługi MSMQ  
  
1.  Zdefiniuj interfejs, który definiuje kontrakt usługi dla klienta WCF wysyła wiadomości do odbiornika usługi MSMQ w kolejce, jak pokazano w poniższym przykładzie kodzie.  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2.  Zdefiniuj klasę klienta używany przez klienta WCF do wywoływania odbiornika usługi MSMQ.  
  
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
