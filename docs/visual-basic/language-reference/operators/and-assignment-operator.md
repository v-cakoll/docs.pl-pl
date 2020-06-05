---
title: '&amp;= — Operator'
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
ms.openlocfilehash: db42f7be7225b866eacf5b73066754e91cd1a0f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371989"
---
# <a name="amp-operator-visual-basic"></a>&amp;= — Operator (Visual Basic)
Łączy `String` wyrażenie ze `String` zmienną lub właściwością i przypisuje wynik do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagany. Dowolna `String` zmienna lub właściwość.  
  
 `expression`  
 Wymagany. Dowolne `String` wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie `&=` operatora może być prostą zmienną skalarną, właściwością lub elementem tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../modifiers/readonly.md). `&=`Operator łączy `String` wyrażenie po prawej stronie ze `String` zmienną lub właściwości po lewej stronie, a następnie przypisuje wynik do zmiennej lub właściwości po lewej stronie.  
  
## <a name="overloading"></a>Przeciążenie  
 [Operator&](concatenation-operator.md) może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Przeciążanie `&` operatora ma wpływ na zachowanie `&=` operatora. Jeśli kod korzysta z `&=` klasy lub struktury, która przeciążania `&` , należy poznać jej ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora, `&=` Aby połączyć dwie `String` zmienne i przypisać wynik do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- [Operator&](concatenation-operator.md)
- [Operator + =](addition-assignment-operator.md)
- [Operatory przypisania](assignment-operators.md)
- [Concatenation — Operatory](concatenation-operators.md)
- [Kolejność wykonywania działań (Visual Basic)](operator-precedence.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Instrukcje](../../programming-guide/language-features/statements.md)
