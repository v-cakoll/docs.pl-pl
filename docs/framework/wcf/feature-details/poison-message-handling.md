---
title: Obsługa komunikatów zanieczyszczonych
ms.date: 03/30/2017
ms.assetid: 8d1c5e5a-7928-4a80-95ed-d8da211b8595
ms.openlocfilehash: fe748ac40f03ed22cacb254ab464a6caf3d27a8c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305029"
---
# <a name="poison-message-handling"></a>Obsługa komunikatów zanieczyszczonych
A *Zarządzanie skażonymi komunikatami* jest komunikat, który przekroczył maksymalną liczbę prób dostarczenia do aplikacji. Ta sytuacja może wystąpić, gdy aplikacja w kolejce nie może przetworzyć komunikatu z powodu błędów. Aby spełniać wymagania niezawodności, aplikację zakolejkowaną odbiera komunikaty, w ramach transakcji. {Przerywanie transakcji, w którym została odebrana wiadomość w kolejce pozostawia wiadomości w kolejce, więc, że komunikat zostanie ponowiony w ramach nowej transakcji. Jeśli ten problem, który spowodował przerwanie transakcji nie zostanie rozwiązany, aplikacja odbierająca może utknąć w pętli, odbierania i przerywanie ten sam komunikat, dopóki nie przekroczono maksymalną liczbę prób dostarczenia i wyniki Zarządzanie skażonymi komunikatami.  
  
 Komunikat może stać się zarządzanie skażonymi komunikatami wielu powodów. Najbardziej typowe przyczyny są określone dla aplikacji. Na przykład jeśli aplikacja odczytuje komunikat z kolejki i przetwarza niektóre bazy danych, aplikacja może zakończyć się niepowodzeniem na uzyskanie blokady w bazie danych, co powoduje przerwać transakcji. Ponieważ transakcji bazy danych zostało przerwane, komunikat pozostaje w kolejce, co powoduje, że aplikacja ponownie odczytać wiadomość po raz drugi i kolejna próba uzyskania blokady w bazie danych. Komunikaty może również stać się zanieczyszczone, jeśli zawierają one nieprawidłowe informacje. Na przykład zamówienie zakupu mogą zawierać nieprawidłowe odbiorcy. W takich przypadkach aplikacja może dobrowolnie przerwać transakcji i wymuszenie komunikat, aby stać się zarządzanie skażonymi komunikatami.  
  
 W rzadkich przypadkach komunikatów może nie uzyskać wysyłane do aplikacji. Warstwy usług Windows Communication Foundation (WCF) może się okazać problem z wiadomości, takich jak Jeśli wiadomość ma niewłaściwy ramce, nieprawidłowy komunikat poświadczenia dołączone do lub nagłówek nieprawidłową akcję. W takich przypadkach aplikacja nigdy nie otrzyma wiadomości; Jednakże komunikat nadal może stać się zarządzanie skażonymi komunikatami i ręczne przetwarzanie.  
  
## <a name="handling-poison-messages"></a>Obsługa wiadomości  
 W programie WCF Zarządzanie skażonymi komunikatami obsługi udostępnia mechanizm aplikacja odbierająca radzenia sobie z wiadomości, które nie mogą być wysyłane do aplikacji lub wiadomości, które są wysyłane do aplikacji, ale które nie mają być przetwarzane z powodu specyficznych dla aplikacji przyczyny. Obsługa skażonych komunikatów jest skonfigurowany za pomocą następujących właściwości we wszystkich dostępnych powiązania umieszczonych w kolejce:  
  
-   `ReceiveRetryCount`. Wartość całkowitą, która określa maksymalną liczbę ponownych prób dostarczenia komunikatu z kolejki aplikacji do aplikacji. Wartość domyślna to 5. Jest to wystarczające w przypadkach, gdzie natychmiastowe ponowienie próby rozwiązuje ten problem, takich jak z tymczasowego zakleszczenie w bazie danych.  
  
-   `MaxRetryCycles`. Wartość całkowitą, która określa maksymalną liczbę ponownych prób cyklów. Cykl składa się z przesyłania wiadomości z kolejki aplikacji, do podrzędnej kolejki ponawiania i po chwili można skonfigurować z kolejki podrzędnej ponownych prób do dostarczania ponownie w kolejce aplikacji. Wartość domyślna to 2. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], komunikat zostanie podjęta próba maksymalnie (`ReceiveRetryCount` + 1) * (`MaxRetryCycles` + 1) razy. `MaxRetryCycles` jest ignorowana na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   `RetryCycleDelay`. Czas opóźnienia między ponownych prób cyklów. Wartość domyślna to 30 minut. `MaxRetryCycles` i `RetryCycleDelay` razem zapewniają mechanizm, aby rozwiązać problem, w którym ponowienie próby po opóźnieniu okresowe rozwiąże problem. Na przykład obsługuje zablokowanego wiersza, ustaw w programie SQL Server do czasu zatwierdzenia transakcji.  
  
