---
title: '&amp; Operator (odwołanie w C#)'
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: a8f76ded0ef9f8e8099838a903d90f1695324991
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "43510981"
---
# <a name="amp-operator-c-reference"></a>&amp; Operator (odwołanie w C#)

`&` Operator jest obsługiwany w dwóch formach: operatora address-of jednoargumentowy lub binarny operator logiczny.

## <a name="unary-address-of-operator"></a>Jednoargumentowy operator address-of

Jednoargumentowy `&` operator zwraca adres jego operandu. Aby uzyskać więcej informacji, zobacz [porady: uzyskiwanie adresu zmiennej](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).

Operator address-of `&` wymaga [niebezpieczne](../keywords/unsafe.md) kontekstu.

## <a name="integer-logical-bitwise-and-operator"></a>Operator logiczny AND bitowa liczba całkowita

Dla typów całkowitoliczbowych `&` operator oblicza logiczne bitowe AND argumentów:

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> W poprzednim przykładzie użyto literały binarne [wprowadzona w C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) i [udoskonalone w C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).

Ponieważ operacje na typy całkowite są ogólnie dozwolone w Typy wyliczeniowe `&` obsługuje także operator [wyliczenia](../keywords/enum.md) argumentów operacji.

## <a name="boolean-logical-and-operator"></a>Operator logiczny AND logiczne

Dla [bool](../keywords/bool.md) operandów, `&` operator oblicza logicznego i jego operandu. Wynik `x & y` jest `true` Jeśli oba `x` i `y` są `true`. W przeciwnym razie wynikiem jest `false`.

`&` Operator ocenia oba operandy nawet wtedy, gdy pierwszy operand ma wartość `false`, dzięki czemu wynik musi być `false` bez względu na wartość drugiego operandu. Poniższy przykład przedstawia tego zachowania:

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

[Operatora warunkowego i](conditional-and-operator.md) `&&` również oblicza logicznym, a z argumentów, ale wartość drugiego operandu tylko wtedy, gdy pierwszy operand ma wartość `true`.

Dla argumentów bool dopuszczającego wartość null, zachowanie `&` operator jest zgodne z logiką przechowywanymi w trzech SQL. Aby uzyskać więcej informacji, zobacz [bool? typu](../../programming-guide/nullable-types/using-nullable-types.md#the-bool-type) części [przy użyciu typów dopuszczających wartości zerowe](../../programming-guide/nullable-types/using-nullable-types.md) artykułu.

## <a name="operator-overloadability"></a>Overloadability — operator

Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) pliku binarnego `&` operatora. Gdy dane binarne `&` operator jest przeciążony, [operator przypisania AND](and-assignment-operator.md) `&=` jest również niejawnie przeciążona.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [operatora address-of](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) i [operatorów logicznych](~/_csharplang/spec/expressions.md#logical-operators) sekcje [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [| operator](or-operator.md)
- [^ — operator](xor-operator.md)
- [~ — operator](bitwise-complement-operator.md)
- [& & — operator](conditional-and-operator.md)
