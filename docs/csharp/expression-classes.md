---
title: Typy platform obsługujące drzewa wyrażeń
description: Informacje o typach framework obsługuje drzew wyrażeń, tworzenia drzew wyrażeń i technik do pracy z drzewa wyrażeń interfejsów API.
ms.date: 06/20/2016
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: c18bbfb1273156a4b070d1f195d9e823256fde9d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198468"
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="08fb6-103">Typy platform obsługujące drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="08fb6-103">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="08fb6-104">Poprzednie — Drzewa wyrażeń — objaśnienie</span><span class="sxs-lookup"><span data-stu-id="08fb6-104">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="08fb6-105">Istnieje duża lista klas w ramach platformy .NET Core, współpracujących z drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="08fb6-105">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="08fb6-106">Można zobaczyć pełną listę w <xref:System.Linq.Expressions>.</span><span class="sxs-lookup"><span data-stu-id="08fb6-106">You can see the full list at <xref:System.Linq.Expressions>.</span></span>
<span data-ttu-id="08fb6-107">Zamiast uruchamiania za pośrednictwem z pełną listą, Przyjrzyjmy się, jak zostały zaprojektowane klasy framework.</span><span class="sxs-lookup"><span data-stu-id="08fb6-107">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="08fb6-108">W projekcie języka wyrażenie jest treść kod, który oblicza i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="08fb6-108">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="08fb6-109">Wyrażenia może być bardzo prosta: wyrażenie stałe `1` zwraca stałej wartości 1.</span><span class="sxs-lookup"><span data-stu-id="08fb6-109">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="08fb6-110">Może być bardziej skomplikowane: Wyrażenie `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` zwraca jeden certyfikat główny dla równaniu kwadratowym (w przypadku, gdy równanie ma rozwiązania).</span><span class="sxs-lookup"><span data-stu-id="08fb6-110">They may be more complicated: The expression `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="08fb6-111">Wszystko zaczyna się od System.Linq.Expression</span><span class="sxs-lookup"><span data-stu-id="08fb6-111">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="08fb6-112">Jest jeden komplikacje związane z pracy z drzew wyrażeń, różne rodzaje wyrażeń są prawidłowe w wielu miejscach w programach.</span><span class="sxs-lookup"><span data-stu-id="08fb6-112">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="08fb6-113">Należy wziąć pod uwagę wyrażenia przypisania.</span><span class="sxs-lookup"><span data-stu-id="08fb6-113">Consider an assignment expression.</span></span> <span data-ttu-id="08fb6-114">Po prawej stronie przypisania może być wartością stałą, zmienną, metodę wyrażenie wywołania lub inne osoby.</span><span class="sxs-lookup"><span data-stu-id="08fb6-114">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="08fb6-115">Elastyczność tego języka oznacza, że może wystąpić wiele typów innego wyrażenia w dowolnym miejscu węzłach drzewa podczas przechodzenia do drzewa wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="08fb6-115">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="08fb6-116">W związku z tym gdy typ bazowy wyrażenia można pracować, to najprostszy sposób pracy.</span><span class="sxs-lookup"><span data-stu-id="08fb6-116">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="08fb6-117">Czasami potrzebny dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="08fb6-117">However, sometimes you need to know more.</span></span>
<span data-ttu-id="08fb6-118">Klasa bazowa wyrażenie zawiera `NodeType` właściwości w tym celu.</span><span class="sxs-lookup"><span data-stu-id="08fb6-118">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="08fb6-119">Zwraca `ExpressionType` czyli wyliczenie typy możliwe wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="08fb6-119">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="08fb6-120">Jeśli znasz już typ węzła, można rzutować go do tego typu i wykonać konkretne akcje, wiedząc, typ węzła wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="08fb6-120">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="08fb6-121">Można wyszukiwania dla niektórych typów węzłów, a następnie pracować z określonymi właściwościami, tego rodzaju wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="08fb6-121">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="08fb6-122">Na przykład ten kod będzie drukować nazwę zmiennej dla wyrażenia dostępu do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="08fb6-122">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="08fb6-123">Czy mogę wykonano praktyka Sprawdzanie typu węzła, a następnie rzutowania wyrażenia dostępu do zmiennej, a następnie zaznaczając właściwości typu określonego wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="08fb6-123">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

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

## <a name="creating-expression-trees"></a><span data-ttu-id="08fb6-124">Tworzenie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="08fb6-124">Creating Expression Trees</span></span>

<span data-ttu-id="08fb6-125">`System.Linq.Expression` Klasa zawiera także wiele metod statycznych, aby tworzyć wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="08fb6-125">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="08fb6-126">Te metody tworzenia węzła wyrażenie, przy użyciu argumenty podane dla jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="08fb6-126">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="08fb6-127">W ten sposób możesz utworzyć wyrażenie z jego węzły liści.</span><span class="sxs-lookup"><span data-stu-id="08fb6-127">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="08fb6-128">Na przykład ten kod tworzy Dodaj wyrażenie:</span><span class="sxs-lookup"><span data-stu-id="08fb6-128">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="08fb6-129">Możesz zobaczyć ten prosty przykład, że wiele typów są zaangażowane w tworzenie i Praca z drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="08fb6-129">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="08fb6-130">Czy złożoność jest zapewnienie możliwości sformatowanego słownictwa zawartym w języku C#.</span><span class="sxs-lookup"><span data-stu-id="08fb6-130">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="08fb6-131">Przejdź do interfejsów API</span><span class="sxs-lookup"><span data-stu-id="08fb6-131">Navigating the APIs</span></span>
<span data-ttu-id="08fb6-132">Istnieją typy węzłów wyrażenie, które mapują na niemal wszystkie elementy składni języka C#.</span><span class="sxs-lookup"><span data-stu-id="08fb6-132">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="08fb6-133">Każdy typ ma określonych metod dla tego typu elementu języka.</span><span class="sxs-lookup"><span data-stu-id="08fb6-133">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="08fb6-134">To znacznie ułatwia głowę w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="08fb6-134">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="08fb6-135">Zamiast próbować pamiętania wszystko, Oto techniki, używanych do pracy z drzewa wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="08fb6-135">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>
1. <span data-ttu-id="08fb6-136">Przyjrzyj się członkowie `ExpressionType` wyliczenia, aby ustalić możliwe węzły, które powinny być testowania oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="08fb6-136">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="08fb6-137">Pomaga to tak naprawdę, gdy użytkownik chce przejść i zrozumieć drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="08fb6-137">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="08fb6-138">Spójrz na statyczne elementy członkowskie `Expression` klasa do tworzenia wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="08fb6-138">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="08fb6-139">Tych metod można tworzyć dowolnego typu wyrażenia z zestawu jej podrzędnych węzłów.</span><span class="sxs-lookup"><span data-stu-id="08fb6-139">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="08fb6-140">Przyjrzyj się `ExpressionVisitor` klasa do tworzenia drzewa wyrażeń zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="08fb6-140">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="08fb6-141">Można znaleźć więcej jak Przyjrzyj się każdej z tych trzech obszarów.</span><span class="sxs-lookup"><span data-stu-id="08fb6-141">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="08fb6-142">Znajdziesz się niezmiennie, należy podczas uruchamiania przy użyciu jednego z tych trzech kroków.</span><span class="sxs-lookup"><span data-stu-id="08fb6-142">Invariably, you will find what you need when you start with one of those three steps.</span></span>
 
 [<span data-ttu-id="08fb6-143">Dalej — Wykonywanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="08fb6-143">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
