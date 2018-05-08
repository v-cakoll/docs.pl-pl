---
title: Porównania wartości (Visual Basic)
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
ms.openlocfilehash: 6e1eda09784814d139ef94b6720b538aef30e5e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="value-comparisons-visual-basic"></a>Porównania wartości (Visual Basic)
Operatory porównania może służyć do konstruowania wyrażeń, które porównanie wartości numerycznych zmiennych. Zwraca tych wyrażeń `Boolean` wartość oparta na czy wynik porównania ma wartość PRAWDA lub FAŁSZ. Przykłady takich wyrażeń.  
  
 `45 > 26`  
  
 `26 > 45`  
  
 Pierwsze wyrażenie daje w wyniku `True`, ponieważ jest większa niż 26 45. Drugi przykład daje w wyniku `False`, ponieważ nie jest większa niż 45 26.  
  
 Wyrażenia liczbowe w ten sposób można także porównać. Wyrażeń, które można porównać się być wyrażenia złożone, jak w poniższym przykładzie.  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 Poprzedniego wyrażenia złożone zawiera literały, zmienne i wywołania funkcji. Wyrażeń po obu stronach operatora porównania są obliczane, a wyniki są porównywane przy użyciu `>=` operator porównania. Jeśli wartość wyrażenia z lewej strony jest większa lub równa wartości wyrażenie po prawej stronie, całe wyrażenie daje w wyniku `True`; w przeciwnym razie daje w wyniku `False`.  
  
 Wyrażeń, które umożliwia porównanie wartości są najczęściej używane w `If...Then` konstrukcje, jak w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#84](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 `=` Znak jest operator porównania, a także operatora przypisania. Gdy jest używany jako operator porównania, ocenia to, czy wartość po lewej stronie jest równa wartości po prawej stronie, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#85](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 Można również użyć wyrażenia porównania dowolnym `Boolean` wartość jest wymagane, na przykład `If`, `While`, `Loop`, lub `ElseIf` instrukcji lub podczas przypisywania do lub przekazanie wartości do `Boolean` zmiennej. W poniższym przykładzie wartość zwrócona przez wyrażenie porównania jest przypisany do `Boolean` zmiennej.  
  
 [!code-vb[VbVbalrOperators#86](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyrażenia logiczne](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Operatory i wyrażenia](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Operatory porównania w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Instrukcje: obliczanie wartości liczbowych](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
