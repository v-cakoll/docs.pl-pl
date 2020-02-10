---
title: Obsługa komunikatów zanieczyszczonych
ms.date: 03/30/2017
ms.assetid: 8d1c5e5a-7928-4a80-95ed-d8da211b8595
ms.openlocfilehash: 378849815617f6556a7d9cc7e89c6697bfdd895d
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094998"
---
# <a name="poison-message-handling"></a>Obsługa komunikatów zanieczyszczonych
*Trująca wiadomość* jest komunikatem, który przekroczył maksymalną liczbę prób dostarczenia do aplikacji. Taka sytuacja może wystąpić, gdy aplikacja oparta na kolejce nie może przetworzyć komunikatu z powodu błędów. Aby spełnić wymagania dotyczące niezawodności, aplikacja umieszczona w kolejce odbiera komunikaty w ramach transakcji. Przerwanie transakcji, w której otrzymano komunikat w kolejce, pozostawia komunikat w kolejce, aby komunikat został ponowiony w ramach nowej transakcji. Jeśli problem, który spowodował przerwanie transakcji, nie zostanie poprawiony, aplikacja otrzymująca może zostać zablokowana w pętli, która odbiera i przerywa ten sam komunikat do momentu przekroczenia maksymalnej liczby prób dostarczenia i zatrucia wyników komunikatów.  
  
 Komunikat może być skażony z wielu powodów. Najczęstszymi przyczynami są specyficzne dla aplikacji. Na przykład, jeśli aplikacja odczytuje komunikat z kolejki i wykonuje przetwarzanie bazy danych, aplikacja może nie można uzyskać blokady bazy danych, powodując przerwanie transakcji. Ponieważ transakcja bazy danych została przerwana, komunikat pozostaje w kolejce, co powoduje, że aplikacja może ponownie odczytać komunikat po raz drugi i podjąć kolejną próbę uzyskania blokady bazy danych. Komunikaty mogą również stać się trujące, jeśli zawierają nieprawidłowe informacje. Na przykład zamówienie zakupu może zawierać nieprawidłowy numer klienta. W takich przypadkach aplikacja może dobrowolnie przerwać transakcję i wymusić, aby komunikat stał się skażonym komunikatem.  
  
 W rzadkich przypadkach komunikaty mogą nie być wysyłane do aplikacji. Warstwa Windows Communication Foundation (WCF) może znaleźć problem z komunikatem, na przykład jeśli komunikat ma złą ramkę, dołączono do niego nieprawidłowe poświadczenia wiadomości lub nieprawidłowy nagłówek akcji. W takich przypadkach aplikacja nigdy nie otrzymuje komunikatu; Jednak komunikat nadal może stać się skażony i być przetwarzany ręcznie.  
  
## <a name="handling-poison-messages"></a>Obsługa skażonych komunikatów  
 W programie WCF Obsługa skażonych komunikatów zapewnia mechanizm do otrzymywania aplikacji, które nie mogą być wysyłane do aplikacji lub komunikatów wysyłanych do aplikacji, ale nie można ich przetworzyć z powodu specyficznej dla aplikacji powodów. Skonfiguruj obsługę skażonych komunikatów z następującymi właściwościami w każdym z dostępnych w kolejce powiązań:  
  
- `ReceiveRetryCount`. Wartość całkowita wskazująca maksymalną liczbę ponownych prób dostarczenia komunikatu z kolejki aplikacji do aplikacji. Wartość domyślna to 5. Jest to wystarczające w przypadkach, gdy natychmiastowa ponowna próba rozwiązuje problem, na przykład przez tymczasowe zakleszczenie w bazie danych.  
  
