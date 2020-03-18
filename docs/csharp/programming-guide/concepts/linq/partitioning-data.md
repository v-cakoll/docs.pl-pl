---
title: Partycjonowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: d9330e9973b2f25903e1f81a7296362e2a7c756b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591591"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="fbf5a-102">Partycjonowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="fbf5a-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="fbf5a-103">Partycjonowanie w LINQ odnosi się do operacji dzielenia sekwencji wejściowej na dwie sekcje, bez zmiany rozmieszczenia elementów, a następnie zwracanie jednej z sekcji.</span><span class="sxs-lookup"><span data-stu-id="fbf5a-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="fbf5a-104">Na poniższej ilustracji przedstawiono wyniki trzech różnych operacji partycjonowania sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="fbf5a-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="fbf5a-105">Pierwsza operacja zwraca pierwsze trzy elementy w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="fbf5a-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="fbf5a-106">Druga operacja pomija pierwsze trzy elementy i zwraca pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="fbf5a-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="fbf5a-107">Trzecia operacja pomija pierwsze dwa elementy w sekwencji i zwraca następne trzy elementy.</span><span class="sxs-lookup"><span data-stu-id="fbf5a-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Ilustracja, która pokazuje trzy operacje partycjonowania LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="fbf5a-109">Standardowe metody operatora kwerendy, które sekwencje partycji są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="fbf5a-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="fbf5a-110">Operatory</span><span class="sxs-lookup"><span data-stu-id="fbf5a-110">Operators</span></span>  
  
|<span data-ttu-id="fbf5a-111">Nazwa operatora</span><span class="sxs-lookup"><span data-stu-id="fbf5a-111">Operator Name</span></span>|<span data-ttu-id="fbf5a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="fbf5a-112">Description</span></span>|<span data-ttu-id="fbf5a-113">Składnia wyrażenia kwerendy c#</span><span class="sxs-lookup"><span data-stu-id="fbf5a-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="fbf5a-114">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="fbf5a-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="fbf5a-115">Skip</span><span class="sxs-lookup"><span data-stu-id="fbf5a-115">Skip</span></span>|<span data-ttu-id="fbf5a-116">Pomija elementy do określonej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="fbf5a-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="fbf5a-117">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="fbf5a-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fbf5a-118">Skipwhile</span><span class="sxs-lookup"><span data-stu-id="fbf5a-118">SkipWhile</span></span>|<span data-ttu-id="fbf5a-119">Pomija elementy na podstawie funkcji predykatu, dopóki element nie spełnia warunku.</span><span class="sxs-lookup"><span data-stu-id="fbf5a-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="fbf5a-120">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="fbf5a-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fbf5a-121">Take</span><span class="sxs-lookup"><span data-stu-id="fbf5a-121">Take</span></span>|<span data-ttu-id="fbf5a-122">Pobiera elementy do określonej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="fbf5a-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="fbf5a-123">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="fbf5a-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fbf5a-124">Takewhile</span><span class="sxs-lookup"><span data-stu-id="fbf5a-124">TakeWhile</span></span>|<span data-ttu-id="fbf5a-125">Pobiera elementy oparte na funkcji predykatu, dopóki element nie spełnia warunku.</span><span class="sxs-lookup"><span data-stu-id="fbf5a-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="fbf5a-126">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="fbf5a-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="fbf5a-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fbf5a-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="fbf5a-128">Omówienie standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="fbf5a-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
