---
title: Bitowe i operatory przesunięcia - C# odwołania
description: Dowiedz się więcej o C# operatorów, które wykonują bitowe logicznej lub operacje przesunięcia z argumentów operacji typu całkowitoliczbowego.
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise logical operators [C#]
- shift operators [C#]
- tilde operator [C#]
- one's complement operator [C#]
- bitwise complement operator [C#]
- ~ operator [C#]
- left shift operator [C#]
- << operator [C#]
- right shift operator [C#]
- '>> operator [C#]'
- bitwise logical AND operator [C#]
- ampersand operator [C#]
- '& operator [C#]'
- bitwise logical exclusive OR operator [C#]
- bitwise logical XOR operator [C#]
- ^ operator [C#]
- bitwise logical OR operator [C#]
- '| operator [C#]'
ms.openlocfilehash: 1f98435aba6994aaca76127cc20b5ffa29df455f
ms.sourcegitcommit: d9c4808739c8c606957dd0964d952b98ea7b6533
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2019
ms.locfileid: "67349770"
---
# <a name="bitwise-and-shift-operators-c-reference"></a>Bitowe i operatory przesunięcia (C# odwołania)

Następujące operatory bitowe wykonywania lub shift operacji przy użyciu argumentów operacji [typów całkowitych](../keywords/integral-types-table.md):

- Jednoargumentowy [ `~` (dopełnienia bitowego)](#bitwise-complement-operator-) — operator
- Binarny [ `<<` (przesunięcia w lewo)](#left-shift-operator-) i [ `>>` (przesunięcia bitowego w prawo)](#right-shift-operator-) operatory przesunięcia
- Binarny [ `&` (operator logiczny oraz)](#logical-and-operator-), [ `|` (operator logiczny lub)](#logical-or-operator-), i [ `^` (logiczne OR wyłączne)](#logical-exclusive-or-operator-) operatorów

Te operatory są zdefiniowane dla `int`, `uint`, `long`, i `ulong` typów. Gdy oba operandy są inne typy całkowitoliczbowe (`sbyte`, `byte`, `short`, `ushort`, lub `char`), ich wartości są konwertowane na `int` typ, który jest również typ wyniku operacji. W przypadku argumentów operacji z różnymi typami całkowitymi, ich wartości są konwertowane do najbliższego zawierającego typu całkowitego. Aby uzyskać więcej informacji, zobacz [promocji na liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

`&`, `|`, I `^` operatory są również określone w przypadku argumentów operacji `bool` typu. Aby uzyskać więcej informacji, zobacz [logiczna operatorów logicznych](boolean-logical-operators.md).

Bitowe OR i operacje przesunięcia nigdy nie spowodować przepełnienie działają tak samo w [checked i unchecked](../keywords/checked-and-unchecked.md) kontekstów.

## <a name="bitwise-complement-operator-"></a>Operator dopełnienia bitowego ~

`~` Operator wytwarza bitowe uzupełnienie swojego operandu odwracając każdy bit:

[!code-csharp-interactive[bitwise NOT](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

Można również użyć `~` symbolu, aby zadeklarować finalizatorów. Aby uzyskać więcej informacji, zobacz [finalizatory](../../programming-guide/classes-and-structs/destructors.md).

## <a name="left-shift-operator-"></a>Operator przesunięcia w lewo \<\<

`<<` Operator przenosi swojego operandu po lewej stronie, w lewo o liczbę bitów zdefiniowane przez jej argument po prawej stronie.

Operacja przesunięcia w lewo odrzuca najbardziej znaczących bitów, które są poza zakresem typu wyniku i ustawia pozycje bitów pusty niskiego rzędu na zero, co ilustruje poniższy przykład:

[!code-csharp-interactive[left shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

Ponieważ operatory przesunięcia, są zdefiniowane tylko w przypadku `int`, `uint`, `long`, i `ulong` typów, wynik operacji zawsze zawiera co najmniej 32-bitowy. Jeśli argument po lewej stronie jest innego typu całkowitego (`sbyte`, `byte`, `short`, `ushort`, lub `char`), jego wartość jest konwertowana na `int` typu, co ilustruje poniższy przykład:

[!code-csharp-interactive[left shift with promotion](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

Aby uzyskać informacje na temat prawostronny operand `<<` operator definiuje licznik przesunięć, zobacz [licznik operatory przesunięcia przesunięć](#shift-count-of-the-shift-operators) sekcji.

## <a name="right-shift-operator-"></a>Operator przesunięcia w prawo >>

`>>` Operator przenosi jego lewostronny operand bezpośrednio przez liczbę bitów zdefiniowane przez jej argument po prawej stronie.

Operacja przesunięcia w prawo powoduje odrzucenie mniej znaczące bity, co ilustruje poniższy przykład:

[!code-csharp-interactive[right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

Pozycje bitów pusty wyższego rzędu jest ustawiona na podstawie typ operandu po lewej stronie w następujący sposób:

- Jeśli lewostronny operand jest typu [int](../keywords/int.md) lub [długie](../keywords/long.md), wykonuje operator przesunięcia w prawo *arytmetyczne* shift: wartość najbardziej znaczący bit (bit znaku) z Lewostronny operand jest propagowana do pozycji bitów pusty wyższego rzędu. Oznacza to, pozycje bitów pusty wyższego rzędu są ustawiane na zero, jeśli argument po lewej stronie jest ujemna i ustawiony na wartość 1, jeśli jest ujemna.

  [!code-csharp-interactive[arithmetic right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- Lewostronny operand jest typu [uint](../keywords/uint.md) lub [ulong](../keywords/ulong.md), operator przesunięcia w prawo wykonuje *logiczne* shift: pozycje bitów pusty wyższego rzędu są zawsze ustawione na zero.

  [!code-csharp-interactive[logical right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

Aby uzyskać informacje na temat prawostronny operand `>>` operator definiuje licznik przesunięć, zobacz [licznik operatory przesunięcia przesunięć](#shift-count-of-the-shift-operators) sekcji.

## <a name="logical-and-operator-"></a> Operator logiczny AND &amp;

`&` Operator oblicza iloczynu bitowego AND logiczne z argumentów:

[!code-csharp-interactive[bitwise AND](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

Dla argumentów operacji `bool` typu `&` oblicza operator [operator logiczny oraz](boolean-logical-operators.md#logical-and-operator-) z argumentów. Jednoargumentowy `&` operator jest [operatora address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Operator logiczny OR wyłączne ^

`^` Operator oblicza wyłączny sumy bitowej dla logicznej lub znany także jako bitowe XOR logiczne z argumentów:

[!code-csharp-interactive[bitwise XOR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

Dla argumentów operacji `bool` typu `^` oblicza operator [logiczne OR wyłączne](boolean-logical-operators.md#logical-exclusive-or-operator-) z argumentów.

## <a name="logical-or-operator-"></a>Operator logiczny OR |

`|` Operator oblicza bitowe OR logiczne z argumentów:

[!code-csharp-interactive[bitwise OR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

Dla argumentów operacji `bool` typu `|` oblicza operator [logiczne OR](boolean-logical-operators.md#logical-or-operator-) z argumentów.

## <a name="compound-assignment"></a>Przydział złożony

Dla operatora binarnego `op`, wyrażenie przypisania złożonego formularza

```csharp
x op= y
```

odpowiada wyrażeniu

```csharp
x = x op y
```

z tą różnicą, że `x` jest obliczany tylko raz.

Poniższy przykład ilustruje użycie przydział złożony przy użyciu bitowego operatora i operatory przesunięcia:

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

Z powodu [promocji na liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions), wynikiem `op` operacji może nie być niejawnie konwertowane na typ `T` z `x`. W takim przypadku jeśli `op` jest wstępnie zdefiniowanego operatora, a wynik operacji jest jawnie konwertowany na typ `T` z `x`, wyrażenia przypisania złożonego w postaci `x op= y` jest odpowiednikiem `x = (T)(x op y)`, z wyjątkiem które `x` jest oceniane tylko raz. Poniższy przykład przedstawia tego zachowania:

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a>Pierwszeństwo operatorów

Następujące listy zamówienia bitowe i operatory przesunięcia od najwyższy priorytet, do najniższego:

- Operator dopełnienia bitowego `~`
- Operatory przesunięcia `<<` i `>>`
- Operator logiczny AND `&`
- Operator logiczny OR wyłączne `^`
- Operator logiczny OR `|`

Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożonych przez pierwszeństwo operatorów:

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

Aby uzyskać pełną listę C# operatory uporządkowane według poziomu priorytetu, zobacz [ C# operatory](index.md).

## <a name="shift-count-of-the-shift-operators"></a>Licznik przesunięć operatorów przesunięcia

Dla operatorów przesunięcia `<<` i `>>`, typ prawostronny operand musi być [int](../keywords/int.md) lub typ, który ma [wstępnie zdefiniowane niejawnych konwersji liczbowych](../keywords/implicit-numeric-conversions-table.md) do `int`.

Aby uzyskać `x << count` i `x >> count` wyrażeń, licznik przesunięć rzeczywistego zależy od rodzaju `x` w następujący sposób:

- Jeśli typ `x` jest [int](../keywords/int.md) lub [uint](../keywords/uint.md), licznik przesunięć jest definiowany przez niskiego rzędu *pięć* bitów prawostronny operand. Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x1F` (lub `count & 0b_1_1111`).

- Jeśli typ `x` jest [długie](../keywords/long.md) lub [ulong](../keywords/ulong.md), licznik przesunięć jest definiowany przez niskiego rzędu *sześć* bitów prawostronny operand. Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x3F` (lub `count & 0b_11_1111`).

Poniższy przykład przedstawia tego zachowania:

[!code-csharp-interactive[shift count example](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a>Operatory logiczne wyliczenia

`~`, `&`, `|`, I `^` operatory również są zdefiniowane dla dowolnego [wyliczenie](../keywords/enum.md) typu. Operandy typu wyliczenia operacji logicznej jest wykonywane na odpowiadające im wartości bazowego typu całkowitego. Na przykład dla dowolnego `x` i `y` typu wyliczeniowego `T` z typu podstawowego `U`, `x & y` wyrażenie daje ten sam wynik jako `(T)((U)x & (U)y)` wyrażenia.

Zazwyczaj używa się operatory logiczne bitowe dla typu wyliczenia, która jest zdefiniowana za pomocą [flagi](xref:System.FlagsAttribute) atrybutu. Aby uzyskać więcej informacji, zobacz [Typy wyliczeniowe jako znaczniki bitowe](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) części [Typy wyliczeniowe](../../programming-guide/enumeration-types.md) artykułu.

## <a name="operator-overloadability"></a>Overloadability — operator

Typ zdefiniowany przez użytkownika może [przeciążenia](../keywords/operator.md) `~`, `<<`, `>>`, `&`, `|`, i `^` operatorów. Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania złożonego jest również niejawnie przeciążona. Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania złożonego.

Jeśli typ zdefiniowany przez użytkownika `T` przeciążenia `<<` lub `>>` operatora, typ lewostronny operand musi być `T` i typ prawostronny operand musi być `int`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Operator dopełnienia bitowego](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [Operatory przesunięcia](~/_csharplang/spec/expressions.md#shift-operators)
- [Operatory logiczne](~/_csharplang/spec/expressions.md#logical-operators)
- [Przydział złożony](~/_csharplang/spec/expressions.md#compound-assignment)
- [Promocji na liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Zobacz także

- [C#Odwołanie](../index.md)
- [Operatory języka C#](index.md)
- [Operatory logiczne logiczne](boolean-logical-operators.md)
