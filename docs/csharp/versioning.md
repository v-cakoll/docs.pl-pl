---
title: C# Versioning - Przewodnik języka C#
description: Dowiedz się, jak działa przechowywanie wersji w językach C# i NET
ms.date: 01/08/2017
ms.technology: csharp-advanced-concepts
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: dc192337e4eaa5f9f1d6509ea8c15deeac34a48c
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645456"
---
# <a name="versioning-in-c"></a>Przechowywanie wersji w języku C\#

W tym samouczku dowiesz się, co oznacza przechowywanie wersji w .NET. Poznasz również czynniki, które należy wziąć pod uwagę podczas przechowywania wersji biblioteki, a także uaktualniania do nowej wersji biblioteki.

## <a name="authoring-libraries"></a>Tworzenie bibliotek

Jako deweloper, który utworzył biblioteki platformy .NET do użytku publicznego, najprawdopodobniej byłeś w sytuacjach, w których musisz wdrożyć nowe aktualizacje. Sposób, w jaki można przejść do tego procesu ma duże znaczenie, jak trzeba, aby upewnić się, że istnieje bezproblemowe przejście istniejącego kodu do nowej wersji biblioteki. Oto kilka rzeczy, które należy wziąć pod uwagę podczas tworzenia nowej wersji:

### <a name="semantic-versioning"></a>Przechowywanie wersji semantycznych

