---
title: polecenie dotnet build
description: Polecenie kompilacji dotnet tworzy projekt i wszystkie jego zależności.
ms.date: 02/14/2020
ms.openlocfilehash: 9f9a78ec0a6a25c54c8a727c05081ce6835514ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503765"
---
# <a name="dotnet-build"></a>dotnet build

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet build`- Buduje projekt i wszystkie jego zależności.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force]
    [--interactive] [--no-dependencies] [--no-incremental] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet build` tworzy projekt i jego zależności w zestaw plików binarnych. Pliki binarne zawierają kod projektu w plikach il (Intermediate Language) z rozszerzeniem *dll.*  W zależności od typu i ustawień projektu mogą być dołączone inne pliki, takie jak:

- Plik wykonywalny, który może służyć do uruchamiania aplikacji, jeśli typ projektu jest wykonywalnym kierowaniem .NET Core 3.0 lub nowszym.
- Pliki symboli używane do debugowania z rozszerzeniem *pdb.*
- Plik *.deps.json,* który zawiera listę zależności aplikacji lub biblioteki.
- Plik *.runtimeconfig.json,* który określa udostępniony czas wykonywania i jego wersję dla aplikacji.
- Inne biblioteki, od których zależy projekt (za pośrednictwem odwołań do projektu lub odwołań do pakietu NuGet).

W przypadku projektów wykonywalnych przeznaczonych dla wersji wcześniejszych niż .NET Core 3.0 zależności biblioteki z NuGet zazwyczaj NIE są kopiowane do folderu wyjściowego.  Są one rozwiązywane z nuget folderu pakietów globalnych w czasie wykonywania. Mając to na uwadze, `dotnet build` produkt nie jest gotowy do przeniesienia na inną maszynę do uruchomienia. Aby utworzyć wersję aplikacji, która może być wdrożona, należy ją opublikować (na przykład [poleceniem publikowania dotnet).](dotnet-publish.md) Aby uzyskać więcej informacji, zobacz [.NET Core Application Deployment](../deploying/index.md).

W przypadku projektów wykonywalnych przeznaczonych na program .NET Core 3.0 i nowszych zależności biblioteki są kopiowane do folderu wyjściowego. Oznacza to, że jeśli nie ma żadnej innej logiki specyficzne dla publikowania (takich jak projekty sieci Web mają), dane wyjściowe kompilacji powinny być wdrażalne.

Tworzenie wymaga pliku *project.assets.json,* który zawiera listę zależności aplikacji. Plik jest tworzony [`dotnet restore`](dotnet-restore.md) podczas wykonywania. Bez pliku zasobów w miejscu, narzędzia nie można rozwiązać zestawy odwołań, co powoduje błędy. W przypadku sdk .NET Core 1.x `dotnet restore` należy `dotnet build`jawnie uruchomić przed uruchomieniem . Począwszy od .NET Core 2.0 `dotnet restore` SDK, `dotnet build`jest uruchamiany niejawnie po uruchomieniu . Jeśli chcesz wyłączyć przywracanie niejawne podczas uruchamiania `--no-restore` polecenia kompilacji, możesz przekazać tę opcję.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

Określa, czy projekt jest wykonywalny, `<OutputType>` czy nie, jest określana przez właściwość w pliku projektu. W poniższym przykładzie przedstawiono projekt, który tworzy kod wykonywalny:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Aby utworzyć bibliotekę, `<OutputType>` pomiń właściwość `Library`lub zmień jej wartość na . Biblioteka IL dla biblioteki nie zawiera punktów wejścia i nie można jej wykonać.

### <a name="msbuild"></a>MSBuild

`dotnet build`używa MSBuild do tworzenia projektu, więc obsługuje kompilacje równoległe i przyrostowe. Aby uzyskać więcej informacji, zobacz [Kompilacje przyrostowe](/visualstudio/msbuild/incremental-builds).

Oprócz opcji `dotnet build` polecenie akceptuje opcje MSBuild, takie `-p` jak ustawianie `-l` właściwości lub definiowanie rejestratora. Aby uzyskać więcej informacji na temat tych opcji, zobacz [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference). Można też użyć polecenia [dotnet msbuild.](dotnet-msbuild.md)

Uruchamianie `dotnet build` jest `dotnet msbuild -restore`równoznaczne z bieganiem; jednak domyślna szczegółowość danych wyjściowych jest inna.

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Projekt lub plik rozwiązania do utworzenia. Jeśli plik projektu lub rozwiązania nie jest określony, MSBuild przeszukuje bieżący katalog roboczy dla pliku, który ma rozszerzenie pliku, który kończy się *proj* lub *sln* i używa tego pliku.

## <a name="options"></a>Opcje

- **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartość domyślna dla `Debug`większości projektów jest , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.

- **`-f|--framework <FRAMEWORK>`**

  Kompiluje dla określonej [struktury](../../standard/frameworks.md). Struktura musi być zdefiniowana w [pliku projektu](csproj.md).

- **`--force`**

  Wymusza rozwiązywanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Umożliwia zatrzymanie polecenia i oczekiwanie na wejście użytkownika lub akcję. Na przykład, aby zakończyć uwierzytelnianie. Dostępne od sdk .NET Core 3.0.

- **`--no-dependencies`**

  Ignoruje odwołania projektu do projektu (P2P) i tworzy tylko określony projekt główny.

- **`--no-incremental`**

  Oznacza kompilację jako niebezpieczną dla kompilacji przyrostowej. Ta flaga wyłącza kompilację przyrostową i wymusza czystą odbudowę wykresu zależności projektu.

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas kompilacji.

- **`--nologo`**

  Nie wyświetla banera startowego ani wiadomości o prawach autorskich. Dostępne od sdk .NET Core 3.0.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Katalog, w którym mają być umieszczane wbudowane pliki binarne. Jeśli nie zostanie określony, `./bin/<configuration>/<framework>/`ścieżka domyślna to .  W przypadku projektów z wieloma `TargetFrameworks` platformami docelowymi (za pośrednictwem właściwości) należy również zdefiniować `--framework` po określeniu tej opcji.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Określa docelowy czas wykonywania. Aby uzyskać listę identyfikatorów runtime (RID), zobacz [katalog RID](../rid-catalog.md).

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości MSBuild. Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i . Wartość domyślna to `minimal`.

- **`--version-suffix <VERSION_SUFFIX>`**

  Ustawia wartość właściwości `$(VersionSuffix)` do użycia podczas tworzenia projektu. To działa tylko `$(Version)` wtedy, gdy właściwość nie jest ustawiona. Następnie `$(Version)` jest ustawiony `$(VersionPrefix)` na połączone `$(VersionSuffix)`z , oddzielone kreską.

## <a name="examples"></a>Przykłady

- Tworzenie projektu i jego zależności:

  ```dotnetcli
  dotnet build
  ```

- Tworzenie projektu i jego zależności przy użyciu konfiguracji wersji:

  ```dotnetcli
  dotnet build --configuration Release
  ```

- Tworzenie projektu i jego zależności dla określonego czasu wykonywania (w tym przykładzie Ubuntu 18.04):

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- Skompiluj projekt i użyj określonego źródła pakietu NuGet podczas operacji przywracania (.NET Core 2.0 SDK i nowsze wersje):

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- Zbuduj projekt i ustaw wersję 1.2.3.4 jako parametr kompilacji przy użyciu `-p` opcji [MSBuild:](#msbuild)

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
