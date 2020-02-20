---
title: polecenie dotnet Pack
description: Polecenie programu dotnet Pack tworzy pakiety NuGet dla projektu .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 865262f1eb314f9b7e8ee713c573a965e89ded93
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503644"
---
# <a name="dotnet-pack"></a>dotnet pack

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji

## <a name="name"></a>Name (Nazwa)

`dotnet pack` — pakuje kod do pakietu NuGet.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable]
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a>Opis

`dotnet pack` polecenie kompiluje projekt i tworzy pakiety NuGet. Wynikiem tego polecenia jest pakiet NuGet (czyli plik *. nupkg* ).

Jeśli chcesz wygenerować pakiet zawierający symbole debugowania, dostępne są dwie opcje:

- `--include-symbols` — tworzy pakiet symboli.
- `--include-source` — tworzy pakiet symboli z folderem `src` wewnątrz zawierającym pliki źródłowe.

Zależności NuGet spakowanego projektu są dodawane do pliku *. nuspec* , więc są one poprawnie rozwiązane po zainstalowaniu pakietu. Odwołania projektu do projektu nie są spakowane w projekcie. Obecnie należy mieć pakiet dla każdego projektu, jeśli istnieją zależności między projektami.

Domyślnie `dotnet pack` kompiluje projekt. Aby uniknąć tego zachowania, należy przekazać opcję `--no-build`. Ta opcja jest często przydatna w scenariuszach kompilacji ciągłej integracji (CI), w których wiadomo, że kod został wcześniej skompilowany.

Można podać właściwości programu MSBuild w `dotnet pack` polecenie dla procesu pakowania. Aby uzyskać więcej informacji, zobacz [właściwości metadanych NuGet](csproj.md#nuget-metadata-properties) i [Dokumentacja wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). W sekcji [przykłady](#examples) pokazano, jak używać przełącznika MSBuild-p w przypadku kilku różnych scenariuszy.

Projekty sieci Web nie są domyślnie objęte pakietem. Aby zastąpić zachowanie domyślne, Dodaj następującą właściwość do pliku *. csproj* :

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

  Projekt lub rozwiązanie do spakowania. Jest to ścieżka do [pliku csproj](csproj.md), pliku rozwiązania lub do katalogu. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla pliku projektu lub rozwiązania.

## <a name="options"></a>Opcje

- **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartość domyślna dla większości projektów jest `Debug`, ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.

- **`--force`**

  Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--include-source`**

  Obejmuje pakiety NuGet symboli debugowania oprócz zwykłych pakietów NuGet w katalogu wyjściowym. Pliki źródeł znajdują się w folderze `src` w pakiecie symboli.

- **`--include-symbols`**

  Obejmuje pakiety NuGet symboli debugowania oprócz zwykłych pakietów NuGet w katalogu wyjściowym.

- **`--interactive`**

  Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład w celu ukończenia uwierzytelniania). Dostępne od wersji .NET Core 3,0 SDK.

- **`--no-build`**

  Nie kompiluje projektu przed opakowaniem. Niejawnie ustawia również flagę `--no-restore`.

- **`--no-dependencies`**

  Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.

- **`--nologo`**

  Nie wyświetla transparentu początkowego ani komunikatu o prawach autorskich. Dostępne od wersji .NET Core 3,0 SDK.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Umieszcza skompilowane pakiety w określonym katalogu.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Określa docelowy środowisko uruchomieniowe, dla którego mają zostać przywrócone pakiety. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).

- **`-s|--serviceable`**

  Ustawia flagę obsługi w pakiecie. Aby uzyskać więcej informacji, zobacz [blog platformy .NET: .NET 4.5.1 obsługuje aktualizacje zabezpieczeń firmy Microsoft dla bibliotek NuGet programu .NET](https://aka.ms/nupkgservicing).

- **`--version-suffix <VERSION_SUFFIX>`**

  Definiuje wartość właściwości `$(VersionSuffix)` MSBuild w projekcie.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.

## <a name="examples"></a>Przykłady

- Pakowanie projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet pack
  ```

- Pakowanie projektu `app1`:

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- Pakowanie projektu w bieżącym katalogu i umieszczenie pakietów powstających w folderze `nupkgs`:

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- Pakowanie projektu w bieżącym katalogu do folderu `nupkgs` i pomijanie kroku kompilacji:

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- Przy użyciu sufiksu wersji projektu skonfigurowanego jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` w pliku *csproj* należy spakować bieżący projekt i zaktualizować uzyskaną wersję pakietu przy użyciu danego sufiksu:

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- Ustaw wersję pakietu na `2.1.0` przy użyciu `PackageVersion` właściwości programu MSBuild:

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- Pakowanie projektu dla konkretnej [platformy docelowej](../../standard/frameworks.md):

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- Pakowanie projektu i użycie określonego środowiska uruchomieniowego (Windows 10) dla operacji przywracania:

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- Pakowanie projektu przy użyciu [pliku. nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
