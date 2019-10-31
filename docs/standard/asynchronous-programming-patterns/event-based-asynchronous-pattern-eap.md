---
title: Asynchroniczny wzorzec oparty na zdarzeniach (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: ee8c90d63478e444b7d25cb7cbb5c969963d7c63
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130942"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="d9d7b-102">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="d9d7b-102">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="d9d7b-103">Istnieje wiele sposobów udostępniania funkcji asynchronicznych kodowi klienta.</span><span class="sxs-lookup"><span data-stu-id="d9d7b-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="d9d7b-104">Wzorzec asynchroniczny oparty na zdarzeniach umożliwia jednokierunkową metodę prezentowania zachowań asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="d9d7b-104">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9d7b-105">Począwszy od .NET Framework 4, Biblioteka zadań równoległych udostępnia nowy model dla programowania asynchronicznego i równoległego.</span><span class="sxs-lookup"><span data-stu-id="d9d7b-105">Starting with the .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="d9d7b-106">Aby uzyskać więcej informacji, zobacz [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md) i [wzorzec asynchroniczny oparty na zadaniach (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="d9d7b-106">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="d9d7b-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="d9d7b-107">In This Section</span></span>

 [<span data-ttu-id="d9d7b-108">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="d9d7b-108">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="d9d7b-109">Opisuje sposób, w jaki wzorzec asynchroniczny oparty na zdarzeniach udostępnia zalety aplikacji wielowątkowych, jednocześnie ukrywając wiele złożonych problemów niezależnych od projektów wielowątkowych.</span><span class="sxs-lookup"><span data-stu-id="d9d7b-109">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="d9d7b-110">Implementowanie wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d9d7b-110">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="d9d7b-111">Opisuje ustandaryzowany sposób spakowania klasy, która ma funkcje asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="d9d7b-111">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="d9d7b-112">Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="d9d7b-112">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="d9d7b-113">Opisuje wymagania dotyczące uwidaczniania funkcji asynchronicznych zgodnie ze wzorcem asynchronicznym opartym na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="d9d7b-113">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="d9d7b-114">Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d9d7b-114">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="d9d7b-115">Opisuje, jak określić, kiedy należy wybrać implementację wzorca asynchronicznego opartego na zdarzeniach zamiast wzorca <xref:System.IAsyncResult> reprezentowanego przez [model programowania asynchronicznego (APM)](asynchronous-programming-model-apm.md)</span><span class="sxs-lookup"><span data-stu-id="d9d7b-115">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="d9d7b-116">Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d9d7b-116">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="d9d7b-117">Opisuje sposób tworzenia składnika implementującego wzorzec asynchroniczny oparty na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="d9d7b-117">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="d9d7b-118">Jest implementowana przy użyciu klas pomocnika z przestrzeni nazw <xref:System.ComponentModel?displayProperty=nameWithType>, co gwarantuje, że składnik działa prawidłowo w ramach dowolnego modelu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d9d7b-118">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="d9d7b-119">Instrukcje: Implementacja klienta wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d9d7b-119">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="d9d7b-120">Opisuje sposób tworzenia klienta korzystającego ze składnika implementującego wzorzec asynchroniczny oparty na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="d9d7b-120">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="d9d7b-121">Instrukcje: Używanie składników obsługujących wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="d9d7b-121">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="d9d7b-122">Opisuje sposób użycia składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="d9d7b-122">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d9d7b-123">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="d9d7b-123">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="d9d7b-124">Opisuje klasę <xref:System.ComponentModel.AsyncOperation> i zawiera linki do wszystkich jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="d9d7b-124">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="d9d7b-125">Opisuje klasę <xref:System.ComponentModel.AsyncOperationManager> i zawiera linki do wszystkich jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="d9d7b-125">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="d9d7b-126">Opisuje składnik <xref:System.ComponentModel.BackgroundWorker> i zawiera linki do wszystkich jego członków.</span><span class="sxs-lookup"><span data-stu-id="d9d7b-126">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d9d7b-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d9d7b-127">Related Sections</span></span>

 [<span data-ttu-id="d9d7b-128">Biblioteka zadań równoległych (TPL)</span><span class="sxs-lookup"><span data-stu-id="d9d7b-128">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="d9d7b-129">Opisuje model programowania dla operacji asynchronicznych i równoległych.</span><span class="sxs-lookup"><span data-stu-id="d9d7b-129">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="d9d7b-130">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="d9d7b-130">Threading</span></span>](../../../docs/standard/threading/index.md)  
 <span data-ttu-id="d9d7b-131">Opisuje funkcje wielowątkowości w programie .NET.</span><span class="sxs-lookup"><span data-stu-id="d9d7b-131">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9d7b-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9d7b-132">See also</span></span>

- [<span data-ttu-id="d9d7b-133">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="d9d7b-133">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)
- [<span data-ttu-id="d9d7b-134">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="d9d7b-134">Events</span></span>](../events/index.md)
- [<span data-ttu-id="d9d7b-135">Wzorce projektowania programowania asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="d9d7b-135">Asynchronous Programming Design Patterns</span></span>](index.md)
