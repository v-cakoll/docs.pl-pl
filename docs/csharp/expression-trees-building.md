---
title: Tworzenie drzew wyrażeń
description: Dowiedz się więcej o technikach tworzenia drzew wyrażeń.
ms.date: 06/20/2016
ms.assetid: 542754a9-7f40-4293-b299-b9f80241902c
ms.openlocfilehash: 7751af17aafa8e2d1a14125da43352108b1c1f95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646601"
---
# <a name="building-expression-trees"></a><span data-ttu-id="4d110-103">Tworzenie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="4d110-103">Building Expression Trees</span></span>

[<span data-ttu-id="4d110-104">Poprzednie — Interpretowanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="4d110-104">Previous -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)

<span data-ttu-id="4d110-105">Drzewa wyrażeń w tym samouczku do tej pory zostały utworzone przez C# kompilatora.</span><span class="sxs-lookup"><span data-stu-id="4d110-105">All the expression trees you've seen so far have been created by the C# compiler.</span></span> <span data-ttu-id="4d110-106">Wszystkie trzeba było robić zostały, utwórz wyrażenie lambda, która została przypisana do zmiennych wpisanych w formie `Expression<Func<T>>` lub podobne typu.</span><span class="sxs-lookup"><span data-stu-id="4d110-106">All you had to do was create a lambda expression that was assigned to a variable typed as an `Expression<Func<T>>` or some similar type.</span></span> <span data-ttu-id="4d110-107">To nie jest jedynym sposobem, aby utworzyć drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="4d110-107">That's not the only way to create an expression tree.</span></span> <span data-ttu-id="4d110-108">Umożliwia obsługę wielu scenariuszy może się okazać, że potrzebne do tworzenia wyrażenia w pamięci w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4d110-108">For many scenarios you may find that you need to build an expression in memory at runtime.</span></span> 

<span data-ttu-id="4d110-109">Tworzenie drzew wyrażeń jest skomplikowane faktem, że te drzew wyrażeń są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="4d110-109">Building Expression Trees is complicated by the fact that those expression trees are immutable.</span></span> <span data-ttu-id="4d110-110">Trwa niezmienne oznacza, że utworzenie drzewa liści do katalogu głównego.</span><span class="sxs-lookup"><span data-stu-id="4d110-110">Being immutable means that you must build the tree from the leaves up to the root.</span></span> <span data-ttu-id="4d110-111">Interfejsy API, które będą używane do tworzenia drzew wyrażeń odzwierciedla fakt: Metody, które będą używane do tworzenia węzła podjąć wszystkie jego elementy podrzędne jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="4d110-111">The APIs you'll use to build expression trees reflect this fact: The methods you'll use to build a node take all its children as arguments.</span></span> <span data-ttu-id="4d110-112">Przejdźmy przez kilka przykładów, aby pokazać Ci te techniki.</span><span class="sxs-lookup"><span data-stu-id="4d110-112">Let's walk through a few examples to show you the techniques.</span></span>

## <a name="creating-nodes"></a><span data-ttu-id="4d110-113">Tworzenie węzłów</span><span class="sxs-lookup"><span data-stu-id="4d110-113">Creating Nodes</span></span>

<span data-ttu-id="4d110-114">Zacznijmy od stosunkowo po prostu ponownie.</span><span class="sxs-lookup"><span data-stu-id="4d110-114">Let's start relatively simply again.</span></span> <span data-ttu-id="4d110-115">Użyjemy dodawania wprowadzone wyrażenie I masz doświadczenie w pracy z całym następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="4d110-115">We'll use the addition expression I've been working with throughout these sections:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

