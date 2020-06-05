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
ms.openlocfilehash: ff7cbb02a9a10dbe11450491e93fd85fd77b44ba
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370664"
---
# <a name="-operator-visual-basic"></a>\<\<= — Operator (Visual Basic)
Wykonuje arytmetyczne przesunięcie w lewo wartości zmiennej lub właściwości i przypisuje wynik z powrotem do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagany. Zmienna lub właściwość typu całkowitego ( `SByte` , `Byte` ,,, `Short` , `UShort` `Integer` `UInteger` , `Long` lub `ULong` ).  
  
 `amount`  
 Wymagany. Wyrażenie liczbowe typu danych, które jest poszerzane do `Integer` .  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie `<<=` operatora może być prostą zmienną skalarną, właściwością lub elementem tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../modifiers/readonly.md).  
  
 `<<=`Operator najpierw wykonuje arytmetyczne przesunięcie w lewo wartości zmiennej lub właściwości. Następnie operator przypisuje wynik tej operacji z powrotem do tej zmiennej lub właściwości.  
  
 Przesunięcia arytmetyczne nie są cykliczne, co oznacza, że bity przesunięte poza jeden koniec wyniku nie są ponownie wprowadzane na drugim końcu. W przypadku przesunięcia w lewo po lewej stronie bity przesunięte poza zakres typu danych wynik są odrzucane, a pozycje bitowe opuszczone po prawej stronie są ustawione na wartość zero.  
  
## <a name="overloading"></a>Przeciążenie  
 [Operator<< ](left-shift-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Przeciążanie `<<` operatora ma wpływ na zachowanie `<<=` operatora. Jeśli kod korzysta z `<<=` klasy lub struktury, która przeciążania `<<` , należy poznać jej ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora, `<<=` Aby przesunąć wzorzec bitowy `Integer` zmiennej o podanej wartości i przypisać wynik do zmiennej.  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>Zobacz też

- [Operator<< ](left-shift-operator.md)
- [Operatory przypisania](assignment-operators.md)
- [Operatory Bit Shift](bit-shift-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Instrukcje](../../programming-guide/language-features/statements.md)
