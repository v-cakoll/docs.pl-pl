---
title: Wątkowość obiektów i funkcji
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a355c2e996ddb00dad804dfeb22987923d91aa6
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144523"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="e3ae9-102">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="e3ae9-102">Threading objects and features</span></span>

<span data-ttu-id="e3ae9-103">Wraz z <xref:System.Threading.Thread?displayProperty=nameWithType> klasy .NET zapewnia szereg klas, które ułatwiają tworzenie aplikacji wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="e3ae9-103">Along with the <xref:System.Threading.Thread?displayProperty=nameWithType> class, .NET provides a number of classes that help you develop multithreaded applications.</span></span> <span data-ttu-id="e3ae9-104">Poniższe artykuły zawierają omówienie tych klas:</span><span class="sxs-lookup"><span data-stu-id="e3ae9-104">The following articles provide overview of those classes:</span></span>

|<span data-ttu-id="e3ae9-105">Tytuł</span><span class="sxs-lookup"><span data-stu-id="e3ae9-105">Title</span></span>|<span data-ttu-id="e3ae9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e3ae9-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e3ae9-107">Zarządzana Pula wątków</span><span class="sxs-lookup"><span data-stu-id="e3ae9-107">The managed thread pool</span></span>](the-managed-thread-pool.md)|<span data-ttu-id="e3ae9-108">W tym artykule opisano <xref:System.Threading.ThreadPool?displayProperty=nameWithType> klasy, która dostarcza puli wątków roboczych, które są zarządzane przez platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="e3ae9-108">Describes the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> class, which provides a pool of worker threads that are managed by .NET.</span></span>|  
|[<span data-ttu-id="e3ae9-109">Czasomierze</span><span class="sxs-lookup"><span data-stu-id="e3ae9-109">Timers</span></span>](timers.md)|<span data-ttu-id="e3ae9-110">W tym artykule opisano czasomierzy .NET, które mogą być używane w środowisku wielowątkowym.</span><span class="sxs-lookup"><span data-stu-id="e3ae9-110">Describes .NET timers that can be used in a multithreaded environment.</span></span>|
|[<span data-ttu-id="e3ae9-111">Przegląd elementów podstawowych synchronizacji</span><span class="sxs-lookup"><span data-stu-id="e3ae9-111">Overview of synchronization primitives</span></span>](overview-of-synchronization-primitives.md)|<span data-ttu-id="e3ae9-112">Opisuje typy, które mogą służyć do synchronizowania dostępu do udostępnionego zasobu lub kontroli wątku interakcji.</span><span class="sxs-lookup"><span data-stu-id="e3ae9-112">Describes types that can be used to synchronize access to a shared resource or control thread interaction.</span></span>|
|[<span data-ttu-id="e3ae9-113">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="e3ae9-113">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)|<span data-ttu-id="e3ae9-114">W tym artykule opisano uchwyty oczekiwania na zdarzenie zarządzane, które są używane do synchronizowania działaniach Sygnalizowanie i Oczekiwanie na sygnałów.</span><span class="sxs-lookup"><span data-stu-id="e3ae9-114">Describes managed event wait handles, which are used to synchronize thread activities by signaling and waiting for signals.</span></span>|
|[<span data-ttu-id="e3ae9-115">Muteksy</span><span class="sxs-lookup"><span data-stu-id="e3ae9-115">Mutexes</span></span>](mutexes.md)|<span data-ttu-id="e3ae9-116">W tym artykule opisano <xref:System.Threading.Mutex?displayProperty=nameWithType>, która przyznaje wyłącznego dostępu do zasobu udostępnionego.</span><span class="sxs-lookup"><span data-stu-id="e3ae9-116">Describes <xref:System.Threading.Mutex?displayProperty=nameWithType>, which grants exclusive access to a shared resource.</span></span>|
|[<span data-ttu-id="e3ae9-117">Semaphore i SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="e3ae9-117">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)|<span data-ttu-id="e3ae9-118">W tym artykule opisano <xref:System.Threading.Semaphore?displayProperty=nameWithType> klasy, która ogranicza liczbę wątków, które mogą uzyskać dostęp do udostępnionego zasobu lub pulę zasobów jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="e3ae9-118">Describes the <xref:System.Threading.Semaphore?displayProperty=nameWithType> class, which limits number of threads that can access a shared resource or a pool of resources concurrently.</span></span>|
|[<span data-ttu-id="e3ae9-119">Barrier</span><span class="sxs-lookup"><span data-stu-id="e3ae9-119">Barrier</span></span>](barrier.md)|<span data-ttu-id="e3ae9-120">W tym artykule opisano <xref:System.Threading.Barrier?displayProperty=nameWithType> klasę, która implementuje wzorzec barierę koordynacji wątków w operacjach etapowe.</span><span class="sxs-lookup"><span data-stu-id="e3ae9-120">Describes the <xref:System.Threading.Barrier?displayProperty=nameWithType> class that implements the barrier pattern for coordination of threads in phased operations.</span></span>|
|[<span data-ttu-id="e3ae9-121">SpinLock</span><span class="sxs-lookup"><span data-stu-id="e3ae9-121">SpinLock</span></span>](spinlock.md)|<span data-ttu-id="e3ae9-122">W tym artykule opisano <xref:System.Threading.SpinLock?displayProperty=nameWithType> struktury, która jest lekkie alternatywą <xref:System.Threading.Monitor?displayProperty=nameWithType> klasy dla niektórych niskiego poziomu scenariuszy blokowania.</span><span class="sxs-lookup"><span data-stu-id="e3ae9-122">Describes the <xref:System.Threading.SpinLock?displayProperty=nameWithType> structure, which is a lightweight alternative to the <xref:System.Threading.Monitor?displayProperty=nameWithType> class for certain low-level locking scenarios.</span></span>|
|[<span data-ttu-id="e3ae9-123">SpinWait</span><span class="sxs-lookup"><span data-stu-id="e3ae9-123">SpinWait</span></span>](spinwait.md)|<span data-ttu-id="e3ae9-124">W tym artykule opisano <xref:System.Threading.SpinWait?displayProperty=nameWithType> struktury, która zapewnia obsługę oczekiwania na podstawie pokrętła.</span><span class="sxs-lookup"><span data-stu-id="e3ae9-124">Describes the <xref:System.Threading.SpinWait?displayProperty=nameWithType> structure, which provides support for spin-based waiting.</span></span>|

## <a name="see-also"></a><span data-ttu-id="e3ae9-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3ae9-125">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [<span data-ttu-id="e3ae9-126">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="e3ae9-126">Using threads and threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="e3ae9-127">Asynchroniczne operacje We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="e3ae9-127">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)
- [<span data-ttu-id="e3ae9-128">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="e3ae9-128">Parallel Programming</span></span>](../parallel-programming/index.md)
- [<span data-ttu-id="e3ae9-129">Biblioteka zadań równoległych (TPL)</span><span class="sxs-lookup"><span data-stu-id="e3ae9-129">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)
