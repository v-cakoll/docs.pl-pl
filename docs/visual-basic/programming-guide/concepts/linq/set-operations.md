---
title: Operacje na zestawie (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2e30c521635326afeea4aad9ce932d5206d06c6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="6d8b5-102">Operacje na zestawie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d8b5-102">Set Operations (Visual Basic)</span></span>
<span data-ttu-id="6d8b5-103">Operacje na zestawie w składniku LINQ odwoływać się do operacji zapytania, które wywołują zestaw wyników, który jest oparty na obecności lub braku równoważne elementów w obrębie tego samego lub oddzielne kolekcje (lub zestawy).</span><span class="sxs-lookup"><span data-stu-id="6d8b5-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="6d8b5-104">Metody operator standardowe zapytań, które wykonują operacje na zestawie są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d8b5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6d8b5-105">Methods</span></span>  
  
|<span data-ttu-id="6d8b5-106">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="6d8b5-106">Method Name</span></span>|<span data-ttu-id="6d8b5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6d8b5-107">Description</span></span>|<span data-ttu-id="6d8b5-108">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6d8b5-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="6d8b5-109">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="6d8b5-109">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="6d8b5-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="6d8b5-110">Distinct</span></span>|<span data-ttu-id="6d8b5-111">Usuwa zduplikowane wartości z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6d8b5-112">Z wyjątkiem</span><span class="sxs-lookup"><span data-stu-id="6d8b5-112">Except</span></span>|<span data-ttu-id="6d8b5-113">Zwraca różnicę zestawu, co oznacza elementy jednej kolekcji, które nie są widoczne w druga kolekcja.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-113">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="6d8b5-114">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-114">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6d8b5-115">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="6d8b5-115">Intersect</span></span>|<span data-ttu-id="6d8b5-116">Zwraca część wspólną zestawu, co oznacza elementy, które są wyświetlane w każdym z dwóch kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-116">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="6d8b5-117">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6d8b5-118">Union</span><span class="sxs-lookup"><span data-stu-id="6d8b5-118">Union</span></span>|<span data-ttu-id="6d8b5-119">Zwraca zestaw, co oznacza unikatowych elementów, które pojawiają się w jednym z dwóch kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-119">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="6d8b5-120">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="6d8b5-121">Porównanie operacje na zestawie</span><span class="sxs-lookup"><span data-stu-id="6d8b5-121">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="6d8b5-122">Distinct</span><span class="sxs-lookup"><span data-stu-id="6d8b5-122">Distinct</span></span>  
 <span data-ttu-id="6d8b5-123">Na poniższej ilustracji przedstawiono zachowania <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody w sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-123">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="6d8b5-124">Zwrócony sekwencja zawiera elementy unikatowe z sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-124">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 <span data-ttu-id="6d8b5-125">![Grafika przedstawiająca zachowanie Distinct &#40; &#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Różne")</span><span class="sxs-lookup"><span data-stu-id="6d8b5-125">![Graphic showing the behavior of Distinct&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/distinct.png "Distinct")</span></span>  
  
### <a name="except"></a><span data-ttu-id="6d8b5-126">Z wyjątkiem</span><span class="sxs-lookup"><span data-stu-id="6d8b5-126">Except</span></span>  
 <span data-ttu-id="6d8b5-127">Na poniższej ilustracji przedstawiono zachowania <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-127">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6d8b5-128">Zwrócony sekwencja zawiera tylko elementy z pierwszego sekwencji wejściowych, które nie znajdują się w drugim sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-128">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="6d8b5-129">![Grafika przedstawiająca działania z wyjątkiem &#40; &#41;. ] (../../../../csharp/programming-guide/concepts/linq/media/except.png "z wyjątkiem")</span><span class="sxs-lookup"><span data-stu-id="6d8b5-129">![Graphic showing the action of Except&#40;&#41;.](../../../../csharp/programming-guide/concepts/linq/media/except.png "Except")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="6d8b5-130">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="6d8b5-130">Intersect</span></span>  
 <span data-ttu-id="6d8b5-131">Na poniższej ilustracji przedstawiono zachowania <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-131">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6d8b5-132">Zwrócony sekwencja zawiera elementy, które są wspólne dla obu sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-132">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 <span data-ttu-id="6d8b5-133">![Grafika przedstawiająca część wspólną dwóch sekwencji. ] (../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span><span class="sxs-lookup"><span data-stu-id="6d8b5-133">![Graphic showing the intersection of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/intersect.png "Intersect")</span></span>  
  
### <a name="union"></a><span data-ttu-id="6d8b5-134">Union</span><span class="sxs-lookup"><span data-stu-id="6d8b5-134">Union</span></span>  
 <span data-ttu-id="6d8b5-135">Na poniższej ilustracji przedstawiono Unii operacji na dwóch sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-135">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="6d8b5-136">Zwrócony sekwencja zawiera elementy unikatowe z obu sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-136">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 <span data-ttu-id="6d8b5-137">![Grafika przedstawiająca złożenie dwóch sekwencji. ] (../../../../csharp/programming-guide/concepts/linq/media/union.png "Unii")</span><span class="sxs-lookup"><span data-stu-id="6d8b5-137">![Graphic showing the union of two sequences.](../../../../csharp/programming-guide/concepts/linq/media/union.png "Union")</span></span>  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="6d8b5-138">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="6d8b5-138">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="6d8b5-139">W poniższym przykładzie użyto `Distinct` podklauzul LINQ zwracać unikatowe numery z listy liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="6d8b5-139">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>  
  
 [!code-vb[CsLINQSetOps#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/set-operations_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6d8b5-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d8b5-140">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="6d8b5-141">Operatory standardowe zapytań — omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d8b5-141">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="6d8b5-142">DISTINCT — klauzula</span><span class="sxs-lookup"><span data-stu-id="6d8b5-142">Distinct Clause</span></span>](../../../../visual-basic/language-reference/queries/distinct-clause.md)  
 [<span data-ttu-id="6d8b5-143">Porady: łączenie i porównywanie kolekcji ciągów (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d8b5-143">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)  
 [<span data-ttu-id="6d8b5-144">Porady: znajdowanie różnicy pomiędzy dwoma listami (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6d8b5-144">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
