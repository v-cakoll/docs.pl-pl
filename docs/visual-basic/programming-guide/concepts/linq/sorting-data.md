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
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="f5460-102">Sorting Data (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5460-102">Sorting Data (Visual Basic)</span></span>

<span data-ttu-id="f5460-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span><span class="sxs-lookup"><span data-stu-id="f5460-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="f5460-104">The first sort criterion performs a primary sort on the elements.</span><span class="sxs-lookup"><span data-stu-id="f5460-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="f5460-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span><span class="sxs-lookup"><span data-stu-id="f5460-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>

<span data-ttu-id="f5460-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span><span class="sxs-lookup"><span data-stu-id="f5460-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>

![Graphic that shows an alphabetical sort operation.](./media/sorting-data/alphabetical-sort-operation.png)

<span data-ttu-id="f5460-108">The standard query operator methods that sort data are listed in the following section.</span><span class="sxs-lookup"><span data-stu-id="f5460-108">The standard query operator methods that sort data are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="f5460-109">Metody</span><span class="sxs-lookup"><span data-stu-id="f5460-109">Methods</span></span>

|<span data-ttu-id="f5460-110">Method Name</span><span class="sxs-lookup"><span data-stu-id="f5460-110">Method Name</span></span>|<span data-ttu-id="f5460-111">Opis</span><span class="sxs-lookup"><span data-stu-id="f5460-111">Description</span></span>|<span data-ttu-id="f5460-112">Visual Basic Query Expression Syntax</span><span class="sxs-lookup"><span data-stu-id="f5460-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="f5460-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="f5460-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="f5460-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="f5460-114">OrderBy</span></span>|<span data-ttu-id="f5460-115">Sorts values in ascending order.</span><span class="sxs-lookup"><span data-stu-id="f5460-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="f5460-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="f5460-116">OrderByDescending</span></span>|<span data-ttu-id="f5460-117">Sorts values in descending order.</span><span class="sxs-lookup"><span data-stu-id="f5460-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="f5460-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="f5460-118">ThenBy</span></span>|<span data-ttu-id="f5460-119">Performs a secondary sort in ascending order.</span><span class="sxs-lookup"><span data-stu-id="f5460-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|
|<span data-ttu-id="f5460-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="f5460-120">ThenByDescending</span></span>|<span data-ttu-id="f5460-121">Performs a secondary sort in descending order.</span><span class="sxs-lookup"><span data-stu-id="f5460-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|
|<span data-ttu-id="f5460-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="f5460-122">Reverse</span></span>|<span data-ttu-id="f5460-123">Reverses the order of the elements in a collection.</span><span class="sxs-lookup"><span data-stu-id="f5460-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="f5460-124">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="f5460-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="f5460-125">Query Expression Syntax Examples</span><span class="sxs-lookup"><span data-stu-id="f5460-125">Query Expression Syntax Examples</span></span>

### <a name="primary-sort-examples"></a><span data-ttu-id="f5460-126">Primary Sort Examples</span><span class="sxs-lookup"><span data-stu-id="f5460-126">Primary Sort Examples</span></span>

#### <a name="primary-ascending-sort"></a><span data-ttu-id="f5460-127">Primary Ascending Sort</span><span class="sxs-lookup"><span data-stu-id="f5460-127">Primary Ascending Sort</span></span>

<span data-ttu-id="f5460-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span><span class="sxs-lookup"><span data-stu-id="f5460-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>

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

#### <a name="primary-descending-sort"></a><span data-ttu-id="f5460-129">Primary Descending Sort</span><span class="sxs-lookup"><span data-stu-id="f5460-129">Primary Descending Sort</span></span>

<span data-ttu-id="f5460-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span><span class="sxs-lookup"><span data-stu-id="f5460-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>

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

### <a name="secondary-sort-examples"></a><span data-ttu-id="f5460-131">Secondary Sort Examples</span><span class="sxs-lookup"><span data-stu-id="f5460-131">Secondary Sort Examples</span></span>

#### <a name="secondary-ascending-sort"></a><span data-ttu-id="f5460-132">Secondary Ascending Sort</span><span class="sxs-lookup"><span data-stu-id="f5460-132">Secondary Ascending Sort</span></span>

<span data-ttu-id="f5460-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span><span class="sxs-lookup"><span data-stu-id="f5460-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="f5460-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span><span class="sxs-lookup"><span data-stu-id="f5460-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>

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

#### <a name="secondary-descending-sort"></a><span data-ttu-id="f5460-135">Secondary Descending Sort</span><span class="sxs-lookup"><span data-stu-id="f5460-135">Secondary Descending Sort</span></span>

<span data-ttu-id="f5460-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span><span class="sxs-lookup"><span data-stu-id="f5460-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="f5460-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span><span class="sxs-lookup"><span data-stu-id="f5460-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f5460-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5460-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="f5460-139">Standard Query Operators Overview (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5460-139">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="f5460-140">Order By, klauzula</span><span class="sxs-lookup"><span data-stu-id="f5460-140">Order By Clause</span></span>](../../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="f5460-141">How to: Sort Query Results</span><span class="sxs-lookup"><span data-stu-id="f5460-141">How to: Sort Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [<span data-ttu-id="f5460-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5460-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
