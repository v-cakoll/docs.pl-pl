---
title: Operatory równości — odwołanie do języka C#
description: Dowiedz się więcej o operatorach porównania równości języka C# i równości typu C#.
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
ms.openlocfilehash: 7dd3e544dc03fb94577892b42aecd1a15a6621ac
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110922"
---
# <a name="equality-operators-c-reference"></a>Operatory równości (odwołanie do języka C#)

Operatorzy [ `==` (równości)](#equality-operator-) i [ `!=` (nierówności)](#inequality-operator-) sprawdzają, czy ich argumenty są równe, czy nie.

## <a name="equality-operator-"></a>Operator równości ==

Operator `==` równości `true` zwraca, jeśli jego argumenty `false` są równe, w przeciwnym razie.

### <a name="value-types-equality"></a>Równość typów wartości

Argumenty [wbudowanych typów wartości](../builtin-types/value-types.md#built-in-value-types) są równe, jeśli ich wartości są równe:

[!code-csharp-interactive[value types equality](snippets/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> Dla `==`, [ `<` `>`, `<=`, `>=` i](comparison-operators.md) operatorów, jeśli którykolwiek z<xref:System.Double.NaN?displayProperty=nameWithType> argumentów nie jest liczbą ( lub <xref:System.Single.NaN?displayProperty=nameWithType>), wynikiem operacji jest `false`. Oznacza to, `NaN` że wartość nie jest większa niż, mniejsza `double` ani `float`równa żadnej `NaN`innej (lub) wartości, w tym . Aby uzyskać więcej informacji i <xref:System.Double.NaN?displayProperty=nameWithType> <xref:System.Single.NaN?displayProperty=nameWithType> przykładów, zobacz artykuł lub odwołania.

Dwa argumenty tego samego typu [wyliczenia](../builtin-types/enum.md) są równe, jeśli odpowiednie wartości typu całkowitego są równe.

Typy [struktury](../builtin-types/struct.md) zdefiniowane przez użytkownika `==` domyślnie nie obsługują operatora. Aby obsługiwać `==` operatora, struktura zdefiniowana przez użytkownika musi ją [przeciążyć.](operator-overloading.md)

Począwszy od języka C# 7.3, `==` i `!=` operatorów są obsługiwane przez [krotek](../../tuples.md)C# . Aby uzyskać więcej informacji, zobacz [równości i krotek](../../tuples.md#equality-and-tuples) sekcji [C# krotka artykułu.](../../tuples.md)

### <a name="reference-types-equality"></a>Równość typów odwołań

Domyślnie dwa argumenty typu odwołania są równe, jeśli odnoszą się do tego samego obiektu:

[!code-csharp[reference type equality](snippets/EqualityOperators.cs#ReferenceTypesEquality)]

Jak pokazano w przykładzie, typy `==` odwołań zdefiniowane przez użytkownika domyślnie obsługują operatora. Jednak typ odwołania może przeciążyć `==` operatora. Jeśli typ odwołania przeciąża `==` operatora, <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> należy użyć metody, aby sprawdzić, czy dwa odwołania tego typu odnoszą się do tego samego obiektu.

### <a name="string-equality"></a>Równość ciągów

Dwa [ciągi](../builtin-types/reference-types.md#the-string-type) są równe, gdy `null` oba wystąpienia są lub oba wystąpienia ciągu mają taką samą długość i mają identyczne znaki w każdej pozycji znaku:

[!code-csharp-interactive[string equality](snippets/EqualityOperators.cs#StringEquality)]

Jest to porównanie porządkowe z uwzględnieniem wielkości liter. Aby uzyskać więcej informacji na temat porównywania [ciągów, zobacz Jak porównać ciągi w języku C#](../../how-to/compare-strings.md).

### <a name="delegate-equality"></a>Deleguj równość

Dwa [argumenty delegata](../../programming-guide/delegates/index.md) tego samego typu środowiska uruchomieniowego `null` są równe, gdy oba są lub ich listy wywołania są tej samej długości i mają równe wpisy w każdej pozycji:

[!code-csharp-interactive[delegate equality](snippets/EqualityOperators.cs#DelegateEquality)]

Aby uzyskać więcej informacji, zobacz delegowania operatorów równości sekcji [specyfikacji języka języka Języka C #, zobacz](~/_csharplang/spec/introduction.md) [delegowanie operatorów równości.](~/_csharplang/spec/expressions.md#delegate-equality-operators)

Delegatów, które są tworzone z oceny semantycznie [identyczne wyrażenia lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nie są równe, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[from identical lambdas](snippets/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a>Operator nierówności !=

Operator `!=` nierówności zwraca, `true` jeśli jego argumenty nie `false` są równe, w przeciwnym razie. W przypadku argumentów [wbudowanych typów](../builtin-types/built-in-types.md)wyrażenie `x != y` daje taki sam wynik `!(x == y)`jak wyrażenie . Aby uzyskać więcej informacji na temat równości typu, zobacz sekcję [operatora równości.](#equality-operator-)

Poniższy przykład pokazuje użycie `!=` operatora:

[!code-csharp-interactive[non-equality examples](snippets/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a>Przeciążenie operatora

Typ zdefiniowany przez użytkownika `==` może `!=` [przeciążać](operator-overloading.md) operatorów i operatorów. Jeśli typ przeciąża jeden z dwóch operatorów, musi również przeciążyć drugi.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [relacyjne i testowania typów operatorów](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) sekcji [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [Porównywanie równości](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [Operatory porównania](comparison-operators.md)
