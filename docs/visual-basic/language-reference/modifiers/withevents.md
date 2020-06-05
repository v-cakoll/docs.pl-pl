---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 48261e27de302c1809c9725e6e2fc0705a803930
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386779"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Określa, że co najmniej jedna zadeklarowana zmienna składowej odnosi się do wystąpienia klasy, która może zgłaszać zdarzenia.

## <a name="remarks"></a>Uwagi

Gdy zmienna jest zdefiniowana przy użyciu `WithEvents` , można deklaratywnie określić, że metoda obsługuje zdarzenia zmiennej przy użyciu `Handles` słowa kluczowego.

Można używać `WithEvents` tylko na poziomie klasy lub modułu. Oznacza to, że kontekst deklaracji dla `WithEvents` zmiennej musi być klasą lub modułem i nie może być plikiem źródłowym, przestrzenią nazw, strukturą ani procedurą.

Nie można użyć `WithEvents` w składowej struktury.

Można zadeklarować tylko pojedyncze zmienne — nie tablice — za pomocą `WithEvents` .

## <a name="rules"></a>Reguły

**Typy elementów.** Należy zadeklarować `WithEvents` zmienne jako zmienne obiektów, aby mogły akceptować wystąpienia klasy. Nie można jednak zadeklarować ich jako `Object` . Należy zadeklarować je jako konkretną klasę, która może zgłaszać zdarzenia.

`WithEvents`Modyfikator może być używany w tym kontekście: [Dim — Instrukcja](../statements/dim-statement.md)

## <a name="example"></a>Przykład

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>Zobacz też

- [Handles](../statements/handles-clause.md)
- [Słowa kluczowe](../keywords/index.md)
- [Zdarzenia](../../programming-guide/language-features/events/index.md)
