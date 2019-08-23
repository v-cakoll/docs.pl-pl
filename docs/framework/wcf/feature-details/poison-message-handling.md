---
title: Obsługa komunikatów zanieczyszczonych
ms.date: 03/30/2017
ms.assetid: 8d1c5e5a-7928-4a80-95ed-d8da211b8595
ms.openlocfilehash: 4813629f5ceec1c1b50dfcebe901f4bc25392ec7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909843"
---
# <a name="poison-message-handling"></a>Obsługa komunikatów zanieczyszczonych
*Trująca wiadomość* jest komunikatem, który przekroczył maksymalną liczbę prób dostarczenia do aplikacji. Taka sytuacja może wystąpić, gdy aplikacja oparta na kolejce nie może przetworzyć komunikatu z powodu błędów. Aby spełnić wymagania dotyczące niezawodności, aplikacja umieszczona w kolejce odbiera komunikaty w ramach transakcji. Przerwanie transakcji, w której otrzymano komunikat w kolejce, pozostawia komunikat w kolejce, aby komunikat został ponowiony w ramach nowej transakcji. Jeśli problem, który spowodował przerwanie transakcji, nie zostanie poprawiony, aplikacja otrzymująca może zostać zablokowana w pętli, która odbiera i przerywa ten sam komunikat do momentu przekroczenia maksymalnej liczby prób dostarczenia i zatrucia wyników komunikatów.  
  
 Komunikat może być skażony z wielu powodów. Najczęstszymi przyczynami są specyficzne dla aplikacji. Na przykład, jeśli aplikacja odczytuje komunikat z kolejki i wykonuje przetwarzanie bazy danych, aplikacja może nie można uzyskać blokady bazy danych, powodując przerwanie transakcji. Ponieważ transakcja bazy danych została przerwana, komunikat pozostaje w kolejce, co powoduje, że aplikacja może ponownie odczytać komunikat po raz drugi i podjąć kolejną próbę uzyskania blokady bazy danych. Komunikaty mogą również stać się trujące, jeśli zawierają nieprawidłowe informacje. Na przykład zamówienie zakupu może zawierać nieprawidłowy numer klienta. W takich przypadkach aplikacja może dobrowolnie przerwać transakcję i wymusić, aby komunikat stał się skażonym komunikatem.  
  
 W rzadkich przypadkach komunikaty mogą nie być wysyłane do aplikacji. Warstwa Windows Communication Foundation (WCF) może znaleźć problem z komunikatem, na przykład jeśli komunikat ma złą ramkę, dołączono do niego nieprawidłowe poświadczenia wiadomości lub nieprawidłowy nagłówek akcji. W takich przypadkach aplikacja nigdy nie otrzymuje komunikatu; Jednak komunikat nadal może stać się skażony i być przetwarzany ręcznie.  
  
## <a name="handling-poison-messages"></a>Obsługa skażonych komunikatów  
 W programie WCF Obsługa skażonych komunikatów zapewnia mechanizm do otrzymywania aplikacji, które nie mogą zostać wysłane do aplikacji ani komunikatów wysyłanych do aplikacji, ale których nie można przetworzyć ze względu na specyficzne dla aplikacji powodów. Obsługa skażonych komunikatów jest konfigurowana przez następujące właściwości w każdym z dostępnych w kolejce powiązań:  
  
- `ReceiveRetryCount`. Wartość całkowita wskazująca maksymalną liczbę ponownych prób dostarczenia komunikatu z kolejki aplikacji do aplikacji. Wartość domyślna to 5. Jest to wystarczające w przypadkach, gdy natychmiastowa ponowna próba rozwiązuje problem, na przykład przez tymczasowe zakleszczenie w bazie danych.  
  
