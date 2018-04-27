---
title: Zdarzenia (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
caps.latest.revision: 43
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4ac62a38698f0e43c2868e86fa8776e913b715d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="934aa-102">Zdarzenia (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="934aa-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="934aa-103">Włącz zdarzenia [klasy](../../../csharp/language-reference/keywords/class.md) lub obiekt, aby powiadomić innych klas lub obiekty coś odsetek sytuacji.</span><span class="sxs-lookup"><span data-stu-id="934aa-103">Events enable a [class](../../../csharp/language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="934aa-104">Klasa, która wysyła (lub *zgłasza*) zdarzenie jest wywoływane *wydawcy* klasy, które odbierają i (lub *obsługi*) zdarzenia są nazywane *subskrybentów* .</span><span class="sxs-lookup"><span data-stu-id="934aa-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
 <span data-ttu-id="934aa-105">Typowa aplikacja formularzy systemu Windows w języku C# lub sieci Web należy subskrybować zdarzenia generowane przez formanty, takie jak przycisków i pola listy.</span><span class="sxs-lookup"><span data-stu-id="934aa-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="934aa-106">Visual C# zintegrowane środowisko programistyczne (IDE) umożliwia przeglądanie zdarzeń, które publikuje formantu i wybrać te, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="934aa-106">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="934aa-107">IDE automatycznie dodaje metoda obsługi zdarzeń pusty i kod, aby subskrybować zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="934aa-107">The IDE automatically adds an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="934aa-108">Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="934aa-108">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="events-overview"></a><span data-ttu-id="934aa-109">Przegląd zdarzeń</span><span class="sxs-lookup"><span data-stu-id="934aa-109">Events Overview</span></span>  
 <span data-ttu-id="934aa-110">Zdarzenia mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="934aa-110">Events have the following properties:</span></span>  
  
-   <span data-ttu-id="934aa-111">Określa wydawcy, gdy zdarzenie jest wywoływane; subskrybentów określają, jakie działanie jest wykonywane w odpowiedzi na zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="934aa-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
-   <span data-ttu-id="934aa-112">Zdarzenie może mieć wielu subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="934aa-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="934aa-113">Subskrybent może obsługiwać wiele zdarzeń z wielu wydawcy.</span><span class="sxs-lookup"><span data-stu-id="934aa-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
-   <span data-ttu-id="934aa-114">Zdarzenia, które mają subskrybentów. nigdy nie są zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="934aa-114">Events that have no subscribers are never raised.</span></span>  
  
-   <span data-ttu-id="934aa-115">Zdarzenia są zwykle używane w celu zasygnalizowania akcje użytkownika, takie jak kliknięcia przycisków lub menu opcji w graficznym interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="934aa-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
-   <span data-ttu-id="934aa-116">Zdarzenia po wielu subskrybentów obsługi zdarzeń są wywoływane synchronicznie, gdy zdarzenie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="934aa-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="934aa-117">Aby wywołać zdarzenia asynchronicznie, zobacz [wywołanie asynchroniczne synchroniczne metody](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="934aa-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
-   <span data-ttu-id="934aa-118">W [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] biblioteki klas, zdarzenia są oparte na <xref:System.EventHandler> delegować i <xref:System.EventArgs> klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="934aa-118">In the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="934aa-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="934aa-119">Related Sections</span></span>  
 <span data-ttu-id="934aa-120">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="934aa-120">For more information, see:</span></span>  
  
-   [<span data-ttu-id="934aa-121">Instrukcje: subskrybowanie i anulowanie subskrypcji zdarzeń</span><span class="sxs-lookup"><span data-stu-id="934aa-121">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [<span data-ttu-id="934aa-122">Instrukcje: publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi platformy .NET Framework</span><span class="sxs-lookup"><span data-stu-id="934aa-122">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [<span data-ttu-id="934aa-123">Instrukcje: wywoływanie zdarzeń klasy podstawowej w klasach pochodnych</span><span class="sxs-lookup"><span data-stu-id="934aa-123">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [<span data-ttu-id="934aa-124">Porady: zdarzenia implementowania interfejsu</span><span class="sxs-lookup"><span data-stu-id="934aa-124">How to:  Implement Interface Events</span></span>](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [<span data-ttu-id="934aa-125">Synchronizacja wątku</span><span class="sxs-lookup"><span data-stu-id="934aa-125">Thread Synchronization</span></span>](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [<span data-ttu-id="934aa-126">Instrukcje: użycie słownika do przechowywania wystąpień zdarzeń</span><span class="sxs-lookup"><span data-stu-id="934aa-126">How to: Use a Dictionary to Store Event Instances</span></span>](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [<span data-ttu-id="934aa-127">Instrukcje: implementowanie niestandardowych metod dostępu zdarzeń</span><span class="sxs-lookup"><span data-stu-id="934aa-127">How to: Implement Custom Event Accessors</span></span>](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="934aa-128">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="934aa-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a><span data-ttu-id="934aa-129">Polecane rozdziały książki</span><span class="sxs-lookup"><span data-stu-id="934aa-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="934aa-130">[Obiekty delegowane, zdarzeń i wyrażenia Lambda](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) w [C# 3.0 Cookbook, trzecia edycja: ponad 250 rozwiązań dla programistów języka C# 3.0](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span><span class="sxs-lookup"><span data-stu-id="934aa-130">[Delegates, Events, and Lambda Expressions](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx)</span></span>  
  
 <span data-ttu-id="934aa-131">[Delegaci i zdarzenia](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) w [Learning C# 3.0: wzorca podstawy języka C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span><span class="sxs-lookup"><span data-stu-id="934aa-131">[Delegates and Events](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934aa-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="934aa-132">See Also</span></span>  
 <xref:System.EventHandler>  
 [<span data-ttu-id="934aa-133">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="934aa-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="934aa-134">Delegaci</span><span class="sxs-lookup"><span data-stu-id="934aa-134">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="934aa-135">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="934aa-135">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="934aa-136">Programowanie wielowątkowości za pomocą wzorca asynchronicznego opartego na zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="934aa-136">Multithreaded Programming with the Event-based Asynchronous Pattern</span></span>](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
