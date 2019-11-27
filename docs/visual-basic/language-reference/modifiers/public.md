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
ms.openlocfilehash: 35bf1a65e0b8f24a1263adc480719c69b95dff9b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351292"
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
Określa, że co najmniej jeden zadeklarowany element programistyczny nie ma ograniczeń dostępu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli publikujesz składnik lub zestaw składników, takich jak Biblioteka klas, zazwyczaj chcesz, aby elementy programistyczne były dostępne dla dowolnego kodu, który współdziała z Twoim zestawem. Aby przyznać takie nieograniczone dostęp do elementu, można zadeklarować go za pomocą `Public`.  
  
 Dostęp publiczny jest normalnym poziomem dla elementu programistycznego, gdy nie trzeba ograniczać dostępu do niego. Należy zauważyć, że poziom dostępu elementu zadeklarowanego w interfejsie, module, klasie lub strukturze domyślnie `Public`, jeśli nie zostanie zadeklarowany w inny sposób.  
  
## <a name="rules"></a>Reguły  
  
- **Kontekst deklaracji.** `Public` można używać tylko na poziomie modułu, interfejsu lub przestrzeni nazw. Oznacza to, że kontekst deklaracji dla elementu `Public` musi być plikiem źródłowym, przestrzenią nazw, interfejsem, modułem, klasą lub strukturą i nie może być procedurą.  
  
## <a name="behavior"></a>Zachowanie  
  
- **Poziom dostępu.** Cały kod, który może uzyskać dostęp do modułu, klasy lub struktury, może uzyskać dostęp do swoich `Public`ych elementów.  
  
- **Dostęp domyślny.** Zmienne lokalne wewnątrz procedury domyślnie mają dostęp publiczny i nie można używać żadnych modyfikatorów dostępu.  
  
- **Modyfikatory dostępu.** Słowa kluczowe określające poziom dostępu są nazywane *modyfikatorami dostępu*. Aby porównać Modyfikatory dostępu, zobacz [poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 Modyfikator `Public` może być używany w tych kontekstach:  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
