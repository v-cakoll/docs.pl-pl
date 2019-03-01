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
ms.openlocfilehash: c7c7987508260a0181904feacf3782f66066309f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968208"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="334ff-102">Do...Loop — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="334ff-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="334ff-103">Powtarza blok instrukcji podczas `Boolean` warunek jest `True` lub dopóki warunek przestaje być `True`.</span><span class="sxs-lookup"><span data-stu-id="334ff-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="334ff-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="334ff-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="334ff-105">Części</span><span class="sxs-lookup"><span data-stu-id="334ff-105">Parts</span></span>  
  
|<span data-ttu-id="334ff-106">Termin</span><span class="sxs-lookup"><span data-stu-id="334ff-106">Term</span></span>|<span data-ttu-id="334ff-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="334ff-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="334ff-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="334ff-108">Required.</span></span> <span data-ttu-id="334ff-109">Uruchamia definicji `Do` pętli.</span><span class="sxs-lookup"><span data-stu-id="334ff-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="334ff-110">Wymagane, chyba że `Until` jest używany.</span><span class="sxs-lookup"><span data-stu-id="334ff-110">Required unless `Until` is used.</span></span> <span data-ttu-id="334ff-111">Powtórz pętli do `condition` jest `False`.</span><span class="sxs-lookup"><span data-stu-id="334ff-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="334ff-112">Wymagane, chyba że `While` jest używany.</span><span class="sxs-lookup"><span data-stu-id="334ff-112">Required unless `While` is used.</span></span> <span data-ttu-id="334ff-113">Powtórz pętli do `condition` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="334ff-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="334ff-114">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="334ff-114">Optional.</span></span> <span data-ttu-id="334ff-115">`Boolean` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="334ff-115">`Boolean` expression.</span></span> <span data-ttu-id="334ff-116">Jeśli `condition` jest `Nothing`, Visual Basic traktuje je jako `False`.</span><span class="sxs-lookup"><span data-stu-id="334ff-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="334ff-117">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="334ff-117">Optional.</span></span> <span data-ttu-id="334ff-118">Jedna lub więcej instrukcji, które są powtarzane while lub do momentu, `condition` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="334ff-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="334ff-119">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="334ff-119">Optional.</span></span> <span data-ttu-id="334ff-120">Przekazuje sterowanie do następnej iteracji `Do` pętli.</span><span class="sxs-lookup"><span data-stu-id="334ff-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="334ff-121">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="334ff-121">Optional.</span></span> <span data-ttu-id="334ff-122">Przekazuje sterowanie poza `Do` pętli.</span><span class="sxs-lookup"><span data-stu-id="334ff-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="334ff-123">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="334ff-123">Required.</span></span> <span data-ttu-id="334ff-124">Kończy definicję `Do` pętli.</span><span class="sxs-lookup"><span data-stu-id="334ff-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="334ff-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="334ff-125">Remarks</span></span>  
 <span data-ttu-id="334ff-126">Użyj `Do...Loop` struktury, gdy chcesz powtórzyć zbiór instrukcji na nieokreśloną liczbę razy, dopóki nie zostanie spełniony jakiś warunek.</span><span class="sxs-lookup"><span data-stu-id="334ff-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="334ff-127">Jeśli chcesz powtórzyć oświadczeń określona liczba razy, [dla... Następna instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md) zazwyczaj jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="334ff-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="334ff-128">Można użyć dowolnego `While` lub `Until` do określenia `condition`, ale nie oba jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="334ff-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="334ff-129">Możesz przetestować `condition` tylko jeden raz na początku lub końcu pętli.</span><span class="sxs-lookup"><span data-stu-id="334ff-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="334ff-130">Jeśli testujesz `condition` przy uruchamianiu pętli (w `Do` instrukcji), pętla nie mogą być uruchamiane jeszcze raz.</span><span class="sxs-lookup"><span data-stu-id="334ff-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="334ff-131">Jeśli test na końcu pętli (w `Loop` instrukcji), pętla zawsze działa co najmniej jeden raz.</span><span class="sxs-lookup"><span data-stu-id="334ff-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="334ff-132">Warunek jest zazwyczaj wynikiem porównania dwóch wartości, ale może być dowolne wyrażenie, które daje w wyniku [typ danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) wartość (`True` lub `False`).</span><span class="sxs-lookup"><span data-stu-id="334ff-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="334ff-133">Obejmuje to wartości inne typy danych, takich jak typy liczbowe, które zostały przekonwertowane na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="334ff-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="334ff-134">Można zagnieżdżać `Do` pętli przez umieszczenie pętli w innym.</span><span class="sxs-lookup"><span data-stu-id="334ff-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="334ff-135">Można także zagnieżdżać różne rodzaje struktur sterujących wewnątrz innych.</span><span class="sxs-lookup"><span data-stu-id="334ff-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="334ff-136">Aby uzyskać więcej informacji, zobacz [zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="334ff-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="334ff-137">`Do...Loop` Struktura zapewnia większą elastyczność niż [podczas... End While-instrukcja](../../../visual-basic/language-reference/statements/while-end-while-statement.md) , ponieważ pozwala zdecydować, czy do zakończenia pętli po `condition` przestanie być `True` lub po raz pierwszy staje się `True`.</span><span class="sxs-lookup"><span data-stu-id="334ff-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="334ff-138">Można również do testowania `condition` na początku lub końcu pętli.</span><span class="sxs-lookup"><span data-stu-id="334ff-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="334ff-139">Zakończ</span><span class="sxs-lookup"><span data-stu-id="334ff-139">Exit Do</span></span>  
 <span data-ttu-id="334ff-140">[Należy zamknąć](../../../visual-basic/language-reference/statements/exit-statement.md) instrukcji może zapewnić alternatywny sposób, aby zakończyć działanie `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="334ff-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="334ff-141">`Exit Do` natychmiast przekazuje sterowanie do instrukcji następującej `Loop` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="334ff-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="334ff-142">`Exit Do` jest często używana po ocenieniu jakiś warunek, na przykład w `If...Then...Else` struktury.</span><span class="sxs-lookup"><span data-stu-id="334ff-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="334ff-143">Można zamknąć pętli, jeśli wykryje warunek, który sprawia, że niepotrzebnych lub niemożliwe kontynuować, iteracja, np. Błędna wartość lub żądanie zakończenia działania.</span><span class="sxs-lookup"><span data-stu-id="334ff-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="334ff-144">Jednym z zastosowań `Exit Do` służy do testowania dla warunku, który może powodować *nieskończoną pętlę*, czyli pętlę, która może działać dużych lub nawet nieskończona liczba prób.</span><span class="sxs-lookup"><span data-stu-id="334ff-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="334ff-145">Możesz użyć `Exit Do` jako znak ucieczki dla pętli.</span><span class="sxs-lookup"><span data-stu-id="334ff-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="334ff-146">Może zawierać dowolną liczbę `Exit Do` instrukcji w `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="334ff-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="334ff-147">Gdy jest używana w ramach zagnieżdżonych `Do` pętli, `Exit Do` przenosi sterowanie na dostęp do najaktualniejszych najbardziej wewnętrznej i do następnego wyższy poziom zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="334ff-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="334ff-148">Przykład</span><span class="sxs-lookup"><span data-stu-id="334ff-148">Example</span></span>  
 <span data-ttu-id="334ff-149">W poniższym przykładzie instrukcje w pętli nadal działać do momentu `index` zmiennej jest większa niż 10.</span><span class="sxs-lookup"><span data-stu-id="334ff-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="334ff-150">`Until` Klauzula jest na końcu pętli.</span><span class="sxs-lookup"><span data-stu-id="334ff-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="334ff-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="334ff-151">Example</span></span>  
 <span data-ttu-id="334ff-152">W poniższym przykładzie użyto `While` klauzuli zamiast `Until` klauzuli i `condition` jest testowany na początku pętli, zamiast na końcu.</span><span class="sxs-lookup"><span data-stu-id="334ff-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="334ff-153">Przykład</span><span class="sxs-lookup"><span data-stu-id="334ff-153">Example</span></span>  
 <span data-ttu-id="334ff-154">W poniższym przykładzie `condition` pętla zatrzymuje się podczas `index` zmiennej jest większa niż 100.</span><span class="sxs-lookup"><span data-stu-id="334ff-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="334ff-155">`If` Instrukcji w pętli, jednak powoduje `Exit Do` instrukcję, aby zatrzymanie pętli, gdy zmienna index jest większy niż 10.</span><span class="sxs-lookup"><span data-stu-id="334ff-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="334ff-156">Przykład</span><span class="sxs-lookup"><span data-stu-id="334ff-156">Example</span></span>  
 <span data-ttu-id="334ff-157">Poniższy przykład odczytuje wszystkie wiersze w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="334ff-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="334ff-158"><xref:System.IO.File.OpenText%2A> Metoda otwiera plik i zwraca <xref:System.IO.StreamReader> , odczytuje znaki.</span><span class="sxs-lookup"><span data-stu-id="334ff-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="334ff-159">W `Do...Loop` warunku <xref:System.IO.StreamReader.Peek%2A> metody `StreamReader` Określa, czy istnieją dodatkowe znaki.</span><span class="sxs-lookup"><span data-stu-id="334ff-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="334ff-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="334ff-160">See also</span></span>
- [<span data-ttu-id="334ff-161">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="334ff-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="334ff-162">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="334ff-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="334ff-163">Boolean, typ danych</span><span class="sxs-lookup"><span data-stu-id="334ff-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="334ff-164">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="334ff-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="334ff-165">Exit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="334ff-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="334ff-166">While...End While, instrukcja</span><span class="sxs-lookup"><span data-stu-id="334ff-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
