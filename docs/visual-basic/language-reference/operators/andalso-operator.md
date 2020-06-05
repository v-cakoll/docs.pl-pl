---
title: AndAlso, operator
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
ms.openlocfilehash: 8b67897956a21d06d465cf206856354d2e3f9d68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371937"
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
|`result`|Wymagany. Dowolne `Boolean` wyrażenie. Wynik jest `Boolean` wynikiem porównania dwóch wyrażeń.|  
|`expression1`|Wymagany. Dowolne `Boolean` wyrażenie.|  
|`expression2`|Wymagany. Dowolne `Boolean` wyrażenie.|  
  
## <a name="remarks"></a>Uwagi  
 Operacja logiczna jest uznawana za *krótką obwód* , jeśli skompilowany kod może pominąć Obliczanie jednego wyrażenia w zależności od wyniku innego wyrażenia. Jeśli wynikiem obliczenia pierwszego wyrażenia jest określenie końcowego wyniku operacji, nie ma potrzeby oceniania drugiego wyrażenia, ponieważ nie można zmienić wyniku końcowego. Krótkie obwody mogą zwiększyć wydajność, jeśli pominięte wyrażenie jest złożone lub jeśli obejmuje wywołania procedur.  
  
 Jeśli oba wyrażenia są szacowane do `True` , `result` is `True` . W poniższej tabeli przedstawiono sposób `result` określania.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|(nie oceniono)|`False`|  
  
## <a name="data-types"></a>Typy danych  
 `AndAlso`Operator jest zdefiniowany tylko dla [typu danych Boolean](../data-types/boolean-data-type.md). Visual Basic konwertuje każdy operand w miarę potrzeb do `Boolean` przed obliczeniem wyrażenia. Jeśli wynik zostanie przypisany do typu liczbowego, Visual Basic konwertuje go z `Boolean` na ten typ, który `False` staje się `0` i `True` staje się `-1` .
Aby uzyskać więcej informacji, zobacz [konwersje typów logicznych](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Przeciążenie  
 Operator [and](and-operator.md) i [operator IsFalse](isfalse-operator.md) mogą być *przeciążone*, co oznacza, że Klasa lub struktura mogą definiować ich zachowanie, gdy operand ma typ tej klasy lub struktury. Przeciążanie `And` operatorów i `IsFalse` wpływa na zachowanie `AndAlso` operatora. Jeśli Twój kod używa `AndAlso` klasy lub struktury, która przeciąża `And` i `IsFalse` , pamiętaj o zrozumieniu ich redefiniowanego zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `AndAlso` operatora do wykonywania logicznego połączenia dwóch wyrażeń. Wynik jest `Boolean` wartością, która reprezentuje, czy całe przyłączone wyrażenie ma wartość true. Jeśli pierwsze wyrażenie ma wartość `False` , sekunda nie jest szacowana.  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 Powyższy przykład daje wyniki `True` , `False` i, `False` odpowiednio. W obliczeniach `secondCheck` drugie wyrażenie nie jest oceniane, ponieważ pierwsze jest już `False` . Drugie wyrażenie jest jednak oceniane w obliczeniach `thirdCheck` .  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje `Function` procedurę, która wyszukuje daną wartość wśród elementów tablicy. Jeśli tablica jest pusta lub długość tablicy została przekroczona, `While` instrukcja nie przetestuje elementu Array względem wartości wyszukiwania.  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a>Zobacz też

- [Operatory logiczne/bitowe (Visual Basic)](logical-bitwise-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [And, operator](and-operator.md)
- [IsFalse, operator](isfalse-operator.md)
- [Operatory logiczne i bitowe w Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
