---
title: Zdarzenia — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
ms.openlocfilehash: 183f53a579bdd9f70deb16ca9157c377fa3aff3f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712315"
---
# <a name="events-c-programming-guide"></a><span data-ttu-id="5a77a-102">Zdarzenia (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="5a77a-102">Events (C# Programming Guide)</span></span>
<span data-ttu-id="5a77a-103">Zdarzenia umożliwiają [klasie](../../language-reference/keywords/class.md) lub obiektowi powiadamianie innych klas lub obiektów w przypadku wystąpienia czegoś zainteresowania.</span><span class="sxs-lookup"><span data-stu-id="5a77a-103">Events enable a [class](../../language-reference/keywords/class.md) or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="5a77a-104">Klasa, która wysyła (lub *podnosi*) zdarzenie, jest nazywana *wydawcą* i klasy, które odbierają (lub *obsługują*) zdarzenie są nazywane *subskrybentami*.</span><span class="sxs-lookup"><span data-stu-id="5a77a-104">The class that sends (or *raises*) the event is called the *publisher* and the classes that receive (or *handle*) the event are called *subscribers*.</span></span>  
  
<span data-ttu-id="5a77a-105">W typowej C# Windows Forms lub aplikacji sieci Web subskrybujesz zdarzenia wywoływane przez kontrolki, takie jak przyciski i pola listy.</span><span class="sxs-lookup"><span data-stu-id="5a77a-105">In a typical C# Windows Forms or Web application, you subscribe to events raised by controls such as buttons and list boxes.</span></span> <span data-ttu-id="5a77a-106">Przy użyciu C# zintegrowanego środowiska programistycznego (IDE) można przeglądać zdarzenia publikowane przez formant i wybierać te, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="5a77a-106">You can use the Visual C# integrated development environment (IDE) to browse the events that a control publishes and select the ones that you want to handle.</span></span> <span data-ttu-id="5a77a-107">Środowisko IDE zapewnia łatwy sposób automatycznego dodawania pustej metody obsługi zdarzeń i kodu w celu subskrybowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5a77a-107">The IDE provides an easy way to automatically add an empty event handler method and the code to subscribe to the event.</span></span> <span data-ttu-id="5a77a-108">Aby uzyskać więcej informacji, zobacz [subskrybowanie i anulowanie subskrypcji zdarzeń](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="5a77a-108">For more information, see [How to subscribe to and unsubscribe from events](./how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>
  
## <a name="events-overview"></a><span data-ttu-id="5a77a-109">Przegląd zdarzeń</span><span class="sxs-lookup"><span data-stu-id="5a77a-109">Events Overview</span></span>  
 <span data-ttu-id="5a77a-110">Zdarzenia mają następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="5a77a-110">Events have the following properties:</span></span>  
  
- <span data-ttu-id="5a77a-111">Wydawca określa, kiedy zdarzenie jest zgłaszane; Subskrybenci określają, jakie działania są podejmowane w odpowiedzi na zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="5a77a-111">The publisher determines when an event is raised; the subscribers determine what action is taken in response to the event.</span></span>  
  
- <span data-ttu-id="5a77a-112">Wydarzenie może mieć wielu subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="5a77a-112">An event can have multiple subscribers.</span></span> <span data-ttu-id="5a77a-113">Subskrybenci mogą obsługiwać wiele zdarzeń z wielu wydawców.</span><span class="sxs-lookup"><span data-stu-id="5a77a-113">A subscriber can handle multiple events from multiple publishers.</span></span>  
  
- <span data-ttu-id="5a77a-114">Zdarzenia, które nie mają subskrybentów nigdy nie są zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="5a77a-114">Events that have no subscribers are never raised.</span></span>  
  
- <span data-ttu-id="5a77a-115">Zdarzenia są zwykle używane do sygnalizowania akcji użytkownika, takich jak kliknięcia przycisków lub menu w graficznym interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5a77a-115">Events are typically used to signal user actions such as button clicks or menu selections in graphical user interfaces.</span></span>  
  
