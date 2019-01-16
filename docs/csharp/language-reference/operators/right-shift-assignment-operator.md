---
title: '&gt;&gt;= — operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 02a9559a5c4086eeed09094c15c3620366ffad8c
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333695"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;= — operator (C# odwołania)

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