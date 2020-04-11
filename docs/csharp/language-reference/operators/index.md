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
ms.openlocfilehash: f0ca111000033f9db84145a38e8d567f96b75d1d
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121076"
---
# <a name="c-operators-c-reference"></a>Operatory języka C# (odwołanie do języka C#)

C# zapewnia szereg operatorów obsługiwanych przez wbudowane typy. Na przykład [operatory arytmetyczne](arithmetic-operators.md) wykonują operacje arytmetyczne za pomocą argumentów liczbowych, a [logiczne operatory logiczne logiczne](boolean-logical-operators.md) wykonują operacje logiczne za pomocą argumentów [bool.](../builtin-types/bool.md) Niektóre operatory mogą być [przeciążone](operator-overloading.md). Z przeciążenia operatora, można określić zachowanie operatora dla operands typu zdefiniowanego przez użytkownika.

W [wyrażeniu](../../programming-guide/statements-expressions-operators/expressions.md)pierwszeństwo i zespolenie operatora określają kolejność wykonywania operacji. Nawiasy można użyć, aby zmienić kolejność oceny narzucone przez pierwszeństwo operatora i zespolenie.

## <a name="operator-precedence"></a>Pierwszeństwo operatorów

W wyrażeniu z wieloma operatorami operatory o wyższym priorytecie są oceniane przed operatorami o niższym priorytecie. W poniższym przykładzie mnożenie jest wykonywane najpierw, ponieważ ma wyższy priorytet niż dodawanie:

```csharp-interactive
var a = 2 + 2 * 2;
Console.WriteLine(a); //  output: 6
```

Użyj nawiasów, aby zmienić kolejność oceny narzuconą przez pierwszeństwo operatora:

```csharp-interactive
var a = (2 + 2) * 2;
Console.WriteLine(a); //  output: 8
```

W poniższej tabeli wymieniono operatory języka C#, począwszy od najwyższego pierwszeństwa do najniższego. Operatory w każdym wierszu mają ten sam priorytet.

