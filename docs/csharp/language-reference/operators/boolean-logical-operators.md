---
title: Boolean operatory logiczne — odwołanie w C#
description: Dowiedz się więcej na temat operatorów języka C#, które wykonują logiczne negacje, połączenie (i), a także wyłączne operacje odłączenia (lub) z argumentami operacji logicznych.
ms.date: 06/29/2020
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: a19c804c624153ef608885bc6493537302275765
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618197"
---
# <a name="boolean-logical-operators-c-reference"></a>Boolean operatory logiczne (odwołanie w C#)

Następujące operatory wykonują operacje logiczne z argumentami operacji [bool](../builtin-types/bool.md) :

- Operator jednoargumentowy [ `!` (logiczne Negacja)](#logical-negation-operator-) .
- Operatory binarne [ `&` (logiczne i)](#logical-and-operator-), [ `|` (logiczne lub)](#logical-or-operator-)i [ `^` (logiczne wyłączne lub)](#logical-exclusive-or-operator-) . Te operatory zawsze obliczają oba operandy.
- Binary [ `&&` (warunkowe logiczne i)](#conditional-logical-and-operator-) oraz operatory [ `||` warunkowe logiczne or](#conditional-logical-or-operator-) . Te operatory obliczają operand z prawej strony tylko wtedy, gdy jest to konieczne.

W przypadku operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md) `&` operatory, `|` i `^` wykonują bitowe operacje logiczne. Aby uzyskać więcej informacji, zobacz [Operatory bitowe i przesunięcia](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Operator logiczny negacji

Jednoargumentowy `!` operator prefiksu oblicza logiczne Negacja operandu. To znaczy, `true` gdy operand jest obliczany do `false` , i `false` , jeśli operand ma wartość `true` :

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

Począwszy od języka C# 8,0, jednoargumentowy operator przyrostkowy `!` jest [operatorem łagodniejszej o wartości null](null-forgiving.md).

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a>Operator logiczny AND&amp;

`&`Operator oblicza wartość logiczną i jej operandów. Wynik `x & y` jest `true` Jeśli oba i są `x` `y` oceniane do `true` . W przeciwnym razie wynik jest `false` .

`&`Operator oblicza oba operandy, nawet jeśli argument operacji po lewej stronie jest obliczany do `false` , tak że wynik operacji jest `false` niezależnie od wartości operandu po prawej stronie.

W poniższym przykładzie operand z prawej strony `&` operatora jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

[Warunkowy operator logiczny and](#conditional-logical-and-operator-) `&&` oblicza również wartość logiczną i jej operandy, ale nie oblicza wartości argumentu po prawej stronie, jeśli argument operacji po lewej stronie ma wartość `false` .

Dla operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md) `&` operator oblicza koniunkcję [bitową i](bitwise-and-shift-operators.md#logical-and-operator-) jej operandy. Operator jednoargumentowy jest operatorem `&` [Address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Operator wyłączny logicznego OR ^

`^`Operator oblicza wartość logiczną na wyłączność lub, znaną również jako logiczna XOR, dla argumentów operacji. Wynik jest w `x ^ y` `true` przypadku, gdy jest `x` obliczany i obliczany do `true` `y` `false` , lub `x` szacuje `false` `y` `true` się w. W przeciwnym razie wynik jest `false` . Oznacza to, że dla `bool` operandów `^` operator oblicza ten sam wynik jako [operator nierówności](equality-operators.md#inequality-operator-) `!=` .

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

W przypadku operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md) `^` operator oblicza [bitową logiczną na wyłączność lub](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) z jej argumentów operacji.

## <a name="logical-or-operator-"></a>Operator logiczny OR |

`|`Operator oblicza wartość logiczną lub argumentów operacji. Wynik jest, `x | y` `true` Jeśli lub jest `x` `y` obliczany do `true` . W przeciwnym razie wynik jest `false` .

`|`Operator oblicza oba operandy, nawet jeśli argument operacji po lewej stronie jest obliczany do `true` , tak że wynik operacji jest `true` niezależnie od wartości operandu po prawej stronie.

W poniższym przykładzie operand z prawej strony `|` operatora jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

[Operator logiczny or](#conditional-logical-or-operator-) `||` oblicza również wartość logiczną lub jej operandy, ale nie oblicza wartości operandu po prawej stronie, jeśli argument operacji po lewej stronie ma wartość `true` .

Dla argumentów operacji [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md) `|` operator oblicza bitową koniunkcję [logiczną lub](bitwise-and-shift-operators.md#logical-or-operator-) argumentów operacji.

## <a name="conditional-logical-and-operator-ampamp"></a><a name="conditional-logical-and-operator-"></a>Warunkowe operatory logiczne i&amp;&amp;

Warunkowy operator logiczny AND `&&` , znany także jako operator logiczny "krótki-obwód", oblicza wartość logiczną i argumentów operacji. Wynik `x && y` jest `true` Jeśli oba i są `x` `y` oceniane do `true` . W przeciwnym razie wynik jest `false` . Jeśli ma `x` wartość `false` , `y` nie jest oceniane.

W poniższym przykładzie operand z prawej strony `&&` operatora jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie ma wartość `false` :

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

[Operator logiczny and](#logical-and-operator-) `&` oblicza również wartość logiczną i jej operandy, ale zawsze oblicza oba operandy.

## <a name="conditional-logical-or-operator-"></a>Warunkowe logiczne OR operator | |

Warunkowy operator logiczny OR `||` , nazywany także "operatorem" krótki-obwód ", oblicza wartość logiczną lub argumentów operacji. Wynik jest, `x || y` `true` Jeśli lub jest `x` `y` obliczany do `true` . W przeciwnym razie wynik jest `false` . Jeśli ma `x` wartość `true` , `y` nie jest oceniane.

W poniższym przykładzie operand z prawej strony `||` operatora jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie ma wartość `true` :

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

[Operator logiczny or](#logical-or-operator-) `|` oblicza również wartość logiczną lub argumentów operacji, ale zawsze oblicza oba operandy.

## <a name="nullable-boolean-logical-operators"></a>Logiczne operatory wartości null

Dla `bool?` operandów operatory [ `&` (logiczne i)](#logical-and-operator-) i [ `|` (logiczne or)](#logical-or-operator-) obsługują logikę o wartości trójwarstwowej w następujący sposób:

- `&`Operator produkuje `true` tylko wtedy, gdy oba jego operandy są szacowane do `true` . Jeśli `x` lub `y` jest obliczany do `false` , `x & y` powstaje `false` (nawet jeśli inny operand jest obliczany do `null` ). W przeciwnym razie wynik `x & y` jest `null` .

- `|`Operator produkuje `false` tylko wtedy, gdy oba jego operandy są szacowane do `false` . Jeśli `x` lub `y` jest obliczany do `true` , `x | y` powstaje `true` (nawet jeśli inny operand jest obliczany do `null` ). W przeciwnym razie wynik `x | y` jest `null` .

W poniższej tabeli przedstawiono semantykę:

|x|Y|x&y|x&#124;y|  
|----|----|----|----|  
|true|true|true|true|  
|true|fałsz|fałsz|true|  
|true|wartość null|wartość null|true|  
|fałsz|true|fałsz|true|  
|fałsz|fałsz|fałsz|fałsz|  
|fałsz|wartość null|fałsz|wartość null|  
|wartość null|true|wartość null|true|  
|wartość null|fałsz|fałsz|wartość null|  
|wartość null|wartość null|wartość null|wartość null|  

Zachowanie tych operatorów różni się od typowego zachowania operatora z zerowymi typami wartości. Zazwyczaj operator, który jest zdefiniowany dla operandów typu wartości, może być również używany z operandami odpowiadającego typu wartości null. Taki operator wytwarza, `null` Jeśli którykolwiek z jego operandów zwróci wartość `null` . Jednak `&` `|` Operatory i mogą generować wartości inne niż null, nawet jeśli jeden z operandów jest wynikiem `null` . Aby uzyskać więcej informacji o zachowaniu operatora z typem wartości null, zobacz sekcję [zniesione operatory](../builtin-types/nullable-value-types.md#lifted-operators) w artykule [typy wartości null](../builtin-types/nullable-value-types.md) .

Można również użyć `!` `^` operatorów i z `bool?` operandami, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

Operatory logiczne warunkowe `&&` i `||` nie obsługują `bool?` argumentów operacji.

## <a name="compound-assignment"></a>Przypisanie złożone

Dla operatora binarnego `op` wyrażenie złożonego przypisania formularza

```csharp
x op= y
```

jest równoważny

```csharp
x = x op y
```

z tą różnicą, że `x` jest obliczana tylko raz.

`&`Operatory, `|` i `^` obsługują przypisanie złożone, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

> [!NOTE]
> Warunkowe operatory logiczne `&&` i `||` nie obsługują przypisania złożonego.

## <a name="operator-precedence"></a>Pierwszeństwo operatorów

Poniższa lista porządkuje operatory logiczne rozpoczynając od najwyższego priorytetu do najniższego:

- Operator logiczny negacji`!`
- Operator logiczny AND`&`
- Operator wyłączny logicznego OR`^`
- Operator logiczny OR`|`
- Warunkowe operatory logiczne i`&&`
- Warunkowy operator logiczny OR`||`

Użyj nawiasów, `()` Aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów:

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

Aby uzyskać pełną listę operatorów języka C# uporządkowanych według poziomu pierwszeństwa, zobacz sekcję [pierwszeństwo](index.md#operator-precedence) operatorów w artykule [operatory języka c#](index.md) .

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) `!` `&` operatory,, `|` , i `^` . Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony. Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.

Typ zdefiniowany przez użytkownika nie może przeciążać warunkowych operatorów logicznych `&&` i `||` . Jednakże, jeśli typ zdefiniowany przez użytkownika przeciążuje [Operatory true i false](true-false-operators.md) oraz `&` operator or `|` w określony sposób, `&&` lub `||` operację, odpowiednio, można obliczyć dla operandów tego typu. Aby uzyskać więcej informacji, zapoznaj się z sekcją wyrażenia [warunkowe operatory logiczne zdefiniowane przez użytkownika](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka C#](~/_csharplang/spec/introduction.md):

- [Operator logiczny negacji](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Operatory logiczne](~/_csharplang/spec/expressions.md#logical-operators)
- [Warunkowe operatory logiczne](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Przypisanie złożone](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Operatory przesunięcia i operatory bitowe](bitwise-and-shift-operators.md)
