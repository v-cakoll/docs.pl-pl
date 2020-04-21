---
title: Przegląd elementów podstawowych synchronizacji
description: Dowiedz się więcej o egoiskach synchronizacji wątku .NET używanych do synchronizowania dostępu do udostępnionego zasobu lub interakcji wątku sterującego
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
ms.openlocfilehash: 7347c9b40f150febc6a163ae3aa3267123ea0e9d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739374"
---
# <a name="overview-of-synchronization-primitives"></a>Przegląd elementów podstawowych synchronizacji

.NET udostępnia zakres typów, których można użyć do synchronizowania dostępu do zasobu udostępnionego lub koordynowania interakcji wątku.

> [!IMPORTANT]
> Użyj tego samego pierwotnego wystąpienia synchronizacji, aby chronić dostęp do zasobu udostępnionego. Jeśli używasz różnych pierwotnych wystąpień synchronizacji do ochrony tego samego zasobu, ominiesz ochronę zapewnianą przez prymitywne synchronizacji.

## <a name="waithandle-class-and-lightweight-synchronization-types"></a>Klasa WaitHandle i lekkie typy synchronizacji

Wiele wierzchołków synchronizacji platformy <xref:System.Threading.WaitHandle?displayProperty=nameWithType> .NET pochodzi z klasy, która hermetyzuje dojście do synchronizacji natywnego systemu operacyjnego i używa mechanizmu sygnalizacji do interakcji z wątkami. Zajęcia te obejmują:

- <xref:System.Threading.Mutex?displayProperty=nameWithType>, który przyznaje wyłączny dostęp do zasobu wspólnego. Stan obiektu mutex jest sygnalizowany, jeśli żaden wątek nie jest jego właścicielem.
- <xref:System.Threading.Semaphore?displayProperty=nameWithType>, który ogranicza liczbę wątków, które mogą uzyskać dostęp do zasobu udostępnionego lub puli zasobów jednocześnie. Stan semafora jest ustawiona na sygnalizowane, gdy jego liczba jest większa niż zero i nonsignaled, gdy jego liczba wynosi zero.
- <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, który reprezentuje zdarzenie synchronizacji wątku i może być w stanie sygnalizowanym lub niepodpisanym.
- <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>, który pochodzi <xref:System.Threading.EventWaitHandle> z i, gdy sygnalizowane, resetuje się automatycznie do stanu niesygnowanego po zwolnieniu jednego wątku oczekiwania.
- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>, który pochodzi <xref:System.Threading.EventWaitHandle> z i, gdy sygnalizowane, pozostaje w <xref:System.Threading.EventWaitHandle.Reset%2A> stanie sygnalizowanym, dopóki metoda jest wywoływana.

W .NET Framework, <xref:System.Threading.WaitHandle> ponieważ <xref:System.MarshalByRefObject?displayProperty=nameWithType>pochodzi od , te typy mogą służyć do synchronizowania działań wątków w granicach domeny aplikacji.

W programach .NET Framework i .NET Core niektóre z tych typów mogą reprezentować nazwane uchwyty synchronizacji systemu, które są widoczne w całym systemie operacyjnym i mogą być używane do synchronizacji między procesami:

- <xref:System.Threading.Mutex>(.NET Framework i .NET Core),
- <xref:System.Threading.Semaphore>(.NET Framework i .NET Core w systemie Windows),
- <xref:System.Threading.EventWaitHandle>(.NET Framework i .NET Core w systemie Windows).

Aby uzyskać więcej <xref:System.Threading.WaitHandle> informacji, zobacz odwołanie do interfejsu API.

Lekkie typy synchronizacji nie opierają się na podstawowych uchwytach systemu operacyjnego i zazwyczaj zapewniają lepszą wydajność. Jednak nie można ich używać do synchronizacji między procesami. Użyj tych typów do synchronizacji wątków w ramach jednej aplikacji.

Niektóre z tych typów są alternatywami <xref:System.Threading.WaitHandle>dla typów pochodzących z . Na przykład <xref:System.Threading.SemaphoreSlim> jest lekką <xref:System.Threading.Semaphore>alternatywą dla .

## <a name="synchronization-of-access-to-a-shared-resource"></a>Synchronizacja dostępu do zasobu udostępnionego

.NET zapewnia zakres ujedkwytów synchronizacji do kontrolowania dostępu do zasobu udostępnionego przez wiele wątków.

### <a name="monitor-class"></a>klasa monitora

