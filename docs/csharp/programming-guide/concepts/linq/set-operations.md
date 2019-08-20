---
title: Operacje Set (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: cea0c0ba4dd6c7f874f69e3ec4a179248397b67d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591120"
---
# <a name="set-operations-c"></a><span data-ttu-id="5cb08-102">Operacje Set (C#)</span><span class="sxs-lookup"><span data-stu-id="5cb08-102">Set Operations (C#)</span></span>
<span data-ttu-id="5cb08-103">Operacje Set w LINQ odnoszą się do operacji zapytania, które tworzą zestaw wyników, który jest oparty na obecności lub braku równoważnych elementów w obrębie tych samych lub oddzielnych kolekcji (lub zestawów).</span><span class="sxs-lookup"><span data-stu-id="5cb08-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="5cb08-104">W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują operacje na zestawach.</span><span class="sxs-lookup"><span data-stu-id="5cb08-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5cb08-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5cb08-105">Methods</span></span>  
  
|<span data-ttu-id="5cb08-106">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="5cb08-106">Method Name</span></span>|<span data-ttu-id="5cb08-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5cb08-107">Description</span></span>|<span data-ttu-id="5cb08-108">C#Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="5cb08-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="5cb08-109">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="5cb08-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="5cb08-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="5cb08-110">Distinct</span></span>|<span data-ttu-id="5cb08-111">Usuwa zduplikowane wartości z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5cb08-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="5cb08-112">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="5cb08-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5cb08-113">Ale</span><span class="sxs-lookup"><span data-stu-id="5cb08-113">Except</span></span>|<span data-ttu-id="5cb08-114">Zwraca różnicę zestawu, co oznacza elementy jednej kolekcji, które nie znajdują się w drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5cb08-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="5cb08-115">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="5cb08-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5cb08-116">Wspólnej</span><span class="sxs-lookup"><span data-stu-id="5cb08-116">Intersect</span></span>|<span data-ttu-id="5cb08-117">Zwraca część wspólną, która oznacza elementy, które pojawiają się w każdej z dwóch kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5cb08-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="5cb08-118">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="5cb08-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5cb08-119">Union</span><span class="sxs-lookup"><span data-stu-id="5cb08-119">Union</span></span>|<span data-ttu-id="5cb08-120">Zwraca zestaw zbiorów, co oznacza unikatowe elementy, które pojawiają się w jednej z dwóch kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5cb08-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="5cb08-121">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="5cb08-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="5cb08-122">Porównanie operacji ustawiania</span><span class="sxs-lookup"><span data-stu-id="5cb08-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="5cb08-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="5cb08-123">Distinct</span></span>  
 <span data-ttu-id="5cb08-124">Poniższa ilustracja przedstawia zachowanie <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody dla sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="5cb08-124">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="5cb08-125">Zwracana sekwencja zawiera unikatowe elementy z sekwencji wejściowej.</span><span class="sxs-lookup"><span data-stu-id="5cb08-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![Ilustracja przedstawiająca zachowanie różnych&#40;&#41;elementów.](./media/set-operations/distinct-method-behavior.png)  
  
### <a name="except"></a><span data-ttu-id="5cb08-127">Ale</span><span class="sxs-lookup"><span data-stu-id="5cb08-127">Except</span></span>  
 <span data-ttu-id="5cb08-128">Na poniższej ilustracji przedstawiono zachowanie <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5cb08-128">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5cb08-129">Zwracana sekwencja zawiera tylko elementy z pierwszej sekwencji wejściowej, które nie znajdują się w drugiej sekwencji wejściowej.</span><span class="sxs-lookup"><span data-stu-id="5cb08-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="5cb08-130">![Ilustracja przedstawiająca akcję z wyjątkiem&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Pokazuje zachowanie z wyjątkiem.")</span><span class="sxs-lookup"><span data-stu-id="5cb08-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="5cb08-131">Wspólnej</span><span class="sxs-lookup"><span data-stu-id="5cb08-131">Intersect</span></span>  
 <span data-ttu-id="5cb08-132">Na poniższej ilustracji przedstawiono zachowanie <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5cb08-132">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5cb08-133">Zwracana sekwencja zawiera elementy, które są wspólne dla obu sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="5cb08-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![Ilustracja przedstawiająca przecięcie dwóch sekwencji.](./media/set-operations/intersection-two-sequences.png)  
 
### <a name="union"></a><span data-ttu-id="5cb08-135">Union</span><span class="sxs-lookup"><span data-stu-id="5cb08-135">Union</span></span>  
 <span data-ttu-id="5cb08-136">Poniższa ilustracja przedstawia operację Union dla dwóch sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="5cb08-136">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="5cb08-137">Zwracana sekwencja zawiera unikatowe elementy z obu sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="5cb08-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![Ilustracja przedstawiająca Unię dwóch sekwencji.](./media/set-operations/union-operation-two-sequences.png)  
## <a name="see-also"></a><span data-ttu-id="5cb08-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5cb08-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="5cb08-140">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="5cb08-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="5cb08-141">Instrukcje: Łączenie i porównywanie kolekcji ciągów (LINQ)C#()</span><span class="sxs-lookup"><span data-stu-id="5cb08-141">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="5cb08-142">Instrukcje: Znajdź różnicę między dwoma listami (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="5cb08-142">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)
