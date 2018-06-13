---
title: Kompilowanie drzew wyrażeń
description: Więcej informacji o technikach tworzenia drzewa wyrażeń.
ms.date: 06/20/2016
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: 52e03bd1ea2635d75da6d70af6918b33b64622b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216317"
---
# <a name="building-expression-trees"></a><span data-ttu-id="42d6e-103">Kompilowanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="42d6e-103">Building Expression Trees</span></span>

[<span data-ttu-id="42d6e-104">Poprzedniej — Interpretowanie wyrażenia</span><span class="sxs-lookup"><span data-stu-id="42d6e-104">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="42d6e-105">Wszystkie drzewa wyrażeń, które w tym samouczku wykonanej do tej pory zostały utworzone przez kompilator języka C#.</span><span class="sxs-lookup"><span data-stu-id="42d6e-105">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="42d6e-106">Wszystkie musiał wykonać zostały Tworzenie wyrażenia lambda, która została przypisana do zmiennych wpisanych w formie `Expression<Func<T>>` lub podobnego typu.</span><span class="sxs-lookup"><span data-stu-id="42d6e-106">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="42d6e-107">To nie jest jedynym sposobem, aby utworzyć drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="42d6e-107">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="42d6e-108">W różnych scenariuszach może się okazać, że jest potrzebne do tworzenia wyrażenia w pamięci w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="42d6e-108">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span> 

<span data-ttu-id="42d6e-109">Tworzenie drzewa wyrażeń jest złożona przez fakt, że te drzew wyrażeń są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="42d6e-109">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="42d6e-110">Trwa niezmienne oznacza, że utworzenie drzewa liści do katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="42d6e-110">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="42d6e-111">Interfejsy API, zostanie użyta do tworzenia drzewa wyrażeń odzwierciedlają fakt: metody, zostanie użyta do tworzenia węzła przyjmują wszystkie elementy podrzędne jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="42d6e-111">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="42d6e-112">Przejdźmy kilka przykładów pokazanie technik.</span><span class="sxs-lookup"><span data-stu-id="42d6e-112">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="42d6e-113">Tworzenie węzłów</span><span class="sxs-lookup"><span data-stu-id="42d6e-113">Creating Nodes</span></span>

<span data-ttu-id="42d6e-114">Zacznijmy stosunkowo po prostu ponownie.</span><span class="sxs-lookup"><span data-stu-id="42d6e-114">Let's start relatively simply again.</span></span> <span data-ttu-id="42d6e-115">Użyjemy wyrażenie dodawania I używane w tych sekcjach:</span><span class="sxs-lookup"><span data-stu-id="42d6e-115">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="42d6e-116">Można utworzyć tego drzewa wyrażenia, należy tworzyć węzłów liści.</span><span class="sxs-lookup"><span data-stu-id="42d6e-116">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="42d6e-117">Węzły liści są stałe, dzięki czemu można używać `Expression.Constant` metodę w celu utworzenia węzłów:</span><span class="sxs-lookup"><span data-stu-id="42d6e-117">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="42d6e-118">Następnie będzie Zbuduj wyrażenie dodatku:</span><span class="sxs-lookup"><span data-stu-id="42d6e-118">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="42d6e-119">Po skonfigurowaniu wyrażenie dodanie można utworzyć wyrażenia lambda:</span><span class="sxs-lookup"><span data-stu-id="42d6e-119">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lamdba = Expression.Lambda(addition);
```

<span data-ttu-id="42d6e-120">To LambdaExpression bardzo proste, ponieważ zawiera ona żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="42d6e-120">This is a very simple LambdaExpression, because it contains no arguments.</span></span>
<span data-ttu-id="42d6e-121">Później w tej sekcji, zobaczysz sposób mapowania argumenty parametrów i tworzenie bardziej złożonych.</span><span class="sxs-lookup"><span data-stu-id="42d6e-121">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="42d6e-122">Wyrażeń, które są tak proste, jak ta mogą łączyć wszystkie wywołania do jednej instrukcji:</span><span class="sxs-lookup"><span data-stu-id="42d6e-122">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="42d6e-123">Tworzenie drzewa</span><span class="sxs-lookup"><span data-stu-id="42d6e-123">Building a Tree</span></span>

<span data-ttu-id="42d6e-124">To podstawy tworzenia drzewa wyrażeń w pamięci.</span><span class="sxs-lookup"><span data-stu-id="42d6e-124">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="42d6e-125">Bardziej złożone drzew zazwyczaj oznacza więcej typów węzłów i większą liczbę węzłów w drzewie.</span><span class="sxs-lookup"><span data-stu-id="42d6e-125">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="42d6e-126">Teraz uruchomić za pomocą jednego więcej przykład i Pokaż dwóch więcej typy węzłów, które zwykle utworzysz podczas tworzenia drzewa wyrażeń: argument węzłów i węzły wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="42d6e-126">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="42d6e-127">Utworzymy drzewo wyrażenia, aby utworzyć tego wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="42d6e-127">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
<span data-ttu-id="42d6e-128">Użytkownik rozpoczyna się przez utworzenie parametr wyrażenia dla `x` i `y`:</span><span class="sxs-lookup"><span data-stu-id="42d6e-128">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="42d6e-129">Tworzenie wyrażeń mnożenia i dodawania jest zgodny ze wzorcem został już wcześniej:</span><span class="sxs-lookup"><span data-stu-id="42d6e-129">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="42d6e-130">Następnie należy utworzyć wyrażenie wywołania metody dla wywołania `Math.Sqrt`.</span><span class="sxs-lookup"><span data-stu-id="42d6e-130">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="42d6e-131">A następnie na koniec, Umieść wywołanie metody do wyrażenia lambda i upewnij się, że do definiowania argumentów do wyrażenia lambda:</span><span class="sxs-lookup"><span data-stu-id="42d6e-131">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="42d6e-132">W tym przykładzie bardziej skomplikowany zobacz temat kilka więcej techniki, które często będą potrzebne do tworzenia drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="42d6e-132">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="42d6e-133">Najpierw należy utworzyć obiekty, które reprezentują parametry lub zmienne lokalne przed ich użyciem.</span><span class="sxs-lookup"><span data-stu-id="42d6e-133">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="42d6e-134">Po utworzeniu tych obiektów, można używać ich w Twojej drzewo wyrażeń, jeśli potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="42d6e-134">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="42d6e-135">Po drugie, należy użyć podzestawu interfejsów API odbicia do utworzenia `MethodInfo` obiekt, w którym można utworzyć drzewa wyrażeń na dostęp do tej metody.</span><span class="sxs-lookup"><span data-stu-id="42d6e-135">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="42d6e-136">Należy ograniczyć się do podzestawu interfejsów API odbicia, które są dostępne na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="42d6e-136">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="42d6e-137">Ponownie te techniki może trwać do innego drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="42d6e-137">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="42d6e-138">Kompilowanie kodu szczegółowo</span><span class="sxs-lookup"><span data-stu-id="42d6e-138">Building Code In Depth</span></span>

<span data-ttu-id="42d6e-139">Nie są ograniczone w przypadku można utworzyć za pomocą tych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="42d6e-139">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="42d6e-140">Jednak bardziej skomplikowane drzewo wyrażeń, który chcesz utworzyć, trudniej kod jest do zarządzania i do odczytu.</span><span class="sxs-lookup"><span data-stu-id="42d6e-140">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span> 

<span data-ttu-id="42d6e-141">Utworzymy drzewo wyrażenia, który jest odpowiednikiem ten kod:</span><span class="sxs-lookup"><span data-stu-id="42d6e-141">Let's build an expression tree that is the equivalent of this code:</span></span>

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

<span data-ttu-id="42d6e-142">Powyżej zauważyć, że nie zbudować drzewo wyrażeń, ale po prostu delegata.</span><span class="sxs-lookup"><span data-stu-id="42d6e-142">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="42d6e-143">Przy użyciu `Expression` klasa, nie można utworzyć instrukcji lambda.</span><span class="sxs-lookup"><span data-stu-id="42d6e-143">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="42d6e-144">Oto kod, który jest wymagany do kompilacji te same funkcje.</span><span class="sxs-lookup"><span data-stu-id="42d6e-144">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="42d6e-145">Jest złożona faktem, że nie ma interfejsu API do tworzenia `while` pętli, zamiast tego należy utworzyć pętli, które zawiera test warunkowy i elementem docelowym etykiety w celu wyjścia z pętli.</span><span class="sxs-lookup"><span data-stu-id="42d6e-145">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span> 

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

<span data-ttu-id="42d6e-146">Kod służący do tworzenia drzewa wyrażenia funkcji silni jest dość nieco dłużej, bardziej skomplikowane i jest on riddled z etykiety i instrukcje break i innymi elementami, które chcielibyśmy uniknąć w naszym codziennie kodowania zadań.</span><span class="sxs-lookup"><span data-stu-id="42d6e-146">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span> 

<span data-ttu-id="42d6e-147">W tej sekcji również po aktualizacji kodu odwiedzający odwiedź każdy węzeł w drzewie tego wyrażenia i zapisywanie informacji o węzłach, które są tworzone w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="42d6e-147">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="42d6e-148">Możesz [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) w repozytorium GitHub dotnet/docs.</span><span class="sxs-lookup"><span data-stu-id="42d6e-148">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="42d6e-149">Eksperymentu dla siebie przez tworzenia i uruchamiania przykładów.</span><span class="sxs-lookup"><span data-stu-id="42d6e-149">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="42d6e-150">Instrukcje pobrania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="42d6e-150">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="42d6e-151">Badanie interfejsy API</span><span class="sxs-lookup"><span data-stu-id="42d6e-151">Examining the APIs</span></span>

<span data-ttu-id="42d6e-152">Drzewo wyrażeń interfejsy API są trudniejsze do nawigacji w .NET Core, ale się.</span><span class="sxs-lookup"><span data-stu-id="42d6e-152">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="42d6e-153">Ich celem jest raczej złożonych przedsiębiorstwa: pisanie kodu, który generuje kod w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="42d6e-153">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="42d6e-154">Są one zawsze skomplikowane, aby zapewnić równowagę między obsługi dostępna w języku C# struktury sterujące i utrzymywanie jak uzasadnione powierzchni interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="42d6e-154">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="42d6e-155">Saldo to oznacza, że wiele struktury sterujące są reprezentowane nie przez ich konstrukcji języka C#, ale przez konstrukcje reprezentujących podstawowej logiki, które kompilator generuje na podstawie tych konstrukcji wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="42d6e-155">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span> 

<span data-ttu-id="42d6e-156">Ponadto w tej chwili brak C# wyrażeń, które nie może zostać utworzony bezpośrednio przy użyciu `Expression` metody klasy.</span><span class="sxs-lookup"><span data-stu-id="42d6e-156">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="42d6e-157">Ogólnie rzecz biorąc będzie to być najnowszej operatory i wyrażenia dodane w języku C# 5 i 6 C#.</span><span class="sxs-lookup"><span data-stu-id="42d6e-157">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="42d6e-158">(Na przykład `async` wyrażenia nie może zostać utworzony, a nowe `?.` operatora nie można bezpośrednio utworzyć.)</span><span class="sxs-lookup"><span data-stu-id="42d6e-158">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="42d6e-159">Next — Tłumaczenia wyrażenia</span><span class="sxs-lookup"><span data-stu-id="42d6e-159">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
