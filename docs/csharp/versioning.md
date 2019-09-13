---
title: C#Obsługa wersji — C# Przewodnik
description: Informacje o C# działaniu wersji i programie .NET
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: bfad7abe6b2b5c6a19324656963a79212a317110
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926579"
---
# <a name="versioning-in-c"></a>Przechowywanie wersji w języku C\#

W tym samouczku dowiesz się, jakie wersje są używane w programie .NET. Poznasz również czynniki, które należy wziąć pod uwagę w przypadku przechowywania wersji biblioteki, a także uaktualniania do nowej wersji biblioteki.

## <a name="authoring-libraries"></a>Tworzenie bibliotek

Jako deweloper, który utworzył biblioteki platformy .NET do użytku publicznego, najprawdopodobniej zachodzi konieczność wdrożenia nowych aktualizacji. Sposób działania tego procesu polega na tym, że zachodzi taka potrzeba, aby upewnić się, że istnieje bezproblemowe przejście istniejącego kodu do nowej wersji biblioteki. Poniżej przedstawiono kilka kwestii, które należy wziąć pod uwagę podczas tworzenia nowej wersji:

### <a name="semantic-versioning"></a>Wersja semantyczna

[Wersja semantyczna](https://semver.org/) (SemVer for Short) to Konwencja nazewnictwa stosowana do wersji biblioteki do oznaczania określonych zdarzeń punktów kontrolnych.
W idealnym przypadku informacje o wersji, którą udostępnia Twoja biblioteka, powinny pomóc deweloperom w ustaleniu zgodności z projektami, które korzystają ze starszych wersji tej samej biblioteki.

Najbardziej podstawowym podejściem do SemVer jest format `MAJOR.MINOR.PATCH`3 składników, gdzie:

* `MAJOR`zwiększa się po wprowadzeniu niezgodnych zmian interfejsu API
* `MINOR`zwiększa się w przypadku dodawania funkcji w sposób zgodny z poprzednimi wersjami
* `PATCH`zwiększa się w przypadku wprowadzania poprawek błędów zgodnych z poprzednimi wersjami

Istnieją również sposoby określania innych scenariuszy, takich jak wersje wstępne itp. w przypadku stosowania informacji o wersji do biblioteki platformy .NET.

### <a name="backwards-compatibility"></a>Zgodność z poprzednimi wersjami

Po udostępnieniu nowych wersji biblioteki, zgodność z poprzednimi wersjami będzie prawdopodobnie jednym z najważniejszych problemów.
Nowa wersja biblioteki jest zgodna ze źródłem w poprzedniej wersji, jeśli kod, który zależy od poprzedniej wersji, może, po ponownym skompilowaniu, współpracować z nową wersją. Nowa wersja biblioteki jest zgodna z binarną, jeśli aplikacja, która jest zależna od starej wersji, może, bez ponownej kompilacji, działała z nową wersją.

Poniżej przedstawiono kilka kwestii, które należy wziąć pod uwagę podczas próby utrzymania zgodności z poprzednimi wersjami w przypadku starszych wersji biblioteki:

* Metody wirtualne: Po wprowadzeniu wirtualnej metody w nowej wersji oznacza to, że projekty, które przesłaniają tę metodę, będą musiały zostać zaktualizowane. Jest to ogromna istotna zmiana i zdecydowanie odradza się.
* Sygnatury metod: Podczas aktualizowania zachowania metody, należy również zmienić jego sygnaturę, zamiast tego należy utworzyć Przeciążenie, aby kod wywołujący metodę będzie nadal działał.
Zawsze możesz manipulować starym podpisem metody, aby wywołać nową metodę sygnatury, tak aby implementacja była spójna.
* [Przestarzały atrybut](programming-guide/concepts/attributes/common-attributes.md#Obsolete): Tego atrybutu można użyć w kodzie, aby określić klasy lub elementy członkowskie klasy, które są przestarzałe i które mogą zostać usunięte w przyszłych wersjach. Dzięki temu deweloperzy korzystający z biblioteki są lepiej przygotowani do istotnych zmian.
* Argumenty metody opcjonalnej: Po wprowadzeniu wcześniej argumentów metody opcjonalnej lub zmianie ich wartości domyślnej, należy zaktualizować cały kod, który nie dostarcza tych argumentów.

> [!NOTE]
> Obowiązkowe opcjonalne argumenty powinny mieć bardzo niewielki wpływ, zwłaszcza jeśli nie zmieniają zachowań metody.

Dzięki temu użytkownicy będą mogli uaktualnić do nowej wersji biblioteki, im większa jest możliwość ich uaktualnienia.

### <a name="application-configuration-file"></a>Plik konfiguracji aplikacji

Deweloperem platformy .NET jest bardzo wysoka szansa [ `app.config` ](../framework/configure-apps/file-schema/index.md) , że plik jest obecny w większości typów projektów.
Ten prosty plik konfiguracji może być długim sposobem ulepszania wdrażania nowych aktualizacji. Zazwyczaj należy zaprojektować biblioteki w taki sposób, że informacje, które mogą być regularnie zmieniane, są przechowywane `app.config` w pliku, w ten sposób, gdy takie informacje zostaną zaktualizowane, plik konfiguracyjny starszych wersji musi zostać zastąpiony nowym bez potrzeby ponownej kompilacji biblioteki.

## <a name="consuming-libraries"></a>Używanie bibliotek

Deweloperzy korzystający z bibliotek .NET zbudowanych przez innych deweloperów najprawdopodobniej wiedzą, że nowa wersja biblioteki może nie być w pełni zgodna z projektem i często można sprawdzić, czy trzeba zaktualizować swój kod, aby pracować z tymi zmianami.

Cieszymy dla Ciebie C# i ekosystem platformy .NET zawiera funkcje i techniki umożliwiające łatwą aktualizację naszej aplikacji do pracy z nowymi wersjami bibliotek, które mogą spowodować istotne zmiany.

### <a name="assembly-binding-redirection"></a>Przekierowanie powiązania zestawu

Możesz użyć `app.config` pliku do zaktualizowania wersji biblioteki używanej przez aplikację. Dodając jak nazywa się [*przekierowanie powiązania*](../framework/configure-apps/redirect-assembly-versions.md) , możesz użyć nowej wersji biblioteki bez konieczności ponownego kompilowania aplikacji. W poniższym przykładzie pokazano, jak `app.config` zaktualizować plik aplikacji tak, `1.0.1` aby korzystał z `1.0.0` wersji `ReferencedLibrary` poprawki zamiast wersji, która została pierwotnie skompilowana za pomocą programu.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Ta metoda będzie działała tylko wtedy, gdy nowa `ReferencedLibrary` wersja pliku jest binarna zgodna z Twoją aplikacją.
> W sekcji [zgodność z poprzednimi wersjami](#backwards-compatibility) powyżej znajdziesz zmiany, które należy wyszukać podczas określania zgodności.

### <a name="new"></a>new

`new` Modyfikator służy do ukrywania dziedziczonych elementów członkowskich klasy bazowej. Jest to jeden ze sposobów, w jaki klasy pochodne mogą odpowiadać na aktualizacje w klasach bazowych.

Wykonaj następujące czynności:

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

**Output**

```
A base method
A derived method
```

Z powyższego przykładu można zobaczyć `DerivedClass` , `MyMethod` jak ukrywa metodę `BaseClass`.
Oznacza to, że gdy klasa bazowa w nowej wersji biblioteki dodaje element członkowski, który już istnieje w klasie pochodnej, można po prostu użyć `new` modyfikatora w składowej klasy pochodnej, aby ukryć element członkowski klasy bazowej.

Gdy nie `new` określono modyfikatora, Klasa pochodna domyślnie ukrywa elementy członkowskie powodujące konflikt w klasie bazowej, mimo że zostanie wygenerowane Ostrzeżenie kompilatora, kod nadal zostanie skompilowany. Oznacza to, że po prostu dodanie nowych elementów członkowskich do istniejącej klasy powoduje, że nowa wersja biblioteki jest zgodna z kodem, który od niego zależy.

### <a name="override"></a>override

`override` Modyfikator oznacza implementację pochodną rozszerza implementację składowej klasy bazowej, a nie ukrywa ją. Do elementu członkowskiego klasy podstawowej należy `virtual` zastosować modyfikator.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

**Output**

```
Base Method One: Method One
Derived Method One: Derived Method One
```

`override` Modyfikator jest oceniany w czasie kompilacji, a kompilator zgłosi błąd, jeśli nie znajdzie wirtualnego elementu członkowskiego do przesłonięcia.

Wiedza na temat omawianych technik, a także zrozumienie, jakie sytuacje ich używania, będzie zbyt długim sposobem, aby zwiększyć łatwość przechodzenia między wersjami biblioteki.
 