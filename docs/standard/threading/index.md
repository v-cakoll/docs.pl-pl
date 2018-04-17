---
title: Zarządzana wątkowość
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
caps.latest.revision: 19
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 26f69429bb6ee479bd981474513698bf27993564
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="managed-threading"></a><span data-ttu-id="4cdbe-102">Zarządzana wątkowość</span><span class="sxs-lookup"><span data-stu-id="4cdbe-102">Managed Threading</span></span>
<span data-ttu-id="4cdbe-103">Czy tworzysz dla komputerów z procesorem jednego lub kilku, mają Twojej aplikacji w celu umożliwienia najbardziej reakcji interakcji z użytkownikiem, nawet wtedy, gdy aplikacja jest aktualnie wykonywanych czynności inne zadania.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="4cdbe-104">Używanie wielu wątków wykonywania jest jednym z najbardziej zaawansowanych sposoby Zachowaj reakcji użytkownikowi aplikacji i w tym samym czasie wykorzystanie procesora w między lub nawet podczas zdarzeń użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="4cdbe-105">Gdy w tej sekcji przedstawiono podstawowe pojęcia związane z wątków, koncentruje się na zarządzanych wątków koncepcje i przy użyciu zarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4cdbe-106">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], znacznie upraszcza programowanie wielowątkowe z <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> klas, [równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), nowej kolekcji współbieżnych klas w <xref:System.Collections.Concurrent?displayProperty=nameWithType> przestrzeń nazw, a nowy model programowania opartego na koncepcji zadania, a nie wątków.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-106">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="4cdbe-107">Aby uzyskać więcej informacji, zobacz [programowania równoległego](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="4cdbe-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4cdbe-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="4cdbe-108">In This Section</span></span>  
 [<span data-ttu-id="4cdbe-109">Zarządzana wątkowość — podstawy</span><span class="sxs-lookup"><span data-stu-id="4cdbe-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="4cdbe-110">Omówienie wątków zarządzanych i omówiono, kiedy należy używać wiele wątków.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="4cdbe-111">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="4cdbe-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="4cdbe-112">Opisano sposób tworzenia, uruchamiania, wstrzymać, wznowić i abort wątków.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="4cdbe-113">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="4cdbe-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="4cdbe-114">Omówienie poziomów synchronizacji, jak uniknąć zakleszczenie i sytuacja wyścigu, jeden procesor i komputerach wieloprocesorowych i inne problemy z wątków.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, single-processor and multiprocessor computers, and other threading issues.</span></span>  
  
 [<span data-ttu-id="4cdbe-115">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="4cdbe-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="4cdbe-116">Zawiera opis klas zarządzanych, które służy do synchronizowania działania wątków i danych dostępne w różnych wątkach obiektów i zawiera omówienie wątków z puli wątków.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4cdbe-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="4cdbe-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="4cdbe-118">Zawiera klasy przy użyciu i synchronizacja wątków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="4cdbe-119">Zawiera klasy kolekcji, które są bezpieczne dla użytku z wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="4cdbe-120">Zawiera klasy służące do tworzenia i planowania zadań jednoczesnych przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4cdbe-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="4cdbe-121">Related Sections</span></span>  
 [<span data-ttu-id="4cdbe-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="4cdbe-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="4cdbe-123">Zawiera omówienie domen aplikacji i ich użycie za pomocą wspólnej infrastruktury języka.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="4cdbe-124">Asynchroniczne operacje We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="4cdbe-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="4cdbe-125">Opis korzyści związanych z wydajnością oraz podstawowych asynchronicznych operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="4cdbe-126">Wzorzec asynchroniczny oparty na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="4cdbe-126">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="4cdbe-127">Omówienie zalecanych wzorca dla programowania asynchronicznego w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="4cdbe-128">Wywoływanie metod synchronicznych w sposób asynchroniczny</span><span class="sxs-lookup"><span data-stu-id="4cdbe-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="4cdbe-129">Wyjaśniono, jak wywoływać metod w wątku puli wątków przy użyciu wbudowanych funkcji obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="4cdbe-130">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="4cdbe-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="4cdbe-131">W tym artykule opisano równoległe programowania, bibliotek, co upraszcza używanie wielu wątków w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="4cdbe-132">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="4cdbe-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 <span data-ttu-id="4cdbe-133">W tym artykule opisano system uruchamiania zapytań równolegle, aby móc korzystać z wielu procesorów.</span><span class="sxs-lookup"><span data-stu-id="4cdbe-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
