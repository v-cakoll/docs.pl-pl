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
ms.openlocfilehash: fe6ee470698504bc0434930cc9aa6de712e04254
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004675"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="cadb7-102">Take While — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cadb7-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="cadb7-103">Zawiera elementy w kolekcji, tak długo, jak określony warunek jest `true` i pomija pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="cadb7-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cadb7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cadb7-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="cadb7-105">Części</span><span class="sxs-lookup"><span data-stu-id="cadb7-105">Parts</span></span>  
  
|<span data-ttu-id="cadb7-106">Termin</span><span class="sxs-lookup"><span data-stu-id="cadb7-106">Term</span></span>|<span data-ttu-id="cadb7-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="cadb7-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="cadb7-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="cadb7-108">Required.</span></span> <span data-ttu-id="cadb7-109">Wyrażenie reprezentujące warunek, dla którego mają zostać przetestowane elementy.</span><span class="sxs-lookup"><span data-stu-id="cadb7-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="cadb7-110">Wyrażenie musi zwracać wartość `Boolean` lub odpowiedni odpowiednik funkcjonalny, taki jak `Integer` do obliczenia jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="cadb7-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cadb7-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cadb7-111">Remarks</span></span>  
 <span data-ttu-id="cadb7-112">Klauzula `Take While` zawiera elementy od początku wyniku zapytania do momentu, gdy podane `expression` zwróci `false`.</span><span class="sxs-lookup"><span data-stu-id="cadb7-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="cadb7-113">Gdy `expression` zwraca `false`, zapytanie spowoduje obejście wszystkich pozostałych elementów.</span><span class="sxs-lookup"><span data-stu-id="cadb7-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="cadb7-114">Wartość `expression` jest ignorowana dla pozostałych wyników.</span><span class="sxs-lookup"><span data-stu-id="cadb7-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="cadb7-115">Klauzula `Take While` różni się od klauzuli `Where`, aby można było użyć klauzuli `Where` do uwzględnienia wszystkich elementów z zapytania, które spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="cadb7-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="cadb7-116">Klauzula `Take While` zawiera elementy tylko do pierwszego niespełnienia warunku.</span><span class="sxs-lookup"><span data-stu-id="cadb7-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="cadb7-117">Klauzula `Take While` jest najbardziej przydatna podczas pracy z wynikiem kwerendy uporządkowanej.</span><span class="sxs-lookup"><span data-stu-id="cadb7-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cadb7-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="cadb7-118">Example</span></span>  
 <span data-ttu-id="cadb7-119">Poniższy przykład kodu używa klauzuli `Take While` do pobierania wyników do momentu, w którym nie zostanie znaleziony pierwszy klient bez zamówień.</span><span class="sxs-lookup"><span data-stu-id="cadb7-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="cadb7-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cadb7-120">See also</span></span>

- [<span data-ttu-id="cadb7-121">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cadb7-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="cadb7-122">Zapytania</span><span class="sxs-lookup"><span data-stu-id="cadb7-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="cadb7-123">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="cadb7-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="cadb7-124">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="cadb7-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="cadb7-125">Take, klauzula</span><span class="sxs-lookup"><span data-stu-id="cadb7-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="cadb7-126">Skip While, klauzula</span><span class="sxs-lookup"><span data-stu-id="cadb7-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="cadb7-127">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="cadb7-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
