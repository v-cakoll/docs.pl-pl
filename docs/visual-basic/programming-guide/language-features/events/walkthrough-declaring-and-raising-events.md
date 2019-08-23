---
title: Deklarowanie i wywoływanie zdarzeń (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 20e2b0efbf40597049c515134f408927f18d5603
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956335"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="a4006-102">Przewodnik: Deklarowanie i wywoływanie zdarzeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4006-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="a4006-103">W tym instruktażu pokazano, jak zadeklarować i zgłosić zdarzenia dla `Widget`klasy o nazwie.</span><span class="sxs-lookup"><span data-stu-id="a4006-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="a4006-104">Po wykonaniu kroków warto przeczytać temat pomocnika, [Przewodnik: Obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), które pokazują, jak używać zdarzeń z `Widget` obiektów w celu dostarczania informacji o stanie w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a4006-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="a4006-105">Klasa widget</span><span class="sxs-lookup"><span data-stu-id="a4006-105">The Widget Class</span></span>  
 <span data-ttu-id="a4006-106">Załóżmy dla momentu, gdy masz `Widget` klasę.</span><span class="sxs-lookup"><span data-stu-id="a4006-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="a4006-107">Twoja `Widget` Klasa ma metodę, która może zająć dużo czasu, i chcesz, aby aplikacja mogła umieścić jakiś wskaźnik uzupełniania.</span><span class="sxs-lookup"><span data-stu-id="a4006-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="a4006-108">Oczywiście można sprawić `Widget` , aby obiekt pokazywał okno dialogowe z wartością procentową, ale w każdym projekcie, w którym została `Widget` użyta Klasa, zostało zablokowane.</span><span class="sxs-lookup"><span data-stu-id="a4006-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="a4006-109">Dobrą zasadą projektowania obiektów jest umożliwienie aplikacji, która używa obiektu obsługującego interfejs użytkownika — chyba że cały cel obiektu ma zarządzać formularzem lub oknem dialogowym.</span><span class="sxs-lookup"><span data-stu-id="a4006-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="a4006-110">Celem `Widget` jest wykonywanie innych zadań, dlatego lepszym rozwiązaniem jest `PercentDone` dodanie zdarzenia i poinformowanie procedury, która wywołuje `Widget`metody obsługi tego zdarzenia i wyświetla aktualizacje stanu.</span><span class="sxs-lookup"><span data-stu-id="a4006-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="a4006-111">`PercentDone` Zdarzenie może również dostarczyć mechanizm anulowania zadania.</span><span class="sxs-lookup"><span data-stu-id="a4006-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="a4006-112">Aby skompilować przykład kodu dla tego tematu</span><span class="sxs-lookup"><span data-stu-id="a4006-112">To build the code example for this topic</span></span>  
  
1. <span data-ttu-id="a4006-113">Otwórz nowy projekt aplikacji Visual Basic systemu Windows i Utwórz formularz o nazwie `Form1`.</span><span class="sxs-lookup"><span data-stu-id="a4006-113">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2. <span data-ttu-id="a4006-114">Dodaj dwa przyciski i etykietę do `Form1`.</span><span class="sxs-lookup"><span data-stu-id="a4006-114">Add two buttons and a label to `Form1`.</span></span>  
  
3. <span data-ttu-id="a4006-115">Nazwij obiekty, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="a4006-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="a4006-116">Obiekt</span><span class="sxs-lookup"><span data-stu-id="a4006-116">Object</span></span>|<span data-ttu-id="a4006-117">Właściwość</span><span class="sxs-lookup"><span data-stu-id="a4006-117">Property</span></span>|<span data-ttu-id="a4006-118">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="a4006-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="a4006-119">Uruchom zadanie</span><span class="sxs-lookup"><span data-stu-id="a4006-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="a4006-120">Anuluj</span><span class="sxs-lookup"><span data-stu-id="a4006-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="a4006-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="a4006-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="a4006-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="a4006-122">lblPercentDone, 0</span></span>|  
  
4. <span data-ttu-id="a4006-123">W menu **projekt** wybierz polecenie **Dodaj klasę** , aby dodać klasę o nazwie `Widget.vb` do projektu.</span><span class="sxs-lookup"><span data-stu-id="a4006-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="a4006-124">Aby zadeklarować zdarzenie dla klasy widget</span><span class="sxs-lookup"><span data-stu-id="a4006-124">To declare an event for the Widget class</span></span>  
  
- <span data-ttu-id="a4006-125">Użyj słowa `Event` kluczowego, aby zadeklarować zdarzenie `Widget` w klasie.</span><span class="sxs-lookup"><span data-stu-id="a4006-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="a4006-126">Należy zauważyć, że zdarzenie może `ByVal` mieć `ByRef` i argumenty, `Widget`jako `PercentDone` zdarzenie:</span><span class="sxs-lookup"><span data-stu-id="a4006-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 <span data-ttu-id="a4006-127">Gdy wywołujący obiekt odbiera `PercentDone` zdarzenie `Percent` , argument zawiera procent wykonanego zadania.</span><span class="sxs-lookup"><span data-stu-id="a4006-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="a4006-128">Argument może być ustawiony na `True` , aby anulować metodę, która wywołała zdarzenie. `Cancel`</span><span class="sxs-lookup"><span data-stu-id="a4006-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4006-129">Argumenty zdarzeń można zadeklarować tak samo jak argumenty procedur, z następującymi wyjątkami: Zdarzenia nie mogą `Optional` mieć `ParamArray` argumentów lub, a zdarzenia nie mają zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="a4006-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="a4006-130">Zdarzenie jest wywoływane `LongTask` przez metodę `Widget` klasy. `PercentDone`</span><span class="sxs-lookup"><span data-stu-id="a4006-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="a4006-131">`LongTask`przyjmuje dwa argumenty: czas, który ma być wykonywany przez metodę, oraz minimalny interwał czasu przed `LongTask` zatrzymaniem `PercentDone` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a4006-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="a4006-132">Aby zgłosić zdarzenie PercentDone</span><span class="sxs-lookup"><span data-stu-id="a4006-132">To raise the PercentDone event</span></span>  
  
1. <span data-ttu-id="a4006-133">Aby uprościć dostęp do `Timer` właściwości używanej przez tę klasę, `Imports` Dodaj instrukcję do górnej części sekcji deklaracji w module `Class Widget` klasy, powyżej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a4006-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. <span data-ttu-id="a4006-134">Dodaj następujący kod do `Widget` klasy:</span><span class="sxs-lookup"><span data-stu-id="a4006-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 <span data-ttu-id="a4006-135">Gdy aplikacja wywołuje `LongTask` metodę `Widget` , Klasa zgłasza `PercentDone` zdarzenie co `MinimumInterval` kilka sekund.</span><span class="sxs-lookup"><span data-stu-id="a4006-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="a4006-136">Po powrocie zdarzenia program `LongTask` sprawdza, `Cancel` czy argument został ustawiony na `True`.</span><span class="sxs-lookup"><span data-stu-id="a4006-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="a4006-137">W tym miejscu należy wprowadzić kilka odrzutów.</span><span class="sxs-lookup"><span data-stu-id="a4006-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="a4006-138">Dla uproszczenia w `LongTask` procedurze założono, że wiesz, jak długo zadanie będzie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="a4006-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="a4006-139">To prawie nigdy nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="a4006-139">This is almost never the case.</span></span> <span data-ttu-id="a4006-140">Dzielenie zadań na fragmenty nawet rozmiaru może być trudne, a często najważniejsze znaczenie dla użytkowników to po prostu ilość czasu, która jest przekazywana przed uzyskaniem wskazującego, że coś się dzieje.</span><span class="sxs-lookup"><span data-stu-id="a4006-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="a4006-141">W tym przykładzie może zostać wykorzystana inna luka.</span><span class="sxs-lookup"><span data-stu-id="a4006-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="a4006-142">`Timer` Właściwość zwraca liczbę sekund, które upłynęły od północy; w związku z tym aplikacja zostaje zablokowana, jeśli zostanie uruchomiona tuż przed północy.</span><span class="sxs-lookup"><span data-stu-id="a4006-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="a4006-143">Bardziej staranne podejście do mierzenia czasu będzie miało wpływ na warunki graniczne, takie jak to, lub uniknąć ich całkowitego, przy `Now`użyciu właściwości, takich jak.</span><span class="sxs-lookup"><span data-stu-id="a4006-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="a4006-144">Teraz, gdy `Widget` Klasa może zgłaszać zdarzenia, możesz przejść do następnego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="a4006-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="a4006-145">[Przewodnik: Obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) pokazuje `WithEvents` ,`PercentDone` jak używać do kojarzenia procedury obsługi zdarzeń ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="a4006-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4006-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4006-146">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [<span data-ttu-id="a4006-147">Przewodnik: Obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a4006-147">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [<span data-ttu-id="a4006-148">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="a4006-148">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
