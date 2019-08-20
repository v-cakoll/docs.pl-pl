---
title: 'Instrukcje: Modyfikuj drzewa wyrażeń (C#)'
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 7875cf1ccca8866cc87ebec80701ad77ad2bea2d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595058"
---
# <a name="how-to-modify-expression-trees-c"></a>Instrukcje: Modyfikuj drzewa wyrażeń (C#)
W tym temacie przedstawiono sposób modyfikowania drzewa wyrażenia. Drzewa wyrażeń są niezmienne, co oznacza, że nie można ich modyfikować bezpośrednio. Aby zmienić drzewo wyrażenia, należy utworzyć kopię istniejącego drzewa wyrażeń i utworzyć kopię, wprowadzić wymagane zmiany. Można użyć <xref:System.Linq.Expressions.ExpressionVisitor> klasy do przechodzenia istniejącego drzewa wyrażeń i kopiowania każdego z nich.  
  
### <a name="to-modify-an-expression-tree"></a>Aby zmodyfikować drzewo wyrażenia  
  
1. Utwórz nowy projekt **aplikacji konsolowej** .  
  
2. Dodaj dyrektywę do pliku `System.Linq.Expressions` dla przestrzeni nazw. `using`  
  
3. `AndAlsoModifier` Dodaj klasę do projektu.  
  
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
  
     Ta klasa dziedziczy <xref:System.Linq.Expressions.ExpressionVisitor> klasę i jest wyspecjalizowany do modyfikowania wyrażeń, które reprezentują `AND` operacje warunkowe. Zmienia te operacje z warunkowego `AND` na warunkowe. `OR` W tym celu Klasa zastępuje <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metodę typu podstawowego, ponieważ wyrażenia warunkowe `AND` są reprezentowane jako wyrażenia binarne. W metodzie, jeśli wyrażenie, które jest przesyłane do niego reprezentuje operację warunkową `AND` , kod tworzy nowe wyrażenie zawierające operator warunkowy `OR` zamiast warunku `AND` `VisitBinary` zakład. Jeśli wyrażenie, które jest przesyłane do `VisitBinary` nie reprezentuje operacji warunkowej `AND` , metoda jest uwzględniana w implementacji klasy podstawowej. Metody klasy bazowej konstruują węzły, które są podobne do drzew wyrażeń, które są przenoszone, ale węzły mają swoje poddrzewa zamienione na drzewa wyrażeń, które są tworzone cyklicznie przez odwiedzających.  
  
4. Dodaj dyrektywę do pliku `System.Linq.Expressions` dla przestrzeni nazw. `using`  
  
5. Dodaj kod do `Main` metody w pliku program.cs, aby utworzyć drzewo wyrażenia i przekazać go do metody, która zmodyfikuje ją.  
  
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
  
     Kod tworzy wyrażenie zawierające operację warunkową `AND` . Następnie tworzy wystąpienie `AndAlsoModifier` klasy i przekazuje wyrażenie `Modify` do metody tej klasy. Wszystkie oryginalne i zmodyfikowane drzewa wyrażeń są zwracane w celu wyświetlenia zmiany.  
  
6. Skompiluj i uruchom aplikację.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wykonywanie drzew wyrażeń (C#)](./how-to-execute-expression-trees.md)
- [Drzewa wyrażeń (C#)](./index.md)
