---
title: '>>= — operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 8cc341c14ee1b90fde2abb369c187e57b4ce5c00
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278983"
---
# <a name="-operator-c-reference"></a>>> = — operator (C# odwołania)

Operator przypisania przesunięcia w prawo.

## <a name="remarks"></a>Uwagi

Wyrażenie formularza

```csharp
x >>= y
```

jest wykonywane jako

```csharp
x = x >> y
```

z tą różnicą, że `x` jest obliczone tylko raz. [Operator >>](right-shift-operator.md) przesuwa `x` w prawo o liczbę bitów określoną przez `y`.

Operatora [ nie można przeciążyć bezpośrednio, ale ](right-shift-operator.md)operator >>[ (zobacz ](../keywords/operator.md)operator) może zostać przeciążony w typach danych zdefiniowanych przez użytkownika.

## <a name="example"></a>Przykład

[!code-csharp[csRefOperators#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#11)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [C#Operatory](index.md)