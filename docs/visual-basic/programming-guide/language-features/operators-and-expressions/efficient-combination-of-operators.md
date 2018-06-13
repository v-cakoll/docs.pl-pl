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
ms.openlocfilehash: 8ced464cb0cc8e1bec3c3449dccb827575599905
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648921"
---
# <a name="efficient-combination-of-operators-visual-basic"></a>Skuteczna kombinacja operatorów (Visual Basic)
Wyrażenia złożone może zawierać wielu różnych operatorów. Ilustruje to poniższy przykład.  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 Tworzenie złożonych wyrażeń, takie jak w poprzednim przykładzie wymaga dogłębnej wiedzy reguły pierwszeństwo operatorów. Aby uzyskać więcej informacji, zobacz [kolejność wykonywania w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="parenthetical-expressions"></a>Wyrażenia w nawiasach  
 Często ma odbywać się w innym porządku niż określana przez kolejność wykonywania działań. Rozważmy następujący przykład.  
  
 `x = z * y + 4`  
  
 Mnoży w poprzednim przykładzie `z` przez `y`, następnie dodaje wynik do `4`. Ale jeśli chcesz dodać `y` i `4` przed pomnożenia wyniku przez `z`, można zastąpić normalne kolejność za pomocą nawiasów. Umieszczając wyrażenia w nawiasach, możesz wymusić tego wyrażenia do obliczenia, niezależnie od tego, kolejność wykonywania działań. Aby wymusić w poprzednim przykładzie w celu dodawania, można napisać ponownie jak w poniższym przykładzie.  
  
 `x = z * (y + 4)`  
  
 W poprzednim przykładzie dodano `y` i `4`, następnie mnoży tej sumy przez `z`.  
  
### <a name="nested-parenthetical-expressions"></a>Zagnieżdżone wyrażenia w nawiasach  
 Można zagnieżdżać wyrażenia w nawiasy, aby zastąpić priorytet jeszcze bardziej wiele poziomów. Wyrażenia najbardziej głęboko zagnieżdżone w nawiasach są oceniane najpierw następuje dalej najbardziej głęboko zagnieżdżone, i tak dalej do najmniej głęboko zagnieżdżone, a na końcu wyrażeń poza nawiasów. Ilustruje to poniższy przykład.  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 W powyższym przykładzie `z + 2` jest pierwszy ocenione, a następnie inne wyrażenia w nawiasach. Zapis wykładniczy, które zwykle mają wyższy priorytet niż dodawanie lub mnożenie, jest obliczane w ostatnio w tym przykładzie, ponieważ inne wyrażenia są ujęte w nawiasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory arytmetyczne w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Operatory porównania w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Operatory logiczne i bitowe w Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [Operatory logiczne/bitowe (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Wyrażenia logiczne](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Porównania wartości](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Instrukcje: obliczanie wartości liczbowych](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
