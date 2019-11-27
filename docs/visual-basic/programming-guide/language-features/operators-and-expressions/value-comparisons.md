---
title: Porównania wartości
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: f766eaaada486a0f70838bafb754d25070ff4174
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346287"
---
# <a name="value-comparisons-visual-basic"></a>Porównania wartości (Visual Basic)
Operatory porównania mogą służyć do konstruowania wyrażeń, które porównują wartości zmiennych liczbowych. Te wyrażenia zwracają wartość `Boolean` na podstawie tego, czy porównanie ma wartość PRAWDA, czy fałsz. Przykłady takiego wyrażenia są następujące.  
  
 `45 > 26`  
  
 `26 > 45`  
  
 Pierwsze wyrażenie szacuje `True`, ponieważ 45 jest większe niż 26. Drugi przykład jest obliczany `False`, ponieważ 26 nie jest większy niż 45.  
  
 Możesz również porównać wyrażenia liczbowe w ten sposób. Porównywane wyrażenia mogą same być wyrażeniami złożonymi, jak w poniższym przykładzie.  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 Poprzednie wyrażenie złożone zawiera literały, zmienne i wywołania funkcji. Wyrażenia po obu stronach operatora porównania są oceniane, a wynikowe wartości są porównywane przy użyciu operatora porównania `>=`. Jeśli wartość wyrażenia po lewej stronie jest większa lub równa wartości wyrażenia z prawej strony, całe wyrażenie szacuje się `True`; w przeciwnym razie szacuje się `False`.  
  
 Wyrażenia, które porównują wartości są najczęściej używane w konstrukcjach `If...Then`, jak w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 Znak `=` jest operatorem porównania, a także operatorem przypisania. Gdy jest używany jako operator porównania, sprawdza, czy wartość po lewej stronie jest równa wartości po prawej stronie, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 Można również użyć wyrażenia porównania w dowolnym miejscu, `Boolean` jest wymagana wartość, na przykład w `If`, `While`, `Loop`lub instrukcji `ElseIf` lub po przypisaniu lub przekazaniu wartości do zmiennej `Boolean`. W poniższym przykładzie wartość zwracana przez wyrażenie porównania jest przypisana do zmiennej `Boolean`.  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyrażenia logiczne](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Operatory i wyrażenia](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Operatory porównania w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Instrukcje: obliczanie wartości liczbowych](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
