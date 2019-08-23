---
title: GoTo — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
ms.openlocfilehash: 3034c84684e94dfe8c334107a16df8cbd227c4d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912449"
---
# <a name="goto-statement"></a><span data-ttu-id="5391a-102">GoTo — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="5391a-102">GoTo Statement</span></span>
<span data-ttu-id="5391a-103">Rozgałęzienia bezwarunkowo do określonego wiersza procedury.</span><span class="sxs-lookup"><span data-stu-id="5391a-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5391a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5391a-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="5391a-105">Części</span><span class="sxs-lookup"><span data-stu-id="5391a-105">Part</span></span>  
 `line`  
 <span data-ttu-id="5391a-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="5391a-106">Required.</span></span> <span data-ttu-id="5391a-107">Dowolna etykieta wiersza.</span><span class="sxs-lookup"><span data-stu-id="5391a-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5391a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5391a-108">Remarks</span></span>  
 <span data-ttu-id="5391a-109">`GoTo` Instrukcja może rozgałęziać tylko do wierszy w procedurze, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="5391a-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="5391a-110">Wiersz musi mieć etykietę wiersza, która `GoTo` może odwoływać się do.</span><span class="sxs-lookup"><span data-stu-id="5391a-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="5391a-111">Aby uzyskać więcej informacji, zobacz [jak: Instrukcje](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)etykiet.</span><span class="sxs-lookup"><span data-stu-id="5391a-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5391a-112">`GoTo`instrukcje mogą utrudniać odczytywanie i konserwację kodu.</span><span class="sxs-lookup"><span data-stu-id="5391a-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="5391a-113">Jeśli to możliwe, zamiast tego użyj struktury formantu.</span><span class="sxs-lookup"><span data-stu-id="5391a-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="5391a-114">Aby uzyskać więcej informacji, zobacz [sterowanie przepływem](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="5391a-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="5391a-115">Nie można użyć `GoTo` instrukcji do rozgałęzienia spoza elementu `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With` lub`Using`... `End Using` konstrukcja do etykiety wewnątrz.</span><span class="sxs-lookup"><span data-stu-id="5391a-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="5391a-116">Rozgałęzianie i próba konstrukcji</span><span class="sxs-lookup"><span data-stu-id="5391a-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="5391a-117">`Try`W... `Catch`... w celu rozgałęziania `GoTo` instrukcji należy zastosować następujące reguły. `Finally`</span><span class="sxs-lookup"><span data-stu-id="5391a-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="5391a-118">Blok lub region</span><span class="sxs-lookup"><span data-stu-id="5391a-118">Block or region</span></span>|<span data-ttu-id="5391a-119">Rozgałęzianie od zewnątrz</span><span class="sxs-lookup"><span data-stu-id="5391a-119">Branching in from outside</span></span>|<span data-ttu-id="5391a-120">Rozgałęzianie od wewnątrz</span><span class="sxs-lookup"><span data-stu-id="5391a-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="5391a-121">`Try`odblokowan</span><span class="sxs-lookup"><span data-stu-id="5391a-121">`Try` block</span></span>|<span data-ttu-id="5391a-122">Tylko z `Catch` bloku tej samej konstrukcji <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="5391a-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="5391a-123">Tylko poza całością konstrukcji</span><span class="sxs-lookup"><span data-stu-id="5391a-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="5391a-124">`Catch`odblokowan</span><span class="sxs-lookup"><span data-stu-id="5391a-124">`Catch` block</span></span>|<span data-ttu-id="5391a-125">Nigdy niedozwolone</span><span class="sxs-lookup"><span data-stu-id="5391a-125">Never allowed</span></span>|<span data-ttu-id="5391a-126">Tylko poza całościową budową lub `Try` blokiem tej samej konstrukcji <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="5391a-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="5391a-127">`Finally`odblokowan</span><span class="sxs-lookup"><span data-stu-id="5391a-127">`Finally` block</span></span>|<span data-ttu-id="5391a-128">Nigdy niedozwolone</span><span class="sxs-lookup"><span data-stu-id="5391a-128">Never allowed</span></span>|<span data-ttu-id="5391a-129">Nigdy niedozwolone</span><span class="sxs-lookup"><span data-stu-id="5391a-129">Never allowed</span></span>|  
  
 <span data-ttu-id="5391a-130"><sup>1</sup> , jeśli `Try`jeden... `Catch`... konstrukcja jest zagnieżdżona w innym `Catch` , `Try` blok może odgałęzić się do bloku na jego własnym poziomie zagnieżdżenia, ale nie w `Try` żadnym innym bloku. `Finally`</span><span class="sxs-lookup"><span data-stu-id="5391a-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="5391a-131">Zagnieżdżony `Try`... `Catch`... konstrukcja musi być całkowicie zawarta `Try` w `Catch` bloku lub konstrukcji, w której jest zagnieżdżona. `Finally`</span><span class="sxs-lookup"><span data-stu-id="5391a-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="5391a-132">Na poniższej ilustracji przedstawiono jedną `Try` konstrukcję zagnieżdżoną w innej.</span><span class="sxs-lookup"><span data-stu-id="5391a-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="5391a-133">Różne gałęzie między blokami dwóch konstrukcji są wskazywane jako prawidłowe lub nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="5391a-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Diagram graficzny rozgałęzień w konstrukcjach try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="5391a-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="5391a-135">Example</span></span>  
 <span data-ttu-id="5391a-136">Poniższy przykład używa `GoTo` instrukcji do rozgałęziania etykiet linii w procedurze.</span><span class="sxs-lookup"><span data-stu-id="5391a-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="5391a-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5391a-137">See also</span></span>

- [<span data-ttu-id="5391a-138">Do...Loop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5391a-138">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="5391a-139">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5391a-139">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="5391a-140">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5391a-140">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="5391a-141">Dyrektywa #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="5391a-141">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="5391a-142">Instrukcja Select...Case</span><span class="sxs-lookup"><span data-stu-id="5391a-142">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="5391a-143">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5391a-143">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="5391a-144">While...End While, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5391a-144">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="5391a-145">With...End With, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5391a-145">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
