---
title: 'Porady: wykonywanie drzew wyrażeń'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: 82801728596449869e5124c3fc92c9c0673f5dd9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332986"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="b1e98-102">Instrukcje: wykonywanie drzew wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1e98-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="b1e98-103">W tym temacie pokazano, jak wykonać drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="b1e98-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="b1e98-104">Wykonanie drzewa wyrażenia może zwrócić wartość lub może po prostu wykonać akcję, taką jak wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="b1e98-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="b1e98-105">Można wykonywać tylko drzewa wyrażeń, które reprezentują wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="b1e98-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="b1e98-106">Drzewa wyrażeń, które reprezentują wyrażenia lambda, są typu <xref:System.Linq.Expressions.LambdaExpression> lub <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="b1e98-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="b1e98-107">Aby wykonać te drzewa wyrażeń, wywołaj metodę <xref:System.Linq.Expressions.LambdaExpression.Compile%2A>, aby utworzyć delegata pliku wykonywalnego, a następnie Wywołaj delegata.</span><span class="sxs-lookup"><span data-stu-id="b1e98-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1e98-108">Jeśli typ delegata nie jest znany, oznacza to, że wyrażenie lambda jest typu <xref:System.Linq.Expressions.LambdaExpression> a nie <xref:System.Linq.Expressions.Expression%601>, należy wywołać metodę <xref:System.Delegate.DynamicInvoke%2A> na delegatze zamiast wywoływania jej bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="b1e98-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="b1e98-109">Jeśli drzewo wyrażenia nie reprezentuje wyrażenia lambda, można utworzyć nowe wyrażenie lambda, które ma pierwotne drzewo wyrażeń jako treść, wywołując metodę <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29>.</span><span class="sxs-lookup"><span data-stu-id="b1e98-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="b1e98-110">Następnie można wykonać wyrażenie lambda zgodnie z opisem we wcześniejszej części tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="b1e98-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1e98-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="b1e98-111">Example</span></span>  
 <span data-ttu-id="b1e98-112">Poniższy przykład kodu demonstruje, jak wykonać drzewo wyrażenia, które reprezentuje podnoszenie liczby do potęgi przez utworzenie wyrażenia lambda i jego wykonanie.</span><span class="sxs-lookup"><span data-stu-id="b1e98-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="b1e98-113">Zostanie wyświetlony wynik, który reprezentuje liczbę podniesioną do potęgi.</span><span class="sxs-lookup"><span data-stu-id="b1e98-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="b1e98-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b1e98-114">Compiling the Code</span></span>  
  
- <span data-ttu-id="b1e98-115">Uwzględnij przestrzeń nazw System. LINQ. Expressions.</span><span class="sxs-lookup"><span data-stu-id="b1e98-115">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1e98-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1e98-116">See also</span></span>

- [<span data-ttu-id="b1e98-117">Drzewa wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1e98-117">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="b1e98-118">Instrukcje: modyfikowanie drzew wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1e98-118">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
