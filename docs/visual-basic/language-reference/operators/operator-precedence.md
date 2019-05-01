---
title: Kolejność wykonywania działań (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: 568927eb4759c214311ad34a5b45e28094dd80be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013533"
---
# <a name="operator-precedence-in-visual-basic"></a>Kolejność wykonywania działań (Visual Basic)
Po wystąpieniu kilka operacji w wyrażeniach, każda część jest obliczane i rozwiązane w określonej kolejności, o nazwie *pierwszeństwo operatorów*.  
  
## <a name="precedence-rules"></a>Reguły pierwszeństwa  
 Gdy wyrażeń zawiera operatory z więcej niż jednej kategorii, ocenia się je zgodnie z następującymi zasadami:  
  
- Operatory arytmetyczne i łączenia mają kolejność pierwszeństwa, opisane w poniższej sekcji, a wszystkie mają wyższy priorytet niż porównania, logiczne i bitowe operatory.  
  
- Wszystkie operatory porównania mają równe pierwszeństwo, a wszystkie mają wyższy priorytet niż operatory logiczne i bitowe, ale niższy priorytet niż operatory arytmetyczne i łączenia.  
  
- Operatory logiczne i bitowe mają kolejność pierwszeństwa, opisane w poniższej sekcji, a wszystkie mają niższy priorytet niż operacje arytmetyczne, łączenie i operatory porównania.  
  
- Operatory o równe pierwszeństwo, są obliczane od lewej do prawej w kolejności, w jakiej występują w wyrażeniu.  
  
## <a name="precedence-order"></a>Kolejność pierwszeństwa  
 Operatory są obliczane w następującej kolejności:  
  
### <a name="await-operator"></a>Await — Operator  
 Operator await  
  
### <a name="arithmetic-and-concatenation-operators"></a>Operacje arytmetyczne i Concatenation — operatory  
 Potęgowania (`^`)  
  
 Jednoargumentowy tożsamości i negacji (`+`, `–`)  
  
 Mnożenie i dzielenie zmiennoprzecinkowe (`*`, `/`)  
  
 Dzielenie liczby całkowitej (`\`)  
  
 Arytmetycznego modulo (`Mod`)  
  
 Dodawanie i odejmowanie (`+`, `–`)  
  
 Łączenie ciągów (`&`)  
  
 Przesunięcie bitu arytmetyczne (`<<`, `>>`)  
  
### <a name="comparison-operators"></a>Operatory porównania  
 Wszystkie operatory porównania (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`... `Is`)  
  
### <a name="logical-and-bitwise-operators"></a>Operatory logiczne i bitowe  
 Negacja (`Not`)  
  
 Razem (`And`, `AndAlso`)  
  
 Włączne rozłączenia (`Or`, `OrElse`)  
  
 Wyłączne rozłączenia (`Xor`)  
  
### <a name="comments"></a>Komentarze  
 `=` Operator jest tylko operator porównania, nie operator przypisania.  
  
 Operator konkatenacji ciągów (`&`) nie jest operator arytmetyczny, ale w pierwszeństwo jest zgrupowany z operatorów arytmetycznych.  
  
 `Is` i `IsNot` operatory są operatory porównania odwołanie do obiektu. Nie porównują wartości dwóch obiektów; Sprawdź ich tylko w celu określenia, czy dwie zmienne do obiektu odnoszą się do tego samego wystąpienia obiektu.  
  
## <a name="associativity"></a>Łączność  
 Gdy operatory równy priorytet pojawiają się razem w wyrażeniu, na przykład mnożenia i dzielenia, kompilator ocenia każdej operacji, jak je napotka od lewej do prawej. Ilustruje to poniższy przykład.  
  
```  
Dim n1 As Integer = 96 / 8 / 4  
Dim n2 As Integer = (96 / 8) / 4  
Dim n3 As Integer = 96 / (8 / 4)  
```  
  
 Pierwsze wyrażenie daje w wyniku dzielenia 96 / 8 (co powoduje 12), a następnie dzielenia 12 / 4, co skutkuje trzy. Ponieważ kompilator ocenia operacjami dotyczącymi `n1` od lewej do prawej, ocena jest taka sama podczas tej kolejności jest wyraźnie wskazane dla `n2`. Zarówno `n1` i `n2` ma trzy wyniku. Z kolei `n3` ma wynik 48, ponieważ nawiasy wymuszają kompilator, aby ocenić 8 / 4 pierwszy.  
  
 Ze względu na to zachowanie operatorów są określane jako *łączność do lewej strony* w języku Visual Basic.  
  
## <a name="overriding-precedence-and-associativity"></a>Zastępowanie pierwszeństwo i łączność  
 Aby wymusić niektórych części wyrażenie ma zostać obliczone przed pozostałymi, można użyć nawiasów. To można zastąpić, zarówno w kolejność pierwszeństwa, jak i kojarzenie po lewej stronie. Visual Basic zawsze wykonuje operacje, które są ujęte w nawiasy przed osób spoza. Jednak w obrębie nawiasów utrzymuje zwykłych pierwszeństwo i łączność, chyba że używasz nawiasów w nawiasach. Ilustruje to poniższy przykład.  
  
```  
Dim a, b, c, d, e, f, g As Double  
a = 8.0  
b = 3.0  
c = 4.0  
d = 2.0  
e = 1.0  
f = a - b + c / d * e  
' The preceding line sets f to 7.0. Because of natural operator   
' precedence and associativity, it is exactly equivalent to the   
' following line.  
f = (a - b) + ((c / d) * e)  
' The following line overrides the natural operator precedence   
' and left associativity.  
g = (a - (b + c)) / (d * e)  
' The preceding line sets g to 0.5.  
```  
  
## <a name="see-also"></a>Zobacz także

- [=, operator](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [Is, operator](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot, operator](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Like, operator](../../../visual-basic/language-reference/operators/like-operator.md)
- [TypeOf, operator](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Await, operator](../../../visual-basic/language-reference/operators/await-operator.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
