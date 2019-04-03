---
title: Private (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
ms.openlocfilehash: d6e28e5e87c3a88e4db3fc81177894683dbb0908
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819480"
---
# <a name="private-visual-basic"></a>Private (Visual Basic)
Określa, że co najmniej jeden zadeklarowany element programistyczny jest dostępny tylko w obrębie ich kontekst deklaracji, łącznie z w obrębie wszystkich typów zawartych.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli elementu programistycznego reprezentuje własnościowych funkcji lub zawiera dane poufne, zazwyczaj chcesz ograniczyć dostęp do niego jako ściśle. Ograniczenie maksymalnej można osiągnąć, zezwalając tylko modułu, klasy lub struktury, który definiuje go do niego dostęp. Aby ograniczyć dostęp do elementu w ten sposób, można zadeklarować za pomocą `Private`.  

> [!NOTE]
> Można również użyć [Private Protected](private-protected.md) modyfikator dostępu, co sprawia, że członek jest dostępny z tej klasy i znajduje się w jego zawierające zestaw klas pochodnych.

## <a name="rules"></a>reguły  

-   **Kontekst deklaracji.** Możesz użyć `Private` tylko na poziomie modułu. Oznacza to, że kontekst deklaracji `Private` elementu musi być modułu, klasy lub struktury, a nie może być plikiem źródłowym, przestrzeń nazw, interfejs lub procedury.  
  
## <a name="behavior"></a>Zachowanie  
  
-   **Poziom dostępu.** Cały kod w kontekście deklaracji mogą uzyskiwać dostęp do jego `Private` elementów. W tym kodu w ramach zamkniętego typu, na przykład klasa zagnieżdżona lub wyrażenia przypisania w wyliczeniu. Żaden kod poza kontekstem deklaracji mogą uzyskiwać dostęp do jego `Private` elementów.  
  
-   **Modyfikatory dostępu.** Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorach dostępu*. Dla porównania modyfikatory dostępu, zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
 `Private` Modyfikator mogą być używane w tych kontekstach:  
  
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
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private Protected](./private-protected.md)
- [Protected Friend](./protected-friend.md)[dostęp do poziomów w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Obiekty i klasy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
