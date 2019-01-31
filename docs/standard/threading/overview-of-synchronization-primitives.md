---
title: Przegląd elementów podstawowych synchronizacji
description: Dowiedz się więcej o podstawowych synchronizacji wątków .NET używane do synchronizowania dostępu do zasobu udostępnionego lub kontroli wątku interakcji
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9faac620c98362c5f9f650121bb88b207ed4863b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270769"
---
# <a name="overview-of-synchronization-primitives"></a>Przegląd elementów podstawowych synchronizacji

.NET oferuje wiele różnych typów, które służy do synchronizowania dostępu do zasobu udostępnionego lub koordynowania interakcji wątku.

> [!IMPORTANT]
> Użyj tego samego wystąpienia pierwotnych synchronizacji, aby chronić każdy dostęp do zasobu udostępnionego. Wiele wątków może uzyskać dostęp do zasobu jednocześnie korzystać z wystąpień pierwotnych różnych synchronizacji w celu ochrony dostępu do zasobu lub niektóre części kodu bezpośrednio uzyskać dostęp do zasobu.

## <a name="waithandle-class-and-lightweight-synchronization-types"></a>WaitHandle — klasa i uproszczone typów synchronizacji

Wiele elementów podstawowych synchronizacji .NET pochodzić od <xref:System.Threading.WaitHandle?displayProperty=nameWithType> klasy, która hermetyzuje dojście synchronizacji macierzystego systemu operacyjnego i używa mechanizmu sygnalizowanie do interakcji z wątku. Tych klas obejmują:

- <xref:System.Threading.Mutex?displayProperty=nameWithType>, która przyznaje wyłącznego dostępu do zasobu udostępnionego. Stan obiektu mutex jest sygnalizowane, jeśli żaden wątek nie jest jego właścicielem.
- <xref:System.Threading.Semaphore?displayProperty=nameWithType>, co ogranicza liczbę wątków, które mogą uzyskać dostęp do udostępnionego zasobu lub pulę zasobów jednocześnie. Stan semafor ustawiono do sygnalizowanego podczas ich liczba jest większa od zera i nonsignaled podczas ich liczba jest równa zero.
- <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, który reprezentuje zdarzenia synchronizacji wątków i może być w stanie sygnałowego lub unsignaled.
- <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType>, która jest pochodną <xref:System.Threading.EventWaitHandle> i, gdy sygnalizowane, przywraca automatycznie unsignaled stanu po przy zwalnianiu pojedynczego wątku oczekiwania.
- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>, który pochodzi od klasy <xref:System.Threading.EventWaitHandle> i w przypadku sygnalizowane, pozostaje w zasygnalizowany stan do momentu <xref:System.Threading.EventWaitHandle.Reset%2A> metoda jest wywoływana.

W .NET Framework ponieważ <xref:System.Threading.WaitHandle> pochodzi od klasy <xref:System.MarshalByRefObject?displayProperty=nameWithType>, tych typów może służyć do synchronizowania działania wątków poza granice domeny aplikacji.

W programie .NET Framework i .NET Core niektóre z tych typów reprezentują nazwane systemu obsługuje synchronizacji, które są widoczne w całym systemie operacyjnym i mogą służyć do synchronizacji między procesami:

- <xref:System.Threading.Mutex> (.NET framework i .NET Core)
- <xref:System.Threading.Semaphore> (.NET framework i .NET Core w Windows)
- <xref:System.Threading.EventWaitHandle> (.NET framework i .NET Core w Windows).

Aby uzyskać więcej informacji, zobacz <xref:System.Threading.WaitHandle> dokumentacja interfejsu API.

Lekkich typów synchronizacji nie zależą od podstawowej obsługi systemu operacyjnego i zwykle zapewniają lepszą wydajność. Jednak nie można używać do synchronizacji między procesami. Te typy na użytek synchronizacji wątków w ramach jednej aplikacji.

Niektóre z tych typów są alternatywy dla typów pochodnych typu <xref:System.Threading.WaitHandle>. Na przykład <xref:System.Threading.SemaphoreSlim> jest uproszczone alternatywa dla <xref:System.Threading.Semaphore>.

## <a name="synchronization-of-access-to-a-shared-resource"></a>Synchronizacja dostęp do udostępnionego zasobu

.NET oferuje szeroką gamę podstawowych synchronizacji w celu kontrolowania dostępu do zasobu udostępnionego przez wiele wątków.

### <a name="monitor-class"></a>klasa monitora

