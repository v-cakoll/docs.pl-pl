---
title: '&amp; = — operator (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: 82d791e5d66c301442c99d2cc73e3172c3e30f17
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591638"
---
# <a name="amp-operator-visual-basic"></a>&amp; = — operator (Visual Basic)
Łączy wyrażenie `String` z zmienną lub właściwością `String` i przypisuje wynik do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagany. Dowolna `String` zmienna lub właściwość.  
  
 `expression`  
 Wymagany. Dowolne wyrażenie `String`.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie operatora `&=` może być prostą zmienną skalarną, właściwością lub elementem tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md). Operator `&=` łączy wyrażenie `String` po prawej stronie z zmienną `String` lub właściwością po lewej stronie, a następnie przypisuje wynik do zmiennej lub właściwości po lewej stronie.  
  
## <a name="overloading"></a>Przeciążenie  
 [Operator &](../../../visual-basic/language-reference/operators/concatenation-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Przeciążanie operatora `&` wpływa na zachowanie operatora `&=`. Jeśli kod używa `&=` na klasie lub strukturze, która przeciąża `&`, należy zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `&=`, aby połączyć dwie zmienne `String` i przypisać wynik do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [&, operator](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [+=, operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operatory łączenia](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
