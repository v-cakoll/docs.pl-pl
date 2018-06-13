---
title: Private (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: 40b64b8d2b6306d458b7a9cc657c5b7dc4270eb2
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234558"
---
# <a name="private-visual-basic"></a>Private (Visual Basic)
Określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie ich kontekście deklaracji, łącznie z wewnątrz żadnych typów zawartych w niej.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli elementu programistycznego reprezentuje własnościowych funkcji lub zawiera dane poufne, mają zwykle jako ściśle ograniczyć do niego dostęp. Ograniczenie maksymalnej można osiągnąć, zezwalając tylko modułu, klasy lub struktury, definiujący go do niego dostęp. Aby ograniczyć dostęp do elementu w ten sposób, mogą zadeklarować za pomocą `Private`.  

> [!NOTE]
> Można również użyć [prywatne chronione](private-protected.md) modyfikator dostępu, co sprawia, że element członkowski jest dostępny z tej klasy i z klas pochodnych znajduje się w jego zawierający zestaw.

## <a name="rules"></a>Reguły  

-   **Kontekst deklaracji.** Można użyć `Private` tylko na poziomie modułu. Oznacza to, że w kontekście deklaracji `Private` elementu musi być modułu, klasy lub struktury i nie może być plik źródłowy, przestrzeń nazw, interfejsem lub procedury.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Poziom dostępu.** Cały kod w kontekście deklaracji mogą uzyskiwać dostęp do jego `Private` elementów. W tym kodu w ramach ograniczonego typu, na przykład klasa zagnieżdżona lub wyrażenie przypisania w wyliczeniu. Brak kodu poza kontekstem deklaracji mogą uzyskiwać dostęp do jego `Private` elementów.  
  
-   **Modyfikatory dostępu.** Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorów dostępu*. Porównanie modyfikatorów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Private` Modyfikatora można używać w tych sytuacjach:  
  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum, instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Prywatne chronione](./private-protected.md)   
 [Protected Friend](./protected-friend.md)[dostępu poziomy w języku Visual Basic    ](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
