---
title: If...Then...Else — Instrukcja (Visual Basic)
ms.date: 04/16/2018
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
ms.openlocfilehash: d91a913d515f36a6b974850bc30079b000a919b4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61637758"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="24199-102">If...Then...Else — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24199-102">If...Then...Else Statement (Visual Basic)</span></span>
<span data-ttu-id="24199-103">Warunkowo wykonuje grupy poleceń w zależności od wartości wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="24199-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24199-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24199-104">Syntax</span></span>  
  
```  
' Multiline syntax:  
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

## <a name="quick-links-to-example-code"></a><span data-ttu-id="24199-105">Szybkie łącza do przykładowego kodu</span><span class="sxs-lookup"><span data-stu-id="24199-105">Quick links to example code</span></span>

<span data-ttu-id="24199-106">W tym artykule przedstawiono kilka przykładów, które ilustrują zastosowań `If`... `Then`... `Else` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="24199-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

* [<span data-ttu-id="24199-107">Przykład składni wielowierszowy</span><span class="sxs-lookup"><span data-stu-id="24199-107">Multiline syntax example</span></span>](#multi-line)
* [<span data-ttu-id="24199-108">Przykład składni zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="24199-108">Nested syntax example</span></span>](#nested)
* [<span data-ttu-id="24199-109">Przykład składni jednowierszowy</span><span class="sxs-lookup"><span data-stu-id="24199-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="24199-110">Części</span><span class="sxs-lookup"><span data-stu-id="24199-110">Parts</span></span>  
 `condition`  
 <span data-ttu-id="24199-111">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="24199-111">Required.</span></span> <span data-ttu-id="24199-112">wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="24199-112">Expression.</span></span> <span data-ttu-id="24199-113">Musi być `True` lub `False`, lub do typu danych, który jest niejawnie konwertowany na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="24199-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 <span data-ttu-id="24199-114">Jeśli wyrażenie ma [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` zmiennej, która daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md), warunek jest traktowany tak, jakby wyrażenie jest `False` i `Else` blok jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="24199-114">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is `False` and the `Else` block is executed.</span></span>  
  
 `Then`  
 <span data-ttu-id="24199-115">Wymagany w składni pojedynczej linii; Opcjonalnie w wielowierszowym składni.</span><span class="sxs-lookup"><span data-stu-id="24199-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>  
  
 `statements`  
 <span data-ttu-id="24199-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="24199-116">Optional.</span></span> <span data-ttu-id="24199-117">Jeden lub więcej następujących instrukcji `If`... `Then` które są wykonywane, jeśli `condition` daje w wyniku `True`.</span><span class="sxs-lookup"><span data-stu-id="24199-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>  
  
 `elseifcondition`  
 <span data-ttu-id="24199-118">Jeśli wymagane `ElseIf` jest obecny.</span><span class="sxs-lookup"><span data-stu-id="24199-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="24199-119">wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="24199-119">Expression.</span></span> <span data-ttu-id="24199-120">Musi być `True` lub `False`, lub do typu danych, który jest niejawnie konwertowany na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="24199-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 `elseifstatements`  
 <span data-ttu-id="24199-121">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="24199-121">Optional.</span></span> <span data-ttu-id="24199-122">Jeden lub więcej następujących instrukcji `ElseIf`... `Then` które są wykonywane, jeśli `elseifcondition` daje w wyniku `True`.</span><span class="sxs-lookup"><span data-stu-id="24199-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>  
  
 `elsestatements`  
 <span data-ttu-id="24199-123">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="24199-123">Optional.</span></span> <span data-ttu-id="24199-124">Jedna lub więcej instrukcji, które są wykonywane, jeśli nie poprzedniej `condition` lub `elseifcondition` wyrażenie daje w wyniku `True`.</span><span class="sxs-lookup"><span data-stu-id="24199-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>  
  
 `End If`  
 <span data-ttu-id="24199-125">Kończy wielowierszowy wersję `If`... `Then`... `Else` bloku.</span><span class="sxs-lookup"><span data-stu-id="24199-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24199-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24199-126">Remarks</span></span>  
  
