---
title: Sortowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 8db5ab2ead0e59b8d41d83704ff237d4493155c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346455"
---
# <a name="sorting-data-c"></a><span data-ttu-id="88d51-102">Sortowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="88d51-102">Sorting Data (C#)</span></span>
<span data-ttu-id="88d51-103">Operacja sortowania Porządkuje elementy sekwencji na podstawie jednego lub większej liczby atrybutów.</span><span class="sxs-lookup"><span data-stu-id="88d51-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="88d51-104">Pierwsze kryterium sortowania wykonuje podstawowe sortowanie elementów.</span><span class="sxs-lookup"><span data-stu-id="88d51-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="88d51-105">Określając drugie kryterium sortowania, można sortować elementy w ramach każdej podstawowej grupy sortowania.</span><span class="sxs-lookup"><span data-stu-id="88d51-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="88d51-106">Na poniższej ilustracji przedstawiono wyniki alfabetycznej operacji sortowania na sekwencji znaków:</span><span class="sxs-lookup"><span data-stu-id="88d51-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span> 
  
 ![Grafika pokazująca alfabetyczną operację sortowania.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="88d51-108">Standardowe metody operatorów zapytań, które sortują dane, są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="88d51-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="88d51-109">Metody</span><span class="sxs-lookup"><span data-stu-id="88d51-109">Methods</span></span>  
  
|<span data-ttu-id="88d51-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="88d51-110">Method Name</span></span>|<span data-ttu-id="88d51-111">Opis</span><span class="sxs-lookup"><span data-stu-id="88d51-111">Description</span></span>|<span data-ttu-id="88d51-112">C#Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="88d51-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="88d51-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="88d51-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="88d51-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="88d51-114">OrderBy</span></span>|<span data-ttu-id="88d51-115">Sortuje wartości w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="88d51-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="88d51-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="88d51-116">OrderByDescending</span></span>|<span data-ttu-id="88d51-117">Sortuje wartości w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="88d51-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="88d51-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="88d51-118">ThenBy</span></span>|<span data-ttu-id="88d51-119">Wykonuje sortowanie pomocnicze w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="88d51-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="88d51-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="88d51-120">ThenByDescending</span></span>|<span data-ttu-id="88d51-121">Wykonuje sortowanie pomocnicze w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="88d51-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="88d51-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="88d51-122">Reverse</span></span>|<span data-ttu-id="88d51-123">Odwraca kolejność elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="88d51-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="88d51-124">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="88d51-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="88d51-125">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="88d51-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="88d51-126">Główne przykłady sortowania</span><span class="sxs-lookup"><span data-stu-id="88d51-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="88d51-127">Podstawowe sortowanie rosnące</span><span class="sxs-lookup"><span data-stu-id="88d51-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="88d51-128">Poniższy przykład ilustruje sposób użycia klauzuli `orderby` w zapytaniu LINQ do sortowania ciągów w tablicy według długości ciągu w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="88d51-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="88d51-129">Sortowanie sortowania podstawowego</span><span class="sxs-lookup"><span data-stu-id="88d51-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="88d51-130">W następnym przykładzie pokazano, jak używać klauzuli `orderby descending` w zapytaniu LINQ do sortowania ciągów według ich pierwszej litery, w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="88d51-130">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="88d51-131">Przykłady sortowania pomocniczego</span><span class="sxs-lookup"><span data-stu-id="88d51-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="88d51-132">Sortowanie pomocnicze rosnąco</span><span class="sxs-lookup"><span data-stu-id="88d51-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="88d51-133">W poniższym przykładzie pokazano, jak używać klauzuli `orderby` w zapytaniu LINQ, aby wykonać podstawowe i pomocnicze sortowanie ciągów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="88d51-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="88d51-134">Ciągi są sortowane głównie według długości i secondarily przez pierwszą literę ciągu, zarówno w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="88d51-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="88d51-135">Sortowanie malejąco</span><span class="sxs-lookup"><span data-stu-id="88d51-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="88d51-136">W następnym przykładzie pokazano, jak używać klauzuli `orderby descending` w zapytaniu LINQ do wykonywania sortowania podstawowego w kolejności rosnącej i sortowania pomocniczego w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="88d51-136">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="88d51-137">Ciągi są sortowane głównie według długości i secondarily przez pierwszą literę ciągu.</span><span class="sxs-lookup"><span data-stu-id="88d51-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88d51-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88d51-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="88d51-139">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="88d51-139">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="88d51-140">orderby, klauzula</span><span class="sxs-lookup"><span data-stu-id="88d51-140">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="88d51-141">Kolejność wyników klauzuli join</span><span class="sxs-lookup"><span data-stu-id="88d51-141">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="88d51-142">Sortowanie lub filtrowanie danych tekstowych według dowolnego wyrazu lub pola (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="88d51-142">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
