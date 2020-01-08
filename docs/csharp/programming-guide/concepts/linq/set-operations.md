---
title: Operacje Set (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 170316b36705eaed51a9a17f8f79333a29e8c315
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346510"
---
# <a name="set-operations-c"></a><span data-ttu-id="140fd-102">Operacje Set (C#)</span><span class="sxs-lookup"><span data-stu-id="140fd-102">Set Operations (C#)</span></span>
<span data-ttu-id="140fd-103">Operacje Set w LINQ odnoszą się do operacji zapytania, które tworzą zestaw wyników, który jest oparty na obecności lub braku równoważnych elementów w obrębie tych samych lub oddzielnych kolekcji (lub zestawów).</span><span class="sxs-lookup"><span data-stu-id="140fd-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="140fd-104">W poniższej sekcji przedstawiono standardowe metody operatorów zapytań, które wykonują operacje na zestawach.</span><span class="sxs-lookup"><span data-stu-id="140fd-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="140fd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="140fd-105">Methods</span></span>  
  
|<span data-ttu-id="140fd-106">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="140fd-106">Method Name</span></span>|<span data-ttu-id="140fd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="140fd-107">Description</span></span>|<span data-ttu-id="140fd-108">C#Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="140fd-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="140fd-109">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="140fd-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="140fd-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="140fd-110">Distinct</span></span>|<span data-ttu-id="140fd-111">Usuwa zduplikowane wartości z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="140fd-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="140fd-112">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="140fd-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="140fd-113">Z wyjątkiem</span><span class="sxs-lookup"><span data-stu-id="140fd-113">Except</span></span>|<span data-ttu-id="140fd-114">Zwraca różnicę zestawu, co oznacza elementy jednej kolekcji, które nie znajdują się w drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="140fd-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="140fd-115">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="140fd-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="140fd-116">wspólnej</span><span class="sxs-lookup"><span data-stu-id="140fd-116">Intersect</span></span>|<span data-ttu-id="140fd-117">Zwraca część wspólną, która oznacza elementy, które pojawiają się w każdej z dwóch kolekcji.</span><span class="sxs-lookup"><span data-stu-id="140fd-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="140fd-118">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="140fd-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="140fd-119">Union</span><span class="sxs-lookup"><span data-stu-id="140fd-119">Union</span></span>|<span data-ttu-id="140fd-120">Zwraca zestaw zbiorów, co oznacza unikatowe elementy, które pojawiają się w jednej z dwóch kolekcji.</span><span class="sxs-lookup"><span data-stu-id="140fd-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="140fd-121">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="140fd-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="140fd-122">Porównanie operacji ustawiania</span><span class="sxs-lookup"><span data-stu-id="140fd-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="140fd-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="140fd-123">Distinct</span></span>  
 <span data-ttu-id="140fd-124">Poniższy przykład ilustruje zachowanie metody <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> na sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="140fd-124">The following example depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="140fd-125">Zwracana sekwencja zawiera unikatowe elementy z sekwencji wejściowej.</span><span class="sxs-lookup"><span data-stu-id="140fd-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![Ilustracja przedstawiająca zachowanie różnych&#40;&#41;elementów.](./media/set-operations/distinct-method-behavior.png)  
 
 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a><span data-ttu-id="140fd-127">Z wyjątkiem</span><span class="sxs-lookup"><span data-stu-id="140fd-127">Except</span></span>  
 <span data-ttu-id="140fd-128">Poniższy przykład przedstawia zachowanie <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="140fd-128">The following example depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="140fd-129">Zwracana sekwencja zawiera tylko elementy z pierwszej sekwencji wejściowej, które nie znajdują się w drugiej sekwencji wejściowej.</span><span class="sxs-lookup"><span data-stu-id="140fd-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="140fd-130">![Ilustracja przedstawiająca akcję z wyjątkiem&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Pokazuje zachowanie z wyjątkiem.")</span><span class="sxs-lookup"><span data-stu-id="140fd-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a><span data-ttu-id="140fd-131">wspólnej</span><span class="sxs-lookup"><span data-stu-id="140fd-131">Intersect</span></span>  
 <span data-ttu-id="140fd-132">Poniższy przykład przedstawia zachowanie <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="140fd-132">The following example depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="140fd-133">Zwracana sekwencja zawiera elementy, które są wspólne dla obu sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="140fd-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![Ilustracja przedstawiająca przecięcie dwóch sekwencji.](./media/set-operations/intersection-two-sequences.png)  
 
[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a><span data-ttu-id="140fd-135">Union</span><span class="sxs-lookup"><span data-stu-id="140fd-135">Union</span></span>  
 <span data-ttu-id="140fd-136">Poniższy przykład przedstawia operację Union dla dwóch sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="140fd-136">The following example depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="140fd-137">Zwracana sekwencja zawiera unikatowe elementy z obu sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="140fd-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![Ilustracja przedstawiająca Unię dwóch sekwencji.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]
 
## <a name="see-also"></a><span data-ttu-id="140fd-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="140fd-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="140fd-140">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="140fd-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="140fd-141">Łączenie i porównywanie kolekcji ciągów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="140fd-141">How to combine and compare string collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="140fd-142">Jak znaleźć różnice między dwoma listami (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="140fd-142">How to find the set difference between two lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)
