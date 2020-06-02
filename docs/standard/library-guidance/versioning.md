---
title: Przechowywanie wersji i biblioteki .NET
description: Zalecenia dotyczące zgodności z wersjami bibliotek platformy .NET.
ms.date: 12/10/2018
ms.openlocfilehash: ab15d56e40abedd842b681496b9e5ee737c8b1cd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290126"
---
# <a name="versioning"></a>Przechowywanie wersji

Biblioteka oprogramowania jest rzadko kompletna w wersji 1,0. Dobre biblioteki są rozwijane wraz z upływem czasu, dodawaniem funkcji, naprawianie usterek i Poprawianie wydajności. Ważne jest, aby można było wydać nowe wersje biblioteki .NET, zapewniając dodatkową wartość w każdej wersji, bez przerywania istniejących użytkowników.

## <a name="breaking-changes"></a>Zmiany powodujące niezgodność

Aby uzyskać informacje na temat obsługi istotnych zmian między wersjami, zobacz artykuł dotyczący [zmiany](./breaking-changes.md).

## <a name="version-numbers"></a>Numery wersji

Biblioteka .NET ma wiele sposobów na określenie wersji. Te wersje są najważniejsze:

### <a name="nuget-package-version"></a>Wersja pakietu NuGet

[Wersja pakietu NuGet](/nuget/reference/package-versioning) jest wyświetlana w NuGet.org, menedżerze pakietów NuGet programu Visual Studio i jest dodawana do kodu źródłowego, gdy używany jest pakiet. Wersja pakietu NuGet to numer wersji, który użytkownicy często zobaczą, i odwołują się do niego podczas rozmowy o wersji biblioteki, z której korzystają. Wersja pakietu NuGet jest używana przez program NuGet i nie ma wpływu na zachowanie w czasie wykonywania.

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

