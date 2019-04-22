---
title: Shadows (Visual Basic)
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
ms.openlocfilehash: c314db90a1a0f89613e20897387bdec8ec534837
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834143"
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)
Określa, że zadeklarowany element programistyczny ponownie deklaruje i ukrywa element o identycznej nazwie, lub zestaw przeciążonych elementów w klasie bazowej.  
  
## <a name="remarks"></a>Uwagi  
 Głównym celem cieniowania (który jest również nazywany *ukrycie przez nazwę*) jest zachowanie definicji usługi składowych klasy. Klasy bazowej może przechodzić zmianę, która tworzy element o takiej samej nazwie jako jeden, który został już zdefiniowany. W takim przypadku `Shadows` wymusza modyfikator odwołuje się do swojej klasy, które mają zostać rozwiązane do elementu członkowskiego zdefiniowane, zamiast na nowy element klasy bazowej.  
  
 Zarówno przesłanianiem i zastępowaniem przedefiniować dziedziczonego elementu, ale istnieją znaczne różnice między dwa podejścia. Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## <a name="rules"></a>reguły  
  
-   **Kontekst deklaracji.** Możesz użyć `Shadows` tylko na poziomie klasy. Oznacza to, że kontekst deklaracji `Shadows` element musi być klasą i nie może być plik źródłowy, przestrzeń nazw, interfejsu, moduł, struktura lub procedury.  
  
     Można zadeklarować tylko jeden element przesłaniania w instrukcji jednej deklaracji.  
  
-   **Modyfikatory połączone.** Nie można określić `Shadows` wraz z `Overloads`, `Overrides`, lub `Static` w tej samej deklaracji.  
  
-   **Typy elementów.** Można w tle dowolnego typu element zadeklarowany za pomocą dowolnego typu. Jeśli użytkownik w tle, właściwość lub procedura z inną właściwość lub procedura, parametry oraz zwracany typ musi odpowiadać znajdującymi się na właściwości klasy bazowej lub procedury.  
  
-   **Uzyskiwanie dostępu do.** Element zasłonięte w klasie bazowej niedostępności zwykle od w klasie pochodnej, która przesłania go. Jednak mają zastosowanie następujące kwestie.  
  
    -   Jeśli element przesłaniania nie jest dostępne z kodu, odwołując się do niego, odwołanie zostaje rozpoznany tekst z cieniem elementu. Na przykład jeśli `Private` element zasłania elementu klasy podstawowej, kod, który nie ma uprawnień dostępu do `Private` element uzyskuje dostęp do elementu klasy podstawowej zamiast tego.  
  
    -   Jeśli w tle elementu możesz uzyskiwać dostęp element zasłonięte przez obiekt, który zadeklarowane z typem klasy bazowej. Możesz również do niego dostęp za pośrednictwem `MyBase`.  
  
 `Shadows` Modyfikator mogą być używane w tych kontekstach:  
  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum, instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrukcja Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
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
- [Przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
