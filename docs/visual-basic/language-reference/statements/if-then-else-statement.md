---
title: "If...Then...Else — Instrukcja (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 898b72055345e88ca35f805de211c0c57cd74200
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="689ed-102">If...Then...Else — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="689ed-102">If...Then...Else Statement (Visual Basic)</span></span>
<span data-ttu-id="689ed-103">Warunkowo wykonuje grupy poleceń w zależności od wartości wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="689ed-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="689ed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="689ed-104">Syntax</span></span>  
  
```  
' Multiple-line syntax:  
If condition [ Then ]  
    [ statements ]  
[ ElseIf elseifcondition [ Then ]  
    [ elseifstatements ] ]  
[ Else  
    [ elsestatements ] ]  
End If  
  
' Single-line syntax:  
If condition Then [ statements ] [ Else [ elsestatements ] ]  
```  
  
## <a name="parts"></a><span data-ttu-id="689ed-105">Części</span><span class="sxs-lookup"><span data-stu-id="689ed-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="689ed-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="689ed-106">Required.</span></span> <span data-ttu-id="689ed-107">Wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="689ed-107">Expression.</span></span> <span data-ttu-id="689ed-108">Musi być `True` lub `False`, lub umożliwiają niejawnej konwersji na typ danych `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="689ed-108">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 <span data-ttu-id="689ed-109">Jeśli wyrażenie jest [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` zmiennej, która daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), warunek jest traktowana tak, jakby to wyrażenie nie jest `True`i `Else` blok wykonywane.</span><span class="sxs-lookup"><span data-stu-id="689ed-109">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is not `True`, and the `Else` block is executed.</span></span>  
  
 `Then`  
 <span data-ttu-id="689ed-110">Wymagany w składni pojedynczej linii; Opcjonalnie w wielu wierszach składni.</span><span class="sxs-lookup"><span data-stu-id="689ed-110">Required in the single-line syntax; optional in the multiple-line syntax.</span></span>  
  
 `statements`  
 <span data-ttu-id="689ed-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="689ed-111">Optional.</span></span> <span data-ttu-id="689ed-112">Jeden lub więcej następujących instrukcji `If`... `Then` wdrożeniowych Jeśli `condition` daje w wyniku `True`.</span><span class="sxs-lookup"><span data-stu-id="689ed-112">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>  
  
 `elseifcondition`  
 <span data-ttu-id="689ed-113">Jeśli wymagane `ElseIf` jest obecny.</span><span class="sxs-lookup"><span data-stu-id="689ed-113">Required if `ElseIf` is present.</span></span> <span data-ttu-id="689ed-114">Wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="689ed-114">Expression.</span></span> <span data-ttu-id="689ed-115">Musi być `True` lub `False`, lub umożliwiają niejawnej konwersji na typ danych `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="689ed-115">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 `elseifstatements`  
 <span data-ttu-id="689ed-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="689ed-116">Optional.</span></span> <span data-ttu-id="689ed-117">Jeden lub więcej następujących instrukcji `ElseIf`... `Then` wdrożeniowych Jeśli `elseifcondition` daje w wyniku `True`.</span><span class="sxs-lookup"><span data-stu-id="689ed-117">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>  
  
 `elsestatements`  
 <span data-ttu-id="689ed-118">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="689ed-118">Optional.</span></span> <span data-ttu-id="689ed-119">Co najmniej jeden instrukcji, które są wykonywane, jeśli nie poprzedniej `condition` lub `elseifcondition` wyrażenie daje w wyniku `True`.</span><span class="sxs-lookup"><span data-stu-id="689ed-119">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>  
  
 `End If`  
 <span data-ttu-id="689ed-120">Kończy `If`... `Then`... `Else` bloku.</span><span class="sxs-lookup"><span data-stu-id="689ed-120">Terminates the `If`...`Then`...`Else` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="689ed-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="689ed-121">Remarks</span></span>  
  
## <a name="multiple-line-syntax"></a><span data-ttu-id="689ed-122">Składnia wielu linii</span><span class="sxs-lookup"><span data-stu-id="689ed-122">Multiple-Line Syntax</span></span>  
 <span data-ttu-id="689ed-123">Gdy `If`... `Then`... `Else` napotkano instrukcji `condition` jest testowana.</span><span class="sxs-lookup"><span data-stu-id="689ed-123">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="689ed-124">Jeśli `condition` jest `True`, instrukcji `Then` są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="689ed-124">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="689ed-125">Jeśli `condition` jest `False`, każdy `ElseIf` instrukcji (jeśli istnieją) są oceniane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="689ed-125">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="689ed-126">Gdy `True``elseifcondition` zostanie znaleziony, natychmiast po skojarzone instrukcje `ElseIf` są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="689ed-126">When a `True``elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="689ed-127">Jeśli nie `elseifcondition` daje w wyniku `True`, lub jeśli występują nie `ElseIf` instrukcje, instrukcji `Else` są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="689ed-127">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="689ed-128">Po wykonaniu następujące instrukcje `Then`, `ElseIf`, lub `Else`, wykonanie będzie kontynuowane przy użyciu następujących instrukcji `End If`.</span><span class="sxs-lookup"><span data-stu-id="689ed-128">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>  
  
 <span data-ttu-id="689ed-129">`ElseIf` i `Else` klauzule są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="689ed-129">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="689ed-130">Może mieć tyle `ElseIf` klauzule jako użytkownik ma `If`... `Then`... `Else` instrukcji, ale nie `ElseIf` klauzula może występować po `Else` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="689ed-130">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="689ed-131">`If`... `Then`... `Else` instrukcje mogą być zagnieżdżone wewnątrz innych.</span><span class="sxs-lookup"><span data-stu-id="689ed-131">`If`...`Then`...`Else` statements can be nested within each other.</span></span>  
  
 <span data-ttu-id="689ed-132">W wielu wierszach składni `If` instrukcja musi być jedyną instrukcją w pierwszym wierszu.</span><span class="sxs-lookup"><span data-stu-id="689ed-132">In the multiple-line syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="689ed-133">`ElseIf`, `Else`, I `End If` instrukcje mogą być poprzedzone tylko etykiety linii.</span><span class="sxs-lookup"><span data-stu-id="689ed-133">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="689ed-134">`If`... `Then`... `Else` musi się kończyć bloku `End If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="689ed-134">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="689ed-135">[Wybierz... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md) może być bardziej użyteczne podczas oceny jedno wyrażenie, które ma kilka możliwych wartości.</span><span class="sxs-lookup"><span data-stu-id="689ed-135">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>  
  
## <a name="single-line-syntax"></a><span data-ttu-id="689ed-136">Składnia jeden wiersz</span><span class="sxs-lookup"><span data-stu-id="689ed-136">Single-Line Syntax</span></span>  
 <span data-ttu-id="689ed-137">Za pomocą składni jeden wiersz dla testów krótkie, proste.</span><span class="sxs-lookup"><span data-stu-id="689ed-137">You can use the single-line syntax for short, simple tests.</span></span> <span data-ttu-id="689ed-138">Jednak składni wielowierszowe zapewnia więcej struktury i elastyczność i ułatwia odczytu, obsługa i debugowania.</span><span class="sxs-lookup"><span data-stu-id="689ed-138">However, the multiple-line syntax provides more structure and flexibility and is usually easier to read, maintain, and debug.</span></span>  
  
 <span data-ttu-id="689ed-139">Jakie następujące `Then` — słowo kluczowe jest sprawdzony w celu określenia, czy instrukcja jest jeden wiersz `If`.</span><span class="sxs-lookup"><span data-stu-id="689ed-139">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="689ed-140">Jeśli jest inny niż komentarz za `Then` w tym samym wierszu, instrukcja jest traktowane jako jeden wiersz `If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="689ed-140">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="689ed-141">Jeśli `Then` jest nieobecne, musi być uruchomienia wielu linii `If`... `Then`... `Else`.</span><span class="sxs-lookup"><span data-stu-id="689ed-141">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>  
  
 <span data-ttu-id="689ed-142">W składni jeden wiersz może mieć wiele instrukcji wykonane w wyniku `If`... `Then` decyzji.</span><span class="sxs-lookup"><span data-stu-id="689ed-142">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="689ed-143">Wszystkie instrukcje musi znajdować się na tym samym wierszu i być oddzielone dwukropkiem.</span><span class="sxs-lookup"><span data-stu-id="689ed-143">All statements must be on the same line and be separated by colons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="689ed-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="689ed-144">Example</span></span>  
 <span data-ttu-id="689ed-145">Poniższy przykład przedstawia użycie składni wielowierszowe `If`... `Then`... `Else` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="689ed-145">The following example illustrates the use of the multiple-line syntax of the `If`...`Then`...`Else` statement.</span></span>  
  
 [!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="689ed-146">Przykład</span><span class="sxs-lookup"><span data-stu-id="689ed-146">Example</span></span>  
 <span data-ttu-id="689ed-147">Poniższy przykład zawiera zagnieżdżone `If`... `Then`... `Else` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="689ed-147">The following example contains nested `If`...`Then`...`Else` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="689ed-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="689ed-148">Example</span></span>  
 <span data-ttu-id="689ed-149">Poniższy przykład przedstawia użycie składni jeden wiersz.</span><span class="sxs-lookup"><span data-stu-id="689ed-149">The following example illustrates the use of the single-line syntax.</span></span>  
  
 [!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="689ed-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="689ed-150">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Switch%2A>  
 [<span data-ttu-id="689ed-151">#If... Then... #Else — dyrektywy</span><span class="sxs-lookup"><span data-stu-id="689ed-151">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="689ed-152">Wybierz... Case-instrukcja</span><span class="sxs-lookup"><span data-stu-id="689ed-152">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)  
 [<span data-ttu-id="689ed-153">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="689ed-153">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="689ed-154">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="689ed-154">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="689ed-155">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="689ed-155">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [<span data-ttu-id="689ed-156">Jeśli — Operator</span><span class="sxs-lookup"><span data-stu-id="689ed-156">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
