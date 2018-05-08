---
title: Przegląd elementów podstawowych synchronizacji
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e35c2337ff7e416cb5f2c869f8ede160e05d369f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="overview-of-synchronization-primitives"></a>Przegląd elementów podstawowych synchronizacji
<a name="top"></a> .NET Framework zapewnia szereg elementy podstawowe synchronizacji kontroli interakcji wątków i unikanie wyścigu. Te można około podzielone na trzy kategorie: blokowanie sygnalizowania i blokowanego operacji.  
  
 Kategorie nie są porządek ani jasno określone: niektóre mechanizmy synchronizacji mają cechy wiele kategorii; zdarzenia, które wersji pojedynczego wątku w czasie funkcjonalnie przypominają blokad; Wersja żadnej blokady można traktować jako sygnał; i operacje blokowane może służyć do skonstruowania blokad. Kategorie są jednak nadal użyteczne.  
  
 Należy pamiętać, że synchronizacja wątku jest współpracy. Jeśli jeszcze jeden wątek pomija mechanizm synchronizacji i uzyskuje bezpośredni dostęp do chronionych zasobów, mechanizmu synchronizacji nie może być skuteczne.  
  
 Ten przegląd zawiera następujące sekcje:  
  
-   [Blokowanie](#locking)  
  
-   [Sygnalizowanie](#signaling)  
  
-   [Typy lekkie synchronizacji](#lightweight_synchronization_types)  
  
-   [SpinWait](#spinwait)  
  
-   [Operacje blokowane](#interlocked_operations)  
  
<a name="locking"></a>   
## <a name="locking"></a>Blokowanie  
 Blokady zapewniają kontrolę nad zasobem jeden wątek w czasie, lub do określonej liczby wątków. Wątek, który żąda w trybie wyłączności, gdy blokady jest w użyciu bloków do momentu udostępnienia blokady.  
  
### <a name="exclusive-locks"></a>Blokady na wyłączność  
 Jest to najprostsza forma blokowania `lock` instrukcji w języku C# i `SyncLock` instrukcji w języku Visual Basic, która kontroluje dostęp do bloku kodu. Takie bloku jest często nazywany sekcja krytyczna. `lock` Instrukcji jest implementowane za pomocą <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> i <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> metod i używa `try…catch…finally` bloku, aby upewnić się, jest zwolnienie blokady.  
  
 Ogólnie rzecz biorąc, przy użyciu `lock` lub `SyncLock` instrukcji, aby chronić małe bloki kodu, nigdy nie obejmujące więcej niż jedną metodę to najlepszy sposób, aby użyć <xref:System.Threading.Monitor> klasy. Chociaż wydajne, <xref:System.Threading.Monitor> klasy jest podatne na oddzielony blokad i zakleszczenia.  
  
#### <a name="monitor-class"></a>Klasa monitora  
 <xref:System.Threading.Monitor> Klasa udostępnia dodatkowe funkcje, które mogą być używane w połączeniu z `lock` instrukcji:  
  
-   <xref:System.Threading.Monitor.TryEnter%2A> Metoda pozwala wątku, który jest zablokowana i czeka na zasobów po upływie określonego czasu. Zwraca wartość logiczną wskazującą powodzenie lub niepowodzenie, która może służyć do wykrywania i uniknąć potencjalnego zakleszczenia.  
  
-   <xref:System.Threading.Monitor.Wait%2A> Metoda jest wywoływana przez wątek w sekcji krytycznych. Udostępnia kontrolą zasobu i bloków do czasu ponownie zasób jest dostępny.  
  
-   <xref:System.Threading.Monitor.Pulse%2A> i <xref:System.Threading.Monitor.PulseAll%2A> metody umożliwiają wątku, który jest około zwalnia blokadę lub <xref:System.Threading.Monitor.Wait%2A> można umieścić w kolejce gotowy, co najmniej jeden wątek, tak aby ich przejęcie blokady.  
  
 Limity czasu na <xref:System.Threading.Monitor.Wait%2A> przeciążenia metody Zezwalaj wątków oczekujących wprowadzić do kolejki gotowe.  
  
 <xref:System.Threading.Monitor> Klasy zapewniają blokowania w wielu domenach aplikacji, jeśli obiekt używany do blokowania pochodną <xref:System.MarshalByRefObject>.  
  
 <xref:System.Threading.Monitor> ma koligacji wątku. Oznacza to, wywołując musi się zakończyć wątku, który wprowadzono monitor <xref:System.Threading.Monitor.Exit%2A> lub <xref:System.Threading.Monitor.Wait%2A>.  
  
 <xref:System.Threading.Monitor> Klasa nie jest tworzone jako wystąpienia. Metody tej klasy są statyczne (`Shared` w języku Visual Basic) i działa na zablokować tworzone jako wystąpienia obiektu.  
  
 Omówienie koncepcji, zobacz [monitorów](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
#### <a name="mutex-class"></a>Mutex — Klasa  
 Żądanie wątków <xref:System.Threading.Mutex> wywołując przeciążenia jego <xref:System.Threading.WaitHandle.WaitOne%2A> metody. Przeciążenia z limitów czasu podano umożliwia wątków czas oczekiwania. W odróżnieniu od <xref:System.Threading.Monitor> klasy obiektu mutex może być lokalnego lub globalnego. Globalne muteksy, skrót o nazwie Muteksy są widoczne w systemie operacyjnym i może służyć do synchronizowania wątków w wielu domenach aplikacji lub procesów. Lokalne muteksy pochodzi od <xref:System.MarshalByRefObject>i można go używać między granicami domeny aplikacji.  
  
 Ponadto <xref:System.Threading.Mutex> pochodną <xref:System.Threading.WaitHandle>, co oznacza, że mogą być używane z mechanizmów sygnalizowania, obsługiwanych przez <xref:System.Threading.WaitHandle>, takich jak <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, i <xref:System.Threading.WaitHandle.SignalAndWait%2A> metody.  
  
 Podobnie jak <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> ma koligacji wątku. W odróżnieniu od <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> jest tworzone jako wystąpienia obiektu.  
  
 Omówienie koncepcji, zobacz [muteksy](../../../docs/standard/threading/mutexes.md).  
  
#### <a name="spinlock-class"></a>Klasa struktury SpinLock  
 Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć <xref:System.Threading.SpinLock> klasy, jeśli obciążenie wymagane przy <xref:System.Threading.Monitor> powoduje spadek wydajności. Gdy <xref:System.Threading.SpinLock> napotka zablokowana sekcja krytyczna ją po prostu obraca w pętli do momentu udostępnienia blokady. Jeśli blokady odbywa się bardzo krótki czas, Obracająca może zapewnić lepszą wydajność niż blokowania. Jednak, jeśli blokada jest używana dla więcej niż kilka dziesiątki cykle, <xref:System.Threading.SpinLock> wykonuje także po prostu jako <xref:System.Threading.Monitor>, ale będzie używać więcej cykli procesora CPU i w związku z tym mogą obniżyć wydajność innych wątków lub procesów.  
  
### <a name="other-locks"></a>Inne blokad  
 Blokady nie musi być wyłącznego. Często jest to przydatne umożliwia ograniczoną liczbę wątków współbieżnych dostęp do zasobu. Semaforów i reader_writer_lock są przeznaczone do kontrolowania tego rodzaju dostęp do puli zasobów.  
  
#### <a name="readerwriterlock-class"></a>ReaderWriterLock — klasa  
 <xref:System.Threading.ReaderWriterLockSlim> Klasy adresów przypadek, w którym wątku, który zmienia danych, moduł zapisujący musi mieć wyłącznego dostępu do zasobu. Jeśli moduł zapisujący nie jest aktywne, dowolną liczbę czytników można uzyskać dostępu do zasobu (na przykład wywołując <xref:System.Threading.ReaderWriterLockSlim.EnterReadLock%2A> metody). Wątek żądanie wyłącznego dostępu (na przykład wywołując <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A> metody), czytnika kolejnych żądań bloku dopiero po zamknięciu wszystkich istniejących czytelników blokady i wprowadził twórcę i zakończony blokady.  
  
 <xref:System.Threading.ReaderWriterLockSlim> ma koligacji wątku.  
  
 Omówienie koncepcji, zobacz [blokuje moduł zapisujący czytnika](../../../docs/standard/threading/reader-writer-locks.md).  
  
#### <a name="semaphore-class"></a>Semaphore — Klasa  
 <xref:System.Threading.Semaphore> Klasa umożliwia określoną liczbę wątków, aby uzyskać dostęp do zasobu. Żądanie bloku zasobu, dopóki wątku zwalnia semafora dodatkowe wątki.  
  
 Podobnie jak <xref:System.Threading.Mutex> klasy <xref:System.Threading.Semaphore> pochodną <xref:System.Threading.WaitHandle>. Chce także <xref:System.Threading.Mutex>, <xref:System.Threading.Semaphore> może być lokalnego lub globalnego. Może służyć poza granice domeny aplikacji.  
  
 W odróżnieniu od <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, i <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Semaphore> nie mają koligacji wątku. Oznacza to, że można w scenariuszach, w której jeden wątek uzyskuje semafor i zwolnieniem innego.  
  
 Omówienie koncepcji, zobacz [semafor i klasa SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).  
  
 <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> to lekkie semafora synchronizacji w obrębie granicy jednego procesu.  
  
 [Powrót do początku](#top)  
  
<a name="signaling"></a>   
## <a name="signaling"></a>Sygnalizowania  
 Najprostszym sposobem oczekiwanie na sygnał z innego wątku jest wywołanie <xref:System.Threading.Thread.Join%2A> metodę, która blokuje dopiero po zakończeniu innego wątku. <xref:System.Threading.Thread.Join%2A> ma dwa przeciążenia, zezwalających na zablokowanych wątków przerwanie poza czas oczekiwania, po upływie określonego interwału.  
  
 Uchwyty oczekiwania Podaj znacznie większego zestawu oczekiwania i sygnalizowania możliwości.  
  
### <a name="wait-handles"></a>Dojścia oczekiwania  
 Uchwyty oczekiwania pochodzi od <xref:System.Threading.WaitHandle> klasy, która z kolei jest pochodną <xref:System.MarshalByRefObject>. W związku z tym uchwyty oczekiwania może służyć do synchronizowania działania wątków poza granice domeny aplikacji.  
  
 Blok wątków na oczekiwania obsługuje przez wywołanie metody wystąpienia <xref:System.Threading.WaitHandle.WaitOne%2A> lub jednej z metod statycznych <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, lub <xref:System.Threading.WaitHandle.SignalAndWait%2A>. Jak są wydawane zależy od wywołano metodę oraz od rodzaju uchwyty oczekiwania.  
  
 Omówienie koncepcji, zobacz [oczekiwania obsługuje](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489).  
  
#### <a name="event-wait-handles"></a>Uchwyty oczekiwania na zdarzenie  
 Uchwyty oczekiwania na zdarzenie obejmują <xref:System.Threading.EventWaitHandle> klasy i jej klas pochodnych <xref:System.Threading.AutoResetEvent> i <xref:System.Threading.ManualResetEvent>. Wątki są zwalniane z dojścia oczekiwania podczas obsługi zdarzenia oczekiwania zostanie zasygnalizowane przez wywołanie jego <xref:System.Threading.EventWaitHandle.Set%2A> metody lub za pomocą <xref:System.Threading.WaitHandle.SignalAndWait%2A> — metoda.  
  
 Zdarzenie poczekaj uchwytów albo samodzielnie automatycznie resetować, takich jak turnstile, który umożliwia tylko jeden wątek za pośrednictwem za każdym razem zostanie zasygnalizowane lub musi zostać zresetowany ręcznie, takie jak brama jest zamknięty, dopóki sygnalizuje, a następnie otwórz dopóki ktoś zostanie zamknięte. Jak oznaczać ich nazw, <xref:System.Threading.AutoResetEvent> i <xref:System.Threading.ManualResetEvent> reprezentują wcześniejsze i drugie, odpowiednio. <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> jest to lekkie zdarzenie synchronizacji w obrębie granicy jednego procesu.  
  
 <xref:System.Threading.EventWaitHandle> Może reprezentować obu typów zdarzeń i może być lokalnego lub globalnego. Klasy pochodne <xref:System.Threading.AutoResetEvent> i <xref:System.Threading.ManualResetEvent> zawsze znajdują się lokalnie.  
  
 Uchwyty oczekiwania na zdarzenie nie mają koligacji wątku. Którymkolwiek wątku mogą sygnalizować dojścia oczekiwania.  
  
 Omówienie koncepcji, zobacz [EventWaitHandle, autoresetevent —, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).  
  
#### <a name="mutex-and-semaphore-classes"></a>Mutex i klasy semafora  
 Ponieważ <xref:System.Threading.Mutex> i <xref:System.Threading.Semaphore> pochodną klasy <xref:System.Threading.WaitHandle>, mogą być używane z metod statycznych <xref:System.Threading.WaitHandle>. Na przykład można użyć wątku <xref:System.Threading.WaitHandle.WaitAll%2A> metody poczekać, aż spełnione są wszystkie trzy z następujących czynności: <xref:System.Threading.EventWaitHandle> zostanie zasygnalizowane <xref:System.Threading.Mutex> wydaniu i <xref:System.Threading.Semaphore> zostanie zwolniony. Analogicznie, można użyć wątku <xref:System.Threading.WaitHandle.WaitAny%2A> metody oczekiwanie na jeden z tych warunków ma wartość true.  
  
 Aby uzyskać <xref:System.Threading.Mutex> lub <xref:System.Threading.Semaphore>, jest sygnalizowane oznacza, że został wydany. Jeśli albo typ jest używany jako pierwszy argument funkcji <xref:System.Threading.WaitHandle.SignalAndWait%2A> metody, jego zwolnienia. W przypadku liczby <xref:System.Threading.Mutex>, który ma koligacji wątków, jest zwracany wyjątek, jeśli wątek wywołujący nie jest właścicielem obiektu mutex. Jak wspomniano wcześniej, semaforów nie mają koligacji wątku.  
  
#### <a name="barrier"></a>Bariera  
 <xref:System.Threading.Barrier> Klasa udostępnia sposób cyklicznie synchronizacji wiele wątków, tak aby wszystkie bloku, w tym samym punktu i poczekaj, aż wszystkie wątki do wykonania. Bariera jest przydatne, gdy jeden lub więcej wątków wymagają wyniki inny wątek przed kontynuowaniem do następnej fazy algorytmu. Aby uzyskać więcej informacji, zobacz [bariery](../../../docs/standard/threading/barrier.md).  
  
 [Powrót do początku](#top)  
  
<a name="lightweight_synchronization_types"></a>   
## <a name="lightweight-synchronization-types"></a>Typy lekkie synchronizacji  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], można użyć elementy podstawowe synchronizacji, które zapewniają szybkie wydajności dzięki unikaniu kosztowne zależność od jądra systemu Win32 obiekty, takie jak oczekiwania dojść, jeśli to możliwe. Ogólnie rzecz biorąc gdy krótki czas oczekiwania, i tylko wtedy, gdy nastąpiła oryginalnego typy synchronizacji i będzie niezadowalające należy używać tych typów. Nie można użyć typu lightweight w scenariuszach, które wymagają komunikacji między procesami.  
  
-   <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> jest to Uproszczona wersja <xref:System.Threading.Semaphore?displayProperty=nameWithType>.  
  
-   <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> jest to Uproszczona wersja <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>.  
  
-   <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> reprezentuje zdarzenie, które staje się sygnalizowane po jego liczba jest równa zero.  
  
-   <xref:System.Threading.Barrier?displayProperty=nameWithType> Umożliwia wiele wątków do synchronizacji ze sobą bez konieczności formantu głównego wątku. Bariery zapobiega każdy wątek kontynuować dopóki wszystkie wątki osiągnięto określony punkt.  
  
 [Powrót do początku](#top)  
  
<a name="spinwait"></a>   
## <a name="spinwait"></a>SpinWait  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], można użyć <xref:System.Threading.SpinWait?displayProperty=nameWithType> struktury, gdy wątek ma oczekiwać na zdarzenie, aby być sygnalizowane lub warunek jest spełniony, a czas oczekiwania rzeczywiste powinien być krótszy niż czas oczekiwania na wymagane przez przy użyciu dojścia oczekiwania lub otherwi SE blokuje bieżącego wątku. Przy użyciu <xref:System.Threading.SpinWait>, można określić krótkiego okresu pokrętła czasu oczekiwania, a następnie użyć instrukcji yield (na przykład przez Oczekiwanie lub uśpiony) tylko wtedy, gdy nie został spełniony warunek w określonym czasie.  
  
 [Powrót do początku](#top)  
  
<a name="interlocked_operations"></a>   
## <a name="interlocked-operations"></a>Operacje blokowane  
 Operacje blokowane są prostych operacji niepodzielnych w lokalizacji pamięci z zastosowaniem metod statycznych <xref:System.Threading.Interlocked> klasy. Tych operacjach niepodzielnych obejmują dodawanie, zwiększyć i zmniejszyć, exchange warunkowego programu exchange, w zależności od porównanie oraz operacje dla 64-bitowych wartości na platformach 32-bitowych odczytu.  
  
> [!NOTE]
>  Gwarancja niepodzielność jest ograniczona do poszczególnych działań; gdy jako jednostka odbywa się wiele operacji, należy użyć więcej coarse-grained mechanizmu synchronizacji.  
  
 Mimo że żaden z tych operacji nie jest blokady lub sygnałów, ich może służyć do skonstruowania sygnałów i blokad. Ponieważ są one natywnego systemu operacyjnego, operacje blokowane są bardzo szybkie.  
  
 Operacje blokowane umożliwia gwarancje volatile pamięci pisać aplikacje, które wykazują współbieżności nieblokujące zaawansowane. Jednak wymagają one programowania zaawansowane, niskiego poziomu, więc w większości przypadków proste blokady są lepszym rozwiązaniem.  
  
 Omówienie koncepcji, zobacz [operacji Blokowanej](../../../docs/standard/threading/interlocked-operations.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Synchronizowanie danych na potrzeby wielowątkowości](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 [Monitory](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 [Muteksy](../../../docs/standard/threading/mutexes.md)  
 [Semaphore i SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [Uchwyty oczekiwania](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [Operacje blokowane](../../../docs/standard/threading/interlocked-operations.md)  
 [reader_writer_lock, klasa](../../../docs/standard/threading/reader-writer-locks.md)  
 [Barrier](../../../docs/standard/threading/barrier.md)  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [SpinLock](../../../docs/standard/threading/spinlock.md)
