---
title: Przegląd elementów podstawowych synchronizacji
description: Dowiedz się więcej o prymitywach synchronizacji wątków .NET używanych do synchronizowania dostępu do interakcji zasobów udostępnionych lub wątku sterowania
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
ms.openlocfilehash: 43f78c914b7cb01f9b0de4c258d5882548e52790
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106591"
---
# <a name="overview-of-synchronization-primitives"></a>Przegląd elementów podstawowych synchronizacji

Platforma .NET udostępnia szereg typów, których można użyć do synchronizacji dostępu do udostępnionego zasobu lub współrzędnych interakcji wątku.

> [!IMPORTANT]
> Użyj tego samego wystąpienia pierwotnego synchronizacji, aby chronić dostęp do zasobu udostępnionego. Jeśli używasz różnych wystąpień pierwotnych synchronizacji do ochrony tego samego zasobu, należy obejść ochronę zapewnianą przez prymityw synchronizacji.

## <a name="waithandle-class-and-lightweight-synchronization-types"></a>WaitHandle klasy i lekkich typów synchronizacji

Wiele elementów pierwotnych synchronizacji .NET <xref:System.Threading.WaitHandle?displayProperty=nameWithType> pochodzi z klasy, która hermetyzuje natywny uchwyt synchronizacji systemu operacyjnego i używa mechanizmu sygnalizacji dla interakcji z wątkami. Zajęcia te obejmują:

- <xref:System.Threading.Mutex?displayProperty=nameWithType>, który zapewnia wyłączny dostęp do zasobu udostępnionego. Stan obiektu mutex jest sygnalizowany, jeśli żaden wątek nie jest jego właścicielem.
- <xref:System.Threading.Semaphore?displayProperty=nameWithType>, co ogranicza liczbę wątków, które mogą uzyskiwać dostęp do zasobu udostępnionego lub puli zasobów jednocześnie. Stan semafora jest ustawiony na sygnalizowane, gdy jego liczba jest większa niż zero, a niesygnalizowane, gdy jego liczba wynosi zero.
- <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, który reprezentuje zdarzenie synchronizacji wątku i może być w stanie sygnalizowanym lub niesygnalizowanym.
- <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>, który wywodzi się z <xref:System.Threading.EventWaitHandle> i, gdy jest sygnalizowany, resetuje się automatycznie do stanu niesygnalizowanego po zwolnieniu pojedynczego wątku oczekiwania.
- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>, który wywodzi się z <xref:System.Threading.EventWaitHandle> i, gdy <xref:System.Threading.EventWaitHandle.Reset%2A> jest sygnalizowany, pozostaje w stanie sygnalizowanym, dopóki metoda nie zostanie wywołana.

W .NET Framework, <xref:System.Threading.WaitHandle> ponieważ <xref:System.MarshalByRefObject?displayProperty=nameWithType>pochodzi z , te typy mogą służyć do synchronizowania działań wątków między granicami domeny aplikacji.

W .NET Framework i .NET Core niektóre z tych typów mogą reprezentować nazwane uchwyty synchronizacji systemu, które są widoczne w całym systemie operacyjnym i mogą być używane do synchronizacji między procesami:

- <xref:System.Threading.Mutex>(.NET Framework i .NET Core),
- <xref:System.Threading.Semaphore>(.NET Framework i .NET Core w systemie Windows),
- <xref:System.Threading.EventWaitHandle>(.NET Framework i .NET Core w systemie Windows).

Aby uzyskać więcej <xref:System.Threading.WaitHandle> informacji, zobacz odwołanie do interfejsu API.

Lekkie typy synchronizacji nie zależą od podstawowych uchwytów systemu operacyjnego i zazwyczaj zapewniają lepszą wydajność. Jednak nie można ich używać do synchronizacji między procesami. Użyj tych typów do synchronizacji wątków w ramach jednej aplikacji.

Niektóre z tych typów są alternatywami <xref:System.Threading.WaitHandle>dla typów pochodzących z . Na przykład, <xref:System.Threading.SemaphoreSlim> jest lekką alternatywą dla <xref:System.Threading.Semaphore>.

## <a name="synchronization-of-access-to-a-shared-resource"></a>Synchronizacja dostępu do zasobu udostępnionego

.NET udostępnia szereg elementów pierwotnych synchronizacji do kontrolowania dostępu do zasobu udostępnionego przez wiele wątków.

### <a name="monitor-class"></a>klasa monitora

