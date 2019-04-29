---
title: Podsumowanie drzew wyrażeń
description: Podsumowania, jak można użyć drzew wyrażeń do tworzenia dynamicznych programów, które interpretacji kodu jako dane oraz tworzyć nowe funkcje, w oparciu o ten kod.
ms.date: 06/20/2016
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 99b9463df096d3aada19ed7995b04ef4bd41c179
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646569"
---
# <a name="expression-trees-summary"></a><span data-ttu-id="6611f-103">Podsumowanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="6611f-103">Expression Trees Summary</span></span>

[<span data-ttu-id="6611f-104">Poprzednie — Translacja wyrażeń</span><span class="sxs-lookup"><span data-stu-id="6611f-104">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="6611f-105">W tej serii przedstawiono sposób korzystania *drzew wyrażeń* do tworzenia dynamicznych programów, które interpretacji kodu jako dane oraz tworzyć nowe funkcje, w oparciu o ten kod.</span><span class="sxs-lookup"><span data-stu-id="6611f-105">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="6611f-106">Można sprawdzić w drzewach wyrażeń w celu zrozumienia intencji algorytmu.</span><span class="sxs-lookup"><span data-stu-id="6611f-106">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="6611f-107">Ten kod nie może tylko sprawdzić.</span><span class="sxs-lookup"><span data-stu-id="6611f-107">You can not only examine that code.</span></span> <span data-ttu-id="6611f-108">Można tworzyć nowe drzew wyrażeń, które reprezentują zmodyfikowanej wersji oryginalnego kodu.</span><span class="sxs-lookup"><span data-stu-id="6611f-108">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="6611f-109">Można również używanie drzew wyrażeń do wzięcia pod algorytmu i tłumaczenie tego algorytmu innego języka lub środowiska.</span><span class="sxs-lookup"><span data-stu-id="6611f-109">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span> 

## <a name="limitations"></a><span data-ttu-id="6611f-110">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="6611f-110">Limitations</span></span>

<span data-ttu-id="6611f-111">Brak niektórych nowszych C# elementów języka, które nie je łatwo przekształcić w drzewach wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="6611f-111">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="6611f-112">Drzewa wyrażeń nie może zawierać `await` wyrażeń, lub `async` wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="6611f-112">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="6611f-113">Funkcje dodane w wielu C# wersji 6 nie pojawiają się dokładnie tak jak napisane w drzewach wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="6611f-113">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="6611f-114">Zamiast tego nowsze funkcje zostaną ujawnione w drzewach wyrażeń w składni jego odpowiednika, wcześniej.</span><span class="sxs-lookup"><span data-stu-id="6611f-114">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="6611f-115">To może nie być tyle to ograniczenie może myśląc.</span><span class="sxs-lookup"><span data-stu-id="6611f-115">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="6611f-116">W rzeczywistości oznacza to, że swój kod, który interpretuje drzew wyrażeń będzie prawdopodobnie nadal działać tak samo, gdy zostaną wprowadzone nowe funkcje języka.</span><span class="sxs-lookup"><span data-stu-id="6611f-116">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="6611f-117">Nawet w przypadku tych ograniczeń drzew wyrażeń umożliwiają tworzenie dynamicznych algorytmy, które opierają się na interpretowaniu i modyfikowania kodu, który jest reprezentowany jako struktury danych.</span><span class="sxs-lookup"><span data-stu-id="6611f-117">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represented as a data structure.</span></span> <span data-ttu-id="6611f-118">Jest zaawansowanym narzędziem, i jest jedną z funkcji ekosystemu .NET, która umożliwia zaawansowane biblioteki, takim jak Entity Framework, aby osiągnąć, co robią.</span><span class="sxs-lookup"><span data-stu-id="6611f-118">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>
