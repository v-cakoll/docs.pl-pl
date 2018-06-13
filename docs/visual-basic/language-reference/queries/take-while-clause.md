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
ms.openlocfilehash: 7e0a6bd77ca2594e9d74e669fcd9cddf91ee1cad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600913"
---
# <a name="take-while-clause-visual-basic"></a>Take While — Klauzula (Visual Basic)
Zawiera elementy w kolekcji, tak długo, jak jest określony warunek `true` i pomija pozostałe elementy.  
  
## <a name="syntax"></a>Składnia  
  
```  
Take While expression  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`expression`|Wymagana. Wyrażenie reprezentuje warunek do sprawdzenia elementów. Wyrażenie musi zwracać `Boolean` wartość lub jej odpowiedniku funkcjonalne, takie jak `Integer` ma zostać obliczone jako `Boolean`.|  
  
## <a name="remarks"></a>Uwagi  
 `Take While` Klauzuli zawiera elementy od początku w wyniku zapytania do podane `expression` zwraca `false`. Po `expression` zwraca `false`, zapytanie będzie pominąć wszystkie pozostałe elementy. `expression` Jest ignorowany w przypadku pozostałych wyników.  
  
 `Take While` Klauzuli różni się od `Where` klauzuli w tym `Where` można użyć klauzuli uwzględnienie wszystkich elementów w wyniku zapytania, które spełniają określony warunek. `Take While` Klauzuli zawiera elementy tylko dopiero po raz pierwszy warunek nie jest spełniony. `Take While` Klauzula jest najbardziej przydatne podczas pracy z wynikiem uporządkowane zapytanie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Take While` klauzuli można pobrać wyników, aż do znalezienia pierwszego klienta bez żadnych zleceń.  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/queries.md)  
 [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Take, klauzula](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Skip While, klauzula](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
