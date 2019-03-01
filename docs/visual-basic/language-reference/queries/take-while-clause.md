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
ms.openlocfilehash: f7e0587d7737d99d48fcc9cd4a102e78248a55e5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979947"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="d4c7e-102">Take While — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4c7e-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="d4c7e-103">Zawiera elementy w kolekcji, tak długo, jak długo określony warunek przyjmuje `true` i pomija pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="d4c7e-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4c7e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d4c7e-104">Syntax</span></span>  
  
```  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="d4c7e-105">Części</span><span class="sxs-lookup"><span data-stu-id="d4c7e-105">Parts</span></span>  
  
|<span data-ttu-id="d4c7e-106">Termin</span><span class="sxs-lookup"><span data-stu-id="d4c7e-106">Term</span></span>|<span data-ttu-id="d4c7e-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="d4c7e-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="d4c7e-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d4c7e-108">Required.</span></span> <span data-ttu-id="d4c7e-109">Wyrażenie, które reprezentuje stan, aby przetestować elementy.</span><span class="sxs-lookup"><span data-stu-id="d4c7e-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="d4c7e-110">Wyrażenie musi zwracać `Boolean` wartość lub równoważnej funkcjonalności, takie jak `Integer` mogło zostać ocenione jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d4c7e-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4c7e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d4c7e-111">Remarks</span></span>  
 <span data-ttu-id="d4c7e-112">`Take While` Klauzula zawiera elementy od początku wyników zapytania do momentu podane `expression` zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="d4c7e-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="d4c7e-113">Po `expression` zwraca `false`, zapytanie będzie pominąć wszystkie pozostałe elementy.</span><span class="sxs-lookup"><span data-stu-id="d4c7e-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="d4c7e-114">`expression` Jest ignorowany dla pozostałych wyników.</span><span class="sxs-lookup"><span data-stu-id="d4c7e-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="d4c7e-115">`Take While` Klauzuli różni się od `Where` klauzuli w tym `Where` można użyć klauzuli, aby uwzględnić wszystkie elementy z zapytania, które spełniają określony warunek.</span><span class="sxs-lookup"><span data-stu-id="d4c7e-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="d4c7e-116">`Take While` Klauzuli zawiera elementy tylko do pierwszego, który nie jest spełniony warunek.</span><span class="sxs-lookup"><span data-stu-id="d4c7e-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="d4c7e-117">`Take While` Klauzula jest najbardziej przydatne podczas pracy z wynikiem zapytania uporządkowane.</span><span class="sxs-lookup"><span data-stu-id="d4c7e-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4c7e-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="d4c7e-118">Example</span></span>  
 <span data-ttu-id="d4c7e-119">Poniższy przykład kodu wykorzystuje `Take While` klauzuli, aby pobrać wyniki, aż do znalezienia pierwszego klienta bez żadnych zamówienia.</span><span class="sxs-lookup"><span data-stu-id="d4c7e-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d4c7e-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d4c7e-120">See also</span></span>
- [<span data-ttu-id="d4c7e-121">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d4c7e-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d4c7e-122">Zapytania</span><span class="sxs-lookup"><span data-stu-id="d4c7e-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="d4c7e-123">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="d4c7e-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="d4c7e-124">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="d4c7e-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="d4c7e-125">Take, klauzula</span><span class="sxs-lookup"><span data-stu-id="d4c7e-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="d4c7e-126">Skip While, klauzula</span><span class="sxs-lookup"><span data-stu-id="d4c7e-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="d4c7e-127">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="d4c7e-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
