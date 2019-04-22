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
ms.openlocfilehash: cb109eaf43fee19b77ac690492b85919c9d78301
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816957"
---
# <a name="take-clause-visual-basic"></a><span data-ttu-id="936ee-102">Take — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="936ee-102">Take Clause (Visual Basic)</span></span>
<span data-ttu-id="936ee-103">Zwraca określoną liczbę elementów sąsiadujących z początku kolekcji.</span><span class="sxs-lookup"><span data-stu-id="936ee-103">Returns a specified number of contiguous elements from the start of a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="936ee-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="936ee-104">Syntax</span></span>  
  
```  
Take count  
```  
  
## <a name="parts"></a><span data-ttu-id="936ee-105">Części</span><span class="sxs-lookup"><span data-stu-id="936ee-105">Parts</span></span>  
 `count`  
 <span data-ttu-id="936ee-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="936ee-106">Required.</span></span> <span data-ttu-id="936ee-107">Wartość lub wyrażenie zwracające liczbę elementów w sekwencji do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="936ee-107">A value or an expression that evaluates to the number of elements of the sequence to return.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="936ee-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="936ee-108">Remarks</span></span>  
 <span data-ttu-id="936ee-109">`Take` Klauzuli powoduje, że zapytanie uwzględnić określoną liczbę elementów sąsiadujących z początku listy wyników.</span><span class="sxs-lookup"><span data-stu-id="936ee-109">The `Take` clause causes a query to include a specified number of contiguous elements from the start of a results list.</span></span> <span data-ttu-id="936ee-110">Liczba elementów do uwzględnienia jest określona przez `count` parametru.</span><span class="sxs-lookup"><span data-stu-id="936ee-110">The number of elements to include is specified by the `count` parameter.</span></span>  
  
 <span data-ttu-id="936ee-111">Możesz użyć `Take` klauzula `Skip` klauzuli, która zwraca zakres danych z dowolnego segmentu zapytania.</span><span class="sxs-lookup"><span data-stu-id="936ee-111">You can use the `Take` clause with the `Skip` clause to return a range of data from any segment of a query.</span></span> <span data-ttu-id="936ee-112">Aby to zrobić, należy przekazać indeksu pierwszego elementu zakresu `Skip` klauzuli i rozmiar zakresu `Take` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="936ee-112">To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.</span></span> <span data-ttu-id="936ee-113">W tym przypadku `Take` musi być określona klauzula po `Skip` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="936ee-113">In this case, the `Take` clause must be specified after the `Skip` clause.</span></span>  
  
 <span data-ttu-id="936ee-114">Kiedy używasz `Take` w klauzuli kwerendy, może być również konieczne upewnij się, że wyniki są zwracane w kolejności, która umożliwi `Take` klauzuli obejmujący zamierzone wyniki.</span><span class="sxs-lookup"><span data-stu-id="936ee-114">When you use the `Take` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Take` clause to include the intended results.</span></span> <span data-ttu-id="936ee-115">Aby uzyskać więcej informacji na temat kolejności wyników zapytania, zobacz [klauzula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md).</span><span class="sxs-lookup"><span data-stu-id="936ee-115">For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).</span></span>  
  
 <span data-ttu-id="936ee-116">Możesz użyć `TakeWhile` klauzulę, aby określić, czy tylko niektóre elementy zostać zwrócone, w zależności od podanym warunku.</span><span class="sxs-lookup"><span data-stu-id="936ee-116">You can use the `TakeWhile` clause to specify that only certain elements be returned, depending on a supplied condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="936ee-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="936ee-117">Example</span></span>  
 <span data-ttu-id="936ee-118">Poniższy przykład kodu wykorzystuje `Take` klauzuli wraz z `Skip` klauzulę, aby zwrócić dane z zapytania na stronach.</span><span class="sxs-lookup"><span data-stu-id="936ee-118">The following code example uses the `Take` clause together with the `Skip` clause to return data from a query in pages.</span></span> <span data-ttu-id="936ee-119">Używa funkcji GetCustomers `Skip` klauzuli, aby pominąć klienci na liście do momentu podany początkowy indeks wartości i używa `Take` klauzuli zwracane strony klientów, począwszy od tej wartości indeksu.</span><span class="sxs-lookup"><span data-stu-id="936ee-119">The GetCustomers function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="936ee-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="936ee-120">See also</span></span>

- [<span data-ttu-id="936ee-121">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="936ee-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="936ee-122">Zapytania</span><span class="sxs-lookup"><span data-stu-id="936ee-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="936ee-123">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="936ee-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="936ee-124">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="936ee-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="936ee-125">Order By, klauzula</span><span class="sxs-lookup"><span data-stu-id="936ee-125">Order By Clause</span></span>](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [<span data-ttu-id="936ee-126">Take While, klauzula</span><span class="sxs-lookup"><span data-stu-id="936ee-126">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="936ee-127">Skip, klauzula</span><span class="sxs-lookup"><span data-stu-id="936ee-127">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
