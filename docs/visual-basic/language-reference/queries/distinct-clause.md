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
ms.openlocfilehash: 00a2e52bd6669869bb2e25bc2857f1598da5763f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971250"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="35ead-102">Distinct — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35ead-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="35ead-103">Ogranicza wartości bieżącej zmiennej zakresu w celu wyeliminowania zduplikowanych wartości w klauzulach kolejnych zapytań.</span><span class="sxs-lookup"><span data-stu-id="35ead-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35ead-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="35ead-104">Syntax</span></span>  
  
```  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="35ead-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35ead-105">Remarks</span></span>  
 <span data-ttu-id="35ead-106">Możesz użyć `Distinct` klauzulę, aby powrócić do listy unikatowych elementów.</span><span class="sxs-lookup"><span data-stu-id="35ead-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="35ead-107">`Distinct` Klauzuli powoduje, że zapytanie, aby zignorować wyników zapytania zduplikowane.</span><span class="sxs-lookup"><span data-stu-id="35ead-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="35ead-108">`Distinct` Klauzuli dotyczy zduplikowane wartości dla wszystkich zwraca pola określone przez `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="35ead-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="35ead-109">Jeśli nie `Select` określono klauzulę `Distinct` klauzula jest stosowany do zmiennej zakresu zapytania w `From` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="35ead-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="35ead-110">Jeśli zmienna zakresu nie jest typem niezmienne, zapytanie tylko zignorować wynik zapytania, jeśli wszystkie elementy członkowskie tego typu odpowiada istniejącej wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="35ead-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35ead-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="35ead-111">Example</span></span>  
 <span data-ttu-id="35ead-112">Poniższe wyrażenie zapytania łączy listę klientów i listę zamówień klienta.</span><span class="sxs-lookup"><span data-stu-id="35ead-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="35ead-113">`Distinct` Klauzula jest aby zwrócić listę klientów unikatowe nazwy i kolejność daty.</span><span class="sxs-lookup"><span data-stu-id="35ead-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="35ead-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35ead-114">See also</span></span>
- [<span data-ttu-id="35ead-115">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35ead-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="35ead-116">Zapytania</span><span class="sxs-lookup"><span data-stu-id="35ead-116">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="35ead-117">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="35ead-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="35ead-118">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="35ead-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="35ead-119">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="35ead-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
