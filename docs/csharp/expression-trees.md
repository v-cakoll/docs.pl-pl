---
title: Drzewa wyrażeń
description: Informacje o drzewach wyrażeń w oprogramowaniu .NET Core i sposobach ich użycia do reprezentowania kodu jako struktur, które można sprawdzić, zmodyfikować i wykonać.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: b7d039ea4585953473dc88cebcc516ea240cdc3a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036320"
---
# <a name="expression-trees"></a><span data-ttu-id="43dbc-103">Drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="43dbc-103">Expression Trees</span></span>

<span data-ttu-id="43dbc-104">Jeśli używasz LINQ, masz doświadczenie w korzystaniu z rozbudowanej biblioteki, w której typy `Func` są częścią zestawu interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="43dbc-104">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="43dbc-105">(Jeśli nie znasz programu LINQ, prawdopodobnie chcesz przeczytać [samouczek LINQ](linq/index.md) i artykuł dotyczący [wyrażeń lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) przed tym.) *Drzewa wyrażeń* zapewniają bogatsze interakcje z argumentami, które są funkcjami.</span><span class="sxs-lookup"><span data-stu-id="43dbc-105">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the article about [lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="43dbc-106">Podczas tworzenia zapytań LINQ można pisać argumenty funkcji, zwykle wykorzystując wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="43dbc-106">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="43dbc-107">W typowej kwerendzie LINQ te argumenty funkcji są przekształcane na delegata tworzonego przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="43dbc-107">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span> 

<span data-ttu-id="43dbc-108">Jeśli chcesz mieć bogatsze interakcje, musisz używać *drzew wyrażeń*.</span><span class="sxs-lookup"><span data-stu-id="43dbc-108">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="43dbc-109">Drzewa wyrażeń reprezentują kod jako strukturę, którą można testować, modyfikować lub wykonywać.</span><span class="sxs-lookup"><span data-stu-id="43dbc-109">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="43dbc-110">Te narzędzia umożliwiają manipulowanie kodem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="43dbc-110">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="43dbc-111">Można napisać kod, który analizuje uruchomione algorytmy, lub wprowadza nowe możliwości.</span><span class="sxs-lookup"><span data-stu-id="43dbc-111">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="43dbc-112">W bardziej zaawansowanych scenariuszach można modyfikować uruchomione algorytmy, a nawet przetłumaczyć C# wyrażenia na inny formularz do wykonania w innym środowisku.</span><span class="sxs-lookup"><span data-stu-id="43dbc-112">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="43dbc-113">Już właśnie Zapisano kod, który używa drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="43dbc-113">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="43dbc-114">Interfejsy API LINQ Entity Framework akceptują drzewa wyrażeń jako argumenty wzorca wyrażenia zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="43dbc-114">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="43dbc-115">Dzięki temu [Entity Framework](/ef/) tłumaczenie zapytania, które zostało napisane w C# języku SQL, który jest wykonywany w aparacie bazy danych.</span><span class="sxs-lookup"><span data-stu-id="43dbc-115">That enables [Entity Framework](/ef/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="43dbc-116">Innym przykładem jest [MOQ](https://github.com/Moq/moq), który jest popularną strukturą dla platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="43dbc-116">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="43dbc-117">Pozostałe sekcje w tym samouczku zapoznają się z drzewami wyrażeń, sprawdzają klasy struktury obsługujące drzewa wyrażeń i pokazują, jak korzystać z drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="43dbc-117">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="43dbc-118">Dowiesz się, jak czytać drzewa wyrażeń, jak tworzyć drzewa wyrażeń, jak tworzyć zmodyfikowane drzewa wyrażeń i jak wykonywać kod reprezentowany przez drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="43dbc-118">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="43dbc-119">Po przeczytaniu będzie można używać tych struktur do tworzenia rozbudowanych algorytmów adaptacyjnych.</span><span class="sxs-lookup"><span data-stu-id="43dbc-119">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="43dbc-120">Drzewa wyrażeń — objaśnienie</span><span class="sxs-lookup"><span data-stu-id="43dbc-120">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="43dbc-121">Zapoznaj się ze strukturą i pojęciami związanymi z *drzewami wyrażeń*.</span><span class="sxs-lookup"><span data-stu-id="43dbc-121">Understand the structure and concepts behind *Expression Trees*.</span></span>
    
2. [<span data-ttu-id="43dbc-122">Typy platform obsługujące drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="43dbc-122">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)
    
    <span data-ttu-id="43dbc-123">Dowiedz się więcej o strukturach i klasach, które definiują drzewa wyrażeń i manipulowania nimi.</span><span class="sxs-lookup"><span data-stu-id="43dbc-123">Learn about the structures and classes that define and manipulate expression trees.</span></span>
    
3. [<span data-ttu-id="43dbc-124">Wykonywanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="43dbc-124">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="43dbc-125">Dowiedz się, jak przekonwertować drzewo wyrażenia reprezentowane jako wyrażenie lambda na delegata i wykonać delegata będącego wynikiem.</span><span class="sxs-lookup"><span data-stu-id="43dbc-125">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="43dbc-126">Interpretowanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="43dbc-126">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="43dbc-127">Dowiedz się, jak przechodzenie i sprawdzanie *drzew wyrażeń* , aby zrozumieć, jaki kod jest reprezentowany przez drzewo wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="43dbc-127">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="43dbc-128">Tworzenie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="43dbc-128">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="43dbc-129">Dowiedz się, jak utworzyć węzły dla drzewa wyrażenia i drzewa wyrażeń kompilacji.</span><span class="sxs-lookup"><span data-stu-id="43dbc-129">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="43dbc-130">Translacja wyrażeń</span><span class="sxs-lookup"><span data-stu-id="43dbc-130">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="43dbc-131">Dowiedz się, jak utworzyć zmodyfikowaną kopię drzewa wyrażenia lub przetłumaczyć drzewo wyrażenia na inny format.</span><span class="sxs-lookup"><span data-stu-id="43dbc-131">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="43dbc-132">Sumowanie</span><span class="sxs-lookup"><span data-stu-id="43dbc-132">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="43dbc-133">Zapoznaj się z informacjami w drzewach wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="43dbc-133">Review the information on expression trees.</span></span>
