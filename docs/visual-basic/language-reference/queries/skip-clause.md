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
ms.openlocfilehash: 615f98bf36d29c1f269d6866b1232ad33a5ae2f2
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925440"
---
# <a name="skip-clause-visual-basic"></a>Skip — Klauzula (Visual Basic)
Pomija określoną liczbę elementów w kolekcji, a następnie zwraca pozostałe elementy.  
  
## <a name="syntax"></a>Składnia  
  
```  
Skip count  
```  
  
## <a name="parts"></a>Części  
 `count`  
 Wymagane. Wartość lub wyrażenie zwracające liczbę elementów w sekwencji, aby pominąć.  
  
## <a name="remarks"></a>Uwagi  
 `Skip` Klauzuli powoduje, że zapytanie w celu obejścia elementów na początku listy wyników i zwracać wszystkie pozostałe elementy. Liczba elementów do pominięcia, które jest identyfikowane za pomocą `count` parametru.  
  
 Możesz użyć `Skip` klauzula `Take` klauzuli, która zwraca zakres danych z dowolnego segmentu zapytania. Aby to zrobić, należy przekazać indeksu pierwszego elementu zakresu `Skip` klauzuli i rozmiar zakresu `Take` klauzuli.  
  
 Kiedy używasz `Skip` w klauzuli kwerendy, może być również konieczne upewnij się, że wyniki są zwracane w kolejności, która umożliwi `Skip` klauzulę, aby pominąć zamierzone wyniki. Aby uzyskać więcej informacji na temat kolejności wyników zapytania, zobacz [klauzula Order By](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Możesz użyć `SkipWhile` klauzulę, aby określić, że tylko niektóre elementy są ignorowane, w zależności od podanym warunku.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje `Skip` klauzuli wraz z `Take` klauzulę, aby zwrócić dane z zapytania na stronach. `GetCustomers` Używa funkcji `Skip` klauzuli, aby pominąć klienci na liście do momentu podany początkowy indeks wartości i używa `Take` klauzuli zwracane strony klientów, począwszy od tej wartości indeksu.  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-clause_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/index.md)  
 [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By, klauzula](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [Skip While, klauzula](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take, klauzula](../../../visual-basic/language-reference/queries/take-clause.md)
