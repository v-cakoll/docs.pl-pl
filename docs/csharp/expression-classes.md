---
title: "Framework typy obsługi drzewa wyrażeń"
description: "Informacje o typach framework obsługi drzewa wyrażeń tworzenia drzewa wyrażeń i techniki pracy z drzewa wyrażenia interfejsów API."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: ed89b286eee9b4c2e11bb27d18e50f777f94f33e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="framework-types-supporting-expression-trees"></a><span data-ttu-id="a3816-104">Framework typy obsługi drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="a3816-104">Framework Types Supporting Expression Trees</span></span>

[<span data-ttu-id="a3816-105">Poprzedniej — Wyjaśniono drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="a3816-105">Previous -- Expression Trees Explained</span></span>](expression-trees-explained.md)

<span data-ttu-id="a3816-106">Brak obszerne listy klas w ramach platformy .NET Core, które współpracują z drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="a3816-106">There is a large list of classes in the .NET Core framework that work with Expression Trees.</span></span>
<span data-ttu-id="a3816-107">Można zapoznać się z pełną listą [tutaj](/dotnet/core/api/System.Linq.Expressions).</span><span class="sxs-lookup"><span data-stu-id="a3816-107">You can see the full list [here](/dotnet/core/api/System.Linq.Expressions).</span></span>
<span data-ttu-id="a3816-108">Zamiast uruchamiania za pomocą z pełną listą, Przyjrzyjmy się, jak zostały zaprojektowane klasy framework.</span><span class="sxs-lookup"><span data-stu-id="a3816-108">Rather than run through the full list, let's understand how the framework classes have been designed.</span></span>

<span data-ttu-id="a3816-109">W języku wyrażenie jest treści kodu, który oblicza i zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="a3816-109">In language design, an expression is a body of code that evaluates and returns a value.</span></span> <span data-ttu-id="a3816-110">Wyrażenia może być bardzo prosta: wyrażenie stałe `1` zwraca stała wartość 1.</span><span class="sxs-lookup"><span data-stu-id="a3816-110">Expressions may be very simple: the constant expression `1` returns the constant value of 1.</span></span> <span data-ttu-id="a3816-111">Może być bardziej skomplikowane: wyrażenie `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` zwraca jeden katalog główny dla kwadratowe równości (w przypadku, gdy równanie ma rozwiązania).</span><span class="sxs-lookup"><span data-stu-id="a3816-111">They may be more complicated: The expression `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` returns one root for a quadratic equation (in the case where the equation has a solution).</span></span>  

## <a name="it-all-starts-with-systemlinqexpression"></a><span data-ttu-id="a3816-112">Rozpoczyna się System.Linq.Expression</span><span class="sxs-lookup"><span data-stu-id="a3816-112">It all starts with System.Linq.Expression</span></span>

<span data-ttu-id="a3816-113">Jednym z złożonością, Praca z drzewa wyrażeń jest różne rodzaje wyrażeń są prawidłowe w wielu miejscach w programach.</span><span class="sxs-lookup"><span data-stu-id="a3816-113">One of the complexities of working with expression trees is that many different kinds of expressions are valid in many places in programs.</span></span> <span data-ttu-id="a3816-114">Należy wziąć pod uwagę wyrażenia przypisania.</span><span class="sxs-lookup"><span data-stu-id="a3816-114">Consider an assignment expression.</span></span> <span data-ttu-id="a3816-115">Po prawej stronie przypisania może być wartością stałą, zmienną, wyrażenie wywołania metody lub innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="a3816-115">The right hand side of an assignment could be a constant value, a variable, a method call expression, or others.</span></span> <span data-ttu-id="a3816-116">Ten język elastyczność oznacza, mogą wystąpić wiele typów różnych wyrażenie w dowolnym miejscu węzły drzewa przechodzenie drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a3816-116">That language flexibility means that you may encounter many different expression types anywhere in the nodes of a tree when you traverse an expression tree.</span></span> <span data-ttu-id="a3816-117">W związku z tym podczas pracy z typem wyrażenia podstawowego, który jest najprostszym sposobem pracy.</span><span class="sxs-lookup"><span data-stu-id="a3816-117">Therefore, when you can work with the base expression type, that's the simplest way to work.</span></span> <span data-ttu-id="a3816-118">Czasami potrzebny dowiedzieć się więcej.</span><span class="sxs-lookup"><span data-stu-id="a3816-118">However, sometimes you need to know more.</span></span>
<span data-ttu-id="a3816-119">Klasa podstawowa wyrażenie zawiera `NodeType` właściwości w tym celu.</span><span class="sxs-lookup"><span data-stu-id="a3816-119">The base Expression class contains a `NodeType` property for this purpose.</span></span>
<span data-ttu-id="a3816-120">Zwraca `ExpressionType` czyli wyliczenie typów możliwy wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="a3816-120">It returns an `ExpressionType` which is an enumeration of possible expression types.</span></span>
<span data-ttu-id="a3816-121">Po sprawdzeniu typ węzła rzutowania go do tego typu, a wykonywanie określonych czynności, które wiedząc typ węzła wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a3816-121">Once you know the type of the node, you can cast it to that type, and perform specific actions knowing the type of the expression node.</span></span> <span data-ttu-id="a3816-122">Wyszukiwanie niektórych typów węzłów i następnie pracować z określone właściwości typu wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a3816-122">You can search for certain node types, and then work with the specific properties of that kind of expression.</span></span>

