---
title: Skip — Klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: c582b014bad4fa8fa3165d2b756f4bc955840cfc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349655"
---
# <a name="skip-clause-visual-basic"></a><span data-ttu-id="7cd6b-102">Skip — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7cd6b-102">Skip Clause (Visual Basic)</span></span>
<span data-ttu-id="7cd6b-103">Pomija określoną liczbę elementów w kolekcji, a następnie zwraca pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="7cd6b-103">Bypasses a specified number of elements in a collection and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cd6b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cd6b-104">Syntax</span></span>  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a><span data-ttu-id="7cd6b-105">Części</span><span class="sxs-lookup"><span data-stu-id="7cd6b-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="7cd6b-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="7cd6b-106">Required.</span></span> <span data-ttu-id="7cd6b-107">Wartość lub wyrażenie, które oblicza liczbę elementów sekwencji do pominięcia.</span><span class="sxs-lookup"><span data-stu-id="7cd6b-107">A value or an expression that evaluates to the number of elements of the sequence to skip.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cd6b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7cd6b-108">Remarks</span></span>  
 <span data-ttu-id="7cd6b-109">Klauzula `Skip` powoduje, że zapytanie pomija elementy na początku listy wyników i zwróci pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="7cd6b-109">The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements.</span></span> <span data-ttu-id="7cd6b-110">Liczba elementów do pominięcia jest identyfikowana przez parametr `count`.</span><span class="sxs-lookup"><span data-stu-id="7cd6b-110">The number of elements to skip is identified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="7cd6b-111">Można użyć klauzuli `Skip` z klauzulą `Take`, aby zwrócić zakres danych z dowolnego segmentu zapytania.</span><span class="sxs-lookup"><span data-stu-id="7cd6b-111">You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="7cd6b-112">W tym celu Przekaż indeks pierwszego elementu zakresu do klauzuli `Skip` i rozmiar zakresu do klauzuli `Take`.</span><span class="sxs-lookup"><span data-stu-id="7cd6b-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span>  
  
 <span data-ttu-id="7cd6b-113">Jeśli używasz klauzuli `Skip` w zapytaniu, możesz również upewnić się, że wyniki są zwracane w kolejności, w której zostanie włączona klauzula `Skip`, aby pominąć zamierzone wyniki.</span><span class="sxs-lookup"><span data-stu-id="7cd6b-113">When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results.</span></span> <span data-ttu-id="7cd6b-114">Aby uzyskać więcej informacji na temat porządkowania wyników zapytania, zobacz [klauzula Order by](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="7cd6b-114">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="7cd6b-115">Można użyć klauzuli `SkipWhile`, aby określić, że tylko niektóre elementy są ignorowane, w zależności od podanego warunku.</span><span class="sxs-lookup"><span data-stu-id="7cd6b-115">You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cd6b-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cd6b-116">Example</span></span>  
 <span data-ttu-id="7cd6b-117">Poniższy przykład kodu używa klauzuli `Skip` razem z klauzulą `Take`, aby zwracać dane ze zapytania na stronach.</span><span class="sxs-lookup"><span data-stu-id="7cd6b-117">The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages.</span></span> <span data-ttu-id="7cd6b-118">Funkcja `GetCustomers` używa klauzuli `Skip`, aby pominąć klientów na liście do momentu podanej wartości indeksu początkowego i używa klauzuli `Take` do zwrócenia strony klientów zaczynających się od tej wartości indeksu.</span><span class="sxs-lookup"><span data-stu-id="7cd6b-118">The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7cd6b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cd6b-119">See also</span></span>

- [<span data-ttu-id="7cd6b-120">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7cd6b-120">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="7cd6b-121">Zapytania</span><span class="sxs-lookup"><span data-stu-id="7cd6b-121">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="7cd6b-122">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="7cd6b-122">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="7cd6b-123">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="7cd6b-123">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="7cd6b-124">Order By, klauzula</span><span class="sxs-lookup"><span data-stu-id="7cd6b-124">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="7cd6b-125">Skip While, klauzula</span><span class="sxs-lookup"><span data-stu-id="7cd6b-125">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="7cd6b-126">Take, klauzula</span><span class="sxs-lookup"><span data-stu-id="7cd6b-126">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
