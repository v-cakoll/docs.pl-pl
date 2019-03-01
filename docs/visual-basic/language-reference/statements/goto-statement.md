---
title: GoTo — instrukcja (Visual Basic)
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
ms.openlocfilehash: 9d2cec7f9cd2cc9d8985c9add103748583c25dc9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968936"
---
# <a name="goto-statement"></a><span data-ttu-id="2a948-102">GoTo — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a948-102">GoTo Statement</span></span>
<span data-ttu-id="2a948-103">Gałęzie przechodzi bezwarunkowo do określonego wiersza procedury.</span><span class="sxs-lookup"><span data-stu-id="2a948-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a948-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2a948-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="2a948-105">Część</span><span class="sxs-lookup"><span data-stu-id="2a948-105">Part</span></span>  
 `line`  
 <span data-ttu-id="2a948-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="2a948-106">Required.</span></span> <span data-ttu-id="2a948-107">Jakakolwiek etykieta wiersza.</span><span class="sxs-lookup"><span data-stu-id="2a948-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a948-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2a948-108">Remarks</span></span>  
 <span data-ttu-id="2a948-109">`GoTo` Instrukcji można rozgałęziać tylko do wierszy w procedurze, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="2a948-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="2a948-110">Wiersz musi mieć wiersz etykiety, która `GoTo` mogą odwoływać się do.</span><span class="sxs-lookup"><span data-stu-id="2a948-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="2a948-111">Aby uzyskać więcej informacji, zobacz [jak: Etykietowanie instrukcji](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="2a948-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a948-112">`GoTo` instrukcje może utrudnić kodu do odczytu i obsługi.</span><span class="sxs-lookup"><span data-stu-id="2a948-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="2a948-113">Jeśli to możliwe, należy użyć struktury sterowania.</span><span class="sxs-lookup"><span data-stu-id="2a948-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="2a948-114">Aby uzyskać więcej informacji, zobacz [przepływ sterowania](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="2a948-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="2a948-115">Nie można użyć `GoTo` instrukcji gałęzi z poza `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, lub `Using`... `End Using` konstrukcji do etykiety wewnątrz.</span><span class="sxs-lookup"><span data-stu-id="2a948-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="2a948-116">Rozgałęzianie i spróbuj konstrukcji</span><span class="sxs-lookup"><span data-stu-id="2a948-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="2a948-117">W ramach `Try`... `Catch`... `Finally` konstrukcji, obowiązują następujące reguły do gałęzi z `GoTo` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2a948-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="2a948-118">Blokowanie lub region</span><span class="sxs-lookup"><span data-stu-id="2a948-118">Block or region</span></span>|<span data-ttu-id="2a948-119">Rozgałęziania w z zewnątrz</span><span class="sxs-lookup"><span data-stu-id="2a948-119">Branching in from outside</span></span>|<span data-ttu-id="2a948-120">Rozgałęziania się od wewnątrz</span><span class="sxs-lookup"><span data-stu-id="2a948-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="2a948-121">`Try` Blok</span><span class="sxs-lookup"><span data-stu-id="2a948-121">`Try` block</span></span>|<span data-ttu-id="2a948-122">Tylko z `Catch` bloku o takiej samej konstrukcji <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2a948-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="2a948-123">Tylko z poza całego konstrukcji</span><span class="sxs-lookup"><span data-stu-id="2a948-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="2a948-124">`Catch` Blok</span><span class="sxs-lookup"><span data-stu-id="2a948-124">`Catch` block</span></span>|<span data-ttu-id="2a948-125">Nigdy nie jest dozwolone</span><span class="sxs-lookup"><span data-stu-id="2a948-125">Never allowed</span></span>|<span data-ttu-id="2a948-126">Tylko z poza całego konstrukcja lub do `Try` bloku o takiej samej konstrukcji <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="2a948-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="2a948-127">`Finally` Blok</span><span class="sxs-lookup"><span data-stu-id="2a948-127">`Finally` block</span></span>|<span data-ttu-id="2a948-128">Nigdy nie jest dozwolone</span><span class="sxs-lookup"><span data-stu-id="2a948-128">Never allowed</span></span>|<span data-ttu-id="2a948-129">Nigdy nie jest dozwolone</span><span class="sxs-lookup"><span data-stu-id="2a948-129">Never allowed</span></span>|  
  
 <span data-ttu-id="2a948-130"><sup>1</sup> Jeśli `Try`... `Catch`... `Finally` konstrukcja jest zagnieżdżony w innym ciągu, `Catch` bloku można rozgałęzić do `Try` bloku swój własny poziom zagnieżdżenia, ale nie do innych `Try` bloku.</span><span class="sxs-lookup"><span data-stu-id="2a948-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="2a948-131">Zagnieżdżone `Try`... `Catch`... `Finally` konstrukcji, które musi znajdować się całkowicie w `Try` lub `Catch` bloku konstruowania, w którym jest zagnieżdżony.</span><span class="sxs-lookup"><span data-stu-id="2a948-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="2a948-132">Poniższa ilustracja przedstawia jedną `Try` konstrukcji zagnieżdżona w innej.</span><span class="sxs-lookup"><span data-stu-id="2a948-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="2a948-133">Różnych gałęziach między bloki konstrukcyjne dwa obiekty są oznaczone jako prawidłowy lub nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="2a948-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 <span data-ttu-id="2a948-134">![Graficzny diagram rozgałęzień w konstrukcji Try](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span><span class="sxs-lookup"><span data-stu-id="2a948-134">![Graphic diagram of branching in Try constructions](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span></span>  
<span data-ttu-id="2a948-135">Prawidłowe i nieprawidłowe gałęzi, skorzystaj z konstrukcji Try</span><span class="sxs-lookup"><span data-stu-id="2a948-135">Valid and invalid branches in Try constructions</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a948-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a948-136">Example</span></span>  
 <span data-ttu-id="2a948-137">W poniższym przykładzie użyto `GoTo` instrukcję, aby gałąź do etykiet linii w procedurze.</span><span class="sxs-lookup"><span data-stu-id="2a948-137">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="2a948-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a948-138">See also</span></span>
- [<span data-ttu-id="2a948-139">Do...Loop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a948-139">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="2a948-140">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a948-140">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="2a948-141">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a948-141">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="2a948-142">Dyrektywa #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="2a948-142">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="2a948-143">Instrukcja Select...Case</span><span class="sxs-lookup"><span data-stu-id="2a948-143">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="2a948-144">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a948-144">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="2a948-145">While...End While, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a948-145">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="2a948-146">With...End With, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2a948-146">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
