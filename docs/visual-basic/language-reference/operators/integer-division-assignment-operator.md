---
title: '\=, operator'
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
ms.openlocfilehash: a546d8b0c9b3852386970f80d3da96794da2351c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370950"
---
# <a name="-operator"></a>\\= — Operator
Dzieli wartość zmiennej lub właściwości przez wartość wyrażenia i przypisuje wynik całkowity do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagany. Dowolna zmienna lub właściwość numeryczna.  
  
 `expression`  
 Wymagany. Dowolne wyrażenie liczbowe.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie `\=` operatora może być prostą zmienną skalarną, właściwością lub elementem tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../modifiers/readonly.md).  
  
 `\=`Operator dzieli wartość zmiennej lub właściwości po lewej stronie przez wartość po prawej stronie, a następnie przypisuje wynik całkowity do zmiennej lub właściwości po jej lewej stronie.  
  
 Aby uzyskać więcej informacji na temat dzielenia liczb całkowitych, zobacz element [\ operator (Visual Basic)](integer-division-operator.md).  
  
## <a name="overloading"></a>Przeciążenie  
 `\`Operator może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Przeciążanie `\` operatora ma wpływ na zachowanie `\=` operatora. Jeśli kod korzysta z `\=` klasy lub struktury, która przeciążania `\` , należy poznać jej ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `\=` operatora do dzielenia jednej `Integer` zmiennej przez sekundę i przypisywania wyniku liczby całkowitej do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Zobacz też

- [\ — Operator (Visual Basic)](integer-division-operator.md)
- [Operator/= (Visual Basic)](floating-point-division-assignment-operator.md)
- [Operatory przypisania](assignment-operators.md)
- [Operatory arytmetyczne](arithmetic-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Instrukcje](../../programming-guide/language-features/statements.md)
