---
title: Operatory równości — odwołanie w C#
description: Dowiedz się więcej na temat operatorów porównania równości języka C# i równości typów języka C#.
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
ms.openlocfilehash: 011ef8b570a0bbbc38ec71df4286c3b08c3109da
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174786"
---
# <a name="equality-operators-c-reference"></a>Operatory równości (odwołanie w C#)

Operatory [ `==` (równość)](#equality-operator-) i [ `!=` (nierówność)](#inequality-operator-) sprawdzają, czy ich operandy są równe, czy nie.

## <a name="equality-operator-"></a>Operator równości = =

Operator równości `==` zwraca `true` , jeśli jego operandy są równe, `false` w przeciwnym razie.

### <a name="value-types-equality"></a>Równość typów wartości

Argumenty operacji [wbudowanych typów wartości](../builtin-types/value-types.md#built-in-value-types) są równe, jeśli ich wartości są równe:

[!code-csharp-interactive[value types equality](snippets/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> Dla `==` operatorów, [ `<` , `>` , `<=` i `>=` ](comparison-operators.md) , jeśli którykolwiek z operandów nie jest liczbą ( <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> ), wynikiem operacji jest `false` . Oznacza to, że `NaN` wartość nie jest większa niż, mniejsza niż ani równa żadnej innej `double` wartości (lub `float` ), w tym `NaN` . Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Double.NaN?displayProperty=nameWithType> <xref:System.Single.NaN?displayProperty=nameWithType> artykuł lub dokumentacja.

Dwa operandy tego samego typu [wyliczeniowego](../builtin-types/enum.md) są równe, jeśli odpowiadające wartości bazowego typu całkowitego są równe.

Zdefiniowane przez użytkownika typy [struktur](../builtin-types/struct.md) nie obsługują `==` operatora domyślnie. Aby zapewnić obsługę `==` operatora, struktura zdefiniowana przez użytkownika musi [przeciążać](operator-overloading.md) ją.

Począwszy od języka C# 7,3 `==` Operatory i `!=` są obsługiwane przez [krotki](../builtin-types/value-tuples.md)języka c#. Aby uzyskać więcej informacji, zobacz sekcję [równość krotki](../builtin-types/value-tuples.md#tuple-equality) w artykule [typy krotek](../builtin-types/value-tuples.md) .

### <a name="reference-types-equality"></a>Równość typów referencyjnych

Domyślnie dwa operandy typu odwołania są równe, jeśli odwołują się do tego samego obiektu:

[!code-csharp[reference type equality](snippets/EqualityOperators.cs#ReferenceTypesEquality)]

Jak pokazano na przykładzie, zdefiniowane przez użytkownika typy odwołań domyślnie obsługują `==` operatora. Jednak typ referencyjny może przeciążać `==` operator. Jeśli typ referencyjny przeciąża `==` operatora, użyj <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metody, aby sprawdzić, czy dwa odwołania tego typu odwołują się do tego samego obiektu.

### <a name="string-equality"></a>Równość ciągów

Dwa operandy [ciągu](../builtin-types/reference-types.md#the-string-type) są równe, gdy oba z nich są `null` lub oba wystąpienia ciągu mają taką samą długość i mają identyczne znaki w każdej pozycji znaku:

[!code-csharp-interactive[string equality](snippets/EqualityOperators.cs#StringEquality)]

Jest to porównanie porządkowe z uwzględnieniem wielkości liter. Aby uzyskać więcej informacji na temat porównywania ciągów, zobacz [Jak porównać ciągi w języku C#](../../how-to/compare-strings.md).

### <a name="delegate-equality"></a>Równość delegowania

Dwa operandy [delegatów](../../programming-guide/delegates/index.md) tego samego typu środowiska uruchomieniowego są równe, gdy oba z nich są `null` lub ich listy wywołań mają taką samą długość i mają równe wpisy w każdej pozycji:

[!code-csharp-interactive[delegate equality](snippets/EqualityOperators.cs#DelegateEquality)]

Aby uzyskać więcej informacji, zobacz sekcję [delegowanie operatorów równości](~/_csharplang/spec/expressions.md#delegate-equality-operators) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).

Delegaty wytwarzane z oceny semantycznie identycznych [wyrażeń lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nie są równe, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[from identical lambdas](snippets/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a>Operator nierówności! =

Operator nierówności `!=` zwraca `true` , jeśli jego operandy nie są równe `false` . w przeciwnym razie. W przypadku operandów [typów wbudowanych](../builtin-types/built-in-types.md)wyrażenie `x != y` daje ten sam wynik co wyrażenie `!(x == y)` . Aby uzyskać więcej informacji na temat równości typów, zobacz sekcję [operator równości](#equality-operator-) .

Poniższy przykład ilustruje użycie `!=` operatora:

[!code-csharp-interactive[non-equality examples](snippets/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) `==` `!=` Operatory i. Jeśli typ przeciąża jeden z dwóch operatorów, musi on również przeciążać pozostałe.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Operatory relacyjne i testowe typu](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [Porównywanie równości](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [Operatory porównania](comparison-operators.md)
