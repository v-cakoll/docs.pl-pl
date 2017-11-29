---
title: "Interpretowanie wyrażenia"
description: "Dowiedz się, jak napisać kod, aby zbadać struktura drzewa wyrażenia."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: e7c5f7404546c6f3812fc5cc3d0320c77816634d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="interpreting-expressions"></a><span data-ttu-id="54e1b-104">Interpretowanie wyrażenia</span><span class="sxs-lookup"><span data-stu-id="54e1b-104">Interpreting Expressions</span></span>

[<span data-ttu-id="54e1b-105">Poprzednie — Wykonywania wyrażenia</span><span class="sxs-lookup"><span data-stu-id="54e1b-105">Previous -- Executing Expressions</span></span>](expression-trees-execution.md)

<span data-ttu-id="54e1b-106">Teraz napisz kod służący do zbadania struktury *drzewo wyrażeń*.</span><span class="sxs-lookup"><span data-stu-id="54e1b-106">Now, let's write some code to examine the structure of an *expression tree*.</span></span> <span data-ttu-id="54e1b-107">Każdy węzeł w drzewie wyrażenie będzie obiektu klasy, która jest pochodną `Expression`.</span><span class="sxs-lookup"><span data-stu-id="54e1b-107">Every node in an expression tree will be an object of a class that is derived from `Expression`.</span></span>

<span data-ttu-id="54e1b-108">Ten projekt sprawia, że odwiedzający wszystkie węzły na drzewo wyrażenia operacji cyklicznej względnie proste do przodu.</span><span class="sxs-lookup"><span data-stu-id="54e1b-108">That design makes visiting all the nodes in an expression tree a relatively straight forward recursive operation.</span></span> <span data-ttu-id="54e1b-109">Ogólne strategii jest rozpocząć od węzła głównego i ustalić, jakiego rodzaju węzła jest.</span><span class="sxs-lookup"><span data-stu-id="54e1b-109">The general strategy is to start at the root node and determine what kind of node it is.</span></span>

<span data-ttu-id="54e1b-110">Jeśli typ węzła ma elementy podrzędne, rekursywnie odwiedzać elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="54e1b-110">If the node type has children, recursively visit the children.</span></span> <span data-ttu-id="54e1b-111">W każdym węźle podrzędnych to wielokrotnie, używane w węźle głównym: Określ typ, a jeśli typ ma elementy podrzędne, odwiedź każdego elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="54e1b-111">At each child node, repeat the process used at the root node: determine the type, and if the type has children, visit each of the children.</span></span>

## <a name="examining-an-expression-with-no-children"></a><span data-ttu-id="54e1b-112">Badanie wyrażenia bez elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="54e1b-112">Examining an Expression with No Children</span></span>
<span data-ttu-id="54e1b-113">Zacznijmy od odwiedzający każdy węzeł w drzewie bardzo proste wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="54e1b-113">Let's start by visiting each node in a very simple expression tree.</span></span>
<span data-ttu-id="54e1b-114">Oto kod, który tworzy wyrażenie stałe, a następnie sprawdza, czy jego właściwości:</span><span class="sxs-lookup"><span data-stu-id="54e1b-114">Here's the code that creates a constant expression and then examines its properties:</span></span>

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

<span data-ttu-id="54e1b-115">Będzie drukować następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="54e1b-115">This will print the following:</span></span>

