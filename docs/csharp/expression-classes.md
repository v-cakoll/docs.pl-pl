---
title: Typy platform obsługujące drzewa wyrażeń
description: Poznaj typy struktur obsługujące drzewa wyrażeń, tworzenie drzew wyrażeń i techniki umożliwiające pracę z interfejsami API drzewa wyrażeń.
ms.date: 06/20/2016
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: d11a13000019faf2ab5c35d41d48fa199e901d1c
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925966"
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="1d28d-103">Typy platform obsługujące drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="1d28d-103">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="1d28d-104">Opisane wcześniej drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="1d28d-104">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="1d28d-105">Istnieje duża lista klas w programie .NET Core Framework, które współpracują z drzewami wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1d28d-105">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="1d28d-106">Pełną listę można zobaczyć pod adresem <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="1d28d-106">You can see the full list at <xref:System.Linq.Expressions>.</span></span>
<span data-ttu-id="1d28d-107">Zamiast korzystać z pełnej listy, przyjrzyjmy się, jak zostały zaprojektowane klasy struktury.</span><span class="sxs-lookup"><span data-stu-id="1d28d-107">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="1d28d-108">W projekcie języka wyrażenie jest treścią kodu, który oblicza i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="1d28d-108">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="1d28d-109">Wyrażenia mogą być bardzo proste: wyrażenie `1` stałe zwraca wartość stałą 1.</span><span class="sxs-lookup"><span data-stu-id="1d28d-109">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="1d28d-110">Mogą być bardziej skomplikowane: Wyrażenie `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` zwraca jeden element główny dla równania kwadratowego (w przypadku, gdy równanie ma rozwiązanie).</span><span class="sxs-lookup"><span data-stu-id="1d28d-110">They may be more complicated: The expression `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="1d28d-111">Wszystko zaczyna się od system. LINQ. Expression</span><span class="sxs-lookup"><span data-stu-id="1d28d-111">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="1d28d-112">Jedną z złożoności pracy z drzewami wyrażeń jest to, że wiele różnych rodzajów wyrażeń jest prawidłowych w wielu miejscach w programach.</span><span class="sxs-lookup"><span data-stu-id="1d28d-112">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="1d28d-113">Rozważ wyrażenie przypisania.</span><span class="sxs-lookup"><span data-stu-id="1d28d-113">Consider an assignment expression.</span></span> <span data-ttu-id="1d28d-114">Prawa strona przypisania może być wartością stałą, zmienną, wyrażeniem wywołania metody lub innymi.</span><span class="sxs-lookup"><span data-stu-id="1d28d-114">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="1d28d-115">Ta elastyczność języka oznacza, że podczas przechodzenia drzewa wyrażenia mogą wystąpić wiele różnych typów wyrażeń w dowolnym miejscu w węzłach drzewa.</span><span class="sxs-lookup"><span data-stu-id="1d28d-115">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="1d28d-116">W związku z tym, jeśli można korzystać z typu wyrażenia podstawowego, jest to najprostszy sposób na działanie.</span><span class="sxs-lookup"><span data-stu-id="1d28d-116">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="1d28d-117">Jednak czasami trzeba dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="1d28d-117">However, sometimes you need to know more.</span></span>
<span data-ttu-id="1d28d-118">Klasa wyrażenie podstawowe zawiera `NodeType` właściwość do tego celu.</span><span class="sxs-lookup"><span data-stu-id="1d28d-118">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="1d28d-119">Zwraca wartość `ExpressionType` , która jest wyliczeniem możliwych typów wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1d28d-119">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="1d28d-120">Po poznaniu typu węzła można rzutować go na ten typ, a następnie wykonywać określone akcje, znając typ węzła wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1d28d-120">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="1d28d-121">Można wyszukiwać określone typy węzłów, a następnie korzystać z określonych właściwości tego rodzaju wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1d28d-121">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="1d28d-122">Na przykład ten kod będzie drukował nazwę zmiennej dla wyrażenia dostępu do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1d28d-122">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="1d28d-123">Po wykonaniu tych wskazówek zawarto sprawdzanie typu węzła, a następnie rzutowanie na wyrażenie dostępu do zmiennej, a następnie Sprawdzanie właściwości konkretnego typu wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="1d28d-123">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

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

## <a name="creating-expression-trees"></a><span data-ttu-id="1d28d-124">Tworzenie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="1d28d-124">Creating Expression Trees</span></span>

<span data-ttu-id="1d28d-125">`System.Linq.Expression` Klasa zawiera również wiele metod statycznych do tworzenia wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1d28d-125">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="1d28d-126">Te metody tworzą węzeł wyrażenia przy użyciu argumentów dostarczonych dla jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="1d28d-126">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="1d28d-127">W ten sposób utworzysz wyrażenie na podstawie jego węzłów liścia.</span><span class="sxs-lookup"><span data-stu-id="1d28d-127">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="1d28d-128">Na przykład ten kod kompiluje wyrażenie Add:</span><span class="sxs-lookup"><span data-stu-id="1d28d-128">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="1d28d-129">W tym prostym przykładzie można zobaczyć, że wiele typów obejmuje tworzenie i pracę z drzewami wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1d28d-129">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="1d28d-130">Ta złożoność jest niezbędna do zapewnienia możliwości rozbudowanego słownictwa dostarczonego przez C# język.</span><span class="sxs-lookup"><span data-stu-id="1d28d-130">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="1d28d-131">Nawigowanie po interfejsach API</span><span class="sxs-lookup"><span data-stu-id="1d28d-131">Navigating the APIs</span></span>
<span data-ttu-id="1d28d-132">Istnieją typy węzłów wyrażeń, które mapują do niemal wszystkich elementów składni C# języka.</span><span class="sxs-lookup"><span data-stu-id="1d28d-132">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="1d28d-133">Każdy typ ma określone metody dla tego typu elementu języka.</span><span class="sxs-lookup"><span data-stu-id="1d28d-133">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="1d28d-134">Jest to bardzo dużo do utrzymania w Twoim głowie.</span><span class="sxs-lookup"><span data-stu-id="1d28d-134">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="1d28d-135">Zamiast próbować znają wszystko, Oto techniki używane do pracy z drzewami wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="1d28d-135">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>

1. <span data-ttu-id="1d28d-136">Sprawdź elementy członkowskie `ExpressionType` wyliczenia, aby określić możliwe węzły, które należy sprawdzić.</span><span class="sxs-lookup"><span data-stu-id="1d28d-136">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="1d28d-137">Jest to naprawdę pomocne, gdy chcesz przechodzenie i zrozumieć drzewo wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1d28d-137">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="1d28d-138">Sprawdź statyczne elementy członkowskie `Expression` klasy, aby utworzyć wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="1d28d-138">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="1d28d-139">Metody te mogą tworzyć dowolne typy wyrażeń z zestawu jego węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="1d28d-139">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="1d28d-140">Przyjrzyj się `ExpressionVisitor` klasie, aby utworzyć zmodyfikowane drzewo wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="1d28d-140">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="1d28d-141">Dowiesz się więcej na temat każdego z tych trzech obszarów.</span><span class="sxs-lookup"><span data-stu-id="1d28d-141">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="1d28d-142">Niezmiennie, czego potrzebujesz, gdy rozpoczniesz pracę z jednym z tych trzech kroków.</span><span class="sxs-lookup"><span data-stu-id="1d28d-142">Invariably, you will find what you need when you start with one of those three steps.</span></span>
 
 [<span data-ttu-id="1d28d-143">Następne--wykonywanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="1d28d-143">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
