---
title: Drzewa wyrażeń (C#)
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: 14ca5394a21b8dddb6c4431e6cabbf44a2f9add2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="expression-trees-c"></a><span data-ttu-id="3f24b-102">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="3f24b-102">Expression Trees (C#)</span></span>
<span data-ttu-id="3f24b-103">Drzewa wyrażeń reprezentuje kod w strukturze drzewa danych każdy węzeł w przypadku wyrażenia, na przykład, wywołanie metody lub operację binarną takich jak `x < y`.</span><span class="sxs-lookup"><span data-stu-id="3f24b-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="3f24b-104">Możesz skompilować i uruchomić kod reprezentowany przez drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="3f24b-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="3f24b-105">Umożliwia dynamiczne modyfikacji kodu wykonywalnego, wysyła zapytanie do wykonywania zapytań LINQ w różnych baz danych i tworzenie zapytań dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="3f24b-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="3f24b-106">Aby uzyskać więcej informacji na temat drzew wyrażeń w składniku LINQ, zobacz [porady: użycie drzew wyrażeń do tworzenia zapytań dynamicznych (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span><span class="sxs-lookup"><span data-stu-id="3f24b-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="3f24b-107">Drzewa wyrażeń są również używane w środowisku uruchomieniowym języka dynamicznego (DLR), aby zapewnić współdziałanie między językami dynamiczne i .NET Framework i umożliwić autorów kompilatora, aby emitować drzew wyrażeń zamiast język pośredni firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="3f24b-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="3f24b-108">Aby uzyskać więcej informacji na temat DLR, zobacz [Przegląd środowiska uruchomieniowego języka dynamicznego](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3f24b-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="3f24b-109">Masz Utwórz drzewo wyrażeń oparte na wyrażeniu lambda anonimowe lub drzew wyrażeń można tworzyć ręcznie za pomocą kompilatora C# lub Visual Basic <xref:System.Linq.Expressions> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3f24b-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="3f24b-110">Tworzenie drzewa wyrażeń z wyrażenia Lambda</span><span class="sxs-lookup"><span data-stu-id="3f24b-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="3f24b-111">Jeśli wyrażenie lambda jest przypisany do zmiennej typu <xref:System.Linq.Expressions.Expression%601>, kompilator emituje kod, aby utworzyć drzewo wyrażenia, który reprezentuje wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="3f24b-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="3f24b-112">Kompilator języka C# można wygenerować drzewa wyrażeń tylko z wyrażenia lambda (lub jednowierszowe wyrażenia lambda).</span><span class="sxs-lookup"><span data-stu-id="3f24b-112">The C# compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="3f24b-113">Nie można go przeanalizować instrukcji lambda (lub wielowierszowego wyrażenia lambda).</span><span class="sxs-lookup"><span data-stu-id="3f24b-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="3f24b-114">Aby uzyskać więcej informacji na temat wyrażeń lambda w języku C#, zobacz [wyrażenia Lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3f24b-114">For more information about lambda expressions in C#, see [Lambda Expressions](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="3f24b-115">W poniższych przykładach kodu przedstawiają sposób kompilatora C# Utwórz drzewo wyrażeń, który reprezentuje wyrażenie lambda ma `num => num < 5`.</span><span class="sxs-lookup"><span data-stu-id="3f24b-115">The following code examples demonstrate how to have the C# compiler create an expression tree that represents the lambda expression `num => num < 5`.</span></span>  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="3f24b-116">Tworzenie przy użyciu interfejsu API drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="3f24b-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="3f24b-117">Aby utworzyć drzewa wyrażeń przy użyciu interfejsu API, użyj <xref:System.Linq.Expressions.Expression> klasy.</span><span class="sxs-lookup"><span data-stu-id="3f24b-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="3f24b-118">Ta klasa zawiera metody statyczne fabryki, tworzone wyrażenia węzły drzewa określonych typów, na przykład <xref:System.Linq.Expressions.ParameterExpression>, reprezentuje zmienna lub parametr, lub <xref:System.Linq.Expressions.MethodCallExpression>, który reprezentuje wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="3f24b-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="3f24b-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, i inne typy specyficzne dla wyrażenia również są definiowane w <xref:System.Linq.Expressions> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3f24b-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="3f24b-120">Te typy pochodzić od typu abstrakcyjnego <xref:System.Linq.Expressions.Expression>.</span><span class="sxs-lookup"><span data-stu-id="3f24b-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="3f24b-121">Poniższy przykładowy kod przedstawia sposób tworzenia drzewo wyrażenia, który reprezentuje wyrażenie lambda `num => num < 5` przy użyciu interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="3f24b-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `num => num < 5` by using the API.</span></span>  
  
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
  
 <span data-ttu-id="3f24b-122">W programie .NET Framework 4 lub nowszym API drzewa wyrażenia obsługuje również przydziałów i wyrażeń przepływu sterowania takich jak pętle, bloków warunkowych i `try-catch` bloków.</span><span class="sxs-lookup"><span data-stu-id="3f24b-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="3f24b-123">Korzystając z interfejsu API, można utworzyć drzewa wyrażeń, które są bardziej złożone niż te, które mogą być tworzone z wyrażenia lambda za pomocą kompilatora C#.</span><span class="sxs-lookup"><span data-stu-id="3f24b-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the C# compiler.</span></span> <span data-ttu-id="3f24b-124">W poniższym przykładzie pokazano, jak utworzyć drzewo wyrażenia, który oblicza silnię liczby.</span><span class="sxs-lookup"><span data-stu-id="3f24b-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
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

<span data-ttu-id="3f24b-125">Aby uzyskać więcej informacji, zobacz [metody dynamiczne generowanie z drzewa wyrażeń w Visual Studio 2010](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), która ma zastosowanie również do nowszej wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3f24b-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://blogs.msdn.microsoft.com/csharpfaq/2009/09/14/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="3f24b-126">Podczas analizowania drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="3f24b-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="3f24b-127">W poniższym przykładzie kodu pokazano, jak wyrażenia drzewa, który reprezentuje wyrażenie lambda `num => num < 5` może być rozłożone na jego części.</span><span class="sxs-lookup"><span data-stu-id="3f24b-127">The following code example demonstrates how the expression tree that represents the lambda expression `num => num < 5` can be decomposed into its parts.</span></span>  
  
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
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="3f24b-128">Immutability drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="3f24b-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="3f24b-129">Drzewa wyrażeń powinno być niezmienialne.</span><span class="sxs-lookup"><span data-stu-id="3f24b-129">Expression trees should be immutable.</span></span> <span data-ttu-id="3f24b-130">Oznacza to zmodyfikować drzewo wyrażenia, kopiując istniejący i zastępowanie węzłów w nim należy tworzyć nowe drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="3f24b-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="3f24b-131">Obiekt odwiedzający wyrażenie drzewa umożliwia przenoszenie istniejących drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="3f24b-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="3f24b-132">Aby uzyskać więcej informacji, zobacz [porady: modyfikowanie drzew wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="3f24b-132">For more information, see [How to: Modify Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="3f24b-133">Kompilowanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="3f24b-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="3f24b-134"><xref:System.Linq.Expressions.Expression%601> Typ zapewnia <xref:System.Linq.Expressions.Expression%601.Compile%2A> metodę, która kompiluje kod reprezentowany przez drzewo wyrażenia do pliku wykonywalnego delegata.</span><span class="sxs-lookup"><span data-stu-id="3f24b-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="3f24b-135">W poniższym przykładzie pokazano, jak skompilować drzewo wyrażeń i uruchomić wynikowy kod.</span><span class="sxs-lookup"><span data-stu-id="3f24b-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
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
  
 <span data-ttu-id="3f24b-136">Aby uzyskać więcej informacji, zobacz [porady: wykonywanie drzew wyrażeń (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="3f24b-136">For more information, see [How to: Execute Expression Trees (C#)](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f24b-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f24b-137">See Also</span></span>  
 <xref:System.Linq.Expressions>  
 [<span data-ttu-id="3f24b-138">Porady: wykonywanie drzew wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="3f24b-138">How to: Execute Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-execute-expression-trees.md)  
 [<span data-ttu-id="3f24b-139">Porady: modyfikowanie drzew wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="3f24b-139">How to: Modify Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)  
 [<span data-ttu-id="3f24b-140">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="3f24b-140">Lambda Expressions</span></span>](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="3f24b-141">Przegląd środowiska uruchomieniowego języka dynamicznego</span><span class="sxs-lookup"><span data-stu-id="3f24b-141">Dynamic Language Runtime Overview</span></span>](../../../../../docs/framework/reflection-and-codedom/dynamic-language-runtime-overview.md)  
 [<span data-ttu-id="3f24b-142">Koncepcje programowania (C#)</span><span class="sxs-lookup"><span data-stu-id="3f24b-142">Programming Concepts (C#)</span></span>](../../../../csharp/programming-guide/concepts/index.md)
