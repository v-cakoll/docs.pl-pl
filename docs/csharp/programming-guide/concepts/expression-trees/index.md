---
title: 'Drzewa wyrażeń (C#)'
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
---
# <a name="expression-trees-c"></a><span data-ttu-id="36ce2-102">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="36ce2-102">Expression Trees (C#)</span></span>
<span data-ttu-id="36ce2-103">Drzew wyrażeń reprezentują kodu struktury drzewa danych, gdzie każdy węzeł jest wyrażeniem, na przykład, wywołanie metody lub operacja binarna, takich jak `x < y`.</span><span class="sxs-lookup"><span data-stu-id="36ce2-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="36ce2-104">Można skompilować i uruchomić kod reprezentowany przez drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="36ce2-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="36ce2-105">Dzięki temu dynamicznych modyfikacji kodu wykonywalnego, wykonywanie zapytań LINQ zapytania w różnych baz danych i tworzenia zapytań dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="36ce2-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="36ce2-106">Aby uzyskać więcej informacji na temat drzew wyrażeń LINQ zobacz [jak: Używanie drzew wyrażeń do kompilowania zapytań dynamicznych (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="36ce2-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="36ce2-107">Drzewa wyrażeń są również używane w środowisko uruchomieniowe języka dynamicznego (DLR), aby zapewnić współdziałanie języków dynamicznego i .NET Framework i umożliwiają twórcom kompilatorów emitować drzew wyrażeń, zamiast języka Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="36ce2-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="36ce2-108">Aby uzyskać więcej informacji na temat DLR zobacz [dynamiczny przegląd środowiska uruchomieniowego języka](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="36ce2-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="36ce2-109">Możesz mieć, aby utworzyć drzewo wyrażenia, oparty na wyrażeniu lambda anonimowe lub tworzenia drzew wyrażeń ręcznie za pomocą kompilatora C# lub Visual Basic <xref:System.Linq.Expressions> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="36ce2-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="36ce2-110">Tworzenie drzew wyrażeń z wyrażenia Lambda</span><span class="sxs-lookup"><span data-stu-id="36ce2-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="36ce2-111">Gdy wyrażenie lambda jest przypisany do zmiennej typu <xref:System.Linq.Expressions.Expression%601>, kompilator generuje kod, aby utworzyć drzewo wyrażenia, który reprezentuje wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="36ce2-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="36ce2-112">Kompilator języka C# można wygenerować drzew wyrażeń, tylko z wyrażenia lambda (lub pojedynczej linii wyrażenia lambda).</span><span class="sxs-lookup"><span data-stu-id="36ce2-112">The C# compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="36ce2-113">Nie można go przeanalizować lambdy instrukcji (lub wielowierszowego wyrażenia lambda).</span><span class="sxs-lookup"><span data-stu-id="36ce2-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="36ce2-114">Aby uzyskać więcej informacji na temat wyrażeń lambda w języku C#, zobacz [wyrażeń Lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="36ce2-114">For more information about lambda expressions in C#, see [Lambda Expressions](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="36ce2-115">Poniższe przykłady kodu ilustrują jak kompilator języka C# utworzyć drzewo wyrażenia, który reprezentuje wyrażenie lambda `num => num < 5`.</span><span class="sxs-lookup"><span data-stu-id="36ce2-115">The following code examples demonstrate how to have the C# compiler create an expression tree that represents the lambda expression `num => num < 5`.</span></span>  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="36ce2-116">Tworzenia drzew wyrażeń, korzystając z interfejsu API</span><span class="sxs-lookup"><span data-stu-id="36ce2-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="36ce2-117">Do tworzenia drzew wyrażeń, korzystając z interfejsu API, należy użyć <xref:System.Linq.Expressions.Expression> klasy.</span><span class="sxs-lookup"><span data-stu-id="36ce2-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="36ce2-118">Ta klasa zawiera statycznych metod fabryki tworzonych wyrażeń węzły drzewa określonych typów, na przykład <xref:System.Linq.Expressions.ParameterExpression>, która reprezentuje zmienna lub parametr, lub <xref:System.Linq.Expressions.MethodCallExpression>, która reprezentuje wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="36ce2-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="36ce2-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, i inne typy wyrażeń określonych również są definiowane w <xref:System.Linq.Expressions> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="36ce2-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="36ce2-120">Te typy pochodzić od typu abstrakcyjnego <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="36ce2-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="36ce2-121">Poniższy przykład kodu demonstruje sposób tworzenia drzewa wyrażeń, który reprezentuje wyrażenie lambda `num => num < 5` za pomocą interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="36ce2-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `num => num < 5` by using the API.</span></span>  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Manually build the expression tree for   
// the lambda expression num => num < 5.  
ParameterExpression numParam = Expression.Parameter(typeof(int), "num");  
ConstantExpression five = Expression.Constant(5, typeof(int));  
BinaryExpression numLessThanFive = Expression.LessThan(numParam, five);  
Expression<Func<int, bool>> lambda1 =  
    Expression.Lambda<Func<int, bool>>(  
        numLessThanFive,  
        new ParameterExpression[] { numParam });  
```  
  
 <span data-ttu-id="36ce2-122">W programie .NET Framework 4 lub nowszym, interfejs API drzew wyrażeń obsługuje również przydziałów i wyrażeń przepływu sterowania takie jak pętle i bloków warunkowych i `try-catch` bloków.</span><span class="sxs-lookup"><span data-stu-id="36ce2-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="36ce2-123">Za pomocą interfejsu API, można utworzyć drzew wyrażeń, które są bardziej skomplikowane niż te, które można tworzyć na podstawie wyrażenia lambda przez kompilator języka C#.</span><span class="sxs-lookup"><span data-stu-id="36ce2-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the C# compiler.</span></span> <span data-ttu-id="36ce2-124">Poniższy przykład przedstawia sposób tworzenia drzewa wyrażeń, który oblicza silnię liczby.</span><span class="sxs-lookup"><span data-stu-id="36ce2-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
```csharp  
// Creating a parameter expression.  
ParameterExpression value = Expression.Parameter(typeof(int), "value");  
  
