---
title: == Operator — C# odwołania
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: 6d86348eefc87e847267f262141ff49e5d51faae
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655962"
---
# <a name="-operator-c-reference"></a>Operator == (odwołanie w C#)

Operator równości `==` zwraca `true` jego operandy są równe, `false` inaczej.

## <a name="value-types-equality"></a>Równość typów wartości

Argumenty operacji [typy wbudowane wartości](../keywords/value-types-table.md) są takie same, jeśli ich wartości są równe:

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> Dla operatorów relacyjnych `==`, `>`, `<`, `>=`, i `<=`, jeśli dowolny z argumentów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>) wynik operacji jest `false`. Oznacza to, że `NaN` wartość jest większe niż, mniejsze ani równy do żadnej innej `double` (lub `float`) wartość. Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> artykule dotyczącym struktury.

Dwóch argumentów operacji tego samego [wyliczenia](../keywords/enum.md) typu są takie same, jeśli odpowiednie wartości typu całkowitego podstawowej są równe.

Domyślnie `==` operator nie jest zdefiniowany dla zdefiniowanej przez użytkownika [struktury](../keywords/struct.md) typu. Typ zdefiniowany przez użytkownika może [przeciążenia](#operator-overloadability) `==` operatora.

Począwszy od C# 7.3, `==` i [ `!=` ](not-equal-operator.md) operatory są obsługiwane przez C# [krotek](../../tuples.md). Aby uzyskać więcej informacji, zobacz [równości i krotek](../../tuples.md#equality-and-tuples) części [ C# typy krotki](../../tuples.md) artykułu.

## <a name="string-equality"></a>Ciąg znaków równości

Dwa [ciąg](../keywords/string.md) operandy są takie same w przypadku, gdy obie z nich są `null` lub oba wystąpienia ciągu mają tę samą długość i mają identyczne znaki w każdym znaku na pozycji:

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

To porównanie porządkowe uwzględniana wielkość liter. Aby uzyskać więcej informacji dotyczących sposobu porównywania ciągów, zobacz [sposób porównywania ciągów w C# ](../../how-to/compare-strings.md).

## <a name="reference-types-equality"></a>Równość typów odwołań

Dwie inne niż `string` operandy typu odwołania są równe, gdy odnoszą się do tego samego obiektu:

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

W przykładzie pokazano, że `==` operator jest obsługiwany przez typy odwołań zdefiniowanych przez użytkownika. Jednakże, typ odwołania zdefiniowane przez użytkownika może doprowadzić do przeciążenia `==` operatora. Jeśli typ referencyjny przeciążenia `==` operatora, użyj <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metodę sprawdzania, jeśli dwa odwołania do tego typu odnoszą się do tego samego obiektu.

## <a name="operator-overloadability"></a>Overloadability — operator

Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `==` operatora. Jeśli typem przeciążenia operatora równości `==`, należy także przeciążyć [operator nierówności](not-equal-operator.md) `!=`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [relacyjne i badania typu operatory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [Porównywanie równości](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