- `MaxRetryCycles`. Wartość całkowita, która wskazuje maksymalną liczbę ponownych prób. Cykl ponowień polega na przesłaniu komunikatu z kolejki aplikacji do podrzędnej kolejki ponownych prób i po skonfigurowaniu opóźnienia z powrotem z kolejki ponownych prób w kolejce aplikacji w celu ponowienia próby dostarczenia. Wartość domyślna to 2. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], komunikat próbuje maksymalnie (`ReceiveRetryCount` + 1) * (`MaxRetryCycles` + 1) razy. `MaxRetryCycles`jest ignorowany [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] w [!INCLUDE[wxp](../../../../includes/wxp-md.md)]systemach i.  
  
- `RetryCycleDelay`. Opóźnienie między cyklami ponawiania prób. Wartość domyślna to 30 minut. `MaxRetryCycles`i `RetryCycleDelay` razem zapewniają mechanizm rozwiązywania problemu, gdy ponowna próba po okresowym opóźnieniu rozwiązuje problem. Na przykład obsługuje zablokowany zestaw wierszy w SQL Server oczekujące zatwierdzenie transakcji.  
  
- `ReceiveErrorHandling`. Wyliczenie, które wskazuje akcję, która ma zostać podjęta dla komunikatu o niepomyślnym dostarczeniu po próbie przeprowadzenia maksymalnej liczby ponownych prób. Wartości mogą być błędne, porzucane, odrzucane i przenoszone. Opcja domyślna to Fault.  
  
- Fault. Ta opcja wysyła błąd do odbiornika, który spowodował `ServiceHost` błąd. Komunikat musi zostać usunięty z kolejki aplikacji przez pewien mechanizm zewnętrzny, aby aplikacja mogła kontynuować przetwarzanie komunikatów z kolejki.  
  
- Listy rozwijanej. Ta opcja powoduje odrzucanie skażonych komunikatów, a komunikat nigdy nie jest dostarczany do aplikacji. Jeśli w tym momencie `TimeToLive` Właściwość komunikatu wygasła, komunikat może się pojawić w kolejce utraconych wiadomości nadawcy. Jeśli nie, komunikat nie pojawia się w dowolnym miejscu. Ta opcja oznacza, że użytkownik nie określił czynności, które należy wykonać, jeśli komunikat zostanie utracony.  
  
- Oznacza. Ta opcja jest dostępna tylko w [!INCLUDE[wv](../../../../includes/wv-md.md)]systemie. Powoduje to zainstruujenie usługi kolejkowania komunikatów (MSMQ) w celu wysłania negatywnego potwierdzenia z powrotem do Menedżera kolejki wysyłania, którego aplikacja nie może odebrać komunikatu. Wiadomość zostanie umieszczona w kolejce utraconych wiadomości Menedżera kolejki wysyłania.  
  
- Przenieś. Ta opcja jest dostępna tylko w [!INCLUDE[wv](../../../../includes/wv-md.md)]systemie. Spowoduje to przeniesienie skażonego komunikatu do kolejki komunikatów trujących w celu późniejszego przetworzenia przez aplikację skażoną komunikatów. "Trująca-komunikat" jest podkolejką kolejki aplikacji. Aplikacja do obsługi komunikatów trujących może być usługą WCF, która odczytuje komunikaty z kolejki trującej. Kolejka Trująca jest podkolejką kolejki aplikacji i może być rozkierowane jako net. MSMQ://\<*Machine-Name*>/*applicationQueue*;p Oison, gdzie *Machine-Name* to nazwa komputera, na którym Kolejka znajduje się i *applicationQueue* jest nazwą kolejki specyficznej dla aplikacji.  
  
 Poniżej przedstawiono maksymalną liczbę prób dostarczenia komunikatu:  
  
- ((ReceiveRetryCount + 1) * (MaxRetryCycles + 1)) w [!INCLUDE[wv](../../../../includes/wv-md.md)]systemie.  
  
- (ReceiveRetryCount + 1) w [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] systemach [!INCLUDE[wxp](../../../../includes/wxp-md.md)]i.  
  
