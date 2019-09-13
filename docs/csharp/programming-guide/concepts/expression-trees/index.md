---
title: Drzewa wyrażeń (C#)
ms.date: 07/20/2015
ms.assetid: 7d0ac21a-6d90-4e2e-8903-528cb78615b7
ms.openlocfilehash: 7e63bf28f10070daa9624daa67bd5118fa67874d
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926713"
---
# <a name="expression-trees-c"></a><span data-ttu-id="a642e-102">Drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="a642e-102">Expression Trees (C#)</span></span>
<span data-ttu-id="a642e-103">Drzewa wyrażeń reprezentują kod w strukturze danych przypominającej drzewo, gdzie każdy węzeł jest wyrażeniem, na przykład wywołaniem metody lub operacją binarną, taką jak `x < y`.</span><span class="sxs-lookup"><span data-stu-id="a642e-103">Expression trees represent code in a tree-like data structure, where each node is an expression, for example, a method call or a binary operation such as `x < y`.</span></span>  
  
 <span data-ttu-id="a642e-104">Można skompilować i uruchomić kod reprezentowany przez drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="a642e-104">You can compile and run code represented by expression trees.</span></span> <span data-ttu-id="a642e-105">Umożliwia to dynamiczną modyfikację kodu wykonywalnego, wykonywanie zapytań LINQ w różnych bazach danych i tworzenie zapytań dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="a642e-105">This enables dynamic modification of executable code, the execution of LINQ queries in various databases, and the creation of dynamic queries.</span></span> <span data-ttu-id="a642e-106">Aby uzyskać więcej informacji na temat drzew wyrażeń w LINQ [, zobacz How to: Używaj drzew wyrażeń do kompilowania zapytań dynamicznychC#(](./how-to-use-expression-trees-to-build-dynamic-queries.md)).</span><span class="sxs-lookup"><span data-stu-id="a642e-106">For more information about expression trees in LINQ, see [How to: Use Expression Trees to Build Dynamic Queries (C#)](./how-to-use-expression-trees-to-build-dynamic-queries.md).</span></span>  
  
 <span data-ttu-id="a642e-107">Drzewa wyrażeń są również używane w środowisku uruchomieniowym języka dynamicznego (DLR) w celu zapewnienia współdziałania między językami dynamicznymi i .NET Framework i umożliwiają autorom kompilatora emitowanie drzew wyrażeń zamiast języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="a642e-107">Expression trees are also used in the dynamic language runtime (DLR) to provide interoperability between dynamic languages and the .NET Framework and to enable compiler writers to emit expression trees instead of Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="a642e-108">Aby uzyskać więcej informacji na temat DLR, zobacz [Omówienie środowiska uruchomieniowego języka dynamicznego](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a642e-108">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>  
  
 <span data-ttu-id="a642e-109">Można utworzyć drzewo wyrażenia C# lub Visual Basic w oparciu o anonimowe wyrażenie lambda lub można utworzyć drzewa wyrażeń ręcznie przy użyciu <xref:System.Linq.Expressions> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a642e-109">You can have the C# or Visual Basic compiler create an expression tree for you based on an anonymous lambda expression, or you can create expression trees manually by using the <xref:System.Linq.Expressions> namespace.</span></span>  
  
## <a name="creating-expression-trees-from-lambda-expressions"></a><span data-ttu-id="a642e-110">Tworzenie drzew wyrażeń na podstawie wyrażeń lambda</span><span class="sxs-lookup"><span data-stu-id="a642e-110">Creating Expression Trees from Lambda Expressions</span></span>  
 <span data-ttu-id="a642e-111">Gdy wyrażenie lambda jest przypisane do zmiennej typu <xref:System.Linq.Expressions.Expression%601>, kompilator emituje kod w celu skompilowania drzewa wyrażenia, które reprezentuje wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="a642e-111">When a lambda expression is assigned to a variable of type <xref:System.Linq.Expressions.Expression%601>, the compiler emits code to build an expression tree that represents the lambda expression.</span></span>  
  
 <span data-ttu-id="a642e-112">C# Kompilator może generować drzewa wyrażeń tylko z wyrażeń lambda (lub jednowierszowych wyrażeń lambda).</span><span class="sxs-lookup"><span data-stu-id="a642e-112">The C# compiler can generate expression trees only from expression lambdas (or single-line lambdas).</span></span> <span data-ttu-id="a642e-113">Nie można analizować instrukcji lambda (lub wielowierszowych wyrażeń lambda).</span><span class="sxs-lookup"><span data-stu-id="a642e-113">It cannot parse statement lambdas (or multi-line lambdas).</span></span> <span data-ttu-id="a642e-114">Aby uzyskać więcej informacji na temat wyrażeń C#lambda w, zobacz [lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="a642e-114">For more information about lambda expressions in C#, see [Lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="a642e-115">W poniższym przykładzie kodu pokazano, jak utworzyć w C# kompilatorze drzewo wyrażenia, które reprezentuje wyrażenie `num => num < 5`lambda.</span><span class="sxs-lookup"><span data-stu-id="a642e-115">The following code examples demonstrate how to have the C# compiler create an expression tree that represents the lambda expression `num => num < 5`.</span></span>  
  
```csharp  
Expression<Func<int, bool>> lambda = num => num < 5;  
```  
  
## <a name="creating-expression-trees-by-using-the-api"></a><span data-ttu-id="a642e-116">Tworzenie drzew wyrażeń przy użyciu interfejsu API</span><span class="sxs-lookup"><span data-stu-id="a642e-116">Creating Expression Trees by Using the API</span></span>  
 <span data-ttu-id="a642e-117">Aby utworzyć drzewa wyrażeń przy użyciu interfejsu API, użyj <xref:System.Linq.Expressions.Expression> klasy.</span><span class="sxs-lookup"><span data-stu-id="a642e-117">To create expression trees by using the API, use the <xref:System.Linq.Expressions.Expression> class.</span></span> <span data-ttu-id="a642e-118">Ta klasa zawiera statyczne metody fabryki, które tworzą węzły drzewa wyrażenia określonych typów, na przykład <xref:System.Linq.Expressions.ParameterExpression>, która reprezentuje zmienną lub parametr lub <xref:System.Linq.Expressions.MethodCallExpression>, który reprezentuje wywołanie metody.</span><span class="sxs-lookup"><span data-stu-id="a642e-118">This class contains static factory methods that create expression tree nodes of specific types, for example, <xref:System.Linq.Expressions.ParameterExpression>, which represents a variable or parameter, or <xref:System.Linq.Expressions.MethodCallExpression>, which represents a method call.</span></span> <span data-ttu-id="a642e-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>i inne typy specyficzne dla wyrażenia są również zdefiniowane <xref:System.Linq.Expressions> w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a642e-119"><xref:System.Linq.Expressions.ParameterExpression>, <xref:System.Linq.Expressions.MethodCallExpression>, and the other expression-specific types are also defined in the <xref:System.Linq.Expressions> namespace.</span></span> <span data-ttu-id="a642e-120">Te typy pochodzą z typu <xref:System.Linq.Expressions.Expression>abstrakcyjnego.</span><span class="sxs-lookup"><span data-stu-id="a642e-120">These types derive from the abstract type <xref:System.Linq.Expressions.Expression>.</span></span>  
  
 <span data-ttu-id="a642e-121">Poniższy przykład kodu ilustruje sposób tworzenia drzewa wyrażenia, które reprezentuje wyrażenie `num => num < 5` lambda przy użyciu interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="a642e-121">The following code example demonstrates how to create an expression tree that represents the lambda expression `num => num < 5` by using the API.</span></span>  
  
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
  
 <span data-ttu-id="a642e-122">W .NET Framework 4 lub nowszych interfejs API drzew wyrażeń obsługuje również przypisania i wyrażenia przepływu sterowania, takie jak pętle, Bloki warunkowe `try-catch` i bloki.</span><span class="sxs-lookup"><span data-stu-id="a642e-122">In .NET Framework 4 or later, the expression trees API also supports assignments and control flow expressions such as loops, conditional blocks, and `try-catch` blocks.</span></span> <span data-ttu-id="a642e-123">Za pomocą interfejsu API można utworzyć drzewa wyrażeń, które są bardziej złożone niż te, które mogą być tworzone na podstawie wyrażeń lambda przez C# kompilator.</span><span class="sxs-lookup"><span data-stu-id="a642e-123">By using the API, you can create expression trees that are more complex than those that can be created from lambda expressions by the C# compiler.</span></span> <span data-ttu-id="a642e-124">Poniższy przykład ilustruje sposób tworzenia drzewa wyrażenia, które oblicza silnię liczby.</span><span class="sxs-lookup"><span data-stu-id="a642e-124">The following example demonstrates how to create an expression tree that calculates the factorial of a number.</span></span>  
  
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

<span data-ttu-id="a642e-125">Aby uzyskać więcej informacji, zobacz [generowanie metod dynamicznych z drzewami wyrażeń w programie Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), które mają zastosowanie również do nowszych wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a642e-125">For more information, see [Generating Dynamic Methods with Expression Trees in Visual Studio 2010](https://devblogs.microsoft.com/csharpfaq/generating-dynamic-methods-with-expression-trees-in-visual-studio-2010/), which also applies to later versions of Visual Studio.</span></span>
  
## <a name="parsing-expression-trees"></a><span data-ttu-id="a642e-126">Analizowanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="a642e-126">Parsing Expression Trees</span></span>  
 <span data-ttu-id="a642e-127">Poniższy przykład kodu demonstruje, jak drzewo wyrażeń reprezentujące wyrażenie `num => num < 5` lambda może być rozłożone na jego części.</span><span class="sxs-lookup"><span data-stu-id="a642e-127">The following code example demonstrates how the expression tree that represents the lambda expression `num => num < 5` can be decomposed into its parts.</span></span>  
  
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
  
## <a name="immutability-of-expression-trees"></a><span data-ttu-id="a642e-128">Niezmienności drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="a642e-128">Immutability of Expression Trees</span></span>  
 <span data-ttu-id="a642e-129">Drzewa wyrażeń powinny być niezmienne.</span><span class="sxs-lookup"><span data-stu-id="a642e-129">Expression trees should be immutable.</span></span> <span data-ttu-id="a642e-130">Oznacza to, że jeśli chcesz zmodyfikować drzewo wyrażenia, należy utworzyć nowe drzewo wyrażeń przez skopiowanie istniejącego i zastępowanie węzłów w tym elemencie.</span><span class="sxs-lookup"><span data-stu-id="a642e-130">This means that if you want to modify an expression tree, you must construct a new expression tree by copying the existing one and replacing nodes in it.</span></span> <span data-ttu-id="a642e-131">Możesz użyć odwiedzania drzewa wyrażenia, aby przejść do istniejącego drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a642e-131">You can use an expression tree visitor to traverse the existing expression tree.</span></span> <span data-ttu-id="a642e-132">Aby uzyskać więcej informacji, zobacz [jak: Modyfikuj drzewa wyrażeń (C#)](./how-to-modify-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="a642e-132">For more information, see [How to: Modify Expression Trees (C#)](./how-to-modify-expression-trees.md).</span></span>  
  
## <a name="compiling-expression-trees"></a><span data-ttu-id="a642e-133">Kompilowanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="a642e-133">Compiling Expression Trees</span></span>  
 <span data-ttu-id="a642e-134"><xref:System.Linq.Expressions.Expression%601> Typ<xref:System.Linq.Expressions.Expression%601.Compile%2A> udostępnia metodę, która kompiluje kod reprezentowany przez drzewo wyrażenia w delegatze pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="a642e-134">The <xref:System.Linq.Expressions.Expression%601> type provides the <xref:System.Linq.Expressions.Expression%601.Compile%2A> method that compiles the code represented by an expression tree into an executable delegate.</span></span>  
  
 <span data-ttu-id="a642e-135">Poniższy przykład kodu demonstruje sposób kompilowania drzewa wyrażenia i uruchamiania wyniku.</span><span class="sxs-lookup"><span data-stu-id="a642e-135">The following code example demonstrates how to compile an expression tree and run the resulting code.</span></span>  
  
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
  
 <span data-ttu-id="a642e-136">Aby uzyskać więcej informacji, zobacz [jak: Wykonywanie drzew wyrażeń (C#)](./how-to-execute-expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="a642e-136">For more information, see [How to: Execute Expression Trees (C#)](./how-to-execute-expression-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a642e-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a642e-137">See also</span></span>

- <xref:System.Linq.Expressions>
- [<span data-ttu-id="a642e-138">Instrukcje: Wykonywanie drzew wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="a642e-138">How to: Execute Expression Trees (C#)</span></span>](./how-to-execute-expression-trees.md)
- [<span data-ttu-id="a642e-139">Instrukcje: Modyfikuj drzewa wyrażeń (C#)</span><span class="sxs-lookup"><span data-stu-id="a642e-139">How to: Modify Expression Trees (C#)</span></span>](./how-to-modify-expression-trees.md)
- [<span data-ttu-id="a642e-140">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="a642e-140">Lambda Expressions</span></span>](../../statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="a642e-141">Przegląd środowiska uruchomieniowego języka dynamicznego</span><span class="sxs-lookup"><span data-stu-id="a642e-141">Dynamic Language Runtime Overview</span></span>](../../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)
- [<span data-ttu-id="a642e-142">Koncepcje programowaniaC#()</span><span class="sxs-lookup"><span data-stu-id="a642e-142">Programming Concepts (C#)</span></span>](../index.md)
