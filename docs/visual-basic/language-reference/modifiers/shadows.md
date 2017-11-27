---
title: Shadows (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb767c372cc05d61d569227af8eef0dc3c67489b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="shadows-visual-basic"></a>Shadows (Visual Basic)
Określa, że zadeklarowany element programistyczny ponownie deklaruje i ukrywa element o identycznej nazwie lub zbiór elementów przeciążona w klasie podstawowej.  
  
## <a name="remarks"></a>Uwagi  
 Głównym celem przesłanianie (który jest również nazywany *ukrywanie według nazwy*) jest zachowanie definicji członkowie klasy. Klasa podstawowa mogą być zmiany, która tworzy element o takiej samej nazwie jako jeden, który został już zdefiniowany. W takim przypadku `Shadows` wymusza modyfikator odwołuje się do klasy mają zostać rozwiązane do elementu członkowskiego zdefiniowane, a nie nowy element klasy podstawowej.  
  
 Zarówno przesłanianiem i zastępowaniem ponownego zdefiniowania odziedziczonego elementu, ale są istotne różnice między dwa podejścia. Aby uzyskać więcej informacji, zobacz [przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
## <a name="rules"></a>Reguły  
  
-   **Kontekst deklaracji.** Można użyć `Shadows` tylko na poziomie klasy. Oznacza to, że w kontekście deklaracji `Shadows` elementu musi być klasą i nie może być plik źródłowy, przestrzeni nazw, interfejsu, modułu, struktury lub procedury.  
  
     Można zadeklarować tylko jeden element przesłaniania w instrukcji jednej deklaracji.  
  
-   **Łączna modyfikatorów.** Nie można określić `Shadows` razem z `Overloads`, `Overrides`, lub `Static` w tej samej deklaracji.  
  
-   **Typy elementów.** Można obserwować dowolny rodzaj elementu zadeklarowany z innego typu. Jeśli cień właściwość lub procedura z inną właściwość lub procedura parametry oraz zwracany typ nie musi odpowiadać w klasie podstawowej właściwość lub procedura.  
  
-   **Uzyskiwanie dostępu do.** Element zasłonięty w klasie podstawowej zwykle z są niedostępne w klasie pochodnej, któremu go. Jednak uwzględnić następujące kwestie.  
  
    -   Jeśli element przesłaniania nie jest dostępny z kod odwołujący się do niego, odwołanie jest rozwiązany do elementu zasłonięty. Na przykład jeśli `Private` element zasłania element klasy podstawowej, kod, który nie ma uprawnień dostępu do `Private` element uzyskuje dostęp do elementu klasy podstawowej zamiast tego.  
  
    -   Jeśli w tle elementu można nadal dostęp do elementu zasłonięty, za pomocą obiektu zadeklarowane z typem klasy podstawowej. Możesz również do niego dostęp za pośrednictwem `MyBase`.  
  
 `Shadows` Modyfikatora można używać w tych sytuacjach:  
  
 [Class — instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const — instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [DECLARE — instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate — instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum — instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event — instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function — instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface — instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property — instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure — instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub — instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Udostępnione](../../../visual-basic/language-reference/modifiers/shared.md)  
 [Statyczne](../../../visual-basic/language-reference/modifiers/static.md)  
 [Prywatne](../../../visual-basic/language-reference/modifiers/private.md)  
 [Me, My, MyBase i MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Podstawowe informacje o dziedziczeniu](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Przeciążenia](../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Możliwym do zastąpienia](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Zastąpienia](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Przesłanianie w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
