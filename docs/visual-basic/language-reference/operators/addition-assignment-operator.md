---
title: +=, operator
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
ms.openlocfilehash: 31a6da163061b905b8ffddcfc4b44978f5cdd55e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350308"
---
# <a name="-operator-visual-basic"></a>+= — Operator (Visual Basic)
Dodaje wartość wyrażenia liczbowego do wartości zmiennej numerycznej lub właściwości i przypisuje wynik do zmiennej lub właściwości. Można również użyć do łączenia wyrażenia `String` ze zmienną `String` lub właściwością i przypisywać wynik do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagany. Dowolna lub `String` zmienna lub właściwość.  
  
 `expression`  
 Wymagany. Dowolne wyrażenie liczbowe lub `String`.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie operatora `+=` może być prostą zmienną skalarną, właściwością lub elementem tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Operator `+=` dodaje wartość po prawej stronie do zmiennej lub właściwości po lewej stronie, a następnie przypisuje wynik do zmiennej lub właściwości po jej lewej stronie. Operatora `+=` można również użyć do łączenia wyrażenia `String` po prawej stronie ze zmienną `String` lub właściwości po lewej stronie, a następnie przypisać wynik do zmiennej lub właściwości po lewej stronie.  
  
> [!NOTE]
> Gdy używasz operatora `+=`, możesz nie być w stanie określić, czy nastąpi próba dodania lub łączenia ciągów. Użyj operatora `&=`, aby nawiązać połączenie w celu wyeliminowania niejednoznaczności i zapewnienia kodu samoobsługowego.  
  
 Ten operator przypisania niejawnie wykonuje rozszerzanie, ale nie ogranicza konwersji, jeśli środowisko kompilacji wymusza ścisłą semantykę. Aby uzyskać więcej informacji na temat tych konwersji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Aby uzyskać więcej informacji na temat semantyki ścisłej i ograniczającej, zobacz [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 Jeśli dozwolone jest semantyka ograniczająca, operator `+=` niejawnie wykonuje szereg konwersji ciągów i liczbowych identycznych z tymi wykonywanymi przez operator `+`. Aby uzyskać szczegółowe informacje na temat tych konwersji, zobacz [+ operator](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## <a name="overloading"></a>Przeciążenie  
 Operator `+` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Przeciążanie operatora `+` ma wpływ na zachowanie operatora `+=`. Jeśli kod używa `+=` na klasie lub strukturze, która przeciąża `+`, należy zapoznać się z jego ponownie zdefiniowanym zachowaniem. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `+=`, aby połączyć wartość jednej zmiennej z inną. Pierwsza część używa `+=` ze zmiennymi numerycznymi w celu dodania jednej wartości do innej. Druga część używa `+=` ze zmiennymi `String` do łączenia jednej wartości z inną. W obu przypadkach wynik jest przypisywany do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 Wartość `num1` to teraz 13, a wartość `str1` to teraz "103".  
  
## <a name="see-also"></a>Zobacz także

- [+, operator](../../../visual-basic/language-reference/operators/addition-operator.md)
- [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operatory łączenia](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
