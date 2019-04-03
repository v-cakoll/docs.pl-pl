---
title: Partycjonowanie danych (C#)
ms.date: 07/20/2015
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
ms.openlocfilehash: b857c8c6e6b56a7263e6725a747e98ccfe4ff4fc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832466"
---
# <a name="partitioning-data-c"></a><span data-ttu-id="f0b33-102">Partycjonowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="f0b33-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="f0b33-103">Partycjonowanie w składniku LINQ odnosi się do funkcjonowania dzielenie sekwencji wejściowych na dwie sekcje bez rozmieszczanie elementów, a następnie powrotu w sekcji.</span><span class="sxs-lookup"><span data-stu-id="f0b33-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="f0b33-104">Poniższa ilustracja przedstawia wyniki trzech różnych partycjonowania operacji na sekwencję znaków.</span><span class="sxs-lookup"><span data-stu-id="f0b33-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="f0b33-105">Pierwsza operacja zwraca pierwsze trzy elementy w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="f0b33-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="f0b33-106">Drugą operację pomija pierwszych trzech elementów i zwraca wszystkie pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="f0b33-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="f0b33-107">Operacja trzeci pomija pierwszych dwóch elementów w sekwencji i zwraca następne trzy elementy.</span><span class="sxs-lookup"><span data-stu-id="f0b33-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 ![Ilustracja przedstawiająca trzy operacje partycjonowania LINQ.](./media/partitioning-data/linq-partitioning-operations.png)  
  
 <span data-ttu-id="f0b33-109">Metody standardowego operatora zapytań, partycji sekwencji, które są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f0b33-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="f0b33-110">Operatory</span><span class="sxs-lookup"><span data-stu-id="f0b33-110">Operators</span></span>  
  
|<span data-ttu-id="f0b33-111">Nazwa operatora</span><span class="sxs-lookup"><span data-stu-id="f0b33-111">Operator Name</span></span>|<span data-ttu-id="f0b33-112">Opis</span><span class="sxs-lookup"><span data-stu-id="f0b33-112">Description</span></span>|<span data-ttu-id="f0b33-113">Składnia wyrażeń zapytania języka C#</span><span class="sxs-lookup"><span data-stu-id="f0b33-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="f0b33-114">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="f0b33-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="f0b33-115">Skip</span><span class="sxs-lookup"><span data-stu-id="f0b33-115">Skip</span></span>|<span data-ttu-id="f0b33-116">Pomija elementy do określonej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="f0b33-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="f0b33-117">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="f0b33-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f0b33-118">SkipWhile</span><span class="sxs-lookup"><span data-stu-id="f0b33-118">SkipWhile</span></span>|<span data-ttu-id="f0b33-119">Pomija elementy oparte na funkcji predykatu, dopóki element nie spełnia warunku.</span><span class="sxs-lookup"><span data-stu-id="f0b33-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="f0b33-120">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="f0b33-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f0b33-121">Take</span><span class="sxs-lookup"><span data-stu-id="f0b33-121">Take</span></span>|<span data-ttu-id="f0b33-122">Pobiera elementy do określonej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="f0b33-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="f0b33-123">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="f0b33-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="f0b33-124">TakeWhile</span><span class="sxs-lookup"><span data-stu-id="f0b33-124">TakeWhile</span></span>|<span data-ttu-id="f0b33-125">Pobiera elementy oparte na funkcji predykatu, dopóki element nie spełnia warunku.</span><span class="sxs-lookup"><span data-stu-id="f0b33-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="f0b33-126">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="f0b33-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="f0b33-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0b33-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="f0b33-128">Omówienie operatorów standardowej kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="f0b33-128">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
