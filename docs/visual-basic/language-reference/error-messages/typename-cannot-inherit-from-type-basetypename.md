---
title: Element „<typename>” nie może dziedziczyć po elemencie <type> „<basetypename>", ponieważ rozszerza dostęp podstawowego elementu <type> poza zestawem
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: aa04c558abbcc4259c2821cdcbdc1669b91ffee0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402775"
---
# <a name="typename-cannot-inherit-from-type-basetypename-because-it-expands-the-access-of-the-base-type-outside-the-assembly"></a>Element „\<typename>” nie może dziedziczyć po elemencie \<type> „\<basetypename>", ponieważ rozszerza dostęp podstawowego elementu \<type> poza zestawem
Klasa lub interfejs dziedziczy z klasy bazowej lub interfejsu, ale ma mniej restrykcyjny poziom dostępu.  
  
 Na przykład `Public` interfejs dziedziczy z `Friend` interfejsu lub `Protected` Klasa dziedziczy z `Private` klasy. To ujawnia klasę bazową lub interfejs, aby uzyskać dostęp poza zaplanowanym poziomem.  
  
 **Identyfikator błędu:** BC30910  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
- Zmień poziom dostępu klasy pochodnej lub interfejsu na co najmniej jako restrykcyjny dla klasy bazowej lub interfejsu.  
  
     -lub-  
  
- Jeśli potrzebujesz mniej restrykcyjnego poziomu dostępu, Usuń `Inherits` instrukcję. Nie można dziedziczyć z bardziej ograniczonej klasy bazowej lub interfejsu.  
  
## <a name="see-also"></a>Zobacz też

- [Class, instrukcja](../statements/class-statement.md)
- [Interface, instrukcja](../statements/interface-statement.md)
- [Inherits — Instrukcja](../statements/inherits-statement.md)
- [Poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
