---
title: Kolejność wykonywania działań
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
ms.openlocfilehash: eef6314f5fc1f5a7fffa7997559f697130f6f755
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401449"
---
# <a name="operator-precedence-in-visual-basic"></a>Kolejność wykonywania działań (Visual Basic)
Gdy w wyrażeniu wystąpią kilka operacji, każda część jest oceniana i rozwiązywana w wstępnie określonej kolejności o nazwie *pierwszeństwo operatorów*.

## <a name="precedence-rules"></a>Reguły pierwszeństwa
 Gdy wyrażenia zawierają operatory z więcej niż jednej kategorii, są oceniane zgodnie z następującymi regułami:

- Operatory arytmetyczne i złączne mają kolejność pierwszeństwa opisaną w poniższej sekcji, a wszystkie mają wyższy priorytet niż operatory porównania, logicznego i bitowego.

- Wszystkie operatory porównania mają równy priorytet, a wszystkie mają wyższy priorytet niż operatory logiczne i bitowe, ale mają niższy priorytet niż operatory arytmetyczne i łączenia.

- Operatory logiczne i bitowe mają kolejność pierwszeństwa opisaną w poniższej sekcji, a wszystkie mają niższy priorytet niż operatory arytmetyczne, łączenia i porównywania.

- Operatory o równym priorytecie są oceniane od lewej do prawej w kolejności, w jakiej występują w wyrażeniu.

## <a name="precedence-order"></a>Kolejność pierwszeństwa
 Operatory są oceniane w następującej kolejności:

### <a name="await-operator"></a>Await — Operator
 Kart

### <a name="arithmetic-and-concatenation-operators"></a>Operatory arytmetyczne i łączenia
 Potęgowanie ( `^` )

 Jednoargumentowa tożsamość i negacja ( `+` , `–` )

 Mnożenie i dzielenie zmiennoprzecinkowe ( `*` , `/` )

 Dzielenie liczb całkowitych ( `\` )

 Moduły arytmetyczne ( `Mod` )

 Dodawanie i odejmowanie ( `+` , `–` )

 Łączenie ciągów ( `&` )

 Przesunięcia bitów arytmetycznych ( `<<` , `>>` )

### <a name="comparison-operators"></a>Operatory porównania
 Wszystkie operatory porównania (,,,,,,,,, `=` `<>` `<` `<=` `>` `>=` `Is` `IsNot` `Like` `TypeOf` ... `Is` )

### <a name="logical-and-bitwise-operators"></a>Operatory logiczne i bitowe
 Negacja ( `Not` )

 Połączenia ( `And` , `AndAlso` )

 Rozłączenie włączne ( `Or` , `OrElse` )

 Rozłączenie wyłączne ( `Xor` )

### <a name="comments"></a>Komentarze
 `=`Operator jest tylko operatorem porównania równości, a nie operatorem przypisania.

 Operator łączenia ciągów ( `&` ) nie jest operatorem arytmetycznym, ale z pierwszeństwem jest zgrupowany z operatorami arytmetycznymi.

 `Is`Operatory i `IsNot` są operatorami porównania odwołań do obiektów. Nie porównują wartości dwóch obiektów; sprawdzają tylko, czy dwie zmienne obiektu odwołują się do tego samego wystąpienia obiektu.

## <a name="associativity"></a>Łączność
 Gdy operatory równego pierwszeństwa pojawiają się razem w wyrażeniu, na przykład mnożenia i dzielenia, kompilator oblicza każdą operację, gdy napotka ją od lewej do prawej. Ilustruje to poniższy przykład.

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 Pierwsze wyrażenie szacuje podział 96/8 (wyniki w 12), a następnie dział 12/4, który powoduje trzy. Ponieważ kompilator ocenia operacje `n1` od lewej do prawej, ocena jest taka sama, gdy ta kolejność jest jawnie wskazywana dla `n2` . Oba `n1` i `n2` mają wynik trzy. Z drugiej strony, `n3` ma wynik 48, ponieważ nawiasy wymuszają kompilator, aby najpierw oszacować 8/4.

 Ze względu na to zachowanie operatory są określane jako *pozostawiły skojarzenie* w Visual Basic.

## <a name="overriding-precedence-and-associativity"></a>Zastępowanie pierwszeństwa i łączność
 Można użyć nawiasów, aby wymusić ocenę niektórych części wyrażenia przed innymi. Może to przesłaniać kolejność pierwszeństwa i lewo łączność. Visual Basic zawsze wykonuje operacje, które są ujęte w nawiasy przed tymi zewnętrznymi. Jednakże w obrębie nawiasów zachowuje zwykłe pierwszeństwo i łączność, chyba że w nawiasach są używane nawiasy. Ilustruje to poniższy przykład.

```vb
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

## <a name="see-also"></a>Zobacz też

- [= — Operator](assignment-operator.md)
- [Is, operator](is-operator.md)
- [IsNot, operator](isnot-operator.md)
- [Like — Operator](like-operator.md)
- [TypeOf — Operator](typeof-operator.md)
- [Operator await](await-operator.md)
- [Operatory według funkcji](operators-listed-by-functionality.md)
- [Operatory i wyrażenia](../../programming-guide/language-features/operators-and-expressions/index.md)
