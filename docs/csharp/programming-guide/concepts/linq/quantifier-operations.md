---
title: Operacje kwantyfikatora (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 090bc53c3dcedc82972ab7d16fa2968011a7db65
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61681786"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="57266-102">Operacje kwantyfikatora (C#)</span><span class="sxs-lookup"><span data-stu-id="57266-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="57266-103">Operacje kwantyfikatora zwracają <xref:System.Boolean> wartość, która wskazuje, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="57266-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="57266-104">Poniższa ilustracja przedstawia dwie operacje kwantyfikatora różnych na dwie sekwencje innego źródła.</span><span class="sxs-lookup"><span data-stu-id="57266-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="57266-105">Pierwszą operacją pytaniem, jeśli co najmniej jeden z elementów jest znak "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="57266-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="57266-106">Pyta drugą operację, jeśli wszystkie elementy są znak "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="57266-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operacje kwantyfikatora LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="57266-108">Metody standardowego operatora zapytań, które wykonują operacje kwantyfikatora są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="57266-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57266-109">Metody</span><span class="sxs-lookup"><span data-stu-id="57266-109">Methods</span></span>  
  
|<span data-ttu-id="57266-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="57266-110">Method Name</span></span>|<span data-ttu-id="57266-111">Opis</span><span class="sxs-lookup"><span data-stu-id="57266-111">Description</span></span>|<span data-ttu-id="57266-112">Składnia wyrażeń zapytania języka C#</span><span class="sxs-lookup"><span data-stu-id="57266-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="57266-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="57266-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="57266-114">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="57266-114">All</span></span>|<span data-ttu-id="57266-115">Określa, czy wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="57266-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="57266-116">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="57266-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="57266-117">Dowolne</span><span class="sxs-lookup"><span data-stu-id="57266-117">Any</span></span>|<span data-ttu-id="57266-118">Określa, czy dowolne elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="57266-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="57266-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="57266-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="57266-120">Zawiera</span><span class="sxs-lookup"><span data-stu-id="57266-120">Contains</span></span>|<span data-ttu-id="57266-121">Określa, czy sekwencja zawiera określony element.</span><span class="sxs-lookup"><span data-stu-id="57266-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="57266-122">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="57266-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="57266-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57266-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="57266-124">Omówienie operatorów standardowej kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="57266-124">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="57266-125">Instrukcje: Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="57266-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="57266-126">Instrukcje: Zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="57266-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
