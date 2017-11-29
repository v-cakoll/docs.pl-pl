---
title: "Drzewa wyrażeń"
description: "Więcej informacji na temat drzew wyrażeń w .NET Core i sposób ich użycia, aby reprezentować kodu struktury, które można zbadać, modyfikowania i wykonać."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: 3935906d9fca81a094999eefdd49ae4ed56990bf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="expression-trees"></a><span data-ttu-id="eabed-104">Drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="eabed-104">Expression Trees</span></span>

<span data-ttu-id="eabed-105">Użycie LINQ masz doświadczenie z biblioteką sformatowanego gdzie `Func` typy są częścią zestawu interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="eabed-105">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="eabed-106">(Jeśli nie znasz za pomocą LINQ, prawdopodobnie chcesz odczytać [samouczek LINQ](linq/index.md) i samouczek dotyczący [wyrażenia lambda](lambda-expressions.md) przed tego.) *Drzewa wyrażeń* Podaj bogatszą interakcję z argumentami, które są funkcje.</span><span class="sxs-lookup"><span data-stu-id="eabed-106">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the tutorial on [lambda expressions](lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="eabed-107">Pisania argumenty funkcji, zwykle za pomocą wyrażenia Lambda, podczas tworzenia zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="eabed-107">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="eabed-108">W typowych zapytań LINQ te argumenty funkcji są przekształcane w delegata, który tworzy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="eabed-108">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span> 

<span data-ttu-id="eabed-109">Jeśli chcesz mieć bogatszą interakcję, należy użyć *drzew wyrażeń*.</span><span class="sxs-lookup"><span data-stu-id="eabed-109">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="eabed-110">Drzewa wyrażeń reprezentują kodu struktury można zbadać, zmodyfikować lub wykonać.</span><span class="sxs-lookup"><span data-stu-id="eabed-110">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="eabed-111">Te narzędzia umożliwiają uprawnienia do modyfikowania kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="eabed-111">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="eabed-112">Można napisać kod, który sprawdza, czy uruchomione algorytmów lub injects nowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="eabed-112">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="eabed-113">W bardziej zaawansowanych scenariuszy można zmodyfikować systemem algorytmów i nawet tłumaczenia wyrażeń C# do innego formularza do wykonania w innym środowisku.</span><span class="sxs-lookup"><span data-stu-id="eabed-113">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="eabed-114">Prawdopodobnie zostały już zapisane kodu korzystającego z drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="eabed-114">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="eabed-115">Interfejsy API programu Entity Framework LINQ zaakceptować drzew wyrażeń jako argumenty wzorzec wyrażenia zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="eabed-115">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="eabed-116">Umożliwiającej [Entity Framework](http://docs.efproject.net/en/latest/) tłumaczenie zapytania napisane w języku C# SQL, która wykonuje aparatu bazy danych.</span><span class="sxs-lookup"><span data-stu-id="eabed-116">That enables [Entity Framework](http://docs.efproject.net/en/latest/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="eabed-117">Innym przykładem jest [Moq](https://github.com/Moq/moq), która jest popularnych framework mocking dla platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="eabed-117">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="eabed-118">Pozostałe sekcje w tym samouczku zostanie Eksploruj są drzewa wyrażeń, zbadać klasy framework, które obsługują drzew wyrażeń i opisano sposób pracy z drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="eabed-118">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="eabed-119">Dowiesz się, jak przeczytać drzew wyrażeń, sposób tworzenia drzewa wyrażeń sposobu tworzenia drzewa wyrażeń zmodyfikowane i jak wykonać kod reprezentowany przez drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="eabed-119">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="eabed-120">Po zapoznaniu się z, będzie gotowa do użycia tych struktur można tworzyć rozbudowane algorytmy adaptacyjną.</span><span class="sxs-lookup"><span data-stu-id="eabed-120">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="eabed-121">Wyjaśniono drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="eabed-121">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="eabed-122">Zrozumienie struktury i pojęć dotyczących *drzew wyrażeń*.</span><span class="sxs-lookup"><span data-stu-id="eabed-122">Understand the structure and concepts behind *Expression Trees*.</span></span>
    
2. [<span data-ttu-id="eabed-123">Framework typy obsługi drzewa wyrażeń</span><span class="sxs-lookup"><span data-stu-id="eabed-123">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)
    
    <span data-ttu-id="eabed-124">Więcej informacji na temat struktury i klasy, które Zdefiniuj i manipulowania drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="eabed-124">Learn about the structures and classes that define and manipulate expression trees.</span></span>
    
3. [<span data-ttu-id="eabed-125">Wykonywania wyrażenia</span><span class="sxs-lookup"><span data-stu-id="eabed-125">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="eabed-126">Dowiedz się, jak można skonwertować na drzewo wyrażenia reprezentowane jako wyrażenie Lambda do delegata i wykonaj wynikowy delegata.</span><span class="sxs-lookup"><span data-stu-id="eabed-126">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="eabed-127">Interpretowanie wyrażenia</span><span class="sxs-lookup"><span data-stu-id="eabed-127">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="eabed-128">Dowiedz się, jak przechodzić między nimi i sprawdź, czy *drzew wyrażeń* zrozumienie kodu drzewa wyrażenia reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="eabed-128">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="eabed-129">Tworzenie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="eabed-129">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="eabed-130">Dowiedz się, jak utworzyć węzły drzewa wyrażeń i tworzenia drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="eabed-130">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="eabed-131">Tłumaczenia wyrażenia</span><span class="sxs-lookup"><span data-stu-id="eabed-131">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="eabed-132">Dowiedz się, jak kompilacji kopię zmodyfikowane drzewo wyrażenia lub tłumaczenie drzewo wyrażenia w innym formacie.</span><span class="sxs-lookup"><span data-stu-id="eabed-132">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="eabed-133">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="eabed-133">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="eabed-134">Przejrzyj informacje na temat drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="eabed-134">Review the information on expression trees.</span></span>
    
