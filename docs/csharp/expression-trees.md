---
title: Drzewa wyrażeń
description: Dowiedz się więcej o drzewach wyrażeń w .NET Core i jak ich używać do reprezentowania kodu jako struktur, które można zbadać, zmodyfikować i wykonać.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: e1026ef70860da519b688a9d67181b88d03f6f0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145842"
---
# <a name="expression-trees"></a><span data-ttu-id="e8512-103">Drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="e8512-103">Expression Trees</span></span>

<span data-ttu-id="e8512-104">Jeśli używasz LINQ, masz doświadczenie z bogatą `Func` biblioteką, w której typy są częścią zestawu interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="e8512-104">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="e8512-105">(Jeśli nie jesteś zaznajomiony z LINQ, prawdopodobnie chcesz przeczytać [samouczek LINQ](linq/index.md) i artykuł o [wyrażeniach lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) przed tym.) *Drzewa wyrażeń* zapewniają bogatszą interakcję z argumentami, które są funkcjami.</span><span class="sxs-lookup"><span data-stu-id="e8512-105">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the article about [lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="e8512-106">Argumenty funkcji, zazwyczaj przy użyciu wyrażenia Lambda, podczas tworzenia kwerend LINQ.</span><span class="sxs-lookup"><span data-stu-id="e8512-106">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="e8512-107">W typowej kwerendy LINQ te argumenty funkcji są przekształcane w pełnomocnika tworzy kompilator.</span><span class="sxs-lookup"><span data-stu-id="e8512-107">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span>

<span data-ttu-id="e8512-108">Jeśli chcesz mieć bogatszą interakcję, musisz użyć *drzew wyrażeń*.</span><span class="sxs-lookup"><span data-stu-id="e8512-108">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="e8512-109">Drzewa wyrażeń reprezentują kod jako strukturę, którą można sprawdzić, zmodyfikować lub wykonać.</span><span class="sxs-lookup"><span data-stu-id="e8512-109">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="e8512-110">Narzędzia te dają możliwość manipulowania kodem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e8512-110">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="e8512-111">Można napisać kod, który sprawdza uruchomione algorytmy lub wstrzykuje nowe możliwości.</span><span class="sxs-lookup"><span data-stu-id="e8512-111">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="e8512-112">W bardziej zaawansowanych scenariuszach można modyfikować uruchomione algorytmy, a nawet tłumaczyć wyrażenia C# na inny formularz do wykonania w innym środowisku.</span><span class="sxs-lookup"><span data-stu-id="e8512-112">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="e8512-113">Prawdopodobnie już napisałkod, który używa drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="e8512-113">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="e8512-114">Interfejsy API LINQ struktury jednostek akceptują drzewa wyrażeń jako argumenty dla wzorca wyrażeń kwerendy LINQ.</span><span class="sxs-lookup"><span data-stu-id="e8512-114">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="e8512-115">Dzięki temu [entity framework](/ef/) przetłumaczyć kwerendę, którą napisałeś w języku C# na SQL, która jest wykonywana w aparatie bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e8512-115">That enables [Entity Framework](/ef/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="e8512-116">Innym przykładem jest [Moq](https://github.com/Moq/moq), który jest popularnym mocking framework dla .NET.</span><span class="sxs-lookup"><span data-stu-id="e8512-116">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="e8512-117">Pozostałe sekcje tego samouczka będzie badać, jakie drzewa wyrażeń są, zbadać klasy struktury, które obsługują drzewa wyrażeń i pokazać, jak pracować z drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="e8512-117">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="e8512-118">Dowiesz się, jak czytać drzewa wyrażeń, jak tworzyć drzewa wyrażeń, jak tworzyć drzewa wyrażeń zmodyfikowanych i jak wykonać kod reprezentowany przez drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="e8512-118">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="e8512-119">Po przeczytaniu będzie gotowy do użycia tych struktur do tworzenia bogatych algorytmów adaptacyjnych.</span><span class="sxs-lookup"><span data-stu-id="e8512-119">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="e8512-120">Drzewa wyrażeń — objaśnienie</span><span class="sxs-lookup"><span data-stu-id="e8512-120">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="e8512-121">Zrozumienie struktury i pojęć za *drzewa wyrazu*.</span><span class="sxs-lookup"><span data-stu-id="e8512-121">Understand the structure and concepts behind *Expression Trees*.</span></span>

2. [<span data-ttu-id="e8512-122">Typy platform obsługujące drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="e8512-122">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

    <span data-ttu-id="e8512-123">Dowiedz się więcej o strukturach i klasach, które definiują drzewa wyrażeń i manipulują nimi.</span><span class="sxs-lookup"><span data-stu-id="e8512-123">Learn about the structures and classes that define and manipulate expression trees.</span></span>

3. [<span data-ttu-id="e8512-124">Wykonywanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="e8512-124">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="e8512-125">Dowiedz się, jak przekonwertować drzewo wyrażeń reprezentowane jako wyrażenie Lambda do delegata i wykonać wynikowy delegata.</span><span class="sxs-lookup"><span data-stu-id="e8512-125">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="e8512-126">Interpretowanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="e8512-126">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="e8512-127">Dowiedz się, jak przechodzić i sprawdzać *drzewa wyrażeń,* aby zrozumieć, jaki kod reprezentuje drzewo wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="e8512-127">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="e8512-128">Tworzenie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="e8512-128">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="e8512-129">Dowiedz się, jak skonstruować węzły drzewa wyrażeń i drzewa wyrażeń kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e8512-129">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="e8512-130">Translacja wyrażeń</span><span class="sxs-lookup"><span data-stu-id="e8512-130">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="e8512-131">Dowiedz się, jak utworzyć zmodyfikowaną kopię drzewa wyrażeń lub przetłumaczyć drzewo wyrażeń na inny format.</span><span class="sxs-lookup"><span data-stu-id="e8512-131">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="e8512-132">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="e8512-132">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="e8512-133">Przejrzyj informacje o drzewach wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="e8512-133">Review the information on expression trees.</span></span>
