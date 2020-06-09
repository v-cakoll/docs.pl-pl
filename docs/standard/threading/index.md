---
title: Zarządzana wątkowość
description: Zobacz linki do artykułów na temat zarządzanych wątków w programie .NET obejmujących podstawowe, najlepsze rozwiązania, obiekty wątkowe & funkcje, strony referencyjne & więcej.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 7b46a7d9-c6f1-46d1-a947-ae97471bba87
ms.openlocfilehash: 570db45138c85c4252967404da4404d434660d69
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599753"
---
# <a name="managed-threading"></a><span data-ttu-id="a6175-103">Zarządzana wątkowość</span><span class="sxs-lookup"><span data-stu-id="a6175-103">Managed Threading</span></span>
<span data-ttu-id="a6175-104">Niezależnie od tego, czy tworzysz komputery z jednym procesorem, czy kilka, chcesz, aby aplikacja zapewniała najbardziej reagującą interakcję z użytkownikiem, nawet jeśli aplikacja wykonuje obecnie inne czynności.</span><span class="sxs-lookup"><span data-stu-id="a6175-104">Whether you are developing for computers with one processor or several, you want your application to provide the most responsive interaction with the user, even if the application is currently doing other work.</span></span> <span data-ttu-id="a6175-105">Korzystanie z wielu wątków wykonywania to jeden z najbardziej zaawansowanych sposobów, aby aplikacja mogła reagować na użytkownika, i w tym samym czasie używa procesora w okresie między lub nawet podczas zdarzeń użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a6175-105">Using multiple threads of execution is one of the most powerful ways to keep your application responsive to the user and at the same time make use of the processor in between or even during user events.</span></span> <span data-ttu-id="a6175-106">W tej sekcji przedstawiono podstawowe pojęcia związane z wątkami, które koncentrują się na zarządzanych pojęciach związanych z wątkami i korzystaniu z zarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="a6175-106">While this section introduces the basic concepts of threading, it focuses on managed threading concepts and using managed threading.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6175-107">Począwszy od .NET Framework 4, programowanie wielowątkowe jest znacznie uproszczone przy użyciu <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> klas i <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> , [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), nowych klas kolekcji współbieżnych w <xref:System.Collections.Concurrent?displayProperty=nameWithType> przestrzeni nazw oraz nowy model programowania oparty na koncepcji zadań, a nie w wątkach.</span><span class="sxs-lookup"><span data-stu-id="a6175-107">Starting with the .NET Framework 4, multithreaded programming is greatly simplified with the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> classes, [Parallel LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md), new concurrent collection classes in the <xref:System.Collections.Concurrent?displayProperty=nameWithType> namespace, and a new programming model that is based on the concept of tasks rather than threads.</span></span> <span data-ttu-id="a6175-108">Aby uzyskać więcej informacji, zobacz [programowanie równoległe](../parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="a6175-108">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6175-109">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a6175-109">In This Section</span></span>  
 [<span data-ttu-id="a6175-110">Zarządzana wątkowość — podstawy</span><span class="sxs-lookup"><span data-stu-id="a6175-110">Managed Threading Basics</span></span>](managed-threading-basics.md)  
 <span data-ttu-id="a6175-111">Zawiera omówienie zarządzania wątkami i omówiono, kiedy należy używać wielu wątków.</span><span class="sxs-lookup"><span data-stu-id="a6175-111">Provides an overview of managed threading and discusses when to use multiple threads.</span></span>  
  
 [<span data-ttu-id="a6175-112">Używanie wątków i wątkowości</span><span class="sxs-lookup"><span data-stu-id="a6175-112">Using Threads and Threading</span></span>](using-threads-and-threading.md)  
 <span data-ttu-id="a6175-113">Wyjaśnia, jak tworzyć, uruchamiać, wstrzymywać, wznawiać i przerywać wątki.</span><span class="sxs-lookup"><span data-stu-id="a6175-113">Explains how to create, start, pause, resume, and abort threads.</span></span>  
  
 [<span data-ttu-id="a6175-114">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="a6175-114">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="a6175-115">Omawia poziomy synchronizacji, sposób unikania zakleszczenii i warunków wyścigu oraz inne problemy z wątkami.</span><span class="sxs-lookup"><span data-stu-id="a6175-115">Discusses levels of synchronization, how to avoid deadlocks and race conditions, and other threading issues.</span></span>  
  
 [<span data-ttu-id="a6175-116">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="a6175-116">Threading Objects and Features</span></span>](threading-objects-and-features.md)  
 <span data-ttu-id="a6175-117">Opisuje zarządzane klasy, których można użyć do synchronizowania działań wątków i danych obiektów, do których dostęp odbywa się w różnych wątkach i zawiera Omówienie wątków puli wątków.</span><span class="sxs-lookup"><span data-stu-id="a6175-117">Describes the managed classes you can use to synchronize the activities of threads and the data of objects accessed on different threads, and provides an overview of thread pool threads.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a6175-118">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="a6175-118">Reference</span></span>  
 <xref:System.Threading>  
 <span data-ttu-id="a6175-119">Zawiera klasy służące do korzystania z i synchronizowania zarządzanych wątków.</span><span class="sxs-lookup"><span data-stu-id="a6175-119">Contains classes for using and synchronizing managed threads.</span></span>  
  
 <xref:System.Collections.Concurrent>  
 <span data-ttu-id="a6175-120">Zawiera klasy kolekcji, które są bezpieczne do użytku z wieloma wątkami.</span><span class="sxs-lookup"><span data-stu-id="a6175-120">Contains collection classes that are safe for use with multiple threads.</span></span>  
  
 <xref:System.Threading.Tasks>  
 <span data-ttu-id="a6175-121">Zawiera klasy służące do tworzenia i planowania współbieżnych zadań przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="a6175-121">Contains classes for creating and scheduling concurrent processing tasks.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a6175-122">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a6175-122">Related Sections</span></span>  
 [<span data-ttu-id="a6175-123">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="a6175-123">Application Domains</span></span>](../../framework/app-domains/application-domains.md)  
 <span data-ttu-id="a6175-124">Zawiera omówienie domen aplikacji i ich użycia przez Common Language Infrastructure.</span><span class="sxs-lookup"><span data-stu-id="a6175-124">Provides an overview of application domains and their use by the Common Language Infrastructure.</span></span>  
  
 [<span data-ttu-id="a6175-125">Asynchroniczne operacje we/wy pliku</span><span class="sxs-lookup"><span data-stu-id="a6175-125">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)  
 <span data-ttu-id="a6175-126">Opis korzyści związanych z wydajnością oraz podstawowych asynchronicznych operacji We/Wy.</span><span class="sxs-lookup"><span data-stu-id="a6175-126">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
 [<span data-ttu-id="a6175-127">Wzorzec asynchroniczny oparty na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="a6175-127">Task-based Asynchronous Pattern (TAP)</span></span>](../asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 <span data-ttu-id="a6175-128">Zawiera omówienie zalecanego wzorca dla programowania asynchronicznego w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="a6175-128">Provides an overview of the recommended pattern for asynchronous programming in .NET.</span></span>  
  
 [<span data-ttu-id="a6175-129">Wywołanie metod synchronicznych w sposób asynchroniczny</span><span class="sxs-lookup"><span data-stu-id="a6175-129">Calling Synchronous Methods Asynchronously</span></span>](../asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 <span data-ttu-id="a6175-130">Wyjaśnia, jak wywoływać metody w wątkach puli wątków przy użyciu wbudowanych funkcji delegatów.</span><span class="sxs-lookup"><span data-stu-id="a6175-130">Explains how to call methods on thread pool threads using built-in features of delegates.</span></span>  
  
 [<span data-ttu-id="a6175-131">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="a6175-131">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="a6175-132">Opisuje równoległe biblioteki programistyczne, które upraszczają korzystanie z wielu wątków w aplikacjach.</span><span class="sxs-lookup"><span data-stu-id="a6175-132">Describes the parallel programming libraries, which simplify the use of multiple threads in applications.</span></span>  
  
 [<span data-ttu-id="a6175-133">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="a6175-133">Parallel LINQ (PLINQ)</span></span>](../parallel-programming/introduction-to-plinq.md)  
 <span data-ttu-id="a6175-134">Opisuje system uruchamiania zapytań równolegle, aby korzystać z wielu procesorów.</span><span class="sxs-lookup"><span data-stu-id="a6175-134">Describes a system for running queries in parallel, to take advantage of multiple processors.</span></span>
