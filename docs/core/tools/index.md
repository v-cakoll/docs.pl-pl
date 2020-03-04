---
title: Interfejs wiersza polecenia platformy .NET Core
titleSuffix: ''
description: Przegląd interfejs wiersza polecenia platformy .NET Core i jego funkcji.
ms.date: 02/13/2020
ms.openlocfilehash: d84f96889cabc3fb4521e39db25050aacdd11546
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156715"
---
# <a name="net-core-cli-overview"></a>Przegląd interfejs wiersza polecenia platformy .NET Core

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

Interfejs wiersza polecenia (CLI) platformy .NET Core to Międzyplatformowy łańcucha narzędzi służący do tworzenia, kompilowania, uruchamiania i publikowania aplikacji platformy .NET Core.

Interfejs wiersza polecenia platformy .NET Core jest dołączona do [zestaw .NET Core SDK](../sdk.md). Aby dowiedzieć się, jak zainstalować zestaw .NET Core SDK, zobacz [Install the zestaw .NET Core SDK](../install/sdk.md).

## <a name="cli-commands"></a>Poleceń interfejsu wiersza polecenia

Następujące polecenia są instalowane domyślnie:

### <a name="basic-commands"></a>Polecenia podstawowe

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [utworzenia](dotnet-build.md)
- [publish](dotnet-publish.md)
- [wykonane](dotnet-run.md)
- [badan](dotnet-test.md)
- [VSTest](dotnet-vstest.md)
- [pakiet](dotnet-pack.md)
- [migrowanie](dotnet-migrate.md)
- [czyst](dotnet-clean.md)
- [sln](dotnet-sln.md)
- [Pomoc](dotnet-help.md)
- [zachować](dotnet-store.md)

### <a name="project-modification-commands"></a>Polecenia modyfikacji projektu

- [Dodaj pakiet](dotnet-add-package.md)
- [Dodaj odwołanie](dotnet-add-reference.md)
- [Usuń pakiet](dotnet-remove-package.md)
- [Usuń odwołanie](dotnet-remove-reference.md)
- [odwołanie do listy](dotnet-list-reference.md)

### <a name="advanced-commands"></a>Polecenia Zaawansowane

- [Usuwanie NuGet](dotnet-nuget-delete.md)
- [Ustawienia regionalne NuGet](dotnet-nuget-locals.md)
- [wypychanie NuGet](dotnet-nuget-push.md)
- [MSBuild](dotnet-msbuild.md)
- [skrypt instalacji dotnet](dotnet-install-script.md)

### <a name="tool-management-commands"></a>Polecenia zarządzania narzędziami

- [Instalacja narzędzia](dotnet-tool-install.md)
- [Lista narzędzi](dotnet-tool-list.md)
- [Aktualizacja narzędzia](dotnet-tool-update.md)
- dostępne [przywracanie narzędzi](global-tools.md#install-a-local-tool) **rozpoczynające się od zestaw .NET Core SDK 3,0**
- dostępne [uruchomienie narzędzia](global-tools.md#invoke-a-local-tool) **rozpoczynające się od zestaw .NET Core SDK 3,0**
- [Odinstalowywanie narzędzia](dotnet-tool-uninstall.md)

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

Aby uruchomić aplikację zależną od platformy, należy określić aplikację po sterowniku, na przykład `dotnet /path/to/my_app.dll`. Podczas wykonywania polecenia z folderu, w którym znajduje się biblioteka DLL aplikacji, wystarczy wykonać `dotnet my_app.dll`. Jeśli chcesz użyć określonej wersji środowiska uruchomieniowego platformy .NET Core, użyj opcji `--fx-version <VERSION>` (zobacz informacje dotyczące [polecenia dotnet](dotnet.md) ).

Gdy podasz polecenie do sterownika, `dotnet.exe` uruchamia proces wykonywania polecenia interfejsu CLI. Na przykład:

```dotnetcli
dotnet build
```

Najpierw sterownik Określa wersję zestawu SDK do użycia. Jeśli nie ma pliku [Global. JSON](global-json.md) , używana jest Najnowsza wersja zestawu SDK. Może to być wersja zapoznawcza lub stabilna, w zależności od tego, co jest najnowsze na komputerze.  Po ustaleniu wersji zestawu SDK wykonuje polecenie.

### <a name="command"></a>Polecenie

Polecenie wykonuje akcję. Na przykład `dotnet build` kompiluje kod. `dotnet publish` publikuje kod. Polecenia są implementowane jako Aplikacja konsolowa przy użyciu konwencji `dotnet {command}`.

### <a name="arguments"></a>Argumenty

Argumenty przekazywane do wiersza polecenia są argumentami wywoływanego polecenia. Na przykład podczas wykonywania `dotnet publish my_app.csproj`argument `my_app.csproj` wskazuje projekt do opublikowania i jest przesyłany do polecenia `publish`.

### <a name="options"></a>Opcje

Opcje, które są przekazywane w wierszu polecenia są opcje wywoływanego polecenia. Na przykład podczas wykonywania `dotnet publish --output /build_output`opcja `--output` i jej wartość są przesyłane do polecenia `publish`.

## <a name="see-also"></a>Zobacz też

- [repozytorium usługi dotnet/zestawu SDK usługi GitHub](https://github.com/dotnet/sdk/)
- [Przewodnik instalacji programu .NET Core](../install/sdk.md)
