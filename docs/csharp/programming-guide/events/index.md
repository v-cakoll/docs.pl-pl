---
title: Zdarzenia — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 0373d9150349dc24653270600a317b0d41b945b1
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859642"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="d359f-102">Zdarzenia (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="d359f-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="d359f-103">Zdarzenie pozwala [klasy](../../../csharp/language-reference/keywords/class.md) lub obiektowi powiadomić inne klasy lub obiekty, gdy wystąpi stanie się coś istotnego.</span><span class="sxs-lookup"><span data-stu-id="d359f-103">Events enable a [class](../../../csharp/language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="d359f-104">Klasa, która wysyła (lub *zgłasza*) nosi nazwę zdarzenia *wydawcy* klas, które odbierają i (lub *obsługi*) zdarzenia są wywoływane *subskrybentów* .</span><span class="sxs-lookup"><span data-stu-id="d359f-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
 <span data-ttu-id="d359f-105">Typowa aplikacja C# Windows Forms lub sieci Web możesz subskrybować zdarzenia wygenerowane przez formanty, takie jak przyciski i pola listy.</span><span class="sxs-lookup"><span data-stu-id="d359f-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="d359f-106">Można użyć Visual C# zintegrowanego środowiska programistycznego (IDE), aby przeglądać zdarzenia, które kontrolki publikuje i wybrać te, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d359f-106">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="d359f-107">Środowisko IDE zapewnia prosty sposób, aby automatycznie dodać metodę programu obsługi zdarzeń pusty i kod, aby subskrybować zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="d359f-107">The IDE provides an easy way to automatically add an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="d359f-108">Aby uzyskać więcej informacji, zobacz [jak: Subskrybowanie i anulowanie subskrypcji zdarzeń](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="d359f-108">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>  
  
## <a name="events-overview"></a><span data-ttu-id="d359f-109">Przegląd zdarzeń</span><span class="sxs-lookup"><span data-stu-id="d359f-109">Events Overview</span></span>  
 <span data-ttu-id="d359f-110">Zdarzenia mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="d359f-110">Events have the following properties:</span></span>  
  
- <span data-ttu-id="d359f-111">Określa wydawcy, gdy wydarzenie jest podniesione; Subskrybenci określają, jakie działania są podejmowane w odpowiedzi na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="d359f-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
- <span data-ttu-id="d359f-112">Zdarzenie może mieć wielu subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="d359f-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="d359f-113">Subskrybent może obsłużyć wielu zdarzeń z wielu wydawców.</span><span class="sxs-lookup"><span data-stu-id="d359f-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
- <span data-ttu-id="d359f-114">Zdarzenia, które mają żadnych subskrybentów nigdy nie są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="d359f-114">Events that have no subscribers are never raised.</span></span>  
  
- <span data-ttu-id="d359f-115">Zdarzenia są zazwyczaj używane w celu sygnalizowania, że akcje użytkownika, takich jak kliknięcia przycisku lub menu opcji w graficznym interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d359f-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
- <span data-ttu-id="d359f-116">Gdy zdarzenie jest wielu subskrybentów, programy obsługi zdarzeń są wywoływane synchronicznie, gdy wydarzenie jest podniesione.</span><span class="sxs-lookup"><span data-stu-id="d359f-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="d359f-117">Aby wywołać zdarzenia asynchronicznie, zobacz [wywołanie asynchroniczne synchroniczne metody](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="d359f-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
- <span data-ttu-id="d359f-118">W bibliotece klas programu .NET Framework, zdarzenia są oparte na <xref:System.EventHandler> delegować i <xref:System.EventArgs> klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="d359f-118">In the .NET Framework class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d359f-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d359f-119">Related Sections</span></span>  
 <span data-ttu-id="d359f-120">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="d359f-120">For more information, see:</span></span>  
  
- [<span data-ttu-id="d359f-121">Instrukcje: Subskrybowanie i anulowanie subskrypcji zdarzeń</span><span class="sxs-lookup"><span data-stu-id="d359f-121">How to: Subscribe to and Unsubscribe from Events</span></span>](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
- [<span data-ttu-id="d359f-122">Instrukcje: Publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d359f-122">How to: Publish Events that Conform to .NET Framework Guidelines</span></span>](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
- [<span data-ttu-id="d359f-123">Instrukcje: Wywoływanie zdarzeń klasy podstawowej w klasach pochodnych</span><span class="sxs-lookup"><span data-stu-id="d359f-123">How to: Raise Base Class Events in Derived Classes</span></span>](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
- [<span data-ttu-id="d359f-124">Instrukcje:  Zdarzenia implementowania interfejsu</span><span class="sxs-lookup"><span data-stu-id="d359f-124">How to:  Implement Interface Events</span></span>](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
- [<span data-ttu-id="d359f-125">Instrukcje: Implementowanie niestandardowych metod dostępu zdarzeń</span><span class="sxs-lookup"><span data-stu-id="d359f-125">How to: Implement Custom Event Accessors</span></span>](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="d359f-126">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d359f-126">C# Language Specification</span></span>  

<span data-ttu-id="d359f-127">Aby uzyskać więcej informacji, zobacz [zdarzenia](~/_csharplang/spec/classes.md#events) w [ C# specyfikacji języka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d359f-127">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="d359f-128">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="d359f-128">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="d359f-129">Polecane rozdziały książki</span><span class="sxs-lookup"><span data-stu-id="d359f-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="d359f-130">[Delegatów, zdarzeń i wyrażenia Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [ C# 3.0 Cookbook, Third Edition: Ponad 250 rozwiązań dla C# ekspertów w programowaniu w wersji 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="d359f-130">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="d359f-131">[Delegaci i zdarzenia](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) w [uczenia C# 3.0: Opanowanie podstaw C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="d359f-131">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d359f-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d359f-132">See also</span></span>

- <xref:System.EventHandler>
- [<span data-ttu-id="d359f-133">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d359f-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d359f-134">Delegaty</span><span class="sxs-lookup"><span data-stu-id="d359f-134">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
- [<span data-ttu-id="d359f-135">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d359f-135">Creating Event Handlers in Windows Forms</span></span>](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
