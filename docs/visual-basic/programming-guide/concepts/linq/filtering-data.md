---
title: Filtrowanie danych
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: f7a1aa76dc93cc03952e55f5f8fc3f75176a3f9f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383420"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="dd6f1-102">Filtrowanie danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd6f1-102">Filtering Data (Visual Basic)</span></span>

<span data-ttu-id="dd6f1-103">Filtrowanie odwołuje się do operacji ograniczającej zestaw wyników tak, aby zawierała tylko te elementy, które spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="dd6f1-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="dd6f1-104">Jest on również znany jako wybór.</span><span class="sxs-lookup"><span data-stu-id="dd6f1-104">It is also known as selection.</span></span>

<span data-ttu-id="dd6f1-105">Na poniższej ilustracji przedstawiono wyniki filtrowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="dd6f1-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="dd6f1-106">Predykat dla operacji filtrowania określa, że znak musi mieć wartość "A".</span><span class="sxs-lookup"><span data-stu-id="dd6f1-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>

![Diagram przedstawiający operację filtrowania LINQ](./media/filtering-data/linq-filter-operation.png)

<span data-ttu-id="dd6f1-108">W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują zaznaczenie.</span><span class="sxs-lookup"><span data-stu-id="dd6f1-108">The standard query operator methods that perform selection are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="dd6f1-109">Metody</span><span class="sxs-lookup"><span data-stu-id="dd6f1-109">Methods</span></span>

|<span data-ttu-id="dd6f1-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="dd6f1-110">Method Name</span></span>|<span data-ttu-id="dd6f1-111">Opis</span><span class="sxs-lookup"><span data-stu-id="dd6f1-111">Description</span></span>|<span data-ttu-id="dd6f1-112">Składnia wyrażenia zapytania Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dd6f1-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="dd6f1-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="dd6f1-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="dd6f1-114">OfType</span><span class="sxs-lookup"><span data-stu-id="dd6f1-114">OfType</span></span>|<span data-ttu-id="dd6f1-115">Wybiera wartości, w zależności od możliwości przerzutowania do określonego typu.</span><span class="sxs-lookup"><span data-stu-id="dd6f1-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="dd6f1-116">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="dd6f1-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="dd6f1-117">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="dd6f1-117">Where</span></span>|<span data-ttu-id="dd6f1-118">Wybiera wartości, które są oparte na funkcji predykatu.</span><span class="sxs-lookup"><span data-stu-id="dd6f1-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="dd6f1-119">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="dd6f1-119">Query Expression Syntax Example</span></span>

<span data-ttu-id="dd6f1-120">W poniższym przykładzie zastosowano `Where` do filtrowania z tablicy te ciągi mające określoną długość.</span><span class="sxs-lookup"><span data-stu-id="dd6f1-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>

```vb
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}

Dim query = From word In words
            Where word.Length = 3
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
```

## <a name="see-also"></a><span data-ttu-id="dd6f1-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd6f1-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="dd6f1-122">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd6f1-122">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="dd6f1-123">Klauzula WHERE</span><span class="sxs-lookup"><span data-stu-id="dd6f1-123">Where Clause</span></span>](../../../language-reference/queries/where-clause.md)
- [<span data-ttu-id="dd6f1-124">Instrukcje: filtrowanie wyników zapytania</span><span class="sxs-lookup"><span data-stu-id="dd6f1-124">How to: Filter Query Results</span></span>](../../language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [<span data-ttu-id="dd6f1-125">Instrukcje: wykonywanie zapytania dotyczącego metadanych zestawu przy użyciu odbicia (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd6f1-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="dd6f1-126">Instrukcje: zapytanie o pliki o określonym atrybucie lub nazwie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd6f1-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="dd6f1-127">Instrukcje: sortowanie lub filtrowanie danych tekstowych według dowolnego wyrazu lub pola (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd6f1-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
