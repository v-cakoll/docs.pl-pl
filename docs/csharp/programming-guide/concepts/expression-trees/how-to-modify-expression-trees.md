---
title: Jak zmodyfikować drzewa wyrażeń (C#)
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: e921c594497d02f5eb16cc60294e947e83636d7a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73969903"
---
# <a name="how-to-modify-expression-trees-c"></a>Jak zmodyfikować drzewa wyrażeń (C#)
W tym temacie przedstawiono sposób modyfikowania drzewa wyrażeń. Drzewa wyrażeń są niezmienne, co oznacza, że nie można ich modyfikować bezpośrednio. Aby zmienić drzewo wyrażeń, należy utworzyć kopię istniejącego drzewa wyrażeń, a podczas tworzenia kopii należy wprowadzić wymagane zmiany. Klasa służy <xref:System.Linq.Expressions.ExpressionVisitor> do przechodzenia przez istniejące drzewo wyrażeń i skopiować każdy węzeł, który odwiedza.  
  
### <a name="to-modify-an-expression-tree"></a>Aby zmodyfikować drzewo wyrażeń  
  
1. Utwórz nowy projekt **aplikacji konsoli.**  
  
2. Dodaj `using` dyrektywę do pliku `System.Linq.Expressions` obszaru nazw.  
  
3. Dodaj `AndAlsoModifier` klasę do projektu.  
  
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
  
     Ta klasa dziedziczy <xref:System.Linq.Expressions.ExpressionVisitor> klasę i specjalizuje się `AND` w modyfikowaniu wyrażeń reprezentujących operacje warunkowe. Zmienia te operacje `AND` z warunkowego na warunkowy `OR`. Aby to zrobić, klasa <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> zastępuje metodę typu podstawowego, ponieważ wyrażenia warunkowe `AND` są reprezentowane jako wyrażenia binarne. W `VisitBinary` metodzie, jeśli wyrażenie, które jest przekazywane `AND` do niego reprezentuje operację warunkową, kod tworzy nowe wyrażenie, które zawiera operator warunkowy `OR` zamiast operatora warunkowego. `AND` Jeśli wyrażenie, które `VisitBinary` jest przekazywane do `AND` nie reprezentuje operacji warunkowej, metoda odracza implementacji klasy podstawowej. Metody klasy podstawowej konstruować węzły, które są jak drzewa wyrażeń, które są przekazywane w, ale węzły mają ich poddrzewa zastąpione drzewa wyrażeń, które są produkowane cyklicznie przez odwiedzającego.  
  
4. Dodaj `using` dyrektywę do pliku `System.Linq.Expressions` obszaru nazw.  
  
5. Dodaj kod `Main` do metody w Program.cs pliku, aby utworzyć drzewo wyrażeń i przekazać go do metody, która będzie go modyfikować.  
  
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
  
     Kod tworzy wyrażenie, które `AND` zawiera operację warunkową. Następnie tworzy wystąpienie `AndAlsoModifier` klasy i przekazuje wyrażenie `Modify` do metody tej klasy. Zarówno oryginalne, jak i zmodyfikowane drzewa wyrażeń są wyprowadzane, aby pokazać zmianę.  
  
6. Skompiluj i uruchom aplikację.  
  
## <a name="see-also"></a>Zobacz też

- [Jak wykonać drzewa wyrażeń (C#)](./how-to-execute-expression-trees.md)
- [Drzewa wyrażeń (C#)](./index.md)
