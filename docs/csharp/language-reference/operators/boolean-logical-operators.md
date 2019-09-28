---
title: Operatory logiczne Boolean — C# odwołanie
description: Dowiedz C# się więcej na temat operatorów, które wykonują logiczne negacje, połączenie (i) i Włączne i wyłączne operacje odłączania (lub) z argumentami operacji logicznych.
ms.date: 04/08/2019
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
ms.openlocfilehash: 39f5be7a667b4e37e84246ef0bfeb03c0099d4b7
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353367"
---
# <a name="boolean-logical-operators-c-reference"></a>Logiczna operatory logiczne (C# odwołanie)

Następujące operatory wykonują operacje logiczne przy użyciu operandów [bool](../keywords/bool.md) :

- Jednoargumentowy [`!` (Negacja logiczna)](#logical-negation-operator-) .
- Binarny [`&` (logiczny i)](#logical-and-operator-), [`|` (logiczne OR)](#logical-or-operator-)i [`^` (logiczne wyłącznych lub)](#logical-exclusive-or-operator-) . Te operatory zawsze obliczają oba operandy.
- Binarny [`&&` (warunkowe logiczne i)](#conditional-logical-and-operator-) i [`||` (warunkowe operatory logiczne or)](#conditional-logical-or-operator-) . Te operatory obliczają operand z prawej strony tylko wtedy, gdy jest to konieczne.

Dla argumentów operacji typów [całkowitych](../builtin-types/integral-numeric-types.md) operatory `&`, `|` i `^` wykonują bitowe operacje logiczne. Aby uzyskać więcej informacji, zobacz [Operatory bitowe i przesunięcia](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Operator logiczny negacji

Operator `!` oblicza logiczne Negacja operandu. Oznacza to, że generuje `true`, jeśli operand zostanie obliczony do `false` i `false`, jeśli operand zostanie obliczony do `true`:

[!code-csharp-interactive[logical negation](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

## <a name="logical-and-operator-"></a>Operatory logiczne i &amp;

Operator `&` oblicza wartość logiczną i jej operandów. Wynik `x & y` jest `true`, jeśli oba `x` i `y` są oceniane do `true`. W przeciwnym razie wynik jest `false`.

Operator `&` oblicza oba operandy nawet wtedy, gdy operand z lewej strony jest obliczany do `false`, tak aby wynik musi być `false` niezależnie od wartości operandu po prawej stronie.

W poniższym przykładzie operand z prawej strony operatora `&` jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:

[!code-csharp-interactive[logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

[Warunkowe operatory logiczne i](#conditional-logical-and-operator-) `&&` oblicza również wartość logiczną i jej operandy, ale nie oblicza wartości operandu po prawej stronie, jeśli wartość argumentu po lewej strony jest równa `false`.

Dla operandów typów całkowitych operator `&` oblicza koniunkcję [bitową i](bitwise-and-shift-operators.md#logical-and-operator-) jej operandy. Operator jednoargumentowy `&` jest operatorem [Address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Operator wyłączny logicznego OR ^

Operator `^` oblicza wartość logiczną na wyłączność lub, znaną również jako logiczna XOR, dla argumentów operacji. Wynik `x ^ y` to `true`, jeśli `x` szacuje się `true` i `y` oblicza do `false`, lub `x` szacuje się `false` i `y` szacuje się `true`. W przeciwnym razie wynik jest `false`. Oznacza to, że w przypadku operandów `bool` operator `^` oblicza ten sam wynik jako [operatora nierówności](equality-operators.md#inequality-operator-) `!=`.

[!code-csharp-interactive[logical exclusive OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

Dla operandów typów całkowitych operator `^` oblicza [bitową koniunkcję logiczną wyłącznych lub](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) jego operandów.

## <a name="logical-or-operator-"></a>Operator logiczny OR |

Operator `|` oblicza wartość logiczną lub argumentów operacji. Wynik `x | y` jest `true`, jeśli `x` lub `y` są oceniane do `true`. W przeciwnym razie wynik jest `false`.

Operator `|` oblicza oba operandy nawet wtedy, gdy operand z lewej strony jest obliczany do `true`, tak aby wynik musi być `true` niezależnie od wartości operandu po prawej stronie.

W poniższym przykładzie operand z prawej strony operatora `|` jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:

[!code-csharp-interactive[logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

[Warunkowe operatory logiczne or](#conditional-logical-or-operator-) `||` oblicza również wartość logiczną lub jej operandy, ale nie oblicza wartości operandu po prawej stronie, jeśli argument operacji leworęcznych ma wartość `true`.

Dla operandów typów całkowitych operator `|` oblicza [bitową](bitwise-and-shift-operators.md#logical-or-operator-) koniunkcję lub jej operandów.

## <a name="conditional-logical-and-operator-"></a>Warunkowe operatory logiczne i &amp; @ no__t-2

Warunkowe operatory logiczne i operator `&&`, znane także jako "koniunkcja" typu "Short-obwóding", oblicza wartość logiczną i jej operandów. Wynik `x && y` jest `true`, jeśli oba `x` i `y` są oceniane do `true`. W przeciwnym razie wynik jest `false`. Jeśli `x` szacuje się do `false`, `y` nie jest oceniane.

W poniższym przykładzie operand z prawej strony operatora `&&` jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie szacuje się na `false`:

[!code-csharp-interactive[conditional logical AND](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

[Operator logiczny i](#logical-and-operator-) `&` oblicza również wartość logiczną i jej operandy, ale zawsze oblicza oba operandy.

## <a name="conditional-logical-or-operator-"></a>Warunkowe logiczne OR operator | |

Warunkowe operatory logiczne OR `||`, nazywane także "operatorem" krótkiego obwodu ", oblicza wartość logiczną lub argumentów operacji. Wynik `x || y` jest `true`, jeśli `x` lub `y` są oceniane do `true`. W przeciwnym razie wynik jest `false`. Jeśli `x` szacuje się do `true`, `y` nie jest oceniane.

W poniższym przykładzie operand z prawej strony operatora `||` jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie szacuje się na `true`:

[!code-csharp-interactive[conditional logical OR](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

[Operator logiczny or](#logical-or-operator-) `|` oblicza również wartość logiczną lub argumentów operacji, ale zawsze oblicza oba operandy.

## <a name="nullable-boolean-logical-operators"></a>Logiczne operatory wartości null

W przypadku operandów `bool?` operatory `&` i `|` obsługują logikę z trzema wartościami. Semantyka tych operatorów jest definiowana przez następującą tabelę:  
  
|x|Y|x & y|x&#124;y|  
|----|----|----|----|  
|true|true|true|true|  
|true|false|false|true|  
|true|wartość null|wartość null|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|wartość null|false|wartość null|  
|wartość null|true|wartość null|true|  
|wartość null|false|false|wartość null|  
|wartość null|wartość null|wartość null|wartość null|  

Zachowanie tych operatorów różni się od typowego zachowania operatora z zerowymi typami wartości. Zazwyczaj operator, który jest zdefiniowany dla operandów typu wartości, może być również używany z operandami odpowiadającego typu wartości null. Taki operator wytwarza `null`, jeśli którykolwiek z jego operandów jest `null`. Jednak operatory `&` i `|` mogą generować wartości inne niż null, nawet jeśli jeden z operandów jest `null`. Aby uzyskać więcej informacji o zachowaniu operatora z typami wartości null, zobacz sekcję [operatorów](../../programming-guide/nullable-types/using-nullable-types.md#operators) w artykule [używanie typów wartości dopuszczających wartość null](../../programming-guide/nullable-types/using-nullable-types.md) .

Można również użyć operatorów `!` i `^` z operandami `bool?`, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[lifted negation and xor](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

Warunkowe operatory logiczne `&&` i `||` nie obsługują argumentów operacji `bool?`.

## <a name="compound-assignment"></a>Przypisanie złożone

Dla operatora `op`binarnego wyrażenie złożonego przypisania formularza

```csharp
x op= y
```

odpowiada wyrażeniu

```csharp
x = x op y
```

z tą różnicą, że `x` jest obliczany tylko raz.

Operatory `&`, `|` i `^` obsługują przypisanie złożone, co ilustruje poniższy przykład:

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

Warunkowe operatory logiczne `&&` i `||` nie obsługują przypisania złożonego.

## <a name="operator-precedence"></a>Pierwszeństwo operatorów

Poniższa lista porządkuje operatory logiczne rozpoczynając od najwyższego priorytetu do najniższego:

- Operator logiczny negacji`!`
- Operatory logiczne i `&`
- Operator wyłączny logicznego OR `^`
- @No__t operatora logicznego OR — 0
- Warunkowe operatory logiczne i `&&`
- Warunkowe operatory logiczne OR `||`

Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów:

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz [ C# operatory](index.md).

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory `!`, `&`, `|` i `^`. Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony. Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.

Typ zdefiniowany przez użytkownika nie może przeciążać warunkowych operatorów logicznych `&&` i `||`. Jednakże, jeśli typ zdefiniowany przez użytkownika przeciążuje [Operatory prawdy i FAŁSZ](true-false-operators.md) oraz operator `&` lub `|` w określony sposób, można również ocenić operacje `&&` lub `||` dla operandów tego typu. Aby uzyskać więcej informacji, zapoznaj się z sekcją [Operatory logiczne warunkowe](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Operator logiczny negacji](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Operatory logiczne](~/_csharplang/spec/expressions.md#logical-operators)
- [Warunkowe operatory logiczne](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Przypisanie złożone](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Operatory bitowe i przesunięcia](bitwise-and-shift-operators.md)
