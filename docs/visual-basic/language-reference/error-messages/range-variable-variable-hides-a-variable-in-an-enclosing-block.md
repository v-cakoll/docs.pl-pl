---
title: Zmienna zakresu &lt;zmiennej&gt; ukrywa zmienną w otaczającym bloku, w uprzednio zdefiniowanej zmiennej zakresu lub w niejawnie zadeklarowanej zmiennej w wyrażeniu zapytania
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: aef52ea912a4180a6505949c8077296628592c72
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54748119"
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>Zmienna zakresu &lt;zmiennej&gt; ukrywa zmienną w otaczającym bloku, w uprzednio zdefiniowanej zmiennej zakresu lub w niejawnie zadeklarowanej zmiennej w wyrażeniu zapytania
Nazwę zmiennej zakresu określonego w `Select`, `From`, `Aggregate`, lub `Let` klauzuli duplikuje nazwę zmiennej zakresu już wcześniej określonych w zapytaniu lub nazwę zmiennej, która została niejawnie zadeklarowana przez zapytanie takie jak nazwa pola lub nazwa funkcji agregującej.  
  
 **Identyfikator błędu:** BC36633  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że wszystkie zmienne zakresu w zakresie określonego zapytania mają unikatowe nazwy. Zapytania można ująć w upewnij się, że zapytań zagnieżdżonej unikatową nazwę zakres za pomocą nawiasów.  
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Let, klauzula](../../../visual-basic/language-reference/queries/let-clause.md)
- [Klauzula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