Klasa <xref:System.Threading.Monitor?displayProperty=nameWithType> udziela wzajemnie wyłącznego dostępu do zasobu udostępnionego przez uzyskanie lub zwolnienie blokady na obiekcie, który identyfikuje zasób. Podczas blokady jest utrzymywany, wątek, który posiada blokadę można ponownie uzyskać i zwolnić blokady. Każdy inny wątek jest zablokowany <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> przed uzyskaniem blokady i metoda czeka, aż blokada zostanie zwolniona. Metoda <xref:System.Threading.Monitor.Enter%2A> uzyskuje zwolnione blokady. Można również użyć <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> metody, aby określić ilość czasu, podczas którego wątek próbuje uzyskać blokadę. Ponieważ <xref:System.Threading.Monitor> klasa ma koligacji wątku, wątek, który uzyskał <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> blokadę musi zwolnić blokady przez wywołanie metody.

Można koordynować interakcję wątków, które uzyskać blokadę na <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>tym <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> samym obiekcie za pomocą , i metody.

Aby uzyskać więcej <xref:System.Threading.Monitor> informacji, zobacz odwołanie do interfejsu API.

> [!NOTE]
> Użyj [lock](../../csharp/language-reference/keywords/lock-statement.md) instrukcji w języku C# i [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) instrukcji w języku Visual Basic <xref:System.Threading.Monitor> do synchronizacji dostępu do zasobu udostępnionego zamiast przy użyciu klasy bezpośrednio. Te instrukcje są implementowane <xref:System.Threading.Monitor.Exit%2A> przy `try…finally` użyciu <xref:System.Threading.Monitor.Enter%2A> i metody i bloku, aby upewnić się, że nabyte blokady jest zawsze zwolniony.

### <a name="mutex-class"></a>Mutex — Klasa

Klasa, <xref:System.Threading.Mutex?displayProperty=nameWithType> na <xref:System.Threading.Monitor>przykład, udziela wyłącznego dostępu do zasobu udostępnionego. Użyj jednego z Przeciążenia Metody [Mutex.WaitOne,](<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>) aby zażądać własności obiektu mutex. Like <xref:System.Threading.Monitor> <xref:System.Threading.Mutex> , ma koligacji wątku i wątku, który <xref:System.Threading.Mutex.ReleaseMutex%2A?displayProperty=nameWithType> nabył mutex musi zwolnić go wywołując metodę.

W <xref:System.Threading.Monitor>przeciwieństwie <xref:System.Threading.Mutex> do , klasa może służyć do synchronizacji między procesami. Aby to zrobić, należy użyć nazwanego obiektu mutex, który jest widoczny w całym systemie operacyjnym. Aby utworzyć wystąpienie o nazwie mutex, należy użyć [konstruktora Mutex,](<xref:System.Threading.Mutex.%23ctor%2A>) który określa nazwę. Można również wywołać <xref:System.Threading.Mutex.OpenExisting%2A?displayProperty=nameWithType> metodę, aby otworzyć istniejący nazwany mutex systemu.
  
Aby uzyskać więcej informacji, zobacz artykuł <xref:System.Threading.Mutex> [Mutexes](mutexes.md) i odwołanie do interfejsu API.

### <a name="spinlock-structure"></a>Struktura SpinLock

Struktura, <xref:System.Threading.SpinLock?displayProperty=nameWithType> na <xref:System.Threading.Monitor>przykład, zapewnia wyłączny dostęp do zasobu udostępnionego na podstawie dostępności blokady. Podczas <xref:System.Threading.SpinLock> próby uzyskania blokady, która jest niedostępna, czeka w pętli, wielokrotnie sprawdzając, aż blokada stanie się dostępna.

Aby uzyskać więcej informacji na temat korzyści i wad przy użyciu <xref:System.Threading.SpinLock> blokady spin, zobacz [SpinLock](spinlock.md) artykuł i odwołanie interfejsu API.

### <a name="readerwriterlockslim-class"></a>ReaderWriterLockSlim, klasa

Klasa <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> udziela wyłącznego dostępu do zasobu udostępnionego do pisania i umożliwia wiele wątków, aby uzyskać dostęp do zasobu jednocześnie do odczytu. Można użyć <xref:System.Threading.ReaderWriterLockSlim> do synchronizacji dostępu do struktury danych udostępnionych, który obsługuje operacje odczytu bezpieczne dla wątków, ale wymaga wyłącznego dostępu do wykonywania operacji zapisu. Gdy wątek żąda wyłącznego dostępu <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A?displayProperty=nameWithType> (na przykład przez wywołanie metody), kolejne żądania czytnika i modułu zapisującego blokują, dopóki wszystkie istniejące czytniki nie zakończą blokady, a moduł zapisujący wprowadził i zakończył blokadę.
  
