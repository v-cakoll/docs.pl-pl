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
ms.openlocfilehash: 0dddb411af1b4ee269e091c07553a94589d90b2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="take-clause-visual-basic"></a>Take — Klauzula (Visual Basic)
Zwraca określoną liczbę elementów ciągłe na początku kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
Take count  
```  
  
## <a name="parts"></a>Części  
 `count`  
 Wymagana. Wartość lub wyrażenie obliczane do liczby elementów sekwencji do zwrócenia.  
  
## <a name="remarks"></a>Uwagi  
 `Take` Klauzuli powoduje uwzględnienie określoną liczbę sąsiadujących elementów od początku listy wyników zapytania. Liczba elementów do uwzględnienia jest określona przez `count` parametru.  
  
 Można użyć `Take` klauzuli z `Skip` klauzuli do zwrócenia zakres danych z dowolnego segmentu zapytania. Aby to zrobić, należy przekazać indeks pierwszego elementu zakresu `Skip` klauzuli i rozmiar zakresu `Take` klauzuli. W takim przypadku `Take` musi być określona klauzula po `Skip` klauzuli.  
  
 Jeśli używasz `Take` klauzuli w zapytaniu, może być również konieczne upewnij się, że wyniki są zwracane w kolejności, która umożliwi `Take` klauzuli uwzględnienie zamierzone wyniki. Aby uzyskać więcej informacji na temat Porządkowanie wyników zapytania, zobacz [klauzula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Można użyć `TakeWhile` klauzuli, aby określić, że tylko niektóre elementy zwrócone, w zależności od warunek podany.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Take` klauzuli razem z `Skip` klauzuli, aby zwrócić dane z zapytania w stronach. Używa funkcji GetCustomers `Skip` klauzuli obejść klienci na liście do momentu dostarczony początkowego indeksu wartość i używa `Take` klauzuli, aby powrócić do strony klientów, począwszy od tej wartości indeksu.  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/queries.md)  
 [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By, klauzula](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Take While, klauzula](../../../visual-basic/language-reference/queries/take-while-clause.md)  
 [Skip, klauzula](../../../visual-basic/language-reference/queries/skip-clause.md)
