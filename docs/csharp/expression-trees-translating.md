---
title: Tłumaczenie drzew wyrażeń
description: Dowiedz się, jak znaleźć każdy węzeł w drzewie wyrażeń podczas kompilowania zmodyfikowanej kopii takiego drzewa wyrażeń.
ms.date: 06/20/2016
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: bd4aec2ef34e4dc972ae867c6b5070f92dcbc498
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45678949"
---
# <a name="translating-expression-trees"></a><span data-ttu-id="79d91-103">Tłumaczenie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="79d91-103">Translating Expression Trees</span></span>

[<span data-ttu-id="79d91-104">Poprzednie — Tworzenie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="79d91-104">Previous -- Building Expressions</span></span>](expression-trees-building.md)

<span data-ttu-id="79d91-105">W tej sekcji końcowej dowiesz się, jak do odwiedzenia każdego węzła w drzewie wyrażeń podczas kompilowania zmodyfikowanej kopii takiego drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="79d91-105">In this final section, you'll learn how to visit each node in an expression tree while building a modified copy of that expression tree.</span></span> <span data-ttu-id="79d91-106">Są to technik, które będą używane w przypadku dwóch scenariuszy ważne.</span><span class="sxs-lookup"><span data-stu-id="79d91-106">These are the techniques that you will use in two important scenarios.</span></span> <span data-ttu-id="79d91-107">Pierwszy to zrozumienie algorytmy wyrażona przez drzewo wyrażenia, dzięki czemu mogą być tłumaczone w innym środowisku.</span><span class="sxs-lookup"><span data-stu-id="79d91-107">The first is to understand the algorithms expressed by an expression tree so that it can be translated into another environment.</span></span> <span data-ttu-id="79d91-108">Drugim jest, jeśli chcesz zmienić algorytmu, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="79d91-108">The second is when you want to change the algorithm that has been created.</span></span> <span data-ttu-id="79d91-109">Może to być dodawanie rejestrowania przechwytuje wywołania metody oraz śledzić ich lub innych celów.</span><span class="sxs-lookup"><span data-stu-id="79d91-109">This might be to add logging, intercept method calls and track them, or other purposes.</span></span>

## <a name="translating-is-visiting"></a><span data-ttu-id="79d91-110">Tłumaczenie jest odwiedzający</span><span class="sxs-lookup"><span data-stu-id="79d91-110">Translating is Visiting</span></span>

<span data-ttu-id="79d91-111">Kod kompilacji do translacji drzewa wyrażenie jest rozszerzeniem już opisane do odwiedzenia wszystkich węzłów w drzewie.</span><span class="sxs-lookup"><span data-stu-id="79d91-111">The code you build to translate an expression tree is an extension of what you've already seen to visit all the nodes in a tree.</span></span> <span data-ttu-id="79d91-112">Tłumaczenie jest drzewo wyrażenia, odwiedź stronę wszystkie węzły, a podczas odwiedzania ich, tworzenie nowego drzewa.</span><span class="sxs-lookup"><span data-stu-id="79d91-112">When you translate an expression tree, you visit all the nodes, and while visiting them, build the new tree.</span></span> <span data-ttu-id="79d91-113">Nowe drzewo może zawierać odwołania do oryginalnego węzłów lub nowe węzły, które zostały umieszczone w drzewie.</span><span class="sxs-lookup"><span data-stu-id="79d91-113">The new tree may contain references to the original nodes, or new nodes that you have placed in the tree.</span></span>

