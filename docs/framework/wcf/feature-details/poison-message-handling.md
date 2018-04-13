---
title: Obsługa komunikatów zanieczyszczonych
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d1c5e5a-7928-4a80-95ed-d8da211b8595
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8202c9f715944c6d556c0023444475838cfd5eab
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2018
---
# <a name="poison-message-handling"></a>Obsługa komunikatów zanieczyszczonych
A *Trująca wiadomość* jest komunikat, który przekracza maksymalną liczbę prób dostarczenia do aplikacji. Taka sytuacja może wystąpić, gdy aplikacja kolejki nie może przetworzyć komunikatu z powodu błędów. Aby spełnić wymagania niezawodności, aplikację zakolejkowaną odbiera komunikaty w ramach transakcji. Przerywanie transakcji, w którym została odebrana wiadomość w kolejce pozostawia wiadomości w kolejce, tak, aby komunikat zostanie ponowiony w nowej transakcji. Jeśli ten problem, który spowodował przerwanie transakcji nie zostanie rozwiązany, aplikacja odbierająca może zostać zablokowane w pętli otrzymywanie i przerywanie tę samą wiadomość do czasu przekroczyła maksymalną liczbę prób dostarczenia i wyniki Trująca wiadomość.  
  
 Komunikat może stać się Trująca wiadomość wielu powodów. Najbardziej typowe przyczyny są określone dla aplikacji. Na przykład jeśli aplikacja odczytuje komunikat z kolejki i przetwarza niektóre bazy danych, aplikacja może się nie powieść uzyskać blokady w bazie danych, co powoduje przerwać transakcji. Ponieważ transakcji bazy danych zostało przerwane, komunikat pozostaje w kolejce, co powoduje, że aplikacja odczytać wiadomość po raz drugi i wprowadzić kolejna próba uzyskania blokady w bazie danych. Komunikaty może również zostać skażone, które zawierają nieprawidłowe informacje. Na przykład zamówienia zakupu mogą zawierać nieprawidłowe odbiorcy. W takich przypadkach aplikacji dobrowolnie może przerwać transakcji i wymusić komunikat, który ma zostać Trująca wiadomość.  
  
 W rzadkich przypadkach wiadomości może nie pobrać wysyłane do aplikacji. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Warstwa może się okazać problem z wiadomości, takie jak wiadomości ma nieprawidłową ramkę, poświadczenia nieprawidłowy komunikat dołączenie do lub nagłówka nieprawidłową akcję. W takich przypadkach aplikacja nigdy nie odbiera wiadomości; Jednakże komunikat nadal może stać się Trująca wiadomość i ręczne przetwarzanie.  
  
## <a name="handling-poison-messages"></a>Obsługa wiadomości  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], skażone komunikat — Obsługa udostępnia mechanizm aplikacja odbierająca na wypadek wiadomości, które nie mogą być wysyłane do aplikacji lub wiadomości, które są wysyłane do aplikacji, ale które nie można przetworzyć z powodu przyczyny specyficzne dla aplikacji. Obsługi uszkodzonych komunikatów jest konfigurowana za pomocą następujących właściwości w każdym z dostępnych powiązań umieszczonych w kolejce:  
  
-   `ReceiveRetryCount`. Wartość całkowitą, która wskazuje maksymalną liczbę ponownych prób dostarczenia komunikatu z kolejki aplikacji do aplikacji. Wartość domyślna to 5. To jest odpowiednia w przypadku, gdy natychmiastowego ponawiania rozwiązuje problem, takich jak z tymczasowego zakleszczenie w bazie danych.  
  
