---
title: Partycjonowanie danych (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 2a5c507b-fe22-443c-a768-dec7f9ec568d
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 32b95887e05767513dd818743dd1726149503b0f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="partitioning-data-c"></a><span data-ttu-id="bf91d-102">Partycjonowanie danych (C#)</span><span class="sxs-lookup"><span data-stu-id="bf91d-102">Partitioning Data (C#)</span></span>
<span data-ttu-id="bf91d-103">Podział na partycje w składniku LINQ odwołuje się do funkcjonowania dzielenie sekwencji wejściowych na dwie sekcje bez zmienianie rozmieszczenia elementów, a następnie zwraca w sekcji.</span><span class="sxs-lookup"><span data-stu-id="bf91d-103">Partitioning in LINQ refers to the operation of dividing an input sequence into two sections, without rearranging the elements, and then returning one of the sections.</span></span>  
  
 <span data-ttu-id="bf91d-104">Na poniższej ilustracji przedstawiono wyniki trzech różnych partycjonowania operacji na sekwencję znaków.</span><span class="sxs-lookup"><span data-stu-id="bf91d-104">The following illustration shows the results of three different partitioning operations on a sequence of characters.</span></span> <span data-ttu-id="bf91d-105">Pierwsza operacja zwraca pierwsze trzy elementy w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="bf91d-105">The first operation returns the first three elements in the sequence.</span></span> <span data-ttu-id="bf91d-106">Druga operacja pomija pierwszych trzech elementów i zwraca wszystkie pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="bf91d-106">The second operation skips the first three elements and returns the remaining elements.</span></span> <span data-ttu-id="bf91d-107">Trzeci operacji pomija pierwsze dwa elementy w sekwencji i zwraca trzech kolejnych elementów.</span><span class="sxs-lookup"><span data-stu-id="bf91d-107">The third operation skips the first two elements in the sequence and returns the next three elements.</span></span>  
  
 <span data-ttu-id="bf91d-108">![LINQ partycjonowania operacji](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span><span class="sxs-lookup"><span data-stu-id="bf91d-108">![LINQ Partitioning Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_partition.png "LINQ_Partition")</span></span>  
  
 <span data-ttu-id="bf91d-109">Metody operator standardowej kwerendy, które partycji sekwencje są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="bf91d-109">The standard query operator methods that partition sequences are listed in the following section.</span></span>  
  
## <a name="operators"></a><span data-ttu-id="bf91d-110">Operatory</span><span class="sxs-lookup"><span data-stu-id="bf91d-110">Operators</span></span>  
  
|<span data-ttu-id="bf91d-111">Nazwa operatora</span><span class="sxs-lookup"><span data-stu-id="bf91d-111">Operator Name</span></span>|<span data-ttu-id="bf91d-112">Opis</span><span class="sxs-lookup"><span data-stu-id="bf91d-112">Description</span></span>|<span data-ttu-id="bf91d-113">Składnia wyrażenia zapytania C#</span><span class="sxs-lookup"><span data-stu-id="bf91d-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="bf91d-114">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="bf91d-114">More Information</span></span>|  
|-------------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="bf91d-115">Skip</span><span class="sxs-lookup"><span data-stu-id="bf91d-115">Skip</span></span>|<span data-ttu-id="bf91d-116">Pomija elementy do określonej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="bf91d-116">Skips elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="bf91d-117">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="bf91d-117">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Skip%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Skip%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="bf91d-118">skipWhile</span><span class="sxs-lookup"><span data-stu-id="bf91d-118">SkipWhile</span></span>|<span data-ttu-id="bf91d-119">Pomija elementy oparte na funkcji predykatu, dopóki element nie spełnia warunku.</span><span class="sxs-lookup"><span data-stu-id="bf91d-119">Skips elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="bf91d-120">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="bf91d-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.SkipWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SkipWhile%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="bf91d-121">Take</span><span class="sxs-lookup"><span data-stu-id="bf91d-121">Take</span></span>|<span data-ttu-id="bf91d-122">Pobiera elementy do określonej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="bf91d-122">Takes elements up to a specified position in a sequence.</span></span>|<span data-ttu-id="bf91d-123">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="bf91d-123">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Take%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Take%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="bf91d-124">takeWhile</span><span class="sxs-lookup"><span data-stu-id="bf91d-124">TakeWhile</span></span>|<span data-ttu-id="bf91d-125">Pobiera elementy oparte na funkcji predykatu, dopóki element nie spełnia warunku.</span><span class="sxs-lookup"><span data-stu-id="bf91d-125">Takes elements based on a predicate function until an element does not satisfy the condition.</span></span>|<span data-ttu-id="bf91d-126">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="bf91d-126">Not applicable.</span></span>|<xref:System.Linq.Enumerable.TakeWhile%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.TakeWhile%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="bf91d-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf91d-127">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="bf91d-128">Operatory standardowe zapytań — omówienie (C#)</span><span class="sxs-lookup"><span data-stu-id="bf91d-128">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
