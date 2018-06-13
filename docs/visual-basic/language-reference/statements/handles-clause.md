---
title: Handles — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 15ce6a25aa5f403a2e55beb57b3693095743e52f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603720"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="8ee28-102">Handles — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ee28-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="8ee28-103">Deklaruje, że procedura obsługuje określone zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="8ee28-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ee28-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8ee28-104">Syntax</span></span>  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="8ee28-105">Części</span><span class="sxs-lookup"><span data-stu-id="8ee28-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="8ee28-106">`Sub` Deklaracja procedury dla tej procedury, która obsłuży zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="8ee28-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="8ee28-107">Lista zdarzeń dla `proceduredeclaration` do obsługi, oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="8ee28-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="8ee28-108">Zdarzenia musi zostać wywołane przez podstawową klasę dla bieżącej klasy lub za pomocą obiektu zadeklarowane za pomocą `WithEvents` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="8ee28-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ee28-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8ee28-109">Remarks</span></span>  
 <span data-ttu-id="8ee28-110">Użyj `Handles` — słowo kluczowe na końcu deklaracji procedury, aby spowodować ich do obsługi zdarzenia generowane przez zmienną obiektu zadeklarowane za pomocą `WithEvents` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="8ee28-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="8ee28-111">`Handles` — Słowo kluczowe można również w klasie pochodnej do obsługi zdarzeń z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="8ee28-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="8ee28-112">`Handles` — Słowo kluczowe i `AddHandler` instrukcji zarówno umożliwiają określenie określone procedury obsługi zdarzeń w szczególności, że istnieją różnice.</span><span class="sxs-lookup"><span data-stu-id="8ee28-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="8ee28-113">Użyj `Handles` — słowo kluczowe podczas definiowania procedury, aby określić, czy obsługuje ona określonego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="8ee28-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="8ee28-114">`AddHandler` Instrukcji procedury łączy się z zdarzenia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8ee28-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="8ee28-115">Aby uzyskać więcej informacji, zobacz [AddHandler — instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8ee28-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="8ee28-116">Dla zdarzeń niestandardowych aplikacji wywołuje zdarzenie `AddHandler` dostępu, gdy procedura dodawane jako program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="8ee28-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="8ee28-117">Aby uzyskać więcej informacji dotyczących zdarzeń niestandardowych, zobacz [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8ee28-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ee28-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ee28-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]  
  
 <span data-ttu-id="8ee28-119">W poniższym przykładzie pokazano, jak używać klasy pochodnej `Handles` instrukcji obsługi zdarzenia z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="8ee28-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="8ee28-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ee28-120">Example</span></span>  
 <span data-ttu-id="8ee28-121">Poniższy przykład zawiera dwa przycisk obsługi zdarzeń **aplikacji WPF** projektu.</span><span class="sxs-lookup"><span data-stu-id="8ee28-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="8ee28-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ee28-122">Example</span></span>  
 <span data-ttu-id="8ee28-123">Poniższy przykład jest odpowiednikiem poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="8ee28-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="8ee28-124">`eventlist` w `Handles` klauzula zawiera zdarzenia dla obu przycisków.</span><span class="sxs-lookup"><span data-stu-id="8ee28-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8ee28-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8ee28-125">See Also</span></span>  
 [<span data-ttu-id="8ee28-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="8ee28-126">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [<span data-ttu-id="8ee28-127">AddHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8ee28-127">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="8ee28-128">RemoveHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8ee28-128">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="8ee28-129">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8ee28-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="8ee28-130">RaiseEvent, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8ee28-130">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)  
 [<span data-ttu-id="8ee28-131">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="8ee28-131">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
