---
title: Take — Klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 3082954ef84560ccb70f7a47cd3532f622829392
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349644"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="a2c7b-102">Take — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2c7b-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="a2c7b-103">Returns a specified number of contiguous elements from the start of a collection.</span><span class="sxs-lookup"><span data-stu-id="a2c7b-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2c7b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2c7b-104">Syntax</span></span>  
  
```vb  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="a2c7b-105">Części</span><span class="sxs-lookup"><span data-stu-id="a2c7b-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="a2c7b-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a2c7b-106">Required.</span></span> <span data-ttu-id="a2c7b-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span><span class="sxs-lookup"><span data-stu-id="a2c7b-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2c7b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2c7b-108">Remarks</span></span>  
 <span data-ttu-id="a2c7b-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span><span class="sxs-lookup"><span data-stu-id="a2c7b-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="a2c7b-110">The number of elements to include is specified by the `count` parameter.</span><span class="sxs-lookup"><span data-stu-id="a2c7b-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="a2c7b-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span><span class="sxs-lookup"><span data-stu-id="a2c7b-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="a2c7b-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span><span class="sxs-lookup"><span data-stu-id="a2c7b-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="a2c7b-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span><span class="sxs-lookup"><span data-stu-id="a2c7b-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="a2c7b-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span><span class="sxs-lookup"><span data-stu-id="a2c7b-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="a2c7b-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="a2c7b-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="a2c7b-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span><span class="sxs-lookup"><span data-stu-id="a2c7b-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2c7b-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="a2c7b-117">Example</span></span>  
 <span data-ttu-id="a2c7b-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span><span class="sxs-lookup"><span data-stu-id="a2c7b-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="a2c7b-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span><span class="sxs-lookup"><span data-stu-id="a2c7b-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a2c7b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2c7b-120">See also</span></span>

- [<span data-ttu-id="a2c7b-121">Introduction to LINQ in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a2c7b-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="a2c7b-122">Zapytania</span><span class="sxs-lookup"><span data-stu-id="a2c7b-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="a2c7b-123">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="a2c7b-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="a2c7b-124">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="a2c7b-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="a2c7b-125">Order By, klauzula</span><span class="sxs-lookup"><span data-stu-id="a2c7b-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="a2c7b-126">Take While, klauzula</span><span class="sxs-lookup"><span data-stu-id="a2c7b-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="a2c7b-127">Skip, klauzula</span><span class="sxs-lookup"><span data-stu-id="a2c7b-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
