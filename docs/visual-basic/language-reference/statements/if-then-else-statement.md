---
title: If...Then...Else, instrukcja
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
ms.openlocfilehash: 0884b71c24742286e695e720add9d00dd4bfe52b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404592"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="f1b32-102">If...Then...Else — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1b32-102">If...Then...Else Statement (Visual Basic)</span></span>

<span data-ttu-id="f1b32-103">Warunkowo wykonuje grupy poleceń w zależności od wartości wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f1b32-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="f1b32-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f1b32-104">Syntax</span></span>

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

## <a name="quick-links-to-example-code"></a><span data-ttu-id="f1b32-105">Szybkie linki do przykładowego kodu</span><span class="sxs-lookup"><span data-stu-id="f1b32-105">Quick links to example code</span></span>

<span data-ttu-id="f1b32-106">Ten artykuł zawiera kilka przykładów ilustrujących zastosowanie `If` ... `Then` ...`Else` Merge</span><span class="sxs-lookup"><span data-stu-id="f1b32-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

- [<span data-ttu-id="f1b32-107">Przykład składni wielowierszowej</span><span class="sxs-lookup"><span data-stu-id="f1b32-107">Multiline syntax example</span></span>](#multi-line)
- [<span data-ttu-id="f1b32-108">Przykład zagnieżdżonej składni</span><span class="sxs-lookup"><span data-stu-id="f1b32-108">Nested syntax example</span></span>](#nested)
- [<span data-ttu-id="f1b32-109">Przykład składni jednowierszowej</span><span class="sxs-lookup"><span data-stu-id="f1b32-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="f1b32-110">Części</span><span class="sxs-lookup"><span data-stu-id="f1b32-110">Parts</span></span>

`condition` \
<span data-ttu-id="f1b32-111">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f1b32-111">Required.</span></span> <span data-ttu-id="f1b32-112">Wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f1b32-112">Expression.</span></span> <span data-ttu-id="f1b32-113">Należy oszacować do `True` lub `False` , lub do typu danych, który jest niejawnie konwertowany na `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="f1b32-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

<span data-ttu-id="f1b32-114">Jeśli wyrażenie jest zmienną [dopuszczającą wartość null](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` , która zwraca wartość [Nothing](../nothing.md), warunek jest traktowany tak, jakby wyrażenie ma wartość `False` , a `ElseIf` bloki są oceniane, jeśli istnieją, lub `Else` Jeśli blok jest wykonywany, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="f1b32-114">If the expression is a [Nullable](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../nothing.md), the condition is treated as if the expression is `False`, and the `ElseIf` blocks are evaluated if they exist, or the `Else` block is executed if it exists.</span></span>

`Then` \
<span data-ttu-id="f1b32-115">Wymagane w składni jednowierszowej; opcjonalne w składni wielowierszowej.</span><span class="sxs-lookup"><span data-stu-id="f1b32-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>

`statements` \
<span data-ttu-id="f1b32-116">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f1b32-116">Optional.</span></span> <span data-ttu-id="f1b32-117">Jedna lub więcej instrukcji `If` `Then` , które są wykonywane, jeśli są `condition` oceniane `True` .</span><span class="sxs-lookup"><span data-stu-id="f1b32-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>

`elseifcondition` \
<span data-ttu-id="f1b32-118">Wymagane, jeśli `ElseIf` jest obecny.</span><span class="sxs-lookup"><span data-stu-id="f1b32-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="f1b32-119">Wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f1b32-119">Expression.</span></span> <span data-ttu-id="f1b32-120">Należy oszacować do `True` lub `False` , lub do typu danych, który jest niejawnie konwertowany na `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="f1b32-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

`elseifstatements` \
<span data-ttu-id="f1b32-121">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f1b32-121">Optional.</span></span> <span data-ttu-id="f1b32-122">Jedna lub więcej instrukcji `ElseIf` `Then` , które są wykonywane, jeśli są `elseifcondition` oceniane `True` .</span><span class="sxs-lookup"><span data-stu-id="f1b32-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>

`elsestatements` \
<span data-ttu-id="f1b32-123">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="f1b32-123">Optional.</span></span> <span data-ttu-id="f1b32-124">Jedna lub więcej instrukcji, które są wykonywane, jeśli nie zostanie `condition` `elseifcondition` obliczone wyrażenie Previous lub `True` .</span><span class="sxs-lookup"><span data-stu-id="f1b32-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>

`End If` \
<span data-ttu-id="f1b32-125">Kończy wielowierszową wersję programu `If` ... `Then` ...`Else` odblokowan.</span><span class="sxs-lookup"><span data-stu-id="f1b32-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="f1b32-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f1b32-126">Remarks</span></span>

### <a name="multiline-syntax"></a><span data-ttu-id="f1b32-127">Składnia wielowierszowa</span><span class="sxs-lookup"><span data-stu-id="f1b32-127">Multiline syntax</span></span>

<span data-ttu-id="f1b32-128">Gdy `If` ... `Then` ...`Else` Napotkano instrukcję, `condition` jest testowana.</span><span class="sxs-lookup"><span data-stu-id="f1b32-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="f1b32-129">Jeśli `condition` jest `True` , `Then` są wykonywane poniższe instrukcje.</span><span class="sxs-lookup"><span data-stu-id="f1b32-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="f1b32-130">Jeśli `condition` jest `False` , każda `ElseIf` instrukcja (jeśli istnieje) jest szacowana w kolejności.</span><span class="sxs-lookup"><span data-stu-id="f1b32-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="f1b32-131">Gdy `True` `elseifcondition` zostanie znaleziony, są wykonywane instrukcje bezpośrednio po skojarzonych z nimi `ElseIf` .</span><span class="sxs-lookup"><span data-stu-id="f1b32-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="f1b32-132">Jeśli `elseifcondition` wartość nie jest równa lub nie ma `True` żadnych `ElseIf` instrukcji, są wykonywane poniższe instrukcje `Else` .</span><span class="sxs-lookup"><span data-stu-id="f1b32-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="f1b32-133">Po wykonaniu instrukcji poniżej `Then` , `ElseIf` lub `Else` , wykonywanie jest kontynuowane przy użyciu instrukcji poniżej `End If` .</span><span class="sxs-lookup"><span data-stu-id="f1b32-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>

<span data-ttu-id="f1b32-134">`ElseIf` `Else` Klauzule i są opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="f1b32-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="f1b32-135">Można utworzyć dowolną liczbę `ElseIf` klauzul w `If` ... `Then` ...`Else` Instrukcja, ale żadna `ElseIf` klauzula nie może występować po `Else` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="f1b32-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="f1b32-136">`If`...`Then` ...`Else` instrukcje mogą być zagnieżdżane w obrębie siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="f1b32-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>

<span data-ttu-id="f1b32-137">W składni wielowierszowej `If` instrukcja musi być jedyną instrukcją w pierwszym wierszu.</span><span class="sxs-lookup"><span data-stu-id="f1b32-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="f1b32-138">`ElseIf`Instrukcje, `Else` i `End If` mogą być poprzedzone tylko etykietą wiersza.</span><span class="sxs-lookup"><span data-stu-id="f1b32-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="f1b32-139">`If`... `Then` ...`Else` blok musi kończyć się `End If` instrukcją.</span><span class="sxs-lookup"><span data-stu-id="f1b32-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>

> [!TIP]
> <span data-ttu-id="f1b32-140">[Wybór... Instrukcja Case](select-case-statement.md) może być bardziej przydatna podczas obliczania pojedynczego wyrażenia, które ma kilka możliwych wartości.</span><span class="sxs-lookup"><span data-stu-id="f1b32-140">The [Select...Case Statement](select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>

### <a name="single-line-syntax"></a><span data-ttu-id="f1b32-141">Składnia jednowierszowa</span><span class="sxs-lookup"><span data-stu-id="f1b32-141">Single-Line syntax</span></span>

<span data-ttu-id="f1b32-142">Można użyć jednowierszowej składni dla jednego warunku z kodem do wykonania, jeśli jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="f1b32-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="f1b32-143">Jednak składnia wielowierszowa zapewnia większą strukturę i elastyczność oraz jest łatwiejsza do odczytania, konserwacji i debugowania.</span><span class="sxs-lookup"><span data-stu-id="f1b32-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>

<span data-ttu-id="f1b32-144">Co następuje po `Then` zbadaniu słowa kluczowego, aby określić, czy instrukcja jest pojedynczą linią `If` .</span><span class="sxs-lookup"><span data-stu-id="f1b32-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="f1b32-145">Jeśli coś innego niż komentarz występuje `Then` w tym samym wierszu, instrukcja jest traktowana jako jednowierszowa `If` instrukcja.</span><span class="sxs-lookup"><span data-stu-id="f1b32-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="f1b32-146">Jeśli `Then` jest nieobecny, musi to być początek wielu wierszy `If` ... `Then` ...`Else`.</span><span class="sxs-lookup"><span data-stu-id="f1b32-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>

<span data-ttu-id="f1b32-147">W składni jednowierszowej można wykonać kilka instrukcji w wyniku `If` ... `Then` decyzja.</span><span class="sxs-lookup"><span data-stu-id="f1b32-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="f1b32-148">Wszystkie instrukcje muszą znajdować się w tym samym wierszu i być rozdzielone średnikami.</span><span class="sxs-lookup"><span data-stu-id="f1b32-148">All statements must be on the same line and be separated by colons.</span></span>

## <a name="multiline-syntax-example"></a><span data-ttu-id="f1b32-149">Przykład składni wielowierszowej</span><span class="sxs-lookup"><span data-stu-id="f1b32-149">Multiline syntax example</span></span>

<a name="multi-line"></a>

<span data-ttu-id="f1b32-150">Poniższy przykład ilustruje użycie składni wielowierszowej `If` ... `Then` ...`Else` Merge.</span><span class="sxs-lookup"><span data-stu-id="f1b32-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a><span data-ttu-id="f1b32-151">Przykład zagnieżdżonej składni</span><span class="sxs-lookup"><span data-stu-id="f1b32-151">Nested syntax example</span></span>

<a name="nested"></a>

<span data-ttu-id="f1b32-152">Poniższy przykład zawiera zagnieżdżonych `If` ... `Then` ...`Else` zatwierdzeni.</span><span class="sxs-lookup"><span data-stu-id="f1b32-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="f1b32-153">Przykład składni jednowierszowej</span><span class="sxs-lookup"><span data-stu-id="f1b32-153">Single-Line syntax example</span></span>

<a name="single-line"></a><span data-ttu-id="f1b32-154">Poniższy przykład ilustruje użycie składni jednowierszowej.</span><span class="sxs-lookup"><span data-stu-id="f1b32-154">The following example illustrates the use of the single-line syntax.</span></span>

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a><span data-ttu-id="f1b32-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f1b32-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="f1b32-156">#If... Then... #Else — dyrektywy</span><span class="sxs-lookup"><span data-stu-id="f1b32-156">#If...Then...#Else Directives</span></span>](../directives/if-then-else-directives.md)
- [<span data-ttu-id="f1b32-157">Select...Case, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f1b32-157">Select...Case Statement</span></span>](select-case-statement.md)
- [<span data-ttu-id="f1b32-158">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="f1b32-158">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="f1b32-159">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="f1b32-159">Decision Structures</span></span>](../../programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="f1b32-160">Operatory logiczne i bitowe w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f1b32-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="f1b32-161">If, operator</span><span class="sxs-lookup"><span data-stu-id="f1b32-161">If Operator</span></span>](../operators/if-operator.md)
