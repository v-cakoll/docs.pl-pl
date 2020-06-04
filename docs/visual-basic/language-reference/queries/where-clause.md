---
title: Where, klauzula
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: b80bb047551dee8ab23cfac06b961996992d69b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359544"
---
# <a name="where-clause-visual-basic"></a>Where — Klauzula (Visual Basic)
Określa warunek filtrowania dla zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
Where condition  
```  
  
## <a name="parts"></a>Części  
 `condition`  
 Wymagany. Wyrażenie określające, czy wartości bieżącego elementu w kolekcji są uwzględniane w kolekcji wyjściowej. Wyrażenie musi być szacowane do `Boolean` wartości lub równoważnej `Boolean` wartości. Jeśli warunek ma wartość `True` , element zostanie uwzględniony w wyniku zapytania; w przeciwnym razie element jest wykluczony z wyniku zapytania.  
  
## <a name="remarks"></a>Uwagi  
 `Where`Klauzula umożliwia filtrowanie danych zapytania przez wybranie tylko elementów spełniających określone kryteria. Elementy, których wartości powodują, że `Where` klauzula do obliczenia, `True` są uwzględniane w wyniku zapytania; inne elementy są wykluczone. Wyrażenie, które jest używane w `Where` klauzuli musi być szacowane do `Boolean` lub równoważne `Boolean` , takie jak liczba całkowita, która daje w `False` wyniku wartość zero. Można połączyć wiele wyrażeń w `Where` klauzuli przy użyciu operatorów logicznych, takich jak `And` , `Or` ,, `AndAlso` , `OrElse` `Is` i `IsNot` .  
  
 Domyślnie wyrażenia zapytania nie są oceniane do momentu uzyskania dostępu do nich, na przykład gdy są one powiązane z danymi lub powtarzane przez `For` pętlę. W związku z tym `Where` klauzula nie jest oceniana do momentu uzyskania dostępu do zapytania. Jeśli masz wartości spoza zapytania, które są używane w `Where` klauzuli, upewnij się, że odpowiednia wartość jest używana w `Where` klauzuli w czasie wykonywania zapytania. Aby uzyskać więcej informacji na temat wykonywania zapytań, zobacz [pisanie pierwszego zapytania LINQ](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Możesz wywoływać funkcje w `Where` klauzuli, aby wykonać obliczenia lub operację na wartości z bieżącego elementu w kolekcji. Wywołanie funkcji w `Where` klauzuli może spowodować, że zapytanie ma być wykonywane natychmiast po jego zdefiniowaniu, a nie w momencie uzyskiwania do niego dostępu. Aby uzyskać więcej informacji na temat wykonywania zapytań, zobacz [pisanie pierwszego zapytania LINQ](../../programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Przykład  
 Następujące wyrażenie zapytania używa klauzuli, `From` Aby zadeklarować zmienną zakresu `cust` dla każdego `Customer` obiektu w `customers` kolekcji. `Where`Klauzula używa zmiennej zakresu w celu ograniczenia danych wyjściowych do klientów z określonego regionu. `For Each`Pętla wyświetla nazwę firmy dla każdego klienta w wyniku zapytania.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie są `And` stosowane `Or` Operatory logiczne w `Where` klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do LINQ w Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](index.md)
- [Klauzula from](from-clause.md)
- [SELECT — klauzula](select-clause.md)
- [For Each...Next, instrukcja](../statements/for-each-next-statement.md)
