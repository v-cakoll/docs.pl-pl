---
title: Public
ms.date: 07/20/2015
f1_keywords:
- vb.Public
helpviewer_keywords:
- Public keyword [Visual Basic]
- Public keyword [Visual Basic], syntax
- Public access modifier
ms.assetid: 284c9e1b-ed23-499b-9bc9-ad87c11485a5
ms.openlocfilehash: 35332e50227cdef6386362df17c10b5b2cdaa689
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415352"
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
Określa, że co najmniej jeden zadeklarowany element programistyczny nie ma ograniczeń dostępu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli publikujesz składnik lub zestaw składników, takich jak Biblioteka klas, zazwyczaj chcesz, aby elementy programistyczne były dostępne dla dowolnego kodu, który współdziała z Twoim zestawem. Aby przyznać takie nieograniczone dostęp do elementu, można zadeklarować go za pomocą `Public` .  
  
 Dostęp publiczny jest normalnym poziomem dla elementu programistycznego, gdy nie trzeba ograniczać dostępu do niego. Należy zauważyć, że poziom dostępu elementu zadeklarowanego w interfejsie, module, klasie lub strukturze domyślnie nie jest `Public` deklarowany w inny sposób.  
  
## <a name="rules"></a>Reguły  
  
- **Kontekst deklaracji.** Można używać `Public` tylko na poziomie modułu, interfejsu lub przestrzeni nazw. Oznacza to, że kontekst deklaracji dla `Public` elementu musi być plikiem źródłowym, przestrzenią nazw, interfejsem, modułem, klasą lub strukturą i nie może być procedurą.  
  
## <a name="behavior"></a>Zachowanie  
  
- **Poziom dostępu.** Cały kod, który może uzyskać dostęp do modułu, klasy lub struktury, może uzyskać dostęp do jego `Public` elementów.  
  
- **Dostęp domyślny.** Zmienne lokalne wewnątrz procedury domyślnie mają dostęp publiczny i nie można używać żadnych modyfikatorów dostępu.  
  
- **Modyfikatory dostępu.** Słowa kluczowe określające poziom dostępu są nazywane *modyfikatorami dostępu*. Aby porównać Modyfikatory dostępu, zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Public`Modyfikator może być używany w tych kontekstach:  
  
 [Class, instrukcja](../statements/class-statement.md)  
  
 [Const, instrukcja](../statements/const-statement.md)  
  
 [Declare — Instrukcja](../statements/declare-statement.md)  
  
 [Delegate — Instrukcja](../statements/delegate-statement.md)  
  
 [Dim, instrukcja](../statements/dim-statement.md)  
  
 [Enum, instrukcja](../statements/enum-statement.md)  
  
 [Event — Instrukcja](../statements/event-statement.md)  
  
 [Function, instrukcja](../statements/function-statement.md)  
  
 [Interface, instrukcja](../statements/interface-statement.md)  
  
 [Module — Instrukcja](../statements/module-statement.md)  
  
 [Operator — Instrukcja](../statements/operator-statement.md)  
  
 [Property — Instrukcja](../statements/property-statement.md)  
  
 [Structure — Instrukcja](../statements/structure-statement.md)  
  
 [Sub, instrukcja](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz też

- [Chronione](protected.md)
- [Osoby](friend.md)
- [Użytek](private.md)
- [Prywatne chronione](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../programming-guide/language-features/procedures/index.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../programming-guide/language-features/objects-and-classes/index.md)
