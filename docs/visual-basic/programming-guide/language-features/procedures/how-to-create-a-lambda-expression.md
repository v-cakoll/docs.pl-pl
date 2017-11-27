---
title: "Porady: tworzenie wyrażenia lambda (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16365b64e5430be61c113ac7601154df260e4ca5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="f85d4-102">Porady: tworzenie wyrażenia lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f85d4-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="f85d4-103">A *wyrażenia lambda* funkcji lub procedury, która nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="f85d4-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="f85d4-104">Wyrażenia lambda można tam, gdzie typ delegata jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="f85d4-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="f85d4-105">Aby utworzyć funkcja wyrażenia lambda jeden wiersz</span><span class="sxs-lookup"><span data-stu-id="f85d4-105">To create a single-line lambda expression function</span></span>  
  
1.  <span data-ttu-id="f85d4-106">W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Function`, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f85d4-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="f85d4-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="f85d4-107">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="f85d4-108">W nawiasach bezpośrednio po `Function`, wpisz parametry funkcji.</span><span class="sxs-lookup"><span data-stu-id="f85d4-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="f85d4-109">Zwróć uwagę, że nie należy określać nazwy po `Function`.</span><span class="sxs-lookup"><span data-stu-id="f85d4-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="f85d4-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="f85d4-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3.  <span data-ttu-id="f85d4-111">Po liście parametrów wpisz jedno wyrażenie jako treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="f85d4-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="f85d4-112">Wartość, która daje w wyniku wyrażenia jest wartość zwrócona przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="f85d4-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="f85d4-113">Nie używaj `As` klauzuli, aby określić typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="f85d4-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     <span data-ttu-id="f85d4-114">Należy wywołać wyrażenia lambda przekazując argument liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="f85d4-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  <span data-ttu-id="f85d4-115">Alternatywnie takiego samego wyniku odbywa się przy następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f85d4-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="f85d4-116">Aby utworzyć podprocedury wyrażenia lambda jeden wiersz</span><span class="sxs-lookup"><span data-stu-id="f85d4-116">To create a single-line lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="f85d4-117">W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Sub`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f85d4-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="f85d4-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="f85d4-118">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="f85d4-119">W nawiasach bezpośrednio po `Sub`, wpisz parametry procedury.</span><span class="sxs-lookup"><span data-stu-id="f85d4-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="f85d4-120">Zwróć uwagę, że nie należy określać nazwy po `Sub`.</span><span class="sxs-lookup"><span data-stu-id="f85d4-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="f85d4-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="f85d4-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="f85d4-122">Po liście parametrów wpisać jednej instrukcji w treści procedury.</span><span class="sxs-lookup"><span data-stu-id="f85d4-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     <span data-ttu-id="f85d4-123">Należy wywołać wyrażenia lambda przekazując argument ciągu.</span><span class="sxs-lookup"><span data-stu-id="f85d4-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="f85d4-124">Aby utworzyć funkcja wyrażenie wielowierszowych wyrażeń lambda</span><span class="sxs-lookup"><span data-stu-id="f85d4-124">To create a multiline lambda expression function</span></span>  
  
1.  <span data-ttu-id="f85d4-125">W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Function`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f85d4-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="f85d4-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="f85d4-126">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="f85d4-127">W nawiasach bezpośrednio po `Function`, wpisz parametry funkcji.</span><span class="sxs-lookup"><span data-stu-id="f85d4-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="f85d4-128">Zwróć uwagę, że nie należy określać nazwy po `Function`.</span><span class="sxs-lookup"><span data-stu-id="f85d4-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="f85d4-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="f85d4-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3.  <span data-ttu-id="f85d4-130">Naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="f85d4-130">Press ENTER.</span></span> <span data-ttu-id="f85d4-131">`End Function` Instrukcja jest automatycznie dodawany.</span><span class="sxs-lookup"><span data-stu-id="f85d4-131">The `End Function` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="f85d4-132">W treści funkcji Dodaj następujący kod do tworzenia wyrażenia i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="f85d4-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="f85d4-133">Nie używaj `As` klauzuli, aby określić typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="f85d4-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     <span data-ttu-id="f85d4-134">Należy wywołać wyrażenia lambda przekazując argument liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="f85d4-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="f85d4-135">Aby utworzyć podprocedury wyrażenie wielowierszowych wyrażeń lambda</span><span class="sxs-lookup"><span data-stu-id="f85d4-135">To create a multiline lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="f85d4-136">W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Sub`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f85d4-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="f85d4-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="f85d4-137">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="f85d4-138">W nawiasach bezpośrednio po `Sub`, wpisz parametry procedury.</span><span class="sxs-lookup"><span data-stu-id="f85d4-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="f85d4-139">Zwróć uwagę, że nie należy określać nazwy po `Sub`.</span><span class="sxs-lookup"><span data-stu-id="f85d4-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="f85d4-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="f85d4-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="f85d4-141">Naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="f85d4-141">Press ENTER.</span></span> <span data-ttu-id="f85d4-142">`End Sub` Instrukcja jest automatycznie dodawany.</span><span class="sxs-lookup"><span data-stu-id="f85d4-142">The `End Sub` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="f85d4-143">W treści funkcji Dodaj następujący kod do wykonania po wywołaniu procedury.</span><span class="sxs-lookup"><span data-stu-id="f85d4-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     <span data-ttu-id="f85d4-144">Należy wywołać wyrażenia lambda przekazując argument ciągu.</span><span class="sxs-lookup"><span data-stu-id="f85d4-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a><span data-ttu-id="f85d4-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="f85d4-145">Example</span></span>  
 <span data-ttu-id="f85d4-146">Zazwyczaj wyrażeń lambda jest używane do definiowania funkcji, która może zostać przekazane za jako argumentu dla parametru o typie `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="f85d4-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="f85d4-147">W poniższym przykładzie <xref:System.Diagnostics.Process.GetProcesses%2A> metoda zwraca tablicę procesów uruchomionych na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="f85d4-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="f85d4-148"><xref:System.Linq.Enumerable.Where%2A> Metody z <xref:System.Linq.Enumerable> wymaga klasy `Boolean` delegata jako jej argument.</span><span class="sxs-lookup"><span data-stu-id="f85d4-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="f85d4-149">Wyrażenia lambda, w tym przykładzie jest używany do tego celu.</span><span class="sxs-lookup"><span data-stu-id="f85d4-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="f85d4-150">Zwraca `True` dla każdego procesu, który ma tylko jeden wątek, a te są zaznaczone w `filteredList`.</span><span class="sxs-lookup"><span data-stu-id="f85d4-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 <span data-ttu-id="f85d4-151">Poprzedni przykład jest odpowiednikiem następujący kod, który jest zapisywany w [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] składni:</span><span class="sxs-lookup"><span data-stu-id="f85d4-151">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f85d4-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f85d4-152">See Also</span></span>  
 <xref:System.Linq.Enumerable>  
 [<span data-ttu-id="f85d4-153">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="f85d4-153">Lambda Expressions</span></span>](./lambda-expressions.md)  
 [<span data-ttu-id="f85d4-154">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f85d4-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="f85d4-155">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f85d4-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="f85d4-156">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="f85d4-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="f85d4-157">Porady: przekazywanie procedur do innej procedury w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f85d4-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [<span data-ttu-id="f85d4-158">Delegate — instrukcja</span><span class="sxs-lookup"><span data-stu-id="f85d4-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="f85d4-159">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f85d4-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
