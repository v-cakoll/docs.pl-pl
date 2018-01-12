---
title: "Wykonywanie drzew wyrażeń"
description: "Więcej informacji na temat wykonywanie drzew wyrażeń konwertując je do pliku wykonywalnego instrukcje języku pośrednim (IL)."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: db481c18a79f55b079ec2558b884ce288e2a9933
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="executing-expression-trees"></a><span data-ttu-id="ab8a2-104">Wykonywanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="ab8a2-104">Executing Expression Trees</span></span>

[<span data-ttu-id="ab8a2-105">Poprzednie — Framework typy obsługi drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="ab8a2-105">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="ab8a2-106">*Drzewo wyrażeń* jest strukturą danych, która reprezentuje kod.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-106">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="ab8a2-107">Nie jest skompilowany i wykonywalnego kodu.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-107">It is not compiled and executable code.</span></span> <span data-ttu-id="ab8a2-108">Jeśli chcesz wykonać kodu platformy .NET, reprezentowanym przez wyrażenie drzewa musi przekształcać je do pliku wykonywalnego instrukcji IL.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-108">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span> 
## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="ab8a2-109">Wyrażenia lambda na funkcje</span><span class="sxs-lookup"><span data-stu-id="ab8a2-109">Lambda Expressions to Functions</span></span>
<span data-ttu-id="ab8a2-110">Możesz przekonwertować wszystkie LambdaExpression lub dowolny typ pochodny LambdaExpression do pliku wykonywalnego IL.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-110">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="ab8a2-111">Inne typy wyrażeń nie można przekonwertować bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-111">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="ab8a2-112">Ograniczenie to ma niewielki wpływ, w praktyce.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-112">This restriction has little effect in practice.</span></span> <span data-ttu-id="ab8a2-113">Wyrażenia lambda są tylko typy wyrażeń, które chcesz wykonać konwersję na język pośredni pliku wykonywalnego (IL).</span><span class="sxs-lookup"><span data-stu-id="ab8a2-113">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="ab8a2-114">(Pomyśl o jakie oznaczałoby to wykonać bezpośrednio `ConstantExpression`.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-114">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="ab8a2-115">Może to oznaczać niczego przydatne?) Wszelkie drzewo wyrażeń, który jest `LamdbaExpression`, lub typ pochodzący od `LambdaExpression` może zostać przekonwertowany na IL.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-115">Would it mean anything useful?) Any expression tree that is a `LamdbaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="ab8a2-116">Typ wyrażenia `Expression<TDelegate>` tylko konkretnych przykład w bibliotekach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-116">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="ab8a2-117">Jest ona używana do reprezentowania wyrażenia mapujący do dowolnego typu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-117">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="ab8a2-118">Ponieważ mapuje ten typ do typu delegata, .NET można zbadać wyrażenie i generowanie IL dla odpowiednich delegata, który pasuje do podpisu wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-118">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span> 

<span data-ttu-id="ab8a2-119">W większości przypadków spowoduje to utworzenie prostego mapowanie między wyrażenia i jego odpowiedniego obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-119">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="ab8a2-120">Na przykład drzewo wyrażenia, który jest reprezentowany przez `Expression<Func<int>>` zostanie przekonwertowana na delegata typu `Func<int>`.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-120">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="ab8a2-121">Wyrażenia lambda z zwracany typ i listy argumentów istnieje typ delegata, który typ docelowy dla kodu wykonywalnego reprezentowany przez tego wyrażenia lamdba.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-121">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lamdba expression.</span></span>

<span data-ttu-id="ab8a2-122">`LamdbaExpression` Typ zawiera `Compile` i `CompileToMethod` elementów członkowskich, które należy użyć, aby przekonwertować kod wykonywalny drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-122">The `LamdbaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="ab8a2-123">`Compile` Metoda tworzy delegata.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-123">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="ab8a2-124">`CompileToMethod` Aktualizacje metody `MethodBuilder` obiektu IL, reprezentujący skompilowanych danych wyjściowych drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-124">The `CompileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="ab8a2-125">Należy pamiętać, że `CompileToMethod` znajduje się tylko w ramach całego pulpitu, a nie na platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-125">Note that `CompileToMethod` is only available on the full desktop framework, not on the .NET Core framework.</span></span>

