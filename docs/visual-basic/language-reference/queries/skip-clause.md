---
title: Skip — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: e52de186e1475bfabd02821a0cd2384d8350eed3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004769"
---
# <a name="skip-clause-visual-basic"></a>Skip — Klauzula (Visual Basic)
Pomija określoną liczbę elementów w kolekcji, a następnie zwraca pozostałe elementy.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a>Części  
 `count`  
 Wymagany. Wartość lub wyrażenie, które oblicza liczbę elementów sekwencji do pominięcia.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula `Skip` powoduje, że zapytanie pomija elementy na początku listy wyników i zwróci pozostałe elementy. Liczba elementów do pominięcia jest identyfikowana przez parametr `count`.  
  
 Można użyć klauzuli `Skip` z klauzulą `Take`, aby zwrócić zakres danych z dowolnego segmentu zapytania. W tym celu Przekaż indeks pierwszego elementu zakresu do klauzuli `Skip` i rozmiaru zakresu do klauzuli `Take`.  
  
 Jeśli używasz klauzuli `Skip` w zapytaniu, możesz również upewnić się, że wyniki są zwracane w kolejności, w której zostanie włączona klauzula `Skip`, aby pominąć zamierzone wyniki. Aby uzyskać więcej informacji na temat porządkowania wyników zapytania, zobacz [klauzula Order by](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Można użyć klauzuli `SkipWhile`, aby określić, że tylko niektóre elementy są ignorowane, w zależności od podanego warunku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu używa klauzuli `Skip` razem z klauzulą `Take` do zwracania danych z zapytania na stronach. Funkcja `GetCustomers` używa klauzuli `Skip` do obejścia klientów na liście do momentu podanej wartości indeksu początkowego i użycia klauzuli `Take` do zwrócenia strony klientów zaczynających się od tej wartości indeksu.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By, klauzula](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Skip While, klauzula](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take, klauzula](../../../visual-basic/language-reference/queries/take-clause.md)