```
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

<span data-ttu-id="54e1b-116">Teraz napisz kod, który będzie zbadać tego wyrażenia i zapisać niektórych właściwości ważnych informacji na ten temat.</span><span class="sxs-lookup"><span data-stu-id="54e1b-116">Now, let's write the code that would examine this expression and write out some important properties about it.</span></span> <span data-ttu-id="54e1b-117">Oto kod:</span><span class="sxs-lookup"><span data-stu-id="54e1b-117">Here's that code:</span></span>

## <a name="examining-a-simple-addition-expression"></a><span data-ttu-id="54e1b-118">Badanie proste wyrażenie dodanie</span><span class="sxs-lookup"><span data-stu-id="54e1b-118">Examining a simple Addition Expression</span></span>

<span data-ttu-id="54e1b-119">Zacznijmy od próbki dodanie z wprowadzenie do tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="54e1b-119">Let's start with the addition sample from the introduction to this section.</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> <span data-ttu-id="54e1b-120">Nie używam `var` można zadeklarować tego drzewa wyrażenia, ponieważ nie jest możliwe ponieważ prawa strona przypisania jest niejawnie wpisanych.</span><span class="sxs-lookup"><span data-stu-id="54e1b-120">I'm not using `var` to declare this expression tree, as it is not possible because the right-hand side of the assignment is implicitly typed.</span></span> <span data-ttu-id="54e1b-121">Aby głębsze to zrozumieć, przeczytaj [tutaj](implicitly-typed-lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="54e1b-121">To understand this more deeply, read [here](implicitly-typed-lambda-expressions.md).</span></span>

<span data-ttu-id="54e1b-122">Węzeł główny jest `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="54e1b-122">The root node is a `LambdaExpression`.</span></span> <span data-ttu-id="54e1b-123">Aby uzyskać po prawej stronie interesującego kodu `=>` operatora, należy znaleźć jednego z elementów podrzędnych `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="54e1b-123">In order to get the interesting code on the right hand side of the `=>` operator, you need to find one of the children of the `LambdaExpression`.</span></span> <span data-ttu-id="54e1b-124">Firma Microsoft zrobić z wszystkie wyrażenia w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="54e1b-124">We'll do that with all the expressions in this section.</span></span> <span data-ttu-id="54e1b-125">Węzeł nadrzędny Pomóż nam Znajdź typ zwracany `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="54e1b-125">The parent node does help us find the return type of the `LambdaExpression`.</span></span>

<span data-ttu-id="54e1b-126">Do sprawdzenia każdego węzła w tym wyrażeniu, firma Microsoft będzie konieczne aby rekursywnie odwiedź stronę liczba węzłów.</span><span class="sxs-lookup"><span data-stu-id="54e1b-126">To examine each node in this expression, we'll need to recursively visit a number of nodes.</span></span> <span data-ttu-id="54e1b-127">Oto prosty implementacji pierwszy:</span><span class="sxs-lookup"><span data-stu-id="54e1b-127">Here's a simple first implementation:</span></span>

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

<span data-ttu-id="54e1b-128">W tym przykładzie drukowane następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="54e1b-128">This sample prints the following output:</span></span>

```
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

<span data-ttu-id="54e1b-129">Można zauważyć aktualnymi w powyższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="54e1b-129">You'll notice a lot of repetition in the code sample above.</span></span>
<span data-ttu-id="54e1b-130">Umożliwia czyszczenie który i tworzenie bardziej ogólnego przeznaczenia osoba odwiedzająca węzła wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="54e1b-130">Let's clean that up and build a more general purpose expression node visitor.</span></span> <span data-ttu-id="54e1b-131">Który będzie wymagają firmie Microsoft w celu zapisu algorytmu cyklicznego.</span><span class="sxs-lookup"><span data-stu-id="54e1b-131">That's going to require us to write a recursive algorithm.</span></span> <span data-ttu-id="54e1b-132">Dowolny węzeł może być typu, który może mieć elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="54e1b-132">Any node could be of a type that might have children.</span></span>
<span data-ttu-id="54e1b-133">Żaden węzeł, który ma elementy podrzędne musimy odwiedź te elementy podrzędne, a następnie określenie tego węzła.</span><span class="sxs-lookup"><span data-stu-id="54e1b-133">Any node that has children requires us to visit those children and determine what that node is.</span></span> <span data-ttu-id="54e1b-134">Oto oczyszczony zapasowej wersji, która używa rekursji do odwiedzenia operacje dodawania:</span><span class="sxs-lookup"><span data-stu-id="54e1b-134">Here's the cleaned up version that utilizes recursion to visit the addition operations:</span></span>

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

<span data-ttu-id="54e1b-135">Ten algorytm stanowi podstawę algorytmu, które mogą odwiedzać dowolny dowolnych `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="54e1b-135">This algorithm is the basis of an algorithm that can visit any arbitrary `LambdaExpression`.</span></span> <span data-ttu-id="54e1b-136">Istnieje wiele luk, czyli kod utworzoną tylko wygląda bardzo małych przykładowe możliwe zestawy węzły drzewa wyrażenia, które może on wystąpić.</span><span class="sxs-lookup"><span data-stu-id="54e1b-136">There are a lot of holes, namely that the code I created only looks for a very small sample of the possible sets of expression tree nodes that it may encounter.</span></span> <span data-ttu-id="54e1b-137">Jednak można wciąż uzyskać dość nieco z go tworzy.</span><span class="sxs-lookup"><span data-stu-id="54e1b-137">However, you can still learn quite a bit from what it produces.</span></span> <span data-ttu-id="54e1b-138">(W przypadku domyślnej `Visitor.CreateFromExpression` metoda wyświetla komunikat do konsoli błąd po napotkaniu nowego typu węzła.</span><span class="sxs-lookup"><span data-stu-id="54e1b-138">(The default case in the `Visitor.CreateFromExpression` method prints a message to the error console when a new node type is encountered.</span></span> <span data-ttu-id="54e1b-139">W ten sposób wiesz, aby dodać nowy typ wyrażenia.)</span><span class="sxs-lookup"><span data-stu-id="54e1b-139">That way, you know to add a new expression type.)</span></span>

