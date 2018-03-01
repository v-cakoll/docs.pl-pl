---
title: "GoTo — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22a6315e69cd6c797d462d0835e85bb1dde67dcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="goto-statement"></a><span data-ttu-id="966fe-102">GoTo — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="966fe-102">GoTo Statement</span></span>
<span data-ttu-id="966fe-103">Przechodzi bezwarunkowo do określonego wiersza procedury.</span><span class="sxs-lookup"><span data-stu-id="966fe-103">Branches unconditionally to a specified line in a procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="966fe-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="966fe-104">Syntax</span></span>  
  
```  
GoTo line  
```  
  
## <a name="part"></a><span data-ttu-id="966fe-105">Część</span><span class="sxs-lookup"><span data-stu-id="966fe-105">Part</span></span>  
 `line`  
 <span data-ttu-id="966fe-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="966fe-106">Required.</span></span> <span data-ttu-id="966fe-107">Wszystkie wiersza etykiety.</span><span class="sxs-lookup"><span data-stu-id="966fe-107">Any line label.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="966fe-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="966fe-108">Remarks</span></span>  
 <span data-ttu-id="966fe-109">`GoTo` Instrukcji można rozgałęzić tylko wiersze w procedurze, w której znajduje się.</span><span class="sxs-lookup"><span data-stu-id="966fe-109">The `GoTo` statement can branch only to lines in the procedure in which it appears.</span></span> <span data-ttu-id="966fe-110">Wiersz musi mieć etykietę linii `GoTo` mogą odwoływać się do.</span><span class="sxs-lookup"><span data-stu-id="966fe-110">The line must have a line label that `GoTo` can refer to.</span></span> <span data-ttu-id="966fe-111">Aby uzyskać więcej informacji, zobacz [porady: Etykieta instrukcji](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span><span class="sxs-lookup"><span data-stu-id="966fe-111">For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="966fe-112">`GoTo`instrukcje może utrudnić kodu do odczytu i obsługi.</span><span class="sxs-lookup"><span data-stu-id="966fe-112">`GoTo` statements can make code difficult to read and maintain.</span></span> <span data-ttu-id="966fe-113">Jeśli to możliwe, należy użyć Struktura kontroli.</span><span class="sxs-lookup"><span data-stu-id="966fe-113">Whenever possible, use a control structure instead.</span></span> <span data-ttu-id="966fe-114">Aby uzyskać więcej informacji, zobacz [przepływ sterowania](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span><span class="sxs-lookup"><span data-stu-id="966fe-114">For more information, see [Control Flow](../../../visual-basic/programming-guide/language-features/control-flow/index.md).</span></span>  
  
 <span data-ttu-id="966fe-115">Nie można użyć `GoTo` instrukcji do gałęzi poza `For`... `Next`, `For Each`... `Next`, `SyncLock`... `End SyncLock`, `Try`... `Catch`... `Finally`, `With`... `End With`, lub `Using`... `End Using` konstrukcji etykietę wewnątrz.</span><span class="sxs-lookup"><span data-stu-id="966fe-115">You cannot use a `GoTo` statement to branch from outside a `For`...`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`, or `Using`...`End Using` construction to a label inside.</span></span>  
  
## <a name="branching-and-try-constructions"></a><span data-ttu-id="966fe-116">Rozgałęzianie i spróbuj konstrukcji</span><span class="sxs-lookup"><span data-stu-id="966fe-116">Branching and Try Constructions</span></span>  
 <span data-ttu-id="966fe-117">W ramach `Try`... `Catch`... `Finally` obowiązują następujące reguły konstrukcji, aby rozgałęziania z `GoTo` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="966fe-117">Within a `Try`...`Catch`...`Finally` construction, the following rules apply to branching with the `GoTo` statement.</span></span>  
  
|<span data-ttu-id="966fe-118">Blokowanie lub region</span><span class="sxs-lookup"><span data-stu-id="966fe-118">Block or region</span></span>|<span data-ttu-id="966fe-119">Rozgałęziania w z poza</span><span class="sxs-lookup"><span data-stu-id="966fe-119">Branching in from outside</span></span>|<span data-ttu-id="966fe-120">Rozgałęziania limit z wewnątrz</span><span class="sxs-lookup"><span data-stu-id="966fe-120">Branching out from inside</span></span>|  
|---------------------|-------------------------------|-------------------------------|  
|<span data-ttu-id="966fe-121">`Try`Blok</span><span class="sxs-lookup"><span data-stu-id="966fe-121">`Try` block</span></span>|<span data-ttu-id="966fe-122">Tylko z `Catch` bloku o takiej samej konstrukcji <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="966fe-122">Only from a `Catch` block of the same construction <sup>1</sup></span></span>|<span data-ttu-id="966fe-123">Tylko poza całego konstrukcji</span><span class="sxs-lookup"><span data-stu-id="966fe-123">Only to outside the whole construction</span></span>|  
|<span data-ttu-id="966fe-124">`Catch`Blok</span><span class="sxs-lookup"><span data-stu-id="966fe-124">`Catch` block</span></span>|<span data-ttu-id="966fe-125">Nigdy nie są dozwolone</span><span class="sxs-lookup"><span data-stu-id="966fe-125">Never allowed</span></span>|<span data-ttu-id="966fe-126">Tylko poza całego konstruowania lub do `Try` bloku o takiej samej konstrukcji <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="966fe-126">Only to outside the whole construction, or to the `Try` block of the same construction <sup>1</sup></span></span>|  
|<span data-ttu-id="966fe-127">`Finally`Blok</span><span class="sxs-lookup"><span data-stu-id="966fe-127">`Finally` block</span></span>|<span data-ttu-id="966fe-128">Nigdy nie są dozwolone</span><span class="sxs-lookup"><span data-stu-id="966fe-128">Never allowed</span></span>|<span data-ttu-id="966fe-129">Nigdy nie są dozwolone</span><span class="sxs-lookup"><span data-stu-id="966fe-129">Never allowed</span></span>|  
  
 <span data-ttu-id="966fe-130"><sup>1</sup> jeden `Try`... `Catch`... `Finally` konstrukcji jest zagnieżdżony w innym, `Catch` bloku można rozgałęzić do `Try` bloku na jego własnej poziom zagnieżdżenia, ale nie do innych `Try` bloku.</span><span class="sxs-lookup"><span data-stu-id="966fe-130"><sup>1</sup> If one `Try`...`Catch`...`Finally` construction is nested within another, a `Catch` block can branch into the `Try` block at its own nesting level, but not into any other `Try` block.</span></span> <span data-ttu-id="966fe-131">Zagnieżdżoną `Try`... `Catch`... `Finally` konstrukcji musi znajdować się całkowicie w `Try` lub `Catch` konstrukcji, w którym jest zagnieżdżony blok.</span><span class="sxs-lookup"><span data-stu-id="966fe-131">A nested `Try`...`Catch`...`Finally` construction must be contained completely in a `Try` or `Catch` block of the construction within which it is nested.</span></span>  
  
 <span data-ttu-id="966fe-132">Na poniższej ilustracji przedstawiono jedną `Try` konstrukcji zagnieżdżone w innym.</span><span class="sxs-lookup"><span data-stu-id="966fe-132">The following illustration shows one `Try` construction nested within another.</span></span> <span data-ttu-id="966fe-133">Różnych gałęzi między bloków dwa obiekty są oznaczone jako prawidłowy lub nieprawidłowy.</span><span class="sxs-lookup"><span data-stu-id="966fe-133">Various branches among the blocks of the two constructions are indicated as valid or invalid.</span></span>  
  
 <span data-ttu-id="966fe-134">![Graficzny diagram rozgałęzień w konstrukcjach Try](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span><span class="sxs-lookup"><span data-stu-id="966fe-134">![Graphic diagram of branching in Try constructions](../../../visual-basic/language-reference/statements/media/trybranching.gif "TryBranching")</span></span>  
<span data-ttu-id="966fe-135">Prawidłowe oraz nieprawidłowe gałęzie w konstrukcjach Try</span><span class="sxs-lookup"><span data-stu-id="966fe-135">Valid and invalid branches in Try constructions</span></span>  
  
## <a name="example"></a><span data-ttu-id="966fe-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="966fe-136">Example</span></span>  
 <span data-ttu-id="966fe-137">W poniższym przykładzie użyto `GoTo` instrukcji do gałęzi etykiet linii w procedurze.</span><span class="sxs-lookup"><span data-stu-id="966fe-137">The following example uses the `GoTo` statement to branch to line labels in a procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#31](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/goto-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="966fe-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="966fe-138">See Also</span></span>  
 [<span data-ttu-id="966fe-139">Czy... Loop — instrukcja</span><span class="sxs-lookup"><span data-stu-id="966fe-139">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="966fe-140">Dla... Next — instrukcja</span><span class="sxs-lookup"><span data-stu-id="966fe-140">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="966fe-141">For Each... Next — instrukcja</span><span class="sxs-lookup"><span data-stu-id="966fe-141">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="966fe-142">IF... Następnie... Else — instrukcja</span><span class="sxs-lookup"><span data-stu-id="966fe-142">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="966fe-143">Wybierz... Case-instrukcja</span><span class="sxs-lookup"><span data-stu-id="966fe-143">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [<span data-ttu-id="966fe-144">Try... CATCH... Finally — instrukcja</span><span class="sxs-lookup"><span data-stu-id="966fe-144">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="966fe-145">While... End While — instrukcja</span><span class="sxs-lookup"><span data-stu-id="966fe-145">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)  
 [<span data-ttu-id="966fe-146">Z... End With — instrukcja</span><span class="sxs-lookup"><span data-stu-id="966fe-146">With...End With Statement</span></span>](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
