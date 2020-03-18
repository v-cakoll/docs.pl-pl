---
title: Wyrażenia Lambda - Przewodnik programowania C#
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: c549b9fcc91401aed846afd39e656b60e16afb74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937601"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="4ad75-102">Wyrażenia Lambda (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="4ad75-102">Lambda expressions (C# Programming Guide)</span></span>

<span data-ttu-id="4ad75-103">Wyrażenie *lambda* jest wyrazem dowolnej z następujących dwóch form:</span><span class="sxs-lookup"><span data-stu-id="4ad75-103">A *lambda expression* is an expression of any of the following two forms:</span></span>

- <span data-ttu-id="4ad75-104">[Wyrażenie lambda,](#expression-lambdas) które ma wyrażenie jako jego treść:</span><span class="sxs-lookup"><span data-stu-id="4ad75-104">[Expression lambda](#expression-lambdas) that has an expression as its body:</span></span>

  ```csharp
  (input-parameters) => expression
  ```

- <span data-ttu-id="4ad75-105">[Oświadczenie lambda,](#statement-lambdas) który ma blok instrukcji jako jego ciało:</span><span class="sxs-lookup"><span data-stu-id="4ad75-105">[Statement lambda](#statement-lambdas) that has a statement block as its body:</span></span>

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

<span data-ttu-id="4ad75-106">Użyj [operatora `=>` deklaracji lambda,](../../language-reference/operators/lambda-operator.md) aby oddzielić listę parametrów lambdy od jego treści.</span><span class="sxs-lookup"><span data-stu-id="4ad75-106">Use the [lambda declaration operator `=>`](../../language-reference/operators/lambda-operator.md) to separate the lambda's parameter list from its body.</span></span> <span data-ttu-id="4ad75-107">Aby utworzyć wyrażenie lambda, należy określić parametry wejściowe (jeśli istnieją) po lewej stronie operatora lambda i wyrażenie lub blok instrukcji po drugiej stronie.</span><span class="sxs-lookup"><span data-stu-id="4ad75-107">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator and an expression or a statement block on the other side.</span></span>

<span data-ttu-id="4ad75-108">Każde wyrażenie lambda można przekonwertować na typ [delegata.](../../language-reference/builtin-types/reference-types.md#the-delegate-type)</span><span class="sxs-lookup"><span data-stu-id="4ad75-108">Any lambda expression can be converted to a [delegate](../../language-reference/builtin-types/reference-types.md#the-delegate-type) type.</span></span> <span data-ttu-id="4ad75-109">Typ delegata, na który można przekonwertować wyrażenie lambda, jest definiowany przez typy jego parametrów i wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="4ad75-109">The delegate type to which a lambda expression can be converted is defined by the types of its parameters and return value.</span></span> <span data-ttu-id="4ad75-110">Jeśli wyrażenie lambda nie zwraca wartości, można go przekonwertować `Action` na jeden z typów delegatów; w przeciwnym razie można go przekonwertować na jeden z typów delegatów. `Func`</span><span class="sxs-lookup"><span data-stu-id="4ad75-110">If a lambda expression doesn't return a value, it can be converted to one of the `Action` delegate types; otherwise, it can be converted to one of the `Func` delegate types.</span></span> <span data-ttu-id="4ad75-111">Na przykład wyrażenie lambda, które ma dwa parametry i zwraca <xref:System.Action%602> wartość nie można przekonwertować na delegata.</span><span class="sxs-lookup"><span data-stu-id="4ad75-111">For example, a lambda expression that has two parameters and returns no value can be converted to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="4ad75-112">Wyrażenie lambda, który ma jeden parametr i zwraca <xref:System.Func%602> wartość można przekonwertować na delegata.</span><span class="sxs-lookup"><span data-stu-id="4ad75-112">A lambda expression that has one parameter and returns a value can be converted to a <xref:System.Func%602> delegate.</span></span> <span data-ttu-id="4ad75-113">W poniższym przykładzie wyrażenie `x => x * x`lambda , które określa parametr, który jest nazwany `x` i zwraca wartość kwadratu, `x` jest przypisany do zmiennej typu delegata:</span><span class="sxs-lookup"><span data-stu-id="4ad75-113">In the following example, the lambda expression `x => x * x`, which specifies a parameter that’s named `x` and returns the value of `x` squared, is assigned to a variable of a delegate type:</span></span>

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="4ad75-114">Wyrażenie lambdas również można przekonwertować na typy [drzewa wyrażeń,](../concepts/expression-trees/index.md) jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4ad75-114">Expression lambdas also can be converted to the [expression tree](../concepts/expression-trees/index.md) types, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="4ad75-115">Wyrażenia lambda można użyć w dowolnym kodzie, który wymaga wystąpień typów delegatów <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> lub drzew wyrażeń, na przykład jako argument do metody, aby przekazać kod, który powinien być wykonywany w tle.</span><span class="sxs-lookup"><span data-stu-id="4ad75-115">You can use lambda expressions in any code that requires instances of delegate types or expression trees, for example as an argument to the <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> method to pass the code that should be executed in the background.</span></span> <span data-ttu-id="4ad75-116">Można również użyć wyrażeń lambda podczas pisania [LINQ w języku C#,](../../linq/index.md)jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4ad75-116">You also can use lambda expressions when you write [LINQ in C#](../../linq/index.md), as the following example shows:</span></span>

[!code-csharp-interactive[lambda is argument in LINQ](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="4ad75-117">W przypadku użycia składni opartej <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> na metodach do wywołania metody w <xref:System.Linq.Enumerable?displayProperty=nameWithType> klasie, na przykład w LINQ <xref:System.Func%602?displayProperty=nameWithType>do obiektów i LINQ do XML, parametr jest typem delegata .</span><span class="sxs-lookup"><span data-stu-id="4ad75-117">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class, for example in LINQ to Objects and LINQ to XML, the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4ad75-118">Podczas wywoływania <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> metody <xref:System.Linq.Queryable?displayProperty=nameWithType> w klasie, na przykład w LINQ do SQL, [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>)typ parametru jest typem drzewa wyrażeń .</span><span class="sxs-lookup"><span data-stu-id="4ad75-118">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class, for example in LINQ to SQL, the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="4ad75-119">W obu przypadkach można użyć tego samego wyrażenia lambda, aby określić wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="4ad75-119">In both cases you can use the same lambda expression to specify the parameter value.</span></span> <span data-ttu-id="4ad75-120">To sprawia, `Select` że dwa wywołania wyglądać podobnie, chociaż w rzeczywistości typ obiektów utworzonych z lambdas jest inny.</span><span class="sxs-lookup"><span data-stu-id="4ad75-120">That makes the two `Select` calls to look similar although in fact the type of objects created from the lambdas is different.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="4ad75-121">Wyrażenie lambdas</span><span class="sxs-lookup"><span data-stu-id="4ad75-121">Expression lambdas</span></span>

<span data-ttu-id="4ad75-122">Wyrażenie lambda z wyrażeniem po prawej `=>` stronie operatora jest nazywany *wyrażenie lambda*.</span><span class="sxs-lookup"><span data-stu-id="4ad75-122">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="4ad75-123">Wyrażenie lambdas są szeroko stosowane w budowie [drzew ekspresji](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="4ad75-123">Expression lambdas are used extensively in the construction of [expression trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="4ad75-124">Lambda wyrażenia zwraca wynik wyrażenia i ma następującą podstawową formę:</span><span class="sxs-lookup"><span data-stu-id="4ad75-124">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="4ad75-125">Nawiasy są opcjonalne tylko wtedy, gdy lambda ma jeden parametr wejściowy; w przeciwnym razie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="4ad75-125">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="4ad75-126">Określanie braku parametrów wejściowych za pomocą pustych nawiasów:</span><span class="sxs-lookup"><span data-stu-id="4ad75-126">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="4ad75-127">Jeśli liczba parametrów wejściowych wynosi dwa lub więcej, te parametry są rozdzielane przecinkami i umieszczone w nawiasach:</span><span class="sxs-lookup"><span data-stu-id="4ad75-127">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="4ad75-128">Czasami jest niemożliwe dla kompilatora wywnioskować typy danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="4ad75-128">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="4ad75-129">Można określić typy jawnie, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4ad75-129">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="4ad75-130">Typy parametrów wejściowych muszą być wszystkie jawne lub wszystkie niejawne; w przeciwnym razie wystąpi błąd kompilatora [CS0748.](../../misc/cs0748.md)</span><span class="sxs-lookup"><span data-stu-id="4ad75-130">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="4ad75-131">Treść wyrażenia lambda może składać się z wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="4ad75-131">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="4ad75-132">Jednak jeśli tworzysz drzewa wyrażeń, które są oceniane poza kontekstem .NET common language runtime, takich jak w programie SQL Server, nie należy używać wywołań metody w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="4ad75-132">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="4ad75-133">Te metody nie będą zrozumiałe poza kontekstem środowiska uruchomieniowego języka wspólnego platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="4ad75-133">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="4ad75-134">Oświadczenie lambdas</span><span class="sxs-lookup"><span data-stu-id="4ad75-134">Statement lambdas</span></span>

<span data-ttu-id="4ad75-135">Lambda instrukcji jest podobna do lambdy wyrażenia, z tym że instrukcje są ujęte w nawiasy klamrowe:</span><span class="sxs-lookup"><span data-stu-id="4ad75-135">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

<span data-ttu-id="4ad75-136">Treść lambdy instrukcji może składać się z dowolnej liczby instrukcji, jednak w praktyce jest ich zwykle nie więcej niż dwie lub trzy.</span><span class="sxs-lookup"><span data-stu-id="4ad75-136">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="4ad75-137">Instrukcja lambdas nie można użyć do tworzenia drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="4ad75-137">Statement lambdas cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="4ad75-138">Async lambdas</span><span class="sxs-lookup"><span data-stu-id="4ad75-138">Async lambdas</span></span>

<span data-ttu-id="4ad75-139">Można łatwo tworzyć wyrażenia lambda i instrukcje, które zawierają przetwarzanie asynchroniczne przy użyciu [asynchronicznych](../../language-reference/keywords/async.md) i [await](../../language-reference/operators/await.md) słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="4ad75-139">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../language-reference/keywords/async.md) and [await](../../language-reference/operators/await.md) keywords.</span></span> <span data-ttu-id="4ad75-140">Na przykład poniższy przykład formularzy systemu Windows zawiera program obsługi zdarzeń, który wywołuje i oczekuje na metodę asynchronia . `ExampleMethodAsync`</span><span class="sxs-lookup"><span data-stu-id="4ad75-140">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="4ad75-141">Można dodać ten sam program obsługi zdarzeń, używając lambdy asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="4ad75-141">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="4ad75-142">Aby dodać ten program `async` obsługi, dodaj modyfikator przed listą parametrów lambda, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="4ad75-142">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

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

<span data-ttu-id="4ad75-143">Aby uzyskać więcej informacji na temat tworzenia i używania metod asynchronicznych, zobacz [Programowanie asynchroniczne z asynchroniczną asynchroniczną i oczekując](../concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="4ad75-143">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="4ad75-144">Wyrażenia lambda i krotek</span><span class="sxs-lookup"><span data-stu-id="4ad75-144">Lambda expressions and tuples</span></span>

<span data-ttu-id="4ad75-145">Począwszy od języka C# 7.0, język Języka C# zapewnia wbudowaną obsługę [krotek](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="4ad75-145">Starting with C# 7.0, the C# language provides built-in support for [tuples](../../tuples.md).</span></span> <span data-ttu-id="4ad75-146">Można podać krotki jako argument do wyrażenia lambda i wyrażenie lambda można również zwrócić krotki.</span><span class="sxs-lookup"><span data-stu-id="4ad75-146">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="4ad75-147">W niektórych przypadkach kompilator C# używa wnioskowania o typie do określenia typów składników krotki.</span><span class="sxs-lookup"><span data-stu-id="4ad75-147">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="4ad75-148">Krotkę można zdefiniować, załączając listę jej składników rozdzielaną przecinkami w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="4ad75-148">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="4ad75-149">W poniższym przykładzie użyto krotki z trzema składnikami, aby przekazać sekwencję liczb do wyrażenia lambda, które podwaja każdą wartość i zwraca krotkę z trzema składnikami, która zawiera wynik mnożenia.</span><span class="sxs-lookup"><span data-stu-id="4ad75-149">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="4ad75-150">Zwykle pola krotki są nazwane `Item1`, `Item2`itp. Można jednak zdefiniować krotkę z nazwanymi składnikami, tak jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4ad75-150">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="4ad75-151">Aby uzyskać więcej informacji na temat krotek języka C#, zobacz [Typy krotki języka C#.](../../tuples.md)</span><span class="sxs-lookup"><span data-stu-id="4ad75-151">For more information about C# tuples, see [C# tuple types](../../tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="4ad75-152">Lambdas ze standardowymi operatorami zapytań</span><span class="sxs-lookup"><span data-stu-id="4ad75-152">Lambdas with the standard query operators</span></span>

<span data-ttu-id="4ad75-153">LINQ do obiektów, wśród innych implementacji mają parametr wejściowy, którego typ jest jednym z <xref:System.Func%601> rodziny delegatów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="4ad75-153">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="4ad75-154">Te delegatów użyć parametrów typu do definiowania liczby i typu parametrów wejściowych i zwracany typ delegata.</span><span class="sxs-lookup"><span data-stu-id="4ad75-154">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="4ad75-155">`Func`delegatów są bardzo przydatne do hermetyzacji wyrażenia zdefiniowane przez użytkownika, które są stosowane do każdego elementu w zestawie danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="4ad75-155">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="4ad75-156">Rozważmy na <xref:System.Func%602> przykład typ delegata:</span><span class="sxs-lookup"><span data-stu-id="4ad75-156">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="4ad75-157">Delegata można utworzyć wystąpienie jako `Func<int, bool>` wystąpienie, `int` w którym `bool` jest parametrem wejściowym i jest wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="4ad75-157">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="4ad75-158">Wartość zwracana jest zawsze określona w ostatnim parametrze typu.</span><span class="sxs-lookup"><span data-stu-id="4ad75-158">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="4ad75-159">Na przykład `Func<int, string, bool>` definiuje delegata z dwoma parametrami wejściowymi `int` i `string` `bool`, i typu zwracanego .</span><span class="sxs-lookup"><span data-stu-id="4ad75-159">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="4ad75-160">Następujący `Func` delegat, gdy jest wywoływany, zwraca wartość logiczną, która wskazuje, czy parametr wejściowy jest równa pięciu:</span><span class="sxs-lookup"><span data-stu-id="4ad75-160">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="4ad75-161">Można również podać wyrażenie lambda, gdy <xref:System.Linq.Expressions.Expression%601>typ argumentu jest , na przykład w <xref:System.Linq.Queryable> standardowych operatorów kwerend, które są zdefiniowane w typie.</span><span class="sxs-lookup"><span data-stu-id="4ad75-161">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="4ad75-162">Po określeniu <xref:System.Linq.Expressions.Expression%601> argumentu lambda jest kompilowany do drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="4ad75-162">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="4ad75-163">W poniższym <xref:System.Linq.Enumerable.Count%2A> przykładzie użyto standardowego operatora kwerendy:</span><span class="sxs-lookup"><span data-stu-id="4ad75-163">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="4ad75-164">Kompilator może wywnioskować typ parametru wejściowego, ale można go również określić w sposób jawny.</span><span class="sxs-lookup"><span data-stu-id="4ad75-164">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="4ad75-165">To szczególne wyrażenie lambda zlicza`n`te liczby całkowite ( ), które po podziale przez dwa mają pozostałą część 1.</span><span class="sxs-lookup"><span data-stu-id="4ad75-165">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="4ad75-166">Poniższy przykład tworzy sekwencję, która zawiera `numbers` wszystkie elementy w tablicy, które poprzedzają 9, ponieważ jest to pierwsza liczba w sekwencji, która nie spełnia warunku:</span><span class="sxs-lookup"><span data-stu-id="4ad75-166">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="4ad75-167">W poniższym przykładzie określono wiele parametrów wejściowych, załączając je w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="4ad75-167">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="4ad75-168">Metoda zwraca wszystkie elementy `numbers` w tablicy, dopóki nie napotka liczby, której wartość jest mniejsza niż jego pozycja porządna w tablicy:</span><span class="sxs-lookup"><span data-stu-id="4ad75-168">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="4ad75-169">Wnioskowanie o typie w wyrażeniach lambda</span><span class="sxs-lookup"><span data-stu-id="4ad75-169">Type inference in lambda expressions</span></span>

<span data-ttu-id="4ad75-170">Podczas pisania lambdas, często nie trzeba określić typ dla parametrów wejściowych, ponieważ kompilator można wywnioskować typ na podstawie obiektu lambda, typy parametrów i inne czynniki opisane w specyfikacji języka C#.</span><span class="sxs-lookup"><span data-stu-id="4ad75-170">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="4ad75-171">Dla większości standardowych operatorów zapytań pierwszy element danych wejściowych jest typem elementów w sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="4ad75-171">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="4ad75-172">Jeśli jesteś wykonywania `IEnumerable<Customer>`kwerendy , a następnie zmienna `Customer` wejściowa jest wywnioskować jako obiekt, co oznacza, że masz dostęp do jego metod i właściwości:</span><span class="sxs-lookup"><span data-stu-id="4ad75-172">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="4ad75-173">Ogólne zasady wnioskowania o typie lambdas są następujące:</span><span class="sxs-lookup"><span data-stu-id="4ad75-173">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="4ad75-174">Wyrażenie lambda musi zawierać taką samą liczbę parametrów jak typ delegata.</span><span class="sxs-lookup"><span data-stu-id="4ad75-174">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="4ad75-175">Każdy parametr wejściowy w wyrażeniu lambda musi umożliwiać niejawną konwersję na odpowiadający mu parametr delegata.</span><span class="sxs-lookup"><span data-stu-id="4ad75-175">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="4ad75-176">Wartość zwracana wyrażenia lambda (jeżeli istnieje) musi umożliwiać niejawną konwersję na zwracany typ delegata.</span><span class="sxs-lookup"><span data-stu-id="4ad75-176">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="4ad75-177">Należy zauważyć, że wyrażenia lambda same w sobie nie mają typu, ponieważ wspólny system typów nie ma wewnętrznej koncepcji "wyrażenia lambda".</span><span class="sxs-lookup"><span data-stu-id="4ad75-177">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="4ad75-178">Jednak czasami wygodnie jest mówić nieformalnie o "typie" wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="4ad75-178">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="4ad75-179">W takich przypadkach typ odnosi się do <xref:System.Linq.Expressions.Expression> typu lub typu delegata, na które konwertowano wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="4ad75-179">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="4ad75-180">Przechwytywanie zmiennych zewnętrznych i zakresu zmiennych w wyrażeniach lambda</span><span class="sxs-lookup"><span data-stu-id="4ad75-180">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="4ad75-181">Lambdas może odwoływać się do *zmiennych zewnętrznych*.</span><span class="sxs-lookup"><span data-stu-id="4ad75-181">Lambdas can refer to *outer variables*.</span></span> <span data-ttu-id="4ad75-182">Są to zmienne, które znajdują się w zakresie w metodzie, która definiuje wyrażenie lambda lub w zakresie w typie, który zawiera wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="4ad75-182">These are the variables that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="4ad75-183">Przechwytywane w ten sposób zmienne są przechowywane do użytku w wyrażeniu lambda, nawet gdyby w innym wypadku te zmienne znalazłyby się poza zakresem i zostałyby usunięte w ramach odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="4ad75-183">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="4ad75-184">Zewnętrzna zmienna musi być zdecydowanie przypisana, aby można jej było użyć w wyrażeniu lambda.</span><span class="sxs-lookup"><span data-stu-id="4ad75-184">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="4ad75-185">W poniższym przykładzie pokazano te reguły:</span><span class="sxs-lookup"><span data-stu-id="4ad75-185">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="4ad75-186">Do zakresu zmiennych w wyrażeniach lambda są stosowane następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="4ad75-186">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="4ad75-187">Zmienna, która jest przechwytywana, nie będzie usuwana w ramach odśmiecania pamięci, dopóki odwołujący się do niej delegat nie będzie podlegał odśmiecaniu pamięci.</span><span class="sxs-lookup"><span data-stu-id="4ad75-187">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="4ad75-188">Zmienne wprowadzone w wyrażeniu lambda nie są widoczne w otaczającej metody.</span><span class="sxs-lookup"><span data-stu-id="4ad75-188">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="4ad75-189">Wyrażenie lambda nie może bezpośrednio przechwytywać [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)lub [out](../../language-reference/keywords/out-parameter-modifier.md) parametr u otaczania metody.</span><span class="sxs-lookup"><span data-stu-id="4ad75-189">A lambda expression cannot directly capture an [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="4ad75-190">Return [return](../../language-reference/keywords/return.md) instrukcji w wyrażeniu lambda nie powoduje otaczającej metody do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="4ad75-190">A [return](../../language-reference/keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="4ad75-191">Wyrażenie lambda nie może zawierać [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md), lub [continue](../../language-reference/keywords/continue.md) instrukcji, jeśli obiekt docelowy tej instrukcji skoku znajduje się poza blokiem wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="4ad75-191">A lambda expression cannot contain a [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md), or [continue](../../language-reference/keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="4ad75-192">Jest to również błąd, aby mieć instrukcję skoku poza blokiem wyrażenia lambda, jeśli obiekt docelowy znajduje się wewnątrz bloku.</span><span class="sxs-lookup"><span data-stu-id="4ad75-192">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4ad75-193">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4ad75-193">C# language specification</span></span>

<span data-ttu-id="4ad75-194">Aby uzyskać więcej informacji, zobacz [anonimowe wyrażenia funkcji](~/_csharplang/spec/expressions.md#anonymous-function-expressions) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="4ad75-194">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="4ad75-195">Polecany rozdział książki</span><span class="sxs-lookup"><span data-stu-id="4ad75-195">Featured book chapter</span></span>

<span data-ttu-id="4ad75-196">[Delegaci, zdarzenia i wyrażenia Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [książce kucharskiej C# 3.0, wydanie trzecie: ponad 250 rozwiązań dla programistów Języka C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="4ad75-196">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ad75-197">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4ad75-197">See also</span></span>

- [<span data-ttu-id="4ad75-198">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="4ad75-198">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4ad75-199">LINQ (zapytanie zintegrowane z językiem)</span><span class="sxs-lookup"><span data-stu-id="4ad75-199">LINQ (Language-Integrated Query)</span></span>](../concepts/linq/index.md)
- [<span data-ttu-id="4ad75-200">Drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="4ad75-200">Expression Trees</span></span>](../concepts/expression-trees/index.md)
- [<span data-ttu-id="4ad75-201">Funkcje lokalne w porównaniu z wyrażeniami lambda</span><span class="sxs-lookup"><span data-stu-id="4ad75-201">Local functions compared to lambda expressions</span></span>](../../local-functions-vs-lambdas.md)
- [<span data-ttu-id="4ad75-202">Wyrażenia lambda wpisane niejawnie</span><span class="sxs-lookup"><span data-stu-id="4ad75-202">Implicitly typed lambda expressions</span></span>](../../implicitly-typed-lambda-expressions.md)
- [<span data-ttu-id="4ad75-203">Przykłady języka C# programu Visual Studio 2008 (zobacz pliki przykładowych zapytań LINQ i program XQuery)</span><span class="sxs-lookup"><span data-stu-id="4ad75-203">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [<span data-ttu-id="4ad75-204">Cykliczne wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="4ad75-204">Recursive lambda expressions</span></span>](https://docs.microsoft.com/archive/blogs/madst/recursive-lambda-expressions)
