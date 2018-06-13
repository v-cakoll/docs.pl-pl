---
title: Filtrowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: ad8c167cf1b084c5e05bec84cd5c2f3f05716d03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321496"
---
# <a name="filtering-data-c"></a><span data-ttu-id="791bb-102">Filtrowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="791bb-102">Filtering Data (C#)</span></span>
<span data-ttu-id="791bb-103">Filtrowanie odnosi się do operacji ograniczyć zestaw wyników do zawierać tylko elementy, które spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="791bb-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="791bb-104">Jest nazywana zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="791bb-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="791bb-105">Na poniższej ilustracji przedstawiono wyniki filtrowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="791bb-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="791bb-106">Predykat dla filtrowania operacji określa, czy znak musi być "A".</span><span class="sxs-lookup"><span data-stu-id="791bb-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="791bb-107">![LINQ filtrowania operacji](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="791bb-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="791bb-108">Metody — operator zapytań standardowe, wykonujących wyboru są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="791bb-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="791bb-109">Metody</span><span class="sxs-lookup"><span data-stu-id="791bb-109">Methods</span></span>  
  
|<span data-ttu-id="791bb-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="791bb-110">Method Name</span></span>|<span data-ttu-id="791bb-111">Opis</span><span class="sxs-lookup"><span data-stu-id="791bb-111">Description</span></span>|<span data-ttu-id="791bb-112">Składnia wyrażenia zapytania C#</span><span class="sxs-lookup"><span data-stu-id="791bb-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="791bb-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="791bb-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="791bb-114">OfType</span><span class="sxs-lookup"><span data-stu-id="791bb-114">OfType</span></span>|<span data-ttu-id="791bb-115">Wybiera wartości, w zależności od ich możliwości można rzutować na określony typ.</span><span class="sxs-lookup"><span data-stu-id="791bb-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="791bb-116">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="791bb-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="791bb-117">Gdzie</span><span class="sxs-lookup"><span data-stu-id="791bb-117">Where</span></span>|<span data-ttu-id="791bb-118">Wybiera wartości, które są oparte na funkcji predykatu.</span><span class="sxs-lookup"><span data-stu-id="791bb-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="791bb-119">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="791bb-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="791bb-120">W poniższym przykładzie użyto `where` klauzulę filtru z tablicy te ciągi, które mają określoną długość.</span><span class="sxs-lookup"><span data-stu-id="791bb-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            where word.Length == 3  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="791bb-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="791bb-121">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="791bb-122">Operatory standardowe zapytań — omówienie (C#)</span><span class="sxs-lookup"><span data-stu-id="791bb-122">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="791bb-123">where, klauzula</span><span class="sxs-lookup"><span data-stu-id="791bb-123">where clause</span></span>](../../../../csharp/language-reference/keywords/where-clause.md)  
 [<span data-ttu-id="791bb-124">Porady: dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="791bb-124">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)  
 [<span data-ttu-id="791bb-125">Porady: zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="791bb-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 [<span data-ttu-id="791bb-126">Porady: zapytanie o pliki o określonym atrybucie lub nazwie (C#)</span><span class="sxs-lookup"><span data-stu-id="791bb-126">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 [<span data-ttu-id="791bb-127">Porady: sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="791bb-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