<span data-ttu-id="54e1b-140">Po uruchomieniu tego obiektu odwiedzającego na wyrażeniu dodanie pokazanym powyżej można uzyskać następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="54e1b-140">When you run this visitor on the addition expression shown above, you get the following output:</span></span>

```
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

<span data-ttu-id="54e1b-141">Teraz, bardziej ogólne implementacji obiektu odwiedzającego został utworzony, można odwiedź i przetwarzać więcej różnego rodzaju wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="54e1b-141">Now that you've built a more general visitor implementation, you can visit and process many more different types of expressions.</span></span>

## <a name="examining-an-addition-expression-with-many-levels"></a><span data-ttu-id="54e1b-142">Badanie wyrażenie dodanie z wiele poziomów</span><span class="sxs-lookup"><span data-stu-id="54e1b-142">Examining an Addition Expression with Many Levels</span></span>

<span data-ttu-id="54e1b-143">Załóżmy spróbuj przykład bardziej skomplikowane, ale nadal Ogranicz typy węzłów można tylko dodanie:</span><span class="sxs-lookup"><span data-stu-id="54e1b-143">Let's try a more complicated example, yet still limit the node types to addition only:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

<span data-ttu-id="54e1b-144">Przed uruchomieniem tego algorytmu obiektu odwiedzającego, spróbuj wykonywania myśl, można sprawdzić, co może być dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="54e1b-144">Before you run this on the visitor algorithm, try a thought exercise to work out what the output might be.</span></span> <span data-ttu-id="54e1b-145">Należy pamiętać, że `+` operator jest *operatora binarnego*: musi mieć dwa elementy podrzędne, reprezentujący lewy i prawy argumentów operacji.</span><span class="sxs-lookup"><span data-stu-id="54e1b-145">Remember that the `+` operator is a *binary operator*: it must have two children, representing the left and right operands.</span></span> <span data-ttu-id="54e1b-146">Istnieje kilka sposobów możliwe można utworzyć drzewa, który może być poprawne:</span><span class="sxs-lookup"><span data-stu-id="54e1b-146">There are several possible ways to construct a tree that could be correct:</span></span>

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

<span data-ttu-id="54e1b-147">Rozdzielenie do dwóch możliwych odpowiedzi, aby wyróżnić najbardziej obietnicy jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="54e1b-147">You can see the separation into two possible answers to highlight the most promising.</span></span> <span data-ttu-id="54e1b-148">Reprezentuje pierwszy *prawo asocjacyjnej* wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="54e1b-148">The first represents *right associative* expressions.</span></span> <span data-ttu-id="54e1b-149">Drugi reprezentują *pozostałych asocjacyjnej* wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="54e1b-149">The second represent *left associative* expressions.</span></span>
<span data-ttu-id="54e1b-150">Zalety obu tych dwóch formatów jest format skaluje się do dowolnej dowolne liczby dodanie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="54e1b-150">The advantage of both of those two formats is that the format scales to any arbitrary number of addition expressions.</span></span> 

<span data-ttu-id="54e1b-151">Po uruchomieniu tego wyrażenia przez obiekt odwiedzający, zobaczysz to te dane wyjściowe, weryfikowanie, czy wyrażenie proste dodanie ma *pozostałych asocjacyjnej*.</span><span class="sxs-lookup"><span data-stu-id="54e1b-151">If you do run this expression through the visitor, you will see this this output, verifying that the simple addition expression is *left associative*.</span></span> 

<span data-ttu-id="54e1b-152">Aby uruchomić ten przykład i Zobacz drzewa wyrażenia pełne, mają I wprowadzenie jednej zmiany źródłowe drzewo wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="54e1b-152">In order to run this sample, and see the full expression tree, I had to make one change to the source expression tree.</span></span> <span data-ttu-id="54e1b-153">Jeśli drzewo wyrażeń zawiera wszystkich stałych, wynikowe drzewo zawiera po prostu stałej wartości `10`.</span><span class="sxs-lookup"><span data-stu-id="54e1b-153">When the expression tree contains all constants, the resulting tree simply contains the constant value of `10`.</span></span> <span data-ttu-id="54e1b-154">Kompilator wykonuje operacji dodawania i zmniejsza wyrażenie najprostszej postaci.</span><span class="sxs-lookup"><span data-stu-id="54e1b-154">The compiler performs all the addition and reduces the expression to its simplest form.</span></span> <span data-ttu-id="54e1b-155">Wystarczy dodać jednej zmiennej w wyrażeniu jest wystarczające wyświetlić oryginalne drzewa:</span><span class="sxs-lookup"><span data-stu-id="54e1b-155">Simply adding one variable in the expression is sufficient to see the original tree:</span></span>

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

<span data-ttu-id="54e1b-156">Utwórz obiekt odwiedzający dla tej sumy i uruchom obiekt odwiedzający zobaczysz te dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="54e1b-156">Create a visitor for this sum and run the visitor you'll see this output:</span></span>

```
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

