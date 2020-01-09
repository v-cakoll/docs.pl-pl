---
title: Operacje kwantyfikatora (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5c931e0971a2ae7970415905be8772a64a82ee39
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635486"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="9ab84-102">Operacje kwantyfikatora (C#)</span><span class="sxs-lookup"><span data-stu-id="9ab84-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="9ab84-103">Operacje kwantyfikatora zwracają <xref:System.Boolean> wartość wskazującą, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="9ab84-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="9ab84-104">Na poniższej ilustracji przedstawiono dwa różne operacje kwantyfikatora dla dwóch różnych sekwencji źródłowych.</span><span class="sxs-lookup"><span data-stu-id="9ab84-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="9ab84-105">Pierwsza operacja pyta, czy co najmniej jeden element jest znakiem "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="9ab84-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="9ab84-106">Druga operacja pyta, czy wszystkie elementy są znakiem "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="9ab84-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operacje kwantyfikatora LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="9ab84-108">Standardowe metody operatorów zapytań, które wykonują operacje kwantyfikatora, są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="9ab84-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ab84-109">Metody</span><span class="sxs-lookup"><span data-stu-id="9ab84-109">Methods</span></span>  
  
|<span data-ttu-id="9ab84-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="9ab84-110">Method Name</span></span>|<span data-ttu-id="9ab84-111">Opis</span><span class="sxs-lookup"><span data-stu-id="9ab84-111">Description</span></span>|<span data-ttu-id="9ab84-112">C#Składnia wyrażenia zapytania</span><span class="sxs-lookup"><span data-stu-id="9ab84-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="9ab84-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="9ab84-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="9ab84-114">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="9ab84-114">All</span></span>|<span data-ttu-id="9ab84-115">Określa, czy wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="9ab84-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="9ab84-116">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="9ab84-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9ab84-117">Dowolne</span><span class="sxs-lookup"><span data-stu-id="9ab84-117">Any</span></span>|<span data-ttu-id="9ab84-118">Określa, czy dowolne elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="9ab84-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="9ab84-119">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="9ab84-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="9ab84-120">Zawiera</span><span class="sxs-lookup"><span data-stu-id="9ab84-120">Contains</span></span>|<span data-ttu-id="9ab84-121">Określa, czy sekwencja zawiera określony element.</span><span class="sxs-lookup"><span data-stu-id="9ab84-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="9ab84-122">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="9ab84-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="9ab84-123">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="9ab84-123">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="9ab84-124">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="9ab84-124">All</span></span>  
<span data-ttu-id="9ab84-125">Poniższy przykład używa `All`, aby sprawdzić, czy wszystkie ciągi mają określoną długość.</span><span class="sxs-lookup"><span data-stu-id="9ab84-125">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="9ab84-126">Dowolne</span><span class="sxs-lookup"><span data-stu-id="9ab84-126">Any</span></span>  
<span data-ttu-id="9ab84-127">Poniższy przykład używa `Any`, aby sprawdzić, czy wszystkie ciągi zaczynają się od "o".</span><span class="sxs-lookup"><span data-stu-id="9ab84-127">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="9ab84-128">Zawiera</span><span class="sxs-lookup"><span data-stu-id="9ab84-128">Contains</span></span>  
<span data-ttu-id="9ab84-129">Poniższy przykład używa `Contains`, aby sprawdzić, czy tablica zawiera określony element.</span><span class="sxs-lookup"><span data-stu-id="9ab84-129">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="9ab84-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ab84-130">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="9ab84-131">Standardowe operatory zapytań — OmówienieC#()</span><span class="sxs-lookup"><span data-stu-id="9ab84-131">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="9ab84-132">Dynamiczne określanie filtrów predykatów w środowisku uruchomieniowym</span><span class="sxs-lookup"><span data-stu-id="9ab84-132">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="9ab84-133">Jak wykonać zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="9ab84-133">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
