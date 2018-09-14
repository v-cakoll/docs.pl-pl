---
title: C# Versioning — Przewodnik po języku C#
description: Zrozumienie sposobu działania przechowywanie wersji w języku C# i .NET
ms.date: 01/08/2017
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 949b7414116169cada62b48392f37809f26d7ff9
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45597748"
---
# <a name="versioning-in-c"></a>Przechowywanie wersji w języku C# #

W tym samouczku dowiesz się, jakie versioning oznacza, że na platformie .NET. Poznasz również czynniki do rozważenia podczas przechowywania wersji biblioteki, a także uaktualnienie do nowej wersji biblioteki.

## <a name="authoring-libraries"></a>Tworzenie bibliotek

Jako deweloper, który został utworzony z bibliotekami .NET do użytku publicznego, udało Ci się najbardziej prawdopodobnie zostały w sytuacjach, w którym trzeba wdrożyć nowe aktualizacje. Jak obniżyć o tym procesie ma znaczenie dużo, jak należy się upewnić, że jest bezproblemowe przejście z istniejącego kodu do nowej wersji biblioteki. Poniżej przedstawiono kilka kwestii, które należy wziąć pod uwagę podczas tworzenia nowej wersji:

### <a name="semantic-versioning"></a>Semantic Versioning

[Przechowywanie wersji semantycznej](http://semver.org/) (SemVer w skrócie) jest konwencję nazewnictwa, stosowany do wersji biblioteki oznaczającego punktów kontrolnych określonych zdarzeń.
Najlepiej, jeśli informacje o wersji, które zapewniają biblioteki powinny pomóc deweloperom Określanie zgodności z projektami, które korzystają z starsze wersje tego takie same biblioteki.

Format składnika 3 jest najbardziej podstawowym sposobem SemVer `MAJOR.MINOR.PATCH`, gdzie:

* `MAJOR` jest zwiększany po wprowadzeniu zmian niezgodnych interfejsów API
* `MINOR` jest zwiększany po dodaniu funkcji w sposób zgodny wstecz
* `PATCH` jest zwiększany po wprowadzeniu poprawki wstecznie zgodny

Istnieją również sposoby, aby określić inne scenariusze, takie jak wersje wstępne itp., stosując informacje o wersji do biblioteki programu .NET.

### <a name="backwards-compatibility"></a>Wstecznej zgodności

Jak zwolnieniu nowe wersje biblioteki wstecznej zgodności z poprzednimi wersjami najprawdopodobniej będzie jedną z głównych problemów.
Nową wersję biblioteki jest zgodna z poprzednią wersją kod, który jest zależny od poprzedniej wersji można gdy kompilowany ponownie, pracować z nową wersją źródłowego. Nową wersję biblioteki jest zgodny z binarnego, aplikacja, która była uzależniona od starej wersji bez ponownej kompilacji, pracy z nową wersją.

Oto kilka rzeczy, które należy uwzględnić podczas próby utrzymania wstecznej zgodności z poprzednimi wersjami biblioteki:

* Metody wirtualne: po ustawieniu metodę wirtualną niewirtualną w nowej wersji oznacza, że projekty, które zastępują tej metody do zaktualizowania. To jest ogromna istotnej zmiany i jest zdecydowanie odradzane.
* Podpisy metod: podczas aktualizowania zachowanie metody wymaga zmień jej sygnaturę tak dobrze, należy zamiast tego utworzyć przeciążenia tak, aby kod wywoływanie tej metody będą nadal działać.
Zawsze możesz manipulować stary podpis metody do wywołania w podpisie metody nowy, aby implementacji pozostanie spójna.
* [Atrybut przestarzałe](programming-guide/concepts/attributes/common-attributes.md#Obsolete): w kodzie można użyć tego atrybutu, aby określić klas lub składowych klasy, które są przestarzałe i może być usunięte w przyszłych wersjach.
Dzięki temu deweloperzy przy użyciu biblioteki lepiej są przygotowywane na temat przełomowych zmian.
* Argumenty opcjonalne. metoda: Po wprowadzić obowiązkowe argumenty metody wcześniej opcjonalne lub zmienić ich wartości domyślne, a następnie cały kod, który nie dostarcza tych argumentów należy do zaktualizowania.
> [!NOTE]
> Tworzenie obowiązkowe Argumenty opcjonalne powinny mieć bardzo niewielkim stopniu wpływa, zwłaszcza, jeśli go nie zmienia zachowanie metody.

Łatwiejsze wprowadzeniu go dla użytkowników uaktualnić do nowej wersji biblioteki, tym bardziej prawdopodobne, ich uaktualni wcześniej.

### <a name="application-configuration-file"></a>Plik konfiguracji aplikacji

Jako deweloper platformy .NET, istnieje wysokie prawdopodobieństwo, napotkanych wcześniej [ `app.config` pliku](../framework/configure-apps/file-schema/index.md) obecne w większości typów projektów.
Ten plik prostej konfiguracji można długą drogę do poprawy wprowadzania nowych aktualizacji. Ogólnie należy projektować bibliotek w taki sposób, że informacje, która prawdopodobnie się regularnie zmieniane są przechowywane w `app.config` plików dzięki temu po zaktualizowaniu tych informacji w pliku config starszych wersji po prostu musi zostać zastąpiony nowym plikiem bez konieczności ponownej kompilacji biblioteki.

## <a name="consuming-libraries"></a>Korzystanie z biblioteki

Jako deweloper, który wykorzystuje bibliotek .NET, utworzone przez innych programistów jest najprawdopodobniej pamiętać, że nowa wersja biblioteki może nie być w pełni zgodne z projektem i często może znaleźć się konieczności aktualizowania kodu do pracy z tymi zmianami.

Szczęście dla Ciebie języka C# i ekosystemu .NET jest powiązana z funkcji i technik, które pozwalają łatwo aktualizować naszej aplikacji do pracy z nowe wersje bibliotek, które może powodować przełomowe zmiany.

### <a name="assembly-binding-redirection"></a>Przekierowanie powiązań zestawów

Możesz użyć `app.config` plik, aby zaktualizować wersję biblioteki używany przez aplikację. Dodając tak zwany [ *przekierowanie powiązania* ](../framework/configure-apps/redirect-assembly-versions.md) usługi można użyć nowej wersji biblioteki, bez konieczności ponownego kompilowania aplikacji. W poniższym przykładzie pokazano, jak należy zaktualizować aplikacji `app.config` plik do użycia `1.0.1` wersję poprawki `ReferencedLibrary` zamiast `1.0.0` pierwotnie został skompilowany przy użyciu wersji.

```xml
<dependentAssembly>
    <assemblyIdentity name="ReferencedLibrary" publicKeyToken="32ab4ba45e0a69a1" culture="en-us" />
    <bindingRedirect oldVersion="1.0.0" newVersion="1.0.1" />
</dependentAssembly>
```

> [!NOTE]
> Ta metoda będzie działać tylko, jeśli nowa wersja `ReferencedLibrary` jest binarny zgodny z aplikacją.
> Zobacz [zgodności z poprzednimi wersjami](#backwards-compatibility) Powyższa sekcja zmian do wyszukania podczas określania zgodności.

### <a name="new"></a>new

Możesz użyć `new` modyfikator, aby ukryć dziedziczone elementy członkowskie klasy bazowej. Jest to jeden sposób pochodne mogą odpowiadać na aktualizacje w klasach bazowych.

Wykonaj poniższy przykład:

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

**Output**

```
A base method
A derived method
```

W powyższym przykładzie widać, jak `DerivedClass` ukrywa `MyMethod` metoda obecne w `BaseClass`.
Oznacza to, że gdy klasę bazową w nowej wersji biblioteki dodaje element członkowski, który już istnieje w klasie pochodnej, można użyć `new` modyfikator w swojej składowej klasy pochodnej spowoduje ukrycie składowej klasy bazowej.

Gdy nie `new` modyfikator jest określony, klasę pochodną będzie domyślnie Ukryj członków powodujące konflikt w klasie bazowej, mimo że ostrzeżenia kompilatora, który zostanie wygenerowany kod zostanie skompilowany nadal. Oznacza to, że dodanie nowych elementów członkowskich do istniejącej klasy sprawia, że nowej wersji biblioteki pliku źródłowym, jak i plik binarny jest zgodny z kodem, który zależy od niego.

### <a name="override"></a>override

`override` Modyfikator oznacza, że implementacja pochodnej rozszerza implementację składowej klasy bazowej, a nie ukrywa go. Składowej klasy bazowej, musi mieć `virtual` modyfikator stosowane do niego.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

**Output**

```
Base Method One: Method One
Derived Method One: Derived Method One
```

`override` Modyfikator jest obliczane w czasie kompilacji i kompilator będzie sygnalizować błąd, jeśli nie znajdzie wirtualna elementu członkowskiego do zastąpienia.

Swojej wiedzy na temat technik opisano, jak również zrozumieć, jakie sytuacjach, aby umożliwić ich używanie będzie długą drogę do poprawienia łatwości przejścia między wersjami biblioteki.
