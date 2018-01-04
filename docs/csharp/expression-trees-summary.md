---
title: "Podsumowanie drzew wyrażeń"
description: "Recaps, jak używanie drzew wyrażeń do tworzenia dynamicznych programów, które interpretacji kodu jako danych i tworzenie nowych funkcji, na podstawie tego kodu."
keywords: .NET, .NET core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: d2754493c782c2550a8b0bd0de274cb8100c78af
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="expression-trees-summary"></a><span data-ttu-id="0dfce-104">Podsumowanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="0dfce-104">Expression Trees Summary</span></span>

[<span data-ttu-id="0dfce-105">Poprzednie — Tłumaczenia wyrażenia</span><span class="sxs-lookup"><span data-stu-id="0dfce-105">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="0dfce-106">W tej serii przedstawiono sposób korzystania *drzew wyrażeń* do tworzenia dynamicznych programów, które interpretacji kodu jako danych i tworzenie nowych funkcji, na podstawie tego kodu.</span><span class="sxs-lookup"><span data-stu-id="0dfce-106">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="0dfce-107">Można sprawdzić drzew wyrażeń do zrozumienia celem algorytmu.</span><span class="sxs-lookup"><span data-stu-id="0dfce-107">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="0dfce-108">Nie można tylko badanie tego kodu.</span><span class="sxs-lookup"><span data-stu-id="0dfce-108">You can not only examine that code.</span></span> <span data-ttu-id="0dfce-109">Można utworzyć nowego drzew wyrażeń, które reprezentują zmodyfikowanej wersji oryginalnego kodu.</span><span class="sxs-lookup"><span data-stu-id="0dfce-109">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="0dfce-110">Można również używanie drzew wyrażeń do przyjrzeć się algorytm i tłumaczenie tego algorytmu inny język lub środowiska.</span><span class="sxs-lookup"><span data-stu-id="0dfce-110">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span> 

## <a name="limitations"></a><span data-ttu-id="0dfce-111">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="0dfce-111">Limitations</span></span>

<span data-ttu-id="0dfce-112">Istnieją pewne nowszej C# języka elementy, które nie je łatwo przekształcić w drzewach wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="0dfce-112">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="0dfce-113">Drzewa wyrażeń nie może zawierać `await` wyrażenia, lub `async` wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="0dfce-113">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="0dfce-114">Funkcje dodane w wersji języka C# 6 nie pojawiają się dokładnie, jak podano w drzewach wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="0dfce-114">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="0dfce-115">Zamiast tego nowsze funkcje mają być widoczne w drzewach wyrażeń w składni równorzędną, wcześniej.</span><span class="sxs-lookup"><span data-stu-id="0dfce-115">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="0dfce-116">To nie może być jako część ograniczenia jak się wydaje.</span><span class="sxs-lookup"><span data-stu-id="0dfce-116">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="0dfce-117">W rzeczywistości oznacza to, że swój kod, który interpretuje drzew wyrażeń będzie prawdopodobnie nadal działać w identyczny gdy wprowadzono nowe funkcje języka.</span><span class="sxs-lookup"><span data-stu-id="0dfce-117">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="0dfce-118">Nawet w przypadku tych ograniczeń drzew wyrażeń umożliwiają tworzenie dynamicznych algorytmy, które opierają się na interpretowanie i modyfikowania kodu, który jest reprezentowany jako struktury danych.</span><span class="sxs-lookup"><span data-stu-id="0dfce-118">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represented as a data structure.</span></span> <span data-ttu-id="0dfce-119">Jest zaawansowanym narzędziem i jest jedną z funkcji ekosystemu .NET, który umożliwia sformatowanego biblioteki, takich jak Entity Framework w celu ich działania.</span><span class="sxs-lookup"><span data-stu-id="0dfce-119">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>

