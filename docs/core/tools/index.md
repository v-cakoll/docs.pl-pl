---
title: Interfejs wiersza polecenia platformy .NET Core
titleSuffix: ''
description: Omówienie cli .NET Core i jego funkcji.
ms.date: 02/13/2020
ms.openlocfilehash: 45a40063f70a621e807abf5e01ceecb125aecd7c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399120"
---
# <a name="net-core-cli-overview"></a>Omówienie procesora CLI programu .NET Core

**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji

Interfejs wiersza polecenia .NET Core (CLI) jest wieloplatformowym łańcuchem narzędzi do tworzenia, tworzenia, uruchamiania i publikowania aplikacji .NET Core.

Wartość .NET Core CLI jest dołączona do [sdk .NET Core .](../sdk.md) Aby dowiedzieć się, jak zainstalować zestaw SDK .NET Core, zobacz [Instalowanie sdk .NET Core .](../install/sdk.md)

## <a name="cli-commands"></a>Polecenia wiersza polecenia

Domyślnie instalowane są następujące polecenia:

### <a name="basic-commands"></a>Podstawowe polecenia

- [`new`](dotnet-new.md)
- [`restore`](dotnet-restore.md)
- [`build`](dotnet-build.md)
- [`publish`](dotnet-publish.md)
- [`run`](dotnet-run.md)
- [`test`](dotnet-test.md)
- [`vstest`](dotnet-vstest.md)
- [`pack`](dotnet-pack.md)
- [`migrate`](dotnet-migrate.md)
- [`clean`](dotnet-clean.md)
- [`sln`](dotnet-sln.md)
- [`help`](dotnet-help.md)
- [`store`](dotnet-store.md)

### <a name="project-modification-commands"></a>Polecenia modyfikacji projektu

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a>Polecenia zaawansowane

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a>Polecenia zarządzania narzędziami

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- [`tool restore`](global-tools.md#install-a-local-tool)Dostępne od .NET Core SDK 3.0.
- [`tool run`](global-tools.md#invoke-a-local-tool)Dostępne od .NET Core SDK 3.0.
- [`tool uninstall`](dotnet-tool-uninstall.md)

Narzędzia są aplikacje konsoli, które są instalowane z pakietów NuGet i są wywoływane z wiersza polecenia. Możesz samodzielnie pisać narzędzia lub instalować narzędzia napisane przez osoby trzecie. Narzędzia są również znane jako narzędzia globalne, narzędzia ścieżki narzędziowej i narzędzia lokalne. Aby uzyskać więcej informacji, zobacz [omówienie narzędzi .NET Core](global-tools.md).

## <a name="command-structure"></a>Struktura poleceń

Struktura polecenia CLI składa się ze [sterownika ("dotnet"),](#driver) [polecenia](#command)i ewentualnie [argumentów](#arguments) poleceń i [opcji](#options). Ten wzorzec jest wyświetlana w większości operacji wiersza polecenia, takich jak tworzenie nowej aplikacji konsoli i uruchamianie jej z wiersza polecenia, zgodnie z poniższymi poleceniami, które są wyświetlane podczas wykonywania z katalogu o nazwie *my_app:*

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a>Sterownik

Sterownik nosi nazwę [dotnet](dotnet.md) i ma dwa obowiązki, uruchamiając [aplikację zależną od struktury](../deploying/index.md) lub wykonując polecenie.

Aby uruchomić aplikację zależną od struktury, określ aplikację `dotnet /path/to/my_app.dll`po sterowniku, na przykład . Podczas wykonywania polecenia z folderu, w którym znajduje się `dotnet my_app.dll`dll aplikacji, wystarczy wykonać . Jeśli chcesz użyć określonej wersji programu .NET Core Runtime, użyj `--fx-version <VERSION>` tej opcji (zobacz odwołanie do polecenia [dotnet).](dotnet.md)

Po dostarczeniu polecenia `dotnet.exe` do sterownika uruchamia proces wykonywania polecenia WIERSZA. Przykład:

```dotnetcli
dotnet build
```

Po pierwsze, sterownik określa wersję sdk do użycia. Jeśli nie ma pliku [global.json,](global-json.md) używana jest najnowsza dostępna wersja sdk. Może to być wersja zapoznawcza lub stabilna, w zależności od tego, co jest najnowsze na komputerze.  Po ustaleniu wersji sdk wykonuje polecenie.

### <a name="command"></a>Polecenie

Polecenie wykonuje akcję. Na przykład `dotnet build` tworzy kod. `dotnet publish`publikuje kod. Polecenia są implementowane jako aplikacja konsoli `dotnet {command}` przy użyciu konwencji.

### <a name="arguments"></a>Argumenty

Argumenty, które przekazujesz w wierszu polecenia są argumentami do wywołanych polecenia. Na przykład podczas `dotnet publish my_app.csproj`wykonywania `my_app.csproj` , argument wskazuje projekt do `publish` opublikowania i jest przekazywany do polecenia.

### <a name="options"></a>Opcje

Opcje, które przekazujesz w wierszu polecenia, są opcjami wywołanych polecenia. Na przykład podczas `dotnet publish --output /build_output`wykonywania, `--output` opcja i jej `publish` wartość są przekazywane do polecenia.

## <a name="see-also"></a>Zobacz też

- [Repozytorium GitHub dotnet/sdk](https://github.com/dotnet/sdk/)
- [Przewodnik instalacji programu .NET Core](../install/sdk.md)
