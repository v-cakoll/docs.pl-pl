---
title: += — Operator (Visual Basic)
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
ms.openlocfilehash: f615df50643912beb12eb89d80b922fc30a3e6df
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944471"
---
# <a name="-operator-visual-basic"></a>+= — Operator (Visual Basic)
Dodaje wartość wyrażenia liczbowego do wartości zmiennej numerycznej lub właściwości i przypisuje wynik do zmiennej lub właściwości. Można również użyć do łączenia `String` wyrażenia `String` z zmienną lub właściwością i przypisywać wynik do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagany. Dowolna wartość `String` liczbowa lub zmienna lub właściwość.  
  
 `expression`  
 Wymagana. Wszystkie wartości liczbowe `String` lub wyrażenia.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie `+=` operatora może być prostą zmienną skalarną, właściwością lub elementem tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `+=` Operator dodaje wartość po prawej stronie do zmiennej lub właściwości po lewej stronie, a następnie przypisuje wynik do zmiennej lub właściwości po jej lewej stronie. Operatora można także użyć do łączenia `String` wyrażenia `String` po prawej stronie ze zmienną lub właściwości po lewej stronie, a następnie przypisywać wynik do zmiennej lub właściwości po lewej stronie. `+=`  
  
> [!NOTE]
> Gdy używasz `+=` operatora, możesz nie być w stanie określić, czy nastąpi próba dodania lub łączenia ciągów. `&=` Użyj operatora do łączenia, aby wyeliminować niejednoznaczność i zapewnić kod służący do samodokumentowania.  
  
 Ten operator przypisania niejawnie wykonuje rozszerzanie, ale nie ogranicza konwersji, jeśli środowisko kompilacji wymusza ścisłą semantykę. Aby uzyskać więcej informacji na temat tych konwersji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Aby uzyskać więcej informacji na temat semantyki ścisłej i ograniczającej, zobacz [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 Jeśli dozwolone jest semantyka ograniczająca, `+=` operator niejawnie wykonuje szereg konwersji ciągów i liczb, identycznych z tymi wykonywanymi `+` przez operatora. Aby uzyskać szczegółowe informacje na temat tych konwersji, zobacz [+ operator](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## <a name="overloading"></a>Przeciążenie  
 Operator może być przeciążony, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. `+` Przeciążanie `+` operatora ma wpływ na zachowanie `+=` operatora. Jeśli kod korzysta `+=` z klasy lub struktury, która przeciążania `+`, należy poznać jej ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora, `+=` aby połączyć wartość jednej zmiennej z inną. Pierwsza część używa `+=` ze zmiennymi liczbowymi, aby dodać jedną wartość do innej. Druga część używa `+=` ze `String` zmiennymi do łączenia jednej wartości z inną. W obu przypadkach wynik jest przypisywany do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 Wartość `num1` to teraz 13, a `str1` wartość to teraz "103".  
  
## <a name="see-also"></a>Zobacz także

- [+, operator](../../../visual-basic/language-reference/operators/addition-operator.md)
- [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operatory łączenia](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
