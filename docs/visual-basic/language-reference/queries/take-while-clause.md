---
title: Take While — Klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 23b7c84a9f896161a66059fcb1f30753d3b863d5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347112"
---
# <a name="take-while-clause-visual-basic"></a>Take While — Klauzula (Visual Basic)
Zawiera elementy w kolekcji, tak długo, jak określony warunek jest `true` i pomija pozostałe elementy.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`expression`|Wymagana. Wyrażenie reprezentujące warunek, dla którego mają zostać przetestowane elementy. Wyrażenie musi zwracać wartość `Boolean` lub odpowiedni odpowiednik funkcjonalny, na przykład `Integer` do oceny jako `Boolean`.|  
  
## <a name="remarks"></a>Uwagi  
 Klauzula `Take While` zawiera elementy od początku wyniku zapytania do momentu, gdy podano `expression` zwraca `false`. Gdy `expression` zwraca `false`, zapytanie spowoduje obejście wszystkich pozostałych elementów. `expression` jest ignorowana dla pozostałych wyników.  
  
 Klauzula `Take While` różni się od klauzuli `Where`, w której klauzula `Where` może być używana do dołączania wszystkich elementów z zapytania, które spełniają określony warunek. Klauzula `Take While` zawiera elementy tylko do pierwszego niespełnienia warunku. Klauzula `Take While` jest najbardziej przydatna podczas pracy z wynikiem kwerendy uporządkowanej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu używa klauzuli `Take While`, aby pobrać wyniki do momentu, w którym nie zostanie znaleziony pierwszy klient bez żadnych zamówień.  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Take, klauzula](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While, klauzula](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
