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
ms.openlocfilehash: c8fb990533d9db90eacf76aff424ea3cf96b0875
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970522"
---
# <a name="-operator-visual-basic"></a>/= — Operator (Visual Basic)
Dzieli wartość zmiennej lub właściwości przez wartość wyrażenia i przypisuje zmiennoprzecinkowych wynik do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagana. Zmienna numeryczna lub właściwość.  
  
 `expression`  
 Wymagana. Dowolne wyrażenie numeryczne.  
  
## <a name="remarks"></a>Uwagi  
 Element w lewej części `/=` operator może być prosta zmienna skalarne, właściwości lub elementu w tablicy. Zmiennej lub właściwości nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `/=` Operator najpierw dzieli wartość zmiennej lub właściwości (po lewej stronie operatora) przez wartość wyrażenia (po prawej stronie operatora). Operator następnie przypisuje zmiennoprzecinkowych wynikiem tej operacji do zmiennej lub właściwości.  
  
 Ta instrukcja przypisuje `Double` wartość do zmiennej lub właściwość po lewej stronie. Jeśli `Option Strict` jest `On`, `variableorproperty` musi być `Double`. Jeśli `Option Strict` jest `Off`, Visual Basic wywołujący niejawną konwersję i przypisuje wartość wynikową do `variableorproperty`, za pomocą możliwy błąd w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [rozszerzanie i zwężanie konwersji](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) i [Option Strict — instrukcja](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Przeciążenie  
 [/ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Przeciążanie `/` operator ma wpływ na zachowanie `/=` operatora. Jeśli kod używa `/=` dla klasy lub struktury, która przeciążenia `/`, należy zrozumieć zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `/=` operator podziału jeden `Integer` zmiennej przez drugi i przypisz iloraz do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Zobacz także
- [/ — Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [\\= — Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
