---
title: Zarządzana wątkowość — podstawy
description: Zobacz linki do innych zarządzanych artykułów wątków, obejmujących tematy, takie jak wyjątki, synchronizowanie danych, pierwszy plan & wątki w tle, Magazyn lokalny i wiele innych.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: d4a4ceabf29bd0f6f537e59ba477f9da686b1ef5
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769096"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="5324a-103">Zarządzane wątki — podstawy</span><span class="sxs-lookup"><span data-stu-id="5324a-103">Managed threading basics</span></span>

<span data-ttu-id="5324a-104">Pięć pierwszych tematów tej sekcji zaprojektowano w celu ułatwienia ustalenia, kiedy należy używać zarządzanych wątków i wyjaśnić niektóre podstawowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="5324a-104">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="5324a-105">Aby uzyskać informacje na temat klas, które udostępniają dodatkowe funkcje, zobacz temat [wątkowość obiektów i funkcji](threading-objects-and-features.md) oraz [Przegląd elementów pierwotnych synchronizacji](overview-of-synchronization-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="5324a-105">For information on classes that provide additional features, see [Threading Objects and Features](threading-objects-and-features.md) and [Overview of Synchronization Primitives](overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="5324a-106">W pozostałych tematach w tej sekcji omówiono zaawansowane tematy, w tym interakcje zarządzanej wątkowości z systemem operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="5324a-106">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5324a-107">W .NET Framework 4, Biblioteka zadań równoległych i PLINQ zapewniają interfejsy API do równoległych zadań i danych w programach wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="5324a-107">In the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="5324a-108">Aby uzyskać więcej informacji, zobacz [programowanie równoległe](../parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="5324a-108">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5324a-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="5324a-109">In this section</span></span>

 [<span data-ttu-id="5324a-110">Wątki i wątkowość</span><span class="sxs-lookup"><span data-stu-id="5324a-110">Threads and Threading</span></span>](threads-and-threading.md)  
 <span data-ttu-id="5324a-111">W tym artykule omówiono zalety i wady wielu wątków oraz opisano scenariusze, w których można tworzyć wątki lub używać wątków puli wątków.</span><span class="sxs-lookup"><span data-stu-id="5324a-111">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="5324a-112">Wyjątki w zarządzanych wątkach</span><span class="sxs-lookup"><span data-stu-id="5324a-112">Exceptions in Managed Threads</span></span>](exceptions-in-managed-threads.md)  
 <span data-ttu-id="5324a-113">Opisuje zachowanie nieobsłużonych wyjątków w wątkach dla różnych wersji .NET Framework, w szczególności sytuacje, w których powodują zakończenie działania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5324a-113">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="5324a-114">Synchronizowanie danych na potrzeby wielowątkowości</span><span class="sxs-lookup"><span data-stu-id="5324a-114">Synchronizing Data for Multithreading</span></span>](synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="5324a-115">Opisuje strategie synchronizowania danych w klasach, które będą używane z wieloma wątkami.</span><span class="sxs-lookup"><span data-stu-id="5324a-115">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="5324a-116">Wątki pierwszego planu i tła</span><span class="sxs-lookup"><span data-stu-id="5324a-116">Foreground and Background Threads</span></span>](foreground-and-background-threads.md)  
 <span data-ttu-id="5324a-117">Wyjaśnia różnice między wątkami na pierwszym planie i w tle.</span><span class="sxs-lookup"><span data-stu-id="5324a-117">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="5324a-118">Zarządzana i niezarządzana wątkowość w systemie Windows</span><span class="sxs-lookup"><span data-stu-id="5324a-118">Managed and Unmanaged Threading in Windows</span></span>](managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="5324a-119">W tym artykule omówiono relacje między zarządzaną i niezarządzaną wielowątkowością, listę zarządzanych odpowiedników interfejsów API wątków systemu Windows i omówiono interakcję apartamentach COM i zarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="5324a-119">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="5324a-120">Pamięć lokalna wątku: powiązane z wątkiem pola statyczne i gniazda danych</span><span class="sxs-lookup"><span data-stu-id="5324a-120">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="5324a-121">Opisuje mechanizmy przechowywania względem wątków.</span><span class="sxs-lookup"><span data-stu-id="5324a-121">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5324a-122">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="5324a-122">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="5324a-123">Zawiera dokumentację referencyjną dla klasy **wątku** , która reprezentuje wątek zarządzany, niezależnie od tego, czy pochodzi ona z kodu niezarządzanego, czy też została utworzona w zarządzanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5324a-123">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="5324a-124">Zapewnia bezpieczny sposób implementacji wielowątkowości w połączeniu z obiektami interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5324a-124">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5324a-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5324a-125">Related sections</span></span>

 [<span data-ttu-id="5324a-126">Przegląd elementów podstawowych synchronizacji</span><span class="sxs-lookup"><span data-stu-id="5324a-126">Overview of Synchronization Primitives</span></span>](overview-of-synchronization-primitives.md)  
 <span data-ttu-id="5324a-127">Opisuje zarządzane klasy używane do synchronizowania działań wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="5324a-127">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="5324a-128">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="5324a-128">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="5324a-129">Opisuje typowe problemy związane z wielowątkowością i strategiami w celu uniknięcia problemów.</span><span class="sxs-lookup"><span data-stu-id="5324a-129">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="5324a-130">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="5324a-130">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="5324a-131">Opisuje bibliotekę zadań równoległych i PLINQ, co znacznie upraszcza pracę tworzenia asynchronicznych i wielowątkowych aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5324a-131">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
