---
title: Interpretowanie wyrażeń
description: Dowiedz się, jak napisać kod, aby sprawdzić strukturę drzewa wyrażenia.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 34434a633d866b82da3da713aaecc218c7d35124
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036898"
---
# <a name="interpreting-expressions"></a><span data-ttu-id="6255a-103">Interpretowanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="6255a-103">Interpreting Expressions</span></span>

[<span data-ttu-id="6255a-104">Poprzednie--wykonywanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="6255a-104">Previous -- Executing Expressions</span></span>](expression-trees-execution.md)

<span data-ttu-id="6255a-105">Teraz Napiszmy kod, aby przeanalizować strukturę *drzewa wyrażenia*.</span><span class="sxs-lookup"><span data-stu-id="6255a-105">Now, let's write some code to examine the structure of an *expression tree*.</span></span> <span data-ttu-id="6255a-106">Każdy węzeł w drzewie wyrażenia będzie obiektem klasy, która jest pochodną `Expression`.</span><span class="sxs-lookup"><span data-stu-id="6255a-106">Every node in an expression tree will be an object of a class that is derived from `Expression`.</span></span>

<span data-ttu-id="6255a-107">Ten projekt umożliwia odwiedzanie wszystkich węzłów w drzewie wyrażenia stosunkowo prostej operacji cyklicznej.</span><span class="sxs-lookup"><span data-stu-id="6255a-107">That design makes visiting all the nodes in an expression tree a relatively straight forward recursive operation.</span></span> <span data-ttu-id="6255a-108">Ogólna strategia jest uruchamiana w węźle głównym i decyduje o rodzaju węzła.</span><span class="sxs-lookup"><span data-stu-id="6255a-108">The general strategy is to start at the root node and determine what kind of node it is.</span></span>

<span data-ttu-id="6255a-109">Jeśli typ węzła ma elementy podrzędne, rekursywnie odwiedza elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="6255a-109">If the node type has children, recursively visit the children.</span></span> <span data-ttu-id="6255a-110">W każdym węźle podrzędnym Powtórz proces używany w węźle głównym: Określ typ, a jeśli typ ma elementy podrzędne, zapoznaj się ze wszystkimi elementami podrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="6255a-110">At each child node, repeat the process used at the root node: determine the type, and if the type has children, visit each of the children.</span></span>

## <a name="examining-an-expression-with-no-children"></a><span data-ttu-id="6255a-111">Badanie wyrażenia bez elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="6255a-111">Examining an Expression with No Children</span></span>
<span data-ttu-id="6255a-112">Zacznijmy od odwiedzenia każdego węzła w bardzo prostym drzewie wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="6255a-112">Let's start by visiting each node in a very simple expression tree.</span></span>
<span data-ttu-id="6255a-113">Oto kod, który tworzy wyrażenie stałe, a następnie analizuje jego właściwości:</span><span class="sxs-lookup"><span data-stu-id="6255a-113">Here's the code that creates a constant expression and then examines its properties:</span></span>

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

<span data-ttu-id="6255a-114">Spowoduje to wydrukowanie następujących danych:</span><span class="sxs-lookup"><span data-stu-id="6255a-114">This will print the following:</span></span>

