---
title: '&amp;= — Operator (odwołanie w C#)'
ms.date: 10/29/2018
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: 8ce27c999cf21a9059ba23ee3c86b8fa024c7341
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "50980612"
---
# <a name="amp-operator-c-reference"></a>&amp;= — Operator (odwołanie w C#)

Operator przypisania AND.

Usługi za pomocą wyrażenia `&=` operatora, takich jak

```csharp
x &= y
```

odpowiada wyrażeniu

```csharp
x = x & y
```

z tą różnicą, że `x` jest obliczany tylko raz.

Dla liczby całkowitej, wykonują się dużo [ `&` operator](and-operator.md) oblicza iloczynu bitowego AND logiczne z argumentów; w przypadku [bool](../keywords/bool.md) operandów, oblicza logicznego i jego operandu.

W poniższym przykładzie pokazano użycie `&=` operator:

[!code-csharp-interactive[AND assignment example](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#AndAssignmentExample)]

## <a name="operator-overloadability"></a>Overloadability — operator

Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [ `&` operator](and-operator.md), operator przypisania AND `&=` niejawnie jest przeciążony. Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania AND.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [przydział złożony](~/_csharplang/spec/expressions.md#compound-assignment) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
