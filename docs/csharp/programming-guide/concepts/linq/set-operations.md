---
title: Operacje na zestawie (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 9e507bbaa39bf040a8ce1564630fb5fbb8c0dbe4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61712216"
---
# <a name="set-operations-c"></a><span data-ttu-id="8945d-102">Operacje na zestawie (C#)</span><span class="sxs-lookup"><span data-stu-id="8945d-102">Set Operations (C#)</span></span>
<span data-ttu-id="8945d-103">Operacje na zestawie w składniku LINQ dotyczą operacje zapytań, które tworzą zestaw wyników, który zależy od obecności lub braku równoważne elementów w obrębie tego samego lub oddzielne kolekcje (lub zestawy).</span><span class="sxs-lookup"><span data-stu-id="8945d-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="8945d-104">Metody standardowego operatora zapytań, które wykonują operacje na zestawie są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="8945d-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8945d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8945d-105">Methods</span></span>  
  
|<span data-ttu-id="8945d-106">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="8945d-106">Method Name</span></span>|<span data-ttu-id="8945d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8945d-107">Description</span></span>|<span data-ttu-id="8945d-108">Składnia wyrażeń zapytania języka C#</span><span class="sxs-lookup"><span data-stu-id="8945d-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="8945d-109">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="8945d-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="8945d-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="8945d-110">Distinct</span></span>|<span data-ttu-id="8945d-111">Usuwa zduplikowane wartości z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8945d-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="8945d-112">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="8945d-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8945d-113">Z wyjątkiem</span><span class="sxs-lookup"><span data-stu-id="8945d-113">Except</span></span>|<span data-ttu-id="8945d-114">Zwraca różnicę zestawu, który oznacza, że elementy jednej kolekcji, które nie są wyświetlane w drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8945d-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="8945d-115">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="8945d-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8945d-116">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="8945d-116">Intersect</span></span>|<span data-ttu-id="8945d-117">Zwraca część wspólną zestawu, co oznacza, elementy, które są wyświetlane w każdym dwie kolekcje.</span><span class="sxs-lookup"><span data-stu-id="8945d-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="8945d-118">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="8945d-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="8945d-119">Union</span><span class="sxs-lookup"><span data-stu-id="8945d-119">Union</span></span>|<span data-ttu-id="8945d-120">Zwraca Unię zestawu, co oznacza unikatowych elementów, które pojawiają się w jednej z dwóch kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="8945d-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="8945d-121">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="8945d-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="8945d-122">Porównanie operacje na zestawie</span><span class="sxs-lookup"><span data-stu-id="8945d-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="8945d-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="8945d-123">Distinct</span></span>  
 <span data-ttu-id="8945d-124">Poniższa ilustracja przedstawia zachowanie <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody w sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="8945d-124">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="8945d-125">Zwracana sekwencja zawiera unikatowych elementów z sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="8945d-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![Grafika przedstawiająca zachowanie słowa kluczowego DISTINCT&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  
  
### <a name="except"></a><span data-ttu-id="8945d-127">Z wyjątkiem</span><span class="sxs-lookup"><span data-stu-id="8945d-127">Except</span></span>  
 <span data-ttu-id="8945d-128">Poniższa ilustracja przedstawia zachowanie <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8945d-128">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8945d-129">Zwracana sekwencja zawiera tylko elementy z pierwszej sekwencji wejściowych, które nie znajdują się w drugiej sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="8945d-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="8945d-130">![Grafika przedstawiająca działania z wyjątkiem&#40;&#41;. ](./media/set-operations/except-behavior-graphic.png "Pokazuje działanie z wyjątkiem.")</span><span class="sxs-lookup"><span data-stu-id="8945d-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="8945d-131">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="8945d-131">Intersect</span></span>  
 <span data-ttu-id="8945d-132">Poniższa ilustracja przedstawia zachowanie <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8945d-132">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8945d-133">Zwracana sekwencja zawiera elementy, które są wspólne dla obu sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="8945d-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![Grafika przedstawiająca części wspólnych dwóch sekwencji.](./media/set-operations/intersection-two-sequences.png)  
 
### <a name="union"></a><span data-ttu-id="8945d-135">Union</span><span class="sxs-lookup"><span data-stu-id="8945d-135">Union</span></span>  
 <span data-ttu-id="8945d-136">Poniższa ilustracja przedstawia operacji union na dwie sekwencje znaków.</span><span class="sxs-lookup"><span data-stu-id="8945d-136">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="8945d-137">Zwracana sekwencja zawiera unikatowych elementów z obu sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="8945d-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![Grafika przedstawiająca sumę dwóch sekwencji.](./media/set-operations/union-operation-two-sequences.png)  
## <a name="see-also"></a><span data-ttu-id="8945d-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8945d-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="8945d-140">Omówienie operatorów standardowej kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="8945d-140">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="8945d-141">Instrukcje: Łączenie i porównywanie kolekcji ciągów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="8945d-141">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="8945d-142">Instrukcje: Wyszukiwanie zestawu różnic między dwoma listami (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="8945d-142">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
