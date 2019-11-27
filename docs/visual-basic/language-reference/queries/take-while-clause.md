---
title: Take While — Klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 23b7c84a9f896161a66059fcb1f30753d3b863d5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347112"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="b99ef-102">Take While — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b99ef-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="b99ef-103">Zawiera elementy w kolekcji, tak długo, jak określony warunek jest `true` i pomija pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="b99ef-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b99ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b99ef-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="b99ef-105">Części</span><span class="sxs-lookup"><span data-stu-id="b99ef-105">Parts</span></span>  
  
|<span data-ttu-id="b99ef-106">Termin</span><span class="sxs-lookup"><span data-stu-id="b99ef-106">Term</span></span>|<span data-ttu-id="b99ef-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="b99ef-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="b99ef-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="b99ef-108">Required.</span></span> <span data-ttu-id="b99ef-109">Wyrażenie reprezentujące warunek, dla którego mają zostać przetestowane elementy.</span><span class="sxs-lookup"><span data-stu-id="b99ef-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="b99ef-110">Wyrażenie musi zwracać wartość `Boolean` lub odpowiedni odpowiednik funkcjonalny, na przykład `Integer` do oceny jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b99ef-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b99ef-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b99ef-111">Remarks</span></span>  
 <span data-ttu-id="b99ef-112">Klauzula `Take While` zawiera elementy od początku wyniku zapytania do momentu, gdy podano `expression` zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="b99ef-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="b99ef-113">Gdy `expression` zwraca `false`, zapytanie spowoduje obejście wszystkich pozostałych elementów.</span><span class="sxs-lookup"><span data-stu-id="b99ef-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="b99ef-114">`expression` jest ignorowana dla pozostałych wyników.</span><span class="sxs-lookup"><span data-stu-id="b99ef-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="b99ef-115">Klauzula `Take While` różni się od klauzuli `Where`, w której klauzula `Where` może być używana do dołączania wszystkich elementów z zapytania, które spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="b99ef-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="b99ef-116">Klauzula `Take While` zawiera elementy tylko do pierwszego niespełnienia warunku.</span><span class="sxs-lookup"><span data-stu-id="b99ef-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="b99ef-117">Klauzula `Take While` jest najbardziej przydatna podczas pracy z wynikiem kwerendy uporządkowanej.</span><span class="sxs-lookup"><span data-stu-id="b99ef-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b99ef-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="b99ef-118">Example</span></span>  
 <span data-ttu-id="b99ef-119">Poniższy przykład kodu używa klauzuli `Take While`, aby pobrać wyniki do momentu, w którym nie zostanie znaleziony pierwszy klient bez żadnych zamówień.</span><span class="sxs-lookup"><span data-stu-id="b99ef-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b99ef-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b99ef-120">See also</span></span>

- [<span data-ttu-id="b99ef-121">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b99ef-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b99ef-122">Zapytania</span><span class="sxs-lookup"><span data-stu-id="b99ef-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="b99ef-123">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="b99ef-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="b99ef-124">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="b99ef-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="b99ef-125">Take, klauzula</span><span class="sxs-lookup"><span data-stu-id="b99ef-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="b99ef-126">Skip While, klauzula</span><span class="sxs-lookup"><span data-stu-id="b99ef-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="b99ef-127">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="b99ef-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
