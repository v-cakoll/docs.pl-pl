---
title: "Kompilowanie drzew wyrażeń"
description: "Więcej informacji o technikach tworzenia drzewa wyrażeń."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: c0d7bcf6e07f4a49e15e6f6f4e028eebfe82d8bf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="building-expression-trees"></a><span data-ttu-id="38f17-104">Kompilowanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="38f17-104">Building Expression Trees</span></span>

[<span data-ttu-id="38f17-105">Poprzedniej — Interpretowanie wyrażenia</span><span class="sxs-lookup"><span data-stu-id="38f17-105">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="38f17-106">Wszystkie drzewa wyrażeń, które w tym samouczku wykonanej do tej pory zostały utworzone przez kompilator języka C#.</span><span class="sxs-lookup"><span data-stu-id="38f17-106">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="38f17-107">Wszystkie musiał wykonać zostały Tworzenie wyrażenia lambda, która została przypisana do zmiennych wpisanych w formie `Expression<Func<T>>` lub podobnego typu.</span><span class="sxs-lookup"><span data-stu-id="38f17-107">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="38f17-108">To nie jest jedynym sposobem, aby utworzyć drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="38f17-108">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="38f17-109">W różnych scenariuszach może się okazać, że jest potrzebne do tworzenia wyrażenia w pamięci w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="38f17-109">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span> 

<span data-ttu-id="38f17-110">Tworzenie drzewa wyrażeń jest złożona przez fakt, że te drzew wyrażeń są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="38f17-110">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="38f17-111">Trwa niezmienne oznacza, że utworzenie drzewa liści do katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="38f17-111">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="38f17-112">Interfejsy API, zostanie użyta do tworzenia drzewa wyrażeń odzwierciedlają fakt: metody, zostanie użyta do tworzenia węzła przyjmują wszystkie elementy podrzędne jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="38f17-112">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="38f17-113">Przejdźmy kilka przykładów pokazanie technik.</span><span class="sxs-lookup"><span data-stu-id="38f17-113">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="38f17-114">Tworzenie węzłów</span><span class="sxs-lookup"><span data-stu-id="38f17-114">Creating Nodes</span></span>

<span data-ttu-id="38f17-115">Zacznijmy stosunkowo po prostu ponownie.</span><span class="sxs-lookup"><span data-stu-id="38f17-115">Let's start relatively simply again.</span></span> <span data-ttu-id="38f17-116">Użyjemy wyrażenie dodawania I używane w tych sekcjach:</span><span class="sxs-lookup"><span data-stu-id="38f17-116">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="38f17-117">Można utworzyć tego drzewa wyrażenia, należy tworzyć węzłów liści.</span><span class="sxs-lookup"><span data-stu-id="38f17-117">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="38f17-118">Węzły liści są stałe, dzięki czemu można używać `Expression.Constant` metodę w celu utworzenia węzłów:</span><span class="sxs-lookup"><span data-stu-id="38f17-118">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="38f17-119">Następnie będzie Zbuduj wyrażenie dodatku:</span><span class="sxs-lookup"><span data-stu-id="38f17-119">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="38f17-120">Po skonfigurowaniu wyrażenie dodanie można utworzyć wyrażenia lambda:</span><span class="sxs-lookup"><span data-stu-id="38f17-120">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lamdba = Expression.Lambda(addition);
```

<span data-ttu-id="38f17-121">To LambdaExpression bardzo proste, ponieważ zawiera ona żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="38f17-121">This is a very simple LambdaExpression, because it contains no arguments.</span></span>
<span data-ttu-id="38f17-122">Później w tej sekcji, zobaczysz sposób mapowania argumenty parametrów i tworzenie bardziej złożonych.</span><span class="sxs-lookup"><span data-stu-id="38f17-122">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="38f17-123">Wyrażeń, które są tak proste, jak ta mogą łączyć wszystkie wywołania do jednej instrukcji:</span><span class="sxs-lookup"><span data-stu-id="38f17-123">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="38f17-124">Tworzenie drzewa</span><span class="sxs-lookup"><span data-stu-id="38f17-124">Building a Tree</span></span>

<span data-ttu-id="38f17-125">To podstawy tworzenia drzewa wyrażeń w pamięci.</span><span class="sxs-lookup"><span data-stu-id="38f17-125">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="38f17-126">Bardziej złożone drzew zazwyczaj oznacza więcej typów węzłów i większą liczbę węzłów w drzewie.</span><span class="sxs-lookup"><span data-stu-id="38f17-126">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="38f17-127">Teraz uruchomić za pomocą jednego więcej przykład i Pokaż dwóch więcej typy węzłów, które zwykle utworzysz podczas tworzenia drzewa wyrażeń: argument węzłów i węzły wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="38f17-127">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="38f17-128">Utworzymy drzewo wyrażenia, aby utworzyć tego wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="38f17-128">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
<span data-ttu-id="38f17-129">Użytkownik rozpoczyna się przez utworzenie parametr wyrażenia dla `x` i `y`:</span><span class="sxs-lookup"><span data-stu-id="38f17-129">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="38f17-130">Tworzenie wyrażeń mnożenia i dodawania jest zgodny ze wzorcem został już wcześniej:</span><span class="sxs-lookup"><span data-stu-id="38f17-130">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="38f17-131">Następnie należy utworzyć wyrażenie wywołania metody dla wywołania `Math.Sqrt`.</span><span class="sxs-lookup"><span data-stu-id="38f17-131">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="38f17-132">A następnie na koniec, Umieść wywołanie metody do wyrażenia lambda i upewnij się, że do definiowania argumentów do wyrażenia lambda:</span><span class="sxs-lookup"><span data-stu-id="38f17-132">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="38f17-133">W tym przykładzie bardziej skomplikowany zobacz temat kilka więcej techniki, które często będą potrzebne do tworzenia drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="38f17-133">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="38f17-134">Najpierw należy utworzyć obiekty, które reprezentują parametry lub zmienne lokalne przed ich użyciem.</span><span class="sxs-lookup"><span data-stu-id="38f17-134">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="38f17-135">Po utworzeniu tych obiektów, można używać ich w Twojej drzewo wyrażeń, jeśli potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="38f17-135">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="38f17-136">Po drugie, należy użyć podzestawu interfejsów API odbicia do utworzenia `MethodInfo` obiekt, w którym można utworzyć drzewa wyrażeń na dostęp do tej metody.</span><span class="sxs-lookup"><span data-stu-id="38f17-136">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="38f17-137">Należy ograniczyć się do podzestawu interfejsów API odbicia, które są dostępne na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="38f17-137">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="38f17-138">Ponownie te techniki może trwać do innego drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="38f17-138">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="38f17-139">Kompilowanie kodu szczegółowo</span><span class="sxs-lookup"><span data-stu-id="38f17-139">Building Code In Depth</span></span>

<span data-ttu-id="38f17-140">Nie są ograniczone w przypadku można utworzyć za pomocą tych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="38f17-140">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="38f17-141">Jednak bardziej skomplikowane drzewo wyrażeń, który chcesz utworzyć, trudniej kod jest do zarządzania i do odczytu.</span><span class="sxs-lookup"><span data-stu-id="38f17-141">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span> 

<span data-ttu-id="38f17-142">Utworzymy drzewo wyrażenia, który jest odpowiednikiem ten kod:</span><span class="sxs-lookup"><span data-stu-id="38f17-142">Let's build an expression tree that is the equivalent of this code:</span></span>

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

<span data-ttu-id="38f17-143">Powyżej zauważyć, że nie zbudować drzewo wyrażeń, ale po prostu delegata.</span><span class="sxs-lookup"><span data-stu-id="38f17-143">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="38f17-144">Przy użyciu `Expression` klasa, nie można utworzyć instrukcji lambda.</span><span class="sxs-lookup"><span data-stu-id="38f17-144">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="38f17-145">Oto kod, który jest wymagany do kompilacji te same funkcje.</span><span class="sxs-lookup"><span data-stu-id="38f17-145">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="38f17-146">Jest złożona faktem, że nie ma interfejsu API do tworzenia `while` pętli, zamiast tego należy utworzyć pętli, które zawiera test warunkowy i elementem docelowym etykiety w celu wyjścia z pętli.</span><span class="sxs-lookup"><span data-stu-id="38f17-146">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span> 

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

<span data-ttu-id="38f17-147">Kod służący do tworzenia drzewa wyrażenia funkcji silni jest dość nieco dłużej, bardziej skomplikowane i jest on riddled z etykiety i instrukcje break i innymi elementami, które chcielibyśmy uniknąć w naszym codziennie kodowania zadań.</span><span class="sxs-lookup"><span data-stu-id="38f17-147">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span> 

<span data-ttu-id="38f17-148">W tej sekcji również po aktualizacji kodu odwiedzający odwiedź każdy węzeł w drzewie tego wyrażenia i zapisywanie informacji o węzłach, które są tworzone w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="38f17-148">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="38f17-149">Możesz [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/docs/tree/master/samples/csharp/expression-trees) w repozytorium GitHub dotnet/docs.</span><span class="sxs-lookup"><span data-stu-id="38f17-149">You can [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="38f17-150">Eksperymentu dla siebie przez tworzenia i uruchamiania przykładów.</span><span class="sxs-lookup"><span data-stu-id="38f17-150">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="38f17-151">Instrukcje pobrania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="38f17-151">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="38f17-152">Badanie interfejsy API</span><span class="sxs-lookup"><span data-stu-id="38f17-152">Examining the APIs</span></span>

<span data-ttu-id="38f17-153">Drzewo wyrażeń interfejsy API są trudniejsze do nawigacji w .NET Core, ale się.</span><span class="sxs-lookup"><span data-stu-id="38f17-153">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="38f17-154">Ich celem jest raczej złożonych przedsiębiorstwa: pisanie kodu, który generuje kod w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="38f17-154">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="38f17-155">Są one zawsze skomplikowane, aby zapewnić równowagę między obsługi dostępna w języku C# struktury sterujące i utrzymywanie jak uzasadnione powierzchni interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="38f17-155">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="38f17-156">Saldo to oznacza, że wiele struktury sterujące są reprezentowane nie przez ich konstrukcji języka C#, ale przez konstrukcje reprezentujących podstawowej logiki, które kompilator generuje na podstawie tych konstrukcji wyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="38f17-156">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span> 

<span data-ttu-id="38f17-157">Ponadto w tej chwili brak C# wyrażeń, które nie może zostać utworzony bezpośrednio przy użyciu `Expression` metody klasy.</span><span class="sxs-lookup"><span data-stu-id="38f17-157">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="38f17-158">Ogólnie rzecz biorąc będzie to być najnowszej operatory i wyrażenia dodane w języku C# 5 i 6 C#.</span><span class="sxs-lookup"><span data-stu-id="38f17-158">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="38f17-159">(Na przykład `async` wyrażenia nie może zostać utworzony, a nowe `?.` operatora nie można bezpośrednio utworzyć.)</span><span class="sxs-lookup"><span data-stu-id="38f17-159">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="38f17-160">Next — Tłumaczenia wyrażenia</span><span class="sxs-lookup"><span data-stu-id="38f17-160">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
