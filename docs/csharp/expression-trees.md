---
title: Drzewa wyrażeń
description: Więcej informacji na temat drzew wyrażeń w .NET Core i jak z nich korzystać, aby reprezentować struktur, które można zbadać, modyfikowania i wykonywanie kodu.
ms.date: 06/20/2016
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: b7a39ccec293a22e4b4d7d01b30f9f441fd0079b
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125840"
---
# <a name="expression-trees"></a><span data-ttu-id="e3f24-103">Drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="e3f24-103">Expression Trees</span></span>

<span data-ttu-id="e3f24-104">Jeśli używano LINQ, gdy potrafisz dzięki rozbudowanej bibliotece gdzie `Func` typy są częścią zestawu interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="e3f24-104">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="e3f24-105">(Jeśli nie jesteś zaznajomiony z LINQ, prawdopodobnie chcesz odczytać [samouczek LINQ](linq/index.md) i artykuł na temat [wyrażeń lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) przed to.) *Drzewa wyrażeń* zapewniają bardziej rozbudowane interakcji z argumentów, które są funkcjami.</span><span class="sxs-lookup"><span data-stu-id="e3f24-105">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the article about [lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="e3f24-106">Można napisać argumentów funkcji, zazwyczaj przy użyciu wyrażeń Lambda, podczas tworzenia zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="e3f24-106">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="e3f24-107">W typowych zapytań LINQ te argumenty funkcji są przekształcane do delegata, który kompilator tworzy.</span><span class="sxs-lookup"><span data-stu-id="e3f24-107">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span> 

<span data-ttu-id="e3f24-108">Umożliwia bogatszych interakcję, należy użyć *drzew wyrażeń*.</span><span class="sxs-lookup"><span data-stu-id="e3f24-108">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="e3f24-109">Drzewa wyrażeń reprezentują kodu struktury, można przejrzeć, zmodyfikować lub wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e3f24-109">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="e3f24-110">Te narzędzia umożliwiają do manipulowania kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e3f24-110">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="e3f24-111">Można napisać kod, który sprawdza, czy uruchamianie algorytmów lub wprowadza nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="e3f24-111">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="e3f24-112">W bardziej zaawansowanych scenariuszy można modyfikować, uruchamianie algorytmów i nawet tłumaczenie C# wyrażeń do innej formy do wykonania w innym środowisku.</span><span class="sxs-lookup"><span data-stu-id="e3f24-112">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="e3f24-113">Kod, który używa drzew wyrażeń prawdopodobnie zostały już zapisane.</span><span class="sxs-lookup"><span data-stu-id="e3f24-113">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="e3f24-114">Interfejsy API programu Entity Framework LINQ zaakceptować drzew wyrażeń jako argumenty do wzorca wyrażenia zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="e3f24-114">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="e3f24-115">Który umożliwia [Entity Framework](/ef/) do translacji zapytania zapisane w C# SQL, który jest wykonywany w aparacie bazy danych.</span><span class="sxs-lookup"><span data-stu-id="e3f24-115">That enables [Entity Framework](/ef/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="e3f24-116">Innym przykładem jest [Moq](https://github.com/Moq/moq), czyli popularnego środowiska pozorowania dla platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="e3f24-116">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="e3f24-117">Pozostałe sekcje w tym samouczku będzie zapoznaj się z drzewa wyrażeń są, sprawdź klasy framework, które obsługują drzew wyrażeń, a dowiesz się, jak pracować z drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="e3f24-117">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="e3f24-118">Dowiesz się, jak odczytać drzew wyrażeń, sposób tworzenia drzew wyrażeń, sposób tworzenia drzew wyrażeń zmodyfikowane i jak wykonywać kod reprezentowany przez drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="e3f24-118">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="e3f24-119">Po czytania, wszystko będzie gotowe do użycia te struktury do tworzenia rozbudowanych adaptacyjnych algorytmów.</span><span class="sxs-lookup"><span data-stu-id="e3f24-119">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="e3f24-120">Drzewa wyrażeń — objaśnienie</span><span class="sxs-lookup"><span data-stu-id="e3f24-120">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="e3f24-121">Omówienie struktury i pojęcia dotyczące *drzew wyrażeń*.</span><span class="sxs-lookup"><span data-stu-id="e3f24-121">Understand the structure and concepts behind *Expression Trees*.</span></span>
    
2. [<span data-ttu-id="e3f24-122">Typy platform obsługujące drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="e3f24-122">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)
    
    <span data-ttu-id="e3f24-123">Więcej informacji na temat struktur i klas definiujących i manipulowania drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="e3f24-123">Learn about the structures and classes that define and manipulate expression trees.</span></span>
    
3. [<span data-ttu-id="e3f24-124">Wykonywanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="e3f24-124">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="e3f24-125">Dowiedz się, jak można przekonwertować na drzewo wyrażenia, w postaci wyrażenia Lambda do delegata, a następnie wykonaj wynikowego delegata.</span><span class="sxs-lookup"><span data-stu-id="e3f24-125">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="e3f24-126">Interpretowanie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="e3f24-126">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="e3f24-127">Dowiedz się, jak przejść i zbadaj *drzew wyrażeń* Aby zrozumieć, co kod drzewa wyrażenie reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="e3f24-127">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="e3f24-128">Tworzenie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="e3f24-128">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="e3f24-129">Dowiedz się, jak utworzyć węzłów do drzewa wyrażenie i tworzenia drzew wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="e3f24-129">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="e3f24-130">Translacja wyrażeń</span><span class="sxs-lookup"><span data-stu-id="e3f24-130">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="e3f24-131">Dowiedz się, jak tworzyć zmodyfikowanej kopii drzewo wyrażenia lub drzewa wyrażenie przekłada się na inny format.</span><span class="sxs-lookup"><span data-stu-id="e3f24-131">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="e3f24-132">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="e3f24-132">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="e3f24-133">Zapoznaj się z informacjami w drzewach wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="e3f24-133">Review the information on expression trees.</span></span>
    
