---
title: 'Instrukcje: Modyfikowanie drzew wyrażeń (C#)'
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 26c00f3acc7ab44e74a81e346ab1c017d95d53b5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59308643"
---
# <a name="how-to-modify-expression-trees-c"></a>Instrukcje: Modyfikowanie drzew wyrażeń (C#)
W tym temacie przedstawiono sposób modyfikowania drzewo wyrażenia. Drzewa wyrażeń są niezmienne, co oznacza, że nie można ich modyfikować bezpośrednio. Aby zmienić drzewo wyrażenia, należy utworzyć kopię istniejącej drzewa wyrażeń i podczas tworzenia kopii, wprowadź wymagane zmiany. Możesz użyć <xref:System.Linq.Expressions.ExpressionVisitor> klasy Przenoszenie istniejących drzewa wyrażeń i skopiuj każdy węzeł, który go wizyty.  
  
### <a name="to-modify-an-expression-tree"></a>Aby zmodyfikować drzewa wyrażeń  
  
1. Utwórz nową **aplikację Konsolową** projektu.  
  
2. Dodaj `using` dyrektywy w pliku `System.Linq.Expressions` przestrzeni nazw.  
  
3. Dodaj `AndAlsoModifier` klasy do projektu.  
  
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
  
     Ta klasa dziedziczy <xref:System.Linq.Expressions.ExpressionVisitor> klasy i jest przeznaczone do modyfikowania wyrażeń, które reprezentują warunkowego `AND` operacji. Zmienia te operacje z warunkowego `AND` do warunkowego `OR`. Aby to zrobić, przesłonięć klasy <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metody typu podstawowego, ponieważ warunkowego `AND` wyrażenia są reprezentowane jako wyrażenia binarnego. W `VisitBinary` metody, jeśli wyrażenie, który jest przekazywany do niego reprezentuje warunkowe `AND` operacji, kod tworzy nowe wyrażenie, które zawiera warunkową `OR` operator zamiast warunkową `AND` operator. Jeśli wyrażenie, które są przekazywane do `VisitBinary` nie reprezentuje warunkowe `AND` operacja, metoda odracza do implementacji klasy podstawowej. Metody klasy bazowej, węzły konstrukcji, które są podobne do drzew wyrażeń, które są przekazywane w, ale węzły mają ich drzew podrzędnych zastąpione drzew wyrażeń, które są generowane cyklicznie przez obiekt odwiedzający.  
  
4. Dodaj `using` dyrektywy w pliku `System.Linq.Expressions` przestrzeni nazw.  
  
5. Dodaj kod, aby `Main` metody w pliku Program.cs, aby utworzyć drzewo wyrażeń i przekazać go do metody, będzie go zmodyfikować.  
  
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
  
     Ten kod tworzy wyrażenia zawierającego warunkowe `AND` operacji. Następnie tworzy wystąpienie `AndAlsoModifier` klasy i przekazuje wyrażenia do `Modify` metody tej klasy. Zarówno oryginał, jak i drzewa wyrażeń zmodyfikowane są zwrócone do wyświetlenia zmiany.  
  
6. Skompilować i uruchomić aplikację.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wykonywanie drzew wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [Drzewa wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
