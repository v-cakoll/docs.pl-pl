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
# <a name="how-to-execute-expression-trees-c"></a>Jak wykonać drzewa wyrażeń (C#)
W tym temacie przedstawiono sposób wykonywania drzewa wyrażeń. Wykonywanie drzewa wyrażeń może zwrócić wartość lub może po prostu wykonać akcję, taką jak wywoływanie metody.  
  
 Można wykonać tylko drzewa wyrażeń reprezentujące wyrażenia lambda. Drzewa wyrażeń reprezentujące wyrażenia <xref:System.Linq.Expressions.LambdaExpression> lambda są typu lub <xref:System.Linq.Expressions.Expression%601>. Aby wykonać te drzewa <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> wyrażeń, wywołać metodę, aby utworzyć delegata wykonywalnego, a następnie wywołać delegata.  
  
> [!NOTE]
> Jeśli typ delegata nie jest znany, oznacza to, że wyrażenie <xref:System.Linq.Expressions.LambdaExpression> lambda jest typu, a nie <xref:System.Linq.Expressions.Expression%601>, należy wywołać <xref:System.Delegate.DynamicInvoke%2A> metodę na delegata zamiast wywoływać go bezpośrednio.  
  
 Jeśli drzewo wyrażeń nie reprezentuje wyrażenia lambda, można utworzyć nowe wyrażenie lambda, które <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> ma oryginalne drzewo wyrażeń jako jego treść, wywołując metodę. Następnie można wykonać wyrażenie lambda zgodnie z opisem wcześniej w tej sekcji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu pokazano, jak wykonać drzewo wyrażeń, który reprezentuje podnoszenie liczby do zasilania, tworząc wyrażenie lambda i wykonując go. Wyświetlany jest wynik, który reprezentuje liczbę podniesioną do potęgi.  
  
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
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
- Dołącz obszar nazw System.Linq.Expressions.  
  
## <a name="see-also"></a>Zobacz też

- [Drzewa wyrażeń (C#)](./index.md)
- [Jak zmodyfikować drzewa wyrażeń (C#)](./how-to-modify-expression-trees.md)
