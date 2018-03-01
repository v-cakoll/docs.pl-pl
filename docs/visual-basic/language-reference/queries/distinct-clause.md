---
title: "Distinct — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ed92d5d601c1ec329728346ac881c4fa2bad8aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="4a1a4-102">Distinct — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4a1a4-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="4a1a4-103">Ogranicza wartości bieżącą zmienną zakresu w celu wyeliminowania zduplikowanych wartości w klauzulach kolejne zapytania.</span><span class="sxs-lookup"><span data-stu-id="4a1a4-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a1a4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a1a4-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="4a1a4-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a1a4-105">Remarks</span></span>  
 <span data-ttu-id="4a1a4-106">Można użyć `Distinct` klauzuli, aby powrócić do listy unikatowych elementów.</span><span class="sxs-lookup"><span data-stu-id="4a1a4-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="4a1a4-107">`Distinct` Klauzuli powoduje, że kwerenda Ignoruj wyników zduplikowane zapytanie.</span><span class="sxs-lookup"><span data-stu-id="4a1a4-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="4a1a4-108">`Distinct` Klauzuli dotyczy zduplikowane wartości dla wszystkich zwraca pola określone przez `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="4a1a4-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="4a1a4-109">Jeśli nie `Select` określono klauzuli `Distinct` klauzuli jest stosowany do zmiennej zakresu dla zapytania, zostały zidentyfikowane w `From` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="4a1a4-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="4a1a4-110">Jeśli zmienna zakresu nie jest typem niezmienne, zapytanie tylko zignoruje w wyniku zapytania, jeśli wszystkie elementy członkowskie tego typu są zgodne istniejącego wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="4a1a4-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a1a4-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a1a4-111">Example</span></span>  
 <span data-ttu-id="4a1a4-112">Poniższe wyrażenie kwerendy łączy listę klientów i listę zamówień klienta.</span><span class="sxs-lookup"><span data-stu-id="4a1a4-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="4a1a4-113">`Distinct` Klauzula jest aby zwrócić listę nazw unikatowych klientów i kolejność daty.</span><span class="sxs-lookup"><span data-stu-id="4a1a4-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4a1a4-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a1a4-114">See Also</span></span>  
 [<span data-ttu-id="4a1a4-115">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a1a4-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="4a1a4-116">Zapytania</span><span class="sxs-lookup"><span data-stu-id="4a1a4-116">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="4a1a4-117">Klauzula FROM</span><span class="sxs-lookup"><span data-stu-id="4a1a4-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="4a1a4-118">SELECT — klauzula</span><span class="sxs-lookup"><span data-stu-id="4a1a4-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="4a1a4-119">Gdy klauzula</span><span class="sxs-lookup"><span data-stu-id="4a1a4-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