<xref:System.Threading.Monitor?displayProperty=nameWithType> Klasy przyznaje wzajemnie wykluczających się dostęp do udostępnionego zasobu przez pobieranie lub zwalniając blokadę na obiekcie, który identyfikuje zasób. Dopóki blokada jest utrzymywana, wątek, który posiada blokadę można ponownie pobrać i zwalnia blokadę. Zablokowano pobieranie blokady innych wątków i <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> metoda czeka, dopóki blokada jest zwalniana. <xref:System.Threading.Monitor.Enter%2A> Metoda uzyskuje blokadę wydane. Można również użyć <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> metodę, aby określić ilość czasu, przez który wątek podejmie próbę uzyskania blokady. Ponieważ <xref:System.Threading.Monitor> klasa ma koligacji wątku, wątek, który blokadę uzyskaną musi zwolnić blokadę, wywołując <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> metody.

Możesz skoordynować interakcji z wątków, które Uzyskaj blokadę na ten sam obiekt przy użyciu <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType>, i <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> metody.

Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Monitor> dokumentacja interfejsu API.

> [!NOTE]
> Użyj [blokady](../../csharp/language-reference/keywords/lock-statement.md) instrukcji w języku C# i [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) instrukcji w języku Visual Basic do synchronizowania dostępu do udostępnionych zasobów zamiast <xref:System.Threading.Monitor> klasy bezpośrednio. Te instrukcje są implementowane przy użyciu <xref:System.Threading.Monitor.Enter%2A> i <xref:System.Threading.Monitor.Exit%2A> metod i `try…finally` bloku, aby upewnić się, zawsze zwolnieniu blokady uzyskano.

### <a name="mutex-class"></a>Mutex — Klasa

<xref:System.Threading.Mutex?displayProperty=nameWithType> Klasy, takie jak <xref:System.Threading.Monitor>, udziela wyłącznego dostępu do zasobu udostępnionego. Użyj jednej z [Mutex.WaitOne](<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType>) przeciążenia metody, aby zażądać własności obiektu mutex. Podobnie jak <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> ma koligacji wątku i wątku, który nabyte mutex musi zwolnić go przez wywołanie metody <xref:System.Threading.Mutex.ReleaseMutex%2A?displayProperty=nameWithType> metody.

W odróżnieniu od <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> klasy może służyć do synchronizacji między procesami. Aby to zrobić, należy użyć nazwanego obiektu mutex, która jest widoczna w całym systemie operacyjnym. Aby utworzyć wystąpienia nazwanego obiektu mutex, użyj [konstruktora obiektu Mutex](<xref:System.Threading.Mutex.%23ctor%2A>) określający nazwę. Można również wywołać <xref:System.Threading.Mutex.OpenExisting%2A?displayProperty=nameWithType> metodę, aby otworzyć istniejący o nazwie systemu element mutex.
  
Aby uzyskać więcej informacji, zobacz [muteksy](mutexes.md) artykułu i <xref:System.Threading.Mutex> dokumentacja interfejsu API.

### <a name="spinlock-structure"></a>Struktura strukturze SpinLock

<xref:System.Threading.SpinLock?displayProperty=nameWithType> Struktury, takie jak <xref:System.Threading.Monitor>, udziela wyłączny dostęp do udostępnionego zasobu, na podstawie dostępności blokadę. Gdy <xref:System.Threading.SpinLock> próbuje uzyskać blokadę, który jest niedostępny, czeka on w pętli, sprawdzanie wielokrotnie, dopóki blokada staje się dostępna.

Aby uzyskać więcej informacji na temat zalety i wady wynikające z użycia pokrętła blokady, zobacz [struktury SpinLock](spinlock.md) artykułu i <xref:System.Threading.SpinLock> dokumentacja interfejsu API.

### <a name="readerwriterlockslim-class"></a>Klasa ReaderWriterLockSlim

<xref:System.Threading.ReaderWriterLockSlim?displayProperty=nameWithType> Klasy udziela wyłączny dostęp do udostępnionego zasobu do zapisu i umożliwia wielu wątkach, aby uzyskać dostęp do zasobu, jednocześnie do odczytu. Możesz chcieć użyć <xref:System.Threading.ReaderWriterLockSlim> do synchronizowania dostępu do struktury danych udostępnionych, która obsługuje operacje odczytu metodą o bezpiecznych wątkach, ale wymaga wyłącznego dostępu do wykonywania operacji zapisu. Gdy wątek żąda wyłącznego dostępu (na przykład przez wywołanie metody <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A?displayProperty=nameWithType> metoda), kolejne bloku czytników i składników zapisywania żądań do wszystkich istniejących czytelnicy opuścili blokady i Edytor wprowadził i zakończony blokady.
  
