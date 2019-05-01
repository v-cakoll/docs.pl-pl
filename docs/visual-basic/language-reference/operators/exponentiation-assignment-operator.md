---
title: ^= — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: fe5d7b3dcb55192167512e0934e09cff7dfddb6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778524"
---
# <a name="-operator-visual-basic"></a>^= — Operator (Visual Basic)
Podnosi wartość zmiennej lub właściwości do potęgi równej wyrażenia i przypisuje wynik do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagana. Zmienna numeryczna lub właściwość.  
  
 `expression`  
 Wymagana. Dowolne wyrażenie numeryczne.  
  
## <a name="remarks"></a>Uwagi  
 Element w lewej części `^=` operator może być prosta zmienna skalarne, właściwości lub elementu w tablicy. Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `^=` Operator najpierw podnosi wartość zmiennej lub właściwości (po lewej stronie operatora) do potęgi równej wartości wyrażenia (po prawej stronie operatora). Operator następnie przypisuje wynik tej operacji do zmiennej lub właściwości.  
  
 Visual Basic zawsze wykonuje potęgowania w [typ danych Double](../../../visual-basic/language-reference/data-types/double-data-type.md). Operandy dowolnego innego typu są konwertowane na `Double`, a wynik jest zawsze `Double`.  
  
 Wartość `expression` może być ułamkową ujemne lub obu.  
  
## <a name="overloading"></a>Przeciążenie  
 [^ — Operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md) może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Przeciążanie `^` operator ma wpływ na zachowanie `^=` operatora. Jeśli kod używa `^=` dla klasy lub struktury, która przeciążenia `^`, należy zrozumieć zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `^=` operator, aby zwiększyć wartość jednego `Integer` zmiennej do potęgi równej Druga zmienna i przypisz wynik do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Zobacz także

- [^, operator](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
