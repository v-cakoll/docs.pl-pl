---
title: Sortowanie danych
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: a5ccff745995ed7f41731cf98fb7c49d3247d994
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406797"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="4effc-102">Sortowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4effc-102">Sorting Data (Visual Basic)</span></span>

<span data-ttu-id="4effc-103">Operacja sortowania Porządkuje elementy sekwencji na podstawie jednego lub większej liczby atrybutów.</span><span class="sxs-lookup"><span data-stu-id="4effc-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="4effc-104">Pierwsze kryterium sortowania wykonuje podstawowe sortowanie elementów.</span><span class="sxs-lookup"><span data-stu-id="4effc-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="4effc-105">Określając drugie kryterium sortowania, można sortować elementy w ramach każdej podstawowej grupy sortowania.</span><span class="sxs-lookup"><span data-stu-id="4effc-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>

<span data-ttu-id="4effc-106">Na poniższej ilustracji przedstawiono wyniki alfabetycznej operacji sortowania na sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="4effc-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>

![Grafika pokazująca alfabetyczną operację sortowania.](./media/sorting-data/alphabetical-sort-operation.png)

<span data-ttu-id="4effc-108">Standardowe metody operatorów zapytań, które sortują dane, są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="4effc-108">The standard query operator methods that sort data are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="4effc-109">Metody</span><span class="sxs-lookup"><span data-stu-id="4effc-109">Methods</span></span>

|<span data-ttu-id="4effc-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="4effc-110">Method Name</span></span>|<span data-ttu-id="4effc-111">Opis</span><span class="sxs-lookup"><span data-stu-id="4effc-111">Description</span></span>|<span data-ttu-id="4effc-112">Składnia wyrażenia zapytania Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4effc-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="4effc-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="4effc-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="4effc-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="4effc-114">OrderBy</span></span>|<span data-ttu-id="4effc-115">Sortuje wartości w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="4effc-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="4effc-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="4effc-116">OrderByDescending</span></span>|<span data-ttu-id="4effc-117">Sortuje wartości w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="4effc-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="4effc-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="4effc-118">ThenBy</span></span>|<span data-ttu-id="4effc-119">Wykonuje sortowanie pomocnicze w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="4effc-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="4effc-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="4effc-120">ThenByDescending</span></span>|<span data-ttu-id="4effc-121">Wykonuje sortowanie pomocnicze w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="4effc-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="4effc-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="4effc-122">Reverse</span></span>|<span data-ttu-id="4effc-123">Odwraca kolejność elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4effc-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="4effc-124">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="4effc-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="4effc-125">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="4effc-125">Query Expression Syntax Examples</span></span>

### <a name="primary-sort-examples"></a><span data-ttu-id="4effc-126">Główne przykłady sortowania</span><span class="sxs-lookup"><span data-stu-id="4effc-126">Primary Sort Examples</span></span>

#### <a name="primary-ascending-sort"></a><span data-ttu-id="4effc-127">Podstawowe sortowanie rosnące</span><span class="sxs-lookup"><span data-stu-id="4effc-127">Primary Ascending Sort</span></span>

<span data-ttu-id="4effc-128">Poniższy przykład ilustruje sposób użycia `Order By` klauzuli w zapytaniu LINQ do sortowania ciągów w tablicy według długości ciągu w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="4effc-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
' quick
' brown
' jumps
```

#### <a name="primary-descending-sort"></a><span data-ttu-id="4effc-129">Sortowanie sortowania podstawowego</span><span class="sxs-lookup"><span data-stu-id="4effc-129">Primary Descending Sort</span></span>

<span data-ttu-id="4effc-130">W następnym przykładzie pokazano, jak używać `Order By Descending` klauzuli w zapytaniu LINQ do sortowania ciągów według ich pierwszej litery, w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="4effc-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Substring(0, 1) Descending
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' quick
' jumps
' fox
' brown
```

### <a name="secondary-sort-examples"></a><span data-ttu-id="4effc-131">Przykłady sortowania pomocniczego</span><span class="sxs-lookup"><span data-stu-id="4effc-131">Secondary Sort Examples</span></span>

#### <a name="secondary-ascending-sort"></a><span data-ttu-id="4effc-132">Sortowanie pomocnicze rosnąco</span><span class="sxs-lookup"><span data-stu-id="4effc-132">Secondary Ascending Sort</span></span>

<span data-ttu-id="4effc-133">Poniższy przykład ilustruje sposób użycia `Order By` klauzuli w zapytaniu LINQ do wykonywania podstawowego i pomocniczego sortowania ciągów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="4effc-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="4effc-134">Ciągi są sortowane głównie według długości i secondarily przez pierwszą literę ciągu, zarówno w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="4effc-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length, word.Substring(0, 1)
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' fox
' the
' brown
' jumps
' quick
```

#### <a name="secondary-descending-sort"></a><span data-ttu-id="4effc-135">Sortowanie malejąco</span><span class="sxs-lookup"><span data-stu-id="4effc-135">Secondary Descending Sort</span></span>

<span data-ttu-id="4effc-136">W następnym przykładzie pokazano, jak używać `Order By Descending` klauzuli w zapytaniu LINQ do wykonywania sortowania podstawowego w kolejności rosnącej i sortowania pomocniczego w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="4effc-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="4effc-137">Ciągi są sortowane głównie według długości i secondarily przez pierwszą literę ciągu.</span><span class="sxs-lookup"><span data-stu-id="4effc-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>

```vb
Dim words = {"the", "quick", "brown", "fox", "jumps"}

Dim sortQuery = From word In words
                Order By word.Length, word.Substring(0, 1) Descending
                Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In sortQuery
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' fox
' the
' quick
' jumps
' brown
```

## <a name="see-also"></a><span data-ttu-id="4effc-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4effc-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="4effc-139">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4effc-139">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="4effc-140">Order By, klauzula</span><span class="sxs-lookup"><span data-stu-id="4effc-140">Order By Clause</span></span>](../../../language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="4effc-141">Instrukcje: sortowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="4effc-141">How to: Sort Query Results</span></span>](../../language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [<span data-ttu-id="4effc-142">Instrukcje: sortowanie lub filtrowanie danych tekstowych według dowolnego wyrazu lub pola (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4effc-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