Aby uzyskać więcej informacji, zobacz <xref:System.Threading.ReaderWriterLockSlim> dokumentacja interfejsu API.

### <a name="semaphore-and-semaphoreslim-classes"></a>Semaphore i SemaphoreSlim klasy

<xref:System.Threading.Semaphore?displayProperty=nameWithType> i <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> klasy ograniczyć liczbę wątków, które mogą uzyskać dostęp do udostępnionego zasobu lub pulę zasobów jednocześnie. Dodatkowe wątki, które żądają zasobu poczekaj, aż wątek zwalnia semafora. Ponieważ semafora nie mają koligacji wątku, wątek mogą nabyć semafora i inną można zwolnić go.

<xref:System.Threading.SemaphoreSlim> jest to uproszczone alternatywa dla <xref:System.Threading.Semaphore> i można używać tylko w przypadku synchronizacji w obrębie granicy pojedynczego procesu.

Windows, mogą używać <xref:System.Threading.Semaphore> synchronizacji między procesami. Aby to zrobić, należy utworzyć <xref:System.Threading.Semaphore> wystąpienie, które przedstawia semafor systemu o nazwie przy użyciu jednej z [semafora konstruktory](<xref:System.Threading.Semaphore.%23ctor%2A>) , który określa nazwę lub <xref:System.Threading.Semaphore.OpenExisting%2A?displayProperty=nameWithType> metody. <xref:System.Threading.SemaphoreSlim> nie obsługuje systemu o nazwie semaforów.

Aby uzyskać więcej informacji, zobacz [Semaphore i SemaphoreSlim](semaphore-and-semaphoreslim.md) artykułu i <xref:System.Threading.Semaphore> lub <xref:System.Threading.SemaphoreSlim> dokumentacja interfejsu API.

## <a name="thread-interaction-or-signaling"></a>Interakcja wątku lub Sygnalizowanie

Interakcji wątku (lub sygnalizowanie wątek) oznacza, że wątek musi czekać dla powiadomienia lub sygnał z jednego lub więcej wątków, aby kontynuować. Na przykład, jeśli wątek A wywołuje <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> metoda wątku B, A wątek jest zablokowany, zakończenie wątku B. Podstawowych synchronizacji opisanych w poprzedniej sekcji Podaj inny mechanizm Sygnalizowanie: zwalniając blokadę, wątek powiadamia inny wątek, który będzie możliwe przez uzyskanie blokady.

W tej sekcji opisano dodatkowe konstrukcje sygnalizowania, dostarczone przez .NET.

### <a name="eventwaithandle-autoresetevent-manualresetevent-and-manualreseteventslim-classes"></a>Klasy EventWaitHandle, autoresetevent —, ManualResetEvent i ManualResetEventSlim

<xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> Klasa reprezentuje zdarzenia synchronizacji wątków.

Zdarzenie synchronizacji może być w stanie unsignaled lub sygnałowego. Gdy stan zdarzenia to unsignaled, wątku wywołującym zdarzenia <xref:System.Threading.WaitHandle.WaitOne%2A?> przeciążenie jest zablokowany do momentu zasygnalizowania zdarzenia. <xref:System.Threading.EventWaitHandle.Set%2A?displayProperty=nameWithType> Metody ustawia stan zdarzenie do sygnalizowanego.

Zachowanie <xref:System.Threading.EventWaitHandle> , zostały zasygnalizują, zależy od jej tryb resetowania:

- <xref:System.Threading.EventWaitHandle> Utworzone za pomocą <xref:System.Threading.EventResetMode.AutoReset?displayProperty=nameWithType> Flaga Resetuje automatycznie po przy zwalnianiu pojedynczego wątku oczekiwania. Przypomina powierzchniowe (s), która zezwala na tylko jeden wątek za pośrednictwem każdorazowo, gdy zostanie zasygnalizowane. <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> Klasy, która jest pochodną <xref:System.Threading.EventWaitHandle>, przedstawia tego zachowania.
- <xref:System.Threading.EventWaitHandle> Utworzone za pomocą <xref:System.Threading.EventResetMode.ManualReset?displayProperty=nameWithType> flagi pozostaje sygnałowego aż do jego <xref:System.Threading.EventWaitHandle.Reset%2A> metoda jest wywoływana. Przypomina bramy, który jest zamknięty, aż sygnalizowane, a następnie pozostanie otwarty, dopóki ktoś zostanie zamknięty. <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Klasy, która jest pochodną <xref:System.Threading.EventWaitHandle>, przedstawia tego zachowania. <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> Klasy jest uproszczone alternatywą do <xref:System.Threading.ManualResetEvent>.

