---
title: "Obsługa zdarzeń (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e4e31937d67d2140865a9626f79fbddc16796709
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-handling-events-visual-basic"></a><span data-ttu-id="844c2-102">Wskazówki: obsługa zdarzeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="844c2-102">Walkthrough: Handling Events (Visual Basic)</span></span>
<span data-ttu-id="844c2-103">Jest to drugi dwa tematy, które przedstawiają sposób pracy ze zdarzeniami.</span><span class="sxs-lookup"><span data-stu-id="844c2-103">This is the second of two topics that demonstrate how to work with events.</span></span> <span data-ttu-id="844c2-104">Pierwszym temacie [wskazówki: deklarujący i wywoływanie zdarzeń](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), pokazuje, jak deklarowanie i wywoływanie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="844c2-104">The first topic, [Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md), shows how to declare and raise events.</span></span> <span data-ttu-id="844c2-105">Ta sekcja używa formularza i klasy z tego przewodnika pokazanie sposobu obsługi zdarzenia, gdy ich została wykonana.</span><span class="sxs-lookup"><span data-stu-id="844c2-105">This section uses the form and class from that walkthrough to show how to handle events when they take place.</span></span>  
  
 <span data-ttu-id="844c2-106">`Widget` Klasy przykładzie użyto tradycyjnych instrukcje obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="844c2-106">The `Widget` class example uses traditional event-handling statements.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="844c2-107">Praca ze zdarzeniami zapewnia innych technik.</span><span class="sxs-lookup"><span data-stu-id="844c2-107"> provides other techniques for working with events.</span></span> <span data-ttu-id="844c2-108">Jako wykonywania można modyfikować w tym przykładzie, aby użyć `AddHandler` i `Handles` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="844c2-108">As an exercise, you can modify this example to use the `AddHandler` and `Handles` statements.</span></span>  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a><span data-ttu-id="844c2-109">Obsługa zdarzenia PercentDone klasy widżetu</span><span class="sxs-lookup"><span data-stu-id="844c2-109">To handle the PercentDone event of the Widget class</span></span>  
  
1.  <span data-ttu-id="844c2-110">Umieść następujący kod w `Form1`:</span><span class="sxs-lookup"><span data-stu-id="844c2-110">Place the following code in `Form1`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_1.vb)]  
  
     <span data-ttu-id="844c2-111">`WithEvents` — Słowo kluczowe Określa, że zmienna `mWidget` służy do obsługi zdarzeń obiektu.</span><span class="sxs-lookup"><span data-stu-id="844c2-111">The `WithEvents` keyword specifies that the variable `mWidget` is used to handle an object's events.</span></span> <span data-ttu-id="844c2-112">Należy określić rodzaj obiektu, podając nazwę klasy, z którego będzie można utworzyć obiektu.</span><span class="sxs-lookup"><span data-stu-id="844c2-112">You specify the kind of object by supplying the name of the class from which the object will be created.</span></span>  
  
     <span data-ttu-id="844c2-113">Zmienna `mWidget` jest zadeklarowana w `Form1` ponieważ `WithEvents` zmienne musi być na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="844c2-113">The variable `mWidget` is declared in `Form1` because `WithEvents` variables must be class-level.</span></span> <span data-ttu-id="844c2-114">Dotyczy to bez względu na typ klasy, która zostanie umieszczony w.</span><span class="sxs-lookup"><span data-stu-id="844c2-114">This is true regardless of the type of class you place them in.</span></span>  
  
     <span data-ttu-id="844c2-115">Zmienna `mblnCancel` jest używany do anulowania `LongTask` metody.</span><span class="sxs-lookup"><span data-stu-id="844c2-115">The variable `mblnCancel` is used to cancel the `LongTask` method.</span></span>  
  
## <a name="writing-code-to-handle-an-event"></a><span data-ttu-id="844c2-116">Pisanie kodu do obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="844c2-116">Writing Code to Handle an Event</span></span>  
 <span data-ttu-id="844c2-117">Jak można zadeklarować zmiennej przy użyciu `WithEvents`, nazwa zmiennej jest wyświetlana na liście rozwijanej po lewej stronie klasy **edytora kodu**.</span><span class="sxs-lookup"><span data-stu-id="844c2-117">As soon as you declare a variable using `WithEvents`, the variable name appears in the left drop-down list of the class's **Code Editor**.</span></span> <span data-ttu-id="844c2-118">Po wybraniu `mWidget`, `Widget` klasy zdarzenia są wyświetlane na liście po prawej listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="844c2-118">When you select `mWidget`, the `Widget` class's events appear in the right drop-down list.</span></span> <span data-ttu-id="844c2-119">Wybranie zdarzenia zawiera procedury odpowiednie zdarzenia z prefiksem `mWidget` i podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="844c2-119">Selecting an event displays the corresponding event procedure, with the prefix `mWidget` and an underscore.</span></span> <span data-ttu-id="844c2-120">Procedur zdarzeń związanych z `WithEvents` zmiennej podano nazwę zmiennej jako prefiksu.</span><span class="sxs-lookup"><span data-stu-id="844c2-120">All the event procedures associated with a `WithEvents` variable are given the variable name as a prefix.</span></span>  
  
