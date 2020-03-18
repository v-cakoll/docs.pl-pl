---
title: Interpretowanie wyrażeń
description: Dowiedz się, jak napisać kod, aby sprawdzić strukturę drzewa wyrażeń.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 1283d7d957c72558652b96cb428efd0f071f0184
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146011"
---
# <a name="interpreting-expressions"></a><span data-ttu-id="3c60c-103">Interpretowanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="3c60c-103">Interpreting Expressions</span></span>

[<span data-ttu-id="3c60c-104">Poprzedni -- Wykonywanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="3c60c-104">Previous -- Executing Expressions</span></span>](expression-trees-execution.md)

<span data-ttu-id="3c60c-105">Teraz napiszmy jakiś kod, aby zbadać strukturę *drzewa wyrażeń*.</span><span class="sxs-lookup"><span data-stu-id="3c60c-105">Now, let's write some code to examine the structure of an *expression tree*.</span></span> <span data-ttu-id="3c60c-106">Każdy węzeł w drzewie wyrażeń będzie obiektem `Expression`klasy, która pochodzi od .</span><span class="sxs-lookup"><span data-stu-id="3c60c-106">Every node in an expression tree will be an object of a class that is derived from `Expression`.</span></span>

<span data-ttu-id="3c60c-107">Ten projekt sprawia, że odwiedzenie wszystkich węzłów w drzewie wyrażeń stosunkowo prostą operacją cykliczną.</span><span class="sxs-lookup"><span data-stu-id="3c60c-107">That design makes visiting all the nodes in an expression tree a relatively straight forward recursive operation.</span></span> <span data-ttu-id="3c60c-108">Ogólną strategią jest rozpoczęcie w węźle głównym i określenie, jaki to rodzaj węzła.</span><span class="sxs-lookup"><span data-stu-id="3c60c-108">The general strategy is to start at the root node and determine what kind of node it is.</span></span>

<span data-ttu-id="3c60c-109">Jeśli typ węzła ma podrzędne, rekursywnie odwiedzić dzieci.</span><span class="sxs-lookup"><span data-stu-id="3c60c-109">If the node type has children, recursively visit the children.</span></span> <span data-ttu-id="3c60c-110">W każdym węźle podrzędny powtórz proces używany w węźle głównym: określ typ, a jeśli typ ma podrzędne, odwiedź każdy z podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="3c60c-110">At each child node, repeat the process used at the root node: determine the type, and if the type has children, visit each of the children.</span></span>

## <a name="examining-an-expression-with-no-children"></a><span data-ttu-id="3c60c-111">Badanie wyrażenia bez dzieci</span><span class="sxs-lookup"><span data-stu-id="3c60c-111">Examining an Expression with No Children</span></span>
<span data-ttu-id="3c60c-112">Zacznijmy od ododwiedzenia każdego węzła w bardzo prostym drzewie wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="3c60c-112">Let's start by visiting each node in a very simple expression tree.</span></span>
<span data-ttu-id="3c60c-113">Oto kod, który tworzy wyrażenie stałe, a następnie sprawdza jego właściwości:</span><span class="sxs-lookup"><span data-stu-id="3c60c-113">Here's the code that creates a constant expression and then examines its properties:</span></span>

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

<span data-ttu-id="3c60c-114">Spowoduje to wydrukowanie następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="3c60c-114">This will print the following:</span></span>

