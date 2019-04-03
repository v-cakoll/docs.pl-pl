---
title: 'Instrukcje: Wykonywanie drzew wyrażeń (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: cccb0b301e1da6d82c616d56604ad46dfde83e2a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837523"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a>Instrukcje: Wykonywanie drzew wyrażeń (Visual Basic)
W tym temacie przedstawiono sposób wykonywania drzewo wyrażenia. Wykonywanie drzewa wyrażenie może zwrócić wartość lub go, że po prostu wykonać akcja, taka jak wywołanie metody.  
  
 Mogą być wykonywane tylko drzew wyrażeń, które reprezentują wyrażenia lambda. Drzewa wyrażeń, które reprezentują wyrażenia lambda są typu <xref:System.Linq.Expressions.LambdaExpression> lub <xref:System.Linq.Expressions.Expression%601>. Aby wykonać te drzew wyrażeń, należy wywołać <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodę, aby utworzyć delegat pliku wykonywalnego, a następnie wywołaj delegat.  
  
> [!NOTE]
>  Jeśli typ delegata nie jest znany, wyrażenie lambda jest typu <xref:System.Linq.Expressions.LambdaExpression> i nie <xref:System.Linq.Expressions.Expression%601>, należy wywołać <xref:System.Delegate.DynamicInvoke%2A> metody delegata zamiast wywołanie go bezpośrednio.  
  
 Drzewo wyrażenia nie reprezentuje wyrażenie lambda, można utworzyć nowe wyrażenie lambda, które ma oryginalnego drzewa wyrażeń jako jego treści, wywołując <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metody. Następnie można wykonać wyrażenia lambda, zgodnie z wcześniejszym opisem w tej sekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób wykonywania drzewo wyrażenia, reprezentujący zwiększenie liczby do potęgi przez tworzenie wyrażenia lambda i jej wykonanie. Wynik, który reprezentuje liczbę podniesioną do potęgi, jest wyświetlany.  
  
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
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
  
-   Dodaj odwołanie do biblioteki System.Core.dll, jeśli nie jest wywoływany.  
  
-   Obejmują System.Linq.Expressions przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz także

- [Drzewa wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Instrukcje: Modyfikowanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
