---
title: "Instrukcje: Wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF"
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
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4b52fe96bc88f09b807640dedcc54a8468dc26e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a>Instrukcje: Wymiana komunikatów znajdujących się w kolejce z punktami końcowymi WCF
Kolejki upewnij się, że niezawodna obsługa komunikatów może wystąpić między klientem a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi, nawet jeśli usługa nie jest dostępna w tym czasie komunikacji. Poniższe procedury pokazują, jak zapewnić niezawodna komunikacja między klientem a usługą przy użyciu standardu w kolejce powiązania podczas implementowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.  
  
 W tej sekcji opisano sposób korzystania <xref:System.ServiceModel.NetMsmqBinding> umieszczonych w kolejce komunikacji między [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.  
  
### <a name="to-use-queuing-in-a-wcf-service"></a>Aby użyć usługi kolejkowania wiadomości usługi WCF  
  
1.  Definiowanie kontraktu usługi przy użyciu interfejsu oznaczony atrybutem <xref:System.ServiceModel.ServiceContractAttribute>. Oznacz operacje w interfejsie, które są częścią kontraktu usługi o <xref:System.ServiceModel.OperationContractAttribute> i określ je jako jednokierunkowe, ponieważ żadna odpowiedź do metody. Następujący kod stanowi przykład kontrakt usługi i jego definicji operacji.  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  Gdy kontrakt usługi przekazuje typy danych zdefiniowane przez użytkownika, należy zdefiniować kontraktów danych dla tych typów. Poniższy kod przedstawia dwa kontrakty danych, `PurchaseOrder` i `PurchaseOrderLineItem`. Te dwa typy zdefiniować dane są przesyłane do usługi. (Należy pamiętać, klasy, które definiują tego kontraktu danych będzie także zdefiniować na wiele sposobów. Te metody nie są traktowane jako część kontraktu danych. Tylko te elementy członkowskie, które są zadeklarowane z `DataMember` atrybut jest częścią kontraktu danych.)  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  Implementuje metody zdefiniowane w interfejsie klasa kontraktu usługi.  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     Powiadomienie <xref:System.ServiceModel.OperationBehaviorAttribute> dotyczącymi `SubmitPurchaseOrder` metody. Określa, czy ta operacja musi zostać wywołana w transakcji i że transakcji automatycznie działanie jest kończone po zakończeniu metody.  
  
4.  Tworzenie kolejki transakcyjnej przy użyciu <xref:System.Messaging>. Można utworzyć kolejkę, zamiast niego Usługa kolejkowania wiadomości firmy Microsoft (MSMQ) programu Microsoft Management Console (MMC). Jeśli tak, upewnij się, że tworzenie kolejką transakcyjną.  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  Zdefiniuj <xref:System.ServiceModel.Description.ServiceEndpoint> w konfiguracji, który określa adres usługi i korzysta ze standardu <xref:System.ServiceModel.NetMsmqBinding> powiązania. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] konfiguracji, zobacz [Konfigurowanie aplikacji systemu Windows Communication Foundation](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a).  
  
  
  
6.  Utwórz hosta dla `OrderProcessing` usługi przy użyciu <xref:System.ServiceModel.ServiceHost> które odczytuje wiadomości z kolejki i przetwarza je. Otworzyć hosta usługi, aby udostępnić usługę. Wyświetla komunikat informujący o użytkownikowi naciśnij dowolny klawisz, aby zakończyć usługi. Wywołanie `ReadLine` oczekiwania klawisz, aby zostać naciśnięte, a następnie Zamknij usługę.  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a>Aby utworzyć klienta usługi kolejki  
  
1.  Poniższy przykład przedstawia sposób uruchomienia hostingu aplikacji i korzystać z narzędzia Svcutil.exe do utworzenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta.  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  Zdefiniuj <xref:System.ServiceModel.Description.ServiceEndpoint> w konfiguracji, który określa adres i korzysta ze standardu <xref:System.ServiceModel.NetMsmqBinding> powiązanie, jak pokazano w poniższym przykładzie.  
  
  
  
3.  Tworzenie zakresu transakcji można zapisać do kolejki transakcyjnej wywołania `SubmitPurchaseOrder` operacji, a następnie Zamknij [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, jak pokazano w poniższym przykładzie.  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach pokazano kod usługi hostingu aplikacji, plik App.config i zawarte w tym przykładzie kodu klienta.  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.NetMsmqBinding>  
 [Transakcyjne powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
 [Usługi kolejkowania wiadomości w programie WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Porady: wymiana komunikatów z punktami końcowymi WCF i aplikacji usługi kolejkowania komunikatów](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Windows Communication Foundation, do usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Instalowanie usługi kolejkowania komunikatów (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Przykłady powiązanie integracji usługi kolejkowania komunikatów](http://msdn.microsoft.com/en-us/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [Obsługa kolejek komunikatów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Zabezpieczenia komunikatów w ramach usługi kolejkowania komunikatów](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
