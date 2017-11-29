---
title: "Wyrażenia lambda"
description: "Odchudzona można użyć wyrażenia lambda, które są bloki kodu wykonywalnego, które mogą być przekazywane jako argumenty."
keywords: ".NET, .NET core, wyrażenia lambda, wyrażenia lambda, obiektów delegowanych"
ms-author: ronpet
author: rpetrusha
ms.date: 11/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b6a0539a-8ce5-4da7-adcf-44be345a2714
ms.openlocfilehash: 1a97d830c675c8e3980eddae78f3face279ec6dc
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2017
---
# <a name="lambda-expressions"></a><span data-ttu-id="788f9-104">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="788f9-104">Lambda expressions</span></span> #

<span data-ttu-id="788f9-105">A *wyrażenia lambda* to blok kodu (wyrażenia lub blok instrukcji), który jest traktowany jako obiekt.</span><span class="sxs-lookup"><span data-stu-id="788f9-105">A *lambda expression* is a block of code (an expression or a statement block) that is treated as an object.</span></span> <span data-ttu-id="788f9-106">Mogą być przekazywane jako argument do metody, a także może być zwracany przez metodę wywołania.</span><span class="sxs-lookup"><span data-stu-id="788f9-106">It can be passed as an argument to methods, and it can also be returned by method calls.</span></span> <span data-ttu-id="788f9-107">Wyrażenia lambda są często używane dla:</span><span class="sxs-lookup"><span data-stu-id="788f9-107">Lambda expressions are used extensively for:</span></span>

- <span data-ttu-id="788f9-108">Przekazywanie kod, który ma zostać wykonana do metod asynchronicznych, takich jak <xref:System.Threading.Tasks.Task.Run(System.Action)>.</span><span class="sxs-lookup"><span data-stu-id="788f9-108">Passing the code that is to be executed to asynchronous methods, such as <xref:System.Threading.Tasks.Task.Run(System.Action)>.</span></span>

- <span data-ttu-id="788f9-109">Zapisywanie [wyrażenia zapytań LINQ](linq/index.md).</span><span class="sxs-lookup"><span data-stu-id="788f9-109">Writing [LINQ query expressions](linq/index.md).</span></span>

- <span data-ttu-id="788f9-110">Tworzenie [drzew wyrażeń](expression-trees-building.md).</span><span class="sxs-lookup"><span data-stu-id="788f9-110">Creating [expression trees](expression-trees-building.md).</span></span>

<span data-ttu-id="788f9-111">Wyrażenia lambda są kodu, który może być reprezentowany jako pełnomocnik lub jako drzewo wyrażenia, który kompiluje się do delegata.</span><span class="sxs-lookup"><span data-stu-id="788f9-111">Lambda expressions are code that can be represented either as a delegate, or as an expression tree that compiles to a delegate.</span></span> <span data-ttu-id="788f9-112">Typ delegata określonego wyrażenia lambda zależy od jego parametrów i zwracać wartość.</span><span class="sxs-lookup"><span data-stu-id="788f9-112">The specific delegate type of a lambda expression depends on its parameters and return value.</span></span> <span data-ttu-id="788f9-113">Wyrażenia lambda, które nie zwracają wartości odpowiadają określonym `Action` delegować, w zależności od jego liczby parametrów.</span><span class="sxs-lookup"><span data-stu-id="788f9-113">Lambda expressions that don't return a value correspond to a specific `Action` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="788f9-114">Wyrażenia lambda, które zwracają wartość odpowiada określonym `Func` delegować, w zależności od jego liczby parametrów.</span><span class="sxs-lookup"><span data-stu-id="788f9-114">Lambda expressions that return a value correspond to a specific `Func` delegate, depending on its number of parameters.</span></span> <span data-ttu-id="788f9-115">Na przykład, wyrażenie lambda, która ma dwa parametry, ale nie zwraca wartości odpowiada <xref:System.Action%602> delegowanie.</span><span class="sxs-lookup"><span data-stu-id="788f9-115">For example, a lambda expression that has two parameters but returns no value corresponds to an <xref:System.Action%602> delegate.</span></span> <span data-ttu-id="788f9-116">Wyrażenie lambda, który ma jeden parametr i zwraca wartość odpowiada <xref:System.Func%602> delegowanie.</span><span class="sxs-lookup"><span data-stu-id="788f9-116">A lambda expression that has one parameter and returns a value corresponds to <xref:System.Func%602> delegate.</span></span>