```output
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

<span data-ttu-id="3c60c-115">Teraz napiszmy kod, który zbada to wyrażenie i zapisać kilka ważnych właściwości na jego temat.</span><span class="sxs-lookup"><span data-stu-id="3c60c-115">Now, let's write the code that would examine this expression and write out some important properties about it.</span></span> <span data-ttu-id="3c60c-116">Oto ten kod:</span><span class="sxs-lookup"><span data-stu-id="3c60c-116">Here's that code:</span></span>

## <a name="examining-a-simple-addition-expression"></a><span data-ttu-id="3c60c-117">Badanie prostego wyrażenia dodawania</span><span class="sxs-lookup"><span data-stu-id="3c60c-117">Examining a simple Addition Expression</span></span>

<span data-ttu-id="3c60c-118">Zacznijmy od przykładu dodawania z wprowadzenia do tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="3c60c-118">Let's start with the addition sample from the introduction to this section.</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> <span data-ttu-id="3c60c-119">Nie używam `var` do deklarowania tego drzewa wyrażeń, ponieważ nie jest to możliwe, ponieważ po prawej stronie przypisania jest wpisywany niejawnie.</span><span class="sxs-lookup"><span data-stu-id="3c60c-119">I'm not using `var` to declare this expression tree, as it is not possible because the right-hand side of the assignment is implicitly typed.</span></span> <span data-ttu-id="3c60c-120">Aby zrozumieć to głębiej, przeczytaj [tutaj](implicitly-typed-lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3c60c-120">To understand this more deeply, read [here](implicitly-typed-lambda-expressions.md).</span></span>

<span data-ttu-id="3c60c-121">Węzeł główny jest `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="3c60c-121">The root node is a `LambdaExpression`.</span></span> <span data-ttu-id="3c60c-122">Aby uzyskać interesujący kod po prawej stronie `=>` operatora, musisz znaleźć jedno z dzieci `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="3c60c-122">In order to get the interesting code on the right hand side of the `=>` operator, you need to find one of the children of the `LambdaExpression`.</span></span> <span data-ttu-id="3c60c-123">Zrobimy to ze wszystkimi wyrażeniami w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="3c60c-123">We'll do that with all the expressions in this section.</span></span> <span data-ttu-id="3c60c-124">Węzeł nadrzędny pomaga nam znaleźć typ `LambdaExpression`zwrotu pliku .</span><span class="sxs-lookup"><span data-stu-id="3c60c-124">The parent node does help us find the return type of the `LambdaExpression`.</span></span>

<span data-ttu-id="3c60c-125">Aby sprawdzić każdy węzeł w tym wyrażeniu, musimy cyklicznie odwiedzić kilka węzłów.</span><span class="sxs-lookup"><span data-stu-id="3c60c-125">To examine each node in this expression, we'll need to recursively visit a number of nodes.</span></span> <span data-ttu-id="3c60c-126">Oto prosta pierwsza implementacja:</span><span class="sxs-lookup"><span data-stu-id="3c60c-126">Here's a simple first implementation:</span></span>

```csharp
Expression<Func<int, int, int>> addition = (a, b) => a + b;

Console.WriteLine($"This expression is a {addition.NodeType} expression type");
Console.WriteLine($"The name of the lambda is {((addition.Name == null) ? "<null>" : addition.Name)}");
Console.WriteLine($"The return type is {addition.ReturnType.ToString()}");
Console.WriteLine($"The expression has {addition.Parameters.Count} arguments. They are:");
foreach(var argumentExpression in addition.Parameters)
{
    Console.WriteLine($"\tParameter Type: {argumentExpression.Type.ToString()}, Name: {argumentExpression.Name}");
}

var additionBody = (BinaryExpression)addition.Body;
Console.WriteLine($"The body is a {additionBody.NodeType} expression");
Console.WriteLine($"The left side is a {additionBody.Left.NodeType} expression");
var left = (ParameterExpression)additionBody.Left;
Console.WriteLine($"\tParameter Type: {left.Type.ToString()}, Name: {left.Name}");
Console.WriteLine($"The right side is a {additionBody.Right.NodeType} expression");
var right= (ParameterExpression)additionBody.Right;
Console.WriteLine($"\tParameter Type: {right.Type.ToString()}, Name: {right.Name}");
```

<span data-ttu-id="3c60c-127">W tym przykładzie wydrukowane są następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="3c60c-127">This sample prints the following output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 arguments. They are:
        Parameter Type: System.Int32, Name: a
        Parameter Type: System.Int32, Name: b
The body is a/an Add expression
The left side is a Parameter expression
        Parameter Type: System.Int32, Name: a
The right side is a Parameter expression
        Parameter Type: System.Int32, Name: b
```

