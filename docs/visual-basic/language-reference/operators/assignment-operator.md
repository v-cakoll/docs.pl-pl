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
ms.openlocfilehash: d260dffb7175e9dddcbf9acb75415f5f973727e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962014"
---
# <a name="-operator-visual-basic"></a>= — Operator (Visual Basic)
Przypisuje wartość do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Dowolna zapisywalna zmienna lub Każda właściwość.  
  
 `value`  
 Dowolny literał, stała lub wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie znaku równości (`=`) może być prostą zmienną skalarną, właściwością lub elementem tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md). `=` Operator przypisuje wartość po prawej stronie do zmiennej lub właściwości po jej lewej stronie.  
  
> [!NOTE]
> `=` Operator jest również używany jako operator porównania. Aby uzyskać szczegółowe informacje, zobacz [Operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## <a name="overloading"></a>Przeciążenie  
 `=` Operator może być przeciążony tylko jako operator porównania relacyjnego, a nie jako operator przypisania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład demonstruje operator przypisania. Wartość po prawej stronie jest przypisana do zmiennej po lewej stronie.  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Zobacz także

- [&=, operator](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [*=, operator](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [+=, operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [-= — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [Operator/= (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\\= — Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [^=, operator](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
- [Operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
