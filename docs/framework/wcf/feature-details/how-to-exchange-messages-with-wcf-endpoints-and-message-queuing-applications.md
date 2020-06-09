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
# <a name="how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications"></a>Instrukcje: Wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów
Istniejące aplikacje usługi kolejkowania komunikatów (MSMQ) można zintegrować z aplikacjami Windows Communication Foundation (WCF) przy użyciu powiązania integracji usługi MSMQ w celu konwertowania komunikatów usługi MSMQ do i z komunikatów WCF. Pozwala to na wywoływanie aplikacji odbiornika usługi MSMQ z klientów WCF, a także wywoływanie usług WCF z aplikacji nadawcy usługi MSMQ.  
  
 W tej sekcji wyjaśniono, jak używać funkcji <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> komunikacji w kolejce między (1) klientem programu WCF i usługą aplikacji MSMQ zapisaną przy użyciu funkcji system. Messaging i (2) klienta aplikacji usługi MSMQ i usługi WCF.  
  
 Aby zapoznać się z kompletnym przykładem, który pokazuje, jak wywołać aplikację odbiornika usługi MSMQ z poziomu klienta WCF, zobacz [Windows Communication Foundation do usługi kolejkowania komunikatów](../samples/wcf-to-message-queuing.md) .  
  
 Aby zapoznać się z kompletnym przykładem, który ilustruje sposób wywoływania usługi WCF z poziomu klienta usługi MSMQ, zobacz [Usługa kolejkowania komunikatów do Windows Communication Foundation](../samples/message-queuing-to-wcf.md) przykład.  
  
### <a name="to-create-a-wcf-service-that-receives-messages-from-a-msmq-client"></a>Aby utworzyć usługę WCF, która odbiera komunikaty z klienta MSMQ  
  
1. Zdefiniuj interfejs, który definiuje kontrakt usługi dla usługi WCF, który odbiera kolejkowane komunikaty z aplikacji nadawcy usługi MSMQ, jak pokazano w poniższym przykładowym kodzie.  
  
     [!code-csharp[S_MsmqToWcf#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#1)]
     [!code-vb[S_MsmqToWcf#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#1)]  
  
2. Zaimplementuj interfejs i Zastosuj <xref:System.ServiceModel.ServiceBehaviorAttribute> atrybut do klasy, jak pokazano w poniższym przykładowym kodzie.  
  
     [!code-csharp[S_MsmqToWcf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmqtowcf/cs/service.cs#2)]
     [!code-vb[S_MsmqToWcf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmqtowcf/vb/service.vb#2)]  
  
3. Utwórz plik konfiguracji, który określa <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> .  

4. Utwórz wystąpienie <xref:System.ServiceModel.ServiceHost> obiektu, który używa skonfigurowanego powiązania.  

### <a name="to-create-a-wcf-client-that-sends-messages-to-a-msmq-receiver-application"></a>Aby utworzyć klienta WCF, który wysyła komunikaty do aplikacji odbiornika usługi MSMQ  
  
1. Zdefiniuj interfejs, który definiuje kontrakt usługi dla klienta WCF, który wysyła wiadomości w kolejce do odbiornika MSMQ, jak pokazano w poniższym przykładowym kodzie.  
  
     [!code-csharp[S_WcfToMsmq#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/proxy.cs#6)]
     [!code-vb[S_WcfToMsmq#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/proxy.vb#6)]  
  
2. Zdefiniuj klasę klienta używaną przez klienta WCF do wywoływania odbiorcy usługi MSMQ.  
  
     [!code-csharp[S_WcfToMsmq#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#2)]
     [!code-vb[S_WcfToMsmq#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#2)]  
  
3. Utwórz konfigurację, która określa użycie powiązania MsmqIntegrationBinding.  
  
     [!code-csharp[S_WcfToMsmq#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/snippets.cs#3)]
     [!code-vb[S_WcfToMsmq#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_wcftomsmq/vb/snippets.vb#3)]  
  
4. Utwórz wystąpienie klasy Client i Wywołaj metodę zdefiniowaną przez usługę otrzymywania wiadomości.  
  
     [!code-csharp[S_WcfToMsmq#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_wcftomsmq/cs/client.cs#4)]  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie kolejek](queues-overview.md)
- [Instrukcje: wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF](how-to-exchange-queued-messages-with-wcf-endpoints.md)
- [Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów](../samples/wcf-to-message-queuing.md)
- [Instalowanie usługi kolejkowania komunikatów (MSMQ)](../samples/installing-message-queuing-msmq.md)
- [Obsługa kolejek komunikatów programu Windows Communication Foundation](../samples/message-queuing-to-wcf.md)
- [Zabezpieczenia komunikatów w ramach kolejkowania komunikatów](../samples/message-security-over-message-queuing.md)
