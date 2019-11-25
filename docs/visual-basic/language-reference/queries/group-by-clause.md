---
title: Group by — Klauzula
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
ms.openlocfilehash: 87080254ad5d237a593f0c35e7c3fdaef3a8ad59
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350473"
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="af80a-102">Group By — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af80a-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="af80a-103">Groups the elements of a query result.</span><span class="sxs-lookup"><span data-stu-id="af80a-103">Groups the elements of a query result.</span></span> <span data-ttu-id="af80a-104">Can also be used to apply aggregate functions to each group.</span><span class="sxs-lookup"><span data-stu-id="af80a-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="af80a-105">The grouping operation is based on one or more keys.</span><span class="sxs-lookup"><span data-stu-id="af80a-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af80a-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="af80a-106">Syntax</span></span>  
  
```vb  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="af80a-107">Części</span><span class="sxs-lookup"><span data-stu-id="af80a-107">Parts</span></span>  
  
- <span data-ttu-id="af80a-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="af80a-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="af80a-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="af80a-109">Optional.</span></span> <span data-ttu-id="af80a-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span><span class="sxs-lookup"><span data-stu-id="af80a-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="af80a-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span><span class="sxs-lookup"><span data-stu-id="af80a-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
- `keyExp1`  
  
     <span data-ttu-id="af80a-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="af80a-112">Required.</span></span> <span data-ttu-id="af80a-113">An expression that identifies the key to use to determine the groups of elements.</span><span class="sxs-lookup"><span data-stu-id="af80a-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="af80a-114">You can specify more than one key to specify a composite key.</span><span class="sxs-lookup"><span data-stu-id="af80a-114">You can specify more than one key to specify a composite key.</span></span>  
  
- `keyExp2`  
  
     <span data-ttu-id="af80a-115">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="af80a-115">Optional.</span></span> <span data-ttu-id="af80a-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span><span class="sxs-lookup"><span data-stu-id="af80a-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
- `aggregateList`  
  
     <span data-ttu-id="af80a-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="af80a-117">Required.</span></span> <span data-ttu-id="af80a-118">One or more expressions that identify how the groups are aggregated.</span><span class="sxs-lookup"><span data-stu-id="af80a-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="af80a-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span><span class="sxs-lookup"><span data-stu-id="af80a-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```vb  
    Into Group  
    ```  
  
     <span data-ttu-id="af80a-120">—lub—</span><span class="sxs-lookup"><span data-stu-id="af80a-120">-or-</span></span>  
  
    ```vb  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="af80a-121">You can also include aggregate functions to apply to the group.</span><span class="sxs-lookup"><span data-stu-id="af80a-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af80a-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="af80a-122">Remarks</span></span>  
 <span data-ttu-id="af80a-123">You can use the `Group By` clause to break the results of a query into groups.</span><span class="sxs-lookup"><span data-stu-id="af80a-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="af80a-124">The grouping is based on a key or a composite key consisting of multiple keys.</span><span class="sxs-lookup"><span data-stu-id="af80a-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="af80a-125">Elements that are associated with matching key values are included in the same group.</span><span class="sxs-lookup"><span data-stu-id="af80a-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="af80a-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span><span class="sxs-lookup"><span data-stu-id="af80a-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="af80a-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span><span class="sxs-lookup"><span data-stu-id="af80a-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="af80a-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="af80a-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="af80a-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="af80a-129">Example</span></span>  
 <span data-ttu-id="af80a-130">The following code example groups a list of customers based on their location (country/region) and provides a count of the customers in each group.</span><span class="sxs-lookup"><span data-stu-id="af80a-130">The following code example groups a list of customers based on their location (country/region) and provides a count of the customers in each group.</span></span> <span data-ttu-id="af80a-131">The results are ordered by country/region name.</span><span class="sxs-lookup"><span data-stu-id="af80a-131">The results are ordered by country/region name.</span></span> <span data-ttu-id="af80a-132">The grouped results are ordered by city name.</span><span class="sxs-lookup"><span data-stu-id="af80a-132">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="af80a-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="af80a-133">See also</span></span>

- [<span data-ttu-id="af80a-134">Introduction to LINQ in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af80a-134">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="af80a-135">Zapytania</span><span class="sxs-lookup"><span data-stu-id="af80a-135">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="af80a-136">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="af80a-136">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="af80a-137">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="af80a-137">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="af80a-138">Order By, klauzula</span><span class="sxs-lookup"><span data-stu-id="af80a-138">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="af80a-139">Aggregate, klauzula</span><span class="sxs-lookup"><span data-stu-id="af80a-139">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="af80a-140">Group Join, klauzula</span><span class="sxs-lookup"><span data-stu-id="af80a-140">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
