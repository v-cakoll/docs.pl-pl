---
title: Operatory porównania — C# odwołanie
description: Więcej informacji C# na temat operatorów porównania, których można użyć do sprawdzenia kolejności wartości liczbowych.
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
ms.openlocfilehash: 5a9235762effef6f9c0ef501a55bca47ef2510cb
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239423"
---
# <a name="comparison-operators-c-reference"></a>Operatory porównania (C# odwołanie)

[`<` (mniejsze niż)](#less-than-operator-), [`>` (większe niż)](#greater-than-operator-), [`<=` (mniejsze niż lub równe)](#less-than-or-equal-operator-)i [`>=` (większe niż lub równe)](#greater-than-or-equal-operator-) porównanie, znane także jako relacyjne, operatory porównują operandy. Te operatory są obsługiwane przez wszystkie typy liczbowe [całkowite](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe](../builtin-types/floating-point-numeric-types.md) .

> [!NOTE]
> Dla operatorów `==`, `<`, `>`, `<=`i `>=`, jeśli którykolwiek z operandów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>), wynik operacji jest `false`. Oznacza to, że wartość `NaN` nie może być większa niż ani równa żadnej innej wartości `double` (lub `float`), w tym `NaN`. Aby uzyskać więcej informacji i przykładów, zobacz artykuł <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> Reference.

Typy wyliczeniowe obsługują również operatory porównania. Dla operandów tego samego typu [wyliczeniowego](../builtin-types/enum.md) , odpowiadające wartości podstawowego typu całkowitego są porównywane.

[Operatory`==` i `!=`](equality-operators.md) sprawdzają, czy ich operandy są równe, czy nie.

## <a name="less-than-operator-"></a>\< operatora mniejszego niż

Operator `<` zwraca `true`, jeśli jego argument operacji po lewej stronie jest krótszy od jego operandu po prawej stronie, `false` w przeciwnym razie:

[!code-csharp-interactive[less than example](~/samples/snippets/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>Więcej niż > operatora

Operator `>` zwraca `true`, jeśli jego argument operacji po lewej stronie jest większy niż jego prawy operand, `false` w przeciwnym razie:

[!code-csharp-interactive[greater than example](~/samples/snippets/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>Mniejsze niż lub równe \<operatora =

Operator `<=` zwraca `true`, jeśli jego argument operacji po lewej stronie jest mniejszy lub równy jego operandu po prawej stronie, `false` w przeciwnym razie:

[!code-csharp-interactive[less than or equal example](~/samples/snippets/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Większe niż lub równe > operatora =

Operator `>=` zwraca `true`, jeśli jego argument operacji po lewej stronie jest większy lub równy jego operandu po prawej stronie, `false` w przeciwnym razie:

[!code-csharp-interactive[greater than or equal example](~/samples/snippets/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) operatory `<`, `>`, `<=`i `>=`.

Jeśli typ przeciążenia jednego z operatorów `<` lub `>`, musi przeciążać zarówno `<`, jak i `>`. Jeśli typ przeciążenia jednego z operatorów `<=` lub `>=`, musi przeciążać zarówno `<=`, jak i `>=`.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Operatory relacyjne i testowe typu](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz też

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Operatory równości](equality-operators.md)
