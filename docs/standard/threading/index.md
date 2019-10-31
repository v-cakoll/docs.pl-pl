---
title: Zarządzana wątkowość
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: d6b8a0a4e16aa3169888958fa1376bfa61526dbd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137929"
---
# <a name="managed-threading"></a><span data-ttu-id="bd024-102">Zarządzana wątkowość</span><span class="sxs-lookup"><span data-stu-id="bd024-102">Managed Threading</span></span>
<span data-ttu-id="bd024-103">Niezależnie od tego, czy tworzysz komputery z jednym procesorem, czy kilka, chcesz, aby aplikacja zapewniała najbardziej reagującą interakcję z użytkownikiem, nawet jeśli aplikacja wykonuje obecnie inne czynności.</span><span class="sxs-lookup"><span data-stu-id="bd024-103">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="bd024-104">Korzystanie z wielu wątków wykonywania to jeden z najbardziej zaawansowanych sposobów, aby aplikacja mogła reagować na użytkownika, i w tym samym czasie używa procesora w okresie między lub nawet podczas zdarzeń użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bd024-104">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="bd024-105">W tej sekcji przedstawiono podstawowe pojęcia związane z wątkami, które koncentrują się na zarządzanych pojęciach związanych z wątkami i korzystaniu z zarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="bd024-105">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd024-106">Począwszy od .NET Framework 4, programowanie wielowątkowe jest znacznie uproszczone przy użyciu klas <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), nowych klas kolekcji współbieżnych w przestrzeni nazw <xref:System.Collections.Concurrent?displayProperty=nameWithType> i nowego modelu programowania na podstawie koncepcji zadań, a nie wątków.</span><span class="sxs-lookup"><span data-stu-id="bd024-106">Starting with the .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="bd024-107">Aby uzyskać więcej informacji, zobacz [programowanie równoległe](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="bd024-107">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bd024-108">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="bd024-108">In This Section</span></span>  
 [<span data-ttu-id="bd024-109">Zarządzana wątkowość — podstawy</span><span class="sxs-lookup"><span data-stu-id="bd024-109">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)  
 <span data-ttu-id="bd024-110">Zawiera omówienie zarządzania wątkami i omówiono, kiedy należy używać wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="bd024-110">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="bd024-111">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="bd024-111">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 <span data-ttu-id="bd024-112">Wyjaśnia, jak tworzyć, uruchamiać, wstrzymywać, wznawiać i przerywać wątki.</span><span class="sxs-lookup"><span data-stu-id="bd024-112">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="bd024-113">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="bd024-113">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 <span data-ttu-id="bd024-114">Omawia poziomy synchronizacji, sposób unikania zakleszczenii i warunków wyścigu oraz inne problemy z wątkami.</span><span class="sxs-lookup"><span data-stu-id="bd024-114">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="bd024-115">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="bd024-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 <span data-ttu-id="bd024-116">Opisuje zarządzane klasy, których można użyć do synchronizowania działań wątków i danych obiektów, do których dostęp odbywa się w różnych wątkach i zawiera Omówienie wątków puli wątków.</span><span class="sxs-lookup"><span data-stu-id="bd024-116">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="bd024-117">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="bd024-117">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="bd024-118">Zawiera klasy służące do korzystania z i synchronizowania zarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="bd024-118">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="bd024-119">Zawiera klasy kolekcji, które są bezpieczne do użytku z wieloma wątkami.</span><span class="sxs-lookup"><span data-stu-id="bd024-119">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="bd024-120">Zawiera klasy służące do tworzenia i planowania współbieżnych zadań przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="bd024-120">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bd024-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="bd024-121">Related Sections</span></span>  
 [<span data-ttu-id="bd024-122">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="bd024-122">Application Domains</span></span>](../../../docs/framework/app-domains/application-domains.md)  
 <span data-ttu-id="bd024-123">Zawiera omówienie domen aplikacji i ich użycia przez Common Language Infrastructure.</span><span class="sxs-lookup"><span data-stu-id="bd024-123">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="bd024-124">Asynchroniczne operacje We/Wy pliku</span><span class="sxs-lookup"><span data-stu-id="bd024-124">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 <span data-ttu-id="bd024-125">Opis korzyści związanych z wydajnością oraz podstawowych asynchronicznych operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="bd024-125">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="bd024-126">Wzorzec asynchroniczny oparty na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="bd024-126">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="bd024-127">Zawiera omówienie zalecanego wzorca dla programowania asynchronicznego w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="bd024-127">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="bd024-128">Wywoływanie metod synchronicznych w sposób asynchroniczny</span><span class="sxs-lookup"><span data-stu-id="bd024-128">Calling Synchronous Methods Asynchronously</span></span>](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="bd024-129">Wyjaśnia, jak wywoływać metody w wątkach puli wątków przy użyciu wbudowanych funkcji delegatów.</span><span class="sxs-lookup"><span data-stu-id="bd024-129">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="bd024-130">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="bd024-130">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 <span data-ttu-id="bd024-131">Opisuje równoległe biblioteki programistyczne, które upraszczają korzystanie z wielu wątków w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="bd024-131">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="bd024-132">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="bd024-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 <span data-ttu-id="bd024-133">Opisuje system uruchamiania zapytań równolegle, aby korzystać z wielu procesorów.</span><span class="sxs-lookup"><span data-stu-id="bd024-133">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
