---
title: Jak zmodyfikować drzewa wyrażeń (C#)
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: e921c594497d02f5eb16cc60294e947e83636d7a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969903"
---
# <a name="how-to-modify-expression-trees-c"></a>Jak zmodyfikować drzewa wyrażeń (C#)
W tym temacie przedstawiono sposób modyfikowania drzewa wyrażenia. Drzewa wyrażeń są niezmienne, co oznacza, że nie można ich modyfikować bezpośrednio. Aby zmienić drzewo wyrażenia, należy utworzyć kopię istniejącego drzewa wyrażeń i utworzyć kopię, wprowadzić wymagane zmiany. Klasy <xref:System.Linq.Expressions.ExpressionVisitor> można użyć do przechodzenia istniejącego drzewa wyrażeń i kopiowania każdego z nich.  
  
### <a name="to-modify-an-expression-tree"></a>Aby zmodyfikować drzewo wyrażenia  
  
1. Utwórz nowy projekt **aplikacji konsolowej** .  
  
2. Dodaj dyrektywę `using` do pliku dla `System.Linq.Expressions` przestrzeni nazw.  
  
3. Dodaj klasę `AndAlsoModifier` do projektu.  
  
    ```csharp  
    public class AndAlsoModifier : ExpressionVisitor  
    {  
        public Expression Modify(Expression expression)  
        {  
            return Visit(expression);  
        }  
  
        protected override Expression VisitBinary(BinaryExpression b)  
        {  
            if (b.NodeType == ExpressionType.AndAlso)  
            {  
                Expression left = this.Visit(b.Left);  
                Expression right = this.Visit(b.Right);  
  
                // Make this binary expression an OrElse operation instead of an AndAlso operation.  
                return Expression.MakeBinary(ExpressionType.OrElse, left, right, b.IsLiftedToNull, b.Method);  
            }  
  
            return base.VisitBinary(b);  
        }  
    }  
    ```  
  
     Ta klasa dziedziczy klasę <xref:System.Linq.Expressions.ExpressionVisitor> i jest wyspecjalizowany do modyfikowania wyrażeń, które reprezentują operacje `AND` warunkowych. Zmienia te operacje z `AND` warunkowego na `OR`warunkowe. W tym celu Klasa zastępuje metodę <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> typu podstawowego, ponieważ wyrażenia warunkowe `AND` są reprezentowane jako wyrażenia binarne. W metodzie `VisitBinary`, jeśli wyrażenie, które jest przesyłane do niego reprezentuje operację warunkową `AND`, kod konstruuje nowe wyrażenie zawierające operator `OR` warunkowego zamiast operatora warunkowego `AND`. Jeśli wyrażenie, które jest przesyłane do `VisitBinary` nie reprezentuje operacji warunkowej `AND`, metoda jest uwzględniana w implementacji klasy podstawowej. Metody klasy bazowej konstruują węzły, które są podobne do drzew wyrażeń, które są przenoszone, ale węzły mają swoje poddrzewa zamienione na drzewa wyrażeń, które są tworzone cyklicznie przez odwiedzających.  
  
4. Dodaj dyrektywę `using` do pliku dla `System.Linq.Expressions` przestrzeni nazw.  
  
5. Dodaj kod do metody `Main` w pliku Program.cs, aby utworzyć drzewo wyrażenia i przekazać go do metody, która zmodyfikuje ją.  
  
    ```csharp  
    Expression<Func<string, bool>> expr = name => name.Length > 10 && name.StartsWith("G");  
    Console.WriteLine(expr);  
  
    AndAlsoModifier treeModifier = new AndAlsoModifier();  
    Expression modifiedExpr = treeModifier.Modify((Expression) expr);  
  
    Console.WriteLine(modifiedExpr);  
  
    /*  This code produces the following output:  
  
        name => ((name.Length > 10) && name.StartsWith("G"))  
        name => ((name.Length > 10) || name.StartsWith("G"))  
    */  
    ```  
  
     Kod tworzy wyrażenie zawierające `AND` warunkowej. Następnie tworzy wystąpienie klasy `AndAlsoModifier` i przekazuje wyrażenie do metody `Modify` tej klasy. Wszystkie oryginalne i zmodyfikowane drzewa wyrażeń są zwracane w celu wyświetlenia zmiany.  
  
6. Skompiluj i uruchom aplikację.  
  
## <a name="see-also"></a>Zobacz także

- [Jak wykonać drzewa wyrażeń (C#)](./how-to-execute-expression-trees.md)
- [Drzewa wyrażeń (C#)](./index.md)
