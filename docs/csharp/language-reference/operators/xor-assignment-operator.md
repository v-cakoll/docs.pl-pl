---
title: ^ = — operator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: 12189d6469a9716d3b7ebcffef23423a75692d1a
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333554"
---
# <a name="-operator-c-reference"></a>^ = — operator (C# odwołania)

Operator przypisania OR wyłączne.

## <a name="remarks"></a>Uwagi

Wyrażenie formularza

```csharp
x ^= y
```

jest wykonywane jako

```csharp
x = x ^ y
```

z tą różnicą, że `x` jest obliczany tylko raz. [^ — Operator](xor-operator.md) wykonuje OR wyłączne operacja bitowa na operandach typu całkowitego i logiczne OR wyłączne na [bool](../keywords/bool.md) argumentów operacji.

^ = — Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [^ — operator](xor-operator.md) (zobacz [operator](../keywords/operator.md)).

## <a name="example"></a>Przykład

[!code-csharp[csRefOperators#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#23)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [C#Operatory](index.md)