---
title: polecenie dotnet Pack
description: Polecenie programu dotnet Pack tworzy pakiety NuGet dla projektu .NET Core.
ms.date: 12/04/2018
ms.openlocfilehash: c5c00f3bb06e5bc5579c0d3d6bdd39fbdf3db656
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202842"
---
# <a name="dotnet-pack"></a>dotnet pack

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet pack`-Pakuje kod do pakietu NuGet.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```console
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

---

## <a name="description"></a>Opis

`dotnet pack` Polecenie kompiluje projekt i tworzy pakiety NuGet. Wynikiem tego polecenia jest pakiet NuGet. Jeśli ta `--include-symbols` opcja jest obecna, tworzony jest inny pakiet zawierający symbole debugowania.

Zależności NuGet spakowanego projektu są dodawane do pliku *. nuspec* , więc są one poprawnie rozwiązane po zainstalowaniu pakietu. Odwołania projektu do projektu nie są spakowane w projekcie. Obecnie należy mieć pakiet dla każdego projektu, jeśli istnieją zależności między projektami.

Domyślnie program `dotnet pack` kompiluje projekt. Jeśli chcesz uniknąć tego zachowania, Przekaż `--no-build` opcję. Ta opcja jest często przydatna w scenariuszach kompilacji ciągłej integracji (CI), w których wiadomo, że kod został wcześniej skompilowany.

Można podać właściwości programu MSBuild do `dotnet pack` polecenia dla procesu pakowania. Aby uzyskać więcej informacji, zobacz [właściwości metadanych NuGet](csproj.md#nuget-metadata-properties) i [Dokumentacja wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). W sekcji [przykłady](#examples) pokazano, jak używać przełącznika MSBuild-p w przypadku kilku różnych scenariuszy.

Projekty sieci Web nie są domyślnie objęte pakietem. Aby zastąpić zachowanie domyślne, Dodaj następującą właściwość do pliku *. csproj* :

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a>Argumenty

* **`PROJECT`**

  Projekt do spakowania. Jest to ścieżka do [pliku csproj](csproj.md) lub katalogu. Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.

## <a name="options"></a>Opcje

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

* **`--force`**

  Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

* **`--include-source`**

  Zawiera pliki źródłowe w pakiecie NuGet. Pliki źródeł znajdują się w `src` folderze programu. `nupkg`

* **`--include-symbols`**

  Generuje symbole `nupkg`.

* **`--no-build`**

  Nie kompiluje projektu przed opakowaniem. Również niejawnie ustawia `--no-restore` flagę.

* **`--no-dependencies`**

  Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.

* **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Umieszcza skompilowane pakiety w określonym katalogu.

* **`--runtime <RUNTIME_IDENTIFIER>`**

  Określa docelowy środowisko uruchomieniowe, dla którego mają zostać przywrócone pakiety. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).

* **`-s|--serviceable`**

  Ustawia flagę obsługi w pakiecie. Aby uzyskać więcej informacji, zobacz [blog platformy .NET: .NET 4.5.1 obsługuje aktualizacje zabezpieczeń firmy Microsoft dla bibliotek NuGet programu .NET](https://aka.ms/nupkgservicing).

* **`--version-suffix <VERSION_SUFFIX>`**

  Definiuje wartość `$(VersionSuffix)` właściwości programu MSBuild w projekcie.

* **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

* **`--include-source`**

  Zawiera pliki źródłowe w pakiecie NuGet. Pliki źródeł znajdują się w `src` folderze programu. `nupkg`

* **`--include-symbols`**

  Generuje symbole `nupkg`.

* **`--no-build`**

  Nie kompiluje projektu przed opakowaniem.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Umieszcza skompilowane pakiety w określonym katalogu.

* **`-s|--serviceable`**

  Ustawia flagę obsługi w pakiecie. Aby uzyskać więcej informacji, zobacz [blog platformy .NET: .NET 4.5.1 obsługuje aktualizacje zabezpieczeń firmy Microsoft dla bibliotek NuGet programu .NET](https://aka.ms/nupkgservicing).

* **`--version-suffix <VERSION_SUFFIX>`**

  Definiuje wartość `$(VersionSuffix)` właściwości programu MSBuild w projekcie.

* **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`

---

## <a name="examples"></a>Przykłady

* Pakowanie projektu w bieżącym katalogu:

  ```console
  dotnet pack
  ```

* `app1` Pakowanie projektu:

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

* Pakowanie projektu w bieżącym katalogu i umieszczenie w nim pakietów `nupkgs` powstających:

  ```console
  dotnet pack --output nupkgs
  ```

* Pakowanie projektu w bieżącym katalogu do `nupkgs` folderu i pomijanie kroku kompilacji:

  ```console
  dotnet pack --no-build --output nupkgs
  ```

* Przy użyciu sufiksu wersji projektu skonfigurowanego `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` jako w pliku *. csproj* należy spakować bieżący projekt i zaktualizować uzyskaną wersję pakietu przy użyciu danego sufiksu:

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

* Ustaw wersję pakietu na `2.1.0` `PackageVersion` za pomocą właściwości MSBuild:

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

* Pakowanie projektu dla konkretnej [platformy docelowej](../../standard/frameworks.md):

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

* Pakowanie projektu i użycie określonego środowiska uruchomieniowego (Windows 10) dla operacji przywracania (zestaw .NET Core SDK 2,0 i nowsze wersje):

  ```console
  dotnet pack --runtime win10-x64
  ```

* Pakowanie projektu przy użyciu [pliku. nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):

  ```console
  dotnet pack ~/projects/app1/project.csproj /p:NuspecFile=~/projects/app1/project.nuspec /p:NuspecBasePath=~/projects/app1/nuget
  ```