Klasa <xref:System.Threading.Monitor?displayProperty=nameWithType> udziela wzajemnie wyłącznego dostępu do zasobu udostępnionego przez nabycie lub zwolnienie blokady na obiekcie, który identyfikuje zasób. Podczas blokady jest wstrzymany, wątek, który posiada blokadę można ponownie nabyć i zwolnić blokady. Każdy inny wątek jest zablokowany przed <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> uzyskaniem blokady i metoda czeka, aż blokada zostanie zwolniona. Metoda <xref:System.Threading.Monitor.Enter%2A> uzyskuje zwolnioną blokadę. Można również użyć <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> metody, aby określić ilość czasu, w którym wątek próbuje uzyskać blokadę. Ponieważ <xref:System.Threading.Monitor> klasa ma koligacji wątku, wątek, który uzyskał blokadę <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> musi zwolnić blokady, wywołując metodę.

Można koordynować interakcję wątków, które uzyskują <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>blokadę na tym samym obiekcie za pomocą , <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>i <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> metody.

Aby uzyskać więcej <xref:System.Threading.Monitor> informacji, zobacz odwołanie do interfejsu API.

> [!NOTE]
> Użyj [instrukcji lock](../../csharp/language-reference/keywords/lock-statement.md) w języku C# i [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) instrukcji w języku Visual <xref:System.Threading.Monitor> Basic, aby zsynchronizować dostęp do zasobu udostępnionego zamiast używać klasy bezpośrednio. Te instrukcje są implementowane <xref:System.Threading.Monitor.Enter%2A> <xref:System.Threading.Monitor.Exit%2A> przy użyciu `try…finally` metod i bloku, aby upewnić się, że przejęta blokada jest zawsze zwalniana.

### <a name="mutex-class"></a>Mutex — Klasa

Klasa, <xref:System.Threading.Mutex?displayProperty=nameWithType> podobnie <xref:System.Threading.Monitor>jak, zapewnia wyłączny dostęp do zasobu udostępnionego. Użyj jednego z [Mutex.WaitOne](<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>) przeciążenia metody do żądania własności obiektu mutex. Podobnie <xref:System.Threading.Monitor> <xref:System.Threading.Mutex> jak , ma koligacji wątku i wątku, który <xref:System.Threading.Mutex.ReleaseMutex%2A?displayProperty=nameWithType> uzyskał mutex musi zwolnić go, wywołując metodę.

W <xref:System.Threading.Monitor>przeciwieństwie <xref:System.Threading.Mutex> do tego, klasa może służyć do synchronizacji między procesami. Aby to zrobić, należy użyć nazwanego obiektu mutex, który jest widoczny w całym systemie operacyjnym. Aby utworzyć nazwane wystąpienie obiektu mutex, należy użyć [konstruktora Mutex,](<xref:System.Threading.Mutex.%23ctor%2A>) który określa nazwę. Można również wywołać metodę, <xref:System.Threading.Mutex.OpenExisting%2A?displayProperty=nameWithType> aby otworzyć istniejące nazwane mutex systemu.
  
Aby uzyskać więcej informacji, zobacz [Muteksy](mutexes.md) artykuł i odwołanie <xref:System.Threading.Mutex> interfejsu API.

### <a name="spinlock-structure"></a>Struktura SpinLock

Struktura, <xref:System.Threading.SpinLock?displayProperty=nameWithType> podobnie <xref:System.Threading.Monitor>jak, zapewnia wyłączny dostęp do zasobu udostępnionego w oparciu o dostępność blokady. Podczas <xref:System.Threading.SpinLock> próby uzyskania blokady, która jest niedostępna, czeka w pętli, wielokrotnie sprawdzając, aż blokada stanie się dostępna.

Aby uzyskać więcej informacji na temat korzyści i wad za pomocą <xref:System.Threading.SpinLock> blokady spin, zobacz [SpinLock](spinlock.md) artykułu i odwołania interfejsu API.

### <a name="readerwriterlockslim-class"></a>ReaderWriterLockSlim, klasa

Klasa <xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> udziela wyłącznego dostępu do zasobu udostępnionego do pisania i umożliwia wielu wątków, aby uzyskać dostęp do zasobu jednocześnie do odczytu. Można użyć <xref:System.Threading.ReaderWriterLockSlim> do synchronizacji dostępu do struktury danych udostępnionych, która obsługuje operacje odczytu bezpieczne dla wątków, ale wymaga wyłącznego dostępu do wykonywania operacji zapisu. Gdy wątek żąda wyłącznego dostępu (na <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A?displayProperty=nameWithType> przykład przez wywołanie metody), kolejne żądania czytnika i modułu zapisującego blokują, dopóki wszyscy istniejący czytelnicy nie opuścili blokady, a moduł zapisujący wprowadził i opuścił blokadę.
  
