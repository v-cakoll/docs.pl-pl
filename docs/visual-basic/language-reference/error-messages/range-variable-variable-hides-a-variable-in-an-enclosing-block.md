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
# <a name="range-variable-ltvariablegt-hides-a-variable-in-an-enclosing-block-a-previously-defined-range-variable-or-an-implicitly-declared-variable-in-a-query-expression"></a>Zmienna zakresu &lt;zmiennej&gt; ukrywa zmienną w otaczającym bloku, w uprzednio zdefiniowanej zmiennej zakresu lub w niejawnie zadeklarowanej zmiennej w wyrażeniu zapytania
Nazwa zmiennej zakresu określonego w `Select`, `From`, `Aggregate`, lub `Let` klauzuli duplikaty nazwę zmiennej zakresu już wcześniej określona w zapytaniu lub nazwę zmiennej, która niejawnie zadeklarowanej przez zapytanie, takie jak nazwa pola lub nazwa funkcji agregującej.  
  
 **Identyfikator błędu:** BC36633  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Upewnij się, że wszystkie zmienne zakresu w zakresie określonego zapytania mają unikatowe nazwy. Zapytania można ująć w nawiasy, aby zapewnić unikatowy zakres zapytania zagnieżdżone.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Klauzula FROM](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Let — klauzula](../../../visual-basic/language-reference/queries/let-clause.md)  
 [AGGREGATE — klauzula](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
 [SELECT — klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
