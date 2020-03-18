---
title: Logiczne operatory logiczne logiczne — odwołanie do języka C#
description: Dowiedz się więcej o operatorach języka C#, które wykonują logiczne negacji, spójnik (I) i włącznie i wyłączne operacje rozłączenia (OR) z operandów logicznych.
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
ms.openlocfilehash: 930329b922f585ac4763e6a66d3b192ae839f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399498"
---
# <a name="boolean-logical-operators-c-reference"></a>Logiczne operatory logiczne (odwołanie do języka C#)

Następujące operatory wykonują operacje logiczne z [bool](../builtin-types/bool.md) operands:

- Operator unary [ `!` (logiczne negacji).](#logical-negation-operator-)
- Operatory [ `&` binarne (logiczne i),](#logical-and-operator-) [ `|` (logiczne LUB)](#logical-or-operator-)i [ `^` (logiczne wyłączne LUB).](#logical-exclusive-or-operator-) Operatorzy ci zawsze oceniają oba argumenty.
- Operatory [ `&&` binarne (warunkowe logiczne I)](#conditional-logical-and-operator-) i [ `||` (warunkowe logiczne LUB).](#conditional-logical-or-operator-) Operatorzy ci oceniają argument y po prawej stronie tylko wtedy, gdy jest to konieczne.

W przypadku operandów [zintegrowanych typów numerycznych](../builtin-types/integral-numeric-types.md) `&`, , `|`i `^` operatory wykonują operacje logiczne bitwise. Aby uzyskać więcej informacji, zobacz [Operatory bitowe i przesuwne](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Logiczny operator negacji!

Operator przedrostka `!` unary oblicza logiczne negacji jego operand. Oznacza to, że `true`produkuje , jeśli operand ocenia , `false`i `false`, `true`jeśli operand ocenia:

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

Począwszy od Języka C# 8.0, `!` operator postfix unary jest [operatorem wyrozumiałym.](null-forgiving.md)

## <a name="logical-and-operator-"></a>Operator logiczny AND&amp;

Operator `&` oblicza logiczną i jego operands. Wynik `x & y` jest, `true` jeśli `x` `y` oba `true`i ocenić . W przeciwnym razie `false`wynikiem jest .

Operator `&` ocenia oba argumenty, nawet jeśli operand po `false`lewej stronie ocenia , `false` tak, że wynik operacji jest niezależnie od wartości operand po prawej stronie.

W poniższym przykładzie operand po prawej `&` stronie operatora jest wywołanie metody, które jest wykonywane niezależnie od wartości operand po lewej stronie:

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

[Warunkowe logiczne and operator](#conditional-logical-and-operator-) `&&` oblicza również logiczne i jego operands, ale nie ocenia operand po prawej stronie, `false`jeśli po lewej stronie operand ocenia .

W przypadku operandów [zintegrowanych typów numerycznych](../builtin-types/integral-numeric-types.md) `&` operator oblicza [bitowy logiczny i](bitwise-and-shift-operators.md#logical-and-operator-) jego argumentów. Operator `&` emancypuje. [address-of operator](pointer-related-operators.md#address-of-operator-)

## <a name="logical-exclusive-or-operator-"></a>Logiczny wyłączny operator OR ^

Operator `^` oblicza logiczne wyłączne OR, znany również jako logiczne XOR, jego operands. `x ^ y` Wynik jest, `true` `x` jeśli ocenia `true` `y` i ocenia `false`, `x` lub `false` ocenia `y` i `true`ocenia . W przeciwnym razie `false`wynikiem jest . Oznacza to, `bool` że w przypadku `^` operandów operator oblicza taki sam wynik jak [operator](equality-operators.md#inequality-operator-) `!=`nierówności.

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

W przypadku operandów [zintegrowanych typów numerycznych](../builtin-types/integral-numeric-types.md) `^` operator oblicza [bitowy logiczny wyłączny lub](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) jego operandów.

## <a name="logical-or-operator-"></a>Logiczny operator OR |

Operator `|` oblicza logiczne LUB jego operandów. Wynik `x | y` jest, `true` jeśli `x` `y` albo lub `true`ocenia . W przeciwnym razie `false`wynikiem jest .

Operator `|` ocenia oba argumenty, nawet jeśli operand po `true`lewej stronie ocenia , `true` tak, że wynik operacji jest niezależnie od wartości operand po prawej stronie.

W poniższym przykładzie operand po prawej `|` stronie operatora jest wywołanie metody, które jest wykonywane niezależnie od wartości operand po lewej stronie:

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

[Operator logiczny warunkowy OR](#conditional-logical-or-operator-) `||` oblicza również logiczny OR jego argumentów, ale nie ocenia operandu po `true`prawej stronie, jeśli lewy operand ocenia .

W przypadku argumentów [zintegrowanych typów numerycznych](../builtin-types/integral-numeric-types.md) `|` operator oblicza [bitowy logiczny LUB](bitwise-and-shift-operators.md#logical-or-operator-) jego argumentów.

## <a name="conditional-logical-and-operator-"></a>Operator warunkowego logicznego AND&amp;&amp;

Warunkowe logiczne and `&&`operator , znany również jako "zwarcie" logiczne i operator, oblicza logiczne i jego operands. Wynik `x && y` jest, `true` jeśli `x` `y` oba `true`i ocenić . W przeciwnym razie `false`wynikiem jest . Jeśli `x` zostanie `false`oceniona , `y` nie jest oceniana.

W poniższym przykładzie operand po prawej `&&` stronie operatora jest wywołanie metody, które nie jest wykonywane, `false`jeśli po lewej stronie operand ocenia:

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

[Operator logiczny AND](#logical-and-operator-) `&` oblicza również logiczną i jego argumenty, ale zawsze ocenia oba argumenty.

## <a name="conditional-logical-or-operator-"></a>Warunkowy operator logiczny OR ||

Warunkowe logiczne or `||`operator , znany również jako "zwarcie" logiczny operator OR, oblicza logiczne LUB jego operandów. Wynik `x || y` jest, `true` jeśli `x` `y` albo lub `true`ocenia . W przeciwnym razie `false`wynikiem jest . Jeśli `x` zostanie `true`oceniona , `y` nie jest oceniana.

W poniższym przykładzie operand po prawej `||` stronie operatora jest wywołanie metody, które nie jest wykonywane, `true`jeśli po lewej stronie operand ocenia:

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

[Operator logiczny OR](#logical-or-operator-) `|` oblicza również logiczny LUB jego argumentów, ale zawsze ocenia oba argumenty.

## <a name="nullable-boolean-logical-operators"></a>Operatory logiczne logiczne logiczne wartości null

W `bool?` przypadku `&` operandów `|` operatorzy i operatorzy obsługują logikę trójwartościową. Semantyka tych operatorów jest zdefiniowana przez następującą tabelę:  
  
|x|t|x&y|x&#124;y|  
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

Zachowanie tych operatorów różni się od typowezachowanie operatora z typami wartości nullable. Zazwyczaj operator, który jest zdefiniowany dla operandów typu wartości może być również używany z argumentów odpowiedniego typu wartości nullable. Taki operator produkuje, `null` jeśli którykolwiek z jego `null`operands ocenia . Jednak `&` operatory `|` i może produkować non-null, nawet jeśli jeden `null`z operands ocenia . Aby uzyskać więcej informacji na temat zachowania operatora z typami wartości nullable, zobacz [Lifted operatorów](../builtin-types/nullable-value-types.md#lifted-operators) sekcji [typy wartości nullable.](../builtin-types/nullable-value-types.md)

Można również użyć `!` `^` i `bool?` operatorów z operandów, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

Warunkowe operatory `&&` `||` logiczne i `bool?` nie obsługują operandów.

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

Program `&` `|`, `^` i operatory obsługują przypisanie złożone, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

Warunkowe operatory `&&` `||` logiczne i nie obsługują przypisania złożonego.

## <a name="operator-precedence"></a>Pierwszeństwo operatorów

Poniższa lista porządkuje operatory logiczne, począwszy od najwyższego pierwszeństwa do najniższego:

- Logiczny operator negacji`!`
- Operator logiczny AND`&`
- Logiczny wyłączny operator OR`^`
- Operator logiczny OR`|`
- Operator warunkowego logicznego AND`&&`
- Operator logiczny warunkowy OR`||`

Użyj nawiasów, `()`, aby zmienić kolejność oceny narzuconą przez pierwszeństwo operatora:

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

Aby uzyskać pełną listę operatorów Języka C# uporządkowane według poziomu pierwszeństwa, zobacz [pierwszeństwo operatora](index.md#operator-precedence) sekcji [operatorów C#artykułu.](index.md)

## <a name="operator-overloadability"></a>Przeciążenie operatora

Typ zdefiniowany przez użytkownika `!`może `&` `|` `^` [przeciążyć](operator-overloading.md) , , i operatorów. Gdy operator binarny jest przeciążony, odpowiedni operator przypisania złożonego jest również niejawnie przeciążony. Typ zdefiniowany przez użytkownika nie może jawnie przeciążać operatora przypisania złożonego.

Typ zdefiniowany przez użytkownika nie może `&&` `||`przeciążać operatorów logicznych warunkowych i . Jednak jeśli typ zdefiniowany przez użytkownika przeciąża `&` [operatory true i false](true-false-operators.md) `||` i lub `|` operator w określony sposób, `&&` lub operacji, odpowiednio, mogą być oceniane dla operandów tego typu. Aby uzyskać więcej informacji, zobacz sekcję [Operatory logiczne warunkowe zdefiniowane przez użytkownika](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)

- [Logiczny operator negacji](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Operatory logiczne](~/_csharplang/spec/expressions.md#logical-operators)
- [Warunkowe operatory logiczne](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Przypisanie złożone](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Operatory przesunięcia i operatory bitowe](bitwise-and-shift-operators.md)
