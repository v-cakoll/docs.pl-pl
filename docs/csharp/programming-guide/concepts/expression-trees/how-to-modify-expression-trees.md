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
# <a name="how-to-modify-expression-trees-c"></a><span data-ttu-id="68e87-102">Instrukcje: Modyfikowanie drzew wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="68e87-102">How to: Modify Expression Trees (C#)</span></span>
<span data-ttu-id="68e87-103">W tym temacie przedstawiono sposób modyfikowania drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="68e87-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="68e87-104">Drzewa wyrażeń są niezmienne, co oznacza, że nie można ich modyfikować bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="68e87-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="68e87-105">Aby zmienić drzewo wyrażenia, należy utworzyć kopię istniejącej drzewa wyrażeń i podczas tworzenia kopii, wprowadź wymagane zmiany.</span><span class="sxs-lookup"><span data-stu-id="68e87-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="68e87-106">Możesz użyć <xref:System.Linq.Expressions.ExpressionVisitor> klasy Przenoszenie istniejących drzewa wyrażeń i skopiuj każdy węzeł, który go wizyty.</span><span class="sxs-lookup"><span data-stu-id="68e87-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="68e87-107">Aby zmodyfikować drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="68e87-107">To modify an expression tree</span></span>  
  
1. <span data-ttu-id="68e87-108">Utwórz nową **aplikację Konsolową** projektu.</span><span class="sxs-lookup"><span data-stu-id="68e87-108">Create a new **Console Application** project.</span></span>  
  
2. <span data-ttu-id="68e87-109">Dodaj `using` dyrektywy w pliku `System.Linq.Expressions` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="68e87-109">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3. <span data-ttu-id="68e87-110">Dodaj `AndAlsoModifier` klasy do projektu.</span><span class="sxs-lookup"><span data-stu-id="68e87-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="68e87-111">Ta klasa dziedziczy <xref:System.Linq.Expressions.ExpressionVisitor> klasy i jest przeznaczone do modyfikowania wyrażeń, które reprezentują warunkowego `AND` operacji.</span><span class="sxs-lookup"><span data-stu-id="68e87-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="68e87-112">Zmienia te operacje z warunkowego `AND` do warunkowego `OR`.</span><span class="sxs-lookup"><span data-stu-id="68e87-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="68e87-113">Aby to zrobić, przesłonięć klasy <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metody typu podstawowego, ponieważ warunkowego `AND` wyrażenia są reprezentowane jako wyrażenia binarnego.</span><span class="sxs-lookup"><span data-stu-id="68e87-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="68e87-114">W `VisitBinary` metody, jeśli wyrażenie, który jest przekazywany do niego reprezentuje warunkowe `AND` operacji, kod tworzy nowe wyrażenie, które zawiera warunkową `OR` operator zamiast warunkową `AND` operator.</span><span class="sxs-lookup"><span data-stu-id="68e87-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="68e87-115">Jeśli wyrażenie, które są przekazywane do `VisitBinary` nie reprezentuje warunkowe `AND` operacja, metoda odracza do implementacji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="68e87-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="68e87-116">Metody klasy bazowej, węzły konstrukcji, które są podobne do drzew wyrażeń, które są przekazywane w, ale węzły mają ich drzew podrzędnych zastąpione drzew wyrażeń, które są generowane cyklicznie przez obiekt odwiedzający.</span><span class="sxs-lookup"><span data-stu-id="68e87-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4. <span data-ttu-id="68e87-117">Dodaj `using` dyrektywy w pliku `System.Linq.Expressions` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="68e87-117">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5. <span data-ttu-id="68e87-118">Dodaj kod, aby `Main` metody w pliku Program.cs, aby utworzyć drzewo wyrażeń i przekazać go do metody, będzie go zmodyfikować.</span><span class="sxs-lookup"><span data-stu-id="68e87-118">Add code to the `Main` method in the Program.cs file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="68e87-119">Ten kod tworzy wyrażenia zawierającego warunkowe `AND` operacji.</span><span class="sxs-lookup"><span data-stu-id="68e87-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="68e87-120">Następnie tworzy wystąpienie `AndAlsoModifier` klasy i przekazuje wyrażenia do `Modify` metody tej klasy.</span><span class="sxs-lookup"><span data-stu-id="68e87-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="68e87-121">Zarówno oryginał, jak i drzewa wyrażeń zmodyfikowane są zwrócone do wyświetlenia zmiany.</span><span class="sxs-lookup"><span data-stu-id="68e87-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6. <span data-ttu-id="68e87-122">Skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="68e87-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68e87-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68e87-123">See also</span></span>

- [<span data-ttu-id="68e87-124">Instrukcje: Wykonywanie drzew wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="68e87-124">How to: Execute Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="68e87-125">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="68e87-125">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)
