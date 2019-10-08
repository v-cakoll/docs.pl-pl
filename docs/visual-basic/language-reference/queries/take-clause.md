---
title: Take — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 32a4c7fd7f1e2f6fe640f3f53f15579f014759d5
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004715"
---
# <a name="take-clause-visual-basic"></a>Take — Klauzula (Visual Basic)
Zwraca określoną liczbę elementów sąsiadujących od początku kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Take count  
```  
  
## <a name="parts"></a>Części  
 `count`  
 Wymagany. Wartość lub wyrażenie, które oblicza liczbę elementów sekwencji do zwrócenia.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula `Take` powoduje, że zapytanie zawiera określoną liczbę elementów sąsiadujących od początku listy wyników. Liczba elementów do dołączenia jest określona przez parametr `count`.  
  
 Można użyć klauzuli `Take` z klauzulą `Skip`, aby zwrócić zakres danych z dowolnego segmentu zapytania. W tym celu Przekaż indeks pierwszego elementu zakresu do klauzuli `Skip` i rozmiaru zakresu do klauzuli `Take`. W takim przypadku klauzula `Take` musi być określona po klauzuli `Skip`.  
  
 Jeśli w zapytaniu jest używana klauzula `Take`, może być również konieczne upewnienie się, że wyniki są zwracane w kolejności, w której zostanie włączona klauzula `Take` w celu uwzględnienia zamierzonych wyników. Aby uzyskać więcej informacji na temat porządkowania wyników zapytania, zobacz [klauzula Order by](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Można użyć klauzuli `TakeWhile`, aby określić, że tylko niektóre elementy mają być zwracane, w zależności od podanego warunku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu używa klauzuli `Take` razem z klauzulą `Skip` do zwracania danych z zapytania na stronach. Funkcja getcustomerss używa klauzuli `Skip` w celu obejścia klientów na liście do momentu podanej wartości indeksu początkowego i użycia klauzuli `Take` do zwrócenia strony klientów zaczynających się od tej wartości indeksu.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By, klauzula](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Take While, klauzula](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Skip, klauzula](../../../visual-basic/language-reference/queries/skip-clause.md)
