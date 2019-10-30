---
title: Wykonywanie drzew wyrażeń
description: Dowiedz się więcej o wykonywaniu drzew wyrażeń, konwertując je na instrukcje wykonywalnego języka pośredniego (IL).
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 9af4b346962cb743daddf774e8b3c1f8fa722ae4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037114"
---
# <a name="executing-expression-trees"></a><span data-ttu-id="35a92-103">Wykonywanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="35a92-103">Executing Expression Trees</span></span>

[<span data-ttu-id="35a92-104">Poprzednie typy struktur obsługujące drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="35a92-104">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="35a92-105">*Drzewo wyrażenia* jest strukturą danych, która reprezentuje kod.</span><span class="sxs-lookup"><span data-stu-id="35a92-105">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="35a92-106">Nie jest skompilowany i kod wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="35a92-106">It is not compiled and executable code.</span></span> <span data-ttu-id="35a92-107">Jeśli chcesz wykonać kod .NET, który jest reprezentowany przez drzewo wyrażenia, należy przekonwertować go na instrukcje pliku wykonywalnego IL.</span><span class="sxs-lookup"><span data-stu-id="35a92-107">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span>

## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="35a92-108">Wyrażenia lambda do funkcji</span><span class="sxs-lookup"><span data-stu-id="35a92-108">Lambda Expressions to Functions</span></span>

<span data-ttu-id="35a92-109">Można przekonwertować dowolne Wyrażenielambda lub dowolny typ pochodzący z Wyrażenielambda do pliku wykonywalnego IL.</span><span class="sxs-lookup"><span data-stu-id="35a92-109">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="35a92-110">Inne typy wyrażeń nie mogą być bezpośrednio konwertowane na kod.</span><span class="sxs-lookup"><span data-stu-id="35a92-110">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="35a92-111">To ograniczenie ma niewielki wpływ na praktyce.</span><span class="sxs-lookup"><span data-stu-id="35a92-111">This restriction has little effect in practice.</span></span> <span data-ttu-id="35a92-112">Wyrażenia lambda są jedynymi typami wyrażeń, które mają być wykonywane przez konwersję do wykonywalnego języka pośredniego (IL).</span><span class="sxs-lookup"><span data-stu-id="35a92-112">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="35a92-113">(Należy zastanowić się, co będzie miało na celu bezpośrednie wykonanie `ConstantExpression`.</span><span class="sxs-lookup"><span data-stu-id="35a92-113">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="35a92-114">Czy to oznacza coś przydatnego?) Dowolne drzewo wyrażeń, które jest `LambdaExpression`lub typ pochodzący od `LambdaExpression` można przekonwertować na IL.</span><span class="sxs-lookup"><span data-stu-id="35a92-114">Would it mean anything useful?) Any expression tree that is a `LambdaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="35a92-115">Typ wyrażenia `Expression<TDelegate>` jest jedynym konkretnym przykładem w bibliotekach .NET Core.</span><span class="sxs-lookup"><span data-stu-id="35a92-115">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="35a92-116">Służy do reprezentowania wyrażenia, które jest mapowane na dowolny typ delegata.</span><span class="sxs-lookup"><span data-stu-id="35a92-116">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="35a92-117">Ponieważ ten typ jest mapowany na typ delegata, .NET może przeanalizować wyrażenie i wygenerować IL dla odpowiedniego delegata, który jest zgodny z podpisem wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="35a92-117">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span> 

<span data-ttu-id="35a92-118">W większości przypadków tworzy proste mapowanie między wyrażeniem i odpowiadającym mu delegatem.</span><span class="sxs-lookup"><span data-stu-id="35a92-118">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="35a92-119">Na przykład drzewo wyrażenia, które jest reprezentowane przez `Expression<Func<int>>`, zostanie przekonwertowane na delegata typu `Func<int>`.</span><span class="sxs-lookup"><span data-stu-id="35a92-119">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="35a92-120">W przypadku wyrażenia lambda z dowolnym typem zwracanym i listą argumentów istnieje typ delegata, który jest typem docelowym dla kodu wykonywalnego reprezentowanego przez to wyrażenie lambda.</span><span class="sxs-lookup"><span data-stu-id="35a92-120">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lambda expression.</span></span>

<span data-ttu-id="35a92-121">Typ `LambdaExpression` zawiera `Compile` i `CompileToMethod` członków, których można użyć do przekonwertowania drzewa wyrażenia na kod wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="35a92-121">The `LambdaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="35a92-122">Metoda `Compile` tworzy delegata.</span><span class="sxs-lookup"><span data-stu-id="35a92-122">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="35a92-123">Metoda `CompileToMethod` aktualizuje obiekt `MethodBuilder` z IL, który reprezentuje skompilowane dane wyjściowe drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="35a92-123">The `CompileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="35a92-124">Należy pamiętać, że `CompileToMethod` jest dostępna tylko w pełnej strukturze pulpitu, a nie w środowisku .NET Core.</span><span class="sxs-lookup"><span data-stu-id="35a92-124">Note that `CompileToMethod` is only available in the full desktop framework, not in the .NET Core.</span></span>

<span data-ttu-id="35a92-125">Opcjonalnie można również udostępnić `DebugInfoGenerator`, które będą otrzymywać informacje o debugowaniu symboli dla wygenerowanego obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="35a92-125">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="35a92-126">Umożliwia to konwertowanie drzewa wyrażenia na obiekt delegata i zawiera pełne informacje o debugowaniu dotyczące wygenerowanego delegata.</span><span class="sxs-lookup"><span data-stu-id="35a92-126">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="35a92-127">Wyrażenie można przekonwertować na delegata przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="35a92-127">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="35a92-128">Należy zauważyć, że typ delegata jest oparty na typie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="35a92-128">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="35a92-129">Musisz znać typ zwracany i listę argumentów, jeśli chcesz użyć obiektu delegata w sposób silnie wpisany.</span><span class="sxs-lookup"><span data-stu-id="35a92-129">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="35a92-130">Metoda `LambdaExpression.Compile()` zwraca typ `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="35a92-130">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="35a92-131">Konieczne będzie przerzutowanie go do poprawnego typu delegata, aby wszystkie narzędzia czasu kompilacji sprawdzają listę argumentów lub typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="35a92-131">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list or return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="35a92-132">Wykonywanie i okresy istnienia</span><span class="sxs-lookup"><span data-stu-id="35a92-132">Execution and Lifetimes</span></span>

