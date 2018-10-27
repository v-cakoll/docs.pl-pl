---
title: Operator %= (odwołanie w C#)
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: ab3a6a8d5cbfeb4d527ca1f9c233ddfaba3d35ff
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188719"
---
# <a name="-operator-c-reference"></a>Operator %= (odwołanie w C#)

Operator przypisania reszty.

Usługi za pomocą wyrażenia `%=` operatora, takich jak  

```csharp
x %= y
```  

odpowiada wyrażeniu  

```csharp
x = x % y
```  

z tą różnicą, że `x` jest obliczany tylko raz.
  
[Operator reszty](remainder-operator.md) `%` oblicza pozostałą po dzielenia swoich argumentów. Jest ona obsługiwana przez wszystkie typy liczbowe.

Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [operator reszty](remainder-operator.md) `%`, operator przypisania reszty `%=` niejawnie jest przeciążony.
  
W poniższym przykładzie pokazano użycie `%=` operator:

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