<span data-ttu-id="3c60c-128">Zauważysz wiele powtórzeń w przykładzie kodu powyżej.</span><span class="sxs-lookup"><span data-stu-id="3c60c-128">You'll notice a lot of repetition in the code sample above.</span></span>
<span data-ttu-id="3c60c-129">Posprzątajmy to i zbudujmy bardziej ogólnego przeznaczenia użytkownika węzła wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="3c60c-129">Let's clean that up and build a more general purpose expression node visitor.</span></span> <span data-ttu-id="3c60c-130">To będzie wymagać od nas napisania algorytmu rekurencyjnego.</span><span class="sxs-lookup"><span data-stu-id="3c60c-130">That's going to require us to write a recursive algorithm.</span></span> <span data-ttu-id="3c60c-131">Każdy węzeł może być typu, który może mieć podrzędne.</span><span class="sxs-lookup"><span data-stu-id="3c60c-131">Any node could be of a type that might have children.</span></span>
<span data-ttu-id="3c60c-132">Każdy węzeł, który ma dzieci, wymaga od nas odwiedzenia tych dzieci i określenia, czym jest ten węzeł.</span><span class="sxs-lookup"><span data-stu-id="3c60c-132">Any node that has children requires us to visit those children and determine what that node is.</span></span> <span data-ttu-id="3c60c-133">Oto oczyszczona wersja, która wykorzystuje rekursję do odwiedzenia operacji dodawania:</span><span class="sxs-lookup"><span data-stu-id="3c60c-133">Here's the cleaned up version that utilizes recursion to visit the addition operations:</span></span>

```csharp
// Base Visitor class:
public abstract class Visitor
{
    private readonly Expression node;

    protected Visitor(Expression node)
    {
        this.node = node;
    }

    public abstract void Visit(string prefix);

    public ExpressionType NodeType => this.node.NodeType;
    public static Visitor CreateFromExpression(Expression node)
    {
        switch(node.NodeType)
        {
            case ExpressionType.Constant:
                return new ConstantVisitor((ConstantExpression)node);
            case ExpressionType.Lambda:
                return new LambdaVisitor((LambdaExpression)node);
            case ExpressionType.Parameter:
                return new ParameterVisitor((ParameterExpression)node);
            case ExpressionType.Add:
                return new BinaryVisitor((BinaryExpression)node);
            default:
                Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
                return default(Visitor);
        }
    }
}

// Lambda Visitor
public class LambdaVisitor : Visitor
{
    private readonly LambdaExpression node;
    public LambdaVisitor(LambdaExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression type");
        Console.WriteLine($"{prefix}The name of the lambda is {((node.Name == null) ? "<null>" : node.Name)}");
        Console.WriteLine($"{prefix}The return type is {node.ReturnType.ToString()}");
        Console.WriteLine($"{prefix}The expression has {node.Parameters.Count} argument(s). They are:");
        // Visit each parameter:
        foreach (var argumentExpression in node.Parameters)
        {
            var argumentVisitor = Visitor.CreateFromExpression(argumentExpression);
            argumentVisitor.Visit(prefix + "\t");
        }
        Console.WriteLine($"{prefix}The expression body is:");
        // Visit the body:
        var bodyVisitor = Visitor.CreateFromExpression(node.Body);
        bodyVisitor.Visit(prefix + "\t");
    }
}

// Binary Expression Visitor:
public class BinaryVisitor : Visitor
{
    private readonly BinaryExpression node;
    public BinaryVisitor(BinaryExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This binary expression is a {NodeType} expression");
        var left = Visitor.CreateFromExpression(node.Left);
        Console.WriteLine($"{prefix}The Left argument is:");
        left.Visit(prefix + "\t");
        var right = Visitor.CreateFromExpression(node.Right);
        Console.WriteLine($"{prefix}The Right argument is:");
        right.Visit(prefix + "\t");
    }
}

// Parameter visitor:
public class ParameterVisitor : Visitor
{
    private readonly ParameterExpression node;
    public ParameterVisitor(ParameterExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}Type: {node.Type.ToString()}, Name: {node.Name}, ByRef: {node.IsByRef}");
    }
}

// Constant visitor:
public class ConstantVisitor : Visitor
{
    private readonly ConstantExpression node;
    public ConstantVisitor(ConstantExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}The type of the constant value is {node.Type}");
        Console.WriteLine($"{prefix}The value of the constant value is {node.Value}");
    }
}
```

