---
title: Take — Klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 3082954ef84560ccb70f7a47cd3532f622829392
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349644"
---
# <a name="take-clause-visual-basic"></a>Take — Klauzula (Visual Basic)
Zwraca określoną liczbę elementów sąsiadujących od początku kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Take count  
```  
  
## <a name="parts"></a>Części  
 `count`  
 Wymagana. Wartość lub wyrażenie, które oblicza liczbę elementów sekwencji do zwrócenia.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula `Take` powoduje, że zapytanie zawiera określoną liczbę elementów sąsiadujących od początku listy wyników. Liczba elementów do dołączenia jest określana przez parametr `count`.  
  
 Można użyć klauzuli `Take` z klauzulą `Skip`, aby zwrócić zakres danych z dowolnego segmentu zapytania. W tym celu Przekaż indeks pierwszego elementu zakresu do klauzuli `Skip` i rozmiar zakresu do klauzuli `Take`. W takim przypadku klauzulę `Take` należy określić po klauzuli `Skip`.  
  
 Jeśli używasz klauzuli `Take` w zapytaniu, możesz również upewnić się, że wyniki są zwracane w kolejności, w której zostanie włączona klauzula `Take` w celu uwzględnienia zamierzonych wyników. Aby uzyskać więcej informacji na temat porządkowania wyników zapytania, zobacz [klauzula Order by](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Można użyć klauzuli `TakeWhile`, aby określić, że tylko niektóre elementy mają być zwracane, w zależności od podanego warunku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu używa klauzuli `Take` razem z klauzulą `Skip`, aby zwracać dane ze zapytania na stronach. Funkcja getcustomerss używa klauzuli `Skip`, aby pominąć klientów na liście do momentu podanej wartości indeksu początkowego, i używa klauzuli `Take`, aby zwrócić stronę klientów rozpoczynającą się od tej wartości indeksu.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By, klauzula](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Take While, klauzula](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Skip, klauzula](../../../visual-basic/language-reference/queries/skip-clause.md)
