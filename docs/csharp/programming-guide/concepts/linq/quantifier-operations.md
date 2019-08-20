---
title: Operacje kwantyfikatora (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 4a0f5b2c90d4b71a945dee02a32cbe897818c538
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591468"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="03d3e-102">Operacje kwantyfikatora (C#)</span><span class="sxs-lookup"><span data-stu-id="03d3e-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="03d3e-103">Operacje kwantyfikatora zwracają <xref:System.Boolean> wartość wskazującą, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="03d3e-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="03d3e-104">Na poniższej ilustracji przedstawiono dwa różne operacje kwantyfikatora dla dwóch różnych sekwencji źródłowych.</span><span class="sxs-lookup"><span data-stu-id="03d3e-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="03d3e-105">Pierwsza operacja pyta, czy co najmniej jeden element jest znakiem "A", a wynikiem jest `true`.</span><span class="sxs-lookup"><span data-stu-id="03d3e-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="03d3e-106">Druga operacja pyta, czy wszystkie elementy są znakiem "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="03d3e-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operacje kwantyfikatora LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="03d3e-108">Standardowe metody operatorów zapytań, które wykonują operacje kwantyfikatora, są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="03d3e-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="03d3e-109">Metody</span><span class="sxs-lookup"><span data-stu-id="03d3e-109">Methods</span></span>  
  
|<span data-ttu-id="03d3e-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="03d3e-110">Method Name</span></span>|<span data-ttu-id="03d3e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="03d3e-111">Description</span></span>|<span data-ttu-id="03d3e-112">C#Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="03d3e-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="03d3e-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="03d3e-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="03d3e-114">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="03d3e-114">All</span></span>|<span data-ttu-id="03d3e-115">Określa, czy wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="03d3e-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="03d3e-116">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="03d3e-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="03d3e-117">Any</span><span class="sxs-lookup"><span data-stu-id="03d3e-117">Any</span></span>|<span data-ttu-id="03d3e-118">Określa, czy dowolne elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="03d3e-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="03d3e-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="03d3e-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="03d3e-120">Zawiera</span><span class="sxs-lookup"><span data-stu-id="03d3e-120">Contains</span></span>|<span data-ttu-id="03d3e-121">Określa, czy sekwencja zawiera określony element.</span><span class="sxs-lookup"><span data-stu-id="03d3e-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="03d3e-122">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="03d3e-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="03d3e-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03d3e-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="03d3e-124">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="03d3e-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="03d3e-125">Instrukcje: Dynamiczne określanie filtrów predykatu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="03d3e-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="03d3e-126">Instrukcje: Zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="03d3e-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
