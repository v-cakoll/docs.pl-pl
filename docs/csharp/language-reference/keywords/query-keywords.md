---
title: Słowa kluczowe zapytania (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 9ec163e1de018bd87348a5b39a1f34654d7d6d84
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46539508"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="a4280-102">Słowa kluczowe zapytania (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a4280-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="a4280-103">Ta sekcja zawiera kontekstowymi słowami kluczowymi, używać w wyrażeniach zapytań.</span><span class="sxs-lookup"><span data-stu-id="a4280-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a4280-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a4280-104">In this section</span></span>

|<span data-ttu-id="a4280-105">Klauzula</span><span class="sxs-lookup"><span data-stu-id="a4280-105">Clause</span></span>|<span data-ttu-id="a4280-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a4280-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="a4280-107">Z</span><span class="sxs-lookup"><span data-stu-id="a4280-107">from</span></span>](from-clause.md)|<span data-ttu-id="a4280-108">Określa źródło danych i zmienną zakresu (podobnie jak zmienna iteracji).</span><span class="sxs-lookup"><span data-stu-id="a4280-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="a4280-109">gdzie</span><span class="sxs-lookup"><span data-stu-id="a4280-109">where</span></span>](where-clause.md)|<span data-ttu-id="a4280-110">Filtry źródła elementy oparte na co najmniej jednego wyrażenia logiczne, rozdzielone i operatory logiczne AND ( `&&` lub <code>&#124;&#124;</code> ).</span><span class="sxs-lookup"><span data-stu-id="a4280-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="a4280-111">Wybierz pozycję</span><span class="sxs-lookup"><span data-stu-id="a4280-111">select</span></span>](select-clause.md)|<span data-ttu-id="a4280-112">Określa typ i kształt, który będzie mieć elementy w zwracanej sekwencji, gdy zapytanie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="a4280-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="a4280-113">Grupy</span><span class="sxs-lookup"><span data-stu-id="a4280-113">group</span></span>](group-clause.md)|<span data-ttu-id="a4280-114">Wyniki zapytania grupy zgodnie z określoną wartością klucza.</span><span class="sxs-lookup"><span data-stu-id="a4280-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="a4280-115">into</span><span class="sxs-lookup"><span data-stu-id="a4280-115">into</span></span>](into.md)|<span data-ttu-id="a4280-116">Zawiera identyfikator, który może służyć jako odwołanie do wyników sprzężenia, grupy lub klauzuli select.</span><span class="sxs-lookup"><span data-stu-id="a4280-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="a4280-117">orderby</span><span class="sxs-lookup"><span data-stu-id="a4280-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="a4280-118">Sortuje wyniki zapytania w kolejności rosnącej lub malejącej w oparciu o domyślny moduł porównujący dla typu elementu.</span><span class="sxs-lookup"><span data-stu-id="a4280-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="a4280-119">join</span><span class="sxs-lookup"><span data-stu-id="a4280-119">join</span></span>](join-clause.md)|<span data-ttu-id="a4280-120">Łączy dwa źródła danych na podstawie porównania równości między dwoma określone kryteria dopasowania.</span><span class="sxs-lookup"><span data-stu-id="a4280-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="a4280-121">Let</span><span class="sxs-lookup"><span data-stu-id="a4280-121">let</span></span>](let-clause.md)|<span data-ttu-id="a4280-122">Wprowadza zmienną zakresu do przechowywania wyników wyrażeń podrzędnych w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="a4280-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="a4280-123">in</span><span class="sxs-lookup"><span data-stu-id="a4280-123">in</span></span>](in.md)|<span data-ttu-id="a4280-124">Kontekstowe słowo kluczowe w [sprzężenia](join-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a4280-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="a4280-125">on</span><span class="sxs-lookup"><span data-stu-id="a4280-125">on</span></span>](on.md)|<span data-ttu-id="a4280-126">Kontekstowe słowo kluczowe w [sprzężenia](join-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a4280-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="a4280-127">equals</span><span class="sxs-lookup"><span data-stu-id="a4280-127">equals</span></span>](equals.md)|<span data-ttu-id="a4280-128">Kontekstowe słowo kluczowe w [sprzężenia](join-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a4280-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="a4280-129">by</span><span class="sxs-lookup"><span data-stu-id="a4280-129">by</span></span>](by.md)|<span data-ttu-id="a4280-130">Kontekstowe słowo kluczowe w [grupy](group-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a4280-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="a4280-131">ascending</span><span class="sxs-lookup"><span data-stu-id="a4280-131">ascending</span></span>](ascending.md)|<span data-ttu-id="a4280-132">Kontekstowe słowo kluczowe w [orderby](orderby-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a4280-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="a4280-133">descending</span><span class="sxs-lookup"><span data-stu-id="a4280-133">descending</span></span>](descending.md)|<span data-ttu-id="a4280-134">Kontekstowe słowo kluczowe w [orderby](orderby-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a4280-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="a4280-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a4280-135">See also</span></span>

- [<span data-ttu-id="a4280-136">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a4280-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a4280-137">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="a4280-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="a4280-138">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="a4280-138">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="a4280-139">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="a4280-139">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)