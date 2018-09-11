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
ms.openlocfilehash: 37abcb6b3a8fdf4ef91d5e946a97db7ca1428ce8
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44365700"
---
# <a name="overview-of-synchronization-primitives"></a>Przegląd elementów podstawowych synchronizacji
<a name="top"></a> .NET Framework oferuje szeroką gamę elementów podstawowych synchronizacji, związanych z kontrolowaniem interakcje wątków i unikanie wyścigu. Te można grubsza podzielić na trzy kategorie: operacji blokowania, Sygnalizowanie i blokowane.  
  
 Kategorie nie są czyste, ani jasno określone: niektóre mechanizmy synchronizacji mają właściwości wielu kategorii; zdarzenia, które wersji pojedynczego wątku w danym momencie funkcjonalnie przypominają blokad; wydanie żadnej blokady mogą być uważane za sygnał; i operacje blokowane może służyć do konstruowania blokad. Kategorie są jednak nadal przydatne.  
  
 Należy pamiętać, że synchronizacji wątków jest wspólne. Jeśli jeszcze jeden wątek pomija mechanizm synchronizacji i uzyskuje dostęp do chronionego zasobu bezpośrednio, ten mechanizm synchronizacji nie może być skuteczne.  
  
 Ten przegląd zawiera następujące sekcje:  
  
