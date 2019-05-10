---
title: 'Instrukcje: Wykonywanie drzew wyrażeń (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: d7e0f5f6687ffb4293209a29279ca16361e7424e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642329"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="b500e-102">Instrukcje: Wykonywanie drzew wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b500e-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="b500e-103">W tym temacie przedstawiono sposób wykonywania drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b500e-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="b500e-104">Wykonywanie drzewa wyrażenie może zwrócić wartość lub go, że po prostu wykonać akcja, taka jak wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="b500e-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="b500e-105">Mogą być wykonywane tylko drzew wyrażeń, które reprezentują wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="b500e-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="b500e-106">Drzewa wyrażeń, które reprezentują wyrażenia lambda są typu <xref:System.Linq.Expressions.LambdaExpression> lub <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="b500e-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="b500e-107">Aby wykonać te drzew wyrażeń, należy wywołać <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodę, aby utworzyć delegat pliku wykonywalnego, a następnie wywołaj delegat.</span><span class="sxs-lookup"><span data-stu-id="b500e-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b500e-108">Jeśli typ delegata nie jest znany, wyrażenie lambda jest typu <xref:System.Linq.Expressions.LambdaExpression> i nie <xref:System.Linq.Expressions.Expression%601>, należy wywołać <xref:System.Delegate.DynamicInvoke%2A> metody delegata zamiast wywołanie go bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="b500e-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="b500e-109">Drzewo wyrażenia nie reprezentuje wyrażenie lambda, można utworzyć nowe wyrażenie lambda, które ma oryginalnego drzewa wyrażeń jako jego treści, wywołując <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metody.</span><span class="sxs-lookup"><span data-stu-id="b500e-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="b500e-110">Następnie można wykonać wyrażenia lambda, zgodnie z wcześniejszym opisem w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="b500e-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b500e-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="b500e-111">Example</span></span>  
 <span data-ttu-id="b500e-112">Poniższy przykład kodu demonstruje sposób wykonywania drzewo wyrażenia, reprezentujący zwiększenie liczby do potęgi przez tworzenie wyrażenia lambda i jej wykonanie.</span><span class="sxs-lookup"><span data-stu-id="b500e-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="b500e-113">Wynik, który reprezentuje liczbę podniesioną do potęgi, jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="b500e-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
```vb  
' The expression tree to execute.  
Dim be As BinaryExpression = Expression.Power(Expression.Constant(2.0R), Expression.Constant(3.0R))  
  
' Create a lambda expression.  
Dim le As Expression(Of Func(Of Double)) = Expression.Lambda(Of Func(Of Double))(be)  
  
' Compile the lambda expression.  
Dim compiledExpression As Func(Of Double) = le.Compile()  
  
' Execute the lambda expression.  
Dim result As Double = compiledExpression()  
  
' Display the result.  
MsgBox(result)  
  
' This code produces the following output:  
' 8  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b500e-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b500e-114">Compiling the Code</span></span>  
  
- <span data-ttu-id="b500e-115">Dodaj odwołanie do biblioteki System.Core.dll, jeśli nie jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="b500e-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
- <span data-ttu-id="b500e-116">Obejmują System.Linq.Expressions przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b500e-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b500e-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b500e-117">See also</span></span>

- [<span data-ttu-id="b500e-118">Drzewa wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b500e-118">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="b500e-119">Instrukcje: Modyfikowanie drzew wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b500e-119">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
