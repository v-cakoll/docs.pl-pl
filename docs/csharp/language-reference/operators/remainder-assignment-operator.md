---
title: '% = — Operator - C# odwołania'
ms.custom: seodec18
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: d0732f9578b64c894ecc1d3bb15cee11a8d5b6a3
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245564"
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
