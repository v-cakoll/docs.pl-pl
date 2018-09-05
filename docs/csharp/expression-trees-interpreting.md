---
title: Interpretowanie wyrażeń
description: Dowiedz się, jak napisać kod, aby sprawdzić strukturę drzewa wyrażenie.
ms.date: 06/20/2016
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 95fbb021aeeb9f2f4eb36f664f9fe904d1d52453
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506422"
---
# <a name="interpreting-expressions"></a><span data-ttu-id="98b0e-103">Interpretowanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="98b0e-103">Interpreting Expressions</span></span>

[<span data-ttu-id="98b0e-104">Poprzednie — Wykonywanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="98b0e-104">Previous -- Executing Expressions</span></span>](expression-trees-execution.md)

<span data-ttu-id="98b0e-105">Teraz umożliwia pisanie kodu w celu zbadania struktury *drzewa wyrażeń*.</span><span class="sxs-lookup"><span data-stu-id="98b0e-105">Now, let's write some code to examine the structure of an *expression tree*.</span></span> <span data-ttu-id="98b0e-106">Każdy węzeł w drzewie wyrażeń będzie obiektem klasy, która jest pochodną `Expression`.</span><span class="sxs-lookup"><span data-stu-id="98b0e-106">Every node in an expression tree will be an object of a class that is derived from `Expression`.</span></span>

<span data-ttu-id="98b0e-107">Ten projekt sprawia, że odwiedzający wszystkich węzłów w drzewie wyrażeń operację cyklicznego stosunkowo proste.</span><span class="sxs-lookup"><span data-stu-id="98b0e-107">That design makes visiting all the nodes in an expression tree a relatively straight forward recursive operation.</span></span> <span data-ttu-id="98b0e-108">Ogólna strategia polega na rozpoczynają się od węzła głównego i ustalić, jakiego typu węzła jest.</span><span class="sxs-lookup"><span data-stu-id="98b0e-108">The general strategy is to start at the root node and determine what kind of node it is.</span></span>

<span data-ttu-id="98b0e-109">Jeśli typ węzła ma elementy podrzędne, rekursywnie można znaleźć elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="98b0e-109">If the node type has children, recursively visit the children.</span></span> <span data-ttu-id="98b0e-110">W każdym węźle podrzędnych należy powtórzyć używane w węźle głównym: Określanie typu, a jeśli typ ma elementy podrzędne, odwiedź każdego elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="98b0e-110">At each child node, repeat the process used at the root node: determine the type, and if the type has children, visit each of the children.</span></span>

## <a name="examining-an-expression-with-no-children"></a><span data-ttu-id="98b0e-111">Badanie wyrażenie żadne elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="98b0e-111">Examining an Expression with No Children</span></span>
<span data-ttu-id="98b0e-112">Zacznijmy od, przechodząc do każdego węzła w drzewie bardzo proste wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="98b0e-112">Let's start by visiting each node in a very simple expression tree.</span></span>
<span data-ttu-id="98b0e-113">Poniżej przedstawiono kod, który tworzy wyrażeniem stałym, a następnie sprawdza, czy jego właściwości:</span><span class="sxs-lookup"><span data-stu-id="98b0e-113">Here's the code that creates a constant expression and then examines its properties:</span></span>

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

<span data-ttu-id="98b0e-114">Zostanie wydrukowany następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="98b0e-114">This will print the following:</span></span>

