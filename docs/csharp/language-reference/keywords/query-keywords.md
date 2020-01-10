---
title: Słowa kluczowe zapytania C# — odwołanie
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 3c08c2b6ecdaa4b875f118531e7e77f7164dd784
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713160"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="6ec4b-102">Słowa kluczowe zapytaniaC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="6ec4b-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="6ec4b-103">Ta sekcja zawiera kontekstowe słowa kluczowe używane w wyrażeniach zapytań.</span><span class="sxs-lookup"><span data-stu-id="6ec4b-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="6ec4b-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="6ec4b-104">In this section</span></span>

|<span data-ttu-id="6ec4b-105">Klauzula</span><span class="sxs-lookup"><span data-stu-id="6ec4b-105">Clause</span></span>|<span data-ttu-id="6ec4b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="6ec4b-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="6ec4b-107">from</span><span class="sxs-lookup"><span data-stu-id="6ec4b-107">from</span></span>](from-clause.md)|<span data-ttu-id="6ec4b-108">Określa źródło danych i zmienną zakresu (podobnie jak Zmienna iteracji).</span><span class="sxs-lookup"><span data-stu-id="6ec4b-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="6ec4b-109">miejscu</span><span class="sxs-lookup"><span data-stu-id="6ec4b-109">where</span></span>](where-clause.md)|<span data-ttu-id="6ec4b-110">Filtruje elementy źródłowe na podstawie co najmniej jednego wyrażenia logicznego oddzielonego operatorami logicznymi i i lub (`&&` lub <code>&#124;&#124;</code>).</span><span class="sxs-lookup"><span data-stu-id="6ec4b-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="6ec4b-111">zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="6ec4b-111">select</span></span>](select-clause.md)|<span data-ttu-id="6ec4b-112">Określa typ i kształt, które elementy w zwracanej sekwencji będą miały miejsce, gdy zapytanie zostanie wykonane.</span><span class="sxs-lookup"><span data-stu-id="6ec4b-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="6ec4b-113">Group</span><span class="sxs-lookup"><span data-stu-id="6ec4b-113">group</span></span>](group-clause.md)|<span data-ttu-id="6ec4b-114">Grupuje wyniki zapytania zgodnie z określoną wartością klucza.</span><span class="sxs-lookup"><span data-stu-id="6ec4b-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="6ec4b-115">into</span><span class="sxs-lookup"><span data-stu-id="6ec4b-115">into</span></span>](into.md)|<span data-ttu-id="6ec4b-116">Dostarcza identyfikator, który może być używany jako odwołanie do wyników klauzuli join, Group lub SELECT.</span><span class="sxs-lookup"><span data-stu-id="6ec4b-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="6ec4b-117">orderby</span><span class="sxs-lookup"><span data-stu-id="6ec4b-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="6ec4b-118">Sortuje wyniki zapytania w porządku rosnącym lub malejącym w oparciu o domyślną funkcję porównującą dla typu elementu.</span><span class="sxs-lookup"><span data-stu-id="6ec4b-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="6ec4b-119">join</span><span class="sxs-lookup"><span data-stu-id="6ec4b-119">join</span></span>](join-clause.md)|<span data-ttu-id="6ec4b-120">Łączy dwa źródła danych na podstawie porównania równości między dwoma określonymi kryteriami dopasowywania.</span><span class="sxs-lookup"><span data-stu-id="6ec4b-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="6ec4b-121">wpuść</span><span class="sxs-lookup"><span data-stu-id="6ec4b-121">let</span></span>](let-clause.md)|<span data-ttu-id="6ec4b-122">Wprowadza zmienną zakresu do przechowywania wyników podwyrażenia w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="6ec4b-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="6ec4b-123">in</span><span class="sxs-lookup"><span data-stu-id="6ec4b-123">in</span></span>](in.md)|<span data-ttu-id="6ec4b-124">Kontekstowe słowo kluczowe w klauzuli [Join](join-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="6ec4b-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="6ec4b-125">on</span><span class="sxs-lookup"><span data-stu-id="6ec4b-125">on</span></span>](on.md)|<span data-ttu-id="6ec4b-126">Kontekstowe słowo kluczowe w klauzuli [Join](join-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="6ec4b-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="6ec4b-127">equals</span><span class="sxs-lookup"><span data-stu-id="6ec4b-127">equals</span></span>](equals.md)|<span data-ttu-id="6ec4b-128">Kontekstowe słowo kluczowe w klauzuli [Join](join-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="6ec4b-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="6ec4b-129">by</span><span class="sxs-lookup"><span data-stu-id="6ec4b-129">by</span></span>](by.md)|<span data-ttu-id="6ec4b-130">Kontekstowe słowo kluczowe w klauzuli [Group](group-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="6ec4b-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="6ec4b-131">ascending</span><span class="sxs-lookup"><span data-stu-id="6ec4b-131">ascending</span></span>](ascending.md)|<span data-ttu-id="6ec4b-132">Kontekstowe słowo kluczowe w klauzuli [OrderBy](orderby-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="6ec4b-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="6ec4b-133">descending</span><span class="sxs-lookup"><span data-stu-id="6ec4b-133">descending</span></span>](descending.md)|<span data-ttu-id="6ec4b-134">Kontekstowe słowo kluczowe w klauzuli [OrderBy](orderby-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="6ec4b-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="6ec4b-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ec4b-135">See also</span></span>

- [<span data-ttu-id="6ec4b-136">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6ec4b-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6ec4b-137">LINQ (zapytanie zintegrowane z językiem)</span><span class="sxs-lookup"><span data-stu-id="6ec4b-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="6ec4b-138">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="6ec4b-138">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="6ec4b-139">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="6ec4b-139">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
