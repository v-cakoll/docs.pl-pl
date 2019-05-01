---
title: Zarządzana wątkowość
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6447cd37e4718093acfb3a0e2db053c13a027d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62015146"
---
# <a name="managed-threading"></a><span data-ttu-id="45501-102">Zarządzana wątkowość</span><span class="sxs-lookup"><span data-stu-id="45501-102">Managed Threading</span></span>
<span data-ttu-id="45501-103">Czy jest tworzona dla komputerów z procesorem jeden lub kilka, ma aplikację w celu zapewnienia najbardziej elastyczny interakcji z użytkownikiem, nawet wtedy, gdy aplikacja wykonuje aktualnie inne prace.</span><span class="sxs-lookup"><span data-stu-id="45501-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="45501-104">Przy użyciu wielu wątków wykonania jest jednym z najbardziej zaawansowanych sposobów prace nad aplikacją reagować na działania użytkownika i w tym samym czasie wykorzystanie procesora pomiędzy lub nawet w trakcie zdarzenia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="45501-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="45501-105">Gdy ten rudział przedstawia podstawowe pojęcia wątkowości, koncentruje się na zarządzanym pojęcia wielowątkowości i przy użyciu zarządzanych wątkach.</span><span class="sxs-lookup"><span data-stu-id="45501-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45501-106">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], programowanie wielowątkowe zostało znacznie uproszczone dzięki <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> klas, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), nowej kolekcji współbieżnych klas w <xref:System.Collections.Concurrent?displayProperty=nameWithType> przestrzeń nazw, a nowy model programowania, który opiera się na koncepcji zadania, a nie wątków.</span><span class="sxs-lookup"><span data-stu-id="45501-106">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="45501-107">Aby uzyskać więcej informacji, zobacz [programowania równoległego](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="45501-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45501-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="45501-108">In This Section</span></span>  
 [<span data-ttu-id="45501-109">Zarządzana wątkowość — podstawy</span><span class="sxs-lookup"><span data-stu-id="45501-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="45501-110">Zawiera omówienie zarządzanych wątkach i omówiono, kiedy należy używać wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="45501-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="45501-111">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="45501-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="45501-112">Opis sposobu tworzenia, uruchamiania, wstrzymać, wznowić i przerwać wątków.</span><span class="sxs-lookup"><span data-stu-id="45501-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="45501-113">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="45501-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="45501-114">W tym artykule omówiono poziomy synchronizacji, wystawia sposoby unikania zakleszczeń i sytuacje wyścigu, a inne wątki.</span><span class="sxs-lookup"><span data-stu-id="45501-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="45501-115">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="45501-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="45501-116">Zawiera opis klas zarządzanych, które służy do synchronizowania działania wątków i dane obiektami w różnych wątkach i zawiera omówienie wątków z puli wątków.</span><span class="sxs-lookup"><span data-stu-id="45501-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="45501-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="45501-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="45501-118">Zawiera klasy dla przy użyciu i synchronizowanie zarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="45501-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="45501-119">Zawiera klasy kolekcji, które są bezpiecznie używać w wielu wątkach.</span><span class="sxs-lookup"><span data-stu-id="45501-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="45501-120">Zawiera klasy służące do tworzenia i planowania zadań jednoczesnych przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="45501-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="45501-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="45501-121">Related Sections</span></span>  
 [<span data-ttu-id="45501-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="45501-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="45501-123">Zawiera omówienie domen aplikacji i ich użycie przez Common Language Infrastructure.</span><span class="sxs-lookup"><span data-stu-id="45501-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="45501-124">Asynchroniczne operacje We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="45501-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="45501-125">Opis korzyści związanych z wydajnością oraz podstawowych asynchronicznych operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="45501-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="45501-126">Wzorzec asynchroniczny oparty na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="45501-126">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="45501-127">Zawiera omówienie zalecany wzorzec dla programowania asynchronicznego w .NET.</span><span class="sxs-lookup"><span data-stu-id="45501-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="45501-128">Wywoływanie metod synchronicznych w sposób asynchroniczny</span><span class="sxs-lookup"><span data-stu-id="45501-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="45501-129">Wyjaśnia, jak wywoływać metody dla wątku za pomocą wbudowanych funkcji obiektów delegowanych z puli wątków.</span><span class="sxs-lookup"><span data-stu-id="45501-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="45501-130">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="45501-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="45501-131">W tym artykule opisano równoległego programowania bibliotek, które upraszczają korzystanie z wielu wątków w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="45501-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="45501-132">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="45501-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 <span data-ttu-id="45501-133">W tym artykule opisano systemem do uruchamiania zapytań równolegle, aby móc korzystać z wielu procesorów.</span><span class="sxs-lookup"><span data-stu-id="45501-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