### <a name="multiline-syntax"></a><span data-ttu-id="24199-127">Składnia wielowierszowy</span><span class="sxs-lookup"><span data-stu-id="24199-127">Multiline syntax</span></span>  
 <span data-ttu-id="24199-128">Gdy `If`... `Then`... `Else` napotkania instrukcji `condition` jest testowana.</span><span class="sxs-lookup"><span data-stu-id="24199-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="24199-129">Jeśli `condition` jest `True`instrukcje po `Then` są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="24199-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="24199-130">Jeśli `condition` jest `False`, każdy `ElseIf` — instrukcja (jeśli istnieją) jest obliczane w kolejności.</span><span class="sxs-lookup"><span data-stu-id="24199-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="24199-131">Gdy `True` `elseifcondition` zostanie znaleziony, instrukcje natychmiast po skojarzonego `ElseIf` są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="24199-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="24199-132">Jeśli nie `elseifcondition` daje w wyniku `True`, lub jeśli występują nie `ElseIf` instrukcji, instrukcje po `Else` są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="24199-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="24199-133">Po wykonaniu następujących instrukcji `Then`, `ElseIf`, lub `Else`, wykonywanie jest kontynuowane przy użyciu następujących instrukcji `End If`.</span><span class="sxs-lookup"><span data-stu-id="24199-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>  
  
 <span data-ttu-id="24199-134">`ElseIf` i `Else` klauzule są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="24199-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="24199-135">Masz tyle `ElseIf` klauzule jako użytkownik ma `If`... `Then`... `Else` instrukcji, ale nie `ElseIf` klauzuli może następować po elemencie `Else` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="24199-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="24199-136">`If`... `Then`... `Else` instrukcje mogą być zagnieżdżone wewnątrz innych.</span><span class="sxs-lookup"><span data-stu-id="24199-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>  
  
 <span data-ttu-id="24199-137">W składni wielowierszowy `If` instrukcja musi być jedyną instrukcją w pierwszym wierszu.</span><span class="sxs-lookup"><span data-stu-id="24199-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="24199-138">`ElseIf`, `Else`, I `End If` instrukcji może być poprzedzony tylko etykieta wiersza.</span><span class="sxs-lookup"><span data-stu-id="24199-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="24199-139">`If`... `Then`... `Else` bloku musi się kończyć `End If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="24199-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="24199-140">[Wybierz... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md) mogą być bardziej przydatne podczas oceny pojedyncze wyrażenie, które ma kilka możliwych wartości.</span><span class="sxs-lookup"><span data-stu-id="24199-140">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>  
  
### <a name="single-line-syntax"></a><span data-ttu-id="24199-141">Składnia jednowierszowy</span><span class="sxs-lookup"><span data-stu-id="24199-141">Single-Line syntax</span></span>  
 <span data-ttu-id="24199-142">Do wykonania, jeśli to PRAWDA, można użyć składni jeden wiersz dla jednego warunku przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="24199-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="24199-143">Jednak składni wielowierszowe zapewnia więcej struktury i elastyczności i łatwiej odczytać, obsługa i debugowania.</span><span class="sxs-lookup"><span data-stu-id="24199-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>  
  
 <span data-ttu-id="24199-144">Poniżej `Then` — słowo kluczowe jest sprawdzane w celu określenia, czy instrukcja jest jeden wiersz `If`.</span><span class="sxs-lookup"><span data-stu-id="24199-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="24199-145">Jeśli coś innego niż komentarz pojawia się po `Then` w tym samym wierszu, instrukcja jest traktowany jako jeden wiersz `If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="24199-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="24199-146">Jeśli `Then` jest nieobecne, należy go z początku wielu linii `If`... `Then`... `Else`.</span><span class="sxs-lookup"><span data-stu-id="24199-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>  
  
 <span data-ttu-id="24199-147">W składni jednowierszowego, może mieć wiele instrukcji wykonane w wyniku `If`... `Then` decyzji.</span><span class="sxs-lookup"><span data-stu-id="24199-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="24199-148">Wszystkie instrukcje musi znajdować się na tym samym wierszu i być rozdzielone średnikami.</span><span class="sxs-lookup"><span data-stu-id="24199-148">All statements must be on the same line and be separated by colons.</span></span>  

## <a name="multiline-syntax-example"></a><span data-ttu-id="24199-149">Przykład składni wielowierszowy</span><span class="sxs-lookup"><span data-stu-id="24199-149">Multiline syntax example</span></span>

<a name="multi-line"></a>
 
 <span data-ttu-id="24199-150">Poniższy przykład ilustruje użycie składni wielowierszowy `If`... `Then`... `Else` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="24199-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>  
  
 [!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a><span data-ttu-id="24199-151">Przykład składni zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="24199-151">Nested syntax example</span></span>

<a name="nested"></a>

 <span data-ttu-id="24199-152">Poniższy przykład zawiera zagnieżdżone `If`... `Then`... `Else` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="24199-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="24199-153">Przykład składni jednowierszowy</span><span class="sxs-lookup"><span data-stu-id="24199-153">Single-Line syntax example</span></span>
  
<a name="single-line"></a> <span data-ttu-id="24199-154">Poniższy przykład ilustruje użycie składni jeden wiersz.</span><span class="sxs-lookup"><span data-stu-id="24199-154">The following example illustrates the use of the single-line syntax.</span></span>  
  
 [!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]
  
## <a name="see-also"></a><span data-ttu-id="24199-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24199-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="24199-156">#If...Then...#Else, dyrektywy</span><span class="sxs-lookup"><span data-stu-id="24199-156">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="24199-157">Instrukcja Select...Case</span><span class="sxs-lookup"><span data-stu-id="24199-157">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="24199-158">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="24199-158">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="24199-159">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="24199-159">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="24199-160">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24199-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="24199-161">If, operator</span><span class="sxs-lookup"><span data-stu-id="24199-161">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
