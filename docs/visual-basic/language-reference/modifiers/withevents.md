---
title: WithEvents
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 2309c675b50a2025d73841a47fe8e30e7cecd522
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350743"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Określa, że co najmniej jedna zadeklarowana zmienna składowej odnosi się do wystąpienia klasy, która może zgłaszać zdarzenia.

## <a name="remarks"></a>Uwagi

Gdy zmienna jest definiowana przy użyciu `WithEvents`, można deklaratywnie określić, że metoda obsługuje zdarzenia zmiennej przy użyciu słowa kluczowego `Handles`.

`WithEvents` można używać tylko na poziomie klasy lub modułu. Oznacza to, że kontekst deklaracji dla zmiennej `WithEvents` musi być klasą lub modułem i nie może być plikiem źródłowym, przestrzenią nazw, strukturą ani procedurą.

Nie można użyć `WithEvents` w składowej struktury.

Można zadeklarować tylko pojedyncze zmienne — nie tablice — z `WithEvents`.

## <a name="rules"></a>Reguły

**Typy elementów.** Należy zadeklarować zmienne `WithEvents` jako zmienne obiektów, aby mogły akceptować wystąpienia klas. Nie można jednak zadeklarować ich jako `Object`. Należy zadeklarować je jako konkretną klasę, która może zgłaszać zdarzenia.

Modyfikator `WithEvents` może być używany w tym kontekście: [Dim — Instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)

## <a name="example"></a>Przykład

```vb
Dim WithEvents app As Application
```

## <a name="see-also"></a>Zobacz także

- [Realizuj](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
- [Zdarzenia](../../../visual-basic/programming-guide/language-features/events/index.md)
