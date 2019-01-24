---
title: '&#39;&lt;Element TypeName&gt; &#39; nie może dziedziczyć z &lt;typu&gt; &#39; &lt;basetypename&gt; &#39; ponieważ rozszerza on dostęp podstawowego &lt;typu&gt; poza zestawem'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: 108025132bdd0fa86df5ed142aaa39c7b7e18062
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556486"
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a>&#39;&lt;Element TypeName&gt; &#39; nie może dziedziczyć z &lt;typu&gt; &#39; &lt;basetypename&gt; &#39; ponieważ rozszerza on dostęp podstawowego &lt;typu&gt; poza zestawem
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