<span data-ttu-id="3c60c-134">Algorytm ten jest podstawą algorytmu, który `LambdaExpression`może odwiedzić dowolne .</span><span class="sxs-lookup"><span data-stu-id="3c60c-134">This algorithm is the basis of an algorithm that can visit any arbitrary `LambdaExpression`.</span></span> <span data-ttu-id="3c60c-135">Istnieje wiele otworów, a mianowicie, że kod, który stworzyłem, szuka tylko bardzo małej próbki możliwych zestawów węzłów drzewa wyrażeń, które może napotkać.</span><span class="sxs-lookup"><span data-stu-id="3c60c-135">There are a lot of holes, namely that the code I created only looks for a very small sample of the possible sets of expression tree nodes that it may encounter.</span></span> <span data-ttu-id="3c60c-136">Jednak nadal można dowiedzieć się sporo od tego, co produkuje.</span><span class="sxs-lookup"><span data-stu-id="3c60c-136">However, you can still learn quite a bit from what it produces.</span></span> <span data-ttu-id="3c60c-137">(Domyślny przypadek w `Visitor.CreateFromExpression` metodzie drukuje komunikat do konsoli błędów po napotkaniu nowego typu węzła.</span><span class="sxs-lookup"><span data-stu-id="3c60c-137">(The default case in the `Visitor.CreateFromExpression` method prints a message to the error console when a new node type is encountered.</span></span> <span data-ttu-id="3c60c-138">W ten sposób wiesz, aby dodać nowy typ wyrażenia.)</span><span class="sxs-lookup"><span data-stu-id="3c60c-138">That way, you know to add a new expression type.)</span></span>

<span data-ttu-id="3c60c-139">Po uruchomieniu tego odwiedzającego na wyrażenie dodawania pokazane powyżej, otrzymasz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="3c60c-139">When you run this visitor on the addition expression shown above, you get the following output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: b, ByRef: False
```

<span data-ttu-id="3c60c-140">Teraz, gdy masz bardziej ogólną implementację odwiedzających, możesz odwiedzić i przetworzyć wiele innych rodzajów wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="3c60c-140">Now that you've built a more general visitor implementation, you can visit and process many more different types of expressions.</span></span>

## <a name="examining-an-addition-expression-with-many-levels"></a><span data-ttu-id="3c60c-141">Badanie wyrażenia dodawania z wieloma poziomami</span><span class="sxs-lookup"><span data-stu-id="3c60c-141">Examining an Addition Expression with Many Levels</span></span>

<span data-ttu-id="3c60c-142">Spróbujmy bardziej skomplikowany przykład, ale nadal ograniczyć typy węzłów tylko do dodawania:</span><span class="sxs-lookup"><span data-stu-id="3c60c-142">Let's try a more complicated example, yet still limit the node types to addition only:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

<span data-ttu-id="3c60c-143">Przed uruchomieniem tego na algorytmie odwiedzającego, spróbuj ćwiczenia myślowego, aby dowiedzieć się, co może być dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="3c60c-143">Before you run this on the visitor algorithm, try a thought exercise to work out what the output might be.</span></span> <span data-ttu-id="3c60c-144">Należy pamiętać, że `+` operator jest *operatorem binarnym:* musi mieć dwoje dzieci, reprezentujących lewe i prawe argumenty.</span><span class="sxs-lookup"><span data-stu-id="3c60c-144">Remember that the `+` operator is a *binary operator*: it must have two children, representing the left and right operands.</span></span> <span data-ttu-id="3c60c-145">Istnieje kilka możliwych sposobów konstruowania drzewa, które mogą być poprawne:</span><span class="sxs-lookup"><span data-stu-id="3c60c-145">There are several possible ways to construct a tree that could be correct:</span></span>

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

<span data-ttu-id="3c60c-146">Możesz zobaczyć separację na dwie możliwe odpowiedzi, aby wyróżnić najbardziej obiecujące.</span><span class="sxs-lookup"><span data-stu-id="3c60c-146">You can see the separation into two possible answers to highlight the most promising.</span></span> <span data-ttu-id="3c60c-147">Pierwszy reprezentuje *prawe wyrażenia asocjacyjne.*</span><span class="sxs-lookup"><span data-stu-id="3c60c-147">The first represents *right associative* expressions.</span></span> <span data-ttu-id="3c60c-148">Drugi reprezentuje *lewych wyrażeń zesychających.*</span><span class="sxs-lookup"><span data-stu-id="3c60c-148">The second represent *left associative* expressions.</span></span>
<span data-ttu-id="3c60c-149">Zaletą obu tych formatów jest to, że format jest skalowany do dowolnej liczby wyrażeń dodawania.</span><span class="sxs-lookup"><span data-stu-id="3c60c-149">The advantage of both of those two formats is that the format scales to any arbitrary number of addition expressions.</span></span>

<span data-ttu-id="3c60c-150">Jeśli to wyrażenie zostanie uruchomione przez odwiedzającego, zobaczysz to dane wyjściowe, sprawdzając, czy proste wyrażenie dodawania *pozostało zesłane.*</span><span class="sxs-lookup"><span data-stu-id="3c60c-150">If you do run this expression through the visitor, you will see this this output, verifying that the simple addition expression is *left associative*.</span></span>

<span data-ttu-id="3c60c-151">Aby uruchomić ten przykład i zobaczyć pełne drzewo wyrażeń, musiałem wprowadzić jedną zmianę do drzewa wyrażeń źródłowych.</span><span class="sxs-lookup"><span data-stu-id="3c60c-151">In order to run this sample, and see the full expression tree, I had to make one change to the source expression tree.</span></span> <span data-ttu-id="3c60c-152">Gdy drzewo wyrażeń zawiera wszystkie stałe, wynikowe `10`drzewo zawiera po prostu stałą wartość .</span><span class="sxs-lookup"><span data-stu-id="3c60c-152">When the expression tree contains all constants, the resulting tree simply contains the constant value of `10`.</span></span> <span data-ttu-id="3c60c-153">Kompilator wykonuje wszystkie dodawanie i zmniejsza wyrażenie do jego najprostszej postaci.</span><span class="sxs-lookup"><span data-stu-id="3c60c-153">The compiler performs all the addition and reduces the expression to its simplest form.</span></span> <span data-ttu-id="3c60c-154">Wystarczy dodać jedną zmienną w wyrażeniu wystarczy, aby zobaczyć oryginalne drzewo:</span><span class="sxs-lookup"><span data-stu-id="3c60c-154">Simply adding one variable in the expression is sufficient to see the original tree:</span></span>

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

<span data-ttu-id="3c60c-155">Utwórz odwiedzającego dla tej sumy i uruchom odwiedzającego zobaczysz to wyjście:</span><span class="sxs-lookup"><span data-stu-id="3c60c-155">Create a visitor for this sum and run the visitor you'll see this output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This binary expression is a Add expression
                        The Left argument is:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                        The Right argument is:
                                This is an Parameter expression type
                                Type: System.Int32, Name: a, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
        The Right argument is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 4
```

