---
title: Operatory porównania — odwołanie w C#
description: Więcej informacji na temat operatorów porównania języka C#, których można użyć do sprawdzenia kolejności wartości liczbowych.
ms.date: 05/11/2020
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
ms.openlocfilehash: eda039d950e4be13d9c041c8bb95b6ea773b83f6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207228"
---
# <a name="comparison-operators-c-reference"></a>Operatory porównania (odwołanie w C#)

[ `<` (Mniejsze niż)](#less-than-operator-), [ `>` (większe](#greater-than-operator-)niż), [ `<=` (mniejsze niż lub równe)](#less-than-or-equal-operator-)i [ `>=` (większe niż lub równe)](#greater-than-or-equal-operator-) porównanie, znane także jako relacyjne, operatory porównują ich operandy. Te operatory są obsługiwane przez wszystkie typy liczbowe [całkowite](../builtin-types/integral-numeric-types.md) i [zmiennoprzecinkowe](../builtin-types/floating-point-numeric-types.md) .

> [!NOTE]
> Dla `==` operatorów, `<` , `>` , `<=` i `>=` , jeśli którykolwiek z operandów nie jest liczbą ( <xref:System.Double.NaN?displayProperty=nameWithType> lub <xref:System.Single.NaN?displayProperty=nameWithType> ), wynikiem operacji jest `false` . Oznacza to, że `NaN` wartość nie jest większa niż, mniejsza niż ani równa żadnej innej `double` wartości (lub `float` ), w tym `NaN` . Aby uzyskać więcej informacji i przykładów, zobacz <xref:System.Double.NaN?displayProperty=nameWithType> <xref:System.Single.NaN?displayProperty=nameWithType> artykuł lub dokumentacja.

Typ [char](../builtin-types/char.md) obsługuje również operatory porównania. W przypadku `char` operandów, odpowiednie kody znaków są porównywane.

Typy wyliczeniowe obsługują również operatory porównania. Dla operandów tego samego typu [wyliczeniowego](../builtin-types/enum.md) , odpowiadające wartości podstawowego typu całkowitego są porównywane.

[ `==` `!=` Operatory i](equality-operators.md) sprawdzają, czy ich operandy są równe, czy nie.

## <a name="less-than-operator-"></a>Operator mniejszości\<

`<`Operator zwraca `true` , jeśli jego lewy argument operacji jest mniejszy niż jego prawy operand, `false` w przeciwnym razie:

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>Więcej niż > operatora

`>`Operator zwraca `true` , jeśli jego argument operacji po lewej stronie jest większy niż jego prawy operand, `false` w przeciwnym razie:

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>Operator mniejszości lub równości\<=

`<=`Operator zwraca `true` , jeśli jego lewy argument operacji jest mniejszy lub równy jego operandu po prawej stronie, `false` w przeciwnym razie:

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Większe niż lub równe >operatora =

`>=`Operator zwraca `true` , jeśli jego argument operacji po lewej stronie jest większy lub równy jego operandu po prawej stronie, `false` w przeciwnym razie:

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Przeciążanie operatora

Typ zdefiniowany przez użytkownika może [przeciążać](operator-overloading.md) `<` `>` operatory,, `<=` , i `>=` .

Jeśli typ przeciąża jeden z `<` `>` operatorów lub, musi przeciążać jednocześnie `<` i `>` . Jeśli typ przeciąża jeden z `<=` `>=` operatorów lub, musi przeciążać jednocześnie `<=` i `>=` .

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [Operatory relacyjne i testowe typu](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Operatory równości](equality-operators.md)