<span data-ttu-id="ab8a2-126">Opcjonalnie można też podać `DebugInfoGenerator` który otrzyma symbol informacji debugowania dla obiekt wygenerowanego obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-126">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="ab8a2-127">Dzięki temu można ich przekonwertować na obiekt delegowany drzewa wyrażenia oraz pełne informacje o debugowaniu o wygenerowanego obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-127">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="ab8a2-128">Czy przekonwertować wyrażenia na delegata, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ab8a2-128">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="ab8a2-129">Zwróć uwagę, że typ delegata jest oparty na typie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-129">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="ab8a2-130">Zwracany typ i listy argumentów musi sprawdzić, czy ma być używany w sposób jednoznaczny obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-130">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="ab8a2-131">`LambdaExpression.Compile()` Metoda zwraca `Delegate` typu.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-131">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="ab8a2-132">Należy rzutować go na typ delegata poprawne mieć żadnych narzędzi kompilacji, zapoznaj się z listą argumentów typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-132">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list of return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="ab8a2-133">Wykonanie i okresy istnienia</span><span class="sxs-lookup"><span data-stu-id="ab8a2-133">Execution and Lifetimes</span></span>

<span data-ttu-id="ab8a2-134">Wykonanie kodu za pomocą delegowanego utworzony podczas wywołania `LamdbaExpression.Compile()`.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-134">You execute the code by invoking the delegate created when you called `LamdbaExpression.Compile()`.</span></span> <span data-ttu-id="ab8a2-135">Widać to powyżej where `add.Compile()` zwraca delegata.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-135">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="ab8a2-136">Wywoływanie tego delegata, wywołując `func()` wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-136">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="ab8a2-137">Ten delegat reprezentuje kod w drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-137">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="ab8a2-138">Możesz zachować dojścia do tego obiektu delegowanego i wywołać go później.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-138">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="ab8a2-139">Nie trzeba było skompilować drzewa wyrażenia zawsze będzie wykonywany kod, który reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-139">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="ab8a2-140">(Pamiętać, że drzew wyrażeń są niezmienne i później kompilowanie tym samym drzewie wyrażenie utworzy delegata, który wykonuje ten sam kod.)</span><span class="sxs-lookup"><span data-stu-id="ab8a2-140">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="ab8a2-141">Zostanie I uwaga przed w trakcie tworzenia jakichkolwiek bardziej zaawansowanych mechanizmów buforowania w celu zwiększenia wydajności dzięki unikaniu kompilacji niepotrzebne wywołania.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-141">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="ab8a2-142">Porównanie dwóch drzew wyrażeń dowolnego, aby ustalić, czy reprezentują ten sam algorytm będzie również dużo czasu na wykonanie.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-142">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="ab8a2-143">Prawdopodobnie znajdziesz czasu obliczeniowego zapisanie unikanie wszelkie dodatkowe wywołania `LambdaExpression.Compile()` zostaną użyte więcej niż w czasie wykonywania kod, który określa dwóch różnych drzewach wyrażeń spowodować tego samego kodu wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-143">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="ab8a2-144">Ostrzeżenia</span><span class="sxs-lookup"><span data-stu-id="ab8a2-144">Caveats</span></span>

<span data-ttu-id="ab8a2-145">Kompilowanie wyrażenia lambda do delegata i wywoływanie ten delegat jest jednym z najprostszym operacje, które można wykonywać na drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-145">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="ab8a2-146">Nawet w przypadku tej operacji proste, istnieją ostrzeżenia, który musi być znane.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-146">However, even with this simple operation, there are caveats you must be aware of.</span></span> 

