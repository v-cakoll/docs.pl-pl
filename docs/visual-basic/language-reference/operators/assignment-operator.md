---
title: = — Operator (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 230005640b2b494e5413b14ba13a7cb82ee9f22b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [& = — operator](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [* = — Operator](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [+= — Operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [-= — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)  
 [/ = — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [\\= — Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [^ = — Operator](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Operatory porównania](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [Wnioskowanie o typie lokalnym](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
