---
title: Tłumaczenie drzew wyrażeń
description: Dowiedz się, jak odwiedzać każdy węzeł w drzewie wyrażenia podczas tworzenia zmodyfikowanej kopii tego drzewa wyrażenia.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: a4cb40e439726e5fff60fe697da70d61bb24cb68
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937221"
---
# <a name="translating-expression-trees"></a><span data-ttu-id="87562-103">Tłumaczenie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="87562-103">Translating Expression Trees</span></span>

[<span data-ttu-id="87562-104">Poprzednie — Kompilowanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="87562-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="87562-105">W tej ostatniej sekcji dowiesz się, jak odwiedzać każdy węzeł w drzewie wyrażenia podczas tworzenia zmodyfikowanej kopii tego drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="87562-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="87562-106">Są to techniki, które będą używane w dwóch ważnych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="87562-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="87562-107">Pierwszy polega na zrozumieniu algorytmów wyrażonych przez drzewo wyrażenia, aby można było je przetłumaczyć na inne środowisko.</span><span class="sxs-lookup"><span data-stu-id="87562-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="87562-108">Druga jest zmiana algorytmu, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="87562-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="87562-109">Może to być dodanie rejestrowania, wywołanie metody przechwytywania i śledzenie ich lub inne cele.</span><span class="sxs-lookup"><span data-stu-id="87562-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="87562-110">Trwa odwiedzanie tłumaczenia</span><span class="sxs-lookup"><span data-stu-id="87562-110">Translating is Visiting</span></span>

<span data-ttu-id="87562-111">Kod, który tworzysz w celu przetłumaczenia drzewa wyrażenia, jest rozszerzeniem tego, co już widzisz, aby odwiedzić wszystkie węzły w drzewie.</span><span class="sxs-lookup"><span data-stu-id="87562-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="87562-112">W przypadku tłumaczenia drzewa wyrażenia odwiedzane są wszystkie węzły, a podczas odwiedzania można utworzyć nowe drzewo.</span><span class="sxs-lookup"><span data-stu-id="87562-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="87562-113">Nowe drzewo może zawierać odwołania do oryginalnych węzłów lub nowe węzły, które zostały umieszczone w drzewie.</span><span class="sxs-lookup"><span data-stu-id="87562-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="87562-114">Zobaczmy to w akcji, odwiedzając drzewo wyrażenia i tworząc nowe drzewo z niektórymi węzłami zastępczymi.</span><span class="sxs-lookup"><span data-stu-id="87562-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="87562-115">W tym przykładzie zamienimy każdą stałą na stałą o dziesięć razy większym.</span><span class="sxs-lookup"><span data-stu-id="87562-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="87562-116">W przeciwnym razie pozostawimy drzewo wyrażenia bez zmian.</span><span class="sxs-lookup"><span data-stu-id="87562-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="87562-117">Zamiast odczytywania wartości stałej i zamieniania jej na nową stałą, wprowadzimy tę zamianę, zastępując węzeł stały nowym węzłem, który wykonuje mnożenie.</span><span class="sxs-lookup"><span data-stu-id="87562-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="87562-118">W tym miejscu po znalezieniu stałego węzła utworzysz nowy węzeł mnożenia, którego elementy podrzędne są pierwotną stałą, a `10`stałej:</span><span class="sxs-lookup"><span data-stu-id="87562-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

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

<span data-ttu-id="87562-119">Zastępując pierwotny węzeł podstawianiem, tworzone jest nowe drzewo zawierające nasze modyfikacje.</span><span class="sxs-lookup"><span data-stu-id="87562-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="87562-120">Możemy sprawdzić, czy przez skompilowanie i wykonanie zastąpionego drzewa.</span><span class="sxs-lookup"><span data-stu-id="87562-120">We can verify that by compiling and executing the replaced tree.</span></span>

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

<span data-ttu-id="87562-121">Tworzenie nowego drzewa jest kombinacją odwiedzanych węzłów w istniejącym drzewie i tworzenie nowych węzłów i wstawianie ich do drzewa.</span><span class="sxs-lookup"><span data-stu-id="87562-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="87562-122">Ten przykład pokazuje ważność drzew wyrażeń, które są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="87562-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="87562-123">Należy zauważyć, że nowe drzewo utworzone powyżej zawiera kombinację nowo utworzonych węzłów i węzłów z istniejącego drzewa.</span><span class="sxs-lookup"><span data-stu-id="87562-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="87562-124">Jest to bezpieczne, ponieważ nie można modyfikować węzłów w istniejącym drzewie.</span><span class="sxs-lookup"><span data-stu-id="87562-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="87562-125">Może to spowodować znaczne zwiększenie wydajności pamięci.</span><span class="sxs-lookup"><span data-stu-id="87562-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="87562-126">Te same węzły można używać w całym drzewie lub w wielu drzewach wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="87562-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="87562-127">Ponieważ węzły nie mogą być modyfikowane, ten sam węzeł może być ponownie używany w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="87562-127">Since nodes can't be modified, the same node can be reused whenever its needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="87562-128">Przechodzenie i wykonywanie dodawania</span><span class="sxs-lookup"><span data-stu-id="87562-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="87562-129">Sprawdźmy to, tworząc drugiego odwiedzającego, który przeprowadzi drzewo węzłów dodawania i obliczy wynik.</span><span class="sxs-lookup"><span data-stu-id="87562-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="87562-130">Można to zrobić, wprowadzając kilka modyfikacji odwiedzanych do tej pory.</span><span class="sxs-lookup"><span data-stu-id="87562-130">You can do this by making a couple modifications to the visitor that you've seen so far.</span></span> <span data-ttu-id="87562-131">W tej nowej wersji odwiedzający zwróci częściową sumę operacji dodawania do tego punktu.</span><span class="sxs-lookup"><span data-stu-id="87562-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="87562-132">Wyrażenie stałe, które jest po prostu wartością wyrażenia stałej.</span><span class="sxs-lookup"><span data-stu-id="87562-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="87562-133">W przypadku wyrażenia dodawania wynik jest sumą argumentów operacji lewy i prawy, gdy te drzewa zostały przesunięte.</span><span class="sxs-lookup"><span data-stu-id="87562-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

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

<span data-ttu-id="87562-134">W tym miejscu jest dość dużo kodu, ale koncepcje są bardzo podejścia.</span><span class="sxs-lookup"><span data-stu-id="87562-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="87562-135">Ten kod wizytuje elementy podrzędne na głębokości pierwszego wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="87562-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="87562-136">Gdy napotka węzeł stały, odwiedzający zwraca wartość stałej.</span><span class="sxs-lookup"><span data-stu-id="87562-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="87562-137">Po odwiedzeniu obu elementów podrzędnych osoby odwiedzające będą obliczać sumę obliczoną dla tego poddrzewa.</span><span class="sxs-lookup"><span data-stu-id="87562-137">After the visitor has visited both children, those children will have computed the sum computed for that sub-tree.</span></span> <span data-ttu-id="87562-138">Węzeł dodawania może teraz obliczyć jego sumę.</span><span class="sxs-lookup"><span data-stu-id="87562-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="87562-139">Po odwiedzeniu wszystkich węzłów w drzewie wyrażenia suma zostanie obliczona.</span><span class="sxs-lookup"><span data-stu-id="87562-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="87562-140">Wykonanie można śledzić przez uruchomienie przykładu w debugerze i śledzenie wykonania.</span><span class="sxs-lookup"><span data-stu-id="87562-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="87562-141">Ułatwiamy śledzenie sposobu analizowania węzłów i sposobu obliczania sumy przez przechodzenie przez drzewo.</span><span class="sxs-lookup"><span data-stu-id="87562-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by traversing the tree.</span></span> <span data-ttu-id="87562-142">Oto zaktualizowana wersja metody agregującej, która zawiera dość kilka informacji o śledzeniu:</span><span class="sxs-lookup"><span data-stu-id="87562-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

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

<span data-ttu-id="87562-143">Uruchomienie go w tym samym wyrażeniu daje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="87562-143">Running it on the same expression yields the following output:</span></span>

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

<span data-ttu-id="87562-144">Śledź dane wyjściowe i postępuj zgodnie z powyższym kodem.</span><span class="sxs-lookup"><span data-stu-id="87562-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="87562-145">Powinien być w stanie dowiedzieć się, jak kod odwiedza każdy węzeł i oblicza sumę w miarę przechodzenia przez drzewo i odnajduje sumę.</span><span class="sxs-lookup"><span data-stu-id="87562-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="87562-146">Teraz przyjrzyjmy się różnemu przebiegowi z wyrażeniem podanym przez `sum1`:</span><span class="sxs-lookup"><span data-stu-id="87562-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="87562-147">Oto dane wyjściowe badania tego wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="87562-147">Here's the output from examining this expression:</span></span>

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

<span data-ttu-id="87562-148">Gdy ostateczna odpowiedź jest taka sama, przechodzenie drzewa jest zupełnie inne.</span><span class="sxs-lookup"><span data-stu-id="87562-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="87562-149">Węzły są przesyłane w innej kolejności, ponieważ drzewo zostało skonstruowane z różnymi operacjami wykonywanymi jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="87562-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="87562-150">Dodatkowe informacje</span><span class="sxs-lookup"><span data-stu-id="87562-150">Learning More</span></span>

<span data-ttu-id="87562-151">Ten przykład pokazuje mały podzbiór kodu, który będzie przepływał i interpretuje algorytmy reprezentowane przez drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="87562-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="87562-152">Aby uzyskać kompletną dyskusję na temat wszystkich zadań niezbędnych do utworzenia biblioteki ogólnego przeznaczenia, która tłumaczy drzewa wyrażeń na inny język, Przeczytaj [tę serię](https://docs.microsoft.com/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) przez otoczkę Warren.</span><span class="sxs-lookup"><span data-stu-id="87562-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](https://docs.microsoft.com/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) by Matt Warren.</span></span> <span data-ttu-id="87562-153">Szczegółowe informacje na temat sposobu tłumaczenia dowolnego kodu, który może znajdować się w drzewie wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="87562-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="87562-154">Mam nadzieję, że już widzisz prawdziwą moc drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="87562-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="87562-155">Możesz sprawdzić zestaw kodu, wprowadzić wszelkie zmiany w tym kodzie i wykonać zmienioną wersję.</span><span class="sxs-lookup"><span data-stu-id="87562-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="87562-156">Ponieważ drzewa wyrażeń są niezmienne, można utworzyć nowe drzewa przy użyciu składników istniejących drzew.</span><span class="sxs-lookup"><span data-stu-id="87562-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="87562-157">Minimalizuje to ilość pamięci wymaganej do utworzenia zmodyfikowanych drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="87562-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="87562-158">Następne — sumowanie</span><span class="sxs-lookup"><span data-stu-id="87562-158">Next -- Summing up</span></span>](expression-trees-summary.md)