<span data-ttu-id="3c60c-156">Można również uruchomić dowolne inne przykłady za pomocą kodu odwiedzającego i zobaczyć, jakie drzewo reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="3c60c-156">You can also run any of the other samples through the visitor code and see what tree it represents.</span></span> <span data-ttu-id="3c60c-157">Oto przykład powyższego `sum3` wyrażenia (z dodatkowym parametrem, aby zapobiec kompilatorowi z obliczania stałej):</span><span class="sxs-lookup"><span data-stu-id="3c60c-157">Here's an example of the `sum3` expression above (with an additional parameter to prevent the compiler from computing the constant):</span></span>

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

<span data-ttu-id="3c60c-158">Oto dane wyjściowe od odwiedzającego:</span><span class="sxs-lookup"><span data-stu-id="3c60c-158">Here's the output from the visitor:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 1
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: b, ByRef: False
```

<span data-ttu-id="3c60c-159">Należy zauważyć, że nawiasy nie są częścią danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="3c60c-159">Notice that the parentheses are not part of the output.</span></span> <span data-ttu-id="3c60c-160">Nie ma węzłów w drzewie wyrażeń, które reprezentują nawiasy w wyrażeniu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="3c60c-160">There are no nodes in the expression tree that represent the parentheses in the input expression.</span></span> <span data-ttu-id="3c60c-161">Struktura drzewa wyrażeń zawiera wszystkie informacje niezbędne do przekazania pierwszeństwa.</span><span class="sxs-lookup"><span data-stu-id="3c60c-161">The structure of the expression tree contains all the information necessary to communicate the precedence.</span></span>

## <a name="extending-from-this-sample"></a><span data-ttu-id="3c60c-162">Rozszerzenie z tego przykładu</span><span class="sxs-lookup"><span data-stu-id="3c60c-162">Extending from this sample</span></span>

<span data-ttu-id="3c60c-163">Przykład dotyczy tylko najbardziej prymitywnych drzew wyrazu.</span><span class="sxs-lookup"><span data-stu-id="3c60c-163">The sample deals with only the most rudimentary expression trees.</span></span> <span data-ttu-id="3c60c-164">Kod, który widzisz w tej sekcji obsługuje tylko stałe liczby `+` całkowite i operator binarny.</span><span class="sxs-lookup"><span data-stu-id="3c60c-164">The code you've seen in this section only handles constant integers and the binary `+` operator.</span></span> <span data-ttu-id="3c60c-165">Jako przykład końcowy zaktualizujmy odwiedzającego, aby obsłużyć bardziej skomplikowane wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="3c60c-165">As a final sample, let's update the visitor to handle a more complicated expression.</span></span> <span data-ttu-id="3c60c-166">Sprawmy, aby to działało w tym zakresie:</span><span class="sxs-lookup"><span data-stu-id="3c60c-166">Let's make it work for this:</span></span>

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ?
    1 :
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

<span data-ttu-id="3c60c-167">Ten kod reprezentuje jedną z możliwych implementacji dla funkcji *matematycznej czynników.*</span><span class="sxs-lookup"><span data-stu-id="3c60c-167">This code represents one possible implementation for the mathematical *factorial* function.</span></span> <span data-ttu-id="3c60c-168">Sposób, w jaki napisałem ten kod, podkreśla dwa ograniczenia budowania drzew wyrażeń, przypisując wyrażenia lambda do wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="3c60c-168">The way I've written this code highlights two limitations of building expression trees by assigning lambda expressions to Expressions.</span></span> <span data-ttu-id="3c60c-169">Po pierwsze, lambdas oświadczenie nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="3c60c-169">First, statement lambdas are not allowed.</span></span> <span data-ttu-id="3c60c-170">Oznacza to, że nie mogę używać pętli, bloków, instrukcji if / else i innych struktur kontroli wspólnych w języku C#.</span><span class="sxs-lookup"><span data-stu-id="3c60c-170">That means I can't use loops, blocks, if / else statements, and other control structures common in C#.</span></span> <span data-ttu-id="3c60c-171">Ograniczam się do używania wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="3c60c-171">I'm limited to using expressions.</span></span> <span data-ttu-id="3c60c-172">Po drugie, nie mogę rekurencyjnego wywołania tego samego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="3c60c-172">Second, I can't recursively call the same expression.</span></span>
<span data-ttu-id="3c60c-173">Mógłbym, gdyby był już delegatem, ale nie mogę go nazwać w formie drzewa wyrazu.</span><span class="sxs-lookup"><span data-stu-id="3c60c-173">I could if it were already a delegate, but I can't call it in its expression tree form.</span></span> <span data-ttu-id="3c60c-174">W sekcji na [budowanie drzew wyrażeń](expression-trees-building.md) nauczysz się technik, aby przezwyciężyć te ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="3c60c-174">In the section on [building expression trees](expression-trees-building.md) you'll learn techniques to overcome these limitations.</span></span>

<span data-ttu-id="3c60c-175">W tym wyrażeniu napotkasz węzły wszystkich tych typów:</span><span class="sxs-lookup"><span data-stu-id="3c60c-175">In this expression, you'll encounter nodes of all these types:</span></span>

1. <span data-ttu-id="3c60c-176">Równe (wyrażenie binarne)</span><span class="sxs-lookup"><span data-stu-id="3c60c-176">Equal (binary expression)</span></span>
2. <span data-ttu-id="3c60c-177">Mnożenie (wyrażenie binarne)</span><span class="sxs-lookup"><span data-stu-id="3c60c-177">Multiply (binary expression)</span></span>
3. <span data-ttu-id="3c60c-178">Warunkowe (?</span><span class="sxs-lookup"><span data-stu-id="3c60c-178">Conditional (the ?</span></span> <span data-ttu-id="3c60c-179">: wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="3c60c-179">: expression)</span></span>
4. <span data-ttu-id="3c60c-180">Wyrażenie wywołania `Range()` metody `Aggregate()`(wywołanie i )</span><span class="sxs-lookup"><span data-stu-id="3c60c-180">Method Call Expression (calling `Range()` and `Aggregate()`)</span></span>

<span data-ttu-id="3c60c-181">Jednym ze sposobów modyfikowania algorytmu odwiedzającego jest kontynuowanie go i `default` pisanie typu węzła za każdym razem, gdy dotrzesz do klauzuli.</span><span class="sxs-lookup"><span data-stu-id="3c60c-181">One way to modify the visitor algorithm is to keep executing it, and write the node type every time you reach your `default` clause.</span></span> <span data-ttu-id="3c60c-182">Po kilku iteracjach zobaczysz każdy z potencjalnych węzłów.</span><span class="sxs-lookup"><span data-stu-id="3c60c-182">After a few iterations, you'll have seen each of the potential nodes.</span></span> <span data-ttu-id="3c60c-183">Następnie masz wszystko, czego potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="3c60c-183">Then, you have all you need.</span></span> <span data-ttu-id="3c60c-184">Wynik byłby mniej więcej taki:</span><span class="sxs-lookup"><span data-stu-id="3c60c-184">The result would be something like this:</span></span>

```csharp
public static Visitor CreateFromExpression(Expression node)
{
    switch(node.NodeType)
    {
        case ExpressionType.Constant:
            return new ConstantVisitor((ConstantExpression)node);
        case ExpressionType.Lambda:
            return new LambdaVisitor((LambdaExpression)node);
        case ExpressionType.Parameter:
            return new ParameterVisitor((ParameterExpression)node);
        case ExpressionType.Add:
        case ExpressionType.Equal:
        case ExpressionType.Multiply:
            return new BinaryVisitor((BinaryExpression)node);
        case ExpressionType.Conditional:
            return new ConditionalVisitor((ConditionalExpression)node);
        case ExpressionType.Call:
            return new MethodCallVisitor((MethodCallExpression)node);
        default:
            Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
            return default(Visitor);
    }
}
```

<span data-ttu-id="3c60c-185">ConditionalVisitor i MethodCallVisitor przetwarzają te dwa węzły:</span><span class="sxs-lookup"><span data-stu-id="3c60c-185">The ConditionalVisitor and MethodCallVisitor process those two nodes:</span></span>

```csharp
public class ConditionalVisitor : Visitor
{
    private readonly ConditionalExpression node;
    public ConditionalVisitor(ConditionalExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        var testVisitor = Visitor.CreateFromExpression(node.Test);
        Console.WriteLine($"{prefix}The Test for this expression is:");
        testVisitor.Visit(prefix + "\t");
        var trueVisitor = Visitor.CreateFromExpression(node.IfTrue);
        Console.WriteLine($"{prefix}The True clause for this expression is:");
        trueVisitor.Visit(prefix + "\t");
        var falseVisitor = Visitor.CreateFromExpression(node.IfFalse);
        Console.WriteLine($"{prefix}The False clause for this expression is:");
        falseVisitor.Visit(prefix + "\t");
    }
}

