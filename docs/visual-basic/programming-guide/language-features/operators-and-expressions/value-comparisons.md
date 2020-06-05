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
ms.openlocfilehash: 01816b5730cf4fda61f1737ce3ce00ab82f57da8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403398"
---
# <a name="value-comparisons-visual-basic"></a>Porównania wartości (Visual Basic)
Operatory porównania mogą służyć do konstruowania wyrażeń, które porównują wartości zmiennych liczbowych. Te wyrażenia zwracają `Boolean` wartość w zależności od tego, czy porównanie ma wartość PRAWDA, czy fałsz. Przykłady takiego wyrażenia są następujące.  
  
 `45 > 26`  
  
 `26 > 45`  
  
 Pierwsze wyrażenie zwraca wartość `True` , ponieważ 45 jest większy niż 26. Drugi przykład jest obliczany do `False` , ponieważ 26 nie jest większy niż 45.  
  
 Możesz również porównać wyrażenia liczbowe w ten sposób. Porównywane wyrażenia mogą same być wyrażeniami złożonymi, jak w poniższym przykładzie.  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 Poprzednie wyrażenie złożone zawiera literały, zmienne i wywołania funkcji. Wyrażenia po obu stronach operatora porównania są oceniane, a wynikowe wartości są porównywane przy użyciu `>=` operatora porównania. Jeśli wartość wyrażenia po lewej stronie jest większa lub równa wartości wyrażenia z prawej strony, całe wyrażenie zostanie obliczone `True` ; w przeciwnym razie zostanie obliczone `False` .  
  
 Wyrażenia, które porównują wartości są najczęściej używane w `If...Then` konstrukcjach, jak w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 `=`Znak jest operatorem porównania, a także operatorem przypisania. Gdy jest używany jako operator porównania, sprawdza, czy wartość po lewej stronie jest równa wartości po prawej stronie, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 Można również użyć wyrażenia porównania w dowolnym miejscu `Boolean` , w którym jest wymagana wartość, na przykład `If` w `While` instrukcji,, `Loop` lub `ElseIf` , lub gdy przypisuje lub przekazywać wartość do `Boolean` zmiennej. W poniższym przykładzie wartość zwracana przez wyrażenie porównania jest przypisana do `Boolean` zmiennej.  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyrażenia logiczne](boolean-expressions.md)
- [Operatory i wyrażenia](index.md)
- [Operatory porównania w Visual Basic](comparison-operators.md)
- [Instrukcje: obliczanie wartości liczbowych](how-to-calculate-numeric-values.md)
- [Kolejność wykonywania działań (Visual Basic)](../../../language-reference/operators/operator-precedence.md)
