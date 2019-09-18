---
title: 'Instrukcje: Modyfikuj drzewa wyrażeń (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: ac196b56f178659765437a97a25f46c04f8040fa
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054213"
---
# <a name="how-to-modify-expression-trees-visual-basic"></a><span data-ttu-id="e0153-102">Instrukcje: Modyfikuj drzewa wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0153-102">How to: Modify Expression Trees (Visual Basic)</span></span>

<span data-ttu-id="e0153-103">W tym temacie przedstawiono sposób modyfikowania drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="e0153-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="e0153-104">Drzewa wyrażeń są niezmienne, co oznacza, że nie można ich modyfikować bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="e0153-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="e0153-105">Aby zmienić drzewo wyrażenia, należy utworzyć kopię istniejącego drzewa wyrażeń i utworzyć kopię, wprowadzić wymagane zmiany.</span><span class="sxs-lookup"><span data-stu-id="e0153-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="e0153-106">Można użyć <xref:System.Linq.Expressions.ExpressionVisitor> klasy do przechodzenia istniejącego drzewa wyrażeń i kopiowania każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="e0153-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>

## <a name="to-modify-an-expression-tree"></a><span data-ttu-id="e0153-107">Aby zmodyfikować drzewo wyrażenia</span><span class="sxs-lookup"><span data-stu-id="e0153-107">To modify an expression tree</span></span>

1. <span data-ttu-id="e0153-108">Utwórz nowy projekt **aplikacji konsolowej** .</span><span class="sxs-lookup"><span data-stu-id="e0153-108">Create a new **Console Application** project.</span></span>

2. <span data-ttu-id="e0153-109">Dodaj instrukcję do pliku `System.Linq.Expressions` dla przestrzeni nazw. `Imports`</span><span class="sxs-lookup"><span data-stu-id="e0153-109">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>

3. <span data-ttu-id="e0153-110">`AndAlsoModifier` Dodaj klasę do projektu.</span><span class="sxs-lookup"><span data-stu-id="e0153-110">Add the `AndAlsoModifier` class to your project.</span></span>

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

    <span data-ttu-id="e0153-111">Ta klasa dziedziczy <xref:System.Linq.Expressions.ExpressionVisitor> klasę i jest wyspecjalizowany do modyfikowania wyrażeń, które reprezentują `AND` operacje warunkowe.</span><span class="sxs-lookup"><span data-stu-id="e0153-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="e0153-112">Zmienia te operacje z warunkowego `AND` na warunkowe. `OR`</span><span class="sxs-lookup"><span data-stu-id="e0153-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="e0153-113">W tym celu Klasa zastępuje <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metodę typu podstawowego, ponieważ wyrażenia warunkowe `AND` są reprezentowane jako wyrażenia binarne.</span><span class="sxs-lookup"><span data-stu-id="e0153-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="e0153-114">W metodzie, jeśli wyrażenie, które jest przesyłane do niego reprezentuje operację warunkową `AND` , kod tworzy nowe wyrażenie zawierające operator warunkowy `OR` zamiast warunku `AND` `VisitBinary` zakład.</span><span class="sxs-lookup"><span data-stu-id="e0153-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="e0153-115">Jeśli wyrażenie, które jest przesyłane do `VisitBinary` nie reprezentuje operacji warunkowej `AND` , metoda jest uwzględniana w implementacji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="e0153-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="e0153-116">Metody klasy bazowej konstruują węzły, które są podobne do drzew wyrażeń, które są przenoszone, ale węzły mają swoje poddrzewa zamienione na drzewa wyrażeń, które są tworzone cyklicznie przez odwiedzających.</span><span class="sxs-lookup"><span data-stu-id="e0153-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>

4. <span data-ttu-id="e0153-117">Dodaj instrukcję do pliku `System.Linq.Expressions` dla przestrzeni nazw. `Imports`</span><span class="sxs-lookup"><span data-stu-id="e0153-117">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>

5. <span data-ttu-id="e0153-118">Dodaj kod do `Main` metody w pliku Module1. vb, aby utworzyć drzewo wyrażenia i przekazać go do metody, która zmodyfikuje ją.</span><span class="sxs-lookup"><span data-stu-id="e0153-118">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span></span>

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

    <span data-ttu-id="e0153-119">Kod tworzy wyrażenie zawierające operację warunkową `AND` .</span><span class="sxs-lookup"><span data-stu-id="e0153-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="e0153-120">Następnie tworzy wystąpienie `AndAlsoModifier` klasy i przekazuje wyrażenie `Modify` do metody tej klasy.</span><span class="sxs-lookup"><span data-stu-id="e0153-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="e0153-121">Wszystkie oryginalne i zmodyfikowane drzewa wyrażeń są zwracane w celu wyświetlenia zmiany.</span><span class="sxs-lookup"><span data-stu-id="e0153-121">Both the original and the modified expression trees are outputted to show the change.</span></span>

6. <span data-ttu-id="e0153-122">Skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="e0153-122">Compile and run the application.</span></span>

## <a name="see-also"></a><span data-ttu-id="e0153-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0153-123">See also</span></span>

- [<span data-ttu-id="e0153-124">Instrukcje: Wykonywanie drzew wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0153-124">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="e0153-125">Drzewa wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0153-125">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
