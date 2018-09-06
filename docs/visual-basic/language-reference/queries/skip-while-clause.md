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
ms.openlocfilehash: a3c0749560d8cea1e46d96298347ce54f0bf9185
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863377"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="a7357-102">Skip While — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a7357-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="a7357-103">Pomija elementy w kolekcji, tak długo, jak długo określony warunek przyjmuje `true` , a następnie zwraca pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="a7357-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7357-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a7357-104">Syntax</span></span>  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="a7357-105">Części</span><span class="sxs-lookup"><span data-stu-id="a7357-105">Parts</span></span>  
  
|<span data-ttu-id="a7357-106">Termin</span><span class="sxs-lookup"><span data-stu-id="a7357-106">Term</span></span>|<span data-ttu-id="a7357-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="a7357-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="a7357-108">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="a7357-108">Required.</span></span> <span data-ttu-id="a7357-109">Wyrażenie, które reprezentuje stan, aby przetestować elementy.</span><span class="sxs-lookup"><span data-stu-id="a7357-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="a7357-110">Wyrażenie musi zwracać `Boolean` wartość lub równoważnej funkcjonalności, takie jak `Integer` mogło zostać ocenione jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="a7357-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7357-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a7357-111">Remarks</span></span>  
 <span data-ttu-id="a7357-112">`Skip While` Klauzuli pomija elementy od początku wynik zapytania do momentu podane `expression` zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="a7357-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="a7357-113">Po `expression` zwraca `false`, zapytanie zwraca wszystkie pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="a7357-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="a7357-114">`expression` Jest ignorowany dla pozostałych wyników.</span><span class="sxs-lookup"><span data-stu-id="a7357-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="a7357-115">`Skip While` Klauzuli różni się od `Where` klauzuli w tym `Where` klauzuli można wykluczyć wszystkie elementy z zapytania, które nie spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="a7357-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="a7357-116">`Skip While` Klauzuli wyklucza elementy tylko do pierwszego, który nie jest spełniony warunek.</span><span class="sxs-lookup"><span data-stu-id="a7357-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="a7357-117">`Skip While` Klauzula jest najbardziej przydatne podczas pracy z wynikiem zapytania uporządkowane.</span><span class="sxs-lookup"><span data-stu-id="a7357-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="a7357-118">Można pominąć określoną liczbę wyników od samego początku wyników zapytania za pomocą `Skip` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a7357-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7357-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7357-119">Example</span></span>  
 <span data-ttu-id="a7357-120">Poniższy przykład kodu wykorzystuje `Skip While` klauzulę, aby pominąć wyników, aż do znalezienia pierwszego klienta ze Stanów Zjednoczonych.</span><span class="sxs-lookup"><span data-stu-id="a7357-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a7357-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a7357-121">See Also</span></span>  
 [<span data-ttu-id="a7357-122">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a7357-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="a7357-123">Zapytania</span><span class="sxs-lookup"><span data-stu-id="a7357-123">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="a7357-124">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="a7357-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="a7357-125">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="a7357-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="a7357-126">Skip, klauzula</span><span class="sxs-lookup"><span data-stu-id="a7357-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)  
 [<span data-ttu-id="a7357-127">Take While, klauzula</span><span class="sxs-lookup"><span data-stu-id="a7357-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [<span data-ttu-id="a7357-128">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="a7357-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
