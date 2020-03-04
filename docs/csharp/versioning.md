---
title: C#Obsługa wersji — C# Przewodnik
description: Informacje o C# działaniu wersji i programie .NET
ms.date: 01/08/2017
ms.technology: csharp-advanced-concepts
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: ee123893ac8baa0a55bdf69ce49fb6fcb87601b4
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240005"
---
# <a name="versioning-in-c"></a>Przechowywanie wersji w języku C\#

W tym samouczku dowiesz się, jakie wersje są używane w programie .NET. Poznasz również czynniki, które należy wziąć pod uwagę w przypadku przechowywania wersji biblioteki, a także uaktualniania do nowej wersji biblioteki.

## <a name="authoring-libraries"></a>Tworzenie bibliotek

Jako deweloper, który utworzył biblioteki platformy .NET do użytku publicznego, najprawdopodobniej zachodzi konieczność wdrożenia nowych aktualizacji. Sposób działania tego procesu polega na tym, że zachodzi taka potrzeba, aby upewnić się, że istnieje bezproblemowe przejście istniejącego kodu do nowej wersji biblioteki. Poniżej przedstawiono kilka kwestii, które należy wziąć pod uwagę podczas tworzenia nowej wersji:

### <a name="semantic-versioning"></a>Wersja semantyczna

