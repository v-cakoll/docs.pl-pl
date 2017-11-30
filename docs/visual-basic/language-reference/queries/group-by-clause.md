---
title: "Group By — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b719bfa2ebe4c324acf82a03e215e481283845fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="cb784-102">Group By — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb784-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="cb784-103">Grupuje elementy w wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="cb784-103">Groups the elements of a query result.</span></span> <span data-ttu-id="cb784-104">Można również zastosować funkcje agregujące do każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="cb784-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="cb784-105">Operacja grupowania jest oparta na co najmniej jeden klucz.</span><span class="sxs-lookup"><span data-stu-id="cb784-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb784-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cb784-106">Syntax</span></span>  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="cb784-107">Części</span><span class="sxs-lookup"><span data-stu-id="cb784-107">Parts</span></span>  
  
-   <span data-ttu-id="cb784-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="cb784-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="cb784-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cb784-109">Optional.</span></span> <span data-ttu-id="cb784-110">Co najmniej jedno pole zmienną zapytania lub zmiennych, które jawnie określić pola do uwzględnienia w wyniku grupowanych.</span><span class="sxs-lookup"><span data-stu-id="cb784-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="cb784-111">Jeśli nie określono pól, wszystkie pola zmienną zapytania lub zmienne są uwzględnione w grupowanych wynik.</span><span class="sxs-lookup"><span data-stu-id="cb784-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
-   `keyExp1`  
  
     <span data-ttu-id="cb784-112">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="cb784-112">Required.</span></span> <span data-ttu-id="cb784-113">Wyrażenie identyfikujące klucz do użycia w celu określenia grupy elementów.</span><span class="sxs-lookup"><span data-stu-id="cb784-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="cb784-114">Można określić więcej niż jednego klucza do określenia klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="cb784-114">You can specify more than one key to specify a composite key.</span></span>  
  
-   `keyExp2`  
  
     <span data-ttu-id="cb784-115">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cb784-115">Optional.</span></span> <span data-ttu-id="cb784-116">Jeden lub więcej dodatkowych kluczy, które są połączone z `keyExp1` można utworzyć klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="cb784-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
-   `aggregateList`  
  
     <span data-ttu-id="cb784-117">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="cb784-117">Required.</span></span> <span data-ttu-id="cb784-118">Co najmniej jednego wyrażenia, które identyfikują agregowaniem grup.</span><span class="sxs-lookup"><span data-stu-id="cb784-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="cb784-119">Aby zidentyfikować nazwę elementu członkowskiego grupowanych wyników, należy użyć `Group` — słowo kluczowe, które mogą być w jednym z następujących formatów:</span><span class="sxs-lookup"><span data-stu-id="cb784-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```  
    Into Group  
    ```  
  
     <span data-ttu-id="cb784-120">—lub—</span><span class="sxs-lookup"><span data-stu-id="cb784-120">-or-</span></span>  
  
    ```  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="cb784-121">Możesz również uwzględnić funkcje agregujące do zastosowania do grupy.</span><span class="sxs-lookup"><span data-stu-id="cb784-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb784-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cb784-122">Remarks</span></span>  
 <span data-ttu-id="cb784-123">Można użyć `Group By` klauzuli można przerwać wyników zapytania w grupach.</span><span class="sxs-lookup"><span data-stu-id="cb784-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="cb784-124">Grupowanie jest oparta na klucz lub klucz złożony składające się z wielu kluczy.</span><span class="sxs-lookup"><span data-stu-id="cb784-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="cb784-125">Elementy, które są skojarzone z takimi samymi wartościami klucza znajdują się w tej samej grupie.</span><span class="sxs-lookup"><span data-stu-id="cb784-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="cb784-126">Możesz użyć `aggregateList` parametr `Into` klauzuli i `Group` — słowo kluczowe, aby zidentyfikować nazwę elementu członkowskiego używanego w taki sposób, aby odwołać się do grupy.</span><span class="sxs-lookup"><span data-stu-id="cb784-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="cb784-127">Możesz również uwzględnić w funkcji agregujących `Into` klauzuli do obliczenia wartości pogrupowanych elementów.</span><span class="sxs-lookup"><span data-stu-id="cb784-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="cb784-128">Aby uzyskać listę standardowych funkcji agregujących, zobacz [Aggregate — klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="cb784-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb784-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb784-129">Example</span></span>  
 <span data-ttu-id="cb784-130">Poniższy przykład kodu grupuje listę klientów, na podstawie ich lokalizacji (kraj) i zapewnia liczenie klienci w każdej grupie.</span><span class="sxs-lookup"><span data-stu-id="cb784-130">The following code example groups a list of customers based on their location (country) and provides a count of the customers in each group.</span></span> <span data-ttu-id="cb784-131">Wyniki są uporządkowane według nazwy kraju.</span><span class="sxs-lookup"><span data-stu-id="cb784-131">The results are ordered by country name.</span></span> <span data-ttu-id="cb784-132">Grupowanych wyniki są uporządkowane według nazwy miasta.</span><span class="sxs-lookup"><span data-stu-id="cb784-132">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-by-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="cb784-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb784-133">See Also</span></span>  
 [<span data-ttu-id="cb784-134">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cb784-134">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="cb784-135">Zapytania</span><span class="sxs-lookup"><span data-stu-id="cb784-135">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="cb784-136">SELECT — klauzula</span><span class="sxs-lookup"><span data-stu-id="cb784-136">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="cb784-137">Klauzula FROM</span><span class="sxs-lookup"><span data-stu-id="cb784-137">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="cb784-138">Order By — klauzula</span><span class="sxs-lookup"><span data-stu-id="cb784-138">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="cb784-139">AGGREGATE — klauzula</span><span class="sxs-lookup"><span data-stu-id="cb784-139">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="cb784-140">Group Join — klauzula</span><span class="sxs-lookup"><span data-stu-id="cb784-140">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
