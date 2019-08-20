---
title: Partycjonowanie danychC#()
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: d9330e9973b2f25903e1f81a7296362e2a7c756b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591591"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="5369b-102">Partycjonowanie danychC#()</span><span class="sxs-lookup"><span data-stu-id="5369b-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="5369b-103">Partycjonowanie w LINQ odwołuje się do operacji dzielenia sekwencji wejściowej na dwie sekcje, bez konieczności ponownej rozmieszczania elementów, a następnie zwrócenia jednej z sekcji.</span><span class="sxs-lookup"><span data-stu-id="5369b-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="5369b-104">Na poniższej ilustracji przedstawiono wyniki trzech różnych operacji partycjonowania na sekwencji znaków.</span><span class="sxs-lookup"><span data-stu-id="5369b-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="5369b-105">Pierwsza operacja zwraca trzy pierwsze elementy w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5369b-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="5369b-106">Druga operacja pomija pierwsze trzy elementy i zwraca pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="5369b-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="5369b-107">Trzecia operacja pomija pierwsze dwa elementy w sekwencji i zwraca następne trzy elementy.</span><span class="sxs-lookup"><span data-stu-id="5369b-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Ilustracja przedstawiająca trzy operacje partycjonowania LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="5369b-109">Standardowe metody operatorów zapytań, które są sekwencje partycji, są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="5369b-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="5369b-110">Operatory</span><span class="sxs-lookup"><span data-stu-id="5369b-110">Operators</span></span>  
  
|<span data-ttu-id="5369b-111">Nazwa operatora</span><span class="sxs-lookup"><span data-stu-id="5369b-111">Operator Name</span></span>|<span data-ttu-id="5369b-112">Opis</span><span class="sxs-lookup"><span data-stu-id="5369b-112">Description</span></span>|<span data-ttu-id="5369b-113">C#Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="5369b-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="5369b-114">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="5369b-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="5369b-115">Skip</span><span class="sxs-lookup"><span data-stu-id="5369b-115">Skip</span></span>|<span data-ttu-id="5369b-116">Pomija elementy do określonej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5369b-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="5369b-117">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="5369b-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5369b-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="5369b-118">SkipWhile</span></span>|<span data-ttu-id="5369b-119">Pomija elementy na podstawie funkcji predykatu, dopóki element nie spełnia warunku.</span><span class="sxs-lookup"><span data-stu-id="5369b-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="5369b-120">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="5369b-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5369b-121">Take</span><span class="sxs-lookup"><span data-stu-id="5369b-121">Take</span></span>|<span data-ttu-id="5369b-122">Pobiera elementy do określonej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="5369b-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="5369b-123">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="5369b-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="5369b-124">TakeWhile —</span><span class="sxs-lookup"><span data-stu-id="5369b-124">TakeWhile</span></span>|<span data-ttu-id="5369b-125">Pobiera elementy na podstawie funkcji predykatu, dopóki element nie spełnia warunku.</span><span class="sxs-lookup"><span data-stu-id="5369b-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="5369b-126">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="5369b-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="5369b-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5369b-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="5369b-128">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="5369b-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
