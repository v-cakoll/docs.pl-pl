---
title: Take, klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 25dd06905525a96bc1504f033eb4f19af6d454a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359635"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="6c8da-102">Take — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c8da-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="6c8da-103">Zwraca określoną liczbę elementów sąsiadujących od początku kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6c8da-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c8da-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6c8da-104">Syntax</span></span>  
  
```vb  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="6c8da-105">Części</span><span class="sxs-lookup"><span data-stu-id="6c8da-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="6c8da-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="6c8da-106">Required.</span></span> <span data-ttu-id="6c8da-107">Wartość lub wyrażenie, które oblicza liczbę elementów sekwencji do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="6c8da-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c8da-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6c8da-108">Remarks</span></span>  
 <span data-ttu-id="6c8da-109">`Take`Klauzula powoduje, że zapytanie zawiera określoną liczbę elementów sąsiadujących od początku listy wyników.</span><span class="sxs-lookup"><span data-stu-id="6c8da-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="6c8da-110">Liczba elementów do dołączenia jest określona przez `count` parametr.</span><span class="sxs-lookup"><span data-stu-id="6c8da-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="6c8da-111">Można użyć `Take` klauzuli z `Skip` klauzulą, aby zwrócić zakres danych z dowolnego segmentu zapytania.</span><span class="sxs-lookup"><span data-stu-id="6c8da-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="6c8da-112">Aby to zrobić, Przekaż indeks pierwszego elementu zakresu do `Skip` klauzuli i rozmiar zakresu do `Take` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="6c8da-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="6c8da-113">W takim przypadku `Take` klauzula musi być określona po `Skip` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="6c8da-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="6c8da-114">W przypadku używania `Take` klauzuli w zapytaniu może być również konieczne upewnienie się, że wyniki są zwracane w kolejności, w której `Take` klauzula będzie zawierać zamierzone wyniki.</span><span class="sxs-lookup"><span data-stu-id="6c8da-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="6c8da-115">Aby uzyskać więcej informacji na temat porządkowania wyników zapytania, zobacz [klauzula Order by](order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="6c8da-115">For more information about ordering query results, see [Order By Clause](order-by-clause.md).</span></span>  
  
 <span data-ttu-id="6c8da-116">Można użyć `TakeWhile` klauzuli, aby określić, że tylko niektóre elementy mają być zwracane, w zależności od podanego warunku.</span><span class="sxs-lookup"><span data-stu-id="6c8da-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c8da-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="6c8da-117">Example</span></span>  
 <span data-ttu-id="6c8da-118">Poniższy przykład kodu używa `Take` klauzuli razem z `Skip` klauzulą, aby zwrócić dane ze zapytania na stronach.</span><span class="sxs-lookup"><span data-stu-id="6c8da-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="6c8da-119">Funkcja getcustomerss używa `Skip` klauzuli do obejścia klientów na liście do momentu podanej wartości indeksu początkowego i użycia `Take` klauzuli do zwrócenia strony klientów zaczynających się od tej wartości indeksu.</span><span class="sxs-lookup"><span data-stu-id="6c8da-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="6c8da-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6c8da-120">See also</span></span>

- [<span data-ttu-id="6c8da-121">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6c8da-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="6c8da-122">Zapytania</span><span class="sxs-lookup"><span data-stu-id="6c8da-122">Queries</span></span>](index.md)
- [<span data-ttu-id="6c8da-123">SELECT — klauzula</span><span class="sxs-lookup"><span data-stu-id="6c8da-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="6c8da-124">Klauzula from</span><span class="sxs-lookup"><span data-stu-id="6c8da-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="6c8da-125">Order By, klauzula</span><span class="sxs-lookup"><span data-stu-id="6c8da-125">Order By Clause</span></span>](order-by-clause.md)
- [<span data-ttu-id="6c8da-126">Take While, klauzula</span><span class="sxs-lookup"><span data-stu-id="6c8da-126">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="6c8da-127">Skip, klauzula</span><span class="sxs-lookup"><span data-stu-id="6c8da-127">Skip Clause</span></span>](skip-clause.md)
