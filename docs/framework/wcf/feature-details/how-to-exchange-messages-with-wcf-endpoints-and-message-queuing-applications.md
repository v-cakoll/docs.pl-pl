---
title: 'Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62210fd8-a372-4d55-ab9b-c99827d1885e
ms.openlocfilehash: 7463f9cfc37c2bf4f271f6e59896a7d77f3f65cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772947"
---
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów
Istniejące aplikacje usługi kolejkowania komunikatów (MSMQ) można zintegrować z aplikacjami Windows Communication Foundation (WCF), przy użyciu powiązanie integracji usługi MSMQ na Konwertowanie wiadomości usługi MSMQ komunikatów WCF. Dzięki temu można wywoływać z aplikacji odbiornika usługi MSMQ z klientów programu WCF, a także wywoływać usługi WCF z usługi MSMQ nadawcy aplikacji.  
  
 W tej sekcji, firma Microsoft wyjaśniają jak używać <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> umieszczonych w kolejce komunikacji między (1) klienta WCF, jak i usługi aplikacji MSMQ napisane przy użyciu System.Messaging i (2) klienta aplikacji usługi MSMQ i usługi WCF.  
  
 Aby uzyskać pełny przykład pokazuje sposób wywołania aplikacji odbiornika usługi MSMQ z klienta programu WCF, zobacz [Windows Communication Foundation do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) próbki.  
  
 Aby uzyskać pełny przykład pokazuje sposób wywołania usługi WCF w kliencie usługi MSMQ, zobacz [usługi kolejkowania komunikatów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) próbki.  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>Aby utworzyć usługę WCF, która odbiera komunikaty z klienta usługi MSMQ  
  
1. Zdefiniuj interfejs, który definiuje kontrakt usługi dla usługi WCF, która odbiera komunikaty w kolejce z usługi MSMQ aplikacji nadawcy, jak pokazano w poniższym przykładowym kodzie.  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. Zaimplementuj interfejs i zastosować <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybutów do klasy, jak pokazano w poniższym przykładowym kodzie.  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. Utwórz plik konfiguracji, który określa <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.  

4. Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> obiektu, który używa skonfigurowanego powiązania.  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>Aby utworzyć klienta WCF, która wysyła komunikaty do aplikacji odbiornika usługi MSMQ  
  
1. Zdefiniuj interfejs, który definiuje kontrakt usługi dla klienta WCF, wysyła wiadomości, do odbiorcy usługi MSMQ w kolejce, jak pokazano w poniższym przykładowym kodzie.  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. Zdefiniuj klasę klienta używanego przez klienta programu WCF do wywoływania odbiornika usługi MSMQ.  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. Utwórz konfigurację, która określa użycie powiązania MsmqIntegrationBinding.  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. Utwórz wystąpienie klasy klienta i wywołanie metody zdefiniowane za pomocą wiadomości Odbieranie usługi.  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Instrukcje: Wymiana zakolejkowanych komunikatów z punktami końcowymi programu WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [Instalowanie usługi kolejkowania komunikatów (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [Obsługa kolejek komunikatów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [Zabezpieczenia komunikatów w ramach kolejkowania komunikatów](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
