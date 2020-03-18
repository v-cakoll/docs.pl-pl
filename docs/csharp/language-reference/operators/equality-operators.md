---
title: Operatory równości — odwołanie do języka C#
description: Dowiedz się więcej o operatorach porównania równości języka C# i równości typów Języka C#.
ms.date: 06/26/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 079522b18afdf86a942d502672174516d45d37fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399568"
---
# <a name="equality-operators-c-reference"></a>Operatory równości (odwołanie do języka C#)

[ `==` Operatorzy (równości)](#equality-operator-) i [ `!=` (nierówności)](#inequality-operator-) sprawdzają, czy ich argumenty są równe, czy nie.

## <a name="equality-operator-"></a>Operator równości ==

Operator `==` równości `true` zwraca, jeśli jego argumenty są równe, `false` w przeciwnym razie.

### <a name="value-types-equality"></a>Równość typów wartości

Argumenty [wbudowanych typów wartości](../builtin-types/value-types.md#built-in-value-types) są równe, jeśli ich wartości są równe:

[!code-csharp-interactive[value types equality](snippets/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> Dla `==`, [ `<` `>`, `<=`, `>=` i](comparison-operators.md) operatorów, jeśli którykolwiek z argumentów <xref:System.Single.NaN?displayProperty=nameWithType>nie jest liczbą ( `false`<xref:System.Double.NaN?displayProperty=nameWithType> lub ), wynikiem działania jest . Oznacza to, `NaN` że wartość nie jest większa niż, mniejsza `double` niż, ani równa żadnej innej (lub) `float`wartości, w tym `NaN`. Aby uzyskać więcej informacji i <xref:System.Double.NaN?displayProperty=nameWithType> <xref:System.Single.NaN?displayProperty=nameWithType> przykładów, zobacz artykuł lub odwołanie.

Dwa argumenty tego samego typu [wyliczenia](../builtin-types/enum.md) są równe, jeśli odpowiednie wartości podstawowego typu integralnego są równe.

Typy [struktury](../builtin-types/struct.md) zdefiniowane przez użytkownika nie `==` obsługują operatora domyślnie. Aby obsługiwać `==` operatora, struktury zdefiniowane przez użytkownika musi [przeciążać](operator-overloading.md) go.

Począwszy od języka C# `==` `!=` 7.3, operatory i są obsługiwane przez [krotek C#](../../tuples.md). Aby uzyskać więcej informacji, zobacz [Równości i krotek](../../tuples.md#equality-and-tuples) sekcji [typu krotka Języka C#.](../../tuples.md)

### <a name="reference-types-equality"></a>Równość typów odwołań

Domyślnie dwa operandy typu odwołania są równe, jeśli odnoszą się do tego samego obiektu:

[!code-csharp[reference type equality](snippets/EqualityOperators.cs#ReferenceTypesEquality)]

Jak pokazano w przykładzie, typy odwołań zdefiniowane przez `==` użytkownika domyślnie obsługują operatora. Jednak typ odwołania może przeciążać `==` operatora. Jeśli typ odwołania przeciążenia `==` operatora, należy użyć <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metody, aby sprawdzić, czy dwa odwołania tego typu odnoszą się do tego samego obiektu.

### <a name="string-equality"></a>Równość ciągów

Dwa [argumenty smyczkowe](../builtin-types/reference-types.md#the-string-type) są równe, `null` gdy oba z nich są lub oba instancje ciągów mają tę samą długość i mają identyczne znaki w każdej pozycji znaku:

[!code-csharp-interactive[string equality](snippets/EqualityOperators.cs#StringEquality)]

Jest to porównanie z uwzględnieniem wielkości liter. Aby uzyskać więcej informacji na temat porównywania [ciągów, zobacz Jak porównać ciągi w języku C#](../../how-to/compare-strings.md).

### <a name="delegate-equality"></a>Delegowanie równości

Dwa operandy [delegata](../../programming-guide/delegates/index.md) tego samego typu wykonywania są `null` równe, gdy oba z nich są lub ich listy wywołań są tej samej długości i mają równe wpisy w każdej pozycji:

[!code-csharp-interactive[delegate equality](snippets/EqualityOperators.cs#DelegateEquality)]

Aby uzyskać więcej informacji, zobacz [delegowanie operatorów równości](~/_csharplang/spec/expressions.md#delegate-equality-operators) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

Delegatów, które są produkowane z oceny semantycznie [identyczne wyrażenia lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nie są równe, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[from identical lambdas](snippets/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a>Operator nierówności !=

Operator `!=` nierówności `true` zwraca, jeśli jego argumenty `false` nie są równe, w przeciwnym razie. Dla operandów [typów wbudowanych](../builtin-types/built-in-types.md)wyrażenie `x != y` daje taki sam wynik jak `!(x == y)`wyrażenie . Aby uzyskać więcej informacji na temat równości typów, zobacz [Equality operator](#equality-operator-) sekcji.

W poniższym przykładzie przedstawiono `!=` użycie operatora:

[!code-csharp-interactive[non-equality examples](snippets/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a>Przeciążenie operatora

Typ zdefiniowany przez użytkownika `==` może `!=` [przeciążać](operator-overloading.md) i operatorów. Jeśli typ przeciążenia jednego z dwóch operatorów, musi również przeciążenia innego.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [relacyjne i typ testowania operatorów](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) sekcji [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [Porównywanie równości](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [Operatory porównania](comparison-operators.md)