<span data-ttu-id="4d110-116">Do konstruowania takiego drzewa wyrażeń, należy tworzyć węzły liści.</span><span class="sxs-lookup"><span data-stu-id="4d110-116">To construct that expression tree, you must construct the leaf nodes.</span></span>
<span data-ttu-id="4d110-117">Węzły liści są stałe, aby można było używać `Expression.Constant` metodę w celu utworzenia węzłów:</span><span class="sxs-lookup"><span data-stu-id="4d110-117">The leaf nodes are constants, so you can use the `Expression.Constant` method to create the nodes:</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
```

<span data-ttu-id="4d110-118">Następnie utworzysz wyrażenie dodawania:</span><span class="sxs-lookup"><span data-stu-id="4d110-118">Next, you'll build the addition expression:</span></span>

```csharp
var addition = Expression.Add(one, two);
```

<span data-ttu-id="4d110-119">Gdy już masz, aby wyrażenie dodawania, można utworzyć wyrażenie lambda:</span><span class="sxs-lookup"><span data-stu-id="4d110-119">Once you've got the addition expression, you can create the lambda expression:</span></span>

```csharp
var lambda = Expression.Lambda(addition);
```

<span data-ttu-id="4d110-120">To wyrażenie lambda bardzo proste, ponieważ zawiera ona żadnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="4d110-120">This is a very simple lambda expression, because it contains no arguments.</span></span>
<span data-ttu-id="4d110-121">Później w tej sekcji pokazano, jak do mapowania argumentów do parametrów i tworzenie bardziej złożonych.</span><span class="sxs-lookup"><span data-stu-id="4d110-121">Later in this section, you'll see how to map arguments to parameters and build more complicated expressions.</span></span>

<span data-ttu-id="4d110-122">W wyrażeniach, które są proste, jak ta można połączyć wszystkie wywołania do pojedynczej instrukcji:</span><span class="sxs-lookup"><span data-stu-id="4d110-122">For expressions that are as simple as this one, you may combine all the calls into a single statement:</span></span>

```csharp
var lambda = Expression.Lambda(
    Expression.Add(
        Expression.Constant(1, typeof(int)),
        Expression.Constant(2, typeof(int))
    )
);
```

## <a name="building-a-tree"></a><span data-ttu-id="4d110-123">Tworzenie drzewa</span><span class="sxs-lookup"><span data-stu-id="4d110-123">Building a Tree</span></span>

<span data-ttu-id="4d110-124">To podstawy tworzenia drzewa wyrażeń w pamięci.</span><span class="sxs-lookup"><span data-stu-id="4d110-124">That's the basics of building an expression tree in memory.</span></span> <span data-ttu-id="4d110-125">Bardziej złożone drzewa zazwyczaj oznacza większą liczbę typów węzła i więcej węzłów w drzewie.</span><span class="sxs-lookup"><span data-stu-id="4d110-125">More complex trees generally mean more node types, and more nodes in the tree.</span></span> <span data-ttu-id="4d110-126">Teraz uruchom za pomocą jednego więcej przykład i Pokaż dwa większą liczbę typów węzłów, które będą zwykle tworzysz podczas tworzenia drzew wyrażeń: argument węzłów i węzłów wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="4d110-126">Let's run through one more example and show two more node types that you will typically build when you create expression trees: the argument nodes, and method call nodes.</span></span>

<span data-ttu-id="4d110-127">Utwórzmy drzewo wyrażenia, aby utworzyć to wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="4d110-127">Let's build an expression tree to create this expression:</span></span>

```csharp
Expression<Func<double, double, double>> distanceCalc =
    (x, y) => Math.Sqrt(x * x + y * y);
```
 
<span data-ttu-id="4d110-128">Użytkownik rozpoczyna się przez utworzenie parametr wyrażenia dla `x` i `y`:</span><span class="sxs-lookup"><span data-stu-id="4d110-128">You'll start by creating parameter expressions for `x` and `y`:</span></span>

```csharp
var xParameter = Expression.Parameter(typeof(double), "x");
var yParameter = Expression.Parameter(typeof(double), "y");
```

<span data-ttu-id="4d110-129">Tworzenie wyrażenia mnożenia i dodanie jest zgodna z wzorcem, został już wcześniej:</span><span class="sxs-lookup"><span data-stu-id="4d110-129">Creating the multiplication and addition expressions follows the pattern you've already seen:</span></span>

```csharp
var xSquared = Expression.Multiply(xParameter, xParameter);
var ySquared = Expression.Multiply(yParameter, yParameter);
var sum = Expression.Add(xSquared, ySquared);
```

<span data-ttu-id="4d110-130">Następnie należy utworzyć metodę wyrażenie wywołania do wywołań `Math.Sqrt`.</span><span class="sxs-lookup"><span data-stu-id="4d110-130">Next, you need to create a method call expression for the call to `Math.Sqrt`.</span></span>

```csharp
var sqrtMethod = typeof(Math).GetMethod("Sqrt", new[] { typeof(double) });
var distance = Expression.Call(sqrtMethod, sum);
```

<span data-ttu-id="4d110-131">A następnie na końcu, Umieść wywołanie metody Wyrażenie lambda i upewnij się zdefiniować argumentów do wyrażenia lambda:</span><span class="sxs-lookup"><span data-stu-id="4d110-131">And  then finally, you put the method call into a lambda expression, and make sure to define the arguments to the lambda expression:</span></span>

```csharp
var distanceLambda = Expression.Lambda(
    distance,
    xParameter,
    yParameter);
