---
title: Grupowanie komunikatów z obsługą kolejek w ramach sesji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 995697e618ff5d56a719efc5d69b97583733d980
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70892740"
---
# <a name="grouping-queued-messages-in-a-session"></a>Grupowanie komunikatów z obsługą kolejek w ramach sesji
Windows Communication Foundation (WCF) to sesja, która umożliwia grupowanie zestawu powiązanych komunikatów w celu przetworzenia przez pojedynczą aplikację otrzymującą. Komunikaty, które są częścią sesji, muszą być częścią tej samej transakcji. Ponieważ wszystkie komunikaty są częścią tej samej transakcji, jeśli nie można przetworzyć jednego komunikatu, cała sesja jest wycofywana. Sesje mają podobne zachowania w odniesieniu do nieutraconych kolejek i trujących kolejek. Właściwość Time to Live (TTL) ustawiona w powiązaniu w kolejce skonfigurowanym dla sesji jest stosowana do sesji jako całości. Jeśli tylko niektóre komunikaty w sesji są wysyłane przed upływem czasu wygaśnięcia, cała sesja zostanie umieszczona w kolejce utraconych wiadomości. Podobnie w przypadku niepowodzenia wysyłania komunikatów w sesji do aplikacji z kolejki aplikacji cała sesja zostanie umieszczona w kolejce trującej (jeśli jest dostępna).  
  
## <a name="message-grouping-example"></a>Przykład grupowania komunikatów  
 Przykładem, gdy pomocne jest grupowanie komunikatów, jest zaimplementowanie aplikacji do przetwarzania zamówień jako usługi WCF. Na przykład klient przesyła do tej aplikacji zamówienie, które zawiera kilka elementów. Dla każdego elementu klient wykonuje wywołanie do usługi, co spowoduje wysłanie osobnej wiadomości. Jest możliwe, aby program mógł otrzymać pierwszy element, a serwer B odbierze drugi element. Za każdym razem, gdy element jest dodawany, serwer przetwarzania tego elementu musi znaleźć odpowiednie zamówienie i dodać do niego element, który jest wysoce nieefektywny. W dalszym ciągu można pracować w taki sposób, że tylko jeden serwer obsługuje wszystkie żądania, ponieważ serwer musi śledzić wszystkie aktualnie przetwarzane zamówienia i określić, do którego, do którego należy nowy element. Grupowanie wszystkich żądań dla pojedynczego zamówienia znacznie upraszcza implementację takiej aplikacji. Aplikacja kliencka wysyła wszystkie elementy z pojedynczej kolejności w sesji, więc gdy usługa przetwarza kolejność, przetwarza całą sesję jednocześnie. \  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>Aby skonfigurować kontrakt usługi do korzystania z sesji  
  
1. Zdefiniuj kontrakt usługi wymagający sesji. Zrób to z <xref:System.ServiceModel.ServiceContractAttribute> atrybutem, określając:  
  
    ```csharp
    SessionMode=SessionMode.Required  
    ```  
  
2. Oznacz operacje w kontrakcie jako jednokierunkowe, ponieważ te metody nie zwracają żadnych elementów. Jest to wykonywane z <xref:System.ServiceModel.OperationContractAttribute> atrybutem, określając:  
  
    ```csharp  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. Zaimplementuj kontrakt usługi i określ <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode>. <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType> Spowoduje to utworzenie wystąpienia usługi tylko raz dla każdej sesji.  
  
    ```csharp  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. Każda operacja usługi wymaga transakcji. Określ ten <xref:System.ServiceModel.OperationBehaviorAttribute> atrybut. Operacja, która kończy transakcję, powinna również <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> mieć `true`ustawioną wartość.  
  
    ```csharp  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5. Skonfiguruj punkt końcowy, który używa powiązania dostarczonego `NetMsmqBinding` przez system.  
  
6. Utwórz kolejkę transakcyjną <xref:System.Messaging>przy użyciu. Możesz również utworzyć kolejkę za pomocą usługi kolejkowania komunikatów (MSMQ) lub MMC. W takim przypadku należy utworzyć kolejkę transakcyjną.  
  
7. Utwórz hosta usługi dla usługi przy użyciu programu <xref:System.ServiceModel.ServiceHost>.  
  
8. Otwórz hosta usługi, aby udostępnić usługę.  
  
9. Zamknij hosta usługi.  
  
#### <a name="to-set-up-a-client"></a>Aby skonfigurować klienta  
  
1. Utwórz zakres transakcji do zapisu w kolejce transakcyjnej.  
  
2. Utwórz klienta WCF za pomocą narzędzia [Svcutil. exe (narzędzie do przesyłania metadanych)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) .  
  
3. Złóż zamówienie.  
  
4. Zamknij klienta WCF.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład zawiera kod dla `IProcessOrder` usługi i klienta programu korzystającego z tej usługi. Pokazuje, w jaki sposób WCF używa kolejkowane sesje, aby zapewnić zachowanie grupowania.  
  
### <a name="code-for-the-service"></a>Kod usługi  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a>Kod dla klienta  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a>Zobacz także

- [Sesje i kolejki](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)