public class MethodCallVisitor : Visitor
{
    private readonly MethodCallExpression node;
    public MethodCallVisitor(MethodCallExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        if (node.Object == null)
            Console.WriteLine($"{prefix}This is a static method call");
        else
        {
            Console.WriteLine($"{prefix}The receiver (this) is:");
            var receiverVisitor = Visitor.CreateFromExpression(node.Object);
            receiverVisitor.Visit(prefix + "\t");
        }

        var methodInfo = node.Method;
        Console.WriteLine($"{prefix}The method name is {methodInfo.DeclaringType}.{methodInfo.Name}");
        // There is more here, like generic arguments, and so on.
        Console.WriteLine($"{prefix}The Arguments are:");
        foreach(var arg in node.Arguments)
        {
            var argVisitor = Visitor.CreateFromExpression(arg);
            argVisitor.Visit(prefix + "\t");
        }
    }
}
```

<span data-ttu-id="3c60c-186">Dane wyjściowe drzewa wyrażeń będą następujące:</span><span class="sxs-lookup"><span data-stu-id="3c60c-186">And the output for the expression tree would be:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: n, ByRef: False
The expression body is:
        This expression is a Conditional expression
        The Test for this expression is:
                This binary expression is a Equal expression
                The Left argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: n, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 0
        The True clause for this expression is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 1
        The False clause for this expression is:
                This expression is a Call expression
                This is a static method call
                The method name is System.Linq.Enumerable.Aggregate
                The Arguments are:
                        This expression is a Call expression
                        This is a static method call
                        The method name is System.Linq.Enumerable.Range
                        The Arguments are:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                                This is an Parameter expression type
                                Type: System.Int32, Name: n, ByRef: False
                        This expression is a Lambda expression type
                        The name of the lambda is <null>
                        The return type is System.Int32
                        The expression has 2 arguments. They are:
                                This is an Parameter expression type
                                Type: System.Int32, Name: product, ByRef: False
                                This is an Parameter expression type
                                Type: System.Int32, Name: factor, ByRef: False
                        The expression body is:
                                This binary expression is a Multiply expression
                                The Left argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: product, ByRef: False
                                The Right argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: factor, ByRef: False
```

