---
title: += — Operator (odwołanie w C#)
ms.date: 10/22/2018
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
- event subscription [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: ee335e3e2e7d352d4e26b802bad2b08a05c666ab
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
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

Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [operator dodawania](addition-operator.md) `+`, operator przypisania dodawania `+=` niejawnie jest przeciążony.

Możesz także użyć `+=` operatora, aby określić metodę programu obsługi zdarzeń podczas subskrybowania [zdarzeń](../keywords/event.md). Aby uzyskać więcej informacji, zobacz [porady: subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

W poniższym przykładzie pokazano użycie `+=` operator:

[!code-csharp-interactive[+= examples](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddAndAssign)]
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [Zdarzenia](../../programming-guide/events/index.md)
- [Delegaty](../../programming-guide/delegates/index.md)
