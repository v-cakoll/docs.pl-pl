---
title: '>= — Operator - C# odwołania'
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- '>=_CSharpKeyword'
helpviewer_keywords:
- greater than or equal to operator (>=) [C#]
- '>= operator [C#]'
ms.assetid: 0db4dcaf-56a3-4884-a7ad-35f64978a58d
ms.openlocfilehash: 0dd3aa8976c10f0adc5dc7620237991202f772ee
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545549"
---
# <a name="-operator-c-reference"></a>> = — operator (C# odwołania)

Operator relacyjny "większe lub równe" `>=` zwraca `true` Jeśli pierwszy argument operacji jest większa lub równa drugim argumentem `false` inaczej. Obsługa wszystkich typów liczbowych i wyliczenie `>=` operatora. Dla argumentów operacji tego samego [wyliczenia](../keywords/enum.md) typu, odpowiadające im wartości typu całkowitego podstawowej są porównywane.

> [!NOTE]
> Dla operatorów relacyjnych `==`, `>`, `<`, `>=`, i `<=`, jeśli dowolny z argumentów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>) wynik operacji jest `false`. Oznacza to, że `NaN` wartość jest większe niż, mniejsze ani równy do żadnej innej `double` (lub `float`) wartość. Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> artykule dotyczącym struktury.

W poniższym przykładzie pokazano użycie `>=` operator:

[!code-csharp-interactive[greater than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Overloadability — operator

Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `>=` operatora. Jeśli typem przeciążenia operatora "większe lub równe" `>=`, należy także przeciążyć [operator "mniejsze niż lub równe"](less-than-equal-operator.md) `<=`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [relacyjne i badania typu operatory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [>, operator](greater-than-operator.md)
- [==, operator](equality-operators.md#equality-operator-)
- <xref:System.IComparable%601?displayProperty=nameWithType>
