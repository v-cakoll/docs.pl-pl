---
title: Operatory równości — C# odwołanie
description: Dowiedz C# się więcej na temat C# operatorów porównania równości i równości typów.
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
ms.openlocfilehash: 6771edcca8159b0805018c16167b25c287d3152c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743742"
---
# <a name="equality-operators-c-reference"></a>Operatory równości (C# odwołanie)

Operatory [`==` (równość)](#equality-operator-) i [`!=` (nierówność)](#inequality-operator-) sprawdzają, czy ich operandy są równe, czy nie.

## <a name="equality-operator-"></a>Operator równości = =

Operator równości `==` zwraca `true`, jeśli jego operandy są równe, `false` w przeciwnym razie.

### <a name="value-types-equality"></a>Równość typów wartości

Argumenty operacji [wbudowanych typów wartości](../builtin-types/value-types.md#built-in-value-types) są równe, jeśli ich wartości są równe:

[!code-csharp-interactive[value types equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> Dla operatorów `==`, [`<`, `>`, `<=`i `>=`](comparison-operators.md) , jeśli którykolwiek z operandów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>), wynik operacji jest `false`. Oznacza to, że wartość `NaN` nie może być większa niż ani równa żadnej innej wartości `double` (lub `float`), w tym `NaN`. Aby uzyskać więcej informacji i przykładów, zobacz artykuł <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> Reference.

Dwa operandy tego samego typu [wyliczeniowego](../builtin-types/enum.md) są równe, jeśli odpowiadające wartości bazowego typu całkowitego są równe.

Zdefiniowane przez użytkownika typy [struktur](../keywords/struct.md) nie obsługują domyślnie operatora `==`. Aby zapewnić obsługę operatora `==`, struktura zdefiniowana przez użytkownika musi [przeciążać](operator-overloading.md) ją.

Począwszy od C# 7,3 operatory `==` i `!=` są obsługiwane przez C# [krotki](../../tuples.md). Aby uzyskać więcej informacji, zobacz sekcję [równości i krotek](../../tuples.md#equality-and-tuples) w artykule [ C# typy krotek](../../tuples.md) .

### <a name="reference-types-equality"></a>Równość typów referencyjnych

Domyślnie dwa operandy typu odwołania są równe, jeśli odwołują się do tego samego obiektu:

[!code-csharp[reference type equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ReferenceTypesEquality)]

Jak pokazano na przykładzie, zdefiniowane przez użytkownika typy odwołań domyślnie obsługują operator `==`. Jednak typ referencyjny może przeciążać operator `==`. Jeśli typ referencyjny przeciąża operator `==`, użyj metody <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>, aby sprawdzić, czy dwa odwołania tego typu odwołują się do tego samego obiektu.

### <a name="string-equality"></a>Równość ciągów

Dwa operandy [ciągu](../builtin-types/reference-types.md#the-string-type) są równe, gdy oba z nich są `null` lub oba wystąpienia ciągu mają taką samą długość i mają identyczne znaki w każdej pozycji znaku:

[!code-csharp-interactive[string equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#StringEquality)]

Jest to porównanie porządkowe z uwzględnieniem wielkości liter. Aby uzyskać więcej informacji na temat porównywania ciągów, zobacz [Jak porównać C#ciągi w ](../../how-to/compare-strings.md).

### <a name="delegate-equality"></a>Równość delegowania

Dwa operandy [delegatów](../../programming-guide/delegates/index.md) tego samego typu środowiska uruchomieniowego są równe, gdy oba z nich są `null` lub ich listy wywołań są o tej samej długości i mają równe wpisy w każdej pozycji:

[!code-csharp-interactive[delegate equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#DelegateEquality)]

Aby uzyskać więcej informacji, zobacz sekcję [delegowanie operatorów równości](~/_csharplang/spec/expressions.md#delegate-equality-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

Delegaty wytwarzane z oceny semantycznie identycznych [wyrażeń lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nie są równe, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[from identical lambdas](~/samples/csharp/language-reference/operators/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a>Operator nierówności! =

Operator nierówności `!=` zwraca `true`, jeśli jego operandy nie są równe, `false` w przeciwnym razie. Dla argumentów operacji [typu wbudowanego](../keywords/built-in-types-table.md)wyrażenie `x != y` daje ten sam wynik, co `!(x == y)`wyrażenia. Aby uzyskać więcej informacji na temat równości typów, zobacz sekcję [operator równości](#equality-operator-) .

Poniższy przykład ilustruje użycie operatora `!=`:

[!code-csharp-interactive[non-equality examples](~/samples/csharp/language-reference/operators/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory `==` i `!=`. Jeśli typ przeciąża jeden z dwóch operatorów, musi również przeciążać inny.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Operatory relacyjne i testowe typu](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [Porównania równości](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [Operatory porównania](comparison-operators.md)