Aby uzyskać więcej <xref:System.Threading.ReaderWriterLockSlim> informacji, zobacz odwołanie do interfejsu API.

### <a name="semaphore-and-semaphoreslim-classes"></a>Klasy Semafora i SemaphoreSlim

I <xref:System.Threading.Semaphore?displayProperty=nameWithType> <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> klasy ograniczyć liczbę wątków, które mogą uzyskać dostęp do zasobu udostępnionego lub puli zasobów jednocześnie. Dodatkowe wątki, które żądają zasób czekać, aż dowolny wątek zwalnia semafora. Ponieważ semafor nie ma koligacji wątku, wątek może nabyć semafor, a inny może go zwolnić.

<xref:System.Threading.SemaphoreSlim>jest lekką <xref:System.Threading.Semaphore> alternatywą i może być używany tylko do synchronizacji w ramach granicy jednego procesu.

W systemie Windows <xref:System.Threading.Semaphore> można użyć do synchronizacji między procesami. Aby to zrobić, <xref:System.Threading.Semaphore> należy utworzyć wystąpienie, które reprezentuje nazwany semafor systemu przy użyciu jednego z [konstruktorów Semafora,](<xref:System.Threading.Semaphore.%23ctor%2A>) który określa nazwę lub <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> metodę. <xref:System.Threading.SemaphoreSlim>nie obsługuje nazwanych semaforów systemowych.

Aby uzyskać więcej informacji, zobacz [Semaphore i SemaphoreSlim](semaphore-and-semaphoreslim.md) artykułu i <xref:System.Threading.Semaphore> odwołania lub <xref:System.Threading.SemaphoreSlim> interfejsu API.

## <a name="thread-interaction-or-signaling"></a>Interakcja wątku lub sygnalizacja

Interakcji wątku (lub sygnalizacji wątku) oznacza, że wątek musi czekać na powiadomienie lub sygnał, z jednego lub więcej wątków, aby kontynuować. Na przykład jeśli wątek <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> A wywołuje metodę wątku B, wątek A jest blokowany do momentu zakończenia wątku B. Prymitywy synchronizacji opisane w poprzedniej sekcji zapewniają inny mechanizm sygnalizacji: zwalniając blokadę, wątek powiadamia inny wątek, że można kontynuować, uzyskując blokadę.

W tej sekcji opisano dodatkowe konstrukcje sygnalizacji dostarczane przez .NET.

### <a name="eventwaithandle-autoresetevent-manualresetevent-and-manualreseteventslim-classes"></a>EventWaitHandle, AutoResetEvent, ManualResetEvent i ManualResetEventSlim klasy

Klasa <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> reprezentuje zdarzenie synchronizacji wątku.

Zdarzenie synchronizacji może być w stanie niesygnalizowanym lub sygnalizowanym. Gdy stan zdarzenia jest niesygnalizowany, wątek, który wywołuje <xref:System.Threading.WaitHandle.WaitOne%2A?> przeciążenie zdarzenia jest zablokowany, dopóki zdarzenie nie zostanie zasygnalizowane. Metoda <xref:System.Threading.EventWaitHandle.Set%2A?displayProperty=nameWithType> ustawia stan zdarzenia na sygnalizowane.

Zachowanie zasygnalizowanego, <xref:System.Threading.EventWaitHandle> zależy od jego trybu resetowania:

- Utworzony <xref:System.Threading.EventWaitHandle> z flagą <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> resetuje się automatycznie po zwolnieniu jednego wątku oczekiwania. To jak kołowrót, który pozwala tylko jeden wątek przez każdym razem jest sygnalizowany. Klasa, <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> która pochodzi <xref:System.Threading.EventWaitHandle>od , reprezentuje to zachowanie.
- Utworzony <xref:System.Threading.EventWaitHandle> z flagą <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> pozostaje sygnalizowany, dopóki jej <xref:System.Threading.EventWaitHandle.Reset%2A> metoda nie zostanie wywołana. To jak brama, która jest zamknięta, dopóki nie zostanie zasygnalizowana, a następnie pozostanie otwarta, dopóki ktoś jej nie zamknie. Klasa, <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> która pochodzi <xref:System.Threading.EventWaitHandle>od , reprezentuje to zachowanie. Klasa <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> jest lekką <xref:System.Threading.ManualResetEvent>alternatywą dla .

