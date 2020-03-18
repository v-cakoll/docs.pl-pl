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
# <a name="how-to-modify-expression-trees-c"></a><span data-ttu-id="faed2-102">Jak zmodyfikować drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="faed2-102">How to modify expression trees (C#)</span></span>
<span data-ttu-id="faed2-103">W tym temacie przedstawiono sposób modyfikowania drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="faed2-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="faed2-104">Drzewa wyrażeń są niezmienne, co oznacza, że nie można ich modyfikować bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="faed2-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="faed2-105">Aby zmienić drzewo wyrażeń, należy utworzyć kopię istniejącego drzewa wyrażeń, a podczas tworzenia kopii należy wprowadzić wymagane zmiany.</span><span class="sxs-lookup"><span data-stu-id="faed2-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="faed2-106">Klasa służy <xref:System.Linq.Expressions.ExpressionVisitor> do przechodzenia przez istniejące drzewo wyrażeń i skopiować każdy węzeł, który odwiedza.</span><span class="sxs-lookup"><span data-stu-id="faed2-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="faed2-107">Aby zmodyfikować drzewo wyrażeń</span><span class="sxs-lookup"><span data-stu-id="faed2-107">To modify an expression tree</span></span>  
  
1. <span data-ttu-id="faed2-108">Utwórz nowy projekt **aplikacji konsoli.**</span><span class="sxs-lookup"><span data-stu-id="faed2-108">Create a new **Console Application** project.</span></span>  
  
2. <span data-ttu-id="faed2-109">Dodaj `using` dyrektywę do pliku `System.Linq.Expressions` obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="faed2-109">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3. <span data-ttu-id="faed2-110">Dodaj `AndAlsoModifier` klasę do projektu.</span><span class="sxs-lookup"><span data-stu-id="faed2-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="faed2-111">Ta klasa dziedziczy <xref:System.Linq.Expressions.ExpressionVisitor> klasę i specjalizuje się `AND` w modyfikowaniu wyrażeń reprezentujących operacje warunkowe.</span><span class="sxs-lookup"><span data-stu-id="faed2-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="faed2-112">Zmienia te operacje `AND` z warunkowego na warunkowy `OR`.</span><span class="sxs-lookup"><span data-stu-id="faed2-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="faed2-113">Aby to zrobić, klasa <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> zastępuje metodę typu podstawowego, ponieważ wyrażenia warunkowe `AND` są reprezentowane jako wyrażenia binarne.</span><span class="sxs-lookup"><span data-stu-id="faed2-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="faed2-114">W `VisitBinary` metodzie, jeśli wyrażenie, które jest przekazywane `AND` do niego reprezentuje operację warunkową, kod tworzy nowe wyrażenie, które zawiera operator warunkowy `OR` zamiast operatora warunkowego. `AND`</span><span class="sxs-lookup"><span data-stu-id="faed2-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="faed2-115">Jeśli wyrażenie, które `VisitBinary` jest przekazywane do `AND` nie reprezentuje operacji warunkowej, metoda odracza implementacji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="faed2-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="faed2-116">Metody klasy podstawowej konstruować węzły, które są jak drzewa wyrażeń, które są przekazywane w, ale węzły mają ich poddrzewa zastąpione drzewa wyrażeń, które są produkowane cyklicznie przez odwiedzającego.</span><span class="sxs-lookup"><span data-stu-id="faed2-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4. <span data-ttu-id="faed2-117">Dodaj `using` dyrektywę do pliku `System.Linq.Expressions` obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="faed2-117">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5. <span data-ttu-id="faed2-118">Dodaj kod `Main` do metody w Program.cs pliku, aby utworzyć drzewo wyrażeń i przekazać go do metody, która będzie go modyfikować.</span><span class="sxs-lookup"><span data-stu-id="faed2-118">Add code to the `Main` method in the Program.cs file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="faed2-119">Kod tworzy wyrażenie, które `AND` zawiera operację warunkową.</span><span class="sxs-lookup"><span data-stu-id="faed2-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="faed2-120">Następnie tworzy wystąpienie `AndAlsoModifier` klasy i przekazuje wyrażenie `Modify` do metody tej klasy.</span><span class="sxs-lookup"><span data-stu-id="faed2-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="faed2-121">Zarówno oryginalne, jak i zmodyfikowane drzewa wyrażeń są wyprowadzane, aby pokazać zmianę.</span><span class="sxs-lookup"><span data-stu-id="faed2-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6. <span data-ttu-id="faed2-122">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="faed2-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faed2-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="faed2-123">See also</span></span>

- [<span data-ttu-id="faed2-124">Jak wykonać drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="faed2-124">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="faed2-125">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="faed2-125">Expression Trees (C#)</span></span>](./index.md)
