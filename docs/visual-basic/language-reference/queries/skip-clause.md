---
title: Skip — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 8441e619cdbd18545be72fd701c2cc9b1cf495d9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971240"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="aaf54-102">Skip — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aaf54-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="aaf54-103">Pomija określoną liczbę elementów w kolekcji, a następnie zwraca pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="aaf54-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaf54-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aaf54-104">Syntax</span></span>  
  
```  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="aaf54-105">Części</span><span class="sxs-lookup"><span data-stu-id="aaf54-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="aaf54-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="aaf54-106">Required.</span></span> <span data-ttu-id="aaf54-107">Wartość lub wyrażenie zwracające liczbę elementów w sekwencji, aby pominąć.</span><span class="sxs-lookup"><span data-stu-id="aaf54-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaf54-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aaf54-108">Remarks</span></span>  
 <span data-ttu-id="aaf54-109">`Skip` Klauzuli powoduje, że zapytanie w celu obejścia elementów na początku listy wyników i zwracać wszystkie pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="aaf54-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="aaf54-110">Liczba elementów do pominięcia, które jest identyfikowane za pomocą `count` parametru.</span><span class="sxs-lookup"><span data-stu-id="aaf54-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="aaf54-111">Możesz użyć `Skip` klauzula `Take` klauzuli, która zwraca zakres danych z dowolnego segmentu zapytania.</span><span class="sxs-lookup"><span data-stu-id="aaf54-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="aaf54-112">Aby to zrobić, należy przekazać indeksu pierwszego elementu zakresu `Skip` klauzuli i rozmiar zakresu `Take` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="aaf54-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="aaf54-113">Kiedy używasz `Skip` w klauzuli kwerendy, może być również konieczne upewnij się, że wyniki są zwracane w kolejności, która umożliwi `Skip` klauzulę, aby pominąć zamierzone wyniki.</span><span class="sxs-lookup"><span data-stu-id="aaf54-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="aaf54-114">Aby uzyskać więcej informacji na temat kolejności wyników zapytania, zobacz [klauzula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="aaf54-114">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="aaf54-115">Możesz użyć `SkipWhile` klauzulę, aby określić, że tylko niektóre elementy są ignorowane, w zależności od podanym warunku.</span><span class="sxs-lookup"><span data-stu-id="aaf54-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aaf54-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="aaf54-116">Example</span></span>  
 <span data-ttu-id="aaf54-117">Poniższy przykład kodu wykorzystuje `Skip` klauzuli wraz z `Take` klauzulę, aby zwrócić dane z zapytania na stronach.</span><span class="sxs-lookup"><span data-stu-id="aaf54-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="aaf54-118">`GetCustomers` Używa funkcji `Skip` klauzuli, aby pominąć klienci na liście do momentu podany początkowy indeks wartości i używa `Take` klauzuli zwracane strony klientów, począwszy od tej wartości indeksu.</span><span class="sxs-lookup"><span data-stu-id="aaf54-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="aaf54-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aaf54-119">See also</span></span>
- [<span data-ttu-id="aaf54-120">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aaf54-120">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="aaf54-121">Zapytania</span><span class="sxs-lookup"><span data-stu-id="aaf54-121">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="aaf54-122">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="aaf54-122">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="aaf54-123">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="aaf54-123">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="aaf54-124">Order By, klauzula</span><span class="sxs-lookup"><span data-stu-id="aaf54-124">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="aaf54-125">Skip While, klauzula</span><span class="sxs-lookup"><span data-stu-id="aaf54-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="aaf54-126">Take, klauzula</span><span class="sxs-lookup"><span data-stu-id="aaf54-126">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