Windows, mogą używać <xref:System.Threading.EventWaitHandle> synchronizacji między procesami. Aby to zrobić, należy utworzyć <xref:System.Threading.EventWaitHandle> wystąpienia, która reprezentuje zdarzenia synchronizacji o nazwie system przy użyciu jednej z [konstruktory EventWaitHandle](<xref:System.Threading.EventWaitHandle.%23ctor%2A>) , który określa nazwę lub <xref:System.Threading.EventWaitHandle.OpenExisting%2A?displayProperty=nameWithType> metody.

Aby uzyskać więcej informacji, zobacz [EventWaitHandle](eventwaithandle.md) i [ManualResetEvent i ManualResetEventSlim](manualresetevent-and-manualreseteventslim.md) artykułów. Aby uzyskać dokumentację interfejsu API, zobacz <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.AutoResetEvent>, <xref:System.Threading.ManualResetEvent>, i <xref:System.Threading.ManualResetEventSlim>.

### <a name="countdownevent-class"></a>Klasa CountdownEvent

<xref:System.Threading.CountdownEvent?displayProperty=nameWithType> Klasa reprezentuje zdarzenie, które staje się ustawić, gdy ich liczba jest równa zero. Gdy <xref:System.Threading.CountdownEvent.CurrentCount?displayProperty=nameWithType> jest większa od zera, wątek, który wywołuje <xref:System.Threading.CountdownEvent.Wait%2A?displayProperty=nameWithType> jest zablokowany. Wywołaj <xref:System.Threading.CountdownEvent.Signal%2A?displayProperty=nameWithType> zmniejszyć liczbę zdarzeń.

W przeciwieństwie do <xref:System.Threading.ManualResetEvent> lub <xref:System.Threading.ManualResetEventSlim>, która umożliwia odblokowanie wiele wątków z sygnałów z jednego wątku, można użyć <xref:System.Threading.CountdownEvent> odblokowania jeden lub więcej wątków z sygnałów z wielu wątków.

Aby uzyskać więcej informacji, zobacz [CountdownEvent](countdownevent.md) artykułu i <xref:System.Threading.CountdownEvent> dokumentacja interfejsu API.

### <a name="barrier-class"></a>Klasa bariery

<xref:System.Threading.Barrier?displayProperty=nameWithType> Klasa reprezentuje barierę wykonanie wątku. Wątek, który wywołuje <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> metoda sygnalizuje, że osiągnęła barierę i czeka aż inne wątki uczestnika barierę. Gdy wszystkie wątki uczestnika osiągną barierę, mogą kontynuować i barierę jest resetowany i mogą być używane ponownie.

Można na przykład <xref:System.Threading.Barrier> Jeżeli jeden lub więcej wątków wymagane wyniki inne wątki przed przejściem do następnej fazy obliczeń.

Aby uzyskać więcej informacji, zobacz [barierę](barrier.md) artykułu i <xref:System.Threading.Barrier> dokumentacja interfejsu API.

## <a name="interlocked-class"></a>Interlocked — Klasa

<xref:System.Threading.Interlocked?displayProperty=nameWithType> Klasa zawiera metody statyczne, wykonujących proste niepodzielne operacje na zmiennej. Te niepodzielne operacje obejmują dodawanie, inkrementacji i dekrementacji, exchange i warunkowego programu exchange, który zależy od porównanie, a operacja wartość 64-bitową liczbę całkowitą odczytu.

Aby uzyskać więcej informacji, zobacz <xref:System.Threading.Interlocked> dokumentacja interfejsu API.

## <a name="spinwait-structure"></a>Struktura metody SpinWait

<xref:System.Threading.SpinWait?displayProperty=nameWithType> Struktura zapewnia obsługę oczekiwania na podstawie pokrętła. Można go używać, gdy wątek ma czekać na zdarzenie ma być zasygnalizowany lub warunek do spełnienia, ale gdy czas oczekiwania rzeczywiste powinien przypadać wcześniej niż czas oczekiwania, wymagane przez przy użyciu dojścia oczekiwania lub w przeciwnym razie blokowanie wątku. Za pomocą <xref:System.Threading.SpinWait>, można określić krótki okres pokrętła oczekiwania, a następnie uzyskanie (np. przez oczekiwania lub uśpiony) tylko wtedy, gdy w określonym czasie nie został spełniony warunek.

Aby uzyskać więcej informacji, zobacz [metody SpinWait](spinwait.md) artykułu i <xref:System.Threading.SpinWait> dokumentacja interfejsu API.

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Kolekcje obsługujące wielowątkowość](../collections/thread-safe/index.md)
- [Wątkowość obiektów i funkcji](threading-objects-and-features.md)
