---
title: Zarządzana wątkowość — podstawy
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5fa91bb22de6492815f79bfd50e1fefc800c6047
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="managed-threading-basics"></a><span data-ttu-id="60935-102">Zarządzana wątkowość — podstawy</span><span class="sxs-lookup"><span data-stu-id="60935-102">Managed Threading Basics</span></span>
<span data-ttu-id="60935-103">Pierwsze pięć tematy w tej sekcji mają ułatwić określenie, kiedy używać zarządzanych wątków i opisano niektóre podstawowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="60935-103">The first five topics of this section are designed to help you determine when to use managed threading, and to explain some basic features.</span></span> <span data-ttu-id="60935-104">Aby informacji na temat klas, które zapewniają dodatkowe funkcje, zobacz [wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md) i [podstawowych Omówienie synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="60935-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="60935-105">Pozostałe tematy w tej sekcji obejmują zaawansowane tematy, w tym interakcji z zarządzanych wątków w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="60935-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="60935-106">W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], bibliotece równoległych zadań i PLINQ podanie interfejsów API równoległość zadań i danych w programów wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="60935-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="60935-107">Aby uzyskać więcej informacji, zobacz [programowania równoległego](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="60935-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="60935-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="60935-108">In This Section</span></span>  
 [<span data-ttu-id="60935-109">Wątki i wątkowość</span><span class="sxs-lookup"><span data-stu-id="60935-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="60935-110">W tym artykule omówiono zalety i wady wiele wątków i opisano scenariusze, w których można utworzyć wątków lub użyj wątków z puli wątków.</span><span class="sxs-lookup"><span data-stu-id="60935-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="60935-111">Wyjątki w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="60935-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="60935-112">Opisuje zachowanie nieobsługiwanych wyjątków w wątkach dla różnych wersji programu .NET Framework, w szczególności sytuacji w co ich spowodować przerwanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="60935-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="60935-113">Synchronizowanie danych na potrzeby wielowątkowości</span><span class="sxs-lookup"><span data-stu-id="60935-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="60935-114">W tym artykule opisano strategie synchronizacji danych w grupach, które będą używane z wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="60935-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="60935-115">Zarządzane stany wątków</span><span class="sxs-lookup"><span data-stu-id="60935-115">Managed Thread States</span></span>](../../../docs/standard/threading/managed-thread-states.md)  
 <span data-ttu-id="60935-116">Opisano stany wątków podstawowych oraz wyjaśniono, jak wykryć, czy wątek jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="60935-116">Describes the basic thread states, and explains how to detect whether a thread is running.</span></span>  
  
 [<span data-ttu-id="60935-117">Wątki pierwszego planu i tła</span><span class="sxs-lookup"><span data-stu-id="60935-117">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="60935-118">Wyjaśniono różnice między wątkami pierwszego planu i tła.</span><span class="sxs-lookup"><span data-stu-id="60935-118">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="60935-119">Zarządzana i niezarządzana wątkowość w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="60935-119">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="60935-120">Związek między zarządzana i niezarządzana wątkowość, zawiera listę zarządzanych odpowiedników wątkowość interfejsów API systemu Windows i w tym artykule omówiono interakcji apartamentach COM i zarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="60935-120">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="60935-121">Thread.Suspend, odzyskiwanie pamięci i punkty bezpieczeństwa</span><span class="sxs-lookup"><span data-stu-id="60935-121">Thread.Suspend, Garbage Collection, and Safe Points</span></span>](../../../docs/standard/threading/thread-suspend-garbage-collection-and-safe-points.md)  
 <span data-ttu-id="60935-122">W tym artykule opisano wątku zawieszenia i odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="60935-122">Describes thread suspension and garbage collection.</span></span>  
  
 [<span data-ttu-id="60935-123">Pamięć lokalna wątku: powiązane z wątkiem pola statyczne i gniazda danych</span><span class="sxs-lookup"><span data-stu-id="60935-123">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="60935-124">W tym artykule opisano mechanizmy magazynu powiązane z wątkiem.</span><span class="sxs-lookup"><span data-stu-id="60935-124">Describes thread-relative storage mechanisms.</span></span>  
  
 [<span data-ttu-id="60935-125">Anulowanie w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="60935-125">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 <span data-ttu-id="60935-126">Opisuje sposób asynchronicznego lub długotrwałe operacje synchroniczne mogą zostać anulowane za pomocą token anulowania.</span><span class="sxs-lookup"><span data-stu-id="60935-126">Describes how asynchronous or long-running synchronous operations can be canceled by using a cancellation token.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="60935-127">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="60935-127">Reference</span></span>  
 <xref:System.Threading.Thread>  
 <span data-ttu-id="60935-128">Zawiera dokumentacja referencyjna dla **wątku** klasy, która reprezentuje zarządzanego wątku, czy pochodzi kodu niezarządzanego, lub został utworzony w zarządzanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="60935-128">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="60935-129">Zapewnia bezpieczny sposób do zaimplementowania wielowątkowości w połączeniu z obiektów interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="60935-129">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="60935-130">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="60935-130">Related Sections</span></span>  
 [<span data-ttu-id="60935-131">Przegląd elementów podstawowych synchronizacji</span><span class="sxs-lookup"><span data-stu-id="60935-131">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="60935-132">W tym artykule opisano klasy zarządzane używane do synchronizowania działania wiele wątków.</span><span class="sxs-lookup"><span data-stu-id="60935-132">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="60935-133">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="60935-133">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="60935-134">W tym artykule opisano typowe problemy z wielowątkowość i strategii unikanie problemów.</span><span class="sxs-lookup"><span data-stu-id="60935-134">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="60935-135">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="60935-135">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="60935-136">Opisuje bibliotece równoległych zadań i PLINQ, co znacznie upraszcza pracy tworzenia aplikacji .NET Framework asynchroniczne i wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="60935-136">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
