---
title: "Porady: wykonywanie drzew wyrażeń (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9a87c9893de2b70c47f0ed78a92adc6bce10db7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-execute-expression-trees-c"></a>Porady: wykonywanie drzew wyrażeń (C#)
W tym temacie przedstawiono sposób wykonania drzewo wyrażenia. Wykonywanie drzewo wyrażenia może zwracać wartości lub może on po prostu wykonać akcję, taką jak wywołanie metody.  
  
 Mogą być wykonywane tylko drzewa wyrażeń, które reprezentują wyrażenia lambda. Drzewa wyrażeń, które reprezentują wyrażenia lambda są typu <xref:System.Linq.Expressions.LambdaExpression> lub <xref:System.Linq.Expressions.Expression%601>. Aby wykonać te drzewa wyrażeń, należy wywołać <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodę, aby utworzyć delegata pliku wykonywalnego, a następnie wywołać delegata.  
  
> [!NOTE]
>  Jeśli typ delegata nie jest znany, wyrażenia lambda jest typu <xref:System.Linq.Expressions.LambdaExpression> i nie <xref:System.Linq.Expressions.Expression%601>, należy wywołać <xref:System.Delegate.DynamicInvoke%2A> metody obiektu delegowanego, zamiast wywoływania go bezpośrednio.  
  
 Drzewo wyrażenia nie reprezentuje wyrażenie lambda, można utworzyć nowego wyrażenia lambda z oryginalnego drzewa wyrażenia jako jego treść przez wywołanie metody <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metody. Następnie można wykonać wyrażenia lambda, jak opisano wcześniej w tej sekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób wykonywania drzewo wyrażenia, które reprezentuje podniesienia liczby do potęgi przez tworzenie wyrażenia lambda i jej wykonanie. Wynik, reprezentujący liczbę podniesioną do potęgi jest wyświetlany.  
  
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
  
-   Dodaj odwołanie projektu do System.Core.dll, jeśli nie jest już używany.  
  
-   Obejmują System.Linq.Expressions przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Drzewa wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [Porady: modyfikowanie drzew wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