-   [Blokowanie](#locking)  
  
-   [Sygnalizowanie](#signaling)  
  
-   [Lekkich typów synchronizacji](#lightweight_synchronization_types)  
  
-   [SpinWait](#spinwait)  
  
-   [Operacje blokowane](#interlocked_operations)  
  
<a name="locking"></a>   
## <a name="locking"></a>Blokowanie  
 Blokady zapewniają kontrolę nad zasobem jednemu wątkowi w czasie lub przez określoną liczbę wątków. Wątek, który żąda blokady na wyłączność, gdy blokada jest używana bloków, dopóki blokada staje się dostępna.  
  
### <a name="exclusive-locks"></a>Blokady na wyłączność  
 To najprostsza forma blokowania `lock` instrukcji w języku C# i `SyncLock` instrukcji w języku Visual Basic, które kontrolują dostęp do bloku kodu. Takie bloku jest często określane jako sekcję krytyczną. `lock` Instrukcji jest implementowany przy użyciu <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> i <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> metody który używa `try…finally` bloku, aby upewnić się, że blokada jest zwalniana.  
  
 Ogólnie rzecz biorąc, przy użyciu `lock` lub `SyncLock` instrukcję, aby chronić małych blokach kodu, nigdy nie obejmujące więcej niż jednej metody to najlepszy sposób, aby użyć <xref:System.Threading.Monitor> klasy. Mimo że jest to wydajne, <xref:System.Threading.Monitor> klasy jest podatna na oddzielony blokad i zakleszczenia.  
  
#### <a name="monitor-class"></a>Klasa monitora  
 <xref:System.Threading.Monitor> Klasa udostępnia dodatkowe funkcje, które mogą być używane w połączeniu z `lock` instrukcji:  
  
-   <xref:System.Threading.Monitor.TryEnter%2A> Metoda umożliwia wątku, który jest zablokowany, oczekiwanie na zasób po upływie określonego czasu. Zwraca wartość logiczną wskazującą, Powodzenie lub niepowodzenie, która może służyć do wykrywania i uniknięcia potencjalnego zakleszczenia.  
  
-   <xref:System.Threading.Monitor.Wait%2A> Metoda jest wywoływana przez wątek w sekcję krytyczną. Zrezygnuje kontrolę nad zasobem i blokuje aż zasób stanie się ponownie dostępny.  
  
-   <xref:System.Threading.Monitor.Pulse%2A> i <xref:System.Threading.Monitor.PulseAll%2A> metody umożliwiają wątek, który jest około zwolnienia blokady lub wywołać <xref:System.Threading.Monitor.Wait%2A> można umieścić w kolejce gotowe, jeden lub więcej wątków, dzięki czemu mogą oni uzyskać blokady.  
  
 Przekroczenie limitu czasu w <xref:System.Threading.Monitor.Wait%2A> przeciążenia metody umożliwia wątków oczekujących jako znak ucieczki w kolejce gotowe.  
  
 <xref:System.Threading.Monitor> Klasy może zapewnić blokowanie w wielu domenach aplikacji, jeśli obiekt używany do blokowania pochodzi od klasy <xref:System.MarshalByRefObject>.  
  
 <xref:System.Threading.Monitor> ma koligacji wątku. Oznacza to, że wątek, który wprowadzono monitora należy zamknąć, wywołując <xref:System.Threading.Monitor.Exit%2A> lub <xref:System.Threading.Monitor.Wait%2A>.  
  
 <xref:System.Threading.Monitor> Nie jest tworzone jako wystąpienia klasy. Jego metody są statyczne (`Shared` w języku Visual Basic) oraz umożliwia korzystanie z zablokować tworzone jako wystąpienia obiektu.  
  
 Aby uzyskać omówienie pojęć, zobacz [monitorów](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
#### <a name="mutex-class"></a>Mutex — Klasa  
 Żądanie wątków <xref:System.Threading.Mutex> poprzez wywołanie przeciążenia jego <xref:System.Threading.WaitHandle.WaitOne%2A> metody. Przeciążenia z limitów czasu podano, wątki czas oczekiwania. W odróżnieniu od <xref:System.Threading.Monitor> klasy obiektu mutex może być lokalne lub globalne. Globalne muteksy, nazywane również o nazwie Muteksy są widoczne w całym systemie operacyjnym i może służyć do synchronizacji wątków w wielu domenach aplikacji lub procesów. Lokalne muteksy pochodzić od <xref:System.MarshalByRefObject>i mogą być używane poza granice domeny aplikacji.  
  
 Ponadto <xref:System.Threading.Mutex> pochodzi od klasy <xref:System.Threading.WaitHandle>, co oznacza, że mogą być używane z sygnalizowanie udostępnionych przez nią mechanizmów <xref:System.Threading.WaitHandle>, takich jak <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, i <xref:System.Threading.WaitHandle.SignalAndWait%2A> metody.  
  
 Podobnie jak <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> ma koligacji wątku. W odróżnieniu od <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> jest tworzone jako wystąpienia obiektu.  
  
 Aby uzyskać omówienie pojęć, zobacz [muteksy](../../../docs/standard/threading/mutexes.md).  
  
#### <a name="spinlock-class"></a>Klasa strukturze SpinLock  
 Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], możesz użyć <xref:System.Threading.SpinLock> klasy, gdy obciążenie wymaga <xref:System.Threading.Monitor> spadku wydajności. Gdy <xref:System.Threading.SpinLock> napotka zablokowane sekcję krytyczną, ją po prostu uruchamia w pętli do momentu blokady staje się dostępna. Jeśli blokada jest posiadane bardzo krótki czas, rotowania może zapewnić lepszą wydajność niż blokowania. Jednak, jeśli blokada jest używana dla więcej niż kilkadziesiąt cykle, <xref:System.Threading.SpinLock> wykonuje równie dobrze jak <xref:System.Threading.Monitor>, ale użyje więcej cykli procesora CPU i dlatego mogą obniżyć wydajność innych wątkach lub procesach.  
  
### <a name="other-locks"></a>Inne blokad  
 Blokady nie muszą być wyłączności. Często jest to przydatne zezwolenie na ograniczonej liczbie wątków równoczesny dostęp do zasobu. Semaforów i reader_writer_lock są przeznaczone do sterowania tego rodzaju dostępu do zasobów w puli.  
  
#### <a name="readerwriterlock-class"></a>ReaderWriterLock — klasa  
 <xref:System.Threading.ReaderWriterLockSlim> Klasy adresy przypadek, gdzie wątek, który zmienia dane, moduł zapisujący musi mieć wyłącznego dostępu do zasobu. Jeśli moduł zapisujący nie jest aktywne, dowolną liczbę czytników można uzyskać dostępu do zasobu (na przykład przez wywołanie metody <xref:System.Threading.ReaderWriterLockSlim.EnterReadLock%2A> metody). Gdy wątek żąda wyłącznego dostępu (na przykład przez wywołanie metody <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A> metoda), czytnika kolejnych żądań bloku dopiero po zamknięciu wszystkich istniejących czytelników blokady i Edytor wprowadził i zakończony blokady.  
  
 <xref:System.Threading.ReaderWriterLockSlim> ma koligacji wątku.  
  
 Aby uzyskać omówienie pojęć, zobacz [blokuje moduł zapisujący czytnika](../../../docs/standard/threading/reader-writer-locks.md).  
  
#### <a name="semaphore-class"></a>Semaphore — Klasa  
 <xref:System.Threading.Semaphore> Klasy zezwala na określoną liczbę wątków, aby uzyskać dostęp do zasobu. Dodatkowe wątki nie żąda bloku zasobów, aż wątek zwalnia semafora.  
  
 Podobnie jak <xref:System.Threading.Mutex> klasy <xref:System.Threading.Semaphore> pochodzi od klasy <xref:System.Threading.WaitHandle>. Ponadto, takich jak <xref:System.Threading.Mutex>, <xref:System.Threading.Semaphore> może być lokalne lub globalne. Może służyć poza granice domeny aplikacji.  
  
 W odróżnieniu od <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex>, i <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Semaphore> nie mają koligacji wątku. Oznacza to, że może służyć w scenariuszach, gdzie jeden wątek uzyskuje semafora i inny do wydania.  
  
 Aby uzyskać omówienie pojęć, zobacz [Semaphore i SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).  
  
 <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> jest uproszczone semafora synchronizacji w obrębie granicy pojedynczego procesu.  
  
 [Powrót do początku](#top)  
  
<a name="signaling"></a>   
## <a name="signaling"></a>Sygnalizowania  
 Najprostszym sposobem na oczekiwanie na sygnał z innego wątku jest wywołanie <xref:System.Threading.Thread.Join%2A> metody, która blokuje ukończenie innego wątku. <xref:System.Threading.Thread.Join%2A> ma dwa przeciążenia, zezwalających na zablokowany wątek zerwać czas oczekiwania, po upływie określonego interwału.  
  
 Uchwyty oczekiwania na zapewnia znacznie większego zestawu oczekiwania i sygnalizowanie możliwości.  
  
### <a name="wait-handles"></a>Dojścia oczekiwania  
 Uchwyty oczekiwania na pochodzić od <xref:System.Threading.WaitHandle> klasy, która z kolei pochodzi od klasy <xref:System.MarshalByRefObject>. W związku z tym uchwytami oczekiwania może służyć do synchronizowania działania wątków poza granice domeny aplikacji.  
  
 Wątki na oczekiwania obsłuży przez wywołanie metody wystąpienia <xref:System.Threading.WaitHandle.WaitOne%2A> lub jednej z metod statycznych <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, lub <xref:System.Threading.WaitHandle.SignalAndWait%2A>. Jak są wydawane zależy od wywołano metodę, która oraz od rodzaju dojść oczekiwania.  
  
 Aby uzyskać omówienie pojęć, zobacz [oczekiwania obsługuje](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489).  
  
#### <a name="event-wait-handles"></a>Uchwyty oczekiwania na zdarzenie  
 Uchwyty oczekiwania na zdarzenie obejmują <xref:System.Threading.EventWaitHandle> klasa i jej klasy pochodne <xref:System.Threading.AutoResetEvent> i <xref:System.Threading.ManualResetEvent>. Wątki są zwalniane z dojścia oczekiwania zdarzenie, kiedy dojście oczekiwania zdarzenie jest sygnalizowane przez wywołanie jego <xref:System.Threading.EventWaitHandle.Set%2A> metody lub za pomocą <xref:System.Threading.WaitHandle.SignalAndWait%2A> metody.  
  
 Zdarzenie poczekaj uchwyty albo samodzielnie automatycznie resetować, takich jak powierzchniowe (s), która zezwala na tylko jeden wątek za pośrednictwem za każdym razem jest sygnalizowane lub muszą zostać zresetowane ręcznie, takie jak bramy, który jest zamknięty, dopóki sygnalizowane, a następnie otwórz aż ktoś zostanie zamknięty. Jak sugerują nazwy <xref:System.Threading.AutoResetEvent> i <xref:System.Threading.ManualResetEvent> reprezentują byłego i ostatniej, odpowiednio. <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> jest to uproszczone zdarzenie synchronizacji w obrębie granicy pojedynczego procesu.  
  
 <xref:System.Threading.EventWaitHandle> Może reprezentować dowolnego typu zdarzenia i może być lokalne lub globalne. Klasy pochodne <xref:System.Threading.AutoResetEvent> i <xref:System.Threading.ManualResetEvent> zawsze są lokalne.  
  
 Uchwyty oczekiwania na zdarzenie nie mają koligacji wątku. Wątek może sygnał dojścia oczekiwania.  
  
 Aby uzyskać omówienie pojęć, zobacz [EventWaitHandle, autoresetevent —, CountdownEvent ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).  
  
#### <a name="mutex-and-semaphore-classes"></a>Mutex i klasy semafora  
 Ponieważ <xref:System.Threading.Mutex> i <xref:System.Threading.Semaphore> klasy pochodzić od <xref:System.Threading.WaitHandle>, może służyć za pomocą metod statycznych <xref:System.Threading.WaitHandle>. Na przykład, można użyć wątku <xref:System.Threading.WaitHandle.WaitAll%2A> metodę, aby poczekać, aż wszystkie trzy następujące czynności są spełnione: <xref:System.Threading.EventWaitHandle> jest sygnalizowane <xref:System.Threading.Mutex> jest zwalniana i <xref:System.Threading.Semaphore> wydaniu. Podobnie, można użyć wątku <xref:System.Threading.WaitHandle.WaitAny%2A> metodę, aby poczekać, aż jeden z tych warunków jest spełniony.  
  
 Aby uzyskać <xref:System.Threading.Mutex> lub <xref:System.Threading.Semaphore>, jest sygnalizowane oznacza, że zostały udostępnione. Jeśli albo typ jest używany jako pierwszy argument <xref:System.Threading.WaitHandle.SignalAndWait%2A> metody, jest on zwalniany. W przypadku właściwości <xref:System.Threading.Mutex>, który ma koligacji wątku, jest zgłaszany wyjątek, jeśli wątek wywołujący nie jest właścicielem obiektu mutex. Jak wspomniano wcześniej, semaforów nie mają koligacji wątku.  
  
#### <a name="barrier"></a>Bariera  
 <xref:System.Threading.Barrier> Klasy zapewnia sposób cyklicznie synchronizacji wielu wątków, tak aby wszystkie bloku, w tym samym punktu i poczekaj, aż wszystkie wątki do ukończenia. Barierę jest przydatne, gdy jeden lub więcej wątków wymagają wyników z innego wątku przed przejściem do następnej fazy algorytmu. Aby uzyskać więcej informacji, zobacz [barierę](../../../docs/standard/threading/barrier.md).  
  
 [Powrót do początku](#top)  
  
<a name="lightweight_synchronization_types"></a>   
## <a name="lightweight-synchronization-types"></a>Lekkich typów synchronizacji  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], możesz użyć podstawowych synchronizacji, które zapewniają wysoką wydajność dzięki unikaniu kosztownych poleganie na Win32 jądra obiektów, takich jak czekać dojść, zawsze, gdy jest to możliwe. Ogólnie rzecz biorąc należy użyć tych typów, gdy krótkie czasy oczekiwania i tylko wtedy, gdy nastąpiła oryginalnego typy synchronizacji i okazały się niezadowalające. Uproszczone typów nie można używać w scenariuszach wymagających komunikacji między procesami.  
  
-   <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> to Uproszczona wersja <xref:System.Threading.Semaphore?displayProperty=nameWithType>.  
  
-   <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> to Uproszczona wersja <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>.  
  
-   <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> reprezentuje zdarzenie, które staje się sygnalizowane, gdy ich liczba jest równa zero.  
  
-   <xref:System.Threading.Barrier?displayProperty=nameWithType> Umożliwia wielu wątków zsynchronizować ze sobą bez konieczności kontroli przez wątek główny. Barierę uniemożliwia każdy wątek kontynuowanie dopóki wszystkie wątki osiągną określony punkt.  
  
 [Powrót do początku](#top)  
  
<a name="spinwait"></a>   
## <a name="spinwait"></a>SpinWait  
 Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], możesz użyć <xref:System.Threading.SpinWait?displayProperty=nameWithType> struktury, gdy wątek ma czekać na zdarzenie ma być zasygnalizowany lub warunek do spełnienia, ale gdy czas oczekiwania rzeczywiste powinien przypadać wcześniej niż czas oczekiwania, wymagane przez przy użyciu dojścia oczekiwania lub otherwi SE blokuje bieżący wątek. Za pomocą <xref:System.Threading.SpinWait>, można określić krótki okres pokrętła oczekiwania, a następnie uzyskanie (np. przez oczekiwania lub uśpiony) tylko wtedy, gdy w określonym czasie nie został spełniony warunek.  
  
 [Powrót do początku](#top)  
  
<a name="interlocked_operations"></a>   
## <a name="interlocked-operations"></a>Operacje blokowane  
 Operacje blokowane są proste niepodzielne operacje wykonywane na lokalizacji w pamięci przy użyciu metod statycznych <xref:System.Threading.Interlocked> klasy. Te niepodzielne operacje obejmują dodawanie, Zwiększ oraz dekrementacja, exchange warunkowego programu exchange w zależności od porównania i operacji odczytu dla 64-bitowych wartości na platformach 32-bitowych.  
  
> [!NOTE]
>  Gwarancja niepodzielności jest ograniczona do poszczególnych operacji; gdy wiele operacji, należy wykonać jako zespół, należy użyć bardziej gruboziarnistych mechanizm synchronizacji.  
  
 Mimo że żaden z tych operacji nie jest blokady lub sygnały, ich może służyć do konstruowania blokad i sygnałów. Ponieważ są one natywnych w systemie operacyjnym Windows, operacje blokowane są bardzo szybkie.  
  
 Operacje blokowane może służyć gwarancje pamięci volatile do pisania aplikacji, które wykazują współbieżności nieblokującej na poziomie zaawansowanym. Jednak wymagają one programowanie zaawansowane, niskiego poziomu, dzięki czemu można w większości przypadków proste blokad lepszym rozwiązaniem.  
  
 Aby uzyskać omówienie pojęć, zobacz [operacji Blokowanej](../../../docs/standard/threading/interlocked-operations.md).  
  
## <a name="see-also"></a>Zobacz także

- [Synchronizowanie danych na potrzeby wielowątkowości](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
- [Monitory](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
- [Muteksy](../../../docs/standard/threading/mutexes.md)  
- [Semaphore i SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [Uchwyty oczekiwania](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
- [Operacje blokowane](../../../docs/standard/threading/interlocked-operations.md)  
- [reader_writer_lock, klasa](../../../docs/standard/threading/reader-writer-locks.md)  
- [Barrier](../../../docs/standard/threading/barrier.md)  
- [SpinWait](../../../docs/standard/threading/spinwait.md)  
- [SpinLock](../../../docs/standard/threading/spinlock.md)
