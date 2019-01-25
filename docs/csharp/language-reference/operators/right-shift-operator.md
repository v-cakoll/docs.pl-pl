---
title: '&gt;&gt; Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: f7cacd740966f0716e125887568a39abf0d9e454
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725431"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt; Operator (odwołanie w C#)

Operator przesunięcia w prawo (`>>`) przenosi pierwszy argument operacji w prawo o liczbę bitów określoną przez drugim argumentem operacji.

## <a name="remarks"></a>Uwagi

Jeśli pierwszy argument jest [int](../keywords/int.md) lub [uint](../keywords/uint.md) (32-bitowy), licznik przesunięć oblicza mniej znaczące bity pięć, drugi operand (drugi operand & 0x1f).

Jeśli pierwszy argument jest [długie](../keywords/long.md) lub [ulong](../keywords/ulong.md) (64-bitowy), licznik przesunięć oblicza mniej znaczące bity sześć, drugi operand (drugi operand & 0x3f).

Jeśli pierwszy argument jest [int](../keywords/int.md) lub [długie](../keywords/long.md), prawy shift jest arytmetycznego przesunięcia (wyższego rzędu pusty bity są ustawione na bit znaku). Jeśli pierwszy operand jest typu [uint](../keywords/uint.md) lub [ulong](../keywords/ulong.md), prawy shift to Przesunięcie logiczne (bity wyższego rzędu są wypełnione przez zera).

Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia `>>` operator; typ pierwszy operand musi być typu zdefiniowanego przez użytkownika, a typ drugiego argumentu operacji musi być [int](../keywords/int.md). Aby uzyskać więcej informacji, zobacz [operator](../keywords/operator.md). Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania, jest również niejawnie przeciążona.

## <a name="example"></a>Przykład

[!code-csharp[csRefOperators#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#26)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [C#Operatory](index.md)