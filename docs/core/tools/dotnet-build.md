---
title: polecenie kompilacji dotnet
description: Polecenie kompilacji dotnet kompiluje projekt i wszystkie jego zależności.
ms.date: 02/14/2020
ms.openlocfilehash: 9f9a78ec0a6a25c54c8a727c05081ce6835514ee
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503765"
---
# <a name="dotnet-build"></a>dotnet build

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji

## <a name="name"></a>Name (Nazwa)

`dotnet build` — kompiluje projekt i wszystkie jego zależności.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force]
    [--interactive] [--no-dependencies] [--no-incremental] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a>Opis

`dotnet build` polecenie kompiluje projekt i jego zależności do zestawu plików binarnych. Pliki binarne zawierają kod projektu w plikach języka pośredniego (IL) z rozszerzeniem *. dll* .  W zależności od typu projektu i ustawień można uwzględnić inne pliki, takie jak:

- Plik wykonywalny, który może służyć do uruchamiania aplikacji, jeśli typem projektu jest plik wykonywalny przeznaczony dla platformy .NET Core 3,0 lub nowszego.
- Pliki symboli używane do debugowania z rozszerzeniem *. pdb* .
- Plik *. deps. JSON* , który zawiera listę zależności aplikacji lub biblioteki.
- Plik *. runtimeconfig. JSON* , który określa udostępnione środowisko uruchomieniowe i jego wersję dla aplikacji.
- Inne biblioteki, od których zależy projekt (za pośrednictwem odwołań projektu lub pakietów NuGet).

W przypadku projektów wykonywalnych przeznaczonych dla wersji wcześniejszej niż .NET Core 3,0, zależności biblioteki z NuGet nie są zwykle kopiowane do folderu wyjściowego.  Są one rozpoznawane z folderu pakietów globalnych NuGet w czasie wykonywania. Z tego względu produkt `dotnet build` nie jest gotowy do przeniesienia na inną maszynę do uruchomienia. Aby utworzyć wersję aplikacji, którą można wdrożyć, należy ją opublikować (na przykład przy użyciu polecenia [dotnet Publish](dotnet-publish.md) ). Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).

W przypadku projektów wykonywalnych przeznaczonych dla platformy .NET Core 3,0 i nowszych zależności biblioteki są kopiowane do folderu wyjściowego. Oznacza to, że jeśli nie ma żadnej innej logiki specyficznej dla publikacji (takiej jak projekty sieci Web), dane wyjściowe kompilacji powinny być możliwe do wdrożenia.

Kompilowanie wymaga pliku *Project. assets. JSON* , który zawiera listę zależności aplikacji. Plik jest tworzony podczas wykonywania [`dotnet restore`](dotnet-restore.md) . Bez pliku zasobów na miejscu narzędzia nie mogą rozpoznać zestawów referencyjnych, które powodują błędy. Przy użyciu zestawu SDK platformy .NET Core 1. x musisz jawnie uruchomić `dotnet restore` przed uruchomieniem `dotnet build`. Począwszy od zestawu SDK programu .NET Core 2,0, `dotnet restore` uruchamiane niejawnie podczas uruchamiania `dotnet build`. Aby wyłączyć niejawne przywracanie podczas wykonywania polecenia Build, można przekazać opcję `--no-restore`.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

Czy projekt jest plikiem wykonywalnym, czy nie jest określony przez właściwość `<OutputType>` w pliku projektu. W poniższym przykładzie przedstawiono projekt tworzący kod wykonywalny:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Aby utworzyć bibliotekę, Pomiń Właściwość `<OutputType>` lub zmień jej wartość na `Library`. Biblioteka DLL IL dla biblioteki nie zawiera punktów wejścia i nie można jej wykonać.

### <a name="msbuild"></a>MSBuild

`dotnet build` używa programu MSBuild do kompilowania projektu, aby obsługiwał kompilacje równoległe i przyrostowe. Aby uzyskać więcej informacji, zobacz [Kompilacje przyrostowe](/visualstudio/msbuild/incremental-builds).

