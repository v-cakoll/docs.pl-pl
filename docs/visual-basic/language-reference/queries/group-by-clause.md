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
ms.openlocfilehash: 04378d2c9a7e565343ff663997e2a3e61f04f9d2
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423579"
---
# <a name="group-by-clause-visual-basic"></a><span data-ttu-id="11133-102">Group By — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11133-102">Group By Clause (Visual Basic)</span></span>
<span data-ttu-id="11133-103">Grupuje elementy wyników zapytań.</span><span class="sxs-lookup"><span data-stu-id="11133-103">Groups the elements of a query result.</span></span> <span data-ttu-id="11133-104">Można również zastosowanie funkcji agregujących do każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="11133-104">Can also be used to apply aggregate functions to each group.</span></span> <span data-ttu-id="11133-105">W operacji grupowania opiera się na co najmniej jeden klucz.</span><span class="sxs-lookup"><span data-stu-id="11133-105">The grouping operation is based on one or more keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11133-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="11133-106">Syntax</span></span>  
  
```  
Group [ listField1 [, listField2 [...] ] By keyExp1 [, keyExp2 [...] ]  
  Into aggregateList  
```  
  
## <a name="parts"></a><span data-ttu-id="11133-107">Części</span><span class="sxs-lookup"><span data-stu-id="11133-107">Parts</span></span>  
  
- <span data-ttu-id="11133-108">`listField1`, `listField2`</span><span class="sxs-lookup"><span data-stu-id="11133-108">`listField1`, `listField2`</span></span>  
  
     <span data-ttu-id="11133-109">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="11133-109">Optional.</span></span> <span data-ttu-id="11133-110">Co najmniej jednego pola zmienna zapytania lub zmienne, które jawnie identyfikować pola, które mają zostać uwzględnione w wynikach zgrupowane.</span><span class="sxs-lookup"><span data-stu-id="11133-110">One or more fields of the query variable or variables that explicitly identify the fields to be included in the grouped result.</span></span> <span data-ttu-id="11133-111">Jeśli nie określono żadnych pól, w wyniku pogrupowanych znajdują się wszystkie pola zmienna zapytania lub zmienne.</span><span class="sxs-lookup"><span data-stu-id="11133-111">If no fields are specified, all fields of the query variable or variables are included in the grouped result.</span></span>  
  
- `keyExp1`  
  
     <span data-ttu-id="11133-112">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="11133-112">Required.</span></span> <span data-ttu-id="11133-113">Wyrażenie identyfikujące klawisz, aby użyć do określenia grupy elementów.</span><span class="sxs-lookup"><span data-stu-id="11133-113">An expression that identifies the key to use to determine the groups of elements.</span></span> <span data-ttu-id="11133-114">Można określić więcej niż jeden klucz w celu określenia klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="11133-114">You can specify more than one key to specify a composite key.</span></span>  
  
- `keyExp2`  
  
     <span data-ttu-id="11133-115">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="11133-115">Optional.</span></span> <span data-ttu-id="11133-116">Co najmniej jeden klucz dodatkowe, które są połączone z `keyExp1` można utworzyć klucza złożonego.</span><span class="sxs-lookup"><span data-stu-id="11133-116">One or more additional keys that are combined with `keyExp1` to create a composite key.</span></span>  
  
