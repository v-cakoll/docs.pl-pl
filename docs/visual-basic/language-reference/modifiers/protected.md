---
title: Protected (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: 86758c68f0f3bfe214a695f656d3924eadd27e31
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642688"
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)
Modyfikator dostępu elementu członkowskiego, który określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie swojej klasy lub z klasy pochodnej.  
  
## <a name="remarks"></a>Uwagi  
 Czasami elementu programistycznego, zadeklarowana w klasie zawiera dane poufne lub ograniczony kod, a użytkownik chce ograniczyć dostęp do elementu. Jednakże jeśli klasa jest dziedziczone, które hierarchii klas pochodnych, może być konieczne dla tych klas pochodnych, uzyskać dostęp do danych lub kod. W takim przypadku należy elementu, który ma być dostępne zarówno z klasy bazowej i wszystkie klasy pochodne. Aby ograniczyć dostęp do elementu w ten sposób, można zadeklarować za pomocą `Protected`.  

> [!NOTE]
> `Protected` Modyfikator dostępu można łączyć z innymi modyfikatorów:
> - [Protected Friend](protected-friend.md) modyfikator sprawia, że element członkowski klasy jest dostępny w obrębie tej klasy z klas pochodnych i z tego samego zestawu, w którym klasa jest zdefiniowana. 
> - [Private Protected](private-protected.md) modyfikator sprawia, że element członkowski klasy dostępne przez typy pochodne, ale tylko w ramach własnego zestawu zawierającego.
  
## <a name="rules"></a>reguły  
  
- **Kontekst deklaracji.** Możesz użyć `Protected` tylko na poziomie klasy. Oznacza to, że kontekst deklaracji `Protected` element musi być klasą i nie może być plik źródłowy, przestrzeń nazw, interfejsu, moduł, struktura lub procedury.  

## <a name="behavior"></a>Zachowanie  
  
- **Poziom dostępu.** Cały kod w klasie mogą uzyskać dostęp do jego elementów. Kod w dowolną klasę pochodzącą z klasy bazowej może uzyskać dostęp do wszystkich `Protected` elementów klasy bazowej. Ta zasada obowiązuje dla wszystkich pokoleń pochodnym. Oznacza to, że dostęp do klasy `Protected` elementy klasę bazową klasy bazowej i tak dalej.  
  
     Chronionego dostępu nie jest nadzbiorem lub podzbiór dostęp zaprzyjaźniony.  
  
- **Modyfikatory dostępu.** Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorach dostępu*. Dla porównania modyfikatory dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Protected` Modyfikator mogą być używane w tych kontekstach:  
  
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

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
