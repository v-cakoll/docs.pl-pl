---
title: Operatory bitowe i przesunięcia C# — odwołanie
description: Dowiedz C# się więcej na temat operatorów, które wykonują bitowe operacje logiczne lub przesunięcia przy użyciu operandów typów całkowitych.
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
ms.openlocfilehash: a6319cbbbe8a691f5d2a01a13a5abfa2550b3705
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239524"
---
# <a name="bitwise-and-shift-operators-c-reference"></a>Operatory bitowe i przesunięciaC# (odwołanie)

Następujące operatory wykonują operacje bitowe lub przesunięcia przy użyciu operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md) lub typu [char](../builtin-types/char.md) :

- Operator jednoargumentowy [`~` (uzupełnienie bitowe)](#bitwise-complement-operator-)
- Operatory przesunięcia`<<` binarnych [(LEFT SHIFT)](#left-shift-operator-) i [`>>` (prawy shift)](#right-shift-operator-)
- Binarne [`&` (logiczne i)](#logical-and-operator-), [`|` (logiczne lub)](#logical-or-operator-)i [`^` (logiczne wyłącznych lub)](#logical-exclusive-or-operator-)

Te operatory są zdefiniowane dla typów `int`, `uint`, `long`i `ulong`. Gdy oba operandy są innymi typami całkowitymi (`sbyte`, `byte`, `short`, `ushort`lub `char`), ich wartości są konwertowane na typ `int`, który jest również typem wyniku operacji. Gdy operandy są różnymi typami całkowitymi, ich wartości są konwertowane na najbliższy typ całkowity. Aby uzyskać więcej informacji, zobacz sekcję " [promocje liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions) " [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

Operatory `&`, `|`i `^` są również zdefiniowane dla argumentów operacji typu `bool`. Aby uzyskać więcej informacji, zobacz logiczne [Operatory logiczne](boolean-logical-operators.md).

Operacje bitowe i przesunięcia nigdy nie powodują przepełnienia i tworzą te same wyniki w kontekstach [zaewidencjonowanych i](../keywords/checked-and-unchecked.md) niezaznaczone.

## <a name="bitwise-complement-operator-"></a>Operator uzupełnienia bitowego ~

Operator `~` generuje bitowe uzupełnienie jego operandu przez odwrócenie każdego bitu:

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

Można również użyć symbolu `~`, aby zadeklarować finalizatory. Aby uzyskać więcej informacji, zobacz [finalizatory](../../programming-guide/classes-and-structs/destructors.md).

## <a name="left-shift-operator-"></a>Operator przesunięcia w lewo \<\<

Operator `<<` przesuwa swój lewy argument operacji w lewo o [liczbę bitów określoną przez jego operand po prawej stronie](#shift-count-of-the-shift-operators).

Operacja przesunięcia w lewo odrzuca bity o wysokim stopniu, które znajdują się poza zakresem wyników, i ustawia puste pozycje bitu w porządku o wartości zero, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[left shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

Ponieważ operatory przesunięcia są zdefiniowane tylko dla typów `int`, `uint`, `long`i `ulong`, wynik operacji zawsze zawiera co najmniej 32 bitów. Jeśli argument operacji po lewej stronie jest innego typu całkowitego (`sbyte`, `byte`, `short`, `ushort`lub `char`), jego wartość jest konwertowana na typ `int`, jak pokazano na poniższym przykładzie:

[!code-csharp-interactive[left shift with promotion](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

Aby uzyskać informacje o tym, jak argument operacji po prawej stronie operatora `<<` definiuje liczbę przesunięć, zobacz [Liczba przesunięć w sekcji operatory przesunięcia](#shift-count-of-the-shift-operators) .

## <a name="right-shift-operator-"></a>Operator przesunięcia w prawo > >

Operator `>>` przesuwa swój lewy argument operacji bezpośrednio przez [liczbę bitów zdefiniowanych przez swój operand z prawej strony](#shift-count-of-the-shift-operators).

Operacja przesunięcia w prawo powoduje odrzucenie bitów o niskiej kolejności, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

Puste pozycje w dużej kolejności są ustawiane na podstawie typu operandu po lewej stronie w następujący sposób:

- Jeśli argument operacji po lewej stronie jest typu `int` lub `long`, operator przesunięcia w prawo wykonuje *arytmetyczne* przesunięcie: wartość najbardziej znaczącego bitu (bit znaku) operandu po lewej stronie jest propagowana do pustych pozycji o dużej liczbie bitów. Oznacza to, że puste pozycje bitu o wysokim stopniu kolejności są ustawione na zero, jeśli argument operacji po lewej stronie jest nieujemny i ustawiony na jeden, jeśli jest ujemny.

  [!code-csharp-interactive[arithmetic right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- Jeśli argument operacji po lewej stronie jest typu `uint` lub `ulong`, operator przesunięcia w prawo wykonuje *logiczne* przesunięcie: wartość pustych pozycji w kolejności pustej jest zawsze równa zero.

  [!code-csharp-interactive[logical right shift](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

Aby uzyskać informacje o tym, jak argument operacji po prawej stronie operatora `>>` definiuje liczbę przesunięć, zobacz [Liczba przesunięć w sekcji operatory przesunięcia](#shift-count-of-the-shift-operators) .

## <a name="logical-and-operator-"></a>Operatory logiczne i &amp;

Operator `&` oblicza koniunkcję bitową i jej operandy:

[!code-csharp-interactive[bitwise AND](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

Dla argumentów operacji `bool` operator `&` oblicza wartość [logiczną i](boolean-logical-operators.md#logical-and-operator-) jej operandów. Jednoargumentowy operator `&` jest [operatorem address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Operator wyłączny logicznego OR ^

Operator `^` oblicza koniunkcję bitową na wyłączność lub, znaną również jako bitowe koniunkcja logiczna XOR, argumentów operacji:

[!code-csharp-interactive[bitwise XOR](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

Dla argumentów operacji `bool` operator `^` oblicza wartość [logiczną na wyłączność lub](boolean-logical-operators.md#logical-exclusive-or-operator-) z jej argumentów operacji.

## <a name="logical-or-operator-"></a>Operator logiczny OR |

Operator `|` oblicza bitowe logiczne lub jego operandy:

[!code-csharp-interactive[bitwise OR](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

Dla argumentów operacji `bool` operator `|` oblicza wartość [logiczną lub](boolean-logical-operators.md#logical-or-operator-) argumentów operacji.

## <a name="compound-assignment"></a>Przypisanie złożone

Dla operatora binarnego `op`wyrażenie złożonego przypisania formularza

```csharp
x op= y
```

odpowiada wyrażeniu

```csharp
x = x op y
```

z tą różnicą, że `x` są oceniane tylko raz.

Poniższy przykład ilustruje użycie przypisania złożonego z operatory bitowe i przesunięcia:

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

Ze względu na [promocje liczbowe](~/_csharplang/spec/expressions.md#numeric-promotions)wynik operacji `op` może nie być niejawnie konwertowany na typ `T` `x`. W takim przypadku, jeśli `op` jest wstępnie zdefiniowanym operatorem, a wynik operacji jest jawnie konwertowany na typ `T` `x`, wyrażenie przypisania złożonego `x op= y` jest równoważne z `x = (T)(x op y)`, z tą różnicą, że `x` są oceniane tylko raz. Poniższy przykład ilustruje takie zachowanie:

[!code-csharp-interactive[compound assignment with cast](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a>Pierwszeństwo operatorów

Poniższa lista porządkuje operatory bitowe i przesunięcia, rozpoczynając od najwyższego priorytetu do najniższego:

- `~` operatora uzupełniania bitowego
- Operatory przesunięcia `<<` i `>>`
- Operatory logiczne i `&`
- `^` operatora logicznego wyłącznego OR
- `|` operatora logicznego OR

Użyj nawiasów `()`, aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów:

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz sekcję [pierwszeństwo](index.md#operator-precedence) operatorów w artykule [ C# Operators](index.md) .

## <a name="shift-count-of-the-shift-operators"></a>Liczba przesunięć operatorów przesunięcia

Dla operatorów przesunięcia `<<` i `>>`typ operandu po prawej stronie musi być `int` lub typem, który ma [wstępnie zdefiniowaną niejawną konwersję liczbową](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) do `int`.

W przypadku wyrażeń `x << count` i `x >> count` rzeczywista liczba przesunięć zależy od typu `x` w następujący sposób:

- Jeśli typ `x` jest `int` lub `uint`, liczba przesunięć jest definiowana przez *pięć* bitów z prawej strony. Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x1F` (lub `count & 0b_1_1111`).

- Jeśli typ `x` jest `long` lub `ulong`, licznik przesunięć jest definiowany przez *sześć* -znaczących bitów operandu po prawej stronie. Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x3F` (lub `count & 0b_11_1111`).

Poniższy przykład ilustruje takie zachowanie:

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> Jak pokazano w powyższym przykładzie, wynik operacji przesunięcia może być różny od zera, nawet jeśli wartość operandu po prawej stronie jest większa niż liczba bitów w lewym operandzie.

## <a name="enumeration-logical-operators"></a>Wyliczanie operatorów logicznych

Operatory `~`, `&`, `|`i `^` są również obsługiwane przez dowolny typ [wyliczeniowy](../builtin-types/enum.md) . Dla operandów o tym samym typie wyliczeniowym operacja logiczna jest wykonywana na odpowiednich wartościach bazowego typu całkowitego. Na przykład dla dowolnych `x` i `y` typu wyliczenia `T` z typem podstawowym `U`, wyrażenie `x & y` generuje ten sam wynik jako wyrażenie `(T)((U)x & (U)y)`.

Zwykle używane są bitowe operatory logiczne z typem wyliczenia, który jest zdefiniowany przy użyciu atrybutu [flags](xref:System.FlagsAttribute) . Aby uzyskać więcej informacji, zobacz sekcję [typy wyliczeniowe jako flagi bitowe](../builtin-types/enum.md#enumeration-types-as-bit-flags) artykułu [typy wyliczeniowe](../builtin-types/enum.md) .

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory `~`, `<<`, `>>`, `&`, `|`i `^`. Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony. Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.

Jeśli typ zdefiniowany przez użytkownika `T` przeciążania operatora `<<` lub `>>`, typem operandu po lewej stronie musi być `T`, a typ operacji po prawej stronie musi być `int`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Operator dopełnienia bitowego](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [Operatory przesunięcia](~/_csharplang/spec/expressions.md#shift-operators)
- [Operatory logiczne](~/_csharplang/spec/expressions.md#logical-operators)
- [Przypisanie złożone](~/_csharplang/spec/expressions.md#compound-assignment)
- [Promocje numeryczne](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Zobacz też

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Operatory logiczne Boolean](boolean-logical-operators.md)
