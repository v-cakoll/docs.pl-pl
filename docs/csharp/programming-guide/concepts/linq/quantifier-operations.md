---
title: Operacje kwantyfikatora (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5899af79799d5b8404e60027d7ba1b005c4b1b79
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423363"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="e3ff5-102">Operacje kwantyfikatora (C#)</span><span class="sxs-lookup"><span data-stu-id="e3ff5-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="e3ff5-103">Operacje kwantyfikatora zwracają <xref:System.Boolean> wartość wskazującą, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="e3ff5-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="e3ff5-104">Na poniższej ilustracji przedstawiono dwa różne operacje kwantyfikatora dla dwóch różnych sekwencji źródłowych.</span><span class="sxs-lookup"><span data-stu-id="e3ff5-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="e3ff5-105">Pierwsza operacja pyta, czy co najmniej jeden element jest znakiem "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="e3ff5-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="e3ff5-106">Druga operacja pyta, czy wszystkie elementy są znakiem "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="e3ff5-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operacje kwantyfikatora LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="e3ff5-108">Standardowe metody operatorów zapytań, które wykonują operacje kwantyfikatora, są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="e3ff5-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e3ff5-109">Metody</span><span class="sxs-lookup"><span data-stu-id="e3ff5-109">Methods</span></span>  
  
|<span data-ttu-id="e3ff5-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="e3ff5-110">Method Name</span></span>|<span data-ttu-id="e3ff5-111">Opis</span><span class="sxs-lookup"><span data-stu-id="e3ff5-111">Description</span></span>|<span data-ttu-id="e3ff5-112">C#Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="e3ff5-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="e3ff5-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="e3ff5-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="e3ff5-114">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="e3ff5-114">All</span></span>|<span data-ttu-id="e3ff5-115">Określa, czy wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="e3ff5-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="e3ff5-116">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="e3ff5-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e3ff5-117">Ile</span><span class="sxs-lookup"><span data-stu-id="e3ff5-117">Any</span></span>|<span data-ttu-id="e3ff5-118">Określa, czy dowolne elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="e3ff5-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="e3ff5-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="e3ff5-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="e3ff5-120">Zawiera</span><span class="sxs-lookup"><span data-stu-id="e3ff5-120">Contains</span></span>|<span data-ttu-id="e3ff5-121">Określa, czy sekwencja zawiera określony element.</span><span class="sxs-lookup"><span data-stu-id="e3ff5-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="e3ff5-122">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="e3ff5-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="e3ff5-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3ff5-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="e3ff5-124">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="e3ff5-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="e3ff5-125">Instrukcje: dynamiczne określanie filtrów predykatu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="e3ff5-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="e3ff5-126">Instrukcje: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="e3ff5-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
