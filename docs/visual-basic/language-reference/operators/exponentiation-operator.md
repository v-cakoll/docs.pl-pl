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
ms.openlocfilehash: 54de9c91d4e166b8ca1733952dfa9c98ebf11ffe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778498"
---
# <a name="-operator-visual-basic"></a>^ — Operator (Visual Basic)

Podnosi liczbę do potęgi równej innej liczbie.

## <a name="syntax"></a>Składnia

```
number ^ exponent
```

## <a name="parts"></a>Części

`number`\
Wymagana. Dowolne wyrażenie numeryczne.

`exponent`\
Wymagana. Dowolne wyrażenie numeryczne.

## <a name="result"></a>Wynik

Wynik jest `number` podniesione do potęgi równej `exponent`, zawsze jako `Double` wartość.

## <a name="supported-types"></a>Obsługiwane typy

`Double`. Operandy dowolnego innego typu są konwertowane na `Double`.

## <a name="remarks"></a>Uwagi

Visual Basic zawsze wykonuje potęgowania w [typ danych Double](../../../visual-basic/language-reference/data-types/double-data-type.md).

Wartość `exponent` może być ułamkową ujemne lub obu.

Gdy więcej niż jeden potęgowania odbywa się w jednym wyrażeniu `^` operator jest oceniane jako napotkano od lewej do prawej.

> [!NOTE]
> `^` Operator może być *przeciążone*, co oznacza, że klasy lub struktury można ponownie zdefiniować jej zachowanie, gdy argument operacji ma typ tej klasy lub struktury. Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz jej zachowanie zmieniony. Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).

## <a name="example"></a>Przykład

W poniższym przykładzie użyto `^` operatora w celu podniesienia liczby do potęgi równej wykładnik. Wynik jest pierwszy operand podniesioną do potęgi drugiego.

[!code-vb[VbVbalrOperators#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#20)]

Poprzedni przykład generuje następujące wyniki:

`exp1` jest równa 4 (kwadrat 2).

`exp2` ustawiono 19683 (3 cubed, następnie wartości sześcianu).

`exp3` ustawiono-125 (sześcianu -5).

`exp4` ustawiono 625 (-5 do potęgi czwarty).

`exp5` jest równa 2 (element główny modułu 8).

`exp6` wynosi 0,5 (1.0 podzielona przez główny modułu 8).

Należy zwrócić uwagę znaczenie nawiasów w wyrażeniach w poprzednim przykładzie. Z powodu *pierwszeństwo operatorów*, Visual Basic zwykle wykonuje `^` operatora przed wszystkie inne pola, nawet jednoargumentowe `–` operatora. Jeśli `exp4` i `exp6` była obliczona bez nawiasów, czy zostały utworzone następujące wyniki:

`exp4 = -5 ^ 4` oblicza — 5 do potęgi czwarty, które mogłyby spowodować-625.

`exp6 = 8 ^ -1.0 / 3.0` oblicza (od 8 do potęgi-1 lub 0,125) podzielony przez 3.0, co mogłoby spowodować 0.041666666666666666666666666666667.

## <a name="see-also"></a>Zobacz także

- [^=, operator](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Operatory arytmetyczne](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory arytmetyczne w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