| Operatory | Kategoria lub nazwa |
| --------- | ---------------- |
| [x.y](member-access-operators.md#member-access-expression-), [x?. y](member-access-operators.md#null-conditional-operators--and-), [x?[ y]](member-access-operators.md#null-conditional-operators--and-), [f(x)](member-access-operators.md#invocation-expression-), [&#91;i&#93;](member-access-operators.md#indexer-operator-), x [++](arithmetic-operators.md#increment-operator-), [x--](arithmetic-operators.md#decrement-operator---), [nowy](new-operator.md), [typeof](type-testing-and-cast.md#typeof-operator), [zaznaczone](../keywords/checked.md), [niezaznaczone](../keywords/unchecked.md), [domyślnie](default.md), [nameof](nameof.md), [delegat](delegate-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [x->y](pointer-related-operators.md#pointer-member-access-operator--) | Podstawowy |
| [+x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [ \!x](boolean-logical-operators.md#logical-negation-operator-), [~x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++x](arithmetic-operators.md#increment-operator-), [--x](arithmetic-operators.md#decrement-operator---), [^x](member-access-operators.md#index-from-end-operator-), [(T)x](type-testing-and-cast.md#cast-expression), [await](await.md), [&x](pointer-related-operators.md#address-of-operator-), [*x](pointer-related-operators.md#pointer-indirection-operator-), [prawda i fałsz](true-false-operators.md) | Jednoargumentowy |
| [X.. Y](member-access-operators.md#range-operator-) | Zakres |
| [switch](../../whats-new/csharp-8.md#switch-expressions) | `switch`Wyrażenie |
| [x * y](arithmetic-operators.md#multiplication-operator-), [x / y](arithmetic-operators.md#division-operator-), [x % y](arithmetic-operators.md#remainder-operator-) | Multiplikatywne|
| [x + y](arithmetic-operators.md#addition-operator-), [x – y](arithmetic-operators.md#subtraction-operator--) | Dodatku |
| [ \< x \< y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-) | Przesunięcia |
| [x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x >= y](comparison-operators.md#greater-than-or-equal-operator-), [jest](type-testing-and-cast.md#is-operator) [,](type-testing-and-cast.md#as-operator) | Badania relacyjne i typu |
| [x == y](equality-operators.md#equality-operator-), [x != y](equality-operators.md#inequality-operator-) | Równość |
| `x & y` | [Logiczne logiczne i](boolean-logical-operators.md#logical-and-operator-) [bitowe logiczne i](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | [Logiczne logiczne XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) lub [logiczne logiczne logiczne XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | [Logiczne logiczne lub](boolean-logical-operators.md#logical-or-operator-) [logiczne logiczne lub logiczne lub logiczne](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x && y](boolean-logical-operators.md#conditional-logical-and-operator-) | AND warunkowe |
| [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | OR warunkowe |
| [X?? Y](null-coalescing-operator.md) | Operator zrzekania się wartości null |
| [C? t : f](conditional-operator.md) | Operator warunkowy |
| [x = y](assignment-operator.md), [x += y](arithmetic-operators.md#compound-assignment), [x -= y](arithmetic-operators.md#compound-assignment), [x *= y](arithmetic-operators.md#compound-assignment), x , [x ,](arithmetic-operators.md#compound-assignment)x , [x %= y](arithmetic-operators.md#compound-assignment), [x &= y](boolean-logical-operators.md#compound-assignment), [x &#124;= y](boolean-logical-operators.md#compound-assignment), [x ^= y](boolean-logical-operators.md#compound-assignment), [x <<= y](bitwise-and-shift-operators.md#compound-assignment), [x >>= y](bitwise-and-shift-operators.md#compound-assignment), [x ?? = y](null-coalescing-operator.md),[=>](lambda-operator.md) | Przypisanie i deklaracja lambda |

## <a name="operator-associativity"></a>Zespolenie operatora

Jeżeli operatory mają ten sam priorytet, skojarzenie operatorów określa kolejność wykonywania operacji:

- *Operatory zespolające lewo* są oceniane w kolejności od lewej do prawej. Z wyjątkiem [operatorów przypisania](assignment-operator.md) i [operatorów zrzeszania wartości null](null-coalescing-operator.md)wszystkie operatory binarne są zespolonej. Na przykład `a + b - c` jest `(a + b) - c`oceniany jako .
- *Operatory zespolające prawo* są oceniane w kolejności od prawej do lewej. Operatory przypisania, operatory zrzeszające wartość null i [ `?:` operator warunkowy](conditional-operator.md) są zespolone z odpowiednimi. Na przykład `x = y = z` jest `x = (y = z)`oceniany jako .

Użyj nawiasów, aby zmienić kolejność oceny narzuconą przez zespolenie operatora:

```csharp-interactive
int a = 13 / 5 / 2;
int b = 13 / (5 / 2);
Console.WriteLine($"a = {a}, b = {b}");  // output: a = 1, b = 6
```

## <a name="operand-evaluation"></a>Ocena operandu

Niezwiązane z pierwszeństwem operatora i zespoleniem, argumenty w wyrażeniu są oceniane od lewej do prawej. Poniższe przykłady pokazują kolejność, w jakiej są oceniane operatory i operandy:

| Wyrażenie | Kolejność obliczeń |
| ---------- | ------------------- |
|`a + b`|a, b, +|
|`a + b * c`|a, b, c, *, +|
|`a / b + c * d`|a, b, /, c, d, *, +|
|`a / (b + c) * d`|a, b, c, +, /, d, *|

Zazwyczaj wszystkie operandy operatora są oceniane. Jednak niektórzy operatorzy oceniają operndy warunkowo. Oznacza to, że wartość lewego operand takiego operatora określa, czy (lub które) inne argumenty powinny być oceniane. Operatory te są operatorami logicznymi warunkowymi [AND`&&`( )](boolean-logical-operators.md#conditional-logical-and-operator-) i OR ( [`||`),](boolean-logical-operators.md#conditional-logical-or-operator-) [operatorami `??` zrzeszeniowymi o `??=`zerowym i ](null-coalescing-operator.md), [operatorami `?.` warunkowymi zerowymi i `?[]` ](member-access-operators.md#null-conditional-operators--and-) [operatorem warunkowym. `?:` ](conditional-operator.md) Aby uzyskać więcej informacji, zobacz opis każdego operatora.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Operatorzy](~/_csharplang/spec/expressions.md#operators) [specyfikacji języka języka języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Wyrażenia](../../programming-guide/statements-expressions-operators/expressions.md)
