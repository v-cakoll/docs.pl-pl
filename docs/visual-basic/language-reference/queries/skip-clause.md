---
title: Skip, klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: 427d14453260a54bd3f2ab9a8ac75dedacd291f4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359661"
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
 `Skip`Klauzula powoduje, że zapytanie pomija elementy na początku listy wyników i zwróci pozostałe elementy. Liczba elementów do pominięcia jest identyfikowana przez `count` parametr.  
  
 Można użyć `Skip` klauzuli z `Take` klauzulą, aby zwrócić zakres danych z dowolnego segmentu zapytania. Aby to zrobić, Przekaż indeks pierwszego elementu zakresu do `Skip` klauzuli i rozmiar zakresu do `Take` klauzuli.  
  
 Gdy używasz `Skip` klauzuli w zapytaniu, możesz również upewnić się, że wyniki są zwracane w kolejności, która spowoduje `Skip` pominięcie zamierzonych wyników. Aby uzyskać więcej informacji na temat porządkowania wyników zapytania, zobacz [klauzula Order by](order-by-clause.md).  
  
 Można użyć `SkipWhile` klauzuli, aby określić, że tylko niektóre elementy są ignorowane, w zależności od podanego warunku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu używa `Skip` klauzuli razem z `Take` klauzulą, aby zwrócić dane ze zapytania na stronach. `GetCustomers`Funkcja używa `Skip` klauzuli do pomijania klientów na liście do momentu podanej wartości indeksu początkowego i używa `Take` klauzuli do zwrócenia strony klientów zaczynających się od tej wartości indeksu.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do LINQ w Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](index.md)
- [SELECT — klauzula](select-clause.md)
- [Klauzula from](from-clause.md)
- [Order By, klauzula](order-by-clause.md)
- [Skip While, klauzula](skip-while-clause.md)
- [Take, klauzula](take-clause.md)