Aby uzyskać więcej <xref:System.Threading.ReaderWriterLockSlim> informacji, zobacz odwołanie do interfejsu API.

### <a name="semaphore-and-semaphoreslim-classes"></a>Klasy Semafora i SemaphoreSlim

Klasy <xref:System.Threading.Semaphore?displayProperty=nameWithType> <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> i ograniczyć liczbę wątków, które mogą uzyskać dostęp do zasobu udostępnionego lub puli zasobów jednocześnie. Dodatkowe wątki, które żądają zasobu czekać, aż dowolny wątek zwalnia semafora. Ponieważ semafor nie ma koligacji wątku, wątek może uzyskać semafora i inny może go zwolnić.

<xref:System.Threading.SemaphoreSlim>jest lekką <xref:System.Threading.Semaphore> alternatywą dla i może być używana tylko do synchronizacji w ramach jednej granicy procesu.

W systemie Windows <xref:System.Threading.Semaphore> można używać do synchronizacji między procesami. Aby to zrobić, <xref:System.Threading.Semaphore> należy utworzyć wystąpienie, które reprezentuje semafora systemu nazwane przy użyciu jednego <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> z [konstruktorów Semaphore,](<xref:System.Threading.Semaphore.%23ctor%2A>) który określa nazwę lub metodę. <xref:System.Threading.SemaphoreSlim>nie obsługuje nazwanych semaforów systemowych.

Aby uzyskać więcej informacji, zobacz [artykuł Semaphore i SemaphoreSlim](semaphore-and-semaphoreslim.md) i odwołanie <xref:System.Threading.Semaphore> lub <xref:System.Threading.SemaphoreSlim> interfejsu API.

## <a name="thread-interaction-or-signaling"></a>Interakcja wątku lub sygnalizacja

Interakcja wątku (lub sygnalizacji wątku) oznacza, że wątek musi czekać na powiadomienie lub sygnał, z jednego lub więcej wątków, aby kontynuować. Na przykład jeśli wątek A wywołuje <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metodę wątku B, wątek A jest zablokowany do zakończenia wątku B. Ujeżdne synchronizacji opisane w poprzedniej sekcji zapewniają inny mechanizm sygnalizacji: zwalniając blokadę, wątek powiadamia inny wątek, że można kontynuować, uzyskując blokadę.

W tej sekcji opisano dodatkowe konstrukcje sygnalizacji dostarczone przez .NET.

### <a name="eventwaithandle-autoresetevent-manualresetevent-and-manualreseteventslim-classes"></a>EventWaitHandle, AutoResetEvent, ManualResetEvent i ManualResetEventSlim klasy

Klasa <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> reprezentuje zdarzenie synchronizacji wątku.

Zdarzenie synchronizacji może być w stanie niesygnalizowanym lub sygnalizowanym. Gdy stan zdarzenia jest niepodpisany, wątek, który <xref:System.Threading.WaitHandle.WaitOne%2A?> wywołuje przeciążenie zdarzenia jest zablokowany, dopóki zdarzenie nie zostanie zasygnalizowane. Metoda <xref:System.Threading.EventWaitHandle.Set%2A?displayProperty=nameWithType> ustawia stan zdarzenia do sygnalizowania.

<xref:System.Threading.EventWaitHandle> Zachowanie, które zostało sygnalizowane zależy od jego trybu resetowania:

- Utworzony <xref:System.Threading.EventWaitHandle> z <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> flagą resetuje się automatycznie po zwolnieniu pojedynczego wątku oczekiwania. To jak kołowrót, który pozwala tylko jeden wątek za każdym razem, gdy jest sygnalizowany. Klasa, <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> która pochodzi <xref:System.Threading.EventWaitHandle>od , reprezentuje to zachowanie.
- Utworzony <xref:System.Threading.EventWaitHandle> z <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> flagą pozostaje sygnalizowane, dopóki jego <xref:System.Threading.EventWaitHandle.Reset%2A> metoda jest wywoływana. To jak brama, która jest zamknięta, dopóki nie zostanie zasygnalizowana, a następnie pozostaje otwarta, dopóki ktoś jej nie zamknie. Klasa, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> która pochodzi <xref:System.Threading.EventWaitHandle>od , reprezentuje to zachowanie. Klasa <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> jest lekką <xref:System.Threading.ManualResetEvent>alternatywą dla .

