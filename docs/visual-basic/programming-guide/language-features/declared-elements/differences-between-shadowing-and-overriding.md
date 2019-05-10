---
title: Różnice pomiędzy przesłanianiem i zastępowaniem (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: 8fcf43040e9cbbcb2a59b1e1cf8c1f58951d5d87
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610475"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>Różnice pomiędzy przesłanianiem i zastępowaniem (Visual Basic)
Podczas definiowania klasy, która dziedziczy z klasy bazowej, czasami trzeba na nowo zdefiniować co najmniej jeden z elementów klasy podstawowej w klasie pochodnej. Przesłanianiem i zastępowaniem są dostępne w tym celu.  
  
## <a name="comparison"></a>Porównanie  
 Przesłanianiem i zastępowaniem są używane, gdy klasa pochodna dziedziczy z klasy bazowej, a jednocześnie ponownie zdefiniować jeden element zadeklarowany z innym. Jednak istnieją znaczne różnice między nimi.  
  
 W poniższej tabeli porównano przesłanianie z nadpisaniem.  
  
||||  
|---|---|---|  
|Punkt odniesienia|Zasłanianie|Zastępowanie|  
|Cel|Chroni przed modyfikację klasy bazowej, w której wprowadzono elementu członkowskiego, które są już zdefiniowane w klasie pochodnej|Osiąga polimorfizm, definiując z inną implementacją procedura lub właściwość o tej samej sekwencja wywoływania<sup>1</sup>|  
|Zmieniony element|Dowolny zadeklarowany typ elementu|Tylko procedurę (`Function`, `Sub`, lub `Operator`) lub właściwości|  
|Zmiana definicji elementu|Dowolny zadeklarowany typ elementu|Procedura lub właściwość o identycznych sekwencja wywoływania<sup>1</sup>|  
|Zmiana definicji elementu poziom dostępu|Dowolny poziom dostępu|Nie można zmienić poziomu dostępu element zastąpiony|  
|Czytelność i obiekty elementu element, definiują na nowo|Dowolna kombinacja|Nie można zmienić czytelności lub obiekty właściwości|  
|Kontrola nad, definiują na nowo|Element klasy bazowej nie może wymusić lub ze Stanów Zjednoczonych zabraniają przesłanianie|Można określić elementu klasy podstawowej `MustOverride`, `NotOverridable`, lub `Overridable`|  
|Użycie słowa kluczowego|`Shadows` Zaleca się w klasie pochodnej; `Shadows` zakłada, że jeśli żadna `Shadows` ani `Overrides` określonego<sup>2</sup>|`Overridable` lub `MustOverride` wymagane w klasie bazowej; `Overrides` wymagane w klasie pochodnej|  
|Zmiana definicji elementu przez klasy wywodzące się z klasy pochodnej dziedziczenia|Przesłanianie elementu dziedziczone przez klasy; dodatkowo pochodne element zasłonięte wciąż ukryte<sup>3</sup>|Zastępowanie elementu dziedziczone przez klasy; dodatkowo pochodne element zastąpiony nadal przesłonięcia|  
  
 <sup>1</sup> *sekwencja wywoływania* składa się z typem elementu (`Function`, `Sub`, `Operator`, lub `Property`), nadaj nazwę liście parametrów i typ zwracany. Nie można zastąpić procedurę z właściwością lub odwrotnie. Nie można przesłonić, jeden rodzaj procedury (`Function`, `Sub`, lub `Operator`) przy użyciu innego rodzaju.  
  
 <sup>2</sup> Jeśli nie określisz `Shadows` lub `Overrides`, kompilator generuje ostrzeżenie, aby ułatwić upewnij się, jakiego rodzaju ponowne zdefiniowanie, do którego chcesz użyć. Jeśli zignorujesz to ostrzeżenie, jest używany mechanizm przesłaniania.  
  
 <sup>3</sup> Jeśli przesłaniania elementu jest niedostępna w klasie pochodnej dalsze, cieniowania nie jest dziedziczony. Na przykład, jeśli zadeklarować przesłaniania elementu jako `Private`, Klasa pochodząca od klasy pochodnej dziedziczy oryginalnego elementu zamiast przesłaniania elementu.  
  
## <a name="guidelines"></a>Wytyczne dotyczące  
 Zwykle używana, zastępowanie w następujących przypadkach:  
  
- Definiujesz polimorficznych klas pochodnych.  
  
- Chcesz, aby bezpieczeństwa mające kompilatora wymusić typ elementu identyczne i sekwencja wywoływania.  
  
 Zwykle używana, przesłanianie w następujących przypadkach:  
  
- Przewiduje się, że klasę bazową mogą zostać zmodyfikowane i zdefiniuj elementu za pomocą tej samej nazwie jako należy do Ciebie.  
  
- Możesz korzystać ze swobody zmieniając typ elementu lub sekwencja wywoływania.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Przesłanianie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Instrukcje: Ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Instrukcje: Ukrywanie dziedziczonej zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Instrukcje: Dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
