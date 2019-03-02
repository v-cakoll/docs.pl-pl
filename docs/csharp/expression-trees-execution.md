---
title: Wykonywanie drzew wyrażeń
description: Więcej informacji na temat wykonywanie drzew wyrażeń, konwertując je do pliku wykonywalnego instrukcje języka pośredniego (IL).
ms.date: 06/20/2016
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: f6dca5a3965924e8eb6e1c04fe7ffc3c78c7df93
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201849"
---
# <a name="executing-expression-trees"></a><span data-ttu-id="9b4cf-103">Wykonywanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="9b4cf-103">Executing Expression Trees</span></span>

[<span data-ttu-id="9b4cf-104">Poprzednie — Typy platform obsługujące drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="9b4cf-104">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="9b4cf-105">*Drzewa wyrażeń* to struktura danych, który reprezentuje kodu.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-105">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="9b4cf-106">Nie jest skompilowany i wykonywalnego kodu.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-106">It is not compiled and executable code.</span></span> <span data-ttu-id="9b4cf-107">Do wykonania kodu platformy .NET, który jest reprezentowany przez drzewo wyrażenia, należy ją przekonwertować do pliku wykonywalnego instrukcje języka IL.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-107">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span>

## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="9b4cf-108">Wyrażenia lambda do funkcji</span><span class="sxs-lookup"><span data-stu-id="9b4cf-108">Lambda Expressions to Functions</span></span>

<span data-ttu-id="9b4cf-109">Możesz również przekonwertować wszystkie Wyrażenielambda lub dowolnego typu opracowane z Wyrażenielambda do pliku wykonywalnego IL.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-109">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="9b4cf-110">Inne typy wyrażenia nie można przekonwertować bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-110">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="9b4cf-111">Ograniczenie to ma niewielki wpływ w praktyce.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-111">This restriction has little effect in practice.</span></span> <span data-ttu-id="9b4cf-112">Wyrażenia lambda są tylko typy wyrażeń, które trzeba będzie wykonać za pomocą konwersji do pliku wykonywalnego języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="9b4cf-112">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="9b4cf-113">(Myśl o tym, na co oznaczałoby bezpośrednie wykonywanie `ConstantExpression`.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-113">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="9b4cf-114">Może to oznaczać żadnych użytecznych?) Wszelkie drzewa wyrażeń, który jest `LambdaExpression`, lub typ pochodzący od `LambdaExpression` mogą być konwertowane na IL.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-114">Would it mean anything useful?) Any expression tree that is a `LambdaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="9b4cf-115">Typ wyrażenia `Expression<TDelegate>` tylko konkretnych przykład w bibliotekach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-115">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="9b4cf-116">Jest ona używana do reprezentowania wyrażenia, który jest mapowany do dowolnego typu delegata.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-116">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="9b4cf-117">Ponieważ ten typ jest mapowany do typu delegata, .NET można zbadać wyrażenie i wygenerować IL dla odpowiednich delegata, który pasuje do podpisu wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-117">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span> 

<span data-ttu-id="9b4cf-118">W większości przypadków spowoduje to utworzenie mapowania proste między wyrażenia oraz jego odpowiednie delegata.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-118">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="9b4cf-119">Na przykład drzewo wyrażenia, który jest reprezentowany przez `Expression<Func<int>>` zostanie przekonwertowana na delegata tego typu `Func<int>`.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-119">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="9b4cf-120">Dla wyrażenia lambda z listy argumentów i zwracanego typu istnieje typ delegata, który jest typem docelowym dla pliku wykonywalnego kodu, reprezentowane przez to wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-120">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lambda expression.</span></span>

<span data-ttu-id="9b4cf-121">`LambdaExpression` Typ zawiera `Compile` i `CompileToMethod` elementów członkowskich, które umożliwiają przekonwertować drzewa wyrażenie kodu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-121">The `LambdaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="9b4cf-122">`Compile` Metoda tworzy delegata.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-122">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="9b4cf-123">`CompileToMethod` Metody aktualizacji `MethodBuilder` obiektu IL, reprezentujący skompilowanych danych wyjściowych drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-123">The `CompileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="9b4cf-124">Należy pamiętać, że `CompileToMethod` dostępną tylko w ramach całego pulpitu, a nie w .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-124">Note that `CompileToMethod` is only available in the full desktop framework, not in the .NET Core.</span></span>

