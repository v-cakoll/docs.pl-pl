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
ms.openlocfilehash: 0b8c31facc3605ff5a77aecf7b11456b33fbab72
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647743"
---
# <a name="public-visual-basic"></a>Public (Visual Basic)
Określa, że co najmniej jeden zadeklarowany element programistyczny nie ma ograniczeń dostępu.  
  
## <a name="remarks"></a>Uwagi  
 W przypadku publikowania składnika lub zestaw składników, takich jak biblioteki klas, ma zwykle programistyczny dostępu przez każdy kod, który współdziała z zestawu. Przyznaje taki dostęp bez ograniczeń dla elementu, można zadeklarować za pomocą `Public`.  
  
 Dostęp publiczny jest normalnego poziomu dla elementu programistycznego, gdy jest konieczne ograniczanie dostępu do niego. Należy pamiętać, poziom dostępu elementu jest zadeklarowany w obrębie interfejsu, modułu, klasy lub struktury wartość domyślna to `Public` nie zadeklarowana w inny sposób.  
  
## <a name="rules"></a>reguły  
  
- **Kontekst deklaracji.** Możesz użyć `Public` tylko na poziomie modułu, interfejsu lub przestrzeni nazw. Oznacza to, że kontekst deklaracji `Public` elementu musi być w pliku źródłowym, przestrzeń nazw, interfejsu, modułu, klasy lub struktury, a nie może być procedurą.  
  
## <a name="behavior"></a>Zachowanie  
  
- **Poziom dostępu.** Cały kod, który mają dostęp do modułu, klasy lub struktury mogą uzyskiwać dostęp do jego `Public` elementów.  
  
- **Dostęp do domyślnej.** Zmiennych lokalnych wewnątrz domyślną procedurę do publicznego dostępu, a nie można użyć dowolnego modyfikatory dostępu na nich.  
  
- **Modyfikatory dostępu.** Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorach dostępu*. Dla porównania modyfikatory dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Public` Modyfikator mogą być używane w tych kontekstach:  
  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const, instrukcja](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate, instrukcja](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim, instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum, instrukcja](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event, instrukcja](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function, instrukcja](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Instrukcja Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Instrukcja Module](../../../visual-basic/language-reference/statements/module-statement.md)  
  
 [Operator, instrukcja](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Instrukcja Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure, instrukcja](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub, instrukcja](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Zobacz także

- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
