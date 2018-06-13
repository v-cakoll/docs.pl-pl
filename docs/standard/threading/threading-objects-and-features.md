---
title: Wątkowość obiektów i funkcji
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02f88faab6ddbaa026e73ad61bc63fbe8e5e00ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591330"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="a7ed4-102">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="a7ed4-102">Threading Objects and Features</span></span>
<span data-ttu-id="a7ed4-103">.NET Framework udostępnia wiele obiektów, które ułatwiają tworzenie i zarządzanie nimi w aplikacjach wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-103">The .NET Framework provides a number of objects that help you create and manage multithreaded applications.</span></span> <span data-ttu-id="a7ed4-104">Zarządzane wątki są reprezentowane przez <xref:System.Threading.Thread> klasy.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-104">Managed threads are represented by the <xref:System.Threading.Thread> class.</span></span> <span data-ttu-id="a7ed4-105"><xref:System.Threading.ThreadPool> Klasa umożliwia łatwe tworzenie i zarządzanie zadaniami w tle wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-105">The <xref:System.Threading.ThreadPool> class provides easy creation and management of multithreaded background tasks.</span></span> <span data-ttu-id="a7ed4-106"><xref:System.ComponentModel.BackgroundWorker> Klasy jest taka sama dla zadania, które współdziałają z interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-106">The <xref:System.ComponentModel.BackgroundWorker> class does the same for tasks that interact with the user interface.</span></span> <span data-ttu-id="a7ed4-107"><xref:System.Threading.Timer> Klasa wykonuje zadania w tle w określonych interwałach.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-107">The <xref:System.Threading.Timer> class executes background tasks at timed intervals.</span></span>  
  
 <span data-ttu-id="a7ed4-108">Ponadto istnieje wiele klas, które synchronizują działania wątków, w tym <xref:System.Threading.Semaphore> i <xref:System.Threading.EventWaitHandle> klas wprowadzonych w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-108">In addition, there are a number of classes that synchronize activities of threads, including the <xref:System.Threading.Semaphore> and <xref:System.Threading.EventWaitHandle> classes introduced in the .NET Framework version 2.0.</span></span> <span data-ttu-id="a7ed4-109">Funkcje te klasy są porównywane w [podstawowych Omówienie synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="a7ed4-109">The features of these classes are compared in [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a7ed4-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a7ed4-110">In This Section</span></span>  
 [<span data-ttu-id="a7ed4-111">Zarządzana pula wątków</span><span class="sxs-lookup"><span data-stu-id="a7ed4-111">The Managed Thread Pool</span></span>](../../../docs/standard/threading/the-managed-thread-pool.md)  
 <span data-ttu-id="a7ed4-112">Wyjaśniono **puli wątków** klasy, która pozwala na żądanie wątku do wykonania zadania bez konieczności zarządzania dowolnego wątku samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-112">Explains the **ThreadPool** class, which enables you to request a thread to execute a task without having to do any thread management yourself.</span></span>  
  
 [<span data-ttu-id="a7ed4-113">Czasomierze</span><span class="sxs-lookup"><span data-stu-id="a7ed4-113">Timers</span></span>](../../../docs/standard/threading/timers.md)  
 <span data-ttu-id="a7ed4-114">Wyjaśniono, jak używać **czasomierza** do określenia delegata do wywołania w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-114">Explains how to use a **Timer** to specify a delegate to be called at a specified time.</span></span>  
  
 [<span data-ttu-id="a7ed4-115">Monitory</span><span class="sxs-lookup"><span data-stu-id="a7ed4-115">Monitors</span></span>](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
 <span data-ttu-id="a7ed4-116">Wyjaśniono, jak używać **Monitor** klasy synchronizujący dostęp do elementu członkowskiego lub do tworzenia własnych wątku typu zarządzania.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-116">Explains how to use the **Monitor** class to synchronize access to a member or to build your own thread management types.</span></span>  
  
 [<span data-ttu-id="a7ed4-117">Uchwyty oczekiwania</span><span class="sxs-lookup"><span data-stu-id="a7ed4-117">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="a7ed4-118">W tym artykule opisano <xref:System.Threading.WaitHandle> klasy, abstrakcyjna klasa podstawowa dla zdarzenia oczekiwania dojść, muteksy i semaforów, dzięki czemu oczekiwanie na wiele zdarzeń synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-118">Describes the <xref:System.Threading.WaitHandle> class, the abstract base class for event wait handles, mutexes, and semaphores, which enables waiting for multiple synchronization events.</span></span>  
  
 [<span data-ttu-id="a7ed4-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="a7ed4-119">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 <span data-ttu-id="a7ed4-120">W tym artykule opisano zarządzanych uchwyty oczekiwania na zdarzenie, które są używane do synchronizowania działania wątku sygnalizacji i Oczekiwanie na sygnały.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-120">Describes managed event wait handles, which are used to synchronize thread activities by signaling and waiting for signals.</span></span>  
  
 [<span data-ttu-id="a7ed4-121">Muteksy</span><span class="sxs-lookup"><span data-stu-id="a7ed4-121">Mutexes</span></span>](../../../docs/standard/threading/mutexes.md)  
 <span data-ttu-id="a7ed4-122">Wyjaśniono, jak używać <xref:System.Threading.Mutex> synchronizujący dostęp do obiektu lub utworzyć własne mechanizmy synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-122">Explains how to use a <xref:System.Threading.Mutex> to synchronize access to an object or to build your own synchronization mechanisms.</span></span>  
  
 [<span data-ttu-id="a7ed4-123">Operacje blokowane</span><span class="sxs-lookup"><span data-stu-id="a7ed4-123">Interlocked Operations</span></span>](../../../docs/standard/threading/interlocked-operations.md)  
 <span data-ttu-id="a7ed4-124">Wyjaśniono, jak używać <xref:System.Threading.Interlocked> klasę, aby zwiększyć lub zmniejszyć wartość i przechowywania wartości w jednej operacji atomic.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-124">Explains how to use the <xref:System.Threading.Interlocked> class to increment or decrement a value and store the value in a single atomic operation.</span></span>  
  
 [<span data-ttu-id="a7ed4-125">reader_writer_lock, klasa</span><span class="sxs-lookup"><span data-stu-id="a7ed4-125">Reader-Writer Locks</span></span>](../../../docs/standard/threading/reader-writer-locks.md)  
 <span data-ttu-id="a7ed4-126">Definiuje blokady, która implementuje semantykę pojedynczego — moduł zapisujący/wielu czytników.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-126">Defines a lock that implements single-writer/multiple-reader semantics.</span></span>  
  
 [<span data-ttu-id="a7ed4-127">Semaphore i SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="a7ed4-127">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
 <span data-ttu-id="a7ed4-128">W tym artykule opisano <xref:System.Threading.Semaphore> obiekty i objaśnienie sposobu ich użyć do kontroli dostępu do zasobów ograniczone.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-128">Describes <xref:System.Threading.Semaphore> objects and explains how to use them to control access to limited resources.</span></span>  
  
 [<span data-ttu-id="a7ed4-129">Przegląd elementów podstawowych synchronizacji</span><span class="sxs-lookup"><span data-stu-id="a7ed4-129">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="a7ed4-130">Porównanie funkcji blokowania i synchronizacja wątków zarządzanych klas .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-130">Compares the features of the .NET Framework classes provided for locking and synchronizing managed threads.</span></span>  
  
 [<span data-ttu-id="a7ed4-131">Barrier</span><span class="sxs-lookup"><span data-stu-id="a7ed4-131">Barrier</span></span>](../../../docs/standard/threading/barrier.md)  
 <span data-ttu-id="a7ed4-132">W tym artykule opisano <xref:System.Threading.Barrier> obiekty, które implementują wzorzec bariery koordynacji wątków w operacjach etapowe.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-132">Describes <xref:System.Threading.Barrier> objects that implement the barrier pattern for coordination of threads in phased operations.</span></span>  
  
 [<span data-ttu-id="a7ed4-133">SpinLock</span><span class="sxs-lookup"><span data-stu-id="a7ed4-133">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)  
 <span data-ttu-id="a7ed4-134">W tym artykule opisano <xref:System.Threading.SpinLock>, lekkie sposobem klasa monitora w niektórych scenariuszach niskiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-134">Describes <xref:System.Threading.SpinLock>, a lightweight alternative to the Monitor class for certain low-level scenarios.</span></span>  
  
 [<span data-ttu-id="a7ed4-135">SpinWait</span><span class="sxs-lookup"><span data-stu-id="a7ed4-135">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 <span data-ttu-id="a7ed4-136">W tym artykule opisano <xref:System.Threading.SpinWait>, pierwotnych niskiego poziomu synchronizacji, który wykonuje zajęty Obracająca przed zainicjowaniem oczekiwania na podstawie jądra.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-136">Describes <xref:System.Threading.SpinWait>, a low level synchronization primitive that performs busy spinning prior to initiating a kernel-based wait.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a7ed4-137">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="a7ed4-137">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="a7ed4-138">Zawiera dokumentacja referencyjna dla **wątku** klasy, która reprezentuje zarządzanego wątku, czy pochodzi kodu niezarządzanego, lub został utworzony w zarządzanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-138">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="a7ed4-139">Umożliwia zadania w tle, które współdziałają z interfejsem użytkownika, komunikację za pomocą zdarzenia wywoływane w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-139">Enables background tasks that interact with the user interface, communicating via events raised on the user-interface thread.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a7ed4-140">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a7ed4-140">Related Sections</span></span>  
 [<span data-ttu-id="a7ed4-141">Asynchroniczne operacje We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="a7ed4-141">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="a7ed4-142">W tym artykule opisano, jak asynchroniczne We/Wy portów za pomocą puli wątków wymagają przetwarzania tylko po zakończeniu operacji wejścia/wyjścia.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-142">Describes how I/O asynchronous completion ports use the thread pool to require processing only when an input/output operation completes.</span></span>  
  
 [<span data-ttu-id="a7ed4-143">Biblioteka zadań równoległych (TPL)</span><span class="sxs-lookup"><span data-stu-id="a7ed4-143">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="a7ed4-144">W tym artykule opisano zalecane podejście do programowania wielowątkowe w [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] i nowszych.</span><span class="sxs-lookup"><span data-stu-id="a7ed4-144">Describes the recommended approach for multithreaded programming in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and later.</span></span>
