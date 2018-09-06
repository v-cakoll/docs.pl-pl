---
title: Operator %= (odwołanie w C#)
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: c475517666bdadaa457dbb4188808b3a96fcdf0e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43880204"
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
  
[Operator reszty](remainder-operator.md) `%` jest obsługiwany przez wszystkie typy liczbowe i oblicza pozostałą po dzielenia swoich argumentów.

Jeśli typ zdefiniowany przez użytkownika [przeciążenia](../keywords/operator.md) [operator reszty](remainder-operator.md) `%`, operator przypisania reszty `%=` niejawnie jest przeciążony.
  
W poniższym przykładzie pokazano użycie `%=` operator:

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
