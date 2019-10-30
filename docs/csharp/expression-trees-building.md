---
title: Kompilowanie drzew wyrażeń
description: Dowiedz się więcej na temat technik tworzenia drzew wyrażeń.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: 45628b00633c8d6ff51dbd5f5dbdda7ca25dd7c4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037091"
---
# <a name="building-expression-trees"></a><span data-ttu-id="df194-103">Kompilowanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="df194-103">Building Expression Trees</span></span>

[<span data-ttu-id="df194-104">Wyrażenia z poprzednią interpretacją</span><span class="sxs-lookup"><span data-stu-id="df194-104">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="df194-105">Wszystkie drzewa wyrażeń, które były już widoczne, zostały utworzone przez C# kompilator.</span><span class="sxs-lookup"><span data-stu-id="df194-105">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="df194-106">Przede wszystkim należało utworzyć wyrażenie lambda, które zostało przypisane do zmiennej wpisanej jako `Expression<Func<T>>` lub innego typu podobnego.</span><span class="sxs-lookup"><span data-stu-id="df194-106">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="df194-107">Nie jest to jedyna metoda tworzenia drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="df194-107">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="df194-108">W przypadku wielu scenariuszy może się okazać, że trzeba utworzyć wyrażenie w pamięci w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="df194-108">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span> 

<span data-ttu-id="df194-109">Kompilowanie drzew wyrażeń jest skomplikowane przez fakt, że te drzewa wyrażeń są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="df194-109">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="df194-110">Niezmienne oznacza, że należy skompilować drzewo od opuszcza do katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="df194-110">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="df194-111">Interfejsy API, które będą używane do tworzenia drzew wyrażeń, odzwierciedlają ten fakt: metody, które będą używane do kompilowania węzła, przyjmują wszystkie jego elementy podrzędne jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="df194-111">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="df194-112">Przechodźmy kilka przykładów, aby wyświetlić te techniki.</span><span class="sxs-lookup"><span data-stu-id="df194-112">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="df194-113">Tworzenie węzłów</span><span class="sxs-lookup"><span data-stu-id="df194-113">Creating Nodes</span></span>

<span data-ttu-id="df194-114">Zacznijmy od samego siebie.</span><span class="sxs-lookup"><span data-stu-id="df194-114">Let's start relatively simply again.</span></span> <span data-ttu-id="df194-115">Użyjemy wyrażenia dodawania, z którym pracujemy w tych sekcjach:</span><span class="sxs-lookup"><span data-stu-id="df194-115">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="df194-116">Aby skonstruować to drzewo wyrażenia, należy skonstruować węzły liścia.</span><span class="sxs-lookup"><span data-stu-id="df194-116">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="df194-117">Węzły liścia są stałymi, więc można użyć metody `Expression.Constant`, aby utworzyć węzły:</span><span class="sxs-lookup"><span data-stu-id="df194-117">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="df194-118">Następnie utworzysz wyrażenie dodawania:</span><span class="sxs-lookup"><span data-stu-id="df194-118">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="df194-119">Po otrzymaniu wyrażenia dodania można utworzyć wyrażenie lambda:</span><span class="sxs-lookup"><span data-stu-id="df194-119">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lambda = Expression.Lambda(addition);
```

<span data-ttu-id="df194-120">Jest to bardzo proste wyrażenie lambda, ponieważ nie zawiera żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="df194-120">This is a very simple lambda expression, because it contains no arguments.</span></span>
<span data-ttu-id="df194-121">W dalszej części tej sekcji zobaczysz sposób mapowania argumentów na parametry i tworzenia bardziej skomplikowanych wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="df194-121">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="df194-122">W przypadku wyrażeń, które są tak proste, można połączyć wszystkie wywołania w pojedynczą instrukcję:</span><span class="sxs-lookup"><span data-stu-id="df194-122">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="df194-123">Kompilowanie drzewa</span><span class="sxs-lookup"><span data-stu-id="df194-123">Building a Tree</span></span>

<span data-ttu-id="df194-124">Jest to podstawą tworzenia drzewa wyrażenia w pamięci.</span><span class="sxs-lookup"><span data-stu-id="df194-124">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="df194-125">Bardziej złożone drzewa zwykle oznaczają więcej typów węzłów i więcej węzłów w drzewie.</span><span class="sxs-lookup"><span data-stu-id="df194-125">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="df194-126">Zacznijmy od jednego przykładu i pokażę dwa typy węzłów, które zwykle utworzysz podczas tworzenia drzew wyrażeń: węzły argumentów i węzły wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="df194-126">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="df194-127">Skompilujmy drzewo wyrażenia, aby utworzyć to wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="df194-127">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
<span data-ttu-id="df194-128">Zacznij od utworzenia wyrażeń parametrów dla `x` i `y`:</span><span class="sxs-lookup"><span data-stu-id="df194-128">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="df194-129">Tworzenie wyrażeń mnożenia i dodawania następuje po wzorcu, który był już widoczny:</span><span class="sxs-lookup"><span data-stu-id="df194-129">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="df194-130">Następnie należy utworzyć wyrażenie wywołania metody dla wywołania do `Math.Sqrt`.</span><span class="sxs-lookup"><span data-stu-id="df194-130">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="df194-131">A następnie na końcu należy umieścić wywołanie metody w wyrażeniu lambda i upewnić się, że argumenty mają być zdefiniowane w wyrażeniu lambda:</span><span class="sxs-lookup"><span data-stu-id="df194-131">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="df194-132">W tym bardziej skomplikowanym przykładzie widać kilka dodatkowych technik, które często są potrzebne do tworzenia drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="df194-132">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="df194-133">Najpierw należy utworzyć obiekty, które reprezentują parametry lub zmienne lokalne przed ich użyciem.</span><span class="sxs-lookup"><span data-stu-id="df194-133">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="df194-134">Po utworzeniu tych obiektów możesz użyć ich w drzewie wyrażenia wszędzie tam, gdzie jest to potrzebne.</span><span class="sxs-lookup"><span data-stu-id="df194-134">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="df194-135">Następnie należy użyć podzestawu interfejsów API odbicia do utworzenia obiektu `MethodInfo`, aby można było utworzyć drzewo wyrażenia, aby uzyskać dostęp do tej metody.</span><span class="sxs-lookup"><span data-stu-id="df194-135">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="df194-136">Musisz ograniczyć się do podzbioru interfejsów API odbicia, które są dostępne na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="df194-136">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="df194-137">Te techniki zostaną rozbudowane do innych drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="df194-137">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="df194-138">Kompilowanie kodu na głębokość</span><span class="sxs-lookup"><span data-stu-id="df194-138">Building Code In Depth</span></span>

<span data-ttu-id="df194-139">Nie masz ograniczeń, co można skompilować za pomocą tych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="df194-139">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="df194-140">Jednak bardziej skomplikowane drzewo wyrażeń, które chcesz skompilować, trudniejsze jest, aby kod był zarządzany i odczytywany.</span><span class="sxs-lookup"><span data-stu-id="df194-140">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span> 

<span data-ttu-id="df194-141">Utwórzmy drzewo wyrażenia, które jest odpowiednikiem tego kodu:</span><span class="sxs-lookup"><span data-stu-id="df194-141">Let's build an expression tree that is the equivalent of this code:</span></span>

```csharp
Func<int, int> factorialFunc = (n) =>
{
    var res = 1;
    while (n > 1)
    {
        res = res * n;
        n--;
    }
    return res;
};
```

<span data-ttu-id="df194-142">Zwróć uwagę na to, że drzewo wyrażenia nie zostało skompilowane, ale po prostu delegat.</span><span class="sxs-lookup"><span data-stu-id="df194-142">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="df194-143">Przy użyciu klasy `Expression` nie można kompilować instrukcji lambda.</span><span class="sxs-lookup"><span data-stu-id="df194-143">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="df194-144">Oto kod, który jest wymagany do skompilowania tych samych funkcji.</span><span class="sxs-lookup"><span data-stu-id="df194-144">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="df194-145">Jest to skomplikowane przez fakt, że nie istnieje interfejs API do kompilowania pętli `while`, zamiast tego należy utworzyć pętlę zawierającą test warunkowy i miejsce docelowe etykiety, aby przerwać pętlę.</span><span class="sxs-lookup"><span data-stu-id="df194-145">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span> 

```csharp
var nArgument = Expression.Parameter(typeof(int), "n");
var result = Expression.Variable(typeof(int), "result");

// Creating a label that represents the return value
LabelTarget label = Expression.Label(typeof(int));

var initializeResult = Expression.Assign(result, Expression.Constant(1));

// This is the inner block that performs the multiplication,
// and decrements the value of 'n'
var block = Expression.Block(
    Expression.Assign(result,
        Expression.Multiply(result, nArgument)),
    Expression.PostDecrementAssign(nArgument)
);

// Creating a method body.
BlockExpression body = Expression.Block(
    new[] { result },
    initializeResult,
    Expression.Loop(
        Expression.IfThenElse(
            Expression.GreaterThan(nArgument, Expression.Constant(1)),
            block,
            Expression.Break(label, result)
        ),
        label
    )
);
```

<span data-ttu-id="df194-146">Kod służący do kompilowania drzewa wyrażeń dla funkcji silniej jest zbyt długi, bardziej skomplikowany i jest riddled przy użyciu etykiet i instrukcji break oraz innych elementów, które chcemy uniknąć w naszych codziennych zadaniach kodowania.</span><span class="sxs-lookup"><span data-stu-id="df194-146">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span> 

<span data-ttu-id="df194-147">W tej sekcji Zaktualizowaliśmy również kod gościa, aby odwiedzić każdy węzeł w tym drzewie wyrażenia i napisać informacje o węzłach, które zostały utworzone w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="df194-147">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="df194-148">Możesz [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) w repozytorium GitHub/docs w serwisie.</span><span class="sxs-lookup"><span data-stu-id="df194-148">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="df194-149">Wypróbuj samodzielnie, kompilując i uruchamiając próbki.</span><span class="sxs-lookup"><span data-stu-id="df194-149">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="df194-150">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="df194-150">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="df194-151">Badanie interfejsów API</span><span class="sxs-lookup"><span data-stu-id="df194-151">Examining the APIs</span></span>

<span data-ttu-id="df194-152">Interfejsy API drzewa wyrażeń są trudniejsze do nawigowania w programie .NET Core, ale jest to odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="df194-152">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="df194-153">Ich celem jest raczej złożone zobowiązanie: pisanie kodu, który generuje kod w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="df194-153">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="df194-154">Są one koniecznie skomplikowane, aby zapewnić równowagę między obsługą wszystkich struktur kontroli dostępnych w C# języku i utrzymywaniem obszaru powierzchni interfejsów API w niewielkim sensie.</span><span class="sxs-lookup"><span data-stu-id="df194-154">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="df194-155">To saldo oznacza, że wiele struktur kontroli nie jest przedstawianych przez ich C# konstrukcje, ale przez konstrukcje, które reprezentują podstawową logikę wygenerowaną przez kompilator z tych konstrukcji wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="df194-155">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span> 

<span data-ttu-id="df194-156">Ponadto w tym momencie istnieją C# wyrażenia, które nie mogą być kompilowane bezpośrednio przy użyciu metod klasy`Expression`.</span><span class="sxs-lookup"><span data-stu-id="df194-156">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="df194-157">Ogólnie rzecz biorąc, są to najnowsze operatory i wyrażenia dodane w C# 5 i C# 6.</span><span class="sxs-lookup"><span data-stu-id="df194-157">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="df194-158">(Na przykład wyrażenia `async` nie mogą być kompilowane i nie można bezpośrednio utworzyć operatora `?.`).</span><span class="sxs-lookup"><span data-stu-id="df194-158">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="df194-159">Następne--tłumaczenie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="df194-159">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
