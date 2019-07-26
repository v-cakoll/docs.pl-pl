---
title: polecenie kompilacji dotnet
description: Polecenie kompilacji dotnet kompiluje projekt i wszystkie jego zależności.
ms.date: 04/24/2019
ms.openlocfilehash: db2c859529d3dd21d2cd43445419b99a4256b42e
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331059"
---
# <a name="dotnet-build"></a>dotnet build

**Ten artykuł dotyczy: ✓** .NET Core 1. x SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet build`-Kompiluje projekt i wszystkie jego zależności.

## <a name="synopsis"></a>Streszczenie

```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--nologo] [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a>Opis

`dotnet build` Polecenie kompiluje projekt i jego zależności do zestawu plików binarnych. Pliki binarne zawierają kod projektu w plikach języka pośredniego (IL) z rozszerzeniem *. dll* i plikami symboli używanymi do debugowania z rozszerzeniem *. pdb* . Tworzony jest plik JSON zależności ( *. deps. JSON*), który zawiera listę zależności aplikacji. Tworzony jest plik *. runtimeconfig. JSON* , który określa udostępnione środowisko uruchomieniowe i jego wersję dla aplikacji.

Jeśli projekt zawiera zależności innych firm, takie jak biblioteki z NuGet, są one rozpoznawane z pamięci podręcznej NuGet i nie są dostępne z skompilowanymi danymi wyjściowymi projektu. Z tego względu `dotnet build` produkt nie jest gotowy do przeniesienia na inną maszynę do uruchomienia. Jest to w przeciwieństwie do zachowania .NET Framework, w którym Kompilowanie projektu wykonywalnego (aplikacji) generuje dane wyjściowe, które są możliwy do uruchomienia na dowolnym komputerze, na którym zainstalowano .NET Framework. Aby korzystać z podobnego środowiska z platformą .NET Core, należy użyć polecenia [dotnet Publish](dotnet-publish.md) . Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).

Kompilowanie wymaga pliku *Project. assets. JSON* , który zawiera listę zależności aplikacji. Plik jest tworzony, gdy [`dotnet restore`](dotnet-restore.md) jest wykonywany. Bez pliku zasobów na miejscu narzędzia nie mogą rozpoznać zestawów referencyjnych, które powodują błędy. Przy użyciu zestawu SDK platformy .NET Core 1. x należy jawnie uruchomić `dotnet restore` program przed uruchomieniem. `dotnet build` Począwszy od zestawu SDK platformy .NET Core `dotnet restore` 2,0, jest uruchamiany niejawnie podczas uruchamiania. `dotnet build` Aby wyłączyć niejawne przywracanie podczas wykonywania polecenia Build, można przekazać `--no-restore` opcję.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

Czy projekt jest plikiem wykonywalnym, czy nie jest określony `<OutputType>` przez właściwość w pliku projektu. W poniższym przykładzie przedstawiono projekt tworzący kod wykonywalny:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Aby utworzyć bibliotekę, należy pominąć `<OutputType>` właściwość. Główną różnicą w skompilowanych danych wyjściowych jest to, że biblioteka IL DLL biblioteki nie zawiera punktów wejścia i nie można jej wykonać.

### <a name="msbuild"></a>MSBuild

`dotnet build`używa programu MSBuild do skompilowania projektu, aby obsługiwał kompilacje równoległe i przyrostowe. Aby uzyskać więcej informacji, [](/visualstudio/msbuild/incremental-builds)Zobacz Kompilacje przyrostowe.

Oprócz opcji, `dotnet build` polecenie akceptuje Opcje programu MSBuild, takie jak `-p` właściwości ustawienia lub `-l` definiowania rejestratora. Aby uzyskać więcej informacji na temat tych opcji, zobacz [informacje dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). Lub można również użyć polecenia programu [dotnet MSBuild](dotnet-msbuild.md) .

Uruchomiona `dotnet build` jest równoważna `dotnet msbuild -restore -target:Build`z.

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Plik projektu lub rozwiązania do skompilowania. Jeśli plik projektu lub rozwiązania nie zostanie określony, program MSBuild przeszukuje bieżący katalog roboczy dla pliku, który ma rozszerzenie pliku, które kończy się w *proj* lub *sln* i używa tego pliku.

## <a name="options"></a>Opcje

* **`-c|--configuration {Debug|Release}`**

  Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

* **`-f|--framework <FRAMEWORK>`**

  Kompiluje dla określonej [struktury](../../standard/frameworks.md). Struktura musi być zdefiniowana w [pliku projektu](csproj.md).

* **`--force`**

  Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* . Dostępne od wersji .NET Core 2,0 SDK.

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

* **`--interactive`**

  Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję. Na przykład, aby ukończyć uwierzytelnianie. Dostępne od wersji .NET Core 3,0 SDK.

* **`--no-dependencies`**

  Ignoruje odwołania między projektami i projektami (P2P) i kompiluje tylko określony projekt główny.

* **`--no-incremental`**

  Oznacza kompilację jako niebezpieczną dla kompilacji przyrostowej. Ta flaga powoduje wyłączenie kompilacji przyrostowej i wymuszenie czystej odbudowy wykresu zależności projektu.

* **`--no-logo`**

  Nie wyświetla transparentu początkowego ani komunikatu o prawach autorskich. Dostępne od wersji .NET Core 3,0 SDK.

* **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas kompilacji. Dostępne od wersji .NET Core 2,0 SDK.

* **`-o|--output <OUTPUT_DIRECTORY>`**

  Katalog, w którym mają zostać umieszczone skompilowane pliki binarne. Należy również zdefiniować `--framework` po określeniu tej opcji. Jeśli nie zostanie określony, ścieżka domyślna to `./bin/<configuration>/<framework>/`.

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Określa docelowy środowisko uruchomieniowe. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).

* **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości programu MSBuild. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]` Wartość domyślna to `minimal`.

* **`--version-suffix <VERSION_SUFFIX>`**

  Ustawia wartość `$(VersionSuffix)` właściwości, która ma być używana podczas kompilowania projektu. Działa to tylko wtedy, `$(Version)` gdy właściwość nie jest ustawiona. Następnie jest ustawiona `$(VersionPrefix)` na połączone z `$(VersionSuffix)`, oddzielone kreską. `$(Version)`

## <a name="examples"></a>Przykłady

* Kompiluj projekt i jego zależności:

  ```console
  dotnet build
  ```

* Kompilowanie projektu i jego zależności przy użyciu konfiguracji wydania:

  ```console
  dotnet build --configuration Release
  ```

* Kompiluj projekt i jego zależności dla określonego środowiska uruchomieniowego (w tym przykładzie Ubuntu 18,04):

  ```console
  dotnet build --runtime ubuntu.18.04-x64
  ```

* Kompiluj projekt i Użyj określonego źródła pakietu NuGet podczas operacji przywracania (zestaw .NET Core 2,0 SDK i nowsze wersje):

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* Skompiluj projekt i ustaw wersję 1.2.3.4 jako parametr kompilacji przy użyciu `-p` [opcji MSBuild](#msbuild):

  ```console
  dotnet build -p:Version=1.2.3.4
  ```
