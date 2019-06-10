---
title: Operatory porównania — C# odwołania
description: Dowiedz się więcej o C# operatory porównania równości.
ms.date: 03/28/2019
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
ms.openlocfilehash: 3b2aeceae8371f0728da2bcebbbe597ee135f256
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758266"
---
# <a name="equality-operators-c-reference"></a>Operatory porównania (C# odwołania)

[ `==` (Równości)](#equality-operator-) i [ `!=` (nierówność)](#inequality-operator-) operatorów, sprawdź, czy operandy są równe.

## <a name="equality-operator-"></a>Operator równości ==

Operator równości `==` zwraca `true` jego operandy są równe, `false` inaczej.

### <a name="value-types-equality"></a>Równość typów wartości

Argumenty operacji [typy wbudowane wartości](../keywords/value-types-table.md) są takie same, jeśli ich wartości są równe:

[!code-csharp-interactive[value types equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> Aby uzyskać `==`, [ `<`, `>`, `<=`, i `>=` ](comparison-operators.md) operatorów, jeśli dowolny z argumentów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>), wynik operacji jest `false`. Oznacza to, że `NaN` wartość jest większe niż, mniejsze ani równy do żadnej innej `double` (lub `float`) wartość, tym `NaN`. Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> artykule dotyczącym struktury.

Dwóch argumentów operacji tego samego [wyliczenia](../keywords/enum.md) typu są takie same, jeśli odpowiednie wartości typu całkowitego podstawowej są równe.

Zdefiniowane przez użytkownika [struktury](../keywords/struct.md) typów nie obsługują `==` operator domyślnie. Do obsługi `==` musi struktury zdefiniowany przez użytkownika operatora [przeciążenia](#operator-overloadability) go.

Począwszy od C# 7.3, `==` i `!=` operatory są obsługiwane przez C# [krotek](../../tuples.md). Aby uzyskać więcej informacji, zobacz [równości i krotek](../../tuples.md#equality-and-tuples) części [ C# typy krotki](../../tuples.md) artykułu.

### <a name="string-equality"></a>Ciąg znaków równości

Dwa [ciąg](../keywords/string.md) operandy są takie same w przypadku, gdy obie z nich są `null` lub oba wystąpienia ciągu mają tę samą długość i mają identyczne znaki w każdym znaku na pozycji:

[!code-csharp-interactive[string equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#StringEquality)]

To porównanie porządkowe uwzględniana wielkość liter. Aby uzyskać więcej informacji na temat porównania ciągów, zobacz [sposób porównywania ciągów w C# ](../../how-to/compare-strings.md).

### <a name="reference-types-equality"></a>Równość typów odwołań

Dwie inne niż `string` operandy typu odwołania są równe, gdy odnoszą się do tego samego obiektu:

[!code-csharp-interactive[reference type equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ReferenceTypesEquality)]

Jak pokazano w przykładzie, odwołanie do zdefiniowanych przez użytkownika typy obsługi `==` operator domyślnie. Jednakże, typ odwołania zdefiniowane przez użytkownika może doprowadzić do przeciążenia `==` operatora. Jeśli typ referencyjny przeciążenia `==` operatora, użyj <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metodę sprawdzania, jeśli dwa odwołania do tego typu odnoszą się do tego samego obiektu.

## <a name="inequality-operator-"></a>Operator nierówności! =

Operator nierówności `!=` zwraca `true` argumentów nie są równe, `false` inaczej. Dla argumentów operacji [wbudowanych typów](../keywords/built-in-types-table.md), wyrażenie `x != y` daje ten sam wynik jako wyrażenie `!(x == y)`. Aby uzyskać więcej informacji na temat typu równości zobacz [operatora równości](#equality-operator-) sekcji.

W poniższym przykładzie pokazano użycie `!=` operator:

[!code-csharp-interactive[non-equality examples](~/samples/csharp/language-reference/operators/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a>Overloadability — operator

Typ zdefiniowany przez użytkownika może [przeciążenia](../keywords/operator.md) `==` i `!=` operatorów. Jeśli typem przeciążeń, jeden z dwóch operatorów on także przeciążać inny.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [relacyjne i badania typu operatory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [Porównywanie równości](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [Operatory porównania](comparison-operators.md)
