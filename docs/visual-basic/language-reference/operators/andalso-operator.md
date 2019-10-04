---
title: AndAlso — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: a52f598c8a7c7a79b0f2436f1add7b3eb5d5261b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835228"
---
# <a name="andalso-operator-visual-basic"></a>AndAlso — Operator (Visual Basic)
Wykonuje krótkie koniunkcje logiczne dla dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`result`|Wymagany. Dowolne wyrażenie `Boolean`. Wynikiem porównania dwóch wyrażeń jest wynik `Boolean`.|  
|`expression1`|Wymagany. Dowolne wyrażenie `Boolean`.|  
|`expression2`|Wymagany. Dowolne wyrażenie `Boolean`.|  
  
## <a name="remarks"></a>Uwagi  
 Operacja logiczna jest uznawana za *krótką obwód* , jeśli skompilowany kod może pominąć Obliczanie jednego wyrażenia w zależności od wyniku innego wyrażenia. Jeśli wynikiem obliczenia pierwszego wyrażenia jest określenie końcowego wyniku operacji, nie ma potrzeby oceniania drugiego wyrażenia, ponieważ nie można zmienić wyniku końcowego. Krótkie obwody mogą zwiększyć wydajność, jeśli pominięte wyrażenie jest złożone lub jeśli obejmuje wywołania procedur.  
  
 Jeśli oba wyrażenia są szacowane do `True`, `result` jest `True`. W poniższej tabeli przedstawiono sposób określania `result`.  
  
|Jeśli `expression1` to|I `expression2` to|Wartość `result` to|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(nie oceniono)|`False`|  
  
## <a name="data-types"></a>Typy danych  
 Operator `AndAlso` jest zdefiniowany tylko dla [typu danych Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Visual Basic konwertuje każdy operand w miarę potrzeb, aby `Boolean` przed szacowaniem wyrażenia. Jeśli wynik zostanie przypisany do typu liczbowego, Visual Basic konwertuje go z `Boolean` na ten typ, który `False` będzie `0` i `True` staje się `-1`.
Aby uzyskać więcej informacji, zobacz [konwersje typów logicznych](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Przeciążenie  
 Operator [and](../../../visual-basic/language-reference/operators/and-operator.md) i [operator IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md) mogą być *przeciążone*, co oznacza, że Klasa lub struktura mogą definiować ich zachowanie, gdy operand ma typ tej klasy lub struktury. Przeciążanie operatorów `And` i `IsFalse` wpływa na zachowanie operatora `AndAlso`. Jeśli kod używa `AndAlso` na klasie lub strukturze, która przeciąża `And` i `IsFalse`, należy zrozumieć swoje ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `AndAlso` do wykonywania logicznego połączenia dwóch wyrażeń. Wynikiem jest wartość `Boolean`, która reprezentuje, czy całe przyłączone wyrażenie ma wartość true. Jeśli pierwsze wyrażenie jest `False`, sekunda nie jest szacowana.  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 W powyższym przykładzie wyniki są odpowiednio `True`, `False` i `False`. W obliczeniach `secondCheck` drugie wyrażenie nie jest oceniane, ponieważ pierwszy jest już `False`. Drugie wyrażenie jest jednak oceniane przy obliczaniu wartości `thirdCheck`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje procedurę `Function`, która wyszukuje daną wartość wśród elementów tablicy. Jeśli tablica jest pusta lub długość tablicy została przekroczona, instrukcja `While` nie przetestuje elementu Array względem wartości wyszukiwania.  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>Zobacz także

- [Operatory logiczne/bitowe (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [And, operator](../../../visual-basic/language-reference/operators/and-operator.md)
- [IsFalse, operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