```
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

<span data-ttu-id="98b0e-115">Teraz napiszmy kod, który może zbadać to wyrażenie i zapisać niektóre ważne właściwości na jego temat.</span><span class="sxs-lookup"><span data-stu-id="98b0e-115">Now, let's write the code that would examine this expression and write out some important properties about it.</span></span> <span data-ttu-id="98b0e-116">Oto kod:</span><span class="sxs-lookup"><span data-stu-id="98b0e-116">Here's that code:</span></span>

## <a name="examining-a-simple-addition-expression"></a><span data-ttu-id="98b0e-117">Badanie proste wyrażenie dodawania</span><span class="sxs-lookup"><span data-stu-id="98b0e-117">Examining a simple Addition Expression</span></span>

<span data-ttu-id="98b0e-118">Zacznijmy od przykład dodawania z wprowadzeniem do tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="98b0e-118">Let's start with the addition sample from the introduction to this section.</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> <span data-ttu-id="98b0e-119">Nie używam `var` do deklarowania tego drzewa wyrażeń, ponieważ nie jest możliwe ponieważ po prawej stronie przypisania został niejawnie wpisany.</span><span class="sxs-lookup"><span data-stu-id="98b0e-119">I'm not using `var` to declare this expression tree, as it is not possible because the right-hand side of the assignment is implicitly typed.</span></span> <span data-ttu-id="98b0e-120">Aby głębiej to zrozumieć, przeczytaj [tutaj](implicitly-typed-lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="98b0e-120">To understand this more deeply, read [here](implicitly-typed-lambda-expressions.md).</span></span>

<span data-ttu-id="98b0e-121">Węzeł główny jest `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="98b0e-121">The root node is a `LambdaExpression`.</span></span> <span data-ttu-id="98b0e-122">Aby uzyskać kod interesujące po prawej stronie `=>` operatora, należy określić jeden z elementów podrzędnych `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="98b0e-122">In order to get the interesting code on the right hand side of the `=>` operator, you need to find one of the children of the `LambdaExpression`.</span></span> <span data-ttu-id="98b0e-123">Możemy to zrobić za pomocą wszystkie wyrażenia w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="98b0e-123">We'll do that with all the expressions in this section.</span></span> <span data-ttu-id="98b0e-124">Węzeł nadrzędny pomagają nam znaleźć zwracany typ `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="98b0e-124">The parent node does help us find the return type of the `LambdaExpression`.</span></span>

<span data-ttu-id="98b0e-125">Aby zbadać każdego węzła w tym wyrażeniu, będzie konieczne rekursywnie odwiedza liczbę węzłów.</span><span class="sxs-lookup"><span data-stu-id="98b0e-125">To examine each node in this expression, we'll need to recursively visit a number of nodes.</span></span> <span data-ttu-id="98b0e-126">Poniżej przedstawiono proste wdrażanie pierwszego:</span><span class="sxs-lookup"><span data-stu-id="98b0e-126">Here's a simple first implementation:</span></span>

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

<span data-ttu-id="98b0e-127">W tym przykładzie wyświetla następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="98b0e-127">This sample prints the following output:</span></span>

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

<span data-ttu-id="98b0e-128">Można zauważyć wiele powtarzających się w powyższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="98b0e-128">You'll notice a lot of repetition in the code sample above.</span></span>
<span data-ttu-id="98b0e-129">Załóżmy, czyszczenie i tworzenia bardziej ogólnego przeznaczenia osoba odwiedzająca węzła wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="98b0e-129">Let's clean that up and build a more general purpose expression node visitor.</span></span> <span data-ttu-id="98b0e-130">Będzie to wymagać napisać algorytm cykliczny przez firmę Microsoft.</span><span class="sxs-lookup"><span data-stu-id="98b0e-130">That's going to require us to write a recursive algorithm.</span></span> <span data-ttu-id="98b0e-131">Dowolny węzeł może być typu, który może mieć elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="98b0e-131">Any node could be of a type that might have children.</span></span>
<span data-ttu-id="98b0e-132">Dowolny węzeł, który ma elementy podrzędne wymaga od nas odwiedź te elementy podrzędne i określenie tego węzła.</span><span class="sxs-lookup"><span data-stu-id="98b0e-132">Any node that has children requires us to visit those children and determine what that node is.</span></span> <span data-ttu-id="98b0e-133">Oto oczyszczony wersji korzystającej z typu rekursji, aby odwiedzić operacji dodawania:</span><span class="sxs-lookup"><span data-stu-id="98b0e-133">Here's the cleaned up version that utilizes recursion to visit the addition operations:</span></span>

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

<span data-ttu-id="98b0e-134">Ten algorytm stanowi podstawę algorytm, które mogą odwiedzać żadnych dowolnego `LambdaExpression`.</span><span class="sxs-lookup"><span data-stu-id="98b0e-134">This algorithm is the basis of an algorithm that can visit any arbitrary `LambdaExpression`.</span></span> <span data-ttu-id="98b0e-135">Istnieje wiele powodów luki, a mianowicie szuka kod utworzoną tylko niewielką próbkę możliwe zestawy węzły drzewa wyrażenie, które może on wystąpić.</span><span class="sxs-lookup"><span data-stu-id="98b0e-135">There are a lot of holes, namely that the code I created only looks for a very small sample of the possible sets of expression tree nodes that it may encounter.</span></span> <span data-ttu-id="98b0e-136">Jednak nadal nauczysz dość nieco od je tworzy.</span><span class="sxs-lookup"><span data-stu-id="98b0e-136">However, you can still learn quite a bit from what it produces.</span></span> <span data-ttu-id="98b0e-137">(W przypadku domyślnej `Visitor.CreateFromExpression` metoda drukuje wiadomość do konsoli błędu po napotkaniu nowego typu węzła.</span><span class="sxs-lookup"><span data-stu-id="98b0e-137">(The default case in the `Visitor.CreateFromExpression` method prints a message to the error console when a new node type is encountered.</span></span> <span data-ttu-id="98b0e-138">W ten sposób możesz wiedzieć, aby dodać nowy typ wyrażenia.)</span><span class="sxs-lookup"><span data-stu-id="98b0e-138">That way, you know to add a new expression type.)</span></span>

