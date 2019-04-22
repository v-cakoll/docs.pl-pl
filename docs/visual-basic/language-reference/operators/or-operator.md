---
title: Or — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 0277b6f24e62ed5f0cad3dae225c86fffc4c09b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835300"
---
# <a name="or-operator-visual-basic"></a>Or — Operator (Visual Basic)
Dokonuje logicznego rozłączenia dwóch `Boolean` wyrażeń lub bitowego rozłączenia dwóch wyrażeń liczbowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Wszelkie `Boolean` lub wyrażenia liczbowego. Aby uzyskać `Boolean` porównania, `result` jest łączną sumę logiczną na dwóch `Boolean` wartości. W przypadku operacji bitowej `result` jest wartość liczbowa reprezentująca włącznie bitowego rozłączenia dwóch wzorców bitowych liczbowych.  
  
 `expression1`  
 Wymagana. Wszelkie `Boolean` lub wyrażenia liczbowego.  
  
 `expression2`  
 Wymagana. Wszelkie `Boolean` lub wyrażenia liczbowego.  
  
## <a name="remarks"></a>Uwagi  
 Dla `Boolean` porównania, `result` jest `False` przypadku i tylko wtedy, gdy oba `expression1` i `expression2` zwrócić `False`. W poniższej tabeli przedstawiono sposób `result` jest określana.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  W `Boolean` porównania, `Or` operator zawsze ocenia oba wyrażenia, które może obejmować wywołania procedury. [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) wykonuje *zwarcie*, co oznacza, że jeśli `expression1` jest `True`, następnie `expression2` nie jest oceniany.  
  
 W przypadku operacji bitowej `Or` operator wykonuje porównanie bitowe identycznie pozycjonowane bitów w dwóch wyrażeń liczbowych i ustawia bit w odpowiednich `result` zgodnie z poniższą tabelą.  
  
|Jeśli bit w `expression1` jest|I bitu w `expression2` jest|Bit w `result` jest|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  Operatory logiczne i bitowe ma niższy priorytet niż inne operatory arytmetyczne i relacyjnych, wszystkie operacje bitowe powinna zostać ujęta w nawiasy, aby zapewnić dokładne wykonanie.  
  
## <a name="data-types"></a>Typy danych  
 Jeśli argumenty operacji składać się z jednego `Boolean` wyrażenie i jedno wyrażenie liczbowe języka Visual Basic konwertuje `Boolean` wyrażenia jest wartość liczbowa (-1 dla `True` i od 0 do `False`) i wykonuje bitową operację.  
  
 Aby uzyskać `Boolean` jest typ danych wyniku porównania, `Boolean`. Porównanie bitowe, typ danych wynik jest typu liczbowego, odpowiednie dla typów danych `expression1` i `expression2`. Znajdują się w tabeli "Relacyjnych i alternatywy bitowej porównania" [typów danych z wyników operatora](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).  
  
## <a name="overloading"></a>Przeciążenie  
 `Or` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Or` operatora, aby wykonać łączną sumę logiczną na dwóch wyrażeń. Wynik jest `Boolean` wartość wskazującą, czy jest jeden z dwóch wyrażeń `True`.  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 Poprzedni przykład generuje wyniki `True`, `True`, i `False`, odpowiednio.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Or` operatora, aby wykonać łączną sumę logiczną na poszczególnych bity dwóch wyrażeń liczbowych. Bit we wzorcu wynik jest ustawiona, jeśli albo odpowiednich bitów w operandów jest ustawiona na 1.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 Poprzedni przykład generuje wyniki, 10, 14 oraz 14, odpowiednio.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [OrElse, operator](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
