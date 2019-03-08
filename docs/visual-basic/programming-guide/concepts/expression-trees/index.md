---
title: Drzewa wyrażeń (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8bbbb02d-7ffc-476b-8c25-118d82bf5d46
---
# <a name="expression-trees-visual-basic"></a><span data-ttu-id="45fa4-102">Drzewa wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45fa4-102">Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="45fa4-103">Drzew wyrażeń reprezentują kodu struktury drzewa danych, gdzie każdy węzeł jest wyrażeniem, na przykład, wywołanie metody lub operacja binarna, takich jak `x < y`.</span><span class="sxs-lookup"><span data-stu-id="45fa4-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="45fa4-104">Można skompilować i uruchomić kod reprezentowany przez drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="45fa4-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="45fa4-105">Dzięki temu dynamicznych modyfikacji kodu wykonywalnego, wykonywanie zapytań LINQ zapytania w różnych baz danych i tworzenia zapytań dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="45fa4-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="45fa4-106">Aby uzyskać więcej informacji na temat drzew wyrażeń LINQ zobacz [jak: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="45fa4-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="45fa4-107">Drzewa wyrażeń są również używane w środowisko uruchomieniowe języka dynamicznego (DLR), aby zapewnić współdziałanie języków dynamicznego i .NET Framework i umożliwiają twórcom kompilatorów emitować drzew wyrażeń, zamiast języka Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="45fa4-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="45fa4-108">Aby uzyskać więcej informacji na temat DLR zobacz [dynamiczny przegląd środowiska uruchomieniowego języka](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="45fa4-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="45fa4-109">Możesz mieć, aby utworzyć drzewo wyrażenia, oparty na wyrażeniu lambda anonimowe lub tworzenia drzew wyrażeń ręcznie za pomocą kompilatora C# lub Visual Basic <xref:System.Linq.Expressions> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="45fa4-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="45fa4-110">Tworzenie drzew wyrażeń z wyrażenia Lambda</span><span class="sxs-lookup"><span data-stu-id="45fa4-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="45fa4-111">Gdy wyrażenie lambda jest przypisany do zmiennej typu <xref:System.Linq.Expressions.Expression%601>, kompilator generuje kod, aby utworzyć drzewo wyrażenia, który reprezentuje wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="45fa4-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="45fa4-112">Kompilator Visual Basic można wygenerować drzew wyrażeń, tylko z wyrażenia lambda (lub pojedynczej linii wyrażenia lambda).</span><span class="sxs-lookup"><span data-stu-id="45fa4-112">The Visual Basic compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="45fa4-113">Nie można go przeanalizować lambdy instrukcji (lub wielowierszowego wyrażenia lambda).</span><span class="sxs-lookup"><span data-stu-id="45fa4-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="45fa4-114">Aby uzyskać więcej informacji na temat wyrażeń lambda w języku Visual Basic, zobacz [wyrażeń Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="45fa4-114">For more information about lambda expressions in Visual Basic, see [Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="45fa4-115">Poniższe przykłady kodu przedstawiają sposób pozwolić kompilatorowi języka Visual Basic, utworzyć drzewo wyrażenia, który reprezentuje wyrażenie lambda `Function(num) num < 5`.</span><span class="sxs-lookup"><span data-stu-id="45fa4-115">The following code examples demonstrate how to have the Visual Basic compiler create an expression tree that represents the lambda expression `Function(num) num < 5`.</span></span>  
  
```vb  
Dim lambda As Expression(Of Func(Of Integer, Boolean)) =  
    Function(num) num < 5  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="45fa4-116">Tworzenia drzew wyrażeń, korzystając z interfejsu API</span><span class="sxs-lookup"><span data-stu-id="45fa4-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="45fa4-117">Do tworzenia drzew wyrażeń, korzystając z interfejsu API, należy użyć <xref:System.Linq.Expressions.Expression> klasy.</span><span class="sxs-lookup"><span data-stu-id="45fa4-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="45fa4-118">Ta klasa zawiera statycznych metod fabryki tworzonych wyrażeń węzły drzewa określonych typów, na przykład <xref:System.Linq.Expressions.ParameterExpression>, która reprezentuje zmienna lub parametr, lub <xref:System.Linq.Expressions.MethodCallExpression>, która reprezentuje wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="45fa4-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="45fa4-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, i inne typy wyrażeń określonych również są definiowane w <xref:System.Linq.Expressions> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="45fa4-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="45fa4-120">Te typy pochodzić od typu abstrakcyjnego <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="45fa4-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="45fa4-121">Poniższy przykład kodu demonstruje sposób tworzenia drzewa wyrażeń, który reprezentuje wyrażenie lambda `Function(num) num < 5` za pomocą interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="45fa4-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `Function(num) num < 5` by using the API.</span></span>  
  
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
  
 <span data-ttu-id="45fa4-122">W programie .NET Framework 4 lub nowszym, interfejs API drzew wyrażeń obsługuje również przydziałów i wyrażeń przepływu sterowania takie jak pętle i bloków warunkowych i `try-catch` bloków.</span><span class="sxs-lookup"><span data-stu-id="45fa4-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="45fa4-123">Za pomocą interfejsu API, można utworzyć drzew wyrażeń, które są bardziej skomplikowane niż te, które można tworzyć na podstawie wyrażenia lambda przez kompilator języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="45fa4-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the Visual Basic compiler.</span></span> <span data-ttu-id="45fa4-124">Poniższy przykład przedstawia sposób tworzenia drzewa wyrażeń, który oblicza silnię liczby.</span><span class="sxs-lookup"><span data-stu-id="45fa4-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
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

<span data-ttu-id="45fa4-125">Aby uzyskać więcej informacji, zobacz [metody dynamiczne generowanie za pomocą drzew w programie Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), która ma zastosowanie również do nowszej wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="45fa4-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="45fa4-126">Podczas analizowania drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="45fa4-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="45fa4-127">Poniższy przykład kodu demonstruje, jak wyrażenie drzewa, która reprezentuje wyrażenia lambda `Function(num) num < 5` może być rozłożone na jego części.</span><span class="sxs-lookup"><span data-stu-id="45fa4-127">The following code example demonstrates how the expression tree that represents the lambda expression `Function(num) num < 5` can be decomposed into its parts.</span></span>  
  
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
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="45fa4-128">Niezmienność drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="45fa4-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="45fa4-129">Drzewa wyrażeń powinno być niezmienialne.</span><span class="sxs-lookup"><span data-stu-id="45fa4-129">Expression trees should be immutable.</span></span> <span data-ttu-id="45fa4-130">Oznacza to zmodyfikować drzewo wyrażenia, przez skopiowanie istniejącego i zastępując węzły w nim należy tworzyć nowego drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="45fa4-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="45fa4-131">Obiekt odwiedzający drzewa wyrażenie umożliwia przenoszenie istniejących drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="45fa4-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="45fa4-132">Aby uzyskać więcej informacji, zobacz [jak: Modyfikowanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="45fa4-132">For more information, see [How to: Modify Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="45fa4-133">Kompilowanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="45fa4-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="45fa4-134"><xref:System.Linq.Expressions.Expression%601> Typ zapewnia <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodę, która kompiluje kod reprezentowany przez drzewo wyrażenia do pliku wykonywalnego delegata.</span><span class="sxs-lookup"><span data-stu-id="45fa4-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="45fa4-135">Poniższy przykład kodu pokazuje, jak skompilować drzewo wyrażeń i uruchomić wynikowy kod.</span><span class="sxs-lookup"><span data-stu-id="45fa4-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
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
  
 <span data-ttu-id="45fa4-136">Aby uzyskać więcej informacji, zobacz [jak: Wykonywanie drzew wyrażeń (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="45fa4-136">For more information, see [How to: Execute Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45fa4-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45fa4-137">See also</span></span>
- <xref:System.Linq.Expressions>
- [<span data-ttu-id="45fa4-138">Instrukcje: Wykonywanie drzew wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45fa4-138">How to: Execute Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="45fa4-139">Instrukcje: Modyfikowanie drzew wyrażeń (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45fa4-139">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [<span data-ttu-id="45fa4-140">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="45fa4-140">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="45fa4-141">Przegląd środowiska uruchomieniowego języka dynamicznego</span><span class="sxs-lookup"><span data-stu-id="45fa4-141">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="45fa4-142">Koncepcje programowania (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45fa4-142">Programming Concepts (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
