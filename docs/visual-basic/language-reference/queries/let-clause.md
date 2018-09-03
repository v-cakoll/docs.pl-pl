---
title: Let — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 34c0fd239d9e08dab4a107cb8447941e7ab3ecbe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480375"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="ab589-102">Let — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab589-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="ab589-103">Oblicza wartość i przypisuje go do nowej zmiennej w ramach zapytania.</span><span class="sxs-lookup"><span data-stu-id="ab589-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab589-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab589-104">Syntax</span></span>  
  
```  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="ab589-105">Części</span><span class="sxs-lookup"><span data-stu-id="ab589-105">Parts</span></span>  
  
|<span data-ttu-id="ab589-106">Termin</span><span class="sxs-lookup"><span data-stu-id="ab589-106">Term</span></span>|<span data-ttu-id="ab589-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="ab589-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="ab589-108">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="ab589-108">Required.</span></span> <span data-ttu-id="ab589-109">Alias, który może służyć do odwołania wyniki podane wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="ab589-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="ab589-110">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="ab589-110">Required.</span></span> <span data-ttu-id="ab589-111">Wyrażenie, które będą oceniane i przypisane do określonej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ab589-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab589-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab589-112">Remarks</span></span>  
 <span data-ttu-id="ab589-113">`Let` Klauzuli pozwala do obliczenia wartości dla każdej wynik zapytania i odwoływać się do nich za pomocą aliasu.</span><span class="sxs-lookup"><span data-stu-id="ab589-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="ab589-114">Alias mogą być używane w innych klauzul takich jak `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="ab589-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="ab589-115">`Let` Klauzuli pozwala na tworzenie instrukcji zapytań, która jest łatwiejsza do odczytania, ponieważ możesz określić alias dla klauzuli wyrażenie uwzględnione w zapytaniu i Zastąp alias zawsze jest używana klauzula wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="ab589-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="ab589-116">Może zawierać dowolną liczbę `variable` i `expression` przydziały w `Let` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="ab589-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="ab589-117">Każdego przypisania należy oddzielić przecinkami (,).</span><span class="sxs-lookup"><span data-stu-id="ab589-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab589-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab589-118">Example</span></span>  
 <span data-ttu-id="ab589-119">Poniższy przykład kodu wykorzystuje `Let` klauzuli do obliczenia 10 procent rabatu na produkty.</span><span class="sxs-lookup"><span data-stu-id="ab589-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ab589-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab589-120">See Also</span></span>  
 [<span data-ttu-id="ab589-121">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab589-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="ab589-122">Zapytania</span><span class="sxs-lookup"><span data-stu-id="ab589-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="ab589-123">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="ab589-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="ab589-124">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="ab589-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="ab589-125">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="ab589-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
