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
ms.openlocfilehash: 5632e69039baebb3d1f1fd90c04586d9e50fe40f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834507"
---
# <a name="where-clause-visual-basic"></a>Where — Klauzula (Visual Basic)
Określa warunek filtrowania dla zapytania.  
  
## <a name="syntax"></a>Składnia  
  
```  
Where condition  
```  
  
## <a name="parts"></a>Części  
 `condition`  
 Wymagana. Wyrażenie, które określa, czy wartości bieżącego elementu w kolekcji są uwzględnione w zbiorze danych wyjściowych. Wyrażenia musi być `Boolean` wartość lub równoważny `Boolean` wartość. Jeśli warunek jest `True`, element jest uwzględniony w wyniku kwerendy; w przeciwnym razie, element jest wykluczony z wyniku zapytania.  
  
## <a name="remarks"></a>Uwagi  
 `Where` Klauzuli pozwala na filtrowanie zapytania o dane, wybierając tylko te elementy, które spełniają określone kryteria. Elementy, których wartości powodują `Where` klauzuli na `True` znajdują się w wyniku zapytania; inne elementy są wyłączone. Wyrażenie, które jest używane w `Where` klauzuli musi zwrócić `Boolean` lub równoważny `Boolean`, takie jak liczba całkowita, która daje w wyniku `False` po jego wartość wynosi zero. Można połączyć wiele wyrażeń w `Where` klauzuli przy użyciu operatorów logicznych, takich jak `And`, `Or`, `AndAlso`, `OrElse`, `Is`, i `IsNot`.  
  
 Domyślnie wyrażenia zapytania nie są sprawdzane, dopóki nie są one używane — na przykład, gdy znajdują się powiązanych z danymi lub iterowany przy użyciu w `For` pętli. W rezultacie `Where` klauzula nie jest oceniany, dopóki nie odbywa się zapytania. Jeśli masz zewnętrzne w stosunku do zapytania, które są używane w wartości `Where` klauzuli, upewnij się, że odpowiednie wartość jest używana w `Where` klauzuli w czasie wykonywania zapytania. Aby uzyskać więcej informacji na temat wykonywania zapytań, zobacz [Your pierwszego zapytania LINQ pisania](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Można wywołać funkcji w ramach `Where` klauzuli wykonać obliczenia lub operacji na podstawie wartości z bieżącego elementu w kolekcji. Wywoływanie funkcji w `Where` klauzuli może spowodować, że zapytanie jest wykonywane natychmiast, gdy jest on zdefiniowany zamiast, gdy jest on dostępny. Aby uzyskać więcej informacji na temat wykonywania zapytań, zobacz [Your pierwszego zapytania LINQ pisania](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie używa wyrażenia `From` klauzulę, aby zadeklarować zmienną zakresu `cust` dla każdego `Customer` obiektu `customers` kolekcji. `Where` Klauzuli używa zmiennej zakresu, aby uniemożliwić klientom określonego regionu danych wyjściowych. `For Each` Pętli Wyświetla nazwę firmy, dla każdego klienta, w wyniku zapytania.  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `And` i `Or` operatory logiczne w `Where` klauzuli.  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do LINQ w Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Zapytania](../../../visual-basic/language-reference/queries/index.md)
- [From, klauzula](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select, klauzula](../../../visual-basic/language-reference/queries/select-clause.md)
- [For Each...Next, instrukcja](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
