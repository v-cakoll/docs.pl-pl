---
title: Zmienna zakresu &lt;zmiennej&gt; ukrywa zmienną w otaczającym bloku, w uprzednio zdefiniowanej zmiennej zakresu lub w niejawnie zadeklarowanej zmiennej w wyrażeniu zapytania
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: f02533cf7cb79c34e5bb5a6d445aaef7ab0e86da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>Zmienna zakresu &lt;zmiennej&gt; ukrywa zmienną w otaczającym bloku, w uprzednio zdefiniowanej zmiennej zakresu lub w niejawnie zadeklarowanej zmiennej w wyrażeniu zapytania
Nazwa zmiennej zakresu określonego w `Select`, `From`, `Aggregate`, lub `Let` klauzuli duplikaty nazwę zmiennej zakresu już wcześniej określona w zapytaniu lub nazwę zmiennej, która niejawnie zadeklarowanej przez zapytanie, takie jak nazwa pola lub nazwa funkcji agregującej.  
  
 **Identyfikator błędu:** BC36633  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że wszystkie zmienne zakresu w zakresie określonego zapytania mają unikatowe nazwy. Zapytania można ująć w nawiasy, aby zapewnić unikatowy zakres zapytania zagnieżdżone.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Let, klauzula](../../../visual-basic/language-reference/queries/let-clause.md)  
 [Aggregate, klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