- <span data-ttu-id="5a77a-116">Gdy zdarzenie ma wielu subskrybentów, programy obsługi zdarzeń są wywoływane synchronicznie, gdy zdarzenie jest zgłaszane.</span><span class="sxs-lookup"><span data-stu-id="5a77a-116">When an event has multiple subscribers, the event handlers are invoked synchronously when an event is raised.</span></span> <span data-ttu-id="5a77a-117">Aby wywoływać zdarzenia asynchronicznie, zobacz [wywoływanie metod synchronicznych asynchronicznie](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="5a77a-117">To invoke events asynchronously, see [Calling Synchronous Methods Asynchronously](../../../standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).</span></span>  
  
- <span data-ttu-id="5a77a-118">W bibliotece klas .NET Framework zdarzenia są oparte na delegatze <xref:System.EventHandler> i <xref:System.EventArgs> klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="5a77a-118">In the .NET Framework class library, events are based on the <xref:System.EventHandler> delegate and the <xref:System.EventArgs> base class.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5a77a-119">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="5a77a-119">Related Sections</span></span>  
 <span data-ttu-id="5a77a-120">Aby uzyskać więcej informacji, zobacz:</span><span class="sxs-lookup"><span data-stu-id="5a77a-120">For more information, see:</span></span>  
  
- [<span data-ttu-id="5a77a-121">Subskrybowanie i anulowanie subskrypcji zdarzeń</span><span class="sxs-lookup"><span data-stu-id="5a77a-121">How to subscribe to and unsubscribe from events</span></span>](./how-to-subscribe-to-and-unsubscribe-from-events.md)

- [<span data-ttu-id="5a77a-122">Jak opublikować zdarzenia zgodne z wytycznymi .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5a77a-122">How to publish events that conform to .NET Framework Guidelines</span></span>](./how-to-publish-events-that-conform-to-net-framework-guidelines.md)

- [<span data-ttu-id="5a77a-123">Jak wywoływać zdarzenia klasy podstawowej w klasach pochodnych</span><span class="sxs-lookup"><span data-stu-id="5a77a-123">How to raise base class events in derived classes</span></span>](./how-to-raise-base-class-events-in-derived-classes.md)

- [<span data-ttu-id="5a77a-124">Jak zaimplementować zdarzenia interfejsu</span><span class="sxs-lookup"><span data-stu-id="5a77a-124">How to implement interface events</span></span>](./how-to-implement-interface-events.md)

- [<span data-ttu-id="5a77a-125">Jak zaimplementować niestandardowe metody dostępu do zdarzeń</span><span class="sxs-lookup"><span data-stu-id="5a77a-125">How to implement custom event accessors</span></span>](./how-to-implement-custom-event-accessors.md)

## <a name="c-language-specification"></a><span data-ttu-id="5a77a-126">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5a77a-126">C# Language Specification</span></span>  

<span data-ttu-id="5a77a-127">Aby uzyskać więcej informacji, zobacz [zdarzenia](~/_csharplang/spec/classes.md#events) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="5a77a-127">For more information, see [Events](~/_csharplang/spec/classes.md#events) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="5a77a-128">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="5a77a-128">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="featured-book-chapters"></a><span data-ttu-id="5a77a-129">Polecane rozdziały książki</span><span class="sxs-lookup"><span data-stu-id="5a77a-129">Featured Book Chapters</span></span>  
 <span data-ttu-id="5a77a-130">[Delegaty, zdarzenia i wyrażenia lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [ C# 3,0 Cookbook, wydanie trzecie: więcej niż 250 rozwiązań dla C# 3,0 programistów](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="5a77a-130">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
 <span data-ttu-id="5a77a-131">[Delegaty i zdarzenia](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) w [uczeniu C# 3,0: główne podstawy C# 3,0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="5a77a-131">[Delegates and Events](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652490%28v=orm.10%29) in [Learning C# 3.0: Master the fundamentals of C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652493%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a77a-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5a77a-132">See also</span></span>

- <xref:System.EventHandler>
- [<span data-ttu-id="5a77a-133">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5a77a-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5a77a-134">Delegaci</span><span class="sxs-lookup"><span data-stu-id="5a77a-134">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="5a77a-135">Tworzenie procedur obsługi zdarzeń w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5a77a-135">Creating Event Handlers in Windows Forms</span></span>](../../../framework/winforms/creating-event-handlers-in-windows-forms.md)
