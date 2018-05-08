---
title: DotNet kompilacji command - .NET Core interfejsu wiersza polecenia
description: Dotnet kompilacji polecenie kompilacji projektu i wszystkie jego zależności.
author: mairaw
ms.author: mairaw
ms.date: 03/10/2018
ms.openlocfilehash: 4fc93e013c271fdf856f5c73affffd3880d0dbea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dotnet-build"></a>dotnet-build

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet build` -Tworzy projekt i wszystkie jego zależności.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
---

## <a name="description"></a>Opis

`dotnet build` Polecenie kompilacji projektu i jego zależności do zestawu plików binarnych. Pliki binarne zawiera kod projektu w języku pośrednim (IL) pliki z *.dll* plików symboli i rozszerzenia, które są używane do debugowania z *.pdb* rozszerzenia. Plik JSON zależności (*\*. deps.json*) jest tworzony który znajduje się wykaz zależności aplikacji. A  *\*. runtimeconfig.json* jest generowany, określającej udostępnionego środowiska uruchomieniowego i wersja aplikacji.

Jeśli projekt zawiera zależności innych firm, takich jak biblioteki z pakietu NuGet, jest rozwiązany z pamięci podręcznej NuGet i nie są dostępne z skompilowanych danych wyjściowych projektu. Z tym pamiętać iloczyn `dotnet build` nie jest gotowa do przeniesienia na inny komputer, aby uruchomić. Dzięki temu nie trzeba zachowanie programu .NET Framework w budynku, który projekt wykonywalny (aplikacja) tworzy dane wyjściowe do uruchomienia na dowolnym komputerze z zainstalowanym programu .NET Framework. Aby podobne możliwości z platformą .NET Core, musisz użyć [publikowania dotnet](dotnet-publish.md) polecenia. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).

Kompilowanie wymaga *project.assets.json* pliku, który zawiera listę zależności aplikacji. Podczas tworzenia pliku [ `dotnet restore` ](dotnet-restore.md) jest wykonywana. Bez miejscowej pliku zasobów narzędzia nie można rozpoznać zestawy referencyjne zakończyło się z błędami. Z platformą .NET Core uruchom 1.x zestawu SDK, trzeba było explicitily `dotnet restore` przed uruchomieniem `dotnet build`. Począwszy od platformy .NET Core SDK 2.0, `dotnet restore` uruchamia implicitily po uruchomieniu `dotnet build`. Jeśli chcesz wyłączyć niejawne przywracania podczas wykonywania poleceń kompilacji, można przekazać `--no-restore` opcji.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

`dotnet build` korzysta z programu MSBuild w celu skompilowania projektu; w związku z tym obsługuje ona zarówno równoległe, jak i przyrostowe kompilacji. Zapoznaj się [kompilacje przyrostowe](/visualstudio/msbuild/incremental-builds) Aby uzyskać więcej informacji.

Oprócz jego opcje `dotnet build` polecenie akceptuje opcje MSBuild `/p` do ustawiania właściwości lub `/l` do definiowania rejestrator. Dowiedz się więcej o tych opcjach w [dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference). 

Określa, czy projekt jest wykonywalne, lub nie jest określany przez `<OutputType>` właściwość w pliku projektu. W poniższym przykładzie przedstawiono projekt, który utworzy kodu wykonywalnego:

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

Aby można było utworzyć bibliotekę, Pomiń `<OutputType>` właściwości. Główna różnica w skompilowanych danych wyjściowych jest nie zawiera punktów wejścia biblioteki DLL IL dla biblioteki oraz nie może zostać wykonana. 

## <a name="arguments"></a>Argumenty

`PROJECT`

Plik projektu do kompilacji. Jeśli nie określono pliku projektu, MSBuild wyszukuje bieżącego katalogu roboczego dla pliku, który ma rozszerzenie pliku, który kończy się *proj* i używa tego pliku.

## <a name="options"></a>Opcje

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Kompiluje z określonym [framework](../../standard/frameworks.md). Platformę musi być zdefiniowana w [pliku projektu](csproj.md).

`--force`

 Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie. Jest to równoważne usuwanie *project.assets.json* pliku.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`--no-dependencies`

Ignoruje odwołuje się do projektu do projektu (P2P) i tylko kompilacje główny projekt określony do kompilacji.

`--no-incremental`

Oznaczenie kompilacji jako niebezpieczny dla kompilacji przyrostowej. To powoduje wyłączenie kompilacji przyrostowej i wymusza czystą kompilowania wykresu zależności projektu.

`--no-restore`

Nie wykonać przywracanie niejawne podczas kompilacji.

`-o|--output <OUTPUT_DIRECTORY>`

Katalog, w którym można umieścić skompilowanych plików binarnych. Należy również określić `--framework` po określeniu tej opcji.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Określa docelowe środowisko uruchomieniowe. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Określa sufiks wersji gwiazdkę (`*`) w polu wersja pliku projektu. Format jest zgodny wytyczne wersja narzędzia NuGet.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

Definiuje konfigurację kompilacji. Wartość domyślna to `Debug`.

`-f|--framework <FRAMEWORK>`

Kompiluje z określonym [framework](../../standard/frameworks.md). Platformę musi być zdefiniowana w [pliku projektu](csproj.md).

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`--no-dependencies`

Ignoruje odwołuje się do projektu do projektu (P2P) i tylko kompilacje główny projekt określony do kompilacji.

`--no-incremental`

Oznaczenie kompilacji jako niebezpieczny dla kompilacji przyrostowej. To powoduje wyłączenie kompilacji przyrostowej i wymusza czystą kompilowania wykresu zależności projektu.

`-o|--output <OUTPUT_DIRECTORY>`

Katalog, w którym można umieścić skompilowanych plików binarnych. Należy również określić `--framework` po określeniu tej opcji.

`-r|--runtime <RUNTIME_IDENTIFIER>`

Określa docelowe środowisko uruchomieniowe. Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.

`--version-suffix <VERSION_SUFFIX>`

Określa sufiks wersji gwiazdkę (`*`) w polu wersja pliku projektu. Format jest zgodny wytyczne wersja narzędzia NuGet.

---

## <a name="examples"></a>Przykłady

Tworzenie projektu i jego zależności:

`dotnet build`

Tworzenie projektu i jego zależności za pomocą wersji konfiguracji:

`dotnet build --configuration Release`

Tworzenie projektu i jego zależności dla określonego środowiska uruchomieniowego (w tym przykładzie Ubuntu 16.04):

`dotnet build --runtime ubuntu.16.04-x64`

Skompiluj projekt i użyj określone źródło pakietu NuGet podczas operacji przywracania (.NET Core SDK 2.0 i nowsze wersje):

`dotnet build --source c:\packages\mypackages`