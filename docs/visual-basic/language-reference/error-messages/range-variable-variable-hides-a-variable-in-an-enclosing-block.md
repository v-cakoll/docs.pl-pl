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
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>Zmienna zakresu \<zmienna > ukrywa zmienną w otaczającym bloku, w uprzednio zdefiniowanej zmiennej zakresu lub w niejawnie zadeklarowanej zmiennej w wyrażeniu zapytania
Nazwę zmiennej zakresu określonego w `Select`, `From`, `Aggregate`, lub `Let` klauzuli duplikuje nazwę zmiennej zakresu już wcześniej określonych w zapytaniu lub nazwę zmiennej, która została niejawnie zadeklarowana przez zapytanie takie jak nazwa pola lub nazwa funkcji agregującej.  
  
 **Identyfikator błędu:** BC36633  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że wszystkie zmienne zakresu w zakresie określonego zapytania mają unikatowe nazwy. Zapytania można ująć w upewnij się, że zapytań zagnieżdżonej unikatową nazwę zakres za pomocą nawiasów.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Let, klauzula](../../../visual-basic/language-reference/queries/let-clause.md)
- [Klauzula Aggregate](../../../visual-basic/language-reference/queries/aggregate-clause.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
