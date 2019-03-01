---
title: And — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: 090ae67c1e5f04c5d9c4f6aed7f8131d8f830166
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56968858"
---
# <a name="and-operator-visual-basic"></a>And — Operator (Visual Basic)
Wykonuje logiczną na dwóch `Boolean` wyrażeń lub koniunkcję bitową na dwóch wyrażeń liczbowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Wszelkie `Boolean` lub wyrażenia liczbowego. Dla porównania logiczna `result` jest logicznego połączenia dwóch `Boolean` wartości. W przypadku operacji bitowej `result` jest wartość liczbowa reprezentująca koniunkcję bitową na dwóch wzorców bitowych liczbowych.  
  
 `expression1`  
 Wymagana. Wszelkie `Boolean` lub wyrażenia liczbowego.  
  
 `expression2`  
 Wymagana. Wszelkie `Boolean` lub wyrażenia liczbowego.  
  
## <a name="remarks"></a>Uwagi  
 Dla porównania logiczna `result` jest `True` przypadku i tylko wtedy, gdy oba `expression1` i `expression2` zwrócić `True`. W poniższej tabeli przedstawiono sposób `result` jest określana.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  Wartość logiczna porównania `And` operator zawsze ocenia oba wyrażenia, które może obejmować wywołania procedury. [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) wykonuje *zwarcie*, co oznacza, że jeśli `expression1` jest `False`, następnie `expression2` nie jest oceniany.  
  
 Gdy jest stosowany do wartości liczbowych `And` operator wykonuje porównanie bitowe identycznie pozycjonowane bitów w dwóch wyrażeń liczbowych i ustawia bit w odpowiednich `result` zgodnie z poniższą tabelą.  
  
|Jeśli bit w `expression1` jest|I bitu w `expression2` jest|Bit w `result` jest|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
>  Operatory logiczne i bitowe ma niższy priorytet niż inne operatory arytmetyczne i relacyjnych, wszystkie operacje bitowe powinna zostać ujęta w nawiasy, aby zapewnić dokładne wyniki.  
  
## <a name="data-types"></a>Typy danych  
 Jeśli argumenty operacji składać się z jednego `Boolean` wyrażenie i jedno wyrażenie liczbowe języka Visual Basic konwertuje `Boolean` wyrażenia jest wartość liczbowa (-1 dla `True` i od 0 do `False`) i wykonuje bitową operację.  
  
 Dla porównania Boolean, typ danych wyniku jest `Boolean`. Porównanie bitowe, typ danych wynik jest typu liczbowego, odpowiednie dla typów danych `expression1` i `expression2`. Znajdują się w tabeli "Relacyjnych i alternatywy bitowej porównania" [typów danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
> [!NOTE]
>  `And` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `And` operator przeprowadzić logicznego połączenia dwóch wyrażeń. Wynik jest `Boolean` wartość wskazującą, czy oba wyrażenia są `True`.  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 Poprzedni przykład generuje wyniki `True` i `False`, odpowiednio.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `And` operatora, aby wykonać połączenie logiczne na poszczególnych bity dwóch wyrażeń liczbowych. Bit we wzorcu wynik jest ustawiona, jeśli odpowiednich bitów w operandy są ustawione na 1.  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 Poprzedni przykład generuje wyniki, 8, 2 i 0, odpowiednio.  
  
## <a name="see-also"></a>Zobacz także
- [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [AndAlso, operator](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
