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
ms.openlocfilehash: fe6ee470698504bc0434930cc9aa6de712e04254
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004675"
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
|`expression`|Wymagany. Wyrażenie reprezentujące warunek, dla którego mają zostać przetestowane elementy. Wyrażenie musi zwracać wartość `Boolean` lub odpowiedni odpowiednik funkcjonalny, taki jak `Integer` do obliczenia jako `Boolean`.|  
  
## <a name="remarks"></a>Uwagi  
 Klauzula `Take While` zawiera elementy od początku wyniku zapytania do momentu, gdy podane `expression` zwróci `false`. Gdy `expression` zwraca `false`, zapytanie spowoduje obejście wszystkich pozostałych elementów. Wartość `expression` jest ignorowana dla pozostałych wyników.  
  
 Klauzula `Take While` różni się od klauzuli `Where`, aby można było użyć klauzuli `Where` do uwzględnienia wszystkich elementów z zapytania, które spełniają określony warunek. Klauzula `Take While` zawiera elementy tylko do pierwszego niespełnienia warunku. Klauzula `Take While` jest najbardziej przydatna podczas pracy z wynikiem kwerendy uporządkowanej.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu używa klauzuli `Take While` do pobierania wyników do momentu, w którym nie zostanie znaleziony pierwszy klient bez zamówień.  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Take, klauzula](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While, klauzula](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Where, klauzula](../../../visual-basic/language-reference/queries/where-clause.md)