> [!NOTE]
> Nie wykonano żadnych ponownych prób dla wiadomości, która została dostarczona pomyślnie.  
  
 Aby śledzić liczbę prób odczytu komunikatu, [!INCLUDE[wv](../../../../includes/wv-md.md)] utrzymuje trwałą Właściwość komunikatu, która zlicza liczbę przerwań i Właściwość liczby przeniesień, która zlicza, ile razy komunikat przechodzi między kolejką aplikacji a podkolejki. Kanał WCF używa tych funkcji do obliczenia liczby ponowień odbioru i liczby ponownych prób. W [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] systemach [!INCLUDE[wxp](../../../../includes/wxp-md.md)]i liczba przerwań jest zachowywana w pamięci przez kanał WCF i jest resetowana w przypadku niepowodzenia aplikacji. Ponadto kanał WCF może w dowolnym momencie przechowywać liczbę przerwań dla maksymalnie 256 komunikatów w pamięci. Jeśli zostanie odczytany komunikat 257th, licznik przerwań najstarszej wiadomości zostanie zresetowany.  
  
 Właściwości liczba przerwań i liczba operacji przenoszenia są dostępne dla operacji usługi za pomocą kontekstu operacji. Poniższy przykład kodu pokazuje, jak uzyskać do nich dostęp.  
  
 [!code-csharp[S_UE_MSMQ_Poison#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/service.cs#1)]  
  
 Funkcja WCF oferuje dwa standardowe powiązania kolejkowane:  
  
- <xref:System.ServiceModel.NetMsmqBinding>. Powiązanie .NET Framework odpowiednie do wykonywania komunikacji opartej na kolejce z innymi punktami końcowymi WCF.  
  
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Powiązanie odpowiednie do komunikacji z istniejącymi aplikacjami usługi kolejkowania komunikatów.  
  
> [!NOTE]
> Można zmienić właściwości w tych powiązaniach na podstawie wymagań usługi WCF. Cały mechanizm obsługi skażonych komunikatów jest lokalny dla aplikacji odbiorczej. Ten proces jest niewidoczny dla aplikacji wysyłającej, chyba że aplikacja otrzymująca ostatecznie zatrzyma się i wyśle negatywną potwierdzenie z powrotem do nadawcy. W takim przypadku wiadomość zostanie przeniesiona do kolejki utraconych wiadomości nadawcy.  
  
## <a name="best-practice-handling-msmqpoisonmessageexception"></a>Najlepsze rozwiązanie: Obsługa MsmqPoisonMessageException —  
 Gdy usługa określa, że komunikat jest trująca, transport umieszczony w kolejce zgłasza <xref:System.ServiceModel.MsmqPoisonMessageException> , że `LookupId` zawiera komunikat trujący.  
  
 Aplikacja do odbioru może zaimplementować <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejs w celu obsługi wszystkich błędów wymaganych przez aplikację. Aby uzyskać więcej informacji, zobacz [Rozszerzanie kontroli nad obsługą błędów i raportowaniem](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md).  
  
 Aplikacja może wymagać pewnego rodzaju automatycznej obsługi skażonych komunikatów, które przenosi trujące komunikaty do kolejki komunikatów trujących, aby usługa mogła uzyskać dostęp do pozostałych komunikatów w kolejce. Jedynym scenariuszem używania mechanizmu obsługi błędów do nasłuchiwania wyjątków komunikatów trujących jest <xref:System.ServiceModel.Configuration.MsmqBindingElementBase.ReceiveErrorHandling%2A> ustawienie <xref:System.ServiceModel.ReceiveErrorHandling.Fault>wartość. Przykładowy komunikat zatrucia dla usługi kolejkowania komunikatów 3,0 pokazuje to zachowanie. Poniżej przedstawiono kroki, które należy wykonać, aby obsłużyć trujące komunikaty, w tym najlepsze rozwiązania:  
  
1. Upewnij się, że ustawienia trujące odzwierciedlają wymagania aplikacji. Podczas pracy z ustawieniami upewnij się, że rozumiesz różnice między możliwościami usługi kolejkowania komunikatów w systemach [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
2. W razie potrzeby Zaimplementuj `IErrorHandler` , aby obsługiwać błędy trujących komunikatów. Ponieważ ustawienie `ReceiveErrorHandling` `IErrorHandler` `ReceiveErrorHandling` `Fault`wymaga ręcznego mechanizmu przenoszenia skażonego komunikatu z kolejki lub do skorygowania zewnętrznego problemu zależnego, typowym użyciem jest zaimplementowanie, gdy jest ustawione na, jako `Fault` pokazano w poniższym kodzie.  
  
     [!code-csharp[S_UE_MSMQ_Poison#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonerrorhandler.cs#2)]  
  
3. `PoisonBehaviorAttribute` Utwórz, że można użyć zachowania usługi. Zachowanie instaluje `IErrorHandler` w dyspozytorze. Zobacz Poniższy przykład kodu.  
  
     [!code-csharp[S_UE_MSMQ_Poison#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonbehaviorattribute.cs#3)]  
  
4. Upewnij się, że Twoja usługa ma adnotację z atrybutem zachowania trujące.  

 Ponadto, jeśli `ReceiveErrorHandling` jest ustawiona na `Fault`, `ServiceHost` błędy podczas napotkania skażonego komunikatu. Można podłączyć do uszkodzonego zdarzenia i zamknąć usługę, podejmować działania naprawcze i ponownie uruchomić. Na przykład, <xref:System.ServiceModel.MsmqPoisonMessageException> w `LookupId` odniesieniu do `IErrorHandler` , można zauważyć, że w przypadku awarii `System.Messaging` hosta usługi, możesz użyć interfejsu API, aby odebrać komunikat z kolejki za pomocą polecenia, `LookupId` aby usunąć komunikat z Kolejkowanie i przechowywanie wiadomości w pewnym zewnętrznym magazynie lub w innej kolejce. Następnie można ponownie uruchomić `ServiceHost` polecenie, aby wznowić normalne przetwarzanie. [Obsługa skażonych komunikatów w usłudze MSMQ 4,0](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md) ilustruje to zachowanie.  
  
## <a name="transaction-time-out-and-poison-messages"></a>Przekroczenie limitu czasu transakcji i skażonych komunikatów  
 Klasa błędów może wystąpić między kanałem transportu umieszczonym w kolejce a kodem użytkownika. Te błędy mogą być wykrywane przez warstwy między, takie jak warstwa zabezpieczeń wiadomości lub logika wysyłania usługi. Na przykład brakuje brakującego certyfikatu X. 509 w warstwie zabezpieczeń protokołu SOAP, a brakująca akcja to przypadki, w których komunikat jest wysyłany do aplikacji. W takim przypadku model usługi porzuca komunikat. Ponieważ komunikat jest odczytywany w transakcji i nie można dostarczyć wyniku dla tej transakcji, transakcja zostanie ostatecznie przesunięta w dół, zostanie przerwana, a komunikat zostanie umieszczony w kolejce. Innymi słowy, w przypadku niektórych klas błędów, transakcja nie jest natychmiast przerywana, ale czeka na przełączenie transakcji. Limit czasu transakcji można zmodyfikować dla usługi przy użyciu <xref:System.ServiceModel.ServiceBehaviorAttribute>programu.  
  
 Aby zmienić limit czasu transakcji na poziomie całego komputera, należy zmodyfikować plik Machine. config i ustawić odpowiedni limit czasu transakcji. Należy pamiętać, że w zależności od czasu ustawionego w transakcji transakcja jest ostatecznie przerywana i wraca do kolejki, a jej licznik przerwań jest zwiększany. Po pewnym czasie wiadomość jest trująca i odpowiednia Dyspozycja zostanie wprowadzona zgodnie z ustawieniami użytkownika.  
  
## <a name="sessions-and-poison-messages"></a>Sesje i trujące komunikaty  
 Sesja przeprowadzi te same procedury obsługi ponowień i komunikatów trujących jako jeden komunikat. Właściwości wymienione wcześniej dla trujących komunikatów mają zastosowanie do całej sesji. Oznacza to, że cała sesja jest ponawiana i przechodzi do ostatniej kolejki trujących komunikatów lub kolejki utraconych wiadomości nadawcy, jeśli komunikat zostanie odrzucony.  
  
## <a name="batching-and-poison-messages"></a>Przetwarzanie wsadowe i trujące komunikaty  
 Jeśli komunikat przejdzie do trującej wiadomości i jest częścią partii, cała partia jest wycofywana, a kanał powróci do odczytu jednej wiadomości w danym momencie. Aby uzyskać więcej informacji o przetwarzaniu wsadowym, zobacz Tworzenie [wsadowe komunikatów w transakcji](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
  
## <a name="poison-message-handling-for-messages-in-a-poison-queue"></a>Obsługa komunikatów trujących dla komunikatów w kolejce trującej  
 Obsługa komunikatów trujących nie kończy się, gdy wiadomość zostanie umieszczona w kolejce trujących komunikatów. Komunikaty w kolejce trujących komunikatów muszą być nadal odczytywane i obsługiwane. Można użyć podzestawu ustawień obsługi komunikatów trujących podczas odczytu komunikatów z podkolejki trującej. Odpowiednie ustawienia to `ReceiveRetryCount` i `ReceiveErrorHandling`. Można ustawić wartość `ReceiveErrorHandling` Drop, Reject lub Fault. `MaxRetryCycles`jest ignorowany i występuje wyjątek, jeśli `ReceiveErrorHandling` jest ustawiony do przenoszenia.  
  
## <a name="windows-vista-windows-server-2003-and-windows-xp-differences"></a>Różnice w systemach Windows Vista, Windows Server 2003 i Windows XP  
 Jak wspomniano wcześniej, nie wszystkie ustawienia obsługi komunikatów trujących mają [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] zastosowanie [!INCLUDE[wxp](../../../../includes/wxp-md.md)]do i. Następujące kluczowe różnice między kolejkami komunikatów w systemie [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], [!INCLUDE[wxp](../../../../includes/wxp-md.md)]i [!INCLUDE[wv](../../../../includes/wv-md.md)] dotyczą obsługi komunikatów trujących:  
  
- Usługa kolejkowania komunikatów w [!INCLUDE[wv](../../../../includes/wv-md.md)] programie obsługuje podkolejki, [!INCLUDE[wxp](../../../../includes/wxp-md.md)] natomiast [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] nie obsługują kolejek. Kolejki podrzędne są używane w obsłudze komunikatów trujących. Kolejki ponawiania prób i kolejka Trująca są podkolejkami do kolejki aplikacji utworzonej na podstawie ustawień obsługi komunikatów trujących. `MaxRetryCycles` Określa liczbę podkolejek ponowień do utworzenia. W związku z tym, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] gdy [!INCLUDE[wxp](../../../../includes/wxp-md.md)]działa `MaxRetryCycles` w systemie lub `ReceiveErrorHandling.Move` , są ignorowane i nie jest dozwolone.  
  
- Usługa kolejkowania komunikatów w [!INCLUDE[wv](../../../../includes/wv-md.md)] programie obsługuje potwierdzenie negatywne [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] , a [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nie. Negatywne potwierdzenie od Menedżera kolejki odbiorczej powoduje, że Menedżer kolejki wysyłania umieszcza odrzucony komunikat w kolejce utraconych wiadomości. W związku z `ReceiveErrorHandling.Reject` tym, nie jest [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] dozwolone [!INCLUDE[wxp](../../../../includes/wxp-md.md)]w i.  
  
- Usługa kolejkowania komunikatów w [!INCLUDE[wv](../../../../includes/wv-md.md)] programie obsługuje Właściwość komunikatu, która zachowuje liczbę prób dostarczenia komunikatu. Ta właściwość liczby przerwań nie jest dostępna [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] w [!INCLUDE[wxp](../../../../includes/wxp-md.md)]systemach i. Funkcja WCF zachowuje liczbę przerwań w pamięci, dlatego jest możliwe, że ta właściwość nie może zawierać dokładnej wartości, gdy ten sam komunikat jest odczytywany przez więcej niż jedną usługę WCF w farmie.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Określanie i obsługa błędów w kontraktach i usługach](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
