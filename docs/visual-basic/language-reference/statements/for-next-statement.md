---
title: For...Next — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
ms.openlocfilehash: cafd59482036a598814dcd4815fa67a791580045
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046300"
---
# <a name="fornext-statement-visual-basic"></a><span data-ttu-id="034a3-102">For...Next — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="034a3-102">For...Next Statement (Visual Basic)</span></span>

<span data-ttu-id="034a3-103">Powtarza grupę instrukcji określoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="034a3-103">Repeats a group of statements a specified number of times.</span></span>

## <a name="syntax"></a><span data-ttu-id="034a3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="034a3-104">Syntax</span></span>

```
For counter [ As datatype ] = start To end [ Step step ]
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ counter ]
```

## <a name="parts"></a><span data-ttu-id="034a3-105">Części</span><span class="sxs-lookup"><span data-stu-id="034a3-105">Parts</span></span>

|<span data-ttu-id="034a3-106">Części</span><span class="sxs-lookup"><span data-stu-id="034a3-106">Part</span></span>|<span data-ttu-id="034a3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="034a3-107">Description</span></span>|
|----------|-----------------|
|`counter`|<span data-ttu-id="034a3-108">Wymagane w `For` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="034a3-108">Required in the `For` statement.</span></span> <span data-ttu-id="034a3-109">Zmienna numeryczna.</span><span class="sxs-lookup"><span data-stu-id="034a3-109">Numeric variable.</span></span> <span data-ttu-id="034a3-110">Zmienna sterująca pętli.</span><span class="sxs-lookup"><span data-stu-id="034a3-110">The control variable for the loop.</span></span> <span data-ttu-id="034a3-111">Aby uzyskać więcej informacji, zobacz wartość [argumentu Counter](#BKMK_Counter) w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="034a3-111">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`datatype`|<span data-ttu-id="034a3-112">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="034a3-112">Optional.</span></span> <span data-ttu-id="034a3-113">Typ `counter`danych.</span><span class="sxs-lookup"><span data-stu-id="034a3-113">Data type of `counter`.</span></span> <span data-ttu-id="034a3-114">Aby uzyskać więcej informacji, zobacz wartość [argumentu Counter](#BKMK_Counter) w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="034a3-114">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|
|`start`|<span data-ttu-id="034a3-115">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="034a3-115">Required.</span></span> <span data-ttu-id="034a3-116">Wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="034a3-116">Numeric expression.</span></span> <span data-ttu-id="034a3-117">Wartość `counter`początkowa.</span><span class="sxs-lookup"><span data-stu-id="034a3-117">The initial value of `counter`.</span></span>|
|`end`|<span data-ttu-id="034a3-118">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="034a3-118">Required.</span></span> <span data-ttu-id="034a3-119">Wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="034a3-119">Numeric expression.</span></span> <span data-ttu-id="034a3-120">Końcowa wartość parametru `counter`.</span><span class="sxs-lookup"><span data-stu-id="034a3-120">The final value of `counter`.</span></span>|
|`step`|<span data-ttu-id="034a3-121">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="034a3-121">Optional.</span></span> <span data-ttu-id="034a3-122">Wyrażenie liczbowe.</span><span class="sxs-lookup"><span data-stu-id="034a3-122">Numeric expression.</span></span> <span data-ttu-id="034a3-123">Wartość, według której `counter` jest zwiększana za każdym razem przez pętlę.</span><span class="sxs-lookup"><span data-stu-id="034a3-123">The amount by which `counter` is incremented each time through the loop.</span></span>|
|`statements`|<span data-ttu-id="034a3-124">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="034a3-124">Optional.</span></span> <span data-ttu-id="034a3-125">Co najmniej jedna instrukcja między `For` i `Next` , która uruchamia określoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="034a3-125">One or more statements between `For` and `Next` that run the specified number of times.</span></span>|
|`Continue For`|<span data-ttu-id="034a3-126">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="034a3-126">Optional.</span></span> <span data-ttu-id="034a3-127">Przenosi formant do następnej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="034a3-127">Transfers control to the next loop iteration.</span></span>|
|`Exit For`|<span data-ttu-id="034a3-128">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="034a3-128">Optional.</span></span> <span data-ttu-id="034a3-129">Przenosi kontrolę z `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="034a3-129">Transfers control out of the `For` loop.</span></span>|
|`Next`|<span data-ttu-id="034a3-130">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="034a3-130">Required.</span></span> <span data-ttu-id="034a3-131">Kończy definicję `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="034a3-131">Terminates the definition of the `For` loop.</span></span>|

> [!NOTE]
> <span data-ttu-id="034a3-132">`To` Słowo kluczowe jest używane w tej instrukcji, aby określić zakres dla licznika.</span><span class="sxs-lookup"><span data-stu-id="034a3-132">The `To` keyword is used in this statement to specify the range for the counter.</span></span> <span data-ttu-id="034a3-133">Można również użyć słowa kluczowego [SELECT... Instrukcja Case](../../../visual-basic/language-reference/statements/select-case-statement.md) i w deklaracjach tablicowych.</span><span class="sxs-lookup"><span data-stu-id="034a3-133">You can also use this keyword in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) and in array declarations.</span></span> <span data-ttu-id="034a3-134">Aby uzyskać więcej informacji na temat deklaracji tablicowych, zobacz [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="034a3-134">For more information about array declarations, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>

## <a name="simple-examples"></a><span data-ttu-id="034a3-135">Proste przykłady</span><span class="sxs-lookup"><span data-stu-id="034a3-135">Simple Examples</span></span>

<span data-ttu-id="034a3-136">`For`Używasz... `Next` struktura, w której chcesz powtórzyć zestaw instrukcji przez określoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="034a3-136">You use a `For`...`Next` structure when you want to repeat a set of statements a set number of times.</span></span>

<span data-ttu-id="034a3-137">W poniższym przykładzie `index` zmienna rozpoczyna się od wartości 1 i zwiększa się wraz z każdą iteracją pętli, kończąc po `index` wartości osiągnie 5.</span><span class="sxs-lookup"><span data-stu-id="034a3-137">In the following example, the `index` variable starts with a value of 1 and is incremented with each iteration of the loop, ending after the value of `index` reaches 5.</span></span>

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

<span data-ttu-id="034a3-138">W poniższym przykładzie `number` zmienna zaczyna się od 2 i jest zmniejszana o 0,25 dla każdej iteracji pętli, kończąc po `number` wartości osiągnie 0.</span><span class="sxs-lookup"><span data-stu-id="034a3-138">In the following example, the `number` variable starts at 2 and is reduced by 0.25 on each iteration of the loop, ending after the value of `number` reaches 0.</span></span> <span data-ttu-id="034a3-139">`Step` Argumentzmniejszawartośćo0,25`-.25` dla każdej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="034a3-139">The `Step` argument of `-.25` reduces the value by 0.25 on each iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> <span data-ttu-id="034a3-140">A [while... Instrukcja End while](../../../visual-basic/language-reference/statements/while-end-while-statement.md) lub [... Instrukcja Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md) działa prawidłowo, gdy nie wiadomo, ile razy należy uruchomić instrukcje w pętli.</span><span class="sxs-lookup"><span data-stu-id="034a3-140">A [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) or [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) works well when you don't know in advance how many times to run the statements in the loop.</span></span> <span data-ttu-id="034a3-141">Jeśli jednak oczekuje się, że pętla zostanie uruchomiona określoną liczbę razy, a `For`... `Next` pętla jest lepszym wyborem.</span><span class="sxs-lookup"><span data-stu-id="034a3-141">However, when you expect to run the loop a specific number of times, a `For`...`Next` loop is a better choice.</span></span> <span data-ttu-id="034a3-142">Należy określić liczbę iteracji podczas pierwszego wprowadzania pętli.</span><span class="sxs-lookup"><span data-stu-id="034a3-142">You determine the number of iterations when you first enter the loop.</span></span>

## <a name="nesting-loops"></a><span data-ttu-id="034a3-143">Pętle zagnieżdżania</span><span class="sxs-lookup"><span data-stu-id="034a3-143">Nesting Loops</span></span>

<span data-ttu-id="034a3-144">Pętle można `For` zagnieżdżać, umieszczając jedną pętlę w innej.</span><span class="sxs-lookup"><span data-stu-id="034a3-144">You can nest `For` loops by putting one loop within another.</span></span> <span data-ttu-id="034a3-145">W poniższym przykładzie pokazano zagnieżdżonych `For`... `Next` struktury, które mają różne wartości kroków.</span><span class="sxs-lookup"><span data-stu-id="034a3-145">The following example demonstrates nested `For`...`Next` structures that have different step values.</span></span> <span data-ttu-id="034a3-146">Pętla zewnętrzna tworzy ciąg dla każdej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="034a3-146">The outer loop creates a string for every iteration of the loop.</span></span> <span data-ttu-id="034a3-147">Pętla wewnętrzna zmniejsza zmienną licznika pętli dla każdej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="034a3-147">The inner loop decrements a loop counter variable for every iteration of the loop.</span></span>

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

<span data-ttu-id="034a3-148">Podczas zagnieżdżania pętli Każda pętla musi mieć unikatową `counter` zmienną.</span><span class="sxs-lookup"><span data-stu-id="034a3-148">When nesting loops, each loop must have a unique `counter` variable.</span></span>

<span data-ttu-id="034a3-149">Można również zagnieżdżać różne struktury kontroli w obrębie siebie.</span><span class="sxs-lookup"><span data-stu-id="034a3-149">You can also nest different kinds control structures within each other.</span></span> <span data-ttu-id="034a3-150">Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="034a3-150">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>

## <a name="exit-for-and-continue-for"></a><span data-ttu-id="034a3-151">Zamknij i Kontynuuj dla</span><span class="sxs-lookup"><span data-stu-id="034a3-151">Exit For and Continue For</span></span>

<span data-ttu-id="034a3-152">Instrukcja natychmiast opuszcza `For`... `Exit For``Next`</span><span class="sxs-lookup"><span data-stu-id="034a3-152">The `Exit For` statement immediately exits the `For`…`Next`</span></span> <span data-ttu-id="034a3-153">Pętla i przeniesie sterowanie do instrukcji, która `Next` następuje po instrukcji.</span><span class="sxs-lookup"><span data-stu-id="034a3-153">loop and transfers control to the statement that follows the `Next` statement.</span></span>

<span data-ttu-id="034a3-154">`Continue For` Instrukcja natychmiast przenosi kontrolę do następnej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="034a3-154">The `Continue For` statement transfers control immediately to the next iteration of the loop.</span></span> <span data-ttu-id="034a3-155">Aby uzyskać więcej informacji, zobacz [Kontynuacja instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="034a3-155">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>

<span data-ttu-id="034a3-156">Poniższy przykład ilustruje użycie `Continue For` instrukcji i. `Exit For`</span><span class="sxs-lookup"><span data-stu-id="034a3-156">The following example illustrates the use of the `Continue For` and `Exit For` statements.</span></span>

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

<span data-ttu-id="034a3-157">Można umieścić dowolną liczbę `Exit For` instrukcji `For`w...`Next`</span><span class="sxs-lookup"><span data-stu-id="034a3-157">You can put any number of `Exit For` statements in a `For`…`Next`</span></span> <span data-ttu-id="034a3-158">for.</span><span class="sxs-lookup"><span data-stu-id="034a3-158">loop.</span></span> <span data-ttu-id="034a3-159">Używany w zagnieżdżonych `For`...`Next`</span><span class="sxs-lookup"><span data-stu-id="034a3-159">When used within nested `For`…`Next`</span></span> <span data-ttu-id="034a3-160">pętle `Exit For` , opuszcza wewnętrzna pętla i przenosi formant na następny wyższy poziom zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="034a3-160">loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

<span data-ttu-id="034a3-161">`Exit For`jest często używany po dokonaniu oszacowania pewnego warunku (na przykład w `If`... `Then`... `Else` struktura).</span><span class="sxs-lookup"><span data-stu-id="034a3-161">`Exit For` is often used after you evaluate some condition (for example, in an `If`...`Then`...`Else` structure).</span></span> <span data-ttu-id="034a3-162">Może być konieczne użycie `Exit For` następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="034a3-162">You might want to use `Exit For` for the following conditions:</span></span>

- <span data-ttu-id="034a3-163">Kontynuowanie iteracji jest niepotrzebne lub niemożliwe.</span><span class="sxs-lookup"><span data-stu-id="034a3-163">Continuing to iterate is unnecessary or impossible.</span></span> <span data-ttu-id="034a3-164">Wartość błędna lub żądanie zakończenia może stworzyć ten warunek.</span><span class="sxs-lookup"><span data-stu-id="034a3-164">An erroneous value or a termination request might create this condition.</span></span>

- <span data-ttu-id="034a3-165">A `Try`... `Catch`... `Finally` instrukcja przechwytuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="034a3-165">A `Try`...`Catch`...`Finally` statement catches an exception.</span></span> <span data-ttu-id="034a3-166">Możesz użyć `Exit For` na końcu `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="034a3-166">You might use `Exit For` at the end of the `Finally` block.</span></span>

- <span data-ttu-id="034a3-167">Masz nieskończoną pętlę, która jest pętlą, która może uruchamiać dużą lub nawet nieskończoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="034a3-167">You have an endless loop, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="034a3-168">Jeśli wykryjesz taki warunek, możesz użyć `Exit For` , aby wyjść z pętli.</span><span class="sxs-lookup"><span data-stu-id="034a3-168">If you detect such a condition, you can use `Exit For` to escape the loop.</span></span> <span data-ttu-id="034a3-169">Aby uzyskać więcej informacji, zobacz [... Loop — instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="034a3-169">For more information, see [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="034a3-170">Realizacja techniczna</span><span class="sxs-lookup"><span data-stu-id="034a3-170">Technical Implementation</span></span>

<span data-ttu-id="034a3-171">`For`Gdy... zaczyna się pętla, Visual Basic `start`oblicza `end`,, `step`i. `Next`</span><span class="sxs-lookup"><span data-stu-id="034a3-171">When a `For`...`Next` loop starts, Visual Basic evaluates `start`, `end`, and `step`.</span></span> <span data-ttu-id="034a3-172">Visual Basic oblicza te wartości tylko w tym momencie, a następnie `start` przypisuje `counter`do.</span><span class="sxs-lookup"><span data-stu-id="034a3-172">Visual Basic evaluates these values only at this time and then assigns `start` to `counter`.</span></span> <span data-ttu-id="034a3-173">Przed uruchomieniem bloku instrukcji Visual Basic porównuje `counter` z `end`.</span><span class="sxs-lookup"><span data-stu-id="034a3-173">Before the statement block runs, Visual Basic compares `counter` to `end`.</span></span> <span data-ttu-id="034a3-174">Jeśli `counter` jest już większa `end` niż wartość (lub mniejsza, jeśli `step` jest ujemna), `For` pętla kończy się i kontrola przechodzi do instrukcji, która następuje `Next` po instrukcji.</span><span class="sxs-lookup"><span data-stu-id="034a3-174">If `counter` is already larger than the `end` value (or smaller if `step` is negative), the `For` loop ends and control passes to the statement that follows the `Next` statement.</span></span> <span data-ttu-id="034a3-175">W przeciwnym razie blok instrukcji zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="034a3-175">Otherwise, the statement block runs.</span></span>

<span data-ttu-id="034a3-176">Za każdym razem, gdy Visual Basic `Next` napotkają instrukcję `step` , zwiększasięprzeziwracadoinstrukcji.`For` `counter`</span><span class="sxs-lookup"><span data-stu-id="034a3-176">Each time Visual Basic encounters the `Next` statement, it increments `counter` by `step` and returns to the `For` statement.</span></span> <span data-ttu-id="034a3-177">Ponownie porównuje `counter` z `end`, a następnie uruchamia blok lub zamyka pętlę, w zależności od wyniku.</span><span class="sxs-lookup"><span data-stu-id="034a3-177">Again it compares `counter` to `end`, and again it either runs the block or exits the loop, depending on the result.</span></span> <span data-ttu-id="034a3-178">Ten proces jest kontynuowany `end` do momentu `counter` przełączenia lub `Exit For` wykonania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="034a3-178">This process continues until `counter` passes `end` or an `Exit For` statement is encountered.</span></span>

<span data-ttu-id="034a3-179">Pętla nie jest zatrzymywana do `end`momentu `counter` przełączenia.</span><span class="sxs-lookup"><span data-stu-id="034a3-179">The loop doesn't stop until `counter` has passed `end`.</span></span> <span data-ttu-id="034a3-180">Jeśli `counter` jest`end`równe, pętla kontynuuje działanie.</span><span class="sxs-lookup"><span data-stu-id="034a3-180">If `counter` is equal to `end`, the loop continues.</span></span> <span data-ttu-id="034a3-181">Porównanie, które określa, czy ma być uruchamiany blok `counter` , `step` ma  >=  `end` `counter`  <=  `end` wartość dodatnią `step` , a jeśli jest ujemna.</span><span class="sxs-lookup"><span data-stu-id="034a3-181">The comparison that determines whether to run the block is `counter` <= `end` if `step` is positive and `counter` >= `end` if `step` is negative.</span></span>

<span data-ttu-id="034a3-182">Jeśli zmienisz wartość `counter` while wewnątrz pętli, kod może być trudniejszy do odczytania i debugowania.</span><span class="sxs-lookup"><span data-stu-id="034a3-182">If you change the value of `counter` while inside a loop, your code might be more difficult to read and debug.</span></span> <span data-ttu-id="034a3-183">Zmiana wartości `start`, `end`lub `step` nie wpływa na wartości iteracji, które zostały określone podczas pierwszego wprowadzenia pętli.</span><span class="sxs-lookup"><span data-stu-id="034a3-183">Changing the value of `start`, `end`, or `step` doesn't affect the iteration values that were determined when the loop was first entered.</span></span>

<span data-ttu-id="034a3-184">Jeśli zagnieżdżasz pętle, kompilator sygnalizuje błąd, jeśli napotka `Next` instrukcję na zewnętrznym poziomie zagnieżdżenia `Next` przed instrukcją wewnętrznego poziomu.</span><span class="sxs-lookup"><span data-stu-id="034a3-184">If you nest loops, the compiler signals an error if it encounters the `Next` statement of an outer nesting level before the `Next` statement of an inner level.</span></span> <span data-ttu-id="034a3-185">Jednak kompilator może wykryć ten błąd nakładający się tylko wtedy, gdy określisz `counter` w każdej `Next` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="034a3-185">However, the compiler can detect this overlapping error only if you specify `counter` in every `Next` statement.</span></span>

### <a name="step-argument"></a><span data-ttu-id="034a3-186">Argument kroku</span><span class="sxs-lookup"><span data-stu-id="034a3-186">Step Argument</span></span>

<span data-ttu-id="034a3-187">Wartość `step` może być dodatnia lub ujemna.</span><span class="sxs-lookup"><span data-stu-id="034a3-187">The value of `step` can be either positive or negative.</span></span> <span data-ttu-id="034a3-188">Ten parametr określa przetwarzanie pętli zgodnie z poniższą tabelą:</span><span class="sxs-lookup"><span data-stu-id="034a3-188">This parameter determines loop processing according to the following table:</span></span>

|<span data-ttu-id="034a3-189">**Wartość kroku**</span><span class="sxs-lookup"><span data-stu-id="034a3-189">**Step value**</span></span>|<span data-ttu-id="034a3-190">**Pętla jest wykonywana, jeśli**</span><span class="sxs-lookup"><span data-stu-id="034a3-190">**Loop executes if**</span></span>|
|--------------------|--------------------------|
|<span data-ttu-id="034a3-191">Wartość dodatnia lub zero</span><span class="sxs-lookup"><span data-stu-id="034a3-191">Positive or zero</span></span>|`counter` <= `end`|
|<span data-ttu-id="034a3-192">Ujemne</span><span class="sxs-lookup"><span data-stu-id="034a3-192">Negative</span></span>|`counter` >= `end`|

<span data-ttu-id="034a3-193">Wartość `step` domyślna to 1.</span><span class="sxs-lookup"><span data-stu-id="034a3-193">The default value of `step` is 1.</span></span>

### <a name="BKMK_Counter"></a><span data-ttu-id="034a3-194">Argument licznika</span><span class="sxs-lookup"><span data-stu-id="034a3-194">Counter Argument</span></span>

<span data-ttu-id="034a3-195">Poniższa tabela wskazuje, `counter` czy definiuje nową zmienną lokalną, która jest objęta zakresem `For…Next` całej pętli.</span><span class="sxs-lookup"><span data-stu-id="034a3-195">The following table indicates whether `counter` defines a new local variable that’s scoped to the entire `For…Next` loop.</span></span> <span data-ttu-id="034a3-196">To określenie zależy od tego, `datatype` czy jest obecne i `counter` czy jest już zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="034a3-196">This determination depends on whether `datatype` is present and whether `counter` is already defined.</span></span>

|<span data-ttu-id="034a3-197">Czy `datatype` istnieje?</span><span class="sxs-lookup"><span data-stu-id="034a3-197">Is `datatype` present?</span></span>|<span data-ttu-id="034a3-198">Czy `counter` jest już zdefiniowany?</span><span class="sxs-lookup"><span data-stu-id="034a3-198">Is `counter` already defined?</span></span>|<span data-ttu-id="034a3-199">Wynik (czy `counter` definiuje nową zmienną lokalną, która jest objęta zakresem całej `For...Next` pętli)</span><span class="sxs-lookup"><span data-stu-id="034a3-199">Result (whether `counter` defines a new local variable that’s scoped to the entire `For...Next` loop)</span></span>|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|<span data-ttu-id="034a3-200">Nie</span><span class="sxs-lookup"><span data-stu-id="034a3-200">No</span></span>|<span data-ttu-id="034a3-201">Tak</span><span class="sxs-lookup"><span data-stu-id="034a3-201">Yes</span></span>|<span data-ttu-id="034a3-202">Nie, ponieważ `counter` jest już zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="034a3-202">No, because `counter` is already defined.</span></span> <span data-ttu-id="034a3-203">Jeśli zakres `counter` nie jest lokalny dla procedury, występuje ostrzeżenie w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="034a3-203">If the scope of `counter` isn't local to the procedure, a compile-time warning occurs.</span></span>|
|<span data-ttu-id="034a3-204">Nie</span><span class="sxs-lookup"><span data-stu-id="034a3-204">No</span></span>|<span data-ttu-id="034a3-205">Nie</span><span class="sxs-lookup"><span data-stu-id="034a3-205">No</span></span>|<span data-ttu-id="034a3-206">Tak.</span><span class="sxs-lookup"><span data-stu-id="034a3-206">Yes.</span></span> <span data-ttu-id="034a3-207">Typ danych jest wywnioskowany na podstawie `start`wyrażeń, `end`i. `step`</span><span class="sxs-lookup"><span data-stu-id="034a3-207">The data type is inferred from the `start`, `end`, and `step` expressions.</span></span> <span data-ttu-id="034a3-208">Aby uzyskać informacje na temat wnioskowania o typie, zobacz [instrukcja SELECT](../../../visual-basic/language-reference/statements/option-infer-statement.md) i [wnioskowanie typu lokalnego](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="034a3-208">For information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>|
|<span data-ttu-id="034a3-209">Tak</span><span class="sxs-lookup"><span data-stu-id="034a3-209">Yes</span></span>|<span data-ttu-id="034a3-210">Tak</span><span class="sxs-lookup"><span data-stu-id="034a3-210">Yes</span></span>|<span data-ttu-id="034a3-211">Tak, ale tylko wtedy, gdy `counter` istniejąca zmienna jest zdefiniowana poza procedurą.</span><span class="sxs-lookup"><span data-stu-id="034a3-211">Yes, but only if the existing `counter` variable is defined outside the procedure.</span></span> <span data-ttu-id="034a3-212">Ta zmienna pozostaje oddzielona.</span><span class="sxs-lookup"><span data-stu-id="034a3-212">That variable remains separate.</span></span> <span data-ttu-id="034a3-213">Jeśli zakres istniejącej `counter` zmiennej jest lokalny dla procedury, wystąpi błąd w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="034a3-213">If the scope of the existing `counter` variable is local to the procedure, a compile-time error occurs.</span></span>|
|<span data-ttu-id="034a3-214">Tak</span><span class="sxs-lookup"><span data-stu-id="034a3-214">Yes</span></span>|<span data-ttu-id="034a3-215">Nie</span><span class="sxs-lookup"><span data-stu-id="034a3-215">No</span></span>|<span data-ttu-id="034a3-216">Tak.</span><span class="sxs-lookup"><span data-stu-id="034a3-216">Yes.</span></span>|

<span data-ttu-id="034a3-217">Typ `counter` danych określa typ iteracji, który musi być jednym z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="034a3-217">The data type of `counter` determines the type of the iteration, which must be one of the following types:</span></span>

- <span data-ttu-id="034a3-218">A `Byte`, `SByte`, ,`UShort` ,,`Decimal`, ,`ULong`,, lub`Double`. `Short` `UInteger` `Integer` `Long` `Single`</span><span class="sxs-lookup"><span data-stu-id="034a3-218">A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.</span></span>

- <span data-ttu-id="034a3-219">Wyliczenie zadeklarowane za pomocą [instrukcji enum](../../../visual-basic/language-reference/statements/enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="034a3-219">An enumeration that you declare by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>

- <span data-ttu-id="034a3-220">A `Object`.</span><span class="sxs-lookup"><span data-stu-id="034a3-220">An `Object`.</span></span>

- <span data-ttu-id="034a3-221">Typ `T` , który ma następujące operatory, gdzie `B` jest typem, który `Boolean` może być używany w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="034a3-221">A type `T` that has the following operators, where `B` is a type that can be used in a `Boolean` expression.</span></span>

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

<span data-ttu-id="034a3-222">Opcjonalnie możesz określić `counter` zmienną `Next` w instrukcji.</span><span class="sxs-lookup"><span data-stu-id="034a3-222">You can optionally specify the `counter` variable in the `Next` statement.</span></span> <span data-ttu-id="034a3-223">Ta składnia zwiększa czytelność programu, zwłaszcza jeśli istnieją zagnieżdżone `For` pętle.</span><span class="sxs-lookup"><span data-stu-id="034a3-223">This syntax improves the readability of your program, especially if you have nested `For` loops.</span></span> <span data-ttu-id="034a3-224">Należy określić zmienną, która pojawia się w odpowiedniej `For` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="034a3-224">You must specify the variable that appears in the corresponding `For` statement.</span></span>

<span data-ttu-id="034a3-225">Wyrażenia `start` `counter`, `end`i mogąbyćocenianedodowolnegotypudanych,któryjestrozszerzanydotypu.`step`</span><span class="sxs-lookup"><span data-stu-id="034a3-225">The `start`, `end`, and `step` expressions can evaluate to any data type that widens to the type of `counter`.</span></span> <span data-ttu-id="034a3-226">Jeśli używasz `counter`typu zdefiniowanego przez użytkownika dla, może być konieczne `CType` zdefiniowanie operatora konwersji, `start`aby przekonwertować typy, `end`lub `step` na typ `counter`.</span><span class="sxs-lookup"><span data-stu-id="034a3-226">If you use a user-defined type for `counter`, you might have to define the `CType` conversion operator to convert the types of `start`, `end`, or `step` to the type of `counter`.</span></span>

## <a name="example"></a><span data-ttu-id="034a3-227">Przykład</span><span class="sxs-lookup"><span data-stu-id="034a3-227">Example</span></span>

<span data-ttu-id="034a3-228">Poniższy przykład usuwa wszystkie elementy z listy ogólnej.</span><span class="sxs-lookup"><span data-stu-id="034a3-228">The following example removes all elements from a generic list.</span></span> <span data-ttu-id="034a3-229">Zamiast [dla każdego... Next](../../../visual-basic/language-reference/statements/for-each-next-statement.md), przykład pokazuje `For`... `Next` instrukcja, która iteruje w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="034a3-229">Instead of a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md), the example shows a `For`...`Next` statement that iterates in descending order.</span></span> <span data-ttu-id="034a3-230">W przykładzie zastosowano tę technikę `removeAt` , ponieważ metoda powoduje, że elementy po usuniętym elemencie mają niższą wartość indeksu.</span><span class="sxs-lookup"><span data-stu-id="034a3-230">The example uses this technique because the `removeAt` method causes elements after the removed element to have a lower index value.</span></span>

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a><span data-ttu-id="034a3-231">Przykład</span><span class="sxs-lookup"><span data-stu-id="034a3-231">Example</span></span>

<span data-ttu-id="034a3-232">Poniższy przykład wykonuje iterację przez Wyliczenie zadeklarowane za pomocą [instrukcji enum](../../../visual-basic/language-reference/statements/enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="034a3-232">The following example iterates through an enumeration that's declared by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a><span data-ttu-id="034a3-233">Przykład</span><span class="sxs-lookup"><span data-stu-id="034a3-233">Example</span></span>

<span data-ttu-id="034a3-234">W poniższym przykładzie parametry instrukcji używają klasy, która ma `+`przeciążenia operatora dla operatorów, `-`, `>=`i `<=` .</span><span class="sxs-lookup"><span data-stu-id="034a3-234">In the following example, the statement parameters use a class that has operator overloads for the `+`, `-`, `>=`, and `<=` operators.</span></span>

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a><span data-ttu-id="034a3-235">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="034a3-235">See also</span></span>

- <xref:System.Collections.Generic.List%601>
- [<span data-ttu-id="034a3-236">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="034a3-236">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="034a3-237">While...End While, instrukcja</span><span class="sxs-lookup"><span data-stu-id="034a3-237">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [<span data-ttu-id="034a3-238">Do...Loop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="034a3-238">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="034a3-239">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="034a3-239">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="034a3-240">Exit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="034a3-240">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="034a3-241">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="034a3-241">Collections</span></span>](../../programming-guide/concepts/collections.md)
