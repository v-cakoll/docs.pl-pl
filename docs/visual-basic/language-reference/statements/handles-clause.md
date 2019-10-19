---
title: Handles — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: ae05e77515e4e2b50cdf5f9a1908375fa311c3a3
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581800"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="2ae46-102">Handles — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ae46-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="2ae46-103">Deklaruje, że procedura obsługuje określone zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="2ae46-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ae46-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2ae46-104">Syntax</span></span>  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="2ae46-105">Części</span><span class="sxs-lookup"><span data-stu-id="2ae46-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="2ae46-106">Procedura `Sub` deklaracji procedury, która będzie obsługiwać zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="2ae46-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="2ae46-107">Lista zdarzeń `proceduredeclaration` do obsłużenia, rozdzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="2ae46-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="2ae46-108">Zdarzenia muszą być wywoływane przez klasę bazową dla bieżącej klasy lub przez obiekt zadeklarowany za pomocą słowa kluczowego `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="2ae46-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ae46-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2ae46-109">Remarks</span></span>  
 <span data-ttu-id="2ae46-110">Użyj słowa kluczowego `Handles` na końcu deklaracji procedury, aby spowodować obsługę zdarzeń wywoływanych przez zmienną obiektu zadeklarowaną za pomocą słowa kluczowego `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="2ae46-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="2ae46-111">Słowa kluczowego `Handles` można również użyć w klasie pochodnej do obsługi zdarzeń z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="2ae46-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="2ae46-112">Słowo kluczowe `Handles` i instrukcja `AddHandler` umożliwiają określenie, że konkretne procedury obsługują określone zdarzenia, ale istnieją różnice.</span><span class="sxs-lookup"><span data-stu-id="2ae46-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="2ae46-113">Użyj słowa kluczowego `Handles` podczas definiowania procedury, aby określić, że obsługuje określone zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="2ae46-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="2ae46-114">Instrukcja `AddHandler` łączy procedury ze zdarzeniami w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2ae46-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="2ae46-115">Aby uzyskać więcej informacji, zobacz [AddHandler instrukcji](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2ae46-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="2ae46-116">W przypadku zdarzeń niestandardowych aplikacja wywołuje metodę dostępu `AddHandler` zdarzenia, gdy dodaje procedurę jako program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2ae46-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="2ae46-117">Aby uzyskać więcej informacji na temat zdarzeń niestandardowych, zobacz [instrukcja zdarzenia](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2ae46-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ae46-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ae46-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="2ae46-119">W poniższym przykładzie pokazano, jak Klasa pochodna może używać instrukcji `Handles`, aby obsłużyć zdarzenie z klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="2ae46-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="2ae46-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ae46-120">Example</span></span>  
 <span data-ttu-id="2ae46-121">Poniższy przykład zawiera dwa programy obsługi zdarzeń przycisków dla projektu **aplikacji WPF** .</span><span class="sxs-lookup"><span data-stu-id="2ae46-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="2ae46-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="2ae46-122">Example</span></span>  
 <span data-ttu-id="2ae46-123">Poniższy przykład jest równoważny z poprzednim przykładem.</span><span class="sxs-lookup"><span data-stu-id="2ae46-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="2ae46-124">@No__t_0 w klauzuli `Handles` zawiera zdarzenia dla obu przycisków.</span><span class="sxs-lookup"><span data-stu-id="2ae46-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="2ae46-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ae46-125">See also</span></span>

- [<span data-ttu-id="2ae46-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="2ae46-126">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
- [<span data-ttu-id="2ae46-127">AddHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2ae46-127">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="2ae46-128">RemoveHandler, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2ae46-128">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="2ae46-129">Event, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2ae46-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="2ae46-130">RaiseEvent, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2ae46-130">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [<span data-ttu-id="2ae46-131">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="2ae46-131">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