<span data-ttu-id="35a92-133">Kod jest wykonywany przez wywoływanie delegata utworzonego podczas wywoływania `LambdaExpression.Compile()`.</span><span class="sxs-lookup"><span data-stu-id="35a92-133">You execute the code by invoking the delegate created when you called `LambdaExpression.Compile()`.</span></span> <span data-ttu-id="35a92-134">Możesz zobaczyć powyższe miejsce, gdzie `add.Compile()` zwraca delegata.</span><span class="sxs-lookup"><span data-stu-id="35a92-134">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="35a92-135">Wywoływanie tego delegata przez wywołanie `func()` wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="35a92-135">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="35a92-136">Ten delegat reprezentuje kod w drzewie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="35a92-136">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="35a92-137">Możesz zachować uchwyt do tego delegata i wywołać go później.</span><span class="sxs-lookup"><span data-stu-id="35a92-137">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="35a92-138">Nie musisz kompilować drzewa wyrażenia za każdym razem, gdy chcesz wykonać kod, który reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="35a92-138">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="35a92-139">(Należy pamiętać, że drzewa wyrażeń są niezmienne i skompilowanie tego samego drzewa wyrażeń później spowoduje utworzenie delegata, który wykonuje ten sam kod).</span><span class="sxs-lookup"><span data-stu-id="35a92-139">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="35a92-140">Będę mieć ostrożność w przypadku tworzenia bardziej zaawansowanych mechanizmów buforowania w celu zwiększenia wydajności poprzez uniknięcie niepotrzebnych wywołań kompilacji.</span><span class="sxs-lookup"><span data-stu-id="35a92-140">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="35a92-141">Porównanie dwóch arbitralnych drzew wyrażeń w celu ustalenia, czy reprezentują one ten sam algorytm, również będzie czasochłonne wykonywanie operacji.</span><span class="sxs-lookup"><span data-stu-id="35a92-141">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="35a92-142">Prawdopodobnie okaże się, że czas obliczeń, który zostanie zapisany, unikając jakichkolwiek dodatkowych wywołań `LambdaExpression.Compile()` będzie większy niż zużyty przez czas wykonywania kodu, który określa dwa różne drzewa wyrażeń wynik ten sam kod wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="35a92-142">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="35a92-143">Zastrzeżenia</span><span class="sxs-lookup"><span data-stu-id="35a92-143">Caveats</span></span>

<span data-ttu-id="35a92-144">Kompilowanie wyrażenia lambda do delegata i wywoływanie tego delegata jest jedną z najprostszych operacji, które można wykonać za pomocą drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="35a92-144">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="35a92-145">Jednak nawet w przypadku tej prostej operacji istnieją zastrzeżenia, których należy wiedzieć.</span><span class="sxs-lookup"><span data-stu-id="35a92-145">However, even with this simple operation, there are caveats you must be aware of.</span></span> 

