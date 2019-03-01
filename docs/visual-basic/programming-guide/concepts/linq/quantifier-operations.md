---
title: Operacje kwantyfikatora (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 966bc958d6feac77ebe1c229bfe5dbb993031676
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976749"
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="cf9f9-102">Operacje kwantyfikatora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf9f9-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="cf9f9-103">Operacje kwantyfikatora zwracają <xref:System.Boolean> wartość, która wskazuje, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="cf9f9-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="cf9f9-104">Poniższa ilustracja przedstawia dwie operacje kwantyfikatora różnych na dwie sekwencje innego źródła.</span><span class="sxs-lookup"><span data-stu-id="cf9f9-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="cf9f9-105">Pierwszą operacją pytaniem, jeśli co najmniej jeden z elementów jest znak "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="cf9f9-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="cf9f9-106">Pyta drugą operację, jeśli wszystkie elementy są znak "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="cf9f9-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="cf9f9-107">![Operacje kwantyfikatora LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="cf9f9-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="cf9f9-108">Metody standardowego operatora zapytań, które wykonują operacje kwantyfikatora są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="cf9f9-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cf9f9-109">Metody</span><span class="sxs-lookup"><span data-stu-id="cf9f9-109">Methods</span></span>  
  
|<span data-ttu-id="cf9f9-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="cf9f9-110">Method Name</span></span>|<span data-ttu-id="cf9f9-111">Opis</span><span class="sxs-lookup"><span data-stu-id="cf9f9-111">Description</span></span>|<span data-ttu-id="cf9f9-112">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cf9f9-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="cf9f9-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="cf9f9-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="cf9f9-114">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="cf9f9-114">All</span></span>|<span data-ttu-id="cf9f9-115">Określa, czy wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="cf9f9-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="cf9f9-116">Dowolne</span><span class="sxs-lookup"><span data-stu-id="cf9f9-116">Any</span></span>|<span data-ttu-id="cf9f9-117">Określa, czy dowolne elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="cf9f9-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="cf9f9-118">Zawiera</span><span class="sxs-lookup"><span data-stu-id="cf9f9-118">Contains</span></span>|<span data-ttu-id="cf9f9-119">Określa, czy sekwencja zawiera określony element.</span><span class="sxs-lookup"><span data-stu-id="cf9f9-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="cf9f9-120">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="cf9f9-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="cf9f9-121">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="cf9f9-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="cf9f9-122">Użyj tych przykładach `Aggregate` klauzuli w języku Visual Basic w ramach warunek filtrowania w zapytaniu programu LINQ.</span><span class="sxs-lookup"><span data-stu-id="cf9f9-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="cf9f9-123">W poniższym przykładzie użyto `Aggregate` klauzuli i <xref:System.Linq.Enumerable.All%2A> metodę rozszerzenia, aby zwrócić ze zbioru osób, których zwierzęta są wszystkie starsze niż określona wieku.</span><span class="sxs-lookup"><span data-stu-id="cf9f9-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#1)]  
  
 <span data-ttu-id="cf9f9-124">W następnym przykładzie użyto `Aggregate` klauzuli i <xref:System.Linq.Enumerable.Any%2A> metodę rozszerzenia, aby zwrócić z kolekcji, te osoby, które mają co najmniej jeden domowe, która jest starsza niż określona wieku.</span><span class="sxs-lookup"><span data-stu-id="cf9f9-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/CsLINQAnyAll/VB/AnyAll.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="cf9f9-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf9f9-125">See also</span></span>
- <xref:System.Linq>
- [<span data-ttu-id="cf9f9-126">Omówienie operatorów standardowej kwerendy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf9f9-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="cf9f9-127">Klauzula Aggregate</span><span class="sxs-lookup"><span data-stu-id="cf9f9-127">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="cf9f9-128">Instrukcje: Zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf9f9-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