[Wersja semantyczna](https://semver.org/) (SemVer for Short) to Konwencja nazewnictwa stosowana do wersji biblioteki do oznaczania określonych zdarzeń punktów kontrolnych.
W idealnym przypadku informacje o wersji, którą udostępnia Twoja biblioteka, powinny pomóc deweloperom w ustaleniu zgodności z projektami, które korzystają ze starszych wersji tej samej biblioteki.

Najbardziej podstawowym podejściem do SemVer jest format 3 składników `MAJOR.MINOR.PATCH`, gdzie:

- `MAJOR` jest zwiększana w przypadku wprowadzania niezgodnych zmian interfejsu API
- `MINOR` zwiększa się w przypadku dodawania funkcji w sposób zgodny z poprzednimi wersjami
- `PATCH` jest zwiększana w przypadku wprowadzania poprawek błędów zgodnych z poprzednimi wersjami

Istnieją również sposoby określania innych scenariuszy, takich jak wersje wstępne itp. w przypadku stosowania informacji o wersji do biblioteki platformy .NET.

### <a name="backwards-compatibility"></a>Zgodność z poprzednimi wersjami

Po udostępnieniu nowych wersji biblioteki, zgodność z poprzednimi wersjami będzie prawdopodobnie jednym z najważniejszych problemów.
Nowa wersja biblioteki jest zgodna ze źródłem w poprzedniej wersji, jeśli kod, który zależy od poprzedniej wersji, może, po ponownym skompilowaniu, współpracować z nową wersją. Nowa wersja biblioteki jest zgodna z binarną, jeśli aplikacja, która jest zależna od starej wersji, może, bez ponownej kompilacji, działała z nową wersją.

Poniżej przedstawiono kilka kwestii, które należy wziąć pod uwagę podczas próby utrzymania zgodności z poprzednimi wersjami w przypadku starszych wersji biblioteki:

- Metody wirtualne: w przypadku wybrania w nowej wersji metody wirtualnej, która nie jest wirtualna, oznacza to, że projekty, które przesłaniają tę metodę, będą musiały zostać zaktualizowane. Jest to ogromna istotna zmiana i zdecydowanie odradza się.
- Sygnatury metod: w przypadku aktualizowania zachowania metody wymaga również zmiany jego podpisu, dlatego należy utworzyć Przeciążenie, aby kod wywołujący do tej metody nadal działał.
Zawsze możesz manipulować starym podpisem metody, aby wywołać nową metodę sygnatury, tak aby implementacja była spójna.
- [Przestarzały atrybut](programming-guide/concepts/attributes/common-attributes.md#Obsolete): można użyć tego atrybutu w kodzie, aby określić klasy lub członków klasy, które są przestarzałe i które mogą zostać usunięte w przyszłych wersjach. Dzięki temu deweloperzy korzystający z biblioteki są lepiej przygotowani do istotnych zmian.
- Argumenty metody opcjonalnej: po wprowadzeniu poprzednio opcjonalne argumenty metody obowiązkowo lub zmiany wartości domyślnej, cały kod, który nie dostarcza tych argumentów, będzie musiał zostać zaktualizowany.

> [!NOTE]
> Obowiązkowe argumenty opcjonalne powinny mieć bardzo niewielki wpływ, zwłaszcza jeśli nie zmieni zachowanie metody.

Dzięki temu użytkownicy będą mogli uaktualnić do nowej wersji biblioteki, im większa jest możliwość ich uaktualnienia.

### <a name="application-configuration-file"></a>Plik konfiguracji aplikacji

Deweloperem platformy .NET jest bardzo wysoka szansa [, że plik `app.config`](../framework/configure-apps/file-schema/index.md) występuje w większości typów projektów.
Ten prosty plik konfiguracji może być długim sposobem ulepszania wdrażania nowych aktualizacji. Zazwyczaj należy zaprojektować biblioteki w taki sposób, że informacje, które prawdopodobnie zmieniają się regularnie, są przechowywane w pliku `app.config`, w ten sposób, gdy takie informacje zostaną zaktualizowane, plik konfiguracyjny starszych wersji musi zostać zastąpiony nowym, bez konieczności ponownej kompilacji biblioteki.

## <a name="consuming-libraries"></a>Używanie bibliotek

Deweloperzy korzystający z bibliotek .NET zbudowanych przez innych deweloperów najprawdopodobniej wiedzą, że nowa wersja biblioteki może nie być w pełni zgodna z projektem i często można sprawdzić, czy trzeba zaktualizować swój kod, aby pracować z tymi zmianami.

Cieszymy dla Ciebie, C# a ekosystem .NET obejmuje funkcje i techniki, które umożliwiają łatwe aktualizowanie naszej aplikacji do pracy z nowymi wersjami bibliotek, które mogą spowodować istotne zmiany.

### <a name="assembly-binding-redirection"></a>Przekierowanie powiązania zestawu

Plik *App. config* służy do aktualizowania wersji biblioteki używanej przez aplikację. Dodając jak nazywa się [*przekierowanie powiązania*](../framework/configure-apps/redirect-assembly-versions.md), możesz użyć nowej wersji biblioteki bez konieczności ponownego kompilowania aplikacji. W poniższym przykładzie pokazano, jak zaktualizować plik *App. config* aplikacji, tak aby używał `1.0.1` wersji poprawki `ReferencedLibrary` zamiast `1.0.0` wersji, w której został on pierwotnie skompilowany.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Ta metoda będzie działała tylko wtedy, gdy nowa wersja `ReferencedLibrary` jest binarna zgodna z Twoją aplikacją.
> W sekcji [zgodność z poprzednimi wersjami](#backwards-compatibility) powyżej znajdziesz zmiany, które należy wyszukać podczas określania zgodności.

### <a name="new"></a>new

Używasz modyfikatora `new`, aby ukryć dziedziczone elementy członkowskie klasy bazowej. Jest to jeden ze sposobów, w jaki klasy pochodne mogą odpowiadać na aktualizacje w klasach bazowych.

Wykonaj następujące czynności:

[!code-csharp[Sample usage of the 'new' modifier](~/samples/snippets/csharp/versioning/new/Program.cs#sample)]

**Dane wyjściowe**

```console
A base method
A derived method
```

Z powyższego przykładu można zobaczyć, jak `DerivedClass` ukrywa metodę `MyMethod` obecną w `BaseClass`.
Oznacza to, że gdy klasa bazowa w nowej wersji biblioteki dodaje element członkowski, który już istnieje w klasie pochodnej, można po prostu użyć modyfikatora `new` w składowej klasy pochodnej, aby ukryć element członkowski klasy bazowej.

Gdy nie jest określony modyfikator `new`, Klasa pochodna domyślnie ukrywa elementy członkowskie powodujące konflikt w klasie bazowej, mimo że zostanie wygenerowane Ostrzeżenie kompilatora, kod nadal zostanie skompilowany. Oznacza to, że po prostu dodanie nowych elementów członkowskich do istniejącej klasy powoduje, że nowa wersja biblioteki jest zgodna z kodem, który od niego zależy.

### <a name="override"></a>zastąpienie

Modyfikator `override` oznacza, że implementacja pochodna rozszerza implementację składowej klasy bazowej, a nie ukrywa ją. Element członkowski klasy bazowej musi mieć zastosowany modyfikator `virtual`.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/snippets/csharp/versioning/override/Program.cs#sample)]

**Dane wyjściowe**

```console
Base Method One: Method One
Derived Method One: Derived Method One
```

Modyfikator `override` jest oceniany w czasie kompilacji, a kompilator zgłosi błąd, jeśli nie znajdzie wirtualnego elementu członkowskiego do przesłonięcia.

Wiedza o omawianych technikach i zrozumieniu sytuacji, w których można z nich korzystać, będzie mieć na celu szybkie przechodzenie między wersjami biblioteki.
