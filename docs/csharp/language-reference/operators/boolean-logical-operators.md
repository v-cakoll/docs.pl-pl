---
title: Operatory logiczne Boolean — C# odwołanie
description: Dowiedz C# się więcej na temat operatorów, które wykonują logiczne negacje, połączenie (i) i Włączne i wyłączne operacje odłączania (lub) z argumentami operacji logicznych.
ms.date: 09/27/2019
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
ms.openlocfilehash: d8fe68fc04300b65bea9b66a6dc6c20e3c69abf4
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239446"
---
# <a name="boolean-logical-operators-c-reference"></a>Logiczna operatory logiczne (C# odwołanie)

Następujące operatory wykonują operacje logiczne z argumentami operacji [bool](../builtin-types/bool.md) :

- Operator jednoargumentowy [`!` (logiczne Negacja)](#logical-negation-operator-) .
- Binarne [`&` (logiczne i)](#logical-and-operator-), [`|` (logiczne lub)](#logical-or-operator-)i [`^` (logiczne wyłącznych lub)](#logical-exclusive-or-operator-) . Te operatory zawsze obliczają oba operandy.
- Binarne [`&&` (warunkowe logiczne i)](#conditional-logical-and-operator-) i [`||` (warunkowe operatory logiczne or)](#conditional-logical-or-operator-) . Te operatory obliczają operand z prawej strony tylko wtedy, gdy jest to konieczne.

W przypadku operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md)operatory `&`, `|`i `^` wykonują bitowe operacje logiczne. Aby uzyskać więcej informacji, zobacz [Operatory bitowe i przesunięcia](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Operator logiczny negacji

Operator jednoargumentowy `!` oblicza logiczne Negacja operandu. Oznacza to, że generuje `true`, jeśli operand zostanie obliczony do `false`i `false`, jeśli operand zostanie obliczony do `true`:

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

Począwszy od C# 8,0, operator jednoargumentowy `!` jest operatorem o [wartości null-łagodniejszej](null-forgiving.md).

## <a name="logical-and-operator-"></a>Operatory logiczne i &amp;

Operator `&` oblicza wartość logiczną i jej operandów. Wynik `x & y` jest `true`, jeśli oba `x` i `y` są oceniane do `true`. W przeciwnym razie wynik jest `false`.

Operator `&` oblicza oba operandy, nawet jeśli argument operacji po lewej stronie szacuje się na `false`, dzięki czemu wynik operacji jest `false` niezależnie od wartości operandu po prawej stronie.

W poniższym przykładzie argument operacji z prawej strony operatora `&` jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

[Warunkowe operatory logiczne i](#conditional-logical-and-operator-) `&&` oblicza również wartości logiczne i jego operandy, ale nie oblicza wartości operandu po prawej stronie, jeśli argument operacji po lewej stronie ma wartość `false`.

Dla operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md)operator `&` oblicza koniunkcję [bitową i](bitwise-and-shift-operators.md#logical-and-operator-) jej operandy. Jednoargumentowy operator `&` jest [operatorem address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Operator wyłączny logicznego OR ^

Operator `^` oblicza wartość logiczną na wyłączność lub, znaną również jako logiczna XOR, jego operandów. Wynik `x ^ y` jest `true`, jeśli `x` oblicza `true` i `y` oblicza `false`, lub `x` oblicza `false`, a `y` oblicza `true`. W przeciwnym razie wynik jest `false`. Oznacza to, że dla operandów `bool` operator `^` oblicza ten sam wynik, co `!=`[operatora nierówności](equality-operators.md#inequality-operator-) .

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

W przypadku operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md)operator `^` oblicza [bitowe logiczne wyłącznych lub](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) jego operandów.

## <a name="logical-or-operator-"></a>Operator logiczny OR |

Operator `|` oblicza wartość logiczną lub argumentów operacji. Wynik `x | y` jest `true`, jeśli `x` lub `y` szacuje się `true`. W przeciwnym razie wynik jest `false`.

Operator `|` oblicza oba operandy, nawet jeśli argument operacji po lewej stronie szacuje się na `true`, dzięki czemu wynik operacji jest `true` niezależnie od wartości operandu po prawej stronie.

W poniższym przykładzie argument operacji z prawej strony operatora `|` jest wywołaniem metody, które jest wykonywane niezależnie od wartości operandu po lewej stronie:

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

[Warunkowy operator logiczny or](#conditional-logical-or-operator-) `||` oblicza również wartość logiczną lub jej operandów, ale nie oblicza wartości operandu po prawej stronie, jeśli argument operacji po lewej stronie szacuje się na `true`.

Dla operandów [całkowitych typów liczbowych](../builtin-types/integral-numeric-types.md)operator `|` oblicza [bitową wartość logiczną lub](bitwise-and-shift-operators.md#logical-or-operator-) jej operandów.

## <a name="conditional-logical-and-operator-"></a>Warunkowe &amp;logiczne i operatory &amp;

Warunkowe operatory logiczne i `&&`, znane także jako operator logiczny "krótki-obwód", oblicza wartość logiczną i argumentów operacji. Wynik `x && y` jest `true`, jeśli oba `x` i `y` są oceniane do `true`. W przeciwnym razie wynik jest `false`. Jeśli `x` oblicza `false`, `y` nie jest oceniane.

W poniższym przykładzie argument operacji po prawej stronie operatora `&&` jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie szacuje się na `false`:

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

[Operator logiczny i](#logical-and-operator-) `&` oblicza również wartości logiczne i jego operandy, ale zawsze oblicza oba operandy.

## <a name="conditional-logical-or-operator-"></a>Warunkowe logiczne OR operator | |

Warunkowe operatory logiczne OR `||`, znane także jako operator logiczny OR "krótkie-obwód", oblicza wartość logiczną lub argumentów operacji. Wynik `x || y` jest `true`, jeśli `x` lub `y` szacuje się `true`. W przeciwnym razie wynik jest `false`. Jeśli `x` oblicza `true`, `y` nie jest oceniane.

W poniższym przykładzie argument operacji po prawej stronie operatora `||` jest wywołaniem metody, które nie jest wykonywane, jeśli argument operacji po lewej stronie szacuje się na `true`:

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

[Operator logiczny or](#logical-or-operator-) `|` oblicza również wartości logiczne lub jego operandy, ale zawsze oblicza oba operandy.

## <a name="nullable-boolean-logical-operators"></a>Logiczne operatory wartości null

Dla argumentów operacji `bool?` operatory `&` i `|` obsługują logikę z trzema wartościami. Semantyka tych operatorów jest definiowana przez następującą tabelę:  
  
|x|{1&gt;y&lt;1}|x & y|x&#124;y|  
|----|----|----|----|  
|true|true|true|true|  
|true|false|false|true|  
|true|null|null|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|null|false|null|  
|null|true|null|true|  
|null|false|false|null|  
|null|null|null|null|  

Zachowanie tych operatorów różni się od typowego zachowania operatora z zerowymi typami wartości. Zazwyczaj operator, który jest zdefiniowany dla operandów typu wartości, może być również używany z operandami odpowiadającego typu wartości null. Taki operator wytwarza `null`, jeśli którykolwiek z jego operandów zwróci `null`. Jednak operatory `&` i `|` mogą generować wartości inne niż null, nawet jeśli jeden z operandów szacuje się w `null`. Aby uzyskać więcej informacji o zachowaniu operatora z typem wartości null, zobacz sekcję [zniesione operatory](../builtin-types/nullable-value-types.md#lifted-operators) w artykule [typy wartości null](../builtin-types/nullable-value-types.md) .

Można również użyć operatorów `!` i `^` z argumentami operacji `bool?`, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

Warunkowe operatory logiczne `&&` i `||` nie obsługują argumentów operacji `bool?`.

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

Operatory `&`, `|`i `^` obsługują przypisanie złożone, co ilustruje poniższy przykład:

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

Warunkowe operatory logiczne `&&` i `||` nie obsługują przypisania złożonego.

## <a name="operator-precedence"></a>Pierwszeństwo operatorów

Poniższa lista porządkuje operatory logiczne rozpoczynając od najwyższego priorytetu do najniższego:

- `!` operatora negacji logicznej
- Operatory logiczne i `&`
- `^` operatora logicznego wyłącznego OR
- `|` operatora logicznego OR
- Warunkowe operatory logiczne i `&&`
- Warunkowe `||` operatora logicznego OR

Użyj nawiasów `()`, aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów:

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

Aby uzyskać pełną listę C# operatorów uporządkowanych według poziomu pierwszeństwa, zobacz sekcję [pierwszeństwo](index.md#operator-precedence) operatorów w artykule [ C# Operators](index.md) .

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory `!`, `&`, `|`i `^`. Gdy operator binarny jest przeciążony, odpowiadający mu operator przypisania złożonego jest również niejawnie przeciążony. Typ zdefiniowany przez użytkownika nie może jawnie przeciążać złożonego operatora przypisania.

Typ zdefiniowany przez użytkownika nie może przeciążać warunkowych operatorów logicznych `&&` i `||`. Jednakże, jeśli typ zdefiniowany przez użytkownika przeciążuje [Operatory true i false](true-false-operators.md) oraz operator `&` lub `|` w określony sposób, `&&` lub `||` operacji, można je obliczyć odpowiednio dla operandów tego typu. Aby uzyskać więcej informacji, zapoznaj się z sekcją [Operatory logiczne warunkowe](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Operator logiczny negacji](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Operatory logiczne](~/_csharplang/spec/expressions.md#logical-operators)
- [Warunkowe operatory logiczne](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Przypisanie złożone](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Zobacz też

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Operatory bitowe i przesunięcia](bitwise-and-shift-operators.md)
