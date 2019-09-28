---
title: /= — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: b4855e8270a329f9345339060a323b5ca9cd9792
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592176"
---
# <a name="-operator-visual-basic"></a>/= — Operator (Visual Basic)
Dzieli wartość zmiennej lub właściwości przez wartość wyrażenia i przypisuje wynik zmiennoprzecinkowy do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagany. Dowolna zmienna lub właściwość numeryczna.  
  
 `expression`  
 Wymagany. Dowolne wyrażenie liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie operatora `/=` może być prostą zmienną skalarną, właściwością lub elementem tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Operator `/=` w pierwszej kolejności dzieli wartość zmiennej lub właściwości (po lewej stronie operatora) przez wartość wyrażenia (po prawej stronie operatora). Następnie operator przypisuje wynik zmiennoprzecinkowy tej operacji do zmiennej lub właściwości.  
  
 Ta instrukcja przypisuje wartość `Double` do zmiennej lub właściwości po lewej stronie. Jeśli `Option Strict` jest `On`, `variableorproperty` musi być `Double`. Jeśli `Option Strict` jest `Off`, Visual Basic wykonuje niejawną konwersję i przypisze wartość wyniku do `variableorproperty`, z możliwym błędem w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) oraz [ścisłe instrukcje Option](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Przeciążenie  
 [Operator/(Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Przeciążanie operatora `/` wpływa na zachowanie operatora `/=`. Jeśli kod używa `/=` na klasie lub strukturze, która przeciąża `/`, należy zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `/=` w celu podzielenia jednej zmiennej `Integer` przez sekundę i przypisanie ilorazu do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Zobacz także

- [/— Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [\\ = — operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
