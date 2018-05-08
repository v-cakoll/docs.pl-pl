---
title: Grupowanie komunikatów z obsługą kolejek w ramach sesji
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 62aa269d138d436824d3c825de9f722490d3b5bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="grouping-queued-messages-in-a-session"></a>Grupowanie komunikatów z obsługą kolejek w ramach sesji
Windows Communication Foundation (WCF) zapewnia sesji, która umożliwia grupowanie zestaw komunikatów powiązane ze sobą do przetworzenia przez aplikację odbierającą pojedynczego. Komunikaty, które są częścią sesji musi być częścią tej samej transakcji. Ponieważ wszystkie komunikaty są częścią tej samej transakcji, jeśli jeden komunikat nie można przetworzyć całej sesji została wycofana. Sesje mają podobne zachowania w odniesieniu do kolejki utraconych wiadomości i kolejki skażone. Czas wygaśnięcia (TTL) ustawiona w Zakolejkowane powiązanie skonfigurowane dla sesji jest stosowany do sesji jako całość. Jeśli tylko niektóre wiadomości w sesji są wysyłane przed wygaśnięciem czas TTL, całej sesji jest umieszczona w kolejce wiadomości utraconych. Podobnie gdy wiadomości w sesji nie mogą być wysyłane do aplikacji z kolejki aplikacji, całej sesji jest umieszczone w kolejce skażone (jeśli jest dostępna).  
  
## <a name="message-grouping-example"></a>Przykład grupowanie komunikatów  
 Przykładem, gdy grupowanie komunikatów jest pomocne jest podczas wdrażania aplikacji jako usługa WCF kolejności przetwarzania. Na przykład klient przesyła kolejności do tej aplikacji, która zawiera liczbę elementów. Dla każdego elementu klient nawiązuje połączenie z usługą, co prowadzi do osobnej wiadomości wysyłane. Istnieje możliwość A służą do odebrania pierwszego elementu i serwer B, aby otrzymywał drugiego elementu. Zawsze, gdy element zostanie dodany serwer przetwarzania elementu ma można znaleźć odpowiedniej kolejności i Dodaj element, który jest bardzo mało wydajne. Nadal uruchamiać się do takich wydajność z tylko jednym serwerem obsługi wszystkich żądań, ponieważ serwer musi śledzić wszystkie zamówienia aktualnie przetwarzane i określić, która z nich nowy element należy do. Grupowanie wszystkie żądania dotyczące pojedynczego zamówienia znacznie upraszcza implementacji takich aplikacji. Aplikacja kliencka wysyła wszystkie elementy dla pojedynczego zamówienia w sesji, więc usługa przetwarza kolejności, przetwarza jednocześnie całej sesji. \  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>Aby skonfigurować kontraktu usługi do użycia sesji  
  
1.  Definiowanie kontraktu usługi, która wymaga sesji. W tym z <xref:System.ServiceModel.OperationContractAttribute> atrybutu i określenie:  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2.  Oznacz operacji w umowie jako jednokierunkowe, ponieważ metody te nie mają żadnych czynności. Jest to zrobić za pomocą <xref:System.ServiceModel.OperationContractAttribute> atrybutu i określenie:  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3.  Implementowanie kontraktu usługi i określ `InstanceContextMode` z `PerSession`. Tworzy to wystąpienie usługi, tylko raz dla każdej sesji.  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4.  Każda operacja usługi wymaga transakcji. Określ ją z <xref:System.ServiceModel.OperationBehaviorAttribute> atrybutu. Operacja, która kończy transakcji należy również ustawić `TransactionAutoComplete` do `true`.  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5.  Konfigurowanie punktu końcowego, który używa dostarczane przez system `NetMsmqBinding` powiązania.  
  
6.  Tworzenie kolejki transakcyjnej przy użyciu <xref:System.Messaging>. Można również utworzyć kolejkę, za pomocą usługi kolejkowania komunikatów (MSMQ) lub programu MMC. Jeśli to zrobisz, Utwórz kolejkę transakcyjną.  
  
7.  Utwórz hosta usługi dla usługi przy użyciu <xref:System.ServiceModel.ServiceHost>.  
  
8.  Otworzyć hosta usługi, aby udostępnić usługę.  
  
9. Zamknij hosta usługi.  
  
#### <a name="to-set-up-a-client"></a>Aby skonfigurować klienta  
  
1.  Tworzenie zakresu transakcji do zapisu transakcyjne kolejki.  
  
2.  Tworzenie klienta WCF, za pomocą [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) narzędzia.  
  
3.  Umieść kolejności.  
  
4.  Zamknij klienta platformy WCF.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie przedstawiono kod `IProcessOrder` usługi i dla klienta, który korzysta z tej usługi. Pokazuje, jak WCF używa umieszczonych w kolejce sesji, aby zapewnić zachowanie grupowania.  
  
### <a name="code-for-the-service"></a>Kod usługi  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  
  
  
  
### <a name="code-for-the-client"></a>Kod dla klienta  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  
  
  
  
## <a name="see-also"></a>Zobacz też  
 [Sesje i kolejki](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)
