---
title: Operacje kwantyfikatora (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5c931e0971a2ae7970415905be8772a64a82ee39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635486"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="562ac-102">Operacje kwantyfikatora (C#)</span><span class="sxs-lookup"><span data-stu-id="562ac-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="562ac-103">Operacje kwantyfikatora <xref:System.Boolean> zwraca wartość, która wskazuje, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="562ac-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="562ac-104">Na poniższej ilustracji przedstawiono dwie różne operacje kwantyfikatora na dwóch różnych sekwencji źródłowych.</span><span class="sxs-lookup"><span data-stu-id="562ac-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="562ac-105">Pierwsza operacja pyta, czy jeden lub więcej elementów to znak "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="562ac-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="562ac-106">Druga operacja pyta, czy wszystkie elementy są znakiem "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="562ac-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operacje kwantyfikatora LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="562ac-108">Standardowe metody operatora kwerendy, które wykonują operacje kwantyfikatora są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="562ac-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="562ac-109">Metody</span><span class="sxs-lookup"><span data-stu-id="562ac-109">Methods</span></span>  
  
|<span data-ttu-id="562ac-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="562ac-110">Method Name</span></span>|<span data-ttu-id="562ac-111">Opis</span><span class="sxs-lookup"><span data-stu-id="562ac-111">Description</span></span>|<span data-ttu-id="562ac-112">Składnia wyrażenia kwerendy c#</span><span class="sxs-lookup"><span data-stu-id="562ac-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="562ac-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="562ac-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="562ac-114">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="562ac-114">All</span></span>|<span data-ttu-id="562ac-115">Określa, czy wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="562ac-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="562ac-116">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="562ac-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="562ac-117">Dowolne</span><span class="sxs-lookup"><span data-stu-id="562ac-117">Any</span></span>|<span data-ttu-id="562ac-118">Określa, czy wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="562ac-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="562ac-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="562ac-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="562ac-120">Contains</span><span class="sxs-lookup"><span data-stu-id="562ac-120">Contains</span></span>|<span data-ttu-id="562ac-121">Określa, czy sekwencja zawiera określony element.</span><span class="sxs-lookup"><span data-stu-id="562ac-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="562ac-122">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="562ac-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="562ac-123">Przykłady składni wyrażenia kwerendy</span><span class="sxs-lookup"><span data-stu-id="562ac-123">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="562ac-124">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="562ac-124">All</span></span>  
<span data-ttu-id="562ac-125">W poniższym `All` przykładzie użyto, aby sprawdzić, czy wszystkie ciągi mają określoną długość.</span><span class="sxs-lookup"><span data-stu-id="562ac-125">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="562ac-126">Dowolne</span><span class="sxs-lookup"><span data-stu-id="562ac-126">Any</span></span>  
<span data-ttu-id="562ac-127">W poniższym `Any` przykładzie użyto, aby sprawdzić, czy wszystkie ciągi są uruchamiane z "o".</span><span class="sxs-lookup"><span data-stu-id="562ac-127">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="562ac-128">Contains</span><span class="sxs-lookup"><span data-stu-id="562ac-128">Contains</span></span>  
<span data-ttu-id="562ac-129">W poniższym `Contains` przykładzie użyto do sprawdzenia tablicy mają określony element.</span><span class="sxs-lookup"><span data-stu-id="562ac-129">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="562ac-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="562ac-130">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="562ac-131">Omówienie standardowych operatorów zapytań (C#)</span><span class="sxs-lookup"><span data-stu-id="562ac-131">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="562ac-132">Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="562ac-132">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="562ac-133">Jak wysyłać zapytania do zdań zawierających określony zestaw słów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="562ac-133">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
