---
title: '&amp;= — Operator (Visual Basic)'
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
ms.openlocfilehash: c3db2d4095600f32af92d1a4ce1f806a3f032af0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="amp-operator-visual-basic"></a>&amp;= — Operator (Visual Basic)
Łączy `String` wyrażenie `String` zmienna lub właściwość i przypisuje wynik do zmiennej lub właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Części  
 `variableorproperty`  
 Wymagana. Wszelkie `String` zmienna lub właściwość.  
  
 `expression`  
 Wymagana. Wszelkie `String` wyrażenia.  
  
## <a name="remarks"></a>Uwagi  
 Element po lewej stronie `&=` operator może być zmienną skalarną proste, właściwością lub element tablicy. Zmienna lub właściwość nie może być [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md). `&=` Łączy operator `String` wyrażenie jego prawej strony, aby `String` zmienna lub właściwość po lewej stronie i przypisuje wynik do zmiennej lub właściwości po lewej stronie.  
  
## <a name="overloading"></a>Przeciążenie  
 [& — Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Przeciążanie `&` operator wpływa na działanie `&=` operatora. Jeśli używa Twój kod `&=` na klasę lub strukturę, która overloads `&`, trzeba koniecznie zapoznać się ponownie zdefiniowany zachowania. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `&=` operator do łączenia dwóch `String` zmiennych i przypisz wynik do pierwszej zmiennej.  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [&, operator](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [+=, operator](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [Operatory przypisania](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Operatory łączenia](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Instrukcje](../../../visual-basic/programming-guide/language-features/statements.md)