-   `ReceiveErrorHandling`. Wyliczenie, które wskazuje akcję do wykonania dla komunikatu, w którym wystąpiła awaria dostarczania po zostanie podjęta określona maksymalna liczba ponownych prób. Wartości może być usterka, listy, Odrzuć i przenieść. Opcja domyślna jest błędów.  
  
-   Fault. Ta opcja wysyła błędów do odbiornika, który spowodował `ServiceHost` do błędów. Komunikat przeznaczonego do usunięcia z kolejki aplikacji przez inny mechanizm zewnętrzny przed aplikacji mogą w dalszym ciągu przetwarzać komunikaty z kolejki.  
  
-   Upuść. Ta opcja umieszcza Zarządzanie skażonymi komunikatami, i, że komunikat nigdy nie jest dostarczony do aplikacji. Jeśli komunikat `TimeToLive` właściwość wygasła w tym momencie, a następnie może zostać wyświetlony komunikat w kolejce wiadomości utraconych nadawcy. W przeciwnym razie komunikat nie występować w dowolnym miejscu. Ta opcja oznacza, że użytkownik nie określił co należy zrobić, jeśli komunikat zostanie utracony.  
  
-   Odrzuć. Ta opcja jest dostępna tylko na [!INCLUDE[wv](../../../../includes/wv-md.md)]. To powoduje, że usługi kolejkowania komunikatów (MSMQ) do odesłania negatywnego potwierdzenia do wysyłania menedżera kolejek, że aplikacja nie może odbierać wiadomości. Komunikat jest umieszczana w kolejce wiadomości utraconych Menedżer kolejki wysyłania.  
  
-   Przeniesienie. Ta opcja jest dostępna tylko na [!INCLUDE[wv](../../../../includes/wv-md.md)]. Powoduje to przeniesienie skażonych komunikatów do kolejki komunikatów poison do późniejszego przetwarzania przez aplikację do obsługi komunikatów poison. Kolejka komunikatów poison to kolejki podrzędnej kolejki aplikacji. Aplikacja Obsługa komunikatów poison może być usługi WCF, która odczytuje komunikaty z kolejki skażone. Skażone kolejki jest kolejki podrzędnej kolejki aplikacji i może zostać zlikwidowane jako net.msmq://\<*Nazwa maszyny*>/*applicationQueue*; skażone, gdzie  *Nazwa maszyny* to nazwa komputera, na którym znajduje się kolejka i *applicationQueue* jest nazwą kolejki specyficzne dla aplikacji.  
  
 Poniżej przedstawiono maksymalną liczbę prób dostarczenia komunikatu:  
  
-   ((ReceiveRetryCount+1) * (MaxRetryCycles + 1)) na [!INCLUDE[wv](../../../../includes/wv-md.md)].  
  
