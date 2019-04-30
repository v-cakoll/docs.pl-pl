---
title: + Operator - C# odwołania
ms.custom: seodec18
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 0f04ba837f9c03107acd0b2174cbd07c14a8c213
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660167"
---
# <a name="-operator-c-reference"></a>+ — Operator (odwołanie w C#)

`+` Operator jest obsługiwany w dwóch formach: jednoargumentowe plus operatora lub operator binarny dodawania.

## <a name="unary-plus-operator"></a>Jednoargumentowy operator plus

Jednoargumentowy `+` operator zwraca wartość swojego operandu. Jest ona obsługiwana przez wszystkie typy liczbowe.

## <a name="numeric-addition"></a>Dodawanie numeryczne

Dla typów liczbowych `+` operator oblicza sumę argumentów:

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

Aby uzyskać więcej informacji na temat operatory arytmetyczne zobaczyć [operatorów arytmetycznych](arithmetic-operators.md).

## <a name="string-concatenation"></a>{1&gt;Łączenie ciągów&lt;1}

Kiedy jeden lub obydwa operandy są typu [ciąg](../keywords/string.md), `+` operator łączy ciągów reprezentujących argumentów:

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

Począwszy od C# 6, [Interpolacja ciągów](../tokens/interpolated.md) zapewnia wygodny sposób na ciągi formatu:

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Delegatów

Aby uzyskać [delegować](../keywords/delegate.md) typów `+` operator zwraca nowe wystąpienie delegata, gdy wywoływany, wywołuje pierwszy operand, a następnie wywołuje drugiego operandu. Jeśli którykolwiek z argumentów jest `null`, `+` operator zwraca wartość innego operandu (które mogą być również `null`). W poniższym przykładzie pokazano, jak delegaty można łączyć z `+` operator:

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

Aby uzyskać więcej informacji na temat typów obiektów delegowanych, zobacz [delegatów](../../programming-guide/delegates/index.md).

## <a name="operator-overloadability"></a>Overloadability — operator

Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) jednoargumentowy i danych binarnych `+` operatorów. Gdy dane binarne `+` operator jest przeciążony, [operator przypisania dodawania](addition-assignment-operator.md) `+=` jest również niejawnie przeciążona.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [jednoargumentowe plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) i [operator dodawania](~/_csharplang/spec/expressions.md#addition-operator) sekcje [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [Interpolacja ciągów](../tokens/interpolated.md)
- [Instrukcje: Łączenie wielu ciągów](../../how-to/concatenate-multiple-strings.md)
- [Delegaty](../../programming-guide/delegates/index.md)
- [Checked i unchecked](../keywords/checked-and-unchecked.md)
