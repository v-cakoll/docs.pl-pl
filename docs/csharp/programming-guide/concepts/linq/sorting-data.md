---
title: Sortowanie danych (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f5756c87f50e759542d0d1ccbb71710ad9eb6e27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sorting-data-c"></a><span data-ttu-id="3d333-102">Sortowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="3d333-102">Sorting Data (C#)</span></span>
<span data-ttu-id="3d333-103">Operacja sortowania Porządkuje elementy sekwencji na podstawie jednego lub więcej atrybutów.</span><span class="sxs-lookup"><span data-stu-id="3d333-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="3d333-104">Pierwsze kryterium sortowania sortuje podstawowe elementy.</span><span class="sxs-lookup"><span data-stu-id="3d333-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="3d333-105">Określając drugie kryterium sortowania, można sortować elementów w każdej grupie głównej sortowania.</span><span class="sxs-lookup"><span data-stu-id="3d333-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="3d333-106">Na poniższej ilustracji przedstawiono wyniki operacji alfabetycznej sortowania na sekwencję znaków.</span><span class="sxs-lookup"><span data-stu-id="3d333-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 <span data-ttu-id="3d333-107">![Operacja sortowania LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span><span class="sxs-lookup"><span data-stu-id="3d333-107">![LINQ Sorting Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span></span>  
  
 <span data-ttu-id="3d333-108">Metody operator standardowej kwerendy, które sortować dane są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="3d333-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3d333-109">Metody</span><span class="sxs-lookup"><span data-stu-id="3d333-109">Methods</span></span>  
  
|<span data-ttu-id="3d333-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="3d333-110">Method Name</span></span>|<span data-ttu-id="3d333-111">Opis</span><span class="sxs-lookup"><span data-stu-id="3d333-111">Description</span></span>|<span data-ttu-id="3d333-112">Składnia wyrażenia zapytania C#</span><span class="sxs-lookup"><span data-stu-id="3d333-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="3d333-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="3d333-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="3d333-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="3d333-114">OrderBy</span></span>|<span data-ttu-id="3d333-115">Sortuje wartości w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="3d333-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3d333-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="3d333-116">OrderByDescending</span></span>|<span data-ttu-id="3d333-117">Sortuje wartości w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="3d333-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3d333-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="3d333-118">ThenBy</span></span>|<span data-ttu-id="3d333-119">Wykonuje dodatkowej sortowania w porządku rosnącym.</span><span class="sxs-lookup"><span data-stu-id="3d333-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3d333-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="3d333-120">ThenByDescending</span></span>|<span data-ttu-id="3d333-121">Sortuje dodatkowej w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="3d333-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3d333-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="3d333-122">Reverse</span></span>|<span data-ttu-id="3d333-123">Odwraca kolejność elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3d333-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="3d333-124">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="3d333-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="3d333-125">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="3d333-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="3d333-126">Przykłady głównej sortowania</span><span class="sxs-lookup"><span data-stu-id="3d333-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="3d333-127">Podstawowy sortowanie w kolejności rosnącej</span><span class="sxs-lookup"><span data-stu-id="3d333-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="3d333-128">W poniższym przykładzie pokazano sposób użycia `orderby` klauzuli w kwerendzie LINQ, aby posortować ciągów w tablicy, długość ciągu w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="3d333-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    brown  
    jumps  
*/  
```  
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="3d333-129">Podstawowy malejącym</span><span class="sxs-lookup"><span data-stu-id="3d333-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="3d333-130">Kolejnym przykładzie pokazano, jak używać `orderby``descending` klauzuli w zapytania LINQ, aby posortować ciągi według ich pierwsza litera w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="3d333-130">The next example demonstrates how to use the `orderby``descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    quick  
    jumps  
    fox  
    brown  
*/  
```  
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="3d333-131">Przykłady sortowania</span><span class="sxs-lookup"><span data-stu-id="3d333-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="3d333-132">Sortowanie w kolejności rosnącej dodatkowej</span><span class="sxs-lookup"><span data-stu-id="3d333-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="3d333-133">W poniższym przykładzie pokazano sposób użycia `orderby` podklauzul LINQ do wykonywania podstawowych i pomocniczych sortowanie ciągów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="3d333-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="3d333-134">Ciągi są sortowane przede wszystkim przez długości i przetworzonych przez pierwszą literę ciągu, zarówno w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="3d333-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1)  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    fox  
    the  
    brown  
    jumps  
    quick  
*/  
```  
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="3d333-135">Dodatkowej malejącym</span><span class="sxs-lookup"><span data-stu-id="3d333-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="3d333-136">Kolejnym przykładzie pokazano, jak używać `orderby``descending` klauzuli w zapytania LINQ, aby wykonać podstawowy sortowania, w rosnącej kolejności i drugiego sortowania w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="3d333-136">The next example demonstrates how to use the `orderby``descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="3d333-137">Ciągi są sortowane przede wszystkim przez długości i przetworzonych przez pierwszą literę ciągu.</span><span class="sxs-lookup"><span data-stu-id="3d333-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    jumps  
    brown  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d333-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d333-138">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="3d333-139">Operatory standardowe zapytań — omówienie (C#)</span><span class="sxs-lookup"><span data-stu-id="3d333-139">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="3d333-140">Klauzula OrderBy</span><span class="sxs-lookup"><span data-stu-id="3d333-140">orderby clause</span></span>](../../../../csharp/language-reference/keywords/orderby-clause.md)  
 [<span data-ttu-id="3d333-141">Porady: kolejność wyników klauzuli Join</span><span class="sxs-lookup"><span data-stu-id="3d333-141">How to: Order the Results of a Join Clause</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
 [<span data-ttu-id="3d333-142">Porady: sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3d333-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