```output
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

<span data-ttu-id="6255a-115">Teraz Napiszmy kod, który będzie przebadał to wyrażenie i napisać kilka ważnych właściwości.</span><span class="sxs-lookup"><span data-stu-id="6255a-115">Now, let's write the code that would examine this expression and write out some important properties about it.</span></span> <span data-ttu-id="6255a-116">Oto kod:</span><span class="sxs-lookup"><span data-stu-id="6255a-116">Here's that code:</span></span>

## <a name="examining-a-simple-addition-expression"></a><span data-ttu-id="6255a-117">Badanie prostego wyrażenia dodawania</span><span class="sxs-lookup"><span data-stu-id="6255a-117">Examining a simple Addition Expression</span></span>

<span data-ttu-id="6255a-118">Zacznijmy od dodania przykładu od wprowadzenia do tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="6255a-118">Let's start with the addition sample from the introduction to this section.</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> <span data-ttu-id="6255a-119">Nie używam `var` do zadeklarować tego drzewa wyrażenia, ponieważ nie jest to możliwe, ponieważ prawa strona przypisania jest niejawnie wpisywana.</span><span class="sxs-lookup"><span data-stu-id="6255a-119">I'm not using `var` to declare this expression tree, as it is not possible because the right-hand side of the assignment is implicitly typed.</span></span> <span data-ttu-id="6255a-120">Więcej informacji można znaleźć [tutaj](implicitly-typed-lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="6255a-120">To understand this more deeply, read [here](implicitly-typed-lambda-expressions.md).</span></span>

<span data-ttu-id="6255a-121">Węzeł główny to `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="6255a-121">The root node is a `LambdaExpression`.</span></span> <span data-ttu-id="6255a-122">Aby uzyskać interesujący kod z prawej strony operatora `=>`, należy znaleźć jeden z elementów podrzędnych `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="6255a-122">In order to get the interesting code on the right hand side of the `=>` operator, you need to find one of the children of the `LambdaExpression`.</span></span> <span data-ttu-id="6255a-123">Wykonamy te czynności ze wszystkimi wyrażeniami w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="6255a-123">We'll do that with all the expressions in this section.</span></span> <span data-ttu-id="6255a-124">Węzeł nadrzędny pomaga nam znaleźć zwracany typ `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="6255a-124">The parent node does help us find the return type of the `LambdaExpression`.</span></span>

<span data-ttu-id="6255a-125">Aby przeanalizować każdy węzeł w tym wyrażeniu, należy rekursywnie odwiedzić liczbę węzłów.</span><span class="sxs-lookup"><span data-stu-id="6255a-125">To examine each node in this expression, we'll need to recursively visit a number of nodes.</span></span> <span data-ttu-id="6255a-126">Oto prosta Pierwsza implementacja:</span><span class="sxs-lookup"><span data-stu-id="6255a-126">Here's a simple first implementation:</span></span>

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

<span data-ttu-id="6255a-127">Ten przykład drukuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="6255a-127">This sample prints the following output:</span></span>

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

<span data-ttu-id="6255a-128">Zobaczysz wiele powtórzeń w przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="6255a-128">You'll notice a lot of repetition in the code sample above.</span></span>
<span data-ttu-id="6255a-129">Wyczyśćmy, jak i kompilować więcej osób odwiedzających węzeł wyrażenia ogólnego przeznaczenia.</span><span class="sxs-lookup"><span data-stu-id="6255a-129">Let's clean that up and build a more general purpose expression node visitor.</span></span> <span data-ttu-id="6255a-130">Ta wartość będzie wymagała zapisania algorytmu cyklicznego.</span><span class="sxs-lookup"><span data-stu-id="6255a-130">That's going to require us to write a recursive algorithm.</span></span> <span data-ttu-id="6255a-131">Dowolny węzeł może być typu, który może mieć elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="6255a-131">Any node could be of a type that might have children.</span></span>
<span data-ttu-id="6255a-132">Każdy węzeł, który ma elementy podrzędne, musi odwiedzać te elementy podrzędne i określić, czym jest ten węzeł.</span><span class="sxs-lookup"><span data-stu-id="6255a-132">Any node that has children requires us to visit those children and determine what that node is.</span></span> <span data-ttu-id="6255a-133">Oto oczyszczona wersja, która wykorzystuje rekursję do odwiedzenia operacji dodawania:</span><span class="sxs-lookup"><span data-stu-id="6255a-133">Here's the cleaned up version that utilizes recursion to visit the addition operations:</span></span>

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

