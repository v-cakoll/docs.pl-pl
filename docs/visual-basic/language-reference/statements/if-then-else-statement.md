---
title: If...Then...Else — Instrukcja
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
ms.openlocfilehash: f505755caeb9cc3cfeeb1ba83b6de15f48314103
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351162"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="d54af-102">If...Then...Else — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d54af-102">If...Then...Else Statement (Visual Basic)</span></span>

<span data-ttu-id="d54af-103">Warunkowo wykonuje grupy poleceń w zależności od wartości wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d54af-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="d54af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d54af-104">Syntax</span></span>

```vb
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

## <a name="quick-links-to-example-code"></a><span data-ttu-id="d54af-105">Szybkie linki do przykładowego kodu</span><span class="sxs-lookup"><span data-stu-id="d54af-105">Quick links to example code</span></span>

<span data-ttu-id="d54af-106">Ten artykuł zawiera kilka przykładów, które ilustrują zastosowania instrukcji `If`...`Then`...`Else`:</span><span class="sxs-lookup"><span data-stu-id="d54af-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

- [<span data-ttu-id="d54af-107">Przykład składni wielowierszowej</span><span class="sxs-lookup"><span data-stu-id="d54af-107">Multiline syntax example</span></span>](#multi-line)
- [<span data-ttu-id="d54af-108">Przykład zagnieżdżonej składni</span><span class="sxs-lookup"><span data-stu-id="d54af-108">Nested syntax example</span></span>](#nested)
- [<span data-ttu-id="d54af-109">Przykład składni jednowierszowej</span><span class="sxs-lookup"><span data-stu-id="d54af-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="d54af-110">Części</span><span class="sxs-lookup"><span data-stu-id="d54af-110">Parts</span></span>

`condition` \
<span data-ttu-id="d54af-111">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d54af-111">Required.</span></span> <span data-ttu-id="d54af-112">Wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d54af-112">Expression.</span></span> <span data-ttu-id="d54af-113">Należy oszacować do `True` lub `False`lub do typu danych, który jest niejawnie konwertowany do `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d54af-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

<span data-ttu-id="d54af-114">Jeśli wyrażenie jest wartością [null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) zmiennej `Boolean`, która zwraca wartość [Nothing](../../../visual-basic/language-reference/nothing.md), warunek jest traktowany tak, jakby wyrażenie jest `False`, a bloki `ElseIf` są oceniane, jeśli istnieją lub jeśli istnieją, blok `Else` jest wykonywany, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="d54af-114">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is `False`, and the `ElseIf` blocks are evaluated if they exist, or the `Else` block is executed if it exists.</span></span>

`Then` \
<span data-ttu-id="d54af-115">Wymagane w składni jednowierszowej; opcjonalne w składni wielowierszowej.</span><span class="sxs-lookup"><span data-stu-id="d54af-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>

`statements` \
<span data-ttu-id="d54af-116">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d54af-116">Optional.</span></span> <span data-ttu-id="d54af-117">Jedna lub więcej instrukcji po `If`...`Then`, które są wykonywane, jeśli `condition` szacuje się `True`.</span><span class="sxs-lookup"><span data-stu-id="d54af-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>

