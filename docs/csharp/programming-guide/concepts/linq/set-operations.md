---
title: Ustawianie operacji (C#)
ms.date: 07/20/2015
ms.assetid: 7c589367-ef8f-4161-9050-642c47e6bf63
ms.openlocfilehash: 44a145a625b5e2e16d2469b20f8cfda1858560a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167936"
---
# <a name="set-operations-c"></a><span data-ttu-id="e89de-102">Ustawianie operacji (C#)</span><span class="sxs-lookup"><span data-stu-id="e89de-102">Set Operations (C#)</span></span>
<span data-ttu-id="e89de-103">Set operations in LINQ odnoszą się do operacji kwerendy, które produkują zestaw wyników, który jest oparty na obecności lub braku równoważnych elementów w ramach tych samych lub oddzielnych kolekcji (lub zestawów).</span><span class="sxs-lookup"><span data-stu-id="e89de-103">Set operations in LINQ refer to query operations that produce a result set that is based on the presence or absence of equivalent elements within the same or separate collections (or sets).</span></span>  
  
 <span data-ttu-id="e89de-104">Standardowe metody operatora kwerendy, które wykonują operacje zestawu są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="e89de-104">The standard query operator methods that perform set operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e89de-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e89de-105">Methods</span></span>  
  
|<span data-ttu-id="e89de-106">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="e89de-106">Method Name</span></span>|<span data-ttu-id="e89de-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e89de-107">Description</span></span>|<span data-ttu-id="e89de-108">Składnia wyrażenia kwerendy c#</span><span class="sxs-lookup"><span data-stu-id="e89de-108">C# Query Expression Syntax</span></span>|<span data-ttu-id="e89de-109">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="e89de-109">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="e89de-110">Distinct</span><span class="sxs-lookup"><span data-stu-id="e89de-110">Distinct</span></span>|<span data-ttu-id="e89de-111">Usuwa zduplikowane wartości z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e89de-111">Removes duplicate values from a collection.</span></span>|<span data-ttu-id="e89de-112">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="e89de-112">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Distinct%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e89de-113">Z wyjątkiem</span><span class="sxs-lookup"><span data-stu-id="e89de-113">Except</span></span>|<span data-ttu-id="e89de-114">Zwraca różnicę zestawu, co oznacza elementy jednej kolekcji, które nie są wyświetlane w drugiej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e89de-114">Returns the set difference, which means the elements of one collection that do not appear in a second collection.</span></span>|<span data-ttu-id="e89de-115">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="e89de-115">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Except%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e89de-116">Przecinają się</span><span class="sxs-lookup"><span data-stu-id="e89de-116">Intersect</span></span>|<span data-ttu-id="e89de-117">Zwraca zestaw przecięcia, co oznacza elementy, które pojawiają się w każdej z dwóch kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e89de-117">Returns the set intersection, which means elements that appear in each of two collections.</span></span>|<span data-ttu-id="e89de-118">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="e89de-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Intersect%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e89de-119">Unia</span><span class="sxs-lookup"><span data-stu-id="e89de-119">Union</span></span>|<span data-ttu-id="e89de-120">Zwraca zestaw unii, co oznacza unikatowe elementy, które pojawiają się w jednej z dwóch kolekcji.</span><span class="sxs-lookup"><span data-stu-id="e89de-120">Returns the set union, which means unique elements that appear in either of two collections.</span></span>|<span data-ttu-id="e89de-121">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="e89de-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Union%2A?displayProperty=nameWithType>|  
  
## <a name="comparison-of-set-operations"></a><span data-ttu-id="e89de-122">Porównanie operacji zestawu</span><span class="sxs-lookup"><span data-stu-id="e89de-122">Comparison of Set Operations</span></span>  
  
### <a name="distinct"></a><span data-ttu-id="e89de-123">Distinct</span><span class="sxs-lookup"><span data-stu-id="e89de-123">Distinct</span></span>  
 <span data-ttu-id="e89de-124">Poniższy przykład przedstawia zachowanie metody <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> na sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="e89de-124">The following example depicts the behavior of the <xref:System.Linq.Enumerable.Distinct%2A?displayProperty=nameWithType> method on a sequence of characters.</span></span> <span data-ttu-id="e89de-125">Zwrócona sekwencja zawiera unikatowe elementy z sekwencji wejściowej.</span><span class="sxs-lookup"><span data-stu-id="e89de-125">The returned sequence contains the unique elements from the input sequence.</span></span>  
  
 ![Grafika przedstawiająca zachowanie distinct&#40;&#41;.](./media/set-operations/distinct-method-behavior.png)  

 [!code-csharp-interactive[Distinct](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#1)]
  
### <a name="except"></a><span data-ttu-id="e89de-127">Z wyjątkiem</span><span class="sxs-lookup"><span data-stu-id="e89de-127">Except</span></span>  
 <span data-ttu-id="e89de-128">Poniższy przykład przedstawia zachowanie <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e89de-128">The following example depicts the behavior of <xref:System.Linq.Enumerable.Except%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e89de-129">Zwrócona sekwencja zawiera tylko elementy z pierwszej sekwencji wejściowej, które nie znajdują się w drugiej sekwencji wejściowej.</span><span class="sxs-lookup"><span data-stu-id="e89de-129">The returned sequence contains only the elements from the first input sequence that are not in the second input sequence.</span></span>  
  
 <span data-ttu-id="e89de-130">![Grafika przedstawiająca działanie z wyjątkiem&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Pokazuje zachowanie except.")</span><span class="sxs-lookup"><span data-stu-id="e89de-130">![Graphic showing the action of Except&#40;&#41;.](./media/set-operations/except-behavior-graphic.png "Shows the behavior of Except.")</span></span>  
  
[!code-csharp-interactive[Except](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#2)]

### <a name="intersect"></a><span data-ttu-id="e89de-131">Przecinają się</span><span class="sxs-lookup"><span data-stu-id="e89de-131">Intersect</span></span>  
 <span data-ttu-id="e89de-132">Poniższy przykład przedstawia zachowanie <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e89de-132">The following example depicts the behavior of <xref:System.Linq.Enumerable.Intersect%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e89de-133">Zwrócona sekwencja zawiera elementy, które są wspólne dla obu sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e89de-133">The returned sequence contains the elements that are common to both of the input sequences.</span></span>  
  
 ![Grafika przedstawiająca przecięcie dwóch sekwencji.](./media/set-operations/intersection-two-sequences.png)  

[!code-csharp-interactive[Intersect](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#3)]

### <a name="union"></a><span data-ttu-id="e89de-135">Unia</span><span class="sxs-lookup"><span data-stu-id="e89de-135">Union</span></span>  
 <span data-ttu-id="e89de-136">Poniższy przykład przedstawia operację unii na dwóch sekwencjach znaków.</span><span class="sxs-lookup"><span data-stu-id="e89de-136">The following example depicts a union operation on two sequences of characters.</span></span> <span data-ttu-id="e89de-137">Zwrócona sekwencja zawiera unikatowe elementy z obu sekwencji wejściowych.</span><span class="sxs-lookup"><span data-stu-id="e89de-137">The returned sequence contains the unique elements from both input sequences.</span></span>  
  
 ![Grafika przedstawiająca połączenie dwóch sekwencji.](./media/set-operations/union-operation-two-sequences.png)  

[!code-csharp-interactive[Union](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQSetOperation/CS/SetOperation.cs#4)]

## <a name="see-also"></a><span data-ttu-id="e89de-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e89de-139">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="e89de-140">Omówienie standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="e89de-140">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="e89de-141">Jak łączyć i porównywać kolekcje ciągów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e89de-141">How to combine and compare string collections (LINQ) (C#)</span></span>](./how-to-combine-and-compare-string-collections-linq.md)
- [<span data-ttu-id="e89de-142">Jak znaleźć różnicę między dwiema listami (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e89de-142">How to find the set difference between two lists (LINQ) (C#)</span></span>](./how-to-find-the-set-difference-between-two-lists-linq.md)
