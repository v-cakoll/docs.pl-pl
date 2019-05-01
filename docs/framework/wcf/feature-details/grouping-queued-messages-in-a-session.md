---
title: Grupowanie komunikatów z obsługą kolejek w ramach sesji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 37f0874ea99ee928e49a54a3e6a05ea4ef06f84e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855923"
---
# <a name="grouping-queued-messages-in-a-session"></a>Grupowanie komunikatów z obsługą kolejek w ramach sesji
Windows Communication Foundation (WCF) zapewnia sesji, która pozwala grupować zestaw komunikatów powiązane ze sobą do przetworzenia przez aplikację odbierającą jednego. Komunikaty, które są częścią sesji musi być częścią tej samej transakcji. Ponieważ wszystkie komunikaty są częścią tej samej transakcji, jeśli jeden komunikat zakończy się niepowodzeniem do przetworzenia całej sesji jest wycofywana. Sesje mają podobne zachowanie w odniesieniu do kolejki utraconych wiadomości i skażone kolejki. Czas wygaśnięcia (TTL) ustawiona w Zakolejkowane powiązanie skonfigurowane dla sesji jest stosowana do sesji jako całości. Jeśli tylko część wiadomości w sesji są wysyłane przed wygaśnięcia, podczas całej sesji jest umieszczana w kolejce wiadomości utraconych. Podobnie po wiadomości w sesji nie można wysyłać do aplikacji z kolejki aplikacji, podczas całej sesji jest umieszczany w kolejce skażone (jeśli jest dostępny).  
  
## <a name="message-grouping-example"></a>Przykład grupowanie komunikatów  
 Przykładem, w których grupowanie komunikatów przydaje się to podczas wdrażania aplikacji przetwarzania zamówień jako usługa WCF. Na przykład klient składa zamówienie do tej aplikacji, która zawiera wiele elementów. Dla każdego elementu klient wysyła wywołania do usługi, co skutkuje osobnej wiadomości wysyłane. Jest możliwe, a będzie służył do odbierania pierwszego elementu a serwer B, aby otrzymywał drugiego elementu. Każdorazowo, gdy element zostanie dodany serwer przetwarzania tego elementu musi znaleźć właściwą kolejność i Dodaj element, który jest bardzo mało wydajne. Nadal występują takie czynniki za pomocą tylko obsługę wszystkich żądań, ponieważ serwer musi śledzić wszystkie zamówienia w danej chwili przetwarzany i określić, której nowy element należy do jednego serwera. Grupowanie wszystkie żądania dotyczące pojedynczego zamówienia znacznie upraszcza implementacji takich aplikacji. Aplikacja kliencka wysyła wszystkie elementy w jednym zamówienia w sesji, dzięki czemu usługa przetworzy to zamówienie, przetwarza jednocześnie całej sesji. \  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>Aby skonfigurować kontraktu usługi do użycia sesji  
  
1. Definiowanie kontraktu usługi, która wymaga sesji. W tym z <xref:System.ServiceModel.OperationContractAttribute> atrybutu i określenie:  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2. Oznacz operacji w umowie jako jednokierunkowe, ponieważ te metody nie zwraca niczego. Jest to zrobić za pomocą <xref:System.ServiceModel.OperationContractAttribute> atrybutu i określenie:  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. Implementowanie kontraktu usługi i określ `InstanceContextMode` z `PerSession`. Tworzy to wystąpienie usługi, tylko jeden raz dla każdej sesji.  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. Każda operacja usługi wymaga transakcji. Określ za pomocą <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu. Operacja, która kończy transakcji należy również ustawić `TransactionAutoComplete` do `true`.  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5. Konfigurowanie punktu końcowego, który używa dostarczane przez system `NetMsmqBinding` powiązania.  
  
6. Utwórz kolejkę transakcyjną za pomocą <xref:System.Messaging>. Można również utworzyć kolejkę przy użyciu usługi kolejkowania komunikatów (MSMQ) lub programu MMC. Jeśli to zrobisz, Utwórz kolejkę transakcyjną.  
  
7. Tworzenie usługi hosta usługi przy użyciu <xref:System.ServiceModel.ServiceHost>.  
  
8. Otwórz hosta usługi, aby udostępnić usługę.  
  
9. Zamknij hosta usługi.  
  
#### <a name="to-set-up-a-client"></a>Aby skonfigurować klienta  
  
1. Tworzenie zakresu transakcji do zapisu do kolejki transakcyjne.  
  
2. Tworzenie klienta WCF, używając [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia.  
  
3. Złóż zamówienie.  
  
4. Zamknij klienta platformy WCF.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono kod używany w `IProcessOrder` usługi i dla klienta, który korzysta z tej usługi. Pokazuje, jak WCF używa sesji w kolejce, aby zapewnić zachowanie grupowania.  
  
### <a name="code-for-the-service"></a>Kod usługi  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a>Kod klienta  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a>Zobacz także

- [Sesje i kolejki](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)