<span data-ttu-id="a3816-123">Na przykład ten kod będzie drukować nazwę zmiennej w wyrażeniu dostępu do zmiennych.</span><span class="sxs-lookup"><span data-stu-id="a3816-123">For example, this code will print the name of a variable for a variable access expression.</span></span> <span data-ttu-id="a3816-124">Już zostały wykonane praktyka Sprawdzanie typu węzła, a następnie rzutowania wyrażenia do dostępu do zmiennych, a następnie zaznaczając właściwości Typ określonego wyrażenia:</span><span class="sxs-lookup"><span data-stu-id="a3816-124">I've followed the practice of checking the node type, then casting to a variable access expression and then checking the properties of the specific expression type:</span></span>

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

## <a name="creating-expression-trees"></a><span data-ttu-id="a3816-125">Tworzenie drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="a3816-125">Creating Expression Trees</span></span>

<span data-ttu-id="a3816-126">`System.Linq.Expression` Klasa zawiera także wiele metod statycznych do tworzenia wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a3816-126">The `System.Linq.Expression` class also contains many static methods to create expressions.</span></span> <span data-ttu-id="a3816-127">Te metody tworzenia węzła wyrażenia przy użyciu argumentów dla jego elementów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a3816-127">These methods create an expression node using the arguments supplied for its children.</span></span> <span data-ttu-id="a3816-128">W ten sposób tworzenia wyrażenia z jego węzłów liści.</span><span class="sxs-lookup"><span data-stu-id="a3816-128">In this way, you build an expression up from its leaf nodes.</span></span> <span data-ttu-id="a3816-129">Na przykład ten kod tworzy wyrażenie Dodaj:</span><span class="sxs-lookup"><span data-stu-id="a3816-129">For example, this code builds an Add expression:</span></span>

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

<span data-ttu-id="a3816-130">Widać w tym prostym przykładzie, że wiele typów są zaangażowane w tworzenie i Praca z drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="a3816-130">You can see from this simple example that many types are involved in creating and working with expression trees.</span></span> <span data-ttu-id="a3816-131">Złożoność jest niezbędne do zapewnienia możliwości sformatowanego słownictwa podał języka C#.</span><span class="sxs-lookup"><span data-stu-id="a3816-131">That complexity is necessary to provide the capabilities of the rich vocabulary provided by the C# language.</span></span>

## <a name="navigating-the-apis"></a><span data-ttu-id="a3816-132">Nawigowanie po interfejsy API</span><span class="sxs-lookup"><span data-stu-id="a3816-132">Navigating the APIs</span></span>
<span data-ttu-id="a3816-133">Brak wyrażenia typy węzłów, które mapują prawie wszystkie elementy składni języka C#.</span><span class="sxs-lookup"><span data-stu-id="a3816-133">There are Expression node types that map to almost all of the syntax elements of the C# language.</span></span> <span data-ttu-id="a3816-134">Każdy typ ma określonej metody dla tego typu elementu języka.</span><span class="sxs-lookup"><span data-stu-id="a3816-134">Each type has specific methods for that type of language element.</span></span> <span data-ttu-id="a3816-135">Istnieje wiele przechowywanych w nagłówek w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="a3816-135">It's a lot to keep in your head at one time.</span></span> <span data-ttu-id="a3816-136">Zamiast próby pamiętania wszystko, Oto techniki, używanych do pracy z drzewa wyrażeń:</span><span class="sxs-lookup"><span data-stu-id="a3816-136">Rather than try to memorize everything, here are the techniques I use to work with Expression trees:</span></span>
1. <span data-ttu-id="a3816-137">Przyjrzyj się członków `ExpressionType` wyliczenia można określić możliwych węzłów, użytkownik powinien być badanie.</span><span class="sxs-lookup"><span data-stu-id="a3816-137">Look at the members of the `ExpressionType` enum to determine possible nodes you should be examining.</span></span> <span data-ttu-id="a3816-138">Pomaga to naprawdę umożliwia przechodzenie między danymi i zrozumienie drzewo wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a3816-138">This really helps when you want to traverse and understand an expression tree.</span></span>
2. <span data-ttu-id="a3816-139">Przyjrzyj się statyczne elementy członkowskie `Expression` klasa do tworzenia wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="a3816-139">Look at the static members of the `Expression` class to build an expression.</span></span> <span data-ttu-id="a3816-140">Tych metod można tworzyć dowolnego typu wyrażenia z zestawu jej podrzędnych węzłów.</span><span class="sxs-lookup"><span data-stu-id="a3816-140">Those methods can build any expression type from a set of its child nodes.</span></span>
3. <span data-ttu-id="a3816-141">Przyjrzyj się `ExpressionVisitor` klasa do tworzenia drzewa wyrażenia zmodyfikowane.</span><span class="sxs-lookup"><span data-stu-id="a3816-141">Look at the `ExpressionVisitor` class to build a modified expression tree.</span></span>

<span data-ttu-id="a3816-142">Można znaleźć więcej podczas wyszukiwania na każdym z tych trzech obszarach.</span><span class="sxs-lookup"><span data-stu-id="a3816-142">You'll find more as you look at each of those three areas.</span></span> <span data-ttu-id="a3816-143">Znajdziesz się niezmiennie, należy podczas uruchamiania jednego z tych trzech kroków.</span><span class="sxs-lookup"><span data-stu-id="a3816-143">Invariably, you will find what you need when you start with one of those three steps.</span></span>
 
 [<span data-ttu-id="a3816-144">Next — Wykonywanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="a3816-144">Next -- Executing Expression Trees</span></span>](expression-trees-execution.md)
 
