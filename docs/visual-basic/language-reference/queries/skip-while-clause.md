---
title: Skip While — Klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 47703e445865435f5bf5312c3fe41833ac21aa3f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333143"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="a0690-102">Skip While — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0690-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="a0690-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span><span class="sxs-lookup"><span data-stu-id="a0690-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0690-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0690-104">Syntax</span></span>  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="a0690-105">Części</span><span class="sxs-lookup"><span data-stu-id="a0690-105">Parts</span></span>  
  
|<span data-ttu-id="a0690-106">Termin</span><span class="sxs-lookup"><span data-stu-id="a0690-106">Term</span></span>|<span data-ttu-id="a0690-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="a0690-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="a0690-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a0690-108">Required.</span></span> <span data-ttu-id="a0690-109">An expression that represents a condition to test elements for.</span><span class="sxs-lookup"><span data-stu-id="a0690-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="a0690-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="a0690-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0690-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0690-111">Remarks</span></span>  
 <span data-ttu-id="a0690-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span><span class="sxs-lookup"><span data-stu-id="a0690-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="a0690-113">After `expression` returns `false`, the query returns all the remaining elements.</span><span class="sxs-lookup"><span data-stu-id="a0690-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="a0690-114">The `expression` is ignored for the remaining results.</span><span class="sxs-lookup"><span data-stu-id="a0690-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="a0690-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span><span class="sxs-lookup"><span data-stu-id="a0690-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="a0690-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span><span class="sxs-lookup"><span data-stu-id="a0690-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="a0690-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span><span class="sxs-lookup"><span data-stu-id="a0690-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="a0690-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span><span class="sxs-lookup"><span data-stu-id="a0690-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0690-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0690-119">Example</span></span>  
 <span data-ttu-id="a0690-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span><span class="sxs-lookup"><span data-stu-id="a0690-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="a0690-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0690-121">See also</span></span>

- [<span data-ttu-id="a0690-122">Introduction to LINQ in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a0690-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="a0690-123">Zapytania</span><span class="sxs-lookup"><span data-stu-id="a0690-123">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="a0690-124">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="a0690-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="a0690-125">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="a0690-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="a0690-126">Skip, klauzula</span><span class="sxs-lookup"><span data-stu-id="a0690-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="a0690-127">Take While, klauzula</span><span class="sxs-lookup"><span data-stu-id="a0690-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="a0690-128">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="a0690-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
