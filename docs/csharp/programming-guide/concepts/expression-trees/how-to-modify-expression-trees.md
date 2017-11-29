---
title: "Porady: modyfikowanie drzew wyrażeń (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4db0abec0df2bc4a17dca0ed1ee88b8a38b8ca8a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-expression-trees-c"></a>Porady: modyfikowanie drzew wyrażeń (C#)
W tym temacie przedstawiono sposób modyfikowania drzewo wyrażenia. Drzewa wyrażeń są niezmienne, co oznacza, że nie można ich modyfikować bezpośrednio. Aby zmienić drzewo wyrażenia, należy utworzyć kopię istniejącej drzewo wyrażeń i podczas tworzenia kopii, wprowadź wymagane zmiany. Można użyć <xref:System.Linq.Expressions.ExpressionVisitor> klasy przechodzenia przez drzewo wyrażeń istniejących i skopiować na każdym węźle, który go odwiedza.  
  
### <a name="to-modify-an-expression-tree"></a>Aby zmodyfikować drzewa wyrażeń  
  
1.  Utwórz nową **aplikacji konsoli** projektu.  
  
2.  Dodaj `using` dyrektywy w pliku `System.Linq.Expressions` przestrzeni nazw.  
  
3.  Dodaj `AndAlsoModifier` klasy do projektu.  
  
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
  
     Ta klasa dziedziczy <xref:System.Linq.Expressions.ExpressionVisitor> klasy i jest przeznaczone do modyfikowania wyrażeń, które reprezentują warunkowego `AND` operacji. Zmienia te operacje z warunkowego `AND` Conditional `OR`. W tym celu przesłonięć klasy <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metody typu podstawowego, ponieważ warunkowego `AND` wyrażenia są reprezentowane jako wyrażenia binarne. W `VisitBinary` metody, jeśli wyrażenie, które jest przekazywane do niego reprezentuje warunkowego `AND` operacji, kod tworzy nowe wyrażenie, które zawiera warunkowe `OR` operator zamiast warunkowe `AND` operator. Jeśli wyrażenie, które są przekazywane do `VisitBinary` nie reprezentuje warunkowego `AND` operacji, metoda różni się do implementacji klasy podstawowej. Metody klasy podstawowej konstrukcja węzłów, które są podobne do drzewa wyrażeń, które są przekazywane w, ale węzły mają ich drzew sub zastąpione drzewa wyrażeń, które są produkowane rekursywnie przez obiekt odwiedzający.  
  
4.  Dodaj `using` dyrektywy w pliku `System.Linq.Expressions` przestrzeni nazw.  
  
5.  Dodaj kod, aby `Main` metody w pliku Program.cs Utwórz drzewo wyrażeń i przekazać go do metody który zmodyfikuje go.  
  
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
  
     Kod tworzy wyrażenia zawierającego warunkowego `AND` operacji. Następnie tworzy wystąpienie `AndAlsoModifier` klasy i przekazuje wyrażenie `Modify` metody tej klasy. Zarówno oryginalnej i drzew wyrażeń zmodyfikowane są wyjściowych, aby pokazać zmiany.  
  
6.  Kompilowanie i uruchamianie aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: wykonywanie drzew wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [Drzewa wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
