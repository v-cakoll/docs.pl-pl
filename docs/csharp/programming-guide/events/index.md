---
title: Zdarzenia — przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 183f53a579bdd9f70deb16ca9157c377fa3aff3f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75712315"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="99511-102">Zdarzenia (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="99511-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="99511-103">Zdarzenia umożliwiają [klasy](../../language-reference/keywords/class.md) lub obiektu, aby powiadomić inne klasy lub obiekty, gdy coś interesującego występuje.</span><span class="sxs-lookup"><span data-stu-id="99511-103">Events enable a [class](../../language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="99511-104">Klasa, która wysyła (lub *wywołuje)* zdarzenie jest wywoływana *wydawcy* i klas, które odbierają (lub *doobsługi)* zdarzenie są nazywane *subskrybentów*.</span><span class="sxs-lookup"><span data-stu-id="99511-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
<span data-ttu-id="99511-105">W typowej aplikacji C# Windows Forms lub Web użytkownik subskrybuje zdarzenia wywoływane przez formanty, takie jak przyciski i pola listy.</span><span class="sxs-lookup"><span data-stu-id="99511-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="99511-106">Można użyć visual c# zintegrowane środowisko programistyczne (IDE) do przeglądania zdarzeń, które formant publikuje i wybrać te, które mają obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="99511-106">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="99511-107">IDE zapewnia łatwy sposób automatycznego dodawania metody obsługi pustych zdarzeń i kodu do subskrybowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="99511-107">The IDE provides an easy way to automatically add an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="99511-108">Aby uzyskać więcej informacji, zobacz [Jak subskrybować wydarzenia i zniej subskrybować je.](./how-to-subscribe-to-and-unsubscribe-from-events.md)</span><span class="sxs-lookup"><span data-stu-id="99511-108">For more information, see [How to subscribe to and unsubscribe from events](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>
  
## <a name="events-overview"></a><span data-ttu-id="99511-109">Przegląd zdarzeń</span><span class="sxs-lookup"><span data-stu-id="99511-109">Events Overview</span></span>  
 <span data-ttu-id="99511-110">Zdarzenia mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="99511-110">Events have the following properties:</span></span>  
  
- <span data-ttu-id="99511-111">Wydawca określa, kiedy zdarzenie jest wywoływane; subskrybenci określają, jakie działania są podejmowane w odpowiedzi na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="99511-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
- <span data-ttu-id="99511-112">Zdarzenie może mieć wielu subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="99511-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="99511-113">Subskrybent może obsługiwać wiele zdarzeń od wielu wydawców.</span><span class="sxs-lookup"><span data-stu-id="99511-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
- <span data-ttu-id="99511-114">Zdarzenia, które nie mają subskrybentów nigdy nie są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="99511-114">Events that have no subscribers are never raised.</span></span>  
  
- <span data-ttu-id="99511-115">Zdarzenia są zwykle używane do sygnalizowania działań użytkownika, takich jak kliknięcia przycisków lub wybór menu w graficznych interfejsach użytkownika.</span><span class="sxs-lookup"><span data-stu-id="99511-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
- <span data-ttu-id="99511-116">Gdy zdarzenie ma wielu subskrybentów, programy obsługi zdarzeń są wywoływane synchronicznie, gdy zdarzenie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="99511-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="99511-117">Aby wywołać zdarzenia asynchronicznie, zobacz [Wywoływanie metod synchronicznych asynchronicznie](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="99511-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
- <span data-ttu-id="99511-118">W bibliotece klas .NET Framework zdarzenia <xref:System.EventHandler> są oparte <xref:System.EventArgs> na delegowaniu i klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="99511-118">In the .NET Framework class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="99511-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="99511-119">Related Sections</span></span>  
 <span data-ttu-id="99511-120">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="99511-120">For more information, see:</span></span>  
  
- [<span data-ttu-id="99511-121">Subskrybowanie i anulowanie subskrypcji zdarzeń</span><span class="sxs-lookup"><span data-stu-id="99511-121">How to subscribe to and unsubscribe from events</span></span>](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [<span data-ttu-id="99511-122">Publikowanie zdarzeń zgodnych ze wskazówkami dotyczącymi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="99511-122">How to publish events that conform to .NET Framework Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [<span data-ttu-id="99511-123">Wywoływanie zdarzeń klasy podstawowej w klasach pochodnych</span><span class="sxs-lookup"><span data-stu-id="99511-123">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)

- [<span data-ttu-id="99511-124">Implementowanie zdarzeń interfejsu</span><span class="sxs-lookup"><span data-stu-id="99511-124">How to implement interface events</span></span>](./how-to-implement-interface-events.md)

- [<span data-ttu-id="99511-125">Implementowanie niestandardowych metod dostępu zdarzeń</span><span class="sxs-lookup"><span data-stu-id="99511-125">How to implement custom event accessors</span></span>](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a><span data-ttu-id="99511-126">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="99511-126">C# Language Specification</span></span>  

<span data-ttu-id="99511-127">Aby uzyskać więcej informacji, zobacz [Zdarzenia](~/_csharplang/spec/classes.md#events) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="99511-127">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="99511-128">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="99511-128">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="99511-129">Polecane rozdziały książki</span><span class="sxs-lookup"><span data-stu-id="99511-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="99511-130">[Delegaci, zdarzenia i wyrażenia Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [książce kucharskiej C# 3.0, wydanie trzecie: ponad 250 rozwiązań dla programistów Języka C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="99511-130">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="99511-131">[Delegaci i wydarzenia](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) w [nauce C# 3.0: Opanuj podstawy języka C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="99511-131">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99511-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="99511-132">See also</span></span>

- <xref:System.EventHandler>
- [<span data-ttu-id="99511-133">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="99511-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="99511-134">Delegaty</span><span class="sxs-lookup"><span data-stu-id="99511-134">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="99511-135">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="99511-135">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
