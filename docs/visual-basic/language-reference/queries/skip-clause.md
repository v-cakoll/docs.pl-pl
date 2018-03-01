---
title: "Skip — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 508f3c094df4c834305bcb4a78223c1cee82b1c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="skip-clause-visual-basic"></a>Skip — Klauzula (Visual Basic)
Pomija określoną liczbę elementów w kolekcji, a następnie zwraca wszystkie pozostałe elementy.  
  
## <a name="syntax"></a>Składnia  
  
```  
Skip count  
```  
  
## <a name="parts"></a>Części  
 `count`  
 Wymagany. Wartość lub wyrażenie obliczane do liczby elementów w sekwencji, aby pominąć.  
  
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
 [SELECT — klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [Klauzula FROM](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Order By — klauzula](../../../visual-basic/language-reference/queries/order-by-clause.md)  
 [SKIP While — klauzula](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Take — klauzula](../../../visual-basic/language-reference/queries/take-clause.md)
