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
ms.openlocfilehash: e8d3e38261a04c4d29faab351d24d6710413b09a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004788"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="3652b-102">Distinct — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3652b-102">Distinct Clause (Visual Basic)</span></span>
<span data-ttu-id="3652b-103">Ogranicza wartości bieżącej zmiennej zakresu w celu wyeliminowania zduplikowanych wartości w kolejnych klauzulach zapytania.</span><span class="sxs-lookup"><span data-stu-id="3652b-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3652b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3652b-104">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="3652b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3652b-105">Remarks</span></span>  
 <span data-ttu-id="3652b-106">Można użyć klauzuli `Distinct`, aby zwrócić listę unikatowych elementów.</span><span class="sxs-lookup"><span data-stu-id="3652b-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="3652b-107">Klauzula `Distinct` powoduje, że zapytanie ignoruje zduplikowane wyniki zapytania.</span><span class="sxs-lookup"><span data-stu-id="3652b-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="3652b-108">Klauzula `Distinct` ma zastosowanie do zduplikowanych wartości dla wszystkich zwracanych pól określonych przez klauzulę `Select`.</span><span class="sxs-lookup"><span data-stu-id="3652b-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="3652b-109">Jeśli nie jest określona klauzula `Select`, klauzula `Distinct` zostanie zastosowana do zmiennej zakresu dla zapytania zidentyfikowanego w klauzuli `From`.</span><span class="sxs-lookup"><span data-stu-id="3652b-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="3652b-110">Jeśli zmienna zakresu nie jest niezmiennym typem, zapytanie zignoruje tylko wynik zapytania, jeśli wszystkie elementy członkowskie tego typu pasują do istniejącego wyniku zapytania.</span><span class="sxs-lookup"><span data-stu-id="3652b-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3652b-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="3652b-111">Example</span></span>  
 <span data-ttu-id="3652b-112">Poniższe wyrażenie zapytania dołącza listę klientów i listę zamówień klientów.</span><span class="sxs-lookup"><span data-stu-id="3652b-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="3652b-113">Klauzula `Distinct` jest uwzględniona w celu zwrócenia listy unikatowych nazw klientów i dat kolejności.</span><span class="sxs-lookup"><span data-stu-id="3652b-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="3652b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3652b-114">See also</span></span>

- [<span data-ttu-id="3652b-115">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3652b-115">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="3652b-116">Zapytania</span><span class="sxs-lookup"><span data-stu-id="3652b-116">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="3652b-117">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="3652b-117">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="3652b-118">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="3652b-118">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="3652b-119">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="3652b-119">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
