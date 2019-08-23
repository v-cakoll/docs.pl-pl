---
title: 'Instrukcje: Wykonywanie drzew wyrażeń (C#)'
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 4a73201d06d21964a40fbbe57fa952da35c5942c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924368"
---
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="7b685-102">Instrukcje: Wykonywanie drzew wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="7b685-102">How to: Execute Expression Trees (C#)</span></span>
<span data-ttu-id="7b685-103">W tym temacie pokazano, jak wykonać drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="7b685-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="7b685-104">Wykonanie drzewa wyrażenia może zwrócić wartość lub może po prostu wykonać akcję, taką jak wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="7b685-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="7b685-105">Można wykonywać tylko drzewa wyrażeń, które reprezentują wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="7b685-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="7b685-106">Drzewa wyrażeń, które reprezentują wyrażenia lambda, są <xref:System.Linq.Expressions.LambdaExpression> typu <xref:System.Linq.Expressions.Expression%601>lub.</span><span class="sxs-lookup"><span data-stu-id="7b685-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="7b685-107">Aby wykonać te drzewa wyrażeń, wywołaj <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodę, aby utworzyć delegata pliku wykonywalnego, a następnie Wywołaj delegata.</span><span class="sxs-lookup"><span data-stu-id="7b685-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b685-108">Jeśli typ delegata jest nieznany, to oznacza, że wyrażenie lambda jest typu <xref:System.Linq.Expressions.LambdaExpression> , a nie <xref:System.Linq.Expressions.Expression%601> <xref:System.Delegate.DynamicInvoke%2A> , należy wywołać metodę w delegatze zamiast wywoływania jej bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="7b685-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="7b685-109">Jeśli drzewo wyrażenia nie reprezentuje wyrażenia lambda, można utworzyć nowe wyrażenie lambda, które ma pierwotne drzewo wyrażenia jako jego treść, wywołując <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metodę.</span><span class="sxs-lookup"><span data-stu-id="7b685-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="7b685-110">Następnie można wykonać wyrażenie lambda zgodnie z opisem we wcześniejszej części tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="7b685-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7b685-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b685-111">Example</span></span>  
 <span data-ttu-id="7b685-112">Poniższy przykład kodu demonstruje, jak wykonać drzewo wyrażenia, które reprezentuje podnoszenie liczby do potęgi przez utworzenie wyrażenia lambda i jego wykonanie.</span><span class="sxs-lookup"><span data-stu-id="7b685-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="7b685-113">Zostanie wyświetlony wynik, który reprezentuje liczbę podniesioną do potęgi.</span><span class="sxs-lookup"><span data-stu-id="7b685-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
```csharp  
// The expression tree to execute.  
BinaryExpression be = Expression.Power(Expression.Constant(2D), Expression.Constant(3D));  
  
// Create a lambda expression.  
Expression<Func<double>> le = Expression.Lambda<Func<double>>(be);  
  
// Compile the lambda expression.  
Func<double> compiledExpression = le.Compile();  
  
// Execute the lambda expression.  
double result = compiledExpression();  
  
// Display the result.  
Console.WriteLine(result);  
  
// This code produces the following output:  
// 8  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7b685-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7b685-114">Compiling the Code</span></span>  
  
- <span data-ttu-id="7b685-115">Uwzględnij przestrzeń nazw System. LINQ. Expressions.</span><span class="sxs-lookup"><span data-stu-id="7b685-115">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b685-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b685-116">See also</span></span>

- [<span data-ttu-id="7b685-117">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="7b685-117">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="7b685-118">Instrukcje: Modyfikuj drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="7b685-118">How to: Modify Expression Trees (C#)</span></span>](./how-to-modify-expression-trees.md)
