---
title: "Porady: wykonywanie drzew wyrażeń (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45a13f13659472b7620b6df070815ace1d6fb0de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-execute-expression-trees-visual-basic"></a>Porady: wykonywanie drzew wyrażeń (Visual Basic)
W tym temacie przedstawiono sposób wykonania drzewo wyrażenia. Wykonywanie drzewo wyrażenia może zwracać wartości lub może on po prostu wykonać akcję, taką jak wywołanie metody.  
  
 Mogą być wykonywane tylko drzewa wyrażeń, które reprezentują wyrażenia lambda. Drzewa wyrażeń, które reprezentują wyrażenia lambda są typu <xref:System.Linq.Expressions.LambdaExpression> lub <xref:System.Linq.Expressions.Expression%601>. Aby wykonać te drzewa wyrażeń, należy wywołać <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> metodę, aby utworzyć delegata pliku wykonywalnego, a następnie wywołać delegata.  
  
> [!NOTE]
>  Jeśli typ delegata nie jest znany, wyrażenia lambda jest typu <xref:System.Linq.Expressions.LambdaExpression> i nie <xref:System.Linq.Expressions.Expression%601>, należy wywołać <xref:System.Delegate.DynamicInvoke%2A> metody obiektu delegowanego, zamiast wywoływania go bezpośrednio.  
  
 Drzewo wyrażenia nie reprezentuje wyrażenie lambda, można utworzyć nowego wyrażenia lambda z oryginalnego drzewa wyrażenia jako jego treść przez wywołanie metody <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> metody. Następnie można wykonać wyrażenia lambda, jak opisano wcześniej w tej sekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób wykonywania drzewo wyrażenia, które reprezentuje podniesienia liczby do potęgi przez tworzenie wyrażenia lambda i jej wykonanie. Wynik, reprezentujący liczbę podniesioną do potęgi jest wyświetlany.  
  
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
  
-   Dodaj odwołanie projektu do System.Core.dll, jeśli nie jest już używany.  
  
-   Obejmują System.Linq.Expressions przestrzeni nazw.  
  
## <a name="see-also"></a>Zobacz też  
 [Drzewa wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)  
 [Porady: modyfikowanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
