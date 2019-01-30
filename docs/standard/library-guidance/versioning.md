---
title: Biblioteki i przechowywania wersji platformy .NET
description: Zalecenia dotyczące najlepszych rozwiązań dla wersji bibliotek platformy .NET.
author: jamesnk
ms.author: mairaw
ms.date: 12/10/2018
ms.openlocfilehash: e6f811039f74649564cbfb42ef67e0a406e4cd70
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204746"
---
# <a name="versioning"></a>Obsługa wersji

Biblioteka oprogramowania rzadko zakończeniu w wersji 1.0. Dobre bibliotek z czasem ewoluować, dodawanie funkcji, naprawianie błędów i poprawę wydajności. Należy pamiętać, że można zwolnić nowe wersje biblioteki .NET, zapewniając dodatkową wartość z każdą wersją, bez przerywania istniejących użytkowników.

## <a name="breaking-changes"></a>Zmiany powodujące niezgodność

Aby uzyskać informacje na temat przełomowych zmian między wersjami obsługi, zobacz [istotne zmiany w](./breaking-changes.md).

## <a name="version-numbers"></a>Numery wersji

Biblioteka .NET zawiera wiele sposobów, aby określić wersję. Te wersje są dla Ciebie najważniejsze:

### <a name="nuget-package-version"></a>Wersja pakietu NuGet

[Pakietu NuGet w wersji](/nuget/reference/package-versioning) jest wyświetlana w witrynie NuGet.org, Menedżer pakietów NuGet usługi Visual Studio i jest dodawany do kodu źródłowego, gdy jest używany pakiet. Wersja pakietu NuGet jest często będzie widoczna dla użytkowników numeru wersji i będzie odnoszą się do niego podczas rozmawiamy o wersji biblioteki, używane. Wersja pakietu NuGet jest używany przez NuGet i nie ma wpływu na zachowanie środowiska uruchomieniowego.

```xml
<PackageVersion>1.0.0-alpha1</PackageVersion>
```

