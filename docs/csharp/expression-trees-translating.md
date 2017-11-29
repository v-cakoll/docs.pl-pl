---
title: "Tłumaczenie drzew wyrażeń"
description: "Dowiedz się, jak można znaleźć każdy węzeł w drzewie wyrażeń podczas kompilowania zmodyfikowane kopię tego drzewa wyrażenia."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: 602a17591d27ebfd098516453b9028bca37ad5e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="translating-expression-trees"></a><span data-ttu-id="641e1-104">Tłumaczenie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="641e1-104">Translating Expression Trees</span></span>

[<span data-ttu-id="641e1-105">Poprzednie — Tworzenie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="641e1-105">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="641e1-106">W tej sekcji końcowego dowiesz się, jak do odwiedzenia każdy węzeł w drzewie wyrażeń podczas kompilowania zmodyfikowane kopię tego drzewa wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="641e1-106">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="641e1-107">Są to te techniki, które będą używane w przypadku dwóch scenariuszy ważne.</span><span class="sxs-lookup"><span data-stu-id="641e1-107">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="641e1-108">Pierwsza to zrozumienie algorytmów wyrażone w drzewo wyrażenia, dzięki czemu można można przetłumaczyć innego środowiska.</span><span class="sxs-lookup"><span data-stu-id="641e1-108">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="641e1-109">Drugim jest, jeśli chcesz zmienić algorytmu, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="641e1-109">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="641e1-110">Może to być dodać rejestrowania, przechwycenia wywołania metody i śledzenie ich lub innych celów.</span><span class="sxs-lookup"><span data-stu-id="641e1-110">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="641e1-111">Tłumaczenie odwiedzania</span><span class="sxs-lookup"><span data-stu-id="641e1-111">Translating is Visiting</span></span>

<span data-ttu-id="641e1-112">Kod kompilacji do drzewa wyrażeń przetłumaczenia jest rozszerzeniem co już w tym samouczku odwiedzać wszystkich węzłów w drzewie.</span><span class="sxs-lookup"><span data-stu-id="641e1-112">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="641e1-113">Tłumaczenie drzewo wyrażenia, odwiedź stronę wszystkich węzłów, a podczas odwiedzania je, należy utworzyć nowe drzewo.</span><span class="sxs-lookup"><span data-stu-id="641e1-113">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="641e1-114">Nowe drzewo może zawierać odwołania do oryginalnego węzłów lub nowe węzły, które zostały umieszczone w drzewie.</span><span class="sxs-lookup"><span data-stu-id="641e1-114">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="641e1-115">Zobaczmy, to w akcji odwiedzając drzewo wyrażeń i tworzenia nowego drzewa węzły zastąpienia.</span><span class="sxs-lookup"><span data-stu-id="641e1-115">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="641e1-116">W tym przykładzie załóżmy Zamień wszystkie stała stałą dziesięć razy większy.</span><span class="sxs-lookup"><span data-stu-id="641e1-116">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="641e1-117">W przeciwnym razie pozostanie drzewa wyrażenia bez zmian.</span><span class="sxs-lookup"><span data-stu-id="641e1-117">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="641e1-118">Zamiast odczytu wartości stałej i zastępowanie stałą nowe, wybierzemy zamiany przez zamianę stałej węzła nowego węzła, który wykonuje mnożenia.</span><span class="sxs-lookup"><span data-stu-id="641e1-118">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="641e1-119">W tym miejscu po znalezieniu stałej węzła tworzenia nowego węzła mnożenia, którego elementy podrzędne są oryginalne stała i stałą `10`:</span><span class="sxs-lookup"><span data-stu-id="641e1-119">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

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

<span data-ttu-id="641e1-120">Przez zastąpienie oryginalnego węzła podstaw, nowe drzewo został uformowany zawierający naszych modyfikacje.</span><span class="sxs-lookup"><span data-stu-id="641e1-120">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="641e1-121">Firma Microsoft może Sprawdź, czy kompilowanie i wykonywania zastąpionego drzewa.</span><span class="sxs-lookup"><span data-stu-id="641e1-121">We can verify that by compiling and executing the replaced tree.</span></span>

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

<span data-ttu-id="641e1-122">Tworzenie nowego drzewa jest kombinacją odwiedzając węzłów w drzewie istniejących i tworzenia nowych węzłów i wstawianie ich do drzewa.</span><span class="sxs-lookup"><span data-stu-id="641e1-122">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="641e1-123">Ten przykład przedstawia znaczenie jest niezmienialny drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="641e1-123">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="641e1-124">Należy zauważyć, że nowe drzewo utworzone powyżej zawiera węzły nowo utworzona i węzłów z istniejącego drzewa.</span><span class="sxs-lookup"><span data-stu-id="641e1-124">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="641e1-125">To bezpieczne, ponieważ nie można zmodyfikować węzłów w drzewie istniejących.</span><span class="sxs-lookup"><span data-stu-id="641e1-125">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="641e1-126">Może to spowodować pamięci znaczących korzyści.</span><span class="sxs-lookup"><span data-stu-id="641e1-126">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="641e1-127">W drzewie lub w wielu drzew wyrażeń można tych samych węzłów.</span><span class="sxs-lookup"><span data-stu-id="641e1-127">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="641e1-128">Ponieważ nie można modyfikować, może być tym samym węźle ponownie po każdej zmianie jego uruchomienie.</span><span class="sxs-lookup"><span data-stu-id="641e1-128">Since nodes can't be modified, the same node can be reused whenever its needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="641e1-129">Przeglądanie i wykonywania dodatku</span><span class="sxs-lookup"><span data-stu-id="641e1-129">Traversing and Executing an Addition</span></span>

<span data-ttu-id="641e1-130">Umożliwia to sprawdzić, tworząc drugi obiekt odwiedzający, który przegląda drzewo dodawania węzłów i oblicza wynik.</span><span class="sxs-lookup"><span data-stu-id="641e1-130">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="641e1-131">Można to zrobić przez kilka vistor, który w tym samouczku wykonanej do tej pory.</span><span class="sxs-lookup"><span data-stu-id="641e1-131">You can do this by making a couple modifications to the vistor that you've seen so far.</span></span> <span data-ttu-id="641e1-132">W tej nowej wersji obiektu odwiedzającego zwróci sumy częściowe operacja dodawania do tego punktu.</span><span class="sxs-lookup"><span data-stu-id="641e1-132">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="641e1-133">Wyrażenie stałe jest po prostu wartość wyrażenia stałej.</span><span class="sxs-lookup"><span data-stu-id="641e1-133">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="641e1-134">Dla wyrażenia dodanie wynik to suma argumentów operacji lewy i prawy po przejść wzdłuż tych drzew.</span><span class="sxs-lookup"><span data-stu-id="641e1-134">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

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

<span data-ttu-id="641e1-135">Występuje dość nieco tutaj kod, ale pojęcia są bardzo przystępne.</span><span class="sxs-lookup"><span data-stu-id="641e1-135">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="641e1-136">Ten kod odwiedza dzieci w wyszukiwaniu pierwszy głębokość.</span><span class="sxs-lookup"><span data-stu-id="641e1-136">This code visits children in a depth first search.</span></span> <span data-ttu-id="641e1-137">Po napotkaniu stałej węzła obiektu odwiedzającego zwraca wartość stałej.</span><span class="sxs-lookup"><span data-stu-id="641e1-137">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="641e1-138">Po obiekt odwiedzający odwiedził obu elementów podrzędnych, te dzieci będzie obliczana sum obliczonych dla tego poddrzewa.</span><span class="sxs-lookup"><span data-stu-id="641e1-138">After the visitor has visited both children, those children will have computed the sum computed for that sub-tree.</span></span> <span data-ttu-id="641e1-139">Dodawanie węzła teraz można obliczyć jego sum.</span><span class="sxs-lookup"><span data-stu-id="641e1-139">The addition node can now compute its sum.</span></span>
<span data-ttu-id="641e1-140">Po odwiedzone wszystkie węzły na drzewo wyrażenia, Suma zostanie obliczone.</span><span class="sxs-lookup"><span data-stu-id="641e1-140">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="641e1-141">Można śledzić realizację uruchamiając próbki w debugerze i śledzenie realizacji.</span><span class="sxs-lookup"><span data-stu-id="641e1-141">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="641e1-142">Załóżmy ułatwić śledzenie jak są analizowane węzły i jak suma jest obliczana przez travsersing drzewa.</span><span class="sxs-lookup"><span data-stu-id="641e1-142">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by travsersing the tree.</span></span> <span data-ttu-id="641e1-143">W tym miejscu jest zaktualizowana wersja metoda agregacji, która zawiera dość bit informacje śledzenia:</span><span class="sxs-lookup"><span data-stu-id="641e1-143">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

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

<span data-ttu-id="641e1-144">Uruchomienie jej w tym samym wyrażeniu daje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="641e1-144">Running it on the same expression yields the following output:</span></span>

```
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

<span data-ttu-id="641e1-145">Dane wyjściowe śledzenia i odbiorze w powyższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="641e1-145">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="641e1-146">Można będzie działać jak kod odwiedza każdego węzła i oblicza sumę, ponieważ przechodzi przez drzewa i wyszukuje suma.</span><span class="sxs-lookup"><span data-stu-id="641e1-146">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="641e1-147">Teraz Przyjrzyjmy różnych Uruchom za pomocą wyrażenia przez `sum1`:</span><span class="sxs-lookup"><span data-stu-id="641e1-147">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="641e1-148">Poniżej przedstawiono dane wyjściowe z badanie tego wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="641e1-148">Here's the output from examining this expression:</span></span>

```
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

<span data-ttu-id="641e1-149">Podczas końcowego odpowiedzi są takie same, całkowicie różni się przechodzenia drzewa.</span><span class="sxs-lookup"><span data-stu-id="641e1-149">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="641e1-150">Węzły są pokonać w innej kolejności, ponieważ drzewa został skonstruowany przy różnych operacji wykonywanych w pierwszym.</span><span class="sxs-lookup"><span data-stu-id="641e1-150">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="641e1-151">Dowiedzieć się więcej</span><span class="sxs-lookup"><span data-stu-id="641e1-151">Learning More</span></span>

<span data-ttu-id="641e1-152">W tym przykładzie pokazano małego podzbioru kod, który będzie kompilacji do przechodzenia i interpretowania algorytmów reprezentowany przez drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="641e1-152">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="641e1-153">Aby uzyskać szczegółowe omówienie pracy niezbędne do tworzenia biblioteki ogólnego przeznaczenia, który tłumaczy drzew wyrażeń do innego języka, przeczytaj [tej serii](http://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) przez Matt Warren.</span><span class="sxs-lookup"><span data-stu-id="641e1-153">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](http://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) by Matt Warren.</span></span> <span data-ttu-id="641e1-154">Przechodzi ona bardzo szczegółowe na temat sposobu tłumaczenia kodu, jakie można znaleźć w drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="641e1-154">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="641e1-155">Mam nadzieję, że obecnie w tym samouczku true możliwości drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="641e1-155">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="641e1-156">Można zbadać zestawu kodu, wprowadź wszelkie zmiany, które chcesz do kodu i wykonaj zmienionych wersji.</span><span class="sxs-lookup"><span data-stu-id="641e1-156">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="641e1-157">Ponieważ drzewa wyrażeń są niezmienne, można utworzyć nowego drzew przy użyciu składników istniejącego drzewa.</span><span class="sxs-lookup"><span data-stu-id="641e1-157">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="641e1-158">Pozwala to zmniejszyć ilość pamięci potrzebnej do tworzenia drzewa wyrażeń zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="641e1-158">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="641e1-159">Następnie — Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="641e1-159">Next -- Summing up</span></span>](expression-trees-summary.md)
