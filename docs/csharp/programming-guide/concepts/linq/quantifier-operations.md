---
title: Operacje kwantyfikatora (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d6152cbbd390508a8ffce732f6cbdf1f2e1aa0f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="6d9bd-102">Operacje kwantyfikatora (C#)</span><span class="sxs-lookup"><span data-stu-id="6d9bd-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="6d9bd-103">Operacje kwantyfikatora zwracać <xref:System.Boolean> wartość, która wskazuje, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="6d9bd-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="6d9bd-104">Na poniższej ilustracji przedstawiono dwie operacje kwantyfikatora różnych na dwóch różnych źródeł sekwencji.</span><span class="sxs-lookup"><span data-stu-id="6d9bd-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="6d9bd-105">Pierwszą operacją zapyta, jeśli co najmniej jeden z elementów jest znak "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="6d9bd-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="6d9bd-106">Druga operacja zapyta, czy wszystkie elementy są znaków "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="6d9bd-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="6d9bd-107">![Operacje kwantyfikatora LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="6d9bd-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="6d9bd-108">Metody — operator standardowe zapytań, które wykonują operacje kwantyfikatora są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="6d9bd-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6d9bd-109">Metody</span><span class="sxs-lookup"><span data-stu-id="6d9bd-109">Methods</span></span>  
  
|<span data-ttu-id="6d9bd-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="6d9bd-110">Method Name</span></span>|<span data-ttu-id="6d9bd-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6d9bd-111">Description</span></span>|<span data-ttu-id="6d9bd-112">Składnia wyrażenia zapytania C#</span><span class="sxs-lookup"><span data-stu-id="6d9bd-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="6d9bd-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="6d9bd-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="6d9bd-114">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="6d9bd-114">All</span></span>|<span data-ttu-id="6d9bd-115">Określa, czy wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="6d9bd-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="6d9bd-116">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="6d9bd-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6d9bd-117">wszystkie</span><span class="sxs-lookup"><span data-stu-id="6d9bd-117">Any</span></span>|<span data-ttu-id="6d9bd-118">Określa, czy wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="6d9bd-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="6d9bd-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="6d9bd-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6d9bd-120">Zawiera</span><span class="sxs-lookup"><span data-stu-id="6d9bd-120">Contains</span></span>|<span data-ttu-id="6d9bd-121">Określa, czy sekwencja zawiera określony element.</span><span class="sxs-lookup"><span data-stu-id="6d9bd-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="6d9bd-122">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="6d9bd-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="6d9bd-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6d9bd-123">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="6d9bd-124">Operatory standardowe zapytań — omówienie (C#)</span><span class="sxs-lookup"><span data-stu-id="6d9bd-124">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="6d9bd-125">Porady: dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="6d9bd-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)  
 [<span data-ttu-id="6d9bd-126">Porady: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="6d9bd-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
