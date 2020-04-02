---
title: Zarządzana wątkowość
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: c5ca102dc98e50067d39d2f0c51a6ff75e342e9f
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588666"
---
# <a name="managed-threading"></a><span data-ttu-id="d96f0-102">Zarządzana wątkowość</span><span class="sxs-lookup"><span data-stu-id="d96f0-102">Managed Threading</span></span>
<span data-ttu-id="d96f0-103">Niezależnie od tego, czy tworzysz dla komputerów z jednym procesorem lub kilku, chcesz, aby aplikacja zapewniała najbardziej responsywną interakcję z użytkownikiem, nawet jeśli aplikacja obecnie wykonuje inną pracę.</span><span class="sxs-lookup"><span data-stu-id="d96f0-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="d96f0-104">Za pomocą wielu wątków wykonywania jest jednym z najbardziej zaawansowanych sposobów, aby aplikacja reaguje na użytkownika i jednocześnie korzystać z procesora pomiędzy lub nawet podczas zdarzeń użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d96f0-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="d96f0-105">W tej sekcji przedstawiono podstawowe pojęcia wątków, koncentruje się na zarządzanych pojęć wątków i przy użyciu zarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="d96f0-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d96f0-106">Począwszy od .NET Framework 4, programowanie <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> wielowątkowe <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> jest znacznie uproszczone z klasami [i, Parallel LINQ (PLINQ),](../../../docs/standard/parallel-programming/introduction-to-plinq.md)nowymi równoczesnymi klasami zbierania w obszarze <xref:System.Collections.Concurrent?displayProperty=nameWithType> nazw i nowym modelem programowania, który jest oparty na koncepcji zadań, a nie wątków.</span><span class="sxs-lookup"><span data-stu-id="d96f0-106">Starting with the .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="d96f0-107">Aby uzyskać więcej informacji, zobacz [Programowanie równoległe](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="d96f0-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d96f0-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d96f0-108">In This Section</span></span>  
 [<span data-ttu-id="d96f0-109">Zarządzana wątkowość — podstawy</span><span class="sxs-lookup"><span data-stu-id="d96f0-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="d96f0-110">Zawiera omówienie zarządzanych wątków i omówiono, kiedy należy używać wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="d96f0-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="d96f0-111">Korzystanie z wątków i wątków</span><span class="sxs-lookup"><span data-stu-id="d96f0-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="d96f0-112">W tym artykule wyjaśniono, jak tworzyć, uruchamiać, wstrzymywać, wznawiać i przerywać wątki.</span><span class="sxs-lookup"><span data-stu-id="d96f0-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="d96f0-113">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="d96f0-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="d96f0-114">W tym artykule omówiono poziomy synchronizacji, jak uniknąć zakleszczenia i warunki wyścigu i inne problemy wątkowe.</span><span class="sxs-lookup"><span data-stu-id="d96f0-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="d96f0-115">Wątki obiektów i operacji</span><span class="sxs-lookup"><span data-stu-id="d96f0-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="d96f0-116">W tym artykule opisano klasy zarządzane, których można użyć do synchronizacji działań wątków i danych obiektów dostępnych w różnych wątkach i zawiera omówienie wątków puli wątków.</span><span class="sxs-lookup"><span data-stu-id="d96f0-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d96f0-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="d96f0-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="d96f0-118">Zawiera klasy do używania i synchronizowania wątków zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="d96f0-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="d96f0-119">Zawiera klasy kolekcji, które są bezpieczne do użycia z wieloma wątkami.</span><span class="sxs-lookup"><span data-stu-id="d96f0-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="d96f0-120">Zawiera klasy do tworzenia i planowania równoczesnych zadań przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="d96f0-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d96f0-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d96f0-121">Related Sections</span></span>  
 [<span data-ttu-id="d96f0-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="d96f0-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="d96f0-123">Zawiera omówienie domen aplikacji i ich użycia przez infrastrukturę języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="d96f0-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="d96f0-124">Asynchroniczne We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="d96f0-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="d96f0-125">Opis korzyści związanych z wydajnością oraz podstawowych asynchronicznych operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="d96f0-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="d96f0-126">Wzorzec asynchroniczny oparty na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="d96f0-126">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="d96f0-127">Zawiera omówienie zalecanego wzorca dla programowania asynchroniowego w .NET.</span><span class="sxs-lookup"><span data-stu-id="d96f0-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="d96f0-128">Wywołanie metod synchronicznych w sposób asynchroniczny</span><span class="sxs-lookup"><span data-stu-id="d96f0-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="d96f0-129">Wyjaśniono, jak wywołać metody w wątkach puli wątków przy użyciu wbudowanych funkcji delegatów.</span><span class="sxs-lookup"><span data-stu-id="d96f0-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="d96f0-130">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="d96f0-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="d96f0-131">W tym artykule opisano biblioteki programowania równoległego, które upraszczają korzystanie z wielu wątków w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="d96f0-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="d96f0-132">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="d96f0-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
 <span data-ttu-id="d96f0-133">W tym artykule opisano system uruchamiania zapytań równolegle, aby skorzystać z wielu procesorów.</span><span class="sxs-lookup"><span data-stu-id="d96f0-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