Identyfikator pakietu NuGet połączony z wersją pakietu NuGet jest używany do identyfikowania pakietu w pakiecie NuGet. Na przykład `Newtonsoft.Json` + `11.0.2`. Pakiet z sufiksem jest pakietem wersji wstępnej i ma specjalne zachowanie, które sprawia, że jest idealnym rozwiązaniem do testowania. Aby uzyskać więcej informacji, zobacz [pakiety wersji wstępnej](./nuget.md#pre-release-packages).

Ponieważ wersja pakietu NuGet jest najbardziej widoczną wersją dla deweloperów, dobrym pomysłem jest zaktualizowanie go przy użyciu [wersji semantycznej (SemVer)](https://semver.org/). SemVer wskazuje istotność zmian między wydaniem i pomaga deweloperom podejmować świadome decyzje podczas wybierania używanej wersji. Na przykład przechodzenie z `1.0` do `2.0` wskazuje, że istnieją potencjalne zmiany.

✔️ ROZWAŻYĆ użycie programu [SemVer 2.0.0](https://semver.org/) w celu uzyskania wersji pakietu NuGet.

✔️ używać wersji pakietu NuGet w publicznej dokumentacji, ponieważ jest to numer wersji, który użytkownicy często zobaczą.

✔️ uwzględnić sufiks wstępnej wersji podczas zwalniania niestabilnego pakietu.

> Użytkownicy muszą wyrazić zgodę na pobranie pakietów w wersji wstępnej, aby zrozumieć, że pakiet nie został ukończony.

### <a name="assembly-version"></a>Wersja zestawu

Wersja zestawu jest używany przez środowisko CLR w czasie wykonywania, aby wybrać wersję zestawu do załadowania. Wybór zestawu przy użyciu wersji ma zastosowanie tylko do zestawów o silnej nazwie.

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

.NET Framework CLR wymaga dokładnego dopasowania do załadowania zestawu o silnej nazwie. Na przykład, `Libary1, Version=1.0.0.0` został skompilowany z odwołaniem do `Newtonsoft.Json, Version=11.0.0.0` . .NET Framework spowoduje załadowanie tylko dokładnej wersji `11.0.0.0` . Aby załadować inną wersję w czasie wykonywania, należy dodać przekierowanie powiązania do pliku konfiguracji aplikacji platformy .NET.

Silne nazewnictwo połączone z wersją zestawu umożliwia [ścisłe ładowanie wersji zestawu](../assembly/versioning.md). Chociaż silne nazewnictwo biblioteki ma wiele korzyści, często wynika to z wyjątków czasu wykonywania, których nie można znaleźć, i [wymaga nawiązania powiązań](../../framework/configure-apps/redirect-assembly-versions.md) w `app.config` lub w `web.config` celu naprawienia. W programie .NET Core ładowanie zestawu jest bardziej swobodne. Środowisko uruchomieniowe platformy .NET Core automatycznie ładuje zestawy o wyższej wersji w czasie wykonywania.

✔️ ROZWAŻYĆ tylko wersję główną w AssemblyVersion.

> na przykład biblioteka 1,0 i Biblioteka 1.0.1 mają AssemblyVersion `1.0.0.0` , natomiast biblioteka 2,0 ma AssemblyVersion `2.0.0.0` . Gdy wersja zestawu zmienia się rzadziej, zmniejsza przekierowania powiązań.

✔️ ROZWAŻYĆ utrzymywanie głównego numeru wersji AssemblyVersion i wersji pakietu NuGet w synchronizacji.

> AssemblyVersion jest dołączany do niektórych komunikatów informacyjnych wyświetlanych użytkownikowi, np. Nazwa zestawu i nazwy typów kwalifikowana zestawu w komunikatach o wyjątku. Utrzymywanie relacji między wersjami zapewnia deweloperom więcej informacji na temat używanej wersji.

❌NIE mają stałego AssemblyVersion.

> Podczas gdy AssemblyVersion nie zmienia się potrzeba przekierowania powiązań, oznacza to, że tylko jedna wersja zestawu może być zainstalowana w globalnej pamięci podręcznej zestawów (GAC). Ponadto aplikacje odwołujące się do zestawu w pamięci podręcznej GAC zostaną przerwane, jeśli inna aplikacja zaktualizuje zestaw GAC przy użyciu istotnych zmian.

### <a name="assembly-file-version"></a>Wersja pliku zestawu

Wersja pliku zestawu jest używana do wyświetlania wersji pliku w systemie Windows i nie ma wpływu na zachowanie w czasie wykonywania. Ustawienie tej wersji jest opcjonalne. Jest on widoczny w oknie dialogowym właściwości pliku w Eksploratorze Windows:

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

![Eksplorator Windows](./media/versioning/win-properties.png "Eksplorator Windows")

✔️ ROZWAŻYĆ uwzględnienie numeru kompilacji ciągłej integracji jako poprawki AssemblyFileVersion.

> Załóżmy na przykład, że tworzysz wersję 1.0.0 projektu, a numer kompilacji ciągłej integracji to 99, a AssemblyFileVersion to 1.0.0.99.

✔️ użyć formatu `Major.Minor.Build.Revision` wersja pliku.

> Mimo że wersja pliku nigdy nie jest używana przez platformę .NET, [system Windows oczekuje, że wersja pliku](/windows/desktop/menurc/versioninfo-resource) jest w `Major.Minor.Build.Revision` formacie. Ostrzeżenie jest zgłaszane, jeśli wersja nie jest zgodna z tym formatem.

### <a name="assembly-informational-version"></a>Informacje o wersji zestawu

Informacje o wersji zestawu są używane do rejestrowania dodatkowych informacji o wersji i nie mają wpływu na zachowanie w czasie wykonywania. Ustawienie tej wersji jest opcjonalne. Jeśli używasz linku źródłowego, ta wersja zostanie ustawiona na kompilację z wersją pakietu NuGet i wersją kontroli źródła. Na przykład `1.0.0-beta1+204ff0a` zawiera skrót zatwierdzenia kodu źródłowego, z którego został skompilowany zestaw. Aby uzyskać więcej informacji, zobacz [link źródłowy](./sourcelink.md).

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> Starsze wersje programu Visual Studio zgłaszają ostrzeżenie kompilacji, jeśli ta wersja nie jest zgodna z formatem `Major.Minor.Build.Revision` . Ostrzeżenie można bezpiecznie zignorować.

❌Należy unikać samodzielnego ustawiania wersji informacyjnej zestawu.

> Zezwól programowi SourceLink na automatyczne generowanie wersji zawierającej metadane narzędzia NuGet i kontroli źródła.

>[!div class="step-by-step"]
>[Poprzedni](publish-nuget-package.md) 
> [Dalej](breaking-changes.md)
