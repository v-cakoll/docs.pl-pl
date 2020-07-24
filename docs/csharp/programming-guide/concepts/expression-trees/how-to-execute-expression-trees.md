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
# <a name="how-to-execute-expression-trees-c"></a>Wykonywanie drzew wyrażeń (C#)
W tym temacie pokazano, jak wykonać drzewo wyrażenia. Wykonanie drzewa wyrażenia może zwrócić wartość lub może po prostu wykonać akcję, taką jak wywołanie metody.  
  
 Można wykonywać tylko drzewa wyrażeń, które reprezentują wyrażenia lambda. Drzewa wyrażeń, które reprezentują wyrażenia lambda, są typu <xref:System.Linq.Expressions.LambdaExpression> lub <xref:System.Linq.Expressions.Expression%601> . Aby wykonać te drzewa wyrażeń, wywołaj <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodę, aby utworzyć delegata pliku wykonywalnego, a następnie Wywołaj delegata.  
  
> [!NOTE]
> Jeśli typ delegata jest nieznany, to oznacza, że wyrażenie lambda jest typu, <xref:System.Linq.Expressions.LambdaExpression> a nie <xref:System.Linq.Expressions.Expression%601> , należy wywołać <xref:System.Delegate.DynamicInvoke%2A> metodę w delegatze zamiast wywoływania jej bezpośrednio.  
  
 Jeśli drzewo wyrażenia nie reprezentuje wyrażenia lambda, można utworzyć nowe wyrażenie lambda, które ma pierwotne drzewo wyrażenia jako jego treść, wywołując <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metodę. Następnie można wykonać wyrażenie lambda zgodnie z opisem we wcześniejszej części tej sekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje, jak wykonać drzewo wyrażenia, które reprezentuje podnoszenie liczby do potęgi przez utworzenie wyrażenia lambda i jego wykonanie. Zostanie wyświetlony wynik, który reprezentuje liczbę podniesioną do potęgi.  
  
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
  
- Uwzględnij przestrzeń nazw System. LINQ. Expressions.  
  
## <a name="see-also"></a>Zobacz też

- [Drzewa wyrażeń (C#)](./index.md)
- [Jak zmodyfikować drzewa wyrażeń (C#)](./how-to-modify-expression-trees.md)
