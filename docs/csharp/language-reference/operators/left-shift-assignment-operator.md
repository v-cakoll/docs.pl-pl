---
title: << = — operator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: 0a005efa19be24f9adbf9031f562a30f9c1b0e34
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258737"
---
# <a name="-operator-c-reference"></a>\<\<= — operator (C# odwołania)

Operator przypisania przesunięcia w lewo.

## <a name="remarks"></a>Uwagi

Wyrażenie formularza

```csharp
x <<= y
```

jest wykonywane jako

```csharp
x = x << y
```

z tą różnicą, że `x` jest obliczone tylko raz. [Operator <<](left-shift-operator.md) przesuwa `x` w lewo o liczbę bitów określoną przez `y`.

Operatora `<<=` nie można przeciążyć bezpośrednio, ale [operator <<](left-shift-operator.md) (zobacz [operator](../keywords/operator.md)) może zostać przeciążony w typach danych zdefiniowanych przez użytkownika.

## <a name="example"></a>Przykład

[!code-csharp[csRefOperators#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#12)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
