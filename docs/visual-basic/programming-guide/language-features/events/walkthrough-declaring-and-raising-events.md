---
title: Deklarowanie i wywoływanie zdarzeń
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], events
- events [Visual Basic], walkthroughs
- declaring events [Visual Basic], walkthroughs
- events [Visual Basic], declaring
- events [Visual Basic], raising
- raising events [Visual Basic], walkthroughs
ms.assetid: 8ffb3be8-097d-4d3c-b71e-04555ebda2a2
ms.openlocfilehash: 6f4c303604f9cf55b4ecd500636e0d2772b6234c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345088"
---
# <a name="walkthrough-declaring-and-raising-events-visual-basic"></a><span data-ttu-id="1602a-102">Wskazówki: deklarowanie i wywoływanie zdarzeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1602a-102">Walkthrough: Declaring and Raising Events (Visual Basic)</span></span>
<span data-ttu-id="1602a-103">W tym instruktażu pokazano, jak zadeklarować i zgłosić zdarzenia dla klasy o nazwie `Widget`.</span><span class="sxs-lookup"><span data-stu-id="1602a-103">This walkthrough demonstrates how to declare and raise events for a class named `Widget`.</span></span> <span data-ttu-id="1602a-104">Po wykonaniu kroków warto przeczytać temat pomocnika, [Przewodnik: obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), który pokazuje, jak używać zdarzeń z `Widget` obiektów w celu zapewnienia informacji o stanie w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1602a-104">After you complete the steps, you might want to read the companion topic, [Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md), which shows how to use events from `Widget` objects to provide status information in an application.</span></span>  
  
## <a name="the-widget-class"></a><span data-ttu-id="1602a-105">Klasa widget</span><span class="sxs-lookup"><span data-stu-id="1602a-105">The Widget Class</span></span>  
 <span data-ttu-id="1602a-106">Załóżmy, że masz już klasę `Widget`.</span><span class="sxs-lookup"><span data-stu-id="1602a-106">Assume for the moment that you have a `Widget` class.</span></span> <span data-ttu-id="1602a-107">Twoja Klasa `Widget` ma metodę, która może zająć dużo czasu, i chcesz, aby aplikacja mogła umieścić jakiś rodzaj wskaźnika uzupełniania.</span><span class="sxs-lookup"><span data-stu-id="1602a-107">Your `Widget` class has a method that can take a long time to execute, and you want your application to be able to put up some kind of completion indicator.</span></span>  
  
 <span data-ttu-id="1602a-108">Oczywiście można sprawić, aby obiekt `Widget` pokazywał okno dialogowe z wartością procentową, ale w każdym projekcie, w którym użyto klasy `Widget`, zostało zablokowane.</span><span class="sxs-lookup"><span data-stu-id="1602a-108">Of course, you could make the `Widget` object show a percent-complete dialog box, but then you would be stuck with that dialog box in every project in which you used the `Widget` class.</span></span> <span data-ttu-id="1602a-109">Dobrą zasadą projektowania obiektów jest umożliwienie aplikacji, która używa obiektu obsługującego interfejs użytkownika — chyba że cały cel obiektu ma zarządzać formularzem lub oknem dialogowym.</span><span class="sxs-lookup"><span data-stu-id="1602a-109">A good principle of object design is to let the application that uses an object handle the user interface—unless the whole purpose of the object is to manage a form or dialog box.</span></span>  
  
 <span data-ttu-id="1602a-110">Celem `Widget` jest wykonywanie innych zadań, dlatego lepiej jest dodać zdarzenie `PercentDone` i pozwolić procedurze wywołującej metody `Widget`obsłużyć to zdarzenie i wyświetlić aktualizacje stanu.</span><span class="sxs-lookup"><span data-stu-id="1602a-110">The purpose of `Widget` is to perform other tasks, so it is better to add a `PercentDone` event and let the procedure that calls `Widget`'s methods handle that event and display status updates.</span></span> <span data-ttu-id="1602a-111">Zdarzenie `PercentDone` może również dostarczyć mechanizm anulowania zadania.</span><span class="sxs-lookup"><span data-stu-id="1602a-111">The `PercentDone` event can also provide a mechanism for canceling the task.</span></span>  
  
#### <a name="to-build-the-code-example-for-this-topic"></a><span data-ttu-id="1602a-112">Aby skompilować przykład kodu dla tego tematu</span><span class="sxs-lookup"><span data-stu-id="1602a-112">To build the code example for this topic</span></span>  
  
1. <span data-ttu-id="1602a-113">Otwórz nowy projekt aplikacji Visual Basic systemu Windows i Utwórz formularz o nazwie `Form1`.</span><span class="sxs-lookup"><span data-stu-id="1602a-113">Open a new Visual Basic Windows Application project and create a form named `Form1`.</span></span>  
  
