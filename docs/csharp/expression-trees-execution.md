---
title: Wykonywanie drzew wyrażeń
description: Dowiedz się więcej o wykonywaniu drzew wyrażeń, konwertując je na instrukcje IL (wykonywalny język pośredni).
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 802a83f52f9c05a99c3f49f8f6511eff81ef3eaa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146024"
---
# <a name="executing-expression-trees"></a><span data-ttu-id="87777-103">Wykonywanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="87777-103">Executing Expression Trees</span></span>

[<span data-ttu-id="87777-104">Poprzedni -- Typy struktury obsługujące drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="87777-104">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="87777-105">*Drzewo wyrażeń* jest strukturą danych, która reprezentuje jakiś kod.</span><span class="sxs-lookup"><span data-stu-id="87777-105">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="87777-106">Nie jest skompilowany i wykonywalny kod.</span><span class="sxs-lookup"><span data-stu-id="87777-106">It is not compiled and executable code.</span></span> <span data-ttu-id="87777-107">Jeśli chcesz wykonać kod .NET, który jest reprezentowany przez drzewo wyrażeń, należy przekonwertować go na wykonywalne instrukcje IL.</span><span class="sxs-lookup"><span data-stu-id="87777-107">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span>

## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="87777-108">Wyrażenia Lambda do funkcji</span><span class="sxs-lookup"><span data-stu-id="87777-108">Lambda Expressions to Functions</span></span>

<span data-ttu-id="87777-109">Można przekonwertować dowolny LambdaExpression lub dowolny typ pochodzący z LambdaExpression do pliku wykonywalnego IL.</span><span class="sxs-lookup"><span data-stu-id="87777-109">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="87777-110">Nie można bezpośrednio przekonwertować innych typów wyrażeń na kod.</span><span class="sxs-lookup"><span data-stu-id="87777-110">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="87777-111">Ograniczenie to ma niewielki wpływ w praktyce.</span><span class="sxs-lookup"><span data-stu-id="87777-111">This restriction has little effect in practice.</span></span> <span data-ttu-id="87777-112">Wyrażenia Lambda są jedynymi typami wyrażeń, które chcesz wykonać, konwertując na wykonywalny język pośredni (IL).</span><span class="sxs-lookup"><span data-stu-id="87777-112">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="87777-113">(Zastanów się, co to `ConstantExpression`znaczy bezpośrednio wykonać .</span><span class="sxs-lookup"><span data-stu-id="87777-113">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="87777-114">Czy oznaczałoby to coś użytecznego?) Każde drzewo `LambdaExpression`wyrażeń, które jest `LambdaExpression` , lub typu pochodzącego z mogą być konwertowane na IL.</span><span class="sxs-lookup"><span data-stu-id="87777-114">Would it mean anything useful?) Any expression tree that is a `LambdaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="87777-115">Typ `Expression<TDelegate>` wyrażenia jest jedynym konkretnym przykładem w bibliotekach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87777-115">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="87777-116">Jest on używany do reprezentowania wyrażenia, które mapuje do dowolnego typu delegata.</span><span class="sxs-lookup"><span data-stu-id="87777-116">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="87777-117">Ponieważ ten typ jest mapowany na typ delegata, program .NET może sprawdzić wyrażenie i wygenerować il dla odpowiedniego delegata, który pasuje do podpisu wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="87777-117">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span>

<span data-ttu-id="87777-118">W większości przypadków tworzy to proste mapowanie między wyrażeniem i jego odpowiedniego delegata.</span><span class="sxs-lookup"><span data-stu-id="87777-118">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="87777-119">Na przykład drzewo wyrażeń, `Expression<Func<int>>` które jest reprezentowane przez zostanie `Func<int>`przekonwertowany na delegata typu .</span><span class="sxs-lookup"><span data-stu-id="87777-119">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="87777-120">Dla wyrażenia lambda z dowolnego typu zwracanego i listy argumentów istnieje typ delegata, który jest typem docelowym dla kodu wykonywalnego reprezentowanego przez to wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="87777-120">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lambda expression.</span></span>

<span data-ttu-id="87777-121">Typ `LambdaExpression` zawiera `Compile` `CompileToMethod` i elementy członkowskie, które można użyć do konwersji drzewa wyrażeń do kodu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="87777-121">The `LambdaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="87777-122">Metoda `Compile` tworzy delegata.</span><span class="sxs-lookup"><span data-stu-id="87777-122">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="87777-123">Metoda `CompileToMethod` aktualizuje `MethodBuilder` obiekt za pomocą IL, który reprezentuje skompilowane dane wyjściowe drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="87777-123">The `CompileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="87777-124">Należy `CompileToMethod` zauważyć, że jest dostępna tylko w pełnej struktury pulpitu, a nie w .NET Core.</span><span class="sxs-lookup"><span data-stu-id="87777-124">Note that `CompileToMethod` is only available in the full desktop framework, not in the .NET Core.</span></span>

<span data-ttu-id="87777-125">Opcjonalnie można również `DebugInfoGenerator` podać, który otrzyma informacje o debugowaniu symbolu dla wygenerowanego obiektu delegata.</span><span class="sxs-lookup"><span data-stu-id="87777-125">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="87777-126">Dzięki temu można przekonwertować drzewo wyrażeń do obiektu delegata i mieć pełne informacje debugowania o wygenerowanym pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="87777-126">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="87777-127">Wyrażenie można przekonwertować na pełnomocnika przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="87777-127">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="87777-128">Należy zauważyć, że typ delegata jest oparty na typie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="87777-128">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="87777-129">Musisz znać typ zwracany i listę argumentów, jeśli chcesz użyć obiektu delegata w sposób silnie typowany.</span><span class="sxs-lookup"><span data-stu-id="87777-129">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="87777-130">Metoda `LambdaExpression.Compile()` zwraca `Delegate` typ.</span><span class="sxs-lookup"><span data-stu-id="87777-130">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="87777-131">Należy rzutować go do prawidłowego typu delegata, aby wszelkie narzędzia czasu kompilacji sprawdzić listę argumentów lub typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="87777-131">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list or return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="87777-132">Wykonanie i okresy istnienia</span><span class="sxs-lookup"><span data-stu-id="87777-132">Execution and Lifetimes</span></span>

<span data-ttu-id="87777-133">Kod można wykonać, wywołując pełnomocnika utworzonego `LambdaExpression.Compile()`po wywołaniu .</span><span class="sxs-lookup"><span data-stu-id="87777-133">You execute the code by invoking the delegate created when you called `LambdaExpression.Compile()`.</span></span> <span data-ttu-id="87777-134">Możesz zobaczyć powyższe, gdzie `add.Compile()` zwraca delegata.</span><span class="sxs-lookup"><span data-stu-id="87777-134">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="87777-135">Wywoływanie tego delegata, `func()` wywołując wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="87777-135">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="87777-136">Ten delegat reprezentuje kod w drzewie wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="87777-136">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="87777-137">Można zachować dojście do tego pełnomocnika i wywołać go później.</span><span class="sxs-lookup"><span data-stu-id="87777-137">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="87777-138">Nie trzeba kompilować drzewa wyrażeń za każdym razem, gdy chcesz wykonać kod, który reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="87777-138">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="87777-139">(Pamiętaj, że drzewa wyrażeń są niezmienne, a kompilacja tego samego drzewa wyrażeń później utworzy pełnomocnika, który wykonuje ten sam kod).</span><span class="sxs-lookup"><span data-stu-id="87777-139">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="87777-140">Przestrzegę przed próbami tworzenia bardziej zaawansowanych mechanizmów buforowania w celu zwiększenia wydajności, unikając niepotrzebnych wywołań kompilacji.</span><span class="sxs-lookup"><span data-stu-id="87777-140">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="87777-141">Porównanie dwóch drzew wyrażeń dowolnego, aby ustalić, czy reprezentują one ten sam algorytm będzie również czasochłonne do wykonania.</span><span class="sxs-lookup"><span data-stu-id="87777-141">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="87777-142">Prawdopodobnie okaże się, że czas obliczeniowy można zapisać `LambdaExpression.Compile()` unikając żadnych dodatkowych wywołań będzie więcej niż zużyte przez czas wykonywania kodu, który określa dwa różne drzewa wyrażeń spowodować ten sam kod wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="87777-142">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="87777-143">Zastrzeżenia</span><span class="sxs-lookup"><span data-stu-id="87777-143">Caveats</span></span>

<span data-ttu-id="87777-144">Kompilowanie wyrażenia lambda do delegata i wywoływanie tego delegata jest jedną z najprostszych operacji, które można wykonać za pomocą drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="87777-144">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="87777-145">Jednak nawet przy tej prostej operacji istnieją zastrzeżenia, o których musisz wiedzieć.</span><span class="sxs-lookup"><span data-stu-id="87777-145">However, even with this simple operation, there are caveats you must be aware of.</span></span>

<span data-ttu-id="87777-146">Wyrażenia Lambda utworzyć zamknięcia nad dowolnymi zmiennymi lokalnymi, które są przywoływani w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="87777-146">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="87777-147">Należy zagwarantować, że wszystkie zmienne, które byłyby częścią delegata są `Compile`użyteczne w lokalizacji, w której wywołasz , i podczas wykonywania wynikowego delegata.</span><span class="sxs-lookup"><span data-stu-id="87777-147">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="87777-148">Ogólnie rzecz biorąc kompilator zapewni, że jest to prawda.</span><span class="sxs-lookup"><span data-stu-id="87777-148">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="87777-149">Jednak jeśli wyrażenie uzyskuje dostęp do `IDisposable`zmiennej, która implementuje , jest możliwe, że kod może usunąć obiektu, gdy jest nadal w posiadaniu drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="87777-149">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="87777-150">Na przykład ten kod działa `int` dobrze, `IDisposable`ponieważ nie implementuje:</span><span class="sxs-lookup"><span data-stu-id="87777-150">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="87777-151">Pełnomocnik przechwycił odwołanie do zmiennej `constant`lokalnej .</span><span class="sxs-lookup"><span data-stu-id="87777-151">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="87777-152">Ta zmienna jest dostępna w dowolnym momencie później, gdy funkcja zwracana przez `CreateBoundFunc` executes.</span><span class="sxs-lookup"><span data-stu-id="87777-152">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="87777-153">Należy jednak wziąć pod uwagę tę (raczej `IDisposable`wymyśloną) klasę, która implementuje:</span><span class="sxs-lookup"><span data-stu-id="87777-153">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

```csharp
public class Resource : IDisposable
{
    private bool isDisposed = false;
    public int Argument
    {
        get
        {
            if (!isDisposed)
                return 5;
            else throw new ObjectDisposedException("Resource");
        }
    }

