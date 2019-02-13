---
title: << = — operator - C# odwołania
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: d2105fbee4ddfe1b2cb3325d82b0f2f8c5559297
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219454"
---
# <a name="-operator-c-reference"></a>\<\<= — operator (C# odwołania)

Operator przypisania przesunięcia w lewo.

Usługi za pomocą wyrażenia `<<=` operatora, takich jak

```csharp
x <<= y
```

odpowiada wyrażeniu

```csharp
x = x << y
```

z tą różnicą, że `x` jest obliczany tylko raz.

[ `<<` Operator](left-shift-operator.md) pierwszy argument operacji lewo o liczbę bitów definicją drugim argumentem operacji przesunięcia.

W poniższym przykładzie pokazano użycie `<<=` operator:

[!code-csharp-interactive[left shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftAssignment)]

## <a name="operator-overloadability"></a>Overloadability — operator

Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [ `<<` operator](left-shift-operator.md), operator przypisania przesunięcia w lewo `<<=` niejawnie jest przeciążony. Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania przesunięcia w lewo.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [przydział złożony](~/_csharplang/spec/expressions.md#compound-assignment) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
