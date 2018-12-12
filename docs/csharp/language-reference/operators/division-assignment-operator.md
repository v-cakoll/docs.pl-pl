---
title: / = — Operator - C# odwołania
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: ed4dd6c0c944b77543aae4de8d51534b4df4f4ef
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286523"
---
# <a name="-operator-c-reference"></a>Operator /= (odwołanie w C#)

Operator przypisania dzielenia.

Usługi za pomocą wyrażenia `/=` operatora, takich jak

```csharp
x /= y
```

odpowiada wyrażeniu

```csharp
x = x / y
```

z tą różnicą, że `x` jest obliczany tylko raz.

[Operator dzielenia](division-operator.md) `/` dzieli pierwszy argument operacji za drugim argumentem. Jest ona obsługiwana przez wszystkie typy liczbowe.

W poniższym przykładzie pokazano użycie `/=` operator:

[!code-csharp-interactive[divide and assign](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#DivisionAssignment)]

## <a name="operator-overloadability"></a>Overloadability — operator

Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [operator dzielenia](division-operator.md) `/`, operator przypisania dzielenia `/=` niejawnie jest przeciążony. Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania dzielenia.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [przydział złożony](~/_csharplang/spec/expressions.md#compound-assignment) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