<span data-ttu-id="98b0e-139">Po uruchomieniu tego obiektu odwiedzającego na wyrażenie dodawania pokazanych powyżej, możesz uzyskać następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="98b0e-139">When you run this visitor on the addition expression shown above, you get the following output:</span></span>

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

<span data-ttu-id="98b0e-140">Teraz, gdy masz utworzoną bardziej ogólnej implementacji obiektu odwiedzającego, można znaleźć i przetwarzać wiele więcej różnych typów wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="98b0e-140">Now that you've built a more general visitor implementation, you can visit and process many more different types of expressions.</span></span>

## <a name="examining-an-addition-expression-with-many-levels"></a><span data-ttu-id="98b0e-141">Badanie wyrażenie dodawania wielu poziomów</span><span class="sxs-lookup"><span data-stu-id="98b0e-141">Examining an Addition Expression with Many Levels</span></span>

<span data-ttu-id="98b0e-142">Teraz spróbuj bardziej skomplikowanych przykładu, ale nadal ograniczyć typy węzłów do dodawania tylko:</span><span class="sxs-lookup"><span data-stu-id="98b0e-142">Let's try a more complicated example, yet still limit the node types to addition only:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

<span data-ttu-id="98b0e-143">Przed rozpoczęciem tego algorytmu obiektu odwiedzającego, spróbuj wykonywania myślowy, określających, co może być danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="98b0e-143">Before you run this on the visitor algorithm, try a thought exercise to work out what the output might be.</span></span> <span data-ttu-id="98b0e-144">Należy pamiętać, że `+` operator jest *operatora binarnego*: musi mieć dwa elementy podrzędne, reprezentujący argumenty operacji po lewej i prawej stronie.</span><span class="sxs-lookup"><span data-stu-id="98b0e-144">Remember that the `+` operator is a *binary operator*: it must have two children, representing the left and right operands.</span></span> <span data-ttu-id="98b0e-145">Istnieje kilka sposobów możliwych do konstruowania drzewa, która może być poprawny:</span><span class="sxs-lookup"><span data-stu-id="98b0e-145">There are several possible ways to construct a tree that could be correct:</span></span>

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

<span data-ttu-id="98b0e-146">Możesz zobaczyć separacji na dwa możliwe odpowiedzi, aby wyróżnić najbardziej obiecujących.</span><span class="sxs-lookup"><span data-stu-id="98b0e-146">You can see the separation into two possible answers to highlight the most promising.</span></span> <span data-ttu-id="98b0e-147">Reprezentuje pierwszy *łączność do prawej strony* wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="98b0e-147">The first represents *right associative* expressions.</span></span> <span data-ttu-id="98b0e-148">Drugi reprezentują *łączność do lewej strony* wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="98b0e-148">The second represent *left associative* expressions.</span></span>
<span data-ttu-id="98b0e-149">Oba te dwa formaty zaletą jest to, czy format można skalować do dowolnego dowolną liczbę wyrażeń dodawania.</span><span class="sxs-lookup"><span data-stu-id="98b0e-149">The advantage of both of those two formats is that the format scales to any arbitrary number of addition expressions.</span></span> 

<span data-ttu-id="98b0e-150">Jeśli uruchamiasz to wyrażenie przez obiekt odwiedzający, zobaczysz następujący te dane wyjściowe weryfikacji, czy wyrażenie proste dodanie *łączność do lewej strony*.</span><span class="sxs-lookup"><span data-stu-id="98b0e-150">If you do run this expression through the visitor, you will see this this output, verifying that the simple addition expression is *left associative*.</span></span> 

