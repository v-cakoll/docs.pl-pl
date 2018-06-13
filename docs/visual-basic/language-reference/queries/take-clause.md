---
title: Take — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 0dddb411af1b4ee269e091c07553a94589d90b2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604032"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="d28dc-102">Take — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d28dc-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="d28dc-103">Zwraca określoną liczbę elementów ciągłe na początku kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d28dc-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d28dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d28dc-104">Syntax</span></span>  
  
```  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="d28dc-105">Części</span><span class="sxs-lookup"><span data-stu-id="d28dc-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="d28dc-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d28dc-106">Required.</span></span> <span data-ttu-id="d28dc-107">Wartość lub wyrażenie obliczane do liczby elementów sekwencji do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="d28dc-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d28dc-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d28dc-108">Remarks</span></span>  
 <span data-ttu-id="d28dc-109">`Take` Klauzuli powoduje uwzględnienie określoną liczbę sąsiadujących elementów od początku listy wyników zapytania.</span><span class="sxs-lookup"><span data-stu-id="d28dc-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="d28dc-110">Liczba elementów do uwzględnienia jest określona przez `count` parametru.</span><span class="sxs-lookup"><span data-stu-id="d28dc-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="d28dc-111">Można użyć `Take` klauzuli z `Skip` klauzuli do zwrócenia zakres danych z dowolnego segmentu zapytania.</span><span class="sxs-lookup"><span data-stu-id="d28dc-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="d28dc-112">Aby to zrobić, należy przekazać indeks pierwszego elementu zakresu `Skip` klauzuli i rozmiar zakresu `Take` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d28dc-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="d28dc-113">W takim przypadku `Take` musi być określona klauzula po `Skip` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d28dc-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="d28dc-114">Jeśli używasz `Take` klauzuli w zapytaniu, może być również konieczne upewnij się, że wyniki są zwracane w kolejności, która umożliwi `Take` klauzuli uwzględnienie zamierzone wyniki.</span><span class="sxs-lookup"><span data-stu-id="d28dc-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="d28dc-115">Aby uzyskać więcej informacji na temat Porządkowanie wyników zapytania, zobacz [klauzula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d28dc-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="d28dc-116">Można użyć `TakeWhile` klauzuli, aby określić, że tylko niektóre elementy zwrócone, w zależności od warunek podany.</span><span class="sxs-lookup"><span data-stu-id="d28dc-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d28dc-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="d28dc-117">Example</span></span>  
 <span data-ttu-id="d28dc-118">Poniższy przykład kodu wykorzystuje `Take` klauzuli razem z `Skip` klauzuli, aby zwrócić dane z zapytania w stronach.</span><span class="sxs-lookup"><span data-stu-id="d28dc-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="d28dc-119">Używa funkcji GetCustomers `Skip` klauzuli obejść klienci na liście do momentu dostarczony początkowego indeksu wartość i używa `Take` klauzuli, aby powrócić do strony klientów, począwszy od tej wartości indeksu.</span><span class="sxs-lookup"><span data-stu-id="d28dc-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d28dc-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d28dc-120">See Also</span></span>  
 [<span data-ttu-id="d28dc-121">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d28dc-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="d28dc-122">Zapytania</span><span class="sxs-lookup"><span data-stu-id="d28dc-122">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="d28dc-123">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="d28dc-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="d28dc-124">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="d28dc-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="d28dc-125">Order By, klauzula</span><span class="sxs-lookup"><span data-stu-id="d28dc-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="d28dc-126">Take While, klauzula</span><span class="sxs-lookup"><span data-stu-id="d28dc-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [<span data-ttu-id="d28dc-127">Skip, klauzula</span><span class="sxs-lookup"><span data-stu-id="d28dc-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
