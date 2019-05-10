---
title: Zmienna zakresu „<variable>” ukrywa zmienną w otaczającym bloku, w uprzednio zdefiniowanej zmiennej zakresu lub w niejawnie zadeklarowanej zmiennej w wyrażeniu zapytania
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: 5e071970eec70828841c686e89aa673d38ff9918
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661620"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="6c37f-102">Zmienna zakresu \<zmienna > ukrywa zmienną w otaczającym bloku, w uprzednio zdefiniowanej zmiennej zakresu lub w niejawnie zadeklarowanej zmiennej w wyrażeniu zapytania</span><span class="sxs-lookup"><span data-stu-id="6c37f-102">Range variable \<variable> hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="6c37f-103">Nazwę zmiennej zakresu określonego w `Select`, `From`, `Aggregate`, lub `Let` klauzuli duplikuje nazwę zmiennej zakresu już wcześniej określonych w zapytaniu lub nazwę zmiennej, która została niejawnie zadeklarowana przez zapytanie takie jak nazwa pola lub nazwa funkcji agregującej.</span><span class="sxs-lookup"><span data-stu-id="6c37f-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="6c37f-104">**Identyfikator błędu:** BC36633</span><span class="sxs-lookup"><span data-stu-id="6c37f-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6c37f-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6c37f-105">To correct this error</span></span>  
  
- <span data-ttu-id="6c37f-106">Upewnij się, że wszystkie zmienne zakresu w zakresie określonego zapytania mają unikatowe nazwy.</span><span class="sxs-lookup"><span data-stu-id="6c37f-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="6c37f-107">Zapytania można ująć w upewnij się, że zapytań zagnieżdżonej unikatową nazwę zakres za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="6c37f-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c37f-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6c37f-108">See also</span></span>

- [<span data-ttu-id="6c37f-109">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6c37f-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="6c37f-110">From, klauzula</span><span class="sxs-lookup"><span data-stu-id="6c37f-110">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="6c37f-111">Let, klauzula</span><span class="sxs-lookup"><span data-stu-id="6c37f-111">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)
- [<span data-ttu-id="6c37f-112">Klauzula Aggregate</span><span class="sxs-lookup"><span data-stu-id="6c37f-112">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [<span data-ttu-id="6c37f-113">Select, klauzula</span><span class="sxs-lookup"><span data-stu-id="6c37f-113">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
