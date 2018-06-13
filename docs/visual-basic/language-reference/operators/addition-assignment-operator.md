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
ms.openlocfilehash: f12a0560d984f871110c02f1df2c2ec42b68809b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604019"
---
# <a name="-operator-visual-basic"></a>+= — Operator (Visual Basic)
Dodaje wartość wyrażenia liczbowego wartość liczbowa zmiennej lub właściwości i przypisuje wynik do zmiennej lub właściwości. Może również służyć do łączenia `String` wyrażenie `String` zmienna lub właściwość i przypisz wynik do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagana. Wszelkie liczbowe lub `String` zmienna lub właściwość.  
  
 `expression`  
 Wymagana. Wszelkie liczbowe lub `String` wyrażenia.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie `+=` operator może być zmienną skalarną proste, właściwością lub element tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `+=` Operator dodaje wartość jego prawej strony, aby zmienna lub właściwość po lewej stronie, a następnie przypisuje wynik do zmiennej lub właściwości po lewej stronie. `+=` Operator może także służyć do łączenia `String` wyrażenie jego prawej strony, aby `String` zmienna lub właściwość w lewo i przypisz wynik do zmiennej lub po lewej stronie.  
  
> [!NOTE]
>  Jeśli używasz `+=` operatora, może nie można ustalić, czy nastąpi dodanie lub ciąg łączenia. Użyj `&=` operatora łączenia wyeliminować niejednoznaczności oraz zapewnienia automatycznie dokumentowane kodu.  
  
 Ten operator przypisania wykonuje niejawnie rozszerzanie, ale nie zawężanie konwersji, jeśli w środowisku kompilacji wymusza semantykę strict. Aby uzyskać więcej informacji o tych konwersji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Aby uzyskać więcej informacji na semantykę ograniczeniami i ograniczająca, zobacz [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 Jeśli dozwolone ograniczająca semantyki, `+=` operator niejawnie wykonuje szereg konwersji ciągu i liczbowe identyczne jak wykonywane przez `+` operatora. Aby uzyskać więcej informacji o tych konwersji, zobacz [operatora +](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## <a name="overloading"></a>Przeciążenie  
 `+` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Przeciążanie `+` operator wpływa na działanie `+=` operatora. Jeśli używa Twój kod `+=` na klasę lub strukturę, która overloads `+`, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `+=` operatora, aby połączyć z inną wartość jednej zmiennej. Pierwsza część używa `+=` się liczbowych zmienne Dodaj jedną wartość na inny. Druga część używa `+=` z `String` zmienne do łączenia jedną wartość na inną. W obu przypadkach wynik jest przypisany do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#7](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_1.vb)]  
  
 [!code-vb[VbVbalrOperators#8](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addition-assignment-operator_2.vb)]  
  
 Wartość `num1` jest teraz 13 i wartość `str1` jest teraz "103".  
  
## <a name="see-also"></a>Zobacz też  
 [+, operator](../../../visual-basic/language-reference/operators/addition-operator.md)  
 [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Operatory łączenia](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
