---
title: "Where — Klauzula (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8c2572f513d00bc72e869cf28d382be799f7a303
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="where-clause-visual-basic"></a>Where — Klauzula (Visual Basic)
Określa warunek filtrowania dla zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```  
Where condition  
```  
  
## <a name="parts"></a>Części  
 `condition`  
 Wymagany. Wyrażenie, które określa, czy wartości dla bieżącego elementu w kolekcji są dołączane do kolekcji danych wyjściowych. Wyrażenia musi być `Boolean` wartość lub odpowiednikiem `Boolean` wartość. Jeśli wynikiem warunku jest `True`, element jest uwzględnione w wynikach zapytania; w przeciwnym razie, element są wykluczane w wyniku zapytania.  
  
## <a name="remarks"></a>Uwagi  
 `Where` Klauzuli umożliwia filtrowanie danych zapytania, wybierając tylko te elementy, które spełniają określone kryteria. Elementy, których wartości powodują `Where` klauzuli mogła zwrócić `True` znajdują się w wynikach zapytania; inne elementy są wyłączone. Wyrażenie, które jest używane w `Where` musi mieć klauzulę `Boolean` lub odpowiednikiem `Boolean`, takie jak liczba całkowita, która daje w wyniku `False` po jego wartość wynosi zero. Można połączyć wiele wyrażeń w `Where` klauzuli przy użyciu operatorów logicznych, takich jak `And`, `Or`, `AndAlso`, `OrElse`, `Is`, i `IsNot`.  
  
 Domyślnie wyrażenia zapytania nie są obliczane aż do uzyskiwania do nich — na przykład, gdy są one powiązane z danymi lub powtórzyć za pośrednictwem w `For` pętli. W związku z tym `Where` klauzula nie jest oceniany, aż do uzyskiwania dostępu do zapytania. Jeśli masz wartości zewnętrznych do zapytania, które są używane w `Where` klauzuli, upewnij się, że odpowiednią wartość jest używana w `Where` klauzuli w czasie wykonywania zapytania. Aby uzyskać więcej informacji na temat wykonywania zapytania, zobacz [Your pierwszego zapytania LINQ zapisu](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Można wywołać funkcji w ramach `Where` klauzuli, aby wykonać obliczenie lub operacja na wartości z bieżącego elementu w kolekcji. Wywoływanie funkcji w `Where` klauzuli może spowodować wykonanie zapytania w celu wykonania natychmiast, gdy jest on zdefiniowany zamiast, gdy jest on dostępny. Aby uzyskać więcej informacji na temat wykonywania zapytania, zobacz [Your pierwszego zapytania LINQ zapisu](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie używa wyrażenia `From` klauzuli, aby zadeklarować zmienną zakresu `cust` dla każdego `Customer` obiektu w `customers` kolekcji. `Where` Klauzuli używa zmiennej zakresu, aby ograniczyć dane wyjściowe do klientów z określonego regionu. `For Each` Pętli Wyświetla nazwę firmy dla każdego klienta w wyniku zapytania.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_1.vb)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `And` i `Or` operatory logiczne w `Where` klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/where-clause_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Zapytania](../../../visual-basic/language-reference/queries/queries.md)  
 [Klauzula FROM](../../../visual-basic/language-reference/queries/from-clause.md)  
 [SELECT — klauzula](../../../visual-basic/language-reference/queries/select-clause.md)  
 [For Each... Next — instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