- `MaxRetryCycles`. Wartość całkowita, która wskazuje maksymalną liczbę ponownych prób. Cykl ponowień polega na przesłaniu komunikatu z kolejki aplikacji do podrzędnej kolejki ponownych prób i po skonfigurowaniu opóźnienia z powrotem z kolejki ponownych prób w kolejce aplikacji w celu ponowienia próby dostarczenia. Wartość domyślna to 2. W systemie Windows Vista komunikat próbuje maksymalnie (`ReceiveRetryCount` + 1) * (`MaxRetryCycles` + 1) razy. `MaxRetryCycles` jest ignorowany w systemach Windows Server 2003 i Windows XP.  
  
- `RetryCycleDelay`. Opóźnienie między cyklami ponawiania prób. Wartość domyślna to 30 minut. `MaxRetryCycles` i `RetryCycleDelay` razem zapewniają mechanizm rozwiązywania problemu, gdy ponowna próba po okresowym opóźnieniu rozwiązuje problem. Na przykład obsługuje zablokowany zestaw wierszy w SQL Server oczekujące zatwierdzenie transakcji.  
  
- `ReceiveErrorHandling`. Wyliczenie, które wskazuje akcję, która ma zostać podjęta dla komunikatu o niepomyślnym dostarczeniu po próbie przeprowadzenia maksymalnej liczby ponownych prób. Wartości mogą być błędne, porzucane, odrzucane i przenoszone. Opcja domyślna to Fault.  
  
- Fault. Ta opcja wysyła błąd do odbiornika, który spowodował błąd `ServiceHost`. Komunikat musi zostać usunięty z kolejki aplikacji przez pewien mechanizm zewnętrzny, aby aplikacja mogła kontynuować przetwarzanie komunikatów z kolejki.  
  
- Listy rozwijanej. Ta opcja powoduje odrzucanie skażonych komunikatów, a komunikat nigdy nie jest dostarczany do aplikacji. Jeśli właściwość `TimeToLive` komunikatu wygasła w tym momencie, komunikat może się pojawić w kolejce utraconych wiadomości nadawcy. Jeśli nie, komunikat nie pojawia się w dowolnym miejscu. Ta opcja oznacza, że użytkownik nie określił czynności, które należy wykonać, jeśli komunikat zostanie utracony.  
  
- Oznacza. Ta opcja jest dostępna tylko w systemie Windows Vista. Powoduje to zainstruujenie usługi kolejkowania komunikatów (MSMQ) w celu wysłania negatywnego potwierdzenia z powrotem do Menedżera kolejki wysyłania, którego aplikacja nie może odebrać komunikatu. Wiadomość zostanie umieszczona w kolejce utraconych wiadomości Menedżera kolejki wysyłania.  
  
- Przenieś. Ta opcja jest dostępna tylko w systemie Windows Vista. Spowoduje to przeniesienie skażonego komunikatu do kolejki komunikatów trujących w celu późniejszego przetworzenia przez aplikację skażoną komunikatów. "Trująca-komunikat" jest podkolejką kolejki aplikacji. Aplikacja do obsługi komunikatów trujących może być usługą WCF, która odczytuje komunikaty z kolejki trującej. Kolejka Trująca jest podkolejką kolejki aplikacji i może być rozkierowane jako net. MSMQ://\<*Machine-name*>/*applicationQueue*;p Oison, gdzie *Machine-Name* to nazwa komputera, na którym znajduje się kolejka, a *applicationQueue* to nazwa kolejki specyficznej dla aplikacji.  
  
Poniżej przedstawiono maksymalną liczbę prób dostarczenia komunikatu:  
  
- ((ReceiveRetryCount + 1) * (MaxRetryCycles + 1)) w systemie Windows Vista.  
  
- (ReceiveRetryCount + 1) w systemie Windows Server 2003 i Windows XP.  
  
