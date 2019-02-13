---
title: '>> Operator - C# odwołania'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 809cd2cab29d3378892ea224cf846e9d0909b073
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219727"
---
# <a name="-operator-c-reference"></a>>> — operator (C# odwołania)

Operator przesunięcia w prawo `>>` bezpośrednio przenosi swojego pierwszego operandu przez liczbę bitów definicją drugim argumentem. Obsługa wszystkich typów całkowitych `>>` operatora. Jednak typ drugiego argumentu operacji musi być [int](../keywords/int.md) lub typ, który ma [wstępnie zdefiniowane niejawnych konwersji liczbowych](../keywords/implicit-numeric-conversions-table.md) do `int`.

Operacja przesunięcia w prawo powoduje odrzucenie mniej znaczące bity. Pozycje bitów pusty wyższego rzędu jest ustawiona na podstawie typu pierwszego operandu w następujący sposób:

- Jeśli pierwszy operand jest typu [int](../keywords/int.md) lub [długie](../keywords/long.md), operator przesunięcia w prawo wykonuje **arytmetyczne** shift: wartość najbardziej znaczący bit (bit znaku) pierwszego argument operacji jest propagowana do pozycji bitów pusty wyższego rzędu. Oznacza to, pozycje bitów pusty wyższego rzędu są ustawiane na zero, jeśli pierwszy argument jest ujemna i ustawiony na wartość 1, jeśli jest ujemna.

- Jeśli pierwszy operand jest typu [uint](../keywords/uint.md) lub [ulong](../keywords/ulong.md), operator przesunięcia w prawo wykonuje **logiczne** shift: pozycje bitów pusty wyższego rzędu są zawsze ustawione na zero.

Poniższy przykład przedstawia tego zachowania:

[!code-csharp-interactive[right shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShift)]

## <a name="shift-count"></a>Licznik przesunięć

Dla wyrażenia `x >> count`, licznik przesunięć rzeczywistego zależy od rodzaju `x` w następujący sposób:

- Jeśli typ `x` jest [int](../keywords/int.md) lub [uint](../keywords/uint.md), licznik przesunięć jest nadawana przez niskiego rzędu *pięć* bitów drugiego operandu. Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x1F` (lub `count & 0b_1_1111`).

- Jeśli typ `x` jest [długie](../keywords/long.md) lub [ulong](../keywords/ulong.md), licznik przesunięć jest nadawana przez niskiego rzędu *sześć* bitów drugiego operandu. Oznacza to, że licznik przesunięć jest obliczany na podstawie `count & 0x3F` (lub `count & 0b_11_1111`).

Poniższy przykład przedstawia tego zachowania:

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftByLargeCount)]

## <a name="remarks"></a>Uwagi

Operacje przesunięcia nigdy nie powodują przepełnienia i działają tak samo w [checked i unchecked](../keywords/checked-and-unchecked.md) kontekstów.

## <a name="operator-overloadability"></a>Overloadability — operator

Typy zdefiniowane przez użytkownika może [przeciążenia](../keywords/operator.md) `>>` operatora. Jeśli typ zdefiniowany przez użytkownika `T` przeciążenia `>>` operatora, musi być typem pierwszego operandu `T` i typ drugiego argumentu operacji musi być `int`. Gdy `>>` operator jest przeciążony, [operator przypisania przesunięcia w prawo](right-shift-assignment-operator.md) `>>=` jest również niejawnie przeciążona.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [operatory przesunięcia](~/_csharplang/spec/expressions.md#shift-operators) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [C#Operatory](index.md)
- [<< — operator](left-shift-operator.md)