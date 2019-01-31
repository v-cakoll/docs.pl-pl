---
title: '>> Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 703d4ee50bb9f49c66df029de9c5a280449d11fa
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255318"
---
# <a name="-operator-c-reference"></a>>> — operator (C# odwołania)

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