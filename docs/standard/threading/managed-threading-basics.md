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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139227"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="455e4-102">Podstawy wątków zarządzanych</span><span class="sxs-lookup"><span data-stu-id="455e4-102">Managed threading basics</span></span>

<span data-ttu-id="455e4-103">Pierwsze pięć tematów tej sekcji zostały zaprojektowane, aby ułatwić określenie, kiedy używać zarządzanych wątków i wyjaśnić niektóre podstawowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="455e4-103">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="455e4-104">Aby uzyskać informacje na temat klas, które zapewniają dodatkowe funkcje, zobacz [Threading obiekty i funkcje](../../../docs/standard/threading/threading-objects-and-features.md) i [Omówienie podstawowych synchronizacji](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="455e4-104">For information on classes that provide additional features, see [Threading Objects and Features](../../../docs/standard/threading/threading-objects-and-features.md) and [Overview of Synchronization Primitives](../../../docs/standard/threading/overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="455e4-105">Pozostałe tematy w tej sekcji obejmują zaawansowane tematy, w tym interakcję zarządzanego wątków z systemem operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="455e4-105">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="455e4-106">W .NET Framework 4 Biblioteka równoległa zadań i PLINQ zapewniają interfejsy API dla równoległości zadań i danych w programach wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="455e4-106">In the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="455e4-107">Aby uzyskać więcej informacji, zobacz [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="455e4-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="455e4-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="455e4-108">In this section</span></span>

 [<span data-ttu-id="455e4-109">Wątki i wątkowość</span><span class="sxs-lookup"><span data-stu-id="455e4-109">Threads and Threading</span></span>](../../../docs/standard/threading/threads-and-threading.md)  
 <span data-ttu-id="455e4-110">W tym artykule omówiono zalety i wady wielu wątków i przedstawia scenariusze, w których można utworzyć wątki lub użyć wątków puli wątków.</span><span class="sxs-lookup"><span data-stu-id="455e4-110">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="455e4-111">Wyjątki w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="455e4-111">Exceptions in Managed Threads</span></span>](../../../docs/standard/threading/exceptions-in-managed-threads.md)  
 <span data-ttu-id="455e4-112">Opisuje zachowanie nieobsługiwanych wyjątków w wątkach dla różnych wersji programu .NET Framework, w szczególności sytuacje, w których powodują one zakończenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="455e4-112">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="455e4-113">Synchronizowanie danych na potrzeby wielowątkowości</span><span class="sxs-lookup"><span data-stu-id="455e4-113">Synchronizing Data for Multithreading</span></span>](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="455e4-114">W tym artykule opisano strategie synchronizowania danych w klasach, które będą używane z wieloma wątkami.</span><span class="sxs-lookup"><span data-stu-id="455e4-114">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="455e4-115">Wątki pierwszego planu i tła</span><span class="sxs-lookup"><span data-stu-id="455e4-115">Foreground and Background Threads</span></span>](../../../docs/standard/threading/foreground-and-background-threads.md)  
 <span data-ttu-id="455e4-116">W tym artykule wyjaśniono różnice między wątkami pierwszego planu i tła.</span><span class="sxs-lookup"><span data-stu-id="455e4-116">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="455e4-117">Zarządzana i niezarządzana wątkowość w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="455e4-117">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="455e4-118">W tym artykule omówiono relację między zarządzanym i niezarządzanym wątkowaniem, wyświetla listę zarządzanych odpowiedników interfejsów API wątków systemu Windows i omówiono interakcję apartamentów COM i wątków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="455e4-118">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="455e4-119">Pamięć lokalna wątku: powiązane z wątkiem pola statyczne i gniazda danych</span><span class="sxs-lookup"><span data-stu-id="455e4-119">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](../../../docs/standard/threading/thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="455e4-120">Opisuje mechanizmy magazynu względnego wątku.</span><span class="sxs-lookup"><span data-stu-id="455e4-120">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="455e4-121">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="455e4-121">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="455e4-122">Zawiera dokumentację referencyjną dla **Thread** klasy, która reprezentuje wątek zarządzany, czy pochodzi z kodu niezarządzanego lub został utworzony w aplikacji zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="455e4-122">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="455e4-123">Zapewnia bezpieczny sposób implementowania wielowątkowości w połączeniu z obiektami interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="455e4-123">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="455e4-124">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="455e4-124">Related sections</span></span>

 [<span data-ttu-id="455e4-125">Omówienie elementów pierwotnych synchronizacji</span><span class="sxs-lookup"><span data-stu-id="455e4-125">Overview of Synchronization Primitives</span></span>](../../../docs/standard/threading/overview-of-synchronization-primitives.md)  
 <span data-ttu-id="455e4-126">Opisuje klasy zarządzane używane do synchronizowania działań wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="455e4-126">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="455e4-127">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="455e4-127">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="455e4-128">Opisuje typowe problemy z wielowątkowości i strategii unikania problemów.</span><span class="sxs-lookup"><span data-stu-id="455e4-128">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="455e4-129">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="455e4-129">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="455e4-130">Opisuje bibliotekę równoległą zadania i PLINQ, które znacznie upraszczają pracę tworzenia aplikacji asynchronicznych i wielowątkowych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="455e4-130">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
