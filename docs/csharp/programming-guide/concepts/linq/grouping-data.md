---
title: Grupowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 7ef3d3c9097d7a9478605565518ac8975feb9fe2
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635746"
---
# <a name="grouping-data-c"></a><span data-ttu-id="84f9e-102">Grupowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="84f9e-102">Grouping Data (C#)</span></span>
<span data-ttu-id="84f9e-103">Grupowanie odwołuje się do operacji umieszczania danych w grupach, tak aby elementy w każdej grupie miały wspólny atrybut.</span><span class="sxs-lookup"><span data-stu-id="84f9e-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="84f9e-104">Na poniższej ilustracji przedstawiono wyniki grupowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="84f9e-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="84f9e-105">Klucz dla każdej grupy jest znakiem.</span><span class="sxs-lookup"><span data-stu-id="84f9e-105">The key for each group is the character.</span></span>  
  
 ![Diagram przedstawiający operację grupowania LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="84f9e-107">Standardowe metody operatorów zapytań, które grupują elementy danych, są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="84f9e-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="84f9e-108">Metody</span><span class="sxs-lookup"><span data-stu-id="84f9e-108">Methods</span></span>  
  
|<span data-ttu-id="84f9e-109">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="84f9e-109">Method Name</span></span>|<span data-ttu-id="84f9e-110">Opis</span><span class="sxs-lookup"><span data-stu-id="84f9e-110">Description</span></span>|<span data-ttu-id="84f9e-111">C#Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="84f9e-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="84f9e-112">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="84f9e-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="84f9e-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="84f9e-113">GroupBy</span></span>|<span data-ttu-id="84f9e-114">Grupuje elementy, które mają wspólny atrybut.</span><span class="sxs-lookup"><span data-stu-id="84f9e-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="84f9e-115">Każda grupa jest reprezentowana przez obiekt <xref:System.Linq.IGrouping%602>.</span><span class="sxs-lookup"><span data-stu-id="84f9e-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="84f9e-116">lub</span><span class="sxs-lookup"><span data-stu-id="84f9e-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="84f9e-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="84f9e-117">ToLookup</span></span>|<span data-ttu-id="84f9e-118">Wstawia elementy do <xref:System.Linq.Lookup%602> (słownik "jeden do wielu") na podstawie funkcji selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="84f9e-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="84f9e-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="84f9e-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="84f9e-120">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="84f9e-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="84f9e-121">Poniższy przykład kodu używa klauzuli `group by` do grupowania liczb całkowitych na liście zgodnie z tym, czy są one parzyste czy nieparzyste.</span><span class="sxs-lookup"><span data-stu-id="84f9e-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="84f9e-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84f9e-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="84f9e-123">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="84f9e-123">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="84f9e-124">group, klauzula</span><span class="sxs-lookup"><span data-stu-id="84f9e-124">group clause</span></span>](../../../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="84f9e-125">Tworzenie grupy zagnieżdżonej</span><span class="sxs-lookup"><span data-stu-id="84f9e-125">Create a nested group</span></span>](../../../linq/create-a-nested-group.md)
- [<span data-ttu-id="84f9e-126">Jak grupować pliki według rozszerzenia (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="84f9e-126">How to group files by extension (LINQ) (C#)</span></span>](./how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="84f9e-127">Grupowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="84f9e-127">Group query results</span></span>](../../../linq/group-query-results.md)
- [<span data-ttu-id="84f9e-128">Wykonanie podzapytania w operacji grupowania</span><span class="sxs-lookup"><span data-stu-id="84f9e-128">Perform a subquery on a grouping operation</span></span>](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="84f9e-129">Jak podzielić plik na wiele plików przy użyciu grup (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="84f9e-129">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
