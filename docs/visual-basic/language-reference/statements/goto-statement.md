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
ms.openlocfilehash: 5e7aa036f632b4c310c4978d0d684c1222d2b096
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125567"
---
# <a name="goto-statement"></a><span data-ttu-id="40eb3-102">GoTo — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="40eb3-102">GoTo Statement</span></span>
<span data-ttu-id="40eb3-103">Gałęzie przechodzi bezwarunkowo do określonego wiersza procedury.</span><span class="sxs-lookup"><span data-stu-id="40eb3-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40eb3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40eb3-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="40eb3-105">Część</span><span class="sxs-lookup"><span data-stu-id="40eb3-105">Part</span></span>  
 `line`  
 <span data-ttu-id="40eb3-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="40eb3-106">Required.</span></span> <span data-ttu-id="40eb3-107">Jakakolwiek etykieta wiersza.</span><span class="sxs-lookup"><span data-stu-id="40eb3-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40eb3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40eb3-108">Remarks</span></span>  
 <span data-ttu-id="40eb3-109">`GoTo` Instrukcji można rozgałęziać tylko do wierszy w procedurze, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="40eb3-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="40eb3-110">Wiersz musi mieć wiersz etykiety, która `GoTo` mogą odwoływać się do.</span><span class="sxs-lookup"><span data-stu-id="40eb3-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="40eb3-111">Aby uzyskać więcej informacji, zobacz [jak: Etykietowanie instrukcji](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="40eb3-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40eb3-112">`GoTo` instrukcje może utrudnić kodu do odczytu i obsługi.</span><span class="sxs-lookup"><span data-stu-id="40eb3-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="40eb3-113">Jeśli to możliwe, należy użyć struktury sterowania.</span><span class="sxs-lookup"><span data-stu-id="40eb3-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="40eb3-114">Aby uzyskać więcej informacji, zobacz [przepływ sterowania](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="40eb3-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="40eb3-115">Nie można użyć `GoTo` instrukcji gałęzi z poza `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, lub `Using`... `End Using` konstrukcji do etykiety wewnątrz.</span><span class="sxs-lookup"><span data-stu-id="40eb3-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="40eb3-116">Rozgałęzianie i spróbuj konstrukcji</span><span class="sxs-lookup"><span data-stu-id="40eb3-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="40eb3-117">W ramach `Try`... `Catch`... `Finally` konstrukcji, obowiązują następujące reguły do gałęzi z `GoTo` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="40eb3-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="40eb3-118">Blokowanie lub region</span><span class="sxs-lookup"><span data-stu-id="40eb3-118">Block or region</span></span>|<span data-ttu-id="40eb3-119">Rozgałęziania w z zewnątrz</span><span class="sxs-lookup"><span data-stu-id="40eb3-119">Branching in from outside</span></span>|<span data-ttu-id="40eb3-120">Rozgałęziania się od wewnątrz</span><span class="sxs-lookup"><span data-stu-id="40eb3-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="40eb3-121">`Try` Blok</span><span class="sxs-lookup"><span data-stu-id="40eb3-121">`Try` block</span></span>|<span data-ttu-id="40eb3-122">Tylko z `Catch` bloku o takiej samej konstrukcji <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="40eb3-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="40eb3-123">Tylko z poza całego konstrukcji</span><span class="sxs-lookup"><span data-stu-id="40eb3-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="40eb3-124">`Catch` Blok</span><span class="sxs-lookup"><span data-stu-id="40eb3-124">`Catch` block</span></span>|<span data-ttu-id="40eb3-125">Nigdy nie jest dozwolone</span><span class="sxs-lookup"><span data-stu-id="40eb3-125">Never allowed</span></span>|<span data-ttu-id="40eb3-126">Tylko z poza całego konstrukcja lub do `Try` bloku o takiej samej konstrukcji <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="40eb3-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="40eb3-127">`Finally` Blok</span><span class="sxs-lookup"><span data-stu-id="40eb3-127">`Finally` block</span></span>|<span data-ttu-id="40eb3-128">Nigdy nie jest dozwolone</span><span class="sxs-lookup"><span data-stu-id="40eb3-128">Never allowed</span></span>|<span data-ttu-id="40eb3-129">Nigdy nie jest dozwolone</span><span class="sxs-lookup"><span data-stu-id="40eb3-129">Never allowed</span></span>|  
  
 <span data-ttu-id="40eb3-130"><sup>1</sup> Jeśli `Try`... `Catch`... `Finally` konstrukcja jest zagnieżdżony w innym ciągu, `Catch` bloku można rozgałęzić do `Try` bloku swój własny poziom zagnieżdżenia, ale nie do innych `Try` bloku.</span><span class="sxs-lookup"><span data-stu-id="40eb3-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="40eb3-131">Zagnieżdżone `Try`... `Catch`... `Finally` konstrukcji, które musi znajdować się całkowicie w `Try` lub `Catch` bloku konstruowania, w którym jest zagnieżdżony.</span><span class="sxs-lookup"><span data-stu-id="40eb3-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="40eb3-132">Poniższa ilustracja przedstawia jedną `Try` konstrukcji zagnieżdżona w innej.</span><span class="sxs-lookup"><span data-stu-id="40eb3-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="40eb3-133">Różnych gałęziach między bloki konstrukcyjne dwa obiekty są oznaczone jako prawidłowy lub nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="40eb3-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 ![Graficzny diagram rozgałęzień w konstrukcji Try](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a><span data-ttu-id="40eb3-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="40eb3-135">Example</span></span>  
 <span data-ttu-id="40eb3-136">W poniższym przykładzie użyto `GoTo` instrukcję, aby gałąź do etykiet linii w procedurze.</span><span class="sxs-lookup"><span data-stu-id="40eb3-136">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a><span data-ttu-id="40eb3-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40eb3-137">See also</span></span>
- [<span data-ttu-id="40eb3-138">Do...Loop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="40eb3-138">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="40eb3-139">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="40eb3-139">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="40eb3-140">For Each...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="40eb3-140">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="40eb3-141">Dyrektywa #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="40eb3-141">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="40eb3-142">Instrukcja Select...Case</span><span class="sxs-lookup"><span data-stu-id="40eb3-142">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="40eb3-143">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="40eb3-143">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="40eb3-144">While...End While, instrukcja</span><span class="sxs-lookup"><span data-stu-id="40eb3-144">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="40eb3-145">With...End With, instrukcja</span><span class="sxs-lookup"><span data-stu-id="40eb3-145">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
