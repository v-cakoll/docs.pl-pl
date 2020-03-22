---
title: Drzewa wyrażeń
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
ms.openlocfilehash: b2266cbae0a9a8a07c2a3569efa33d162ffedd1d
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266420"
---
# <a name="expression-trees-visual-basic"></a><span data-ttu-id="d4c0a-102">Drzewa wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4c0a-102">Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="d4c0a-103">Drzewa wyrażeń reprezentują kod w strukturze danych podobnej do drzewa, gdzie każdy węzeł jest `x < y`wyrażeniem, na przykład wywołaniem metody lub operacją binarną, taką jak .</span><span class="sxs-lookup"><span data-stu-id="d4c0a-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="d4c0a-104">Można skompilować i uruchomić kod reprezentowany przez drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="d4c0a-105">Umożliwia to dynamiczną modyfikację kodu wykonywalnego, wykonywanie zapytań LINQ w różnych bazach danych i tworzenie zapytań dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="d4c0a-106">Aby uzyskać więcej informacji na temat drzew wyrażeń w LINQ, zobacz [Jak: Używanie drzew wyrażeń do tworzenia zapytań dynamicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="d4c0a-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="d4c0a-107">Drzewa wyrażeń są również używane w dynamicznym czasie wykonywania języka (DLR), aby zapewnić współdziałanie między językami dynamicznymi a programem .NET Framework i umożliwić modułom zbierającym kompilatora emitowanie drzew wyrażeń zamiast języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="d4c0a-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="d4c0a-108">Aby uzyskać więcej informacji na temat biblioteki DLR, zobacz [Omówienie dynamicznego środowiska wykonawczego języka](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d4c0a-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="d4c0a-109">Kompilator języka C# lub Visual Basic może utworzyć dla Ciebie drzewo wyrażeń na podstawie anonimowego wyrażenia <xref:System.Linq.Expressions> lambda lub można ręcznie utworzyć drzewa wyrażeń przy użyciu obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="d4c0a-110">Tworzenie drzew wyrażeń z wyrażeń Lambda</span><span class="sxs-lookup"><span data-stu-id="d4c0a-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="d4c0a-111">Gdy wyrażenie lambda jest przypisane do <xref:System.Linq.Expressions.Expression%601>zmiennej typu, kompilator emituje kod do tworzenia drzewa wyrażeń, który reprezentuje wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="d4c0a-112">Kompilator języka Visual Basic może generować drzewa wyrażeń tylko z wyrażenie lambdas (lub lambdas jednowierszowe).</span><span class="sxs-lookup"><span data-stu-id="d4c0a-112">The Visual Basic compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="d4c0a-113">Nie można przeanalizować instrukcji lambdas (lub lambdas wieloliniowych).</span><span class="sxs-lookup"><span data-stu-id="d4c0a-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="d4c0a-114">Aby uzyskać więcej informacji na temat wyrażeń lambda w języku Visual Basic, zobacz [Wyrażenia Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d4c0a-114">For more information about lambda expressions in Visual Basic, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="d4c0a-115">Poniższe przykłady kodu pokazują, jak kompilator języka Visual Basic utworzył `Function(num) num < 5`drzewo wyrażeń, które reprezentuje wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-115">The following code examples demonstrate how to have the Visual Basic compiler create an expression tree that represents the lambda expression `Function(num) num < 5`.</span></span>  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="d4c0a-116">Tworzenie drzew wyrażeń przy użyciu interfejsu API</span><span class="sxs-lookup"><span data-stu-id="d4c0a-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="d4c0a-117">Aby utworzyć drzewa wyrażeń przy <xref:System.Linq.Expressions.Expression> użyciu interfejsu API, należy użyć klasy.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="d4c0a-118">Ta klasa zawiera statyczne metody fabryczne, które tworzą węzły drzewa wyrażeń określonych typów, na przykład , <xref:System.Linq.Expressions.ParameterExpression>który reprezentuje zmienną lub parametr lub <xref:System.Linq.Expressions.MethodCallExpression>, który reprezentuje wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="d4c0a-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>a inne typy specyficzne dla wyrażenia <xref:System.Linq.Expressions> są również zdefiniowane w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="d4c0a-120">Te typy pochodzą od <xref:System.Linq.Expressions.Expression>typu abstrakcyjnego .</span><span class="sxs-lookup"><span data-stu-id="d4c0a-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="d4c0a-121">Poniższy przykład kodu pokazuje, jak utworzyć drzewo wyrażeń, który reprezentuje wyrażenie `Function(num) num < 5` lambda przy użyciu interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `Function(num) num < 5` by using the API.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Manually build the expression tree for the lambda expression num => num < 5.  
Dim numParam As ParameterExpression = Expression.Parameter(GetType(Integer), "num")  
Dim five As ConstantExpression = Expression.Constant(5, GetType(Integer))  
Dim numLessThanFive As BinaryExpression = Expression.LessThan(numParam, five)  
Dim lambda1 As Expression(Of Func(Of Integer, Boolean)) =  
  Expression.Lambda(Of Func(Of Integer, Boolean))(  
        numLessThanFive,  
        New ParameterExpression() {numParam})  
