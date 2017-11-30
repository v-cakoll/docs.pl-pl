---
title: Sortowanie danych (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f81065c-0c89-4bf3-a6d8-442273f8810e
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8f17c6ecad721dd3a48a01c09693b0a1cf723a5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-data-visual-basic"></a><span data-ttu-id="d0b41-102">Sortowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0b41-102">Sorting Data (Visual Basic)</span></span>
<span data-ttu-id="d0b41-103">Operacja sortowania Porządkuje elementy sekwencji na podstawie jednego lub więcej atrybutów.</span><span class="sxs-lookup"><span data-stu-id="d0b41-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="d0b41-104">Pierwsze kryterium sortowania sortuje podstawowe elementy.</span><span class="sxs-lookup"><span data-stu-id="d0b41-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="d0b41-105">Określając drugie kryterium sortowania, można sortować elementów w każdej grupie głównej sortowania.</span><span class="sxs-lookup"><span data-stu-id="d0b41-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="d0b41-106">Na poniższej ilustracji przedstawiono wyniki operacji alfabetycznej sortowania na sekwencję znaków.</span><span class="sxs-lookup"><span data-stu-id="d0b41-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 <span data-ttu-id="d0b41-107">![Operacja sortowania LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span><span class="sxs-lookup"><span data-stu-id="d0b41-107">![LINQ Sorting Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span></span>  
  
 <span data-ttu-id="d0b41-108">Metody operator standardowej kwerendy, które sortować dane są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="d0b41-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0b41-109">Metody</span><span class="sxs-lookup"><span data-stu-id="d0b41-109">Methods</span></span>  
  
|<span data-ttu-id="d0b41-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="d0b41-110">Method Name</span></span>|<span data-ttu-id="d0b41-111">Opis</span><span class="sxs-lookup"><span data-stu-id="d0b41-111">Description</span></span>|<span data-ttu-id="d0b41-112">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d0b41-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="d0b41-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="d0b41-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="d0b41-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="d0b41-114">OrderBy</span></span>|<span data-ttu-id="d0b41-115">Sortuje wartości w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="d0b41-115">Sorts values in ascending order.</span></span>|`Order By`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d0b41-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="d0b41-116">OrderByDescending</span></span>|<span data-ttu-id="d0b41-117">Sortuje wartości w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="d0b41-117">Sorts values in descending order.</span></span>|`Order By … Descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d0b41-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="d0b41-118">ThenBy</span></span>|<span data-ttu-id="d0b41-119">Wykonuje dodatkowej sortowania w porządku rosnącym.</span><span class="sxs-lookup"><span data-stu-id="d0b41-119">Performs a secondary sort in ascending order.</span></span>|`Order By …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d0b41-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="d0b41-120">ThenByDescending</span></span>|<span data-ttu-id="d0b41-121">Sortuje dodatkowej w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="d0b41-121">Performs a secondary sort in descending order.</span></span>|`Order By …, … Descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d0b41-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="d0b41-122">Reverse</span></span>|<span data-ttu-id="d0b41-123">Odwraca kolejność elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d0b41-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="d0b41-124">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="d0b41-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="d0b41-125">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="d0b41-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="d0b41-126">Przykłady głównej sortowania</span><span class="sxs-lookup"><span data-stu-id="d0b41-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="d0b41-127">Podstawowy sortowanie w kolejności rosnącej</span><span class="sxs-lookup"><span data-stu-id="d0b41-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="d0b41-128">W poniższym przykładzie pokazano sposób użycia `Order By` klauzuli w kwerendzie LINQ, aby posortować ciągów w tablicy, długość ciągu w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="d0b41-128">The following example demonstrates how to use the `Order By` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="d0b41-129">Podstawowy malejącym</span><span class="sxs-lookup"><span data-stu-id="d0b41-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="d0b41-130">Kolejnym przykładzie pokazano, jak używać `Order By Descending` klauzuli w zapytania LINQ, aby posortować ciągi według ich pierwsza litera w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="d0b41-130">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="d0b41-131">Przykłady sortowania</span><span class="sxs-lookup"><span data-stu-id="d0b41-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="d0b41-132">Sortowanie w kolejności rosnącej dodatkowej</span><span class="sxs-lookup"><span data-stu-id="d0b41-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="d0b41-133">W poniższym przykładzie pokazano sposób użycia `Order By` podklauzul LINQ do wykonywania podstawowych i pomocniczych sortowanie ciągów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="d0b41-133">The following example demonstrates how to use the `Order By` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="d0b41-134">Ciągi są sortowane przede wszystkim przez długości i przetworzonych przez pierwszą literę ciągu, zarówno w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="d0b41-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="d0b41-135">Dodatkowej malejącym</span><span class="sxs-lookup"><span data-stu-id="d0b41-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="d0b41-136">Kolejnym przykładzie pokazano, jak używać `Order By Descending` klauzuli w zapytania LINQ, aby wykonać podstawowy sortowania, w rosnącej kolejności i drugiego sortowania w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="d0b41-136">The next example demonstrates how to use the `Order By Descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="d0b41-137">Ciągi są sortowane przede wszystkim przez długości i przetworzonych przez pierwszą literę ciągu.</span><span class="sxs-lookup"><span data-stu-id="d0b41-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d0b41-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0b41-138">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="d0b41-139">Operatory standardowe zapytań — omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0b41-139">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="d0b41-140">Order By — klauzula</span><span class="sxs-lookup"><span data-stu-id="d0b41-140">Order By Clause</span></span>](../../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="d0b41-141">Porady: sortowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="d0b41-141">How to: Sort Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-sort-query-results-by-using-linq.md)  
 [<span data-ttu-id="d0b41-142">Porady: sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d0b41-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
