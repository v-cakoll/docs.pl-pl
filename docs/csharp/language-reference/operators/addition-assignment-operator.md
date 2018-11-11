---
title: += — Operator (odwołanie w C#)
ms.date: 10/29/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: ac9330e283cb58ae4e0ee7b644aa2c22bdf64c46
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2018
ms.locfileid: "50192034"
---
# <a name="-operator-c-reference"></a>+= — Operator (odwołanie w C#)

Operator przypisania dodawania.

Usługi za pomocą wyrażenia `+=` operatora, takich jak

```csharp
x += y
```

odpowiada wyrażeniu

```csharp
x = x + y
```

z tą różnicą, że `x` jest obliczany tylko raz.
  
Dla typów liczbowych [operator dodawania](addition-operator.md) `+` oblicza sumę argumentów. Jeśli jeden lub obydwa operandy typu [ciąg](../keywords/string.md), łączy on ciągów reprezentujących swoich argumentów. Dla typów delegowanych `+` operator zwraca nowe wystąpienie delegata, który jest kombinacja argumentów.

Możesz także użyć `+=` operatora, aby określić metodę programu obsługi zdarzeń podczas subskrybowania [zdarzeń](../keywords/event.md). Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

W poniższym przykładzie pokazano użycie `+=` operator:

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]

## <a name="operator-overloadability"></a>Overloadability — operator

Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [operator dodawania](addition-operator.md) `+`, operator przypisania dodawania `+=` niejawnie jest przeciążony. Typ zdefiniowany przez użytkownika nie można jawnie przeciążyć operator przypisania dodawania.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [przydział złożony](~/_csharplang/spec/expressions.md#compound-assignment) i [przypisanie zdarzenia](~/_csharplang/spec/expressions.md#event-assignment) sekcje [ C# specyfikacji języka](../language-specification/index.md).
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [Zdarzenia](../../programming-guide/events/index.md)
- [Delegaty](../../programming-guide/delegates/index.md)
