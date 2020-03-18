---
title: Grupowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: 7ef3d3c9097d7a9478605565518ac8975feb9fe2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635746"
---
# <a name="grouping-data-c"></a><span data-ttu-id="0df15-102">Grupowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="0df15-102">Grouping Data (C#)</span></span>
<span data-ttu-id="0df15-103">Grupowanie odnosi się do działania umieszczania danych w grupach, tak aby elementy w każdej grupie współużytkują wspólny atrybut.</span><span class="sxs-lookup"><span data-stu-id="0df15-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="0df15-104">Na poniższej ilustracji przedstawiono wyniki grupowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="0df15-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="0df15-105">Kluczem dla każdej grupy jest znak.</span><span class="sxs-lookup"><span data-stu-id="0df15-105">The key for each group is the character.</span></span>  
  
 ![Diagram, który pokazuje operację linq grupowanie.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="0df15-107">Standardowe metody operatora kwerendy, które grupują elementy danych są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="0df15-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0df15-108">Metody</span><span class="sxs-lookup"><span data-stu-id="0df15-108">Methods</span></span>  
  
|<span data-ttu-id="0df15-109">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="0df15-109">Method Name</span></span>|<span data-ttu-id="0df15-110">Opis</span><span class="sxs-lookup"><span data-stu-id="0df15-110">Description</span></span>|<span data-ttu-id="0df15-111">Składnia wyrażenia kwerendy c#</span><span class="sxs-lookup"><span data-stu-id="0df15-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="0df15-112">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="0df15-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="0df15-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="0df15-113">GroupBy</span></span>|<span data-ttu-id="0df15-114">Grupje elementy, które mają wspólny atrybut.</span><span class="sxs-lookup"><span data-stu-id="0df15-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="0df15-115">Każda grupa jest reprezentowana przez obiekt. <xref:System.Linq.IGrouping%602></span><span class="sxs-lookup"><span data-stu-id="0df15-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="0df15-116">— lub —</span><span class="sxs-lookup"><span data-stu-id="0df15-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="0df15-117">Tolookup</span><span class="sxs-lookup"><span data-stu-id="0df15-117">ToLookup</span></span>|<span data-ttu-id="0df15-118">Wstawia elementy <xref:System.Linq.Lookup%602> do (słownik jeden-do-wielu) na podstawie funkcji selektora kluczy.</span><span class="sxs-lookup"><span data-stu-id="0df15-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="0df15-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="0df15-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="0df15-120">Przykład składni wyrażenia kwerendy</span><span class="sxs-lookup"><span data-stu-id="0df15-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="0df15-121">Poniższy przykład kodu `group by` używa klauzuli do grupowania liczb całkowitych na liście w zależności od tego, czy są one parzyste, czy nieparzyste.</span><span class="sxs-lookup"><span data-stu-id="0df15-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0df15-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0df15-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="0df15-123">Omówienie standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="0df15-123">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="0df15-124">group, klauzula</span><span class="sxs-lookup"><span data-stu-id="0df15-124">group clause</span></span>](../../../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="0df15-125">Tworzenie grupy zagnieżdżonej</span><span class="sxs-lookup"><span data-stu-id="0df15-125">Create a nested group</span></span>](../../../linq/create-a-nested-group.md)
- [<span data-ttu-id="0df15-126">Jak grupować pliki według rozszerzenia (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="0df15-126">How to group files by extension (LINQ) (C#)</span></span>](./how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="0df15-127">Grupowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="0df15-127">Group query results</span></span>](../../../linq/group-query-results.md)
- [<span data-ttu-id="0df15-128">Wykonywanie podzapytania w operacji grupowania</span><span class="sxs-lookup"><span data-stu-id="0df15-128">Perform a subquery on a grouping operation</span></span>](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="0df15-129">Jak podzielić plik na wiele plików przy użyciu grup (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="0df15-129">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