// Creating an expression to hold a local variable.   
ParameterExpression result = Expression.Parameter(typeof(int), "result");  
  
// Creating a label to jump to from a loop.  
LabelTarget label = Expression.Label(typeof(int));  
  
// Creating a method body.  
BlockExpression block = Expression.Block(  
    // Adding a local variable.  
    new[] { result },  
    // Assigning a constant to a local variable: result = 1  
    Expression.Assign(result, Expression.Constant(1)),  
    // Adding a loop.  
        Expression.Loop(  
    // Adding a conditional block into the loop.  
           Expression.IfThenElse(  
    // Condition: value > 1  
               Expression.GreaterThan(value, Expression.Constant(1)),  
    // If true: result *= value --  
               Expression.MultiplyAssign(result,  
                   Expression.PostDecrementAssign(value)),  
    // If false, exit the loop and go to the label.  
               Expression.Break(label, result)  
           ),  
    // Label to jump to.  
       label  
    )  
);  
  
// Compile and execute an expression tree.  
int factorial = Expression.Lambda<Func<int, int>>(block, value).Compile()(5);  
  
Console.WriteLine(factorial);  
// Prints 120.  
```

<span data-ttu-id="36ce2-125">Aby uzyskać więcej informacji, zobacz [metody dynamiczne generowanie za pomocą drzew w programie Visual Studio 2010](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), która ma zastosowanie również do nowszej wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="36ce2-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="36ce2-126">Podczas analizowania drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="36ce2-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="36ce2-127">Poniższy przykład kodu demonstruje, jak wyrażenie drzewa, która reprezentuje wyrażenia lambda `num => num < 5` może być rozłożone na jego części.</span><span class="sxs-lookup"><span data-stu-id="36ce2-127">The following code example demonstrates how the expression tree that represents the lambda expression `num => num < 5` can be decomposed into its parts.</span></span>  
  
```csharp  
// Add the following using directive to your code file:  
// using System.Linq.Expressions;  
  
// Create an expression tree.  
Expression<Func<int, bool>> exprTree = num => num < 5;  
  
// Decompose the expression tree.  
ParameterExpression param = (ParameterExpression)exprTree.Parameters[0];  
BinaryExpression operation = (BinaryExpression)exprTree.Body;  
ParameterExpression left = (ParameterExpression)operation.Left;  
ConstantExpression right = (ConstantExpression)operation.Right;  
  
Console.WriteLine("Decomposed expression: {0} => {1} {2} {3}",  
                  param.Name, left.Name, operation.NodeType, right.Value);  
  
// This code produces the following output:  
  
// Decomposed expression: num => num LessThan 5  
```  
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="36ce2-128">Niezmienność drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="36ce2-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="36ce2-129">Drzewa wyrażeń powinno być niezmienialne.</span><span class="sxs-lookup"><span data-stu-id="36ce2-129">Expression trees should be immutable.</span></span> <span data-ttu-id="36ce2-130">Oznacza to zmodyfikować drzewo wyrażenia, przez skopiowanie istniejącego i zastępując węzły w nim należy tworzyć nowego drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="36ce2-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="36ce2-131">Obiekt odwiedzający drzewa wyrażenie umożliwia przenoszenie istniejących drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="36ce2-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="36ce2-132">Aby uzyskać więcej informacji, zobacz [jak: Modyfikowanie drzew wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="36ce2-132">For more information, see [How to: Modify Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="36ce2-133">Kompilowanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="36ce2-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="36ce2-134"><xref:System.Linq.Expressions.Expression%601> Typ zapewnia <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodę, która kompiluje kod reprezentowany przez drzewo wyrażenia do pliku wykonywalnego delegata.</span><span class="sxs-lookup"><span data-stu-id="36ce2-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="36ce2-135">Poniższy przykład kodu pokazuje, jak skompilować drzewo wyrażeń i uruchomić wynikowy kod.</span><span class="sxs-lookup"><span data-stu-id="36ce2-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
```csharp  
// Creating an expression tree.  
Expression<Func<int, bool>> expr = num => num < 5;  
  
// Compiling the expression tree into a delegate.  
Func<int, bool> result = expr.Compile();  
  
// Invoking the delegate and writing the result to the console.  
Console.WriteLine(result(4));  
  
// Prints True.  
  
// You can also use simplified syntax  
// to compile and run an expression tree.  
// The following line can replace two previous statements.  
Console.WriteLine(expr.Compile()(4));  
  
// Also prints True.  
```  
  
 <span data-ttu-id="36ce2-136">Aby uzyskać więcej informacji, zobacz [jak: Wykonywanie drzew wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="36ce2-136">For more information, see [How to: Execute Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36ce2-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36ce2-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="36ce2-138">Instrukcje: Wykonywanie drzew wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="36ce2-138">How to: Execute Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)
- [<span data-ttu-id="36ce2-139">Instrukcje: Modyfikowanie drzew wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="36ce2-139">How to: Modify Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
- [<span data-ttu-id="36ce2-140">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="36ce2-140">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="36ce2-141">Przegląd środowiska uruchomieniowego języka dynamicznego</span><span class="sxs-lookup"><span data-stu-id="36ce2-141">Dynamic Language Runtime Overview</span></span>](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="36ce2-142">Koncepcje programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="36ce2-142">Programming Concepts (C#)</span></span>](../../../../csharp/programming-guide/concepts/index.md)
