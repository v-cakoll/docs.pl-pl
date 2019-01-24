---
title: '&gt;&gt;= — Operator (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: fbfdd471a5241234780c05c0f1a045db2476f773
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570780"
---
# <a name="gtgt-operator-visual-basic"></a>&gt;&gt;= — Operator (Visual Basic)
Wykonuje arytmetyczne przesunięcie w prawo na wartość zmiennej lub właściwości, a następnie przypisuje wynik do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagana. Zmiennej lub właściwości typu całkowitego (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, lub `ULong`).  
  
 `amount`  
 Wymagana. Wyrażenia liczbowego typu danych, która rozszerza się na `Integer`.  
  
## <a name="remarks"></a>Uwagi  
 Element w lewej części `>>=` operator może być prosta zmienna skalarne, właściwości lub elementu w tablicy. Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `>>=` Operator najpierw wykonuje arytmetyczne przesunięcie w prawo na wartość zmiennej lub właściwości. Operator następnie przypisuje wynik tej operacji do zmiennej lub właściwości.  
  
 Arytmetycznego przesunięcia nie są cykliczne, co oznacza, że bity przesunięte poza jednym końcu wynik nie są ponownie wprowadzone po drugiej stronie. W arytmetyczne przesunięcie w prawo bity przesunięte poza Pozycja bitu po prawej stronie są odrzucane i skrajnie po lewej stronie bit jest propagowana do pozycji bitów zwolnione w wyniku po lewej stronie. Oznacza to, że jeśli `variableorproperty` ma wartość ujemną, opuszczone pozycje są ustawione na jeden. Jeśli `variableorproperty` jest dodatnia, lub jeśli jego typem jest typ bez znaku, pozycje opuszczonych zostaną ustawione na zero.  
  
## <a name="overloading"></a>Przeciążenie  
 [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Przeciążanie `>>` operator ma wpływ na zachowanie `>>=` operatora. Jeśli kod używa `>>=` dla klasy lub struktury, która przeciążenia `>>`, należy zrozumieć zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `>>=` operatora przesunięcia wzorca bitowego `Integer` zmiennej bezpośrednio przez określony przedział i przypisz wynik do zmiennej.  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [>>, operator](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operatory Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
