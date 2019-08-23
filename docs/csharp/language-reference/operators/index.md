---
title: C#Operatory — C# odwołanie
ms.date: 08/20/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- operators [C#]
- operator precedence [C#]
- operator associativity [C#]
- expressions [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 75697a7a52fbfb04e1b44ecf591e271217a69bf4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924653"
---
# <a name="c-operators-c-reference"></a>C#Operatory (C# odwołanie)

C#udostępnia wiele operatorów obsługiwanych przez typy wbudowane. Na przykład [Operatory arytmetyczne](arithmetic-operators.md) wykonują operacje arytmetyczne przy użyciu liczbowych argumentów operacji, a [Operatory logiczne Boolean](boolean-logical-operators.md) wykonują operacje logiczne przy użyciu operandów [bool](../keywords/bool.md) . Niektóre operatory mogą być [przeciążone](operator-overloading.md). Dzięki przeciążeniu operatora można określić zachowanie operatora dla argumentów operacji typu zdefiniowanego przez użytkownika.

W [wyrażeniu](../../programming-guide/statements-expressions-operators/expressions.md)pierwszeństwo operatorów i łączność określają kolejność wykonywania operacji. Możesz użyć nawiasów, aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów i łączność.

## <a name="operator-precedence"></a>Pierwszeństwo operatorów

W wyrażeniu zawierającym wiele operatorów operatory o wyższym priorytecie są oceniane przed operatorami o niższym priorytecie. W poniższym przykładzie mnożenie jest wykonywane jako pierwsze, ponieważ ma wyższy priorytet niż dodanie:

```csharp-interactive
var a = 2 + 2 * 2;
Console.WriteLine(a); //  output: 6
```

Użyj nawiasów, aby zmienić kolejność oceny nałożona przez pierwszeństwo operatorów:

```csharp-interactive
var a = (2 + 2) * 2;
Console.WriteLine(a); //  output: 8
```

Poniższa tabela zawiera listę C# operatorów zaczynających się od najwyższego pierwszeństwa. Operatory w każdym wierszu mają takie samo pierwszeństwo.

| Operatory | Kategoria lub nazwa |
| --------- | ---------------- |
| [x. y](member-access-operators.md#member-access-operator-), [x?. y](member-access-operators.md#null-conditional-operators--and-), [x? [ y]](member-access-operators.md#null-conditional-operators--and-), [f (x)](member-access-operators.md#invocation-operator-), [a&#91;&#93;](member-access-operators.md#indexer-operator-), [x + +](arithmetic-operators.md#increment-operator-), [x--](arithmetic-operators.md#decrement-operator---), [New](new-operator.md), [typeof](type-testing-and-cast.md#typeof-operator), [Checked](../keywords/checked.md), unchecked, [default](default.md), [nameof](nameof.md), [Delegate](delegate-operator.md), [sizeof](sizeof.md), [](../keywords/unchecked.md) [stackalloc](stackalloc.md), [x-> y](pointer-related-operators.md#pointer-member-access-operator--) | Podstawowy |
| [+ x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [ \!x](boolean-logical-operators.md#logical-negation-operator-), [~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [+ + x](arithmetic-operators.md#increment-operator-), [--x](arithmetic-operators.md#decrement-operator---), [(T) x](type-testing-and-cast.md#cast-operator-), [await](../keywords/await.md), [& x](pointer-related-operators.md#address-of-operator-), [* x](pointer-related-operators.md#pointer-indirection-operator-), [true i false](true-false-operators.md) | Jednostk |
| [x * y](arithmetic-operators.md#multiplication-operator-), [x/y](arithmetic-operators.md#division-operator-), [x% y](arithmetic-operators.md#remainder-operator-) | Mnożeniowy|
| [x + y](arithmetic-operators.md#addition-operator-), [x – y](arithmetic-operators.md#subtraction-operator--) | Dana |
| [ x\< y ,\< ](bitwise-and-shift-operators.md#left-shift-operator-) [x > > y](bitwise-and-shift-operators.md#right-shift-operator-) | Shift |
| [x\< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x > = y](comparison-operators.md#greater-than-or-equal-operator-), [is](type-testing-and-cast.md#is-operator), [as](type-testing-and-cast.md#as-operator) | Relacyjne i testy typu |
| [x = = y](equality-operators.md#equality-operator-), [x! = y](equality-operators.md#inequality-operator-) | Równości |
| `x & y` | Koniunkcja logiczna logicznej [i](boolean-logical-operators.md#logical-and-operator-) [koniunkcji logicznej](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | Logiczna logiczna [XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) lub [KONIUNKCJa logiczna XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | Logiczna [logiczne or](boolean-logical-operators.md#logical-or-operator-) lub [bitowe logiczne lub](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) | Warunkowego AND |
| [x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | Warunkowego OR |
| [x? t](null-coalescing-operator.md) | Operator łączenia wartości null |
| [s? t: f](conditional-operator.md) | Operator warunkowy |
| [x = y](assignment-operator.md), [x + = y](arithmetic-operators.md#compound-assignment), [x-= y](arithmetic-operators.md#compound-assignment), [x * = y](arithmetic-operators.md#compound-assignment), [x/= y](arithmetic-operators.md#compound-assignment), [x% = y](arithmetic-operators.md#compound-assignment), [x & = y](boolean-logical-operators.md#compound-assignment), [x &#124;= y](boolean-logical-operators.md#compound-assignment), [x ^ = y](boolean-logical-operators.md#compound-assignment), [x < < = y](bitwise-and-shift-operators.md#compound-assignment), [x > > = y](bitwise-and-shift-operators.md#compound-assignment),[=>](lambda-operator.md) | Przypisanie i Deklaracja lambda |

## <a name="operator-associativity"></a>Łączność operatora

Gdy operatory mają takie samo pierwszeństwo, łączność operatorów określa kolejność wykonywania operacji:

- Operatory kojarzenia w *lewo* są oceniane w kolejności od lewej do prawej. Z wyjątkiem [operatorów przypisania](assignment-operator.md) i [operatora `??`łączenia wartości null ](null-coalescing-operator.md)wszystkie operatory binarne są z lewej strony skojarzenia. Na przykład, `a + b - c` jest oceniane jako `(a + b) - c`.
- Operatory kojarzenia w *prawo* są oceniane w kolejności od prawej do lewej. Operatory przypisania, operator `??`łączenia wartości null i [operator `?:` warunkowy](conditional-operator.md) są z prawej strony skojarzenia. Na przykład, `x = y = z` jest oceniane jako `x = (y = z)`.

Użyj nawiasów, aby zmienić kolejność oceny nałożona przez operator łączność:

```csharp-interactive
int a = 13 / 5 / 2;
int b = 13 / (5 / 2);
Console.WriteLine($"a = {a}, b = {b}");  // output: a = 1, b = 6
```

## <a name="operand-evaluation"></a>Obliczanie operandu

Niepowiązane z pierwszeństwem operatora i łączność, operandy w wyrażeniu są oceniane od lewej do prawej. W poniższych przykładach pokazano kolejność, w której są oceniane operatory i operandy:

| Wyrażenie | Kolejność obliczeń |
| ---------- | ------------------- |
|`a + b`|a, b, +|
|`a + b * c`|a, b, c, *, +|
|`a / b + c * d`|a, b,/, c, d, *, +|
|`a / (b + c) * d`|a, b, c, +,/, d, *|

Zazwyczaj są oceniane wszystkie operandy operatora. Niektóre operatory jednocześnie szacują operandy. Oznacza to, że wartość pierwszego operandu takiego operatora definiuje, czy należy ocenić inne operandy. Operatory te są operatorami logicznymi [i`&&`](boolean-logical-operators.md#conditional-logical-and-operator-) () i [lub`||`()](boolean-logical-operators.md#conditional-logical-or-operator-) , [operatorem `??`łączenia wartości null ](null-coalescing-operator.md), [operatorami `?.` warunkowymi null i `?[]` ](member-access-operators.md#null-conditional-operators--and-)i [ operator`?:`warunkowy ](conditional-operator.md). Aby uzyskać więcej informacji, zobacz opis każdego operatora.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [operatorów](~/_csharplang/spec/expressions.md#operators) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Wyrażenia](../../programming-guide/statements-expressions-operators/expressions.md)
