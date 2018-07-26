---
title: 'Porady: tworzenie wyrażenia lambda (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: f437166bc5206b4145d6508aa2131ec94d6eca95
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244901"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="8bfbf-102">Porady: tworzenie wyrażenia lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8bfbf-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="8bfbf-103">A *wyrażenia lambda* jest funkcji lub podprocedury, który nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="8bfbf-104">Wyrażenie lambda może służyć wszędzie tam, gdzie typ obiektu delegowanego jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="8bfbf-105">Aby utworzyć funkcję wyrażenia lambda pojedynczej linii</span><span class="sxs-lookup"><span data-stu-id="8bfbf-105">To create a single-line lambda expression function</span></span>  
  
1.  <span data-ttu-id="8bfbf-106">W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Function`, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8bfbf-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="8bfbf-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="8bfbf-107">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="8bfbf-108">W nawiasach bezpośrednio po `Function`, typów parametrów funkcji.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="8bfbf-109">Zwróć uwagę, czy nie określisz nazwy po `Function`.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="8bfbf-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="8bfbf-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3.  <span data-ttu-id="8bfbf-111">Po liście parametrów należy wpisać jedno wyrażenie jako treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="8bfbf-112">Wartość, która daje w wyniku wyrażenia jest wartość zwrócona przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="8bfbf-113">Nie używaj `As` klauzulę, aby określić typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     <span data-ttu-id="8bfbf-114">Możesz wywołać Wyrażenie lambda przekazanie w argumencie liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  <span data-ttu-id="8bfbf-115">Alternatywnie ten sam wynik odbywa się w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8bfbf-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="8bfbf-116">Aby utworzyć procedurę wyrażenia lambda jednowierszowy</span><span class="sxs-lookup"><span data-stu-id="8bfbf-116">To create a single-line lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="8bfbf-117">W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Sub`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="8bfbf-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="8bfbf-118">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="8bfbf-119">W nawiasach bezpośrednio po `Sub`, typów parametrów procedury.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="8bfbf-120">Zwróć uwagę, czy nie określisz nazwy po `Sub`.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="8bfbf-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="8bfbf-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="8bfbf-122">Po liście parametrów wpisz pojedynczą instrukcję jako treść procedurę.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     <span data-ttu-id="8bfbf-123">Możesz wywołać Wyrażenie lambda przekazanie argumentu ciągu.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="8bfbf-124">Aby utworzyć funkcję wyrażenia lambda wielowierszowy</span><span class="sxs-lookup"><span data-stu-id="8bfbf-124">To create a multiline lambda expression function</span></span>  
  
1.  <span data-ttu-id="8bfbf-125">W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Function`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="8bfbf-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="8bfbf-126">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="8bfbf-127">W nawiasach bezpośrednio po `Function`, typów parametrów funkcji.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="8bfbf-128">Zwróć uwagę, czy nie określisz nazwy po `Function`.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="8bfbf-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="8bfbf-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3.  <span data-ttu-id="8bfbf-130">Naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-130">Press ENTER.</span></span> <span data-ttu-id="8bfbf-131">`End Function` Instrukcji jest automatycznie dodawany.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-131">The `End Function` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="8bfbf-132">W treści funkcji Dodaj następujący kod do tworzenia wyrażenia i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="8bfbf-133">Nie używaj `As` klauzulę, aby określić typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     <span data-ttu-id="8bfbf-134">Możesz wywołać Wyrażenie lambda przekazanie w argumencie liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="8bfbf-135">Aby utworzyć procedurę wyrażenia lambda wielowierszowy</span><span class="sxs-lookup"><span data-stu-id="8bfbf-135">To create a multiline lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="8bfbf-136">W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Sub`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8bfbf-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="8bfbf-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="8bfbf-137">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="8bfbf-138">W nawiasach bezpośrednio po `Sub`, typów parametrów procedury.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="8bfbf-139">Zwróć uwagę, czy nie określisz nazwy po `Sub`.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="8bfbf-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="8bfbf-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="8bfbf-141">Naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-141">Press ENTER.</span></span> <span data-ttu-id="8bfbf-142">`End Sub` Instrukcji jest automatycznie dodawany.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-142">The `End Sub` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="8bfbf-143">W treści funkcji Dodaj następujący kod do wykonania, gdy jest wywoływana przez procedurę.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     <span data-ttu-id="8bfbf-144">Możesz wywołać Wyrażenie lambda przekazanie argumentu ciągu.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a><span data-ttu-id="8bfbf-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="8bfbf-145">Example</span></span>  
 <span data-ttu-id="8bfbf-146">Zazwyczaj jest używane, wyrażeń lambda do definiowania funkcji, które mogą być przekazywane jako argumentu dla parametru, którego typem jest `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="8bfbf-147">W poniższym przykładzie <xref:System.Diagnostics.Process.GetProcesses%2A> metoda zwraca tablicę procesów uruchomionych na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="8bfbf-148"><xref:System.Linq.Enumerable.Where%2A> Metody z <xref:System.Linq.Enumerable> klasa wymaga `Boolean` delegować jako argumentem.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="8bfbf-149">Wyrażenia lambda w przykładzie jest używany do tego celu.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="8bfbf-150">Zwraca `True` dla każdego procesu, który ma tylko jeden wątek, a te są zaznaczone w `filteredList`.</span><span class="sxs-lookup"><span data-stu-id="8bfbf-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 <span data-ttu-id="8bfbf-151">Poprzedni przykład jest równoważny z następującym kodem, które są zapisywane w [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] składni:</span><span class="sxs-lookup"><span data-stu-id="8bfbf-151">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8bfbf-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8bfbf-152">See Also</span></span>  
 <xref:System.Linq.Enumerable>  
 [<span data-ttu-id="8bfbf-153">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="8bfbf-153">Lambda Expressions</span></span>](./lambda-expressions.md)  
 [<span data-ttu-id="8bfbf-154">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8bfbf-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="8bfbf-155">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8bfbf-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="8bfbf-156">Delegaci</span><span class="sxs-lookup"><span data-stu-id="8bfbf-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="8bfbf-157">Porady: przekazywanie procedur do innej procedury w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8bfbf-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [<span data-ttu-id="8bfbf-158">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8bfbf-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="8bfbf-159">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8bfbf-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
