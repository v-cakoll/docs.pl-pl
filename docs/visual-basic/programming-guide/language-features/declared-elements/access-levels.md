---
title: Poziomy dostępu w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- members [Visual Basic], accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private access modifier
- declared elements [Visual Basic], access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
ms.openlocfilehash: 6f8fda62e468e3735e3ae36afdebe440a8e4bc04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="access-levels-in-visual-basic"></a>Poziomy dostępu w Visual Basic
*Poziom dostępu* zadeklarowany element jest zakres możliwości dostępu do niego, oznacza to, jaki kod ma uprawnienie do jego odczytu lub zapisu do niego. Jest to określane nie tylko przez jak zadeklarować samego elementu, ale również przez poziom dostępu do kontenera elementu. Kod, który nie ma dostępu do elementu zawierającego nie może uzyskać dostępu do jego zawartych w niej elementów, nawet te zadeklarowany jako `Public`. Na przykład `Public` zmiennej w `Private` struktury są dostępne z wewnątrz klasy, która zawiera strukturę, ale nie z spoza tej klasy.  
  
## <a name="public"></a>Public  
 [Publicznego](../../../../visual-basic/language-reference/modifiers/public.md) — słowo kluczowe w instrukcji deklaracji określa, że elementy są dostępne z kodu w dowolnym miejscu tego samego projektu z innych projektów, które odwołują się do projektu i z wszelkich zestawu utworzonego na podstawie projektu. Poniższy kod przedstawia przykład `Public` deklaracji.  
  
```  
Public Class classForEverybody  
```  
  
 Można użyć `Public` tylko na poziomie modułu, interfejsem lub przestrzeni nazw. Oznacza to, że można zadeklarować elementu publicznego na poziomie pliku źródłowego lub obszaru nazw, lub wewnątrz interfejsu modułu, klasy lub struktury, ale nie w procedurze.  
  
## <a name="protected"></a>Protected  
 [Chronione](../../../../visual-basic/language-reference/modifiers/protected.md) — słowo kluczowe w instrukcji deklaracji określa, czy elementy są dostępne tylko z należące do tej samej klasy lub z klasy pochodzącej od tej klasy. Poniższy kod przedstawia przykład `Protected` deklaracji.  
  
```  
Protected Class classForMyHeirs  
```  
  
 Można użyć `Protected` tylko w klasie poziomu, a tylko po deklaracji elementu członkowskiego klasy. Oznacza to, że można zadeklarować elementu chroniony w klasie, ale nie na poziomie pliku źródłowego lub obszaru nazw lub wewnątrz interfejsu, modułu, struktury lub procedury.  
  
## <a name="friend"></a>Friend  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) — słowo kluczowe w instrukcji deklaracji określa, czy elementy są dostępne z wewnątrz tego samego zestawu, ale nie z poza zestaw. Poniższy kod przedstawia przykład `Friend` deklaracji.  
  
```  
Friend stringForThisProject As String  
```  
  
 Można użyć `Friend` tylko na poziomie modułu, interfejsem lub przestrzeni nazw. Oznacza to, że można deklarować elementu przyjaznego na poziomie pliku źródłowego lub obszaru nazw, lub wewnątrz interfejsu modułu, klasy lub struktury, ale nie w procedurze.  
  
## <a name="protected-friend"></a>Friend chronionych  
 `Protected` i `Friend` słowa kluczowe w instrukcji deklaracji określają, że elementy są dostępne z klasy pochodnej lub z poziomu tego samego zestawu, lub obie. Poniższy kod przedstawia przykład `Protected Friend` deklaracji.  
  
```  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 Można użyć `Protected Friend` tylko w klasie poziomu, a tylko po deklaracji elementu członkowskiego klasy. Oznacza to, że można deklarować elementu przyjaznego chronionych w klasie, ale nie na poziomie pliku źródłowego lub obszaru nazw lub wewnątrz interfejsu, modułu, struktury lub procedury.  
  
## <a name="private"></a>Private  
 [Prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) — słowo kluczowe w instrukcji deklaracji określa, że elementy są dostępne tylko z wewnątrz tego samego modułu, klasy lub struktury. Poniższy kod przedstawia przykład `Private` deklaracji.  
  
```  
Private numberForMeOnly As Integer  
```  
  
 Można użyć `Private` tylko na poziomie modułu. Oznacza to, że można zadeklarować elementu prywatnej wewnątrz modułu, klasy lub struktury, ale nie na poziomie pliku źródłowego lub obszaru nazw, w interfejsie lub w procedurze.  
  
 Na poziomie modułu `Dim` instrukcję bez żadnych słowa kluczowe do poziomu dostępu jest odpowiednikiem `Private` deklaracji. Jednak możesz chcieć użyć `Private` — słowo kluczowe w celu uczynienia kodu jest łatwiej odczytywać i interpretowania.  
  
## <a name="access-modifiers"></a>Modyfikatory dostępu  
 Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorów dostępu*. W poniższej tabeli porównano modyfikatorów dostępu.  
  
|Modyfikator dostępu|Poziom dostępu przyznanych|Elementy można zadeklarować tego poziomu dostępu|Kontekst deklaracji w ramach którego można użyć modyfikator|  
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|  
|`Public`|Bez ograniczeń:<br /><br /> Wszelki kod, który można wyświetlić elementu publiczny dostęp do niego|Interfejsy<br /><br /> Moduły<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Elementy członkowskie struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne Członkowskie<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Plik źródłowy<br /><br /> Przestrzeń nazw<br /><br /> Interface<br /><br /> Moduł<br /><br /> Class<br /><br /> Struktura|  
|`Protected`|Derivational:<br /><br /> Kod w klasie, która deklaruje chronionego elementu lub klasę pochodną, mogą uzyskiwać dostęp do elementu|Interfejsy<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne Członkowskie<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Class|  
|`Friend`|Zestaw:<br /><br /> Kod w zestawie, która deklaruje friend element do niego dostęp|Interfejsy<br /><br /> Moduły<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Elementy członkowskie struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne Członkowskie<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Plik źródłowy<br /><br /> Przestrzeń nazw<br /><br /> Interface<br /><br /> Moduł<br /><br /> Class<br /><br /> Struktura|  
|`Protected``Friend`|Union z `Protected` i `Friend`:<br /><br /> Kod w tej samej klasy lub tego samego zestawu jako element friend chronionych lub w dowolnej klasy pochodnej z klasy elementu, do niego dostęp|Interfejsy<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne Członkowskie<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Class|  
|`Private`|Kontekst deklaracji:<br /><br /> Kod w typie, który deklaruje element prywatny, tym kod w typach zawartych w niej mogą uzyskiwać dostęp do elementu|Interfejsy<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Elementy członkowskie struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne Członkowskie<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Moduł<br /><br /> Class<br /><br /> Struktura|  
  
## <a name="see-also"></a>Zobacz też  
 [Dim, instrukcja](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)  
 [Nazwy zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Charakterystyka zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [Okres istnienia w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Instrukcje: kontrolowanie dostępności zmiennej](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-availability-of-a-variable.md)  
 [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
