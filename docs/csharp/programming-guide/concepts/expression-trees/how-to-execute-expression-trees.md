---
title: Jak wykonać drzewa wyrażeń (C#)
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: e7d408ea154572dc8b45d2e67bca3f05837868d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73969881"
---
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="b1e13-102">Jak wykonać drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="b1e13-102">How to execute expression trees (C#)</span></span>
<span data-ttu-id="b1e13-103">W tym temacie przedstawiono sposób wykonywania drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="b1e13-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="b1e13-104">Wykonywanie drzewa wyrażeń może zwrócić wartość lub może po prostu wykonać akcję, taką jak wywoływanie metody.</span><span class="sxs-lookup"><span data-stu-id="b1e13-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="b1e13-105">Można wykonać tylko drzewa wyrażeń reprezentujące wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="b1e13-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="b1e13-106">Drzewa wyrażeń reprezentujące wyrażenia <xref:System.Linq.Expressions.LambdaExpression> lambda są typu lub <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="b1e13-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="b1e13-107">Aby wykonać te drzewa <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> wyrażeń, wywołać metodę, aby utworzyć delegata wykonywalnego, a następnie wywołać delegata.</span><span class="sxs-lookup"><span data-stu-id="b1e13-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1e13-108">Jeśli typ delegata nie jest znany, oznacza to, że wyrażenie <xref:System.Linq.Expressions.LambdaExpression> lambda jest typu, a nie <xref:System.Linq.Expressions.Expression%601>, należy wywołać <xref:System.Delegate.DynamicInvoke%2A> metodę na delegata zamiast wywoływać go bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="b1e13-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="b1e13-109">Jeśli drzewo wyrażeń nie reprezentuje wyrażenia lambda, można utworzyć nowe wyrażenie lambda, które <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> ma oryginalne drzewo wyrażeń jako jego treść, wywołując metodę.</span><span class="sxs-lookup"><span data-stu-id="b1e13-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="b1e13-110">Następnie można wykonać wyrażenie lambda zgodnie z opisem wcześniej w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="b1e13-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1e13-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="b1e13-111">Example</span></span>  
 <span data-ttu-id="b1e13-112">W poniższym przykładzie kodu pokazano, jak wykonać drzewo wyrażeń, który reprezentuje podnoszenie liczby do zasilania, tworząc wyrażenie lambda i wykonując go.</span><span class="sxs-lookup"><span data-stu-id="b1e13-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="b1e13-113">Wyświetlany jest wynik, który reprezentuje liczbę podniesioną do potęgi.</span><span class="sxs-lookup"><span data-stu-id="b1e13-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="b1e13-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="b1e13-114">Compiling the Code</span></span>  
  
- <span data-ttu-id="b1e13-115">Dołącz obszar nazw System.Linq.Expressions.</span><span class="sxs-lookup"><span data-stu-id="b1e13-115">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1e13-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b1e13-116">See also</span></span>

- [<span data-ttu-id="b1e13-117">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="b1e13-117">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="b1e13-118">Jak zmodyfikować drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="b1e13-118">How to modify expression trees (C#)</span></span>](./how-to-modify-expression-trees.md)