[Przechowywanie wersji semantycznych](https://semver.org/) (w skrócie SemVer) to konwencja nazewnictwa stosowana do wersji biblioteki w celu oznaczenia określonych zdarzeń punktu kontrolnego.
W idealnym przypadku informacje o wersji, które podajesz biblioteki powinny pomóc deweloperom określić zgodność z ich projektów, które korzystają ze starszych wersji tej samej biblioteki.

Najbardziej podstawowym podejściem do SemVer jest `MAJOR.MINOR.PATCH`format 3-komponentowy, w którym:

- `MAJOR`zwiększa się po wprowadzeniu niezgodnych zmian interfejsu API
- `MINOR`zwiększa się po dodaniu funkcji w sposób zgodny z do tyłu
- `PATCH`jest zwiększany po dokonywalnych wstecznych poprawkach błędów

Istnieją również sposoby, aby określić inne scenariusze, takie jak wersje wstępne itp podczas stosowania informacji o wersji do biblioteki .NET.

### <a name="backwards-compatibility"></a>Zgodność z przewładem

Podczas wydawania nowych wersji biblioteki zgodność z poprzednimi wersjami będzie najprawdopodobniej jedną z głównych obaw.
Nowa wersja biblioteki jest źródłem zgodnym z poprzednią wersją, jeśli kod zależny od poprzedniej wersji może, po ponownym skompilacji, pracować z nową wersją.
Nowa wersja biblioteki jest zgodna z binarnym, jeśli aplikacja, która zależała od starej wersji może bez ponownej kompilacji pracować z nową wersją.

Oto kilka rzeczy, które należy wziąć pod uwagę podczas próby zachowania zgodności z powrotem ze starszymi wersjami biblioteki:

- Metody wirtualne: Po wprowadzeniu metody wirtualnej niewirtuatu w nowej wersji oznacza to, że projekty, które zastępują tę metodę, będą musiały zostać zaktualizowane. Jest to ogromna zmiana łamiąca i jest zdecydowanie odradzana.
- Podpisy metody: Podczas aktualizowania zachowania metody wymaga zmiany jego podpisu, jak również, zamiast tego należy utworzyć przeciążenie, dzięki czemu kod wywołujący do tej metody będzie nadal działać.
Zawsze można manipulować podpis starej metody, aby wywołać do nowego podpisu metody, tak aby implementacja pozostaje spójna.
- [Przestarzały atrybut:](language-reference/attributes/general.md#obsolete-attribute)Można użyć tego atrybutu w kodzie, aby określić klasy lub członków klasy, które są przestarzałe i mogą zostać usunięte w przyszłych wersjach. Dzięki temu deweloperzy korzystający z biblioteki są lepiej przygotowani do przełomowych zmian.
- Opcjonalne argumenty metody: Po wprowadzeniu wcześniej opcjonalnych argumentów metody obowiązkowe lub zmienić ich wartość domyślną następnie cały kod, który nie dostarcza tych argumentów będą musiały zostać zaktualizowane.

> [!NOTE]
> Dokonywanie obowiązkowe argumenty opcjonalne powinny mieć bardzo niewielki wpływ, zwłaszcza jeśli nie zmienia zachowanie metody.

Im łatwiej będzie użytkownikom uaktualnić do nowej wersji biblioteki, tym większe prawdopodobieństwo, że uaktualnią wcześniej.

### <a name="application-configuration-file"></a>Plik konfiguracji aplikacji

Jako deweloper platformy .NET istnieje bardzo duża szansa, że napotkałeś [ `app.config` plik](../framework/configure-apps/file-schema/index.md) obecny w większości typów projektów.
Ten prosty plik konfiguracyjny może przejść długą drogę do poprawy wdrażania nowych aktualizacji. Zazwyczaj należy zaprojektować biblioteki w taki sposób, aby informacje, które `app.config` mogą się regularnie zmieniać, były przechowywane w pliku, w ten sposób, gdy takie informacje są aktualizowane, plik konfiguracyjny starszych wersji po prostu musi zostać zastąpiony nowym bez konieczności ponownej kompilacji biblioteki.

## <a name="consuming-libraries"></a>Korzystanie z bibliotek

Jako deweloper, który korzysta z bibliotek platformy .NET utworzonych przez innych deweloperów, najprawdopodobniej zdajesz sobie sprawę, że nowa wersja biblioteki może nie być w pełni zgodna z projektem i często może się okazać, że musisz zaktualizować kod, aby pracować z tymi zmianami.

Na szczęście dla Ciebie, C# i ekosystemu .NET jest wyposażony w funkcje i techniki, które pozwalają nam łatwo zaktualizować naszą aplikację do pracy z nowymi wersjami bibliotek, które mogą wprowadzać przełomowe zmiany.

### <a name="assembly-binding-redirection"></a>Przekierowanie powiązania zestawu

Za pomocą pliku *app.config* można zaktualizować wersję biblioteki używanej przez aplikację. Dodając to, co nazywa się [*przekierowaniem powiązania,*](../framework/configure-apps/redirect-assembly-versions.md)można użyć nowej wersji biblioteki bez konieczności ponownej kompilacji aplikacji. Poniższy przykład pokazuje, jak można zaktualizować plik *app.config* aplikacji, `ReferencedLibrary` aby użyć `1.0.0` wersji `1.0.1` poprawki zamiast wersji, z którą została pierwotnie skompilowana.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Takie podejście będzie działać tylko `ReferencedLibrary` wtedy, gdy nowa wersja jest binarna zgodna z aplikacją.
> Zobacz [sekcję Zgodność wsteczna](#backwards-compatibility) powyżej, aby uzyskać zmiany, na które należy zwrócić uwagę podczas określania zgodności.

### <a name="new"></a>new

`new` Modyfikator służy do ukrywania odziedziczonych elementów członkowskich klasy podstawowej. Jest to jeden ze sposobów klas pochodnych może odpowiadać na aktualizacje w klasach podstawowych.

Weźmy następujący przykład:

[!code-csharp[Sample usage of the 'new' modifier](~/samples/snippets/csharp/versioning/new/Program.cs#sample)]

**Dane wyjściowe**

```console
A base method
A derived method
```

Z powyższego przykładu `DerivedClass` można zobaczyć, jak ukrywa metodę obecną `MyMethod` w `BaseClass`.
Oznacza to, że gdy klasa podstawowa w nowej wersji biblioteki dodaje element członkowski, który `new` już istnieje w klasie pochodnej, można po prostu użyć modyfikatora na element członkowski klasy pochodnej, aby ukryć element członkowski klasy podstawowej.

Gdy `new` nie określono modyfikatora, klasa pochodna domyślnie ukryje elementy członkowskie powodujące konflikt w klasie podstawowej, chociaż zostanie wygenerowane ostrzeżenie kompilatora, że kod będzie nadal kompilowany. Oznacza to, że po prostu dodanie nowych elementów członkowskich do istniejącej klasy sprawia, że nowa wersja biblioteki zarówno źródła i binarne zgodne z kodem, który zależy od niego.

### <a name="override"></a>override

Modyfikator `override` oznacza implementacji pochodnej rozszerza implementację elementu członkowskiego klasy podstawowej, a nie ukrywa go. Element członkowski klasy podstawowej musi mieć `virtual` modyfikator stosowane do niego.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/snippets/csharp/versioning/override/Program.cs#sample)]

**Dane wyjściowe**

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

Modyfikator `override` jest oceniany w czasie kompilacji i kompilator zrzuci błąd, jeśli nie znajdzie wirtualnego elementu członkowskiego do zastąpienia.

Twoja wiedza na temat omawianych technik i zrozumienie sytuacji, w których można z nich korzystać, będzie przejść długą drogę w kierunku złagodzenia przejścia między wersjami biblioteki.
