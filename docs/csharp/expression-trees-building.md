---
title: Drzewa wyrażeń budowlanych
description: Dowiedz się więcej o technikach budowania drzew wyrażeń.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: c93eb16ebf2ff66dc0162afb6841f2cadfce174e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146050"
---
# <a name="building-expression-trees"></a><span data-ttu-id="a0f30-103">Drzewa wyrażeń budowlanych</span><span class="sxs-lookup"><span data-stu-id="a0f30-103">Building Expression Trees</span></span>

[<span data-ttu-id="a0f30-104">Poprzedni -- Interpretacja wyrażeń</span><span class="sxs-lookup"><span data-stu-id="a0f30-104">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="a0f30-105">Wszystkie drzewa wyrażeń, które widziałeś do tej pory zostały utworzone przez kompilator C#.</span><span class="sxs-lookup"><span data-stu-id="a0f30-105">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="a0f30-106">Wszystko, co musisz zrobić, to utworzyć wyrażenie lambda, który `Expression<Func<T>>` został przypisany do zmiennej wpisane jako lub podobny typ.</span><span class="sxs-lookup"><span data-stu-id="a0f30-106">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="a0f30-107">To nie jedyny sposób tworzenia drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="a0f30-107">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="a0f30-108">W wielu scenariuszach może się okazać, że należy utworzyć wyrażenie w pamięci w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a0f30-108">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span>

<span data-ttu-id="a0f30-109">Budowanie drzewa wyrażenia jest skomplikowane przez fakt, że te drzewa wyrażeń są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="a0f30-109">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="a0f30-110">Bycie niezmiennym oznacza, że musisz zbudować drzewo od liści do korzenia.</span><span class="sxs-lookup"><span data-stu-id="a0f30-110">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="a0f30-111">Interfejsy API, których użyjesz do tworzenia drzew wyrażeń, odzwierciedlają ten fakt: Metody, których użyjesz do utworzenia węzła, przyjmują wszystkie jego elementy podrzędne jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="a0f30-111">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="a0f30-112">Przejdźmy przez kilka przykładów, aby pokazać techniki.</span><span class="sxs-lookup"><span data-stu-id="a0f30-112">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="a0f30-113">Tworzenie węzłów</span><span class="sxs-lookup"><span data-stu-id="a0f30-113">Creating Nodes</span></span>

<span data-ttu-id="a0f30-114">Zacznijmy stosunkowo po prostu od nowa.</span><span class="sxs-lookup"><span data-stu-id="a0f30-114">Let's start relatively simply again.</span></span> <span data-ttu-id="a0f30-115">Użyjemy wyrażenia dodawania, z którym pracowałem w tych sekcjach:</span><span class="sxs-lookup"><span data-stu-id="a0f30-115">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="a0f30-116">Aby skonstruować to drzewo wyrażeń, należy skonstruować węzły liścia.</span><span class="sxs-lookup"><span data-stu-id="a0f30-116">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="a0f30-117">Węzły liścia są stałymi, dzięki `Expression.Constant` czemu można użyć metody do utworzenia węzłów:</span><span class="sxs-lookup"><span data-stu-id="a0f30-117">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="a0f30-118">Następnie stworzysz wyrażenie dodawania:</span><span class="sxs-lookup"><span data-stu-id="a0f30-118">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="a0f30-119">Po uzyskaniu wyrażenia dodawania można utworzyć wyrażenie lambda:</span><span class="sxs-lookup"><span data-stu-id="a0f30-119">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lambda = Expression.Lambda(addition);
```

<span data-ttu-id="a0f30-120">Jest to bardzo proste wyrażenie lambda, ponieważ nie zawiera żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="a0f30-120">This is a very simple lambda expression, because it contains no arguments.</span></span>
<span data-ttu-id="a0f30-121">W dalszej części tej sekcji zobaczysz, jak mapować argumenty na parametry i tworzyć bardziej skomplikowane wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a0f30-121">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="a0f30-122">W przypadku wyrażeń, które są tak proste, jak ten, można połączyć wszystkie wywołania w jednej instrukcji:</span><span class="sxs-lookup"><span data-stu-id="a0f30-122">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="a0f30-123">Budowanie drzewa</span><span class="sxs-lookup"><span data-stu-id="a0f30-123">Building a Tree</span></span>

<span data-ttu-id="a0f30-124">To podstawy budowania drzewa wyrażeń w pamięci.</span><span class="sxs-lookup"><span data-stu-id="a0f30-124">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="a0f30-125">Bardziej złożone drzewa zazwyczaj oznacza więcej typów węzłów i więcej węzłów w drzewie.</span><span class="sxs-lookup"><span data-stu-id="a0f30-125">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="a0f30-126">Przejdźmy przez jeszcze jeden przykład i pokaż dwa więcej typów węzłów, które zazwyczaj będą tworzyć podczas tworzenia drzew wyrażeń: węzłów argumentów i węzłów wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="a0f30-126">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="a0f30-127">Skompilujmy drzewo wyrażeń, aby utworzyć to wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="a0f30-127">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```

<span data-ttu-id="a0f30-128">Rozpoczniesz od utworzenia wyrażeń parametrów dla `x` i: `y`</span><span class="sxs-lookup"><span data-stu-id="a0f30-128">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="a0f30-129">Tworzenie wyrażeń mnożenia i dodawania jest zgodne z wzorcem, który już widziałeś:</span><span class="sxs-lookup"><span data-stu-id="a0f30-129">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="a0f30-130">Następnie należy utworzyć wyrażenie wywołania metody dla `Math.Sqrt`wywołania .</span><span class="sxs-lookup"><span data-stu-id="a0f30-130">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="a0f30-131">I na koniec, można umieścić wywołanie metody w wyrażeniu lambda i upewnij się, że zdefiniowanie argumentów do wyrażenia lambda:</span><span class="sxs-lookup"><span data-stu-id="a0f30-131">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="a0f30-132">W tym bardziej skomplikowanym przykładzie zobaczysz kilka technik, które często będą potrzebne do utworzenia drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="a0f30-132">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="a0f30-133">Najpierw należy utworzyć obiekty, które reprezentują parametry lub zmienne lokalne przed ich użyciem.</span><span class="sxs-lookup"><span data-stu-id="a0f30-133">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="a0f30-134">Po utworzeniu tych obiektów można ich używać w drzewie wyrażeń w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="a0f30-134">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="a0f30-135">Po drugie, należy użyć podzbioru interfejsów API odbicia, aby utworzyć `MethodInfo` obiekt, aby można było utworzyć drzewo wyrażeń w celu uzyskania dostępu do tej metody.</span><span class="sxs-lookup"><span data-stu-id="a0f30-135">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="a0f30-136">Należy ograniczyć się do podzbioru interfejsów API odbicia, które są dostępne na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a0f30-136">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="a0f30-137">Ponownie, techniki te obejmie inne drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="a0f30-137">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="a0f30-138">Szczegółowy kod budynku</span><span class="sxs-lookup"><span data-stu-id="a0f30-138">Building Code In Depth</span></span>

<span data-ttu-id="a0f30-139">Nie są ograniczone w co można tworzyć przy użyciu tych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="a0f30-139">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="a0f30-140">Jednak bardziej skomplikowane drzewo wyrażeń, które chcesz utworzyć, tym trudniej jest zarządzać i czytać.</span><span class="sxs-lookup"><span data-stu-id="a0f30-140">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span>

<span data-ttu-id="a0f30-141">Skompilujmy drzewo wyrażeń, które jest odpowiednikiem tego kodu:</span><span class="sxs-lookup"><span data-stu-id="a0f30-141">Let's build an expression tree that is the equivalent of this code:</span></span>

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

<span data-ttu-id="a0f30-142">Zauważ powyżej, że nie skompilowałem drzewa wyrażeń, ale po prostu pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="a0f30-142">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="a0f30-143">Za `Expression` pomocą klasy, nie można utworzyć lambdas instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a0f30-143">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="a0f30-144">Oto kod, który jest wymagany do tworzenia tych samych funkcji.</span><span class="sxs-lookup"><span data-stu-id="a0f30-144">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="a0f30-145">Jest to skomplikowane przez fakt, że nie ma interfejsu `while` API do tworzenia pętli, zamiast tego należy utworzyć pętlę, która zawiera test warunkowy i cel etykiety, aby wyrwać się z pętli.</span><span class="sxs-lookup"><span data-stu-id="a0f30-145">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span>

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

<span data-ttu-id="a0f30-146">Kod do tworzenia drzewa wyrażeń dla funkcji faktorii jest nieco dłuższy, bardziej skomplikowany i jest pełen etykiet i instrukcji break i innych elementów, których chcielibyśmy uniknąć w naszych codziennych zadaniach kodowania.</span><span class="sxs-lookup"><span data-stu-id="a0f30-146">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span>

<span data-ttu-id="a0f30-147">W tej sekcji zaktualizowałem również kod odwiedzającego, aby odwiedzić każdy węzeł w tym drzewie wyrażeń i zapisać informacje o węzłach utworzonych w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a0f30-147">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="a0f30-148">Przykładowy kod można [wyświetlić lub pobrać w](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) repozytorium GitHub dotnet/docs.</span><span class="sxs-lookup"><span data-stu-id="a0f30-148">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="a0f30-149">Eksperymentuj dla siebie, budując i uruchamiając próbki.</span><span class="sxs-lookup"><span data-stu-id="a0f30-149">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="a0f30-150">Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="a0f30-150">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="a0f30-151">Badanie interfejsów API</span><span class="sxs-lookup"><span data-stu-id="a0f30-151">Examining the APIs</span></span>

<span data-ttu-id="a0f30-152">Interfejsy API drzewa wyrażeń są jednymi z trudniejszych do nawigowania w .NET Core, ale to dobrze.</span><span class="sxs-lookup"><span data-stu-id="a0f30-152">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="a0f30-153">Ich celem jest dość złożone przedsięwzięcie: pisanie kodu, który generuje kod w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a0f30-153">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="a0f30-154">Są one koniecznie skomplikowane, aby zapewnić równowagę między obsługą wszystkich struktur kontroli dostępnych w języku Języka C# i utrzymanie powierzchni interfejsów API tak małe, jak uzasadnione.</span><span class="sxs-lookup"><span data-stu-id="a0f30-154">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="a0f30-155">Ta równowaga oznacza, że wiele struktur kontroli są reprezentowane nie przez ich konstrukcje C#, ale przez konstrukcje, które reprezentują logikę podstawową, że kompilator generuje z tych konstrukcji wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="a0f30-155">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span>

<span data-ttu-id="a0f30-156">Ponadto w tej chwili istnieją wyrażenia C#, które `Expression` nie mogą być budowane bezpośrednio przy użyciu metod klasy.</span><span class="sxs-lookup"><span data-stu-id="a0f30-156">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="a0f30-157">Ogólnie rzecz biorąc będą to najnowsze operatory i wyrażenia dodane w językach C# 5 i C# 6.</span><span class="sxs-lookup"><span data-stu-id="a0f30-157">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="a0f30-158">(Na przykład `async` wyrażenia nie mogą być `?.` budowane i nie można bezpośrednio utworzyć nowego operatora).</span><span class="sxs-lookup"><span data-stu-id="a0f30-158">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="a0f30-159">Dalej - Tłumaczenie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="a0f30-159">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
