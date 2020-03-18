---
title: Tłumaczenie drzew wyrażeń
description: Dowiedz się, jak odwiedzić każdy węzeł w drzewie wyrażeń podczas tworzenia zmodyfikowanej kopii tego drzewa wyrażeń.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: f60c447d5c89aa83f85073e642e621608131ed8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76115775"
---
# <a name="translate-expression-trees"></a><span data-ttu-id="cebaf-103">Przetłumacz drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="cebaf-103">Translate expression trees</span></span>

[<span data-ttu-id="cebaf-104">Poprzedni -- Budowanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="cebaf-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="cebaf-105">W tej ostatniej sekcji dowiesz się, jak odwiedzić każdy węzeł w drzewie wyrażeń podczas tworzenia zmodyfikowanej kopii tego drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="cebaf-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="cebaf-106">Są to techniki, które będą używane w dwóch ważnych scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="cebaf-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="cebaf-107">Pierwszym z nich jest zrozumienie algorytmów wyrażonych przez drzewo wyrażeń, dzięki czemu można je przetłumaczyć na inne środowisko.</span><span class="sxs-lookup"><span data-stu-id="cebaf-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="cebaf-108">Drugi to, kiedy chcesz zmienić algorytm, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="cebaf-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="cebaf-109">Może to być dodanie rejestrowania, przechwytywania wywołań metody i śledzenie ich lub innych celów.</span><span class="sxs-lookup"><span data-stu-id="cebaf-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="cebaf-110">Tłumaczenie polega na odwiedzeniu</span><span class="sxs-lookup"><span data-stu-id="cebaf-110">Translating is Visiting</span></span>

<span data-ttu-id="cebaf-111">Kod, który tworzysz w celu przetłumaczenia drzewa wyrażeń jest rozszerzeniem tego, co już widziałeś, aby odwiedzić wszystkie węzły w drzewie.</span><span class="sxs-lookup"><span data-stu-id="cebaf-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="cebaf-112">Po przetłumaczeniu drzewa wyrażeń, odwiedź wszystkie węzły i podczas ich wizyty, zbudować nowe drzewo.</span><span class="sxs-lookup"><span data-stu-id="cebaf-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="cebaf-113">Nowe drzewo może zawierać odwołania do oryginalnych węzłów lub nowe węzły, które zostały umieszczone w drzewie.</span><span class="sxs-lookup"><span data-stu-id="cebaf-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="cebaf-114">Zobaczmy to w akcji, odwiedzając drzewo wyrażeń i tworząc nowe drzewo z niektórymi węzłami zastępczymi.</span><span class="sxs-lookup"><span data-stu-id="cebaf-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="cebaf-115">W tym przykładzie zastąpmy dowolną stałą stałą, która jest dziesięć razy większa.</span><span class="sxs-lookup"><span data-stu-id="cebaf-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="cebaf-116">W przeciwnym razie pozostawimy drzewo wyrażeń nienaruszone.</span><span class="sxs-lookup"><span data-stu-id="cebaf-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="cebaf-117">Zamiast odczytywać wartość stałej i zastępować ją nową stałą, dokonamy tego zastąpienia, zastępując węzeł stały nowym węzłem, który wykonuje mnożenie.</span><span class="sxs-lookup"><span data-stu-id="cebaf-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="cebaf-118">W tym miejscu po znalezieniu stałego węzła można utworzyć nowy węzeł mnożenia, `10`którego podrzędne są oryginalną stałą, a stała:</span><span class="sxs-lookup"><span data-stu-id="cebaf-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

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

<span data-ttu-id="cebaf-119">Zastępując oryginalny węzeł substytutem, powstaje nowe drzewo, które zawiera nasze modyfikacje.</span><span class="sxs-lookup"><span data-stu-id="cebaf-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="cebaf-120">Możemy to sprawdzić, kompilując i wykonując zastąpione drzewo.</span><span class="sxs-lookup"><span data-stu-id="cebaf-120">We can verify that by compiling and executing the replaced tree.</span></span>

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

<span data-ttu-id="cebaf-121">Tworzenie nowego drzewa jest kombinacją odwiedzania węzłów w istniejącym drzewie i tworzenia nowych węzłów i wstawiania ich do drzewa.</span><span class="sxs-lookup"><span data-stu-id="cebaf-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="cebaf-122">W tym przykładzie pokazano znaczenie drzewa wyrażenie jest niezmienne.</span><span class="sxs-lookup"><span data-stu-id="cebaf-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="cebaf-123">Należy zauważyć, że nowe drzewo utworzone powyżej zawiera mieszaninę nowo utworzonych węzłów i węzłów z istniejącego drzewa.</span><span class="sxs-lookup"><span data-stu-id="cebaf-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="cebaf-124">Jest to bezpieczne, ponieważ węzłów w istniejącym drzewie nie można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="cebaf-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="cebaf-125">Może to spowodować znaczną wydajność pamięci.</span><span class="sxs-lookup"><span data-stu-id="cebaf-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="cebaf-126">Te same węzły mogą być używane w całym drzewie lub w wielu drzewach wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="cebaf-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="cebaf-127">Ponieważ węzłów nie można modyfikować, ten sam węzeł może być ponownie użyty, gdy jest to potrzebne.</span><span class="sxs-lookup"><span data-stu-id="cebaf-127">Since nodes can't be modified, the same node can be reused whenever it's needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="cebaf-128">Przechodzenie przez i wykonywanie dodawania</span><span class="sxs-lookup"><span data-stu-id="cebaf-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="cebaf-129">Sprawdźmy to, budując drugiego odwiedzającego, który przechodzi przez drzewo węzłów dodawania i oblicza wynik.</span><span class="sxs-lookup"><span data-stu-id="cebaf-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="cebaf-130">Możesz to zrobić, dokonując kilku modyfikacji dla odwiedzającego, który widziałeś do tej pory.</span><span class="sxs-lookup"><span data-stu-id="cebaf-130">You can do this by making a couple modifications to the visitor that you've seen so far.</span></span> <span data-ttu-id="cebaf-131">W tej nowej wersji użytkownik zwróci częściową sumę operacji dodawania do tego momentu.</span><span class="sxs-lookup"><span data-stu-id="cebaf-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="cebaf-132">Dla wyrażenia stałego jest to po prostu wartość wyrażenia stałego.</span><span class="sxs-lookup"><span data-stu-id="cebaf-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="cebaf-133">Dla wyrażenia dodawania wynik jest sumą lewego i prawego argumentów, gdy te drzewa zostały przeciągnięte.</span><span class="sxs-lookup"><span data-stu-id="cebaf-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

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

<span data-ttu-id="cebaf-134">Jest tu sporo kodu, ale pojęcia są bardzo przystępne.</span><span class="sxs-lookup"><span data-stu-id="cebaf-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="cebaf-135">Ten kod odwiedza dzieci w dogłębnym pierwszym wyszukiwaniu.</span><span class="sxs-lookup"><span data-stu-id="cebaf-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="cebaf-136">Gdy napotka węzeł stały, gość zwraca wartość stałej.</span><span class="sxs-lookup"><span data-stu-id="cebaf-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="cebaf-137">Po użytkownik odwiedził oba dzieci, te dzieci będą obliczać sumę obliczoną dla tego poddrzewa.</span><span class="sxs-lookup"><span data-stu-id="cebaf-137">After the visitor has visited both children, those children will have computed the sum computed for that subtree.</span></span> <span data-ttu-id="cebaf-138">Węzeł dodawania można teraz obliczyć jego sumę.</span><span class="sxs-lookup"><span data-stu-id="cebaf-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="cebaf-139">Po odwiedzeniu wszystkich węzłów w drzewie wyrażeń suma zostanie obliczona.</span><span class="sxs-lookup"><span data-stu-id="cebaf-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="cebaf-140">Można śledzić wykonanie, uruchamiając przykład w debugerze i śledzenia wykonania.</span><span class="sxs-lookup"><span data-stu-id="cebaf-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="cebaf-141">Ułatwiamy śledzenie, jak węzły są analizowane i jak suma jest obliczana przez przechodzenie przez drzewo.</span><span class="sxs-lookup"><span data-stu-id="cebaf-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by traversing the tree.</span></span> <span data-ttu-id="cebaf-142">Oto zaktualizowana wersja metody Agreguj, która zawiera sporo informacji o śledzeniu:</span><span class="sxs-lookup"><span data-stu-id="cebaf-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

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

<span data-ttu-id="cebaf-143">Uruchomienie go na tym samym wyrażeniu daje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="cebaf-143">Running it on the same expression yields the following output:</span></span>

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

<span data-ttu-id="cebaf-144">Śledzenie danych wyjściowych i postępuj zgodnie z powyższym kodem.</span><span class="sxs-lookup"><span data-stu-id="cebaf-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="cebaf-145">Powinieneś być w stanie ustalić, jak kod odwiedza każdy węzeł i oblicza sumę, jak przechodzi przez drzewo i znajduje sumę.</span><span class="sxs-lookup"><span data-stu-id="cebaf-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="cebaf-146">Teraz przyjrzyjmy się innemu przebiegowi, `sum1`z wyrażeniem podanym przez:</span><span class="sxs-lookup"><span data-stu-id="cebaf-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="cebaf-147">Oto dane wyjściowe z badania tego wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="cebaf-147">Here's the output from examining this expression:</span></span>

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

<span data-ttu-id="cebaf-148">Podczas gdy ostateczna odpowiedź jest taka sama, przechodzenie drzewa jest zupełnie inna.</span><span class="sxs-lookup"><span data-stu-id="cebaf-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="cebaf-149">Węzły są przemieszczane w innej kolejności, ponieważ drzewo zostało zbudowane z różnych operacji występujących najpierw.</span><span class="sxs-lookup"><span data-stu-id="cebaf-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="cebaf-150">Dodatkowe informacje</span><span class="sxs-lookup"><span data-stu-id="cebaf-150">Learning More</span></span>

<span data-ttu-id="cebaf-151">W tym przykładzie przedstawiono mały podzbiór kodu, który można utworzyć do przechodzenia i interpretować algorytmy reprezentowane przez drzewo wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="cebaf-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="cebaf-152">Aby uzyskać pełną dyskusję na temat wszystkich prac niezbędnych do zbudowania biblioteki ogólnego przeznaczenia, która tłumaczy drzewa wyrażeń na inny język, przeczytaj [tę serię autorstwa](https://docs.microsoft.com/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) Matta Warrena.</span><span class="sxs-lookup"><span data-stu-id="cebaf-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](https://docs.microsoft.com/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) by Matt Warren.</span></span> <span data-ttu-id="cebaf-153">Przechodzi do bardzo szczegółowo, jak przetłumaczyć dowolny kod, który można znaleźć w drzewie wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="cebaf-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="cebaf-154">Mam nadzieję, że widzieliście teraz prawdziwą moc drzew ekspresji.</span><span class="sxs-lookup"><span data-stu-id="cebaf-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="cebaf-155">Można sprawdzić zestaw kodu, wprowadzić wszelkie zmiany, które chcesz do tego kodu i wykonać zmienioną wersję.</span><span class="sxs-lookup"><span data-stu-id="cebaf-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="cebaf-156">Ponieważ drzewa wyrażeń są niezmienne, można utworzyć nowe drzewa przy użyciu składników istniejących drzew.</span><span class="sxs-lookup"><span data-stu-id="cebaf-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="cebaf-157">Minimalizuje to ilość pamięci potrzebnej do utworzenia drzew wyrażeń zmodyfikowanych.</span><span class="sxs-lookup"><span data-stu-id="cebaf-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="cebaf-158">Dalej -- Podsumowując</span><span class="sxs-lookup"><span data-stu-id="cebaf-158">Next -- Summing up</span></span>](expression-trees-summary.md)