<span data-ttu-id="54e1b-157">Można również uruchomić dowolne inne przykłady przez obiekt odwiedzający kod i Zobacz drzewa, które reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="54e1b-157">You can also run any of the other samples through the visitor code and see what tree it represents.</span></span> <span data-ttu-id="54e1b-158">Oto przykład `sum3` wyrażenie powyżej (za pomocą dodatkowej parametru aby zapobiec obliczeniowych stałą kompilatora):</span><span class="sxs-lookup"><span data-stu-id="54e1b-158">Here's an example of the `sum3` expression above (with an additional parameter to prevent the compiler from computing the constant):</span></span>

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

<span data-ttu-id="54e1b-159">Poniżej przedstawiono dane wyjściowe obiektu odwiedzającego:</span><span class="sxs-lookup"><span data-stu-id="54e1b-159">Here's the output from the visitor:</span></span>

```
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

<span data-ttu-id="54e1b-160">Zwróć uwagę, że nawiasy nie są częścią danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="54e1b-160">Notice that the parentheses are not part of the output.</span></span> <span data-ttu-id="54e1b-161">Nie ma żadnych węzłów w drzewie wyrażenia, reprezentujące nawiasów w wyrażeniu wejściowego.</span><span class="sxs-lookup"><span data-stu-id="54e1b-161">There are no nodes in the expression tree that represent the parentheses in the input expression.</span></span> <span data-ttu-id="54e1b-162">Struktura drzewa wyrażenia zawiera wszystkie informacje niezbędne do komunikowania się pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="54e1b-162">The structure of the expression tree contains all the information necessary to communicate the precedence.</span></span>

## <a name="extending-from-this-sample"></a><span data-ttu-id="54e1b-163">Rozszerzanie od tego przykładu</span><span class="sxs-lookup"><span data-stu-id="54e1b-163">Extending from this sample</span></span>

<span data-ttu-id="54e1b-164">Przykład dotyczy tylko najbardziej podstawowe drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="54e1b-164">The sample deals with only the most rudimentary expression trees.</span></span> <span data-ttu-id="54e1b-165">Kod w tej sekcji przedstawiono obsługuje tylko stałe całkowite i plik binarny `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="54e1b-165">The code you've seen in this section only handles constant integers and the binary `+` operator.</span></span> <span data-ttu-id="54e1b-166">Jako próbkę końcowego umożliwia aktualizacji obiekt odwiedzający do obsługi bardziej złożone wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="54e1b-166">As a final sample, let's update the visitor to handle a more complicated expression.</span></span> <span data-ttu-id="54e1b-167">Upewnijmy działa w przypadku to:</span><span class="sxs-lookup"><span data-stu-id="54e1b-167">Let's make it work for this:</span></span>

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

