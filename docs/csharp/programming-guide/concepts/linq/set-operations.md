---
title: Operacje na zestawie (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b5b546d9df8752fd7afd6e0db4525bc923a74bbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="set-operations-c"></a><span data-ttu-id="82343-102">Operacje na zestawie (C#)</span><span class="sxs-lookup"><span data-stu-id="82343-102">Set Operations (C#)</span></span>
<span data-ttu-id="82343-103">Operacje na zestawie w składniku LINQ odwoływać się do operacji zapytania, które wywołują zestaw wyników, który jest oparty na obecności lub braku równoważne elementów w obrębie tego samego lub oddzielne kolekcje (lub zestawy).</span><span class="sxs-lookup"><span data-stu-id="82343-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="82343-104">Metody operator standardowe zapytań, które wykonują operacje na zestawie są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="82343-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="82343-105">Metody</span><span class="sxs-lookup"><span data-stu-id="82343-105">Methods</span></span>  
  
|<span data-ttu-id="82343-106">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="82343-106">Method Name</span></span>|<span data-ttu-id="82343-107">Opis</span><span class="sxs-lookup"><span data-stu-id="82343-107">Description</span></span>|<span data-ttu-id="82343-108">Składnia wyrażenia zapytania C#</span><span class="sxs-lookup"><span data-stu-id="82343-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="82343-109">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="82343-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="82343-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="82343-110">Distinct</span></span>|<span data-ttu-id="82343-111">Usuwa zduplikowane wartości z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="82343-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="82343-112">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="82343-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="82343-113">Z wyjątkiem</span><span class="sxs-lookup"><span data-stu-id="82343-113">Except</span></span>|<span data-ttu-id="82343-114">Zwraca różnicę zestawu, co oznacza elementy jednej kolekcji, które nie są widoczne w druga kolekcja.</span><span class="sxs-lookup"><span data-stu-id="82343-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="82343-115">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="82343-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="82343-116">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="82343-116">Intersect</span></span>|<span data-ttu-id="82343-117">Zwraca część wspólną zestawu, co oznacza elementy, które są wyświetlane w każdym z dwóch kolekcji.</span><span class="sxs-lookup"><span data-stu-id="82343-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="82343-118">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="82343-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="82343-119">Union</span><span class="sxs-lookup"><span data-stu-id="82343-119">Union</span></span>|<span data-ttu-id="82343-120">Zwraca zestaw, co oznacza unikatowych elementów, które pojawiają się w jednym z dwóch kolekcji.</span><span class="sxs-lookup"><span data-stu-id="82343-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="82343-121">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="82343-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="82343-122">Porównanie operacje na zestawie</span><span class="sxs-lookup"><span data-stu-id="82343-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="82343-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="82343-123">Distinct</span></span>  
 <span data-ttu-id="82343-124">Na poniższej ilustracji przedstawiono zachowania <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody w sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="82343-124">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="82343-125">Zwrócony sekwencja zawiera elementy unikatowe z sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="82343-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 <span data-ttu-id="82343-126">![Grafika przedstawiająca zachowanie Distinct &#40; &#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Różne")</span><span class="sxs-lookup"><span data-stu-id="82343-126">![Graphic showing the behavior of Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span></span>  
  
### <a name="except"></a><span data-ttu-id="82343-127">Z wyjątkiem</span><span class="sxs-lookup"><span data-stu-id="82343-127">Except</span></span>  
 <span data-ttu-id="82343-128">Na poniższej ilustracji przedstawiono zachowania <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="82343-128">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="82343-129">Zwrócony sekwencja zawiera tylko elementy z pierwszego sekwencji wejściowych, które nie znajdują się w drugim sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="82343-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="82343-130">![Grafika przedstawiająca działania z wyjątkiem &#40; &#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/except.png "z wyjątkiem")</span><span class="sxs-lookup"><span data-stu-id="82343-130">![Graphic showing the action of Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="82343-131">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="82343-131">Intersect</span></span>  
 <span data-ttu-id="82343-132">Na poniższej ilustracji przedstawiono zachowania <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="82343-132">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="82343-133">Zwrócony sekwencja zawiera elementy, które są wspólne dla obu sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="82343-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 <span data-ttu-id="82343-134">![Grafika przedstawiająca część wspólną dwóch sekwencji. ] (../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span><span class="sxs-lookup"><span data-stu-id="82343-134">![Graphic showing the intersection of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span></span>  
  
### <a name="union"></a><span data-ttu-id="82343-135">Union</span><span class="sxs-lookup"><span data-stu-id="82343-135">Union</span></span>  
 <span data-ttu-id="82343-136">Na poniższej ilustracji przedstawiono Unii operacji na dwóch sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="82343-136">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="82343-137">Zwrócony sekwencja zawiera elementy unikatowe z obu sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="82343-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 <span data-ttu-id="82343-138">![Grafika przedstawiająca złożenie dwóch sekwencji. ] (../../../../csharp/programming-guide/concepts/linq/media/union.png "Unii")</span><span class="sxs-lookup"><span data-stu-id="82343-138">![Graphic showing the union of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82343-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82343-139">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="82343-140">Operatory standardowe zapytań — omówienie (C#)</span><span class="sxs-lookup"><span data-stu-id="82343-140">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="82343-141">Porady: łączenie i porównywanie kolekcji ciągów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="82343-141">How to: Combine and Compare String Collections (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [<span data-ttu-id="82343-142">Porady: znajdowanie różnicy pomiędzy dwoma listami (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="82343-142">How to: Find the Set Difference Between Two Lists (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