<span data-ttu-id="9b4cf-125">Opcjonalnie możesz też podać `DebugInfoGenerator` , zostanie wyświetlony symbol informacji debugowania dla obiektu delegowanego wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-125">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="9b4cf-126">Dzięki temu można przekonwertować na drzewo wyrażenia do obiektu delegowanego i mają pełne informacje debugowania o wygenerowanym delegata.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-126">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="9b4cf-127">Wyrażenie może przekonwertować na obiekt delegowany, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="9b4cf-127">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="9b4cf-128">Należy zauważyć, że typ delegata jest oparty na typ wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-128">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="9b4cf-129">Jeśli chcesz użyć obiektu delegowanego w silnie typizowany sposób musisz znać typ zwracany i listą argumentów.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-129">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="9b4cf-130">`LambdaExpression.Compile()` Metoda zwraca `Delegate` typu.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-130">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="9b4cf-131">Będzie trzeba go rzutować na typ delegata poprawne mieć żadnych narzędzi kompilacji, zapoznaj się z listą argument lub zwracany typ.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-131">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list or return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="9b4cf-132">Okresy istnienia i wykonywanie</span><span class="sxs-lookup"><span data-stu-id="9b4cf-132">Execution and Lifetimes</span></span>

<span data-ttu-id="9b4cf-133">Wykonywania kodu za pomocą wywołania delegata utworzone podczas wywołania `LambdaExpression.Compile()`.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-133">You execute the code by invoking the delegate created when you called `LambdaExpression.Compile()`.</span></span> <span data-ttu-id="9b4cf-134">Widać to powyżej gdzie `add.Compile()` zwraca delegata.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-134">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="9b4cf-135">Wywołanie delegata, wywołując `func()` wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-135">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="9b4cf-136">Ten delegat reprezentuje kod w drzewie wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-136">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="9b4cf-137">Można zachować dojścia do delegata i wywoływać go później.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-137">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="9b4cf-138">Nie musisz skompilować każdorazowo, którą chcesz wykonywać kod, który reprezentuje drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-138">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="9b4cf-139">(Należy pamiętać, że drzew wyrażeń są niezmienne i kompilowanie później tego samego drzewa wyrażeń utworzy obiekt delegowany, który jest wykonywany ten sam kod).</span><span class="sxs-lookup"><span data-stu-id="9b4cf-139">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="9b4cf-140">I będzie przestrzega przed w trakcie tworzenia jakichkolwiek bardziej zaawansowanych mechanizmów buforowania, co pozwoli zwiększyć wydajność przez unikanie niepotrzebnych kompilacji wywołania.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-140">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="9b4cf-141">Porównywanie dwa drzewa wykonania dowolnego wyrażenia, aby określić, czy stanowią one ten sam algorytm będzie również dużo czasu do wykonania.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-141">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="9b4cf-142">Prawdopodobnie okaże czas obliczeń zapisanie unikanie wszelkie dodatkowe wywołania `LambdaExpression.Compile()` będzie możliwe więcej niż przez czas wykonywania kodu, który określa dwóch różnych drzew wyrażeń spowodować tego samego kodu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-142">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="9b4cf-143">Ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="9b4cf-143">Caveats</span></span>

<span data-ttu-id="9b4cf-144">Kompilowanie wyrażenia lambda do delegata i wywoływania delegata jest jednym z najprostszym operacje, które można wykonywać na drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-144">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="9b4cf-145">Jednak nawet w przypadku tej operacji proste, istnieją zastrzeżenia, których należy wiedzieć.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-145">However, even with this simple operation, there are caveats you must be aware of.</span></span> 

