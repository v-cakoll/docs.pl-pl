---
title: Operacje kwantyfikatora (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 24c8f9a6b589592c26c8a514bc44ff9623a82d2f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523108"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="3e2de-102">Operacje kwantyfikatora (C#)</span><span class="sxs-lookup"><span data-stu-id="3e2de-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="3e2de-103">Operacje kwantyfikatora zwracają <xref:System.Boolean> wartość, która wskazuje, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="3e2de-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="3e2de-104">Poniższa ilustracja przedstawia dwie operacje kwantyfikatora różnych na dwie sekwencje innego źródła.</span><span class="sxs-lookup"><span data-stu-id="3e2de-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="3e2de-105">Pierwszą operacją pytaniem, jeśli co najmniej jeden z elementów jest znak "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="3e2de-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="3e2de-106">Pyta drugą operację, jeśli wszystkie elementy są znak "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="3e2de-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="3e2de-107">![Operacje kwantyfikatora LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="3e2de-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="3e2de-108">Metody standardowego operatora zapytań, które wykonują operacje kwantyfikatora są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="3e2de-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e2de-109">Metody</span><span class="sxs-lookup"><span data-stu-id="3e2de-109">Methods</span></span>  
  
|<span data-ttu-id="3e2de-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="3e2de-110">Method Name</span></span>|<span data-ttu-id="3e2de-111">Opis</span><span class="sxs-lookup"><span data-stu-id="3e2de-111">Description</span></span>|<span data-ttu-id="3e2de-112">Składnia wyrażeń zapytania języka C#</span><span class="sxs-lookup"><span data-stu-id="3e2de-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="3e2de-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="3e2de-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="3e2de-114">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="3e2de-114">All</span></span>|<span data-ttu-id="3e2de-115">Określa, czy wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="3e2de-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="3e2de-116">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="3e2de-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3e2de-117">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="3e2de-117">Any</span></span>|<span data-ttu-id="3e2de-118">Określa, czy dowolne elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="3e2de-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="3e2de-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="3e2de-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="3e2de-120">Zawiera</span><span class="sxs-lookup"><span data-stu-id="3e2de-120">Contains</span></span>|<span data-ttu-id="3e2de-121">Określa, czy sekwencja zawiera określony element.</span><span class="sxs-lookup"><span data-stu-id="3e2de-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="3e2de-122">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="3e2de-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="3e2de-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e2de-123">See Also</span></span>

- <xref:System.Linq>  
- [<span data-ttu-id="3e2de-124">Omówienie operatorów standardowej kwerendy (C#)</span><span class="sxs-lookup"><span data-stu-id="3e2de-124">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
- [<span data-ttu-id="3e2de-125">Porady: dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="3e2de-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)  
- [<span data-ttu-id="3e2de-126">Porady: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="3e2de-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