<span data-ttu-id="79d91-114">Zobaczmy, to w działaniu strony drzewo wyrażenia, tworzenie nowego drzewa węzły zastępczy.</span><span class="sxs-lookup"><span data-stu-id="79d91-114">Let's see this in action by visiting an expression tree, and creating a new tree with some replacement nodes.</span></span> <span data-ttu-id="79d91-115">W tym przykładzie Przyjrzyjmy zastąpić dowolną stałą ze stałą, której jest dziesięć razy większy.</span><span class="sxs-lookup"><span data-stu-id="79d91-115">In this example, let's replace any constant with a constant that is ten times larger.</span></span>
<span data-ttu-id="79d91-116">W przeciwnym razie pozostawimy drzewa wyrażeń bez zmian.</span><span class="sxs-lookup"><span data-stu-id="79d91-116">Otherwise, we'll leave the expression tree intact.</span></span> <span data-ttu-id="79d91-117">Zamiast odczytu wartości stałej i zamianę stałą nowe, My sprawiamy, żeby ta zastępowania, zastępując stałej węzła nowy węzeł, który wykonuje mnożenia.</span><span class="sxs-lookup"><span data-stu-id="79d91-117">Rather than reading the value of the constant, and replacing it with a new constant, we'll make this replacement by replacing the constant node with a new node that performs the multiplication.</span></span>

<span data-ttu-id="79d91-118">W tym miejscu po odnalezieniu stałej węzła tworzysz nowy węzeł mnożenia, którego elementy podrzędne są oryginalne stała i stałą `10`:</span><span class="sxs-lookup"><span data-stu-id="79d91-118">Here, once you find a constant node, you create a new multiplication node whose children are the original constant, and the constant `10`:</span></span>

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

<span data-ttu-id="79d91-119">Przez zastąpienie pierwotnego węzła zastępczych, nowego drzewa, tworzy zawiera modyfikacje.</span><span class="sxs-lookup"><span data-stu-id="79d91-119">By replacing the original node with the substitute, a new tree is formed that contains our modifications.</span></span> <span data-ttu-id="79d91-120">Zweryfikowanie, kompilując i wykonywania drzewie zastąpione.</span><span class="sxs-lookup"><span data-stu-id="79d91-120">We can verify that by compiling and executing the replaced tree.</span></span>

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

<span data-ttu-id="79d91-121">Tworzenie nowego drzewa jest kombinacją odwiedzający węzły w istniejącym drzewie i tworzenia nowych węzłów i wstawiania ich do drzewa.</span><span class="sxs-lookup"><span data-stu-id="79d91-121">Building a new tree is a combination of visiting the nodes in the existing tree, and creating new nodes and inserting them into the tree.</span></span>

<span data-ttu-id="79d91-122">W tym przykładzie przedstawiono znaczenie drzew wyrażeń, które są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="79d91-122">This example shows the importance of expression trees being immutable.</span></span> <span data-ttu-id="79d91-123">Należy zauważyć, że nowe drzewo utworzonego powyżej zawiera kombinację nowo utworzony węzłów i węzłów z istniejącym drzewie.</span><span class="sxs-lookup"><span data-stu-id="79d91-123">Notice that the new tree created above contains a mixture of newly created nodes, and nodes from the existing tree.</span></span> <span data-ttu-id="79d91-124">To bezpieczne, ponieważ nie można zmodyfikować węzły w istniejącym drzewie.</span><span class="sxs-lookup"><span data-stu-id="79d91-124">That's safe, because the nodes in the existing tree cannot be modified.</span></span> <span data-ttu-id="79d91-125">Może to spowodować, że pamięć znaczne korzyści.</span><span class="sxs-lookup"><span data-stu-id="79d91-125">This can result in significant memory efficiencies.</span></span>
<span data-ttu-id="79d91-126">Tym samym węzłów może służyć w całym drzewie lub w wielu drzewach wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="79d91-126">The same nodes can be used throughout a tree, or in multiple expression trees.</span></span> <span data-ttu-id="79d91-127">Ponieważ nie można modyfikować, tego samego węzła może być ponownie użyte w każdym przypadku, gdy jego potrzebne.</span><span class="sxs-lookup"><span data-stu-id="79d91-127">Since nodes can't be modified, the same node can be reused whenever its needed.</span></span>

## <a name="traversing-and-executing-an-addition"></a><span data-ttu-id="79d91-128">Przeglądanie i wykonywanie dodatku</span><span class="sxs-lookup"><span data-stu-id="79d91-128">Traversing and Executing an Addition</span></span>

