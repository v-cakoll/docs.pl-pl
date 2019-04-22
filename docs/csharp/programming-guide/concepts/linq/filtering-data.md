---
title: Filtrowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: fbaece0d-0f23-47f7-89c5-f3ea8db692b6
ms.openlocfilehash: 61d80674fd858063e77749342a33d714e3a57c6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826070"
---
# <a name="filtering-data-c"></a><span data-ttu-id="aa0df-102">Filtrowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="aa0df-102">Filtering Data (C#)</span></span>
<span data-ttu-id="aa0df-103">Filtrowanie odnosi się do operacji ograniczyć zestaw wyników, aby zawiera tylko te elementy, które spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="aa0df-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="aa0df-104">Jest również nazywany zaznaczenia.</span><span class="sxs-lookup"><span data-stu-id="aa0df-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="aa0df-105">Poniższa ilustracja przedstawia wyniki filtrowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="aa0df-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="aa0df-106">Predykat dla filtrowania operacji określa, że znak musi być "A".</span><span class="sxs-lookup"><span data-stu-id="aa0df-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 ![Diagram przedstawiający filtrowanie operację LINQ](./media/filtering-data/linq-filter-operation.png)  
  
 <span data-ttu-id="aa0df-108">Metody standardowego operatora zapytań, które wykonują wyboru są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="aa0df-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aa0df-109">Metody</span><span class="sxs-lookup"><span data-stu-id="aa0df-109">Methods</span></span>  
  
|<span data-ttu-id="aa0df-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="aa0df-110">Method Name</span></span>|<span data-ttu-id="aa0df-111">Opis</span><span class="sxs-lookup"><span data-stu-id="aa0df-111">Description</span></span>|<span data-ttu-id="aa0df-112">Składnia wyrażeń zapytania języka C#</span><span class="sxs-lookup"><span data-stu-id="aa0df-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="aa0df-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="aa0df-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="aa0df-114">OfType</span><span class="sxs-lookup"><span data-stu-id="aa0df-114">OfType</span></span>|<span data-ttu-id="aa0df-115">Wybiera wartości, w zależności od ich możliwości, można rzutować do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="aa0df-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="aa0df-116">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="aa0df-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="aa0df-117">Gdzie</span><span class="sxs-lookup"><span data-stu-id="aa0df-117">Where</span></span>|<span data-ttu-id="aa0df-118">Wybiera wartości, które są oparte na funkcji predykatu.</span><span class="sxs-lookup"><span data-stu-id="aa0df-118">Selects values that are based on a predicate function.</span></span>|`where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="aa0df-119">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="aa0df-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="aa0df-120">W poniższym przykładzie użyto `where` klauzulę filtrującą dane z tablicy tych ciągów, które mają określonej długości.</span><span class="sxs-lookup"><span data-stu-id="aa0df-120">The following example uses the `where` clause to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="aa0df-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa0df-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="aa0df-122">Omówienie operatorów standardowej kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="aa0df-122">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="aa0df-123">where, klauzula</span><span class="sxs-lookup"><span data-stu-id="aa0df-123">where clause</span></span>](../../../../csharp/language-reference/keywords/where-clause.md)
- [<span data-ttu-id="aa0df-124">Instrukcje: Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="aa0df-124">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="aa0df-125">Instrukcje: Zapytanie dotyczące metadanych zestawu z odbiciem (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="aa0df-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="aa0df-126">Instrukcje: Zapytanie o pliki o określonym atrybucie lub nazwie (C#)</span><span class="sxs-lookup"><span data-stu-id="aa0df-126">How to: Query for Files with a Specified Attribute or Name (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="aa0df-127">Instrukcje: Sortowanie lub filtrowanie danych tekstowych według dowolnego słowa lub pola (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="aa0df-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
