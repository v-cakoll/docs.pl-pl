---
title: Poziomy dostępu w Visual Basic
ms.date: 05/10/2018
helpviewer_keywords:
- members [Visual Basic], accessing in Visual Basic
- Friend access modifier
- access levels, declared elements
- access levels
- access modifiers
- Public access modifier
- Protected access modifier
- Protected Friend access modifier
- Private Protected access modifier
- Private access modifier
- declared elements [Visual Basic], access level
ms.assetid: 6e06c1ab-fd78-47f0-83a8-1152780b5e1a
ms.openlocfilehash: 433d5dfd4bb3af9b6fbd0dfc951bb0448eb7efcd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183148"
---
# <a name="access-levels-in-visual-basic"></a>Poziomy dostępu w Visual Basic
*Poziom dostępu* zadeklarowanych elementów jest w zakresie możliwości dostępu do niego, oznacza to, jaki kod ma uprawnienia do jego odczytu lub zapisanie w nim. Jest to ustalane nie tylko, jak zadeklarować elementu, ale z poziomem dostępu do kontenera elementu. Kod, który nie może uzyskać dostępu zawierającego element nie może uzyskać dostępu do dowolnego z jego zawartych elementów, nawet te zadeklarowane jako `Public`. Na przykład `Public` zmienną `Private` struktury jest możliwy z wewnątrz klasy, która zawiera strukturę, ale nie z spoza tej klasy.  
  
## <a name="public"></a>Public  
 [Publicznych](../../../../visual-basic/language-reference/modifiers/public.md) słowo kluczowe w instrukcji deklaracji określa, czy element jest możliwy z kodu w dowolnym miejscu w tym samym projekcie, inne projekty, które odwołują się projektu i z dowolnego zestawu zbudowany z projektu. Poniższy kod przedstawia przykład `Public` deklaracji.  
  
```vb  
Public Class classForEverybody  
```  
  
 Możesz użyć `Public` tylko na poziomie modułu, interfejsu lub przestrzeni nazw. Oznacza to, że można zadeklarować elementu publicznego na poziomie pliku źródłowego lub obszaru nazw, lub wewnątrz interfejsu, modułu, klasy lub struktury, ale nie w procedurze.  
  
## <a name="protected"></a>Protected  
 [Chronione](../../../../visual-basic/language-reference/modifiers/protected.md) słowo kluczowe w instrukcji deklaracji określa, czy element jest możliwy tylko z w ramach tej samej klasy lub z klasy pochodzącej od tej klasy. Poniższy kod przedstawia przykład `Protected` deklaracji.  
  
```vb  
Protected Class classForMyHeirs  
```  
  
 Możesz użyć `Protected` tylko w klasie poziomu i tylko po zadeklarowaniu składową klasy. Oznacza to, że można zadeklarować elementu chronionego w klasie, ale nie na poziomie pliku źródłowego lub obszaru nazw lub wewnątrz interfejsu, moduł, struktura lub procedury.  
  
## <a name="friend"></a>Friend  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) słowo kluczowe w instrukcji deklaracji określa, czy element jest możliwy z w obrębie tego samego zestawu, ale nie z spoza zestawu. Poniższy kod przedstawia przykład `Friend` deklaracji.  
  
```vb  
Friend stringForThisProject As String  
```  
  
 Możesz użyć `Friend` tylko na poziomie modułu, interfejsu lub przestrzeni nazw. Oznacza to, że możesz deklarować elementu przyjaznego na poziomie pliku źródłowego lub obszaru nazw, lub wewnątrz interfejsu, modułu, klasy lub struktury, ale nie w procedurze.  
  
## <a name="protected-friend"></a>Chronione Friend  
 [Protected Friend](../../../language-reference/modifiers/protected-friend.md) kombinacja słów kluczowych w instrukcji deklaracji określa, czy element jest możliwy z klasy pochodnej lub z poziomu tego samego zestawu lub obie. Poniższy kod przedstawia przykład `Protected Friend` deklaracji.  
  
```vb  
Protected Friend stringForProjectAndHeirs As String  
```  
  
 Możesz użyć `Protected Friend` tylko w klasie poziomu i tylko po zadeklarowaniu składową klasy. Oznacza to, że możesz deklarować elementu przyjaznego chronionych w klasie, ale nie na poziomie pliku źródłowego lub obszaru nazw lub wewnątrz interfejsu, moduł, struktura lub procedury.  
  
## <a name="private"></a>Private  
 [Prywatnej](../../../../visual-basic/language-reference/modifiers/private.md) słowo kluczowe w instrukcji deklaracji określa, czy element jest możliwy tylko z w obrębie tego samego modułu, klasy lub struktury. Poniższy kod przedstawia przykład `Private` deklaracji.  
  
