---
title: Podsumowanie drzew wyrażeń
description: Recaps jak można użyć drzewa wyrażeń do tworzenia dynamicznych programów, które interpretują kod jako dane i tworzyć nowe funkcje na podstawie tego kodu.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 513244a987e295c81cfb5d00d9a0cfd6912074e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145894"
---
# <a name="expression-trees-summary"></a><span data-ttu-id="b408a-103">Podsumowanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="b408a-103">Expression Trees Summary</span></span>

[<span data-ttu-id="b408a-104">Poprzedni -- Tłumaczenie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="b408a-104">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="b408a-105">W tej serii widać, jak można użyć *drzewa wyrażeń* do tworzenia dynamicznych programów, które interpretują kod jako dane i tworzą nowe funkcje na podstawie tego kodu.</span><span class="sxs-lookup"><span data-stu-id="b408a-105">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="b408a-106">Można sprawdzić drzewa wyrażeń, aby zrozumieć intencji algorytmu.</span><span class="sxs-lookup"><span data-stu-id="b408a-106">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="b408a-107">Możesz nie tylko sprawdzić ten kod.</span><span class="sxs-lookup"><span data-stu-id="b408a-107">You can not only examine that code.</span></span> <span data-ttu-id="b408a-108">Można utworzyć nowe drzewa wyrażeń, które reprezentują zmodyfikowane wersje oryginalnego kodu.</span><span class="sxs-lookup"><span data-stu-id="b408a-108">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="b408a-109">Można również użyć drzewa wyrażeń, aby spojrzeć na algorytm i przetłumaczyć ten algorytm na inny język lub środowisko.</span><span class="sxs-lookup"><span data-stu-id="b408a-109">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span>

## <a name="limitations"></a><span data-ttu-id="b408a-110">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="b408a-110">Limitations</span></span>

<span data-ttu-id="b408a-111">Istnieje kilka nowszych elementów języka Języka C#, które nie przekładają się dobrze na drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="b408a-111">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="b408a-112">Drzewa wyrażeń nie mogą zawierać `await` wyrażeń ani `async` wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="b408a-112">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="b408a-113">Wiele funkcji dodanych w wersji C# 6 nie są wyświetlane dokładnie tak, jak napisane w drzewach wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="b408a-113">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="b408a-114">Zamiast tego nowsze funkcje będą widoczne w wyrażeniach drzew w równoważnej, wcześniejszej składni.</span><span class="sxs-lookup"><span data-stu-id="b408a-114">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="b408a-115">Może to nie być tak duże ograniczenie, jak mogłoby się wydawać.</span><span class="sxs-lookup"><span data-stu-id="b408a-115">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="b408a-116">W rzeczywistości oznacza to, że kod, który interpretuje drzewa wyrażeń prawdopodobnie nadal będzie działać tak samo po wprowadzeniu nowych funkcji języka.</span><span class="sxs-lookup"><span data-stu-id="b408a-116">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="b408a-117">Nawet przy tych ograniczeniach drzewa wyrażeń umożliwiają tworzenie dynamicznych algorytmów, które opierają się na interpretacji i modyfikowaniu kodu, który jest reprezentowany jako struktura danych.</span><span class="sxs-lookup"><span data-stu-id="b408a-117">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represented as a data structure.</span></span> <span data-ttu-id="b408a-118">Jest to zaawansowane narzędzie i jest to jedna z funkcji ekosystemu .NET, która umożliwia bogatym bibliotekom, takim jak Entity Framework, osiągnięcie tego, co robią.</span><span class="sxs-lookup"><span data-stu-id="b408a-118">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>
