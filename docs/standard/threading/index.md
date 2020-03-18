---
title: Zarządzana wątkowość
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: d6b8a0a4e16aa3169888958fa1376bfa61526dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137929"
---
# <a name="managed-threading"></a><span data-ttu-id="bc27d-102">Zarządzana wątkowość</span><span class="sxs-lookup"><span data-stu-id="bc27d-102">Managed Threading</span></span>
<span data-ttu-id="bc27d-103">Niezależnie od tego, czy tworzysz komputery z jednym procesorem, czy kilkoma, aplikacja ma zapewniać najbardziej responsywną interakcję z użytkownikiem, nawet jeśli aplikacja wykonuje obecnie inną pracę.</span><span class="sxs-lookup"><span data-stu-id="bc27d-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="bc27d-104">Przy użyciu wielu wątków wykonywania jest jednym z najbardziej zaawansowanych sposobów, aby utrzymać aplikację reaguje na użytkownika i jednocześnie korzystać z procesora pomiędzy lub nawet podczas zdarzeń użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bc27d-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="bc27d-105">Podczas gdy w tej sekcji wprowadza podstawowe pojęcia wątków, koncentruje się na zarządzanych wątków i przy użyciu zarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="bc27d-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bc27d-106">Począwszy od .NET Framework 4, programowanie wielowątkowe <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> jest znacznie uproszczone za pomocą i klas, Parallel <xref:System.Collections.Concurrent?displayProperty=nameWithType> [LINQ (PLINQ),](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)nowych klas kolekcji równoczesnych w przestrzeni nazw i nowego modelu programowania, który jest oparty na koncepcji zadań, a nie wątków.</span><span class="sxs-lookup"><span data-stu-id="bc27d-106">Starting with the .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="bc27d-107">Aby uzyskać więcej informacji, zobacz [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="bc27d-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bc27d-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="bc27d-108">In This Section</span></span>  
 [<span data-ttu-id="bc27d-109">Zarządzana wątkowość — podstawy</span><span class="sxs-lookup"><span data-stu-id="bc27d-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="bc27d-110">Zawiera omówienie zarządzanych wątków i omówiono, kiedy należy używać wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="bc27d-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="bc27d-111">Korzystanie z wątków i wątków</span><span class="sxs-lookup"><span data-stu-id="bc27d-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="bc27d-112">W tym artykule wyjaśniono, jak tworzyć, uruchamiać, wstrzymywać, wznawiać i przerywać wątki.</span><span class="sxs-lookup"><span data-stu-id="bc27d-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="bc27d-113">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="bc27d-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="bc27d-114">W tym artykule omówiono poziomy synchronizacji, jak uniknąć zakleszczenia i warunków wyścigu i innych problemów wątków.</span><span class="sxs-lookup"><span data-stu-id="bc27d-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="bc27d-115">Wątkowe obiekty i operacje</span><span class="sxs-lookup"><span data-stu-id="bc27d-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="bc27d-116">Opisuje klasy zarządzane, których można użyć do synchronizacji działań wątków i danych obiektów dostępnych w różnych wątkach i zawiera omówienie wątków puli wątków.</span><span class="sxs-lookup"><span data-stu-id="bc27d-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bc27d-117">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="bc27d-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="bc27d-118">Zawiera klasy do używania i synchronizowania wątków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="bc27d-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="bc27d-119">Zawiera klasy kolekcji, które są bezpieczne do użytku z wieloma wątkami.</span><span class="sxs-lookup"><span data-stu-id="bc27d-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="bc27d-120">Zawiera klasy do tworzenia i planowania równoczesnych zadań przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="bc27d-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bc27d-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="bc27d-121">Related Sections</span></span>  
 [<span data-ttu-id="bc27d-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="bc27d-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="bc27d-123">Zawiera omówienie domen aplikacji i ich używania przez infrastrukturę języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="bc27d-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="bc27d-124">Asynchroniczne We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="bc27d-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="bc27d-125">Opis korzyści związanych z wydajnością oraz podstawowych asynchronicznych operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="bc27d-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="bc27d-126">Wzorzec asynchroniczny oparty na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="bc27d-126">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="bc27d-127">Zawiera omówienie zalecanego wzorca programowania asynchronicznego w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="bc27d-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="bc27d-128">Wywołanie metod synchronicznych w sposób asynchroniczny</span><span class="sxs-lookup"><span data-stu-id="bc27d-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="bc27d-129">W tym artykule wyjaśniono, jak wywoływać metody w wątkach puli wątków przy użyciu wbudowanych funkcji delegatów.</span><span class="sxs-lookup"><span data-stu-id="bc27d-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="bc27d-130">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="bc27d-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="bc27d-131">Opisuje równoległe biblioteki programowania, które upraszczają korzystanie z wielu wątków w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="bc27d-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="bc27d-132">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="bc27d-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 <span data-ttu-id="bc27d-133">W tym artykule opisano system do uruchamiania kwerend równolegle, aby skorzystać z wielu procesorów.</span><span class="sxs-lookup"><span data-stu-id="bc27d-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
