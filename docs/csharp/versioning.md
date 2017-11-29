---
title: "C# Versioning — przewodnik C#"
description: "Zrozumieć sposób działania kontroli wersji w języku C# i .NET"
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.date: 01/08/2017
ms.topic: article
ms.prod: visual-studio-dev-14
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: aa8732d7-5cd0-46e1-994a-78017f20d861
ms.openlocfilehash: 0b671333019c00abafcfb72533e30936f8fc6ad7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="versioning-in-c"></a>Przechowywanie wersji w języku C# #

W tym samouczku nauczysz się, jakie versioning oznacza, że w środowisku .NET. Dowiesz się czynniki do rozważenia podczas przechowywania wersji biblioteki, a także uaktualnienie do nowej wersji biblioteki.

## <a name="authoring-libraries"></a>Tworzenie bibliotek

Deweloperzy tworzący bibliotek .NET do użytku publicznego udało Ci się najbardziej prawdopodobnie zostały w sytuacjach, w których konieczne wdrażanie nowych aktualizacji. Jak przejść na ten tego procesu ma znaczenie dużo, jak należy się upewnić, że jest płynne przejście z istniejącego kodu do nowej wersji biblioteki. Oto kilka kwestii, które należy wziąć pod uwagę podczas tworzenia nowej wersji:

### <a name="semantic-versioning"></a>Wersjonowania semantycznego

