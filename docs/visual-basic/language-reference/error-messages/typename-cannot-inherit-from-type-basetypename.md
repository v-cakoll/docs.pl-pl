---
title: '&#39;&lt;Właściwość TypeName&gt; &#39; nie może dziedziczyć po &lt;typu&gt; &#39; &lt;basetypename&gt; &#39; ponieważ rozszerza on dostęp podstawowego &lt;typu&gt; poza zestaw'
ms.date: 07/20/2015
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
ms.openlocfilehash: f747b2b24f5fecc22b9e1fbc6ba26b634e9ead2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a>&#39;&lt;Właściwość TypeName&gt; &#39; nie może dziedziczyć po &lt;typu&gt; &#39; &lt;basetypename&gt; &#39; ponieważ rozszerza on dostęp podstawowego &lt;typu&gt; poza zestaw
Klasy lub interfejsu dziedziczy z klasy podstawowej lub interfejsu, ale ma mniej restrykcyjną poziom dostępu.  
  
 Na przykład `Public` dziedziczy interfejs `Friend` interfejsu, lub `Protected` klasa dziedziczy `Private` klasy. Udostępnia to klasy podstawowej lub interfejsu dostępu poza poziomem przeznaczone do.  
  
 **Identyfikator błędu:** BC30910  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Zmień poziom dostępu do klasy pochodnej lub interfejsu się co najmniej stosować jak największe restrykcje klasy podstawowej lub interfejsu.  
  
     —lub—  
  
-   Jeśli potrzebujesz poziom dostępu mniej restrykcyjny, Usuń `Inherits` instrukcji. Nie można dziedziczyć bardziej ograniczony w klasie podstawowej lub interfejsu.  
  
## <a name="see-also"></a>Zobacz też  
 [Class, instrukcja](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface, instrukcja](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Inherits, instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Poziomy dostępu w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
