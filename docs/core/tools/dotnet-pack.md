---
title: polecenie dotnet Pack
description: Polecenie programu dotnet Pack tworzy pakiety NuGet dla projektu .NET Core.
ms.date: 04/28/2020
ms.openlocfilehash: 00cda2c52a12a7a3aef5f61291120f522536131d
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442231"
---
# <a name="dotnet-pack"></a>dotnet pack

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet pack`-Pakuje kod do pakietu NuGet.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output <OUTPUT_DIRECTORY>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--serviceable] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet pack -h|--help
```

## <a name="description"></a>Opis

`dotnet pack`Polecenie kompiluje projekt i tworzy pakiety NuGet. Wynikiem tego polecenia jest pakiet NuGet (czyli plik *. nupkg* ).

Jeśli chcesz wygenerować pakiet zawierający symbole debugowania, dostępne są dwie opcje:

- `--include-symbols`— tworzy pakiet symboli.
- `--include-source`— tworzy pakiet symboli z `src` folderem zawierającym pliki źródłowe.

Zależności NuGet spakowanego projektu są dodawane do pliku *. nuspec* , więc są one poprawnie rozwiązane po zainstalowaniu pakietu. Odwołania projektu do projektu nie są spakowane w projekcie. Obecnie należy mieć pakiet dla każdego projektu, jeśli istnieją zależności między projektami.

Domyślnie program `dotnet pack` kompiluje projekt. Jeśli chcesz uniknąć tego zachowania, Przekaż `--no-build` opcję. Ta opcja jest często przydatna w scenariuszach kompilacji ciągłej integracji (CI), w których wiadomo, że kod został wcześniej skompilowany.

> [!NOTE]
> W niektórych przypadkach nie można wykonać niejawnej kompilacji. Taka sytuacja może wystąpić `GeneratePackageOnBuild` , gdy jest ustawiona, aby uniknąć cyklicznej zależności między obiektami docelowymi kompilacji i pakietów. Kompilacja może również zakończyć się niepowodzeniem, jeśli istnieje zablokowany plik lub inny problem.

Można podać właściwości programu MSBuild do `dotnet pack` polecenia dla procesu pakowania. Aby uzyskać więcej informacji, zobacz [właściwości metadanych NuGet](csproj.md#nuget-metadata-properties) i [Dokumentacja wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). W sekcji [przykłady](#examples) pokazano, jak używać przełącznika MSBuild-p w przypadku kilku różnych scenariuszy.

Projekty sieci Web nie są domyślnie objęte pakietem. Aby zastąpić zachowanie domyślne, Dodaj następującą właściwość do pliku *. csproj* :

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

### <a name="implicit-restore"></a>Przywracanie niejawne

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

  Projekt lub rozwiązanie do spakowania. Jest to ścieżka do [pliku csproj](csproj.md), plik vbproj, plik fsproj, plik rozwiązania lub do katalogu. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla pliku projektu lub rozwiązania.

## <a name="options"></a>Opcje

- **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartością domyślną dla większości projektów jest `Debug` , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.

- **`--force`**

  Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--include-source`**

  Obejmuje pakiety NuGet symboli debugowania oprócz zwykłych pakietów NuGet w katalogu wyjściowym. Pliki źródeł są dołączone do `src` folderu w pakiecie symboli.

- **`--include-symbols`**

  Obejmuje pakiety NuGet symboli debugowania oprócz zwykłych pakietów NuGet w katalogu wyjściowym.

- **`--interactive`**

  Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład w celu ukończenia uwierzytelniania). Dostępne od wersji .NET Core 3,0 SDK.

- **`--no-build`**

  Nie kompiluje projektu przed opakowaniem. Również niejawnie ustawia `--no-restore` flagę.

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

  Definiuje wartość `$(VersionSuffix)` Właściwości programu MSBuild w projekcie.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` .

## <a name="examples"></a>Przykłady

- Pakowanie projektu w bieżącym katalogu:

  ```dotnetcli
  dotnet pack
  ```

- Pakowanie `app1` projektu:

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- Pakowanie projektu w bieżącym katalogu i umieszczenie w nim pakietów powstających `nupkgs` :

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- Pakowanie projektu w bieżącym katalogu do `nupkgs` folderu i pomijanie kroku kompilacji:

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- Przy użyciu sufiksu wersji projektu skonfigurowanego jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` w pliku *. csproj* należy spakować bieżący projekt i zaktualizować uzyskaną wersję pakietu przy użyciu danego sufiksu:

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- Ustaw wersję pakietu na `2.1.0` za pomocą `PackageVersion` właściwości MSBuild:

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

- Pakowanie projektu przy użyciu pliku *. nuspec* :

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```

  Informacje o sposobach korzystania z `NuspecFile` programu, `NuspecBasePath` i `NuspecProperties` można znaleźć w następujących zasobach:
  
  - [Pakowanie przy użyciu elementu. nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)
  - [Zaawansowane punkty rozszerzenia do tworzenia dostosowanego pakietu](https://docs.microsoft.com/nuget/reference/msbuild-targets#advanced-extension-points-to-create-customized-package)
  - [Właściwości globalne](https://docs.microsoft.com/visualstudio/msbuild/msbuild-properties?view=vs-2019#global-properties)