```vb  
Private numberForMeOnly As Integer  
```  
  
 Możesz użyć `Private` tylko na poziomie modułu. Oznacza to, że można zadeklarować elementu prywatnej wewnątrz modułu, klasy lub struktury, ale nie na poziomie pliku źródłowego lub obszaru nazw, wewnątrz interfejs lub w procedurze.  
  
 Na poziomie modułu `Dim` instrukcję bez żadnych słów kluczowych do poziomu dostępu jest odpowiednikiem `Private` deklaracji. Jednakże, możesz chcieć użyć `Private` — słowo kluczowe, aby ułatwić odczytanie i interpretację swój kod.  

## <a name="private-protected"></a>Prywatny chroniony

[Private Protected](../../../language-reference/modifiers/private-protected.md) kombinacja słów kluczowych w instrukcji deklaracji określa, czy element jest możliwy tylko z w ramach tej samej klasy, a także od klas pochodnych, w tym samym zestawie co klasa zawierająca. `Private Protected` Modyfikator dostępu jest obsługiwane począwszy od wersji 15.5 programu Visual Basic.

W poniższym przykładzie przedstawiono `Private Protected` deklaracji:

```vb
Private Protected internalValue As Integer
```

Można zadeklarować `Private Protected` element tylko wewnątrz klasy. Nie można zadeklarować ją w ramach interfejsu lub struktury, nie można zadeklarować je na poziomie pliku źródłowego lub obszaru nazw, wewnątrz interfejsu lub struktury lub w procedurze.

`Private Protected` Modyfikator dostępu jest obsługiwane w wersji 15.5 programu Visual Basic lub nowszy. Aby go użyć, Dodaj następujący element do pliku projektu (*.vbproj) języka Visual Basic. Jak długo, jak 15.5 Visual Basic lub nowszy jest zainstalowany w systemie, umożliwia korzystanie z zalet wszystkich funkcji językowych obsługiwanych przez najnowszą wersję kompilatora języka Visual Basic:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Aby użyć `Private Protected` modyfikator dostępu, należy dodać następujący element do pliku projektu (*.vbproj) języka Visual Basic:

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Aby uzyskać więcej informacji, zobacz [ustawienie wersji języka Visual Basic](../../../language-reference/configure-language-version.md).

 ## <a name="access-modifiers"></a>Modyfikatory dostępu  
 Słowa kluczowe, które określają poziom dostępu są nazywane *modyfikatorach dostępu*. W poniższej tabeli porównano modyfikatorami dostępu.  
  
|Modyfikator dostępu|Poziom dostępu przyznane|Elementy można zadeklarować za pomocą tego poziomu dostępu|Kontekst deklaracji, w którym można użyć ten modyfikator|  
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|  
|`Public`|Bez ograniczeń:<br /><br /> Wszelki kod, który można zobaczyć element publiczny dostęp do niego|Interfejsy<br /><br /> Moduły<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Elementy członkowskie struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne Członkowskie<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Plik źródłowy<br /><br /> Przestrzeń nazw<br /><br /> Interface<br /><br /> Moduł<br /><br /> Class<br /><br /> Struktura|  
|`Protected`|Derivational:<br /><br /> Możesz pisać kod w klasie, która deklaruje, że chroniony element lub klasę pochodną, mogą uzyskiwać dostęp do elementu|Interfejsy<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne Członkowskie<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Class|  
|`Friend`|Zestaw:<br /><br /> Kod w zestawie, który deklaruje, że element znajomego do niego dostęp|Interfejsy<br /><br /> Moduły<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Elementy członkowskie struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne Członkowskie<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Plik źródłowy<br /><br /> Przestrzeń nazw<br /><br /> Interface<br /><br /> Moduł<br /><br /> Class<br /><br /> Struktura|  
|`Protected``Friend`|Złożenia z `Protected` i `Friend`:<br /><br /> Możesz pisać kod w tej samej klasie lub tego samego zestawu jako element friend chronionej lub w dowolnej klasie pochodnej z klasy elementu, można uzyskać do niego dostęp|Interfejsy<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne Członkowskie<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Class|  
|`Private`|Kontekst deklaracji:<br /><br /> Kod w typie, który deklaruje, że element prywatne, łącznie z kodem w ramach zamkniętego typów mogą uzyskiwać dostęp do elementu|Interfejsy<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Elementy członkowskie struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne Członkowskie<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Moduł<br /><br /> Class<br /><br /> Struktura|
|`Private Protected`|Kod w klasie, która deklaruje element prywatny chroniony lub kod w klasie pochodnej, w tym samym zestawie co klasa bas.|Interfejsy<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne Członkowskie<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Class|
  
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
