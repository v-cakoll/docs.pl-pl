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
# <a name="how-to-modify-expression-trees-c"></a><span data-ttu-id="f1fd2-102">Jak zmodyfikować drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="f1fd2-102">How to modify expression trees (C#)</span></span>
<span data-ttu-id="f1fd2-103">W tym temacie przedstawiono sposób modyfikowania drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="f1fd2-104">Drzewa wyrażeń są niezmienne, co oznacza, że nie można ich modyfikować bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="f1fd2-105">Aby zmienić drzewo wyrażenia, należy utworzyć kopię istniejącego drzewa wyrażeń i utworzyć kopię, wprowadzić wymagane zmiany.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="f1fd2-106">Klasy <xref:System.Linq.Expressions.ExpressionVisitor> można użyć do przechodzenia istniejącego drzewa wyrażeń i kopiowania każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="f1fd2-107">Aby zmodyfikować drzewo wyrażenia</span><span class="sxs-lookup"><span data-stu-id="f1fd2-107">To modify an expression tree</span></span>  
  
1. <span data-ttu-id="f1fd2-108">Utwórz nowy projekt **aplikacji konsolowej** .</span><span class="sxs-lookup"><span data-stu-id="f1fd2-108">Create a new **Console Application** project.</span></span>  
  
2. <span data-ttu-id="f1fd2-109">Dodaj dyrektywę `using` do pliku dla `System.Linq.Expressions` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-109">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3. <span data-ttu-id="f1fd2-110">Dodaj klasę `AndAlsoModifier` do projektu.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="f1fd2-111">Ta klasa dziedziczy klasę <xref:System.Linq.Expressions.ExpressionVisitor> i jest wyspecjalizowany do modyfikowania wyrażeń, które reprezentują operacje `AND` warunkowych.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="f1fd2-112">Zmienia te operacje z `AND` warunkowego na `OR`warunkowe.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="f1fd2-113">W tym celu Klasa zastępuje metodę <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> typu podstawowego, ponieważ wyrażenia warunkowe `AND` są reprezentowane jako wyrażenia binarne.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="f1fd2-114">W metodzie `VisitBinary`, jeśli wyrażenie, które jest przesyłane do niego reprezentuje operację warunkową `AND`, kod konstruuje nowe wyrażenie zawierające operator `OR` warunkowego zamiast operatora warunkowego `AND`.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="f1fd2-115">Jeśli wyrażenie, które jest przesyłane do `VisitBinary` nie reprezentuje operacji warunkowej `AND`, metoda jest uwzględniana w implementacji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="f1fd2-116">Metody klasy bazowej konstruują węzły, które są podobne do drzew wyrażeń, które są przenoszone, ale węzły mają swoje poddrzewa zamienione na drzewa wyrażeń, które są tworzone cyklicznie przez odwiedzających.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4. <span data-ttu-id="f1fd2-117">Dodaj dyrektywę `using` do pliku dla `System.Linq.Expressions` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-117">Add a `using` directive to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5. <span data-ttu-id="f1fd2-118">Dodaj kod do metody `Main` w pliku Program.cs, aby utworzyć drzewo wyrażenia i przekazać go do metody, która zmodyfikuje ją.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-118">Add code to the `Main` method in the Program.cs file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="f1fd2-119">Kod tworzy wyrażenie zawierające `AND` warunkowej.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="f1fd2-120">Następnie tworzy wystąpienie klasy `AndAlsoModifier` i przekazuje wyrażenie do metody `Modify` tej klasy.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="f1fd2-121">Wszystkie oryginalne i zmodyfikowane drzewa wyrażeń są zwracane w celu wyświetlenia zmiany.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6. <span data-ttu-id="f1fd2-122">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="f1fd2-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1fd2-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f1fd2-123">See also</span></span>

- [<span data-ttu-id="f1fd2-124">Jak wykonać drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="f1fd2-124">How to execute expression trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="f1fd2-125">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="f1fd2-125">Expression Trees (C#)</span></span>](./index.md)
