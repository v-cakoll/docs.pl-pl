---
title: "Skip — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 508f3c094df4c834305bcb4a78223c1cee82b1c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="51360-102">Skip — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51360-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="51360-103">Pomija określoną liczbę elementów w kolekcji, a następnie zwraca wszystkie pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="51360-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51360-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="51360-104">Syntax</span></span>  
  
```  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="51360-105">Części</span><span class="sxs-lookup"><span data-stu-id="51360-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="51360-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="51360-106">Required.</span></span> <span data-ttu-id="51360-107">Wartość lub wyrażenie obliczane do liczby elementów w sekwencji, aby pominąć.</span><span class="sxs-lookup"><span data-stu-id="51360-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51360-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51360-108">Remarks</span></span>  
 <span data-ttu-id="51360-109">`Skip` Klauzuli powoduje, że zapytanie w celu obejścia elementów na początku listy wyników i zwracać wszystkie pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="51360-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="51360-110">Liczba elementów do pominięcia są identyfikowane przez `count` parametru.</span><span class="sxs-lookup"><span data-stu-id="51360-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="51360-111">Można użyć `Skip` klauzuli z `Take` klauzuli do zwrócenia zakres danych z dowolnego segmentu zapytania.</span><span class="sxs-lookup"><span data-stu-id="51360-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="51360-112">Aby to zrobić, należy przekazać indeks pierwszego elementu zakresu `Skip` klauzuli i rozmiar zakresu `Take` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="51360-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="51360-113">Jeśli używasz `Skip` klauzuli w zapytaniu, może być również konieczne upewnij się, że wyniki są zwracane w kolejności, która umożliwi `Skip` klauzuli obejść zamierzone wyniki.</span><span class="sxs-lookup"><span data-stu-id="51360-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="51360-114">Aby uzyskać więcej informacji na temat Porządkowanie wyników zapytania, zobacz [klauzula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="51360-114">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="51360-115">Można użyć `SkipWhile` klauzuli, aby określić, że tylko niektóre elementy są ignorowane, w zależności od warunek podany.</span><span class="sxs-lookup"><span data-stu-id="51360-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51360-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="51360-116">Example</span></span>  
 <span data-ttu-id="51360-117">Poniższy przykład kodu wykorzystuje `Skip` klauzuli razem z `Take` klauzuli, aby zwrócić dane z zapytania w stronach.</span><span class="sxs-lookup"><span data-stu-id="51360-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="51360-118">`GetCustomers` Używa `Skip` klauzuli obejść klienci na liście do momentu dostarczony początkowego indeksu wartość i używa `Take` klauzuli, aby powrócić do strony klientów, począwszy od tej wartości indeksu.</span><span class="sxs-lookup"><span data-stu-id="51360-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="51360-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51360-119">See Also</span></span>  
 [<span data-ttu-id="51360-120">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="51360-120">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="51360-121">Zapytania</span><span class="sxs-lookup"><span data-stu-id="51360-121">Queries</span></span>](../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="51360-122">SELECT — klauzula</span><span class="sxs-lookup"><span data-stu-id="51360-122">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="51360-123">Klauzula FROM</span><span class="sxs-lookup"><span data-stu-id="51360-123">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="51360-124">Order By — klauzula</span><span class="sxs-lookup"><span data-stu-id="51360-124">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [<span data-ttu-id="51360-125">SKIP While — klauzula</span><span class="sxs-lookup"><span data-stu-id="51360-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="51360-126">Take — klauzula</span><span class="sxs-lookup"><span data-stu-id="51360-126">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
