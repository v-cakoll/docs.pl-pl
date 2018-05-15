---
title: Podsumowanie drzew wyrażeń
description: Recaps, jak używanie drzew wyrażeń do tworzenia dynamicznych programów, które interpretacji kodu jako danych i tworzenie nowych funkcji, na podstawie tego kodu.
ms.date: 06/20/2016
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: e0d46aa67b61fd4e1d2bcc20b4a567524bb00301
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="expression-trees-summary"></a><span data-ttu-id="cc0e9-103">Podsumowanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="cc0e9-103">Expression Trees Summary</span></span>

[<span data-ttu-id="cc0e9-104">Poprzednie — Tłumaczenia wyrażenia</span><span class="sxs-lookup"><span data-stu-id="cc0e9-104">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="cc0e9-105">W tej serii przedstawiono sposób korzystania *drzew wyrażeń* do tworzenia dynamicznych programów, które interpretacji kodu jako danych i tworzenie nowych funkcji, na podstawie tego kodu.</span><span class="sxs-lookup"><span data-stu-id="cc0e9-105">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="cc0e9-106">Można sprawdzić drzew wyrażeń do zrozumienia celem algorytmu.</span><span class="sxs-lookup"><span data-stu-id="cc0e9-106">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="cc0e9-107">Nie można tylko badanie tego kodu.</span><span class="sxs-lookup"><span data-stu-id="cc0e9-107">You can not only examine that code.</span></span> <span data-ttu-id="cc0e9-108">Można utworzyć nowego drzew wyrażeń, które reprezentują zmodyfikowanej wersji oryginalnego kodu.</span><span class="sxs-lookup"><span data-stu-id="cc0e9-108">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="cc0e9-109">Można również używanie drzew wyrażeń do przyjrzeć się algorytm i tłumaczenie tego algorytmu inny język lub środowiska.</span><span class="sxs-lookup"><span data-stu-id="cc0e9-109">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span> 

## <a name="limitations"></a><span data-ttu-id="cc0e9-110">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="cc0e9-110">Limitations</span></span>

<span data-ttu-id="cc0e9-111">Istnieją pewne nowszej C# języka elementy, które nie je łatwo przekształcić w drzewach wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="cc0e9-111">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="cc0e9-112">Drzewa wyrażeń nie może zawierać `await` wyrażenia, lub `async` wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="cc0e9-112">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="cc0e9-113">Funkcje dodane w wersji języka C# 6 nie pojawiają się dokładnie, jak podano w drzewach wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="cc0e9-113">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="cc0e9-114">Zamiast tego nowsze funkcje mają być widoczne w drzewach wyrażeń w składni równorzędną, wcześniej.</span><span class="sxs-lookup"><span data-stu-id="cc0e9-114">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="cc0e9-115">To nie może być jako część ograniczenia jak się wydaje.</span><span class="sxs-lookup"><span data-stu-id="cc0e9-115">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="cc0e9-116">W rzeczywistości oznacza to, że swój kod, który interpretuje drzew wyrażeń będzie prawdopodobnie nadal działać w identyczny gdy wprowadzono nowe funkcje języka.</span><span class="sxs-lookup"><span data-stu-id="cc0e9-116">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="cc0e9-117">Nawet w przypadku tych ograniczeń drzew wyrażeń umożliwiają tworzenie dynamicznych algorytmy, które opierają się na interpretowanie i modyfikowania kodu, który jest reprezentowany jako struktury danych.</span><span class="sxs-lookup"><span data-stu-id="cc0e9-117">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represented as a data structure.</span></span> <span data-ttu-id="cc0e9-118">Jest zaawansowanym narzędziem i jest jedną z funkcji ekosystemu .NET, który umożliwia sformatowanego biblioteki, takich jak Entity Framework w celu ich działania.</span><span class="sxs-lookup"><span data-stu-id="cc0e9-118">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>

