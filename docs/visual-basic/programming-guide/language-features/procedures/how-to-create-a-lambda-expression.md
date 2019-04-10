---
title: 'Instrukcje: Tworzenie wyrażenia Lambda (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: fc2b7ed2004b842116d051b393f00506428def61
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344549"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="ed432-102">Instrukcje: Tworzenie wyrażenia Lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed432-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="ed432-103">A *wyrażenia lambda* jest funkcji lub podprocedury, który nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="ed432-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="ed432-104">Wyrażenie lambda może służyć wszędzie tam, gdzie typ obiektu delegowanego jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="ed432-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="ed432-105">Aby utworzyć funkcję wyrażenia lambda pojedynczej linii</span><span class="sxs-lookup"><span data-stu-id="ed432-105">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="ed432-106">W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Function`, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ed432-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     `Dim add1 =`   `Function`  
  
2. <span data-ttu-id="ed432-107">W nawiasach bezpośrednio po `Function`, typów parametrów funkcji.</span><span class="sxs-lookup"><span data-stu-id="ed432-107">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="ed432-108">Zwróć uwagę, czy nie określisz nazwy po `Function`.</span><span class="sxs-lookup"><span data-stu-id="ed432-108">Notice that you do not specify a name after `Function`.</span></span>  
  
     `Dim add1 = Function`   `(num As Integer)`  
  
3. <span data-ttu-id="ed432-109">Po liście parametrów należy wpisać jedno wyrażenie jako treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="ed432-109">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="ed432-110">Wartość, która daje w wyniku wyrażenia jest wartość zwrócona przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="ed432-110">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="ed432-111">Nie używaj `As` klauzulę, aby określić typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="ed432-111">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="ed432-112">Możesz wywołać Wyrażenie lambda przekazanie w argumencie liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="ed432-112">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="ed432-113">Alternatywnie ten sam wynik odbywa się w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ed432-113">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="ed432-114">Aby utworzyć procedurę wyrażenia lambda jednowierszowy</span><span class="sxs-lookup"><span data-stu-id="ed432-114">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="ed432-115">W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Sub`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ed432-115">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     `Dim add1 =`   `Sub`  
  
2. <span data-ttu-id="ed432-116">W nawiasach bezpośrednio po `Sub`, typów parametrów procedury.</span><span class="sxs-lookup"><span data-stu-id="ed432-116">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="ed432-117">Zwróć uwagę, czy nie określisz nazwy po `Sub`.</span><span class="sxs-lookup"><span data-stu-id="ed432-117">Notice that you do not specify a name after `Sub`.</span></span>  
  
     `Dim add1 = Sub`   `(msg As String)`  
  
3. <span data-ttu-id="ed432-118">Po liście parametrów wpisz pojedynczą instrukcję jako treść procedurę.</span><span class="sxs-lookup"><span data-stu-id="ed432-118">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="ed432-119">Możesz wywołać Wyrażenie lambda przekazanie argumentu ciągu.</span><span class="sxs-lookup"><span data-stu-id="ed432-119">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="ed432-120">Aby utworzyć funkcję wyrażenia lambda wielowierszowy</span><span class="sxs-lookup"><span data-stu-id="ed432-120">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="ed432-121">W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Function`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ed432-121">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     `Dim add1 =`   `Function`  
  
2. <span data-ttu-id="ed432-122">W nawiasach bezpośrednio po `Function`, typów parametrów funkcji.</span><span class="sxs-lookup"><span data-stu-id="ed432-122">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="ed432-123">Zwróć uwagę, czy nie określisz nazwy po `Function`.</span><span class="sxs-lookup"><span data-stu-id="ed432-123">Notice that you do not specify a name after `Function`.</span></span>  
  
     `Dim add1 = Function`   `(index As Integer)`  
  
3. <span data-ttu-id="ed432-124">Naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="ed432-124">Press ENTER.</span></span> <span data-ttu-id="ed432-125">`End Function` Instrukcji jest automatycznie dodawany.</span><span class="sxs-lookup"><span data-stu-id="ed432-125">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="ed432-126">W treści funkcji Dodaj następujący kod do tworzenia wyrażenia i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="ed432-126">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="ed432-127">Nie używaj `As` klauzulę, aby określić typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="ed432-127">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="ed432-128">Możesz wywołać Wyrażenie lambda przekazanie w argumencie liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="ed432-128">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="ed432-129">Aby utworzyć procedurę wyrażenia lambda wielowierszowy</span><span class="sxs-lookup"><span data-stu-id="ed432-129">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="ed432-130">W każdej sytuacji, w których można użyć typu delegata, wpisz słowo kluczowe `Sub`, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ed432-130">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     `Dim add1 =`   `Sub`  
  
2. <span data-ttu-id="ed432-131">W nawiasach bezpośrednio po `Sub`, typów parametrów procedury.</span><span class="sxs-lookup"><span data-stu-id="ed432-131">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="ed432-132">Zwróć uwagę, czy nie określisz nazwy po `Sub`.</span><span class="sxs-lookup"><span data-stu-id="ed432-132">Notice that you do not specify a name after `Sub`.</span></span>  
  
     `Dim add1 = Sub`  `(msg As String)`  
  
3. <span data-ttu-id="ed432-133">Naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="ed432-133">Press ENTER.</span></span> <span data-ttu-id="ed432-134">`End Sub` Instrukcji jest automatycznie dodawany.</span><span class="sxs-lookup"><span data-stu-id="ed432-134">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="ed432-135">W treści funkcji Dodaj następujący kod do wykonania, gdy jest wywoływana przez procedurę.</span><span class="sxs-lookup"><span data-stu-id="ed432-135">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="ed432-136">Możesz wywołać Wyrażenie lambda przekazanie argumentu ciągu.</span><span class="sxs-lookup"><span data-stu-id="ed432-136">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="ed432-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="ed432-137">Example</span></span>  
 <span data-ttu-id="ed432-138">Zazwyczaj jest używane, wyrażeń lambda do definiowania funkcji, które mogą być przekazywane jako argumentu dla parametru, którego typem jest `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="ed432-138">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="ed432-139">W poniższym przykładzie <xref:System.Diagnostics.Process.GetProcesses%2A> metoda zwraca tablicę procesów uruchomionych na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="ed432-139">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="ed432-140"><xref:System.Linq.Enumerable.Where%2A> Metody z <xref:System.Linq.Enumerable> klasa wymaga `Boolean` delegować jako argumentem.</span><span class="sxs-lookup"><span data-stu-id="ed432-140">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="ed432-141">Wyrażenia lambda w przykładzie jest używany do tego celu.</span><span class="sxs-lookup"><span data-stu-id="ed432-141">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="ed432-142">Zwraca `True` dla każdego procesu, który ma tylko jeden wątek, a te są zaznaczone w `filteredList`.</span><span class="sxs-lookup"><span data-stu-id="ed432-142">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="ed432-143">Poprzedni przykład jest równoważny z następującym kodem, które są zapisywane w [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] składni:</span><span class="sxs-lookup"><span data-stu-id="ed432-143">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="ed432-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed432-144">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="ed432-145">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="ed432-145">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="ed432-146">Function — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="ed432-146">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="ed432-147">Sub — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="ed432-147">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="ed432-148">Delegaty</span><span class="sxs-lookup"><span data-stu-id="ed432-148">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="ed432-149">Instrukcje: Przekazywanie procedur do innej procedury w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ed432-149">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="ed432-150">Delegate — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="ed432-150">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="ed432-151">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ed432-151">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
