---
title: Filtrowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 74399244990f8ff2deaa1d10576ea94a57c16bee
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346993"
---
# <a name="filtering-data-c"></a><span data-ttu-id="b88bf-102">Filtrowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="b88bf-102">Filtering Data (C#)</span></span>
<span data-ttu-id="b88bf-103">Filtrowanie odwołuje się do operacji ograniczającej zestaw wyników tak, aby zawierała tylko te elementy, które spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="b88bf-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="b88bf-104">Jest on również znany jako wybór.</span><span class="sxs-lookup"><span data-stu-id="b88bf-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="b88bf-105">Na poniższej ilustracji przedstawiono wyniki filtrowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="b88bf-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="b88bf-106">Predykat dla operacji filtrowania określa, że znak musi mieć wartość "A".</span><span class="sxs-lookup"><span data-stu-id="b88bf-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Diagram przedstawiający operację filtrowania LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="b88bf-108">W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="b88bf-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b88bf-109">Metody</span><span class="sxs-lookup"><span data-stu-id="b88bf-109">Methods</span></span>  
  
|<span data-ttu-id="b88bf-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="b88bf-110">Method Name</span></span>|<span data-ttu-id="b88bf-111">Opis</span><span class="sxs-lookup"><span data-stu-id="b88bf-111">Description</span></span>|<span data-ttu-id="b88bf-112">C#Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="b88bf-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="b88bf-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="b88bf-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="b88bf-114">OfType</span><span class="sxs-lookup"><span data-stu-id="b88bf-114">OfType</span></span>|<span data-ttu-id="b88bf-115">Wybiera wartości, w zależności od możliwości przerzutowania do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="b88bf-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="b88bf-116">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="b88bf-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b88bf-117">Gdzie</span><span class="sxs-lookup"><span data-stu-id="b88bf-117">Where</span></span>|<span data-ttu-id="b88bf-118">Wybiera wartości, które są oparte na funkcji predykatu.</span><span class="sxs-lookup"><span data-stu-id="b88bf-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="b88bf-119">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="b88bf-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="b88bf-120">W poniższym przykładzie zastosowano klauzulę `where` do filtrowania z tablicy te ciągi mające określoną długość.</span><span class="sxs-lookup"><span data-stu-id="b88bf-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b88bf-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b88bf-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="b88bf-122">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="b88bf-122">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="b88bf-123">where, klauzula</span><span class="sxs-lookup"><span data-stu-id="b88bf-123">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="b88bf-124">Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="b88bf-124">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="b88bf-125">Jak wykonać zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b88bf-125">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="b88bf-126">Jak wykonać zapytanie o pliki o określonym atrybucie lub nazwie (C#)</span><span class="sxs-lookup"><span data-stu-id="b88bf-126">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="b88bf-127">Sortowanie lub filtrowanie danych tekstowych według dowolnego wyrazu lub pola (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b88bf-127">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
