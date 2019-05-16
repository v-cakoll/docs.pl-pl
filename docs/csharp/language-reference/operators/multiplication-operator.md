---
title: '* Operator - C# odwołania'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: 76ba0d9ac9ea6a2859dda31988588c3b3dd21807
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632919"
---
# <a name="-operator-c-reference"></a>* — operator (C# odwołania)

`*` Operator jest obsługiwany w dwóch formach: operatora jednoargumentowego operatora pośredniego wskaźnika lub operatora mnożenia danych binarnych.

## <a name="pointer-indirection-operator"></a>Operatora pośredniego wskaźnika

Użyj jednoargumentowego `*` operator można uzyskać zmiennej, na który wskazuje operand typu wskaźnika. Aby uzyskać więcej informacji, zobacz [porady: uzyskiwanie wartości zmiennej wskaźnikowej](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-value-of-a-pointer-variable.md).

Operatora pośredniego wskaźnika `*` wymaga [niebezpieczne](../keywords/unsafe.md) kontekstu.

## <a name="multiplication-operator"></a>Operator mnożenia

Dla typów liczbowych `*` operator Oblicza iloczyn argumentów:

[!code-csharp-interactive[multiplication](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#Multiply)]

## <a name="operator-overloadability"></a>Overloadability — operator

Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) dane binarne `*` operatora. Gdy dane binarne `*` operator jest przeciążony, [operator przypisania mnożenia](multiplication-assignment-operator.md) `*=` jest również niejawnie przeciążona.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [operację wskaźnika pośredniego](~/_csharplang/spec/unsafe-code.md#pointer-indirection) i [operator mnożenia](~/_csharplang/spec/expressions.md#multiplication-operator) sekcje [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md)
