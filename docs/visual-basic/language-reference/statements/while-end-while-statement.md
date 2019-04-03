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
ms.openlocfilehash: 00ca0ad24231128b25a988921386d6bd3265e9a0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843715"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="5e41c-102">While...End While — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e41c-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="5e41c-103">Uruchamia serię instrukcji tak długo, jak jest dany warunek `True`.</span><span class="sxs-lookup"><span data-stu-id="5e41c-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e41c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e41c-104">Syntax</span></span>  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="5e41c-105">Części</span><span class="sxs-lookup"><span data-stu-id="5e41c-105">Parts</span></span>  
  
|<span data-ttu-id="5e41c-106">Termin</span><span class="sxs-lookup"><span data-stu-id="5e41c-106">Term</span></span>|<span data-ttu-id="5e41c-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="5e41c-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="5e41c-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5e41c-108">Required.</span></span> <span data-ttu-id="5e41c-109">`Boolean` wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="5e41c-109">`Boolean` expression.</span></span> <span data-ttu-id="5e41c-110">Jeśli `condition` jest `Nothing`, Visual Basic traktuje je jako `False`.</span><span class="sxs-lookup"><span data-stu-id="5e41c-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="5e41c-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5e41c-111">Optional.</span></span> <span data-ttu-id="5e41c-112">Jeden lub więcej następujących instrukcji `While`, uruchamiania każdym `condition` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="5e41c-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="5e41c-113">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5e41c-113">Optional.</span></span> <span data-ttu-id="5e41c-114">Przekazuje sterowanie do następnej iteracji `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="5e41c-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="5e41c-115">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5e41c-115">Optional.</span></span> <span data-ttu-id="5e41c-116">Przekazuje sterowanie poza `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="5e41c-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="5e41c-117">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5e41c-117">Required.</span></span> <span data-ttu-id="5e41c-118">Kończy definicję `While` bloku.</span><span class="sxs-lookup"><span data-stu-id="5e41c-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e41c-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e41c-119">Remarks</span></span>  
 <span data-ttu-id="5e41c-120">Użyj `While...End While` struktury, gdy chcesz powtórzyć zbiór instrukcji na nieokreśloną liczbę razy, tak długo, jak długo pozostaje warunek `True`.</span><span class="sxs-lookup"><span data-stu-id="5e41c-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="5e41c-121">Jeśli chcesz, większą elastyczność, gdy test warunku lub co powoduje, możesz ją przetestować, aby możesz preferować [zrobić... Instrukcja pętli](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5e41c-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="5e41c-122">Jeśli chcesz powtórzyć oświadczeń określona liczba razy, [dla... Następna instrukcja](../../../visual-basic/language-reference/statements/for-next-statement.md) zazwyczaj jest lepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="5e41c-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e41c-123">`While` — Słowo kluczowe jest również używany w [zrobić... Instrukcja pętli](../../../visual-basic/language-reference/statements/do-loop-statement.md), [Skip While — klauzula](../../../visual-basic/language-reference/queries/skip-while-clause.md) i [Take While — klauzula](../../../visual-basic/language-reference/queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="5e41c-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="5e41c-124">Jeśli `condition` jest `True`, wszystkie z `statements` wykonywania do momentu `End While` napotkania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5e41c-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="5e41c-125">Następnie zwraca do kontrolowania `While` instrukcji i `condition` zaznaczono opcję ponownie.</span><span class="sxs-lookup"><span data-stu-id="5e41c-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="5e41c-126">Jeśli `condition` jest nadal `True`, proces jest powtarzany.</span><span class="sxs-lookup"><span data-stu-id="5e41c-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="5e41c-127">Jeśli ma on `False`, kontrola przechodzi do instrukcji następującej `End While` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5e41c-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="5e41c-128">`While` Instrukcja zawsze sprawdza warunek, zanim zacznie pętli.</span><span class="sxs-lookup"><span data-stu-id="5e41c-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="5e41c-129">Tworzenie pętli będzie się powtarzać, gdy warunek jest `True`.</span><span class="sxs-lookup"><span data-stu-id="5e41c-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="5e41c-130">Jeśli `condition` jest `False` podczas wpisywania pętli nie działa ona jeszcze raz.</span><span class="sxs-lookup"><span data-stu-id="5e41c-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="5e41c-131">`condition` Zazwyczaj wynikiem porównania dwóch wartości, ale może być dowolne wyrażenie, które daje w wyniku [typ danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) wartość (`True` lub `False`).</span><span class="sxs-lookup"><span data-stu-id="5e41c-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="5e41c-132">To wyrażenie może zawierać wartości innego typu danych, takich jak typ liczbowy, który został przekonwertowany na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="5e41c-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="5e41c-133">Można zagnieżdżać `While` pętli przez umieszczenie pętli w innym.</span><span class="sxs-lookup"><span data-stu-id="5e41c-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="5e41c-134">Można także zagnieżdżać różne rodzaje struktur sterujących w ramach siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="5e41c-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="5e41c-135">Aby uzyskać więcej informacji, zobacz [zagnieżdżone struktury sterujące](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="5e41c-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="5e41c-136">Zakończ podczas</span><span class="sxs-lookup"><span data-stu-id="5e41c-136">Exit While</span></span>  
 <span data-ttu-id="5e41c-137">[Wyjść, gdy](../../../visual-basic/language-reference/statements/exit-statement.md) instrukcji może zapewnić innym sposobem, aby zakończyć działanie `While` pętli.</span><span class="sxs-lookup"><span data-stu-id="5e41c-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="5e41c-138">`Exit While` natychmiast przekazuje sterowanie do instrukcji następującej `End While` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5e41c-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="5e41c-139">Zazwyczaj używa się `Exit While` po ocenieniu jakiś warunek (na przykład w `If...Then...Else` struktury).</span><span class="sxs-lookup"><span data-stu-id="5e41c-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="5e41c-140">Można zamknąć pętli, jeśli wykryje warunek, który sprawia, że niepotrzebnych lub niemożliwe kontynuować, iteracja, np. Błędna wartość lub żądanie zakończenia działania.</span><span class="sxs-lookup"><span data-stu-id="5e41c-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="5e41c-141">Możesz użyć `Exit While` podczas testowania dla warunku, który może powodować *nieskończoną pętlę*, czyli pętlę, która może działać bardzo duże lub nawet nieskończona liczba prób.</span><span class="sxs-lookup"><span data-stu-id="5e41c-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="5e41c-142">Następnie można użyć `Exit While` jako znak ucieczki dla pętli.</span><span class="sxs-lookup"><span data-stu-id="5e41c-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="5e41c-143">Można umieścić dowolną liczbę `Exit While` instrukcji w `While` pętli.</span><span class="sxs-lookup"><span data-stu-id="5e41c-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="5e41c-144">Gdy jest używana w ramach zagnieżdżonych `While` pętli, `Exit While` przenosi sterowanie na dostęp do najaktualniejszych najbardziej wewnętrznej i do następnego wyższy poziom zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="5e41c-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="5e41c-145">`Continue While` Instrukcji natychmiast przekazuje sterowanie do następnej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="5e41c-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="5e41c-146">Aby uzyskać więcej informacji, zobacz [nadal instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5e41c-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e41c-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e41c-147">Example</span></span>  
 <span data-ttu-id="5e41c-148">W poniższym przykładzie instrukcje w pętli nadal działać do momentu `index` zmiennej jest większa niż 10.</span><span class="sxs-lookup"><span data-stu-id="5e41c-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="5e41c-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e41c-149">Example</span></span>  
 <span data-ttu-id="5e41c-150">Poniższy przykład ilustruje użycie `Continue While` i `Exit While` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5e41c-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="5e41c-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="5e41c-151">Example</span></span>  
 <span data-ttu-id="5e41c-152">Poniższy przykład odczytuje wszystkie wiersze w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="5e41c-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="5e41c-153"><xref:System.IO.File.OpenText%2A> Metoda otwiera plik i zwraca <xref:System.IO.StreamReader> , odczytuje znaki.</span><span class="sxs-lookup"><span data-stu-id="5e41c-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="5e41c-154">W `While` warunku <xref:System.IO.StreamReader.Peek%2A> metody `StreamReader` Określa, czy plik zawiera dodatkowe znaki.</span><span class="sxs-lookup"><span data-stu-id="5e41c-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="5e41c-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e41c-155">See also</span></span>

- [<span data-ttu-id="5e41c-156">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="5e41c-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="5e41c-157">Do...Loop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5e41c-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="5e41c-158">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5e41c-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="5e41c-159">Boolean, typ danych</span><span class="sxs-lookup"><span data-stu-id="5e41c-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="5e41c-160">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="5e41c-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="5e41c-161">Exit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5e41c-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="5e41c-162">Continue, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5e41c-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