2. <span data-ttu-id="1602a-114">Dodaj dwa przyciski i etykietę do `Form1`.</span><span class="sxs-lookup"><span data-stu-id="1602a-114">Add two buttons and a label to `Form1`.</span></span>  
  
3. <span data-ttu-id="1602a-115">Nazwij obiekty, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="1602a-115">Name the objects as shown in the following table.</span></span>  
  
    |<span data-ttu-id="1602a-116">Obiekt</span><span class="sxs-lookup"><span data-stu-id="1602a-116">Object</span></span>|<span data-ttu-id="1602a-117">Właściwość</span><span class="sxs-lookup"><span data-stu-id="1602a-117">Property</span></span>|<span data-ttu-id="1602a-118">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="1602a-118">Setting</span></span>|  
    |------------|--------------|-------------|  
    |`Button1`|`Text`|<span data-ttu-id="1602a-119">Uruchom zadanie</span><span class="sxs-lookup"><span data-stu-id="1602a-119">Start Task</span></span>|  
    |`Button2`|`Text`|<span data-ttu-id="1602a-120">Cancel</span><span class="sxs-lookup"><span data-stu-id="1602a-120">Cancel</span></span>|  
    |`Label`|<span data-ttu-id="1602a-121">`(Name)`, `Text`</span><span class="sxs-lookup"><span data-stu-id="1602a-121">`(Name)`, `Text`</span></span>|<span data-ttu-id="1602a-122">lblPercentDone, 0</span><span class="sxs-lookup"><span data-stu-id="1602a-122">lblPercentDone, 0</span></span>|  
  
4. <span data-ttu-id="1602a-123">W menu **projekt** wybierz polecenie **Dodaj klasę** , aby dodać klasę o nazwie `Widget.vb` do projektu.</span><span class="sxs-lookup"><span data-stu-id="1602a-123">On the **Project** menu, choose **Add Class** to add a class named `Widget.vb` to the project.</span></span>  
  
#### <a name="to-declare-an-event-for-the-widget-class"></a><span data-ttu-id="1602a-124">Aby zadeklarować zdarzenie dla klasy widget</span><span class="sxs-lookup"><span data-stu-id="1602a-124">To declare an event for the Widget class</span></span>  
  
- <span data-ttu-id="1602a-125">Użyj słowa kluczowego `Event`, aby zadeklarować zdarzenie w klasie `Widget`.</span><span class="sxs-lookup"><span data-stu-id="1602a-125">Use the `Event` keyword to declare an event in the `Widget` class.</span></span> <span data-ttu-id="1602a-126">Należy zauważyć, że zdarzenie może mieć `ByVal` i `ByRef` argumentów, ponieważ `PercentDone` zdarzenia `Widget`ilustruje:</span><span class="sxs-lookup"><span data-stu-id="1602a-126">Note that an event can have `ByVal` and `ByRef` arguments, as `Widget`'s `PercentDone` event demonstrates:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#1)]  
  
 <span data-ttu-id="1602a-127">Gdy wywołujący obiekt odbiera zdarzenie `PercentDone`, argument `Percent` zawiera wartość procentową wykonanego zadania.</span><span class="sxs-lookup"><span data-stu-id="1602a-127">When the calling object receives a `PercentDone` event, the `Percent` argument contains the percentage of the task that is complete.</span></span> <span data-ttu-id="1602a-128">Argument `Cancel` można ustawić na `True`, aby anulować metodę, która wywołała zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="1602a-128">The `Cancel` argument can be set to `True` to cancel the method that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1602a-129">Argumenty zdarzeń można zadeklarować tak samo jak argumenty procedur, z następującymi wyjątkami: zdarzenia nie mogą mieć `Optional` lub `ParamArray` argumentów, a zdarzenia nie mają zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="1602a-129">You can declare event arguments just as you do arguments of procedures, with the following exceptions: Events cannot have `Optional` or `ParamArray` arguments, and events do not have return values.</span></span>  
  
 <span data-ttu-id="1602a-130">Zdarzenie `PercentDone` jest zgłaszane przez metodę `LongTask` klasy `Widget`.</span><span class="sxs-lookup"><span data-stu-id="1602a-130">The `PercentDone` event is raised by the `LongTask` method of the `Widget` class.</span></span> <span data-ttu-id="1602a-131">`LongTask` przyjmuje dwa argumenty: czas, który ma być wykonywany przez metodę, oraz minimalny interwał czasu przed za`LongTask` wstrzymywaniem w celu podniesienia `PercentDone` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1602a-131">`LongTask` takes two arguments: the length of time the method pretends to be doing work, and the minimum time interval before `LongTask` pauses to raise the `PercentDone` event.</span></span>  
  
#### <a name="to-raise-the-percentdone-event"></a><span data-ttu-id="1602a-132">Aby zgłosić zdarzenie PercentDone</span><span class="sxs-lookup"><span data-stu-id="1602a-132">To raise the PercentDone event</span></span>  
  
