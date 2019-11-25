---
title: RaiseEvent — Instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
ms.openlocfilehash: e04f2bbaf57789f0bdaa07c1ebd68b22e3ae6178
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333059"
---
# <a name="raiseevent-statement"></a><span data-ttu-id="53285-102">RaiseEvent — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="53285-102">RaiseEvent Statement</span></span>
<span data-ttu-id="53285-103">Triggers an event declared at module level within a class, form, or document.</span><span class="sxs-lookup"><span data-stu-id="53285-103">Triggers an event declared at module level within a class, form, or document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53285-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53285-104">Syntax</span></span>  
  
```vb  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a><span data-ttu-id="53285-105">Części</span><span class="sxs-lookup"><span data-stu-id="53285-105">Parts</span></span>  
 `eventname`  
 <span data-ttu-id="53285-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="53285-106">Required.</span></span> <span data-ttu-id="53285-107">Name of the event to trigger.</span><span class="sxs-lookup"><span data-stu-id="53285-107">Name of the event to trigger.</span></span>  
  
 `argumentlist`  
 <span data-ttu-id="53285-108">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="53285-108">Optional.</span></span> <span data-ttu-id="53285-109">Comma-delimited list of variables, arrays, or expressions.</span><span class="sxs-lookup"><span data-stu-id="53285-109">Comma-delimited list of variables, arrays, or expressions.</span></span> <span data-ttu-id="53285-110">The `argumentlist` argument must be enclosed by parentheses.</span><span class="sxs-lookup"><span data-stu-id="53285-110">The `argumentlist` argument must be enclosed by parentheses.</span></span> <span data-ttu-id="53285-111">If there are no arguments, the parentheses must be omitted.</span><span class="sxs-lookup"><span data-stu-id="53285-111">If there are no arguments, the parentheses must be omitted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53285-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53285-112">Remarks</span></span>  
 <span data-ttu-id="53285-113">The required `eventname` is the name of an event declared within the module.</span><span class="sxs-lookup"><span data-stu-id="53285-113">The required `eventname` is the name of an event declared within the module.</span></span> <span data-ttu-id="53285-114">It follows Visual Basic variable naming conventions.</span><span class="sxs-lookup"><span data-stu-id="53285-114">It follows Visual Basic variable naming conventions.</span></span>  
  
 <span data-ttu-id="53285-115">If the event has not been declared within the module in which it is raised, an error occurs.</span><span class="sxs-lookup"><span data-stu-id="53285-115">If the event has not been declared within the module in which it is raised, an error occurs.</span></span> <span data-ttu-id="53285-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span><span class="sxs-lookup"><span data-stu-id="53285-116">The following code fragment illustrates an event declaration and a procedure in which the event is raised.</span></span>  
  
 [!code-vb[VbVbalrEvents#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#37)]  
  
 <span data-ttu-id="53285-117">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span><span class="sxs-lookup"><span data-stu-id="53285-117">You cannot use `RaiseEvent` to raise events that are not explicitly declared in the module.</span></span> <span data-ttu-id="53285-118">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, it cannot be raised using `RaiseEvent` in a derived form.</span><span class="sxs-lookup"><span data-stu-id="53285-118">For example, all forms inherit a <xref:System.Windows.Forms.Control.Click> event from <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, it cannot be raised using `RaiseEvent` in a derived form.</span></span> <span data-ttu-id="53285-119">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span><span class="sxs-lookup"><span data-stu-id="53285-119">If you declare a `Click` event in the form module, it shadows the form's own <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="53285-120">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span><span class="sxs-lookup"><span data-stu-id="53285-120">You can still invoke the form's <xref:System.Windows.Forms.Control.Click> event by calling the <xref:System.Windows.Forms.Control.OnClick%2A> method.</span></span>  
  
 <span data-ttu-id="53285-121">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span><span class="sxs-lookup"><span data-stu-id="53285-121">By default, an event defined in Visual Basic raises its event handlers in the order that the connections are established.</span></span> <span data-ttu-id="53285-122">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span><span class="sxs-lookup"><span data-stu-id="53285-122">Because events can have `ByRef` parameters, a process that connects late may receive parameters that have been changed by an earlier event handler.</span></span> <span data-ttu-id="53285-123">After the event handlers execute, control is returned to the subroutine that raised the event.</span><span class="sxs-lookup"><span data-stu-id="53285-123">After the event handlers execute, control is returned to the subroutine that raised the event.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53285-124">Non-shared events should not be raised within the constructor of the class in which they are declared.</span><span class="sxs-lookup"><span data-stu-id="53285-124">Non-shared events should not be raised within the constructor of the class in which they are declared.</span></span> <span data-ttu-id="53285-125">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span><span class="sxs-lookup"><span data-stu-id="53285-125">Although such events do not cause run-time errors, they may fail to be caught by associated event handlers.</span></span> <span data-ttu-id="53285-126">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span><span class="sxs-lookup"><span data-stu-id="53285-126">Use the `Shared` modifier to create a shared event if you need to raise an event from a constructor.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53285-127">You can change the default behavior of events by defining a custom event.</span><span class="sxs-lookup"><span data-stu-id="53285-127">You can change the default behavior of events by defining a custom event.</span></span> <span data-ttu-id="53285-128">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span><span class="sxs-lookup"><span data-stu-id="53285-128">For custom events, the `RaiseEvent` statement invokes the event's `RaiseEvent` accessor.</span></span> <span data-ttu-id="53285-129">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="53285-129">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="53285-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="53285-130">Example</span></span>  
 <span data-ttu-id="53285-131">The following example uses events to count down seconds from 10 to 0.</span><span class="sxs-lookup"><span data-stu-id="53285-131">The following example uses events to count down seconds from 10 to 0.</span></span> <span data-ttu-id="53285-132">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span><span class="sxs-lookup"><span data-stu-id="53285-132">The code illustrates several of the event-related methods, properties, and statements, including the `RaiseEvent` statement.</span></span>  
  
 <span data-ttu-id="53285-133">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span><span class="sxs-lookup"><span data-stu-id="53285-133">The class that raises an event is the event source, and the methods that process the event are the event handlers.</span></span> <span data-ttu-id="53285-134">An event source can have multiple handlers for the events it generates.</span><span class="sxs-lookup"><span data-stu-id="53285-134">An event source can have multiple handlers for the events it generates.</span></span> <span data-ttu-id="53285-135">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span><span class="sxs-lookup"><span data-stu-id="53285-135">When the class raises the event, that event is raised on every class that has elected to handle events for that instance of the object.</span></span>  
  
 <span data-ttu-id="53285-136">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span><span class="sxs-lookup"><span data-stu-id="53285-136">The example also uses a form (`Form1`) with a button (`Button1`) and a text box (`TextBox1`).</span></span> <span data-ttu-id="53285-137">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span><span class="sxs-lookup"><span data-stu-id="53285-137">When you click the button, the first text box displays a countdown from 10 to 0 seconds.</span></span> <span data-ttu-id="53285-138">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span><span class="sxs-lookup"><span data-stu-id="53285-138">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
 <span data-ttu-id="53285-139">The code for `Form1` specifies the initial and terminal states of the form.</span><span class="sxs-lookup"><span data-stu-id="53285-139">The code for `Form1` specifies the initial and terminal states of the form.</span></span> <span data-ttu-id="53285-140">It also contains the code executed when events are raised.</span><span class="sxs-lookup"><span data-stu-id="53285-140">It also contains the code executed when events are raised.</span></span>  
  
 <span data-ttu-id="53285-141">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span><span class="sxs-lookup"><span data-stu-id="53285-141">To use this example, open a new Windows Application project, add a button named `Button1` and a text box named `TextBox1` to the main form, named `Form1`.</span></span> <span data-ttu-id="53285-142">Then right-click the form and click **View Code** to open the Code Editor.</span><span class="sxs-lookup"><span data-stu-id="53285-142">Then right-click the form and click **View Code** to open the Code Editor.</span></span>  
  
 <span data-ttu-id="53285-143">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span><span class="sxs-lookup"><span data-stu-id="53285-143">Add a `WithEvents` variable to the declarations section of the `Form1` class.</span></span>  
  
 [!code-vb[VbVbalrEvents#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="53285-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="53285-144">Example</span></span>  
 <span data-ttu-id="53285-145">Add the following code to the code for `Form1`.</span><span class="sxs-lookup"><span data-stu-id="53285-145">Add the following code to the code for `Form1`.</span></span> <span data-ttu-id="53285-146">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span><span class="sxs-lookup"><span data-stu-id="53285-146">Replace any duplicate procedures that may exist, such as `Form_Load`, or `Button_Click`.</span></span>  
  
 [!code-vb[VbVbalrEvents#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#15)]  
  
 <span data-ttu-id="53285-147">Press F5 to run the preceding example, and click the button labeled **Start**.</span><span class="sxs-lookup"><span data-stu-id="53285-147">Press F5 to run the preceding example, and click the button labeled **Start**.</span></span> <span data-ttu-id="53285-148">The first text box starts to count down the seconds.</span><span class="sxs-lookup"><span data-stu-id="53285-148">The first text box starts to count down the seconds.</span></span> <span data-ttu-id="53285-149">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span><span class="sxs-lookup"><span data-stu-id="53285-149">When the full time (10 seconds) has elapsed, the first text box displays "Done".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53285-150">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span><span class="sxs-lookup"><span data-stu-id="53285-150">The `My.Application.DoEvents` method does not process events in exactly the same way as the form does.</span></span> <span data-ttu-id="53285-151">To allow the form to handle the events directly, you can use multithreading.</span><span class="sxs-lookup"><span data-stu-id="53285-151">To allow the form to handle the events directly, you can use multithreading.</span></span> <span data-ttu-id="53285-152">For more information, see [Managed Threading](../../../standard/threading/index.md).</span><span class="sxs-lookup"><span data-stu-id="53285-152">For more information, see [Managed Threading](../../../standard/threading/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53285-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="53285-153">See also</span></span>

- [<span data-ttu-id="53285-154">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="53285-154">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="53285-155">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="53285-155">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="53285-156">AddHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="53285-156">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="53285-157">RemoveHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="53285-157">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="53285-158">Handles</span><span class="sxs-lookup"><span data-stu-id="53285-158">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