<span data-ttu-id="98b0e-151">Aby można było uruchomić ten przykład i Zobacz drzewa pełnego wyrażenia, miałem wprowadzić zmianę w jednej na drzewo wyrażenia źródłowego.</span><span class="sxs-lookup"><span data-stu-id="98b0e-151">In order to run this sample, and see the full expression tree, I had to make one change to the source expression tree.</span></span> <span data-ttu-id="98b0e-152">Jeśli drzewa wyrażenie zawiera wszystkich stałych, wynikowe drzewo zawiera po prostu stałej wartości `10`.</span><span class="sxs-lookup"><span data-stu-id="98b0e-152">When the expression tree contains all constants, the resulting tree simply contains the constant value of `10`.</span></span> <span data-ttu-id="98b0e-153">Kompilator wykonuje wszystkie dodatkowe i zmniejsza wyrażenie które ma najprostszej postaci.</span><span class="sxs-lookup"><span data-stu-id="98b0e-153">The compiler performs all the addition and reduces the expression to its simplest form.</span></span> <span data-ttu-id="98b0e-154">Dodanie jednej zmiennej w wyrażeniu jest wystarczająca zobaczyć, oryginalnym drzewa:</span><span class="sxs-lookup"><span data-stu-id="98b0e-154">Simply adding one variable in the expression is sufficient to see the original tree:</span></span>

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

<span data-ttu-id="98b0e-155">Utwórz obiekt odwiedzający dla tej sumy, i uruchom odwiedzający zobaczysz następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="98b0e-155">Create a visitor for this sum and run the visitor you'll see this output:</span></span>

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

<span data-ttu-id="98b0e-156">Można również uruchomić dowolne inne przykłady przez obiekt odwiedzający kod i zobacz jakie drzewa, czyli przedstawia liczbę.</span><span class="sxs-lookup"><span data-stu-id="98b0e-156">You can also run any of the other samples through the visitor code and see what tree it represents.</span></span> <span data-ttu-id="98b0e-157">Oto przykład `sum3` wyrażenie powyżej (o dodatkowy parametr, aby uniemożliwić kompilatorowi obliczeń stała):</span><span class="sxs-lookup"><span data-stu-id="98b0e-157">Here's an example of the `sum3` expression above (with an additional parameter to prevent the compiler from computing the constant):</span></span>

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

<span data-ttu-id="98b0e-158">Oto dane wyjściowe obiektu odwiedzającego:</span><span class="sxs-lookup"><span data-stu-id="98b0e-158">Here's the output from the visitor:</span></span>

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

<span data-ttu-id="98b0e-159">Należy zauważyć, że nawiasy nie są częścią danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="98b0e-159">Notice that the parentheses are not part of the output.</span></span> <span data-ttu-id="98b0e-160">Brak żadnych węzłów w drzewie wyrażeń, które reprezentują nawiasy w wyrażenia wejściowego.</span><span class="sxs-lookup"><span data-stu-id="98b0e-160">There are no nodes in the expression tree that represent the parentheses in the input expression.</span></span> <span data-ttu-id="98b0e-161">Struktura drzewa wyrażenie zawiera wszystkie informacje niezbędne do komunikowania się pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="98b0e-161">The structure of the expression tree contains all the information necessary to communicate the precedence.</span></span>

## <a name="extending-from-this-sample"></a><span data-ttu-id="98b0e-162">Rozszerzanie od tego przykładu</span><span class="sxs-lookup"><span data-stu-id="98b0e-162">Extending from this sample</span></span>

<span data-ttu-id="98b0e-163">Przykład dotyczy tylko najbardziej podstawowe drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="98b0e-163">The sample deals with only the most rudimentary expression trees.</span></span> <span data-ttu-id="98b0e-164">Kod w tej sekcji przedstawiono obsługuje tylko stałych liczb całkowitych i plik binarny `+` operatora.</span><span class="sxs-lookup"><span data-stu-id="98b0e-164">The code you've seen in this section only handles constant integers and the binary `+` operator.</span></span> <span data-ttu-id="98b0e-165">Jako przykład końcowej zaktualizujmy obiektu odwiedzającego, aby obsłużyć bardziej skomplikowanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="98b0e-165">As a final sample, let's update the visitor to handle a more complicated expression.</span></span> <span data-ttu-id="98b0e-166">Upewnijmy się, to działa, w tym:</span><span class="sxs-lookup"><span data-stu-id="98b0e-166">Let's make it work for this:</span></span>

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ? 
    1 : 
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