<span data-ttu-id="ab8a2-147">Wyrażenia lambda utworzyć zamknięcia przez wszystkie zmienne lokalne, których istnieją odwołania w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-147">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="ab8a2-148">Musi gwarantuje, że wszystkie zmienne, które są częścią delegata są użyteczne, w lokalizacji, w którym należy wywołać `Compile`, a podczas wykonywania wynikowy delegata.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-148">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="ab8a2-149">Ogólnie rzecz biorąc kompilator zagwarantować, że jest to true.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-149">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="ab8a2-150">Jednak jeśli w wyrażeniu uzyskuje dostęp do zmiennej, która implementuje `IDisposable`, istnieje możliwość, że kodu może zlikwidować obiektu podczas, gdy nadal jest przechowywany przez drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-150">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="ab8a2-151">Na przykład ten kod działa prawidłowo, ponieważ `int` nie implementuje `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="ab8a2-151">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="ab8a2-152">Delegat zostały przechwycone odwołanie do zmiennej lokalnej `constant`.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-152">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="ab8a2-153">Tej zmiennej jest dostępny w dowolnym momencie później, gdy wartość zwrócona przez funkcję przez `CreateBoundFunc` wykonuje.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-153">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="ab8a2-154">Jednak wziąć pod uwagę tej klasy (zamiast contrived), który implementuje `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="ab8a2-154">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

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

<span data-ttu-id="ab8a2-155">Jeśli można go użyć w wyrażeniu w sposób przedstawiony poniżej, otrzymasz `ObjectDisposedException` podczas wykonywania kodu odwołuje się `Resource.Argument` właściwości:</span><span class="sxs-lookup"><span data-stu-id="ab8a2-155">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

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

<span data-ttu-id="ab8a2-156">Delegat zwracane z tej metody został zamknięty przez `constant` obiektu, który został zlikwidowany.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-156">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="ab8a2-157">(Jest został usunięty, ponieważ zostało zadeklarowane w `using` instrukcji.)</span><span class="sxs-lookup"><span data-stu-id="ab8a2-157">(It's been disposed, because it was declared in a `using` statement.)</span></span> 

<span data-ttu-id="ab8a2-158">Teraz, po wykonaniu delegata zwracane z tej metody należy `ObjecctDisposedException` zgłoszony w punkcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-158">Now, when you execute the delegate returned from this method, you'll have a `ObjecctDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="ab8a2-159">Wydawać się dziwne błąd środowiska uruchomieniowego reprezentujący konstrukcję kompilacji, ale jest to world, którego możemy wprowadzić podczas współpracy z drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-159">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="ab8a2-160">Istnieje wiele permutacji ten problem, tak trudno oferują ogólne wskazówki, aby uniknąć tego problemu.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-160">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="ab8a2-161">Należy zachować ostrożność podczas uzyskiwania dostępu do zmiennych lokalnych podczas definiowania wyrażeń i należy zachować ostrożność podczas uzyskiwania dostępu do stanu w bieżącym obiekcie (reprezentowane przez `this`) podczas tworzenia drzewa wyrażeń, który może być zwracany przez publiczny interfejs API.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-161">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="ab8a2-162">Kod w wyrażeniu mogą odwoływać się do metody lub właściwości w innych zestawów.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-162">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="ab8a2-163">Tego zestawu musi być dostępny, gdy zdefiniowano wyrażenia i gdy jest on skompilowany i po wywołaniu wynikowy delegata.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-163">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="ab8a2-164">Będzie spełnienia z `ReferencedAssemblyNotFoundException` w przypadkach, gdy nie jest obecny.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-164">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="ab8a2-165">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="ab8a2-165">Summary</span></span>

<span data-ttu-id="ab8a2-166">Drzewa wyrażeń, które reprezentują wyrażenia lambda, może zostać skompilowany do utworzenia delegata, który może zostać uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-166">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="ab8a2-167">Zapewnia jeden mechanizm można wykonać kod reprezentowany przez drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-167">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="ab8a2-168">Drzewo wyrażenia reprezentuje kod, który jest wykonywany dla danego konstrukcji utworzone.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-168">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="ab8a2-169">Tak długo, jak środowisko, gdzie skompilować i wykonywania kodu zgodne środowisko, w której utworzono wyrażenie, wszystko działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-169">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="ab8a2-170">Gdy które się nie stało, błędy są bardzo przewidywalne i zostanie przechwycony w pierwszym testów dowolnego kodu przy użyciu drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="ab8a2-170">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="ab8a2-171">Dalej — Interpretowanie wyrażenia</span><span class="sxs-lookup"><span data-stu-id="ab8a2-171">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)
