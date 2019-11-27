---
title: Poziomy dostępu
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
ms.openlocfilehash: 33a218a2acc3c876428d6c9a887280a559f84323
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348680"
---
# <a name="access-levels-in-visual-basic"></a>Poziomy dostępu w Visual Basic

*Poziom dostępu* zadeklarowanego elementu to zakres możliwości dostępu do niego, czyli kod, który ma uprawnienia do odczytu lub zapisu. Jest to ustalane nie tylko w przypadku deklarowania samego elementu, ale również według poziomu dostępu kontenera elementu. Kod, który nie może uzyskać dostępu do elementu zawierającego, nie może uzyskać dostępu do żadnego z zawartych w nim elementów, nawet tych zadeklarowanych jako `Public`. Na przykład można uzyskać dostęp do zmiennej `Public` w strukturze `Private` z wnętrza klasy, która zawiera strukturę, ale nie spoza tej klasy.

## <a name="public"></a>Public

[Publiczne](../../../language-reference/modifiers/public.md) słowo kluczowe w instrukcji deklaracji określa, że do elementu można uzyskać dostęp z dowolnego miejsca w tym samym projekcie, od innych projektów odwołujących się do projektu oraz z dowolnego zestawu skompilowanego z projektu. Poniższy kod przedstawia przykładową deklarację `Public`:

```vb
Public Class ClassForEverybody
```

`Public` można używać tylko na poziomie modułu, interfejsu lub przestrzeni nazw. Oznacza to, że można zadeklarować element publiczny na poziomie pliku źródłowego lub przestrzeni nazw albo wewnątrz interfejsu, modułu, klasy lub struktury, ale nie w procedurze.
  
## <a name="protected"></a>Protected

[Chronione](../../../language-reference/modifiers/protected.md) słowo kluczowe w instrukcji deklaracji określa, że do elementu można uzyskać dostęp tylko z tej samej klasy lub z klasy pochodnej tej klasy. Poniższy kod przedstawia przykładową deklarację `Protected`:

```vb
Protected Class ClassForMyHeirs
```

`Protected` można używać tylko na poziomie klasy i tylko wtedy, gdy deklarujesz składową klasy. Oznacza to, że można zadeklarować element chroniony w klasie, ale nie na poziomie pliku źródłowego lub przestrzeni nazw lub wewnątrz interfejsu, modułu, struktury lub procedury.

## <a name="friend"></a>Friend

Słowo kluczowe [zaprzyjaźnione](../../../language-reference/modifiers/friend.md) w instrukcji deklaracji określa, że do elementu można uzyskać dostęp z tego samego zestawu, ale nie z spoza zestawu. Poniższy kod przedstawia przykładową deklarację `Friend`:

```vb
Friend stringForThisProject As String
```

`Friend` można używać tylko na poziomie modułu, interfejsu lub przestrzeni nazw. Oznacza to, że można zadeklarować zaprzyjaźniony element na poziomie pliku źródłowego lub przestrzeni nazw albo wewnątrz interfejsu, modułu, klasy lub struktury, ale nie w procedurze.

## <a name="protected-friend"></a>Protected Friend

Kombinacja [chronionych słów kluczowych zaprzyjaźniona](../../../language-reference/modifiers/protected-friend.md) w instrukcji deklaracji określa, że do elementu można uzyskać dostęp z klas pochodnych lub z tego samego zestawu lub obu tych elementów. Poniższy kod przedstawia przykładową deklarację `Protected Friend`:

```vb
Protected Friend stringForProjectAndHeirs As String
```

`Protected Friend` można używać tylko na poziomie klasy i tylko wtedy, gdy deklarujesz składową klasy. Oznacza to, że można zadeklarować chroniony element zaprzyjaźniony w klasie, ale nie na poziomie pliku źródłowego lub przestrzeni nazw lub wewnątrz interfejsu, modułu, struktury lub procedury.

## <a name="private"></a>Private

[Prywatne](../../../language-reference/modifiers/private.md) słowo kluczowe w instrukcji deklaracji określa, że do elementu można uzyskać dostęp tylko z tego samego modułu, klasy lub struktury. Poniższy kod przedstawia przykładową deklarację `Private`:

```vb
Private _numberForMeOnly As Integer
```

`Private` można używać tylko na poziomie modułu. Oznacza to, że można zadeklarować element prywatny wewnątrz modułu, klasy lub struktury, ale nie na poziomie pliku źródłowego lub przestrzeni nazw, wewnątrz interfejsu lub w procedurze.

Na poziomie modułu instrukcja `Dim` bez żadnych słów kluczowych poziomu dostępu jest równoważna z deklaracją `Private`. Można jednak użyć słowa kluczowego `Private`, aby ułatwić odczytywanie i interpretację kodu.

## <a name="private-protected"></a>Private Protected