    public void Dispose()
    {
        isDisposed = true;
    }
}
```

<span data-ttu-id="87777-154">Jeśli używasz go w wyrażeniu, jak `ObjectDisposedException` pokazano poniżej, otrzymasz po `Resource.Argument` wykonaniu kodu, do którego odwołuje się właściwość:</span><span class="sxs-lookup"><span data-stu-id="87777-154">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

```csharp
private static Func<int, int> CreateBoundResource()
{
    using (var constant = new Resource()) // constant is captured by the expression tree
    {
        Expression<Func<int, int>> expression = (b) => constant.Argument + b;
        var rVal = expression.Compile();
        return rVal;
    }
}
```

<span data-ttu-id="87777-155">Delegat zwrócony z tej metody został `constant` zamknięty nad obiektem, który został usunięty.</span><span class="sxs-lookup"><span data-stu-id="87777-155">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="87777-156">(Został usunięty, ponieważ został zadeklarowany w `using` oświadczeniu).)</span><span class="sxs-lookup"><span data-stu-id="87777-156">(It's been disposed, because it was declared in a `using` statement.)</span></span>

<span data-ttu-id="87777-157">Teraz po wykonaniu pełnomocnika zwrócone z tej metody, `ObjectDisposedException` będziesz miał wygenerowany w punkcie wykonania.</span><span class="sxs-lookup"><span data-stu-id="87777-157">Now, when you execute the delegate returned from this method, you'll have a `ObjectDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="87777-158">Wydaje się dziwne, że błąd wykonywania reprezentującykompilacji kompilacji czas, ale to jest świat, który wchodzimy podczas pracy z drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="87777-158">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="87777-159">Istnieje wiele permutacji tego problemu, więc trudno jest zaoferować ogólne wskazówki, aby go uniknąć.</span><span class="sxs-lookup"><span data-stu-id="87777-159">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="87777-160">Należy zachować ostrożność podczas uzyskiwania dostępu do zmiennych lokalnych podczas definiowania wyrażeń i należy zachować ostrożność podczas uzyskiwania dostępu do stanu w bieżącym obiekcie (reprezentowany przez `this`) podczas tworzenia drzewa wyrażeń, które mogą być zwracane przez publiczny interfejs API.</span><span class="sxs-lookup"><span data-stu-id="87777-160">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="87777-161">Kod w wyrażeniu może odwoływać się do metod lub właściwości w innych zestawach.</span><span class="sxs-lookup"><span data-stu-id="87777-161">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="87777-162">Ten zestaw musi być dostępny, gdy wyrażenie jest zdefiniowane i gdy jest kompilowany i gdy wynikowy delegat jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="87777-162">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="87777-163">Spotkasz się z `ReferencedAssemblyNotFoundException` w przypadkach, gdy nie jest obecny.</span><span class="sxs-lookup"><span data-stu-id="87777-163">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="87777-164">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="87777-164">Summary</span></span>

<span data-ttu-id="87777-165">Drzewa wyrażeń reprezentujące wyrażenia lambda można skompilować w celu utworzenia pełnomocnika, który można wykonać.</span><span class="sxs-lookup"><span data-stu-id="87777-165">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="87777-166">Zapewnia to jeden mechanizm do wykonania kodu reprezentowanego przez drzewo wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="87777-166">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="87777-167">Drzewo wyrażeń reprezentuje kod, który będzie wykonywany dla dowolnej konstrukcji, którą tworzysz.</span><span class="sxs-lookup"><span data-stu-id="87777-167">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="87777-168">Tak długo, jak środowisko, w którym skompilować i wykonać kod pasuje do środowiska, w którym można utworzyć wyrażenie, wszystko działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="87777-168">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="87777-169">Jeśli tak się nie stanie, błędy są bardzo przewidywalne i zostaną one przechwycone w pierwszych testach dowolnego kodu przy użyciu drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="87777-169">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="87777-170">Dalej - Interpretacja wyrażeń</span><span class="sxs-lookup"><span data-stu-id="87777-170">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)