#### <a name="to-handle-an-event"></a><span data-ttu-id="844c2-121">Do obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="844c2-121">To handle an event</span></span>  
  
1.  <span data-ttu-id="844c2-122">Wybierz `mWidget` z listy rozwijanej po lewej stronie **edytora kodu**.</span><span class="sxs-lookup"><span data-stu-id="844c2-122">Select `mWidget` from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="844c2-123">Wybierz `PercentDone` zdarzenie na liście po prawej listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="844c2-123">Select the `PercentDone` event from the right drop-down list.</span></span> <span data-ttu-id="844c2-124">**Edytora kodu** otwiera `mWidget_PercentDone` procedury zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="844c2-124">The **Code Editor** opens the `mWidget_PercentDone` event procedure.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="844c2-125">**Edytora kodu** jest przydatne, ale nie jest to wymagane, wstawiania nowych programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="844c2-125">The **Code Editor** is useful, but not required, for inserting new event handlers.</span></span> <span data-ttu-id="844c2-126">W tym przewodniku jest bardziej bezpośrednio po prostu skopiuj obsługi zdarzeń bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="844c2-126">In this walkthrough, it is more direct to just copy the event handlers directly into your code.</span></span>  
  
3.  <span data-ttu-id="844c2-127">Dodaj następujący kod do `mWidget_PercentDone` obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="844c2-127">Add the following code to the `mWidget_PercentDone` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_2.vb)]  
  
     <span data-ttu-id="844c2-128">Zawsze, gdy `PercentDone` zdarzenie jest zgłaszane, procedura zdarzenia wyświetlane wykonano w `Label` formantu.</span><span class="sxs-lookup"><span data-stu-id="844c2-128">Whenever the `PercentDone` event is raised, the event procedure displays the percent complete in a `Label` control.</span></span> <span data-ttu-id="844c2-129">`DoEvents` Metoda pozwala etykiety do odświeżenia, a także daje użytkownikowi możliwość kliknij **anulować** przycisk.</span><span class="sxs-lookup"><span data-stu-id="844c2-129">The `DoEvents` method allows the label to repaint, and also gives the user the opportunity to click the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="844c2-130">Dodaj następujący kod do `Button2_Click` obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="844c2-130">Add the following code for the `Button2_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_3.vb)]  
  
 <span data-ttu-id="844c2-131">Gdy użytkownik kliknie **anulować** przycisk podczas `LongTask` jest uruchomiona, `Button2_Click` zdarzeń jest wykonywane tak szybko, jak `DoEvents` instrukcji umożliwia przetwarzanie zdarzenia występują.</span><span class="sxs-lookup"><span data-stu-id="844c2-131">If the user clicks the **Cancel** button while `LongTask` is running, the `Button2_Click` event is executed as soon as the `DoEvents` statement allows event processing to occur.</span></span> <span data-ttu-id="844c2-132">Zmienna poziomie klasy `mblnCancel` ustawiono `True`i `mWidget_PercentDone` zdarzeń następnie sprawdza ją i ustawia `ByRef Cancel` argument `True`.</span><span class="sxs-lookup"><span data-stu-id="844c2-132">The class-level variable `mblnCancel` is set to `True`, and the `mWidget_PercentDone` event then tests it and sets the `ByRef Cancel` argument to `True`.</span></span>  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a><span data-ttu-id="844c2-133">Łączenie do obiektu zmiennej WithEvents</span><span class="sxs-lookup"><span data-stu-id="844c2-133">Connecting a WithEvents Variable to an Object</span></span>  
 <span data-ttu-id="844c2-134">`Form1`jest teraz skonfigurowane do obsługi `Widget` zdarzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="844c2-134">`Form1` is now set up to handle a `Widget` object's events.</span></span> <span data-ttu-id="844c2-135">Wszystkie opcje, które pozostaje jest znalezienie `Widget` innym.</span><span class="sxs-lookup"><span data-stu-id="844c2-135">All that remains is to find a `Widget` somewhere.</span></span>  
  
 <span data-ttu-id="844c2-136">Gdy zadeklarować zmiennej `WithEvents` w czasie projektowania, żaden obiekt jest skojarzony z nim.</span><span class="sxs-lookup"><span data-stu-id="844c2-136">When you declare a variable `WithEvents` at design time, no object is associated with it.</span></span> <span data-ttu-id="844c2-137">A `WithEvents` zmienna jest podobnie jak inne zmienna obiektu.</span><span class="sxs-lookup"><span data-stu-id="844c2-137">A `WithEvents` variable is just like any other object variable.</span></span> <span data-ttu-id="844c2-138">Należy utworzyć obiekt i przypisać odwołanie do niej z `WithEvents` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="844c2-138">You have to create an object and assign a reference to it with the `WithEvents` variable.</span></span>  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a><span data-ttu-id="844c2-139">Aby utworzyć obiekt i przypisać odwołanie do niej</span><span class="sxs-lookup"><span data-stu-id="844c2-139">To create an object and assign a reference to it</span></span>  
  
1.  <span data-ttu-id="844c2-140">Wybierz **(Form1 zdarzeń)** z listy rozwijanej po lewej stronie **edytora kodu**.</span><span class="sxs-lookup"><span data-stu-id="844c2-140">Select **(Form1 Events)** from the left drop-down list in the **Code Editor**.</span></span>  
  
2.  <span data-ttu-id="844c2-141">Wybierz `Load` zdarzenie na liście po prawej listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="844c2-141">Select the `Load` event from the right drop-down list.</span></span> <span data-ttu-id="844c2-142">**Edytora kodu** otwiera `Form1_Load` procedury zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="844c2-142">The **Code Editor** opens the `Form1_Load` event procedure.</span></span>  
  
3.  <span data-ttu-id="844c2-143">Dodaj następujący kod do `Form1_Load` procedury zdarzenia można utworzyć `Widget`:</span><span class="sxs-lookup"><span data-stu-id="844c2-143">Add the following code for the `Form1_Load` event procedure to create the `Widget`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_4.vb)]  
  
 <span data-ttu-id="844c2-144">Podczas tego kodu, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tworzy `Widget` obiektu i jego zdarzeń nawiązanie połączenia procedur zdarzeń związanych z `mWidget`.</span><span class="sxs-lookup"><span data-stu-id="844c2-144">When this code executes, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] creates a `Widget` object and connects its events to the event procedures associated with `mWidget`.</span></span> <span data-ttu-id="844c2-145">Od tego punktu, gdy `Widget` zgłasza jego `PercentDone` zdarzenia `mWidget_PercentDone` zdarzeń procedura jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="844c2-145">From that point on, whenever the `Widget` raises its `PercentDone` event, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
#### <a name="to-call-the-longtask-method"></a><span data-ttu-id="844c2-146">Aby wywołać metodę LongTask</span><span class="sxs-lookup"><span data-stu-id="844c2-146">To call the LongTask method</span></span>  
  
-   <span data-ttu-id="844c2-147">Dodaj następujący kod do `Button1_Click` obsługi zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="844c2-147">Add the following code to the `Button1_Click` event handler:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_5.vb)]  
  
 <span data-ttu-id="844c2-148">Przed `LongTask` metoda jest wywoływana etykiety wyświetla procentu ukończenia musi zostać zainicjowany i poziomie klasy `Boolean` Flaga anulowanie metoda musi mieć ustawioną `False`.</span><span class="sxs-lookup"><span data-stu-id="844c2-148">Before the `LongTask` method is called, the label that displays the percent complete must be initialized, and the class-level `Boolean` flag for canceling the method must be set to `False`.</span></span>  
  
 <span data-ttu-id="844c2-149">`LongTask`jest wywoływana z czas trwania zadania 12.2 sekund.</span><span class="sxs-lookup"><span data-stu-id="844c2-149">`LongTask` is called with a task duration of 12.2 seconds.</span></span> <span data-ttu-id="844c2-150">`PercentDone` Zdarzenie jest wywoływane po każdym jedna trzecia sekundy.</span><span class="sxs-lookup"><span data-stu-id="844c2-150">The `PercentDone` event is raised once every one-third of a second.</span></span> <span data-ttu-id="844c2-151">Zawsze zdarzenie jest zgłaszane, `mWidget_PercentDone` zdarzeń procedura jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="844c2-151">Each time the event is raised, the `mWidget_PercentDone` event procedure is executed.</span></span>  
  
 <span data-ttu-id="844c2-152">Podczas `LongTask` jest wykonywana, `mblnCancel` jest testowany, aby sprawdzić, czy `LongTask` zakończone normalnie, lub jeśli zatrzymana, ponieważ `mblnCancel` ustawiono `True`.</span><span class="sxs-lookup"><span data-stu-id="844c2-152">When `LongTask` is done, `mblnCancel` is tested to see if `LongTask` ended normally, or if it stopped because `mblnCancel` was set to `True`.</span></span> <span data-ttu-id="844c2-153">Procent wykonania jest aktualizowany tylko w pierwszym przypadku.</span><span class="sxs-lookup"><span data-stu-id="844c2-153">The percent complete is updated only in the former case.</span></span>  
  
#### <a name="to-run-the-program"></a><span data-ttu-id="844c2-154">Aby uruchomić program</span><span class="sxs-lookup"><span data-stu-id="844c2-154">To run the program</span></span>  
  
1.  <span data-ttu-id="844c2-155">Naciśnij klawisz F5, aby umieścić projektu w trybie uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="844c2-155">Press F5 to put the project in run mode.</span></span>  
  
2.  <span data-ttu-id="844c2-156">Kliknij przycisk **Rozpocznij zadanie** przycisku.</span><span class="sxs-lookup"><span data-stu-id="844c2-156">Click the **Start Task** button.</span></span> <span data-ttu-id="844c2-157">Zawsze `PercentDone` zdarzenie jest zgłaszane, etykiety został zaktualizowany o procent wykonania zadania.</span><span class="sxs-lookup"><span data-stu-id="844c2-157">Each time the `PercentDone` event is raised, the label is updated with the percentage of the task that is complete.</span></span>  
  
3.  <span data-ttu-id="844c2-158">Kliknij przycisk **anulować** przycisk, aby zatrzymać zadanie.</span><span class="sxs-lookup"><span data-stu-id="844c2-158">Click the **Cancel** button to stop the task.</span></span> <span data-ttu-id="844c2-159">Zwróć uwagę, że wygląd **anulować** natychmiast po kliknięciu przycisku nie ulega zmianie.</span><span class="sxs-lookup"><span data-stu-id="844c2-159">Notice that the appearance of the **Cancel** button does not change immediately when you click it.</span></span> <span data-ttu-id="844c2-160">`Click` Zdarzeń nie może mieć miejsce, do `My.Application.DoEvents` instrukcji umożliwia przetwarzanie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="844c2-160">The `Click` event cannot happen until the `My.Application.DoEvents` statement allows event processing.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="844c2-161">`My.Application.DoEvents` — Metoda nie przetwarza zdarzenia w taki sam sposób jak w formularzu.</span><span class="sxs-lookup"><span data-stu-id="844c2-161">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="844c2-162">Na przykład, w tym przewodniku muszą kliknij **anulować** dwa razy przycisk.</span><span class="sxs-lookup"><span data-stu-id="844c2-162">For example, in this walkthrough, you must click the **Cancel** button twice.</span></span> <span data-ttu-id="844c2-163">Aby zezwolić na formularzu, aby obsługiwać zdarzenia bezpośrednio, można użyć wielowątkowości.</span><span class="sxs-lookup"><span data-stu-id="844c2-163">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="844c2-164">Aby uzyskać więcej informacji, zobacz [wątki](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span><span class="sxs-lookup"><span data-stu-id="844c2-164">For more information, see [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
 <span data-ttu-id="844c2-165">Może być istotne, aby uruchomić program z F11 i krokowo kodu wiersza w czasie.</span><span class="sxs-lookup"><span data-stu-id="844c2-165">You may find it instructive to run the program with F11 and step through the code a line at a time.</span></span> <span data-ttu-id="844c2-166">Wyraźnie widać, jak wykonanie wprowadza `LongTask`i następnie krótko ponownie wprowadzenia `Form1` zawsze `PercentDone` zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="844c2-166">You can clearly see how execution enters `LongTask`, and then briefly re-enters `Form1` each time the `PercentDone` event is raised.</span></span>  
  
 <span data-ttu-id="844c2-167">Co się stanie, jeśli podczas wykonywania ponownie kod `Form1`, `LongTask` metody wywołane ponownie?</span><span class="sxs-lookup"><span data-stu-id="844c2-167">What would happen if, while execution was back in the code of `Form1`, the `LongTask` method were called again?</span></span> <span data-ttu-id="844c2-168">W najgorszym przepełnienie stosu może wystąpić, jeśli `LongTask` były nazywane za każdym razem, gdy wywołano zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="844c2-168">At worst, a stack overflow might occur if `LongTask` were called every time the event was raised.</span></span>  
  
 <span data-ttu-id="844c2-169">Zmienna może spowodować `mWidget` do obsługi zdarzeń dla innej `Widget` obiektu przypisując odwołanie do nowego `Widget` do `mWidget`.</span><span class="sxs-lookup"><span data-stu-id="844c2-169">You can cause the variable `mWidget` to handle events for a different `Widget` object by assigning a reference to the new `Widget` to `mWidget`.</span></span> <span data-ttu-id="844c2-170">W rzeczywistości wprowadzisz kod w `Button1_Click` to zrobić, za każdym razem, kliknij przycisk.</span><span class="sxs-lookup"><span data-stu-id="844c2-170">In fact, you can make the code in `Button1_Click` do this every time you click the button.</span></span>  
  
#### <a name="to-handle-events-for-a-different-widget"></a><span data-ttu-id="844c2-171">Do obsługi zdarzeń dla różnych widżetu</span><span class="sxs-lookup"><span data-stu-id="844c2-171">To handle events for a different widget</span></span>  
  
-   <span data-ttu-id="844c2-172">Dodaj następujący wiersz kodu w celu `Button1_Click` procedura bezpośrednio po wierszu `mWidget.LongTask(12.2, 0.33)`:</span><span class="sxs-lookup"><span data-stu-id="844c2-172">Add the following line of code to the `Button1_Click` procedure, immediately preceding the line that reads `mWidget.LongTask(12.2, 0.33)`:</span></span>  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](../../../../visual-basic/programming-guide/language-features/events/codesnippet/VisualBasic/walkthrough-handling-events_6.vb)]  
  
 <span data-ttu-id="844c2-173">Powyższy kod tworzy nową `Widget` każdym kliknięciu przycisku.</span><span class="sxs-lookup"><span data-stu-id="844c2-173">The code above creates a new `Widget` each time the button is clicked.</span></span> <span data-ttu-id="844c2-174">Jak najszybciej `LongTask` metody zakończeniu odwołanie do `Widget` wydaniu i `Widget` zostanie zniszczony.</span><span class="sxs-lookup"><span data-stu-id="844c2-174">As soon as the `LongTask` method completes, the reference to the `Widget` is released, and the `Widget` is destroyed.</span></span>  
  
 <span data-ttu-id="844c2-175">A `WithEvents` zmienna może zawierać tylko jeden obiekt odniesienia w czasie, tak więc jeśli możesz przypisać inną `Widget` do obiektu `mWidget`, poprzedniej `Widget` zdarzeń obiektu będzie już obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="844c2-175">A `WithEvents` variable can contain only one object reference at a time, so if you assign a different `Widget` object to `mWidget`, the previous `Widget` object's events will no longer be handled.</span></span> <span data-ttu-id="844c2-176">Jeśli `mWidget` jest tylko zmienna obiektu zawierające odwołania do starego `Widget`, obiekt zostanie zniszczony.</span><span class="sxs-lookup"><span data-stu-id="844c2-176">If `mWidget` is the only object variable containing a reference to the old `Widget`, the object is destroyed.</span></span> <span data-ttu-id="844c2-177">Jeśli chcesz obsługiwać zdarzenia z kilku `Widget` obiektów, użyj `AddHandler` instrukcji przetwarzania zdarzeń z każdego obiektu osobno.</span><span class="sxs-lookup"><span data-stu-id="844c2-177">If you want to handle events from several `Widget` objects, use the `AddHandler` statement to process events from each object separately.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="844c2-178">Można zadeklarować tyle `WithEvents` muszą zmienne jako użytkownik, ale tablice `WithEvents` zmienne nie są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="844c2-178">You can declare as many `WithEvents` variables as you need, but arrays of `WithEvents` variables are not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="844c2-179">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="844c2-179">See Also</span></span>  
 [<span data-ttu-id="844c2-180">Wskazówki: Deklarowanie i wywoływanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="844c2-180">Walkthrough: Declaring and Raising Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)  
 [<span data-ttu-id="844c2-181">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="844c2-181">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