<span data-ttu-id="79d91-129">Możemy to sprawdzić, tworząc drugi obiekt odwiedzający, który przegląda drzewo dodawania węzłów i oblicza wynik.</span><span class="sxs-lookup"><span data-stu-id="79d91-129">Let's verify this by building a second visitor that walks the tree of addition nodes and computes the result.</span></span> <span data-ttu-id="79d91-130">Można to zrobić, wprowadzając kilka zmian vistor, który w tym samouczku do tej pory.</span><span class="sxs-lookup"><span data-stu-id="79d91-130">You can do this by making a couple modifications to the vistor that you've seen so far.</span></span> <span data-ttu-id="79d91-131">W tej nowej wersji odwiedzający zwróci częściowej sumy operacji dodawania do tej pory.</span><span class="sxs-lookup"><span data-stu-id="79d91-131">In this new version, the visitor will return the partial sum of the addition operation up to this point.</span></span> <span data-ttu-id="79d91-132">Wyrażenie stałe to po prostu wartość wyrażenie stałe.</span><span class="sxs-lookup"><span data-stu-id="79d91-132">For a constant expression, that is simply the value of the constant expression.</span></span> <span data-ttu-id="79d91-133">Wyrażenie dodawania wynik jest sumę argumentów operacji po lewej i prawej stronie, gdy-przenoszone tych drzew.</span><span class="sxs-lookup"><span data-stu-id="79d91-133">For an addition expression, the result is the sum of the left and right operands, once those trees have been traversed.</span></span>

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

<span data-ttu-id="79d91-134">Brak znacznej liczby tutaj kod, ale podstawowe koncepcje są bardzo przystępne.</span><span class="sxs-lookup"><span data-stu-id="79d91-134">There's quite a bit of code here, but the concepts are very approachable.</span></span>
<span data-ttu-id="79d91-135">Ten kod odwiedza dzieci w wyszukiwaniu pierwszy głębi.</span><span class="sxs-lookup"><span data-stu-id="79d91-135">This code visits children in a depth first search.</span></span> <span data-ttu-id="79d91-136">Po napotkaniu stałej węzła, odwiedzający zwraca wartość stałej.</span><span class="sxs-lookup"><span data-stu-id="79d91-136">When it encounters a constant node, the visitor returns the value of the constant.</span></span> <span data-ttu-id="79d91-137">Po użytkownik odwiedził oba elementy podrzędne, te elementy podrzędne zostanie obliczona suma obliczana dla tego poddrzewa.</span><span class="sxs-lookup"><span data-stu-id="79d91-137">After the visitor has visited both children, those children will have computed the sum computed for that sub-tree.</span></span> <span data-ttu-id="79d91-138">Dodawanie węzła teraz można obliczyć jego sum.</span><span class="sxs-lookup"><span data-stu-id="79d91-138">The addition node can now compute its sum.</span></span>
<span data-ttu-id="79d91-139">Po odwiedzone wszystkich węzłów w drzewie wyrażeń suma zostaną obliczone.</span><span class="sxs-lookup"><span data-stu-id="79d91-139">Once all the nodes in the expression tree have been visited, the sum will have been computed.</span></span> <span data-ttu-id="79d91-140">Uruchamianie przykładu w debugerze i śledzenie wykonywania można śledzić wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="79d91-140">You can trace the execution by running the sample in the debugger and tracing the execution.</span></span>

<span data-ttu-id="79d91-141">Spróbujmy ułatwiają śledzenie sposobu węzły są analizowane i jak suma jest obliczana przez travsersing drzewa.</span><span class="sxs-lookup"><span data-stu-id="79d91-141">Let's make it easier to trace how the nodes are analyzed and how the sum is computed by travsersing the tree.</span></span> <span data-ttu-id="79d91-142">Oto zaktualizowaną wersję metoda agregacji, która obejmuje znacznej liczby informacji śledzenia:</span><span class="sxs-lookup"><span data-stu-id="79d91-142">Here's an updated version of the Aggregate method that includes quite a bit of tracing information:</span></span>

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

<span data-ttu-id="79d91-143">Uruchomiony na tym samym wyrażeniu daje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="79d91-143">Running it on the same expression yields the following output:</span></span>

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

