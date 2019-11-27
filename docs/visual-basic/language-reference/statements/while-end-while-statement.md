---
title: While...End While, instrukcja
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 87f6fbd6147b6dbfbe08c93e862d58b9868f9201
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352752"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="b221a-102">While...End While — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b221a-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="b221a-103">Uruchamia serię instrukcji pod warunkiem, że dany warunek jest `True`.</span><span class="sxs-lookup"><span data-stu-id="b221a-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b221a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b221a-104">Syntax</span></span>  
  
```vb  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="b221a-105">Części</span><span class="sxs-lookup"><span data-stu-id="b221a-105">Parts</span></span>  
  
|<span data-ttu-id="b221a-106">Termin</span><span class="sxs-lookup"><span data-stu-id="b221a-106">Term</span></span>|<span data-ttu-id="b221a-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="b221a-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="b221a-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b221a-108">Required.</span></span> <span data-ttu-id="b221a-109">wyrażenie `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b221a-109">`Boolean` expression.</span></span> <span data-ttu-id="b221a-110">Jeśli `condition` jest `Nothing`, Visual Basic traktuje ją jako `False`.</span><span class="sxs-lookup"><span data-stu-id="b221a-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="b221a-111">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="b221a-111">Optional.</span></span> <span data-ttu-id="b221a-112">Co najmniej jedna instrukcja `While`, która jest uruchamiana za każdym razem, gdy `condition` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="b221a-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="b221a-113">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="b221a-113">Optional.</span></span> <span data-ttu-id="b221a-114">Przenosi formant do następnej iteracji bloku `While`.</span><span class="sxs-lookup"><span data-stu-id="b221a-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="b221a-115">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="b221a-115">Optional.</span></span> <span data-ttu-id="b221a-116">Przenosi kontrolę z bloku `While`.</span><span class="sxs-lookup"><span data-stu-id="b221a-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="b221a-117">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b221a-117">Required.</span></span> <span data-ttu-id="b221a-118">Kończy definicję bloku `While`.</span><span class="sxs-lookup"><span data-stu-id="b221a-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b221a-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b221a-119">Remarks</span></span>  
 <span data-ttu-id="b221a-120">Użyj struktury `While...End While`, gdy chcesz powtórzyć zestaw instrukcji przez nieokreśloną liczbę razy, tak długo, jak warunek pozostanie `True`.</span><span class="sxs-lookup"><span data-stu-id="b221a-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="b221a-121">Jeśli potrzebujesz większej elastyczności, w której testować warunek lub wynik, dla którego chcesz go przetestować, możesz preferować do [... Loop — instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b221a-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="b221a-122">Jeśli chcesz powtórzyć instrukcje określoną liczbę razy, [dla... Kolejną instrukcją](../../../visual-basic/language-reference/statements/for-next-statement.md) jest zwykle lepszy wybór.</span><span class="sxs-lookup"><span data-stu-id="b221a-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b221a-123">Słowo kluczowe `While` jest również używane w. [.. Instrukcja Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md), [klauzula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) i [klauzula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b221a-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="b221a-124">Jeśli `condition` jest `True`, wszystkie `statements` uruchamiane do momentu napotkania instrukcji `End While`.</span><span class="sxs-lookup"><span data-stu-id="b221a-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="b221a-125">Następnie formant wraca do instrukcji `While` i ponownie sprawdzane `condition`.</span><span class="sxs-lookup"><span data-stu-id="b221a-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="b221a-126">Jeśli `condition` nadal jest `True`, proces jest powtarzany.</span><span class="sxs-lookup"><span data-stu-id="b221a-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="b221a-127">Jeśli jest `False`, sterowanie przechodzi do instrukcji, która następuje po instrukcji `End While`.</span><span class="sxs-lookup"><span data-stu-id="b221a-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="b221a-128">Instrukcja `While` zawsze sprawdza warunek przed rozpoczęciem pętli.</span><span class="sxs-lookup"><span data-stu-id="b221a-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="b221a-129">Zapętlenie jest kontynuowane, gdy warunek pozostanie `True`.</span><span class="sxs-lookup"><span data-stu-id="b221a-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="b221a-130">Jeśli `condition` jest `False`, gdy po raz pierwszy wprowadzisz pętlę, nie zostanie ona uruchomiona nawet raz.</span><span class="sxs-lookup"><span data-stu-id="b221a-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="b221a-131">`condition` zwykle wynika z porównania dwóch wartości, ale może to być dowolne wyrażenie, które daje w wyniku wartość [typu Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` lub `False`).</span><span class="sxs-lookup"><span data-stu-id="b221a-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="b221a-132">To wyrażenie może zawierać wartość innego typu danych, na przykład typ liczbowy, który został przekonwertowany na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b221a-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="b221a-133">Pętle `While` można zagnieżdżać, umieszczając jedną pętlę w innej.</span><span class="sxs-lookup"><span data-stu-id="b221a-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="b221a-134">Można również zagnieżdżać różne rodzaje struktur kontroli w obrębie siebie.</span><span class="sxs-lookup"><span data-stu-id="b221a-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="b221a-135">Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="b221a-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="b221a-136">Zakończ, gdy</span><span class="sxs-lookup"><span data-stu-id="b221a-136">Exit While</span></span>  
 <span data-ttu-id="b221a-137">Instrukcja [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) może zapewnić inny sposób, aby zakończyć pętlę `While`.</span><span class="sxs-lookup"><span data-stu-id="b221a-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="b221a-138">`Exit While` natychmiast przenosi kontrolę do instrukcji, która następuje po instrukcji `End While`.</span><span class="sxs-lookup"><span data-stu-id="b221a-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="b221a-139">Zazwyczaj używa się `Exit While` po obliczeniu pewnego warunku (na przykład w strukturze `If...Then...Else`).</span><span class="sxs-lookup"><span data-stu-id="b221a-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="b221a-140">Możesz chcieć zakończyć pętlę, jeśli wykryjesz warunek, który sprawia, że nie jest to konieczne lub niemożliwe do kontynuowania iteracji, na przykład błędnej wartości lub żądania zakończenia.</span><span class="sxs-lookup"><span data-stu-id="b221a-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="b221a-141">`Exit While` można użyć podczas testowania dla warunku, który może spowodować nieskończoną *pętlę*, która jest pętlą, która może uruchamiać bardzo dużą lub nawet nieskończoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="b221a-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="b221a-142">Następnie można użyć `Exit While` do ucieczki pętli.</span><span class="sxs-lookup"><span data-stu-id="b221a-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="b221a-143">Dowolną liczbę instrukcji `Exit While` można umieścić w dowolnym miejscu w pętli `While`.</span><span class="sxs-lookup"><span data-stu-id="b221a-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="b221a-144">Gdy jest używany w zagnieżdżonych pętlach `While`, `Exit While` transferuje kontrolę z wewnętrznej pętli i na następny wyższy poziom zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="b221a-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="b221a-145">Instrukcja `Continue While` natychmiast przenosi formant do następnej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="b221a-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="b221a-146">Aby uzyskać więcej informacji, zobacz [Kontynuacja instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b221a-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b221a-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="b221a-147">Example</span></span>  
 <span data-ttu-id="b221a-148">W poniższym przykładzie instrukcje w pętli są nadal wykonywane, dopóki zmienna `index` nie będzie większa niż 10.</span><span class="sxs-lookup"><span data-stu-id="b221a-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="b221a-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="b221a-149">Example</span></span>  
 <span data-ttu-id="b221a-150">Poniższy przykład ilustruje użycie instrukcji `Continue While` i `Exit While`.</span><span class="sxs-lookup"><span data-stu-id="b221a-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="b221a-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="b221a-151">Example</span></span>  
 <span data-ttu-id="b221a-152">Poniższy przykład odczytuje wszystkie wiersze w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="b221a-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="b221a-153">Metoda <xref:System.IO.File.OpenText%2A> otwiera plik i zwraca <xref:System.IO.StreamReader>, który odczytuje znaki.</span><span class="sxs-lookup"><span data-stu-id="b221a-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="b221a-154">W warunku `While` Metoda <xref:System.IO.StreamReader.Peek%2A> `StreamReader` określa, czy plik zawiera dodatkowe znaki.</span><span class="sxs-lookup"><span data-stu-id="b221a-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="b221a-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b221a-155">See also</span></span>

- [<span data-ttu-id="b221a-156">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="b221a-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="b221a-157">Do...Loop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b221a-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="b221a-158">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b221a-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="b221a-159">Boolean, typ danych</span><span class="sxs-lookup"><span data-stu-id="b221a-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="b221a-160">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="b221a-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="b221a-161">Exit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b221a-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="b221a-162">Continue, instrukcja</span><span class="sxs-lookup"><span data-stu-id="b221a-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
