---
title: polecenie dotnet pack
description: Polecenie dotnet pack tworzy pakiety NuGet dla projektu .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 865262f1eb314f9b7e8ee713c573a965e89ded93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503644"
---
# <a name="dotnet-pack"></a>dotnet pack

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet pack`- Pakuje kod do pakietu NuGet.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable]
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet pack` tworzy projekt i tworzy pakiety NuGet. Wynikiem tego polecenia jest pakiet NuGet (czyli plik *.nupkg).*

Jeśli chcesz wygenerować pakiet zawierający symbole debugowania, dostępne są dwie opcje:

- `--include-symbols`- tworzy pakiet symboli.
- `--include-source`- tworzy pakiet symboli `src` z folderem wewnątrz zawierającym pliki źródłowe.

NuGet zależności spakowanego projektu są dodawane do pliku *nuspec,* więc są one poprawnie rozwiązane po zainstalowaniu pakietu. Odwołania do projektu nie są pakowane wewnątrz projektu. Obecnie musisz mieć pakiet na projekt, jeśli masz zależności projektu do projektu.

Domyślnie `dotnet pack` najpierw tworzy projekt. Jeśli chcesz uniknąć tego zachowania, `--no-build` przekaż tę opcję. Ta opcja jest często przydatne w scenariuszach kompilacji ciągłej integracji (CI), gdzie wiadomo, że kod został wcześniej zbudowany.

Można podać msbuild właściwości `dotnet pack` do polecenia dla procesu pakowania. Aby uzyskać więcej informacji, zobacz [NuGet właściwości metadanych](csproj.md#nuget-metadata-properties) i [MSBuild command-line odwołania](/visualstudio/msbuild/msbuild-command-line-reference). Przykłady [Examples](#examples) sekcji pokazuje, jak używać przełącznika MSBuild -p dla kilku różnych scenariuszy.

Projekty sieci Web nie są domyślnie pakowane. Aby zastąpić zachowanie domyślne, dodaj następującą właściwość do pliku *csproj:*

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

  Projekt lub rozwiązanie do spakowania. Jest to albo ścieżka do [pliku csproj](csproj.md), pliku rozwiązania, albo do katalogu. Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog w poszukiwaniu pliku projektu lub rozwiązania.

## <a name="options"></a>Opcje

- **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartość domyślna dla `Debug`większości projektów jest , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.

- **`--force`**

  Wymusza rozwiązywanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--include-source`**

  Zawiera symbole debugowania Pakiety NuGet oprócz zwykłych pakietów NuGet w katalogu wyjściowym. Pliki źródeł znajdują się `src` w folderze w pakiecie symboli.

- **`--include-symbols`**

  Zawiera symbole debugowania Pakiety NuGet oprócz zwykłych pakietów NuGet w katalogu wyjściowym.

- **`--interactive`**

  Umożliwia polecenie, aby zatrzymać i czekać na dane wejściowe użytkownika lub akcji (na przykład, aby zakończyć uwierzytelnianie). Dostępne od sdk .NET Core 3.0.

- **`--no-build`**

  Nie tworzy projektu przed pakowaniem. To również niejawnie ustawia `--no-restore` flagę.

- **`--no-dependencies`**

  Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas uruchamiania polecenia.

- **`--nologo`**

  Nie wyświetla banera startowego ani wiadomości o prawach autorskich. Dostępne od sdk .NET Core 3.0.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Umieszcza wbudowane pakiety w określonym katalogu.

- **`--runtime <RUNTIME_IDENTIFIER>`**

  Określa docelowy czas wykonywania, dla której ma zostać przywrócony pakiety. Aby uzyskać listę identyfikatorów runtime (RID), zobacz [katalog RID](../rid-catalog.md).

- **`-s|--serviceable`**

  Ustawia w pakiecie flagę z możliwością serwisowania. Aby uzyskać więcej informacji, zobacz [.NET Blog: .NET 4.5.1 Obsługuje aktualizacje zabezpieczeń firmy Microsoft dla bibliotek .NET NuGet](https://aka.ms/nupkgservicing).

- **`--version-suffix <VERSION_SUFFIX>`**

  Definiuje wartość właściwości `$(VersionSuffix)` MSBuild w projekcie.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .

## <a name="examples"></a>Przykłady

- Zapakuj projekt w bieżącym katalogu:

  ```dotnetcli
  dotnet pack
  ```

- Zapakuj `app1` projekt:

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- Zapakuj projekt w bieżącym katalogu i `nupkgs` umieść powstałe pakiety w folderze:

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- Spakować projekt w bieżącym `nupkgs` katalogu do folderu i pominąć krok kompilacji:

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- Z sufiksem wersji projektu `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` skonfigurowanym jak w pliku *csproj,* zapakuj bieżący projekt i zaktualizuj wynikową wersję pakietu z danym sufiksem:

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- Ustaw wersję pakietu `2.1.0` za `PackageVersion` pomocą właściwości MSBuild:

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- Spakować projekt dla określonych [ram docelowych:](../../standard/frameworks.md)

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- Spakować projekt i użyć określonego środowiska uruchomieniowego (Windows 10) dla operacji przywracania:

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- Spakować projekt przy użyciu [pliku nuspec:](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
