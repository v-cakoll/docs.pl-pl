---
title: 'Porady: tworzenie wyrażenia lambda'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: bb0bdb3c10a7df2ca954fbdb9382a25bf805068d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349741"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="ae358-102">Porady: tworzenie wyrażenia lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae358-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="ae358-103">A *lambda expression* is a function or subroutine that does not have a name.</span><span class="sxs-lookup"><span data-stu-id="ae358-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="ae358-104">A lambda expression can be used wherever a delegate type is valid.</span><span class="sxs-lookup"><span data-stu-id="ae358-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="ae358-105">To create a single-line lambda expression function</span><span class="sxs-lookup"><span data-stu-id="ae358-105">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="ae358-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span><span class="sxs-lookup"><span data-stu-id="ae358-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="ae358-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="ae358-107">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="ae358-108">In parentheses, directly after `Function`, type the parameters of the function.</span><span class="sxs-lookup"><span data-stu-id="ae358-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="ae358-109">Notice that you do not specify a name after `Function`.</span><span class="sxs-lookup"><span data-stu-id="ae358-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="ae358-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="ae358-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3. <span data-ttu-id="ae358-111">Following the parameter list, type a single expression as the body of the function.</span><span class="sxs-lookup"><span data-stu-id="ae358-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="ae358-112">The value that the expression evaluates to is the value returned by the function.</span><span class="sxs-lookup"><span data-stu-id="ae358-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="ae358-113">You do not use an `As` clause to specify the return type.</span><span class="sxs-lookup"><span data-stu-id="ae358-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="ae358-114">You call the lambda expression by passing in an integer argument.</span><span class="sxs-lookup"><span data-stu-id="ae358-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="ae358-115">Alternatively, the same result is accomplished by the following example:</span><span class="sxs-lookup"><span data-stu-id="ae358-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="ae358-116">To create a single-line lambda expression subroutine</span><span class="sxs-lookup"><span data-stu-id="ae358-116">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="ae358-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span><span class="sxs-lookup"><span data-stu-id="ae358-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="ae358-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="ae358-118">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="ae358-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span><span class="sxs-lookup"><span data-stu-id="ae358-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="ae358-120">Notice that you do not specify a name after `Sub`.</span><span class="sxs-lookup"><span data-stu-id="ae358-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="ae358-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="ae358-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3. <span data-ttu-id="ae358-122">Following the parameter list, type a single statement as the body of the subroutine.</span><span class="sxs-lookup"><span data-stu-id="ae358-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="ae358-123">You call the lambda expression by passing in a string argument.</span><span class="sxs-lookup"><span data-stu-id="ae358-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="ae358-124">To create a multiline lambda expression function</span><span class="sxs-lookup"><span data-stu-id="ae358-124">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="ae358-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span><span class="sxs-lookup"><span data-stu-id="ae358-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="ae358-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="ae358-126">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="ae358-127">In parentheses, directly after `Function`, type the parameters of the function.</span><span class="sxs-lookup"><span data-stu-id="ae358-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="ae358-128">Notice that you do not specify a name after `Function`.</span><span class="sxs-lookup"><span data-stu-id="ae358-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="ae358-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="ae358-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3. <span data-ttu-id="ae358-130">Press ENTER.</span><span class="sxs-lookup"><span data-stu-id="ae358-130">Press ENTER.</span></span> <span data-ttu-id="ae358-131">The `End Function` statement is automatically added.</span><span class="sxs-lookup"><span data-stu-id="ae358-131">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="ae358-132">Within the body of the function, add the following code to create an expression and return the value.</span><span class="sxs-lookup"><span data-stu-id="ae358-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="ae358-133">You do not use an `As` clause to specify the return type.</span><span class="sxs-lookup"><span data-stu-id="ae358-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="ae358-134">You call the lambda expression by passing in an integer argument.</span><span class="sxs-lookup"><span data-stu-id="ae358-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="ae358-135">To create a multiline lambda expression subroutine</span><span class="sxs-lookup"><span data-stu-id="ae358-135">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="ae358-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span><span class="sxs-lookup"><span data-stu-id="ae358-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="ae358-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="ae358-137">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="ae358-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span><span class="sxs-lookup"><span data-stu-id="ae358-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="ae358-139">Notice that you do not specify a name after `Sub`.</span><span class="sxs-lookup"><span data-stu-id="ae358-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="ae358-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="ae358-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3. <span data-ttu-id="ae358-141">Press ENTER.</span><span class="sxs-lookup"><span data-stu-id="ae358-141">Press ENTER.</span></span> <span data-ttu-id="ae358-142">The `End Sub` statement is automatically added.</span><span class="sxs-lookup"><span data-stu-id="ae358-142">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="ae358-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span><span class="sxs-lookup"><span data-stu-id="ae358-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="ae358-144">You call the lambda expression by passing in a string argument.</span><span class="sxs-lookup"><span data-stu-id="ae358-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="ae358-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="ae358-145">Example</span></span>  
 <span data-ttu-id="ae358-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="ae358-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="ae358-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span><span class="sxs-lookup"><span data-stu-id="ae358-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="ae358-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span><span class="sxs-lookup"><span data-stu-id="ae358-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="ae358-149">The lambda expression in the example is used for that purpose.</span><span class="sxs-lookup"><span data-stu-id="ae358-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="ae358-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span><span class="sxs-lookup"><span data-stu-id="ae358-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="ae358-151">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span><span class="sxs-lookup"><span data-stu-id="ae358-151">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="ae358-152">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae358-152">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="ae358-153">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="ae358-153">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="ae358-154">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ae358-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="ae358-155">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ae358-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="ae358-156">Delegaci</span><span class="sxs-lookup"><span data-stu-id="ae358-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="ae358-157">How to: Pass Procedures to Another Procedure in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae358-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="ae358-158">Delegate, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ae358-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="ae358-159">Introduction to LINQ in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ae358-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
