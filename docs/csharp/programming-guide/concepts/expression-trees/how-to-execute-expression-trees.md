---
title: Wykonywanie drzew wyrażeń (C#)
description: Dowiedz się, jak wykonać drzewo wyrażenia, aby zwrócić wartość, lub wykonać akcję, taką jak wywołanie metody.
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 9e306da545ba6c6275f36b8f6dd4e98bb91ed54e
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105615"
---
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="a3963-103">Wykonywanie drzew wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="a3963-103">How to execute expression trees (C#)</span></span>
<span data-ttu-id="a3963-104">W tym temacie pokazano, jak wykonać drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a3963-104">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="a3963-105">Wykonanie drzewa wyrażenia może zwrócić wartość lub może po prostu wykonać akcję, taką jak wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="a3963-105">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="a3963-106">Można wykonywać tylko drzewa wyrażeń, które reprezentują wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="a3963-106">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="a3963-107">Drzewa wyrażeń, które reprezentują wyrażenia lambda, są typu <xref:System.Linq.Expressions.LambdaExpression> lub <xref:System.Linq.Expressions.Expression%601> .</span><span class="sxs-lookup"><span data-stu-id="a3963-107">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="a3963-108">Aby wykonać te drzewa wyrażeń, wywołaj <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodę, aby utworzyć delegata pliku wykonywalnego, a następnie Wywołaj delegata.</span><span class="sxs-lookup"><span data-stu-id="a3963-108">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3963-109">Jeśli typ delegata jest nieznany, to oznacza, że wyrażenie lambda jest typu, <xref:System.Linq.Expressions.LambdaExpression> a nie <xref:System.Linq.Expressions.Expression%601> , należy wywołać <xref:System.Delegate.DynamicInvoke%2A> metodę w delegatze zamiast wywoływania jej bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="a3963-109">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="a3963-110">Jeśli drzewo wyrażenia nie reprezentuje wyrażenia lambda, można utworzyć nowe wyrażenie lambda, które ma pierwotne drzewo wyrażenia jako jego treść, wywołując <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metodę.</span><span class="sxs-lookup"><span data-stu-id="a3963-110">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="a3963-111">Następnie można wykonać wyrażenie lambda zgodnie z opisem we wcześniejszej części tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="a3963-111">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3963-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="a3963-112">Example</span></span>  
 <span data-ttu-id="a3963-113">Poniższy przykład kodu demonstruje, jak wykonać drzewo wyrażenia, które reprezentuje podnoszenie liczby do potęgi przez utworzenie wyrażenia lambda i jego wykonanie.</span><span class="sxs-lookup"><span data-stu-id="a3963-113">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="a3963-114">Zostanie wyświetlony wynik, który reprezentuje liczbę podniesioną do potęgi.</span><span class="sxs-lookup"><span data-stu-id="a3963-114">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="a3963-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="a3963-115">Compiling the Code</span></span>  
  
- <span data-ttu-id="a3963-116">Uwzględnij przestrzeń nazw System. LINQ. Expressions.</span><span class="sxs-lookup"><span data-stu-id="a3963-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3963-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a3963-117">See also</span></span>

- [<span data-ttu-id="a3963-118">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="a3963-118">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="a3963-119">Jak zmodyfikować drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="a3963-119">How to modify expression trees (C#)</span></span>](./how-to-modify-expression-trees.md)