## <a name="extending-the-sample-library"></a><span data-ttu-id="3c60c-187">Rozszerzanie przykładowej biblioteki</span><span class="sxs-lookup"><span data-stu-id="3c60c-187">Extending the Sample Library</span></span>

<span data-ttu-id="3c60c-188">Przykłady w tej sekcji pokazują podstawowych technik do odwiedzenia i zbadania węzłów w drzewie wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="3c60c-188">The samples in this section show the core techniques to visit and examine nodes in an expression tree.</span></span> <span data-ttu-id="3c60c-189">I błyszczące na wiele działań może być konieczne, aby skoncentrować się na podstawowych zadań odwiedzania i uzyskiwania dostępu do węzłów w drzewie wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="3c60c-189">I glossed over many actions you might need in order to concentrate on the core tasks of visiting and accessing nodes in an expression tree.</span></span>

<span data-ttu-id="3c60c-190">Po pierwsze, odwiedzający obsługują tylko stałe, które są liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="3c60c-190">First, the visitors only handle constants that are integers.</span></span> <span data-ttu-id="3c60c-191">Stałe wartości mogą być dowolny inny typ numeryczny, a język C# obsługuje konwersje i promocje między tymi typami.</span><span class="sxs-lookup"><span data-stu-id="3c60c-191">Constant values could be any other numeric type, and the C# language supports conversions and promotions between those types.</span></span> <span data-ttu-id="3c60c-192">Bardziej niezawodna wersja tego kodu będzie odzwierciedlać wszystkie te możliwości.</span><span class="sxs-lookup"><span data-stu-id="3c60c-192">A more robust version of this code would mirror all those capabilities.</span></span>

