---
title: Do...Loop — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: 3ff3d67f38f510b798da3e470de066cff1e98f29
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826044"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="f186e-102">Do...Loop — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f186e-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="f186e-103">Powtarza blok instrukcji podczas `Boolean` warunek jest `True` lub dopóki warunek przestaje być `True`.</span><span class="sxs-lookup"><span data-stu-id="f186e-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f186e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f186e-104">Syntax</span></span>  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="f186e-105">Części</span><span class="sxs-lookup"><span data-stu-id="f186e-105">Parts</span></span>  
  
|<span data-ttu-id="f186e-106">Termin</span><span class="sxs-lookup"><span data-stu-id="f186e-106">Term</span></span>|<span data-ttu-id="f186e-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="f186e-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="f186e-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f186e-108">Required.</span></span> <span data-ttu-id="f186e-109">Uruchamia definicji `Do` pętli.</span><span class="sxs-lookup"><span data-stu-id="f186e-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="f186e-110">Wymagane, chyba że `Until` jest używany.</span><span class="sxs-lookup"><span data-stu-id="f186e-110">Required unless `Until` is used.</span></span> <span data-ttu-id="f186e-111">Powtórz pętli do `condition` jest `False`.</span><span class="sxs-lookup"><span data-stu-id="f186e-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="f186e-112">Wymagane, chyba że `While` jest używany.</span><span class="sxs-lookup"><span data-stu-id="f186e-112">Required unless `While` is used.</span></span> <span data-ttu-id="f186e-113">Powtórz pętli do `condition` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="f186e-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="f186e-114">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="f186e-114">Optional.</span></span> <span data-ttu-id="f186e-115">`Boolean` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="f186e-115">`Boolean` expression.</span></span> <span data-ttu-id="f186e-116">Jeśli `condition` jest `Nothing`, Visual Basic traktuje je jako `False`.</span><span class="sxs-lookup"><span data-stu-id="f186e-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="f186e-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="f186e-117">Optional.</span></span> <span data-ttu-id="f186e-118">Jedna lub więcej instrukcji, które są powtarzane while lub do momentu, `condition` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="f186e-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="f186e-119">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="f186e-119">Optional.</span></span> <span data-ttu-id="f186e-120">Przekazuje sterowanie do następnej iteracji `Do` pętli.</span><span class="sxs-lookup"><span data-stu-id="f186e-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="f186e-121">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="f186e-121">Optional.</span></span> <span data-ttu-id="f186e-122">Przekazuje sterowanie poza `Do` pętli.</span><span class="sxs-lookup"><span data-stu-id="f186e-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="f186e-123">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f186e-123">Required.</span></span> <span data-ttu-id="f186e-124">Kończy definicję `Do` pętli.</span><span class="sxs-lookup"><span data-stu-id="f186e-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f186e-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f186e-125">Remarks</span></span>  
 <span data-ttu-id="f186e-126">Użyj `Do...Loop` struktury, gdy chcesz powtórzyć zbiór instrukcji na nieokreśloną liczbę razy, dopóki nie zostanie spełniony jakiś warunek.</span><span class="sxs-lookup"><span data-stu-id="f186e-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="f186e-127">Jeśli chcesz powtórzyć oświadczeń określona liczba razy, [dla... Następna instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md) zazwyczaj jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="f186e-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="f186e-128">Można użyć dowolnego `While` lub `Until` do określenia `condition`, ale nie oba jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="f186e-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="f186e-129">Możesz przetestować `condition` tylko jeden raz na początku lub końcu pętli.</span><span class="sxs-lookup"><span data-stu-id="f186e-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="f186e-130">Jeśli testujesz `condition` przy uruchamianiu pętli (w `Do` instrukcji), pętla nie mogą być uruchamiane jeszcze raz.</span><span class="sxs-lookup"><span data-stu-id="f186e-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="f186e-131">Jeśli test na końcu pętli (w `Loop` instrukcji), pętla zawsze działa co najmniej jeden raz.</span><span class="sxs-lookup"><span data-stu-id="f186e-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="f186e-132">Warunek jest zazwyczaj wynikiem porównania dwóch wartości, ale może być dowolne wyrażenie, które daje w wyniku [typ danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) wartość (`True` lub `False`).</span><span class="sxs-lookup"><span data-stu-id="f186e-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="f186e-133">Obejmuje to wartości inne typy danych, takich jak typy liczbowe, które zostały przekonwertowane na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="f186e-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="f186e-134">Można zagnieżdżać `Do` pętli przez umieszczenie pętli w innym.</span><span class="sxs-lookup"><span data-stu-id="f186e-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="f186e-135">Można także zagnieżdżać różne rodzaje struktur sterujących wewnątrz innych.</span><span class="sxs-lookup"><span data-stu-id="f186e-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="f186e-136">Aby uzyskać więcej informacji, zobacz [zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="f186e-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f186e-137">`Do...Loop` Struktura zapewnia większą elastyczność niż [podczas... End While-instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md) , ponieważ pozwala zdecydować, czy do zakończenia pętli po `condition` przestanie być `True` lub po raz pierwszy staje się `True`.</span><span class="sxs-lookup"><span data-stu-id="f186e-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="f186e-138">Można również do testowania `condition` na początku lub końcu pętli.</span><span class="sxs-lookup"><span data-stu-id="f186e-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="f186e-139">Zakończ</span><span class="sxs-lookup"><span data-stu-id="f186e-139">Exit Do</span></span>  
 <span data-ttu-id="f186e-140">[Należy zamknąć](../../../visual-basic/language-reference/statements/exit-statement.md) instrukcji może zapewnić alternatywny sposób, aby zakończyć działanie `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="f186e-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="f186e-141">`Exit Do` natychmiast przekazuje sterowanie do instrukcji następującej `Loop` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f186e-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="f186e-142">`Exit Do` jest często używana po ocenieniu jakiś warunek, na przykład w `If...Then...Else` struktury.</span><span class="sxs-lookup"><span data-stu-id="f186e-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="f186e-143">Można zamknąć pętli, jeśli wykryje warunek, który sprawia, że niepotrzebnych lub niemożliwe kontynuować, iteracja, np. Błędna wartość lub żądanie zakończenia działania.</span><span class="sxs-lookup"><span data-stu-id="f186e-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="f186e-144">Jednym z zastosowań `Exit Do` służy do testowania dla warunku, który może powodować *nieskończoną pętlę*, czyli pętlę, która może działać dużych lub nawet nieskończona liczba prób.</span><span class="sxs-lookup"><span data-stu-id="f186e-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="f186e-145">Możesz użyć `Exit Do` jako znak ucieczki dla pętli.</span><span class="sxs-lookup"><span data-stu-id="f186e-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="f186e-146">Może zawierać dowolną liczbę `Exit Do` instrukcji w `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="f186e-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="f186e-147">Gdy jest używana w ramach zagnieżdżonych `Do` pętli, `Exit Do` przenosi sterowanie na dostęp do najaktualniejszych najbardziej wewnętrznej i do następnego wyższy poziom zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="f186e-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f186e-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="f186e-148">Example</span></span>  
 <span data-ttu-id="f186e-149">W poniższym przykładzie instrukcje w pętli nadal działać do momentu `index` zmiennej jest większa niż 10.</span><span class="sxs-lookup"><span data-stu-id="f186e-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="f186e-150">`Until` Klauzula jest na końcu pętli.</span><span class="sxs-lookup"><span data-stu-id="f186e-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="f186e-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="f186e-151">Example</span></span>  
 <span data-ttu-id="f186e-152">W poniższym przykładzie użyto `While` klauzuli zamiast `Until` klauzuli i `condition` jest testowany na początku pętli, zamiast na końcu.</span><span class="sxs-lookup"><span data-stu-id="f186e-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="f186e-153">Przykład</span><span class="sxs-lookup"><span data-stu-id="f186e-153">Example</span></span>  
 <span data-ttu-id="f186e-154">W poniższym przykładzie `condition` pętla zatrzymuje się podczas `index` zmiennej jest większa niż 100.</span><span class="sxs-lookup"><span data-stu-id="f186e-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="f186e-155">`If` Instrukcji w pętli, jednak powoduje `Exit Do` instrukcję, aby zatrzymanie pętli, gdy zmienna index jest większy niż 10.</span><span class="sxs-lookup"><span data-stu-id="f186e-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="f186e-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="f186e-156">Example</span></span>  
 <span data-ttu-id="f186e-157">Poniższy przykład odczytuje wszystkie wiersze w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="f186e-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="f186e-158"><xref:System.IO.File.OpenText%2A> Metoda otwiera plik i zwraca <xref:System.IO.StreamReader> , odczytuje znaki.</span><span class="sxs-lookup"><span data-stu-id="f186e-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="f186e-159">W `Do...Loop` warunku <xref:System.IO.StreamReader.Peek%2A> metody `StreamReader` Określa, czy istnieją dodatkowe znaki.</span><span class="sxs-lookup"><span data-stu-id="f186e-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="f186e-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f186e-160">See also</span></span>

- [<span data-ttu-id="f186e-161">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="f186e-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="f186e-162">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f186e-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="f186e-163">Boolean, typ danych</span><span class="sxs-lookup"><span data-stu-id="f186e-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="f186e-164">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="f186e-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="f186e-165">Exit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f186e-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="f186e-166">While...End While, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f186e-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
