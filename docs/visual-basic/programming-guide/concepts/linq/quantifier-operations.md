---
title: Operacje kwantyfikatora (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ae1a2b73-503c-4f4b-a3fd-31b5adbee67c
ms.openlocfilehash: 0a0a5fae35a14ab6451f2f56fb2eedd92ac437e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="quantifier-operations-visual-basic"></a><span data-ttu-id="2b7c0-102">Operacje kwantyfikatora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b7c0-102">Quantifier Operations (Visual Basic)</span></span>
<span data-ttu-id="2b7c0-103">Operacje kwantyfikatora zwracać <xref:System.Boolean> wartość, która wskazuje, czy niektóre lub wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="2b7c0-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="2b7c0-104">Na poniższej ilustracji przedstawiono dwie operacje kwantyfikatora różnych na dwóch różnych źródeł sekwencji.</span><span class="sxs-lookup"><span data-stu-id="2b7c0-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="2b7c0-105">Pierwszą operacją zapyta, jeśli co najmniej jeden z elementów jest znak "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="2b7c0-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="2b7c0-106">Druga operacja zapyta, czy wszystkie elementy są znaków "A", a wynik jest `true`.</span><span class="sxs-lookup"><span data-stu-id="2b7c0-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 <span data-ttu-id="2b7c0-107">![Operacje kwantyfikatora LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span><span class="sxs-lookup"><span data-stu-id="2b7c0-107">![LINQ Quantifier Operations](../../../../csharp/programming-guide/concepts/linq/media/linq_quantifier.png "LINQ_Quantifier")</span></span>  
  
 <span data-ttu-id="2b7c0-108">Metody — operator standardowe zapytań, które wykonują operacje kwantyfikatora są wymienione w poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="2b7c0-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2b7c0-109">Metody</span><span class="sxs-lookup"><span data-stu-id="2b7c0-109">Methods</span></span>  
  
|<span data-ttu-id="2b7c0-110">Nazwa metody</span><span class="sxs-lookup"><span data-stu-id="2b7c0-110">Method Name</span></span>|<span data-ttu-id="2b7c0-111">Opis</span><span class="sxs-lookup"><span data-stu-id="2b7c0-111">Description</span></span>|<span data-ttu-id="2b7c0-112">Składnia wyrażeń języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b7c0-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="2b7c0-113">Więcej informacji</span><span class="sxs-lookup"><span data-stu-id="2b7c0-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="2b7c0-114">Wszystkie</span><span class="sxs-lookup"><span data-stu-id="2b7c0-114">All</span></span>|<span data-ttu-id="2b7c0-115">Określa, czy wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="2b7c0-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into All(…)`|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2b7c0-116">wszystkie</span><span class="sxs-lookup"><span data-stu-id="2b7c0-116">Any</span></span>|<span data-ttu-id="2b7c0-117">Określa, czy wszystkie elementy w sekwencji spełniają warunek.</span><span class="sxs-lookup"><span data-stu-id="2b7c0-117">Determines whether any elements in a sequence satisfy a condition.</span></span>|`Aggregate … In … Into Any()`|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="2b7c0-118">Zawiera</span><span class="sxs-lookup"><span data-stu-id="2b7c0-118">Contains</span></span>|<span data-ttu-id="2b7c0-119">Określa, czy sekwencja zawiera określony element.</span><span class="sxs-lookup"><span data-stu-id="2b7c0-119">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="2b7c0-120">Nie dotyczy.</span><span class="sxs-lookup"><span data-stu-id="2b7c0-120">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="2b7c0-121">Przykłady składni wyrażeń zapytania</span><span class="sxs-lookup"><span data-stu-id="2b7c0-121">Query Expression Syntax Examples</span></span>  
 <span data-ttu-id="2b7c0-122">Użyj tych przykładów `Aggregate` klauzuli w języku Visual Basic w ramach warunek filtrowania w zapytaniu składnika LINQ.</span><span class="sxs-lookup"><span data-stu-id="2b7c0-122">These examples use the `Aggregate` clause in Visual Basic as part of the filtering condition in a LINQ query.</span></span>  
  
 <span data-ttu-id="2b7c0-123">W poniższym przykładzie użyto `Aggregate` klauzuli i <xref:System.Linq.Enumerable.All%2A> — metoda rozszerzenia do zwrócenia z kolekcji osoby, których zwierząt domowych są wszystkie starsze niż określony okres ważności.</span><span class="sxs-lookup"><span data-stu-id="2b7c0-123">The following example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.All%2A> extension method to return from a collection those people whose pets are all older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#1](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_1.vb)]  
  
 <span data-ttu-id="2b7c0-124">W następnym przykładzie użyto `Aggregate` klauzuli i <xref:System.Linq.Enumerable.Any%2A> — metoda rozszerzenia do zwrócenia z kolekcji tych osób, które mają co najmniej jeden domowe, która jest starsza niż określony okres ważności.</span><span class="sxs-lookup"><span data-stu-id="2b7c0-124">The next example uses the `Aggregate` clause and the <xref:System.Linq.Enumerable.Any%2A> extension method to return from a collection those people who have at least one pet that is older than a specified age.</span></span>  
  
 [!code-vb[CsLINQAnyAll#2](../../../../visual-basic/programming-guide/concepts/linq/codesnippet/VisualBasic/quantifier-operations_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2b7c0-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b7c0-125">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="2b7c0-126">Operatory standardowe zapytań — omówienie (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b7c0-126">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="2b7c0-127">Aggregate, klauzula</span><span class="sxs-lookup"><span data-stu-id="2b7c0-127">Aggregate Clause</span></span>](../../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="2b7c0-128">Porady: zapytanie o zdania zawierające określony zestaw wyrazów (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2b7c0-128">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-sentences-that-contain-a-specified-set-of-words.md)