W systemie Windows <xref:System.Threading.EventWaitHandle> można użyć do synchronizacji między procesami. Aby to zrobić, <xref:System.Threading.EventWaitHandle> należy utworzyć wystąpienie, które reprezentuje zdarzenie synchronizacji systemu o nazwie przy użyciu jednego <xref:System.Threading.EventWaitHandle.OpenExisting%2A?displayProperty=nameWithType> z [EventWaitHandle konstruktorów,](<xref:System.Threading.EventWaitHandle.%23ctor%2A>) który określa nazwę lub metodę.

Aby uzyskać więcej informacji, zobacz [EventWaitHandle](eventwaithandle.md) artykułu. Aby zapoznać się z <xref:System.Threading.EventWaitHandle> <xref:System.Threading.AutoResetEvent>odniesieniem do interfejsu API, zobacz , , <xref:System.Threading.ManualResetEvent>, i <xref:System.Threading.ManualResetEventSlim>.

### <a name="countdownevent-class"></a>CountdownEvent, klasa

Klasa <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> reprezentuje zdarzenie, które staje się ustawione, gdy jego liczba wynosi zero. Gdy <xref:System.Threading.CountdownEvent.CurrentCount?displayProperty=nameWithType> jest większa niż zero, <xref:System.Threading.CountdownEvent.Wait%2A?displayProperty=nameWithType> wątek, który wywołuje jest zablokowany. Wywołanie, <xref:System.Threading.CountdownEvent.Signal%2A?displayProperty=nameWithType> aby zniweczyć liczbę zdarzeń.

W przeciwieństwie <xref:System.Threading.ManualResetEvent> <xref:System.Threading.ManualResetEventSlim>do lub , które można użyć do odblokowania wielu wątków <xref:System.Threading.CountdownEvent> za pomocą sygnału z jednego wątku, można użyć do odblokowania jednego lub więcej wątków z sygnałami z wielu wątków.

Aby uzyskać więcej informacji, zobacz [CountdownEvent](countdownevent.md) artykułu i odwołania <xref:System.Threading.CountdownEvent> interfejsu API.

### <a name="barrier-class"></a>Klasa bariery

Klasa <xref:System.Threading.Barrier?displayProperty=nameWithType> reprezentuje barierę wykonywania wątku. Wątek, który <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> wywołuje metodę sygnalizuje, że osiągnął barierę i czeka, aż inne wątki uczestnika dotrą do bariery. Gdy wszystkie wątki uczestnika dotrą do bariery, postępują, a bariera zostanie zresetowana i może być ponownie użyta.

Można użyć, <xref:System.Threading.Barrier> gdy jeden lub więcej wątków wymagają wyników innych wątków przed przejściem do następnej fazy obliczeń.

Aby uzyskać więcej [Barrier](barrier.md) informacji, zobacz <xref:System.Threading.Barrier> Barrier artykułu i odwołania interfejsu API.

## <a name="interlocked-class"></a>Interlocked — Klasa

Klasa <xref:System.Threading.Interlocked?displayProperty=nameWithType> udostępnia metody statyczne, które wykonują proste operacje atomowe na zmiennej. Te operacje atomowe obejmują dodawanie, przyrost i zmniejszanie, wymianę i wymianę warunkową, która zależy od porównania, oraz operację odczytu 64-bitowej wartości całkowitej.

Aby uzyskać więcej <xref:System.Threading.Interlocked> informacji, zobacz odwołanie do interfejsu API.

## <a name="spinwait-structure"></a>Struktura SpinWait

Struktura <xref:System.Threading.SpinWait?displayProperty=nameWithType> zapewnia obsługę oczekiwania opartego na spinach. Można go użyć, gdy wątek musi czekać na zdarzenie, które mają być sygnalizowane lub warunek, który ma być spełniony, ale gdy rzeczywisty czas oczekiwania ma być krótszy niż czas oczekiwania wymagany przy użyciu uchwytu oczekiwania lub w inny sposób blokując wątek. Za <xref:System.Threading.SpinWait>pomocą , można określić krótki okres czasu, aby obracać się podczas oczekiwania, a następnie plon (na przykład przez oczekiwanie lub spanie) tylko wtedy, gdy warunek nie został spełniony w określonym czasie.

Aby uzyskać więcej informacji, zobacz <xref:System.Threading.SpinWait> [SpinWait](spinwait.md) artykuł i odwołanie interfejsu API.

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekcje bezpieczne dla wątków](../collections/thread-safe/index.md)
- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