`elseifcondition` \
<span data-ttu-id="d54af-118">Wymagane, jeśli `ElseIf` jest obecny.</span><span class="sxs-lookup"><span data-stu-id="d54af-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="d54af-119">Wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d54af-119">Expression.</span></span> <span data-ttu-id="d54af-120">Należy oszacować do `True` lub `False`lub do typu danych, który jest niejawnie konwertowany do `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d54af-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

`elseifstatements` \
<span data-ttu-id="d54af-121">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d54af-121">Optional.</span></span> <span data-ttu-id="d54af-122">Jedna lub więcej instrukcji po `ElseIf`...`Then`, które są wykonywane, jeśli `elseifcondition` szacuje się `True`.</span><span class="sxs-lookup"><span data-stu-id="d54af-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>

`elsestatements` \
<span data-ttu-id="d54af-123">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="d54af-123">Optional.</span></span> <span data-ttu-id="d54af-124">Jedna lub więcej instrukcji, które są wykonywane, jeśli żadne poprzednie `condition` lub wyrażenie `elseifcondition` nie zwróci `True`.</span><span class="sxs-lookup"><span data-stu-id="d54af-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>

`End If` \
<span data-ttu-id="d54af-125">Kończy wielowierszową wersję `If`...`Then`...`Else` bloku.</span><span class="sxs-lookup"><span data-stu-id="d54af-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="d54af-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d54af-126">Remarks</span></span>

### <a name="multiline-syntax"></a><span data-ttu-id="d54af-127">Składnia wielowierszowa</span><span class="sxs-lookup"><span data-stu-id="d54af-127">Multiline syntax</span></span>

<span data-ttu-id="d54af-128">Po napotkaniu instrukcji `If`...`Then`...`Else` `condition` jest testowana.</span><span class="sxs-lookup"><span data-stu-id="d54af-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="d54af-129">Jeśli `condition` jest `True`, są wykonywane następujące instrukcje `Then`.</span><span class="sxs-lookup"><span data-stu-id="d54af-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="d54af-130">Jeśli `condition` jest `False`, każda instrukcja `ElseIf` (jeśli istnieje) jest szacowana w kolejności.</span><span class="sxs-lookup"><span data-stu-id="d54af-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="d54af-131">Po znalezieniu `elseifcondition` `True` są wykonywane instrukcje bezpośrednio po skojarzonych `ElseIf`.</span><span class="sxs-lookup"><span data-stu-id="d54af-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="d54af-132">Jeśli żaden `elseifcondition` nie jest obliczany do `True`, lub jeśli nie ma żadnych instrukcji `ElseIf`, są wykonywane następujące instrukcje `Else`.</span><span class="sxs-lookup"><span data-stu-id="d54af-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="d54af-133">Po wykonaniu instrukcji następujących `Then`, `ElseIf`lub `Else`wykonywanie jest kontynuowane przy użyciu instrukcji następujących `End If`.</span><span class="sxs-lookup"><span data-stu-id="d54af-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>

<span data-ttu-id="d54af-134">Klauzule `ElseIf` i `Else` są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="d54af-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="d54af-135">W instrukcji `If`...`Then`...`Else` można utworzyć dowolną liczbę klauzul `ElseIf`, ale po klauzuli `ElseIf` nie może wystąpić żadna klauzula `Else`.</span><span class="sxs-lookup"><span data-stu-id="d54af-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="d54af-136">instrukcje `If`...`Then`...`Else` mogą być zagnieżdżane w obrębie siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="d54af-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>

<span data-ttu-id="d54af-137">W składni wielowierszowej instrukcja `If` musi być jedyną instrukcją w pierwszym wierszu.</span><span class="sxs-lookup"><span data-stu-id="d54af-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="d54af-138">Instrukcje `ElseIf`, `Else`i `End If` mogą być poprzedzone tylko etykietą wiersza.</span><span class="sxs-lookup"><span data-stu-id="d54af-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="d54af-139">Blok `If`...`Then`...`Else` musi kończyć się instrukcją `End If`.</span><span class="sxs-lookup"><span data-stu-id="d54af-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>

> [!TIP]
> <span data-ttu-id="d54af-140">[Wybór... Instrukcja Case](../../../visual-basic/language-reference/statements/select-case-statement.md) może być bardziej przydatna podczas obliczania pojedynczego wyrażenia, które ma kilka możliwych wartości.</span><span class="sxs-lookup"><span data-stu-id="d54af-140">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>

### <a name="single-line-syntax"></a><span data-ttu-id="d54af-141">Składnia jednowierszowa</span><span class="sxs-lookup"><span data-stu-id="d54af-141">Single-Line syntax</span></span>

<span data-ttu-id="d54af-142">Można użyć jednowierszowej składni dla jednego warunku z kodem do wykonania, jeśli jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="d54af-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="d54af-143">Jednak składnia wielowierszowa zapewnia większą strukturę i elastyczność oraz jest łatwiejsza do odczytania, konserwacji i debugowania.</span><span class="sxs-lookup"><span data-stu-id="d54af-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>

<span data-ttu-id="d54af-144">Co następuje po `Then` słowo kluczowe jest badane, aby określić, czy instrukcja jest `If`jednowierszową.</span><span class="sxs-lookup"><span data-stu-id="d54af-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="d54af-145">Jeśli coś innego niż komentarz pojawia się po `Then` w tym samym wierszu, instrukcja jest traktowana jako jednowierszowa instrukcja `If`.</span><span class="sxs-lookup"><span data-stu-id="d54af-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="d54af-146">Jeśli nie ma `Then`, musi to być początek `If`wielu wierszy...`Then`...`Else`.</span><span class="sxs-lookup"><span data-stu-id="d54af-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>

<span data-ttu-id="d54af-147">W składni jednowierszowej można wykonać kilka instrukcji w wyniku `If`...`Then` decyzji.</span><span class="sxs-lookup"><span data-stu-id="d54af-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="d54af-148">Wszystkie instrukcje muszą znajdować się w tym samym wierszu i być rozdzielone średnikami.</span><span class="sxs-lookup"><span data-stu-id="d54af-148">All statements must be on the same line and be separated by colons.</span></span>

## <a name="multiline-syntax-example"></a><span data-ttu-id="d54af-149">Przykład składni wielowierszowej</span><span class="sxs-lookup"><span data-stu-id="d54af-149">Multiline syntax example</span></span>

<a name="multi-line"></a>

<span data-ttu-id="d54af-150">Poniższy przykład ilustruje użycie składni wielowierszowej `If`...`Then`...`Else` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d54af-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a><span data-ttu-id="d54af-151">Przykład zagnieżdżonej składni</span><span class="sxs-lookup"><span data-stu-id="d54af-151">Nested syntax example</span></span>

<a name="nested"></a>

<span data-ttu-id="d54af-152">Poniższy przykład zawiera zagnieżdżonych instrukcji `If`...`Then`...`Else`.</span><span class="sxs-lookup"><span data-stu-id="d54af-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="d54af-153">Przykład składni jednowierszowej</span><span class="sxs-lookup"><span data-stu-id="d54af-153">Single-Line syntax example</span></span>

<a name="single-line"></a><span data-ttu-id="d54af-154">Poniższy przykład ilustruje użycie składni jednowierszowej.</span><span class="sxs-lookup"><span data-stu-id="d54af-154">The following example illustrates the use of the single-line syntax.</span></span>

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a><span data-ttu-id="d54af-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d54af-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="d54af-156">#If...Then...#Else, dyrektywy</span><span class="sxs-lookup"><span data-stu-id="d54af-156">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="d54af-157">Select...Case, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d54af-157">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="d54af-158">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="d54af-158">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="d54af-159">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="d54af-159">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="d54af-160">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d54af-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="d54af-161">If, operator</span><span class="sxs-lookup"><span data-stu-id="d54af-161">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
