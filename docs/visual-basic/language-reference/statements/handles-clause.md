---
title: Handles — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 50a449ea8a5131c878cf703f44695cd2e2304444
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842580"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="94d72-102">Handles — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94d72-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="94d72-103">Deklaruje, że procedura obsługuje określone zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="94d72-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94d72-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="94d72-104">Syntax</span></span>  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="94d72-105">Części</span><span class="sxs-lookup"><span data-stu-id="94d72-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="94d72-106">`Sub` Deklaracja procedury dla procedury, która obsłuży zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="94d72-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="94d72-107">Lista zdarzeń dla `proceduredeclaration` do obsługi, oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="94d72-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="94d72-108">Zdarzenia musi zostać wywołane, albo klasę bazową dla bieżącej klasy lub obiekt, który został zadeklarowany za pomocą `WithEvents` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="94d72-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94d72-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="94d72-109">Remarks</span></span>  
 <span data-ttu-id="94d72-110">Użyj `Handles` — słowo kluczowe na końcu deklaracja procedury, aby spowodować, że obsługa zdarzeń wywołanych przez zmienną obiektu zadeklarowane za pomocą `WithEvents` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="94d72-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="94d72-111">`Handles` — Słowo kluczowe można również w klasie pochodnej do obsługi zdarzeń z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="94d72-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="94d72-112">Zarówno słowo kluczowe `Handles`, jak i instrukcja `AddHandler` umożliwiają określenie konkretnych procedur do obsługi konkretnych zdarzeń, ale występują tu pewne różnice.</span><span class="sxs-lookup"><span data-stu-id="94d72-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="94d72-113">Słowa kluczowego `Handles` należy użyć podczas definiowania procedury, aby określić, że ma ona obsługiwać konkretne zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="94d72-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="94d72-114">Instrukcja `AddHandler` łączy procedury ze zdarzeniami w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="94d72-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="94d72-115">Aby uzyskać więcej informacji, zobacz [AddHandler — instrukcja](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="94d72-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="94d72-116">Dla zdarzenia niestandardowe, aplikacja wywołuje zdarzenie `AddHandler` dostępu, jeśli zwiększy procedury jako program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="94d72-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="94d72-117">Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz artykuł [Instrukcja Event](../../../visual-basic/language-reference/statements/event-statement.md)</span><span class="sxs-lookup"><span data-stu-id="94d72-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94d72-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="94d72-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="94d72-119">W poniższym przykładzie pokazano, jak używać klasy pochodnej `Handles` instrukcję, aby obsłużyć zdarzenie z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="94d72-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="94d72-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="94d72-120">Example</span></span>  
 <span data-ttu-id="94d72-121">Poniższy przykład zawiera dwa programy obsługi zdarzeń przycisku dla **aplikacji WPF** projektu.</span><span class="sxs-lookup"><span data-stu-id="94d72-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="94d72-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="94d72-122">Example</span></span>  
 <span data-ttu-id="94d72-123">Poniższy przykład jest równoważny do poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="94d72-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="94d72-124">`eventlist` w `Handles` klauzula zawiera zdarzenia dla obu przycisków.</span><span class="sxs-lookup"><span data-stu-id="94d72-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="94d72-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="94d72-125">See also</span></span>

- [<span data-ttu-id="94d72-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="94d72-126">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
- [<span data-ttu-id="94d72-127">AddHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="94d72-127">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="94d72-128">RemoveHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="94d72-128">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="94d72-129">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="94d72-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="94d72-130">RaiseEvent, instrukcja</span><span class="sxs-lookup"><span data-stu-id="94d72-130">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [<span data-ttu-id="94d72-131">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="94d72-131">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
