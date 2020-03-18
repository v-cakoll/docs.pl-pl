---
title: Operatory języka C# — odwołanie do języka C#
ms.date: 08/20/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- operators [C#]
- operator precedence [C#]
- operator associativity [C#]
- expressions [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 11c544e7fc923b0820141fb2e096ef7707f0a95f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74552477"
---
# <a name="c-operators-c-reference"></a>Operatory języka C# (odwołanie do języka C#)

C# udostępnia szereg operatorów obsługiwanych przez typy wbudowane. Na przykład [operatory arytmetyczne](arithmetic-operators.md) wykonują operacje arytmetyczne z operandami liczbowymi, a [logiczne operatory logiczne logiczne](boolean-logical-operators.md) wykonują operacje logiczne z operandami [bool.](../builtin-types/bool.md) Niektórzy operatorzy mogą być [przeciążeni.](operator-overloading.md) Przy przeciążeniu operatora można określić zachowanie operatora dla operandów typu zdefiniowanego przez użytkownika.

W [wyrażeniu](../../programming-guide/statements-expressions-operators/expressions.md)pierwszeństwo operatora i kojarzenie określają kolejność wykonywania operacji. Nawiasy można użyć do zmiany kolejności oceny nałożone przez pierwszeństwo operatora i kojarzenia.

## <a name="operator-precedence"></a>Pierwszeństwo operatorów

W wyrażeniu z wieloma operatorami operatory o wyższym priorytecie są oceniane przed operatorami o niższym priorytecie. W poniższym przykładzie mnożenie jest wykonywane jako pierwsze, ponieważ ma wyższy priorytet niż dodawanie:

```csharp-interactive
var a = 2 + 2 * 2;
Console.WriteLine(a); //  output: 6
```

Użyj nawiasów, aby zmienić kolejność oceny narzuconą przez pierwszeństwo operatora:

```csharp-interactive
var a = (2 + 2) * 2;
Console.WriteLine(a); //  output: 8
```

W poniższej tabeli wymieniono operatory Języka C#, począwszy od najwyższego pierwszeństwa do najniższego. Operatory w każdym wierszu mają ten sam priorytet.

| Operatory | Kategoria lub nazwa |
| --------- | ---------------- |
| [x.y](member-access-operators.md#member-access-operator-), [x?. y](member-access-operators.md#null-conditional-operators--and-), [x?[ y]](member-access-operators.md#null-conditional-operators--and-), [f(x)](member-access-operators.md#invocation-operator-), [&#91;i&#93;](member-access-operators.md#indexer-operator-), x [++](arithmetic-operators.md#increment-operator-), [x--](arithmetic-operators.md#decrement-operator---), [nowy](new-operator.md), [typeof](type-testing-and-cast.md#typeof-operator), [zaznaczone](../keywords/checked.md), [niezaznaczone](../keywords/unchecked.md), [domyślnie](default.md), [nameof](nameof.md), [delegat](delegate-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [x->y](pointer-related-operators.md#pointer-member-access-operator--) | Podstawowy |
| [+x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [ \!x](boolean-logical-operators.md#logical-negation-operator-), [~x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++x](arithmetic-operators.md#increment-operator-), [--x](arithmetic-operators.md#decrement-operator---), [^x](member-access-operators.md#index-from-end-operator-), [(T)x](type-testing-and-cast.md#cast-operator-), [await](await.md), [&x](pointer-related-operators.md#address-of-operator-), [*x](pointer-related-operators.md#pointer-indirection-operator-), [prawda i fałsz](true-false-operators.md) | Jednoargumentowy |
| [X.. Y](member-access-operators.md#range-operator-) | Zakres |
| [x * y](arithmetic-operators.md#multiplication-operator-), [x / y](arithmetic-operators.md#division-operator-), x % [y](arithmetic-operators.md#remainder-operator-) | Multiplikatywne|
| [x + y](arithmetic-operators.md#addition-operator-), [x – y](arithmetic-operators.md#subtraction-operator--) | Dodatku |
| [ \< x \< y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-) | Przesunięcia |
| [x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), x [ \<= y](comparison-operators.md#less-than-or-equal-operator-), x >= [y](comparison-operators.md#greater-than-or-equal-operator-), [jest](type-testing-and-cast.md#is-operator), [jak](type-testing-and-cast.md#as-operator) | Badanie relacyjne i typu |
| [x == y](equality-operators.md#equality-operator-), [x != y](equality-operators.md#inequality-operator-) | Równość |
| `x & y` | [Logiczne logiczne i](boolean-logical-operators.md#logical-and-operator-) [logiczne i bitowe i](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | [Logiczny XOR lub](boolean-logical-operators.md#logical-exclusive-or-operator-) [logiczny XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | [Logiczny lub](boolean-logical-operators.md#logical-or-operator-) [logiczny LUB logiczny lub logiczny](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x && y](boolean-logical-operators.md#conditional-logical-and-operator-) | AND warunkowe |
| [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | OR warunkowe |
| [X?? Y](null-coalescing-operator.md) | Operator łączenia wartości null |
| [C? t : f](conditional-operator.md) | Operator warunkowy |
| [x = y](assignment-operator.md), [x += y](arithmetic-operators.md#compound-assignment), x [-= y](arithmetic-operators.md#compound-assignment), x [*= y](arithmetic-operators.md#compound-assignment), x [/= y](arithmetic-operators.md#compound-assignment), x [%= y](arithmetic-operators.md#compound-assignment), x &= [y](boolean-logical-operators.md#compound-assignment), x x &#124;[= y](boolean-logical-operators.md#compound-assignment), x [^= y](boolean-logical-operators.md#compound-assignment), x <<= [y](bitwise-and-shift-operators.md#compound-assignment), x >>[= y](bitwise-and-shift-operators.md#compound-assignment), [x ?? = y](null-coalescing-operator.md),[=>](lambda-operator.md) | Przypisanie i deklaracja lambda |

## <a name="operator-associativity"></a>Zespolenie operatora

Gdy operatory mają ten sam priorytet, asocjalność operatorów określa kolejność wykonywania operacji:

- *Operatory zesłanek* lewicowych są oceniane w kolejności od lewej do prawej. Z wyjątkiem [operatorów przypisania](assignment-operator.md) i [operatorów zerowych łączenia](null-coalescing-operator.md), wszystkie operatory binarne są zestosujące. Na przykład `a + b - c` jest oceniana jako `(a + b) - c`.
- *Operatory asocjacyjne* są oceniane w kolejności od prawej do lewej. Operatory przypisania, operatory null-łączenie i [operator `?:` warunkowy](conditional-operator.md) są zestosujące. Na przykład `x = y = z` jest oceniana jako `x = (y = z)`.

Użyj nawiasów, aby zmienić kolejność oceny narzuconą przez kojarzenie operatora:

```csharp-interactive
int a = 13 / 5 / 2;
int b = 13 / (5 / 2);
Console.WriteLine($"a = {a}, b = {b}");  // output: a = 1, b = 6
```

## <a name="operand-evaluation"></a>Ocena operandu

Niezwiązane z pierwszeństwooperatora i kojarzenia, operandy w wyrażeniu są oceniane od lewej do prawej. Poniższe przykłady pokazują kolejność, w jakiej operatory i operandy są oceniane:

| Wyrażenie | Kolejność obliczeń |
| ---------- | ------------------- |
|`a + b`|a, b, +|
|`a + b * c`|a, b, c, *, +|
|`a / b + c * d`|a, b, /, c, d, *, +|
|`a / (b + c) * d`|a, b, c, +, /, d, *|

Zazwyczaj wszystkie operandy operatora są oceniane. Jednak niektóre operatory oceniają operandy warunkowo. Oznacza to, że wartość lewego operandu takiego operatora określa, czy (lub które) inne argumenty powinny być oceniane. Operatory te są operatorami logicznymi [i`&&`()](boolean-logical-operators.md#conditional-logical-and-operator-) i [OR (`||`),](boolean-logical-operators.md#conditional-logical-or-operator-) [operatorami `??` zerowymi i `??=` ](null-coalescing-operator.md) [operatorami warunkowymi `?.` zerowymi oraz `?[]` ](member-access-operators.md#null-conditional-operators--and-) [operatorem warunkowym. `?:` ](conditional-operator.md) Aby uzyskać więcej informacji, zobacz opis każdego operatora.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [sekcję Operatory](~/_csharplang/spec/expressions.md#operators) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Wyrażenia](../../programming-guide/statements-expressions-operators/expressions.md)
