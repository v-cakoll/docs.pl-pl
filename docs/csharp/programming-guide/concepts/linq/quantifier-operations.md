---
title: Operacje kwantyfikatora (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: dac5ca7349a45f5fc37cff0cb83bd6b2e1292568
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339868"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="d0179-102">Operacje kwantyfikatora (C#)</span><span class="sxs-lookup"><span data-stu-id="d0179-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="d0179-103">Operacje kwantyfikatora zwracać <xref:System.Boolean> wartość, która wskazuje, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="d0179-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="d0179-104">Na poniższej ilustracji przedstawiono dwie operacje kwantyfikatora różnych na dwóch różnych źródeł sekwencji.</span><span class="sxs-lookup"><span data-stu-id="d0179-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="d0179-105">Pierwszą operacją zapyta, jeśli co najmniej jeden z elementów jest znak "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="d0179-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="d0179-106">Druga operacja zapyta, czy wszystkie elementy są znaków "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="d0179-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="d0179-107">![Operacje kwantyfikatora LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="d0179-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="d0179-108">Metody — operator standardowe zapytań, które wykonują operacje kwantyfikatora są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="d0179-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0179-109">Metody</span><span class="sxs-lookup"><span data-stu-id="d0179-109">Methods</span></span>  
  
|<span data-ttu-id="d0179-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="d0179-110">Method Name</span></span>|<span data-ttu-id="d0179-111">Opis</span><span class="sxs-lookup"><span data-stu-id="d0179-111">Description</span></span>|<span data-ttu-id="d0179-112">Składnia wyrażenia zapytania C#</span><span class="sxs-lookup"><span data-stu-id="d0179-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="d0179-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="d0179-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="d0179-114">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="d0179-114">All</span></span>|<span data-ttu-id="d0179-115">Określa, czy wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="d0179-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="d0179-116">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="d0179-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d0179-117">wszystkie</span><span class="sxs-lookup"><span data-stu-id="d0179-117">Any</span></span>|<span data-ttu-id="d0179-118">Określa, czy wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="d0179-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="d0179-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="d0179-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d0179-120">Zawiera</span><span class="sxs-lookup"><span data-stu-id="d0179-120">Contains</span></span>|<span data-ttu-id="d0179-121">Określa, czy sekwencja zawiera określony element.</span><span class="sxs-lookup"><span data-stu-id="d0179-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="d0179-122">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="d0179-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="d0179-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0179-123">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="d0179-124">Operatory standardowe zapytań — omówienie (C#)</span><span class="sxs-lookup"><span data-stu-id="d0179-124">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="d0179-125">Porady: dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="d0179-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../../csharp/programming-guide/linq-query-expressions/how-to-dynamically-specify-predicate-filters-at-runtime.md)  
 [<span data-ttu-id="d0179-126">Porady: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d0179-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
