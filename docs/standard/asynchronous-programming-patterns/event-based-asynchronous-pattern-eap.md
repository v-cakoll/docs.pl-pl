---
title: Asynchroniczny wzorzec oparty na zdarzeniach (EAP)
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7811113244d8c5f7d79a55ebb01f04e99e9bd2a6
ms.sourcegitcommit: e8dc507cfdaad504fc9d4c83d28d24569dcef91c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/03/2018
ms.locfileid: "33567809"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="6fb7d-102">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="6fb7d-102">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="6fb7d-103">Istnieją różne sposoby do udostępnienia asynchronicznego cech dla kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="6fb7d-104">Asynchroniczny wzorzec oparty na zdarzeniach określa jeden ze sposobów dla klas przedstawić zachowanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-104">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6fb7d-105">Począwszy od programu .NET Framework 4 w bibliotece zadań równoległych przewiduje nowy model programowania asynchronicznego i równoległego.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-105">Starting with the .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="6fb7d-106">Aby uzyskać więcej informacji, zobacz [Biblioteka zadań równoległych (TPL)](../parallel-programming/task-parallel-library-tpl.md) i [opartego na zadaniach asynchronicznej wzorca (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="6fb7d-106">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="6fb7d-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6fb7d-107">In This Section</span></span>

 [<span data-ttu-id="6fb7d-108">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="6fb7d-108">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="6fb7d-109">W tym artykule opisano, jak asynchroniczny wzorzec oparty na zdarzeniach udostępnia zalety aplikacji wielowątkowych wiele skomplikowane problemy związane z wielowątkowych projektu są ukryte.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-109">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="6fb7d-110">Implementowanie wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="6fb7d-110">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="6fb7d-111">W tym artykule opisano standardowy sposób pakietu klasę, która ma funkcje asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-111">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="6fb7d-112">Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="6fb7d-112">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="6fb7d-113">W tym artykule opisano wymagania dotyczące udostępniania funkcje asynchroniczne zgodnie z wzorca asynchronicznego opartego na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-113">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="6fb7d-114">Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="6fb7d-114">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="6fb7d-115">Opisuje sposób określenia, kiedy należy wybrać implementacji wzorca asynchronicznego opartego na zdarzeniach — zamiast <xref:System.IAsyncResult> wzorzec reprezentowany przez [modelu programowania asynchronicznego (APM)](asynchronous-programming-model-apm.md)</span><span class="sxs-lookup"><span data-stu-id="6fb7d-115">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="6fb7d-116">Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="6fb7d-116">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="6fb7d-117">W tym artykule opisano sposób tworzenia składnika, który implementuje wzorzec asynchroniczny oparty na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-117">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="6fb7d-118">Jej implementacji przy użyciu klas pomocy z <xref:System.ComponentModel?displayProperty=nameWithType> przestrzeń nazw, która zapewnia składnika działa prawidłowo w ramach dowolnego modelu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-118">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="6fb7d-119">Instrukcje: Implementacja klienta wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="6fb7d-119">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="6fb7d-120">W tym artykule opisano sposób tworzenia klienta, który używa składnika, który implementuje wzorzec asynchroniczny oparty na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-120">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="6fb7d-121">Instrukcje: Używanie składników obsługujących wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="6fb7d-121">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="6fb7d-122">Opisuje sposób używania składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-122">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6fb7d-123">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="6fb7d-123">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="6fb7d-124">W tym artykule opisano <xref:System.ComponentModel.AsyncOperation> klasy i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-124">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="6fb7d-125">W tym artykule opisano <xref:System.ComponentModel.AsyncOperationManager> klasy i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-125">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="6fb7d-126">W tym artykule opisano <xref:System.ComponentModel.BackgroundWorker> składnika i zawiera linki do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-126">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6fb7d-127">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="6fb7d-127">Related Sections</span></span>

 [<span data-ttu-id="6fb7d-128">Biblioteka zadań równoległych (TPL)</span><span class="sxs-lookup"><span data-stu-id="6fb7d-128">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="6fb7d-129">W tym artykule opisano model programowania dla operacji asynchronicznych i równoległych.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-129">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="6fb7d-130">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="6fb7d-130">Threading</span></span>](../../../docs/standard/threading/index.md)  
 <span data-ttu-id="6fb7d-131">Opisuje funkcje wielowątkowości w środowisku .NET.</span><span class="sxs-lookup"><span data-stu-id="6fb7d-131">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fb7d-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fb7d-132">See also</span></span>

 [<span data-ttu-id="6fb7d-133">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="6fb7d-133">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)  
 [<span data-ttu-id="6fb7d-134">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="6fb7d-134">Events</span></span>](../events/index.md)  
 [<span data-ttu-id="6fb7d-135">Wzorce projektowania programowania asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="6fb7d-135">Asynchronous Programming Design Patterns</span></span>](index.md)