<span data-ttu-id="788f9-117">Wyrażenie lambda `=>`, [operator deklaracji lambda](language-reference/operators/lambda-operator.md), aby oddzielić listy parametrów lambda z jego kodu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="788f9-117">A lambda expression uses `=>`, the [lambda declaration operator](language-reference/operators/lambda-operator.md), to separate the lambda's parameter list from its executable code.</span></span> <span data-ttu-id="788f9-118">Aby utworzyć wyrażenie lambda, należy określić parametry wejściowe (jeśli istnieją) po lewej stronie operatora lambda i umieść blok wyrażenia lub instrukcji z drugiej strony.</span><span class="sxs-lookup"><span data-stu-id="788f9-118">To create a lambda expression, you specify input parameters (if any) on the left side of the lambda operator, and you put the expression or statement block on the other side.</span></span> <span data-ttu-id="788f9-119">Na przykład, wyrażenie lambda jednowierszowego `x => x * x` określa parametr o nazwie `x` i zwraca wartość `x` kwadratów.</span><span class="sxs-lookup"><span data-stu-id="788f9-119">For example, the single-line lambda expression `x => x * x` specifies a parameter that’s named `x` and returns the value of `x` squared.</span></span> <span data-ttu-id="788f9-120">To wyrażenie można przypisać do typu delegata, tak jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="788f9-120">You can assign this expression to a delegate type, as the following example shows:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda1.cs#1)]

<span data-ttu-id="788f9-121">Lub przekaż go bezpośrednio jako argument metody:</span><span class="sxs-lookup"><span data-stu-id="788f9-121">Or you can pass it directly as a method argument:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/lambda2.cs#2)]

## <a name="expression-lambdas"></a><span data-ttu-id="788f9-122">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="788f9-122">Expression lambdas</span></span> ##

 <span data-ttu-id="788f9-123">Wyrażenia lambda za pomocą wyrażenia po prawej stronie = > — operator jest wywoływana *wyrażenia lambda*.</span><span class="sxs-lookup"><span data-stu-id="788f9-123">A lambda expression with an expression on the right side of the => operator is called an *expression lambda*.</span></span> <span data-ttu-id="788f9-124">Wyrażenia lambda są często używane w konstrukcji [drzew wyrażeń](expression-trees.md).</span><span class="sxs-lookup"><span data-stu-id="788f9-124">Expression lambdas are used extensively in the construction of [expression trees](expression-trees.md).</span></span> <span data-ttu-id="788f9-125">Lambda wyrażenia zwraca wynik wyrażenia i ma następującą podstawową formę:</span><span class="sxs-lookup"><span data-stu-id="788f9-125">An expression lambda returns the result of the expression and takes the following basic form:</span></span>

```csharp
(input parameters) => expression
```

<span data-ttu-id="788f9-126">Nawiasy są opcjonalne tylko wtedy, gdy lambda ma jeden parametr wejściowy; w przeciwnym razie są wymagane.</span><span class="sxs-lookup"><span data-stu-id="788f9-126">The parentheses are optional only if the lambda has one input parameter; otherwise they are required.</span></span> <span data-ttu-id="788f9-127">Określanie braku parametrów wejściowych za pomocą pustych nawiasów:</span><span class="sxs-lookup"><span data-stu-id="788f9-127">Specify zero input parameters with empty parentheses:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#1)]

<span data-ttu-id="788f9-128">Jeśli liczba parametrów wejściowych wynosi dwa lub więcej, te parametry są rozdzielane przecinkami i umieszczone w nawiasach:</span><span class="sxs-lookup"><span data-stu-id="788f9-128">Two or more input parameters are separated by commas enclosed in parentheses:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#2)]

