---
title: 'Instrukcje: Wykonywanie drzew wyrażeń (C#)'
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 202118fa33b80a9a94b0d902ff2d9f90185e550b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595086"
---
# <a name="how-to-execute-expression-trees-c"></a>Instrukcje: Wykonywanie drzew wyrażeń (C#)
W tym temacie pokazano, jak wykonać drzewo wyrażenia. Wykonanie drzewa wyrażenia może zwrócić wartość lub może po prostu wykonać akcję, taką jak wywołanie metody.  
  
 Można wykonywać tylko drzewa wyrażeń, które reprezentują wyrażenia lambda. Drzewa wyrażeń, które reprezentują wyrażenia lambda, są <xref:System.Linq.Expressions.LambdaExpression> typu <xref:System.Linq.Expressions.Expression%601>lub. Aby wykonać te drzewa wyrażeń, wywołaj <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodę, aby utworzyć delegata pliku wykonywalnego, a następnie Wywołaj delegata.  
  
> [!NOTE]
>  Jeśli typ delegata jest nieznany, to oznacza, że wyrażenie lambda jest typu <xref:System.Linq.Expressions.LambdaExpression> , a nie <xref:System.Linq.Expressions.Expression%601> <xref:System.Delegate.DynamicInvoke%2A> , należy wywołać metodę w delegatze zamiast wywoływania jej bezpośrednio.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Drzewa wyrażeń (C#)](./index.md)
- [Instrukcje: Modyfikuj drzewa wyrażeń (C#)](./how-to-modify-expression-trees.md)
