---
title: polecenie Pakiet DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie Pakiet dotnet tworzy pakietów NuGet dla projektu platformy .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 8c2569ec7598b21fe9b673176143d0e54b9eb065
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696822"
---
# <a name="dotnet-pack"></a>Pakiet DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet pack` -Pakietów kodu do pakietu NuGet.

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

`dotnet pack` Polecenie kompilacji projektu i tworzy pakietów NuGet. Wynik tego polecenia jest pakietem NuGet. Jeśli `--include-symbols` opcji, jest tworzony przez inny pakiet zawierający symboli debugowania.

Zależności NuGet spakowana projektu są dodawane do *.nuspec* plików, dzięki czemu są poprawnie rozpoznać po zainstalowaniu pakietu. Odwołania projektu do projektu nie są umieszczone wewnątrz projektu. Obecnie musi mieć pakiet w projekcie, jeśli masz zależności projektu do projektu.

Domyślnie `dotnet pack` najpierw tworzy projekt. Jeśli chcesz uniknąć tego zachowania, należy przekazać `--no-build` opcji. Ta opcja jest często przydatne w scenariuszach kompilacji ciągłej integracji (CI), gdy wiesz, że kod został wcześniej utworzony.

Możesz podać właściwości programu MSBuild do `dotnet pack` polecenia procesu pakowania. Aby uzyskać więcej informacji, zobacz [właściwości metadanych NuGet](csproj.md#nuget-metadata-properties) i [dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). [Przykłady](#examples) sekcji przedstawia sposób użycia przełącznika MSBuild z kilku różnych scenariuszy.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Argumenty

`PROJECT`

Projekt do pakietu. Jest ścieżką do [plik csproj](csproj.md) lub w katalogu. Jeśli nie zostanie określony, domyślnie do bieżącego katalogu.

## <a name="options"></a>Opcje

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`--force`

Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie. Określenie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`--include-source`

Zawiera pliki źródłowe pakietu NuGet. Pliki źródłowe znajdują się w `src` folder w `nupkg`.

`--include-symbols`

Generuje symbole `nupkg`.

`--no-build`

Nie Skompiluj projekt przed pakowania. Niejawne także ustawia `--no-restore` flagi.

`--no-dependencies`

Ignoruje odwołania projektu do projektu i przywraca tylko projektu głównego.

`--no-restore`

Podczas uruchamiania polecenia przywracania niejawne nie jest wykonywana.

`-o|--output <OUTPUT_DIRECTORY>`

Umieszcza pakiety wbudowanych w katalogu określonym.

`--runtime <RUNTIME_IDENTIFIER>`

Określa docelowe środowisko uruchomieniowe pod kątem przywracania pakietów dla. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).

`-s|--serviceable`

Ustawia flagę obsługiwanych w pakiecie. Aby uzyskać więcej informacji, zobacz [blogu .NET: platforma .NET 4.5.1 zabezpieczeń firmy Microsoft obsługuje aktualizacje programu .NET NuGet biblioteki](https://aka.ms/nupkgservicing).

`--version-suffix <VERSION_SUFFIX>`

Definiuje wartość dla `$(VersionSuffix)` właściwości programu MSBuild w projekcie.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`--include-source`

Zawiera pliki źródłowe pakietu NuGet. Pliki źródłowe znajdują się w `src` folder w `nupkg`.

`--include-symbols`

Generuje symbole `nupkg`.

`--no-build`

Nie Skompiluj projekt przed pakowania.

`-o|--output <OUTPUT_DIRECTORY>`

Umieszcza pakiety wbudowanych w katalogu określonym.

`-s|--serviceable`

Ustawia flagę obsługiwanych w pakiecie. Aby uzyskać więcej informacji, zobacz [blogu .NET: platforma .NET 4.5.1 zabezpieczeń firmy Microsoft obsługuje aktualizacje programu .NET NuGet biblioteki](https://aka.ms/nupkgservicing).

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

Pakiet projektu w bieżącym katalogu i umieszczenie wynikowy pakietów do `nupkgs` folderu:

`dotnet pack --output nupkgs`

Pakiet projektu w bieżącym katalogu do `nupkgs` folderu i Pomiń krok kompilacji:

`dotnet pack --no-build --output nupkgs`

W projekcie sufiks wersji skonfigurowana jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` w *.csproj* pliku, pakiet bieżącego projektu i zaktualizować wynikowy wersja pakietu z danego sufiksu:

`dotnet pack --version-suffix "ci-1234"`

Ustaw wersję pakietu do `2.1.0` z `PackageVersion` właściwości programu MSBuild:

`dotnet pack /p:PackageVersion=2.1.0`

Projekt dla określonego pakietu [platformy docelowej](../../standard/frameworks.md):

`dotnet pack /p:TargetFrameworks=net45`

Pakiet projektu i użyć określonego środowiska wykonawczego (systemu Windows Windows 10) dla operacji przywracania (.NET Core SDK 2.0 i nowsze wersje):

`dotnet pack --runtime win10-x64`