<span data-ttu-id="788f9-129">Zwykle kompilator używa wnioskowanie o typie przy określaniu typów parametrów.</span><span class="sxs-lookup"><span data-stu-id="788f9-129">Ordinarily, the compiler uses type inference in determining parameter types.</span></span> <span data-ttu-id="788f9-130">Jednak czasami jest trudne lub niemożliwe dla kompilatora w celu uwzględnienia typów wejściowych.</span><span class="sxs-lookup"><span data-stu-id="788f9-130">However, sometimes it is difficult or impossible for the compiler to infer the input types.</span></span> <span data-ttu-id="788f9-131">W takiej sytuacji możesz określić typy jawnie, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="788f9-131">When this occurs, you can specify the types explicitly, as in the following example:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/expression3.cs#3)]

<span data-ttu-id="788f9-132">Należy zauważyć, że w poprzednim przykładzie treść wyrażenia lambda może składać się z wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="788f9-132">Note in the previous example that the body of an expression lambda can consist of a method call.</span></span> <span data-ttu-id="788f9-133">Jednak w przypadku tworzenia drzewa wyrażeń, które są oceniane poza programu .NET Framework, takich jak w programie SQL Server lub Entity Framework (EF), użytkownik powinien zaniechania przy użyciu wywołania metody w wyrażeniach lambda, ponieważ te metody mogą mieć znaczenia poza kontekstem implementacji .NET.</span><span class="sxs-lookup"><span data-stu-id="788f9-133">However, if you are creating expression trees that are evaluated outside of the .NET Framework, such as in SQL Server or Entity Framework (EF), you should refrain from using method calls in lambda expressions, since the methods may have no meaning outside the context of the .NET implementation.</span></span> <span data-ttu-id="788f9-134">Jeśli chcesz użyć w tym przypadku wywołania metody, należy sprawdzić je, aby dokładnie upewnij się, że pomyślnie rozpoznane wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="788f9-134">If you do choose to use method calls in this case, be sure to test them thoroughly to ensure that the method calls can be successfuly resolved.</span></span>

## <a name="statement-lambdas"></a><span data-ttu-id="788f9-135">Instrukcji lambda</span><span class="sxs-lookup"><span data-stu-id="788f9-135">Statement lambdas</span></span> ##

<span data-ttu-id="788f9-136">Lambda instrukcji jest podobna do lambdy wyrażenia, z tym że instrukcje są ujęte w nawiasy klamrowe:</span><span class="sxs-lookup"><span data-stu-id="788f9-136">A statement lambda resembles an expression lambda except that the statement(s) is enclosed in braces:</span></span>

```csharp
(input parameters) => { statement; }
```

<span data-ttu-id="788f9-137">Treść lambdy instrukcji może składać się z dowolnej liczby instrukcji, jednak w praktyce jest ich zwykle nie więcej niż dwie lub trzy.</span><span class="sxs-lookup"><span data-stu-id="788f9-137">The body of a statement lambda can consist of any number of statements; however, in practice there are typically no more than two or three.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/statement1.cs#1)]

<span data-ttu-id="788f9-138">Lambd instrukcji, podobnie jak metod anonimowych, nie można używać do tworzenia drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="788f9-138">Statement lambdas, like anonymous methods, cannot be used to create expression trees.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="788f9-139">Asynchronicznych wyrażeń lambda</span><span class="sxs-lookup"><span data-stu-id="788f9-139">Async lambdas</span></span> ##

<span data-ttu-id="788f9-140">Można jednak łatwo tworzyć wyrażenia lambda i instrukcje zawierające przetwarzania asynchronicznego przy użyciu [async](language-reference/keywords/async.md) i [await](language-reference/keywords/await.md) słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="788f9-140">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [async](language-reference/keywords/async.md) and [await](language-reference/keywords/await.md) keywords.</span></span> <span data-ttu-id="788f9-141">Na przykład przykład wywołuje `ShowSquares` metodę, która działa w sposób asynchroniczny.</span><span class="sxs-lookup"><span data-stu-id="788f9-141">For example, the example calls a `ShowSquares` method that executes asynchronously.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/async1.cs#1)]

