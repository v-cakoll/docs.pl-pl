---
title: OrElse, operator
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
ms.openlocfilehash: 3095a11523eeb8ec531c7f312fca74d2a070c92f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401410"
---
# <a name="orelse-operator-visual-basic"></a>OrElse — Operator (Visual Basic)
Wykonuje krótkie rozłączne logiczne rozłączenie dwóch wyrażeń.  
  
## <a name="syntax"></a>Składnia  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Dowolne `Boolean` wyrażenie.  
  
 `expression1`  
 Wymagany. Dowolne `Boolean` wyrażenie.  
  
 `expression2`  
 Wymagany. Dowolne `Boolean` wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Operacja logiczna jest uznawana za *krótką obwód* , jeśli skompilowany kod może pominąć Obliczanie jednego wyrażenia w zależności od wyniku innego wyrażenia. Jeśli wynikiem obliczenia pierwszego wyrażenia jest określenie końcowego wyniku operacji, nie ma potrzeby oceniania drugiego wyrażenia, ponieważ nie można zmienić wyniku końcowego. Krótkie obwody mogą zwiększyć wydajność, jeśli pominięte wyrażenie jest złożone lub jeśli obejmuje wywołania procedur.  
  
 Jeśli w obu wyrażeniach lub obu tych wyrażeń `True` jest wynikiem, `result` jest `True` . W poniższej tabeli przedstawiono sposób `result` określania.  
  
|Jeśli `expression1` jest|I `expression2` jest|Wartość `result` jest|  
|-------------------------|--------------------------|------------------------------|  
|`True`|(nie oceniono)|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a>Typy danych  
 `OrElse`Operator jest zdefiniowany tylko dla [typu danych Boolean](../data-types/boolean-data-type.md). Visual Basic konwertuje każdy operand w miarę potrzeb do `Boolean` przed obliczeniem wyrażenia. Jeśli wynik zostanie przypisany do typu liczbowego, Visual Basic konwertuje go z `Boolean` na ten typ, który `False` staje się `0` i `True` staje się `-1` .
Aby uzyskać więcej informacji, zobacz [konwersje typów logicznych](../data-types/boolean-data-type.md#type-conversions).
  
## <a name="overloading"></a>Przeciążenie  
 Operator [or](or-operator.md) i [operator IsTrue](istrue-operator.md) mogą być *przeciążone*, co oznacza, że Klasa lub struktura mogą definiować ich zachowanie, gdy operand ma typ tej klasy lub struktury. Przeciążanie `Or` operatorów i `IsTrue` wpływa na zachowanie `OrElse` operatora. Jeśli Twój kod używa `OrElse` klasy lub struktury, która przeciąża `Or` i `IsTrue` , pamiętaj o zrozumieniu ich redefiniowanego zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `OrElse` operatora do wykonywania logicznego rozłączenia dwóch wyrażeń. Wynik jest `Boolean` wartością, która reprezentuje, czy jedno z dwóch wyrażeń ma wartość true. Jeśli pierwsze wyrażenie ma wartość `True` , sekunda nie jest szacowana.  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 Powyższy przykład daje wyniki `True` , `True` i `False` odpowiednio. W obliczeniach `firstCheck` drugie wyrażenie nie jest oceniane, ponieważ pierwsze jest już `True` . Drugie wyrażenie jest jednak oceniane w obliczeniach `secondCheck` .  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano `If` instrukcję... `Then` zawierające dwa wywołania procedur. Jeśli pierwsze wywołanie zwraca `True` , Druga procedura nie jest wywoływana. Może to spowodować nieoczekiwane wyniki, jeśli druga procedura wykonuje ważne zadania, które powinny być zawsze wykonywane, gdy ta sekcja kodu zostanie uruchomiona.  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a>Zobacz też

- [Operatory logiczne/bitowe (Visual Basic)](logical-bitwise-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Or, operator](or-operator.md)
- [IsTrue, operator](istrue-operator.md)
- [Operatory logiczne i bitowe w Visual Basic](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
