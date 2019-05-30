---
title: Operatory logiczne logiczne - C# odwołania
description: Dowiedz się więcej o C# operatorów, które wykonują logiczna Negacja, połączeniu (oraz) i operacje włączne i wyłączne rozłączenia (lub) argumentów logicznych.
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
ms.openlocfilehash: 3ac3479de0bd3c95256741a8b3075f2e5786b65c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300101"
---
# <a name="boolean-logical-operators-c-reference"></a>Wartość logiczna operatorów logicznych (C# odwołania)

Następujące operatory logiczne wykonania operacji związanych z [bool](../keywords/bool.md) argumenty:

- Jednoargumentowy [ `!` (negacja logiczna)](#logical-negation-operator-) operatora.
- Binarny [ `&` (operator logiczny oraz)](#logical-and-operator-), [ `|` (operator logiczny lub)](#logical-or-operator-), i [ `^` (logiczne OR wyłączne)](#logical-exclusive-or-operator-) operatorów. Te operatory zawsze należy przeprowadzić ocenę oba operandy.
- Binarny [ `&&` (warunkowego operator logiczny oraz)](#conditional-logical-and-operator-) i [ `||` (logiczne OR warunkowe)](#conditional-logical-or-operator-) operatorów. Te operatory ocenić drugi argument operacji tylko wtedy, gdy jest to konieczne.

Dla argumentów operacji [całkowitego](../keywords/integral-types-table.md) typów `&`, `|`, i `^` Operatorzy wykonywać operacje logiczne bitowe. Aby uzyskać więcej informacji, zobacz [operatory bitowe- and -shift](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Operator logiczny negacji!

`!` Operator oblicza Negacja logiczna swojego operandu. Oznacza to, tworzy `true`, jeśli argument daje w wyniku `false`, i `false`, jeśli argument daje w wyniku `true`:

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Negation)]

## <a name="logical-and-operator-amp"></a>Operator logiczny AND &amp;

`&` Operator oblicza logicznego i jego operandu. Wynik `x & y` jest `true` Jeśli oba `x` i `y` zwrócić `true`. W przeciwnym razie wynikiem jest `false`.

`&` Operator ocenia oba operandy nawet wtedy, gdy pierwszy operand ma wartość `false`, dzięki czemu wynik musi być `false` bez względu na wartość drugiego operandu.

W poniższym przykładzie, drugi operand `&` operator jest wywołanie metody, które jest wykonywane niezależnie od wartości pierwszego operandu:

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#And)]

[Warunkowego logicznego operatora AND](#conditional-logical-and-operator-) `&&` również oblicza logicznego i jego operandu, ale nie ocenia drugiego operandu, jeśli pierwszy operand ma wartość `false`.

Dla argumentów operacji typu całkowitoliczbowego `&` oblicza operator [iloczynu bitowego AND logiczne](bitwise-and-shift-operators.md#logical-and-operator-) z argumentów. Jednoargumentowy `&` operator jest [operatora address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Operator logiczny OR wyłączne ^

`^` Operator oblicza wyłącznie logiczny lub, znany także jako XOR logiczne, z argumentów. Wynik `x ^ y` jest `true` Jeśli `x` daje w wyniku `true` i `y` daje w wyniku `false`, lub `x` daje w wyniku `false` i `y` daje w wyniku `true`. W przeciwnym razie wynikiem jest `false`. Oznacza to aby uzyskać `bool` operandów, `^` operator oblicza ten sam wynik jako [operator nierówności](equality-operators.md#inequality-operator-) `!=`.

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Xor)]

Dla argumentów operacji typu całkowitoliczbowego `^` oblicza operator [bitowe wykluczające OR logiczne](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) z argumentów.

## <a name="logical-or-operator-"></a>Operator logiczny OR |

`|` Operator oblicza operator logiczny lub jego operandu. Wynik `x | y` jest `true` Jeśli `x` lub `y` daje w wyniku `true`. W przeciwnym razie wynikiem jest `false`.

`|` Operator ocenia oba operandy nawet wtedy, gdy pierwszy operand ma wartość `true`, dzięki czemu wynik musi być `true` bez względu na wartość drugiego operandu.

W poniższym przykładzie, drugi operand `|` operator jest wywołanie metody, które jest wykonywane niezależnie od wartości pierwszego operandu:

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Or)]

[Warunkowego logicznego operatora OR](#conditional-logical-or-operator-) `||` również oblicza logiczne OR z argumentów, ale nie ocenia drugiego operandu, jeśli pierwszy operand ma wartość `true`.

Dla argumentów operacji typu całkowitoliczbowego `|` oblicza operator [bitowe OR logiczne](bitwise-and-shift-operators.md#logical-or-operator-) z argumentów.

## <a name="conditional-logical-and-operator-ampamp"></a>Operator logiczny AND warunkowe &amp;&amp;

Operator logiczny AND warunkowe `&&`, znany także jako "zwarcie" logicznego operatora AND, oblicza logicznego i jego operandu. Wynik `x && y` jest `true` Jeśli oba `x` i `y` zwrócić `true`. W przeciwnym razie wynikiem jest `false`. Jeśli pierwszy operand ma wartość `false`, drugi operand nie jest oceniany.

W poniższym przykładzie, drugi operand `&&` operator jest wywołanie metody, które nie jest wykonywane, jeśli pierwszy operand ma wartość `false`:

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalAnd)]

[Logicznego operatora AND](#logical-and-operator-) `&` oblicza również operator logiczny oraz z argumentów, ale zawsze ocenia oba operandy.

## <a name="conditional-logical-or-operator-"></a>Operator warunkowy OR logiczne ||

Operator logiczny OR warunkowe `||`, znany także jako "zwarcie" logicznego operatora OR, oblicza operator logiczny lub jego operandu. Wynik `x || y` jest `true` Jeśli `x` lub `y` daje w wyniku `true`. W przeciwnym razie wynikiem jest `false`. Jeśli pierwszy operand ma wartość `true`, drugi operand nie jest oceniany.

W poniższym przykładzie, drugi operand `||` operator jest wywołanie metody, które nie jest wykonywane, jeśli pierwszy operand ma wartość `true`:

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalOr)]

