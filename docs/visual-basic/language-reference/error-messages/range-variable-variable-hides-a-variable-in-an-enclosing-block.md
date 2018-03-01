---
title: "Zmienna zakresu &lt;zmiennej&gt; ukrywa zmienną w otaczającym bloku, w uprzednio zdefiniowanej zmiennej zakresu lub w niejawnie zadeklarowanej zmiennej w wyrażeniu zapytania"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ccbac48694a13daa09f2511cf39d5dbd51cdaaf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a><span data-ttu-id="b56ec-102">Zmienna zakresu &lt;zmiennej&gt; ukrywa zmienną w otaczającym bloku, w uprzednio zdefiniowanej zmiennej zakresu lub w niejawnie zadeklarowanej zmiennej w wyrażeniu zapytania</span><span class="sxs-lookup"><span data-stu-id="b56ec-102">Range variable &lt;variable&gt; hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression</span></span>
<span data-ttu-id="b56ec-103">Nazwa zmiennej zakresu określonego w `Select`, `From`, `Aggregate`, lub `Let` klauzuli duplikaty nazwę zmiennej zakresu już wcześniej określona w zapytaniu lub nazwę zmiennej, która niejawnie zadeklarowanej przez zapytanie, takie jak nazwa pola lub nazwa funkcji agregującej.</span><span class="sxs-lookup"><span data-stu-id="b56ec-103">A range variable name specified in a `Select`, `From`, `Aggregate`, or `Let` clause duplicates the name of a range variable already specified previously in the query, or the name of a variable that is implicitly declared by the query, such as a field name or the name of an aggregate function.</span></span>  
  
 <span data-ttu-id="b56ec-104">**Identyfikator błędu:** BC36633</span><span class="sxs-lookup"><span data-stu-id="b56ec-104">**Error ID:** BC36633</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b56ec-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b56ec-105">To correct this error</span></span>  
  
-   <span data-ttu-id="b56ec-106">Upewnij się, że wszystkie zmienne zakresu w zakresie określonego zapytania mają unikatowe nazwy.</span><span class="sxs-lookup"><span data-stu-id="b56ec-106">Ensure that all range variables in a particular query scope have unique names.</span></span> <span data-ttu-id="b56ec-107">Zapytania można ująć w nawiasy, aby zapewnić unikatowy zakres zapytania zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="b56ec-107">You can enclose a query in parentheses to ensure that nested queries have a unique scope.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b56ec-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b56ec-108">See Also</span></span>  
 [<span data-ttu-id="b56ec-109">Wprowadzenie do LINQ w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b56ec-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="b56ec-110">Klauzula FROM</span><span class="sxs-lookup"><span data-stu-id="b56ec-110">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="b56ec-111">Let — klauzula</span><span class="sxs-lookup"><span data-stu-id="b56ec-111">Let Clause</span></span>](../../../visual-basic/language-reference/queries/let-clause.md)  
 [<span data-ttu-id="b56ec-112">AGGREGATE — klauzula</span><span class="sxs-lookup"><span data-stu-id="b56ec-112">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [<span data-ttu-id="b56ec-113">SELECT — klauzula</span><span class="sxs-lookup"><span data-stu-id="b56ec-113">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
