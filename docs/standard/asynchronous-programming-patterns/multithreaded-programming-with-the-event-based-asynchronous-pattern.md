---
title: Programowanie wielowątkowości za pomocą wzorca asynchronicznego opartego na zdarzeniach
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 958d6617-5e70-4b36-b5db-63c16dc35e43
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6d93e449877456e415ebd4d3490a7df99280e7e5
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2018
---
# <a name="multithreaded-programming-with-the-event-based-asynchronous-pattern"></a><span data-ttu-id="338c2-102">Programowanie wielowątkowości za pomocą wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="338c2-102">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="338c2-103">Istnieje wiele sposobów, aby udostępnić funkcje asynchroniczne do kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="338c2-103">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="338c2-104">Asynchroniczny wzorzec oparty na zdarzeniach określa zalecany sposób klasy do prezentowania zachowanie asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="338c2-104">The Event-based Asynchronous Pattern prescribes the recommended way for classes to present asynchronous behavior.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="338c2-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="338c2-105">In This Section</span></span>  
 [<span data-ttu-id="338c2-106">Asynchroniczny wzorzec oparty na zdarzeniach — omówienie</span><span class="sxs-lookup"><span data-stu-id="338c2-106">Event-based Asynchronous Pattern Overview</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="338c2-107">W tym artykule opisano, jak wzorca asynchronicznego opartego na zdarzeniach udostępnia zalety aplikacji wielowątkowych wiele złożonych problemów w wielowątkowe projektu są ukryte.</span><span class="sxs-lookup"><span data-stu-id="338c2-107">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="338c2-108">Implementowanie wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="338c2-108">Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="338c2-109">Opisuje sposób Zestandaryzowany do pakietu klasy, która ma funkcje asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="338c2-109">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="338c2-110">Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="338c2-110">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="338c2-111">Opisuje wymagania dotyczące udostępnianie funkcje asynchroniczne zgodnie ze wzorca asynchronicznego opartego na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="338c2-111">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="338c2-112">Decydowanie o czasie implementacji wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="338c2-112">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="338c2-113">Opisuje sposób określania, kiedy użytkownik powinien wybrać implementacji wzorca asynchronicznego opartego na zdarzeniach zamiast <xref:System.IAsyncResult> wzorca.</span><span class="sxs-lookup"><span data-stu-id="338c2-113">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern.</span></span>  
  
 [<span data-ttu-id="338c2-114">Przewodnik: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="338c2-114">Walkthrough: Implementing a Component That Supports the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="338c2-115">Ilustruje sposób tworzenia składnika, który implementuje wzorzec asynchroniczny oparty na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="338c2-115">Illustrates how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="338c2-116">Jest stosowana przy użyciu klasy pomocy z <xref:System.ComponentModel?displayProperty=nameWithType> przestrzeni nazw, który zapewnia składnika działa prawidłowo w dowolnej aplikacji modelu.</span><span class="sxs-lookup"><span data-stu-id="338c2-116">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  
  
 [<span data-ttu-id="338c2-117">Instrukcje: Używanie składników obsługujących wzorzec asynchroniczny oparty na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="338c2-117">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="338c2-118">Informacje dotyczące używania składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="338c2-118">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="338c2-119">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="338c2-119">Reference</span></span>  
 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="338c2-120">W tym artykule opisano <xref:System.ComponentModel.AsyncOperation> klasy i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="338c2-120">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="338c2-121">W tym artykule opisano <xref:System.ComponentModel.AsyncOperationManager> klasy i zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="338c2-121">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="338c2-122">W tym artykule opisano <xref:System.ComponentModel.BackgroundWorker> części oraz zawiera łącza do wszystkich jej członków.</span><span class="sxs-lookup"><span data-stu-id="338c2-122">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="338c2-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="338c2-123">See Also</span></span>  
 [<span data-ttu-id="338c2-124">Zarządzana wątkowość — najlepsze rozwiązania</span><span class="sxs-lookup"><span data-stu-id="338c2-124">Managed Threading Best Practices</span></span>](../../../docs/standard/threading/managed-threading-best-practices.md)  
 [<span data-ttu-id="338c2-125">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="338c2-125">Events</span></span>](../../../docs/standard/events/index.md)  
 [<span data-ttu-id="338c2-126">Wielowątkowość składników</span><span class="sxs-lookup"><span data-stu-id="338c2-126">Multithreading in Components</span></span>](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [<span data-ttu-id="338c2-127">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="338c2-127">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
