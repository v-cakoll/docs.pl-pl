---
title: Take While — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 7e0a6bd77ca2594e9d74e669fcd9cddf91ee1cad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600913"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="5825b-102">Take While — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5825b-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="5825b-103">Zawiera elementy w kolekcji, tak długo, jak jest określony warunek `true` i pomija pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="5825b-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5825b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5825b-104">Syntax</span></span>  
  
```  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="5825b-105">Części</span><span class="sxs-lookup"><span data-stu-id="5825b-105">Parts</span></span>  
  
|<span data-ttu-id="5825b-106">Termin</span><span class="sxs-lookup"><span data-stu-id="5825b-106">Term</span></span>|<span data-ttu-id="5825b-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="5825b-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="5825b-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5825b-108">Required.</span></span> <span data-ttu-id="5825b-109">Wyrażenie reprezentuje warunek do sprawdzenia elementów.</span><span class="sxs-lookup"><span data-stu-id="5825b-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="5825b-110">Wyrażenie musi zwracać `Boolean` wartość lub jej odpowiedniku funkcjonalne, takie jak `Integer` ma zostać obliczone jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="5825b-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5825b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5825b-111">Remarks</span></span>  
 <span data-ttu-id="5825b-112">`Take While` Klauzuli zawiera elementy od początku w wyniku zapytania do podane `expression` zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="5825b-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="5825b-113">Po `expression` zwraca `false`, zapytanie będzie pominąć wszystkie pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="5825b-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="5825b-114">`expression` Jest ignorowany w przypadku pozostałych wyników.</span><span class="sxs-lookup"><span data-stu-id="5825b-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="5825b-115">`Take While` Klauzuli różni się od `Where` klauzuli w tym `Where` można użyć klauzuli uwzględnienie wszystkich elementów w wyniku zapytania, które spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="5825b-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="5825b-116">`Take While` Klauzuli zawiera elementy tylko dopiero po raz pierwszy warunek nie jest spełniony.</span><span class="sxs-lookup"><span data-stu-id="5825b-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="5825b-117">`Take While` Klauzula jest najbardziej przydatne podczas pracy z wynikiem uporządkowane zapytanie.</span><span class="sxs-lookup"><span data-stu-id="5825b-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5825b-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="5825b-118">Example</span></span>  
 <span data-ttu-id="5825b-119">Poniższy przykład kodu wykorzystuje `Take While` klauzuli można pobrać wyników, aż do znalezienia pierwszego klienta bez żadnych zleceń.</span><span class="sxs-lookup"><span data-stu-id="5825b-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="5825b-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5825b-120">See Also</span></span>  
 [<span data-ttu-id="5825b-121">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5825b-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="5825b-122">Zapytania</span><span class="sxs-lookup"><span data-stu-id="5825b-122">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="5825b-123">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="5825b-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="5825b-124">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="5825b-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="5825b-125">Take, klauzula</span><span class="sxs-lookup"><span data-stu-id="5825b-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="5825b-126">Skip While, klauzula</span><span class="sxs-lookup"><span data-stu-id="5825b-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="5825b-127">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="5825b-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
