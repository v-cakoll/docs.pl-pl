---
title: Tłumaczenie drzew wyrażeń
description: Dowiedz się, jak odwiedzać każdy węzeł w drzewie wyrażenia podczas tworzenia zmodyfikowanej kopii tego drzewa wyrażenia.
ms.date: 06/20/2016
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: b3c575876b6d53e9db366f59ad45aac714923c45
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202952"
---
# <a name="translating-expression-trees"></a><span data-ttu-id="232d5-103">Tłumaczenie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="232d5-103">Translating Expression Trees</span></span>

[<span data-ttu-id="232d5-104">Poprzednie — Kompilowanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="232d5-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="232d5-105">W tej ostatniej sekcji dowiesz się, jak odwiedzać każdy węzeł w drzewie wyrażenia podczas tworzenia zmodyfikowanej kopii tego drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="232d5-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="232d5-106">Są to techniki, które będą używane w dwóch ważnych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="232d5-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="232d5-107">Pierwszy polega na zrozumieniu algorytmów wyrażonych przez drzewo wyrażenia, aby można było je przetłumaczyć na inne środowisko.</span><span class="sxs-lookup"><span data-stu-id="232d5-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="232d5-108">Druga jest zmiana algorytmu, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="232d5-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="232d5-109">Może to być dodanie rejestrowania, wywołanie metody przechwytywania i śledzenie ich lub inne cele.</span><span class="sxs-lookup"><span data-stu-id="232d5-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="232d5-110">Trwa odwiedzanie tłumaczenia</span><span class="sxs-lookup"><span data-stu-id="232d5-110">Translating is Visiting</span></span>

<span data-ttu-id="232d5-111">Kod, który tworzysz w celu przetłumaczenia drzewa wyrażenia, jest rozszerzeniem tego, co już widzisz, aby odwiedzić wszystkie węzły w drzewie.</span><span class="sxs-lookup"><span data-stu-id="232d5-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="232d5-112">W przypadku tłumaczenia drzewa wyrażenia odwiedzane są wszystkie węzły, a podczas odwiedzania można utworzyć nowe drzewo.</span><span class="sxs-lookup"><span data-stu-id="232d5-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="232d5-113">Nowe drzewo może zawierać odwołania do oryginalnych węzłów lub nowe węzły, które zostały umieszczone w drzewie.</span><span class="sxs-lookup"><span data-stu-id="232d5-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="232d5-114">Zobaczmy to w akcji, odwiedzając drzewo wyrażenia i tworząc nowe drzewo z niektórymi węzłami zastępczymi.</span><span class="sxs-lookup"><span data-stu-id="232d5-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="232d5-115">W tym przykładzie zamienimy każdą stałą na stałą o dziesięć razy większym.</span><span class="sxs-lookup"><span data-stu-id="232d5-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="232d5-116">W przeciwnym razie pozostawimy drzewo wyrażenia bez zmian.</span><span class="sxs-lookup"><span data-stu-id="232d5-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="232d5-117">Zamiast odczytywania wartości stałej i zamieniania jej na nową stałą, wprowadzimy tę zamianę, zastępując węzeł stały nowym węzłem, który wykonuje mnożenie.</span><span class="sxs-lookup"><span data-stu-id="232d5-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="232d5-118">W tym miejscu po znalezieniu stałego węzła utworzysz nowy węzeł mnożenia, którego elementy podrzędne są pierwotną stałą i stałą `10`:</span><span class="sxs-lookup"><span data-stu-id="232d5-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

```csharp
private static Expression ReplaceNodes(Expression original)
{
    if (original.NodeType == ExpressionType.Constant)
    {
        return Expression.Multiply(original, Expression.Constant(10));
    }
    else if (original.NodeType == ExpressionType.Add)
    {
        var binaryExpression = (BinaryExpression)original;
        return Expression.Add(
            ReplaceNodes(binaryExpression.Left),
            ReplaceNodes(binaryExpression.Right));
    }
    return original;
}
```

<span data-ttu-id="232d5-119">Zastępując pierwotny węzeł podstawianiem, tworzone jest nowe drzewo zawierające nasze modyfikacje.</span><span class="sxs-lookup"><span data-stu-id="232d5-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="232d5-120">Możemy sprawdzić, czy przez skompilowanie i wykonanie zastąpionego drzewa.</span><span class="sxs-lookup"><span data-stu-id="232d5-120">We can verify that by compiling and executing the replaced tree.</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
var sum = ReplaceNodes(addition);
var executableFunc = Expression.Lambda(sum);

var func = (Func<int>)executableFunc.Compile();
var answer = func();
Console.WriteLine(answer);
```

<span data-ttu-id="232d5-121">Tworzenie nowego drzewa jest kombinacją odwiedzanych węzłów w istniejącym drzewie i tworzenie nowych węzłów i wstawianie ich do drzewa.</span><span class="sxs-lookup"><span data-stu-id="232d5-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="232d5-122">Ten przykład pokazuje ważność drzew wyrażeń, które są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="232d5-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="232d5-123">Należy zauważyć, że nowe drzewo utworzone powyżej zawiera kombinację nowo utworzonych węzłów i węzłów z istniejącego drzewa.</span><span class="sxs-lookup"><span data-stu-id="232d5-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="232d5-124">Jest to bezpieczne, ponieważ nie można modyfikować węzłów w istniejącym drzewie.</span><span class="sxs-lookup"><span data-stu-id="232d5-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="232d5-125">Może to spowodować znaczne zwiększenie wydajności pamięci.</span><span class="sxs-lookup"><span data-stu-id="232d5-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="232d5-126">Te same węzły można używać w całym drzewie lub w wielu drzewach wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="232d5-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="232d5-127">Ponieważ węzły nie mogą być modyfikowane, ten sam węzeł może być ponownie używany w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="232d5-127">Since nodes can't be modified, the same node can be reused whenever its needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="232d5-128">Przechodzenie i wykonywanie dodawania</span><span class="sxs-lookup"><span data-stu-id="232d5-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="232d5-129">Sprawdźmy to, tworząc drugiego odwiedzającego, który przeprowadzi drzewo węzłów dodawania i obliczy wynik.</span><span class="sxs-lookup"><span data-stu-id="232d5-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="232d5-130">Można to zrobić, wprowadzając kilka modyfikacji odwiedzanych do tej pory.</span><span class="sxs-lookup"><span data-stu-id="232d5-130">You can do this by making a couple modifications to the visitor that you've seen so far.</span></span> <span data-ttu-id="232d5-131">W tej nowej wersji odwiedzający zwróci częściową sumę operacji dodawania do tego punktu.</span><span class="sxs-lookup"><span data-stu-id="232d5-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="232d5-132">Wyrażenie stałe, które jest po prostu wartością wyrażenia stałej.</span><span class="sxs-lookup"><span data-stu-id="232d5-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="232d5-133">W przypadku wyrażenia dodawania wynik jest sumą argumentów operacji lewy i prawy, gdy te drzewa zostały przesunięte.</span><span class="sxs-lookup"><span data-stu-id="232d5-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var three= Expression.Constant(3, typeof(int));
var four = Expression.Constant(4, typeof(int));
var addition = Expression.Add(one, two);
var add2 = Expression.Add(three, four);
var sum = Expression.Add(addition, add2);

// Declare the delegate, so we can call it
// from itself recursively:
Func<Expression, int> aggregate = null;
// Aggregate, return constants, or the sum of the left and right operand.
// Major simplification: Assume every binary expression is an addition.
aggregate = (exp) =>
    exp.NodeType == ExpressionType.Constant ?
    (int)((ConstantExpression)exp).Value :
    aggregate(((BinaryExpression)exp).Left) + aggregate(((BinaryExpression)exp).Right);

var theSum = aggregate(sum);
Console.WriteLine(theSum);
```

<span data-ttu-id="232d5-134">W tym miejscu jest dość dużo kodu, ale koncepcje są bardzo podejścia.</span><span class="sxs-lookup"><span data-stu-id="232d5-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="232d5-135">Ten kod wizytuje elementy podrzędne na głębokości pierwszego wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="232d5-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="232d5-136">Gdy napotka węzeł stały, odwiedzający zwraca wartość stałej.</span><span class="sxs-lookup"><span data-stu-id="232d5-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="232d5-137">Po odwiedzeniu obu elementów podrzędnych osoby odwiedzające będą obliczać sumę obliczoną dla tego poddrzewa.</span><span class="sxs-lookup"><span data-stu-id="232d5-137">After the visitor has visited both children, those children will have computed the sum computed for that sub-tree.</span></span> <span data-ttu-id="232d5-138">Węzeł dodawania może teraz obliczyć jego sumę.</span><span class="sxs-lookup"><span data-stu-id="232d5-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="232d5-139">Po odwiedzeniu wszystkich węzłów w drzewie wyrażenia suma zostanie obliczona.</span><span class="sxs-lookup"><span data-stu-id="232d5-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="232d5-140">Wykonanie można śledzić przez uruchomienie przykładu w debugerze i śledzenie wykonania.</span><span class="sxs-lookup"><span data-stu-id="232d5-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="232d5-141">Ułatwiamy śledzenie sposobu analizowania węzłów i sposobu obliczania sumy przez przechodzenie przez drzewo.</span><span class="sxs-lookup"><span data-stu-id="232d5-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by traversing the tree.</span></span> <span data-ttu-id="232d5-142">Oto zaktualizowana wersja metody agregującej, która zawiera dość kilka informacji o śledzeniu:</span><span class="sxs-lookup"><span data-stu-id="232d5-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

```csharp
private static int Aggregate(Expression exp)
{
    if (exp.NodeType == ExpressionType.Constant)
    {
        var constantExp = (ConstantExpression)exp;
        Console.Error.WriteLine($"Found Constant: {constantExp.Value}");
        return (int)constantExp.Value;
    }
    else if (exp.NodeType == ExpressionType.Add)
    {
        var addExp = (BinaryExpression)exp;
        Console.Error.WriteLine("Found Addition Expression");
        Console.Error.WriteLine("Computing Left node");
        var leftOperand = Aggregate(addExp.Left);
        Console.Error.WriteLine($"Left is: {leftOperand}");
        Console.Error.WriteLine("Computing Right node");
        var rightOperand = Aggregate(addExp.Right);
        Console.Error.WriteLine($"Right is: {rightOperand}");
        var sum = leftOperand + rightOperand;
        Console.Error.WriteLine($"Computed sum: {sum}");
        return sum;
    }
    else throw new NotSupportedException("Haven't written this yet");
}
```

<span data-ttu-id="232d5-143">Uruchomienie go w tym samym wyrażeniu daje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="232d5-143">Running it on the same expression yields the following output:</span></span>

```output
10
Found Addition Expression
Computing Left node
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Constant: 2
Right is: 2
Computed sum: 3
Left is: 3
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 10
10
```

<span data-ttu-id="232d5-144">Śledź dane wyjściowe i postępuj zgodnie z powyższym kodem.</span><span class="sxs-lookup"><span data-stu-id="232d5-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="232d5-145">Powinien być w stanie dowiedzieć się, jak kod odwiedza każdy węzeł i oblicza sumę w miarę przechodzenia przez drzewo i odnajduje sumę.</span><span class="sxs-lookup"><span data-stu-id="232d5-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="232d5-146">Teraz przyjrzyjmy się różnemu przebiegowi z wyrażeniem podanym przez `sum1`:</span><span class="sxs-lookup"><span data-stu-id="232d5-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="232d5-147">Oto dane wyjściowe badania tego wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="232d5-147">Here's the output from examining this expression:</span></span>

```output
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 2
Left is: 2
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 9
Right is: 9
Computed sum: 10
10
```

<span data-ttu-id="232d5-148">Gdy ostateczna odpowiedź jest taka sama, przechodzenie drzewa jest zupełnie inne.</span><span class="sxs-lookup"><span data-stu-id="232d5-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="232d5-149">Węzły są przesyłane w innej kolejności, ponieważ drzewo zostało skonstruowane z różnymi operacjami wykonywanymi jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="232d5-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="232d5-150">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="232d5-150">Learning More</span></span>

<span data-ttu-id="232d5-151">Ten przykład pokazuje mały podzbiór kodu, który będzie przepływał i interpretuje algorytmy reprezentowane przez drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="232d5-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="232d5-152">Aby uzyskać kompletną dyskusję na temat wszystkich zadań niezbędnych do utworzenia biblioteki ogólnego przeznaczenia, która tłumaczy drzewa wyrażeń na inny język, Przeczytaj [tę serię](https://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) przez otoczkę Warren.</span><span class="sxs-lookup"><span data-stu-id="232d5-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](https://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) by Matt Warren.</span></span> <span data-ttu-id="232d5-153">Szczegółowe informacje na temat sposobu tłumaczenia dowolnego kodu, który może znajdować się w drzewie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="232d5-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="232d5-154">Mam nadzieję, że już widzisz prawdziwą moc drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="232d5-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="232d5-155">Możesz sprawdzić zestaw kodu, wprowadzić wszelkie zmiany w tym kodzie i wykonać zmienioną wersję.</span><span class="sxs-lookup"><span data-stu-id="232d5-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="232d5-156">Ponieważ drzewa wyrażeń są niezmienne, można utworzyć nowe drzewa przy użyciu składników istniejących drzew.</span><span class="sxs-lookup"><span data-stu-id="232d5-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="232d5-157">Minimalizuje to ilość pamięci wymaganej do utworzenia zmodyfikowanych drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="232d5-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="232d5-158">Następne — sumowanie</span><span class="sxs-lookup"><span data-stu-id="232d5-158">Next -- Summing up</span></span>](expression-trees-summary.md)
