---
title: 'Porady: wykonywanie drzew wyrażeń'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: 7b7b08ea1a7a1310b1d98876be96f1fa28ecba91
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84375333"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a>Instrukcje: wykonywanie drzew wyrażeń (Visual Basic)
W tym temacie pokazano, jak wykonać drzewo wyrażenia. Wykonanie drzewa wyrażenia może zwrócić wartość lub może po prostu wykonać akcję, taką jak wywołanie metody.  
  
 Można wykonywać tylko drzewa wyrażeń, które reprezentują wyrażenia lambda. Drzewa wyrażeń, które reprezentują wyrażenia lambda, są typu <xref:System.Linq.Expressions.LambdaExpression> lub <xref:System.Linq.Expressions.Expression%601> . Aby wykonać te drzewa wyrażeń, wywołaj <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodę, aby utworzyć delegata pliku wykonywalnego, a następnie Wywołaj delegata.  
  
> [!NOTE]
> Jeśli typ delegata jest nieznany, to oznacza, że wyrażenie lambda jest typu, <xref:System.Linq.Expressions.LambdaExpression> a nie <xref:System.Linq.Expressions.Expression%601> , należy wywołać <xref:System.Delegate.DynamicInvoke%2A> metodę w delegatze zamiast wywoływania jej bezpośrednio.  
  
 Jeśli drzewo wyrażenia nie reprezentuje wyrażenia lambda, można utworzyć nowe wyrażenie lambda, które ma pierwotne drzewo wyrażenia jako jego treść, wywołując <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metodę. Następnie można wykonać wyrażenie lambda zgodnie z opisem we wcześniejszej części tej sekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje, jak wykonać drzewo wyrażenia, które reprezentuje podnoszenie liczby do potęgi przez utworzenie wyrażenia lambda i jego wykonanie. Zostanie wyświetlony wynik, który reprezentuje liczbę podniesioną do potęgi.  
  
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
  
## <a name="compile-the-code"></a>Kompiluj kod  
  
- Uwzględnij przestrzeń nazw System. LINQ. Expressions.  
  
## <a name="see-also"></a>Zobacz też

- [Drzewa wyrażeń (Visual Basic)](index.md)
- [Instrukcje: modyfikowanie drzew wyrażeń (Visual Basic)](how-to-modify-expression-trees.md)
