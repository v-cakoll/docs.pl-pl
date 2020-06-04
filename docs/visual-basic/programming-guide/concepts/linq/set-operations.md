---
title: Operacje na zestawie
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: b6ff14794343ae7623ee38894cef02cfc0a2a597
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406823"
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="34926-102">Operacje Set (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34926-102">Set Operations (Visual Basic)</span></span>

<span data-ttu-id="34926-103">Operacje Set w LINQ odnoszą się do operacji zapytania, które tworzą zestaw wyników, który jest oparty na obecności lub braku równoważnych elementów w obrębie tych samych lub oddzielnych kolekcji (lub zestawów).</span><span class="sxs-lookup"><span data-stu-id="34926-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>

<span data-ttu-id="34926-104">W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują operacje na zestawach.</span><span class="sxs-lookup"><span data-stu-id="34926-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="34926-105">Metody</span><span class="sxs-lookup"><span data-stu-id="34926-105">Methods</span></span>

|<span data-ttu-id="34926-106">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="34926-106">Method Name</span></span>|<span data-ttu-id="34926-107">Opis</span><span class="sxs-lookup"><span data-stu-id="34926-107">Description</span></span>|<span data-ttu-id="34926-108">Składnia wyrażenia zapytania Visual Basic</span><span class="sxs-lookup"><span data-stu-id="34926-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="34926-109">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="34926-109">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="34926-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="34926-110">Distinct</span></span>|<span data-ttu-id="34926-111">Usuwa zduplikowane wartości z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="34926-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|
|<span data-ttu-id="34926-112">Z wyjątkiem</span><span class="sxs-lookup"><span data-stu-id="34926-112">Except</span></span>|<span data-ttu-id="34926-113">Zwraca różnicę zestawu, co oznacza elementy jednej kolekcji, które nie znajdują się w drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="34926-113">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="34926-114">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="34926-114">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|
|<span data-ttu-id="34926-115">Wspólnej</span><span class="sxs-lookup"><span data-stu-id="34926-115">Intersect</span></span>|<span data-ttu-id="34926-116">Zwraca część wspólną, która oznacza elementy, które pojawiają się w każdej z dwóch kolekcji.</span><span class="sxs-lookup"><span data-stu-id="34926-116">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="34926-117">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="34926-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|
|<span data-ttu-id="34926-118">Unia</span><span class="sxs-lookup"><span data-stu-id="34926-118">Union</span></span>|<span data-ttu-id="34926-119">Zwraca zestaw zbiorów, co oznacza unikatowe elementy, które pojawiają się w jednej z dwóch kolekcji.</span><span class="sxs-lookup"><span data-stu-id="34926-119">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="34926-120">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="34926-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|

## <a name="comparison-of-set-operations"></a><span data-ttu-id="34926-121">Porównanie operacji ustawiania</span><span class="sxs-lookup"><span data-stu-id="34926-121">Comparison of Set Operations</span></span>

### <a name="distinct"></a><span data-ttu-id="34926-122">Distinct</span><span class="sxs-lookup"><span data-stu-id="34926-122">Distinct</span></span>

<span data-ttu-id="34926-123">Poniższa ilustracja przedstawia zachowanie <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody dla sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="34926-123">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="34926-124">Zwracana sekwencja zawiera unikatowe elementy z sekwencji wejściowej.</span><span class="sxs-lookup"><span data-stu-id="34926-124">The returned sequence contains the unique elements from the input sequence.</span></span>

![Ilustracja przedstawiająca zachowanie odrębnych&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)

### <a name="except"></a><span data-ttu-id="34926-126">Z wyjątkiem</span><span class="sxs-lookup"><span data-stu-id="34926-126">Except</span></span>

<span data-ttu-id="34926-127">Na poniższej ilustracji przedstawiono zachowanie <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="34926-127">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="34926-128">Zwracana sekwencja zawiera tylko elementy z pierwszej sekwencji wejściowej, które nie znajdują się w drugiej sekwencji wejściowej.</span><span class="sxs-lookup"><span data-stu-id="34926-128">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>

<span data-ttu-id="34926-129">![Ilustracja przedstawiająca akcję z wyjątkiem&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Pokazuje zachowanie z wyjątkiem.")</span><span class="sxs-lookup"><span data-stu-id="34926-129">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>

### <a name="intersect"></a><span data-ttu-id="34926-130">Wspólnej</span><span class="sxs-lookup"><span data-stu-id="34926-130">Intersect</span></span>

<span data-ttu-id="34926-131">Na poniższej ilustracji przedstawiono zachowanie <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="34926-131">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="34926-132">Zwracana sekwencja zawiera elementy, które są wspólne dla obu sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="34926-132">The returned sequence contains the elements that are common to both of the input sequences.</span></span>

![Ilustracja przedstawiająca przecięcie dwóch sekwencji.](./media/set-operations/intersection-two-sequences.png)

### <a name="union"></a><span data-ttu-id="34926-134">Unia</span><span class="sxs-lookup"><span data-stu-id="34926-134">Union</span></span>

<span data-ttu-id="34926-135">Poniższa ilustracja przedstawia operację Union dla dwóch sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="34926-135">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="34926-136">Zwracana sekwencja zawiera unikatowe elementy z obu sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="34926-136">The returned sequence contains the unique elements from both input sequences.</span></span>

![Ilustracja przedstawiająca Unię dwóch sekwencji.](./media/set-operations/union-operation-two-sequences.png)

## <a name="query-expression-syntax-example"></a><span data-ttu-id="34926-138">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="34926-138">Query Expression Syntax Example</span></span>

<span data-ttu-id="34926-139">W poniższym przykładzie zastosowano `Distinct` klauzulę w zapytaniu LINQ do zwrócenia unikatowych liczb z listy liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="34926-139">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>

[!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]

## <a name="see-also"></a><span data-ttu-id="34926-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34926-140">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="34926-141">Standardowe operatory zapytań — Omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34926-141">Standard Query Operators Overview (Visual Basic)</span></span>](standard-query-operators-overview.md)
- [<span data-ttu-id="34926-142">Distinct, klauzula</span><span class="sxs-lookup"><span data-stu-id="34926-142">Distinct Clause</span></span>](../../../language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="34926-143">Instrukcje: łączenie i porównywanie kolekcji ciągów (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34926-143">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="34926-144">Instrukcje: Wyszukiwanie zestawu różnic między dwoma listami (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34926-144">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](how-to-find-the-set-difference-between-two-lists-linq.md)
