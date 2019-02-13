---
title: << operator - C# odwołania
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: deea2d0f720ba7f096e65c67378586bc88f24673
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219440"
---
# <a name="-operator-c-reference"></a>\<\< Operator (odwołanie w C#)

Operator przesunięcia w lewo `<<` pierwszy argument operacji lewo o liczbę bitów definicją drugim argumentem operacji przesunięcia. Obsługa wszystkich typów całkowitych `<<` operatora. Jednak typ drugiego argumentu operacji musi być [int](../keywords/int.md) lub typ, który ma [wstępnie zdefiniowane niejawnych konwersji liczbowych](../keywords/implicit-numeric-conversions-table.md) do `int`.

Najbardziej znaczących bitów, które są poza zakresem typu wyniku są odrzucane, a następnie pozycje bitów pusty niskiego rzędu są ustawiane na zero, co ilustruje poniższy przykład:

[!code-csharp-interactive[left shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShift)]

## <a name="shift-count"></a>Licznik przesunięć

Dla wyrażenia `x << count`, licznik przesunięć rzeczywistego zależy od rodzaju `x` w następujący sposób:

- Jeśli typ `x` jest [int](../keywords/int.md) lub [uint](../keywords/uint.md), licznik przesunięć jest nadawana przez niskiego rzędu *pięć* bitów drugiego operandu. Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x1F` (lub `count & 0b_1_1111`).

- Jeśli typ `x` jest [długie](../keywords/long.md) lub [ulong](../keywords/ulong.md), licznik przesunięć jest nadawana przez niskiego rzędu *sześć* bitów drugiego operandu. Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x3F` (lub `count & 0b_11_1111`).

Poniższy przykład przedstawia tego zachowania:

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftByLargeCount)]

## <a name="remarks"></a>Uwagi

Operacje przesunięcia nigdy nie powodują przepełnienia i działają tak samo w [checked i unchecked](../keywords/checked-and-unchecked.md) kontekstów.

## <a name="operator-overloadability"></a>Overloadability — operator

Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `<<` operatora. Jeśli typ zdefiniowany przez użytkownika `T` przeciążenia `<<` operatora, musi być typem pierwszego operandu `T` i typ drugiego argumentu operacji musi być `int`. Gdy `<<` operator jest przeciążony, [operator przypisania przesunięcia w lewo](left-shift-assignment-operator.md) `<<=` jest również niejawnie przeciążona.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [operatory przesunięcia](~/_csharplang/spec/expressions.md#shift-operators) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [>> — operator](right-shift-operator.md)
