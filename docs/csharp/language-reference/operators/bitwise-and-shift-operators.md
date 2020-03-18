---
title: Operatory bitowe i przesuwowe — odwołanie do języka C#
description: Dowiedz się więcej o operatorach języka C#, które wykonują operacje logiczne lub przesunięcia bitowego za pomocą operacji typów całkowitych.
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
ms.openlocfilehash: 54198368672e0c9324210a232c7851b5a90402cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399267"
---
# <a name="bitwise-and-shift-operators-c-reference"></a>Operatory bitowe i przesuwne (odwołanie do języka C#)

Następujące operatory wykonują operacje bitowe lub przesuwne z operandami [zintegrowanych typów numerycznych](../builtin-types/integral-numeric-types.md) lub typu [char:](../builtin-types/char.md)

- Operator bezary [ `~` (bitowy dopełnienie)](#bitwise-complement-operator-)
- Operatory przesunięcia binarnego [ `<<` (przesunięcie w lewo)](#left-shift-operator-) i [ `>>` (przesunięcie w prawo)](#right-shift-operator-)
- Operatory [ `&` binarne (logiczne I)](#logical-and-operator-) [ `|` ( logiczne LUB)](#logical-or-operator-)i [ `^` (logiczne wyłączne LUB)](#logical-exclusive-or-operator-)

Te operatory są `int`zdefiniowane `uint` `long`dla `ulong` , , i typów. Gdy oba operandy są innych`sbyte` `byte`typów `short` `ushort`integralnych `char`( , , , `int` lub ), ich wartości są konwertowane na typ, który jest również typu wynik operacji. Gdy operandy są różnych typów całki, ich wartości są konwertowane na najbliższy zawierający typ całki. Aby uzyskać więcej informacji, zobacz [numeryczne promocje](~/_csharplang/spec/expressions.md#numeric-promotions) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

, `&` `|`i `^` operatory są również zdefiniowane dla `bool` operandów typu. Aby uzyskać więcej informacji, zobacz [Logiczne operatory logiczne](boolean-logical-operators.md).

Operacje bitowe i przesuwne nigdy nie powodują przepełnienia i dają takie same wyniki w [kontekstach sprawdzanych i niezaznaczonych.](../keywords/checked-and-unchecked.md)

## <a name="bitwise-complement-operator-"></a>Bitowy operator dopełniacza ~

Operator `~` tworzy bitowy uzupełnienie swojego operandu, odwracając każdy bit:

[!code-csharp-interactive[bitwise NOT](snippets/BitwiseAndShiftOperators.cs#BitwiseComplement)]

Można również użyć `~` symbolu do deklarowania finalizatorów. Aby uzyskać więcej informacji, zobacz [Finalizatory](../../programming-guide/classes-and-structs/destructors.md).

## <a name="left-shift-operator-"></a>Operator zmiany lewej\<\<

Operator `<<` przesuwa swój lewy operand w lewo przez [liczbę bitów zdefiniowanych przez jego prawostronny operand](#shift-count-of-the-shift-operators).

Operacja zmiany po lewej stronie odrzuca bity wysokiego rzędu, które znajdują się poza zakresem typu wynikowego i ustawia niskie pozycje pustych bitów na zero, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[left shift](snippets/BitwiseAndShiftOperators.cs#LeftShift)]

Ponieważ operatory przesunięcia `int`są `uint` `long`zdefiniowane `ulong` tylko dla , , i typów, wynik operacji zawsze zawiera co najmniej 32 bity. Jeśli argument po lewej stronie jest innego`sbyte` `byte`typu `short` `ushort`integralnego `char`( , , , `int` lub ), jego wartość jest konwertowana na typ, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[left shift with promotion](snippets/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

Aby uzyskać informacje o tym, jak `<<` operand po prawej stronie operatora definiuje liczbę zmian, zobacz Licznik zmian w sekcji [operatorzy zmian.](#shift-count-of-the-shift-operators)

## <a name="right-shift-operator-"></a> >> operatora zmiany prawej

Operator `>>` przesuwa swój lewy operand w prawo o [liczbę bitów zdefiniowanych przez jego prawy operand](#shift-count-of-the-shift-operators).

Operacja zmiany po prawej stronie odrzuca bity niskiego rzędu, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[right shift](snippets/BitwiseAndShiftOperators.cs#RightShift)]

Puste pozycje bitowe o wysokim zamówieniu są ustawiane na podstawie typu operandu po lewej stronie w następujący sposób:

- Jeśli operand po lewej stronie `int` `long`jest typu lub , operator prawego shift wykonuje przesunięcie *arytmetyczne:* wartość najbardziej znaczącego bitu (bitu znaku) operandu po lewej stronie jest propagowana do pozycji pustych bitów o wysokim rzędu. Oznacza to, że pozycje pustebitu wysokiego rzędu są ustawione na zero, jeśli argument po lewej stronie jest nieujemna i ustawiona na jedną, jeśli jest ujemna.

  [!code-csharp-interactive[arithmetic right shift](snippets/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- Jeśli operand po lewej stronie `uint` `ulong`jest typu lub , operator prawego przesunięcia wykonuje *logiczną* zmianę: wysokiej klasy puste pozycje bitowe są zawsze ustawione na zero.

  [!code-csharp-interactive[logical right shift](snippets/BitwiseAndShiftOperators.cs#LogicalRightShift)]

Aby uzyskać informacje o tym, jak `>>` operand po prawej stronie operatora definiuje liczbę zmian, zobacz Licznik zmian w sekcji [operatorzy zmian.](#shift-count-of-the-shift-operators)

## <a name="logical-and-operator-"></a>Operator logiczny AND&amp;

Operator `&` oblicza bitwise logiczne i jego operands:

[!code-csharp-interactive[bitwise AND](snippets/BitwiseAndShiftOperators.cs#BitwiseAnd)]

W `bool` przypadku operandów `&` operator oblicza [logiczną i](boolean-logical-operators.md#logical-and-operator-) jego argumenty. Operator `&` emancypuje. [address-of operator](pointer-related-operators.md#address-of-operator-)

## <a name="logical-exclusive-or-operator-"></a>Logiczny wyłączny operator OR ^

Operator `^` oblicza bitwise logiczne wyłączne LUB, znany również jako bitowy logiczny XOR, jego operands:

[!code-csharp-interactive[bitwise XOR](snippets/BitwiseAndShiftOperators.cs#BitwiseXor)]

W `bool` przypadku operandów `^` operator oblicza [logiczną wyłączną lub](boolean-logical-operators.md#logical-exclusive-or-operator-) jego operandów.

## <a name="logical-or-operator-"></a>Logiczny operator OR |

Operator `|` oblicza bitowy logiczny LUB jego operandów:

[!code-csharp-interactive[bitwise OR](snippets/BitwiseAndShiftOperators.cs#BitwiseOr)]

W `bool` przypadku operandów `|` operator oblicza [logiczny OR](boolean-logical-operators.md#logical-or-operator-) jego argumentów.

## <a name="compound-assignment"></a>Przypisanie złożone

Dla operatora `op`binarnego wyrażenie przypisania złożonego formularza

```csharp
x op= y
```

jest równoważny

```csharp
x = x op y
```

chyba `x` że jest oceniana tylko raz.

W poniższym przykładzie pokazano użycie przypisania złożonego z operatorami bitowym i shift:

[!code-csharp-interactive[compound assignment](snippets/BitwiseAndShiftOperators.cs#CompoundAssignment)]

Ze względu na [promocje liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions)wynik `op` operacji może nie być `T` `x`niejawnie konwertowalny na typ . W takim przypadku, `op` jeśli jest wstępnie zdefiniowanyoperator i wynik operacji jest `T` jawnie konwertowalne na typ `x`, wyrażenie przypisania złożonego formularza `x op= y` jest równoważne `x = (T)(x op y)`, z wyjątkiem, że `x` jest oceniane tylko raz. W poniższym przykładzie przedstawiono to zachowanie:

[!code-csharp-interactive[compound assignment with cast](snippets/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a>Pierwszeństwo operatorów

Następująca lista zamówienia bitowej i operatory zmiany ruchu, począwszy od najwyższego pierwszeństwa do najniższego:

- Operator dopełniacza bitowego`~`
- Operatorzy zmian `<<` i`>>`
- Operator logiczny AND`&`
- Logiczny wyłączny operator OR`^`
- Operator logiczny OR`|`

Użyj nawiasów, `()`, aby zmienić kolejność oceny narzuconą przez pierwszeństwo operatora:

[!code-csharp-interactive[operator precedence](snippets/BitwiseAndShiftOperators.cs#Precedence)]

Aby uzyskać pełną listę operatorów Języka C# uporządkowane według poziomu pierwszeństwa, zobacz [pierwszeństwo operatora](index.md#operator-precedence) sekcji [operatorów C#artykułu.](index.md)

## <a name="shift-count-of-the-shift-operators"></a>Liczba zmian operatorów zmianowych

`<<` Dla operatorów przesunięcia i `>>`, typ operand `int` po prawej stronie musi być lub typu, który ma [wstępnie zdefiniowane niejawne konwersji liczbowej](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) do `int`.

Dla `x << count` wyrażeń i `x >> count` wyrażenia rzeczywista liczba `x` zmian zależy od typu w następujący sposób:

- Jeśli typ `x` jest `int` `uint`lub , liczba zmian jest definiowana przez niskokondygnacje *pięć* bitów operandpo prawej stronie. Oznacza to, że liczba zmian `count & 0x1F` jest `count & 0b_1_1111`obliczana z (lub ).

- Jeśli typ `x` jest `long` `ulong`lub , liczba zmian jest definiowana przez niskokondygnacje *sześć* bitów operandpo prawej stronie. Oznacza to, że liczba zmian `count & 0x3F` jest `count & 0b_11_1111`obliczana z (lub ).

W poniższym przykładzie przedstawiono to zachowanie:

[!code-csharp-interactive[shift count example](snippets/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> Jak pokazano w poprzednim przykładzie, wynik operacji zmiany może być różny od zera, nawet jeśli wartość operandu po prawej stronie jest większa niż liczba bitów w operandzie po lewej stronie.

## <a name="enumeration-logical-operators"></a>Operatory logiczne wyliczania

Program `~` `&`, `|`, `^` i operatory są również obsługiwane przez dowolny typ [wyliczenia.](../builtin-types/enum.md) W przypadku argumentów tego samego typu wyliczenia wykonywana jest operacja logiczna na odpowiednich wartościach podstawowego typu integralnego. Na przykład dla `x` `y` dowolnego `T` i typu wyliczenia `U`z `x & y` typem bazowym wyrażenie `(T)((U)x & (U)y)` daje taki sam wynik jak wyrażenie.

Zazwyczaj używasz bitowych operatorów logicznych z typem wyliczenia, który jest zdefiniowany za pomocą [Flags](xref:System.FlagsAttribute) atrybutu. Aby uzyskać więcej informacji, zobacz [Typy wyliczania jako flagi bitowe](../builtin-types/enum.md#enumeration-types-as-bit-flags) sekcji [Typy wyliczania.](../builtin-types/enum.md)

## <a name="operator-overloadability"></a>Przeciążenie operatora

Typ zdefiniowany przez użytkownika `~`może `<<` `>>` `&` [przeciążyć](operator-overloading.md) `^` operatory , , , i `|`operatorów. Gdy operator binarny jest przeciążony, odpowiedni operator przypisania złożonego jest również niejawnie przeciążony. Typ zdefiniowany przez użytkownika nie może jawnie przeciążać operatora przypisania złożonego.

Jeśli `T` typ zdefiniowany przez `<<` użytkownika `>>` przeciąża lub operator, musi być `T` typ operandu po lewej stronie `int`i typ argumentu po prawej stronie.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)

- [Operator dopełniacza bitowego](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [Operatory przesunięcia](~/_csharplang/spec/expressions.md#shift-operators)
- [Operatory logiczne](~/_csharplang/spec/expressions.md#logical-operators)
- [Przypisanie złożone](~/_csharplang/spec/expressions.md#compound-assignment)
- [Promocje numeryczne](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Operatory logiczne (Boolean)](boolean-logical-operators.md)