```  
  
 <span data-ttu-id="d4c0a-122">W .NET Framework 4 lub nowszym interfejs API drzew wyrażeń obsługuje również przypisania `try-catch` i sterowanie wyrażeniami przepływu, takimi jak pętle, bloki warunkowe i bloki.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="d4c0a-123">Za pomocą interfejsu API, można utworzyć drzewa wyrażeń, które są bardziej złożone niż te, które mogą być tworzone z wyrażeń lambda przez kompilator języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the Visual Basic compiler.</span></span> <span data-ttu-id="d4c0a-124">W poniższym przykładzie pokazano, jak utworzyć drzewo wyrażeń, które oblicza argument liczbowy liczby.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```vb  
' Creating a parameter expression.  
Dim value As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "value")  
  
' Creating an expression to hold a local variable.
Dim result As ParameterExpression =  
    Expression.Parameter(GetType(Integer), "result")  
  
' Creating a label to jump to from a loop.  
Dim label As LabelTarget = Expression.Label(GetType(Integer))  
  
' Creating a method body.  
Dim block As BlockExpression = Expression.Block(  
    New ParameterExpression() {result},  
    Expression.Assign(result, Expression.Constant(1)),  
    Expression.Loop(  
        Expression.IfThenElse(  
            Expression.GreaterThan(value, Expression.Constant(1)),  
            Expression.MultiplyAssign(result,  
                Expression.PostDecrementAssign(value)),  
            Expression.Break(label, result)  
        ),  
        label  
    )  
)  
  
' Compile an expression tree and return a delegate.  
Dim factorial As Integer =  
    Expression.Lambda(Of Func(Of Integer, Integer))(block, value).Compile()(5)  
  
Console.WriteLine(factorial)  
' Prints 120.  
```

<span data-ttu-id="d4c0a-125">Aby uzyskać więcej informacji, zobacz [Generowanie metod dynamicznych za pomocą drzew wyrażeń w programie Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), który ma również zastosowanie do nowszych wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="d4c0a-126">Analizowanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="d4c0a-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="d4c0a-127">Poniższy przykład kodu pokazuje, jak drzewo wyrażeń, który reprezentuje wyrażenie `Function(num) num < 5` lambda mogą być rozłożone na jego części.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-127">The following code example demonstrates how the expression tree that represents the lambda expression `Function(num) num < 5` can be decomposed into its parts.</span></span>  
  
```vb  
' Import the following namespace to your project: System.Linq.Expressions  
  
' Create an expression tree.  
Dim exprTree As Expression(Of Func(Of Integer, Boolean)) = Function(num) num < 5  
  
' Decompose the expression tree.  
Dim param As ParameterExpression = exprTree.Parameters(0)  
Dim operation As BinaryExpression = exprTree.Body  
Dim left As ParameterExpression = operation.Left  
Dim right As ConstantExpression = operation.Right  
  
Console.WriteLine(String.Format("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value))  
  
' This code produces the following output:  
'  
' Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="d4c0a-128">Niezmienność drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="d4c0a-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="d4c0a-129">Drzewa wyrażeń powinny być niezmienne.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-129">Expression trees should be immutable.</span></span> <span data-ttu-id="d4c0a-130">Oznacza to, że jeśli chcesz zmodyfikować drzewo wyrażeń, należy utworzyć nowe drzewo wyrażeń, kopiując istniejący i zastępując węzły w nim.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="d4c0a-131">Można użyć odwiedzającego drzewa wyrażeń, aby przejść przez istniejące drzewo wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="d4c0a-132">Aby uzyskać więcej informacji, zobacz [Jak: Modyfikowanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="d4c0a-132">For more information, see [How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="d4c0a-133">Kompilowanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="d4c0a-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="d4c0a-134">Typ <xref:System.Linq.Expressions.Expression%601> zawiera <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodę, która kompiluje kod reprezentowany przez drzewo wyrażeń do delegata wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="d4c0a-135">Poniższy przykład kodu pokazuje, jak skompilować drzewo wyrażeń i uruchomić wynikowy kod.</span><span class="sxs-lookup"><span data-stu-id="d4c0a-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```vb  
' Creating an expression tree.  
Dim expr As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
  
' Compiling the expression tree into a delegate.  
Dim result As Func(Of Integer, Boolean) = expr.Compile()  
  
' Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4))  
  
' Prints True.  
  
' You can also use simplified syntax  
' to compile and run an expression tree.  
' The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4))  
  
' Also prints True.  
```  
  
 <span data-ttu-id="d4c0a-136">Aby uzyskać więcej informacji, zobacz [Jak: Wykonywanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="d4c0a-136">For more information, see [How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4c0a-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4c0a-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="d4c0a-138">Jak: Wykonywanie drzew wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4c0a-138">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="d4c0a-139">Jak: Modyfikowanie drzew wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4c0a-139">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [<span data-ttu-id="d4c0a-140">Wyrażenia Lambda</span><span class="sxs-lookup"><span data-stu-id="d4c0a-140">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="d4c0a-141">Omówienie dynamicznego środowiska wykonawczego języka</span><span class="sxs-lookup"><span data-stu-id="d4c0a-141">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="d4c0a-142">Pojęcia programistyczne (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4c0a-142">Programming Concepts (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
