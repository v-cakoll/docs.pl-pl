---
title: 'Instrukcje: Modyfikowanie drzew wyrażeń (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: a9b94cbd7bf24b0cc8efcfc66d8c5e7df4e27307
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305328"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a>Instrukcje: Modyfikowanie drzew wyrażeń (Visual Basic)
W tym temacie przedstawiono sposób modyfikowania drzewo wyrażenia. Drzewa wyrażeń są niezmienne, co oznacza, że nie można ich modyfikować bezpośrednio. Aby zmienić drzewo wyrażenia, należy utworzyć kopię istniejącej drzewa wyrażeń i podczas tworzenia kopii, wprowadź wymagane zmiany. Możesz użyć <xref:System.Linq.Expressions.ExpressionVisitor> klasy Przenoszenie istniejących drzewa wyrażeń i skopiuj każdy węzeł, który go wizyty.  
  
### <a name="to-modify-an-expression-tree"></a>Aby zmodyfikować drzewa wyrażeń  
  
1. Utwórz nową **aplikację Konsolową** projektu.  
  
2. Dodaj `Imports` instrukcji do pliku `System.Linq.Expressions` przestrzeni nazw.  
  
3. Dodaj `AndAlsoModifier` klasy do projektu.  
  
    ```vb  
    Public Class AndAlsoModifier  
        Inherits ExpressionVisitor  
  
        Public Function Modify(ByVal expr As Expression) As Expression  
            Return Visit(expr)  
        End Function  
  
        Protected Overrides Function VisitBinary(ByVal b As BinaryExpression) As Expression  
            If b.NodeType = ExpressionType.AndAlso Then  
                Dim left = Me.Visit(b.Left)  
                Dim right = Me.Visit(b.Right)  
  
                ' Make this binary expression an OrElse operation instead   
                ' of an AndAlso operation.  
                Return Expression.MakeBinary(ExpressionType.OrElse, left, right, _  
                                             b.IsLiftedToNull, b.Method)  
            End If  
  
            Return MyBase.VisitBinary(b)  
        End Function  
    End Class  
    ```  
  
     Ta klasa dziedziczy <xref:System.Linq.Expressions.ExpressionVisitor> klasy i jest przeznaczone do modyfikowania wyrażeń, które reprezentują warunkowego `AND` operacji. Zmienia te operacje z warunkowego `AND` do warunkowego `OR`. Aby to zrobić, przesłonięć klasy <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metody typu podstawowego, ponieważ warunkowego `AND` wyrażenia są reprezentowane jako wyrażenia binarnego. W `VisitBinary` metody, jeśli wyrażenie, który jest przekazywany do niego reprezentuje warunkowe `AND` operacji, kod tworzy nowe wyrażenie, które zawiera warunkową `OR` operator zamiast warunkową `AND` operator. Jeśli wyrażenie, które są przekazywane do `VisitBinary` nie reprezentuje warunkowe `AND` operacja, metoda odracza do implementacji klasy podstawowej. Metody klasy bazowej, węzły konstrukcji, które są podobne do drzew wyrażeń, które są przekazywane w, ale węzły mają ich drzew podrzędnych zastąpione drzew wyrażeń, które są generowane cyklicznie przez obiekt odwiedzający.  
  
4. Dodaj `Imports` instrukcji do pliku `System.Linq.Expressions` przestrzeni nazw.  
  
5. Dodaj kod, aby `Main` metody w pliku Module1.vb, aby utworzyć drzewo wyrażeń i przekazać go do metody, będzie go zmodyfikować.  
  
    ```vb  
    Dim expr As Expression(Of Func(Of String, Boolean)) = _  
        Function(name) name.Length > 10 AndAlso name.StartsWith("G")  
  
    Console.WriteLine(expr)  
  
    Dim modifier As New AndAlsoModifier()  
    Dim modifiedExpr = modifier.Modify(CType(expr, Expression))  
  
    Console.WriteLine(modifiedExpr)  
  
    ' This code produces the following output:  
    ' name => ((name.Length > 10) && name.StartsWith("G"))  
    ' name => ((name.Length > 10) || name.StartsWith("G"))  
    ```  
  
     Ten kod tworzy wyrażenia zawierającego warunkowe `AND` operacji. Następnie tworzy wystąpienie `AndAlsoModifier` klasy i przekazuje wyrażenia do `Modify` metody tej klasy. Zarówno oryginał, jak i drzewa wyrażeń zmodyfikowane są zwrócone do wyświetlenia zmiany.  
  
6. Skompilować i uruchomić aplikację.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wykonywanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Drzewa wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
