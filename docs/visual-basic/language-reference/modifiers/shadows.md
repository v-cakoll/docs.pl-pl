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
ms.openlocfilehash: e9a423fa69ad1dcd8c1d4a5b7085e5b5da548f93
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351263"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)

Określa, że zadeklarowany element programistyczny ponownie deklaruje i ukrywa element o identycznej nazwie, lub zestaw przeciążonych elementów w klasie bazowej.

## <a name="remarks"></a>Uwagi

Głównym celem przesłaniania (który jest również znany jako *ukrywanie według nazwy*) jest zachowanie definicji elementów członkowskich klasy. Klasa bazowa może ulec zmianie, która tworzy element o takiej samej nazwie jak już zdefiniowany. Jeśli tak się stanie, modyfikator `Shadows` wymusza odwołania za pomocą klasy, aby można go było rozpoznać do zdefiniowanego elementu członkowskiego, a nie do nowego elementu klasy bazowej.

Zarówno przesłanianie, jak i przesłonięcie przedefiniują Dziedziczony element, ale istnieją znaczne różnice między tymi dwoma podejściami. Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).

## <a name="rules"></a>Reguły

- **Kontekst deklaracji.** `Shadows` można użyć tylko na poziomie klasy. Oznacza to, że kontekst deklaracji dla elementu `Shadows` musi być klasą i nie może być plikiem źródłowym, przestrzenią nazw, interfejsem, strukturą ani procedurą.

  Można zadeklarować tylko jeden element przesłaniania w jednej instrukcji deklaracji.

- **Połączone modyfikatory.** Nie można określić `Shadows` razem z `Overloads`, `Overrides`lub `Static` w tej samej deklaracji.

- **Typy elementów.** Można obsłużyć dowolny rodzaj zadeklarowanego elementu z dowolnego innego rodzaju. Jeśli właściwość lub procedura została przesłonięta przez inną właściwość lub procedurę, parametry i zwracany typ nie muszą pasować do tych w właściwości lub procedurze klasy bazowej.

- **Korzystając.** Element shadowd w klasie bazowej jest zwykle niedostępny z poziomu klasy pochodnej, która go zasłania. Jednak obowiązują następujące zagadnienia.

  - Jeśli element przesłaniania nie jest dostępny z kodu odwołującego się do niego, odwołanie jest rozpoznawane jako element w tle. Na przykład, jeśli element `Private` zasłania element klasy bazowej, kod, który nie ma uprawnień dostępu do elementu `Private`, zamiast tego uzyskuje dostęp do elementu klasy bazowej.

  - W przypadku obserwowania elementu można nadal uzyskać dostęp do elementu w tle za pomocą obiektu zadeklarowanego z typem klasy bazowej. Możesz również uzyskać do niego dostęp za poorednictwem `MyBase`.

Modyfikator `Shadows` może być używany w tych kontekstach:

- [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)

- [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)

- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)

- [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)

- [Enum, instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)

- [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)

- [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)

- [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)

- [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)

- [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)

- [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Zobacz także

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Me, My, MyBase i MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Obserwowanie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
