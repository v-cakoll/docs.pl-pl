---
title: OrElse — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 8290e642db3ec76a931bdd2febe427309457bc86
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835241"
---
# <a name="orelse-operator-visual-basic"></a>OrElse — Operator (Visual Basic)
Wykonuje krótkie rozłączne logiczne rozłączenie dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Dowolne wyrażenie `Boolean`.  
  
 `expression1`  
 Wymagany. Dowolne wyrażenie `Boolean`.  
  
 `expression2`  
 Wymagany. Dowolne wyrażenie `Boolean`.  
  
## <a name="remarks"></a>Uwagi  
 Operacja logiczna jest uznawana za *krótką obwód* , jeśli skompilowany kod może pominąć Obliczanie jednego wyrażenia w zależności od wyniku innego wyrażenia. Jeśli wynikiem obliczenia pierwszego wyrażenia jest określenie końcowego wyniku operacji, nie ma potrzeby oceniania drugiego wyrażenia, ponieważ nie można zmienić wyniku końcowego. Krótkie obwody mogą zwiększyć wydajność, jeśli pominięte wyrażenie jest złożone lub jeśli obejmuje wywołania procedur.  
  
 Jeśli lub oba wyrażenia obliczają `True`, `result` jest `True`. W poniższej tabeli przedstawiono sposób określania `result`.  
  
|Jeśli `expression1` to|I `expression2` to|Wartość `result` to|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(nie oceniono)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Typy danych  
 Operator `OrElse` jest zdefiniowany tylko dla [typu danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic konwertuje każdy operand w miarę potrzeb, aby `Boolean` przed szacowaniem wyrażenia. Jeśli wynik zostanie przypisany do typu liczbowego, Visual Basic konwertuje go z `Boolean` na ten typ, który `False` będzie `0` i `True` staje się `-1`.
Aby uzyskać więcej informacji, zobacz [konwersje typów logicznych](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Przeciążenie  
 Operator [or](../../../visual-basic/language-reference/operators/or-operator.md) i [operator IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) mogą być *przeciążone*, co oznacza, że Klasa lub struktura mogą definiować ich zachowanie, gdy operand ma typ tej klasy lub struktury. Przeciążanie operatorów `Or` i `IsTrue` wpływa na zachowanie operatora `OrElse`. Jeśli kod używa `OrElse` na klasie lub strukturze, która przeciąża `Or` i `IsTrue`, należy zrozumieć swoje ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `OrElse` w celu logicznego rozłączenia dwóch wyrażeń. Wynikiem jest wartość `Boolean`, która reprezentuje, czy jedno z dwóch wyrażeń ma wartość true. Jeśli pierwsze wyrażenie jest `True`, sekunda nie jest szacowana.  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 Powyższy przykład daje wyniki `True`, `True` i `False`. W obliczeniach `firstCheck` drugie wyrażenie nie jest oceniane, ponieważ pierwszy jest już `True`. Drugie wyrażenie jest jednak oceniane przy obliczaniu wartości `secondCheck`.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano instrukcję `If`... `Then`, która zawiera dwa wywołania procedur. Jeśli pierwsze wywołanie zwraca `True`, Druga procedura nie jest wywoływana. Może to spowodować nieoczekiwane wyniki, jeśli druga procedura wykonuje ważne zadania, które powinny być zawsze wykonywane, gdy ta sekcja kodu zostanie uruchomiona.  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>Zobacz także

- [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Or, operator](../../../visual-basic/language-reference/operators/or-operator.md)
- [IsTrue, operator](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
