---
title: Słowa kluczowe zapytania — odwołanie do języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 01134eda540c5141afbd11b2c89ff779da495a9a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173526"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="0cf81-102">Słowa kluczowe zapytania (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="0cf81-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="0cf81-103">Ta sekcja zawiera kontekstowe słowa kluczowe używane w wyrażeniach kwerend.</span><span class="sxs-lookup"><span data-stu-id="0cf81-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0cf81-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0cf81-104">In this section</span></span>

|<span data-ttu-id="0cf81-105">Klauzula</span><span class="sxs-lookup"><span data-stu-id="0cf81-105">Clause</span></span>|<span data-ttu-id="0cf81-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0cf81-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="0cf81-107">Z</span><span class="sxs-lookup"><span data-stu-id="0cf81-107">from</span></span>](from-clause.md)|<span data-ttu-id="0cf81-108">Określa źródło danych i zmienną zakresu (podobną do zmiennej iteracji).</span><span class="sxs-lookup"><span data-stu-id="0cf81-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="0cf81-109">Gdzie</span><span class="sxs-lookup"><span data-stu-id="0cf81-109">where</span></span>](where-clause.md)|<span data-ttu-id="0cf81-110">Filtruje elementy źródłowe na podstawie jednego lub większej liczby `&&` <code>&#124;&#124;</code> wyrażeń logicznych oddzielonych operatorami logicznymi and AND i OR ( lub ).</span><span class="sxs-lookup"><span data-stu-id="0cf81-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="0cf81-111">Wybierz</span><span class="sxs-lookup"><span data-stu-id="0cf81-111">select</span></span>](select-clause.md)|<span data-ttu-id="0cf81-112">Określa typ i kształt, które elementy w zwróconej sekwencji będą miały podczas wykonywania kwerendy.</span><span class="sxs-lookup"><span data-stu-id="0cf81-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="0cf81-113">Grupa</span><span class="sxs-lookup"><span data-stu-id="0cf81-113">group</span></span>](group-clause.md)|<span data-ttu-id="0cf81-114">Grupy kwerendy wyniki zgodnie z określoną wartością klucza.</span><span class="sxs-lookup"><span data-stu-id="0cf81-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="0cf81-115">Do</span><span class="sxs-lookup"><span data-stu-id="0cf81-115">into</span></span>](into.md)|<span data-ttu-id="0cf81-116">Zawiera identyfikator, który może służyć jako odwołanie do wyników sprzężenia, grupy lub select klauzuli.</span><span class="sxs-lookup"><span data-stu-id="0cf81-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="0cf81-117">Orderby</span><span class="sxs-lookup"><span data-stu-id="0cf81-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="0cf81-118">Sortuje wyniki kwerendy w kolejności rosnącej lub malejącej na podstawie domyślnego porównania dla typu elementu.</span><span class="sxs-lookup"><span data-stu-id="0cf81-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="0cf81-119">join</span><span class="sxs-lookup"><span data-stu-id="0cf81-119">join</span></span>](join-clause.md)|<span data-ttu-id="0cf81-120">Łączy dwa źródła danych na podstawie porównania równości między dwoma określonymi kryteriami dopasowywania.</span><span class="sxs-lookup"><span data-stu-id="0cf81-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="0cf81-121">Niech</span><span class="sxs-lookup"><span data-stu-id="0cf81-121">let</span></span>](let-clause.md)|<span data-ttu-id="0cf81-122">Wprowadza zmienną zakresu do przechowywania wyników wyrażenia podrzędnego w wyrażeniu kwerendy.</span><span class="sxs-lookup"><span data-stu-id="0cf81-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="0cf81-123">Cala</span><span class="sxs-lookup"><span data-stu-id="0cf81-123">in</span></span>](in.md)|<span data-ttu-id="0cf81-124">Kontekstowe słowo kluczowe w klauzuli [sprzężenia.](join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="0cf81-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="0cf81-125">Na</span><span class="sxs-lookup"><span data-stu-id="0cf81-125">on</span></span>](on.md)|<span data-ttu-id="0cf81-126">Kontekstowe słowo kluczowe w klauzuli [sprzężenia.](join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="0cf81-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="0cf81-127">equals</span><span class="sxs-lookup"><span data-stu-id="0cf81-127">equals</span></span>](equals.md)|<span data-ttu-id="0cf81-128">Kontekstowe słowo kluczowe w klauzuli [sprzężenia.](join-clause.md)</span><span class="sxs-lookup"><span data-stu-id="0cf81-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="0cf81-129">Przez</span><span class="sxs-lookup"><span data-stu-id="0cf81-129">by</span></span>](by.md)|<span data-ttu-id="0cf81-130">Kontekstowe słowo kluczowe w klauzuli [grupy.](group-clause.md)</span><span class="sxs-lookup"><span data-stu-id="0cf81-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="0cf81-131">ascending</span><span class="sxs-lookup"><span data-stu-id="0cf81-131">ascending</span></span>](ascending.md)|<span data-ttu-id="0cf81-132">Kontekstowe słowo kluczowe w [klauzuli orderby.](orderby-clause.md)</span><span class="sxs-lookup"><span data-stu-id="0cf81-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="0cf81-133">descending</span><span class="sxs-lookup"><span data-stu-id="0cf81-133">descending</span></span>](descending.md)|<span data-ttu-id="0cf81-134">Kontekstowe słowo kluczowe w [klauzuli orderby.](orderby-clause.md)</span><span class="sxs-lookup"><span data-stu-id="0cf81-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="0cf81-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0cf81-135">See also</span></span>

- [<span data-ttu-id="0cf81-136">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0cf81-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0cf81-137">LINQ (zapytanie zintegrowane z językiem)</span><span class="sxs-lookup"><span data-stu-id="0cf81-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="0cf81-138">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="0cf81-138">LINQ in C#</span></span>](../../linq/index.md)
