---
title: Shadows
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: 7aed6bec21bd484cca019b061bd5915de13a9eb8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402710"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)

Określa, że zadeklarowany element programistyczny ponownie deklaruje i ukrywa element o identycznej nazwie, lub zestaw przeciążonych elementów w klasie bazowej.

## <a name="remarks"></a>Uwagi

Głównym celem przesłaniania (który jest również znany jako *ukrywanie według nazwy*) jest zachowanie definicji elementów członkowskich klasy. Klasa bazowa może ulec zmianie, która tworzy element o takiej samej nazwie jak już zdefiniowany. W takim przypadku `Shadows` modyfikator wymusza odwołania za pomocą klasy, aby można było rozpoznać element członkowski zdefiniowany przez użytkownika, a nie do nowego elementu klasy bazowej.

Zarówno przesłanianie, jak i przesłonięcie przedefiniują Dziedziczony element, ale istnieją znaczne różnice między tymi dwoma podejściami. Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).

## <a name="rules"></a>Reguły

- **Kontekst deklaracji.** Można używać `Shadows` tylko na poziomie klasy. Oznacza to, że kontekst deklaracji dla `Shadows` elementu musi być klasą i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, modułem, strukturą ani procedurą.

  Można zadeklarować tylko jeden element przesłaniania w jednej instrukcji deklaracji.

- **Połączone modyfikatory.** Nie można określić `Shadows` razem z `Overloads` , `Overrides` , lub `Static` w tej samej deklaracji.

- **Typy elementów.** Można obsłużyć dowolny rodzaj zadeklarowanego elementu z dowolnego innego rodzaju. Jeśli właściwość lub procedura została przesłonięta przez inną właściwość lub procedurę, parametry i zwracany typ nie muszą pasować do tych w właściwości lub procedurze klasy bazowej.

- **Korzystając.** Element shadowd w klasie bazowej jest zwykle niedostępny z poziomu klasy pochodnej, która go zasłania. Jednak obowiązują następujące zagadnienia.

  - Jeśli element przesłaniania nie jest dostępny z kodu odwołującego się do niego, odwołanie jest rozpoznawane jako element w tle. Na przykład, jeśli `Private` element zasłania element klasy bazowej, kod, który nie ma uprawnień dostępu do `Private` elementu uzyskuje dostęp do elementu klasy bazowej.

  - W przypadku obserwowania elementu można nadal uzyskać dostęp do elementu w tle za pomocą obiektu zadeklarowanego z typem klasy bazowej. Możesz również uzyskać do niego dostęp za poorednictwem `MyBase` .

`Shadows`Modyfikator może być używany w tych kontekstach:

- [Class, instrukcja](../statements/class-statement.md)

- [Const, instrukcja](../statements/const-statement.md)

- [Declare — Instrukcja](../statements/declare-statement.md)

- [Delegate — Instrukcja](../statements/delegate-statement.md)

- [Dim, instrukcja](../statements/dim-statement.md)

- [Enum, instrukcja](../statements/enum-statement.md)

- [Event — Instrukcja](../statements/event-statement.md)

- [Function, instrukcja](../statements/function-statement.md)

- [Interface, instrukcja](../statements/interface-statement.md)

- [Property — Instrukcja](../statements/property-statement.md)

- [Structure — Instrukcja](../statements/structure-statement.md)

- [Sub, instrukcja](../statements/sub-statement.md)

## <a name="see-also"></a>Zobacz też

- [Shared](shared.md)
- [Ruchom](static.md)
- [Użytek](private.md)
- [Me, My, MyBase i MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Podstawowe informacje o dziedziczeniu](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](mustoverride.md)
- [NotOverridable](notoverridable.md)
- [Przeciążenia](overloads.md)
- [Overridable](overridable.md)
- [Przesłonięcia](overrides.md)
- [Przesłanianie w Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
