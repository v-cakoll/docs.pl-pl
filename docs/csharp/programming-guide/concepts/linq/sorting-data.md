---
title: Sortowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 29a5e3e685bdc73536961b7783f4986796b46bdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167910"
---
# <a name="sorting-data-c"></a><span data-ttu-id="5efd2-102">Sortowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="5efd2-102">Sorting Data (C#)</span></span>
<span data-ttu-id="5efd2-103">Operacja sortowania porządkuje elementy sekwencji na podstawie jednego lub więcej atrybutów.</span><span class="sxs-lookup"><span data-stu-id="5efd2-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="5efd2-104">Pierwsze kryterium sortowania wykonuje sortowanie podstawowe na elementach.</span><span class="sxs-lookup"><span data-stu-id="5efd2-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="5efd2-105">Określając drugie kryterium sortowania, można sortować elementy w każdej podstawowej grupie sortowania.</span><span class="sxs-lookup"><span data-stu-id="5efd2-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="5efd2-106">Na poniższej ilustracji przedstawiono wyniki operacji sortowania alfabetycznego na sekwencji znaków:</span><span class="sxs-lookup"><span data-stu-id="5efd2-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span>
  
 ![Grafika przedstawiająca operację sortowania alfabetycznego.](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="5efd2-108">Standardowe metody operatora kwerendy, które sortują dane są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="5efd2-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5efd2-109">Metody</span><span class="sxs-lookup"><span data-stu-id="5efd2-109">Methods</span></span>  
  
|<span data-ttu-id="5efd2-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="5efd2-110">Method Name</span></span>|<span data-ttu-id="5efd2-111">Opis</span><span class="sxs-lookup"><span data-stu-id="5efd2-111">Description</span></span>|<span data-ttu-id="5efd2-112">Składnia wyrażenia kwerendy c#</span><span class="sxs-lookup"><span data-stu-id="5efd2-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="5efd2-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="5efd2-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="5efd2-114">Orderby</span><span class="sxs-lookup"><span data-stu-id="5efd2-114">OrderBy</span></span>|<span data-ttu-id="5efd2-115">Sortuje wartości w porządku rosnącym.</span><span class="sxs-lookup"><span data-stu-id="5efd2-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5efd2-116">Orderbydescending</span><span class="sxs-lookup"><span data-stu-id="5efd2-116">OrderByDescending</span></span>|<span data-ttu-id="5efd2-117">Sortuje wartości w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="5efd2-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5efd2-118">Thenby</span><span class="sxs-lookup"><span data-stu-id="5efd2-118">ThenBy</span></span>|<span data-ttu-id="5efd2-119">Wykonuje sortowanie pomocnicze w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="5efd2-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5efd2-120">Thenbydescending</span><span class="sxs-lookup"><span data-stu-id="5efd2-120">ThenByDescending</span></span>|<span data-ttu-id="5efd2-121">Wykonuje sortowanie pomocnicze w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="5efd2-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5efd2-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="5efd2-122">Reverse</span></span>|<span data-ttu-id="5efd2-123">Odwraca kolejność elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5efd2-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="5efd2-124">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="5efd2-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="5efd2-125">Przykłady składni wyrażenia kwerendy</span><span class="sxs-lookup"><span data-stu-id="5efd2-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="5efd2-126">Podstawowe przykłady sortowania</span><span class="sxs-lookup"><span data-stu-id="5efd2-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="5efd2-127">Podstawowy sortowanie wstępne</span><span class="sxs-lookup"><span data-stu-id="5efd2-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="5efd2-128">W poniższym przykładzie pokazano, jak używać `orderby` klauzuli w kwerendzie LINQ do sortowania ciągów w tablicy według długości ciągu, w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="5efd2-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="5efd2-129">Podstawowy sortowanie malejące</span><span class="sxs-lookup"><span data-stu-id="5efd2-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="5efd2-130">W następnym przykładzie pokazano, `orderby descending` jak używać klauzuli w kwerendzie LINQ do sortowania ciągów według ich pierwszej litery, w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="5efd2-130">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="5efd2-131">Przykłady sortowania pomocniczego</span><span class="sxs-lookup"><span data-stu-id="5efd2-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="5efd2-132">Pomocniczy sortowanie wstępne</span><span class="sxs-lookup"><span data-stu-id="5efd2-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="5efd2-133">W poniższym przykładzie pokazano, jak używać `orderby` klauzuli w kwerendzie LINQ do wykonywania podstawowego i pomocniczego rodzaju ciągów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="5efd2-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="5efd2-134">Ciągi są sortowane głównie według długości i drugorzędnie według pierwszej litery ciągu, zarówno w porządku rosnącym.</span><span class="sxs-lookup"><span data-stu-id="5efd2-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="5efd2-135">Pomocniczy sortowanie malejące</span><span class="sxs-lookup"><span data-stu-id="5efd2-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="5efd2-136">W następnym przykładzie pokazano, `orderby descending` jak używać klauzuli w kwerendzie LINQ do wykonywania sortowania podstawowego, w porządku rosnącym i sortowania pomocniczego w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="5efd2-136">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="5efd2-137">Ciągi są sortowane głównie według długości i drugorzędnie według pierwszej litery ciągu.</span><span class="sxs-lookup"><span data-stu-id="5efd2-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5efd2-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5efd2-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="5efd2-139">Omówienie standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="5efd2-139">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="5efd2-140">Klauzula orderby</span><span class="sxs-lookup"><span data-stu-id="5efd2-140">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="5efd2-141">Kolejność wyników klauzuli join</span><span class="sxs-lookup"><span data-stu-id="5efd2-141">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="5efd2-142">Jak sortować lub filtrować dane tekstowe według dowolnego wyrazu lub pola (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="5efd2-142">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
