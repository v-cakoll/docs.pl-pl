---
title: Zmienna zakresu „<variable>” ukrywa zmienną w otaczającym bloku, w uprzednio zdefiniowanej zmiennej zakresu lub w niejawnie zadeklarowanej zmiennej w wyrażeniu zapytania
ms.date: 07/20/2015
f1_keywords:
- bc36633
- vbc36633
helpviewer_keywords:
- BC36633
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
ms.openlocfilehash: 290ca81dea500558ed73956c91bdf7bfec312014
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400399"
---
# <a name="range-variable-variable-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>Zmienna zakresu „\<variable>” ukrywa zmienną w otaczającym bloku, w uprzednio zdefiniowanej zmiennej zakresu lub w niejawnie zadeklarowanej zmiennej w wyrażeniu zapytania
Nazwa zmiennej zakresu określona w `Select` `From` klauzuli,, `Aggregate` , lub `Let` duplikuje nazwę zmiennej zakresu, która została już wcześniej określona w zapytaniu, lub nazwę zmiennej, która jest niejawnie zadeklarowana przez zapytanie, takie jak nazwa pola lub nazwa funkcji agregującej.  
  
 **Identyfikator błędu:** BC36633  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Upewnij się, że wszystkie zmienne zakresów w konkretnym zakresie zapytania mają unikatowe nazwy. Zapytanie można ująć w nawiasy, aby upewnić się, że zagnieżdżone zapytania mają unikatowy zakres.  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do LINQ w Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Klauzula from](../queries/from-clause.md)
- [Klauzula Let](../queries/let-clause.md)
- [Aggregate, klauzula](../queries/aggregate-clause.md)
- [SELECT — klauzula](../queries/select-clause.md)
