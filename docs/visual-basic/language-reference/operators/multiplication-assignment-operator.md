---
title: '*= — Operator (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: 3aa1d563b9657d4e80425b8c2d29e069ca2ef06a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601886"
---
# <a name="-operator-visual-basic"></a>*= — Operator (Visual Basic)
Mnoży wartość zmiennej lub właściwości przez wartość wyrażenia i przypisuje wynik do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
variableorproperty *= expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagana. Zmienna numeryczna lub właściwość.  
  
 `expression`  
 Wymagana. Dowolne wyrażenie numeryczne.  
  
## <a name="remarks"></a>Uwagi  
 Element w lewej części `*=` operator może być prosta zmienna skalarne, właściwości lub elementu w tablicy. Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `*=` Operator najpierw Mnoży wartość wyrażenia (po prawej stronie operatora) przez wartość zmiennej lub właściwości (po lewej stronie operatora). Operator następnie przypisuje wynik tej operacji do zmiennej lub właściwości.  
  
## <a name="overloading"></a>Przeciążenie  
 [* — Operator](../../../visual-basic/language-reference/operators/multiplication-operator.md) może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Przeciążanie `*` operator ma wpływ na zachowanie `*=` operatora. Jeśli kod używa `*=` dla klasy lub struktury, która przeciążenia `*`, należy zrozumieć zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `*=` operatora przez jeden `Integer` zmiennej przez drugi i przypisz wynik do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#5](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/multiplication-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [*, operator](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