[Operator logiczny OR](#logical-or-operator-) `|` oblicza również logiczne OR z argumentów, ale zawsze ocenia oba operandy.

## <a name="nullable-boolean-logical-operators"></a>Operatory dopuszczające wartość null, Boolean i logiczne

Dla `bool?` operandów, `&` i `|` Operatorzy pomocy technicznej przechowywanymi w trzech logiki. Semantyka te operatory jest zdefiniowane w poniższej tabeli:  
  
|x|t|x i y|x&#124;y|  
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

Zachowanie tych operatorów różni się od zachowania typowe operatora z typami wartości null. Zazwyczaj operator, który jest zdefiniowany w przypadku argumentów operacji typu wartości również można argumentów odpowiedni typ wartości null. Generuje taki operator `null` Jeśli którykolwiek z argumentów jest `null`. Jednak `&` i `|` operatorów może utworzyć inną niż null, nawet jeśli jeden z argumentów jest `null`. Aby uzyskać więcej informacji o zachowaniu operatora z typami wartości null, zobacz [operatory](../../programming-guide/nullable-types/using-nullable-types.md#operators) części [przy użyciu typów dopuszczających wartości zerowe](../../programming-guide/nullable-types/using-nullable-types.md) artykułu.

Można również użyć `!` i `^` operatory o `bool?` operandów, co ilustruje poniższy przykład:

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#WithNullableBoolean)]

Operatory logiczne warunkowe `&&` i `||` nie obsługują `bool?` argumentów operacji.

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

`&`, `|`, I `^` operatory obsługują także przypisanie złożone, co ilustruje poniższy przykład:

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#CompoundAssignment)]

Operatory logiczne warunkowe `&&` i `||` nie obsługują przypisania złożonego.

## <a name="operator-precedence"></a>Pierwszeństwo operatorów

Poniższa lista zamówień operatorów logicznych, zaczynając od najwyższy priorytet do najniższego:

- Operator logiczny negacji `!`
- Operator logiczny AND `&`
- Operator logiczny OR wyłączne `^`
- Operator logiczny OR `|`
- Operator logiczny AND warunkowe `&&`
- Operator logiczny OR warunkowe `||`

Użyj nawiasów, `()`, aby zmienić kolejność oceny nałożonych przez pierwszeństwo operatorów:

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Precedence)]

Aby uzyskać pełną listę C# operatory uporządkowane według poziomu priorytetu, zobacz [ C# operatory](index.md).

## <a name="operator-overloadability"></a>Overloadability — operator

Typ zdefiniowany przez użytkownika może [przeciążenia](../keywords/operator.md) `!`, `&`, `|`, i `^` operatorów. Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania złożonego jest również niejawnie przeciążona. Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania złożonego.

Typ zdefiniowany przez użytkownika nie mogą przeciążać operatory logiczne warunkowe `&&` i `||`. Jednak jeśli typ zdefiniowany przez użytkownika przeciążenia [operatory true i false](true-false-operators.md) i `&` lub `|` operatora w określony sposób, `&&` lub `||` operacji, odpowiednio, może zostać obliczone dla Operandy typu. Aby uzyskać więcej informacji, zobacz [zdefiniowanych przez użytkownika operatorów logicznych warunkowych](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):

- [Operator logiczny negacji](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Operatory logiczne](~/_csharplang/spec/expressions.md#logical-operators)
- [Operatory logiczne warunkowe](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Przydział złożony](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [Bitowe i operatory przesunięcia](bitwise-and-shift-operators.md)
