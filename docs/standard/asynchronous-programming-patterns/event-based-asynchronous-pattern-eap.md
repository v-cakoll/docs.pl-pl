---
title: Asynchroniczny wzorzec oparty na zdarzeniach (EAP)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
caps.latest.revision: 20
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fecd71355d53f1e3937d3724569b10fa0c8e50da
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="ad0e5-102">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="ad0e5-102">Event-based Asynchronous Pattern (EAP)</span></span>
<span data-ttu-id="ad0e5-103">Istnieje wiele sposobów, aby udostępnić funkcje asynchroniczne do kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="ad0e5-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="ad0e5-104">Asynchroniczny wzorzec oparty na zdarzeniach Określa jedną z metod dla klas do prezentowania zachowanie asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="ad0e5-104">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad0e5-105">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], biblioteka zadań równoległych zapewnia nowy model programowania asynchronicznego i równolegle.</span><span class="sxs-lookup"><span data-stu-id="ad0e5-105">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="ad0e5-106">Aby uzyskać więcej informacji, zobacz [programowania równoległego](../../../docs/standard/parallel-programming/index.md).</span><span class="sxs-lookup"><span data-stu-id="ad0e5-106">For more information, see [Parallel Programming](../../../docs/standard/parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ad0e5-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ad0e5-107">In This Section</span></span>  
 [<span data-ttu-id="ad0e5-108">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="ad0e5-108">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="ad0e5-109">W tym artykule opisano, jak wzorca asynchronicznego opartego na zdarzeniach udostępnia zalety aplikacji wielowątkowych wiele złożonych problemów w wielowątkowe projektu są ukryte.</span><span class="sxs-lookup"><span data-stu-id="ad0e5-109">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="ad0e5-110">Implementowanie wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="ad0e5-110">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="ad0e5-111">Opisuje sposób Zestandaryzowany do pakietu klasy, która ma funkcje asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="ad0e5-111">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="ad0e5-112">Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ad0e5-112">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="ad0e5-113">Opisuje wymagania dotyczące udostępnianie funkcje asynchroniczne zgodnie ze wzorca asynchronicznego opartego na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="ad0e5-113">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="ad0e5-114">Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="ad0e5-114">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="ad0e5-115">Opisuje sposób określania, kiedy użytkownik powinien wybrać implementacji wzorca asynchronicznego opartego na zdarzeniach zamiast <xref:System.IAsyncResult> wzorca.</span><span class="sxs-lookup"><span data-stu-id="ad0e5-115">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern.</span></span>  
  
 [<span data-ttu-id="ad0e5-116">Przewodnik: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="ad0e5-116">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="ad0e5-117">Ilustruje sposób tworzenia składnika, który implementuje wzorzec asynchroniczny oparty na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="ad0e5-117">Illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="ad0e5-118">Jest stosowana przy użyciu klasy pomocy z <xref:System.ComponentModel?displayProperty=nameWithType> przestrzeni nazw, który zapewnia składnika działa prawidłowo w dowolnej aplikacji modelu.</span><span class="sxs-lookup"><span data-stu-id="ad0e5-118">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  
  
 [<span data-ttu-id="ad0e5-119">Instrukcje: Używanie składników obsługujących wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="ad0e5-119">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="ad0e5-120">Informacje dotyczące używania składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="ad0e5-120">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ad0e5-121">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="ad0e5-121">Reference</span></span>  
 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="ad0e5-122">W tym artykule opisano <xref:System.ComponentModel.AsyncOperation> klasy i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="ad0e5-122">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="ad0e5-123">W tym artykule opisano <xref:System.ComponentModel.AsyncOperationManager> klasy i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="ad0e5-123">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="ad0e5-124">W tym artykule opisano <xref:System.ComponentModel.BackgroundWorker> części oraz zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="ad0e5-124">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ad0e5-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ad0e5-125">Related Sections</span></span>  
 [<span data-ttu-id="ad0e5-126">Biblioteka zadań równoległych (TPL)</span><span class="sxs-lookup"><span data-stu-id="ad0e5-126">Task Parallel Library (TPL)</span></span>](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="ad0e5-127">W tym artykule opisano model programowania dla operacji asynchronicznych i równolegle.</span><span class="sxs-lookup"><span data-stu-id="ad0e5-127">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="ad0e5-128">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="ad0e5-128">Threading</span></span>](../../../docs/standard/threading/index.md)  
 <span data-ttu-id="ad0e5-129">Zawiera opis funkcji wielowątkowości w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ad0e5-129">Describes multithreading features in the .NET Framework.</span></span>  
  
 [<span data-ttu-id="ad0e5-130">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="ad0e5-130">Threading</span></span>](https://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)  
 <span data-ttu-id="ad0e5-131">Zawiera opis funkcji wielowątkowości w języku C# i Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ad0e5-131">Describes multithreading features in the C# and Visual Basic languages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad0e5-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad0e5-132">See Also</span></span>  
 [<span data-ttu-id="ad0e5-133">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ad0e5-133">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [<span data-ttu-id="ad0e5-134">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="ad0e5-134">Events</span></span>](../../../docs/standard/events/index.md)  
 [<span data-ttu-id="ad0e5-135">Wielowątkowość składników</span><span class="sxs-lookup"><span data-stu-id="ad0e5-135">Multithreading in Components</span></span>](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [<span data-ttu-id="ad0e5-136">Asynchroniczne wzorce projektowe programowania</span><span class="sxs-lookup"><span data-stu-id="ad0e5-136">Asynchronous Programming Design Patterns</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
