---
title: Sortowanie danych (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
ms.openlocfilehash: 5875b15dbdec69aca653b8f6cca4dd07fc9af343
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58126256"
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="c11e9-102">Sortowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c11e9-102">Sorting Data (Visual Basic)</span></span>
<span data-ttu-id="c11e9-103">Operacja sortowania Porządkuje elementy które sekwencji, w oparciu o jeden lub więcej atrybutów.</span><span class="sxs-lookup"><span data-stu-id="c11e9-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="c11e9-104">Kryterium sortowania sortuje podstawowe elementy.</span><span class="sxs-lookup"><span data-stu-id="c11e9-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="c11e9-105">Określając drugie kryterium sortowania, możesz sortować elementów w każdej grupie podstawowej sortowania.</span><span class="sxs-lookup"><span data-stu-id="c11e9-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="c11e9-106">Poniższa ilustracja przedstawia wyniki operacji sortowania alfabetycznego na sekwencję znaków.</span><span class="sxs-lookup"><span data-stu-id="c11e9-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 ![Grafika przedstawiająca operacji sortowania alfabetycznego.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="c11e9-108">Metody standardowego operatora zapytań, sortować dane, które są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="c11e9-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c11e9-109">Metody</span><span class="sxs-lookup"><span data-stu-id="c11e9-109">Methods</span></span>  
  
|<span data-ttu-id="c11e9-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="c11e9-110">Method Name</span></span>|<span data-ttu-id="c11e9-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c11e9-111">Description</span></span>|<span data-ttu-id="c11e9-112">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c11e9-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="c11e9-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="c11e9-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="c11e9-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="c11e9-114">OrderBy</span></span>|<span data-ttu-id="c11e9-115">Sortuje wartości w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="c11e9-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c11e9-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="c11e9-116">OrderByDescending</span></span>|<span data-ttu-id="c11e9-117">Sortuje wartości w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="c11e9-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c11e9-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="c11e9-118">ThenBy</span></span>|<span data-ttu-id="c11e9-119">Wykonuje dodatkowej sortowanie w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="c11e9-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c11e9-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="c11e9-120">ThenByDescending</span></span>|<span data-ttu-id="c11e9-121">Wykonuje dodatkowej sortowanie w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="c11e9-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c11e9-122">zwrotny</span><span class="sxs-lookup"><span data-stu-id="c11e9-122">Reverse</span></span>|<span data-ttu-id="c11e9-123">Odwraca kolejność elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c11e9-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="c11e9-124">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="c11e9-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="c11e9-125">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="c11e9-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="c11e9-126">Przykłady podstawowej sortowania</span><span class="sxs-lookup"><span data-stu-id="c11e9-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="c11e9-127">Sortowanie w kolejności rosnącej podstawowego</span><span class="sxs-lookup"><span data-stu-id="c11e9-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="c11e9-128">Poniższy przykład pokazuje sposób użycia `Order By` klauzuli w zapytaniu LINQ, aby posortować ciągi w tablicy przez długość ciągu, w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="c11e9-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="c11e9-129">Podstawowy Sortuj malejąco</span><span class="sxs-lookup"><span data-stu-id="c11e9-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="c11e9-130">Następny przykład pokazuje sposób użycia `Order By Descending` klauzuli w zapytaniu LINQ, aby posortować ciągi według ich pierwsza litera w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="c11e9-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="c11e9-131">Sortowanie dodatkowe przykłady</span><span class="sxs-lookup"><span data-stu-id="c11e9-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="c11e9-132">Sortowanie w kolejności rosnącej dodatkowej</span><span class="sxs-lookup"><span data-stu-id="c11e9-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="c11e9-133">Poniższy przykład pokazuje sposób użycia `Order By` klauzuli w zapytaniu programu LINQ do wykonywania podstawowych i pomocniczych sortowania ciągów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="c11e9-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="c11e9-134">Ciągi są sortowane, przede wszystkim przez długość i przetworzonych przez pierwszą literę ciągu, zarówno w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="c11e9-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="c11e9-135">Pomocniczy Sortuj malejąco</span><span class="sxs-lookup"><span data-stu-id="c11e9-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="c11e9-136">Następny przykład pokazuje sposób użycia `Order By Descending` klauzuli w zapytaniu LINQ, aby wykonać podstawowy sortowania, w kolejności rosnącej kolejności i dodatkowej sortowania, w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="c11e9-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="c11e9-137">Ciągi są sortowane, przede wszystkim przez długość i przetworzonych przez pierwszą literę ciągu.</span><span class="sxs-lookup"><span data-stu-id="c11e9-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c11e9-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c11e9-138">See also</span></span>
- <xref:System.Linq>
- [<span data-ttu-id="c11e9-139">Omówienie operatorów standardowej kwerendy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c11e9-139">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="c11e9-140">Order By, klauzula</span><span class="sxs-lookup"><span data-stu-id="c11e9-140">Order By Clause</span></span>](../../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="c11e9-141">Instrukcje: Sortowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="c11e9-141">How to: Sort Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)
- [<span data-ttu-id="c11e9-142">Instrukcje: Sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c11e9-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
