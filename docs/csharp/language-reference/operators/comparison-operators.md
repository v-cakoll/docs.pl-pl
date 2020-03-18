---
title: Operatory porównania — odwołanie do języka C#
description: Dowiedz się więcej o operatorach porównania języka C#, których można użyć do sprawdzenia kolejności wartości liczbowych.
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
ms.openlocfilehash: 68502205193a1fc8ab7410053e13274560ffffb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399246"
---
# <a name="comparison-operators-c-reference"></a>Operatory porównania (odwołanie do języka C#)

[ `<` (mniej niż)](#less-than-operator-) [ `>` (większe niż)](#greater-than-operator-), [ `<=` (mniejsze lub równe)](#less-than-or-equal-operator-)i [ `>=` (większe lub równe)](#greater-than-or-equal-operator-) porównanie, znane również jako relacyjne, operatorzy porównują swoje argumenty. Te operatory są obsługiwane przez wszystkie [typy liczbowe integralne](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe.](../builtin-types/floating-point-numeric-types.md)

> [!NOTE]
> Dla `==`, `<` `>`, `<=`, `>=` i operatorów, jeśli którykolwiek z argumentów nie jest liczbą (<xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType>), wynikiem działania jest `false`. Oznacza to, `NaN` że wartość nie jest większa niż, mniejsza `double` niż, ani równa żadnej innej (lub) `float`wartości, w tym `NaN`. Aby uzyskać więcej informacji i <xref:System.Double.NaN?displayProperty=nameWithType> <xref:System.Single.NaN?displayProperty=nameWithType> przykładów, zobacz artykuł lub odwołanie.

Typy wyliczania obsługują również operatory porównania. W przypadku argumentów tego samego typu [wyliczenia](../builtin-types/enum.md) porównywane są odpowiednie wartości podstawowego typu integralnego.

[ `==` Operatorzy i `!=` ](equality-operators.md) sprawdzić, czy ich operandy są równe, czy nie.

## <a name="less-than-operator-"></a>Mniej niż operator\<

Operator `<` zwraca, `true` jeśli jego po lewej stronie operand jest `false` mniejsza niż jego prawostronny argument, w przeciwnym razie:

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>Większa niż > operatora

Operator `>` zwraca, `true` jeśli jego po lewej stronie operand jest `false` większa niż jego prawostronny operand, w przeciwnym razie:

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>Mniej niż lub równe operatora\<=

Operator `<=` zwraca, `true` jeśli jego lewy argument jest mniejszy lub równy jego `false` prawostronnemu argumentowi, w przeciwnym razie:

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Większa lub równa >operatora =

Operator `>=` zwraca, `true` jeśli jego lewy argument jest większy lub równy jego `false` prawostronnemu argumentowi, w przeciwnym razie:

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Przeciążenie operatora

Typ zdefiniowany przez użytkownika `<`może `>` `<=` `>=` [przeciążyć](operator-overloading.md) , , i operatorów.

Jeśli typ przeciążenia `<` jednego `>` z operatorów, musi `<` `>`przeciążać zarówno i . Jeśli typ przeciążenia `<=` jednego `>=` z operatorów, musi `<=` `>=`przeciążać zarówno i .

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [relacyjne i typ testowania operatorów](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) sekcji [specyfikacji języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Operatorzy równości](equality-operators.md)
