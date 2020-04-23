---
title: Wyrażenia Lambda — Przewodnik programowania języka C#
ms.date: 07/29/2019
helpviewer_keywords:
- lambda expressions [C#]
- outer variables [C#]
- statement lambda [C#]
- expression lambda [C#]
- expressions [C#], lambda
ms.assetid: 57e3ba27-9a82-4067-aca7-5ca446b7bf93
ms.openlocfilehash: 6fd2dab09fe97aa4af87d82e2d23664c4347c8b3
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82101998"
---
# <a name="lambda-expressions-c-programming-guide"></a><span data-ttu-id="d17d4-102">Wyrażenia Lambda (Przewodnik programowania języka C#)</span><span class="sxs-lookup"><span data-stu-id="d17d4-102">Lambda expressions (C# Programming Guide)</span></span>

<span data-ttu-id="d17d4-103">Wyrażenie *lambda* jest wyrażeniem dowolnej z następujących dwóch form:</span><span class="sxs-lookup"><span data-stu-id="d17d4-103">A *lambda expression* is an expression of any of the following two forms:</span></span>

- <span data-ttu-id="d17d4-104">[Wyrażenie lambda,](#expression-lambdas) które ma wyrażenie jako jego ciało:</span><span class="sxs-lookup"><span data-stu-id="d17d4-104">[Expression lambda](#expression-lambdas) that has an expression as its body:</span></span>

  ```csharp
  (input-parameters) => expression
  ```

- <span data-ttu-id="d17d4-105">[Instrukcja lambda,](#statement-lambdas) która ma blok instrukcji jako jego treść:</span><span class="sxs-lookup"><span data-stu-id="d17d4-105">[Statement lambda](#statement-lambdas) that has a statement block as its body:</span></span>

  ```csharp  
  (input-parameters) => { <sequence-of-statements> }
  ```

<span data-ttu-id="d17d4-106">Operator [deklaracji `=>` lambda](../../language-reference/operators/lambda-operator.md) służy do oddzielania listy parametrów lambda od jego treści.</span><span class="sxs-lookup"><span data-stu-id="d17d4-106">Use the [lambda declaration operator `=>`](../../language-reference/operators/lambda-operator.md) to separate the lambda's parameter list from its body.</span></span> <span data-ttu-id="d17d4-107">Aby utworzyć wyrażenie lambda, należy określić parametry wejściowe (jeśli istnieją) po lewej stronie operatora lambda i wyrażenie lub blok instrukcji po drugiej stronie.</span><span class="sxs-lookup"><span data-stu-id="d17d4-107">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator and an expression or a statement block on the other side.</span></span>

<span data-ttu-id="d17d4-108">Dowolne wyrażenie lambda można przekonwertować na typ [delegata.](../../language-reference/builtin-types/reference-types.md#the-delegate-type)</span><span class="sxs-lookup"><span data-stu-id="d17d4-108">Any lambda expression can be converted to a [delegate](../../language-reference/builtin-types/reference-types.md#the-delegate-type) type.</span></span> <span data-ttu-id="d17d4-109">Typ delegata, na który można przekonwertować wyrażenie lambda, jest definiowany przez typy jego parametrów i wartość zwracaną.</span><span class="sxs-lookup"><span data-stu-id="d17d4-109">The delegate type to which a lambda expression can be converted is defined by the types of its parameters and return value.</span></span> <span data-ttu-id="d17d4-110">Jeśli wyrażenie lambda nie zwraca wartości, można go przekonwertować na `Action` jeden z typów delegata; w przeciwnym razie można go przekonwertować na `Func` jeden z typów delegata.</span><span class="sxs-lookup"><span data-stu-id="d17d4-110">If a lambda expression doesn't return a value, it can be converted to one of the `Action` delegate types; otherwise, it can be converted to one of the `Func` delegate types.</span></span> <span data-ttu-id="d17d4-111">Na przykład wyrażenie lambda, który ma dwa parametry i zwraca <xref:System.Action%602> żadną wartość można przekonwertować na pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="d17d4-111">For example, a lambda expression that has two parameters and returns no value can be converted to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="d17d4-112">Wyrażenie lambda, który ma jeden parametr i zwraca <xref:System.Func%602> wartość można przekonwertować na pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="d17d4-112">A lambda expression that has one parameter and returns a value can be converted to a <xref:System.Func%602> delegate.</span></span> <span data-ttu-id="d17d4-113">W poniższym przykładzie wyrażenie `x => x * x`lambda , które określa `x` parametr, który `x` jest nazwany i zwraca wartość kwadratu, jest przypisany do zmiennej typu delegata:</span><span class="sxs-lookup"><span data-stu-id="d17d4-113">In the following example, the lambda expression `x => x * x`, which specifies a parameter that’s named `x` and returns the value of `x` squared, is assigned to a variable of a delegate type:</span></span>

[!code-csharp-interactive[lambda is delegate](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Delegate)]

<span data-ttu-id="d17d4-114">Wyrażenie lambdas można również przekonwertować na typy [drzew wyrażeń,](../concepts/expression-trees/index.md) jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d17d4-114">Expression lambdas can also be converted to the [expression tree](../concepts/expression-trees/index.md) types, as the following example shows:</span></span>

[!code-csharp-interactive[lambda is expression tree](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#ExpressionTree)]

<span data-ttu-id="d17d4-115">Można użyć wyrażeń lambda w dowolnym kodzie, który wymaga wystąpień typów <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> delegatów lub drzew wyrażeń, na przykład jako argument do metody przekazywania kodu, który powinien być wykonywany w tle.</span><span class="sxs-lookup"><span data-stu-id="d17d4-115">You can use lambda expressions in any code that requires instances of delegate types or expression trees, for example as an argument to the <xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType> method to pass the code that should be executed in the background.</span></span> <span data-ttu-id="d17d4-116">Można również użyć wyrażeń lambda podczas pisania [LINQ w języku C#](../../linq/index.md), jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d17d4-116">You can also use lambda expressions when you write [LINQ in C#](../../linq/index.md), as the following example shows:</span></span>

[!code-csharp-interactive[lambda is argument in LINQ](~/samples/snippets/csharp/programming-guide/lambda-expressions/Introduction.cs#Argument)]

<span data-ttu-id="d17d4-117">W przypadku używania składni opartej <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> na <xref:System.Linq.Enumerable?displayProperty=nameWithType> metodzie do wywoływania metody w klasie, na przykład w LINQ do obiektów i LINQ do XML, parametr jest typem <xref:System.Func%602?displayProperty=nameWithType>delegata .</span><span class="sxs-lookup"><span data-stu-id="d17d4-117">When you use method-based syntax to call the <xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Enumerable?displayProperty=nameWithType> class, for example in LINQ to Objects and LINQ to XML, the parameter is a delegate type <xref:System.Func%602?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d17d4-118">Po wywołaniu <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> metody <xref:System.Linq.Queryable?displayProperty=nameWithType> w klasie, na przykład w LINQ do SQL, [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>)typ parametru jest typem drzewa wyrażeń .</span><span class="sxs-lookup"><span data-stu-id="d17d4-118">When you call the <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType> method in the <xref:System.Linq.Queryable?displayProperty=nameWithType> class, for example in LINQ to SQL, the parameter type is an expression tree type [`Expression<Func<TSource,TResult>>`](<xref:System.Linq.Expressions.Expression%601>).</span></span> <span data-ttu-id="d17d4-119">W obu przypadkach można użyć tego samego wyrażenia lambda, aby określić wartość parametru.</span><span class="sxs-lookup"><span data-stu-id="d17d4-119">In both cases you can use the same lambda expression to specify the parameter value.</span></span> <span data-ttu-id="d17d4-120">To sprawia, `Select` że dwa wywołania wyglądają podobnie, chociaż w rzeczywistości typ obiektów utworzonych z lambdas jest inny.</span><span class="sxs-lookup"><span data-stu-id="d17d4-120">That makes the two `Select` calls to look similar although in fact the type of objects created from the lambdas is different.</span></span>
  
## <a name="expression-lambdas"></a><span data-ttu-id="d17d4-121">Wyrażenie lambdas</span><span class="sxs-lookup"><span data-stu-id="d17d4-121">Expression lambdas</span></span>

<span data-ttu-id="d17d4-122">Wyrażenie lambda z wyrażeniem po prawej `=>` stronie operatora jest nazywane *wyrażeniem lambda*.</span><span class="sxs-lookup"><span data-stu-id="d17d4-122">A lambda expression with an expression on the right side of the `=>` operator is called an *expression lambda*.</span></span> <span data-ttu-id="d17d4-123">Wyrażenie lambdas są szeroko stosowane w budowie [drzew ekspresji](../concepts/expression-trees/index.md).</span><span class="sxs-lookup"><span data-stu-id="d17d4-123">Expression lambdas are used extensively in the construction of [expression trees](../concepts/expression-trees/index.md).</span></span> <span data-ttu-id="d17d4-124">Lambda wyrażenia zwraca wynik wyrażenia i ma następującą podstawową formę:</span><span class="sxs-lookup"><span data-stu-id="d17d4-124">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input-parameters) => expression
```

<span data-ttu-id="d17d4-125">Nawiasy są opcjonalne tylko wtedy, gdy lambda ma jeden parametr wejściowy; w przeciwnym razie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="d17d4-125">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span>

<span data-ttu-id="d17d4-126">Określanie braku parametrów wejściowych za pomocą pustych nawiasów:</span><span class="sxs-lookup"><span data-stu-id="d17d4-126">Specify zero input parameters with empty parentheses:</span></span>  

[!code-csharp[zero parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ZeroParameters)]

<span data-ttu-id="d17d4-127">Jeśli liczba parametrów wejściowych wynosi dwa lub więcej, te parametry są rozdzielane przecinkami i umieszczone w nawiasach:</span><span class="sxs-lookup"><span data-stu-id="d17d4-127">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[two parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#TwoParameters)]

<span data-ttu-id="d17d4-128">Czasami jest to niemożliwe dla kompilatora wywnioskować typy danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="d17d4-128">Sometimes it's impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="d17d4-129">Można określić typy jawnie, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d17d4-129">You can specify the types explicitly as shown in the following example:</span></span>

[!code-csharp[explicitly typed parameters](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#ExplicitlyTypedParameters)]

<span data-ttu-id="d17d4-130">Typy parametrów wejściowych muszą być jawne lub wszystkie niejawne; w przeciwnym razie wystąpi błąd kompilatora [CS0748.](../../misc/cs0748.md)</span><span class="sxs-lookup"><span data-stu-id="d17d4-130">Input parameter types must be all explicit or all implicit; otherwise, a [CS0748](../../misc/cs0748.md) compiler error occurs.</span></span>

<span data-ttu-id="d17d4-131">Treść wyrażenia lambda może składać się z wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="d17d4-131">The body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="d17d4-132">Jednak jeśli tworzysz drzewa wyrażeń, które są oceniane poza kontekstem środowiska wykonawczego języka wspólnego .NET, na przykład w programie SQL Server, nie należy używać wywołań metod w wyrażeniach lambda.</span><span class="sxs-lookup"><span data-stu-id="d17d4-132">However, if you are creating expression trees that are evaluated outside the context of the .NET common language runtime, such as in SQL Server, you should not use method calls in lambda expressions.</span></span> <span data-ttu-id="d17d4-133">Te metody nie będą zrozumiałe poza kontekstem środowiska uruchomieniowego języka wspólnego platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="d17d4-133">The methods will have no meaning outside the context of the .NET common language runtime.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="d17d4-134">Oświadczenie lambdas</span><span class="sxs-lookup"><span data-stu-id="d17d4-134">Statement lambdas</span></span>

<span data-ttu-id="d17d4-135">Lambda instrukcji jest podobna do lambdy wyrażenia, z tym że instrukcje są ujęte w nawiasy klamrowe:</span><span class="sxs-lookup"><span data-stu-id="d17d4-135">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp  
(input-parameters) => { <sequence-of-statements> }
```

<span data-ttu-id="d17d4-136">Treść lambdy instrukcji może składać się z dowolnej liczby instrukcji, jednak w praktyce jest ich zwykle nie więcej niż dwie lub trzy.</span><span class="sxs-lookup"><span data-stu-id="d17d4-136">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp-interactive[statement lambda](~/samples/snippets/csharp/programming-guide/lambda-expressions/ExpressionAndStatementLambdas.cs#StatementLambda)]

<span data-ttu-id="d17d4-137">Instrukcja lambdas nie może służyć do tworzenia drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="d17d4-137">Statement lambdas cannot be used to create expression trees.</span></span>
  
## <a name="async-lambdas"></a><span data-ttu-id="d17d4-138">Jagnięcina asynchronizów</span><span class="sxs-lookup"><span data-stu-id="d17d4-138">Async lambdas</span></span>

<span data-ttu-id="d17d4-139">Można łatwo utworzyć wyrażenia lambda i instrukcje, które zawierają przetwarzanie asynchroniczne przy użyciu [asynchronicznych](../../language-reference/keywords/async.md) i [await](../../language-reference/operators/await.md) słowa kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d17d4-139">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](../../language-reference/keywords/async.md) and [await](../../language-reference/operators/await.md) keywords.</span></span> <span data-ttu-id="d17d4-140">Na przykład poniższy przykład formularzy systemu Windows zawiera program obsługi zdarzeń, który wywołuje metodę asynchronizową i oczekuje na metodę asynchronizowania. `ExampleMethodAsync`</span><span class="sxs-lookup"><span data-stu-id="d17d4-140">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="d17d4-141">Można dodać ten sam program obsługi zdarzeń, używając lambdy asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="d17d4-141">You can add the same event handler by using an async lambda.</span></span> <span data-ttu-id="d17d4-142">Aby dodać ten program `async` obsługi, dodaj modyfikator przed listą parametrów lambda, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="d17d4-142">To add this handler, add an `async` modifier before the lambda parameter list, as the following example shows:</span></span>

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

<span data-ttu-id="d17d4-143">Aby uzyskać więcej informacji na temat tworzenia i używania metod [asynchronicznych, zobacz Programowanie asynchroniczne za pomocą asynchronii i czekaj](../concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="d17d4-143">For more information about how to create and use async methods, see [Asynchronous Programming with async and await](../concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="d17d4-144">Wyrażenia lambda i krotek</span><span class="sxs-lookup"><span data-stu-id="d17d4-144">Lambda expressions and tuples</span></span>

<span data-ttu-id="d17d4-145">Począwszy od języka C# 7.0, język C# zapewnia wbudowaną obsługę [krotek.](../../tuples.md)</span><span class="sxs-lookup"><span data-stu-id="d17d4-145">Starting with C# 7.0, the C# language provides built-in support for [tuples](../../tuples.md).</span></span> <span data-ttu-id="d17d4-146">Można podać krotek jako argument do wyrażenia lambda i wyrażenie lambda może również zwrócić krotki.</span><span class="sxs-lookup"><span data-stu-id="d17d4-146">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="d17d4-147">W niektórych przypadkach kompilator języka C# używa wnioskowania o typie do określenia typów składników krotki.</span><span class="sxs-lookup"><span data-stu-id="d17d4-147">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span>

<span data-ttu-id="d17d4-148">Krotka definiuje się, otaczając listę rozdzielanych przecinkami jej komponentów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="d17d4-148">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="d17d4-149">W poniższym przykładzie użyto krotki z trzema składnikami, aby przekazać sekwencję liczb do wyrażenia lambda, które podwaja każdą wartość i zwraca krotki z trzema składnikami, która zawiera wynik mnożenia.</span><span class="sxs-lookup"><span data-stu-id="d17d4-149">The following example uses tuple with three components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with three components that contains the result of the multiplications.</span></span>

[!code-csharp-interactive[lambda and tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithoutComponentName)]

<span data-ttu-id="d17d4-150">Zazwyczaj pola krotki są nazwane `Item1`, `Item2`itp. Można jednak zdefiniować krotek z nazwanych składników, jak w poniższym przykładzie nie.</span><span class="sxs-lookup"><span data-stu-id="d17d4-150">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp-interactive[lambda and named tuples](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasAndTuples.cs#WithComponentName)]

<span data-ttu-id="d17d4-151">Aby uzyskać więcej informacji na temat krotek języka C#, zobacz [typy krotek języka C#.](../../tuples.md)</span><span class="sxs-lookup"><span data-stu-id="d17d4-151">For more information about C# tuples, see [C# tuple types](../../tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="d17d4-152">Lambdas ze standardowymi operatorami zapytań</span><span class="sxs-lookup"><span data-stu-id="d17d4-152">Lambdas with the standard query operators</span></span>

<span data-ttu-id="d17d4-153">LINQ do obiektów, wśród innych implementacji, mają parametr <xref:System.Func%601> wejściowy, którego typ jest jednym z rodziny delegatów rodzajowych.</span><span class="sxs-lookup"><span data-stu-id="d17d4-153">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="d17d4-154">Te delegatów używać parametrów typu do definiowania liczby i typu parametrów wejściowych i typu zwracanego delegata.</span><span class="sxs-lookup"><span data-stu-id="d17d4-154">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="d17d4-155">`Func`delegatów są bardzo przydatne do hermetyzacji wyrażeń zdefiniowanych przez użytkownika, które są stosowane do każdego elementu w zestawie danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="d17d4-155">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="d17d4-156">Rozważmy na <xref:System.Func%602> przykład typ delegata:</span><span class="sxs-lookup"><span data-stu-id="d17d4-156">For example, consider the <xref:System.Func%602> delegate type:</span></span>  

```csharp
public delegate TResult Func<in T, out TResult>(T arg)
```

<span data-ttu-id="d17d4-157">Pełnomocnik może być wystąpienia jako `Func<int, bool>` wystąpienie, gdzie `int` `bool` jest parametrem wejściowym i jest wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="d17d4-157">The delegate can be instantiated as a `Func<int, bool>` instance where `int` is an input parameter and `bool` is the return value.</span></span> <span data-ttu-id="d17d4-158">Wartość zwracana jest zawsze określona w ostatnim parametrze typu.</span><span class="sxs-lookup"><span data-stu-id="d17d4-158">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="d17d4-159">Na przykład `Func<int, string, bool>` definiuje delegata z dwoma `int` `string`parametrami wejściowymi `bool`oraz i typem zwracanym .</span><span class="sxs-lookup"><span data-stu-id="d17d4-159">For example, `Func<int, string, bool>` defines a delegate with two input parameters, `int` and `string`, and a return type of `bool`.</span></span> <span data-ttu-id="d17d4-160">Następujący `Func` delegat, gdy jest wywoływany, zwraca wartość logiczną, która wskazuje, czy parametr wejściowy jest równy pięciu:</span><span class="sxs-lookup"><span data-stu-id="d17d4-160">The following `Func` delegate, when it's invoked, returns Boolean value that indicates whether the input parameter is equal to five:</span></span>

[!code-csharp-interactive[Func example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Func)]

<span data-ttu-id="d17d4-161">Można również podać wyrażenie lambda, gdy <xref:System.Linq.Expressions.Expression%601>typ argumentu jest , na przykład <xref:System.Linq.Queryable> w standardowych operatorów kwerend, które są zdefiniowane w typie.</span><span class="sxs-lookup"><span data-stu-id="d17d4-161">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="d17d4-162">Po określeniu <xref:System.Linq.Expressions.Expression%601> argumentu lambda jest kompilowany do drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="d17d4-162">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span>
  
<span data-ttu-id="d17d4-163">W poniższym przykładzie użyto standardowego <xref:System.Linq.Enumerable.Count%2A> operatora kwerendy:</span><span class="sxs-lookup"><span data-stu-id="d17d4-163">The following example uses the <xref:System.Linq.Enumerable.Count%2A> standard query operator:</span></span>

[!code-csharp-interactive[Count example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#Count)]

<span data-ttu-id="d17d4-164">Kompilator może wywnioskować typ parametru wejściowego, ale można go również określić w sposób jawny.</span><span class="sxs-lookup"><span data-stu-id="d17d4-164">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="d17d4-165">To szczególne wyrażenie lambda zlicza`n`te liczby całkowite ( ), które po podzieleniu przez dwa mają pozostałą część 1.</span><span class="sxs-lookup"><span data-stu-id="d17d4-165">This particular lambda expression counts those integers (`n`) which when divided by two have a remainder of 1.</span></span>

<span data-ttu-id="d17d4-166">Poniższy przykład tworzy sekwencję, która `numbers` zawiera wszystkie elementy w tablicy, które poprzedzają 9, ponieważ jest to pierwsza liczba w sekwencji, która nie spełnia warunku:</span><span class="sxs-lookup"><span data-stu-id="d17d4-166">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition:</span></span>

[!code-csharp-interactive[TakeWhile example](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhile)]

<span data-ttu-id="d17d4-167">Poniższy przykład określa wiele parametrów wejściowych, otaczając je w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="d17d4-167">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="d17d4-168">Metoda zwraca wszystkie elementy `numbers` w tablicy, dopóki nie napotka liczby, której wartość jest mniejsza niż jego położenie porządkowe w tablicy:</span><span class="sxs-lookup"><span data-stu-id="d17d4-168">The method returns all the elements in the `numbers` array until it encounters a number whose value is less than its ordinal position in the array:</span></span>

[!code-csharp-interactive[TakeWhile example 2](~/samples/snippets/csharp/programming-guide/lambda-expressions/LambdasWithQueryMethods.cs#TakeWhileWithIndex)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="d17d4-169">Wnioskowanie o typie w wyrażeniach lambda</span><span class="sxs-lookup"><span data-stu-id="d17d4-169">Type inference in lambda expressions</span></span>

<span data-ttu-id="d17d4-170">Podczas pisania lambdas, często nie trzeba określić typ parametrów wejściowych, ponieważ kompilator można wywnioskować typ na podstawie treści lambda, typy parametrów i inne czynniki, jak opisano w specyfikacji języka C#.</span><span class="sxs-lookup"><span data-stu-id="d17d4-170">When writing lambdas, you often don't have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors as described in the C# language specification.</span></span> <span data-ttu-id="d17d4-171">Dla większości standardowych operatorów zapytań pierwszy element danych wejściowych jest typem elementów w sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="d17d4-171">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="d17d4-172">Jeśli kwerendy , `IEnumerable<Customer>`a następnie zmienna wejściowa jest `Customer` wnioskowany jako obiekt, co oznacza, że masz dostęp do jego metod i właściwości:</span><span class="sxs-lookup"><span data-stu-id="d17d4-172">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>  

```csharp
customers.Where(c => c.City == "London");
```

<span data-ttu-id="d17d4-173">Ogólne zasady wnioskowania o typie lambdów są następujące:</span><span class="sxs-lookup"><span data-stu-id="d17d4-173">The general rules for type inference for lambdas are as follows:</span></span>

- <span data-ttu-id="d17d4-174">Wyrażenie lambda musi zawierać taką samą liczbę parametrów jak typ delegata.</span><span class="sxs-lookup"><span data-stu-id="d17d4-174">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="d17d4-175">Każdy parametr wejściowy w wyrażeniu lambda musi umożliwiać niejawną konwersję na odpowiadający mu parametr delegata.</span><span class="sxs-lookup"><span data-stu-id="d17d4-175">Each input parameter in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="d17d4-176">Wartość zwracana wyrażenia lambda (jeżeli istnieje) musi umożliwiać niejawną konwersję na zwracany typ delegata.</span><span class="sxs-lookup"><span data-stu-id="d17d4-176">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>
  
<span data-ttu-id="d17d4-177">Należy zauważyć, że wyrażenia lambda same w sobie nie mają typu, ponieważ system typów typowych nie ma wewnętrznego pojęcia "wyrażenia lambda".</span><span class="sxs-lookup"><span data-stu-id="d17d4-177">Note that lambda expressions in themselves don't have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="d17d4-178">Jednak czasami wygodnie jest mówić nieformalnie o "typie" wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="d17d4-178">However, it's sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="d17d4-179">W takich przypadkach typ odnosi się <xref:System.Linq.Expressions.Expression> do typu delegata lub typu, na który konwertowane jest wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="d17d4-179">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="capture-of-outer-variables-and-variable-scope-in-lambda-expressions"></a><span data-ttu-id="d17d4-180">Przechwytywanie zmiennych zewnętrznych i zmiennego zakresu w wyrażeniach lambda</span><span class="sxs-lookup"><span data-stu-id="d17d4-180">Capture of outer variables and variable scope in lambda expressions</span></span>

<span data-ttu-id="d17d4-181">Lambdas może odnosić się do *zmiennych zewnętrznych*.</span><span class="sxs-lookup"><span data-stu-id="d17d4-181">Lambdas can refer to *outer variables*.</span></span> <span data-ttu-id="d17d4-182">Są to zmienne, które znajdują się w zakresie w metodzie, która definiuje wyrażenie lambda lub w zakresie w typie, który zawiera wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="d17d4-182">These are the variables that are in scope in the method that defines the lambda expression, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="d17d4-183">Przechwytywane w ten sposób zmienne są przechowywane do użytku w wyrażeniu lambda, nawet gdyby w innym wypadku te zmienne znalazłyby się poza zakresem i zostałyby usunięte w ramach odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="d17d4-183">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="d17d4-184">Zewnętrzna zmienna musi być zdecydowanie przypisana, aby można jej było użyć w wyrażeniu lambda.</span><span class="sxs-lookup"><span data-stu-id="d17d4-184">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="d17d4-185">W poniższym przykładzie pokazano te reguły:</span><span class="sxs-lookup"><span data-stu-id="d17d4-185">The following example demonstrates these rules:</span></span>

[!code-csharp[variable scope](~/samples/snippets/csharp/programming-guide/lambda-expressions/VariableScopeWithLambdas.cs#VariableScope)]

<span data-ttu-id="d17d4-186">Do zakresu zmiennych w wyrażeniach lambda są stosowane następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="d17d4-186">The following rules apply to variable scope in lambda expressions:</span></span>  

- <span data-ttu-id="d17d4-187">Zmienna, która jest przechwytywana, nie będzie usuwana w ramach odśmiecania pamięci, dopóki odwołujący się do niej delegat nie będzie podlegał odśmiecaniu pamięci.</span><span class="sxs-lookup"><span data-stu-id="d17d4-187">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="d17d4-188">Zmienne wprowadzone w wyrażeniu lambda nie są widoczne w otaczającej metody.</span><span class="sxs-lookup"><span data-stu-id="d17d4-188">Variables introduced within a lambda expression are not visible in the enclosing method.</span></span>

- <span data-ttu-id="d17d4-189">Wyrażenie lambda nie może bezpośrednio przechwycić [parametru in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md)lub [out](../../language-reference/keywords/out-parameter-modifier.md) z metody otaczającej.</span><span class="sxs-lookup"><span data-stu-id="d17d4-189">A lambda expression cannot directly capture an [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), or [out](../../language-reference/keywords/out-parameter-modifier.md) parameter from the enclosing method.</span></span>

- <span data-ttu-id="d17d4-190">Instrukcja [return](../../language-reference/keywords/return.md) w wyrażeniu lambda nie powoduje, że otaczająca metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="d17d4-190">A [return](../../language-reference/keywords/return.md) statement in a lambda expression doesn't cause the enclosing method to return.</span></span>

- <span data-ttu-id="d17d4-191">Wyrażenie lambda nie może zawierać [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md)lub [continue](../../language-reference/keywords/continue.md) instrukcji, jeśli obiekt docelowy tej instrukcji skoku znajduje się poza blokiem wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="d17d4-191">A lambda expression cannot contain a [goto](../../language-reference/keywords/goto.md), [break](../../language-reference/keywords/break.md), or [continue](../../language-reference/keywords/continue.md) statement if the target of that jump statement is outside the lambda expression block.</span></span> <span data-ttu-id="d17d4-192">Jest to również błąd, aby instrukcja skoku poza blok wyrażenia lambda, jeśli obiekt docelowy znajduje się wewnątrz bloku.</span><span class="sxs-lookup"><span data-stu-id="d17d4-192">It's also an error to have a jump statement outside the lambda expression block if the target is inside the block.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d17d4-193">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d17d4-193">C# language specification</span></span>

<span data-ttu-id="d17d4-194">Aby uzyskać więcej informacji, zobacz sekcję [Wyrażenia funkcji anonimowe](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [w specyfikacji języka języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="d17d4-194">For more information, see the [Anonymous function expressions](~/_csharplang/spec/expressions.md#anonymous-function-expressions) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="featured-book-chapter"></a><span data-ttu-id="d17d4-195">Polecany rozdział książki</span><span class="sxs-lookup"><span data-stu-id="d17d4-195">Featured book chapter</span></span>

<span data-ttu-id="d17d4-196">[Delegaci, wydarzenia i wyrażenia Lambda](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) w [książce kucharskiej C# 3.0, wydanie trzecie: ponad 250 rozwiązań dla programistów języka C# 3.0](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span><span class="sxs-lookup"><span data-stu-id="d17d4-196">[Delegates, Events, and Lambda Expressions](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518994%28v=orm.10%29) in [C# 3.0 Cookbook, Third Edition: More than 250 solutions for C# 3.0 programmers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff518995%28v=orm.10%29)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d17d4-197">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d17d4-197">See also</span></span>

- [<span data-ttu-id="d17d4-198">C# Przewodnik programowania</span><span class="sxs-lookup"><span data-stu-id="d17d4-198">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d17d4-199">LINQ (zapytanie zintegrowane z językiem)</span><span class="sxs-lookup"><span data-stu-id="d17d4-199">LINQ (Language-Integrated Query)</span></span>](../concepts/linq/index.md)
- [<span data-ttu-id="d17d4-200">Drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="d17d4-200">Expression Trees</span></span>](../concepts/expression-trees/index.md)
- [<span data-ttu-id="d17d4-201">Funkcje lokalne a wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="d17d4-201">Local functions vs. lambda expressions</span></span>](../classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions)
- [<span data-ttu-id="d17d4-202">Niejawnie wpisane wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="d17d4-202">Implicitly typed lambda expressions</span></span>](../../implicitly-typed-lambda-expressions.md)
- [<span data-ttu-id="d17d4-203">Przykłady programu Visual Studio 2008 C# (zobacz przykładowe pliki zapytań LINQ i program XQuery)</span><span class="sxs-lookup"><span data-stu-id="d17d4-203">Visual Studio 2008 C# Samples (see LINQ Sample Queries files and XQuery program)</span></span>](https://code.msdn.microsoft.com/Visual-Studio-2008-C-d295cdba)
- [<span data-ttu-id="d17d4-204">Rekursywne wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="d17d4-204">Recursive lambda expressions</span></span>](https://docs.microsoft.com/archive/blogs/madst/recursive-lambda-expressions)