<span data-ttu-id="98b0e-167">Ten kod przedstawia jedna implementacja możliwe matematyczne *silnię* funkcji.</span><span class="sxs-lookup"><span data-stu-id="98b0e-167">This code represents one possible implementation for the mathematical *factorial* function.</span></span> <span data-ttu-id="98b0e-168">Sposób moje recenzje ten kod wyróżnia dwa ograniczenia tworzenia drzew wyrażeń, przypisując wyrażeń lambda wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="98b0e-168">The way I've written this code highlights two limitiations of building expression trees by assigning lambda expressions to Expressions.</span></span> <span data-ttu-id="98b0e-169">Po pierwsze instrukcji wyrażenia lambda nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="98b0e-169">First, statement lambdas are not allowed.</span></span> <span data-ttu-id="98b0e-170">Oznacza to, nie można użyć pętli, bloki, jeśli / inne instrukcje i inne kontrolowanie struktury typowe w języku C#.</span><span class="sxs-lookup"><span data-stu-id="98b0e-170">That means I can't use loops, blocks, if / else statements, and other control structures common in C#.</span></span> <span data-ttu-id="98b0e-171">Jestem maksymalnie za pomocą wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="98b0e-171">I'm limited to using expressions.</span></span> <span data-ttu-id="98b0e-172">Po drugie nie można rekursywnie wywołania to samo wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="98b0e-172">Second, I can't recursively call the same expression.</span></span>
<span data-ttu-id="98b0e-173">Było to możliwe, jeśli zostały już delegata, ale nie można wywołać ją w postaci drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="98b0e-173">I could if it were already a delegate, but I can't call it in its expression tree form.</span></span> <span data-ttu-id="98b0e-174">W sekcji [tworzenia drzew wyrażeń](expression-trees-building.md) dowiesz się, techniki, aby wyeliminować te ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="98b0e-174">In the section on [building expression trees](expression-trees-building.md) you'll learn techniques to overcome these limitations.</span></span>


<span data-ttu-id="98b0e-175">W tym wyrażeniu spotkasz się węzły te typy:</span><span class="sxs-lookup"><span data-stu-id="98b0e-175">In this expression, you'll encounter nodes of all these types:</span></span>
1. <span data-ttu-id="98b0e-176">Równe (wyrażenia binarnego)</span><span class="sxs-lookup"><span data-stu-id="98b0e-176">Equal (binary expression)</span></span>
2. <span data-ttu-id="98b0e-177">Mnożenie (wyrażenia binarnego)</span><span class="sxs-lookup"><span data-stu-id="98b0e-177">Multiply (binary expression)</span></span>
3. <span data-ttu-id="98b0e-178">Warunkowy (?</span><span class="sxs-lookup"><span data-stu-id="98b0e-178">Conditional (the ?</span></span> <span data-ttu-id="98b0e-179">: wyrażenie)</span><span class="sxs-lookup"><span data-stu-id="98b0e-179">: expression)</span></span>
4. <span data-ttu-id="98b0e-180">Wyrażenia wywołania metody (wywołanie `Range()` i `Aggregate()`)</span><span class="sxs-lookup"><span data-stu-id="98b0e-180">Method Call Expression (calling `Range()` and `Aggregate()`)</span></span>

<span data-ttu-id="98b0e-181">Jednym ze sposobów modyfikowania algorytm osoby odwiedzającej jest zachowania, ale wykonanie go i zapisać typu węzła za każdym razem, gdy osiągniesz swoje `default` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="98b0e-181">One way to modify the visitor algorithm is to keep executing it, and write the node type every time you reach your `default` clause.</span></span> <span data-ttu-id="98b0e-182">Po kilku iteracjach będzie wiesz potencjalnych węzłach.</span><span class="sxs-lookup"><span data-stu-id="98b0e-182">After a few iterations, you'll have seen each of the potential nodes.</span></span> <span data-ttu-id="98b0e-183">Następnie masz wszystko, czego potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="98b0e-183">Then, you have all you need.</span></span> <span data-ttu-id="98b0e-184">Wynik będzie podobny do poniższego:</span><span class="sxs-lookup"><span data-stu-id="98b0e-184">The result would be something like this:</span></span>

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

<span data-ttu-id="98b0e-185">ConditionalVisitor i MethodCallVisitor proces tych dwóch węzłów:</span><span class="sxs-lookup"><span data-stu-id="98b0e-185">The ConditionalVisitor and MethodCallVisitor process those two nodes:</span></span>

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