-   (ReceiveRetryCount + 1) na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
> [!NOTE]
>  Brak ponownych prób są wprowadzane dla komunikatu, która jest dostarczana pomyślnie.  
  
 Aby śledzić liczbę wiadomości odczytu zostanie podjęta, [!INCLUDE[wv](../../../../includes/wv-md.md)] przechowuje właściwości trwały komunikat, który zlicza liczbę przerwań i właściwości Liczba przenoszenia, który zlicza ile razy komunikat przechodzi między kolejki aplikacji i podkolejek. Kanał WCF używa ich do obliczenia liczby ponownych prób odbierania i liczby ponownych prób cyklów. Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)], liczba przerwania jest utrzymywany w pamięci przez kanał WCF i jest resetowana, jeśli aplikacja zakończy się niepowodzeniem. Ponadto kanału WCF mogą przechowywać przerwanie liczba komunikatów do 256 w pamięci w dowolnym momencie. Jeśli 257th komunikat jest odczytywany, licznik przerwania najstarsze komunikat zostanie zresetowany.  
  
 Przerwanie count i przenieść właściwości Liczba służą do operacji usługi za pomocą kontekstu operacji. W poniższym przykładzie kodu pokazano, jak można uzyskać do nich dostęp.  
  
 [!code-csharp[S_UE_MSMQ_Poison#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/service.cs#1)]  
  
 Usługi WCF oferuje dwa standardowe powiązania umieszczonych w kolejce:  
  
-   <xref:System.ServiceModel.NetMsmqBinding>. A [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] powiązanie odpowiednie dla komunikacji z innymi punktami końcowymi programu WCF z kolejki wykonywania.  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>. Powiązanie odpowiednie dla komunikacji z istniejącymi aplikacjami usługi kolejkowania komunikatów.  
  
> [!NOTE]
>  Można zmienić właściwości w tych powiązań, w oparciu o wymagania usługi WCF. Całe Zarządzanie skażonymi komunikatami, mechanizm obsługi jest lokalny do aplikacji odbierającej. Ten proces jest niewidoczny dla aplikacji wysyłającej, chyba że aplikacja odbierająca ostatecznie zatrzymuje i wysyła negatywnego potwierdzenia do nadawcy. W takim przypadku wiadomość zostanie przeniesiona do kolejki utraconych wiadomości przez nadawcę.  
  
## <a name="best-practice-handling-msmqpoisonmessageexception"></a>Najlepszym rozwiązaniem jest: Msmqpoisonmessageexception — Obsługa  
 Gdy usługa określa, czy komunikat jest skażone, zgłasza umieszczonych w kolejce transportu <xref:System.ServiceModel.MsmqPoisonMessageException> zawierający `LookupId` skażone wiadomości.  
  
 Aplikację można wdrożyć <xref:System.ServiceModel.Dispatcher.IErrorHandler> interfejsu do obsługi błędów, których wymaga aplikacja. Aby uzyskać więcej informacji, zobacz [rozszerzanie kontroli nad obsługę błędów i raportowanie](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md).  
  
 Aplikacja może wymagać pewnego rodzaju automatycznych obsługi skażone komunikaty przenosi skażone komunikaty do kolejki Zarządzanie skażonymi komunikatami, tak, że usługi mogą uzyskiwać dostęp do pozostałej części wiadomości w kolejce. Jest to tylko scenariusz przy użyciu mechanizmu obsługi błędów do nasłuchiwania wiadomości poison wyjątki, gdy <xref:System.ServiceModel.Configuration.MsmqBindingElementBase.ReceiveErrorHandling%2A> ustawienie ma wartość <xref:System.ServiceModel.ReceiveErrorHandling.Fault>. W przykładzie poison wiadomości dla wersji 3.0 pokazano to zachowanie. Poniżej opisano czynności wymagane do obsługi skażone komunikaty, łącznie z najlepszymi rozwiązaniami:  
  
1. Upewnij się, że ustawienia skażone odzwierciedla wymagania aplikacji. Podczas pracy z ustawieniami, upewnij się, zrozumieć różnice między możliwości usługi kolejkowania komunikatów na [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
2. W razie potrzeby Implementowanie `IErrorHandler` do obsługi błędów poison wiadomości. Ponieważ ustawienie `ReceiveErrorHandling` do `Fault` wymaga mechanizm ręcznie przenieść skażone wiadomości w kolejce lub zewnętrznego problemu zależnych zwykle jest używane do implementowania `IErrorHandler` podczas `ReceiveErrorHandling` jest ustawiona na `Fault`, jako pokazano w poniższym kodzie.  
  
     [!code-csharp[S_UE_MSMQ_Poison#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonerrorhandler.cs#2)]  
  
3. Utwórz `PoisonBehaviorAttribute` używanego zachowania usługi. Instaluje zachowanie `IErrorHandler` na Dyspozytor. Zobacz poniższy przykład kodu.  
  
     [!code-csharp[S_UE_MSMQ_Poison#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_ue_msmq_poison/cs/poisonbehaviorattribute.cs#3)]  
  
4. Upewnij się, że usługa jest oznaczony za pomocą atrybutu skażone zachowanie.  

 Ponadto jeśli `ReceiveErrorHandling` ustawiono `Fault`, `ServiceHost` błędów w przypadku napotkania Zarządzanie skażonymi komunikatami. Można podpiąć zdarzenie uszkodzoną i wyłączenie usługi, akcje naprawcze i ponownie uruchomić. Na przykład `LookupId` w <xref:System.ServiceModel.MsmqPoisonMessageException> propagowane do `IErrorHandler` można zauważyć i kiedy błędy hosta usług, można użyć `System.Messaging` interfejsu API do odbierania wiadomości z kolejki przy użyciu `LookupId` do usunięcia komunikatu z kolejki i przechowywać wiadomości w niektórych magazynu zewnętrznego lub innej kolejki. Następnie można ponownie uruchomić `ServiceHost` Wznowienie normalnego przetwarzania. [Obsługa zanieczyszczonych komunikatów, obsługa w usłudze MSMQ 4.0](../../../../docs/framework/wcf/samples/poison-message-handling-in-msmq-4-0.md) przedstawia tego zachowania.  
  
## <a name="transaction-time-out-and-poison-messages"></a>Limit czasu transakcji i skażone komunikaty  
 Klasa błędów może wystąpić między kanał transportowy umieszczonych w kolejce i kod użytkownika. Te błędy mogą być wykryte przez wewnętrzne, takie jak warstwa zabezpieczeń wiadomości lub usługa wysyła logiki warstwy. Na przykład brakującego certyfikatu X.509 wykryte w warstwę zabezpieczeń protokołu SOAP i Brak akcji są przypadki, w którym komunikat Pobierz wysyłane do aplikacji. W takim przypadku modelu usługi porzuca wiadomość. Komunikat został odczytany w transakcji, a wynik dla transakcji nie może być podany limit czasu po pewnym czasie transakcji, dlatego przerwań i wiadomość jest przywracane do kolejki. Innymi słowy niektóre klasy błędów, transakcja nie przerwać natychmiast, ale czeka, aż upłynie limit czasu transakcji. Można zmodyfikować limitu czasu transakcji dla usługi przy użyciu <xref:System.ServiceModel.ServiceBehaviorAttribute>.  
  
 Aby zmienić limit czasu transakcji na podstawie całego komputera, zmodyfikuj plik machine.config i ustawianie limitu czasu odpowiednie transakcji. Należy zauważyć, że, w zależności od limitu czasu w transakcji, transakcja po pewnym czasie przerywa i powraca do kolejki i przerwania licznik jest zwiększany. Po pewnym czasie komunikat staje się zanieczyszczone i odpowiednie dyspozycji składa się zgodnie z ustawieniami użytkownika.  
  
## <a name="sessions-and-poison-messages"></a>Sesje i skażone komunikaty  
 Sesję ulega ponawiania tego samego i procedury obsługi komunikatów poison jako pojedynczą wiadomość. Właściwości, w wymienionych powyżej skażone komunikaty mają zastosowanie do całej sesji. Oznacza to, że podczas całej sesji jest próba uzyskania i przechodzi do kolejki utraconych wiadomości przez nadawcę lub końcowego kolejki poison wiadomości, jeśli komunikat zostanie odrzucony.  
  
## <a name="batching-and-poison-messages"></a>Przetwarzania wsadowego i skażonych komunikatów  
 Jeśli komunikat staje się zarządzanie skażonymi komunikatami, jest częścią partii całą partię zostanie wycofana i kanał wróci do odczytywania jeden komunikat w danym momencie. Aby uzyskać więcej informacji na temat dzielenia na partie, zobacz [tworzenie partii komunikatów w ramach transakcji](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
  
## <a name="poison-message-handling-for-messages-in-a-poison-queue"></a>Obsługa komunikatów w kolejce skażone wiadomości poison  
 Obsługa komunikatów poison nie kończy się na komunikat jest umieszczany w kolejce komunikatów poison. Komunikaty w kolejce komunikatów poison nadal należy odczytać i obsługiwane. Podzbiór ustawienia Obsługa komunikatów poison można użyć podczas odczytu komunikatów z ostatnim skażone kolejki podrzędnej. Ustawienia stosowane są `ReceiveRetryCount` i `ReceiveErrorHandling`. Możesz ustawić `ReceiveErrorHandling` upuść i Odrzuć lub błędów. `MaxRetryCycles` jest ignorowany i jest zgłaszany wyjątek, jeśli `ReceiveErrorHandling` jest ustawiony do przeniesienia.  
  
## <a name="windows-vista-windows-server-2003-and-windows-xp-differences"></a>Windows Vista, Windows Server 2003 i Windows XP różnice  
 Jak wspomniano wcześniej, nie wszystkie ustawienia Obsługa komunikatów poison dotyczą [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. Następujące kluczowe różnice między usługi kolejkowania komunikatów na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], [!INCLUDE[wxp](../../../../includes/wxp-md.md)], i [!INCLUDE[wv](../../../../includes/wv-md.md)] mają zastosowanie do obsługi komunikatów poison:  
  
-   Wiadomości usługi MSMQ w [!INCLUDE[wv](../../../../includes/wv-md.md)] obsługuje podkolejkami, podczas gdy [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nie obsługują podkolejek. Podkolejki są używane w obsłudze poison komunikatów. Kolejki ponownych prób i skażone kolejki są podkolejkami do kolejki aplikacji, który jest tworzony na podstawie ustawień poison postępowanie. `MaxRetryCycles` Decyduje o ile ponów podkolejkami do utworzenia. W związku z tym podczas uruchamiania na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] lub [!INCLUDE[wxp](../../../../includes/wxp-md.md)], `MaxRetryCycles` są ignorowane i `ReceiveErrorHandling.Move` jest niedozwolone.  
  
-   Wiadomości usługi MSMQ w [!INCLUDE[wv](../../../../includes/wv-md.md)] obsługuje ujemne potwierdzenia, podczas gdy [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)] nie obsługują. Negatywnego potwierdzenia z Menedżera kolejki odbierającej powoduje, że Menedżer kolejki wysyłania umieścić odrzuconych komunikatów w kolejce wiadomości utraconych. W efekcie `ReceiveErrorHandling.Reject` nie jest dozwolona z [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)].  
  
-   Wiadomości usługi MSMQ w [!INCLUDE[wv](../../../../includes/wv-md.md)] obsługuje podejmowana jest próba właściwości wiadomości, która utrzymuje liczbę razy dostarczanie komunikatów. Ta właściwość liczba przerwania nie jest dostępny na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)]. Usługi WCF przechowuje licznik przerwań w pamięci, więc istnieje możliwość, że ta właściwość nie może zawierać dokładną wartość, gdy ten sam komunikat jest odczytywany przez więcej niż jednej usługi WCF w farmie.  
  
## <a name="see-also"></a>Zobacz także

- [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [Różnice w funkcjach kolejkowania w systemach Windows Vista, Windows Server 2003 i Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)
- [Określanie i obsługa błędów w kontraktach i usługach](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
