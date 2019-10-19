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
ms.openlocfilehash: 5da05835998b2e9ef9aeefe5b00faf9e1ecb9ce2
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582268"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="23e6e-102">While...End While — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23e6e-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="23e6e-103">Uruchamia serię instrukcji pod warunkiem, że dany warunek jest `True`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23e6e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="23e6e-104">Syntax</span></span>  
  
```vb  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="23e6e-105">Części</span><span class="sxs-lookup"><span data-stu-id="23e6e-105">Parts</span></span>  
  
|<span data-ttu-id="23e6e-106">Termin</span><span class="sxs-lookup"><span data-stu-id="23e6e-106">Term</span></span>|<span data-ttu-id="23e6e-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="23e6e-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="23e6e-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="23e6e-108">Required.</span></span> <span data-ttu-id="23e6e-109">wyrażenie `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-109">`Boolean` expression.</span></span> <span data-ttu-id="23e6e-110">Jeśli `condition` jest `Nothing`, Visual Basic traktuje ją jako `False`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="23e6e-111">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="23e6e-111">Optional.</span></span> <span data-ttu-id="23e6e-112">Co najmniej jedna instrukcja `While`, która jest uruchamiana za każdym razem, gdy `condition` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="23e6e-113">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="23e6e-113">Optional.</span></span> <span data-ttu-id="23e6e-114">Przenosi formant do następnej iteracji bloku `While`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="23e6e-115">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="23e6e-115">Optional.</span></span> <span data-ttu-id="23e6e-116">Przenosi kontrolę z bloku `While`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="23e6e-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="23e6e-117">Required.</span></span> <span data-ttu-id="23e6e-118">Kończy definicję bloku `While`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23e6e-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="23e6e-119">Remarks</span></span>  
 <span data-ttu-id="23e6e-120">Użyj struktury `While...End While`, gdy chcesz powtórzyć zestaw instrukcji przez nieokreśloną liczbę razy, tak długo, jak warunek pozostanie `True`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="23e6e-121">Jeśli potrzebujesz większej elastyczności, w której testować warunek lub wynik, dla którego chcesz go przetestować, możesz preferować do [... Loop — instrukcja](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="23e6e-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="23e6e-122">Jeśli chcesz powtórzyć instrukcje określoną liczbę razy, [dla... Kolejną instrukcją](../../../visual-basic/language-reference/statements/for-next-statement.md) jest zwykle lepszy wybór.</span><span class="sxs-lookup"><span data-stu-id="23e6e-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23e6e-123">Słowo kluczowe `While` jest również używane w. [.. Instrukcja Loop](../../../visual-basic/language-reference/statements/do-loop-statement.md), [klauzula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) i [klauzula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="23e6e-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="23e6e-124">Jeśli `condition` jest `True`, wszystkie `statements` uruchamiane do momentu napotkania instrukcji `End While`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="23e6e-125">Następnie formant wraca do instrukcji `While` i ponownie sprawdzane `condition`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="23e6e-126">Jeśli `condition` nadal jest `True`, proces jest powtarzany.</span><span class="sxs-lookup"><span data-stu-id="23e6e-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="23e6e-127">Jeśli jest `False`, sterowanie przechodzi do instrukcji, która następuje po instrukcji `End While`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="23e6e-128">Instrukcja `While` zawsze sprawdza warunek przed rozpoczęciem pętli.</span><span class="sxs-lookup"><span data-stu-id="23e6e-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="23e6e-129">Zapętlenie jest kontynuowane, gdy warunek pozostanie `True`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="23e6e-130">Jeśli `condition` jest `False`, gdy po raz pierwszy wprowadzisz pętlę, nie zostanie ona uruchomiona nawet raz.</span><span class="sxs-lookup"><span data-stu-id="23e6e-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="23e6e-131">@No__t_0 zwykle wynika z porównania dwóch wartości, ale może to być dowolne wyrażenie, które daje w wyniku wartość [typu Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` lub `False`).</span><span class="sxs-lookup"><span data-stu-id="23e6e-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="23e6e-132">To wyrażenie może zawierać wartość innego typu danych, na przykład typ liczbowy, który został przekonwertowany na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="23e6e-133">Pętle `While` można zagnieżdżać, umieszczając jedną pętlę w innej.</span><span class="sxs-lookup"><span data-stu-id="23e6e-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="23e6e-134">Można również zagnieżdżać różne rodzaje struktur kontroli w obrębie siebie.</span><span class="sxs-lookup"><span data-stu-id="23e6e-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="23e6e-135">Aby uzyskać więcej informacji, zobacz [struktury formantów zagnieżdżonych](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="23e6e-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="23e6e-136">Zakończ, gdy</span><span class="sxs-lookup"><span data-stu-id="23e6e-136">Exit While</span></span>  
 <span data-ttu-id="23e6e-137">Instrukcja [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) może zapewnić inny sposób, aby zakończyć pętlę `While`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="23e6e-138">`Exit While` natychmiast przenosi kontrolę do instrukcji, która następuje po instrukcji `End While`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="23e6e-139">Zazwyczaj używa się `Exit While` po obliczeniu pewnego warunku (na przykład w strukturze `If...Then...Else`).</span><span class="sxs-lookup"><span data-stu-id="23e6e-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="23e6e-140">Możesz chcieć zakończyć pętlę, jeśli wykryjesz warunek, który sprawia, że nie jest to konieczne lub niemożliwe do kontynuowania iteracji, na przykład błędnej wartości lub żądania zakończenia.</span><span class="sxs-lookup"><span data-stu-id="23e6e-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="23e6e-141">@No__t_0 można użyć podczas testowania dla warunku, który może spowodować nieskończoną *pętlę*, która jest pętlą, która może uruchamiać bardzo dużą lub nawet nieskończoną liczbę razy.</span><span class="sxs-lookup"><span data-stu-id="23e6e-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="23e6e-142">Następnie można użyć `Exit While` do ucieczki pętli.</span><span class="sxs-lookup"><span data-stu-id="23e6e-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="23e6e-143">Dowolną liczbę instrukcji `Exit While` można umieścić w dowolnym miejscu w pętli `While`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="23e6e-144">Gdy jest używany w zagnieżdżonych pętlach `While`, `Exit While` transferuje kontrolę z wewnętrznej pętli i na następny wyższy poziom zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="23e6e-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="23e6e-145">Instrukcja `Continue While` natychmiast przenosi formant do następnej iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="23e6e-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="23e6e-146">Aby uzyskać więcej informacji, zobacz [Kontynuacja instrukcji](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="23e6e-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23e6e-147">Przykład</span><span class="sxs-lookup"><span data-stu-id="23e6e-147">Example</span></span>  
 <span data-ttu-id="23e6e-148">W poniższym przykładzie instrukcje w pętli są nadal wykonywane, dopóki zmienna `index` nie będzie większa niż 10.</span><span class="sxs-lookup"><span data-stu-id="23e6e-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="23e6e-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="23e6e-149">Example</span></span>  
 <span data-ttu-id="23e6e-150">Poniższy przykład ilustruje użycie instrukcji `Continue While` i `Exit While`.</span><span class="sxs-lookup"><span data-stu-id="23e6e-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="23e6e-151">Przykład</span><span class="sxs-lookup"><span data-stu-id="23e6e-151">Example</span></span>  
 <span data-ttu-id="23e6e-152">Poniższy przykład odczytuje wszystkie wiersze w pliku tekstowym.</span><span class="sxs-lookup"><span data-stu-id="23e6e-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="23e6e-153">Metoda <xref:System.IO.File.OpenText%2A> otwiera plik i zwraca <xref:System.IO.StreamReader>, który odczytuje znaki.</span><span class="sxs-lookup"><span data-stu-id="23e6e-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="23e6e-154">W warunku `While` Metoda <xref:System.IO.StreamReader.Peek%2A> `StreamReader` określa, czy plik zawiera dodatkowe znaki.</span><span class="sxs-lookup"><span data-stu-id="23e6e-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="23e6e-155">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="23e6e-155">See also</span></span>

- [<span data-ttu-id="23e6e-156">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="23e6e-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="23e6e-157">Do...Loop, instrukcja</span><span class="sxs-lookup"><span data-stu-id="23e6e-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="23e6e-158">For...Next, instrukcja</span><span class="sxs-lookup"><span data-stu-id="23e6e-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="23e6e-159">Boolean, typ danych</span><span class="sxs-lookup"><span data-stu-id="23e6e-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="23e6e-160">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="23e6e-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="23e6e-161">Exit, instrukcja</span><span class="sxs-lookup"><span data-stu-id="23e6e-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="23e6e-162">Continue, instrukcja</span><span class="sxs-lookup"><span data-stu-id="23e6e-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
