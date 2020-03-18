---
title: Przechowywanie wersji i biblioteki .NET
description: Najlepsze zalecenia dotyczące wersji bibliotek .NET.
ms.date: 12/10/2018
ms.openlocfilehash: a274410714791e2790da0e3deb2a595390ee9389
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400401"
---
# <a name="versioning"></a>Obsługa wersji

Biblioteka oprogramowania jest rzadko kompletna w wersji 1.0. Dobre biblioteki ewoluują wraz z uchwycone, dodając funkcje, naprawiając błędy i poprawiając wydajność. Ważne jest, aby można było zwolnić nowe wersje biblioteki .NET, zapewniając dodatkową wartość dla każdej wersji, bez przerywania istniejących użytkowników.

## <a name="breaking-changes"></a>Zmiany powodujące niezgodność

Aby uzyskać informacje dotyczące obsługi zmian krytycznych między wersjami, zobacz [Zmiany dotyczące podziału](./breaking-changes.md).

## <a name="version-numbers"></a>Numery wersji

Biblioteka .NET ma wiele sposobów określania wersji. Te wersje są najważniejsze:

### <a name="nuget-package-version"></a>Wersja pakietu NuGet

[Wersja pakietu NuGet](/nuget/reference/package-versioning) jest wyświetlany na NuGet.org, Visual Studio NuGet menedżera pakietów i jest dodawany do kodu źródłowego, gdy pakiet jest używany. Wersja pakietu NuGet jest numer wersji, który użytkownicy będą powszechnie widzieć i będą się do niego odwoływać, gdy mówią o wersji biblioteki, z których korzystają. Wersja pakietu NuGet jest używana przez NuGet i nie ma wpływu na zachowanie w czasie wykonywania.

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