Oprócz opcji, polecenie `dotnet build` akceptuje Opcje programu MSBuild, takie jak `-p` do ustawiania właściwości lub `-l` w celu zdefiniowania rejestratora. Aby uzyskać więcej informacji na temat tych opcji, zobacz [informacje dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). Lub można również użyć polecenia programu [dotnet MSBuild](dotnet-msbuild.md) .

Uruchamianie `dotnet build` jest równoważne działaniu `dotnet msbuild -restore`; jednak domyślny poziom szczegółowości danych wyjściowych jest inny.

## <a name="arguments"></a>Argumenty

`PROJECT | SOLUTION`

Plik projektu lub rozwiązania do skompilowania. Jeśli plik projektu lub rozwiązania nie zostanie określony, program MSBuild przeszukuje bieżący katalog roboczy dla pliku, który ma rozszerzenie pliku, które kończy się w *proj* lub *sln* i używa tego pliku.

## <a name="options"></a>Opcje

- **`-c|--configuration <CONFIGURATION>`**

  Definiuje konfigurację kompilacji. Wartość domyślna dla większości projektów jest `Debug`, ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.

- **`-f|--framework <FRAMEWORK>`**

  Kompiluje dla określonej [struktury](../../standard/frameworks.md). Struktura musi być zdefiniowana w [pliku projektu](csproj.md).

- **`--force`**

  Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie. Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję. Na przykład, aby ukończyć uwierzytelnianie. Dostępne od wersji .NET Core 3,0 SDK.

- **`--no-dependencies`**

  Ignoruje odwołania między projektami i projektami (P2P) i kompiluje tylko określony projekt główny.

- **`--no-incremental`**

  Oznacza kompilację jako niebezpieczną dla kompilacji przyrostowej. Ta flaga powoduje wyłączenie kompilacji przyrostowej i wymuszenie czystej odbudowy wykresu zależności projektu.

- **`--no-restore`**

  Nie wykonuje przywracania niejawnego podczas kompilacji.

- **`--nologo`**

  Nie wyświetla transparentu początkowego ani komunikatu o prawach autorskich. Dostępne od wersji .NET Core 3,0 SDK.

- **`-o|--output <OUTPUT_DIRECTORY>`**

  Katalog, w którym mają zostać umieszczone skompilowane pliki binarne. Jeśli nie zostanie określony, domyślną ścieżką jest `./bin/<configuration>/<framework>/`.  W przypadku projektów z wieloma platformami docelowymi (za pomocą właściwości `TargetFrameworks`) należy również zdefiniować `--framework` po określeniu tej opcji.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Określa docelowy środowisko uruchomieniowe. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości programu MSBuild. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Wartość domyślna to `minimal`.

- **`--version-suffix <VERSION_SUFFIX>`**

  Ustawia wartość właściwości `$(VersionSuffix)`, która ma być używana podczas kompilowania projektu. Działa to tylko wtedy, gdy właściwość `$(Version)` nie jest ustawiona. Następnie `$(Version)` jest ustawiony na `$(VersionPrefix)` połączony z `$(VersionSuffix)`rozdzielony kreską.

## <a name="examples"></a>Przykłady

- Kompiluj projekt i jego zależności:

  ```dotnetcli
  dotnet build
  ```

- Kompilowanie projektu i jego zależności przy użyciu konfiguracji wydania:

  ```dotnetcli
  dotnet build --configuration Release
  ```

- Kompiluj projekt i jego zależności dla określonego środowiska uruchomieniowego (w tym przykładzie Ubuntu 18,04):

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- Kompiluj projekt i Użyj określonego źródła pakietu NuGet podczas operacji przywracania (zestaw .NET Core 2,0 SDK i nowsze wersje):

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- Skompiluj projekt i ustaw wersję 1.2.3.4 jako parametr kompilacji przy użyciu [opcji `-p` MSBuild](#msbuild):

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
