---
title: Przechowywanie wersji języka C# — przewodnik po języku C#
description: Dowiedz się, jak działa przechowywanie wersji w językach C# i .NET
ms.date: 01/08/2017
ms.technology: csharp-advanced-concepts
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 124cce51865f04a555bc121fb6ce18cc95591bdc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156470"
---
# <a name="versioning-in-c"></a>Przechowywanie wersji w C\#

W tym samouczku dowiesz się, co oznacza przechowywanie wersji w .NET. Dowiesz się również, które należy wziąć pod uwagę podczas wersji biblioteki, a także uaktualniania do nowej wersji biblioteki.

## <a name="authoring-libraries"></a>Biblioteki tworzenia

Jako deweloper, który utworzył biblioteki .NET do użytku publicznego, najprawdopodobniej byłeś w sytuacjach, w których musisz wdrożyć nowe aktualizacje. Sposób, w jaki przechodzisz do tego procesu, ma duże znaczenie, ponieważ musisz upewnić się, że istnieje płynne przejście istniejącego kodu do nowej wersji biblioteki. Oto kilka rzeczy, które należy wziąć pod uwagę podczas tworzenia nowej wersji:

### <a name="semantic-versioning"></a>Przechowywanie wersji semantycznych

[Przechowywanie wersji semantycznych](https://semver.org/) (semver w skrócie) jest konwencją nazewnictwa stosowaną do wersji biblioteki w celu oznaczania określonych zdarzeń punktu kontrolnego.
W idealnym przypadku informacje o wersji, które podajesz biblioteki powinny pomóc deweloperom określić zgodność z ich projektów, które korzystają ze starszych wersji tej samej biblioteki.

Najbardziej podstawowym podejściem do SemVer `MAJOR.MINOR.PATCH`jest format komponentu 3, gdzie:

- `MAJOR`jest zwiększana po wprowadzeniu niezgodnych zmian interfejsu API
- `MINOR`jest zwiększana po dodaniu funkcji w sposób zgodny z poprzednimi wersjami
- `PATCH`jest zwiększana po wprowadzeniu poprawek błędów zgodnych z poprzednimi wersjami

Istnieją również sposoby określania innych scenariuszy, takich jak wersje wstępne itp.

### <a name="backwards-compatibility"></a>Zgodność z poprzednimi wersjami

Wraz z wydaniem nowych wersji biblioteki, wsteczna kompatybilność z poprzednimi wersjami będzie najprawdopodobniej jednym z głównych problemów.
Nowa wersja biblioteki jest potomna zgodna z poprzednią wersją, jeśli kod, który zależy od poprzedniej wersji, może, po ponownym skompilowaniu, pracować z nową wersją.
Nowa wersja biblioteki jest zgodna z plikami binarnymi, jeśli aplikacja, która zależała od starej wersji, może bez ponownej kompilacji pracować z nową wersją.

Oto kilka rzeczy, które należy wziąć pod uwagę podczas próby zachowania zgodności wstecznej ze starszymi wersjami biblioteki:

- Metody wirtualne: Po uczynieniu metody wirtualnej niewirtualnej w nowej wersji oznacza to, że projekty, które zastępują tę metodę, będą musiały zostać zaktualizowane. Jest to ogromna przełomowa zmiana i zdecydowanie odradza się.
- Podpisy metody: Podczas aktualizowania zachowanie metody wymaga zmiany jego podpis, jak również, należy zamiast tego utworzyć przeciążenie, tak aby wywołanie kodu do tej metody będzie nadal działać.
Zawsze można manipulować podpis starej metody, aby wywołać podpis nowej metody, dzięki czemu implementacja pozostaje spójna.
- [Atrybut Przestarzały](programming-guide/concepts/attributes/common-attributes.md#Obsolete): Można użyć tego atrybutu w kodzie, aby określić klasy lub elementy członkowskie klasy, które są przestarzałe i prawdopodobnie zostaną usunięte w przyszłych wersjach. Dzięki temu deweloperzy korzystający z biblioteki są lepiej przygotowani do przełomowych zmian.
- Opcjonalne argumenty metody: Po wprowadzeniu wcześniej opcjonalnych argumentów metody obowiązkowe lub zmienić ich wartość domyślną, a następnie cały kod, który nie dostarcza tych argumentów będą musiały zostać zaktualizowane.

> [!NOTE]
> Wprowadzenie obowiązkowych argumentów opcjonalne powinno mieć bardzo niewielki wpływ, zwłaszcza jeśli nie zmienia zachowania metody.

Im łatwiej będzie użytkownikom uaktualnić do nowej wersji biblioteki, tym bardziej prawdopodobne jest, że zostaną uaktualnieni wcześniej.

### <a name="application-configuration-file"></a>Plik konfiguracji aplikacji

Jako programista .NET istnieje bardzo duża szansa, że napotkałeś [ `app.config` plik](../framework/configure-apps/file-schema/index.md) obecny w większości typów projektów.
Ten prosty plik konfiguracyjny może przejść długą drogę do poprawy wdrażania nowych aktualizacji. Zazwyczaj należy zaprojektować biblioteki w taki sposób, aby informacje, które mogą `app.config` się regularnie zmieniać, były przechowywane w pliku, w ten sposób, gdy takie informacje są aktualizowane, plik konfiguracyjny starszych wersji po prostu musi zostać zastąpiony nową bez konieczności ponownej kompilacji biblioteki.

## <a name="consuming-libraries"></a>Korzystanie z bibliotek

Jako deweloper, który zużywa biblioteki .NET utworzone przez innych deweloperów najprawdopodobniej wiesz, że nowa wersja biblioteki może nie być w pełni zgodne z projektem i często może się okazać, że musisz zaktualizować kod, aby pracować z tymi zmianami.

Na szczęście dla Ciebie, C# i ekosystemu .NET pochodzi z funkcji i technik, które pozwalają nam łatwo zaktualizować naszą aplikację do pracy z nowymi wersjami bibliotek, które mogą wprowadzać przełomowe zmiany.

### <a name="assembly-binding-redirection"></a>Przekierowanie wiązania złożenia

Za pomocą pliku *app.config* można zaktualizować wersję biblioteki używanej przez aplikację. Dodając tak zwane [*przekierowanie powiązania,*](../framework/configure-apps/redirect-assembly-versions.md)można użyć nowej wersji biblioteki bez konieczności ponownej kompilacji aplikacji. W poniższym przykładzie pokazano, jak zaktualizować plik *app.config* `ReferencedLibrary` aplikacji, `1.0.0` aby użyć wersji `1.0.1` poprawki zamiast wersji, z którą został pierwotnie skompilowany.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Takie podejście będzie działać tylko `ReferencedLibrary` wtedy, gdy nowa wersja jest zgodna z plikami binarnymi z aplikacją.
> Zobacz [wstecznej zgodności](#backwards-compatibility) sekcji powyżej zmian, na które należy zwrócić uwagę podczas określania zgodności.

### <a name="new"></a>new

Modyfikator służy `new` do ukrywania dziedziczonych członków klasy podstawowej. Jest to jeden ze sposobów pochodnych klas można odpowiedzieć na aktualizacje w klasach podstawowych.

Weźmy następujący przykład:

[!code-csharp[Sample usage of the 'new' modifier](~/samples/snippets/csharp/versioning/new/Program.cs#sample)]

**Wyjście**

```console
A base method
A derived method
```

W powyższym przykładzie można `DerivedClass` zobaczyć, `MyMethod` jak `BaseClass`ukrywa metodę obecną w pliku .
Oznacza to, że gdy klasa podstawowa w nowej wersji biblioteki dodaje element członkowski, `new` który już istnieje w klasie pochodnej, można po prostu użyć modyfikatora na element członkowski klasy pochodnej, aby ukryć element członkowski klasy podstawowej.

Po `new` nie modyfikator jest określony, klasa pochodna domyślnie ukryć elementy członkowskie powodujące konflikt w klasie podstawowej, mimo że ostrzeżenie kompilatora zostanie wygenerowany kod będzie nadal kompilować. Oznacza to, że po prostu dodawanie nowych elementów członkowskich do istniejącej klasy sprawia, że nowa wersja biblioteki zarówno źródło, jak i binarny zgodny z kodem, który zależy od niego.

### <a name="override"></a>override

Modyfikator `override` oznacza implementacji pochodnej rozszerza implementację elementu członkowskiego klasy podstawowej, a nie ukrywa go. Element członkowski klasy `virtual` podstawowej musi mieć modyfikator zastosowany do niego.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/snippets/csharp/versioning/override/Program.cs#sample)]

**Wyjście**

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

Modyfikator `override` jest oceniany w czasie kompilacji i kompilator będzie zgłaszać błąd, jeśli nie znajdzie członka wirtualnego do zastąpienia.

Twoja wiedza na temat omawianych technik i zrozumienie sytuacji, w których można z nich korzystać, będzie przejść długą drogę w kierunku złagodzenia przejścia między wersjami biblioteki.
