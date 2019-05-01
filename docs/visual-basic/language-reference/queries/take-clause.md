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
ms.openlocfilehash: cb109eaf43fee19b77ac690492b85919c9d78301
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054396"
---
# <a name="take-clause-visual-basic"></a>Take — Klauzula (Visual Basic)
Zwraca określoną liczbę elementów sąsiadujących z początku kolekcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
Take count  
```  
  
## <a name="parts"></a>Części  
 `count`  
 Wymagana. Wartość lub wyrażenie zwracające liczbę elementów w sekwencji do zwrócenia.  
  
## <a name="remarks"></a>Uwagi  
 `Take` Klauzuli powoduje, że zapytanie uwzględnić określoną liczbę elementów sąsiadujących z początku listy wyników. Liczba elementów do uwzględnienia jest określona przez `count` parametru.  
  
 Możesz użyć `Take` klauzula `Skip` klauzuli, która zwraca zakres danych z dowolnego segmentu zapytania. Aby to zrobić, należy przekazać indeksu pierwszego elementu zakresu `Skip` klauzuli i rozmiar zakresu `Take` klauzuli. W tym przypadku `Take` musi być określona klauzula po `Skip` klauzuli.  
  
 Kiedy używasz `Take` w klauzuli kwerendy, może być również konieczne upewnij się, że wyniki są zwracane w kolejności, która umożliwi `Take` klauzuli obejmujący zamierzone wyniki. Aby uzyskać więcej informacji na temat kolejności wyników zapytania, zobacz [klauzula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Możesz użyć `TakeWhile` klauzulę, aby określić, czy tylko niektóre elementy zostać zwrócone, w zależności od podanym warunku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Take` klauzuli wraz z `Skip` klauzulę, aby zwrócić dane z zapytania na stronach. Używa funkcji GetCustomers `Skip` klauzuli, aby pominąć klienci na liście do momentu podany początkowy indeks wartości i używa `Take` klauzuli zwracane strony klientów, począwszy od tej wartości indeksu.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By, klauzula](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Take While, klauzula](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Skip, klauzula](../../../visual-basic/language-reference/queries/skip-clause.md)
