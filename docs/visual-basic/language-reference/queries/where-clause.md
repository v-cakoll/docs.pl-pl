---
title: Where — Klauzula (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 404dd848058f7e5c9bc8a74b6d89df18c6c55fad
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005000"
---
# <a name="where-clause-visual-basic"></a>Where — Klauzula (Visual Basic)
Określa warunek filtrowania dla zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a>Części  
 `condition`  
 Wymagany. Wyrażenie określające, czy wartości bieżącego elementu w kolekcji są uwzględniane w kolekcji wyjściowej. Wyrażenie musi mieć wartość `Boolean` lub być równoważną wartością `Boolean`. Jeśli warunek ma wartość `True`, element zostanie uwzględniony w wyniku zapytania; w przeciwnym razie element jest wykluczony z wyniku zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Klauzula `Where` umożliwia filtrowanie danych zapytania przez wybranie tylko elementów spełniających określone kryteria. Elementy, których wartości powodują, że klauzula `Where` jest szacowana do `True` są uwzględniane w wyniku zapytania; inne elementy są wykluczone. Wyrażenie użyte w klauzuli `Where` musi być szacowane do `Boolean` lub równoważnej `Boolean`, takiej jak liczba całkowita, która daje w wyniku `False`, gdy jego wartość wynosi zero. Można połączyć wiele wyrażeń w klauzuli `Where` za pomocą operatorów logicznych, takich jak `And`, `Or`, `AndAlso`, `OrElse`, `Is` i `IsNot`.  
  
 Domyślnie wyrażenia zapytania nie są oceniane do momentu uzyskania dostępu do nich, na przykład gdy są one powiązane z danymi lub powtarzane w pętli `For`. W efekcie klauzula `Where` nie jest oceniana do momentu uzyskania dostępu do zapytania. Jeśli masz wartości spoza zapytania, które są używane w klauzuli `Where`, upewnij się, że odpowiednia wartość jest używana w klauzuli `Where` w czasie wykonywania zapytania. Aby uzyskać więcej informacji na temat wykonywania zapytań, zobacz [pisanie pierwszego zapytania LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Możesz wywoływać funkcje w klauzuli `Where`, aby wykonać obliczenia lub operację na wartości z bieżącego elementu w kolekcji. Wywołanie funkcji w klauzuli `Where` może spowodować, że zapytanie ma być wykonywane natychmiast po jego zdefiniowaniu, a nie w momencie uzyskiwania do niego dostępu. Aby uzyskać więcej informacji na temat wykonywania zapytań, zobacz [pisanie pierwszego zapytania LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Przykład  
 Następujące wyrażenie zapytania używa klauzuli `From`, aby zadeklarować zmienną zakresu `cust` dla każdego obiektu `Customer` w kolekcji `customers`. Klauzula `Where` używa zmiennej zakresu w celu ograniczenia danych wyjściowych do klientów z określonego regionu. Pętla `For Each` Wyświetla nazwę firmy dla każdego klienta w wyniku zapytania.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie są stosowane operatory logiczne `And` i `Or` w klauzuli `Where`.  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [For Each...Next, instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
