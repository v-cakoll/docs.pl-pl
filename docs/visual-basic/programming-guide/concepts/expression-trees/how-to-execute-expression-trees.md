---
title: 'Porady: wykonywanie drzew wyrażeń (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: 5fbd9ea2842a87a941a1b572acadc93b0a7d2e11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643656"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="b550e-102">Porady: wykonywanie drzew wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b550e-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="b550e-103">W tym temacie przedstawiono sposób wykonania drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b550e-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="b550e-104">Wykonywanie drzewo wyrażenia może zwracać wartości lub może on po prostu wykonać akcję, taką jak wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="b550e-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="b550e-105">Mogą być wykonywane tylko drzewa wyrażeń, które reprezentują wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="b550e-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="b550e-106">Drzewa wyrażeń, które reprezentują wyrażenia lambda są typu <xref:System.Linq.Expressions.LambdaExpression> lub <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="b550e-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="b550e-107">Aby wykonać te drzewa wyrażeń, należy wywołać <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodę, aby utworzyć delegata pliku wykonywalnego, a następnie wywołać delegata.</span><span class="sxs-lookup"><span data-stu-id="b550e-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b550e-108">Jeśli typ delegata nie jest znany, wyrażenia lambda jest typu <xref:System.Linq.Expressions.LambdaExpression> i nie <xref:System.Linq.Expressions.Expression%601>, należy wywołać <xref:System.Delegate.DynamicInvoke%2A> metody obiektu delegowanego, zamiast wywoływania go bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="b550e-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="b550e-109">Drzewo wyrażenia nie reprezentuje wyrażenie lambda, można utworzyć nowego wyrażenia lambda z oryginalnego drzewa wyrażenia jako jego treść przez wywołanie metody <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metody.</span><span class="sxs-lookup"><span data-stu-id="b550e-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="b550e-110">Następnie można wykonać wyrażenia lambda, jak opisano wcześniej w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="b550e-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b550e-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="b550e-111">Example</span></span>  
 <span data-ttu-id="b550e-112">Poniższy przykład kodu pokazuje sposób wykonywania drzewo wyrażenia, które reprezentuje podniesienia liczby do potęgi przez tworzenie wyrażenia lambda i jej wykonanie.</span><span class="sxs-lookup"><span data-stu-id="b550e-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="b550e-113">Wynik, reprezentujący liczbę podniesioną do potęgi jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="b550e-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="b550e-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b550e-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="b550e-115">Dodaj odwołanie projektu do System.Core.dll, jeśli nie jest już używany.</span><span class="sxs-lookup"><span data-stu-id="b550e-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="b550e-116">Obejmują System.Linq.Expressions przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b550e-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b550e-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b550e-117">See Also</span></span>  
 [<span data-ttu-id="b550e-118">Drzewa wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b550e-118">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="b550e-119">Porady: modyfikowanie drzew wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b550e-119">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