-   `MaxRetryCycles`. Wartość całkowitą, która wskazuje maksymalną liczbę cykli ponownych prób. Cykl składa się z przesyłania wiadomości z kolejki aplikacji do ponawiania i opóźnieniem można skonfigurować z ponawiania do kolejki aplikacji do dostarczania Ponów. Wartość domyślna to 2. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], komunikat zostanie podjęta próba maksymalnie (`ReceiveRetryCount` + 1) * (`MaxRetryCycles` + 1) razy. `MaxRetryCycles` jest ignorowany w [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   `RetryCycleDelay`. Czas opóźnienia między liczbę cykli ponownych prób. Wartość domyślna to 30 minut. `MaxRetryCycles` i `RetryCycleDelay` razem udostępniają mechanizm rozwiązać problem, gdzie ponowna próba opóźnieniem okresowe rozwiązuje problem. Na przykład obsługuje wierszem zablokowanym ustawiony w programie SQL Server oczekiwania zatwierdzania transakcji.  
  
-   `ReceiveErrorHandling`. Wyliczenie wskazujący akcję do wykonania dla komunikatu, której nie dostarczania po prób wykonania maksymalnej liczby ponownych prób. Wartości można być Odrzuć usterka, Drop i przenieść. Opcja domyślna jest błędem.  
  
-   Fault. Ta opcja wysyła odbiornika, który spowodował błąd `ServiceHost` do błędów. Komunikat należy usunąć z kolejki aplikacji przez inny mechanizm zewnętrzny przed kontynuowaniem aplikacji do przetwarzania komunikatów z kolejki.  
  
-   Upuść. Ta opcja powoduje Trująca wiadomość i komunikat nigdy nie jest dostarczany do aplikacji. Jeśli komunikat `TimeToLive` właściwości wygasła w tym momencie, a następnie może zostać wyświetlony komunikat w kolejce wiadomości utraconych nadawcy. Jeśli nie, wiadomość nie jest wyświetlana z dowolnego miejsca. Ta opcja oznacza, że użytkownik nie określił co zrobić, jeśli komunikat zostanie utracony.  
  
-   Odrzuć. Ta opcja jest dostępna tylko na [!INCLUDE[wv](../../../../includes/wv-md.md)]. Powoduje to, że usługi kolejkowania komunikatów (MSMQ) do odesłania negatywnego potwierdzenia do wysyłania menedżera kolejek, że aplikacja nie może odebrać komunikatu. Wiadomość jest umieszczana w kolejce wiadomości utraconych wysyłania menedżera kolejek.  
  
-   Przenieś. Ta opcja jest dostępna tylko na [!INCLUDE[wv](../../../../includes/wv-md.md)]. Spowoduje to przeniesienie Trująca wiadomość do kolejki komunikatów poison do późniejszego przetwarzania przez aplikację do obsługi komunikatów poison. Kolejka komunikatów poison jest podkolejki kolejki aplikacji. Może być aplikacją poison komunikat — Obsługa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, która odczytuje wiadomości z kolejki skażone. Trująca kolejki jest podkolejki kolejki aplikacji i może zostać zlikwidowane jako net.msmq://\<*nazw komputerów*>/*applicationQueue*; skażone, gdzie  *Nazwa maszyny* to nazwa komputera, na którym znajduje się kolejka i *applicationQueue* jest nazwą kolejki specyficzne dla aplikacji.  
  
 Maksymalna liczba prób dostarczenia komunikatu są następujące:  
  
-   ((ReceiveRetryCount+1) * (MaxRetryCycles + 1)) na [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
-   (ReceiveRetryCount + 1) na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
> [!NOTE]
>  Brak ponownych prób są nawiązywane komunikatu, który jest dostarczany pomyślnie.  
  
 Aby śledzić liczbę razy, przeczytaj wiadomość zostanie podjęta, [!INCLUDE[wv](../../../../includes/wv-md.md)] przechowuje właściwości trwałe wiadomości, które zlicza liczbę przerwań i właściwość count przeniesienie, które zlicza liczbę razy komunikat są przenoszone między kolejki aplikacji i kolejki podrzędne. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Kanału wykorzystuje te można obliczyć liczby ponownych prób receive i liczby cykli ponownych prób. Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)], liczba przerwania jest przechowywana w pamięci przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanału i jest resetowana, jeśli aplikacja nie powiedzie się. Ponadto [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanału może przechowywać przerwanie liczby komunikatów do 256 w pamięci w dowolnym momencie. Jeśli 257th wiadomość zostanie odczytana, następnie najstarsze komunikat przerwania zostanie zresetowany.  
  
 Przerwanie liczba i Przenieś liczby właściwości są dostępne dla operacji usługi za pomocą kontekstu operacji. Poniższy przykład kodu pokazuje, jak uzyskać do nich dostęp.  
  
 [!code-csharp[S_UE_MSMQ_Poison#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/service.cs#1)]  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] udostępnia dwa standardowe powiązania w kolejce:  
  
-   <xref:System.ServiceModel.NetMsmqBinding>. A [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] powiązanie odpowiednie dla komunikacji z innymi kolejki wykonywania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punktów końcowych.  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Powiązanie odpowiednie dla komunikacji z istniejącymi aplikacjami usługi kolejkowania komunikatów.  
  
> [!NOTE]
>  Można zmienić właściwości w tych powiązań, w oparciu o wymagania Twojej [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi. Cały Trująca wiadomość mechanizmu obsługi jest lokalny do aplikacji odbierającej. Proces jest niewidoczne aplikacja wysyłająca, chyba że aplikacja odbierająca ostatecznie zatrzymuje i wysyła potwierdzenie negatywne do nadawcy. W takim przypadku wiadomość zostanie przeniesiona do kolejki utraconych wiadomości nadawcy.  
  
## <a name="best-practice-handling-msmqpoisonmessageexception"></a>Najlepsze rozwiązanie: Msmqpoisonmessageexception — Obsługa  
 Gdy usługa określa, że wiadomość jest skażone, transport z kolejką zgłasza <xref:System.ServiceModel.MsmqPoisonMessageException> zawierający `LookupId` skażone wiadomości.  
  
 Aplikację można wdrożyć <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejs do obsługi błędów wymagane przez tę aplikację. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Rozszerzanie kontroli obsługi i raportowania błędów](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md).  
  
 Aplikacja może wymagać określonego rodzaju automatycznych Obsługa skażone wiadomości, który przenosi skażone wiadomości do kolejki Trująca wiadomość, dzięki czemu usługa dostęp pozostałej części wiadomości w kolejce. Jest to tylko scenariusz przy użyciu mechanizmu obsługi błędów do nasłuchiwania wyjątki poison wiadomości, gdy <xref:System.ServiceModel.Configuration.MsmqBindingElementBase.ReceiveErrorHandling%2A> mają ustawioną wartość <xref:System.ServiceModel.ReceiveErrorHandling.Fault>. Przykładowy komunikat poison dla wersji 3.0 pokazano to zachowanie. Poniżej opisano czynności wymagane do obsługi skażone komunikaty, w tym najlepsze rozwiązania:  
  
1.  Upewnij się, że ustawienia skażone uwzględnić wymagania dotyczące aplikacji. Podczas pracy z ustawieniami, upewnij się, poznać różnice między możliwości usługi kolejkowania komunikatów na [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
2.  W razie potrzeby Implementowanie `IErrorHandler` do obsługi błędów poison wiadomości. Ponieważ ustawienie `ReceiveErrorHandling` do `Fault` wymaga ręcznego mechanizmu przenieść skażone wiadomości z kolejki lub skorygować zewnętrznego problemem zależnych, jest zaimplementowanie typowego użycia `IErrorHandler` podczas `ReceiveErrorHandling` ma ustawioną wartość `Fault`, jako pokazano w poniższym kodzie.  
  
     [!code-csharp[S_UE_MSMQ_Poison#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonerrorhandler.cs#2)]  
  
3.  Utwórz `PoisonBehaviorAttribute` używanego zachowanie usługi. Instaluje zachowanie `IErrorHandler` na Dyspozytor. Zobacz poniższy przykład kodu.  
  
     [!code-csharp[S_UE_MSMQ_Poison#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonbehaviorattribute.cs#3)]  
  
4.  Upewnij się, że usługa jest adnotowany przy użyciu atrybutu skażone zachowanie.  
  
  
  
 Ponadto jeśli `ReceiveErrorHandling` ustawiono `Fault`, `ServiceHost` błędów w przypadku napotkania Trująca wiadomość. Można Podłączanie do zdarzeń błędnej i zamknąć usługę, wykonaj działania naprawcze i ponownie uruchomić. Na przykład `LookupId` w <xref:System.ServiceModel.MsmqPoisonMessageException> propagowane do `IErrorHandler` można zauważyć i kiedy błędów hosta usługi, można używać `System.Messaging` interfejsu API do odbierania wiadomości z kolejki przy użyciu `LookupId` można usunąć wiadomości z kolejki i zapisać komunikatu w niektórych zewnętrznym sklepie lub innej kolejki. Następnie można ponownie uruchomić `ServiceHost` Wznowienie normalnego przetwarzania. [Zanieczyszczonych obsługi wiadomości MSMQ 4.0](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md) pokazano to zachowanie.  
  
## <a name="transaction-time-out-and-poison-messages"></a>Limit czasu transakcji i skażone wiadomości  
 Klasa błędów, może wystąpić między kanał transportu umieszczonych w kolejce i kod użytkownika. Błędy te mogą być wykrywane przez między nimi, takie jak warstwa zabezpieczeń wiadomości lub usługa wysyła logiki warstwy. Na przykład brakującego certyfikatu X.509 wykryto warstwy zabezpieczeń SOAP i Brak akcji są przypadki, w którym komunikat get wysyłane do aplikacji. W takim przypadku modelu usług odrzuca komunikat. Komunikat został odczytany w transakcji i wyniki dla tej transakcji nie może być podany limit czasu po pewnym czasie transakcji, dlatego przerwań i wiadomość jest przywracane do kolejki. Innymi słowy niektóre klasy błędów, transakcja nie przerwać natychmiast, ale oczekuje, aż upłynie limit czasu transakcji. Można zmodyfikować limitu czasu transakcji dla usługi przy użyciu <xref:System.ServiceModel.ServiceBehaviorAttribute>.  
  
 Aby zmienić limit czasu transakcji na poziomie komputera, modyfikowania pliku machine.config i ustawiania limitu czasu transakcji odpowiednie. Należy pamiętać, że, w zależności od limit czasu ustawiony w transakcji, transakcji po pewnym czasie przerywa i wraca do kolejki i licznika przerwania jest zwiększany. Po pewnym czasie komunikat staje się skażone i prawej dyspozycji staje się zgodnie z ustawieniami użytkownika.  
  
## <a name="sessions-and-poison-messages"></a>Sesje i skażone wiadomości  
 Sesja ulega poison komunikat — Obsługa procedur i ponów próbę wykonania tego samego jako pojedynczym komunikacie. Właściwości wymienionego powyżej skażone komunikaty dotyczą całej sesji. Oznacza to, że całej sesji próba zostanie ponowiona i przechodzi do końcowego kolejki komunikatów poison lub kolejki utraconych wiadomości nadawcy, jeśli komunikat zostanie odrzucony.  
  
## <a name="batching-and-poison-messages"></a>Przetwarzanie wsadowe i skażone komunikaty  
 Jeśli wiadomość staje się Trująca wiadomość i jest częścią partii, całą partię zostanie wycofana i zwraca kanału do odczytywania jeden komunikat w czasie. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Przetwarzanie wsadowe, zobacz [tworzenie partii komunikatów w ramach transakcji](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
  
## <a name="poison-message-handling-for-messages-in-a-poison-queue"></a>Obsługa komunikatów w kolejce skażone poison komunikatów  
 Obsługa komunikatów poison nie zakończy się wiadomość jest umieszczana w kolejce wiadomości poison. Wiadomości w kolejce wiadomości poison nadal musi być do odczytu i obsługi. Podzbiór ustawienia poison komunikat — Obsługa można użyć podczas odczytywania wiadomości z ostatnim trującej. Są stosowane ustawienia `ReceiveRetryCount` i `ReceiveErrorHandling`. Można ustawić `ReceiveErrorHandling` porzucić Odrzuć lub Fault. `MaxRetryCycles` jest ignorowany i jest zwracany wyjątek, jeśli `ReceiveErrorHandling` ma wartość Move.  
  
## <a name="windows-vista-windows-server-2003-and-windows-xp-differences"></a>Windows Vista, Windows Server 2003 i Windows XP różnic  
 Jak wspomniano wcześniej, nie wszystkie ustawienia poison komunikat — Obsługa dotyczą [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. Poniższy klucz różnice między usługi kolejkowania komunikatów na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], [!INCLUDE[wxp](../../../../includes/wxp-md.md)], i [!INCLUDE[wv](../../../../includes/wv-md.md)] mają zastosowanie do obsługi komunikatów poison:  
  
-   Komunikatów usługi kolejkowania wiadomości w [!INCLUDE[wv](../../../../includes/wv-md.md)] obsługuje podkolejki, podczas gdy [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nie obsługują podkolejki. Kolejki podrzędne są używane w obsłudze poison komunikatów. Kolejki ponownych prób i skażone kolejki są podkolejki do kolejki aplikacji, która jest tworzona na podstawie ustawień poison komunikat — Obsługa. `MaxRetryCycles` Określa, ile ponów podkolejki do utworzenia. W związku z tym podczas uruchamiania [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` są ignorowane i `ReceiveErrorHandling.Move` jest niedozwolone.  
  
-   Komunikatów usługi kolejkowania wiadomości w [!INCLUDE[wv](../../../../includes/wv-md.md)] obsługuje negatywną potwierdzenie, podczas gdy [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nie. Potwierdzenie negatywne z odbierającego menedżera kolejek powoduje wysyłanie menedżera kolejek można umieścić odrzucone wiadomości w kolejce wiadomości utraconych. W efekcie `ReceiveErrorHandling.Reject` jest niedozwolone w przypadku [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   Komunikatów usługi kolejkowania wiadomości w [!INCLUDE[wv](../../../../includes/wv-md.md)] obsługuje nastąpiła właściwości wiadomości, które zlicza liczbę dostarczanie komunikatów. Ta właściwość count przerwania nie jest dostępny na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] przechowuje liczby przerwania w pamięci, dlatego jest możliwe, że ta właściwość nie może zawierać dokładne wartości, gdy ten sam komunikat jest odczytywany przez więcej niż jeden [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługę w farmie.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 [Określanie i obsługa błędów w kontraktach i usługach](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