<span data-ttu-id="98b0e-186">I dane wyjściowe do drzewa wyrażenie będą:</span><span class="sxs-lookup"><span data-stu-id="98b0e-186">And the output for the expression tree would be:</span></span>

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

## <a name="extending-the-sample-library"></a><span data-ttu-id="98b0e-187">Rozszerzanie biblioteki próbki</span><span class="sxs-lookup"><span data-stu-id="98b0e-187">Extending the Sample Library</span></span>

<span data-ttu-id="98b0e-188">W tej sekcji przedstawiają technik core, aby znaleźć i zbadaj węzłów na drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="98b0e-188">The samples in this section show the core techniques to visit and examine nodes in an expression tree.</span></span> <span data-ttu-id="98b0e-189">Czy mogę glossed przez wiele akcji, które może być konieczne, aby można było skupić się na podstawowych zadaniach, odwiedzając i uzyskiwania dostępu do węzłów na drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="98b0e-189">I glossed over many actions you might need in order to concentrate on the core tasks of visiting and accessing nodes in an expression tree.</span></span> 

<span data-ttu-id="98b0e-190">Po pierwsze gości obsługiwać stałe, które są liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="98b0e-190">First, the visitors only handle constants that are integers.</span></span> <span data-ttu-id="98b0e-191">Stałe wartości może być dowolnego typu liczbowego, a w języku C# obsługuje konwersji i promocje między tymi typami.</span><span class="sxs-lookup"><span data-stu-id="98b0e-191">Constant values could be any other numeric type, and the C# language supports conversions and promotions between those types.</span></span> <span data-ttu-id="98b0e-192">Bardziej niezawodna wersję ten kod będzie dublować wszystkie te funkcje.</span><span class="sxs-lookup"><span data-stu-id="98b0e-192">A more robust version of this code would mirror all those capabilities.</span></span>

<span data-ttu-id="98b0e-193">Nawet w ostatnim przykładzie rozpoznaje podzbiór typy węzłów.</span><span class="sxs-lookup"><span data-stu-id="98b0e-193">Even the last example recognizes a subset of the possible node types.</span></span>
<span data-ttu-id="98b0e-194">Można nadal dostarczyć on wiele wyrażeń, które spowoduje jego nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="98b0e-194">You can still feed it many expressions that will cause it to fail.</span></span>
<span data-ttu-id="98b0e-195">Pełną implementację znajduje się w programie .NET Standard pod nazwą <xref:System.Linq.Expressions.ExpressionVisitor> i może obsługiwać wszystkie typy węzłów.</span><span class="sxs-lookup"><span data-stu-id="98b0e-195">A full implementation is included in the .NET Standard under the name <xref:System.Linq.Expressions.ExpressionVisitor> and can handle all the possible node types.</span></span>

<span data-ttu-id="98b0e-196">Na koniec biblioteki używane w tym artykule została stworzona z myślą demonstracji i szkolenia.</span><span class="sxs-lookup"><span data-stu-id="98b0e-196">Finally, the library I used in this article was built for demonstration and learning.</span></span> <span data-ttu-id="98b0e-197">Nie jest zoptymalizowany.</span><span class="sxs-lookup"><span data-stu-id="98b0e-197">It's not optimized.</span></span> <span data-ttu-id="98b0e-198">Napisałem, aby struktur używane oczywiste, a aby wyróżnić te techniki do odwiedzenia węzły i analizowanie, co jest.</span><span class="sxs-lookup"><span data-stu-id="98b0e-198">I wrote it to make the structures used very clear, and to highlight the techniques used to visit the nodes and analyze what's there.</span></span> <span data-ttu-id="98b0e-199">Implementacji produkcyjnej może zwrócić uwagę na wydajność nie mam.</span><span class="sxs-lookup"><span data-stu-id="98b0e-199">A production implementation would pay more attention to performance than I have.</span></span>

<span data-ttu-id="98b0e-200">Nawet w przypadku tych ograniczeń powinno być na dobrej drodze do pisania algorytmów przeczytać i sprawdzić drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="98b0e-200">Even with those limitations, you should be well on your way to writing algorithms that read and understand expression trees.</span></span>

[<span data-ttu-id="98b0e-201">Następnie — Budowanie wyrażenia</span><span class="sxs-lookup"><span data-stu-id="98b0e-201">Next -- Building Expressions</span></span>](expression-trees-building.md)
