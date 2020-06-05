---
title: += — Operator
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: c2ce384901a9f0207e8279a5a07a88600c875e7f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372210"
---
# <a name="-operator-visual-basic"></a>+= — Operator (Visual Basic)
Dodaje wartość wyrażenia liczbowego do wartości zmiennej numerycznej lub właściwości i przypisuje wynik do zmiennej lub właściwości. Można również użyć do łączenia `String` wyrażenia z `String` zmienną lub właściwością i przypisywać wynik do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagany. Dowolna wartość liczbowa lub `String` zmienna lub właściwość.  
  
 `expression`  
 Wymagany. Wszystkie wartości liczbowe lub `String` wyrażenia.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie `+=` operatora może być prostą zmienną skalarną, właściwością lub elementem tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../modifiers/readonly.md).  
  
 `+=`Operator dodaje wartość po prawej stronie do zmiennej lub właściwości po lewej stronie, a następnie przypisuje wynik do zmiennej lub właściwości po jej lewej stronie. `+=`Operatora można także użyć do łączenia `String` wyrażenia po prawej stronie ze `String` zmienną lub właściwości po lewej stronie, a następnie przypisywać wynik do zmiennej lub właściwości po lewej stronie.  
  
> [!NOTE]
> Gdy używasz `+=` operatora, możesz nie być w stanie określić, czy nastąpi próba dodania lub łączenia ciągów. Użyj `&=` operatora do łączenia, aby wyeliminować niejednoznaczność i zapewnić kod służący do samodokumentowania.  
  
 Ten operator przypisania niejawnie wykonuje rozszerzanie, ale nie ogranicza konwersji, jeśli środowisko kompilacji wymusza ścisłą semantykę. Aby uzyskać więcej informacji na temat tych konwersji, zobacz [rozszerzanie i zwężanie konwersji](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Aby uzyskać więcej informacji na temat semantyki ścisłej i ograniczającej, zobacz [Option Strict Statement](../statements/option-strict-statement.md).  
  
 Jeśli dozwolone jest semantyka ograniczająca, `+=` operator niejawnie wykonuje szereg konwersji ciągów i liczb, identycznych z tymi wykonywanymi przez `+` operatora. Aby uzyskać szczegółowe informacje na temat tych konwersji, zobacz [+ operator](addition-operator.md).  
  
## <a name="overloading"></a>Przeciążenie  
 `+`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Przeciążanie `+` operatora ma wpływ na zachowanie `+=` operatora. Jeśli kod korzysta z `+=` klasy lub struktury, która przeciążania `+` , należy poznać jej ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora, `+=` Aby połączyć wartość jednej zmiennej z inną. Pierwsza część używa `+=` ze zmiennymi liczbowymi, aby dodać jedną wartość do innej. Druga część używa `+=` ze `String` zmiennymi do łączenia jednej wartości z inną. W obu przypadkach wynik jest przypisywany do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 Wartość `num1` to teraz 13, a wartość `str1` to teraz "103".  
  
## <a name="see-also"></a>Zobacz też

- [+ — Operator](addition-operator.md)
- [Operatory przypisania](assignment-operators.md)
- [Operatory arytmetyczne](arithmetic-operators.md)
- [Concatenation — Operatory](concatenation-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Instrukcje](../../programming-guide/language-features/statements.md)
