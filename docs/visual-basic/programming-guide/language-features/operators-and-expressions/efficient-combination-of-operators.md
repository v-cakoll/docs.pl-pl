---
title: Skuteczna kombinacja operatorów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: 8f5dd6c56b3e4576b9d798e0e5e10b2996f558dc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841267"
---
# <a name="efficient-combination-of-operators-visual-basic"></a>Skuteczna kombinacja operatorów (Visual Basic)
Złożonych wyrażeń może zawierać wiele różnych operatorów. Ilustruje to poniższy przykład.  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 Tworzenie złożonych wyrażeń, takiego jak w poprzednim przykładzie wymaga dogłębnej wiedzy w zakresie zasad pierwszeństwo operatorów. Aby uzyskać więcej informacji, zobacz [pierwszeństwo operatorów w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="parenthetical-expressions"></a>Wyrażenia w nawiasach  
 Często ma operacje, aby przejść w innym porządku niż określonej przez priorytet operatorów. Rozważmy następujący przykład.  
  
 `x = z * y + 4`  
  
 Poprzedni przykład mnoży `z` przez `y`, następnie dodaje wynik do `4`. Ale jeśli chcesz dodać `y` i `4` przed pomnożenia wyniku przez `z`, pierwszeństwo operatorów normalne można zastąpić za pomocą nawiasów. Umieszczając wyrażenia w nawiasach, możesz wymusić to wyrażenie do obliczenia, niezależnie od tego, pierwszeństwo operatorów. Aby wymusić w poprzednim przykładzie w celu dodawania, można przepisać go tak, jak w poniższym przykładzie.  
  
 `x = z * (y + 4)`  
  
 W poprzednim przykładzie dodano `y` i `4`, następnie mnoży tej sumy przez `z`.  
  
### <a name="nested-parenthetical-expressions"></a>Zagnieżdżone wyrażenia w nawiasach  
 Można zagnieżdżać wyrażenia w nawiasy, aby zastąpić jeszcze bardziej priorytet na wielu poziomach. Wyrażenia najgłębiej zagnieżdżony w nawiasach są obliczane najpierw następuje dalej, najgłębiej zagnieżdżony i tak dalej do najmniej głęboko zagnieżdżone, a na końcu wyrażeń poza nawiasów. Ilustruje to poniższy przykład.  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 W powyższym przykładzie `z + 2` jest pierwszy ocenione, a następnie inne wyrażenia w nawiasach. Zapis wykładniczy, która zwykle ma wyższy priorytet niż dodawanie i mnożenie, jest oceniany w ostatniej w tym przykładzie, ponieważ inne wyrażenia są ujęte w nawiasy.  
  
## <a name="see-also"></a>Zobacz także

- [Operatory arytmetyczne w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operatory porównania w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operatory logiczne i bitowe w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Operatory logiczne/bitowe (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Wyrażenia logiczne](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Instrukcje: Obliczanie wartości liczbowych](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
