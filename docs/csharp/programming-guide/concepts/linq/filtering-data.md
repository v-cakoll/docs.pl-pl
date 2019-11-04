---
title: Filtrowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: eb448c1c2ea6d9b3fcf0120043cafebc01cd3805
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418474"
---
# <a name="filtering-data-c"></a><span data-ttu-id="fc478-102">Filtrowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="fc478-102">Filtering Data (C#)</span></span>
<span data-ttu-id="fc478-103">Filtrowanie odwołuje się do operacji ograniczającej zestaw wyników tak, aby zawierała tylko te elementy, które spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="fc478-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="fc478-104">Jest on również znany jako wybór.</span><span class="sxs-lookup"><span data-stu-id="fc478-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="fc478-105">Na poniższej ilustracji przedstawiono wyniki filtrowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="fc478-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="fc478-106">Predykat dla operacji filtrowania określa, że znak musi mieć wartość "A".</span><span class="sxs-lookup"><span data-stu-id="fc478-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Diagram przedstawiający operację filtrowania LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="fc478-108">W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="fc478-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc478-109">Metody</span><span class="sxs-lookup"><span data-stu-id="fc478-109">Methods</span></span>  
  
|<span data-ttu-id="fc478-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="fc478-110">Method Name</span></span>|<span data-ttu-id="fc478-111">Opis</span><span class="sxs-lookup"><span data-stu-id="fc478-111">Description</span></span>|<span data-ttu-id="fc478-112">C#Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="fc478-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="fc478-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="fc478-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="fc478-114">OfType</span><span class="sxs-lookup"><span data-stu-id="fc478-114">OfType</span></span>|<span data-ttu-id="fc478-115">Wybiera wartości, w zależności od możliwości przerzutowania do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="fc478-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="fc478-116">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="fc478-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fc478-117">Gdzie</span><span class="sxs-lookup"><span data-stu-id="fc478-117">Where</span></span>|<span data-ttu-id="fc478-118">Wybiera wartości, które są oparte na funkcji predykatu.</span><span class="sxs-lookup"><span data-stu-id="fc478-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="fc478-119">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="fc478-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="fc478-120">W poniższym przykładzie zastosowano klauzulę `where` do filtrowania z tablicy te ciągi mające określoną długość.</span><span class="sxs-lookup"><span data-stu-id="fc478-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fc478-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc478-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="fc478-122">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="fc478-122">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="fc478-123">where, klauzula</span><span class="sxs-lookup"><span data-stu-id="fc478-123">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="fc478-124">Instrukcje: dynamiczne określanie filtrów predykatu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="fc478-124">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="fc478-125">Instrukcje: zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="fc478-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="fc478-126">Instrukcje: zapytanie o pliki o określonym atrybucie lub nazwie (C#)</span><span class="sxs-lookup"><span data-stu-id="fc478-126">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="fc478-127">Instrukcje: sortowanie lub filtrowanie danych tekstowych według dowolnego wyrazu lub pola (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="fc478-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
