---
title: Drzewa wyrażeń
description: Więcej informacji na temat drzew wyrażeń w .NET Core i sposób ich użycia, aby reprezentować kodu struktury, które można zbadać, modyfikowania i wykonać.
ms.date: 06/20/2016
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: db35dd99dadc4e49aaaebd5d3782409a206cafc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214916"
---
# <a name="expression-trees"></a><span data-ttu-id="fb289-103">Drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="fb289-103">Expression Trees</span></span>

<span data-ttu-id="fb289-104">Użycie LINQ masz doświadczenie z biblioteką sformatowanego gdzie `Func` typy są częścią zestawu interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="fb289-104">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="fb289-105">(Jeśli nie znasz za pomocą LINQ, prawdopodobnie chcesz odczytać [samouczek LINQ](linq/index.md) i samouczek dotyczący [wyrażenia lambda](lambda-expressions.md) przed tego.) *Drzewa wyrażeń* Podaj bogatszą interakcję z argumentami, które są funkcje.</span><span class="sxs-lookup"><span data-stu-id="fb289-105">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the tutorial on [lambda expressions](lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="fb289-106">Pisania argumenty funkcji, zwykle za pomocą wyrażenia Lambda, podczas tworzenia zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="fb289-106">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="fb289-107">W typowych zapytań LINQ te argumenty funkcji są przekształcane w delegata, który tworzy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="fb289-107">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span> 

<span data-ttu-id="fb289-108">Jeśli chcesz mieć bogatszą interakcję, należy użyć *drzew wyrażeń*.</span><span class="sxs-lookup"><span data-stu-id="fb289-108">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="fb289-109">Drzewa wyrażeń reprezentują kodu struktury można zbadać, zmodyfikować lub wykonać.</span><span class="sxs-lookup"><span data-stu-id="fb289-109">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="fb289-110">Te narzędzia umożliwiają uprawnienia do modyfikowania kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fb289-110">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="fb289-111">Można napisać kod, który sprawdza, czy uruchomione algorytmów lub injects nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="fb289-111">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="fb289-112">W bardziej zaawansowanych scenariuszy można zmodyfikować systemem algorytmów i nawet tłumaczenia wyrażeń C# do innego formularza do wykonania w innym środowisku.</span><span class="sxs-lookup"><span data-stu-id="fb289-112">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="fb289-113">Prawdopodobnie zostały już zapisane kodu korzystającego z drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="fb289-113">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="fb289-114">Interfejsy API programu Entity Framework LINQ zaakceptować drzew wyrażeń jako argumenty wzorzec wyrażenia zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="fb289-114">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="fb289-115">Umożliwiającej [Entity Framework](http://docs.efproject.net/en/latest/) tłumaczenie zapytania napisane w języku C# SQL, która wykonuje aparatu bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fb289-115">That enables [Entity Framework](http://docs.efproject.net/en/latest/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="fb289-116">Innym przykładem jest [Moq](https://github.com/Moq/moq), która jest popularnych framework mocking dla platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="fb289-116">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="fb289-117">Pozostałe sekcje w tym samouczku zostanie Eksploruj są drzewa wyrażeń, zbadać klasy framework, które obsługują drzew wyrażeń i opisano sposób pracy z drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="fb289-117">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="fb289-118">Dowiesz się, jak przeczytać drzew wyrażeń, sposób tworzenia drzewa wyrażeń sposobu tworzenia drzewa wyrażeń zmodyfikowane i jak wykonać kod reprezentowany przez drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="fb289-118">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="fb289-119">Po zapoznaniu się z, będzie gotowa do użycia tych struktur można tworzyć rozbudowane algorytmy adaptacyjną.</span><span class="sxs-lookup"><span data-stu-id="fb289-119">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="fb289-120">Drzewa wyrażeń — objaśnienie</span><span class="sxs-lookup"><span data-stu-id="fb289-120">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="fb289-121">Zrozumienie struktury i pojęć dotyczących *drzew wyrażeń*.</span><span class="sxs-lookup"><span data-stu-id="fb289-121">Understand the structure and concepts behind *Expression Trees*.</span></span>
    
2. [<span data-ttu-id="fb289-122">Typy platform obsługujące drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="fb289-122">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)
    
    <span data-ttu-id="fb289-123">Więcej informacji na temat struktury i klasy, które Zdefiniuj i manipulowania drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="fb289-123">Learn about the structures and classes that define and manipulate expression trees.</span></span>
    
3. [<span data-ttu-id="fb289-124">Wykonywanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="fb289-124">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="fb289-125">Dowiedz się, jak można skonwertować na drzewo wyrażenia reprezentowane jako wyrażenie Lambda do delegata i wykonaj wynikowy delegata.</span><span class="sxs-lookup"><span data-stu-id="fb289-125">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="fb289-126">Interpretowanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="fb289-126">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="fb289-127">Dowiedz się, jak przechodzić między nimi i sprawdź, czy *drzew wyrażeń* zrozumienie kodu drzewa wyrażenia reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="fb289-127">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="fb289-128">Tworzenie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="fb289-128">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="fb289-129">Dowiedz się, jak utworzyć węzły drzewa wyrażeń i tworzenia drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="fb289-129">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="fb289-130">Translacja wyrażeń</span><span class="sxs-lookup"><span data-stu-id="fb289-130">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="fb289-131">Dowiedz się, jak kompilacji kopię zmodyfikowane drzewo wyrażenia lub tłumaczenie drzewo wyrażenia w innym formacie.</span><span class="sxs-lookup"><span data-stu-id="fb289-131">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="fb289-132">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="fb289-132">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="fb289-133">Przejrzyj informacje na temat drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="fb289-133">Review the information on expression trees.</span></span>
    
