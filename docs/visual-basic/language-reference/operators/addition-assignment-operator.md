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
ms.openlocfilehash: 4b8f36397d0f52866ebe9fa188d6b163364aeffc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839023"
---
# <a name="-operator-visual-basic"></a>+= — Operator (Visual Basic)
Dodaje wartość wyrażenia liczbowego wartość liczbową zmiennej lub właściwości, a następnie przypisuje wynik do zmiennej lub właściwości. Może również służyć do łączenia `String` wyrażenie `String` zmiennej lub właściwości i przypisz wynik do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagana. Wszelkie wartości numeryczne lub `String` zmiennej lub właściwości.  
  
 `expression`  
 Wymagana. Wszelkie wartości numeryczne lub `String` wyrażenia.  
  
## <a name="remarks"></a>Uwagi  
 Element w lewej części `+=` operator może być prosta zmienna skalarne, właściwości lub elementu w tablicy. Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `+=` Operator dodaje wartość jego prawej strony do zmiennej lub właściwość po lewej stronie i przypisuje wynik do zmiennej lub właściwość po lewej stronie. `+=` Operator może również służyć do łączenia `String` wyrażenie po jego prawej stronie, aby `String` zmiennej lub właściwość po lewej stronie i przypisz wynik do zmiennej lub właściwość po lewej stronie.  
  
> [!NOTE]
>  Kiedy używasz `+=` operatora, może nie można określić, czy dodanie lub ciąg łączenie wystąpi. Użyj `&=` operatora łączenia, aby wyeliminować niejednoznaczności i zapewnienie automatycznie dokumentowane kodu.  
  
 Ten operator przypisania niejawnie wykonuje rozszerzenia, ale nie zawężających, jeśli środowisko kompilacji Wymusza ścisłą semantykę. Aby uzyskać więcej informacji na temat takiej konwersji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Aby uzyskać więcej informacji na semantyce ograniczeniami i ograniczające, zobacz [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 Jeśli mogą ograniczająca semantyki `+=` operator niejawnie wykonuje szereg konwersji ciągu i liczbowe identyczne z tymi wykonywane przez `+` operatora. Szczegółowe informacje na temat takiej konwersji, [+ — Operator](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## <a name="overloading"></a>Przeciążenie  
 `+` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Przeciążanie `+` operator ma wpływ na zachowanie `+=` operatora. Jeśli kod używa `+=` dla klasy lub struktury, która przeciążenia `+`, należy zrozumieć zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `+=` operatora łączenia wartości jednej zmiennej z inną. Pierwsza część używa `+=` z Zmienne liczbowe, aby dodać jedną wartość na inny. Druga część używa `+=` z `String` zmienne do łączenia jednej wartości z inną. W obu przypadkach wynik jest przypisany do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 Wartość `num1` jest teraz 13 i wartość `str1` jest teraz "103".  
  
## <a name="see-also"></a>Zobacz także

- [+, operator](../../../visual-basic/language-reference/operators/addition-operator.md)
- [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operatory łączenia](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
