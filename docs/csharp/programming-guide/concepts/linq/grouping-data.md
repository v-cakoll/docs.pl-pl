---
title: Grupowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: a85babc43f673711fe1bdfa5cec1836a5073c785
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753913"
---
# <a name="grouping-data-c"></a><span data-ttu-id="4b638-102">Grupowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="4b638-102">Grouping Data (C#)</span></span>
<span data-ttu-id="4b638-103">Grupowanie odnosi się do operacji umieszczania danych do grup, tak aby elementów w każdej grupie udostępniać wspólny atrybut.</span><span class="sxs-lookup"><span data-stu-id="4b638-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="4b638-104">Poniższa ilustracja przedstawia wyniki grupowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="4b638-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="4b638-105">Klucz dla każdej grupy jest znakiem.</span><span class="sxs-lookup"><span data-stu-id="4b638-105">The key for each group is the character.</span></span>  
  
 ![Diagram przedstawiający operacji grupowania LINQ.](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="4b638-107">Metody standardowego operatora zapytań, które grupują elementy danych są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="4b638-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b638-108">Metody</span><span class="sxs-lookup"><span data-stu-id="4b638-108">Methods</span></span>  
  
|<span data-ttu-id="4b638-109">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="4b638-109">Method Name</span></span>|<span data-ttu-id="4b638-110">Opis</span><span class="sxs-lookup"><span data-stu-id="4b638-110">Description</span></span>|<span data-ttu-id="4b638-111">Składnia wyrażeń zapytania języka C#</span><span class="sxs-lookup"><span data-stu-id="4b638-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="4b638-112">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="4b638-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="4b638-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="4b638-113">GroupBy</span></span>|<span data-ttu-id="4b638-114">Grupuje elementy, które współużytkują wspólny atrybut.</span><span class="sxs-lookup"><span data-stu-id="4b638-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="4b638-115">Każda grupa jest reprezentowany przez <xref:System.Linq.IGrouping%602> obiektu.</span><span class="sxs-lookup"><span data-stu-id="4b638-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="4b638-116">—lub—</span><span class="sxs-lookup"><span data-stu-id="4b638-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4b638-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="4b638-117">ToLookup</span></span>|<span data-ttu-id="4b638-118">Wstawia elementy do <xref:System.Linq.Lookup%602> (Słownik jeden do wielu) na podstawie selektora kluczy funkcji.</span><span class="sxs-lookup"><span data-stu-id="4b638-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="4b638-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="4b638-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="4b638-120">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="4b638-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="4b638-121">Poniższy przykład kodu wykorzystuje `group by` klauzuli grupy liczb całkowitych, na liście według tego, czy jest parzysta lub nieparzysta.</span><span class="sxs-lookup"><span data-stu-id="4b638-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4b638-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b638-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="4b638-123">Omówienie operatorów standardowej kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="4b638-123">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="4b638-124">group, klauzula</span><span class="sxs-lookup"><span data-stu-id="4b638-124">group clause</span></span>](../../../../csharp/language-reference/keywords/group-clause.md)
- [<span data-ttu-id="4b638-125">Instrukcje: Tworzenie grup zagnieżdżonych</span><span class="sxs-lookup"><span data-stu-id="4b638-125">How to: Create a Nested Group</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-create-a-nested-group.md)
- [<span data-ttu-id="4b638-126">Instrukcje: Grupowanie plików według rozszerzenia (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="4b638-126">How to: Group Files by Extension (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="4b638-127">Instrukcje: Grupowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="4b638-127">How to: Group Query Results</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-group-query-results.md)
- [<span data-ttu-id="4b638-128">Instrukcje: Wykonanie podzapytania w operacji grupowania</span><span class="sxs-lookup"><span data-stu-id="4b638-128">How to: Perform a Subquery on a Grouping Operation</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="4b638-129">Instrukcje: Dzielenie pliku na kilka plików za pomocą grup (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="4b638-129">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
