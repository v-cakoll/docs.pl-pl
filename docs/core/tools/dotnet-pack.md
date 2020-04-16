---
title: dotnet pack, polecenie
description: Polecenie dotnet pack tworzy pakiety NuGet dla projektu .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 3b9c46ecd5d67519728896b0018e27fb41ebd861
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463510"
---
# <a name="dotnet-pack"></a>dotnet pack

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet pack`- Pakuje kod do pakietu NuGet.

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

Polecenie `dotnet pack` tworzy projekt i tworzy pakiety NuGet. Wynikiem tego polecenia jest pakiet NuGet (czyli plik *nupkg).*

Jeśli chcesz wygenerować pakiet, który zawiera symbole debugowania, masz dwie opcje dostępne:

- `--include-symbols`- tworzy pakiet symboli.
- `--include-source`- tworzy pakiet symboli `src` z folderem wewnątrz zawierającym pliki źródłowe.

Zależności NuGet spakowanego projektu są dodawane do pliku *nuspec,* więc są poprawnie rozpoznawane po zainstalowaniu pakietu. Odwołania do projektu nie są pakowane wewnątrz projektu. Obecnie musisz mieć pakiet na projekt, jeśli masz zależności między projektem.

Domyślnie `dotnet pack` najpierw tworzy projekt. Jeśli chcesz uniknąć tego zachowania, `--no-build` przekaż tę opcję. Ta opcja jest często przydatne w scenariuszach kompilacji ciągłej integracji (CI), w których wiesz, że kod został wcześniej skompilowany.

> [!NOTE]
> W niektórych przypadkach nie można wykonać kompilacji niejawnej. Może to `GeneratePackageOnBuild` nastąpić, gdy jest ustawiona, aby uniknąć cyklicznej zależności między kompilacji i pack obiektów docelowych. Kompilacja może również zakończyć się niepowodzeniem, jeśli istnieje zablokowany plik lub inny problem.

Właściwości MSBuild można podać `dotnet pack` do polecenia dla procesu pakowania. Aby uzyskać więcej informacji, zobacz [Właściwości metadanych NuGet](csproj.md#nuget-metadata-properties) i [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). [Przykłady](#examples) sekcja pokazuje, jak używać przełącznika MSBuild -p dla kilku różnych scenariuszy.

Projekty sieci Web nie są domyślnie spakowane. Aby zastąpić zachowanie domyślne, dodaj następującą właściwość do pliku *csproj:*

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

  Definiuje konfigurację kompilacji. Wartość domyślna dla `Debug`większości projektów to , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.

- **`--force`**

  Wymusza wszystkie zależności do rozwiązania, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--include-source`**

  Zawiera symbole debugowania Pakiety NuGet oprócz zwykłych pakietów NuGet w katalogu wyjściowym. Pliki źródeł są zawarte w `src` folderze w pakiecie symboli.

- **`--include-symbols`**

  Zawiera symbole debugowania Pakiety NuGet oprócz zwykłych pakietów NuGet w katalogu wyjściowym.

- **`--interactive`**

  Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika (na przykład w celu ukończenia uwierzytelniania). Dostępne od .NET Core 3.0 SDK.

- **`--no-build`**

  Nie buduje projektu przed pakowanie. Również niejawnie `--no-restore` ustawia flagę.

- **`--no-dependencies`**

  Ignoruje odwołania do projektu i przywraca tylko projekt główny.

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas uruchamiania polecenia.

- **`--nologo`**

  Nie wyświetla banera startowego ani wiadomości o prawach autorskich. Dostępne od .NET Core 3.0 SDK.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Umieszcza wbudowane pakiety w określonym katalogu.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Określa docelowy czas wykonywania do przywrócenia pakietów dla. Aby uzyskać listę identyfikatorów środowiska wykonawczego (RID), zobacz [katalog RID](../rid-catalog.md).

- **`-s|--serviceable`**

  Ustawia flagę z obsługą w pakiecie. Aby uzyskać więcej informacji, zobacz [blog platformy .NET: .NET 4.5.1 obsługuje aktualizacje zabezpieczeń firmy Microsoft dla bibliotek nugetów .NET](https://aka.ms/nupkgservicing).

- **`--version-suffix <VERSION_SUFFIX>`**

  Definiuje wartość właściwości `$(VersionSuffix)` MSBuild w projekcie.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .

## <a name="examples"></a>Przykłady

- Zapakuj projekt do bieżącego katalogu:

  ```dotnetcli
  dotnet pack
  ```

- Zapakuj `app1` projekt:

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- Zapakuj projekt do bieżącego katalogu i `nupkgs` umieść powstałe pakiety w folderze:

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- Zapakuj projekt w bieżącym `nupkgs` katalogu do folderu i pomiń krok kompilacji:

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- Za pomocą sufiksu wersji `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` projektu skonfigurowanym tak jak w pliku *csproj,* zapakuj bieżący projekt i zaktualizuj wynikową wersję pakietu z danym sufiksem:

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- Ustaw wersję pakietu `2.1.0` z `PackageVersion` właściwością MSBuild:

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- Zapakuj projekt do określonej [ramy docelowej:](../../standard/frameworks.md)

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- Zapakuj projekt i użyj określonego środowiska uruchomieniowego (Windows 10) do operacji przywracania:

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- Zapakuj projekt za pomocą [pliku nuspec:](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
