---
title: 'Instrukcje: Wykonywanie drzew wyrażeń (C#)'
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: acf841194ef0990d2eb00481454c89088f4616c8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586137"
---
# <a name="how-to-execute-expression-trees-c"></a>Instrukcje: Wykonywanie drzew wyrażeń (C#)
W tym temacie przedstawiono sposób wykonywania drzewo wyrażenia. Wykonywanie drzewa wyrażenie może zwrócić wartość lub go, że po prostu wykonać akcja, taka jak wywołanie metody.  
  
 Mogą być wykonywane tylko drzew wyrażeń, które reprezentują wyrażenia lambda. Drzewa wyrażeń, które reprezentują wyrażenia lambda są typu <xref:System.Linq.Expressions.LambdaExpression> lub <xref:System.Linq.Expressions.Expression%601>. Aby wykonać te drzew wyrażeń, należy wywołać <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodę, aby utworzyć delegat pliku wykonywalnego, a następnie wywołaj delegat.  
  
> [!NOTE]
>  Jeśli typ delegata nie jest znany, wyrażenie lambda jest typu <xref:System.Linq.Expressions.LambdaExpression> i nie <xref:System.Linq.Expressions.Expression%601>, należy wywołać <xref:System.Delegate.DynamicInvoke%2A> metody delegata zamiast wywołanie go bezpośrednio.  
  
 Drzewo wyrażenia nie reprezentuje wyrażenie lambda, można utworzyć nowe wyrażenie lambda, które ma oryginalnego drzewa wyrażeń jako jego treści, wywołując <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metody. Następnie można wykonać wyrażenia lambda, zgodnie z wcześniejszym opisem w tej sekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób wykonywania drzewo wyrażenia, reprezentujący zwiększenie liczby do potęgi przez tworzenie wyrażenia lambda i jej wykonanie. Wynik, który reprezentuje liczbę podniesioną do potęgi, jest wyświetlany.  
  
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
  
- Obejmują System.Linq.Expressions przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Drzewa wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
- [Instrukcje: Modyfikowanie drzew wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
