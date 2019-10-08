---
title: Group By — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupByInto
- vb.QueryGroupBy
- vb.QueryGroupRef
- vb.QueryGroupInto
- vb.QueryGroup
helpviewer_keywords:
- queries [Visual Basic], Group By
- Group By statement [Visual Basic]
- Group By clause [Visual Basic]
ms.assetid: b1b5dcea-6654-473b-a2db-01f7e4c265d7
ms.openlocfilehash: 8b3a480c226debc529c268e83437d15192592bd3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004753"
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="316a7-102">Group By — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="316a7-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="316a7-103">Grupuje elementy wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="316a7-103">Groups the elements of a query result.</span></span> <span data-ttu-id="316a7-104">Może również służyć do stosowania funkcji agregujących do każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="316a7-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="316a7-105">Operacja grupowania jest oparta na jednym lub większej liczbie kluczy.</span><span class="sxs-lookup"><span data-stu-id="316a7-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="316a7-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="316a7-106">Syntax</span></span>  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="316a7-107">Części</span><span class="sxs-lookup"><span data-stu-id="316a7-107">Parts</span></span>  
  
- <span data-ttu-id="316a7-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="316a7-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="316a7-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="316a7-109">Optional.</span></span> <span data-ttu-id="316a7-110">Co najmniej jedno pole zmiennej zapytania lub zmienne, które jawnie identyfikują pola, które mają być uwzględnione w zgrupowanym wyniku.</span><span class="sxs-lookup"><span data-stu-id="316a7-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="316a7-111">Jeśli nie określono żadnych pól, do pogrupowanego wyniku są uwzględniane wszystkie pola zmiennej zapytania lub zmiennych.</span><span class="sxs-lookup"><span data-stu-id="316a7-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
- `keyExp1`  
  
     <span data-ttu-id="316a7-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="316a7-112">Required.</span></span> <span data-ttu-id="316a7-113">Wyrażenie, które identyfikuje klucz używany do określenia grup elementów.</span><span class="sxs-lookup"><span data-stu-id="316a7-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="316a7-114">Można określić więcej niż jeden klucz do określenia klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="316a7-114">You can specify more than one key to specify a composite key.</span></span>  
  
- `keyExp2`  
  
     <span data-ttu-id="316a7-115">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="316a7-115">Optional.</span></span> <span data-ttu-id="316a7-116">Jeden lub więcej kluczy, które są połączone z `keyExp1` w celu utworzenia klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="316a7-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
- `aggregateList`  
  
     <span data-ttu-id="316a7-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="316a7-117">Required.</span></span> <span data-ttu-id="316a7-118">Co najmniej jedno wyrażenie określające sposób agregowania grup.</span><span class="sxs-lookup"><span data-stu-id="316a7-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="316a7-119">Aby zidentyfikować nazwę elementu członkowskiego pogrupowanych wyników, użyj słowa kluczowego `Group`, które może znajdować się w jednej z następujących form:</span><span class="sxs-lookup"><span data-stu-id="316a7-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```vb  
    Into Group  
    ```  
  
     <span data-ttu-id="316a7-120">—lub—</span><span class="sxs-lookup"><span data-stu-id="316a7-120">-or-</span></span>  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="316a7-121">Można również dołączyć funkcje agregujące, które mają zostać zastosowane do grupy.</span><span class="sxs-lookup"><span data-stu-id="316a7-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="316a7-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="316a7-122">Remarks</span></span>  
 <span data-ttu-id="316a7-123">Można użyć klauzuli `Group By`, aby przerwać wyniki zapytania do grup.</span><span class="sxs-lookup"><span data-stu-id="316a7-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="316a7-124">Grupowanie jest oparte na kluczu lub złożonym kluczu składającym się z wielu kluczy.</span><span class="sxs-lookup"><span data-stu-id="316a7-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="316a7-125">Elementy, które są skojarzone z pasującymi wartościami klucza, są uwzględniane w tej samej grupie.</span><span class="sxs-lookup"><span data-stu-id="316a7-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="316a7-126">Aby określić nazwę elementu członkowskiego, który jest używany do odwoływania się do grupy, należy użyć parametru `aggregateList` klauzuli `Into` i słowa kluczowego `Group`.</span><span class="sxs-lookup"><span data-stu-id="316a7-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="316a7-127">Możesz również uwzględnić funkcje agregujące w klauzuli `Into`, aby obliczyć wartości dla zgrupowanych elementów.</span><span class="sxs-lookup"><span data-stu-id="316a7-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="316a7-128">Aby zapoznać się z listą standardowych funkcji agregujących, zobacz [klauzula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="316a7-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="316a7-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="316a7-129">Example</span></span>  
 <span data-ttu-id="316a7-130">Poniższy przykład kodu grupuje listę klientów w oparciu o ich lokalizację (kraj/region) i udostępnia liczbę klientów w każdej grupie.</span><span class="sxs-lookup"><span data-stu-id="316a7-130">The following code example groups a list of customers based on their location (country/region) and provides a count of the customers in each group.</span></span> <span data-ttu-id="316a7-131">Wyniki są uporządkowane według nazwy kraju/regionu.</span><span class="sxs-lookup"><span data-stu-id="316a7-131">The results are ordered by country/region name.</span></span> <span data-ttu-id="316a7-132">Pogrupowane wyniki są uporządkowane według nazwy miasta.</span><span class="sxs-lookup"><span data-stu-id="316a7-132">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="316a7-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="316a7-133">See also</span></span>

- [<span data-ttu-id="316a7-134">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="316a7-134">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="316a7-135">Zapytania</span><span class="sxs-lookup"><span data-stu-id="316a7-135">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="316a7-136">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="316a7-136">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="316a7-137">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="316a7-137">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="316a7-138">Order By, klauzula</span><span class="sxs-lookup"><span data-stu-id="316a7-138">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="316a7-139">Aggregate, klauzula</span><span class="sxs-lookup"><span data-stu-id="316a7-139">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="316a7-140">Group Join, klauzula</span><span class="sxs-lookup"><span data-stu-id="316a7-140">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
