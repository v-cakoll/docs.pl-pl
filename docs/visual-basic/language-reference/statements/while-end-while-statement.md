---
title: While...End While — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 9f46a6ec65faef4448bdd25e30a6cc0c605cd0f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="45e3e-102">While...End While — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45e3e-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="45e3e-103">Uruchamia serię instrukcji tak długo, jak jest dany warunek `True`.</span><span class="sxs-lookup"><span data-stu-id="45e3e-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45e3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="45e3e-104">Syntax</span></span>  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="45e3e-105">Części</span><span class="sxs-lookup"><span data-stu-id="45e3e-105">Parts</span></span>  
  
|<span data-ttu-id="45e3e-106">Termin</span><span class="sxs-lookup"><span data-stu-id="45e3e-106">Term</span></span>|<span data-ttu-id="45e3e-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="45e3e-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="45e3e-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="45e3e-108">Required.</span></span> <span data-ttu-id="45e3e-109">`Boolean` Wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="45e3e-109">`Boolean` expression.</span></span> <span data-ttu-id="45e3e-110">Jeśli `condition` jest `Nothing`, Visual Basic traktuje ją jako `False`.</span><span class="sxs-lookup"><span data-stu-id="45e3e-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="45e3e-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="45e3e-111">Optional.</span></span> <span data-ttu-id="45e3e-112">Jeden lub więcej następujących instrukcji `While`, uruchamiania zawsze `condition` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="45e3e-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="45e3e-113">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="45e3e-113">Optional.</span></span> <span data-ttu-id="45e3e-114">Przekazuje sterowanie do następnej iteracji `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="45e3e-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="45e3e-115">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="45e3e-115">Optional.</span></span> <span data-ttu-id="45e3e-116">Przekazuje sterowanie poza `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="45e3e-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="45e3e-117">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="45e3e-117">Required.</span></span> <span data-ttu-id="45e3e-118">Kończy definicję `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="45e3e-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45e3e-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45e3e-119">Remarks</span></span>  
 <span data-ttu-id="45e3e-120">Użyj `While...End While` struktury, gdy ma zostać powtórzony zestaw instrukcji o nieograniczonej liczby godzin, warunek nie zostanie `True`.</span><span class="sxs-lookup"><span data-stu-id="45e3e-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="45e3e-121">Jeśli chcesz bardziej elastyczne, z którym testować warunek lub to, co powoduje, należy przetestować go dla łączyli [czy... Pętla instrukcji](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="45e3e-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="45e3e-122">Jeśli chcesz powtarzać instrukcje jest określona liczba razy, [dla... Następna instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md) jest zwykle lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="45e3e-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45e3e-123">`While` — Słowo kluczowe jest również używana w [czy... Pętla instrukcji](../../../visual-basic/language-reference/statements/do-loop-statement.md), [Skip While — klauzula](../../../visual-basic/language-reference/queries/skip-while-clause.md) i [Take While — klauzula](../../../visual-basic/language-reference/queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="45e3e-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="45e3e-124">Jeśli `condition` jest `True`, wszystkie z `statements` do wykonywania `End While` napotkano instrukcji.</span><span class="sxs-lookup"><span data-stu-id="45e3e-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="45e3e-125">Zwraca do kontrolowania `While` instrukcji i `condition` ponownie jest zaznaczony.</span><span class="sxs-lookup"><span data-stu-id="45e3e-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="45e3e-126">Jeśli `condition` jest nadal `True`, proces jest powtarzany.</span><span class="sxs-lookup"><span data-stu-id="45e3e-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="45e3e-127">Jeśli ma ona `False`, kontrola przechodzi do instrukcji następującej `End While` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="45e3e-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="45e3e-128">`While` Przed uruchomieniem jej pętli instrukcji zawsze sprawdza warunek.</span><span class="sxs-lookup"><span data-stu-id="45e3e-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="45e3e-129">Zapętlenie będzie nadal występować, gdy warunek jest `True`.</span><span class="sxs-lookup"><span data-stu-id="45e3e-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="45e3e-130">Jeśli `condition` jest `False` podczas wpisywania pętli nie Uruchom jeszcze raz.</span><span class="sxs-lookup"><span data-stu-id="45e3e-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="45e3e-131">`condition` Zazwyczaj wyniki porównania dwóch wartości, ale może być dowolne wyrażenie obliczane do [— typ danych logicznych](../../../visual-basic/language-reference/data-types/boolean-data-type.md) wartość (`True` lub `False`).</span><span class="sxs-lookup"><span data-stu-id="45e3e-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="45e3e-132">Wyrażenie nie może zawierać wartości inny typ danych, takich jak typu liczbowego, który został przekonwertowany na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="45e3e-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="45e3e-133">Można zagnieżdżać `While` pętle, umieszczając pętli w innym.</span><span class="sxs-lookup"><span data-stu-id="45e3e-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="45e3e-134">Można zagnieżdżać w różnych rodzajów struktury sterujące wewnątrz innych.</span><span class="sxs-lookup"><span data-stu-id="45e3e-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="45e3e-135">Aby uzyskać więcej informacji, zobacz [zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="45e3e-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="45e3e-136">Zakończ podczas</span><span class="sxs-lookup"><span data-stu-id="45e3e-136">Exit While</span></span>  
 <span data-ttu-id="45e3e-137">[Wyjść, gdy](../../../visual-basic/language-reference/statements/exit-statement.md) instrukcji można podać inny sposób, aby zakończyć `While` pętli.</span><span class="sxs-lookup"><span data-stu-id="45e3e-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="45e3e-138">`Exit While` natychmiast przenosi kontroli do instrukcji następującej `End While` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="45e3e-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="45e3e-139">Zazwyczaj używają `Exit While` po spełnienia określonego warunku jest obliczane (na przykład w `If...Then...Else` struktury).</span><span class="sxs-lookup"><span data-stu-id="45e3e-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="45e3e-140">Możesz zamknąć pętlę Jeśli wykryć warunek, który ułatwia niepotrzebnych lub nie można kontynuować iteracja, takich jak Błędna wartość lub zakończenia żądania.</span><span class="sxs-lookup"><span data-stu-id="45e3e-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="45e3e-141">Można użyć `Exit While` podczas testowania dla warunku, który może powodować *nieskończonej pętli*, która jest pętli, które można uruchomić bardzo duże lub nawet nieskończoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="45e3e-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="45e3e-142">Następnie można użyć `Exit While` wyjścia z pętli.</span><span class="sxs-lookup"><span data-stu-id="45e3e-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="45e3e-143">Może zawierać dowolną liczbę `Exit While` instrukcje w `While` pętli.</span><span class="sxs-lookup"><span data-stu-id="45e3e-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="45e3e-144">Gdy jest używany w zagnieżdżonych `While` pętle, `Exit While` przekazuje sterowanie poza najbardziej pętli i do następnego wyższy poziom zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="45e3e-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="45e3e-145">`Continue While` Instrukcji natychmiast przekazuje sterowanie do następnej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="45e3e-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="45e3e-146">Aby uzyskać więcej informacji, zobacz [kontynuować instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="45e3e-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="45e3e-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="45e3e-147">Example</span></span>  
 <span data-ttu-id="45e3e-148">W poniższym przykładzie instrukcje w pętli kontynuować do momentu zakończenia `index` zmiennej jest większa niż 10.</span><span class="sxs-lookup"><span data-stu-id="45e3e-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="45e3e-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="45e3e-149">Example</span></span>  
 <span data-ttu-id="45e3e-150">Poniższy przykład przedstawia użycie `Continue While` i `Exit While` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="45e3e-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="45e3e-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="45e3e-151">Example</span></span>  
 <span data-ttu-id="45e3e-152">Poniższy przykład odczytuje wszystkie wiersze w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="45e3e-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="45e3e-153"><xref:System.IO.File.OpenText%2A> Metoda otwiera plik i zwraca <xref:System.IO.StreamReader> które odczytuje znaki.</span><span class="sxs-lookup"><span data-stu-id="45e3e-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="45e3e-154">W `While` warunku, <xref:System.IO.StreamReader.Peek%2A> metoda `StreamReader` Określa, czy plik zawiera dodatkowe znaki.</span><span class="sxs-lookup"><span data-stu-id="45e3e-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="45e3e-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45e3e-155">See Also</span></span>  
 [<span data-ttu-id="45e3e-156">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="45e3e-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="45e3e-157">Do...Loop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="45e3e-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="45e3e-158">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="45e3e-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="45e3e-159">Boolean, typ danych</span><span class="sxs-lookup"><span data-stu-id="45e3e-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [<span data-ttu-id="45e3e-160">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="45e3e-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="45e3e-161">Exit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="45e3e-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="45e3e-162">Continue, instrukcja</span><span class="sxs-lookup"><span data-stu-id="45e3e-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
