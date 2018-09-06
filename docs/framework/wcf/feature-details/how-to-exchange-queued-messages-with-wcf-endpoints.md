---
title: 'Instrukcje: Wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: 185bcb64522115d0c60ae90ee22a73610139c8c3
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865598"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a>Instrukcje: Wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF
Kolejki upewnij się, że niezawodna obsługa komunikatów może wystąpić między klientem a usługą Windows Communication Foundation (WCF), nawet jeśli usługa nie jest dostępna w czasie komunikacji. Poniższe procedury pokazują, jak zapewnić niezawodne komunikacji między klientem a usługą przy użyciu standardu w kolejce wiążące podczas implementowania usługi WCF.  
  
 W tej sekcji wyjaśniono, jak używać <xref:System.ServiceModel.NetMsmqBinding> umieszczonych w kolejce komunikacji między klienta programu WCF i usługi WCF.  
  
### <a name="to-use-queuing-in-a-wcf-service"></a>Aby użyć usługi kolejkowania wiadomości w usłudze WCF  
  
1.  Definiowanie kontraktu usługi przy użyciu interfejsu oznaczone <xref:System.ServiceModel.ServiceContractAttribute>. Oznacz operacji w interfejsie, które są częścią kontraktu usługi o <xref:System.ServiceModel.OperationContractAttribute> i określ je jako jednokierunkowe, ponieważ zwracany jest brak odpowiedzi do metody. Poniższy kod stanowi przykład kontrakt usługi i jego definicję operacji.  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  Gdy kontrakt usługi przekazuje typy zdefiniowane przez użytkownika, należy zdefiniować kontraktów danych do tych typów. W poniższym kodzie pokazano dwa kontraktów danych `PurchaseOrder` i `PurchaseOrderLineItem`. Tych dwóch typów zdefiniować dane, które są wysyłane do usługi. (Zwróć uwagę, że klasy, które definiują ten kontrakt danych również zdefiniować na wiele sposobów. Te metody nie są uważane za część kontraktu danych. Tylko te elementy członkowskie, które są zadeklarowane za pomocą `DataMember` atrybutu są częścią kontraktu danych.)  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  Implementuje metody zdefiniowane w interfejsie w klasie kontraktu usługi.  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     Zwróć uwagę <xref:System.ServiceModel.OperationBehaviorAttribute> umieszczone na `SubmitPurchaseOrder` metody. Określa, że ta operacja musi zostać wywołana w transakcji i że transakcja automatycznie kończy się po zakończeniu działania metody.  
  
4.  Utwórz kolejkę transakcyjną za pomocą <xref:System.Messaging>. Można utworzyć kolejkę, zamiast Microsoft usługi kolejkowania komunikatów (MSMQ) programu Microsoft Management Console (MMC). Jeśli tak, upewnij się, że można utworzyć kolejkę transakcyjną.  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  Zdefiniuj <xref:System.ServiceModel.Description.ServiceEndpoint> w konfiguracji, który określa adres usługi i używa standardu <xref:System.ServiceModel.NetMsmqBinding> powiązania. Aby uzyskać więcej informacji na temat korzystania z konfiguracji usługi WCF, zobacz [Konfigurowanie aplikacji systemu Windows Communication Foundation](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).  
  
  
  
6.  Tworzenie hosta dla `OrderProcessing` usługi przy użyciu <xref:System.ServiceModel.ServiceHost> która odczytuje komunikaty z kolejki i przetwarza je. Otwórz hosta usługi, aby udostępnić usługę. Wyświetlenie komunikatu, informujący użytkownika, naciśnij dowolny klawisz, aby zakończyć usługi. Wywołaj `ReadLine` oczekiwania klawisz, aby zostać naciśnięte, a następnie Zamknij usługę.  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a>Można utworzyć klienta dla usługi w kolejce  
  
1.  Poniższy przykład pokazuje, jak do uruchamiania aplikacji macierzystej, a za pomocą narzędzia Svcutil.exe, aby utworzyć klienta WCF.  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  Zdefiniuj <xref:System.ServiceModel.Description.ServiceEndpoint> w konfiguracji, który określa adres i używa standardowych <xref:System.ServiceModel.NetMsmqBinding> powiązania, jak pokazano w poniższym przykładzie.  
  
  
  
3.  Tworzenie zakresu transakcji do zapisu do kolejki transakcyjne, wywołanie `SubmitPurchaseOrder` operacji, a następnie Zamknij klienta WCF, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano kod usługi, aplikacji macierzystej, plik App.config i kod klienta zawarte w tym przykładzie.  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.NetMsmqBinding>  
 [Transakcyjne powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
 [Tworzenie kolejek w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Instrukcje: wymiana komunikatów z punktami końcowymi programu WCF i aplikacjami do obsługi kolejek komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Wysyłanie komunikatów z usługi WCF do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Instalowanie usługi kolejkowania komunikatów (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Przykłady powiązania Integracja usługi kolejkowania komunikatów](https://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [Obsługa kolejek komunikatów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Zabezpieczenia komunikatów w ramach kolejkowania komunikatów](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