<span data-ttu-id="54e1b-168">Ten kod reprezentuje jedna implementacja możliwe matematyczne *silnię* funkcji.</span><span class="sxs-lookup"><span data-stu-id="54e1b-168">This code represents one possible implementation for the mathematical *factorial* function.</span></span> <span data-ttu-id="54e1b-169">Sposób I napisanych ten kod prezentuje dwa limitiations tworzenia drzewa wyrażeń przypisując wyrażenia lambda wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="54e1b-169">The way I've written this code highlights two limitiations of building expression trees by assigning lambda expressions to Expressions.</span></span> <span data-ttu-id="54e1b-170">Po pierwsze instrukcji lambda nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="54e1b-170">First, statement lambdas are not allowed.</span></span> <span data-ttu-id="54e1b-171">Oznacza to, nie można używać pętli, bloków, jeśli / else — instrukcje i innych kontrolowanie struktury typowe w języku C#.</span><span class="sxs-lookup"><span data-stu-id="54e1b-171">That means I can't use loops, blocks, if / else statements, and other control structures common in C#.</span></span> <span data-ttu-id="54e1b-172">Jestem maksymalnie za pomocą wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="54e1b-172">I'm limited to using expressions.</span></span> <span data-ttu-id="54e1b-173">Po drugie nie można rekursywnie wywołania jednego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="54e1b-173">Second, I can't recursively call the same expression.</span></span>
<span data-ttu-id="54e1b-174">Było to możliwe, jeśli już zostały delegata, ale nie można wywołać ją w postaci drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="54e1b-174">I could if it were already a delegate, but I can't call it in its expression tree form.</span></span> <span data-ttu-id="54e1b-175">W sekcji [drzew wyrażeń do kompilowania](expression-trees-building.md) dowiesz się techniki, aby wyeliminować te ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="54e1b-175">In the section on [building expression trees](expression-trees-building.md) you'll learn techniques to overcome these limitations.</span></span>


