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
ms.openlocfilehash: 5f279ed0a33840bb1f2321c17a1ffba412837c07
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234760"
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)
Modyfikator dostępu elementu członkowskiego, który określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie swojej klasy lub z klasy pochodnej.  
  
## <a name="remarks"></a>Uwagi  
 Czasami elementu programistycznego zadeklarowana w klasie zawierają dane poufne lub ograniczone kod, a użytkownik chce ograniczyć dostęp do elementu. Jednak jeśli oczekujesz hierarchii klas pochodnych klasy jest dziedziczona, może być konieczne dla tych klas pochodnych dostępu do danych lub kodu. W takim przypadku ma element ma być dostępny zarówno z klasy podstawowej i wszystkich klas pochodnych. Aby ograniczyć dostęp do elementu w ten sposób, mogą zadeklarować za pomocą `Protected`.  

> [!NOTE]
> `Protected` Modyfikator dostępu można łączyć z dwóch innych modyfikatorów:
> - [Protected Friend](protected-friend.md) modyfikator sprawia, że element członkowski klasy jest dostępny w obrębie klasy, z klasy pochodnej i z tego samego zestawu, w którym klasa jest zdefiniowana. 
> - [Prywatne chronione](private-protected.md) modyfikator sprawia, że element członkowski klasy dostępne przez typy pochodne, ale tylko w obrębie zawierający go zestaw.
  
## <a name="rules"></a>Reguły  
  
-   **Kontekst deklaracji.** Można użyć `Protected` tylko na poziomie klasy. Oznacza to, że w kontekście deklaracji `Protected` elementu musi być klasą i nie może być plik źródłowy, przestrzeni nazw, interfejsu, modułu, struktury lub procedury.  

## <a name="behavior"></a>Zachowanie  
  
-   **Poziom dostępu.** Cały kod w klasie mogą uzyskiwać dostęp do swoich elementów. Kod w dowolnej klasy, która pochodzi z klasy podstawowej można uzyskać dostęp do wszystkich `Protected` elementy klasy podstawowej. Jest to istotne dla wszystkich generacji pochodnym. Oznacza to, że klasa może uzyskać dostęp `Protected` elementy klasy podstawowej klasy podstawowej i tak dalej.  
  
     Chronionego dostępu nie jest nadzbiorem lub podzbiór przyjaznego dostępu.  
  
-   **Modyfikatory dostępu.** Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorów dostępu*. Porównanie modyfikatorów dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Protected` Modyfikatora można używać w tych sytuacjach:  
  
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
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../visual-basic/language-reference/modifiers/private.md)  
 [Prywatne chronione](private-protected.md)   
 [Friend chronionych](protected-friend.md)   
 [Poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
