---
title: 'Porady: tworzenie wyrażenia lambda'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 7affc84fa501ba98bdfa93835f0b0e381580b9bd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388390"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="11823-102">Porady: tworzenie wyrażenia lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11823-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="11823-103">*Wyrażenie lambda* jest funkcją lub podprocedurą, która nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="11823-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="11823-104">Wyrażenia lambda można użyć wszędzie tam, gdzie typ delegata jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="11823-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="11823-105">Aby utworzyć jednowierszową funkcję wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="11823-105">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="11823-106">W każdej sytuacji, w której można użyć typu delegata, wpisz słowo kluczowe `Function` , jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="11823-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="11823-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="11823-107">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="11823-108">W nawiasach, bezpośrednio po `Function` , wpisz parametry funkcji.</span><span class="sxs-lookup"><span data-stu-id="11823-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="11823-109">Należy zauważyć, że nie określisz nazwy po `Function` .</span><span class="sxs-lookup"><span data-stu-id="11823-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="11823-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="11823-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3. <span data-ttu-id="11823-111">Po liście parametrów wpisz pojedyncze wyrażenie jako treść funkcji.</span><span class="sxs-lookup"><span data-stu-id="11823-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="11823-112">Wartością zwracaną przez wyrażenie jest wartość zwrócona przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="11823-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="11823-113">Nie używasz `As` klauzuli do określenia typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="11823-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="11823-114">Wyrażenie lambda jest wywoływane przez przekazanie argumentu w postaci liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="11823-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="11823-115">Alternatywnie, ten sam wynik jest realizowany przez następujący przykład:</span><span class="sxs-lookup"><span data-stu-id="11823-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="11823-116">Aby utworzyć jednowierszową podprocedurę wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="11823-116">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="11823-117">W każdej sytuacji, w której można użyć typu delegata, wpisz słowo kluczowe `Sub` , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="11823-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="11823-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="11823-118">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="11823-119">W nawiasach, bezpośrednio po `Sub` , wpisz parametry procedury podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="11823-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="11823-120">Należy zauważyć, że nie określisz nazwy po `Sub` .</span><span class="sxs-lookup"><span data-stu-id="11823-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="11823-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="11823-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3. <span data-ttu-id="11823-122">Po liście parametrów wpisz pojedynczą instrukcję jako treść procedury podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="11823-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="11823-123">Wyrażenie lambda jest wywoływane przez przekazanie argumentu ciągu.</span><span class="sxs-lookup"><span data-stu-id="11823-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="11823-124">Aby utworzyć wielowierszową funkcję wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="11823-124">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="11823-125">W każdej sytuacji, w której można użyć typu delegata, wpisz słowo kluczowe `Function` , jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="11823-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="11823-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="11823-126">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="11823-127">W nawiasach, bezpośrednio po `Function` , wpisz parametry funkcji.</span><span class="sxs-lookup"><span data-stu-id="11823-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="11823-128">Należy zauważyć, że nie określisz nazwy po `Function` .</span><span class="sxs-lookup"><span data-stu-id="11823-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="11823-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="11823-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3. <span data-ttu-id="11823-130">Naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="11823-130">Press ENTER.</span></span> <span data-ttu-id="11823-131">Ta `End Function` instrukcja jest automatycznie dodawana.</span><span class="sxs-lookup"><span data-stu-id="11823-131">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="11823-132">W treści funkcji Dodaj następujący kod, aby utworzyć wyrażenie i zwrócić wartość.</span><span class="sxs-lookup"><span data-stu-id="11823-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="11823-133">Nie używasz `As` klauzuli do określenia typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="11823-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="11823-134">Wyrażenie lambda jest wywoływane przez przekazanie argumentu w postaci liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="11823-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="11823-135">Aby utworzyć wielowierszową procedurę wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="11823-135">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="11823-136">W każdej sytuacji, w której można użyć typu delegata, wpisz słowo kluczowe `Sub` , jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="11823-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="11823-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="11823-137">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="11823-138">W nawiasach, bezpośrednio po `Sub` , wpisz parametry procedury podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="11823-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="11823-139">Należy zauważyć, że nie określisz nazwy po `Sub` .</span><span class="sxs-lookup"><span data-stu-id="11823-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="11823-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="11823-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3. <span data-ttu-id="11823-141">Naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="11823-141">Press ENTER.</span></span> <span data-ttu-id="11823-142">Ta `End Sub` instrukcja jest automatycznie dodawana.</span><span class="sxs-lookup"><span data-stu-id="11823-142">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="11823-143">W treści funkcji Dodaj następujący kod, aby wykonać po wywołaniu procedury podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="11823-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="11823-144">Wyrażenie lambda jest wywoływane przez przekazanie argumentu ciągu.</span><span class="sxs-lookup"><span data-stu-id="11823-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="11823-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="11823-145">Example</span></span>  
 <span data-ttu-id="11823-146">Typowym zastosowaniem wyrażeń lambda jest zdefiniowanie funkcji, która może być przenoszona jako argument dla parametru, którego typem jest `Delegate` .</span><span class="sxs-lookup"><span data-stu-id="11823-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="11823-147">W poniższym przykładzie <xref:System.Diagnostics.Process.GetProcesses%2A> Metoda zwraca tablicę procesów uruchomionych na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="11823-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="11823-148"><xref:System.Linq.Enumerable.Where%2A>Metoda z <xref:System.Linq.Enumerable> klasy wymaga `Boolean` delegata jako argumentu.</span><span class="sxs-lookup"><span data-stu-id="11823-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="11823-149">Wyrażenie lambda w przykładzie jest używane do tego celu.</span><span class="sxs-lookup"><span data-stu-id="11823-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="11823-150">Zwraca `True` dla każdego procesu, który ma tylko jeden wątek i są wybrane w `filteredList` .</span><span class="sxs-lookup"><span data-stu-id="11823-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="11823-151">Poprzedni przykład jest odpowiednikiem poniższego kodu, który jest zapisywana w składni języka (LINQ) zintegrowanego z językiem:</span><span class="sxs-lookup"><span data-stu-id="11823-151">The previous example is equivalent to the following code, which is written in Language-Integrated Query (LINQ) syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="11823-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11823-152">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="11823-153">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="11823-153">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="11823-154">Function, instrukcja</span><span class="sxs-lookup"><span data-stu-id="11823-154">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="11823-155">Sub, instrukcja</span><span class="sxs-lookup"><span data-stu-id="11823-155">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="11823-156">Delegaci</span><span class="sxs-lookup"><span data-stu-id="11823-156">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="11823-157">Porady: przekazywanie procedur do innej procedury w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="11823-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="11823-158">Delegate — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="11823-158">Delegate Statement</span></span>](../../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="11823-159">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="11823-159">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
