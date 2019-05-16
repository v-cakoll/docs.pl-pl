---
title: Operatory porównania — C# odwołania
description: Dowiedz się więcej o C# operatorów porównania, które służy do Sprawdź kolejność wartości liczbowych.
ms.date: 04/25/2019
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: 6d3751ff1ee2c6ee2f058eeda4ffd5db188a988e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633757"
---
# <a name="comparison-operators-c-reference"></a>Operatory porównania (C# odwołania)

[ `<` (Mniejsze niż)](#less-than-operator-), [ `>` (większe niż)](#greater-than-operator-), [ `<=` (mniejsze niż lub równe)](#less-than-or-equal-operator-), i [ `>=` () większe niż lub równe)](#greater-than-or-equal-operator-) porównania, nazywana również relacyjna, operatory porównania ich operandami. Te operatory obsługują wszystkie [całkowitego](../keywords/integral-types-table.md) i [zmiennoprzecinkowych](../keywords/floating-point-types-table.md) typów liczbowych.

> [!NOTE]
> Aby uzyskać `==`, `<`, `>`, `<=`, i `>=` operatorów, jeśli dowolny z argumentów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>), wynik operacji jest `false`. Oznacza to, że `NaN` wartość jest większe niż, mniejsze ani równy do żadnej innej `double` (lub `float`) wartość, tym `NaN`. Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> artykule dotyczącym struktury.

Typy wyliczeniowe obsługują także operatory porównania. Dla argumentów operacji tego samego [wyliczenia](../keywords/enum.md) typu, odpowiadające im wartości typu całkowitego podstawowej są porównywane.

[ `==` i `!=` operatory](equality-operators.md) Sprawdź, czy operandy są równe.

## <a name="less-than-operator-"></a>Operator mniejszości \<

`<` Operator zwraca `true` Jeśli pierwszy argument operacji jest mniejszy niż drugi argument operacji `false` inaczej:

[!code-csharp-interactive[less than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Less)]

## <a name="greater-than-operator-"></a>Operator Grater than >

`>` Operator zwraca `true` Jeśli pierwszy argument operacji jest większy niż drugi argument operacji `false` inaczej:

[!code-csharp-interactive[greater than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>Mniejsze niż lub równe — operator \<=

`<=` Operator zwraca `true` Jeśli pierwszy argument operacji jest mniejszy niż drugi argument operacji `false` inaczej:

[!code-csharp-interactive[less than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Większe lub równe — operator > =

`>=` Operator zwraca `true` Jeśli pierwszy argument operacji jest większa lub równa drugim argumentem `false` inaczej:

[!code-csharp-interactive[greater than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Overloadability — operator

Typ zdefiniowany przez użytkownika może [przeciążenia](../keywords/operator.md) `<`, `>`, `<=`, i `>=` operatorów.

Jeśli typem przeciążenia, jeden z `<` lub `>` operatorów, należy przeciąża zarówno `<` i `>`. Jeśli typem przeciążenia, jeden z `<=` lub `>=` operatorów, należy przeciąża zarówno `<=` i `>=`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [relacyjne i badania typu operatory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) części [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Operatory równości](equality-operators.md)