<span data-ttu-id="54e1b-176">W tym wyrażeniu podłączania węzłów z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="54e1b-176">In this expression, you'll encounter nodes of all these types:</span></span>
1. <span data-ttu-id="54e1b-177">Równości (wyrażenie binarne)</span><span class="sxs-lookup"><span data-stu-id="54e1b-177">Equal (binary expression)</span></span>
2. <span data-ttu-id="54e1b-178">Mnożenie (wyrażenie binarne)</span><span class="sxs-lookup"><span data-stu-id="54e1b-178">Multiply (binary expression)</span></span>
3. <span data-ttu-id="54e1b-179">Warunkowy (?</span><span class="sxs-lookup"><span data-stu-id="54e1b-179">Conditional (the ?</span></span> <span data-ttu-id="54e1b-180">: wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="54e1b-180">: expression)</span></span>
4. <span data-ttu-id="54e1b-181">Wyrażenia wywołania metody (wywoływania `Range()` i `Aggregate()`)</span><span class="sxs-lookup"><span data-stu-id="54e1b-181">Method Call Expression (calling `Range()` and `Aggregate()`)</span></span>

<span data-ttu-id="54e1b-182">Jednym ze sposobów zmodyfikować algorytm osoby odwiedzającej jest zachować jej wykonanie i zapisać typu węzła za każdym razem, gdy zostanie wyświetlona z `default` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="54e1b-182">One way to modify the visitor algorithm is to keep executing it, and write the node type every time you reach your `default` clause.</span></span> <span data-ttu-id="54e1b-183">Po kilku iteracji będzie przejrzane potencjalnych węzłach.</span><span class="sxs-lookup"><span data-stu-id="54e1b-183">After a few iterations, you'll have seen each of the potential nodes.</span></span> <span data-ttu-id="54e1b-184">Następnie należy wymagany.</span><span class="sxs-lookup"><span data-stu-id="54e1b-184">Then, you have all you need.</span></span> <span data-ttu-id="54e1b-185">Wynik będzie podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="54e1b-185">The result would be something like this:</span></span>

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

<span data-ttu-id="54e1b-186">ConditionalVisitor i MethodCallVisitor proces tych dwóch węzłów:</span><span class="sxs-lookup"><span data-stu-id="54e1b-186">The ConditionalVisitor and MethodCallVisitor process those two nodes:</span></span>

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

<span data-ttu-id="54e1b-187">I będą dane wyjściowe dla drzewa wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="54e1b-187">And the output for the expression tree would be:</span></span>

```
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

## <a name="extending-the-sample-library"></a><span data-ttu-id="54e1b-188">Rozszerzanie biblioteki próbki</span><span class="sxs-lookup"><span data-stu-id="54e1b-188">Extending the Sample Library</span></span>

<span data-ttu-id="54e1b-189">Przykłady w tej sekcji zawierają techniki core do odwiedzenia i zbadać węzłów na drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="54e1b-189">The samples in this section show the core techniques to visit and examine nodes in an expression tree.</span></span> <span data-ttu-id="54e1b-190">I glossed przez wiele akcji, które mogą wymagać, aby skoncentrować się na podstawowych zadań funkcji odwiedzając i uzyskiwania dostępu do węzłów na drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="54e1b-190">I glossed over many actions you might need in order to concentrate on the core tasks of visiting and accessing nodes in an expression tree.</span></span> 

<span data-ttu-id="54e1b-191">Po pierwsze gości obsługiwać tylko stałe, które są liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="54e1b-191">First, the visitors only handle constants that are integers.</span></span> <span data-ttu-id="54e1b-192">Wartości stałe może być dowolnego typu liczbowego i języka C# obsługuje konwersje i promocji między tymi typami.</span><span class="sxs-lookup"><span data-stu-id="54e1b-192">Constant values could be any other numeric type, and the C# language supports conversions and promotions between those types.</span></span> <span data-ttu-id="54e1b-193">Bardziej niezawodna wersja ten kod będzie duplikatów wszystkie te funkcje.</span><span class="sxs-lookup"><span data-stu-id="54e1b-193">A more robust version of this code would mirror all those capabilities.</span></span>

<span data-ttu-id="54e1b-194">Nawet przykładu rozpoznaje podzbiór typy węzłów.</span><span class="sxs-lookup"><span data-stu-id="54e1b-194">Even the last example recognizes a subset of the possible node types.</span></span>
<span data-ttu-id="54e1b-195">Użytkownik może nadal źródła strumieniowego go wiele wyrażeń, które spowoduje jego awarię.</span><span class="sxs-lookup"><span data-stu-id="54e1b-195">You can still feed it many expressions that will cause it to fail.</span></span>
<span data-ttu-id="54e1b-196">Pełnego wdrożenia znajduje się w .NET Standard pod nazwą [ExpressionVisitor](/dotnet/core/api/System.Linq.Expressions.ExpressionVisitor) i może obsługiwać wszystkie typy węzłów.</span><span class="sxs-lookup"><span data-stu-id="54e1b-196">A full implementation is included in the .NET Standard under the name [ExpressionVisitor](/dotnet/core/api/System.Linq.Expressions.ExpressionVisitor) and can handle all the possible node types.</span></span>

<span data-ttu-id="54e1b-197">Na koniec biblioteki używane w tym artykule został utworzony dla pokazu i uczenie się.</span><span class="sxs-lookup"><span data-stu-id="54e1b-197">Finally, the library I used in this article was built for demonstration and learning.</span></span> <span data-ttu-id="54e1b-198">Nie jest zoptymalizowana.</span><span class="sxs-lookup"><span data-stu-id="54e1b-198">It's not optimized.</span></span> <span data-ttu-id="54e1b-199">Napisane aby struktur oczywiste, a aby wyróżnić techniki stosowana do odwiedzenia węzły i analizowanie, co jest.</span><span class="sxs-lookup"><span data-stu-id="54e1b-199">I wrote it to make the structures used very clear, and to highlight the techniques used to visit the nodes and analyze what's there.</span></span> <span data-ttu-id="54e1b-200">Implementacji produkcyjnej może zwrócić uwagę na wydajność niż mam.</span><span class="sxs-lookup"><span data-stu-id="54e1b-200">A production implementation would pay more attention to performance than I have.</span></span>

<span data-ttu-id="54e1b-201">Nawet w przypadku tych ograniczeń należy również na sposób zapisywania algorytmów przeczytane i zrozumiane drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="54e1b-201">Even with those limitations, you should be well on your way to writing algorithms that read and understand expression trees.</span></span>

[<span data-ttu-id="54e1b-202">Następnie — Tworzenie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="54e1b-202">Next -- Building Expressions</span></span>](expression-trees-building.md)
