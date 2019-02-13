---
title: '>>= — operator - C# odwołania'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 51914bb5e9ebffd5d868528b5a8d3072a956cea6
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220916"
---
# <a name="-operator-c-reference"></a>>> = — operator (C# odwołania)

Operator przypisania przesunięcia w prawo.

Usługi za pomocą wyrażenia `>>=` operatora, takich jak

```csharp
x >>= y
```

odpowiada wyrażeniu

```csharp
x = x >> y
```

z tą różnicą, że `x` jest obliczany tylko raz.

[ `>>` Operator](right-shift-operator.md) bezpośrednio przenosi swojego pierwszego operandu przez liczbę bitów definicją drugim argumentem.

W poniższym przykładzie pokazano użycie `>>=` operator:

[!code-csharp-interactive[right shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftAssignment)]

## <a name="operator-overloadability"></a>Overloadability — operator

Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [ `>>` operator](right-shift-operator.md), operator przypisania przesunięcia w prawo `>>=` niejawnie jest przeciążony. Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania przesunięcia w prawo.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [przydział złożony](~/_csharplang/spec/expressions.md#compound-assignment) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [C#Operatory](index.md)