<span data-ttu-id="788f9-142">Aby uzyskać więcej informacji o sposobie tworzenia i używania metody asynchroniczne, zobacz [programowanie asynchroniczne z async i await](programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="788f9-142">For more information about how to create and use async methods, see [Asynchronous programming with async and await](programming-guide/concepts/async/index.md).</span></span>

## <a name="lambda-expressions-and-tuples"></a><span data-ttu-id="788f9-143">Wyrażenia lambda i spójnych kolekcji</span><span class="sxs-lookup"><span data-stu-id="788f9-143">Lambda expressions and tuples</span></span> ##

<span data-ttu-id="788f9-144">Począwszy od wersji 7.0 C# w języku C# udostępnia wbudowaną obsługę spójnych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="788f9-144">Starting with C# 7.0, the C# language provides built-in support for tuples.</span></span> <span data-ttu-id="788f9-145">Krotka można podać jako argument wyrażenia lambda, a w wyrażeniu lambda może również zwrócić spójnych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="788f9-145">You can provide a tuple as an argument to a lambda expression, and your lambda expression can also return a tuple.</span></span> <span data-ttu-id="788f9-146">W niektórych przypadkach kompilatora C# używa wnioskowanie o typie, aby określić typy składników spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="788f9-146">In some cases, the C# compiler uses type inference to determine the types of tuple components.</span></span> 

<span data-ttu-id="788f9-147">Należy zdefiniować krotka umieszczając rozdzielana przecinkami lista składników w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="788f9-147">You define a tuple by enclosing a comma-delimited list of its components in parentheses.</span></span> <span data-ttu-id="788f9-148">W poniższym przykładzie użyto krotki ze składnikami 5 do przekazania wyrażenia lambda, który podwaja każdej wartości i zwraca spójną kolekcję z 5 składniki zawierający wynik mnożenia sekwencji liczb.</span><span class="sxs-lookup"><span data-stu-id="788f9-148">The following example uses tuple with 5 components to pass a sequence of numbers to a lambda expression, which doubles each value and returns a tuple with 5 components that contains the result of the multiplications.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples1.cs#1)]

<span data-ttu-id="788f9-149">Zwykle są nazywane pola krotka `Item1`, `Item2`itp. Można jednak zdefiniować krotka ze składnikami nazwanego, tak jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="788f9-149">Ordinarily, the fields of a tuple are named `Item1`, `Item2`, etc. You can, however, define a tuple with named components, as the following example does.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/tuples2.cs#1)]

<span data-ttu-id="788f9-150">Aby uzyskać więcej informacji na obsługę krotek w języku C#, zobacz [typów C# krotki](tuples.md).</span><span class="sxs-lookup"><span data-stu-id="788f9-150">For more information on support for tuples in C#, see [C# Tuple types](tuples.md).</span></span>

## <a name="lambdas-with-the-standard-query-operators"></a><span data-ttu-id="788f9-151">Wyrażenia lambda z standardowych operatorów zapytań</span><span class="sxs-lookup"><span data-stu-id="788f9-151">Lambdas with the standard query operators</span></span> ##

<span data-ttu-id="788f9-152">LINQ do obiektów, między innymi implementacjami ma parametr wejściowy, którego typ jest jednym z <xref:System.Func%601> rodzina delegatów.</span><span class="sxs-lookup"><span data-stu-id="788f9-152">LINQ to Objects, among other implementations, have an input parameter whose type is one of the <xref:System.Func%601> family of generic delegates.</span></span> <span data-ttu-id="788f9-153">Te obiekty delegowane używać parametrów typu, aby określić liczbę i typ parametrów wejściowych i typ zwracany delegata.</span><span class="sxs-lookup"><span data-stu-id="788f9-153">These delegates use type parameters to define the number and type of input parameters, and the return type of the delegate.</span></span> <span data-ttu-id="788f9-154">`Func`Obiekty delegowane są bardzo przydatne w przypadku hermetyzując wyrażenia zdefiniowane przez użytkownika, które są stosowane do każdego elementu w zestawie danych źródłowych.</span><span class="sxs-lookup"><span data-stu-id="788f9-154">`Func` delegates are very useful for encapsulating user-defined expressions that are applied to each element in a set of source data.</span></span> <span data-ttu-id="788f9-155">Rozważmy na przykład <xref:System.Func%601> delegata, którego składnia jest następująca:</span><span class="sxs-lookup"><span data-stu-id="788f9-155">For example, consider the <xref:System.Func%601> delegate, whose syntax is:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#1)]

<span data-ttu-id="788f9-156">Delegat można wdrożyć z kodem podobne do poniższych</span><span class="sxs-lookup"><span data-stu-id="788f9-156">The delegate can be instantiated with code like the following</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#2)]

<span data-ttu-id="788f9-157">gdzie `int` jest parametrem wejściowym i `bool` jest zwracana wartość.</span><span class="sxs-lookup"><span data-stu-id="788f9-157">where `int` is an input parameter, and `bool` is the return value.</span></span> <span data-ttu-id="788f9-158">Wartość zwracana jest zawsze określona w ostatnim parametrze typu.</span><span class="sxs-lookup"><span data-stu-id="788f9-158">The return value is always specified in the last type parameter.</span></span> <span data-ttu-id="788f9-159">Gdy następujące `Func` jest wywoływany delegat, zwraca wartość PRAWDA lub FAŁSZ, aby wskazać, czy parametr wejściowy jest równa 5:</span><span class="sxs-lookup"><span data-stu-id="788f9-159">When the following `Func` delegate is invoked, it returns true or false to indicate whether the input parameter is equal to 5:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#3)]

<span data-ttu-id="788f9-160">Może też podawać wyrażenia lambda, gdy typ argumentu jest <xref:System.Linq.Expressions.Expression%601>, na przykład w przypadku standardowych operatorów zapytań zdefiniowane w <xref:System.Linq.Queryable> typu.</span><span class="sxs-lookup"><span data-stu-id="788f9-160">You can also supply a lambda expression when the argument type is an <xref:System.Linq.Expressions.Expression%601>, for example in the standard query operators that are defined in the <xref:System.Linq.Queryable> type.</span></span> <span data-ttu-id="788f9-161">Po określeniu <xref:System.Linq.Expressions.Expression%601> kompilowania argument, wyrażenie lambda na drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="788f9-161">When you specify an <xref:System.Linq.Expressions.Expression%601> argument, the lambda is compiled to an expression tree.</span></span> <span data-ttu-id="788f9-162">W poniższym przykładzie użyto [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) — operator zapytań standardowa.</span><span class="sxs-lookup"><span data-stu-id="788f9-162">The following example uses the [System.Linq.Enumerable.Count](xref:System.Linq.Enumerable.Count%60%601(System.Collections.Generic.IEnumerable{%60%600})) standard query operator.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#4)]

<span data-ttu-id="788f9-163">Kompilator może wywnioskować typ parametru wejściowego, ale można go również określić w sposób jawny.</span><span class="sxs-lookup"><span data-stu-id="788f9-163">The compiler can infer the type of the input parameter, or you can also specify it explicitly.</span></span> <span data-ttu-id="788f9-164">To wyrażenie lambda określonej liczby tych liczb całkowitych (`n`), który podzielony przez dwa, mieć reszty 1.</span><span class="sxs-lookup"><span data-stu-id="788f9-164">This particular lambda expression counts those integers (`n`) that, when divided by two, have a remainder of 1.</span></span>

<span data-ttu-id="788f9-165">Poniższy przykład tworzy sekwencję, który zawiera wszystkie elementy w `numbers` tablica, która poprzedzać 9, ponieważ jest to pierwszy numer w sekwencji, które nie spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="788f9-165">The following example produces a sequence that contains all elements in the `numbers` array that precede the 9, because that's the first number in the sequence that doesn't meet the condition.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#5)]

<span data-ttu-id="788f9-166">W poniższym przykładzie wiele parametrów wejściowych ujęte w nawiasy.</span><span class="sxs-lookup"><span data-stu-id="788f9-166">The following example specifies multiple input parameters by enclosing them in parentheses.</span></span> <span data-ttu-id="788f9-167">Metoda zwraca wszystkie elementy w tablicy liczb, aż do napotkania numer, którego wartość jest mniejsza niż jego porządkowym w tablicy.</span><span class="sxs-lookup"><span data-stu-id="788f9-167">The method returns all the elements in the numbers array until it encounters a number whose value is less than its ordinal position in the array.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/query1.cs#6)]

## <a name="type-inference-in-lambda-expressions"></a><span data-ttu-id="788f9-168">Wnioskowanie o typie w wyrażeniach lambda</span><span class="sxs-lookup"><span data-stu-id="788f9-168">Type inference in lambda expressions</span></span> ##

<span data-ttu-id="788f9-169">Podczas pisania wyrażeń lambda, często nie trzeba określać typ dla parametrów wejściowych, ponieważ kompilator może wnioskować o typie na podstawie treści lambda, typy parametrów i innych czynników, zgodnie z opisem w specyfikacji języka C#.</span><span class="sxs-lookup"><span data-stu-id="788f9-169">When writing lambdas, you often do not have to specify a type for the input parameters because the compiler can infer the type based on the lambda body, the parameter types, and other factors, as described in the C# Language Specification.</span></span> <span data-ttu-id="788f9-170">Dla większości standardowych operatorów zapytań pierwszy element danych wejściowych jest typem elementów w sekwencji źródłowej.</span><span class="sxs-lookup"><span data-stu-id="788f9-170">For most of the standard query operators, the first input is the type of the elements in the source sequence.</span></span> <span data-ttu-id="788f9-171">Wyszukując `IEnumerable<Customer>`, następnie wejściowego zmiennej jest wywnioskowany jako `Customer` obiektu, co oznacza, że masz dostęp do właściwości i metod:</span><span class="sxs-lookup"><span data-stu-id="788f9-171">If you are querying an `IEnumerable<Customer>`, then the input variable is inferred to be a `Customer` object, which means you have access to its methods and properties:</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/infer1.cs#1)]

<span data-ttu-id="788f9-172">Ogólne zasady wnioskowanie o typie dla wyrażeń lambda są:</span><span class="sxs-lookup"><span data-stu-id="788f9-172">The general rules for type inference for lambdas are:</span></span>

- <span data-ttu-id="788f9-173">Wyrażenie lambda musi zawierać taką samą liczbę parametrów jak typ delegata.</span><span class="sxs-lookup"><span data-stu-id="788f9-173">The lambda must contain the same number of parameters as the delegate type.</span></span>

- <span data-ttu-id="788f9-174">Każdy argument wejściowy w wyrażeniu lambda musi być umożliwiają niejawnej konwersji na jego odpowiadającego mu parametru delegowanego.</span><span class="sxs-lookup"><span data-stu-id="788f9-174">Each input argument in the lambda must be implicitly convertible to its corresponding delegate parameter.</span></span>

- <span data-ttu-id="788f9-175">Wartość zwracana wyrażenia lambda (jeżeli istnieje) musi umożliwiać niejawną konwersję na zwracany typ delegata.</span><span class="sxs-lookup"><span data-stu-id="788f9-175">The return value of the lambda (if any) must be implicitly convertible to the delegate's return type.</span></span>

<span data-ttu-id="788f9-176">Należy zauważyć, że wyrażenia lambda same w sobie nie mają typu, ponieważ system typów wspólnych nie obejmuje wewnętrznej koncepcji „wyrażenia lambda”.</span><span class="sxs-lookup"><span data-stu-id="788f9-176">Note that lambda expressions in themselves do not have a type because the common type system has no intrinsic concept of "lambda expression."</span></span> <span data-ttu-id="788f9-177">Jednak czasami wygodnie jest mówić potocznie o „typie” wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="788f9-177">However, it is sometimes convenient to speak informally of the "type" of a lambda expression.</span></span> <span data-ttu-id="788f9-178">W takich przypadkach typ odwołuje się do typu delegata lub <xref:System.Linq.Expressions.Expression> wpisz jest konwertowane Wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="788f9-178">In these cases the type refers to the delegate type or <xref:System.Linq.Expressions.Expression> type to which the lambda expression is converted.</span></span>

## <a name="variable-scope-in-lambda-expressions"></a><span data-ttu-id="788f9-179">Zakres zmiennych w wyrażeniach lambda</span><span class="sxs-lookup"><span data-stu-id="788f9-179">Variable Scope in Lambda Expressions</span></span> ##

<span data-ttu-id="788f9-180">Wyrażenia lambda, może się odwoływać do *zmienne zewnętrzne* (zobacz [metod anonimowych](programming-guide/statements-expressions-operators/anonymous-methods.md)) w zakresie w metodę, która definiuje funkcję lambda, lub w zakresie w typie, który zawiera wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="788f9-180">Lambdas can refer to *outer variables* (see [Anonymous methods](programming-guide/statements-expressions-operators/anonymous-methods.md)) that are in scope in the method that defines the lambda function, or in scope in the type that contains the lambda expression.</span></span> <span data-ttu-id="788f9-181">Przechwytywane w ten sposób zmienne są przechowywane do użytku w wyrażeniu lambda, nawet gdyby w innym wypadku te zmienne znalazłyby się poza zakresem i zostałyby usunięte w ramach odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="788f9-181">Variables that are captured in this manner are stored for use in the lambda expression even if the variables would otherwise go out of scope and be garbage collected.</span></span> <span data-ttu-id="788f9-182">Zewnętrzna zmienna musi być zdecydowanie przypisana, aby można jej było użyć w wyrażeniu lambda.</span><span class="sxs-lookup"><span data-stu-id="788f9-182">An outer variable must be definitely assigned before it can be consumed in a lambda expression.</span></span> <span data-ttu-id="788f9-183">W poniższym przykładzie pokazano tych reguł.</span><span class="sxs-lookup"><span data-stu-id="788f9-183">The following example demonstrates these rules.</span></span>

[!code-csharp[csSnippets.Lambdas](../../samples/snippets/csharp/concepts/lambda-expressions/scope.cs#1)]

 <span data-ttu-id="788f9-184">Do zakresu zmiennych w wyrażeniach lambda są stosowane następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="788f9-184">The following rules apply to variable scope in lambda expressions:</span></span>

- <span data-ttu-id="788f9-185">Zmienna, która jest przechwytywana, nie będzie usuwana w ramach odśmiecania pamięci, dopóki odwołujący się do niej delegat nie będzie podlegał odśmiecaniu pamięci.</span><span class="sxs-lookup"><span data-stu-id="788f9-185">A variable that is captured will not be garbage-collected until the delegate that references it becomes eligible for garbage collection.</span></span>

- <span data-ttu-id="788f9-186">Zmienne zawarte w wyrażeniu lambda nie są widoczne w metodzie zewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="788f9-186">Variables introduced within a lambda expression are not visible in the outer method.</span></span>

- <span data-ttu-id="788f9-187">Wyrażenia lambda nie może bezpośrednio przechwytywania `ref` lub `out` parametru z metody otaczającej.</span><span class="sxs-lookup"><span data-stu-id="788f9-187">A lambda expression cannot directly capture a `ref` or `out` parameter from an enclosing method.</span></span>

- <span data-ttu-id="788f9-188">Instrukcja return w wyrażeniu lambda nie powoduje wykonania instrukcji return w otaczającej go metodzie.</span><span class="sxs-lookup"><span data-stu-id="788f9-188">A return statement in a lambda expression does not cause the enclosing method to return.</span></span>

- <span data-ttu-id="788f9-189">Wyrażenia lambda nie może zawierać `goto` instrukcji, `break` instrukcji lub `continue` instrukcji, która znajduje się wewnątrz funkcji lambda w przypadku docelowej instrukcji skok poza blokiem.</span><span class="sxs-lookup"><span data-stu-id="788f9-189">A lambda expression cannot contain a `goto` statement, `break` statement, or `continue` statement that is inside the lambda function if the jump statement’s target is outside the block.</span></span> <span data-ttu-id="788f9-190">Błędem jest również instrukcja skoku poza blok funkcji lambda, jeśli obiekt docelowy znajduje się wewnątrz bloku.</span><span class="sxs-lookup"><span data-stu-id="788f9-190">It is also an error to have a jump statement outside the lambda function block if the target is inside the block.</span></span>

## <a name="see-also"></a><span data-ttu-id="788f9-191">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="788f9-191">See also</span></span> ##

<span data-ttu-id="788f9-192">[LINQ (zapytania o języku zintegrowanym)](../standard/using-linq.md) </span><span class="sxs-lookup"><span data-stu-id="788f9-192">[LINQ (Language-Integrated Query)](../standard/using-linq.md) </span></span>  
<span data-ttu-id="788f9-193">[Metody anonimowe](programming-guide/statements-expressions-operators/anonymous-methods.md) </span><span class="sxs-lookup"><span data-stu-id="788f9-193">[Anonymous methods](programming-guide/statements-expressions-operators/anonymous-methods.md) </span></span>  
[<span data-ttu-id="788f9-194">Drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="788f9-194">Expression trees</span></span>](expression-trees.md)