<span data-ttu-id="3c60c-193">Nawet ostatni przykład rozpoznaje podzbiór możliwych typów węzłów.</span><span class="sxs-lookup"><span data-stu-id="3c60c-193">Even the last example recognizes a subset of the possible node types.</span></span>
<span data-ttu-id="3c60c-194">Nadal można karmić go wiele wyrażeń, które spowoduje, że nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="3c60c-194">You can still feed it many expressions that will cause it to fail.</span></span>
<span data-ttu-id="3c60c-195">Pełna implementacja znajduje się w standardzie <xref:System.Linq.Expressions.ExpressionVisitor> .NET pod nazwą i może obsługiwać wszystkie możliwe typy węzłów.</span><span class="sxs-lookup"><span data-stu-id="3c60c-195">A full implementation is included in the .NET Standard under the name <xref:System.Linq.Expressions.ExpressionVisitor> and can handle all the possible node types.</span></span>

<span data-ttu-id="3c60c-196">Wreszcie, biblioteka użyłem w tym artykule został zbudowany do demonstracji i uczenia się.</span><span class="sxs-lookup"><span data-stu-id="3c60c-196">Finally, the library I used in this article was built for demonstration and learning.</span></span> <span data-ttu-id="3c60c-197">Nie jest zoptymalizowany.</span><span class="sxs-lookup"><span data-stu-id="3c60c-197">It's not optimized.</span></span> <span data-ttu-id="3c60c-198">Napisałem go, aby struktury były bardzo jasne i aby podkreślić techniki używane do odwiedzania węzłów i analizowania tego, co tam jest.</span><span class="sxs-lookup"><span data-stu-id="3c60c-198">I wrote it to make the structures used very clear, and to highlight the techniques used to visit the nodes and analyze what's there.</span></span> <span data-ttu-id="3c60c-199">Implementacja produkcji zwracałaby większą uwagę na wydajność niż ja.</span><span class="sxs-lookup"><span data-stu-id="3c60c-199">A production implementation would pay more attention to performance than I have.</span></span>

<span data-ttu-id="3c60c-200">Nawet z tymi ograniczeniami, powinieneś być na dobrej drodze do pisania algorytmów, które czytają i rozumieją drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="3c60c-200">Even with those limitations, you should be well on your way to writing algorithms that read and understand expression trees.</span></span>

[<span data-ttu-id="3c60c-201">Dalej -- Budowanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="3c60c-201">Next -- Building Expressions</span></span>](expression-trees-building.md)
