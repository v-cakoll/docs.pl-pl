---
title: = — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 55b3a8201940a6fec351327aaa88e4ac1ee9246a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-visual-basic"></a>= — Operator (Visual Basic)
Przypisuje wartość do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wszystkie zapisywalne zmiennej lub dowolną właściwość.  
  
 `value`  
 Wszelkie literal, stałej lub wyrażenia.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie znaku równości (`=`) może być zmienną skalarną proste, właściwością lub element tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md). `=` Operator przypisuje wartość jego prawej strony, aby zmienna lub właściwość po lewej stronie.  
  
> [!NOTE]
>  `=` Operator jest również używany jako operator porównania. Aby uzyskać więcej informacji, zobacz [operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## <a name="overloading"></a>Przeciążenie  
 `=` Operator może być przeciążona tylko jako operator porównania relacyjne, a nie jako operatora przypisania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano operator przypisania. Wartość po prawej stronie jest przypisany do zmiennej po lewej stronie.  
  
 [!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [&=, operator](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [*=, operator](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [+=, operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [-= — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)  
 [/ = — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [\\= — Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [^=, operator](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