W systemie Windows <xref:System.Threading.EventWaitHandle> można używać do synchronizacji między procesami. Aby to zrobić, <xref:System.Threading.EventWaitHandle> należy utworzyć wystąpienie, które reprezentuje zdarzenie synchronizacji systemu o nazwie przy użyciu <xref:System.Threading.EventWaitHandle.OpenExisting%2A?displayProperty=nameWithType> jednego z [EventWaitHandle konstruktorów,](<xref:System.Threading.EventWaitHandle.%23ctor%2A>) który określa nazwę lub metodę.

Aby uzyskać więcej informacji, zobacz [EventWaitHandle](eventwaithandle.md) artykułu. Aby uzyskać informacje <xref:System.Threading.EventWaitHandle>o <xref:System.Threading.AutoResetEvent> <xref:System.Threading.ManualResetEvent>interfejsie <xref:System.Threading.ManualResetEventSlim>API, zobacz , , i .

### <a name="countdownevent-class"></a>Klasa CountdownEvent

Klasa <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> reprezentuje zdarzenie, które staje się ustawione, gdy jego liczba wynosi zero. Gdy <xref:System.Threading.CountdownEvent.CurrentCount?displayProperty=nameWithType> jest większa niż zero, <xref:System.Threading.CountdownEvent.Wait%2A?displayProperty=nameWithType> wątek, który wywołuje jest zablokowany. Wywołanie, <xref:System.Threading.CountdownEvent.Signal%2A?displayProperty=nameWithType> aby zdeklignować liczbę zdarzeń.

W przeciwieństwie <xref:System.Threading.ManualResetEvent> <xref:System.Threading.ManualResetEventSlim>do lub , które można użyć do odblokowania wielu wątków <xref:System.Threading.CountdownEvent> z sygnałem z jednego wątku, można użyć do odblokowania jednego lub więcej wątków z sygnałami z wielu wątków.

Aby uzyskać więcej informacji, zobacz [CountdownEvent](countdownevent.md) artykuł i odwołanie interfejsu <xref:System.Threading.CountdownEvent> API.

### <a name="barrier-class"></a>Klasa bariery

Klasa <xref:System.Threading.Barrier?displayProperty=nameWithType> reprezentuje barierę wykonywania wątku. Wątek, <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> który wywołuje metodę sygnalizuje, że osiągnął barierę i czeka, aż inne wątki uczestnika dotrzeć do bariery. Gdy wszystkie wątki uczestnika dotrą do bariery, postępują, a bariera jest resetowana i może być ponownie użyta.

Można użyć, <xref:System.Threading.Barrier> gdy jeden lub więcej wątków wymaga wyników innych wątków przed przejściem do następnej fazy obliczeń.

Aby uzyskać więcej [Barrier](barrier.md) informacji, zobacz <xref:System.Threading.Barrier> Barrier artykułu i odwołania interfejsu API.

## <a name="interlocked-class"></a>Interlocked — Klasa

Klasa <xref:System.Threading.Interlocked?displayProperty=nameWithType> zawiera metody statyczne, które wykonują proste operacje niepodzielne na zmiennej. Te operacje niepodzielne obejmują dodawanie, zwiększanie i zmniejszanie, wymianę i wymianę warunkową, która zależy od porównania, oraz operację odczytu 64-bitowej wartości całkowitej.

Aby uzyskać więcej <xref:System.Threading.Interlocked> informacji, zobacz odwołanie do interfejsu API.

## <a name="spinwait-structure"></a>Struktura SpinWait

Struktura <xref:System.Threading.SpinWait?displayProperty=nameWithType> zapewnia obsługę oczekiwania opartego na spinie. Można go używać, gdy wątek musi czekać na zdarzenie, które mają być sygnalizowane lub warunek, który ma być spełniony, ale gdy rzeczywisty czas oczekiwania ma być mniejsza niż czas oczekiwania wymagany przy użyciu dojścia oczekiwania lub w inny sposób blokowania wątku. Za <xref:System.Threading.SpinWait>pomocą programu można określić krótki okres czasu do obracania podczas oczekiwania, a następnie wydajność (na przykład przez oczekiwanie lub uśpienie) tylko wtedy, gdy warunek nie został spełniony w określonym czasie.

Aby uzyskać więcej informacji, zobacz [SpinWait](spinwait.md) artykuł i odwołanie interfejsu <xref:System.Threading.SpinWait> API.

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekcje bezpieczne wątkowo](../collections/thread-safe/index.md)
- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
