---
title: Operator -=
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: 4f403cd8a28f8d9d0ba1d24b0792a352a9c961db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406408"
---
# <a name="--operator-visual-basic"></a>-= — Operator (Visual Basic)
Odejmuje wartość wyrażenia od wartości zmiennej lub właściwości i przypisuje wynik do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagany. Dowolna zmienna lub właściwość numeryczna.  
  
 `expression`  
 Wymagany. Dowolne wyrażenie liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie `-=` operatora może być prostą zmienną skalarną, właściwością lub elementem tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../modifiers/readonly.md).  
  
 `-=`Operator najpierw odejmuje wartość wyrażenia (po prawej stronie operatora) od wartości zmiennej lub właściwości (po lewej stronie operatora), która znajduje się po raz pierwszy. Następnie operator przypisuje wynik tej operacji do zmiennej lub właściwości.  
  
## <a name="overloading"></a>Przeciążenie  
 [Operator-(Visual Basic)](subtraction-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Przeciążanie `-` operatora ma wpływ na zachowanie `-=` operatora. Jeśli kod korzysta z `-=` klasy lub struktury, która przeciążania `-` , należy poznać jej ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora, `-=` aby odjąć jedną `Integer` zmienną od innej i przypisać wynik do ostatniej zmiennej.  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Zobacz też

- [-— Operator (Visual Basic)](subtraction-operator.md)
- [Operatory przypisania](assignment-operators.md)
- [Operatory arytmetyczne](arithmetic-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Instrukcje](../../programming-guide/language-features/statements.md)