Identyfikator pakietu NuGet w połączeniu z wersją pakietu NuGet służy do identyfikowania pakietu w NuGet. Na przykład `Newtonsoft.Json` + `11.0.2`. Pakiet z sufiksem jest pakietem w wersji wstępnej i ma specjalne zachowanie, które sprawia, że jest idealny do testowania. Aby uzyskać więcej informacji, zobacz [Pakiety wersji wstępnej](./nuget.md#pre-release-packages).

Ponieważ wersja pakietu NuGet jest najbardziej widoczną wersją dla deweloperów, warto zaktualizować ją za pomocą [wersji semantycznej (SemVer).](https://semver.org/) SemVer wskazuje znaczenie zmian między wydaniem i pomaga deweloperom podjąć świadomą decyzję przy wyborze wersji do użycia. Na przykład przechodzenie od `1.0` do `2.0` wskazuje, że istnieją potencjalnie przełomowe zmiany.

✔️ ZASTANÓW SIĘ przy użyciu [SemVer 2.0.0](https://semver.org/) do wersji pakietu NuGet.

✔️ używać wersji pakietu NuGet w dokumentacji publicznej, ponieważ jest to numer wersji, który użytkownicy będą często widzieć.

✔️ DO zawierają sufiks w wersji wstępnej podczas zwalniania niestabilnego pakietu.

> Użytkownicy muszą zdecydować się na uzyskiwanie pakietów w wersji wstępnej, więc zrozumieją, że pakiet nie został ukończony.

### <a name="assembly-version"></a>Wersja zestawu

Wersja zestawu jest to, co CLR używa w czasie wykonywania, aby wybrać, która wersja zestawu do załadowania. Wybranie złożenia przy użyciu wersji dotyczy tylko zestawów o silnej nazwie.

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

Windows .NET Framework CLR wymaga dokładnego dopasowania, aby załadować silny nazwany zestaw. Na przykład `Libary1, Version=1.0.0.0` został skompilowany `Newtonsoft.Json, Version=11.0.0.0`z odniesieniem do . Program .NET Framework załaduje `11.0.0.0`tylko tę dokładną wersję . Aby załadować inną wersję w czasie wykonywania, przekierowanie powiązania należy dodać do pliku konfiguracyjnego aplikacji .NET.

Silne nazewnictwo w połączeniu z wersją złożenia umożliwia [ładowanie wersji zestawu ścisłego.](../assembly/versioning.md) Podczas silnego nazewnictwa biblioteki ma wiele zalet, często powoduje wyjątki w czasie wykonywania, że zestaw `app.config` / `web.config` nie można odnaleźć i [wymaga powiązań przekierowuje](../../framework/configure-apps/redirect-assembly-versions.md) w zostać naprawione. Ładowanie zestawu .NET Core zostało złagodzone, a środowisko CLR .NET Core automatycznie załaduje zestawy w czasie wykonywania z wyższą wersją.

✔️ NALEŻY WZIĄĆ tylko w tym wersji głównej w AssemblyVersion.

> na przykład Biblioteka 1.0 i Biblioteka 1.0.1 mają `1.0.0.0`AssemblyVersion , podczas gdy `2.0.0.0`Biblioteka 2.0 ma AssemblyVersion . Gdy wersja zestawu zmienia się rzadziej, zmniejsza redirects powiązania.

✔️ NALEŻY ROZWAŻYĆ przechowywanie numer wersji głównej AssemblyVersion i nuget wersji pakietu w synchronizacji.

> AssemblyVersion znajduje się w niektórych komunikatów informacyjnych wyświetlanych użytkownikowi, na przykład nazwy zestawu i zestawu kwalifikowanych nazw typów w komunikatach o wyjątkach. Utrzymywanie relacji między wersjami zapewnia deweloperom więcej informacji o używanej wersji.

❌NIE mają stałej AssemblyVersion.

> Podczas gdy niezmienna AssemblyVersion unika konieczności powiązań przekierowuje, oznacza to, że tylko jedna wersja zestawu może być zainstalowany w globalnej pamięci podręcznej zestawów (GAC). Ponadto aplikacje, które odwołują się do zestawu w GAC zostanie przerwana, jeśli inna aplikacja aktualizuje zestaw GAC z łamania zmian.

### <a name="assembly-file-version"></a>Wersja pliku zestawu

Wersja pliku zestawu służy do wyświetlania wersji pliku w systemie Windows i nie ma wpływu na zachowanie środowiska uruchomieniowego. Ustawienie tej wersji jest opcjonalne. Jest on widoczny w oknie dialogowym Właściwości pliku w Eksploratorze Windows:

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

![Eksplorator Windows](./media/versioning/win-properties.png "Eksplorator Windows")

✔️ ZAStanów się, w tym numer kompilacji ciągłej integracji jako AssemblyFileVersion wersji.

> Na przykład tworzysz wersję 1.0.0 projektu, a numer kompilacji ciągłej integracji wynosi 99, więc plik FileVersion jest 1.0.0.99.

✔️ używać formatu `Major.Minor.Build.Revision` dla wersji pliku.

> Podczas gdy wersja pliku nigdy nie jest używana przez .NET, [system Windows oczekuje, że wersja pliku](/windows/desktop/menurc/versioninfo-resource) będzie w `Major.Minor.Build.Revision` formacie. Ostrzeżenie jest wywoływane, jeśli wersja nie jest zgodna z tym formatem.

### <a name="assembly-informational-version"></a>Wersja informacyjna zestawu

Wersja informacyjna zestawu służy do rejestrowania dodatkowych informacji o wersji i nie ma wpływu na zachowanie w czasie wykonywania. Ustawienie tej wersji jest opcjonalne. Jeśli używasz source link, ta wersja zostanie ustawiona na kompilacji z nuget wersji pakietu oraz wersji kontroli źródła. Na przykład `1.0.0-beta1+204ff0a` zawiera skrót zatwierdzania kodu źródłowego, z którego został utworzony zestaw. Aby uzyskać więcej informacji, zobacz [Łącze źródłowe](./sourcelink.md).

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> Starsze wersje programu Visual Studio podnieść ostrzeżenie kompilacji, `Major.Minor.Build.Revision`jeśli ta wersja nie jest zgodna z formatem . Ostrzeżenie można bezpiecznie zignorować.

❌UNIKAJ samodzielnego ustawiania wersji informacyjnej zestawu.

> Zezwalaj sourcelink automatycznie generować wersję zawierającą NuGet i metadanych kontroli źródła.

>[!div class="step-by-step"]
>[Poprzedni](publish-nuget-package.md)
>[następny](breaking-changes.md)
