---
title: 'Porady: wykonywanie drzew wyrażeń (C#)'
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 0ebdcb603a1adf3602e897db284faa2f75b7de7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322094"
---
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="80414-102">Porady: wykonywanie drzew wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="80414-102">How to: Execute Expression Trees (C#)</span></span>
<span data-ttu-id="80414-103">W tym temacie przedstawiono sposób wykonania drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="80414-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="80414-104">Wykonywanie drzewo wyrażenia może zwracać wartości lub może on po prostu wykonać akcję, taką jak wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="80414-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="80414-105">Mogą być wykonywane tylko drzewa wyrażeń, które reprezentują wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="80414-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="80414-106">Drzewa wyrażeń, które reprezentują wyrażenia lambda są typu <xref:System.Linq.Expressions.LambdaExpression> lub <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="80414-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="80414-107">Aby wykonać te drzewa wyrażeń, należy wywołać <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodę, aby utworzyć delegata pliku wykonywalnego, a następnie wywołać delegata.</span><span class="sxs-lookup"><span data-stu-id="80414-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="80414-108">Jeśli typ delegata nie jest znany, wyrażenia lambda jest typu <xref:System.Linq.Expressions.LambdaExpression> i nie <xref:System.Linq.Expressions.Expression%601>, należy wywołać <xref:System.Delegate.DynamicInvoke%2A> metody obiektu delegowanego, zamiast wywoływania go bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="80414-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="80414-109">Drzewo wyrażenia nie reprezentuje wyrażenie lambda, można utworzyć nowego wyrażenia lambda z oryginalnego drzewa wyrażenia jako jego treść przez wywołanie metody <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metody.</span><span class="sxs-lookup"><span data-stu-id="80414-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="80414-110">Następnie można wykonać wyrażenia lambda, jak opisano wcześniej w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="80414-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80414-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="80414-111">Example</span></span>  
 <span data-ttu-id="80414-112">Poniższy przykład kodu pokazuje sposób wykonywania drzewo wyrażenia, które reprezentuje podniesienia liczby do potęgi przez tworzenie wyrażenia lambda i jej wykonanie.</span><span class="sxs-lookup"><span data-stu-id="80414-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="80414-113">Wynik, reprezentujący liczbę podniesioną do potęgi jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="80414-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="80414-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="80414-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="80414-115">Dodaj odwołanie projektu do System.Core.dll, jeśli nie jest już używany.</span><span class="sxs-lookup"><span data-stu-id="80414-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="80414-116">Obejmują System.Linq.Expressions przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="80414-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80414-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80414-117">See Also</span></span>  
 [<span data-ttu-id="80414-118">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="80414-118">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="80414-119">Porady: modyfikowanie drzew wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="80414-119">How to: Modify Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
