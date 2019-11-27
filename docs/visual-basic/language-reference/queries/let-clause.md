---
title: Let, klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QueryLet
helpviewer_keywords:
- queries [Visual Basic], Let
- Let clause [Visual Basic]
- Let statement [Visual Basic]
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
ms.openlocfilehash: 63eaf97016db259870eb77199651ecbdc5f809c7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350433"
---
# <a name="let-clause-visual-basic"></a><span data-ttu-id="29ccb-102">Let — Klauzula (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29ccb-102">Let Clause (Visual Basic)</span></span>
<span data-ttu-id="29ccb-103">Oblicza wartość i przypisuje ją do nowej zmiennej w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="29ccb-103">Computes a value and assigns it to a new variable within the query.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ccb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29ccb-104">Syntax</span></span>  
  
```vb  
Let variable = expression [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="29ccb-105">Części</span><span class="sxs-lookup"><span data-stu-id="29ccb-105">Parts</span></span>  
  
|<span data-ttu-id="29ccb-106">Termin</span><span class="sxs-lookup"><span data-stu-id="29ccb-106">Term</span></span>|<span data-ttu-id="29ccb-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="29ccb-107">Definition</span></span>|  
|---|---|  
|`variable`|<span data-ttu-id="29ccb-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="29ccb-108">Required.</span></span> <span data-ttu-id="29ccb-109">Alias, który może służyć do odwoływania się do wyników podanego wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="29ccb-109">An alias that can be used to reference the results of the supplied expression.</span></span>|  
|`expression`|<span data-ttu-id="29ccb-110">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="29ccb-110">Required.</span></span> <span data-ttu-id="29ccb-111">Wyrażenie, które zostanie obliczone i przypisane do określonej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="29ccb-111">An expression that will be evaluated and assigned to the specified variable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29ccb-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29ccb-112">Remarks</span></span>  
 <span data-ttu-id="29ccb-113">Klauzula `Let` umożliwia obliczanie wartości dla każdego wyniku zapytania i odwoływanie się do nich za pomocą aliasu.</span><span class="sxs-lookup"><span data-stu-id="29ccb-113">The `Let` clause enables you to compute values for each query result and reference them by using an alias.</span></span> <span data-ttu-id="29ccb-114">Alias może być używany w innych klauzulach, takich jak klauzula `Where`.</span><span class="sxs-lookup"><span data-stu-id="29ccb-114">The alias can be used in other clauses, such as the `Where` clause.</span></span> <span data-ttu-id="29ccb-115">Klauzula `Let` umożliwia utworzenie instrukcji zapytania, która jest łatwiejsza do odczytania, ponieważ można określić alias dla klauzuli Expression zawartej w zapytaniu i zastąpić alias za każdym razem, gdy zostanie użyta klauzula wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="29ccb-115">The `Let` clause enables you to create a query statement that is easier to read because you can specify an alias for an expression clause included in the query and substitute the alias each time the expression clause is used.</span></span>  
  
 <span data-ttu-id="29ccb-116">W klauzuli `Let` można uwzględnić dowolną liczbę `variable` i `expression` przypisania.</span><span class="sxs-lookup"><span data-stu-id="29ccb-116">You can include any number of `variable` and `expression` assignments in the `Let` clause.</span></span> <span data-ttu-id="29ccb-117">Każde przypisanie należy oddzielić przecinkami (,).</span><span class="sxs-lookup"><span data-stu-id="29ccb-117">Separate each assignment with a comma (,).</span></span>  
  
## <a name="example"></a><span data-ttu-id="29ccb-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="29ccb-118">Example</span></span>  
 <span data-ttu-id="29ccb-119">Poniższy przykład kodu używa klauzuli `Let`, aby obliczyć rabat 10% na produkty.</span><span class="sxs-lookup"><span data-stu-id="29ccb-119">The following code example uses the `Let` clause to compute a 10 percent discount on products.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#16)]  
  
## <a name="see-also"></a><span data-ttu-id="29ccb-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29ccb-120">See also</span></span>

- [<span data-ttu-id="29ccb-121">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="29ccb-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="29ccb-122">Zapytania</span><span class="sxs-lookup"><span data-stu-id="29ccb-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="29ccb-123">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="29ccb-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="29ccb-124">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="29ccb-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="29ccb-125">Where, klauzula</span><span class="sxs-lookup"><span data-stu-id="29ccb-125">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
