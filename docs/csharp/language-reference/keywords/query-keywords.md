---
title: Słowa kluczowe zapytania C# — odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 44af3bf1a7c013c16c7b4a4528c3516621bea149
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422538"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="036a1-102">Słowa kluczowe zapytaniaC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="036a1-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="036a1-103">Ta sekcja zawiera kontekstowe słowa kluczowe używane w wyrażeniach zapytań.</span><span class="sxs-lookup"><span data-stu-id="036a1-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="036a1-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="036a1-104">In this section</span></span>

|<span data-ttu-id="036a1-105">Klauzula</span><span class="sxs-lookup"><span data-stu-id="036a1-105">Clause</span></span>|<span data-ttu-id="036a1-106">Opis</span><span class="sxs-lookup"><span data-stu-id="036a1-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="036a1-107">wniosek</span><span class="sxs-lookup"><span data-stu-id="036a1-107">from</span></span>](from-clause.md)|<span data-ttu-id="036a1-108">Określa źródło danych i zmienną zakresu (podobnie jak Zmienna iteracji).</span><span class="sxs-lookup"><span data-stu-id="036a1-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="036a1-109">miejscu</span><span class="sxs-lookup"><span data-stu-id="036a1-109">where</span></span>](where-clause.md)|<span data-ttu-id="036a1-110">Filtruje elementy źródłowe na podstawie co najmniej jednego wyrażenia logicznego oddzielonego operatorami logicznymi i i lub (`&&` lub <code>&#124;&#124;</code>).</span><span class="sxs-lookup"><span data-stu-id="036a1-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="036a1-111">zaznaczenia</span><span class="sxs-lookup"><span data-stu-id="036a1-111">select</span></span>](select-clause.md)|<span data-ttu-id="036a1-112">Określa typ i kształt, które elementy w zwracanej sekwencji będą miały miejsce, gdy zapytanie zostanie wykonane.</span><span class="sxs-lookup"><span data-stu-id="036a1-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="036a1-113">Group</span><span class="sxs-lookup"><span data-stu-id="036a1-113">group</span></span>](group-clause.md)|<span data-ttu-id="036a1-114">Grupuje wyniki zapytania zgodnie z określoną wartością klucza.</span><span class="sxs-lookup"><span data-stu-id="036a1-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="036a1-115">into</span><span class="sxs-lookup"><span data-stu-id="036a1-115">into</span></span>](into.md)|<span data-ttu-id="036a1-116">Dostarcza identyfikator, który może być używany jako odwołanie do wyników klauzuli join, Group lub SELECT.</span><span class="sxs-lookup"><span data-stu-id="036a1-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="036a1-117">OrderBy</span><span class="sxs-lookup"><span data-stu-id="036a1-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="036a1-118">Sortuje wyniki zapytania w porządku rosnącym lub malejącym w oparciu o domyślną funkcję porównującą dla typu elementu.</span><span class="sxs-lookup"><span data-stu-id="036a1-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="036a1-119">Złącza</span><span class="sxs-lookup"><span data-stu-id="036a1-119">join</span></span>](join-clause.md)|<span data-ttu-id="036a1-120">Łączy dwa źródła danych na podstawie porównania równości między dwoma określonymi kryteriami dopasowywania.</span><span class="sxs-lookup"><span data-stu-id="036a1-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="036a1-121">wpuść</span><span class="sxs-lookup"><span data-stu-id="036a1-121">let</span></span>](let-clause.md)|<span data-ttu-id="036a1-122">Wprowadza zmienną zakresu do przechowywania wyników podwyrażenia w wyrażeniu zapytania.</span><span class="sxs-lookup"><span data-stu-id="036a1-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="036a1-123">in</span><span class="sxs-lookup"><span data-stu-id="036a1-123">in</span></span>](in.md)|<span data-ttu-id="036a1-124">Kontekstowe słowo kluczowe w klauzuli [Join](join-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="036a1-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="036a1-125">on</span><span class="sxs-lookup"><span data-stu-id="036a1-125">on</span></span>](on.md)|<span data-ttu-id="036a1-126">Kontekstowe słowo kluczowe w klauzuli [Join](join-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="036a1-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="036a1-127">equals</span><span class="sxs-lookup"><span data-stu-id="036a1-127">equals</span></span>](equals.md)|<span data-ttu-id="036a1-128">Kontekstowe słowo kluczowe w klauzuli [Join](join-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="036a1-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="036a1-129">by</span><span class="sxs-lookup"><span data-stu-id="036a1-129">by</span></span>](by.md)|<span data-ttu-id="036a1-130">Kontekstowe słowo kluczowe w klauzuli [Group](group-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="036a1-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="036a1-131">ascending</span><span class="sxs-lookup"><span data-stu-id="036a1-131">ascending</span></span>](ascending.md)|<span data-ttu-id="036a1-132">Kontekstowe słowo kluczowe w klauzuli [OrderBy](orderby-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="036a1-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="036a1-133">descending</span><span class="sxs-lookup"><span data-stu-id="036a1-133">descending</span></span>](descending.md)|<span data-ttu-id="036a1-134">Kontekstowe słowo kluczowe w klauzuli [OrderBy](orderby-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="036a1-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="036a1-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="036a1-135">See also</span></span>

- [<span data-ttu-id="036a1-136">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="036a1-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="036a1-137">LINQ (zapytanie zintegrowane z językiem)</span><span class="sxs-lookup"><span data-stu-id="036a1-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="036a1-138">LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="036a1-138">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="036a1-139">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="036a1-139">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