[Prywatna kombinacja prywatnych](../../../language-reference/modifiers/private-protected.md) słów kluczowych w instrukcji deklaracji określa, że element jest dostępny tylko w obrębie tej samej klasy, a także z klas pochodnych, które znajdują się w tym samym zestawie, co Klasa zawierająca. Modyfikator dostępu `Private Protected` jest obsługiwany począwszy od Visual Basic 15,5.

W poniższym przykładzie pokazano `Private Protected` deklaracji:

```vb
Private Protected internalValue As Integer
```

Element `Private Protected` można zadeklarować tylko wewnątrz klasy. Nie można zadeklarować go w obrębie interfejsu lub struktury ani nie można go zadeklarować na poziomie pliku źródłowego lub przestrzeni nazw, wewnątrz interfejsu lub struktury lub w procedurze.

Modyfikator dostępu `Private Protected` jest obsługiwany przez Visual Basic 15,5 i nowsze. Aby go użyć, należy dodać następujący element do pliku projektu Visual Basic ( *\*. vbproj*). Tak długo, jak Visual Basic 15,5 lub nowszy jest zainstalowany w systemie, umożliwia korzystanie ze wszystkich funkcji językowych obsługiwanych przez najnowszą wersję kompilatora Visual Basic:

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

Aby użyć modyfikatora dostępu `Private Protected`, należy dodać następujący element do pliku projektu Visual Basic ( *\*. vbproj*):

```xml
<PropertyGroup>
   <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Aby uzyskać więcej informacji [, zobacz Ustawianie wersji językowej Visual Basic](../../../language-reference/configure-language-version.md).

## <a name="access-modifiers"></a>Modyfikatory dostępu

Słowa kluczowe określające poziom dostępu są nazywane *modyfikatorami dostępu*. W poniższej tabeli porównano Modyfikatory dostępu:

|Modyfikator dostępu|Udzielony poziom dostępu|Elementy, które można zadeklarować przy użyciu tego poziomu dostępu|Kontekst deklaracji, w ramach którego można użyć tego modyfikatora|
|---------------------|--------------------------|-----------------------------------------------------|----------------------------------------------------------------|
|`Public`|Nieograniczone<br /><br /> Każdy kod, który może zobaczyć element publiczny, może uzyskać do niego dostęp|Interfejsy<br /><br /> Moduły<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Elementy członkowskie struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne składowe<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Plik źródłowy<br /><br /> Przestrzeń nazw<br /><br /> Interface<br /><br /> Moduł<br /><br /> Class<br /><br /> Struktura|
|`Protected`|Tworzenie pochodne:<br /><br /> Kod w klasie, która deklaruje chroniony element lub Klasa pochodna, może uzyskać dostęp do elementu|Interfejsy<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne składowe<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Class|
|`Friend`|Zestaw:<br /><br /> Kod w zestawie, który deklaruje element zaprzyjaźniony, może uzyskać do niego dostęp|Interfejsy<br /><br /> Moduły<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Elementy członkowskie struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne składowe<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Plik źródłowy<br /><br /> Przestrzeń nazw<br /><br /> Interface<br /><br /> Moduł<br /><br /> Class<br /><br /> Struktura|
|`Protected``Friend`|Unia `Protected` i `Friend`:<br /><br /> Kod znajdujący się w tej samej klasie lub w tym samym zestawie, co chroniony element zaprzyjaźniony, lub w dowolnej klasie pochodnej klasy elementu, może uzyskać do niej dostęp|Interfejsy<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne składowe<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Class|
|`Private`|Kontekst deklaracji:<br /><br /> Kod w typie, który deklaruje prywatny element, łącznie z kodem w zawartych typach, może uzyskać dostęp do elementu|Interfejsy<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Elementy członkowskie struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne składowe<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Moduł<br /><br /> Class<br /><br /> Struktura|
|`Private Protected`|Kod w klasie, która deklaruje prywatny element chroniony lub kod w klasie pochodnej znaleziono w tym samym zestawie, co Klasa bas.|Interfejsy<br /><br /> Klasy<br /><br /> Struktury<br /><br /> Procedury<br /><br /> Właściwości<br /><br /> Zmienne składowe<br /><br /> Stałe<br /><br /> Wyliczenia<br /><br /> Zdarzenia<br /><br /> Deklaracje zewnętrzne<br /><br /> Delegaty|Class|

## <a name="see-also"></a>Zobacz także

- [Dim, instrukcja](../../../language-reference/statements/dim-statement.md)
- [Static](../../../language-reference/modifiers/static.md)
- [Nazwy zadeklarowanych elementów](declared-element-names.md)
- [Odwołania do elementów zadeklarowanych](references-to-declared-elements.md)
- [Charakterystyka zadeklarowanych elementów](declared-element-characteristics.md)
- [Okres istnienia w Visual Basic](lifetime.md)
- [Zakres w Visual Basic](scope.md)
- [Instrukcje: kontrolowanie dostępności zmiennej](how-to-control-the-availability-of-a-variable.md)
- [Zmienne](../variables/index.md)
- [Deklaracja zmiennej](../variables/variable-declaration.md)
