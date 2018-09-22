---
title: polecenie pakietu DotNet - interfejsu wiersza polecenia platformy .NET Core
description: Polecenie pakietu dotnet tworzy pakiety NuGet do projektu .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 434f1c97af24d1417cd79edd52b63814fd4c6512
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46585405"
---
# <a name="dotnet-pack"></a>pakietu DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet pack` -Pakiety kodu do pakietu NuGet.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a>Opis

`dotnet pack` Polecenie tworzy projekt i tworzy pakiety NuGet. Wynik tego polecenia jest pakiet NuGet. Jeśli `--include-symbols` opcji, jest tworzony inny pakiet zawierający symboli debugowania.

Zależności NuGet upakowaną projektu zostaną dodane do *.nuspec* pliku, dzięki czemu są one prawidłowo rozwiązany po zainstalowaniu pakietu. Odwołania projekt projekt nie są spakowane w projekcie. Obecnie konieczne jest posiadanie pakietu dla projektu w przypadku zależności projektu do projektu.

Domyślnie `dotnet pack` najpierw tworzy projekt. Jeśli chcesz uniknąć tego zachowania, należy przekazać `--no-build` opcji. Ta opcja jest często przydatne w scenariuszach kompilacji ciągłej integracji (CI), gdy wiesz, że kod została wcześniej skompilowana.

Możesz podać właściwości programu MSBuild do `dotnet pack` polecenie, aby uzyskać proces pakowania. Aby uzyskać więcej informacji, zobacz [właściwości metadanych NuGet](csproj.md#nuget-metadata-properties) i [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). [Przykłady](#examples) sekcja przedstawia sposób użycia przełącznika -p MSBuild z kilku różnych scenariuszy.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Argumenty

`PROJECT`

Projekt do pakietu. Jest ścieżką do [pliku csproj](csproj.md) lub w katalogu. Jeśli nie zostanie określony, jego wartość domyślna w bieżącym katalogu.

## <a name="options"></a>Opcje

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`--force`

Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie. Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`--include-source`

Zawiera pliki źródłowe pakietu NuGet. Pliki źródłowe znajdują się w `src` folder wewnątrz `nupkg`.

`--include-symbols`

Generuje symbole `nupkg`.

`--no-build`

Nie da się skompilować projektu przed pakowania. Ustawia ona również niejawne `--no-restore` flagi.

`--no-dependencies`

Ignoruje odwołania projekt projekt i przywraca jedynie projektu głównego.

`--no-restore`

Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.

`-o|--output <OUTPUT_DIRECTORY>`

Pakiety utworzone w katalogu wskazanym miejsca.

`--runtime <RUNTIME_IDENTIFIER>`

Określa docelowe środowisko uruchomieniowe w celu przywrócenia pakietów dla. Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).

`-s|--serviceable`

Ustawia flagę zdatne do użytku w pakiecie. Aby uzyskać więcej informacji, zobacz [bloga platformy .NET: .NET 4.5.1 zabezpieczeń firmy Microsoft obsługuje aktualizacje programu .NET NuGet biblioteki](https://aka.ms/nupkgservicing).

`--version-suffix <VERSION_SUFFIX>`

Definiuje wartość dla `$(VersionSuffix)` właściwości programu MSBuild w projekcie.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

> [!NOTE]
> Projekty sieci Web nie są packable domyślnie. Aby zastąpić domyślne zachowanie, dodaj następującą właściwość do Twojej *.csproj* pliku:
> ```xml
> <PropertyGroup>
>    <IsPackable>true</IsPackable>
> </PropertyGroup>
> ```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`--include-source`

Zawiera pliki źródłowe pakietu NuGet. Pliki źródłowe znajdują się w `src` folder wewnątrz `nupkg`.

`--include-symbols`

Generuje symbole `nupkg`.

`--no-build`

Nie da się skompilować projektu przed pakowania.

`-o|--output <OUTPUT_DIRECTORY>`

Pakiety utworzone w katalogu wskazanym miejsca.

`-s|--serviceable`

Ustawia flagę zdatne do użytku w pakiecie. Aby uzyskać więcej informacji, zobacz [bloga platformy .NET: .NET 4.5.1 zabezpieczeń firmy Microsoft obsługuje aktualizacje programu .NET NuGet biblioteki](https://aka.ms/nupkgservicing).

`--version-suffix <VERSION_SUFFIX>`

Definiuje wartość dla `$(VersionSuffix)` właściwości programu MSBuild w projekcie.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

---

## <a name="examples"></a>Przykłady

Pakiet projektu w bieżącym katalogu:

`dotnet pack`

Pakiet `app1` projektu:

`dotnet pack ~/projects/app1/project.csproj`

Pakowanie projekt w bieżącym katalogu i umieścić wynikowy pakietów do `nupkgs` folderu:

`dotnet pack --output nupkgs`

Pakiet projektu w bieżącym katalogu do `nupkgs` folder i Pomiń krok kompilacji:

`dotnet pack --no-build --output nupkgs`

Z projektem sufiks wersji skonfigurowana jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` w *.csproj* pliku, pakiet bieżącego projektu i zaktualizuj wynikowy wersja pakietu przy użyciu danego sufiksu:

`dotnet pack --version-suffix "ci-1234"`

Ustaw wersję pakietu `2.1.0` z `PackageVersion` właściwości MSBuild:

`dotnet pack -p:PackageVersion=2.1.0`

Projekt dla określonego pakietu [platformę docelową](../../standard/frameworks.md):

`dotnet pack -p:TargetFrameworks=net45`

Pakowanie projektu i użyć określonego środowiska uruchomieniowego (system Windows 10) dla operacji przywracania (.NET Core SDK 2.0 i nowsze wersje):

`dotnet pack --runtime win10-x64`
