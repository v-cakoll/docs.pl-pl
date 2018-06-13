---
title: Różnice pomiędzy przesłanianiem i zastępowaniem (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: 94ce3e7fe25b7942730e6e89a53654b03d91c42b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649636"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>Różnice pomiędzy przesłanianiem i zastępowaniem (Visual Basic)
Po zdefiniowaniu klasy, która dziedziczy po klasie podstawowej czasami chcą ponownie zdefiniować co najmniej jeden z elementów klasy podstawowej w klasie pochodnej. Przesłanianiem i zastępowaniem są dostępne w tym celu.  
  
## <a name="comparison"></a>Porównanie  
 Przesłanianiem i zastępowaniem są używane podczas klasy pochodnej dziedziczy z klasy podstawowej, a jednocześnie ponownie definiować jeden element zadeklarowany z innym. Ale są istotne różnice między nimi.  
  
 W poniższej tabeli porównano przesłanianie z zastępowanie.  
  
||||  
|---|---|---|  
|Porównania|Przesłanianie|Zastępowanie|  
|Cel|Chroni przed zmianie klasy podstawowej, przedstawiający element członkowski, który już został zdefiniowany w klasie pochodnej|Osiąga polimorfizm, definiując inną implementację procedura lub właściwość o tej samej sekwencja wywoływania<sup>1</sup>|  
|Ponownie zdefiniowany element|Wszelkie zadeklarowany jako typ elementu|Tylko procedurę (`Function`, `Sub`, lub `Operator`) lub właściwość|  
|Ponowne definiowanie — element|Wszelkie zadeklarowany jako typ elementu|Procedura lub właściwość o identycznych sekwencja wywoływania<sup>1</sup>|  
|Ponowne definiowanie element poziom dostępu|Dowolny poziom dostępu|Nie można zmienić poziom dostępu element zastąpiony|  
|Zwiększyć czytelność, a writability o ponownym zdefiniowaniem — element|Dowolna kombinacja|Nie można zmienić czytelności lub writability przesłanianej właściwości|  
|Kontrola nad ponowne definiowanie|Klasy podstawowej elementu nie można wymusić lub zabronić przesłanianie|Można określić elementu klasy podstawowej `MustOverride`, `NotOverridable`, lub `Overridable`|  
|Użycie słowa kluczowego|`Shadows` zalecane w klasie pochodnej; `Shadows` zakłada, że jeśli żadna `Shadows` ani `Overrides` określonego<sup>2</sup>|`Overridable` lub `MustOverride` wymagane w klasie podstawowej; `Overrides` wymagane w klasie pochodnej|  
|Ponowne definiowanie elementu przez klasy wywodzące się z klasy pochodnej dziedziczenia|Przesłanianie elementu dziedziczone przez klasy; dalsze pochodne element zasłonięty wciąż ukryte<sup>3</sup>|Zastępowanie elementu dziedziczone przez klasy; dalsze pochodne element zastąpiony nadal przesłonięcia|  
  
 <sup>1</sup> *sekwencja wywoływania* składa się z typem elementu (`Function`, `Sub`, `Operator`, lub `Property`), name, lista parametrów i typ zwracany. Nie można zastąpić procedurę z właściwością ani odwrotnie. Nie można zastąpić jedną rodzaj procedury (`Function`, `Sub`, lub `Operator`) z innego rodzaju.  
  
 <sup>2</sup> Jeśli nie określisz albo `Shadows` lub `Overrides`, kompilator generuje ostrzeżenie ułatwiające upewnij się, jakiego rodzaju zmiana definicji, którego chcesz użyć. Jeśli zignorujesz to ostrzeżenie jest używany mechanizm przesłaniania.  
  
 <sup>3</sup> przypadku przesłaniania element jest niedostępny w dalszych klasy pochodnej, cieniowania nie jest dziedziczone. Na przykład w przypadku przesłaniania element jako `Private`, tworzenia klasy pochodnej z klasy pochodnej klasy dziedziczy oryginalnego elementu zamiast elementu przesłaniania.  
  
## <a name="guidelines"></a>Wytyczne dotyczące  
 Zwykle jest używana zastępowanie w następujących przypadkach:  
  
-   Definiujesz polimorficzne klas pochodnych.  
  
-   Ma bezpieczeństwa o kompilatora zapewniać taki sam typ elementu i sekwencja wywoływania.  
  
 Zwykle jest używana funkcja obserwowania w następujących przypadkach:  
  
-   Spodziewasz się, że klasy podstawowej mogą zostać zmodyfikowane i zdefiniować element przy użyciu takiej samej nazwie jako należy do Ciebie.  
  
-   Ma swobody zmiana typu element lub sekwencja wywoływania.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Przesłanianie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Instrukcje: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [Instrukcje: ukrywanie dziedziczonej zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [Instrukcje: dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