- `aggregateList`  
  
     <span data-ttu-id="11133-117">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="11133-117">Required.</span></span> <span data-ttu-id="11133-118">Co najmniej jednego wyrażenia, które określają, jak te grupy są agregowane.</span><span class="sxs-lookup"><span data-stu-id="11133-118">One or more expressions that identify how the groups are aggregated.</span></span> <span data-ttu-id="11133-119">Aby zidentyfikować nazwę elementu członkowskiego pogrupowane wyniki, należy użyć `Group` słowo kluczowe, które mogą znajdować się w jednej z następujących form:</span><span class="sxs-lookup"><span data-stu-id="11133-119">To identify a member name for the grouped results, use the `Group` keyword, which can be in either of the following forms:</span></span>  
  
    ```  
    Into Group  
    ```  
  
     <span data-ttu-id="11133-120">—lub—</span><span class="sxs-lookup"><span data-stu-id="11133-120">-or-</span></span>  
  
    ```  
    Into <alias> = Group  
    ```  
  
     <span data-ttu-id="11133-121">Może również zawierać funkcje agregujące do zastosowania w grupie.</span><span class="sxs-lookup"><span data-stu-id="11133-121">You can also include aggregate functions to apply to the group.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="11133-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11133-122">Remarks</span></span>  
 <span data-ttu-id="11133-123">Możesz użyć `Group By` klauzuli, aby przerwać wyników zapytania z grupy.</span><span class="sxs-lookup"><span data-stu-id="11133-123">You can use the `Group By` clause to break the results of a query into groups.</span></span> <span data-ttu-id="11133-124">Grupowanie jest oparte na klucz lub klucz złożony składający się z wielu kluczy.</span><span class="sxs-lookup"><span data-stu-id="11133-124">The grouping is based on a key or a composite key consisting of multiple keys.</span></span> <span data-ttu-id="11133-125">Elementy, które są skojarzone z takimi samymi wartościami klucza znajdują się w tej samej grupie.</span><span class="sxs-lookup"><span data-stu-id="11133-125">Elements that are associated with matching key values are included in the same group.</span></span>  
  
 <span data-ttu-id="11133-126">Możesz użyć `aggregateList` parametru `Into` klauzuli i `Group` — słowo kluczowe, aby zidentyfikować nazwę elementu członkowskiego, służący do odwoływać się do niej.</span><span class="sxs-lookup"><span data-stu-id="11133-126">You use the `aggregateList` parameter of the `Into` clause and the `Group` keyword to identify the member name that is used to reference the group.</span></span> <span data-ttu-id="11133-127">Możesz również uwzględnić w funkcjach agregujących `Into` klauzuli do obliczenia wartości pogrupowanych elementów.</span><span class="sxs-lookup"><span data-stu-id="11133-127">You can also include aggregate functions in the `Into` clause to compute values for the grouped elements.</span></span> <span data-ttu-id="11133-128">Aby uzyskać listę standardowych funkcji agregujących, zobacz [Aggregate — klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span><span class="sxs-lookup"><span data-stu-id="11133-128">For a list of standard aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="11133-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="11133-129">Example</span></span>  
 <span data-ttu-id="11133-130">Poniższy przykład kodu grupuje listę klientów, na podstawie ich lokalizacji (kraj/region) i zapewnia liczenie klientom w każdej grupie.</span><span class="sxs-lookup"><span data-stu-id="11133-130">The following code example groups a list of customers based on their location (country/region) and provides a count of the customers in each group.</span></span> <span data-ttu-id="11133-131">Wyniki są uporządkowane według nazwy kraju/regionu.</span><span class="sxs-lookup"><span data-stu-id="11133-131">The results are ordered by country/region name.</span></span> <span data-ttu-id="11133-132">Pogrupowane wyniki są uporządkowane według nazwy miasta.</span><span class="sxs-lookup"><span data-stu-id="11133-132">The grouped results are ordered by city name.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="11133-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11133-133">See also</span></span>

- [<span data-ttu-id="11133-134">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="11133-134">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="11133-135">Zapytania</span><span class="sxs-lookup"><span data-stu-id="11133-135">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="11133-136">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="11133-136">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="11133-137">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="11133-137">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="11133-138">Order By, klauzula</span><span class="sxs-lookup"><span data-stu-id="11133-138">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="11133-139">Klauzula Aggregate</span><span class="sxs-lookup"><span data-stu-id="11133-139">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="11133-140">Klauzula Group Join</span><span class="sxs-lookup"><span data-stu-id="11133-140">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
