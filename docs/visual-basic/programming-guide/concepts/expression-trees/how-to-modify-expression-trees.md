---
title: 'Porady: modyfikowanie drzew wyrażeń (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: 92a0fb37e2a383c68beb2e4a56deb16f89a9bd28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643879"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a>Porady: modyfikowanie drzew wyrażeń (Visual Basic)
W tym temacie przedstawiono sposób modyfikowania drzewo wyrażenia. Drzewa wyrażeń są niezmienne, co oznacza, że nie można ich modyfikować bezpośrednio. Aby zmienić drzewo wyrażenia, należy utworzyć kopię istniejącej drzewo wyrażeń i podczas tworzenia kopii, wprowadź wymagane zmiany. Można użyć <xref:System.Linq.Expressions.ExpressionVisitor> klasy przechodzenia przez drzewo wyrażeń istniejących i skopiować na każdym węźle, który go odwiedza.  
  
### <a name="to-modify-an-expression-tree"></a>Aby zmodyfikować drzewa wyrażeń  
  
1.  Utwórz nową **aplikacji konsoli** projektu.  
  
2.  Dodaj `Imports` instrukcji do pliku `System.Linq.Expressions` przestrzeni nazw.  
  
3.  Dodaj `AndAlsoModifier` klasy do projektu.  
  
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
  
     Ta klasa dziedziczy <xref:System.Linq.Expressions.ExpressionVisitor> klasy i jest przeznaczone do modyfikowania wyrażeń, które reprezentują warunkowego `AND` operacji. Zmienia te operacje z warunkowego `AND` Conditional `OR`. W tym celu przesłonięć klasy <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metody typu podstawowego, ponieważ warunkowego `AND` wyrażenia są reprezentowane jako wyrażenia binarne. W `VisitBinary` metody, jeśli wyrażenie, które jest przekazywane do niego reprezentuje warunkowego `AND` operacji, kod tworzy nowe wyrażenie, które zawiera warunkowe `OR` operator zamiast warunkowe `AND` operator. Jeśli wyrażenie, które są przekazywane do `VisitBinary` nie reprezentuje warunkowego `AND` operacji, metoda różni się do implementacji klasy podstawowej. Metody klasy podstawowej konstrukcja węzłów, które są podobne do drzewa wyrażeń, które są przekazywane w, ale węzły mają ich drzew sub zastąpione drzewa wyrażeń, które są produkowane rekursywnie przez obiekt odwiedzający.  
  
4.  Dodaj `Imports` instrukcji do pliku `System.Linq.Expressions` przestrzeni nazw.  
  
5.  Dodaj kod, aby `Main` metody w pliku Module1.vb Utwórz drzewo wyrażeń i przekazać go do metody który zmodyfikuje go.  
  
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
  
     Kod tworzy wyrażenia zawierającego warunkowego `AND` operacji. Następnie tworzy wystąpienie `AndAlsoModifier` klasy i przekazuje wyrażenie `Modify` metody tej klasy. Zarówno oryginalnej i drzew wyrażeń zmodyfikowane są wyjściowych, aby pokazać zmiany.  
  
6.  Kompilowanie i uruchamianie aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: wykonywanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [Drzewa wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
