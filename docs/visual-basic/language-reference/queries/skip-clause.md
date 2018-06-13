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
ms.openlocfilehash: 1810bf4a6573c6fa36f1d8149bf341d45cfd6f52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602830"
---
# <a name="skip-clause-visual-basic"></a>Skip — Klauzula (Visual Basic)
Pomija określoną liczbę elementów w kolekcji, a następnie zwraca wszystkie pozostałe elementy.  
  
## <a name="syntax"></a>Składnia  
  
```  
Skip count  
```  
  
## <a name="parts"></a>Części  
 `count`  
 Wymagana. Wartość lub wyrażenie obliczane do liczby elementów w sekwencji, aby pominąć.  
  
## <a name="remarks"></a>Uwagi  
 `Skip` Klauzuli powoduje, że zapytanie w celu obejścia elementów na początku listy wyników i zwracać wszystkie pozostałe elementy. Liczba elementów do pominięcia są identyfikowane przez `count` parametru.  
  
 Można użyć `Skip` klauzuli z `Take` klauzuli do zwrócenia zakres danych z dowolnego segmentu zapytania. Aby to zrobić, należy przekazać indeks pierwszego elementu zakresu `Skip` klauzuli i rozmiar zakresu `Take` klauzuli.  
  
 Jeśli używasz `Skip` klauzuli w zapytaniu, może być również konieczne upewnij się, że wyniki są zwracane w kolejności, która umożliwi `Skip` klauzuli obejść zamierzone wyniki. Aby uzyskać więcej informacji na temat Porządkowanie wyników zapytania, zobacz [klauzula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Można użyć `SkipWhile` klauzuli, aby określić, że tylko niektóre elementy są ignorowane, w zależności od warunek podany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Skip` klauzuli razem z `Take` klauzuli, aby zwrócić dane z zapytania w stronach. `GetCustomers` Używa `Skip` klauzuli obejść klienci na liście do momentu dostarczony początkowego indeksu wartość i używa `Take` klauzuli, aby powrócić do strony klientów, począwszy od tej wartości indeksu.  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/queries.md)  
 [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By, klauzula](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Skip While, klauzula](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take, klauzula](../../../visual-basic/language-reference/queries/take-clause.md)
