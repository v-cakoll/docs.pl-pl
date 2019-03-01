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
ms.openlocfilehash: 50054b9e32f4d49a34c1bb1a5c79129662019aee
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965914"
---
# <a name="value-comparisons-visual-basic"></a>Porównania wartości (Visual Basic)
Operatory porównania może służyć do konstruowania wyrażeń, które Porównaj wartości liczbowe zmiennych. Zwraca te wyrażenia `Boolean` wartość oparta na czy wynik porównania ma wartość PRAWDA lub FAŁSZ. Przykłady takich wyrażeń.  
  
 `45 > 26`  
  
 `26 > 45`  
  
 Pierwsze wyrażenie, które daje w wyniku `True`, ponieważ 45 jest większa od 26. Drugi przykład daje w wyniku `False`, ponieważ nie jest większa niż 45 26.  
  
 Można również porównać wyrażeń liczbowych w ten sposób. Same wyrażeń, które można porównać mogą być złożone wyrażenia, jak w poniższym przykładzie.  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 Poprzedni złożone wyrażenie zawiera literały, zmienne i wywołania funkcji. Wyrażenia po obu stronach operatora porównania są obliczane i wynikające z tego wartości są porównywane za pomocą `>=` operator porównania. Jeśli wartość wyrażenia po lewej stronie jest większa lub równa wartości wyrażenia po prawej stronie, całe wyrażenie daje w wyniku `True`; w przeciwnym razie daje w wyniku `False`.  
  
 Wyrażeń, Porównaj wartości, które są najczęściej używane w `If...Then` konstrukcje, jak w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 `=` Znak jest operator porównania, a także operator przypisania. Gdy jest używana jako operator porównania, ocenia to, czy wartość po lewej stronie jest równa wartości po prawej stronie, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 Umożliwia także wyrażenia porównania dowolnym `Boolean` wartość jest wymagane, na przykład `If`, `While`, `Loop`, lub `ElseIf` instrukcji, lub podczas przypisywania do lub przekazanie wartości do `Boolean` zmiennej. W poniższym przykładzie przypisano wartości zwracanych przez wyrażenie porównania `Boolean` zmiennej.  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a>Zobacz także
- [Wyrażenia logiczne](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Operatory i wyrażenia](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Operatory porównania w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Instrukcje: Obliczanie wartości liczbowych](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