> [!NOTE]
> Nie wykonano żadnych ponownych prób dla wiadomości, która została dostarczona pomyślnie.  
  
 Aby śledzić liczbę prób odczytu komunikatu, system Windows Vista utrzymuje trwałą Właściwość komunikatu, która zlicza liczbę przerwań i Właściwość liczby przeniesień, która zlicza, ile razy komunikat przechodzi między kolejką aplikacji a podkolejkami. Kanał WCF używa tych funkcji do obliczenia liczby ponowień odbioru i liczby ponownych prób. W systemach Windows Server 2003 i Windows XP licznik przerwań jest zachowywany w pamięci przez kanał WCF i jest resetowany w przypadku niepowodzenia aplikacji. Ponadto kanał WCF może w dowolnym momencie przechowywać liczbę przerwań dla maksymalnie 256 komunikatów w pamięci. Jeśli zostanie odczytany komunikat 257th, licznik przerwań najstarszej wiadomości zostanie zresetowany.  
  
 Właściwości liczba przerwań i liczba operacji przenoszenia są dostępne dla operacji usługi za pomocą kontekstu operacji. Poniższy przykład kodu pokazuje, jak uzyskać do nich dostęp.  
  
 [!code-csharp[S_UE_MSMQ_Poison#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/service.cs#1)]  
  
 Funkcja WCF oferuje dwa standardowe powiązania kolejkowane:  
  
- <xref:System.ServiceModel.NetMsmqBinding>. Powiązanie .NET Framework odpowiednie do wykonywania komunikacji opartej na kolejce z innymi punktami końcowymi WCF.  
  
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Powiązanie odpowiednie do komunikacji z istniejącymi aplikacjami usługi kolejkowania komunikatów.  
  
> [!NOTE]
> Można zmienić właściwości w tych powiązaniach na podstawie wymagań usługi WCF. Cały mechanizm obsługi skażonych komunikatów jest lokalny dla aplikacji odbiorczej. Ten proces jest niewidoczny dla aplikacji wysyłającej, chyba że aplikacja otrzymująca ostatecznie zatrzyma się i wyśle negatywną potwierdzenie z powrotem do nadawcy. W takim przypadku wiadomość zostanie przeniesiona do kolejki utraconych wiadomości nadawcy.  
  
## <a name="best-practice-handling-msmqpoisonmessageexception"></a>Najlepsze rozwiązanie: Obsługa MsmqPoisonMessageException —  
 Gdy usługa określa, że komunikat jest trująca, transport w kolejce zgłasza <xref:System.ServiceModel.MsmqPoisonMessageException>, który zawiera `LookupId` trującej wiadomości.  
  
 Aplikacja do odbioru może zaimplementować interfejs <xref:System.ServiceModel.Dispatcher.IErrorHandler>, aby obsłużyć wszelkie błędy wymagane przez aplikację. Aby uzyskać więcej informacji, zobacz [Rozszerzanie kontroli nad obsługą błędów i raportowaniem](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md).  
  
 Aplikacja może wymagać pewnego rodzaju automatycznej obsługi skażonych komunikatów, które przenosi trujące komunikaty do kolejki komunikatów trujących, aby usługa mogła uzyskać dostęp do pozostałych komunikatów w kolejce. Jedynym scenariuszem dotyczącym używania mechanizmu obsługi błędów do nasłuchiwania wyjątków komunikatów trujących jest ustawienie <xref:System.ServiceModel.Configuration.MsmqBindingElementBase.ReceiveErrorHandling%2A> <xref:System.ServiceModel.ReceiveErrorHandling.Fault>. Przykładowy komunikat zatrucia dla usługi kolejkowania komunikatów 3,0 pokazuje to zachowanie. Poniżej przedstawiono kroki, które należy wykonać, aby obsłużyć trujące komunikaty, w tym najlepsze rozwiązania:  
  
1. Upewnij się, że ustawienia trujące odzwierciedlają wymagania aplikacji. Podczas pracy z ustawieniami upewnij się, że rozumiesz różnice między możliwościami usługi kolejkowania komunikatów w systemach Windows Vista, Windows Server 2003 i Windows XP.  
  
2. W razie potrzeby Zaimplementuj `IErrorHandler`, aby obsłużyć błędy komunikatów trujących. Ponieważ ustawienie `ReceiveErrorHandling` `Fault` wymaga ręcznego mechanizmu przenoszenia skażonego komunikatu z kolejki lub do skorygowania zewnętrznego problemu zależnego, typowym użyciem jest zaimplementowanie `IErrorHandler`, gdy `ReceiveErrorHandling` jest ustawiona na `Fault`, jak pokazano w poniższym kodzie.  
  
     [!code-csharp[S_UE_MSMQ_Poison#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonerrorhandler.cs#2)]  
  
3. Utwórz `PoisonBehaviorAttribute`, których może używać zachowanie usługi. Zachowanie instaluje `IErrorHandler` w dyspozytorze. Zobacz Poniższy przykład kodu.  
  
     [!code-csharp[S_UE_MSMQ_Poison#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonbehaviorattribute.cs#3)]  
  
4. Upewnij się, że Twoja usługa ma adnotację z atrybutem zachowania trujące.  

 Ponadto, jeśli `ReceiveErrorHandling` jest ustawiona na `Fault`, `ServiceHost` błędy podczas napotkania skażonego komunikatu. Można podłączyć do uszkodzonego zdarzenia i zamknąć usługę, podejmować działania naprawcze i ponownie uruchomić. Na przykład `LookupId` w <xref:System.ServiceModel.MsmqPoisonMessageException> propagowany do `IErrorHandler` może zostać odnotowane i w przypadku wystąpienia błędów hosta usługi można użyć interfejsu API `System.Messaging` do odebrania komunikatu z kolejki przy użyciu `LookupId`, aby usunąć komunikat z kolejki i zapisać go w zewnętrznym magazynie lub innej kolejce. Następnie można ponownie uruchomić `ServiceHost`, aby wznowić normalne przetwarzanie. [Obsługa skażonych komunikatów w usłudze MSMQ 4,0](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md) ilustruje to zachowanie.  
  
## <a name="transaction-time-out-and-poison-messages"></a>Przekroczenie limitu czasu transakcji i skażonych komunikatów  
 Klasa błędów może wystąpić między kanałem transportu umieszczonym w kolejce a kodem użytkownika. Te błędy mogą być wykrywane przez warstwy między, takie jak warstwa zabezpieczeń wiadomości lub logika wysyłania usługi. Na przykład brakuje brakującego certyfikatu X. 509 w warstwie zabezpieczeń protokołu SOAP, a brakująca akcja to przypadki, w których komunikat jest wysyłany do aplikacji. W takim przypadku model usługi porzuca komunikat. Ponieważ komunikat jest odczytywany w transakcji i nie można dostarczyć wyniku dla tej transakcji, transakcja zostanie ostatecznie przesunięta w dół, zostanie przerwana, a komunikat zostanie umieszczony w kolejce. Innymi słowy, w przypadku niektórych klas błędów, transakcja nie jest natychmiast przerywana, ale czeka na przełączenie transakcji. Limit czasu transakcji dla usługi można zmodyfikować za pomocą <xref:System.ServiceModel.ServiceBehaviorAttribute>.  
  
 Aby zmienić limit czasu transakcji na poziomie całego komputera, należy zmodyfikować plik Machine. config i ustawić odpowiedni limit czasu transakcji. Należy pamiętać, że w zależności od czasu ustawionego w transakcji transakcja jest ostatecznie przerywana i wraca do kolejki, a jej licznik przerwań jest zwiększany. Po pewnym czasie wiadomość jest trująca i odpowiednia Dyspozycja zostanie wprowadzona zgodnie z ustawieniami użytkownika.  
  
## <a name="sessions-and-poison-messages"></a>Sesje i trujące komunikaty  
 Sesja przeprowadzi te same procedury obsługi ponowień i komunikatów trujących jako jeden komunikat. Właściwości wymienione wcześniej dla trujących komunikatów mają zastosowanie do całej sesji. Oznacza to, że cała sesja jest ponawiana i przechodzi do ostatniej kolejki trujących komunikatów lub kolejki utraconych wiadomości nadawcy, jeśli komunikat zostanie odrzucony.  
  
## <a name="batching-and-poison-messages"></a>Przetwarzanie wsadowe i trujące komunikaty  
 Jeśli komunikat przejdzie do trującej wiadomości i jest częścią partii, cała partia jest wycofywana, a kanał powróci do odczytu jednej wiadomości w danym momencie. Aby uzyskać więcej informacji o przetwarzaniu wsadowym, zobacz Tworzenie [wsadowe komunikatów w transakcji](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
  
## <a name="poison-message-handling-for-messages-in-a-poison-queue"></a>Obsługa komunikatów trujących dla komunikatów w kolejce trującej  
 Obsługa komunikatów trujących nie kończy się, gdy wiadomość zostanie umieszczona w kolejce trujących komunikatów. Komunikaty w kolejce trujących komunikatów muszą być nadal odczytywane i obsługiwane. Można użyć podzestawu ustawień obsługi komunikatów trujących podczas odczytu komunikatów z podkolejki trującej. Odpowiednie ustawienia są `ReceiveRetryCount` i `ReceiveErrorHandling`. Możesz ustawić `ReceiveErrorHandling` do porzucenia, odrzucić lub błędu. `MaxRetryCycles` jest ignorowany i występuje wyjątek, jeśli `ReceiveErrorHandling` jest ustawiony do przenoszenia.  
  
## <a name="windows-vista-windows-server-2003-and-windows-xp-differences"></a>Różnice w systemach Windows Vista, Windows Server 2003 i Windows XP  
 Jak wspomniano wcześniej, nie wszystkie ustawienia obsługi komunikatów trujących dotyczą systemu Windows Server 2003 i Windows XP. Następujące kluczowe różnice między usługą kolejkowania komunikatów w systemie Windows Server 2003, Windows XP i Windows Vista mają zastosowanie do obsługi komunikatów trujących:  
  
- Usługa kolejkowania komunikatów w systemie Windows Vista obsługuje podkolejki, a systemy Windows Server 2003 i Windows XP nie obsługują kolejek. Kolejki podrzędne są używane w obsłudze komunikatów trujących. Kolejki ponawiania prób i kolejka Trująca są podkolejkami do kolejki aplikacji utworzonej na podstawie ustawień obsługi komunikatów trujących. `MaxRetryCycles` określa liczbę podkolejek ponowień do utworzenia. W związku z tym w przypadku uruchamiania w systemie Windows Server 2003 lub Windows XP `MaxRetryCycles` są ignorowane i `ReceiveErrorHandling.Move` jest niedozwolone.  
  
- Usługa kolejkowania komunikatów w systemie Windows Vista obsługuje potwierdzenie negatywne, a systemy Windows Server 2003 i Windows XP nie są. Negatywne potwierdzenie od Menedżera kolejki odbiorczej powoduje, że Menedżer kolejki wysyłania umieszcza odrzucony komunikat w kolejce utraconych wiadomości. W związku z tym `ReceiveErrorHandling.Reject` nie jest dozwolone w przypadku systemów Windows Server 2003 i Windows XP.  
  
- Usługa kolejkowania komunikatów w systemie Windows Vista obsługuje Właściwość komunikatu, która zachowuje liczbę prób dostarczenia komunikatu. Ta właściwość liczby przerwań nie jest dostępna w systemach Windows Server 2003 i Windows XP. Funkcja WCF zachowuje liczbę przerwań w pamięci, dlatego jest możliwe, że ta właściwość nie może zawierać dokładnej wartości, gdy ten sam komunikat jest odczytywany przez więcej niż jedną usługę WCF w farmie.  
  
## <a name="see-also"></a>Zobacz też

- [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Określanie i obsługa błędów w kontraktach i usługach](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
