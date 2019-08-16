---
title: C#Operatory — C# odwołanie
ms.date: 04/30/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: a072ff48005155df86fbfe756a772e08a3b0d8db
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545171"
---
# <a name="c-operators-c-reference"></a>C#Operatory (C# odwołanie)

C#udostępnia wiele wstępnie zdefiniowanych operatorów obsługiwanych przez typy wbudowane. Na przykład [Operatory arytmetyczne](arithmetic-operators.md) wykonują operacje arytmetyczne przy użyciu operandów wbudowanych typów liczbowych i logicznych [Operatory logiczne](boolean-logical-operators.md) wykonują operacje logiczne przy użyciu operandów [bool](../keywords/bool.md) .

Typ zdefiniowany przez użytkownika może przeciążać pewne operatory, aby zdefiniować odpowiednie zachowanie dla operandów tego typu. Aby uzyskać więcej informacji, zobacz przeciążanie [operatora](operator-overloading.md).

Poniższa tabela zawiera listę C# operatorów zaczynających się od najwyższego pierwszeństwa. Operatory w poszczególnych wierszach mają ten sam poziom pierwszeństwa.

| Operatory | Kategoria lub nazwa |
| --------- | ---------------- |
| [x. y](member-access-operators.md#member-access-operator-), [x?. y](member-access-operators.md#null-conditional-operators--and-), [x? [ y]](member-access-operators.md#null-conditional-operators--and-), [f (x)](member-access-operators.md#invocation-operator-), [a&#91;&#93;](member-access-operators.md#indexer-operator-), [x + +](arithmetic-operators.md#increment-operator-), [x--](arithmetic-operators.md#decrement-operator---), [New](new-operator.md), [typeof](type-testing-and-conversion-operators.md#typeof-operator), [Checked](../keywords/checked.md), unchecked, [default](default.md), [nameof](nameof.md), [Delegate](delegate-operator.md), [sizeof](sizeof.md), [](../keywords/unchecked.md) [stackalloc](stackalloc.md), [x-> y](pointer-related-operators.md#pointer-member-access-operator--) | Podstawowy |
| [+ x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [ \!x](boolean-logical-operators.md#logical-negation-operator-), [~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [+ + x](arithmetic-operators.md#increment-operator-), [--x](arithmetic-operators.md#decrement-operator---), [(T) x](type-testing-and-conversion-operators.md#cast-operator-), [await](../keywords/await.md), [& x](pointer-related-operators.md#address-of-operator-), [* x](pointer-related-operators.md#pointer-indirection-operator-), [true i false](true-false-operators.md) | Jednostk |
| [x * y](arithmetic-operators.md#multiplication-operator-), [x/y](arithmetic-operators.md#division-operator-), [x% y](arithmetic-operators.md#remainder-operator-) | Mnożeniowy|
| [x + y](arithmetic-operators.md#addition-operator-), [x – y](arithmetic-operators.md#subtraction-operator--) | Dana |
| [ x\< y ,\< ](bitwise-and-shift-operators.md#left-shift-operator-) [x > > y](bitwise-and-shift-operators.md#right-shift-operator-) | Shift |
| [x\< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x > = y](comparison-operators.md#greater-than-or-equal-operator-), [is](type-testing-and-conversion-operators.md#is-operator), [as](type-testing-and-conversion-operators.md#as-operator) | Relacyjne i testy typu |
| [x = = y](equality-operators.md#equality-operator-), [x! = y](equality-operators.md#inequality-operator-) | Równości |
| `x & y` | Koniunkcja logiczna logicznej [i](boolean-logical-operators.md#logical-and-operator-) [koniunkcji logicznej](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | Logiczna logiczna [XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) lub [KONIUNKCJa logiczna XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | Logiczna [logiczne or](boolean-logical-operators.md#logical-or-operator-) lub [bitowe logiczne lub](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) | Warunkowego AND |
| [x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | Warunkowego OR |
| [x? t](null-coalescing-operator.md) | Operator łączenia wartości null |
| [s? t: f](conditional-operator.md) | Operator warunkowy |
| [x = y](assignment-operator.md), [x + = y](arithmetic-operators.md#compound-assignment), [x-= y](arithmetic-operators.md#compound-assignment), [x * = y](arithmetic-operators.md#compound-assignment), [x/= y](arithmetic-operators.md#compound-assignment), [x% = y](arithmetic-operators.md#compound-assignment), [x & = y](boolean-logical-operators.md#compound-assignment), [x &#124;= y](boolean-logical-operators.md#compound-assignment), [x ^ = y](boolean-logical-operators.md#compound-assignment), [x < < = y](bitwise-and-shift-operators.md#compound-assignment), [x > > = y](bitwise-and-shift-operators.md#compound-assignment),[=>](lambda-operator.md) | Przypisanie i Deklaracja lambda |

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory](../../programming-guide/statements-expressions-operators/operators.md)
