---
title: Typy platform obsługujące drzewa wyrażeń
description: Dowiedz się więcej o typach struktury obsługujących drzewa wyrażeń, tworzeniu drzew wyrażeń i technikach pracy z interfejsami API drzewa wyrażeń.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 8483c46dde3ea97138e55ab84a5924a3d2578730
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146089"
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="22788-103">Typy platform obsługujące drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="22788-103">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="22788-104">Poprzedni -- Drzewa wyrażenia wyjaśnione</span><span class="sxs-lookup"><span data-stu-id="22788-104">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="22788-105">Istnieje duża lista klas w ramach .NET Core, które współpracują z drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="22788-105">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="22788-106">Pełną listę można <xref:System.Linq.Expressions>zobaczyć na .</span><span class="sxs-lookup"><span data-stu-id="22788-106">You can see the full list at <xref:System.Linq.Expressions>.</span></span>
<span data-ttu-id="22788-107">Zamiast uruchamiać pełną listę, zrozummy, jak zostały zaprojektowane klasy framework.</span><span class="sxs-lookup"><span data-stu-id="22788-107">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="22788-108">W projekcie języka wyrażenie jest treścią kodu, który oblicza i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="22788-108">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="22788-109">Wyrażenia mogą być bardzo proste: `1` wyrażenie stałe zwraca stałą wartość 1.</span><span class="sxs-lookup"><span data-stu-id="22788-109">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="22788-110">Mogą być bardziej skomplikowane: `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` wyrażenie zwraca jeden katalog główny dla równania kwadratowego (w przypadku, gdy równanie ma rozwiązanie).</span><span class="sxs-lookup"><span data-stu-id="22788-110">They may be more complicated: The expression `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="22788-111">Wszystko zaczyna się od System.Linq.Expression</span><span class="sxs-lookup"><span data-stu-id="22788-111">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="22788-112">Jedną ze złożoności pracy z drzewami wyrażeń jest to, że wiele różnych rodzajów wyrażeń jest prawidłowych w wielu miejscach w programach.</span><span class="sxs-lookup"><span data-stu-id="22788-112">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="22788-113">Należy wziąć pod uwagę wyrażenie przypisania.</span><span class="sxs-lookup"><span data-stu-id="22788-113">Consider an assignment expression.</span></span> <span data-ttu-id="22788-114">Prawa strona przypisania może być wartością stałą, zmienną, wyrażeniem wywołania metody lub innymi.</span><span class="sxs-lookup"><span data-stu-id="22788-114">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="22788-115">Ta elastyczność języka oznacza, że można napotkać wiele różnych typów wyrażeń w dowolnym miejscu w węzłach drzewa podczas przechodzenia przez drzewo wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="22788-115">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="22788-116">W związku z tym, gdy można pracować z typem wyrażenia podstawowego, jest to najprostszy sposób pracy.</span><span class="sxs-lookup"><span data-stu-id="22788-116">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="22788-117">Czasami jednak musisz wiedzieć więcej.</span><span class="sxs-lookup"><span data-stu-id="22788-117">However, sometimes you need to know more.</span></span>
<span data-ttu-id="22788-118">Klasa wyrażenia podstawowego `NodeType` zawiera właściwość w tym celu.</span><span class="sxs-lookup"><span data-stu-id="22788-118">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="22788-119">Zwraca, `ExpressionType` który jest wyliczenie możliwych typów wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="22788-119">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="22788-120">Gdy znasz typ węzła, można rzutować go do tego typu i wykonywać określone akcje znając typ węzła wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="22788-120">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="22788-121">Można wyszukać niektóre typy węzłów, a następnie pracować z określonymi właściwościami tego rodzaju wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="22788-121">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="22788-122">Na przykład ten kod spowoduje wydrukowanie nazwy zmiennej dla wyrażenia dostępu zmiennego.</span><span class="sxs-lookup"><span data-stu-id="22788-122">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="22788-123">Postępowałem zgodnie z praktyką sprawdzania typu węzła, a następnie rzutowania do wyrażenia dostępu zmiennego, a następnie sprawdzania właściwości określonego typu wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="22788-123">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

```csharp
Expression<Func<int, int>> addFive = (num) => num + 5;

if (addFive.NodeType == ExpressionType.Lambda)
{
    var lambdaExp = (LambdaExpression)addFive;

    var parameter = lambdaExp.Parameters.First();

    Console.WriteLine(parameter.Name);
    Console.WriteLine(parameter.Type);
}
```

## <a name="creating-expression-trees"></a><span data-ttu-id="22788-124">Tworzenie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="22788-124">Creating Expression Trees</span></span>

<span data-ttu-id="22788-125">Klasa `System.Linq.Expression` zawiera również wiele metod statycznych do tworzenia wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="22788-125">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="22788-126">Metody te tworzą węzeł wyrażenia przy użyciu argumentów dostarczonych dla jego podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="22788-126">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="22788-127">W ten sposób można utworzyć wyrażenie z jego węzłów liścia.</span><span class="sxs-lookup"><span data-stu-id="22788-127">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="22788-128">Na przykład ten kod tworzy add wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="22788-128">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="22788-129">W tym prostym przykładzie można zobaczyć, że wiele typów są zaangażowane w tworzenie i pracy z drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="22788-129">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="22788-130">Ta złożoność jest niezbędna do zapewnienia możliwości bogatego słownictwa dostarczonego przez język C#.</span><span class="sxs-lookup"><span data-stu-id="22788-130">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="22788-131">Nawigowanie po interfejsach API</span><span class="sxs-lookup"><span data-stu-id="22788-131">Navigating the APIs</span></span>
<span data-ttu-id="22788-132">Istnieją typy węzłów wyrażenia, które mapują do prawie wszystkich elementów składni języka C#.</span><span class="sxs-lookup"><span data-stu-id="22788-132">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="22788-133">Każdy typ ma określone metody dla tego typu elementu języka.</span><span class="sxs-lookup"><span data-stu-id="22788-133">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="22788-134">To dużo, aby utrzymać się w głowie w jednym czasie.</span><span class="sxs-lookup"><span data-stu-id="22788-134">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="22788-135">Zamiast próbować zapamiętać wszystko, oto techniki, których używam do pracy z drzewami wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="22788-135">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>

1. <span data-ttu-id="22788-136">Spójrz na członków `ExpressionType` wyliczenia, aby określić możliwe węzły, które należy zbadać.</span><span class="sxs-lookup"><span data-stu-id="22788-136">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="22788-137">To naprawdę pomaga, gdy chcesz przechodzenia i zrozumieć drzewo wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="22788-137">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="22788-138">Spójrz na statycznych `Expression` elementów członkowskich klasy do tworzenia wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="22788-138">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="22788-139">Te metody można utworzyć dowolny typ wyrażenia z zestawu węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="22788-139">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="22788-140">Spójrz na `ExpressionVisitor` klasę, aby utworzyć drzewo wyrażenia zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="22788-140">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="22788-141">Znajdziesz więcej, gdy spojrzysz na każdy z tych trzech obszarów.</span><span class="sxs-lookup"><span data-stu-id="22788-141">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="22788-142">Niezmiennie, znajdziesz to, czego potrzebujesz, gdy zaczniesz od jednego z tych trzech kroków.</span><span class="sxs-lookup"><span data-stu-id="22788-142">Invariably, you will find what you need when you start with one of those three steps.</span></span>

 [<span data-ttu-id="22788-143">Dalej - Wykonywanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="22788-143">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
