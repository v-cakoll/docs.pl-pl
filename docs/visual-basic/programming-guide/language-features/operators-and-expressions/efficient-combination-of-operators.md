---
title: Skuteczna kombinacja operatorów
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
ms.openlocfilehash: 3088072646278dac13e4d483cb4f99297eaad9ca
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403475"
---
# <a name="efficient-combination-of-operators-visual-basic"></a>Skuteczna kombinacja operatorów (Visual Basic)
Wyrażenia złożone mogą zawierać wiele różnych operatorów. Ilustruje to poniższy przykład.  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 Tworzenie złożonych wyrażeń, takich jak jeden w poprzednim przykładzie, wymaga dokładnego poznania reguł pierwszeństwa operatorów. Aby uzyskać więcej informacji, zobacz [pierwszeństwo operatorów w Visual Basic](../../../language-reference/operators/operator-precedence.md).  
  
## <a name="parenthetical-expressions"></a>Wyrażenia w nawiasach  
 Często operacje mają być wykonywane w innej kolejności niż określona przez pierwszeństwo operatorów. Rozważmy następujący przykład.  
  
 `x = z * y + 4`  
  
 Poprzedni przykład mnoży `z` przez `y` , a następnie dodaje wynik do `4` . Ale jeśli chcesz dodać `y` i `4` przed pomnożeniem wyniku przez, można `z` przesłonić normalny priorytet operatorów przy użyciu nawiasów. Umieszczając wyrażenie w nawiasach, należy wymusić, aby wyrażenie było oceniane jako pierwsze, niezależnie od pierwszeństwa operatora. Aby wymusić powyższy przykład, aby najpierw wykonać dodanie, można napisać go ponownie tak, jak w poniższym przykładzie.  
  
 `x = z * (y + 4)`  
  
 Powyższy przykład dodaje `y` i `4` , a następnie mnoży sumę według `z` .  
  
### <a name="nested-parenthetical-expressions"></a>Zagnieżdżone wyrażenia ujęte w nawiasy  
 Można zagnieżdżać wyrażenia na wielu poziomach nawiasów, aby jeszcze bardziej zastępować pierwszeństwo. Wyrażenia najbardziej głęboko zagnieżdżone w nawiasach są oceniane jako pierwsze, po których następuje następne przeważnie zagnieżdżone i tak dalej, jak najmniej głęboko zagnieżdżone, a wreszcie wyrażenia poza nawiasy. Ilustruje to poniższy przykład.  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 W poprzednim przykładzie `z + 2` jest oceniane jako pierwsze, a następnie inne wyrażenia ujęte w nawiasy. Potęga, która zwykle ma wyższy priorytet niż Dodawanie lub mnożenie, jest szacowana jako Ostatnia w tym przykładzie, ponieważ inne wyrażenia są ujęte w nawiasy.  
  
## <a name="see-also"></a>Zobacz też

- [Operatory arytmetyczne w Visual Basic](arithmetic-operators.md)
- [Operatory porównania w Visual Basic](comparison-operators.md)
- [Operatory logiczne i bitowe w Visual Basic](logical-and-bitwise-operators.md)
- [Operatory logiczne/bitowe (Visual Basic)](../../../language-reference/operators/logical-bitwise-operators.md)
- [Wyrażenia logiczne](boolean-expressions.md)
- [Porównania wartości](value-comparisons.md)
- [Instrukcje: obliczanie wartości liczbowych](how-to-calculate-numeric-values.md)
- [Kolejność wykonywania działań (Visual Basic)](../../../language-reference/operators/operator-precedence.md)
