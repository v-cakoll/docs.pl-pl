---
title: Asynchroniczny wzorzec oparty na zdarzeniach (EAP)
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7811113244d8c5f7d79a55ebb01f04e99e9bd2a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="ff7c4-102">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="ff7c4-102">Event-based Asynchronous Pattern (EAP)</span></span>
<span data-ttu-id="ff7c4-103">Istnieje wiele sposobów, aby udostępnić funkcje asynchroniczne do kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="ff7c4-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="ff7c4-104">Asynchroniczny wzorzec oparty na zdarzeniach Określa jedną z metod dla klas do prezentowania zachowanie asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="ff7c4-104">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ff7c4-105">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], biblioteka zadań równoległych zapewnia nowy model programowania asynchronicznego i równolegle.</span><span class="sxs-lookup"><span data-stu-id="ff7c4-105">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="ff7c4-106">Aby uzyskać więcej informacji, zobacz [programowania równoległego](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="ff7c4-106">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ff7c4-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ff7c4-107">In This Section</span></span>  
 [<span data-ttu-id="ff7c4-108">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="ff7c4-108">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="ff7c4-109">W tym artykule opisano, jak wzorca asynchronicznego opartego na zdarzeniach udostępnia zalety aplikacji wielowątkowych wiele złożonych problemów w wielowątkowe projektu są ukryte.</span><span class="sxs-lookup"><span data-stu-id="ff7c4-109">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="ff7c4-110">Implementowanie wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="ff7c4-110">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="ff7c4-111">Opisuje sposób Zestandaryzowany do pakietu klasy, która ma funkcje asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="ff7c4-111">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="ff7c4-112">Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ff7c4-112">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="ff7c4-113">Opisuje wymagania dotyczące udostępnianie funkcje asynchroniczne zgodnie ze wzorca asynchronicznego opartego na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="ff7c4-113">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="ff7c4-114">Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="ff7c4-114">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="ff7c4-115">Opisuje sposób określania, kiedy użytkownik powinien wybrać implementacji wzorca asynchronicznego opartego na zdarzeniach zamiast <xref:System.IAsyncResult> wzorca.</span><span class="sxs-lookup"><span data-stu-id="ff7c4-115">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern.</span></span>  
  
 [<span data-ttu-id="ff7c4-116">Przewodnik: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="ff7c4-116">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="ff7c4-117">Ilustruje sposób tworzenia składnika, który implementuje wzorzec asynchroniczny oparty na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="ff7c4-117">Illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="ff7c4-118">Jest stosowana przy użyciu klasy pomocy z <xref:System.ComponentModel?displayProperty=nameWithType> przestrzeni nazw, który zapewnia składnika działa prawidłowo w dowolnej aplikacji modelu.</span><span class="sxs-lookup"><span data-stu-id="ff7c4-118">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  
  
 [<span data-ttu-id="ff7c4-119">Instrukcje: Używanie składników obsługujących wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="ff7c4-119">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="ff7c4-120">Informacje dotyczące używania składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="ff7c4-120">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ff7c4-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="ff7c4-121">Reference</span></span>  
 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="ff7c4-122">W tym artykule opisano <xref:System.ComponentModel.AsyncOperation> klasy i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="ff7c4-122">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="ff7c4-123">W tym artykule opisano <xref:System.ComponentModel.AsyncOperationManager> klasy i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="ff7c4-123">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="ff7c4-124">W tym artykule opisano <xref:System.ComponentModel.BackgroundWorker> części oraz zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="ff7c4-124">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ff7c4-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ff7c4-125">Related Sections</span></span>  
 [<span data-ttu-id="ff7c4-126">Biblioteka zadań równoległych (TPL)</span><span class="sxs-lookup"><span data-stu-id="ff7c4-126">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="ff7c4-127">W tym artykule opisano model programowania dla operacji asynchronicznych i równolegle.</span><span class="sxs-lookup"><span data-stu-id="ff7c4-127">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="ff7c4-128">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="ff7c4-128">Threading</span></span>](../../../docs/standard/threading/index.md)  
 <span data-ttu-id="ff7c4-129">Zawiera opis funkcji wielowątkowości w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ff7c4-129">Describes multithreading features in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="ff7c4-130">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="ff7c4-130">Threading</span></span>](https://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)  
 <span data-ttu-id="ff7c4-131">Zawiera opis funkcji wielowątkowości w języku C# i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ff7c4-131">Describes multithreading features in the C# and Visual Basic languages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff7c4-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff7c4-132">See Also</span></span>  
 [<span data-ttu-id="ff7c4-133">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ff7c4-133">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [<span data-ttu-id="ff7c4-134">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ff7c4-134">Events</span></span>](../../../docs/standard/events/index.md)  
 [<span data-ttu-id="ff7c4-135">Wielowątkowość składników</span><span class="sxs-lookup"><span data-stu-id="ff7c4-135">Multithreading in Components</span></span>](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [<span data-ttu-id="ff7c4-136">Asynchroniczne wzorce projektowe programowania</span><span class="sxs-lookup"><span data-stu-id="ff7c4-136">Asynchronous Programming Design Patterns</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
