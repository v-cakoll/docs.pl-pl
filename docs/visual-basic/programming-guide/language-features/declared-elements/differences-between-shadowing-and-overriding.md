---
title: Różnice pomiędzy przesłanianiem i zastępowaniem
ms.date: 07/20/2015
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
ms.openlocfilehash: 8d1ebdcd0a23dff69a7acca22268c03e30ec06d9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345417"
---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a>Różnice pomiędzy przesłanianiem i zastępowaniem (Visual Basic)
Podczas definiowania klasy, która dziedziczy z klasy bazowej, Czasami chcesz zmienić definicję co najmniej jednego elementu klasy bazowej w klasie pochodnej. W tym celu są dostępne zarówno przesłanianie, jak i przesłanianie.  
  
## <a name="comparison"></a>Porównanie  
 Przesłonięcie i przesłanianie są używane, gdy Klasa pochodna dziedziczy z klasy bazowej, i obie przedefiniują jeden zadeklarowany element z innym. Istnieją jednak znaczące różnice między nimi.  
  
 Poniższa tabela zawiera porównanie przesłaniania z zastępowaniem.  
  
||||  
|---|---|---|  
|Punkt porównania|Zasłanianie|Zastępuje|  
|Przeznaczenie|Chroni przed kolejną modyfikacją klasy podstawowej, która wprowadza element członkowski, który został już zdefiniowany w klasie pochodnej|Osiąga polimorfizm przez zdefiniowanie innej implementacji procedury lub właściwości z tą samą sekwencją wywołania<sup>1</sup>|  
|Ponownie zdefiniowany element|Dowolny zadeklarowany typ elementu|Tylko procedura (`Function`, `Sub`lub `Operator`) lub właściwość|  
|Ponowne definiowanie elementu|Dowolny zadeklarowany typ elementu|Tylko procedura lub właściwość o identycznej sekwencji wywołania<sup>1</sup>|  
|Poziom dostępu elementu do ponownego definiowania|Dowolny poziom dostępu|Nie można zmienić poziomu dostępu przesłoniętego elementu|  
|Czytelność i writability ponownego definiowania elementu|Dowolna kombinacja|Nie można zmienić wartości Read lub writability zastąpionej właściwości|  
|Kontrola nad ponownym definiowaniem|Element klasy bazowej nie może wymusić lub zabronić przesłaniania|Element klasy bazowej może określać `MustOverride`, `NotOverridable`lub `Overridable`|  
|Użycie słowa kluczowego|`Shadows` zalecane w klasie pochodnej; przyjęto `Shadows`, jeśli nie `Shadows` ani `Overrides` określone<sup>2</sup>|`Overridable` lub `MustOverride` wymagane w klasie bazowej; `Overrides` wymagane w klasie pochodnej|  
|Dziedziczenie elementu do ponownego definiowania przez klasy pochodne z klasy pochodnej|Element Shadows dziedziczony przez dalsze klasy pochodne; element w tle nadal ukryty<sup>3</sup>|Przesłanianie elementu dziedziczone przez dalsze klasy pochodne; element zastąpiony nadal został zastąpiony|  
  
 <sup>1</sup> *sekwencja wywołująca* składa się z typu elementu (`Function`, `Sub`, `Operator`lub `Property`), nazwy, listy parametrów i typu zwracanego. Nie można przesłonić procedury z właściwością ani w inny sposób. Nie można zastąpić jednego rodzaju procedury (`Function`, `Sub`lub `Operator`) innym rodzajem.  
  
 <sup>2</sup> Jeśli nie określisz żadnej `Shadows` lub `Overrides`, kompilator generuje komunikat ostrzegawczy, aby upewnić się, jakiego rodzaju zmiana definicji ma być używana. Jeśli zignorujesz ostrzeżenie, zostanie użyty mechanizm przesłaniania.  
  
 <sup>3</sup> Jeśli element przesłaniania jest niedostępny w dalszej klasie pochodnej, przesłanianie nie jest dziedziczone. Na przykład jeśli zadeklarujesz element shadowing jako `Private`, Klasa pochodna klasy pochodnej dziedziczy oryginalny element zamiast elementu shadowing.  
  
## <a name="guidelines"></a>Wytyczne dotyczące  
 Zwykle używasz przesłaniania w następujących przypadkach:  
  
- Definiujesz klasy pochodne polimorficzne.  
  
- Bezpieczeństwo posiadania kompilatora wymusza identyczny typ elementu i sekwencję wywoływania.  
  
 Zwykle używasz obserwowania w następujących przypadkach:  
  
- Przewiduje się, że klasa bazowa może zostać zmodyfikowana, i zdefiniować element przy użyciu takiej samej nazwy jak nazwa użytkownika.  
  
- Potrzebujesz swobody zmiany typu elementu lub sekwencji wywołania.  
  
## <a name="see-also"></a>Zobacz także

- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Obserwowanie w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Instrukcje: ukrywanie zmiennej o tej samej nazwie jako zmiennej użytkownika](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Instrukcje: ukrywanie dziedziczonej zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Instrukcje: dostęp do zmiennej ukrytej przez klasę pochodną](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
