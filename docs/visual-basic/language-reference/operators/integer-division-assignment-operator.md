---
title: '\= — Operator (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: bcfc59efda0627f83713fe9ada24cedc20d823e3
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2018
ms.locfileid: "39198211"
---
# <a name="-operator"></a>\\= — Operator
Dzieli wartość zmiennej lub właściwości przez wartość wyrażenia i przypisuje wyniku liczby całkowitej do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
variableorproperty \= expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagane. Zmienna numeryczna lub właściwość.  
  
 `expression`  
 Wymagane. Dowolne wyrażenie numeryczne.  
  
## <a name="remarks"></a>Uwagi  
 Element w lewej części `\=` operator może być prosta zmienna skalarne, właściwości lub elementu w tablicy. Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `\=` Operator dzieli wartość zmiennej lub właściwość po lewej stronie według wartości w jego prawej stronie, a następnie przypisuje wyniku liczby całkowitej, zmienna lub właściwość po lewej stronie  
  
 Aby uzyskać więcej informacji na temat dzielenie liczby całkowitej, zobacz [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).  
  
## <a name="overloading"></a>Przeciążenie  
 `\` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Przeciążanie `\` operator ma wpływ na zachowanie `\=` operatora. Jeśli kod używa `\=` dla klasy lub struktury, która przeciążenia `\`, należy zrozumieć zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `\=` operator podziału jeden `Integer` zmiennej, sekundy i Przypisz liczbę całkowitą wyniku do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#19](codesnippet/VisualBasic/integer-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [\ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [/ = — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