[Wersjonowania semantycznego](http://semver.org/) (programu SemVer skrócie) jest Konwencja nazewnictwa stosowana do wersji biblioteki oznaczającego zdarzenia określonego punktu kontrolnego.
Najlepiej, jeśli informacje o wersji, nadaj biblioteki powinny pomóc deweloperom określania zgodności z projektami korzystające z starsze wersje tego same biblioteki.

Najprostsze podejście do programu SemVer jest w formacie 3 składnika `MAJOR.MINOR.PATCH`, gdzie:
 
* `MAJOR`jest zwiększany po wprowadzeniu zmian interfejsu API niezgodne
* `MINOR`jest zwiększany po dodaniu funkcji w sposób zgodny wstecz
* `PATCH`jest zwiększany po wprowadzeniu wstecznie zgodna poprawki błędów

Istnieją również sposobów, aby określić inne scenariusze, takie jak wersje wstępne itp., stosując informacje o wersji do biblioteki programu .NET.

### <a name="backwards-compatibility"></a>Zapewnienia zgodności

Jak zwolnić nowych wersji biblioteki, Wstecz zgodność z poprzednimi wersjami najprawdopodobniej będzie jedną z głównych problemów.
Nowa wersja biblioteki jest zgodny z poprzedniej wersji kodu, który jest zależny od poprzedniej wersji gdy ponownie skompilowana, pracy z nową wersję źródła. Nowa wersja biblioteki jest zgodny z binarnego, jeśli aplikację, która była uzależniona od starej wersji bez ponownej kompilacji, pracować z nowej wersji.

Poniżej przedstawiono niektóre czynności, które należy uwzględnić podczas próby Obsługa zapewnienia zgodności z poprzednimi wersjami biblioteki:

* Metody wirtualne: podczas wprowadzania metody wirtualnej Niewirtualny w nowej wersji oznacza to, że projekty, które zastępują tej metody do zaktualizowania. To jest duży istotnej zmiany i jest zalecane.
* Metoda podpisów: Jeśli aktualizowanie zachowania — metoda wymaga zmiany jego sygnatura również, należy zamiast tego utworzyć przeciążenia tak, aby kod wywoływanie metody będą nadal działać.
Zawsze można manipulować starego podpis metody do wywołania do nowego podpisu metody, aby implementacji pozostaje spójna.
* [Atrybut przestarzałe](programming-guide/concepts/attributes/common-attributes.md#Obsolete): w kodzie można użyć tego atrybutu, aby określić klasy lub elementów członkowskich klasy, które zostały uznane za przestarzałe i może być usunięte w przyszłych wersjach.
Dzięki temu deweloperzy przy użyciu biblioteki są lepiej przygotowane pod kątem fundamentalne zmiany.
* Argumenty opcjonalne metody: Podczas wprowadzania metody wcześniej opcjonalne argumenty obowiązkowe lub zmienić ich wartości domyślne, a następnie całego kodu, który nie dostarcza tych argumentów będzie muszą zostać zaktualizowane.
> [!NOTE]
> Tworzenie obowiązkowego Argumenty opcjonalne powinien mieć bardzo mały wpływ, zwłaszcza, jeśli nie zmienia zachowanie metody.

Łatwiej można ustawić dla użytkowników, aby uaktualnić do nowej wersji biblioteki, tym bardziej prawdopodobne one uaktualni wcześniej.

### <a name="application-configuration-file"></a>Plik konfiguracji aplikacji

Projektant .NET istnieje bardzo duże ryzyko został napotkany [ `app.config` pliku](https://msdn.microsoft.com/en-us/library/1fk1t1t0(v=vs.110).aspx) w większości typów projektów.
Ten plik prostą konfigurację można zdecydowanie do poprawy wdrażanie nowych aktualizacji. Ogólnie należy projektować w bibliotekach w taki sposób, że mogą się zmieniać regularnie informacje są przechowywane w `app.config` pliku w ten sposób po zaktualizowaniu tych informacji w pliku config starszych wersji musi być zastąpiony nowym bez konieczności ponownej kompilacji biblioteki.

## <a name="consuming-libraries"></a>Korzystanie z biblioteki

Deweloper, który wykorzystuje utworzony przez innych bibliotek .NET jest najprawdopodobniej pamiętać, że nowa wersja biblioteki nie może być całkowicie zgodne z projektem i często może okaże się, że konieczności zaktualizuj kod do pracy z tymi zmianami.

Szczęście dla Ciebie C# i ekosystemem .NET zawiera funkcje i techniki, które umożliwiają łatwe aktualizacji aplikacji do pracy z nowe wersje bibliotek, które może powodować istotne zmiany.

### <a name="assembly-binding-redirection"></a>Przekierowanie powiązań zestawów

Można użyć `app.config` plik, aby zaktualizować wersję biblioteki używany przez aplikację. Dodając tak zwany [ *przekierowania powiązania* ](https://msdn.microsoft.com/en-us/library/7wd6ex19(v=vs.110).aspx) Twojego można korzystać z nowych wersji biblioteki bez konieczności ponownego kompilowania aplikacji. W poniższym przykładzie pokazano, jak będzie aktualizował aplikacji `app.config` plik `1.0.1` wersja poprawki `ReferencedLibrary` zamiast `1.0.0` pierwotnie został skompilowany z wersji.

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

Możesz użyć `new` modyfikator, aby ukryć dziedziczone elementy członkowskie klasy podstawowej. Jest to jeden sposób pochodne mogą odpowiadać na aktualizacje w klasach podstawowych.

Wykonaj poniższy przykład:

[!code-csharp[Sample usage of the 'new' modifier](../../samples/csharp/versioning/new/Program.cs#sample)]

**Dane wyjściowe**

```
A base method
A derived method
```

W powyższym przykładzie widać, jak `DerivedClass` ukrywa `MyMethod` metody w `BaseClass`.
Oznacza to, że gdy klasy podstawowej w nowej wersji biblioteki dodaje elementu członkowskiego, który już istnieje w klasie pochodnej, możesz użyć `new` modyfikator użytkownika elementu członkowskiego klasy pochodnej, aby ukryć element członkowski klasy podstawowej.

Gdy nie `new` modyfikator jest określony, klasa pochodna domyślnie ukrywa powodujące konflikt elementów członkowskich w klasie podstawowej, chociaż zostaną wygenerowane ostrzeżenie kompilatora nadal kompilacji kodu. Oznacza to, że po prostu dodanie nowych elementów członkowskich do istniejącej klasy sprawia, że nowej wersji biblioteki źródłowym i danych binarnych jest zgodny z kodem, która zależy od niego.

### <a name="override"></a>override

`override` Modyfikator oznacza pochodnej implementacji rozszerza implementacja elementu członkowskiego klasy podstawowej, a nie ukrywa go. Element członkowski klasy podstawowej musi mieć `virtual` modyfikator zastosować dla niego.

[!code-csharp[Sample usage of the 'override' modifier](../../samples/csharp/versioning/override/Program.cs#sample)]

**Dane wyjściowe**

```
Base Method One: Method One
Derived Method One: Derived Method One
```

`override` Modyfikator jest obliczane w czasie kompilacji i kompilator zgłosi błąd, jeśli nie znajdzie członka wirtualnego do zastąpienia.

Swoją wiedzę techniki opisano, jak również zrozumienie z jakich sytuacjach do korzystania z nich będzie zdecydowanie do zwiększania łatwość przejścia między wersjami biblioteki.