Identyfikator pakietu NuGet, które są połączone z wersji pakietu NuGet służy do identyfikowania pakiet nuget. Na przykład `Newtonsoft.Json`  +  `11.0.2`. Pakiet z sufiksem to pakiet wersji wstępnej i ma specjalne zachowanie, który sprawia, że niezwykle przydatna przy testowaniu. Aby uzyskać więcej informacji, zobacz [pakiety w wersji wstępnej](./nuget.md#pre-release-packages).

Ponieważ wersja pakietu NuGet jest najbardziej widoczne wersji dla deweloperów, to dobry pomysł, aby zaktualizować go za pomocą [Semantic Versioning (SemVer)](https://semver.org/). SemVer oznacza znaczenie zmiany między wersji, a także pomaga deweloperom podjąć świadomą decyzję, wybierając jakie wersję do użycia. Na przykład, przechodząc od `1.0` do `2.0` oznacza, że są potencjalnie przełomowe zmiany.

**ROZWAŻ ✔️** przy użyciu [SemVer 2.0.0](https://semver.org/) do wersji pakietu NuGet.

**CZY ✔️** używać wersji pakietu NuGet w publiczną dokumentację, ponieważ numer wersji, którą użytkownicy zobaczą często.

**CZY ✔️** zawierać sufiks wersji wstępnej, podczas przekazywania pakietu niż wersja stabilna.

> Użytkownicy muszą zgadzaj się na wprowadzenie pakiety w wersji wstępnej, dzięki czemu będzie zrozumiałe, że pakiet nie została zakończona.

### <a name="assembly-version"></a>Wersja zestawu

Wersja zestawu jest środowisko CLR używa w czasie wykonywania, aby wybrać wersję zestawu do załadowania. Wybieranie zestawu przy użyciu tylko wersji mają zastosowanie do zestawów o silnej nazwie.

```xml
<AssemblyVersion>1.0.0.0</AssemblyVersion>
```

Windows .NET Framework w CLR wymaga dokładnie dopasowany do obciążenia silne silną. Na przykład `Libary1, Version=1.0.0.0` został skompilowany z odwołaniem do `Newtonsoft.Json, Version=11.0.0.0`. .NET Framework załaduje tylko tej wersji dokładnie `11.0.0.0`. Aby załadować innej wersji w czasie wykonywania, należy dodać przekierowanie powiązania do pliku konfiguracji aplikacji .NET.

Silne nazwy w połączeniu z wersji zestawu umożliwia [ładowania wersji zestawu strict](../../framework/app-domains/assembly-versioning.md). Chociaż silnych nazw biblioteki ma wiele korzyści, często powoduje wyjątki środowiska uruchomieniowego, których nie można znaleźć zestawu i [wymaga przekierowania powiązań](../../framework/configure-apps/redirect-assembly-versions.md) w `app.config` / `web.config` naprawy. Ładowanie zestawu .NET core została swobodna i .NET Core CLR zostanie automatycznie załadowany zestawów w czasie wykonywania za pomocą nowszej wersji.

**ROZWAŻ ✔️** tylko tym wersja główna w AssemblyVersion.

> np. 1.0 biblioteki i biblioteki 1.0.1 zarówno mają AssemblyVersion z `1.0.0.0`, podczas gdy biblioteki w wersji 2.0 ma AssemblyVersion z `2.0.0.0`. Jeśli wersja zestawu zmienia się rzadziej, zmniejsza przekierowań powiązań.

**ROZWAŻ ✔️** synchronizacja główny numer wersji AssemblyVersion i wersję pakietu NuGet.

> AssemblyVersion znajduje się w niektórych komunikaty informacyjne, wyświetlana użytkownikowi, np. Nazwa zestawu i zestawu kwalifikowane nazwy typów w komunikaty o wyjątkach. Utrzymywanie relacji między wersjami zawiera więcej informacji dla deweloperów, która wersja używają.

**❌ NIE** mają stały AssemblyVersion.

> Podczas niezmiennych AssemblyVersion eliminuje potrzebę przekierowania powiązań, oznacza to, że tylko jedną wersję zestawu można zainstalować w globalnej pamięci podręcznej zestawów (GAC). Ponadto aplikacje, które odwołują się do zestawu w GAC spowoduje awarię, jeśli inna aplikacja zostaje zaktualizowana o przełomowe zmiany zestawu w globalnej pamięci podręcznej zestawów.

### <a name="assembly-file-version"></a>Wersja pliku zestawu

Wersja pliku zestawu jest używana do wyświetlania wersji pliku w Windows i nie ma wpływu na zachowanie środowiska uruchomieniowego. Ustawienie tej wersji jest opcjonalne. Jest ona widoczna w oknie dialogowym właściwości pliku w Eksploratorze Windows:

```xml
<FileVersion>11.0.2.21924</FileVersion>
```

![Windows Explorer](./media/versioning/win-properties.png "Windows Explorer")

**ROZWAŻ ✔️** tym ciągłej integracji kompilacji numer poprawki AssemblyFileVersion.

> Na przykład tworzysz projekt w wersji 1.0.0 i numer kompilacji ciągłej integracji jest 99, więc Twoja AssemblyFileVersion jest 1.0.0.99.

**CZY ✔️** używają formatu `Major.Minor.Build.Revision` wersji pliku.

> Gdy wersja pliku nigdy nie jest używany przez platformy .NET, [Windows oczekuje, że wersja pliku](/windows/desktop/menurc/versioninfo-resource) w `Major.Minor.Build.Revision` formatu. Ostrzeżenie jest zgłaszane w przypadku wersji on skorzystać z tego formatu.

### <a name="assembly-informational-version"></a>Informacje o wersji zestawu

Informacje o wersji zestawu jest używana do rejestrowania dodatkowe informacje o wersji i nie ma wpływu na zachowanie środowiska uruchomieniowego. Ustawienie tej wersji jest opcjonalne. Jeśli używasz Linku źródłowego, ta wersja zostanie ustawiona na kompilacji z wersji pakietu NuGet oraz wersja kontroli źródła. Na przykład `1.0.0-beta1+204ff0a` zawiera skrót zatwierdzenia zestawu został skompilowany z kodu źródłowego. Aby uzyskać więcej informacji, zobacz [Linku źródłowego](./sourcelink.md).

```xml
<AssemblyInformationalVersion>The quick brown fox jumped over the lazy dog.</AssemblyInformationalVersion>
```

> [!NOTE]
> Starsze wersje programu Visual Studio Zgłoś ostrzeżenia kompilacji, jeśli ta wersja nie postępuj zgodnie z formatu `Major.Minor.Build.Revision`. Można bezpiecznie zignorować to ostrzeżenie.

**Należy UNIKAĆ ❌** samodzielnie ustawienie informacje o wersji zestawu.

> Zezwalaj na SourceLink do automatycznego generowania wersji zawierający metadane kontroli źródła i NuGet.

>[!div class="step-by-step"]
>[Poprzednie](publish-nuget-package.md)
>[dalej](breaking-changes.md)
