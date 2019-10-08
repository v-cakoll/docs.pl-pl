---
title: Skip While — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 7f37a6fa1c9ba7fdf7978ac6853e4c2985bf72e7
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004701"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="20fd9-102">Skip While — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="20fd9-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="20fd9-103">Pomija elementy w kolekcji, tak długo, jak określony warunek jest `true`, a następnie zwraca pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="20fd9-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20fd9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="20fd9-104">Syntax</span></span>  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="20fd9-105">Części</span><span class="sxs-lookup"><span data-stu-id="20fd9-105">Parts</span></span>  
  
|<span data-ttu-id="20fd9-106">Termin</span><span class="sxs-lookup"><span data-stu-id="20fd9-106">Term</span></span>|<span data-ttu-id="20fd9-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="20fd9-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="20fd9-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="20fd9-108">Required.</span></span> <span data-ttu-id="20fd9-109">Wyrażenie reprezentujące warunek, dla którego mają zostać przetestowane elementy.</span><span class="sxs-lookup"><span data-stu-id="20fd9-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="20fd9-110">Wyrażenie musi zwracać wartość `Boolean` lub odpowiedni odpowiednik funkcjonalny, taki jak `Integer` do obliczenia jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="20fd9-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="20fd9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="20fd9-111">Remarks</span></span>  
 <span data-ttu-id="20fd9-112">Klauzula `Skip While` pomija elementy od początku wyniku zapytania, dopóki podane `expression` nie zwróci `false`.</span><span class="sxs-lookup"><span data-stu-id="20fd9-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="20fd9-113">Po `expression` zwraca `false`, zapytanie zwraca wszystkie pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="20fd9-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="20fd9-114">Wartość `expression` jest ignorowana dla pozostałych wyników.</span><span class="sxs-lookup"><span data-stu-id="20fd9-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="20fd9-115">Klauzula `Skip While` różni się od klauzuli `Where`, aby można było użyć klauzuli `Where` do wykluczenia wszystkich elementów z zapytania, które nie spełniają określonego warunku.</span><span class="sxs-lookup"><span data-stu-id="20fd9-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="20fd9-116">Klauzula `Skip While` wyklucza elementy tylko do pierwszego niespełnienia warunku.</span><span class="sxs-lookup"><span data-stu-id="20fd9-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="20fd9-117">Klauzula `Skip While` jest najbardziej przydatna podczas pracy z wynikiem kwerendy uporządkowanej.</span><span class="sxs-lookup"><span data-stu-id="20fd9-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="20fd9-118">Możesz pominąć określoną liczbę wyników od początku wyniku zapytania, używając klauzuli `Skip`.</span><span class="sxs-lookup"><span data-stu-id="20fd9-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20fd9-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="20fd9-119">Example</span></span>  
 <span data-ttu-id="20fd9-120">Poniższy przykład kodu używa klauzuli `Skip While`, aby pominąć wyniki do momentu, gdy zostanie znaleziony pierwszy klient z Stany Zjednoczone.</span><span class="sxs-lookup"><span data-stu-id="20fd9-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="20fd9-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="20fd9-121">See also</span></span>

- [<span data-ttu-id="20fd9-122">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="20fd9-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="20fd9-123">Zapytania</span><span class="sxs-lookup"><span data-stu-id="20fd9-123">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="20fd9-124">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="20fd9-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="20fd9-125">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="20fd9-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="20fd9-126">Skip, klauzula</span><span class="sxs-lookup"><span data-stu-id="20fd9-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="20fd9-127">Take While, klauzula</span><span class="sxs-lookup"><span data-stu-id="20fd9-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="20fd9-128">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="20fd9-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
