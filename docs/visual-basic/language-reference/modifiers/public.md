---
title: Public (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: a5e9161132ba6d571daa30ce82e1bfb1dd2b064f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
Określa, że co najmniej jeden zadeklarowany element programistyczny nie ma ograniczeń dostępu.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku publikowania składnika lub zestaw składników, takich jak biblioteki klas, zazwyczaj mają programistyczny dostępu przez dowolny kod, który współdziała z tym zestawem. Przyznanie takich nieograniczonego dostępu w elemencie, mogą zadeklarować go przy użyciu `Public`.  
  
 Dostępu publicznego jest normalnego poziomu dla elementu programistycznego, gdy jest konieczne ograniczenie dostępu do niego. Należy pamiętać, że poziom dostępu do elementu zadeklarowany w interfejsie, modułu, klasy lub struktury domyślnie `Public` nie zadeklarowana w inny sposób.  
  
## <a name="rules"></a>Reguły  
  
-   **Kontekst deklaracji.** Można użyć `Public` tylko na poziomie modułu, interfejsem lub przestrzeni nazw. Oznacza to, że w kontekście deklaracji `Public` elementu musi być pliku źródłowego, przestrzeń nazw, interfejsu, modułu, klasy lub struktury i nie może być procedury.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Poziom dostępu.** Cały kod, który można uzyskać dostępu do modułu, klasy lub struktury mogą uzyskiwać dostęp do jego `Public` elementów.  
  
-   **Dostęp do domyślnej.** Zmiennych lokalnych wewnątrz procedury domyślnie dostępu publicznego, a nie można użyć dowolnego modyfikatorów dostępu na nich.  
  
-   **Modyfikatory dostępu.** Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorów dostępu*. Porównanie modyfikatorów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Public` Modyfikatora można używać w tych sytuacjach:  
  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum, instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Module, instrukcja](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property, instrukcja](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Prywatne chronione](private-protected.md)   
 [Friend chronionych](protected-friend.md)   
 [Poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
