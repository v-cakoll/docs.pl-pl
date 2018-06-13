---
title: Distinct — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 4b0ce12f6361d3dc6e5cc3601e96fc3a9bcf3841
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603980"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="d28a2-102">Distinct — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d28a2-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="d28a2-103">Ogranicza wartości bieżącą zmienną zakresu w celu wyeliminowania zduplikowanych wartości w klauzulach kolejne zapytania.</span><span class="sxs-lookup"><span data-stu-id="d28a2-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d28a2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d28a2-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="d28a2-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d28a2-105">Remarks</span></span>  
 <span data-ttu-id="d28a2-106">Można użyć `Distinct` klauzuli, aby powrócić do listy unikatowych elementów.</span><span class="sxs-lookup"><span data-stu-id="d28a2-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="d28a2-107">`Distinct` Klauzuli powoduje, że kwerenda Ignoruj wyników zduplikowane zapytanie.</span><span class="sxs-lookup"><span data-stu-id="d28a2-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="d28a2-108">`Distinct` Klauzuli dotyczy zduplikowane wartości dla wszystkich zwraca pola określone przez `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d28a2-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="d28a2-109">Jeśli nie `Select` określono klauzuli `Distinct` klauzuli jest stosowany do zmiennej zakresu dla zapytania, zostały zidentyfikowane w `From` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d28a2-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="d28a2-110">Jeśli zmienna zakresu nie jest typem niezmienne, zapytanie tylko zignoruje w wyniku zapytania, jeśli wszystkie elementy członkowskie tego typu są zgodne istniejącego wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="d28a2-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d28a2-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="d28a2-111">Example</span></span>  
 <span data-ttu-id="d28a2-112">Poniższe wyrażenie kwerendy łączy listę klientów i listę zamówień klienta.</span><span class="sxs-lookup"><span data-stu-id="d28a2-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="d28a2-113">`Distinct` Klauzula jest aby zwrócić listę nazw unikatowych klientów i kolejność daty.</span><span class="sxs-lookup"><span data-stu-id="d28a2-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/distinct-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d28a2-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d28a2-114">See Also</span></span>  
 [<span data-ttu-id="d28a2-115">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d28a2-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="d28a2-116">Zapytania</span><span class="sxs-lookup"><span data-stu-id="d28a2-116">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="d28a2-117">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="d28a2-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="d28a2-118">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="d28a2-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="d28a2-119">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="d28a2-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