<span data-ttu-id="9b4cf-146">Wyrażenia lambda Utwórz wolnych od pracy nad zmienne lokalne, które są przywoływane w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-146">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="9b4cf-147">Musisz gwarantować, wszystkie zmienne, które są częścią obiektu delegowanego jest użyteczne w lokalizacji, gdzie jest wywoływana `Compile`, a podczas wykonywania wynikowego delegata.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-147">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="9b4cf-148">Ogólnie rzecz biorąc kompilator zapewnia, że ta zasada obowiązuje.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-148">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="9b4cf-149">Jednakże jeśli wyrażenie uzyskuje dostęp do zmiennej, która implementuje `IDisposable`, istnieje możliwość, że Twój kod może usunąć obiekt podczas nadal odbywa się przez drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-149">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="9b4cf-150">Na przykład, ten kod działa poprawnie, ponieważ `int` nie implementuje `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="9b4cf-150">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="9b4cf-151">Delegat został przechwycony odwołaniem do zmiennej lokalnej `constant`.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-151">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="9b4cf-152">Tej zmiennej jest dostępna w dowolnym momencie później, po wartość zwrócona przez funkcję przez `CreateBoundFunc` wykonuje.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-152">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="9b4cf-153">Jednak wziąć pod uwagę tej klasy (zamiast contrived), który implementuje `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="9b4cf-153">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

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

<span data-ttu-id="9b4cf-154">Jeśli jest ona używana w wyrażeniu jak pokazano poniżej, otrzymasz `ObjectDisposedException` podczas wykonywania kodu, odwołuje się `Resource.Argument` właściwości:</span><span class="sxs-lookup"><span data-stu-id="9b4cf-154">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

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

<span data-ttu-id="9b4cf-155">Delegat zwrócone w wyniku tej metody został zamknięty przez `constant` obiektu, który został zlikwidowany.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-155">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="9b4cf-156">(Jest został usunięty, ponieważ została ona zadeklarowana w `using` instrukcja.)</span><span class="sxs-lookup"><span data-stu-id="9b4cf-156">(It's been disposed, because it was declared in a `using` statement.)</span></span> 

<span data-ttu-id="9b4cf-157">Teraz, po wykonaniu delegata zwrócone w wyniku tej metody, będziesz mieć `ObjectDisposedException` generowany w momencie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-157">Now, when you execute the delegate returned from this method, you'll have a `ObjectDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="9b4cf-158">Wydawać się dziwne mają reprezentujących konstrukcję kompilacji błąd w czasie wykonywania, ale jest to świecie, w którym możemy wprowadzić, kiedy będziemy pracować z drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-158">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="9b4cf-159">Dlatego jest trudny do oferty ogólne wskazówki, aby uniknąć tego błędu jest dostępnych wiele permutacji tego problemu.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-159">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="9b4cf-160">Należy zachować ostrożność podczas definiowania wyrażeń uzyskiwania dostępu do zmiennych lokalnych i należy zachować ostrożność w przypadku uzyskiwania dostępu do stanu w bieżącym obiekcie (reprezentowane przez `this`) podczas tworzenia drzewa wyrażenie, które mogą być zwrócone przez publiczny interfejs API.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-160">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="9b4cf-161">Kod w swoim wyrażeniu może odwoływać się do metody lub właściwości w innych zestawach.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-161">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="9b4cf-162">Ten zestaw musi być dostępny, gdy wyrażenie jest zdefiniowany i gdy jest ona kompilowana i kiedy wynikowy obiekt delegowany jest wywoływany.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-162">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="9b4cf-163">Można będzie spełniony przy użyciu `ReferencedAssemblyNotFoundException` w przypadkach, gdy nie jest obecny.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-163">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="9b4cf-164">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="9b4cf-164">Summary</span></span>

<span data-ttu-id="9b4cf-165">Drzewa wyrażeń, które reprezentują wyrażenia lambda może być kompilowane do utworzenia delegata, który może zostać uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-165">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="9b4cf-166">Zapewnia jeden mechanizm, aby wykonać ten kod reprezentowany przez drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-166">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="9b4cf-167">Drzewo wyrażenia reprezentuje kod, który jest wykonywany dla danego konstrukcji, które można utworzyć.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-167">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="9b4cf-168">Tak długo, jak środowisko, gdzie skompilować i wykonać ten kod jest zgodny z środowisku, w którym są tworzone wyrażenie, wszystko działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-168">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="9b4cf-169">Jeśli nie mają miejsce, błędy są bardzo przewidywalny i zostanie przechwycony w testach pierwszy dowolnego kodu, przy użyciu drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="9b4cf-169">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="9b4cf-170">Dalej — Interpretowanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="9b4cf-170">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)