<span data-ttu-id="79d91-144">Dane wyjściowe śledzenia i kontynuować pracę w powyższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="79d91-144">Trace the output and follow along in the code above.</span></span> <span data-ttu-id="79d91-145">Powinien móc wyglądają jak kod odwiedza każdy węzeł i oblicza sumę przechodzi przez drzewo i wyszukuje sumy.</span><span class="sxs-lookup"><span data-stu-id="79d91-145">You should be able to work out how the code visits each node and computes the sum as it goes through the tree and finds the sum.</span></span>

<span data-ttu-id="79d91-146">Teraz Przyjrzyjmy się inny przebieg, za pomocą wyrażenia określone przez `sum1`:</span><span class="sxs-lookup"><span data-stu-id="79d91-146">Now, let's look at a different run, with the expression given by `sum1`:</span></span>

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

<span data-ttu-id="79d91-147">Oto dane wyjściowe sprawdzając to wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="79d91-147">Here's the output from examining this expression:</span></span>

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

<span data-ttu-id="79d91-148">Mimo że końcowy odpowiedź jest taka sama, przechodzenie drzewa jest całkowicie inny.</span><span class="sxs-lookup"><span data-stu-id="79d91-148">While the final answer is the same, the tree traversal is completely different.</span></span> <span data-ttu-id="79d91-149">Węzły są w czasie podróży w innej kolejności, ponieważ drzewie został skonstruowany przy użyciu różnych operacji występujących najpierw.</span><span class="sxs-lookup"><span data-stu-id="79d91-149">The nodes are traveled in a different order, because the tree was constructed with different operations occurring first.</span></span>

## <a name="learning-more"></a><span data-ttu-id="79d91-150">Dowiedz się więcej</span><span class="sxs-lookup"><span data-stu-id="79d91-150">Learning More</span></span>

<span data-ttu-id="79d91-151">Niniejszy przykład pokazuje mały podzbiór kod, który tworzysz przechodzenia i interpretować algorytmów, reprezentowane przez drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="79d91-151">This sample shows a small subset of the code you would build to traverse and interpret the algorithms represented by an expression tree.</span></span> <span data-ttu-id="79d91-152">Szczegółowe omówienie pracy niezbędne do tworzenia biblioteki ogólnego przeznaczenia, która przekształca drzew wyrażeń w innym języku, należy przeczytać [tę serię](https://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) przez Matt Warren.</span><span class="sxs-lookup"><span data-stu-id="79d91-152">For a complete discussion of all the work necessary to build a general purpose library that translates expression trees into another language, please read [this series](https://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) by Matt Warren.</span></span> <span data-ttu-id="79d91-153">Przechodzi ona bardzo szczegółowe na temat sposobu translacji kodu, które mogą okazać się w drzewie wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="79d91-153">It goes into great detail on how to translate any of the code you might find in an expression tree.</span></span>

<span data-ttu-id="79d91-154">Mam nadzieję, że teraz w tym samouczku prawdziwą moc drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="79d91-154">I hope you've now seen the true power of expression trees.</span></span>
<span data-ttu-id="79d91-155">Można zbadać zestawu kodu, wprowadź zmiany, które chcesz do tego kodu i wykonaj zmienionych wersji.</span><span class="sxs-lookup"><span data-stu-id="79d91-155">You can examine a set of code, make any changes you'd like to that code, and execute the changed version.</span></span> <span data-ttu-id="79d91-156">Ponieważ drzew wyrażeń są niezmienne, można utworzyć nowego drzewa, przy użyciu składników istniejących drzew.</span><span class="sxs-lookup"><span data-stu-id="79d91-156">Because the expression trees are immutable, you can create new trees by using the components of existing trees.</span></span> <span data-ttu-id="79d91-157">Zmniejsza to ilość pamięci wymaganej do tworzenia drzew wyrażeń zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="79d91-157">This minimizes the amount of memory needed to create modified expression trees.</span></span>

[<span data-ttu-id="79d91-158">Następnie — Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="79d91-158">Next -- Summing up</span></span>](expression-trees-summary.md)
