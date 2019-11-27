---
title: Sortowanie danych
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: f1d4d8afb9b6e176a7ac048ba3270ecafdce24c9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350584"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="36abb-102">Sortowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36abb-102">Sorting Data (Visual Basic)</span></span>

<span data-ttu-id="36abb-103">Operacja sortowania Porządkuje elementy sekwencji na podstawie jednego lub większej liczby atrybutów.</span><span class="sxs-lookup"><span data-stu-id="36abb-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="36abb-104">Pierwsze kryterium sortowania wykonuje podstawowe sortowanie elementów.</span><span class="sxs-lookup"><span data-stu-id="36abb-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="36abb-105">Określając drugie kryterium sortowania, można sortować elementy w ramach każdej podstawowej grupy sortowania.</span><span class="sxs-lookup"><span data-stu-id="36abb-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>

<span data-ttu-id="36abb-106">Na poniższej ilustracji przedstawiono wyniki alfabetycznej operacji sortowania na sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="36abb-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>

![Grafika pokazująca alfabetyczną operację sortowania.](./media/sorting-data/alphabetical-sort-operation.png)

<span data-ttu-id="36abb-108">Standardowe metody operatorów zapytań, które sortują dane, są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="36abb-108">The standard query operator methods that sort data are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="36abb-109">Metody</span><span class="sxs-lookup"><span data-stu-id="36abb-109">Methods</span></span>

|<span data-ttu-id="36abb-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="36abb-110">Method Name</span></span>|<span data-ttu-id="36abb-111">Opis</span><span class="sxs-lookup"><span data-stu-id="36abb-111">Description</span></span>|<span data-ttu-id="36abb-112">Składnia wyrażenia zapytania Visual Basic</span><span class="sxs-lookup"><span data-stu-id="36abb-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="36abb-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="36abb-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="36abb-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="36abb-114">OrderBy</span></span>|<span data-ttu-id="36abb-115">Sortuje wartości w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="36abb-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="36abb-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="36abb-116">OrderByDescending</span></span>|<span data-ttu-id="36abb-117">Sortuje wartości w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="36abb-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="36abb-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="36abb-118">ThenBy</span></span>|<span data-ttu-id="36abb-119">Wykonuje sortowanie pomocnicze w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="36abb-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="36abb-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="36abb-120">ThenByDescending</span></span>|<span data-ttu-id="36abb-121">Wykonuje sortowanie pomocnicze w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="36abb-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="36abb-122">Cofnięci</span><span class="sxs-lookup"><span data-stu-id="36abb-122">Reverse</span></span>|<span data-ttu-id="36abb-123">Odwraca kolejność elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="36abb-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="36abb-124">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="36abb-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="36abb-125">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="36abb-125">Query Expression Syntax Examples</span></span>

### <a name="primary-sort-examples"></a><span data-ttu-id="36abb-126">Główne przykłady sortowania</span><span class="sxs-lookup"><span data-stu-id="36abb-126">Primary Sort Examples</span></span>

#### <a name="primary-ascending-sort"></a><span data-ttu-id="36abb-127">Podstawowe sortowanie rosnące</span><span class="sxs-lookup"><span data-stu-id="36abb-127">Primary Ascending Sort</span></span>

<span data-ttu-id="36abb-128">Poniższy przykład ilustruje sposób użycia klauzuli `Order By` w zapytaniu LINQ do sortowania ciągów w tablicy według długości ciągu w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="36abb-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>

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

#### <a name="primary-descending-sort"></a><span data-ttu-id="36abb-129">Sortowanie sortowania podstawowego</span><span class="sxs-lookup"><span data-stu-id="36abb-129">Primary Descending Sort</span></span>

<span data-ttu-id="36abb-130">W następnym przykładzie pokazano, jak używać klauzuli `Order By Descending` w zapytaniu LINQ do sortowania ciągów według ich pierwszej litery, w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="36abb-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>

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

### <a name="secondary-sort-examples"></a><span data-ttu-id="36abb-131">Przykłady sortowania pomocniczego</span><span class="sxs-lookup"><span data-stu-id="36abb-131">Secondary Sort Examples</span></span>

#### <a name="secondary-ascending-sort"></a><span data-ttu-id="36abb-132">Sortowanie pomocnicze rosnąco</span><span class="sxs-lookup"><span data-stu-id="36abb-132">Secondary Ascending Sort</span></span>

<span data-ttu-id="36abb-133">W poniższym przykładzie pokazano, jak używać klauzuli `Order By` w zapytaniu LINQ, aby wykonać podstawowe i pomocnicze sortowanie ciągów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="36abb-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="36abb-134">Ciągi są sortowane głównie według długości i secondarily przez pierwszą literę ciągu, zarówno w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="36abb-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>

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

#### <a name="secondary-descending-sort"></a><span data-ttu-id="36abb-135">Sortowanie malejąco</span><span class="sxs-lookup"><span data-stu-id="36abb-135">Secondary Descending Sort</span></span>

<span data-ttu-id="36abb-136">W następnym przykładzie pokazano, jak używać klauzuli `Order By Descending` w zapytaniu LINQ do wykonywania sortowania podstawowego w kolejności rosnącej i sortowania pomocniczego w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="36abb-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="36abb-137">Ciągi są sortowane głównie według długości i secondarily przez pierwszą literę ciągu.</span><span class="sxs-lookup"><span data-stu-id="36abb-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="36abb-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36abb-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="36abb-139">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36abb-139">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="36abb-140">Order By, klauzula</span><span class="sxs-lookup"><span data-stu-id="36abb-140">Order By Clause</span></span>](../../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="36abb-141">Instrukcje: sortowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="36abb-141">How to: Sort Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [<span data-ttu-id="36abb-142">Instrukcje: sortowanie lub filtrowanie danych tekstowych według dowolnego wyrazu lub pola (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36abb-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
