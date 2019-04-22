---
title: Element „<typename>” nie może dziedziczyć po elemencie <type> „<basetypename>", ponieważ rozszerza dostęp podstawowego elementu <type> poza zestawem
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: dc979a66c73fdf15a4349a003680156e0ce27ed3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838953"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>"\<typename >' nie może dziedziczyć z \<typu >"\<basetypename > ", ponieważ rozszerza on dostęp podstawowego \<typ > spoza zestawu
Klasa lub interfejs dziedziczy z klasy bazowej lub interfejsu, lecz jest mniej restrykcyjny poziom dostępu.  
  
 Na przykład `Public` interfejs dziedziczy z `Friend` interfejsu, lub `Protected` klasa dziedziczy `Private` klasy. Udostępnia to klasy bazowej lub interfejsu, aby uzyskać dostęp poza poziomem zamierzone.  
  
 **Identyfikator błędu:** BC30910  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zmień poziom dostępu pochodne klasy lub interfejsu restrykcyjną co najmniej tak jak w przypadku klasy bazowej lub interfejsu.  
  
     —lub—  
  
-   Jeśli potrzebujesz mniej restrykcyjny poziom dostępu, Usuń `Inherits` instrukcji. Nie można dziedziczyć bardziej ograniczony klasy bazowej lub interfejsu.  
  
## <a name="see-also"></a>Zobacz także

- [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)
- [Instrukcja Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Inherits, instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