```

<span data-ttu-id="4d110-132">W tym przykładzie bardziej skomplikowane widzisz kilka więcej technik, które często należy do tworzenia drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="4d110-132">In this more complicated example, you see a couple more techniques that you will often need to create expression trees.</span></span>

<span data-ttu-id="4d110-133">Najpierw musisz utworzyć obiekty, które reprezentują parametry lub zmienne lokalne, przed ich użyciem.</span><span class="sxs-lookup"><span data-stu-id="4d110-133">First, you need to create the objects that represent parameters or local variables before you use them.</span></span> <span data-ttu-id="4d110-134">Po utworzeniu tych obiektów można ich używać w Twojej drzewa wyrażeń wszędzie tam, gdzie należy.</span><span class="sxs-lookup"><span data-stu-id="4d110-134">Once you've created those objects, you can use them in your expression tree wherever you need.</span></span>

<span data-ttu-id="4d110-135">Po drugie, musisz użyć podzestawu interfejsów API odbicia do utworzenia `MethodInfo` obiekt, w którym można utworzyć drzewa wyrażenie na dostęp do tej metody.</span><span class="sxs-lookup"><span data-stu-id="4d110-135">Second, you need to use a subset of the Reflection APIs to create a `MethodInfo` object so that you can create an expression tree to access that method.</span></span> <span data-ttu-id="4d110-136">Trzeba ograniczać się do podzbioru interfejsów API odbicia, które są dostępne na platformie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4d110-136">You must limit yourself to the subset of the Reflection APIs that are available on the .NET Core platform.</span></span> <span data-ttu-id="4d110-137">Ponownie techniki te będą dotyczyć innych drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="4d110-137">Again, these techniques will extend to other expression trees.</span></span>

## <a name="building-code-in-depth"></a><span data-ttu-id="4d110-138">Tworzenie kodu w głębi</span><span class="sxs-lookup"><span data-stu-id="4d110-138">Building Code In Depth</span></span>

<span data-ttu-id="4d110-139">Nie są ograniczone, w jakie możesz tworzyć zawartość przy użyciu tych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="4d110-139">You aren't limited in what you can build using these APIs.</span></span> <span data-ttu-id="4d110-140">Jednak bardziej skomplikowane drzewa wyrażeń, który chcesz skompilować, tym trudniej kod jest do zarządzania i do odczytu.</span><span class="sxs-lookup"><span data-stu-id="4d110-140">However, the more complicated expression tree that you want to build, the more difficult the code is to manage and to read.</span></span> 

<span data-ttu-id="4d110-141">Utwórzmy drzewo wyrażenia, który jest odpowiednikiem tego kodu:</span><span class="sxs-lookup"><span data-stu-id="4d110-141">Let's build an expression tree that is the equivalent of this code:</span></span>

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

<span data-ttu-id="4d110-142">Zwróć uwagę, powyżej, czy nie skompilowano drzewa wyrażeń, ale po prostu delegata.</span><span class="sxs-lookup"><span data-stu-id="4d110-142">Notice above that I did not build the expression tree, but simply the delegate.</span></span> <span data-ttu-id="4d110-143">Za pomocą `Expression` klasy, nie można przeprowadzić kompilacji lambdy instrukcji.</span><span class="sxs-lookup"><span data-stu-id="4d110-143">Using the `Expression` class, you can't build statement lambdas.</span></span> <span data-ttu-id="4d110-144">Poniżej przedstawiono kod, który jest wymagany do kompilowania taką samą funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="4d110-144">Here's the code that is required to build the same functionality.</span></span> <span data-ttu-id="4d110-145">Jest to skomplikowane faktem, że nie ma interfejs API umożliwiający tworzenie `while` pętli, zamiast tego trzeba tworzyć pętli, który zawiera test warunkowy i cel etykiety, aby zerwać pętlę.</span><span class="sxs-lookup"><span data-stu-id="4d110-145">It's complicated by the fact that there isn't an API to build a `while` loop, instead you need to build a loop that contains a conditional test, and a label target to break out of the loop.</span></span> 

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

<span data-ttu-id="4d110-146">Kod, aby zbudować drzewa wyrażeń silni funkcji jest dość to nieco dłużej, bardziej skomplikowane i jest on riddled z etykietami i instrukcji break i inne elementy, które firma Microsoft chce uniknąć w naszym codziennie kodowania zadań.</span><span class="sxs-lookup"><span data-stu-id="4d110-146">The code to build the expression tree for the factorial function is quite a bit longer, more complicated, and it's riddled with labels and break statements and other elements we'd like to avoid in our everyday coding tasks.</span></span> 

<span data-ttu-id="4d110-147">W tej sekcji również po aktualizacji obiektu odwiedzającego kodu do odwiedzenia każdego węzła w tym drzewa wyrażeń i zapisać informacje o węzłach, które są tworzone w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="4d110-147">For this section, I've also updated the visitor code to visit every node in this expression tree and write out information about the nodes that are created in this sample.</span></span> <span data-ttu-id="4d110-148">Możesz [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) w repozytorium dotnet/docs w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="4d110-148">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/csharp/expression-trees) at the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="4d110-149">Poeksperymentuj samodzielnie, tworząc i uruchamianie przykładów programu.</span><span class="sxs-lookup"><span data-stu-id="4d110-149">Experiment for yourself by building and running the samples.</span></span> <span data-ttu-id="4d110-150">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="4d110-150">For download instructions, see [Samples and Tutorials](../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="examining-the-apis"></a><span data-ttu-id="4d110-151">Badanie interfejsów API</span><span class="sxs-lookup"><span data-stu-id="4d110-151">Examining the APIs</span></span>

<span data-ttu-id="4d110-152">Drzewo wyrażenia interfejsy API są niektóre trudniejsze do nawigacji w programie .NET Core, ale jest dobrym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="4d110-152">The expression tree APIs are some of the more difficult to navigate in .NET Core, but that's fine.</span></span> <span data-ttu-id="4d110-153">Ich celem jest raczej złożonych przedsiębiorstwa: pisanie kodu, który generuje kod w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="4d110-153">Their purpose is a rather complex undertaking: writing code that generates code at runtime.</span></span> <span data-ttu-id="4d110-154">Są one zawsze skomplikowane zapewnienie równowagi między Obsługa dostępne w struktur sterujących C# języka i utrzymywanie powierzchni interfejsów API niewielkie jako uzasadnione.</span><span class="sxs-lookup"><span data-stu-id="4d110-154">They are necessarily complicated to provide a balance between supporting all the control structures available in the C# language and keeping the surface area of the APIs as small as reasonable.</span></span> <span data-ttu-id="4d110-155">Saldo to oznacza, że wielu struktur sterowania są reprezentowane nie przez ich C# konstrukcji, ale przez konstrukcji, które reprezentują podstawowej logiki, które kompilator generuje na podstawie tych wyższego poziomu konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="4d110-155">This balance means that many control structures are represented not by their C# constructs, but by constructs that represent the underlying logic that the compiler generates from these higher level constructs.</span></span> 

<span data-ttu-id="4d110-156">W tej chwili istnieje też C# wyrażeń, które nie może zostać utworzony bezpośrednio przy użyciu `Expression` metody klasy.</span><span class="sxs-lookup"><span data-stu-id="4d110-156">Also, at this time, there are C# expressions that cannot be built directly using `Expression` class methods.</span></span> <span data-ttu-id="4d110-157">Ogólnie rzecz biorąc, będą one najnowszych operatory i wyrażenia dodane w C# 5 i C# 6.</span><span class="sxs-lookup"><span data-stu-id="4d110-157">In general, these will be the newest operators and expressions added in C# 5 and C# 6.</span></span> <span data-ttu-id="4d110-158">(Na przykład `async` wyrażenia nie może być kompilowana, a nowe `?.` operator nie można bezpośrednio utworzyć.)</span><span class="sxs-lookup"><span data-stu-id="4d110-158">(For example, `async` expressions cannot be built, and the new `?.` operator cannot be directly created.)</span></span>

[<span data-ttu-id="4d110-159">Dalej — Translacja wyrażeń</span><span class="sxs-lookup"><span data-stu-id="4d110-159">Next -- Translating Expressions</span></span>](expression-trees-translating.md)
