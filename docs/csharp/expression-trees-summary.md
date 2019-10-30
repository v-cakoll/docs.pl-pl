---
title: Podsumowanie drzew wyrażeń
description: Ponowne użycie drzew wyrażeń do tworzenia programów dynamicznych, które interpretują kod jako dane i tworzą nowe funkcje na podstawie tego kodu.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: eb687ebd-1149-4453-9fc1-12a084495a66
ms.openlocfilehash: 43715c94b70f1cd7f758cde91ae7c8d1b2f70f9f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036755"
---
# <a name="expression-trees-summary"></a><span data-ttu-id="44a8a-103">Podsumowanie drzew wyrażeń</span><span class="sxs-lookup"><span data-stu-id="44a8a-103">Expression Trees Summary</span></span>

[<span data-ttu-id="44a8a-104">Poprzednie — tłumaczenie wyrażeń</span><span class="sxs-lookup"><span data-stu-id="44a8a-104">Previous -- Translating Expressions</span></span>](expression-trees-translating.md)

<span data-ttu-id="44a8a-105">W tej serii pokazano, jak można używać *drzew wyrażeń* do tworzenia programów dynamicznych, które interpretują kod jako dane i tworzą nowe funkcje na podstawie tego kodu.</span><span class="sxs-lookup"><span data-stu-id="44a8a-105">In this series, you've seen how you can use *expression trees* to create dynamic programs that interpret code as data and build new functionality based on that code.</span></span>

<span data-ttu-id="44a8a-106">Można sprawdzić drzewa wyrażeń, aby zrozumieć intencję algorytmu.</span><span class="sxs-lookup"><span data-stu-id="44a8a-106">You can examine expression trees to understand the intent of an algorithm.</span></span> <span data-ttu-id="44a8a-107">Nie można przeanalizować tego kodu.</span><span class="sxs-lookup"><span data-stu-id="44a8a-107">You can not only examine that code.</span></span> <span data-ttu-id="44a8a-108">Można utworzyć nowe drzewa wyrażeń, które reprezentują zmodyfikowane wersje oryginalnego kodu.</span><span class="sxs-lookup"><span data-stu-id="44a8a-108">You can build new expression trees that represent modified versions of the original code.</span></span>

<span data-ttu-id="44a8a-109">Można również użyć drzew wyrażeń do przyjrzeć się algorytmowi i przetłumaczyć ten algorytm na inny język lub środowisko.</span><span class="sxs-lookup"><span data-stu-id="44a8a-109">You can also use expression trees to look at an algorithm, and translate that algorithm into another language or environment.</span></span> 

## <a name="limitations"></a><span data-ttu-id="44a8a-110">Ograniczenia</span><span class="sxs-lookup"><span data-stu-id="44a8a-110">Limitations</span></span>

<span data-ttu-id="44a8a-111">Istnieją pewne nowsze C# elementy języka, które nie są poprawnie tłumaczone na drzewa wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="44a8a-111">There are some newer C# language elements that don't translate well into expression trees.</span></span> <span data-ttu-id="44a8a-112">Drzewa wyrażeń nie mogą zawierać wyrażeń `await` ani `async` wyrażeń lambda.</span><span class="sxs-lookup"><span data-stu-id="44a8a-112">Expression trees cannot contain `await` expressions, or `async` lambda expressions.</span></span> <span data-ttu-id="44a8a-113">Wiele funkcji dodanych w C# 6 Release nie pojawia się dokładnie jako zapisywana w drzewach wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="44a8a-113">Many of the features added in the C# 6 release don't appear exactly as written in expression trees.</span></span> <span data-ttu-id="44a8a-114">Zamiast tego nowe funkcje zostaną uwidocznione w drzewach wyrażeń w równoważnej, wcześniejszej składni.</span><span class="sxs-lookup"><span data-stu-id="44a8a-114">Instead, newer features will be exposed in expressions trees in the equivalent, earlier syntax.</span></span> <span data-ttu-id="44a8a-115">Może to nie być tak samo, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="44a8a-115">This may not be as much of a limitation as you might think.</span></span> <span data-ttu-id="44a8a-116">W rzeczywistości oznacza to, że kod, który interpretuje drzewa wyrażeń prawdopodobnie nadal będzie działał tak samo, gdy zostaną wprowadzone nowe funkcje językowe.</span><span class="sxs-lookup"><span data-stu-id="44a8a-116">In fact, it means that your code that interprets expression trees will likely still work the same when new language features are introduced.</span></span>

<span data-ttu-id="44a8a-117">Nawet przy tych ograniczeniach drzewa wyrażeń umożliwiają tworzenie algorytmów dynamicznych, które opierają się na interpretowaniu i modyfikowaniu kodu, który jest reprezentowany jako struktura danych.</span><span class="sxs-lookup"><span data-stu-id="44a8a-117">Even with these limitations, expression trees do enable you to create dynamic algorithms that rely on interpreting and modifying code that is represented as a data structure.</span></span> <span data-ttu-id="44a8a-118">Jest to zaawansowane narzędzie i jest jednym z funkcji ekosystemu .NET, które umożliwiają rozbudowane biblioteki, takie jak Entity Framework, do wykonywania tych czynności.</span><span class="sxs-lookup"><span data-stu-id="44a8a-118">It's a powerful tool, and it's one of the features of the .NET ecosystem that enables rich libraries such as Entity Framework to accomplish what they do.</span></span>
