---
title: 'Porady: modyfikowanie drzew wyrażeń (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: d1309fff-28bd-4d8e-a2cf-75725999e8f2
ms.openlocfilehash: 92a0fb37e2a383c68beb2e4a56deb16f89a9bd28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-modify-expression-trees-visual-basic"></a><span data-ttu-id="34d3e-102">Porady: modyfikowanie drzew wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34d3e-102">How to: Modify Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="34d3e-103">W tym temacie przedstawiono sposób modyfikowania drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="34d3e-103">This topic shows you how to modify an expression tree.</span></span> <span data-ttu-id="34d3e-104">Drzewa wyrażeń są niezmienne, co oznacza, że nie można ich modyfikować bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="34d3e-104">Expression trees are immutable, which means that they cannot be modified directly.</span></span> <span data-ttu-id="34d3e-105">Aby zmienić drzewo wyrażenia, należy utworzyć kopię istniejącej drzewo wyrażeń i podczas tworzenia kopii, wprowadź wymagane zmiany.</span><span class="sxs-lookup"><span data-stu-id="34d3e-105">To change an expression tree, you must create a copy of an existing expression tree and when you create the copy, make the required changes.</span></span> <span data-ttu-id="34d3e-106">Można użyć <xref:System.Linq.Expressions.ExpressionVisitor> klasy przechodzenia przez drzewo wyrażeń istniejących i skopiować na każdym węźle, który go odwiedza.</span><span class="sxs-lookup"><span data-stu-id="34d3e-106">You can use the <xref:System.Linq.Expressions.ExpressionVisitor> class to traverse an existing expression tree and to copy each node that it visits.</span></span>  
  
### <a name="to-modify-an-expression-tree"></a><span data-ttu-id="34d3e-107">Aby zmodyfikować drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="34d3e-107">To modify an expression tree</span></span>  
  
1.  <span data-ttu-id="34d3e-108">Utwórz nową **aplikacji konsoli** projektu.</span><span class="sxs-lookup"><span data-stu-id="34d3e-108">Create a new **Console Application** project.</span></span>  
  
2.  <span data-ttu-id="34d3e-109">Dodaj `Imports` instrukcji do pliku `System.Linq.Expressions` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="34d3e-109">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
3.  <span data-ttu-id="34d3e-110">Dodaj `AndAlsoModifier` klasy do projektu.</span><span class="sxs-lookup"><span data-stu-id="34d3e-110">Add the `AndAlsoModifier` class to your project.</span></span>  
  
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
  
     <span data-ttu-id="34d3e-111">Ta klasa dziedziczy <xref:System.Linq.Expressions.ExpressionVisitor> klasy i jest przeznaczone do modyfikowania wyrażeń, które reprezentują warunkowego `AND` operacji.</span><span class="sxs-lookup"><span data-stu-id="34d3e-111">This class inherits the <xref:System.Linq.Expressions.ExpressionVisitor> class and is specialized to modify expressions that represent conditional `AND` operations.</span></span> <span data-ttu-id="34d3e-112">Zmienia te operacje z warunkowego `AND` Conditional `OR`.</span><span class="sxs-lookup"><span data-stu-id="34d3e-112">It changes these operations from a conditional `AND` to a conditional `OR`.</span></span> <span data-ttu-id="34d3e-113">W tym celu przesłonięć klasy <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> metody typu podstawowego, ponieważ warunkowego `AND` wyrażenia są reprezentowane jako wyrażenia binarne.</span><span class="sxs-lookup"><span data-stu-id="34d3e-113">To do this, the class overrides the <xref:System.Linq.Expressions.ExpressionVisitor.VisitBinary%2A> method of the base type, because conditional `AND` expressions are represented as binary expressions.</span></span> <span data-ttu-id="34d3e-114">W `VisitBinary` metody, jeśli wyrażenie, które jest przekazywane do niego reprezentuje warunkowego `AND` operacji, kod tworzy nowe wyrażenie, które zawiera warunkowe `OR` operator zamiast warunkowe `AND` operator.</span><span class="sxs-lookup"><span data-stu-id="34d3e-114">In the `VisitBinary` method, if the expression that is passed to it represents a conditional `AND` operation, the code constructs a new expression that contains the conditional `OR` operator instead of the conditional `AND` operator.</span></span> <span data-ttu-id="34d3e-115">Jeśli wyrażenie, które są przekazywane do `VisitBinary` nie reprezentuje warunkowego `AND` operacji, metoda różni się do implementacji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="34d3e-115">If the expression that is passed to `VisitBinary` does not represent a conditional `AND` operation, the method defers to the base class implementation.</span></span> <span data-ttu-id="34d3e-116">Metody klasy podstawowej konstrukcja węzłów, które są podobne do drzewa wyrażeń, które są przekazywane w, ale węzły mają ich drzew sub zastąpione drzewa wyrażeń, które są produkowane rekursywnie przez obiekt odwiedzający.</span><span class="sxs-lookup"><span data-stu-id="34d3e-116">The base class methods construct nodes that are like the expression trees that are passed in, but the nodes have their sub trees replaced with the expression trees that are produced recursively by the visitor.</span></span>  
  
4.  <span data-ttu-id="34d3e-117">Dodaj `Imports` instrukcji do pliku `System.Linq.Expressions` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="34d3e-117">Add an `Imports` statement to the file for the `System.Linq.Expressions` namespace.</span></span>  
  
5.  <span data-ttu-id="34d3e-118">Dodaj kod, aby `Main` metody w pliku Module1.vb Utwórz drzewo wyrażeń i przekazać go do metody który zmodyfikuje go.</span><span class="sxs-lookup"><span data-stu-id="34d3e-118">Add code to the `Main` method in the Module1.vb file to create an expression tree and pass it to the method that will modify it.</span></span>  
  
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
  
     <span data-ttu-id="34d3e-119">Kod tworzy wyrażenia zawierającego warunkowego `AND` operacji.</span><span class="sxs-lookup"><span data-stu-id="34d3e-119">The code creates an expression that contains a conditional `AND` operation.</span></span> <span data-ttu-id="34d3e-120">Następnie tworzy wystąpienie `AndAlsoModifier` klasy i przekazuje wyrażenie `Modify` metody tej klasy.</span><span class="sxs-lookup"><span data-stu-id="34d3e-120">It then creates an instance of the `AndAlsoModifier` class and passes the expression to the `Modify` method of this class.</span></span> <span data-ttu-id="34d3e-121">Zarówno oryginalnej i drzew wyrażeń zmodyfikowane są wyjściowych, aby pokazać zmiany.</span><span class="sxs-lookup"><span data-stu-id="34d3e-121">Both the original and the modified expression trees are outputted to show the change.</span></span>  
  
6.  <span data-ttu-id="34d3e-122">Kompilowanie i uruchamianie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="34d3e-122">Compile and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34d3e-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34d3e-123">See Also</span></span>  
 [<span data-ttu-id="34d3e-124">Porady: wykonywanie drzew wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34d3e-124">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [<span data-ttu-id="34d3e-125">Drzewa wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34d3e-125">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