<span data-ttu-id="6255a-134">Ten algorytm jest podstawą algorytmu, który może odwiedzać dowolny `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="6255a-134">This algorithm is the basis of an algorithm that can visit any arbitrary `LambdaExpression`.</span></span> <span data-ttu-id="6255a-135">Istnieje wiele otworów, w tym, że kod, który został utworzony, szuka bardzo małego przykładu możliwych zestawów węzłów drzewa wyrażeń, które może napotkać.</span><span class="sxs-lookup"><span data-stu-id="6255a-135">There are a lot of holes, namely that the code I created only looks for a very small sample of the possible sets of expression tree nodes that it may encounter.</span></span> <span data-ttu-id="6255a-136">Jednak nadal możesz uzyskać nieco informacji o tym, co produkuje.</span><span class="sxs-lookup"><span data-stu-id="6255a-136">However, you can still learn quite a bit from what it produces.</span></span> <span data-ttu-id="6255a-137">(Przypadek domyślny w metodzie `Visitor.CreateFromExpression` drukuje komunikat do konsoli błędów, gdy zostanie napotkany nowy typ węzła.</span><span class="sxs-lookup"><span data-stu-id="6255a-137">(The default case in the `Visitor.CreateFromExpression` method prints a message to the error console when a new node type is encountered.</span></span> <span data-ttu-id="6255a-138">Dzięki temu możesz dodać nowy typ wyrażenia.)</span><span class="sxs-lookup"><span data-stu-id="6255a-138">That way, you know to add a new expression type.)</span></span>

<span data-ttu-id="6255a-139">Po uruchomieniu tego gościa w wyrażeniu dodawania pokazanym powyżej otrzymujesz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="6255a-139">When you run this visitor on the addition expression shown above, you get the following output:</span></span>

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

<span data-ttu-id="6255a-140">Teraz, gdy została skompilowana bardziej ogólna implementacja gościa, można odwiedzać i przetwarzać wiele innych typów wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="6255a-140">Now that you've built a more general visitor implementation, you can visit and process many more different types of expressions.</span></span>

## <a name="examining-an-addition-expression-with-many-levels"></a><span data-ttu-id="6255a-141">Badanie dodawania wyrażenia z wieloma poziomami</span><span class="sxs-lookup"><span data-stu-id="6255a-141">Examining an Addition Expression with Many Levels</span></span>

<span data-ttu-id="6255a-142">Wypróbujmy bardziej skomplikowany przykład, ale nadal ograniczasz typy węzłów tylko do dodawania:</span><span class="sxs-lookup"><span data-stu-id="6255a-142">Let's try a more complicated example, yet still limit the node types to addition only:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

<span data-ttu-id="6255a-143">Przed uruchomieniem tego polecenia w algorytmie odwiedzającym, wypróbuj ćwiczenie, aby obejść dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="6255a-143">Before you run this on the visitor algorithm, try a thought exercise to work out what the output might be.</span></span> <span data-ttu-id="6255a-144">Należy pamiętać, że operator `+` jest *operatorem binarnym*: musi mieć dwa elementy podrzędne, reprezentujący lewy i prawy operand.</span><span class="sxs-lookup"><span data-stu-id="6255a-144">Remember that the `+` operator is a *binary operator*: it must have two children, representing the left and right operands.</span></span> <span data-ttu-id="6255a-145">Istnieje kilka możliwych sposobów konstruowania drzewa, które może być poprawne:</span><span class="sxs-lookup"><span data-stu-id="6255a-145">There are several possible ways to construct a tree that could be correct:</span></span>

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

<span data-ttu-id="6255a-146">Rozdzielenie można zobaczyć na dwie możliwe odpowiedzi, aby wyróżnić najbardziej obiecujące.</span><span class="sxs-lookup"><span data-stu-id="6255a-146">You can see the separation into two possible answers to highlight the most promising.</span></span> <span data-ttu-id="6255a-147">Pierwsze reprezentuje wyrażenia *asocjacyjne z prawej strony* .</span><span class="sxs-lookup"><span data-stu-id="6255a-147">The first represents *right associative* expressions.</span></span> <span data-ttu-id="6255a-148">Druga reprezentuje wyrażenia *asocjacyjne z lewej strony* .</span><span class="sxs-lookup"><span data-stu-id="6255a-148">The second represent *left associative* expressions.</span></span>
<span data-ttu-id="6255a-149">Zaletą obu tych dwóch formatów jest skalowanie do dowolnej dowolnej liczby wyrażeń dodawania.</span><span class="sxs-lookup"><span data-stu-id="6255a-149">The advantage of both of those two formats is that the format scales to any arbitrary number of addition expressions.</span></span> 

<span data-ttu-id="6255a-150">Jeśli to wyrażenie zostanie uruchomione za pomocą gościa, zobaczysz to dane wyjściowe, sprawdzając, czy proste wyrażenie dodawania jest *polewane*.</span><span class="sxs-lookup"><span data-stu-id="6255a-150">If you do run this expression through the visitor, you will see this this output, verifying that the simple addition expression is *left associative*.</span></span> 

<span data-ttu-id="6255a-151">Aby można było uruchomić ten przykład i zobaczyć pełne drzewo wyrażeń, musiałem wprowadzić jedną zmianę w drzewie wyrażenia źródłowego.</span><span class="sxs-lookup"><span data-stu-id="6255a-151">In order to run this sample, and see the full expression tree, I had to make one change to the source expression tree.</span></span> <span data-ttu-id="6255a-152">Gdy drzewo wyrażenia zawiera wszystkie stałe, utworzone drzewo po prostu zawiera stałą wartość `10`.</span><span class="sxs-lookup"><span data-stu-id="6255a-152">When the expression tree contains all constants, the resulting tree simply contains the constant value of `10`.</span></span> <span data-ttu-id="6255a-153">Kompilator wykonuje wszystkie Dodawanie i zmniejsza wyrażenie do najprostszego formularza.</span><span class="sxs-lookup"><span data-stu-id="6255a-153">The compiler performs all the addition and reduces the expression to its simplest form.</span></span> <span data-ttu-id="6255a-154">Po prostu dodanie jednej zmiennej w wyrażeniu jest wystarczające, aby wyświetlić pierwotne drzewo:</span><span class="sxs-lookup"><span data-stu-id="6255a-154">Simply adding one variable in the expression is sufficient to see the original tree:</span></span>

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

<span data-ttu-id="6255a-155">Utwórz osobę odwiedzającą dla tej sumy i uruchom gościa, zobaczysz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="6255a-155">Create a visitor for this sum and run the visitor you'll see this output:</span></span>

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

<span data-ttu-id="6255a-156">Możesz również uruchomić dowolną z innych próbek za pomocą kodu gościa i zobaczyć, jakie drzewo reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="6255a-156">You can also run any of the other samples through the visitor code and see what tree it represents.</span></span> <span data-ttu-id="6255a-157">Oto przykład powyższego wyrażenia `sum3` (z dodatkowym parametrem uniemożliwiającym kompilatorowi Obliczanie stałej):</span><span class="sxs-lookup"><span data-stu-id="6255a-157">Here's an example of the `sum3` expression above (with an additional parameter to prevent the compiler from computing the constant):</span></span>

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

<span data-ttu-id="6255a-158">Oto dane wyjściowe od odwiedzających:</span><span class="sxs-lookup"><span data-stu-id="6255a-158">Here's the output from the visitor:</span></span>

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

<span data-ttu-id="6255a-159">Zauważ, że nawiasy nie są częścią danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="6255a-159">Notice that the parentheses are not part of the output.</span></span> <span data-ttu-id="6255a-160">W drzewie wyrażenia nie ma węzłów, które reprezentują nawiasy w wyrażeniu wejściowym.</span><span class="sxs-lookup"><span data-stu-id="6255a-160">There are no nodes in the expression tree that represent the parentheses in the input expression.</span></span> <span data-ttu-id="6255a-161">Struktura drzewa wyrażenia zawiera wszystkie informacje niezbędne do przekazania pierwszeństwa.</span><span class="sxs-lookup"><span data-stu-id="6255a-161">The structure of the expression tree contains all the information necessary to communicate the precedence.</span></span>

## <a name="extending-from-this-sample"></a><span data-ttu-id="6255a-162">Rozszerzanie z tego przykładu</span><span class="sxs-lookup"><span data-stu-id="6255a-162">Extending from this sample</span></span>

<span data-ttu-id="6255a-163">Przykład dotyczy tylko najbardziej podstawoweych drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="6255a-163">The sample deals with only the most rudimentary expression trees.</span></span> <span data-ttu-id="6255a-164">Kod widziany w tej sekcji obsługuje tylko stałe liczby całkowite i binarny operator `+`.</span><span class="sxs-lookup"><span data-stu-id="6255a-164">The code you've seen in this section only handles constant integers and the binary `+` operator.</span></span> <span data-ttu-id="6255a-165">Jako ostatni przykład zaktualizujmy gościa, aby obsługiwał bardziej skomplikowane wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="6255a-165">As a final sample, let's update the visitor to handle a more complicated expression.</span></span> <span data-ttu-id="6255a-166">Przyjrzyjmy się temu:</span><span class="sxs-lookup"><span data-stu-id="6255a-166">Let's make it work for this:</span></span>

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

<span data-ttu-id="6255a-167">Ten kod reprezentuje jedną możliwą implementację funkcji *silnie* arytmetycznej.</span><span class="sxs-lookup"><span data-stu-id="6255a-167">This code represents one possible implementation for the mathematical *factorial* function.</span></span> <span data-ttu-id="6255a-168">Sposób pisania tego kodu wyróżnia dwa ograniczenia dotyczące kompilowania drzew wyrażeń, przypisując wyrażenia lambda do wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="6255a-168">The way I've written this code highlights two limitations of building expression trees by assigning lambda expressions to Expressions.</span></span> <span data-ttu-id="6255a-169">Najpierw wyrażenia lambda są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="6255a-169">First, statement lambdas are not allowed.</span></span> <span data-ttu-id="6255a-170">Oznacza to, że nie można używać pętli, bloków, instrukcji if/else i innych struktur formantów wspólnych C#w.</span><span class="sxs-lookup"><span data-stu-id="6255a-170">That means I can't use loops, blocks, if / else statements, and other control structures common in C#.</span></span> <span data-ttu-id="6255a-171">Nie mogę używać wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="6255a-171">I'm limited to using expressions.</span></span> <span data-ttu-id="6255a-172">Po drugie nie można rekursywnie wywołać tego samego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="6255a-172">Second, I can't recursively call the same expression.</span></span>
<span data-ttu-id="6255a-173">Mam już delegata, ale nie można go wywołać w jego formularzu drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="6255a-173">I could if it were already a delegate, but I can't call it in its expression tree form.</span></span> <span data-ttu-id="6255a-174">W sekcji dotyczącej [tworzenia drzew wyrażeń](expression-trees-building.md) dowiesz się, jak można przezwyciężyć te ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="6255a-174">In the section on [building expression trees](expression-trees-building.md) you'll learn techniques to overcome these limitations.</span></span>

<span data-ttu-id="6255a-175">W tym wyrażeniu zobaczysz węzły wszystkich następujących typów:</span><span class="sxs-lookup"><span data-stu-id="6255a-175">In this expression, you'll encounter nodes of all these types:</span></span>

1. <span data-ttu-id="6255a-176">Równe (wyrażenie binarne)</span><span class="sxs-lookup"><span data-stu-id="6255a-176">Equal (binary expression)</span></span>
2. <span data-ttu-id="6255a-177">Pomnóż (wyrażenie binarne)</span><span class="sxs-lookup"><span data-stu-id="6255a-177">Multiply (binary expression)</span></span>
3. <span data-ttu-id="6255a-178">Warunkowo (?</span><span class="sxs-lookup"><span data-stu-id="6255a-178">Conditional (the ?</span></span> <span data-ttu-id="6255a-179">wyrażenia</span><span class="sxs-lookup"><span data-stu-id="6255a-179">: expression)</span></span>
4. <span data-ttu-id="6255a-180">Wyrażenie wywołania metody (wywołujące `Range()` i `Aggregate()`)</span><span class="sxs-lookup"><span data-stu-id="6255a-180">Method Call Expression (calling `Range()` and `Aggregate()`)</span></span>

<span data-ttu-id="6255a-181">Jednym ze sposobów modyfikowania algorytmu gościa jest zachowanie go i zapisanie typu węzła za każdym razem, gdy docierasz do klauzuli `default`.</span><span class="sxs-lookup"><span data-stu-id="6255a-181">One way to modify the visitor algorithm is to keep executing it, and write the node type every time you reach your `default` clause.</span></span> <span data-ttu-id="6255a-182">Po kilku iteracjach zobaczysz każdy z potencjalnych węzłów.</span><span class="sxs-lookup"><span data-stu-id="6255a-182">After a few iterations, you'll have seen each of the potential nodes.</span></span> <span data-ttu-id="6255a-183">Następnie masz wszystko, co jest potrzebne.</span><span class="sxs-lookup"><span data-stu-id="6255a-183">Then, you have all you need.</span></span> <span data-ttu-id="6255a-184">Wynik będzie wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="6255a-184">The result would be something like this:</span></span>

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

<span data-ttu-id="6255a-185">Proces ConditionalVisitor i MethodCallVisitor te dwa węzły:</span><span class="sxs-lookup"><span data-stu-id="6255a-185">The ConditionalVisitor and MethodCallVisitor process those two nodes:</span></span>

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

<span data-ttu-id="6255a-186">A dane wyjściowe dla drzewa wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="6255a-186">And the output for the expression tree would be:</span></span>

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

## <a name="extending-the-sample-library"></a><span data-ttu-id="6255a-187">Rozszerzanie biblioteki przykładowej</span><span class="sxs-lookup"><span data-stu-id="6255a-187">Extending the Sample Library</span></span>

<span data-ttu-id="6255a-188">W przykładach w tej sekcji przedstawiono podstawowe techniki do odwiedzania i sprawdzenia węzłów w drzewie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="6255a-188">The samples in this section show the core techniques to visit and examine nodes in an expression tree.</span></span> <span data-ttu-id="6255a-189">Mam wiele akcji, które mogą być potrzebne, aby skoncentrować się na podstawowych zadaniach związanych z odwiedzaniem i uzyskiwaniem dostępu do węzłów w drzewie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="6255a-189">I glossed over many actions you might need in order to concentrate on the core tasks of visiting and accessing nodes in an expression tree.</span></span> 

<span data-ttu-id="6255a-190">Najpierw Goście obsługują tylko stałe, które są liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="6255a-190">First, the visitors only handle constants that are integers.</span></span> <span data-ttu-id="6255a-191">Stałe wartości mogą być dowolnego innego typu liczbowego, a C# język obsługuje konwersje i promocje między tymi typami.</span><span class="sxs-lookup"><span data-stu-id="6255a-191">Constant values could be any other numeric type, and the C# language supports conversions and promotions between those types.</span></span> <span data-ttu-id="6255a-192">Bardziej niezawodna wersja tego kodu będzie dublować wszystkie te funkcje.</span><span class="sxs-lookup"><span data-stu-id="6255a-192">A more robust version of this code would mirror all those capabilities.</span></span>

<span data-ttu-id="6255a-193">Nawet ostatni przykład rozpoznaje podzestaw możliwych typów węzłów.</span><span class="sxs-lookup"><span data-stu-id="6255a-193">Even the last example recognizes a subset of the possible node types.</span></span>
<span data-ttu-id="6255a-194">Nadal można uzyskać wiele wyrażeń, które spowodują niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="6255a-194">You can still feed it many expressions that will cause it to fail.</span></span>
<span data-ttu-id="6255a-195">Pełna implementacja jest uwzględniona w .NET Standard pod nazwą <xref:System.Linq.Expressions.ExpressionVisitor> i może obsługiwać wszystkie możliwe typy węzłów.</span><span class="sxs-lookup"><span data-stu-id="6255a-195">A full implementation is included in the .NET Standard under the name <xref:System.Linq.Expressions.ExpressionVisitor> and can handle all the possible node types.</span></span>

<span data-ttu-id="6255a-196">Na koniec Biblioteka użyta w tym artykule została skompilowana w celu pokazania i uczenia się.</span><span class="sxs-lookup"><span data-stu-id="6255a-196">Finally, the library I used in this article was built for demonstration and learning.</span></span> <span data-ttu-id="6255a-197">Nie została zoptymalizowana.</span><span class="sxs-lookup"><span data-stu-id="6255a-197">It's not optimized.</span></span> <span data-ttu-id="6255a-198">Ja został napisany, aby zapewnić, że struktury są bardzo jasne, i aby wyróżnić techniki używane do odwiedzania węzłów i przeanalizować zawartość.</span><span class="sxs-lookup"><span data-stu-id="6255a-198">I wrote it to make the structures used very clear, and to highlight the techniques used to visit the nodes and analyze what's there.</span></span> <span data-ttu-id="6255a-199">Implementacja produkcyjna zwróci więcej uwagi na wydajność niż mam.</span><span class="sxs-lookup"><span data-stu-id="6255a-199">A production implementation would pay more attention to performance than I have.</span></span>

<span data-ttu-id="6255a-200">Nawet z tymi ograniczeniami, należy być dobrym sposobem pisania algorytmów, które odczytują i opisują drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="6255a-200">Even with those limitations, you should be well on your way to writing algorithms that read and understand expression trees.</span></span>

[<span data-ttu-id="6255a-201">Następne — tworzenie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="6255a-201">Next -- Building Expressions</span></span>](expression-trees-building.md)
