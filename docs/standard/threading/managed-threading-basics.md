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
ms.openlocfilehash: bec769043ab630b37609bed12302ceff5b90474a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139227"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="0af92-102">Zarządzane wątki — podstawy</span><span class="sxs-lookup"><span data-stu-id="0af92-102">Managed threading basics</span></span>

<span data-ttu-id="0af92-103">Pięć pierwszych tematów tej sekcji zaprojektowano w celu ułatwienia ustalenia, kiedy należy używać zarządzanych wątków i wyjaśnić niektóre podstawowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="0af92-103">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="0af92-104">Aby uzyskać informacje na temat klas, które udostępniają dodatkowe funkcje, zobacz temat [wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md) oraz [Przegląd elementów pierwotnych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="0af92-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="0af92-105">W pozostałych tematach w tej sekcji omówiono zaawansowane tematy, w tym interakcje zarządzanej wątkowości z systemem operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="0af92-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0af92-106">W .NET Framework 4, Biblioteka zadań równoległych i PLINQ zapewniają interfejsy API do równoległych zadań i danych w programach wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="0af92-106">In the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="0af92-107">Aby uzyskać więcej informacji, zobacz [programowanie równoległe](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="0af92-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0af92-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0af92-108">In this section</span></span>

 [<span data-ttu-id="0af92-109">Wątki i wątkowość</span><span class="sxs-lookup"><span data-stu-id="0af92-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="0af92-110">W tym artykule omówiono zalety i wady wielu wątków oraz opisano scenariusze, w których można tworzyć wątki lub używać wątków puli wątków.</span><span class="sxs-lookup"><span data-stu-id="0af92-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="0af92-111">Wyjątki w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="0af92-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="0af92-112">Opisuje zachowanie nieobsłużonych wyjątków w wątkach dla różnych wersji .NET Framework, w szczególności sytuacje, w których powodują zakończenie działania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0af92-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="0af92-113">Synchronizowanie danych na potrzeby wielowątkowości</span><span class="sxs-lookup"><span data-stu-id="0af92-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="0af92-114">Opisuje strategie synchronizowania danych w klasach, które będą używane z wieloma wątkami.</span><span class="sxs-lookup"><span data-stu-id="0af92-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="0af92-115">Wątki pierwszego planu i tła</span><span class="sxs-lookup"><span data-stu-id="0af92-115">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="0af92-116">Wyjaśnia różnice między wątkami na pierwszym planie i w tle.</span><span class="sxs-lookup"><span data-stu-id="0af92-116">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="0af92-117">Zarządzana i niezarządzana wątkowość w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="0af92-117">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="0af92-118">W tym artykule omówiono relacje między zarządzaną i niezarządzaną wielowątkowością, listę zarządzanych odpowiedników interfejsów API wątków systemu Windows i omówiono interakcję apartamentach COM i zarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="0af92-118">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="0af92-119">Pamięć lokalna wątku: powiązane z wątkiem pola statyczne i gniazda danych</span><span class="sxs-lookup"><span data-stu-id="0af92-119">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="0af92-120">Opisuje mechanizmy przechowywania względem wątków.</span><span class="sxs-lookup"><span data-stu-id="0af92-120">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0af92-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="0af92-121">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="0af92-122">Zawiera dokumentację referencyjną dla klasy **wątku** , która reprezentuje wątek zarządzany, niezależnie od tego, czy pochodzi ona z kodu niezarządzanego, czy też została utworzona w zarządzanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0af92-122">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="0af92-123">Zapewnia bezpieczny sposób implementacji wielowątkowości w połączeniu z obiektami interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0af92-123">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0af92-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0af92-124">Related sections</span></span>

 [<span data-ttu-id="0af92-125">Przegląd elementów podstawowych synchronizacji</span><span class="sxs-lookup"><span data-stu-id="0af92-125">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="0af92-126">Opisuje zarządzane klasy używane do synchronizowania działań wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="0af92-126">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="0af92-127">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="0af92-127">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="0af92-128">Opisuje typowe problemy związane z wielowątkowością i strategiami w celu uniknięcia problemów.</span><span class="sxs-lookup"><span data-stu-id="0af92-128">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="0af92-129">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="0af92-129">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="0af92-130">Opisuje bibliotekę zadań równoległych i PLINQ, co znacznie upraszcza pracę tworzenia asynchronicznych i wielowątkowych aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0af92-130">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
