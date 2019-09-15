---
title: 'Instrukcje: wymiana zakolejkowanych komunikatów z punktami końcowymi WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: 09b21c9483b4f2716409b560dbbb478fe5a6badd
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972221"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a>Instrukcje: wymiana zakolejkowanych komunikatów z punktami końcowymi WCF
Kolejki zapewniają niezawodne komunikaty między klientem a usługą Windows Communication Foundation (WCF), nawet jeśli usługa nie jest dostępna w chwili komunikacji. Poniższe procedury przedstawiają sposób zapewnienia trwałej komunikacji między klientem a usługą przy użyciu standardowego powiązania kolejkowanego w kolejce podczas implementowania usługi WCF.  
  
 W tej sekcji wyjaśniono, <xref:System.ServiceModel.NetMsmqBinding> jak używać w kolejce komunikacji między klientem programu WCF a usługą WCF.  
  
### <a name="to-use-queuing-in-a-wcf-service"></a>Aby użyć kolejkowania w usłudze WCF  
  
1. Zdefiniuj kontrakt usługi przy użyciu interfejsu oznaczonego za <xref:System.ServiceModel.ServiceContractAttribute>pomocą. Oznacz operacje w interfejsie, który jest częścią kontraktu usługi z <xref:System.ServiceModel.OperationContractAttribute> i określ je jako jednokierunkowe, ponieważ nie jest zwracana żadna odpowiedź na metodę. Poniższy kod zawiera przykładowy kontrakt usługi i jego definicję operacji.  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2. Gdy kontrakt usługi przekazuje typy zdefiniowane przez użytkownika, należy zdefiniować Kontrakty danych dla tych typów. Poniższy kod przedstawia dwa kontrakty `PurchaseOrder` danych i. `PurchaseOrderLineItem` Te dwa typy definiują dane, które są wysyłane do usługi. (Należy zauważyć, że klasy, które definiują ten kontrakt danych, również definiują wiele metod. Te metody nie są uważane za część kontraktu danych. Tylko te elementy członkowskie, które są zadeklarowane z <xref:System.Runtime.Serialization.DataMemberAttribute> atrybutem, są częścią kontraktu danych.  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3. Zaimplementuj metody kontraktu usług zdefiniowanego w interfejsie w klasie.  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     Zwróć uwagę na `SubmitPurchaseOrder`umieszczeniemetody . <xref:System.ServiceModel.OperationBehaviorAttribute> Oznacza to, że ta operacja musi zostać wywołana w ramach transakcji i że transakcja zostanie automatycznie zakończona po zakończeniu metody.  
  
4. Utwórz kolejkę transakcyjną <xref:System.Messaging>przy użyciu. Zamiast tego można utworzyć kolejkę za pomocą programu Microsoft Management Console (MMC). Jeśli tak, upewnij się, że tworzysz kolejkę transakcyjną.  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5. Zdefiniuj w konfiguracji, która określa adres usługi i używa standardowego <xref:System.ServiceModel.NetMsmqBinding> powiązania. <xref:System.ServiceModel.Description.ServiceEndpoint> Aby uzyskać więcej informacji o korzystaniu z konfiguracji WCF, zobacz [Konfigurowanie usług WCF](../configuring-services.md).  

6. Utwórz hosta dla `OrderProcessing` usługi korzystającej z <xref:System.ServiceModel.ServiceHost> programu, która odczytuje komunikaty z kolejki i przetwarza je. Otwórz hosta usługi, aby udostępnić usługę. Wyświetl komunikat informujący użytkownika o naciśnięciu dowolnego klawisza w celu zakończenia usługi. Wywołaj `ReadLine` , aby poczekać na naciśnięcie klawisza, a następnie zamknij usługę.  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a>Aby utworzyć klienta dla usługi w kolejce  
  
1. Poniższy przykład pokazuje, jak uruchomić aplikację hostingu i użyć narzędzia Svcutil. exe, aby utworzyć klienta WCF.  
  
    ```console
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2. Zdefiniuj w konfiguracji, która określa adres i używa standardowego <xref:System.ServiceModel.NetMsmqBinding> powiązania, jak pokazano w poniższym przykładzie. <xref:System.ServiceModel.Description.ServiceEndpoint>  

3. Utwórz zakres transakcji do zapisu w kolejce transakcyjnej, wywołaj `SubmitPurchaseOrder` operację i Zamknij klienta WCF, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a>Przykład  
 Poniższe przykłady przedstawiają kod usługi, aplikację hostingu, plik App. config oraz kod klienta uwzględniony w tym przykładzie.  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  

 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  

## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.NetMsmqBinding>
- [Transakcyjne powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)
- [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Instrukcje: Wymiana komunikatów z punktami końcowymi WCF i aplikacjami usługi kolejkowania komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [Instalowanie usługi kolejkowania komunikatów (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [Obsługa kolejek komunikatów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [Zabezpieczenia komunikatów w ramach kolejkowania komunikatów](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