<span data-ttu-id="35a92-146">Wyrażenia lambda tworzą zamknięcia na wszystkich zmiennych lokalnych, do których istnieją odwołania w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="35a92-146">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="35a92-147">Należy zagwarantować, że wszystkie zmienne, które będą częścią delegata, są użyteczne w lokalizacji, w której jest wywoływana `Compile`, i po wykonaniu wyniku delegowanego.</span><span class="sxs-lookup"><span data-stu-id="35a92-147">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="35a92-148">Ogólnie rzecz biorąc, kompilator zapewni, że jest to prawdziwe.</span><span class="sxs-lookup"><span data-stu-id="35a92-148">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="35a92-149">Jeśli jednak wyrażenie uzyskuje dostęp do zmiennej implementującej `IDisposable`, możliwe jest, że kod może usunąć obiekt, gdy nadal jest przechowywany w drzewie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="35a92-149">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="35a92-150">Na przykład ten kod działa prawidłowo, ponieważ `int` nie implementuje `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="35a92-150">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="35a92-151">Delegat przechwycił odwołanie do zmiennej lokalnej `constant`.</span><span class="sxs-lookup"><span data-stu-id="35a92-151">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="35a92-152">Ta zmienna jest używana w dowolnym momencie później, gdy zostanie wykonana funkcja zwrócona przez `CreateBoundFunc`.</span><span class="sxs-lookup"><span data-stu-id="35a92-152">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="35a92-153">Należy jednak wziąć pod uwagę tę klasę (raczej contrived) implementującą `IDisposable`:</span><span class="sxs-lookup"><span data-stu-id="35a92-153">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

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

<span data-ttu-id="35a92-154">Jeśli używasz go w wyrażeniu, jak pokazano poniżej, uzyskasz `ObjectDisposedException` podczas wykonywania kodu, do którego odwołuje się Właściwość `Resource.Argument`:</span><span class="sxs-lookup"><span data-stu-id="35a92-154">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

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

<span data-ttu-id="35a92-155">Delegat zwrócony z tej metody został zamknięty przez obiekt `constant`, który został usunięty.</span><span class="sxs-lookup"><span data-stu-id="35a92-155">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="35a92-156">(Element został usunięty, ponieważ został zadeklarowany w instrukcji `using`).</span><span class="sxs-lookup"><span data-stu-id="35a92-156">(It's been disposed, because it was declared in a `using` statement.)</span></span> 

<span data-ttu-id="35a92-157">Teraz po wykonaniu delegata zwróconego przez tę metodę będziesz mieć `ObjectDisposedException` zgłoszony w punkcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="35a92-157">Now, when you execute the delegate returned from this method, you'll have a `ObjectDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="35a92-158">Wydaje się, że wystąpił błąd środowiska uruchomieniowego reprezentujący konstrukcję w czasie kompilacji, ale jest to na świecie wprowadzanym podczas pracy z drzewami wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="35a92-158">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="35a92-159">Istnieje wiele permutacji tego problemu, dlatego trudno jest zaoferować ogólne wskazówki, aby tego uniknąć.</span><span class="sxs-lookup"><span data-stu-id="35a92-159">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="35a92-160">Pamiętaj o uzyskiwaniu dostępu do zmiennych lokalnych podczas definiowania wyrażeń i należy `this`zachować ostrożność podczas tworzenia drzewa wyrażenia, które może zostać zwrócone przez publiczny interfejs API.</span><span class="sxs-lookup"><span data-stu-id="35a92-160">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="35a92-161">Kod w wyrażeniu może odwoływać się do metod lub właściwości w innych zestawach.</span><span class="sxs-lookup"><span data-stu-id="35a92-161">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="35a92-162">Ten zestaw musi być dostępny, gdy wyrażenie jest zdefiniowane, a kiedy jest kompilowane, oraz kiedy wywoływany jest otrzymany delegat.</span><span class="sxs-lookup"><span data-stu-id="35a92-162">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="35a92-163">Zostanie osiągnięty `ReferencedAssemblyNotFoundException` w przypadkach, w których nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="35a92-163">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="35a92-164">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="35a92-164">Summary</span></span>

<span data-ttu-id="35a92-165">Drzewa wyrażeń, które reprezentują wyrażenia lambda, można skompilować, aby utworzyć delegata, który można wykonać.</span><span class="sxs-lookup"><span data-stu-id="35a92-165">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="35a92-166">Zapewnia to jeden mechanizm do wykonywania kodu reprezentowanego przez drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="35a92-166">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="35a92-167">Drzewo wyrażenia reprezentuje kod, który będzie wykonywany dla każdej utworzonej konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="35a92-167">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="35a92-168">Tak długo, jak środowisko, w którym kompilujesz i wykonujesz kod, jest zgodne ze środowiskiem, w którym tworzysz wyrażenie, wszystko działa zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="35a92-168">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="35a92-169">Gdy tak się nie stanie, błędy są bardzo przewidywalne i zostaną przechwycone podczas pierwszych testów dowolnego kodu przy użyciu drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="35a92-169">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="35a92-170">Wyrażenia następnej interpretacji</span><span class="sxs-lookup"><span data-stu-id="35a92-170">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)
