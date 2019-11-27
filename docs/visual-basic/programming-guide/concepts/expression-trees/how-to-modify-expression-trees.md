---
title: 'Porady: modyfikowanie drzew wyrażeń'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: 12ccad6df7d6c7d91ebc290163db362eae173209
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353744"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a>Instrukcje: modyfikowanie drzew wyrażeń (Visual Basic)

W tym temacie przedstawiono sposób modyfikowania drzewa wyrażenia. Drzewa wyrażeń są niezmienne, co oznacza, że nie można ich modyfikować bezpośrednio. Aby zmienić drzewo wyrażenia, należy utworzyć kopię istniejącego drzewa wyrażeń i utworzyć kopię, wprowadzić wymagane zmiany. Klasy <xref:System.Linq.Expressions.ExpressionVisitor> można użyć do przechodzenia istniejącego drzewa wyrażeń i kopiowania każdego z nich.

## <a name="to-modify-an-expression-tree"></a>Aby zmodyfikować drzewo wyrażenia

1. Utwórz nowy projekt **aplikacji konsolowej** .

2. Dodaj instrukcję `Imports` do pliku dla `System.Linq.Expressions` przestrzeni nazw.

3. Dodaj klasę `AndAlsoModifier` do projektu.

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

    Ta klasa dziedziczy klasę <xref:System.Linq.Expressions.ExpressionVisitor> i jest wyspecjalizowany do modyfikowania wyrażeń, które reprezentują operacje `AND` warunkowych. Zmienia te operacje z `AND` warunkowego na `OR`warunkowe. W tym celu Klasa zastępuje metodę <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> typu podstawowego, ponieważ wyrażenia warunkowe `AND` są reprezentowane jako wyrażenia binarne. W metodzie `VisitBinary`, jeśli wyrażenie, które jest przesyłane do niego reprezentuje operację warunkową `AND`, kod konstruuje nowe wyrażenie zawierające operator `OR` warunkowego zamiast operatora warunkowego `AND`. Jeśli wyrażenie, które jest przesyłane do `VisitBinary` nie reprezentuje operacji warunkowej `AND`, metoda jest uwzględniana w implementacji klasy podstawowej. Metody klasy bazowej konstruują węzły, które są podobne do drzew wyrażeń, które są przenoszone, ale węzły mają swoje poddrzewa zamienione na drzewa wyrażeń, które są tworzone cyklicznie przez odwiedzających.

4. Dodaj instrukcję `Imports` do pliku dla `System.Linq.Expressions` przestrzeni nazw.

5. Dodaj kod do metody `Main` w pliku Module1. vb, aby utworzyć drzewo wyrażenia i przekazać go do metody, która zmodyfikuje ją.

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

    Kod tworzy wyrażenie zawierające `AND` warunkowej. Następnie tworzy wystąpienie klasy `AndAlsoModifier` i przekazuje wyrażenie do metody `Modify` tej klasy. Wszystkie oryginalne i zmodyfikowane drzewa wyrażeń są zwracane w celu wyświetlenia zmiany.

6. Skompiluj i uruchom aplikację.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: wykonywanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Drzewa wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
