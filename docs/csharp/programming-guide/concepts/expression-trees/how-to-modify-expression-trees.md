---
title: Jak zmodyfikować drzewa wyrażeń (C#)
description: Dowiedz się, jak modyfikować drzewo wyrażeń, tworząc kopię istniejącego drzewa wyrażeń i wprowadzając wymagane zmiany.
ms.date: 07/20/2015
ms.assetid: 9b0cd8c2-457e-4833-9e36-31e79545f442
ms.openlocfilehash: 45aea18e253811d4e5c60f23f7f8496d4358f64c
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105606"
---
# <a name="how-to-modify-expression-trees-c"></a><span data-ttu-id="f4878-103">Jak zmodyfikować drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="f4878-103">How to modify expression trees (C#)</span></span>
<span data-ttu-id="f4878-104">W tym temacie przedstawiono sposób modyfikowania drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f4878-104">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="f4878-105">Drzewa wyrażeń są niezmienne, co oznacza, że nie można ich modyfikować bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="f4878-105">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="f4878-106">Aby zmienić drzewo wyrażenia, należy utworzyć kopię istniejącego drzewa wyrażeń i utworzyć kopię, wprowadzić wymagane zmiany.</span><span class="sxs-lookup"><span data-stu-id="f4878-106">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="f4878-107">Można użyć <xref:System.Linq.Expressions.ExpressionVisitor> klasy do przechodzenia istniejącego drzewa wyrażeń i kopiowania każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="f4878-107">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="f4878-108">Aby zmodyfikować drzewo wyrażenia</span><span class="sxs-lookup"><span data-stu-id="f4878-108">To modify an expression tree</span></span>  
  
1. <span data-ttu-id="f4878-109">Utwórz nowy projekt **aplikacji konsolowej** .</span><span class="sxs-lookup"><span data-stu-id="f4878-109">Create a new **Console Application** project.</span></span>  
  
2. <span data-ttu-id="f4878-110">Dodaj `using` dyrektywę do pliku dla `System.Linq.Expressions` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f4878-110">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3. <span data-ttu-id="f4878-111">Dodaj `AndAlsoModifier` klasę do projektu.</span><span class="sxs-lookup"><span data-stu-id="f4878-111">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="f4878-112">Ta klasa dziedziczy <xref:System.Linq.Expressions.ExpressionVisitor> klasę i jest wyspecjalizowany do modyfikowania wyrażeń, które reprezentują `AND` operacje warunkowe.</span><span class="sxs-lookup"><span data-stu-id="f4878-112">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="f4878-113">Zmienia te operacje z warunkowego `AND` na warunkowe `OR` .</span><span class="sxs-lookup"><span data-stu-id="f4878-113">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="f4878-114">W tym celu Klasa zastępuje <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metodę typu podstawowego, ponieważ wyrażenia warunkowe `AND` są reprezentowane jako wyrażenia binarne.</span><span class="sxs-lookup"><span data-stu-id="f4878-114">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="f4878-115">W `VisitBinary` metodzie, jeśli wyrażenie, które jest przesyłane do niego reprezentuje operację warunkową `AND` , kod konstruuje nowe wyrażenie zawierające operator warunkowy `OR` zamiast operatora warunkowego `AND` .</span><span class="sxs-lookup"><span data-stu-id="f4878-115">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="f4878-116">Jeśli wyrażenie, które jest przesyłane do `VisitBinary` nie reprezentuje operacji warunkowej `AND` , metoda jest uwzględniana w implementacji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="f4878-116">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="f4878-117">Metody klasy bazowej konstruują węzły, które są podobne do drzew wyrażeń, które są przenoszone, ale węzły mają swoje poddrzewa zamienione na drzewa wyrażeń, które są tworzone cyklicznie przez odwiedzających.</span><span class="sxs-lookup"><span data-stu-id="f4878-117">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4. <span data-ttu-id="f4878-118">Dodaj `using` dyrektywę do pliku dla `System.Linq.Expressions` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f4878-118">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5. <span data-ttu-id="f4878-119">Dodaj kod do `Main` metody w pliku program.cs, aby utworzyć drzewo wyrażenia i przekazać go do metody, która zmodyfikuje ją.</span><span class="sxs-lookup"><span data-stu-id="f4878-119">Add code to the `Main` method in the Program.cs file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="f4878-120">Kod tworzy wyrażenie zawierające operację warunkową `AND` .</span><span class="sxs-lookup"><span data-stu-id="f4878-120">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="f4878-121">Następnie tworzy wystąpienie `AndAlsoModifier` klasy i przekazuje wyrażenie do `Modify` metody tej klasy.</span><span class="sxs-lookup"><span data-stu-id="f4878-121">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="f4878-122">Wszystkie oryginalne i zmodyfikowane drzewa wyrażeń są zwracane w celu wyświetlenia zmiany.</span><span class="sxs-lookup"><span data-stu-id="f4878-122">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6. <span data-ttu-id="f4878-123">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="f4878-123">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4878-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f4878-124">See also</span></span>

- [<span data-ttu-id="f4878-125">Wykonywanie drzew wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="f4878-125">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="f4878-126">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="f4878-126">Expression Trees (C#)</span></span>](./index.md)
