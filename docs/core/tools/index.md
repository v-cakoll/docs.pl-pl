---
title: Interfejs wiersza polecenia platformy .NET Core
titleSuffix: ''
description: Przegląd interfejs wiersza polecenia platformy .NET Core i jego funkcji.
ms.date: 02/13/2020
ms.openlocfilehash: f92151c85b4816fef1859e84ad94945445db1854
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2020
ms.locfileid: "86415971"
---
# <a name="net-core-cli-overview"></a>Omówienie interfejsu wiersza polecenia platformy .NET Core

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

Interfejs wiersza polecenia (CLI) platformy .NET Core to Międzyplatformowy łańcucha narzędzi służący do tworzenia, kompilowania, uruchamiania i publikowania aplikacji platformy .NET Core.

Interfejs wiersza polecenia platformy .NET Core jest dołączona do [zestaw .NET Core SDK](../sdk.md). Aby dowiedzieć się, jak zainstalować zestaw .NET Core SDK, zobacz [Instalowanie programu .NET Core](../install/windows.md).

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

### <a name="advanced-commands"></a>Polecenia Zaawansowane

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a>Polecenia zarządzania narzędziami

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- [`tool restore`](global-tools.md#install-a-local-tool)Dostępne od zestaw .NET Core SDK 3,0.
- [`tool run`](global-tools.md#invoke-a-local-tool)Dostępne od zestaw .NET Core SDK 3,0.
- [`tool uninstall`](dotnet-tool-uninstall.md)

Narzędzia są aplikacjami konsolowymi, które są instalowane z pakietów NuGet i są wywoływane z wiersza polecenia. Narzędzia można pisać samodzielnie lub instalować Narzędzia zapisane przez inne firmy. Narzędzia są również nazywane narzędziami globalnymi, narzędziami ścieżki narzędzi i narzędziami lokalnymi. Aby uzyskać więcej informacji, zobacz [Narzędzia platformy .NET Core — Omówienie](global-tools.md).

## <a name="command-structure"></a>Struktura poleceń

Struktura poleceń interfejsu wiersza polecenia składa się ze [sterownika ("dotnet")](#driver), [polecenia](#command)oraz możliwych [argumentów](#arguments) i [opcji](#options)polecenia. Ten wzorzec jest widoczny w większości operacji interfejsu wiersza polecenia, takich jak tworzenie nowej aplikacji konsolowej i uruchamianie jej z poziomu wiersza poleceń, ponieważ następujące polecenia pokazują, że są wykonywane z katalogu o nazwie *my_app*:

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a>Sterownik

Sterownik nosi nazwę [dotnet](dotnet.md) i ma dwie obowiązki, uruchamiają [aplikację zależną od platformy](../deploying/index.md) lub wykonując polecenie.

Aby uruchomić aplikację zależną od platformy, należy określić aplikację po stronie sterownika, na przykład `dotnet /path/to/my_app.dll` . Gdy wykonujesz polecenie z folderu, w którym znajduje się biblioteka DLL aplikacji, po prostu wykonaj `dotnet my_app.dll` . Jeśli chcesz użyć określonej wersji środowiska uruchomieniowego platformy .NET Core, użyj `--fx-version <VERSION>` opcji (zobacz informacje dotyczące [polecenia dotnet](dotnet.md) ).

Po podaniu polecenia do sterownika program `dotnet.exe` uruchamia proces wykonywania poleceń interfejsu wiersza polecenia. Przykład:

```dotnetcli
dotnet build
```

Najpierw sterownik Określa wersję zestawu SDK do użycia. Jeśli nie ma [global.jsw](global-json.md) pliku, używana jest Najnowsza wersja zestawu SDK. Może to być wersja zapoznawcza lub stabilna, w zależności od tego, co jest najnowsze na komputerze.  Po ustaleniu wersji zestawu SDK wykonuje polecenie.

### <a name="command"></a>Polecenie

Polecenie wykonuje akcję. Na przykład `dotnet build` kompiluje kod. `dotnet publish`publikuje kod. Polecenia są implementowane jako Aplikacja konsolowa przy użyciu `dotnet {command}` Konwencji.

### <a name="arguments"></a>Argumenty

Argumenty przekazywane do wiersza polecenia są argumentami wywoływanego polecenia. Na przykład po wykonaniu `dotnet publish my_app.csproj` `my_app.csproj` argument wskazuje projekt do opublikowania i jest przesyłany do `publish` polecenia.

### <a name="options"></a>Opcje

Opcje, które są przekazywane w wierszu polecenia są opcje wywoływanego polecenia. Na przykład po wykonaniu `dotnet publish --output /build_output` `--output` opcji i jej wartości są przesyłane do `publish` polecenia.

## <a name="see-also"></a>Zobacz także

- [repozytorium usługi dotnet/zestawu SDK usługi GitHub](https://github.com/dotnet/sdk/)
- [Przewodnik instalacji programu .NET Core](../install/windows.md)
