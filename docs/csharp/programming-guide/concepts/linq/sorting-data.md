---
title: Sortowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 90ff7d52e6832935fe16e081e904acae3a24669a
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245439"
---
# <a name="sorting-data-c"></a><span data-ttu-id="ea690-102">Sortowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="ea690-102">Sorting Data (C#)</span></span>
<span data-ttu-id="ea690-103">Operacja sortowania Porządkuje elementy które sekwencji, w oparciu o jeden lub więcej atrybutów.</span><span class="sxs-lookup"><span data-stu-id="ea690-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="ea690-104">Kryterium sortowania sortuje podstawowe elementy.</span><span class="sxs-lookup"><span data-stu-id="ea690-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="ea690-105">Określając drugie kryterium sortowania, możesz sortować elementów w każdej grupie podstawowej sortowania.</span><span class="sxs-lookup"><span data-stu-id="ea690-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="ea690-106">Poniższa ilustracja przedstawia wyniki operacji sortowania alfabetycznego na sekwencję znaków.</span><span class="sxs-lookup"><span data-stu-id="ea690-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters.</span></span>  
  
 <span data-ttu-id="ea690-107">![Sortowanie operację LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span><span class="sxs-lookup"><span data-stu-id="ea690-107">![LINQ Sorting Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_ordering.png "LINQ_Ordering")</span></span>  
  
 <span data-ttu-id="ea690-108">Metody standardowego operatora zapytań, sortować dane, które są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="ea690-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea690-109">Metody</span><span class="sxs-lookup"><span data-stu-id="ea690-109">Methods</span></span>  
  
|<span data-ttu-id="ea690-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="ea690-110">Method Name</span></span>|<span data-ttu-id="ea690-111">Opis</span><span class="sxs-lookup"><span data-stu-id="ea690-111">Description</span></span>|<span data-ttu-id="ea690-112">Składnia wyrażeń zapytania języka C#</span><span class="sxs-lookup"><span data-stu-id="ea690-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="ea690-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="ea690-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="ea690-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="ea690-114">OrderBy</span></span>|<span data-ttu-id="ea690-115">Sortuje wartości w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="ea690-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ea690-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="ea690-116">OrderByDescending</span></span>|<span data-ttu-id="ea690-117">Sortuje wartości w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="ea690-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ea690-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="ea690-118">ThenBy</span></span>|<span data-ttu-id="ea690-119">Wykonuje dodatkowej sortowanie w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="ea690-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ea690-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="ea690-120">ThenByDescending</span></span>|<span data-ttu-id="ea690-121">Wykonuje dodatkowej sortowanie w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="ea690-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="ea690-122">zwrotny</span><span class="sxs-lookup"><span data-stu-id="ea690-122">Reverse</span></span>|<span data-ttu-id="ea690-123">Odwraca kolejność elementów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ea690-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="ea690-124">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="ea690-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="ea690-125">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="ea690-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="ea690-126">Przykłady podstawowej sortowania</span><span class="sxs-lookup"><span data-stu-id="ea690-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="ea690-127">Sortowanie w kolejności rosnącej podstawowego</span><span class="sxs-lookup"><span data-stu-id="ea690-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="ea690-128">Poniższy przykład pokazuje sposób użycia `orderby` klauzuli w zapytaniu LINQ, aby posortować ciągi w tablicy przez długość ciągu, w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="ea690-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="ea690-129">Podstawowy Sortuj malejąco</span><span class="sxs-lookup"><span data-stu-id="ea690-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="ea690-130">Następny przykład pokazuje sposób użycia `orderby descending` klauzuli w zapytaniu LINQ, aby posortować ciągi według ich pierwsza litera w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="ea690-130">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="ea690-131">Sortowanie dodatkowe przykłady</span><span class="sxs-lookup"><span data-stu-id="ea690-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="ea690-132">Sortowanie w kolejności rosnącej dodatkowej</span><span class="sxs-lookup"><span data-stu-id="ea690-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="ea690-133">Poniższy przykład pokazuje sposób użycia `orderby` klauzuli w zapytaniu programu LINQ do wykonywania podstawowych i pomocniczych sortowania ciągów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="ea690-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="ea690-134">Ciągi są sortowane, przede wszystkim przez długość i przetworzonych przez pierwszą literę ciągu, zarówno w kolejności rosnącej.</span><span class="sxs-lookup"><span data-stu-id="ea690-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="ea690-135">Pomocniczy Sortuj malejąco</span><span class="sxs-lookup"><span data-stu-id="ea690-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="ea690-136">Następny przykład pokazuje sposób użycia `orderby descending` klauzuli w zapytaniu LINQ, aby wykonać podstawowy sortowania, w kolejności rosnącej kolejności i dodatkowej sortowania, w kolejności malejącej.</span><span class="sxs-lookup"><span data-stu-id="ea690-136">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="ea690-137">Ciągi są sortowane, przede wszystkim przez długość i przetworzonych przez pierwszą literę ciągu.</span><span class="sxs-lookup"><span data-stu-id="ea690-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ea690-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ea690-138">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="ea690-139">Omówienie operatorów standardowej kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="ea690-139">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="ea690-140">orderby, klauzula</span><span class="sxs-lookup"><span data-stu-id="ea690-140">orderby clause</span></span>](../../../../csharp/language-reference/keywords/orderby-clause.md)  
 [<span data-ttu-id="ea690-141">Porady: kolejność wyników klauzuli Join</span><span class="sxs-lookup"><span data-stu-id="ea690-141">How to: Order the Results of a Join Clause</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-order-the-results-of-a-join-clause.md)  
 [<span data-ttu-id="ea690-142">Porady: sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="ea690-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
