---
title: polecenie kompilacji dotnet
description: Polecenie kompilacji dotnet tworzy projekt i wszystkie jego zależności.
ms.date: 02/14/2020
ms.openlocfilehash: 27deca4ab1c12314db5214c73660862a8a57a398
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463708"
---
# <a name="dotnet-build"></a>dotnet build

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet build`- Buduje projekt i wszystkie jego zależności.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet build -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet build` tworzy projekt i jego zależności do zestawu plików binarnych. Pliki binarne zawierają kod projektu w plikach języka pośredniego (IL) z rozszerzeniem *.dll.*  W zależności od typu projektu i ustawień mogą zostać dołączone inne pliki, takie jak:

- Plik wykonywalny, który może służyć do uruchamiania aplikacji, jeśli typ projektu jest wykonywalnym kierowaniem .NET Core 3.0 lub nowszym.
- Pliki symboli używane do debugowania z rozszerzeniem *pdb.*
- Plik *deps.json,* który wyświetla listę zależności aplikacji lub biblioteki.
- Plik *.runtimeconfig.json,* który określa udostępnione środowisko uruchomieniowe i jego wersję dla aplikacji.
- Inne biblioteki, od których zależy projekt (za pośrednictwem odwołań do projektu lub odwołań do pakietu NuGet).

W przypadku projektów wykonywalnych przeznaczonych dla wersji wcześniejszych niż .NET Core 3.0 zależności biblioteki z NuGet zazwyczaj NIE są kopiowane do folderu wyjściowego.  Są one rozpoznawane z folderu pakietów globalnych NuGet w czasie wykonywania. Mając to na uwadze, `dotnet build` produkt nie jest gotowy do przeniesienia na inną maszynę do uruchomienia. Aby utworzyć wersję aplikacji, która może być wdrożona, należy ją opublikować (na przykład za pomocą polecenia [publikowania dotnet).](dotnet-publish.md) Aby uzyskać więcej informacji, zobacz [.NET Core Application Deployment](../deploying/index.md).

W przypadku projektów wykonywalnych przeznaczonych dla platformy .NET Core 3.0 lub nowszych zależności biblioteki są kopiowane do folderu wyjściowego. Oznacza to, że jeśli nie ma żadnej innej logiki specyficzne dla publikowania (takich jak projekty sieci Web), dane wyjściowe kompilacji powinny być wdrażalne.

Tworzenie wymaga pliku *project.assets.json,* który zawiera listę zależności aplikacji. Plik jest tworzony [`dotnet restore`](dotnet-restore.md) podczas wykonywania. Bez pliku zasobów w miejscu narzędzia nie można rozpoznać zestawów odwołań, co powoduje błędy. W pliku .NET Core 1.x SDK `dotnet restore` konieczne `dotnet build`było jawne uruchomienie przed uruchomieniem . Począwszy od pliku .NET Core 2.0 SDK, `dotnet restore` działa niejawnie po uruchomieniu `dotnet build`. Jeśli chcesz wyłączyć niejawne przywracanie podczas uruchamiania `--no-restore` polecenia kompilacji, możesz przekazać tę opcję.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

Określana przez `<OutputType>` właściwość w pliku projektu, czy projekt jest wykonywalny. W poniższym przykładzie pokazano projekt, który tworzy kod wykonywalny:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Aby utworzyć bibliotekę, `<OutputType>` pomiń właściwość `Library`lub zmień jej wartość na . Biblioteka DLL IL dla biblioteki nie zawiera punktów wejścia i nie może być wykonana.

### <a name="msbuild"></a>MSBuild

`dotnet build`używa MSBuild do tworzenia projektu, więc obsługuje zarówno równoległe, jak i przyrostowe kompilacje. Aby uzyskać więcej informacji, zobacz [Kompilacje przyrostowe](/visualstudio/msbuild/incremental-builds).

Oprócz opcji `dotnet build` polecenie akceptuje opcje MSBuild, takie `-p` jak ustawienie właściwości `-l` lub zdefiniowanie rejestratora. Aby uzyskać więcej informacji na temat tych opcji, zobacz [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). Można też użyć polecenia [dotnet msbuild.](dotnet-msbuild.md)

Bieganie `dotnet build` jest `dotnet msbuild -restore`równoznaczne z bieganiem; jednak domyślna szczegółowość danych wyjściowych jest inna.

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Plik projektu lub rozwiązania do utworzenia. Jeśli plik projektu lub rozwiązania nie jest określony, MSBuild przeszukuje bieżący katalog roboczy dla pliku, który ma rozszerzenie pliku, który kończy się *proj* lub *sln* i używa tego pliku.

## <a name="options"></a>Opcje

- **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartość domyślna dla `Debug`większości projektów to , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.

- **`-f|--framework <FRAMEWORK>`**

  Kompiluje dla określonej [struktury](../../standard/frameworks.md). Struktura musi być zdefiniowana w [pliku projektu](csproj.md).

- **`--force`**

  Wymusza wszystkie zależności do rozwiązania, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika. Na przykład, aby zakończyć uwierzytelnianie. Dostępne od .NET Core 3.0 SDK.

- **`--no-dependencies`**

  Ignoruje odwołania do projektu do projektu (P2P) i tworzy tylko określony projekt główny.

- **`--no-incremental`**

  Oznacza kompilacji jako niebezpieczne dla kompilacji przyrostowej. Ta flaga wyłącza kompilacji przyrostowej i wymusza czyste odbudowanie wykresu zależności projektu.

- **`--no-restore`**

  Nie wykonuje niejawnego przywracania podczas kompilacji.

- **`--nologo`**

  Nie wyświetla banera startowego ani wiadomości o prawach autorskich. Dostępne od .NET Core 3.0 SDK.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Katalog, w którym można umieścić wbudowane pliki binarne. Jeśli nie zostanie określona, domyślną ścieżką jest `./bin/<configuration>/<framework>/`.  W przypadku projektów z wieloma `TargetFrameworks` strukturami docelowymi (za pośrednictwem właściwości) należy również zdefiniować `--framework` podczas określania tej opcji.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Określa docelowy czas wykonywania. Aby uzyskać listę identyfikatorów środowiska wykonawczego (RID), zobacz [katalog RID](../rid-catalog.md).

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości MSBuild. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i . Wartość domyślna to `minimal`.

- **`--version-suffix <VERSION_SUFFIX>`**

  Ustawia wartość właściwości `$(VersionSuffix)` do użycia podczas tworzenia projektu. To działa tylko `$(Version)` wtedy, gdy właściwość nie jest ustawiona. Następnie `$(Version)` jest ustawiona `$(VersionPrefix)` na `$(VersionSuffix)`połączone z , oddzielone kreską.

## <a name="examples"></a>Przykłady

- Tworzenie projektu i jego zależności:

  ```dotnetcli
  dotnet build
  ```

- Tworzenie projektu i jego zależności przy użyciu konfiguracji wydania:

  ```dotnetcli
  dotnet build --configuration Release
  ```

- Tworzenie projektu i jego zależności dla określonego środowiska uruchomieniowego (w tym przykładzie Ubuntu 18.04):

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- Skompiluj projekt i użyj określonego źródła pakietu NuGet podczas operacji przywracania (.NET Core 2.0 SDK i nowsze wersje):

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- Skompiluj projekt i ustaw wersję 1.2.3.4 jako parametr kompilacji przy użyciu `-p` opcji [MSBuild:](#msbuild)

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
