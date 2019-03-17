---
title: Wyrażenia lambda - C# Programming Guide
ms.custom: seodec18
ms.date: 03/14/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: dd9b77a90030a96d17104c8c0e48964b6a85d165
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125736"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="66ea7-102">Wyrażenia lambda (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="66ea7-102">Lambda expressions (C# Programming Guide)</span></span>

<span data-ttu-id="66ea7-103">A *wyrażenia lambda* to blok kodu (wyrażenia lub blok instrukcji), który jest traktowany jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="66ea7-103">A *lambda expression* is a block of code (an expression or a statement block) that is treated as an object.</span></span> <span data-ttu-id="66ea7-104">Może być przekazywany jako argument do metody, a także mogą być zwrócone przez funkcję wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="66ea7-104">It can be passed as an argument to methods, and it can also be returned by method calls.</span></span> <span data-ttu-id="66ea7-105">Wyrażenia lambda są często używane do:</span><span class="sxs-lookup"><span data-stu-id="66ea7-105">Lambda expressions are used extensively for:</span></span>

- <span data-ttu-id="66ea7-106">Przekazywanie kodu, który jest wykonywany do metod asynchronicznych, takich jak <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="66ea7-106">Passing the code that is to be executed to asynchronous methods, such as <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="66ea7-107">Zapisywanie [wyrażenia zapytań LINQ](../../linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="66ea7-107">Writing [LINQ query expressions](../../linq/index.md).</span></span>

- <span data-ttu-id="66ea7-108">Tworzenie [drzew wyrażeń](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="66ea7-108">Creating [expression trees](../concepts/expression-trees/index.md).</span></span>

<span data-ttu-id="66ea7-109">Wyrażenia lambda są kod, który może być reprezentowany jako obiekt delegowany lub jako drzewo wyrażenia, który kompiluje do delegata.</span><span class="sxs-lookup"><span data-stu-id="66ea7-109">Lambda expressions are code that can be represented either as a delegate, or as an expression tree that compiles to a delegate.</span></span> <span data-ttu-id="66ea7-110">Typ delegata określonego wyrażenia lambda jest zależna od jego parametrów i zwracają wartość.</span><span class="sxs-lookup"><span data-stu-id="66ea7-110">The specific delegate type of a lambda expression depends on its parameters and return value.</span></span> <span data-ttu-id="66ea7-111">Wyrażenia lambda, które nie zwracają wartości odpowiadają określonym `Action` delegować, w zależności od jego liczba parametrów.</span><span class="sxs-lookup"><span data-stu-id="66ea7-111">Lambda expressions that don't return a value correspond to a specific `Action` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="66ea7-112">Wyrażenia lambda, które zwracają wartości odpowiadają określonym `Func` delegować, w zależności od jego liczba parametrów.</span><span class="sxs-lookup"><span data-stu-id="66ea7-112">Lambda expressions that return a value correspond to a specific `Func` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="66ea7-113">Na przykład, wyrażenie lambda, która ma dwa parametry, ale nie zwraca żadnej wartości odnosi się do <xref:System.Action%602> delegować.</span><span class="sxs-lookup"><span data-stu-id="66ea7-113">For example, a lambda expression that has two parameters but returns no value corresponds to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="66ea7-114">Wyrażenie lambda, która ma jeden parametr i zwraca wartość odpowiada <xref:System.Func%602> delegować.</span><span class="sxs-lookup"><span data-stu-id="66ea7-114">A lambda expression that has one parameter and returns a value corresponds to <xref:System.Func%602> delegate.</span></span>

<span data-ttu-id="66ea7-115">Używa wyrażenia lambda `=>`, [operatora deklaracji lambda](../../language-reference/operators/lambda-operator.md), aby oddzielić listą parametrów lambda z jego kodu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="66ea7-115">A lambda expression uses `=>`, the [lambda declaration operator](../../language-reference/operators/lambda-operator.md), to separate the lambda's parameter list from its executable code.</span></span> <span data-ttu-id="66ea7-116">Aby utworzyć wyrażenie lambda, należy określić parametry wejściowe (jeśli istnieją) po lewej stronie operatora lambda i umieścić blok wyrażenia lub instrukcji po drugiej stronie.</span><span class="sxs-lookup"><span data-stu-id="66ea7-116">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator, and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="66ea7-117">Na przykład, wyrażenie lambda jednowierszowego `x => x * x` określa parametr o nazwie `x` i zwraca wartość `x` kwadratów.</span><span class="sxs-lookup"><span data-stu-id="66ea7-117">For example, the single-line lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="66ea7-118">To wyrażenie można przypisać do typu delegata, tak jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="66ea7-118">You can assign this expression to a delegate type, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="66ea7-119">Można także przypisać wyrażenia lambda do Typ drzewa wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="66ea7-119">You also can assign a lambda expression to an expression tree type:</span></span>

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="66ea7-120">Lub można je przekazać bezpośrednio jako argumentu metody:</span><span class="sxs-lookup"><span data-stu-id="66ea7-120">Or you can pass it directly as a method argument:</span></span>

[!code-csharp-interactive[lambda is argument](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="66ea7-121">Kiedy używasz składni oparte na metodzie do wywołania <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in Class metoda <xref:System.Linq.Enumerable?displayProperty=nameWithType> klasy (tak jak w technologii LINQ do obiektów i LINQ to XML) parametr jest typem delegowanym <xref:System.Func%602?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="66ea7-121">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class (as you do in LINQ to Objects and LINQ to XML) the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="66ea7-122">Użycie wyrażenia lambda jest najwygodniejszym sposobem tworzenia delegata.</span><span class="sxs-lookup"><span data-stu-id="66ea7-122">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="66ea7-123">Gdy wywołujesz <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in Class metoda <xref:System.Linq.Queryable?displayProperty=nameWithType> klasy (tak jak w składniku LINQ to SQL) typ parametru jest typ drzewa wyrażeń [ `Expression<Func<TSource,TResult>>` ](<xref:System.Linq.Expressions.Expression%601>).</span><span class="sxs-lookup"><span data-stu-id="66ea7-123">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class (as you do in LINQ to SQL) the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="66ea7-124">I znowu wyrażenie lambda jest tylko bardzo zwięzłym sposobem konstruowania takiego drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="66ea7-124">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="66ea7-125">Dzięki wyrażeniom lambda `Select` wywołania wyglądają podobnie, choć w rzeczywistości typ obiektu utworzonego z lambdy jest inny.</span><span class="sxs-lookup"><span data-stu-id="66ea7-125">The lambdas allow the `Select` calls to look similar although in fact the type of object created from the lambda is different.</span></span>

<span data-ttu-id="66ea7-126">Wszystkie ograniczenia, które są stosowane do [anonimowymi](anonymous-methods.md) dotyczą także wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="66ea7-126">All restrictions that apply to [anonymous methods](anonymous-methods.md) also apply to lambda expressions.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="66ea7-127">Lambdy wyrażeń</span><span class="sxs-lookup"><span data-stu-id="66ea7-127">Expression lambdas</span></span>

<span data-ttu-id="66ea7-128">Wyrażenie lambda z wyrażeniem po prawej stronie `=>` operator jest nazywany *wyrażenia lambda*.</span><span class="sxs-lookup"><span data-stu-id="66ea7-128">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="66ea7-129">Lambdy wyrażeń są często używane w konstrukcji [drzew wyrażeń](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="66ea7-129">Expression lambdas are used extensively in the construction of [expression trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="66ea7-130">Lambda wyrażenia zwraca wynik wyrażenia i ma następującą podstawową formę:</span><span class="sxs-lookup"><span data-stu-id="66ea7-130">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="66ea7-131">Nawiasy są opcjonalne tylko wtedy, gdy lambda ma jeden parametr wejściowy; w przeciwnym razie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="66ea7-131">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="66ea7-132">Określanie braku parametrów wejściowych za pomocą pustych nawiasów:</span><span class="sxs-lookup"><span data-stu-id="66ea7-132">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="66ea7-133">Jeśli liczba parametrów wejściowych wynosi dwa lub więcej, te parametry są rozdzielane przecinkami i umieszczone w nawiasach:</span><span class="sxs-lookup"><span data-stu-id="66ea7-133">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="66ea7-134">Czasami niemożliwe jest dla kompilatora wywnioskowanie typów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="66ea7-134">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="66ea7-135">Można określić typy jawne, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="66ea7-135">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="66ea7-136">Typy parametru wejściowego muszą być wszystkie jawne lub niejawne; w przeciwnym razie [CS0748](../../misc/cs0748.md) występuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="66ea7-136">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="66ea7-137">Treść wyrażenia lambda może zawierać wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="66ea7-137">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="66ea7-138">Jednak w przypadku tworzenia drzew wyrażeń, które są obliczane poza kontekstem .NET środowiska uruchomieniowego języka wspólnego, takie jak w programie SQL Server, możesz nie należy używać metody wywołań w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="66ea7-138">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="66ea7-139">Te metody nie będą zrozumiałe poza kontekstem środowiska uruchomieniowego języka wspólnego platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="66ea7-139">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="66ea7-140">Lambdy instrukcji</span><span class="sxs-lookup"><span data-stu-id="66ea7-140">Statement lambdas</span></span>

<span data-ttu-id="66ea7-141">Lambda instrukcji jest podobna do lambdy wyrażenia, z tym że instrukcje są ujęte w nawiasy klamrowe:</span><span class="sxs-lookup"><span data-stu-id="66ea7-141">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { statement; }
```

<span data-ttu-id="66ea7-142">Treść lambdy instrukcji może składać się z dowolnej liczby instrukcji, jednak w praktyce jest ich zwykle nie więcej niż dwie lub trzy.</span><span class="sxs-lookup"><span data-stu-id="66ea7-142">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="66ea7-143">Lambd instrukcji, podobnie jak metod anonimowych, nie można używać do tworzenia drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="66ea7-143">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="66ea7-144">Lambdy asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="66ea7-144">Async lambdas</span></span>

<span data-ttu-id="66ea7-145">Możesz łatwo tworzyć wyrażenia lambda i instrukcje, które zawierają Przetwarzanie asynchroniczne przy użyciu [async](../../language-reference/keywords/async.md) i [await](../../language-reference/keywords/await.md) słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="66ea7-145">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../language-reference/keywords/async.md) and [await](../../language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="66ea7-146">Na przykład, poniższy przykład Windows Forms zawiera program obsługi zdarzeń, który wywołuje i czeka na metodę asynchroniczną `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="66ea7-146">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += button1_Click;
    }

    private async void button1_Click(object sender, EventArgs e)
    {
        await ExampleMethodAsync();
        textBox1.Text += "\r\nControl returned to Click event handler.\n";
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="66ea7-147">Można dodać ten sam program obsługi zdarzeń, używając lambdy asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="66ea7-147">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="66ea7-148">Aby dodać ten program obsługi `async` modyfikator przed listą parametrów lambda, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="66ea7-148">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

```csharp
public partial class Form1 : Form
{
    public Form1()
    {
        InitializeComponent();
        button1.Click += async (sender, e) =>
        {
            await ExampleMethodAsync();
            textBox1.Text += "\r\nControl returned to Click event handler.\n";
        };
    }

    private async Task ExampleMethodAsync()
    {
        // The following line simulates a task-returning asynchronous process.
        await Task.Delay(1000);
    }
}
```

<span data-ttu-id="66ea7-149">Aby uzyskać więcej informacji na temat sposobu tworzenia i używania metod asynchronicznych, zobacz [Asynchronous Programming with async i await](../concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="66ea7-149">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="66ea7-150">Wyrażenia lambda i krotki</span><span class="sxs-lookup"><span data-stu-id="66ea7-150">Lambda expressions and tuples</span></span>

<span data-ttu-id="66ea7-151">Począwszy od C# 7.0, C# język zapewnia wbudowaną obsługę [krotek](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="66ea7-151">Starting with C# 7.0, the C# language provides built-in support for [tuples](../../tuples.md).</span></span> <span data-ttu-id="66ea7-152">Spójna Kolekcja może zapewnić jako argument do wyrażenia lambda i Wyrażenie lambda może również zwracać krotki.</span><span class="sxs-lookup"><span data-stu-id="66ea7-152">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="66ea7-153">W niektórych przypadkach kompilator języka C# używa wnioskowanie o typie, aby określić typy elementów krotki.</span><span class="sxs-lookup"><span data-stu-id="66ea7-153">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="66ea7-154">Należy zdefiniować krotki umieszczając rozdzielana przecinkami lista składników w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="66ea7-154">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="66ea7-155">W poniższym przykładzie użyto krotki z trzech składników do przekazania w sekwencji liczb do wyrażenia lambda, rozwiązanie quorum zwiększa dwukrotnie każdej wartości, która zwraca krotki z trzech składników, który zawiera wynik mnożenia.</span><span class="sxs-lookup"><span data-stu-id="66ea7-155">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="66ea7-156">Zazwyczaj są nazywane polami krotki `Item1`, `Item2`itp. Można jednak zdefiniować krotki ze składnikami nazwane, tak jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="66ea7-156">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="66ea7-157">Aby uzyskać więcej informacji na temat C# krotek, zobacz [ C# typy krotki](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="66ea7-157">For more information about C# tuples, see [C# tuple types](../../tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="66ea7-158">Lambdy ze standardowych operatorów zapytań</span><span class="sxs-lookup"><span data-stu-id="66ea7-158">Lambdas with the standard query operators</span></span>

<span data-ttu-id="66ea7-159">LINQ do obiektów, między innymi implementacjami posiada parametr wejściowy, którego typ jest jednym z <xref:System.Func%601> rodziny ogólnych delegatów.</span><span class="sxs-lookup"><span data-stu-id="66ea7-159">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="66ea7-160">Ci delegaci używać parametrów typu, aby zdefiniować liczbę i typ parametrów danych wejściowych oraz zwracany typ delegata.</span><span class="sxs-lookup"><span data-stu-id="66ea7-160">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="66ea7-161">`Func` Obiekty delegowane są bardzo przydatne do hermetyzowania wyrażeń zdefiniowanych przez użytkownika, które są stosowane do każdego elementu w zestawie danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="66ea7-161">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="66ea7-162">Na przykład, rozważmy <xref:System.Func%602> typ delegata:</span><span class="sxs-lookup"><span data-stu-id="66ea7-162">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="66ea7-163">Delegat może być utworzone jako `Func<int, bool>` wystąpienia gdzie `int` jest parametrem wejściowym i `bool` jest wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="66ea7-163">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="66ea7-164">Wartość zwracana jest zawsze określona w ostatnim parametrze typu.</span><span class="sxs-lookup"><span data-stu-id="66ea7-164">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="66ea7-165">Na przykład `Func<int, string, bool>` definiuje delegata z dwoma parametrami wejściowymi `int` i `string`, a zwracany typ `bool`.</span><span class="sxs-lookup"><span data-stu-id="66ea7-165">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="66ea7-166">Następujące `Func` delegata, gdy jest wywoływana, zwraca wartość Boolean wskazującą, czy parametr wejściowy jest równy 5:</span><span class="sxs-lookup"><span data-stu-id="66ea7-166">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="66ea7-167">Można również dostarczyć Wyrażenie lambda, gdy typ argumentu jest <xref:System.Linq.Expressions.Expression%601>, na przykład w standardowych operatorów zapytań, które są zdefiniowane w <xref:System.Linq.Queryable> typu.</span><span class="sxs-lookup"><span data-stu-id="66ea7-167">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="66ea7-168">Po określeniu <xref:System.Linq.Expressions.Expression%601> argument, wyrażenie lambda jest kompilowana do drzewa wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="66ea7-168">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="66ea7-169">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Count%2A> standardowego operatora zapytania:</span><span class="sxs-lookup"><span data-stu-id="66ea7-169">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="66ea7-170">Kompilator może wywnioskować typ parametru wejściowego, ale można go również określić w sposób jawny.</span><span class="sxs-lookup"><span data-stu-id="66ea7-170">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="66ea7-171">To konkretne wyrażenie lambda liczy te liczby całkowite (`n`) które podzielone przez dwa dają resztę 1.</span><span class="sxs-lookup"><span data-stu-id="66ea7-171">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="66ea7-172">Poniższy przykład tworzy sekwencję zawierającą wszystkie elementy w `numbers` tablica, która poprzedzać 9, ponieważ jest to pierwszy numer w sekwencji, która nie spełnia warunku:</span><span class="sxs-lookup"><span data-stu-id="66ea7-172">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="66ea7-173">W poniższym przykładzie określono wiele parametrów danych wejściowych, umieszczając je w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="66ea7-173">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="66ea7-174">Metoda ta zwraca wszystkie elementy w `numbers` tablicy, dopóki nie napotka liczby, w których wartość jest mniejsza niż jej porządkowym w tablicy:</span><span class="sxs-lookup"><span data-stu-id="66ea7-174">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="66ea7-175">Wnioskowanie o typie w wyrażeniach lambda</span><span class="sxs-lookup"><span data-stu-id="66ea7-175">Type inference in lambda expressions</span></span>

<span data-ttu-id="66ea7-176">Podczas pisania wyrażeń lambda, często nie trzeba określać typu parametrów wejściowych, ponieważ kompilator może wywnioskować typ bazując na treść lambda, typy parametrów i inne czynniki, zgodnie z opisem w C# specyfikacji języka.</span><span class="sxs-lookup"><span data-stu-id="66ea7-176">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="66ea7-177">Dla większości standardowych operatorów zapytań pierwszy element danych wejściowych jest typem elementów w sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="66ea7-177">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="66ea7-178">Jeśli jest wykonywane zapytanie `IEnumerable<Customer>`, a następnie wywnioskowana jest zmienna wejściowa jest `Customer` obiektu, co oznacza, że masz dostęp do metod i właściwości:</span><span class="sxs-lookup"><span data-stu-id="66ea7-178">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="66ea7-179">Ogólne zasady wnioskowanie o typie dla wyrażeń lambda są następujące:</span><span class="sxs-lookup"><span data-stu-id="66ea7-179">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="66ea7-180">Wyrażenie lambda musi zawierać taką samą liczbę parametrów jak typ delegata.</span><span class="sxs-lookup"><span data-stu-id="66ea7-180">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="66ea7-181">Każdy parametr wejściowy w wyrażeniu lambda musi umożliwiać niejawną konwersję na odpowiadający mu parametr delegata.</span><span class="sxs-lookup"><span data-stu-id="66ea7-181">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="66ea7-182">Wartość zwracana wyrażenia lambda (jeżeli istnieje) musi umożliwiać niejawną konwersję na zwracany typ delegata.</span><span class="sxs-lookup"><span data-stu-id="66ea7-182">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="66ea7-183">Należy pamiętać, że wyrażenia lambda same w sobie nie mają typu, ponieważ wspólny system typów nie używa wewnętrznej koncepcji "wyrażenia lambda".</span><span class="sxs-lookup"><span data-stu-id="66ea7-183">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="66ea7-184">Jednak czasami wygodnie jest mówić potocznie o "type" wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="66ea7-184">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="66ea7-185">W takich przypadkach typ odnosi się do typu delegata lub <xref:System.Linq.Expressions.Expression> typ do którego jest konwertowane Wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="66ea7-185">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="66ea7-186">Zakres zmiennych w wyrażeniach lambda</span><span class="sxs-lookup"><span data-stu-id="66ea7-186">Variable scope in lambda expressions</span></span>

<span data-ttu-id="66ea7-187">Wyrażenia lambda mogą odwoływać się do *zmiennych zewnętrznych* (zobacz [anonimowymi](anonymous-methods.md)) znajdujących się w zasięgu w metodzie, która definiuje wyrażenie lambda lub w zakresie typu, który zawiera wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="66ea7-187">Lambdas can refer to *outer variables* (see [Anonymous methods](anonymous-methods.md)) that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="66ea7-188">Przechwytywane w ten sposób zmienne są przechowywane do użytku w wyrażeniu lambda, nawet gdyby w innym wypadku te zmienne znalazłyby się poza zakresem i zostałyby usunięte w ramach odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="66ea7-188">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="66ea7-189">Zewnętrzna zmienna musi być zdecydowanie przypisana, aby można jej było użyć w wyrażeniu lambda.</span><span class="sxs-lookup"><span data-stu-id="66ea7-189">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="66ea7-190">W poniższym przykładzie pokazano te reguły:</span><span class="sxs-lookup"><span data-stu-id="66ea7-190">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="66ea7-191">Do zakresu zmiennych w wyrażeniach lambda są stosowane następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="66ea7-191">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="66ea7-192">Zmienna, która jest przechwytywana, nie będzie usuwana w ramach odśmiecania pamięci, dopóki odwołujący się do niej delegat nie będzie podlegał odśmiecaniu pamięci.</span><span class="sxs-lookup"><span data-stu-id="66ea7-192">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="66ea7-193">Zmienne zawarte w wyrażeniu lambda nie są widoczne w otaczającej go metodzie.</span><span class="sxs-lookup"><span data-stu-id="66ea7-193">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="66ea7-194">Wyrażenie lambda nie może bezpośrednio przechwycić [w](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), lub [się](../../language-reference/keywords/out-parameter-modifier.md) parametr z otaczającym metody.</span><span class="sxs-lookup"><span data-stu-id="66ea7-194">A lambda expression cannot directly capture an [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="66ea7-195">A [zwracają](../../language-reference/keywords/return.md) instrukcji w wyrażeniu lambda nie powoduje otaczającej go metodzie do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="66ea7-195">A [return](../../language-reference/keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="66ea7-196">Wyrażenie lambda nie może zawierać [goto](../../language-reference/keywords/goto.md), [podziału](../../language-reference/keywords/break.md), lub [nadal](../../language-reference/keywords/continue.md) instrukcji, jeśli obiekt docelowy, szybkie instrukcji znajduje się poza blokiem wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="66ea7-196">A lambda expression cannot contain a [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md), or [continue](../../language-reference/keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="66ea7-197">Jest również błędu, aby mieć instrukcja skoku poza blok wyrażenia lambda, jeśli element docelowy znajduje się wewnątrz bloku.</span><span class="sxs-lookup"><span data-stu-id="66ea7-197">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="66ea7-198">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="66ea7-198">C# language specification</span></span>

<span data-ttu-id="66ea7-199">Aby uzyskać więcej informacji, zobacz [wyrażenia funkcji anonimowych](~/_csharplang/spec/expressions.md#anonymous-function-expressions) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="66ea7-199">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="66ea7-200">polecany rozdział książki</span><span class="sxs-lookup"><span data-stu-id="66ea7-200">Featured book chapter</span></span>

<span data-ttu-id="66ea7-201">[Delegatów, zdarzeń i wyrażenia Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [ C# 3.0 Cookbook, Third Edition: Ponad 250 rozwiązań dla C# ekspertów w programowaniu w wersji 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="66ea7-201">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66ea7-202">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="66ea7-202">See also</span></span>

- [<span data-ttu-id="66ea7-203">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="66ea7-203">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="66ea7-204">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="66ea7-204">LINQ (Language-Integrated Query)</span></span>](../concepts/linq/index.md)
- [<span data-ttu-id="66ea7-205">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="66ea7-205">Anonymous Methods</span></span>](anonymous-methods.md)
- [<span data-ttu-id="66ea7-206">Drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="66ea7-206">Expression Trees</span></span>](../concepts/expression-trees/index.md)
- [<span data-ttu-id="66ea7-207">Funkcje lokalne w porównaniu do wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="66ea7-207">Local functions compared to lambda expressions</span></span>](../../local-functions-vs-lambdas.md)
- [<span data-ttu-id="66ea7-208">Wyrażenia lambda niejawnie wpisane</span><span class="sxs-lookup"><span data-stu-id="66ea7-208">Implicitly typed lambda expressions</span></span>](../../implicitly-typed-lambda-expressions.md)
- [<span data-ttu-id="66ea7-209">Visual Studio 2008 C# Samples (zobacz pliki LINQ przykładowe zapytania i XQuery program)</span><span class="sxs-lookup"><span data-stu-id="66ea7-209">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [<span data-ttu-id="66ea7-210">Powtarzalne wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="66ea7-210">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
