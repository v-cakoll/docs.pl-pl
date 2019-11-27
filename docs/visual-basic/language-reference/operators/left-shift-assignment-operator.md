---
title: <<=, operator
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: cc89e0dadc7148b21e695a53a2e746a00ed66441
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350954"
---
# <a name="-operator-visual-basic"></a>\<\<= — operator (Visual Basic)
Wykonuje arytmetyczne przesunięcie w lewo wartości zmiennej lub właściwości i przypisuje wynik z powrotem do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagana. Zmienna lub właściwość typu całkowitego (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`lub `ULong`).  
  
 `amount`  
 Wymagana. Wyrażenie liczbowe typu danych, które poszerza do `Integer`.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie operatora `<<=` może być prostą zmienną skalarną, właściwością lub elementem tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Operator `<<=` najpierw wykonuje arytmetyczne przesunięcie w lewo wartości zmiennej lub właściwości. Następnie operator przypisuje wynik tej operacji z powrotem do tej zmiennej lub właściwości.  
  
 Przesunięcia arytmetyczne nie są cykliczne, co oznacza, że bity przesunięte poza jeden koniec wyniku nie są ponownie wprowadzane na drugim końcu. W przypadku przesunięcia w lewo po lewej stronie bity przesunięte poza zakres typu danych wynik są odrzucane, a pozycje bitowe opuszczone po prawej stronie są ustawione na wartość zero.  
  
## <a name="overloading"></a>Przeciążenie  
 [Operator < <](../../../visual-basic/language-reference/operators/left-shift-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Przeciążanie operatora `<<` ma wpływ na zachowanie operatora `<<=`. Jeśli kod używa `<<=` na klasie lub strukturze, która przeciąża `<<`, należy zapoznać się z jego ponownie zdefiniowanym zachowaniem. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `<<=`, aby przesunąć wzorzec bitowy zmiennej `Integer` po lewej stronie o określoną wartość i przypisać wynik do zmiennej.  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>Zobacz także

- [<<, operator](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operatory Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
