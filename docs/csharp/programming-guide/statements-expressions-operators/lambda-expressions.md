---
title: Wyrażenia lambda — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 03/14/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 546feb6f3c4515ceecdb5b5afa14c0fc99ab7020
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363907"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="83125-102">Wyrażenia lambda (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="83125-102">Lambda expressions (C# Programming Guide)</span></span>

<span data-ttu-id="83125-103">*Wyrażenie lambda* jest blokiem kodu (wyrażenie lub blok instrukcji), który jest traktowany jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="83125-103">A *lambda expression* is a block of code (an expression or a statement block) that is treated as an object.</span></span> <span data-ttu-id="83125-104">Może być przekazana jako argument do metod i może być również zwracany przez wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="83125-104">It can be passed as an argument to methods, and it can also be returned by method calls.</span></span> <span data-ttu-id="83125-105">Wyrażenia lambda są używane w szerokim stopniu dla:</span><span class="sxs-lookup"><span data-stu-id="83125-105">Lambda expressions are used extensively for:</span></span>

- <span data-ttu-id="83125-106">Przekazywanie kodu, który ma być wykonywany w metodach asynchronicznych, takich <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>jak.</span><span class="sxs-lookup"><span data-stu-id="83125-106">Passing the code that is to be executed to asynchronous methods, such as <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="83125-107">Pisanie [wyrażeń zapytań LINQ](../../linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="83125-107">Writing [LINQ query expressions](../../linq/index.md).</span></span>

- <span data-ttu-id="83125-108">Tworzenie [drzew wyrażeń](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="83125-108">Creating [expression trees](../concepts/expression-trees/index.md).</span></span>

<span data-ttu-id="83125-109">Wyrażenia lambda to kod, który może być reprezentowany jako delegat lub jako drzewo wyrażenia, które kompiluje do delegata.</span><span class="sxs-lookup"><span data-stu-id="83125-109">Lambda expressions are code that can be represented either as a delegate, or as an expression tree that compiles to a delegate.</span></span> <span data-ttu-id="83125-110">Określony typ delegata wyrażenia lambda zależy od jego parametrów i wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="83125-110">The specific delegate type of a lambda expression depends on its parameters and return value.</span></span> <span data-ttu-id="83125-111">Wyrażenia lambda, które nie zwracają wartości, odpowiadają określonemu `Action` delegatowi, w zależności od jego liczby parametrów.</span><span class="sxs-lookup"><span data-stu-id="83125-111">Lambda expressions that don't return a value correspond to a specific `Action` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="83125-112">Wyrażenia lambda, które zwracają wartość, odpowiadają określonemu `Func` delegatowi, w zależności od jego liczby parametrów.</span><span class="sxs-lookup"><span data-stu-id="83125-112">Lambda expressions that return a value correspond to a specific `Func` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="83125-113">Na przykład wyrażenie lambda, które ma dwa parametry, ale nie zwraca wartości odnosi się do <xref:System.Action%602> delegata.</span><span class="sxs-lookup"><span data-stu-id="83125-113">For example, a lambda expression that has two parameters but returns no value corresponds to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="83125-114">Wyrażenie lambda, które ma jeden parametr i zwraca wartość odnosi się do <xref:System.Func%602> delegata.</span><span class="sxs-lookup"><span data-stu-id="83125-114">A lambda expression that has one parameter and returns a value corresponds to <xref:System.Func%602> delegate.</span></span>

<span data-ttu-id="83125-115">Wyrażenie lambda używa `=>` [operatora deklaracji lambda](../../language-reference/operators/lambda-operator.md), aby oddzielić listę parametrów lambda z jego kodu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="83125-115">A lambda expression uses `=>`, the [lambda declaration operator](../../language-reference/operators/lambda-operator.md), to separate the lambda's parameter list from its executable code.</span></span> <span data-ttu-id="83125-116">Aby utworzyć wyrażenie lambda, należy określić parametry wejściowe (jeśli istnieją) po lewej stronie operatora lambda, i umieścić wyrażenie lub blok instrukcji po drugiej stronie.</span><span class="sxs-lookup"><span data-stu-id="83125-116">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator, and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="83125-117">Na przykład jednowierszowe wyrażenie `x => x * x` lambda określa parametr o nazwie `x` `x` i zwraca wartość kwadratową.</span><span class="sxs-lookup"><span data-stu-id="83125-117">For example, the single-line lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="83125-118">To wyrażenie można przypisać do typu delegata, tak jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="83125-118">You can assign this expression to a delegate type, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="83125-119">Można również przypisać wyrażenie lambda do typu drzewa wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="83125-119">You also can assign a lambda expression to an expression tree type:</span></span>

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="83125-120">Lub można przekazać ją bezpośrednio jako argument metody:</span><span class="sxs-lookup"><span data-stu-id="83125-120">Or you can pass it directly as a method argument:</span></span>

[!code-csharp-interactive[lambda is argument](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="83125-121">Przy użyciu składni opartej na metodzie wywoływanie <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> metody <xref:System.Linq.Enumerable?displayProperty=nameWithType> w klasie (jak w LINQ to Objects i LINQ to XML) parametr jest typem <xref:System.Func%602?displayProperty=nameWithType>delegata.</span><span class="sxs-lookup"><span data-stu-id="83125-121">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class (as you do in LINQ to Objects and LINQ to XML) the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="83125-122">Użycie wyrażenia lambda jest najwygodniejszym sposobem tworzenia delegata.</span><span class="sxs-lookup"><span data-stu-id="83125-122">A lambda expression is the most convenient way to create that delegate.</span></span> <span data-ttu-id="83125-123">Po wywołaniu <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> metody <xref:System.Linq.Queryable?displayProperty=nameWithType> w klasie (jak w LINQ to SQL) typem parametru jest typ [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>)drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="83125-123">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class (as you do in LINQ to SQL) the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="83125-124">I znowu wyrażenie lambda jest tylko bardzo zwięzłym sposobem konstruowania takiego drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="83125-124">Again, a lambda expression is just a very concise way to construct that expression tree.</span></span> <span data-ttu-id="83125-125">Wyrażenia lambda umożliwiają `Select` podobne wywołania, chociaż w rzeczywistości typ obiektu utworzonego na podstawie wyrażenia lambda jest inny.</span><span class="sxs-lookup"><span data-stu-id="83125-125">The lambdas allow the `Select` calls to look similar although in fact the type of object created from the lambda is different.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="83125-126">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="83125-126">Expression lambdas</span></span>

<span data-ttu-id="83125-127">Wyrażenie lambda z wyrażeniem po prawej stronie `=>` operatora jest nazywane wyrażeniem *lambda*.</span><span class="sxs-lookup"><span data-stu-id="83125-127">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="83125-128">Wyrażenia lambda są szeroko używane w konstruowaniu [drzew wyrażeń](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="83125-128">Expression lambdas are used extensively in the construction of [expression trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="83125-129">Lambda wyrażenia zwraca wynik wyrażenia i ma następującą podstawową formę:</span><span class="sxs-lookup"><span data-stu-id="83125-129">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="83125-130">Nawiasy są opcjonalne tylko wtedy, gdy lambda ma jeden parametr wejściowy; w przeciwnym razie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="83125-130">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="83125-131">Określanie braku parametrów wejściowych za pomocą pustych nawiasów:</span><span class="sxs-lookup"><span data-stu-id="83125-131">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="83125-132">Jeśli liczba parametrów wejściowych wynosi dwa lub więcej, te parametry są rozdzielane przecinkami i umieszczone w nawiasach:</span><span class="sxs-lookup"><span data-stu-id="83125-132">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="83125-133">Czasami w kompilatorze nie można wywnioskować typów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="83125-133">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="83125-134">Możesz określić typy jawnie, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="83125-134">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="83125-135">Typy parametrów wejściowych muszą być jawne lub niejawne; w przeciwnym razie wystąpi błąd kompilatora [CS0748](../../misc/cs0748.md) .</span><span class="sxs-lookup"><span data-stu-id="83125-135">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="83125-136">Treść wyrażenia lambda może składać się z wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="83125-136">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="83125-137">Jeśli jednak tworzysz drzewa wyrażeń, które są oceniane poza kontekstem środowiska uruchomieniowego języka wspólnego .NET, na przykład w SQL Server, nie należy używać wywołań metod w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="83125-137">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="83125-138">Te metody nie będą zrozumiałe poza kontekstem środowiska uruchomieniowego języka wspólnego platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="83125-138">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="83125-139">Instrukcja lambda</span><span class="sxs-lookup"><span data-stu-id="83125-139">Statement lambdas</span></span>

<span data-ttu-id="83125-140">Lambda instrukcji jest podobna do lambdy wyrażenia, z tym że instrukcje są ujęte w nawiasy klamrowe:</span><span class="sxs-lookup"><span data-stu-id="83125-140">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { statement; }
```

<span data-ttu-id="83125-141">Treść lambdy instrukcji może składać się z dowolnej liczby instrukcji, jednak w praktyce jest ich zwykle nie więcej niż dwie lub trzy.</span><span class="sxs-lookup"><span data-stu-id="83125-141">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="83125-142">Instrukcji lambda nie można używać do tworzenia drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="83125-142">Statement lambdas cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="83125-143">Asynchroniczne wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="83125-143">Async lambdas</span></span>

<span data-ttu-id="83125-144">Możesz łatwo tworzyć wyrażenia lambda i instrukcje, które zawierają asynchroniczne przetwarzanie przy użyciu słów kluczowych [Async](../../language-reference/keywords/async.md) i [await](../../language-reference/keywords/await.md) .</span><span class="sxs-lookup"><span data-stu-id="83125-144">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../language-reference/keywords/async.md) and [await](../../language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="83125-145">Na przykład poniższy Windows Forms przykład zawiera procedurę obsługi zdarzeń, która wywołuje i czeka na metodę `ExampleMethodAsync`asynchroniczną.</span><span class="sxs-lookup"><span data-stu-id="83125-145">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="83125-146">Można dodać ten sam program obsługi zdarzeń, używając lambdy asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="83125-146">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="83125-147">Aby dodać ten program obsługi, Dodaj `async` modyfikator przed listą parametrów lambda, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="83125-147">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

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

<span data-ttu-id="83125-148">Aby uzyskać więcej informacji na temat tworzenia i używania metod asynchronicznych, zobacz [programowanie asynchroniczne z Async i await](../concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="83125-148">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="83125-149">Wyrażenia lambda i krotki</span><span class="sxs-lookup"><span data-stu-id="83125-149">Lambda expressions and tuples</span></span>

<span data-ttu-id="83125-150">Począwszy od C# 7,0, C# język zapewnia wbudowaną obsługę [krotek](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="83125-150">Starting with C# 7.0, the C# language provides built-in support for [tuples](../../tuples.md).</span></span> <span data-ttu-id="83125-151">Można podać krotkę jako argument wyrażenia lambda, a wyrażenie lambda może również zwracać krotkę.</span><span class="sxs-lookup"><span data-stu-id="83125-151">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="83125-152">W niektórych przypadkach C# kompilator używa wnioskowania o typie, aby określić typy składników spójnych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="83125-152">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="83125-153">Można zdefiniować krotkę, umieszczając w nawiasach rozdzielaną przecinkami listę składników.</span><span class="sxs-lookup"><span data-stu-id="83125-153">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="83125-154">Poniższy przykład używa krotki z trzema składnikami, aby przekazać sekwencję liczb do wyrażenia lambda, które podwaja każdą wartość i zwraca spójną kolekcję z trzema składnikami, które zawierają wynik mnożenia.</span><span class="sxs-lookup"><span data-stu-id="83125-154">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="83125-155">Zwykle pola krotki mają nazwę `Item1`, `Item2`itp. Można jednak zdefiniować krotkę z nazwanymi składnikami, tak jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="83125-155">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="83125-156">Aby uzyskać więcej informacji C# na temat krotek, zobacz [ C# typy krotek](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="83125-156">For more information about C# tuples, see [C# tuple types](../../tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="83125-157">Wyrażenia lambda ze standardowymi operatorami zapytań</span><span class="sxs-lookup"><span data-stu-id="83125-157">Lambdas with the standard query operators</span></span>

<span data-ttu-id="83125-158">LINQ to Objects, między innymi implementacjami, mają parametr wejściowy, którego typ jest jedną <xref:System.Func%601> z rodziny delegatów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="83125-158">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="83125-159">Te Delegaty używają parametrów typu, aby zdefiniować liczbę i typ parametrów wejściowych oraz zwracany typ delegata.</span><span class="sxs-lookup"><span data-stu-id="83125-159">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="83125-160">`Func`Delegaty są bardzo przydatne do hermetyzowania wyrażeń zdefiniowanych przez użytkownika, które są stosowane do każdego elementu w zestawie danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="83125-160">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="83125-161">Rozważmy na przykład typ <xref:System.Func%602> delegata:</span><span class="sxs-lookup"><span data-stu-id="83125-161">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="83125-162">Delegat można utworzyć jako `Func<int, bool>` wystąpienie, gdzie `int` jest parametrem wejściowym i `bool` jest wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="83125-162">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="83125-163">Wartość zwracana jest zawsze określona w ostatnim parametrze typu.</span><span class="sxs-lookup"><span data-stu-id="83125-163">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="83125-164">Na przykład `Func<int, string, bool>` definiuje delegata z dwoma `int` parametrami wejściowymi i `string`i typem `bool`zwracanym.</span><span class="sxs-lookup"><span data-stu-id="83125-164">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="83125-165">Następujący `Func` delegat, gdy jest wywoływany, zwraca wartość logiczną, która wskazuje, czy parametr wejściowy jest równy pięć:</span><span class="sxs-lookup"><span data-stu-id="83125-165">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="83125-166">Można również podać wyrażenie lambda <xref:System.Linq.Expressions.Expression%601>, gdy typem argumentu jest, na przykład w standardowych operatorów zapytań, które są zdefiniowane <xref:System.Linq.Queryable> w typie.</span><span class="sxs-lookup"><span data-stu-id="83125-166">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="83125-167">Po określeniu <xref:System.Linq.Expressions.Expression%601> argumentu lambda jest kompilowane do drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="83125-167">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="83125-168">W poniższym przykładzie użyto <xref:System.Linq.Enumerable.Count%2A> standardowego operatora zapytania:</span><span class="sxs-lookup"><span data-stu-id="83125-168">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="83125-169">Kompilator może wywnioskować typ parametru wejściowego, ale można go również określić w sposób jawny.</span><span class="sxs-lookup"><span data-stu-id="83125-169">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="83125-170">To konkretne wyrażenie lambda liczy te liczby całkowite (`n`), które podzielone przez dwa mają resztę 1.</span><span class="sxs-lookup"><span data-stu-id="83125-170">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="83125-171">Poniższy przykład tworzy sekwencję zawierającą wszystkie elementy w `numbers` tablicy, która poprzedza 9, ponieważ jest to pierwszy numer w sekwencji, która nie spełnia warunku:</span><span class="sxs-lookup"><span data-stu-id="83125-171">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="83125-172">W poniższym przykładzie określono wiele parametrów wejściowych, umieszczając je w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="83125-172">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="83125-173">Metoda zwraca wszystkie elementy w `numbers` tablicy do momentu napotkania liczby, której wartość jest mniejsza niż jej pozycja porządkowa w tablicy:</span><span class="sxs-lookup"><span data-stu-id="83125-173">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="83125-174">Wnioskowanie o typie w wyrażeniach lambda</span><span class="sxs-lookup"><span data-stu-id="83125-174">Type inference in lambda expressions</span></span>

<span data-ttu-id="83125-175">Podczas pisania wyrażeń lambda często nie trzeba określać typu parametrów wejściowych, ponieważ kompilator może wywnioskować typ na podstawie treści wyrażenia lambda, typów parametrów i innych czynników, zgodnie z opisem w specyfikacji C# języka.</span><span class="sxs-lookup"><span data-stu-id="83125-175">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="83125-176">Dla większości standardowych operatorów zapytań pierwszy element danych wejściowych jest typem elementów w sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="83125-176">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="83125-177">Jeśli wykonujesz zapytania `IEnumerable<Customer>`, wówczas zmienna wejściowa jest wywnioskowana `Customer` jako obiekt, co oznacza, że masz dostęp do jego metod i właściwości:</span><span class="sxs-lookup"><span data-stu-id="83125-177">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="83125-178">Ogólne reguły wnioskowania o typie dla wyrażeń lambda są następujące:</span><span class="sxs-lookup"><span data-stu-id="83125-178">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="83125-179">Wyrażenie lambda musi zawierać taką samą liczbę parametrów jak typ delegata.</span><span class="sxs-lookup"><span data-stu-id="83125-179">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="83125-180">Każdy parametr wejściowy w wyrażeniu lambda musi umożliwiać niejawną konwersję na odpowiadający mu parametr delegata.</span><span class="sxs-lookup"><span data-stu-id="83125-180">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="83125-181">Wartość zwracana wyrażenia lambda (jeżeli istnieje) musi umożliwiać niejawną konwersję na zwracany typ delegata.</span><span class="sxs-lookup"><span data-stu-id="83125-181">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="83125-182">Należy zauważyć, że wyrażenia lambda same w sobie nie mają typu, ponieważ system typów wspólnych nie ma wewnętrznej koncepcji "wyrażenie lambda".</span><span class="sxs-lookup"><span data-stu-id="83125-182">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="83125-183">Jednak czasami wygodnie jest mówić nieformalnie "Type" wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="83125-183">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="83125-184">W takich przypadkach typ odwołuje się do typu delegata <xref:System.Linq.Expressions.Expression> lub typu, do którego wyrażenie lambda jest konwertowane.</span><span class="sxs-lookup"><span data-stu-id="83125-184">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="83125-185">Przechwycenie zmiennych zewnętrznych i zakresu zmiennych w wyrażeniach lambda</span><span class="sxs-lookup"><span data-stu-id="83125-185">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="83125-186">Wyrażenia lambda mogą odwoływać się do *zmiennych zewnętrznych*.</span><span class="sxs-lookup"><span data-stu-id="83125-186">Lambdas can refer to *outer variables*.</span></span> <span data-ttu-id="83125-187">Są to zmienne, które znajdują się w zakresie metody, która definiuje wyrażenie lambda lub w zakresie typu, który zawiera wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="83125-187">These are the variables that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="83125-188">Przechwytywane w ten sposób zmienne są przechowywane do użytku w wyrażeniu lambda, nawet gdyby w innym wypadku te zmienne znalazłyby się poza zakresem i zostałyby usunięte w ramach odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="83125-188">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="83125-189">Zewnętrzna zmienna musi być zdecydowanie przypisana, aby można jej było użyć w wyrażeniu lambda.</span><span class="sxs-lookup"><span data-stu-id="83125-189">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="83125-190">W poniższym przykładzie pokazano te reguły:</span><span class="sxs-lookup"><span data-stu-id="83125-190">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="83125-191">Do zakresu zmiennych w wyrażeniach lambda są stosowane następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="83125-191">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="83125-192">Zmienna, która jest przechwytywana, nie będzie usuwana w ramach odśmiecania pamięci, dopóki odwołujący się do niej delegat nie będzie podlegał odśmiecaniu pamięci.</span><span class="sxs-lookup"><span data-stu-id="83125-192">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="83125-193">Zmienne wprowadzone w wyrażeniu lambda nie są widoczne w otaczającej metodzie.</span><span class="sxs-lookup"><span data-stu-id="83125-193">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="83125-194">Wyrażenie lambda nie może bezpośrednio przechwycić parametru [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)lub [out](../../language-reference/keywords/out-parameter-modifier.md) z otaczającej metody.</span><span class="sxs-lookup"><span data-stu-id="83125-194">A lambda expression cannot directly capture an [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="83125-195">Instrukcja [Return](../../language-reference/keywords/return.md) w wyrażeniu lambda nie powoduje zwrócenia otaczającej metody.</span><span class="sxs-lookup"><span data-stu-id="83125-195">A [return](../../language-reference/keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="83125-196">Wyrażenie lambda nie może zawierać instrukcji [goto](../../language-reference/keywords/goto.md), [Break](../../language-reference/keywords/break.md)ani [Continue](../../language-reference/keywords/continue.md) , jeśli element docelowy instrukcji skoku znajduje się poza blokiem wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="83125-196">A lambda expression cannot contain a [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md), or [continue](../../language-reference/keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="83125-197">Występuje również błąd instrukcji skoku poza blokiem wyrażenia lambda, jeśli obiekt docelowy znajduje się wewnątrz bloku.</span><span class="sxs-lookup"><span data-stu-id="83125-197">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="83125-198">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="83125-198">C# language specification</span></span>

<span data-ttu-id="83125-199">Aby uzyskać więcej informacji, zobacz sekcję [wyrażenia funkcji anonimowej](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="83125-199">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="83125-200">Polecany rozdział książki</span><span class="sxs-lookup"><span data-stu-id="83125-200">Featured book chapter</span></span>

<span data-ttu-id="83125-201">[Delegaty, zdarzenia i wyrażenia lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [ C# 3,0 Cookbook, wydanie trzecie: Ponad 250 rozwiązań dla C# programistów 3,0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="83125-201">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83125-202">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83125-202">See also</span></span>

- [<span data-ttu-id="83125-203">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="83125-203">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="83125-204">LINQ (zapytanie zintegrowane z językiem)</span><span class="sxs-lookup"><span data-stu-id="83125-204">LINQ (Language-Integrated Query)</span></span>](../concepts/linq/index.md)
- [<span data-ttu-id="83125-205">Drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="83125-205">Expression Trees</span></span>](../concepts/expression-trees/index.md)
- [<span data-ttu-id="83125-206">Funkcje lokalne w porównaniu z wyrażeniami lambda</span><span class="sxs-lookup"><span data-stu-id="83125-206">Local functions compared to lambda expressions</span></span>](../../local-functions-vs-lambdas.md)
- [<span data-ttu-id="83125-207">Niejawnie wpisane wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="83125-207">Implicitly typed lambda expressions</span></span>](../../implicitly-typed-lambda-expressions.md)
- [<span data-ttu-id="83125-208">Przykłady dla programu C# Visual Studio 2008 (Zobacz pliki przykładowe zapytania LINQ i program XQuery)</span><span class="sxs-lookup"><span data-stu-id="83125-208">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [<span data-ttu-id="83125-209">Cykliczne wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="83125-209">Recursive lambda expressions</span></span>](https://blogs.msdn.microsoft.com/madst/2007/05/11/recursive-lambda-expressions/)
