---
title: + i += operatory — odwołanie do języka C#
ms.date: 05/24/2019
f1_keywords:
- +_CSharpKeyword
- +=_CSharpKeyword
helpviewer_keywords:
- addition operator [C#]
- concatenation operator [C#]
- delegate combination [C#]
- + operator [C#]
- addition assignment operator [C#]
- event subscription [C#]
- += operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: cafd07f4b4aefdcc4b43750d61c155fe3d65aa46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399302"
---
# <a name="-and--operators-c-reference"></a>+ i += operatory (odwołanie do Języka C#)

`+` Operatory `+=` i są obsługiwane przez wbudowane [typy liczbowe integralne](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe,](../builtin-types/floating-point-numeric-types.md) typ [ciągu](../builtin-types/reference-types.md#the-string-type) i typy [delegatów.](../builtin-types/reference-types.md#the-delegate-type)

Aby uzyskać informacje na `+` temat operatora arytmetycznego, zobacz [operatory nieparzyste plus i minus](arithmetic-operators.md#unary-plus-and-minus-operators) [oraz Operator dodawania +](arithmetic-operators.md#addition-operator-) w artykule [Operatory arytmetyczne.](arithmetic-operators.md)

## <a name="string-concatenation"></a>Ciągów

Gdy jeden lub oba operandy są `+` [typu ciągu,](../builtin-types/reference-types.md#the-string-type)operator łączy reprezentacje ciągu jego operands:

[!code-csharp-interactive[string concatenation](snippets/AdditionOperator.cs#AddStrings)]

Począwszy od C# 6, [interpolacja ciągów](../tokens/interpolated.md) zapewnia wygodniejszy sposób formatowania ciągów:

[!code-csharp-interactive[string interpolation](snippets/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Kombinacja pełnomocników

W przypadku operandów tego samego `+` typu [delegata](../builtin-types/reference-types.md#the-delegate-type) operator zwraca nowe wystąpienie delegata, które po wywołaniu wywołuje operand po lewej stronie, a następnie wywołuje operand po prawej stronie. Jeśli którykolwiek z argumentów `null` `+` jest , operator zwraca wartość innego operand (który również może być `null`). W poniższym przykładzie pokazano, jak `+` delegatów można łączyć z operatorem:

[!code-csharp-interactive[delegate combination](snippets/AdditionOperator.cs#AddDelegates)]

Aby wykonać usunięcie delegata, należy użyć [ `-` operatora](subtraction-operator.md#delegate-removal).

Aby uzyskać więcej informacji na temat typów pełnomocników, zobacz [Delegatów](../../programming-guide/delegates/index.md).

## <a name="addition-assignment-operator-"></a>Operator przypisania dodatku +=

Wyrażenie używające `+=` operatora, takie jak

```csharp
x += y
```

jest równoważny

```csharp
x = x + y
```

chyba `x` że jest oceniana tylko raz.

W poniższym przykładzie przedstawiono `+=` użycie operatora:

[!code-csharp-interactive[+= examples](snippets/AdditionOperator.cs#AddAndAssign)]

Operator służy `+=` również do określania metody obsługi zdarzeń podczas subskrybowania [zdarzenia](../keywords/event.md). Aby uzyskać więcej informacji, zobacz [Jak: subskrybować i anulować subskrypcję wydarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Przeciążenie operatora

Typ zdefiniowany przez użytkownika `+` może [przeciążać](operator-overloading.md) operatora. Gdy operator `+` binarny jest `+=` przeciążony, operator jest również niejawnie przeciążony. Typ zdefiniowany przez użytkownika nie `+=` może jawnie przeciążać operatora.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) i [Dodawanie operator](~/_csharplang/spec/expressions.md#addition-operator) sekcje [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Jak połączyć wiele ciągów](../../how-to/concatenate-multiple-strings.md)
- [Zdarzenia](../../programming-guide/events/index.md)
- [Operatory arytmetyczne](arithmetic-operators.md)
- [- i -= operatory](subtraction-operator.md)
