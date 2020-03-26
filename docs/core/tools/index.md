---
title: Interfejs wiersza polecenia platformy .NET Core
titleSuffix: ''
description: Omówienie interfejsu wiersza polecenia .NET Core i jego funkcji.
ms.date: 02/13/2020
ms.openlocfilehash: ac5988bacbef41326f2501a2cff6c3f5aa0be798
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110844"
---
# <a name="net-core-cli-overview"></a>Omówienie interfejsu wiersza polecenia platformy .NET Core

**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach

Interfejs wiersza polecenia .NET Core (CLI) to wieloplatformowy toolchain do tworzenia, tworzenia, uruchamiania i publikowania aplikacji .NET Core.

Plik .NET Core CLI jest dołączony do [interfejsu SDK .NET Core](../sdk.md). Aby dowiedzieć się, jak zainstalować pakiet .NET Core SDK, zobacz [Instalowanie pakietu .NET Core SDK](../install/sdk.md).

## <a name="cli-commands"></a>Polecenia interfejsu wiersza polecenia

Następujące polecenia są instalowane domyślnie:

### <a name="basic-commands"></a>Polecenia podstawowe

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

### <a name="advanced-commands"></a>Zaawansowane polecenia

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

Narzędzia są aplikacje konsoli, które są instalowane z pakietów NuGet i są wywoływane z wiersza polecenia. Możesz samodzielnie napisać narzędzia lub zainstalować narzędzia napisane przez osoby trzecie. Narzędzia są również nazywane narzędziami globalnymi, narzędziami ścieżki narzędzi i narzędziami lokalnymi. Aby uzyskać więcej informacji, zobacz [omówienie narzędzi .NET Core](global-tools.md).

## <a name="command-structure"></a>Struktura poleceń

Struktura poleceń interfejsu wiersza polecenia składa się ze [sterownika ("dotnet")](#driver), [polecenia](#command)i ewentualnie [argumentów](#arguments) i [opcji](#options)polecenia. Ten wzorzec jest widoczny w większości operacji interfejsu wiersza polecenia, takich jak tworzenie nowej aplikacji konsoli i uruchamianie jej z wiersza polecenia, jak pokazują następujące polecenia podczas wykonywania z katalogu o nazwie *my_app:*

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a>Sterownik

Sterownik nosi nazwę [dotnet](dotnet.md) i ma dwa obowiązki, albo z uruchomionym [aplikacją zależną od struktury,](../deploying/index.md) albo wykonując polecenie.

Aby uruchomić aplikację zależną od struktury, określ aplikację `dotnet /path/to/my_app.dll`po sterowniku, na przykład . Podczas wykonywania polecenia z folderu, w którym znajduje się biblioteka DLL aplikacji, wystarczy wykonać `dotnet my_app.dll`. Jeśli chcesz użyć określonej wersji środowiska uruchomieniowego .NET Core, użyj `--fx-version <VERSION>` tej opcji (zobacz odwołanie do polecenia [dotnet).](dotnet.md)

Po podaniu polecenia do `dotnet.exe` sterownika, rozpoczyna proces wykonywania polecenia interfejsu wiersza polecenia. Przykład:

```dotnetcli
dotnet build
```

Najpierw sterownik określa wersję sdk do użycia. Jeśli nie ma pliku [global.json,](global-json.md) używana jest najnowsza wersja sdk. Może to być wersja zapoznawcza lub stabilna, w zależności od tego, co jest najnowsze na komputerze.  Po określeniu wersji SDK wykonuje polecenie.

### <a name="command"></a>Polecenie

Polecenie wykonuje akcję. Na przykład `dotnet build` tworzy kod. `dotnet publish`publikuje kod. Polecenia są implementowane jako aplikacja konsoli `dotnet {command}` przy użyciu konwencji.

### <a name="arguments"></a>Argumenty

Argumenty przekazywane w wierszu polecenia są argumentami do wywoływanego polecenia. Na przykład podczas `dotnet publish my_app.csproj`wykonywania `my_app.csproj` argument wskazuje projekt do opublikowania i `publish` jest przekazywany do polecenia.

### <a name="options"></a>Opcje

Opcje przekazywane w wierszu polecenia są opcjami wywoływanym poleceniem. Na przykład podczas `dotnet publish --output /build_output`wykonywania `--output` , opcja i jej `publish` wartość są przekazywane do polecenia.

## <a name="see-also"></a>Zobacz też

- [repozytorium Dotnet/Sdk GitHub](https://github.com/dotnet/sdk/)
- [Przewodnik instalacji .NET Core](../install/sdk.md)