1. <span data-ttu-id="1602a-133">Aby uprościć dostęp do właściwości `Timer` używanej przez tę klasę, Dodaj instrukcję `Imports` do górnej części sekcji deklaracji w module klasy, powyżej instrukcji `Class Widget`.</span><span class="sxs-lookup"><span data-stu-id="1602a-133">To simplify access to the `Timer` property used by this class, add an `Imports` statement to the top of the declarations section of your class module, above the `Class Widget` statement.</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#2)]  
  
2. <span data-ttu-id="1602a-134">Dodaj następujący kod do klasy `Widget`:</span><span class="sxs-lookup"><span data-stu-id="1602a-134">Add the following code to the `Widget` class:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Widget.vb#3)]  
  
 <span data-ttu-id="1602a-135">Gdy aplikacja wywołuje metodę `LongTask`, Klasa `Widget` zgłasza zdarzenie `PercentDone` co `MinimumInterval` sekund.</span><span class="sxs-lookup"><span data-stu-id="1602a-135">When your application calls the `LongTask` method, the `Widget` class raises the `PercentDone` event every `MinimumInterval` seconds.</span></span> <span data-ttu-id="1602a-136">Po powrocie zdarzenia `LongTask` sprawdza, czy argument `Cancel` został ustawiony na `True`.</span><span class="sxs-lookup"><span data-stu-id="1602a-136">When the event returns, `LongTask` checks to see if the `Cancel` argument was set to `True`.</span></span>  
  
 <span data-ttu-id="1602a-137">W tym miejscu należy wprowadzić kilka odrzutów.</span><span class="sxs-lookup"><span data-stu-id="1602a-137">A few disclaimers are necessary here.</span></span> <span data-ttu-id="1602a-138">Dla uproszczenia w procedurze `LongTask` założono, że wiesz, jak długo zadanie będzie wykonywane.</span><span class="sxs-lookup"><span data-stu-id="1602a-138">For simplicity, the `LongTask` procedure assumes you know in advance how long the task will take.</span></span> <span data-ttu-id="1602a-139">To prawie nigdy nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="1602a-139">This is almost never the case.</span></span> <span data-ttu-id="1602a-140">Dzielenie zadań na fragmenty nawet rozmiaru może być trudne, a często najważniejsze znaczenie dla użytkowników to po prostu ilość czasu, która jest przekazywana przed uzyskaniem wskazującego, że coś się dzieje.</span><span class="sxs-lookup"><span data-stu-id="1602a-140">Dividing tasks into chunks of even size can be difficult, and often what matters most to users is simply the amount of time that passes before they get an indication that something is happening.</span></span>  
  
 <span data-ttu-id="1602a-141">W tym przykładzie może zostać wykorzystana inna luka.</span><span class="sxs-lookup"><span data-stu-id="1602a-141">You may have spotted another flaw in this sample.</span></span> <span data-ttu-id="1602a-142">Właściwość `Timer` zwraca liczbę sekund, które upłynęły od północy; w związku z tym aplikacja zostanie zablokowana, jeśli zostanie uruchomiona tuż przed północy.</span><span class="sxs-lookup"><span data-stu-id="1602a-142">The `Timer` property returns the number of seconds that have passed since midnight; therefore, the application gets stuck if it is started just before midnight.</span></span> <span data-ttu-id="1602a-143">Bardziej staranne podejście do mierzenia czasu będzie miało wpływ na warunki graniczne, takie jak to, lub uniknąć ich całkowitego, przy użyciu właściwości, takich jak `Now`.</span><span class="sxs-lookup"><span data-stu-id="1602a-143">A more careful approach to measuring time would take boundary conditions such as this into consideration, or avoid them altogether, using properties such as `Now`.</span></span>  
  
 <span data-ttu-id="1602a-144">Teraz, gdy Klasa `Widget` może zgłaszać zdarzenia, możesz przejść do następnego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="1602a-144">Now that the `Widget` class can raise events, you can move to the next walkthrough.</span></span> <span data-ttu-id="1602a-145">Wskazówki [: obsługa zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) pokazuje, jak za pomocą `WithEvents` skojarzyć procedurę obsługi zdarzeń ze zdarzeniem `PercentDone`.</span><span class="sxs-lookup"><span data-stu-id="1602a-145">[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md) demonstrates how to use `WithEvents` to associate an event handler with the `PercentDone` event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1602a-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1602a-146">See also</span></span>

- <xref:Microsoft.VisualBasic.DateAndTime.Timer%2A>
- <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>
- [<span data-ttu-id="1602a-147">Przewodnik: obsługa zdarzeń</span><span class="sxs-lookup"><span data-stu-id="1602a-147">Walkthrough: Handling Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)
- [<span data-ttu-id="1602a-148">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1602a-148">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
