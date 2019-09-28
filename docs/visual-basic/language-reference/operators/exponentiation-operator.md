---
title: ^ — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponentiation
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
ms.openlocfilehash: 8cdfbec917608211e19c39eb37bd12dbc7c4d33f
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592222"
---
# <a name="-operator-visual-basic"></a>^ — Operator (Visual Basic)

Podnosi liczbę do potęgi innej liczby.

## <a name="syntax"></a>Składnia

```vb
number ^ exponent
```

## <a name="parts"></a>Części

`number`\
Wymagany. Dowolne wyrażenie liczbowe.

`exponent`\
Wymagany. Dowolne wyrażenie liczbowe.

## <a name="result"></a>Wynik

Wynikiem jest `number` podniesioną do potęgi `exponent`, zawsze jako wartość `Double`.

## <a name="supported-types"></a>Obsługiwane typy

`Double`. Operandy dowolnego typu są konwertowane na `Double`.

## <a name="remarks"></a>Uwagi

Visual Basic zawsze wykonuje potęgowanie w [podwójnym typie danych](../../../visual-basic/language-reference/data-types/double-data-type.md).

Wartość `exponent` może być ułamkowa, ujemna lub jednocześnie.

Gdy w jednym wyrażeniu jest wykonywanych więcej niż jedna potęga, operator `^` jest oceniany, ponieważ występuje od lewej do prawej.

> [!NOTE]
> Operator `^` może być *przeciążony*, co oznacza, że Klasa lub struktura może przedefiniować jej zachowanie, gdy operand ma typ tej klasy lub struktury. Jeśli Twój kod używa tego operatora dla takiej klasy lub struktury, pamiętaj o tym, aby zrozumieć jego ponownie zdefiniowane zachowanie. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Przykład

Poniższy przykład używa operatora `^`, aby podnieść liczbę do potęgi wykładnika. Wynikiem jest pierwszy operand podniesiony do potęgi sekundy.

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

Poprzedni przykład daje następujące wyniki:

wartość `exp1` to 4 (2 kwadraty).

`exp2` jest ustawiona na 19683 (3 Cubed, a następnie wartość cubed).

`exp3` jest ustawiona na-125 (-5 cubed).

`exp4` jest ustawiona na 625 (-5 do czwartej potęgi).

`exp5` jest ustawiona na 2 (korzeń modułu 8).

`exp6` jest ustawiony na 0,5 (1,0 podzielony przez korzeń modułu 8).

Zanotuj znaczenie nawiasów w wyrażeniach w poprzednim przykładzie. Ze względu na *pierwszeństwo operatorów*, Visual Basic zwykle wykonuje operator `^` przed innymi, nawet jednoargumentowy operator `–`. Jeśli `exp4` i `exp6` zostały obliczone bez nawiasów, zostałyby utworzone następujące wyniki:

`exp4 = -5 ^ 4` zostałyby obliczone jako – (5 do czwartej potęgi), co spowodowałoby 625.

`exp6 = 8 ^ -1.0 / 3.0` zostałaby obliczona jako (8 do potęgi – 1 lub 0,125) podzielona przez 3,0, co spowodowałoby 0.041666666666666666666666666666667.

## <a name="see-also"></a>Zobacz także

- [^=, operator](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
