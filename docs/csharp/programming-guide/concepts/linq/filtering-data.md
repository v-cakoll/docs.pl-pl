---
title: Filtrowanie danych (C#)
description: Filtrowanie, znane także jako zaznaczenie, ogranicza wyniki na podstawie warunku. Dowiedz się więcej na temat standardowych metod operatorów zapytań w LINQ w języku C#, które wykonują filtrowanie.
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: f9f6d691da73b566e5135f6692c87ba3a8978005
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103923"
---
# <a name="filtering-data-c"></a><span data-ttu-id="53fbb-104">Filtrowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="53fbb-104">Filtering Data (C#)</span></span>
<span data-ttu-id="53fbb-105">Filtrowanie odwołuje się do operacji ograniczającej zestaw wyników tak, aby zawierała tylko te elementy, które spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="53fbb-105">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="53fbb-106">Jest on również znany jako wybór.</span><span class="sxs-lookup"><span data-stu-id="53fbb-106">It is also known as selection.</span></span>  
  
 <span data-ttu-id="53fbb-107">Na poniższej ilustracji przedstawiono wyniki filtrowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="53fbb-107">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="53fbb-108">Predykat dla operacji filtrowania określa, że znak musi mieć wartość "A".</span><span class="sxs-lookup"><span data-stu-id="53fbb-108">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Diagram przedstawiający operację filtrowania LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="53fbb-110">W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="53fbb-110">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="53fbb-111">Metody</span><span class="sxs-lookup"><span data-stu-id="53fbb-111">Methods</span></span>  
  
|<span data-ttu-id="53fbb-112">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="53fbb-112">Method Name</span></span>|<span data-ttu-id="53fbb-113">Opis</span><span class="sxs-lookup"><span data-stu-id="53fbb-113">Description</span></span>|<span data-ttu-id="53fbb-114">Składnia wyrażenia zapytania C#</span><span class="sxs-lookup"><span data-stu-id="53fbb-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="53fbb-115">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="53fbb-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="53fbb-116">OfType</span><span class="sxs-lookup"><span data-stu-id="53fbb-116">OfType</span></span>|<span data-ttu-id="53fbb-117">Wybiera wartości, w zależności od możliwości przerzutowania do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="53fbb-117">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="53fbb-118">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="53fbb-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="53fbb-119">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="53fbb-119">Where</span></span>|<span data-ttu-id="53fbb-120">Wybiera wartości, które są oparte na funkcji predykatu.</span><span class="sxs-lookup"><span data-stu-id="53fbb-120">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="53fbb-121">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="53fbb-121">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="53fbb-122">W poniższym przykładzie zastosowano `where` klauzulę do filtrowania z tablicy te ciągi mające określoną długość.</span><span class="sxs-lookup"><span data-stu-id="53fbb-122">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53fbb-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53fbb-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="53fbb-124">Standardowe operatory zapytań — Omówienie (C#)</span><span class="sxs-lookup"><span data-stu-id="53fbb-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="53fbb-125">Klauzula where</span><span class="sxs-lookup"><span data-stu-id="53fbb-125">where clause</span></span>](../../../language-reference/keywords/where-clause.md)
- [<span data-ttu-id="53fbb-126">Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="53fbb-126">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="53fbb-127">Jak wykonać zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="53fbb-127">How to query an assembly's metadata with Reflection (LINQ) (C#)</span></span>](./how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="53fbb-128">Jak wykonać zapytanie o pliki o określonym atrybucie lub nazwie (C#)</span><span class="sxs-lookup"><span data-stu-id="53fbb-128">How to query for files with a specified attribute or name (C#)</span></span>](./how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="53fbb-129">Sortowanie lub filtrowanie danych tekstowych według dowolnego wyrazu lub pola (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="53fbb-129">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
