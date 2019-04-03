---
title: Operacje na zestawie (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 2b06e822-e030-438f-9db7-ee402bd3a706
ms.openlocfilehash: 59ab09607462c762758e6a246ec218a92e01f5de
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825786"
---
# <a name="set-operations-visual-basic"></a><span data-ttu-id="69565-102">Operacje na zestawie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69565-102">Set Operations (Visual Basic)</span></span>
<span data-ttu-id="69565-103">Operacje na zestawie w składniku LINQ dotyczą operacje zapytań, które tworzą zestaw wyników, który zależy od obecności lub braku równoważne elementów w obrębie tego samego lub oddzielne kolekcje (lub zestawy).</span><span class="sxs-lookup"><span data-stu-id="69565-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="69565-104">Metody standardowego operatora zapytań, które wykonują operacje na zestawie są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="69565-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69565-105">Metody</span><span class="sxs-lookup"><span data-stu-id="69565-105">Methods</span></span>  
  
|<span data-ttu-id="69565-106">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="69565-106">Method Name</span></span>|<span data-ttu-id="69565-107">Opis</span><span class="sxs-lookup"><span data-stu-id="69565-107">Description</span></span>|<span data-ttu-id="69565-108">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="69565-108">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="69565-109">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="69565-109">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="69565-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="69565-110">Distinct</span></span>|<span data-ttu-id="69565-111">Usuwa zduplikowane wartości z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="69565-111">Removes duplicate values from a collection.</span></span>|`Distinct`|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="69565-112">Z wyjątkiem</span><span class="sxs-lookup"><span data-stu-id="69565-112">Except</span></span>|<span data-ttu-id="69565-113">Zwraca różnicę zestawu, który oznacza, że elementy jednej kolekcji, które nie są wyświetlane w drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="69565-113">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="69565-114">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="69565-114">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="69565-115">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="69565-115">Intersect</span></span>|<span data-ttu-id="69565-116">Zwraca część wspólną zestawu, co oznacza, elementy, które są wyświetlane w każdym dwie kolekcje.</span><span class="sxs-lookup"><span data-stu-id="69565-116">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="69565-117">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="69565-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="69565-118">Union</span><span class="sxs-lookup"><span data-stu-id="69565-118">Union</span></span>|<span data-ttu-id="69565-119">Zwraca Unię zestawu, co oznacza unikatowych elementów, które pojawiają się w jednej z dwóch kolekcjach.</span><span class="sxs-lookup"><span data-stu-id="69565-119">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="69565-120">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="69565-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="69565-121">Porównanie operacje na zestawie</span><span class="sxs-lookup"><span data-stu-id="69565-121">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="69565-122">Distinct</span><span class="sxs-lookup"><span data-stu-id="69565-122">Distinct</span></span>  
 <span data-ttu-id="69565-123">Poniższa ilustracja przedstawia zachowanie <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> metody w sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="69565-123">The following illustration depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="69565-124">Zwracana sekwencja zawiera unikatowych elementów z sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="69565-124">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![Grafika przedstawiająca zachowanie słowa kluczowego DISTINCT&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  
  
### <a name="except"></a><span data-ttu-id="69565-126">Z wyjątkiem</span><span class="sxs-lookup"><span data-stu-id="69565-126">Except</span></span>  
 <span data-ttu-id="69565-127">Poniższa ilustracja przedstawia zachowanie <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="69565-127">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="69565-128">Zwracana sekwencja zawiera tylko elementy z pierwszej sekwencji wejściowych, które nie znajdują się w drugiej sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="69565-128">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="69565-129">![Grafika przedstawiająca działania z wyjątkiem&#40;&#41;. ](./media/set-operations/except-behavior-graphic.png "Pokazuje działanie z wyjątkiem.")</span><span class="sxs-lookup"><span data-stu-id="69565-129">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
### <a name="intersect"></a><span data-ttu-id="69565-130">INTERSECT</span><span class="sxs-lookup"><span data-stu-id="69565-130">Intersect</span></span>  
 <span data-ttu-id="69565-131">Poniższa ilustracja przedstawia zachowanie <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="69565-131">The following illustration depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="69565-132">Zwracana sekwencja zawiera elementy, które są wspólne dla obu sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="69565-132">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![Grafika przedstawiająca części wspólnych dwóch sekwencji.](./media/set-operations/intersection-two-sequences.png)    
### <a name="union"></a><span data-ttu-id="69565-134">Union</span><span class="sxs-lookup"><span data-stu-id="69565-134">Union</span></span>  
 <span data-ttu-id="69565-135">Poniższa ilustracja przedstawia operacji union na dwie sekwencje znaków.</span><span class="sxs-lookup"><span data-stu-id="69565-135">The following illustration depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="69565-136">Zwracana sekwencja zawiera unikatowych elementów z obu sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="69565-136">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![Grafika przedstawiająca sumę dwóch sekwencji.](./media/set-operations/union-operation-two-sequences.png)    
## <a name="query-expression-syntax-example"></a><span data-ttu-id="69565-138">Przykład składni wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="69565-138">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="69565-139">W poniższym przykładzie użyto `Distinct` klauzuli w zapytaniu programu LINQ do zwrócenia unikatowe numery z listy liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="69565-139">The following example uses the `Distinct` clause in a LINQ query to return the unique numbers from a list of integers.</span></span>  
  
 [!code-vb[CsLINQSetOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQSetOps/VB/setops.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="69565-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69565-140">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="69565-141">Omówienie operatorów standardowej kwerendy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69565-141">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="69565-142">Distinct, klauzula</span><span class="sxs-lookup"><span data-stu-id="69565-142">Distinct Clause</span></span>](../../../../visual-basic/language-reference/queries/distinct-clause.md)
- [<span data-ttu-id="69565-143">Instrukcje: Łączenie i porównywanie kolekcji ciągów (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69565-143">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="69565-144">Instrukcje: Wyszukiwanie zestawu różnic między dwoma listami (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="69565-144">How to: Find the Set Difference Between Two Lists (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-find-the-set-difference-between-two-lists-linq.md)
