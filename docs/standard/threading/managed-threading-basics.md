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
ms.openlocfilehash: 7241dfb7e31ed2f83bf7af0ecc6bf0d97363b999
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960362"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="58c5d-102">Zarządzana wątkowość — podstawy</span><span class="sxs-lookup"><span data-stu-id="58c5d-102">Managed threading basics</span></span>

<span data-ttu-id="58c5d-103">Pięciu pierwszych tematach w tej sekcji mają ułatwić ustalenie, kiedy używać zarządzanych wątkach i wyjaśnić niektóre podstawowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="58c5d-103">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="58c5d-104">Aby uzyskać informacji na temat klas, które zapewniają dodatkowe funkcje, zobacz [wątkowość obiektów i funkcji](../../../docs/standard/threading/threading-objects-and-features.md) i [Przegląd podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="58c5d-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="58c5d-105">Pozostałe tematy w tej sekcji cover zaawansowane tematy, w tym interakcję zarządzanych wątkach w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="58c5d-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58c5d-106">W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], bibliotece równoległych zadań i PLINQ zapewniają interfejsy API równoległość zadań i danych w programach wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="58c5d-106">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="58c5d-107">Aby uzyskać więcej informacji, zobacz [programowania równoległego](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="58c5d-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="58c5d-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="58c5d-108">In this section</span></span>

 [<span data-ttu-id="58c5d-109">Wątki i wątkowość</span><span class="sxs-lookup"><span data-stu-id="58c5d-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="58c5d-110">W tym artykule omówiono zalety i wady wielu wątków i opisano scenariusze, w których może utworzyć wątków lub użyj wątków z puli wątków.</span><span class="sxs-lookup"><span data-stu-id="58c5d-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="58c5d-111">Wyjątki w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="58c5d-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="58c5d-112">W tym artykule opisano zachowanie nieobsługiwanych wyjątków w wątkach dla różnych wersji programu .NET Framework, w szczególności sytuacje, w której powodują one zakończeniu działania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="58c5d-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="58c5d-113">Synchronizowanie danych na potrzeby wielowątkowości</span><span class="sxs-lookup"><span data-stu-id="58c5d-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="58c5d-114">W tym artykule opisano strategie synchronizowanie danych w klasach, które będą używane w wielu wątkach.</span><span class="sxs-lookup"><span data-stu-id="58c5d-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="58c5d-115">Wątki pierwszego planu i tła</span><span class="sxs-lookup"><span data-stu-id="58c5d-115">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="58c5d-116">W tym artykule wyjaśniono różnice między wątki pierwszego planu i tła.</span><span class="sxs-lookup"><span data-stu-id="58c5d-116">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="58c5d-117">Zarządzana i niezarządzana wątkowość w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="58c5d-117">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="58c5d-118">Związek między zarządzana i niezarządzana wątkowość, zawiera listę zarządzanych odpowiedników dla Windows wątkowości interfejsów API, a w tym artykule omówiono interakcji apartamentach COM i zarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="58c5d-118">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="58c5d-119">Lokalny magazyn wątków: Względne wątkom pola statyczne i gniazda danych</span><span class="sxs-lookup"><span data-stu-id="58c5d-119">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="58c5d-120">W tym artykule opisano mechanizmy względne wątkom magazynu.</span><span class="sxs-lookup"><span data-stu-id="58c5d-120">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="58c5d-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="58c5d-121">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="58c5d-122">Zawiera dokumentację referencyjną dla **wątku** klasy, która reprezentuje wątków zarządzanych, czy pochodzi z niezarządzanego kodu, czy został utworzony w zarządzanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="58c5d-122">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="58c5d-123">Zapewnia bezpieczny sposób implementacji wielowątkowości w połączeniu z obiektami interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="58c5d-123">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="58c5d-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="58c5d-124">Related sections</span></span>

 [<span data-ttu-id="58c5d-125">Przegląd elementów podstawowych synchronizacji</span><span class="sxs-lookup"><span data-stu-id="58c5d-125">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="58c5d-126">Zawiera opis klas zarządzanych, używane do synchronizowania działania wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="58c5d-126">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="58c5d-127">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="58c5d-127">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="58c5d-128">W tym artykule opisano typowe problemy z usługą wielowątkowości i strategii unikanie problemów.</span><span class="sxs-lookup"><span data-stu-id="58c5d-128">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="58c5d-129">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="58c5d-129">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="58c5d-130">W tym artykule opisano bibliotece równoległych zadań i PLINQ, które znacznie upraszczają pracę tworzenie wielowątkowych i asynchronicznego aplikacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="58c5d-130">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
