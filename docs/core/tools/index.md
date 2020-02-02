---
title: Interfejs wiersza polecenia platformy .NET Core
titleSuffix: ''
description: Przegląd interfejs wiersza polecenia platformy .NET Core i jego funkcji.
ms.date: 08/14/2017
ms.openlocfilehash: b0a8e0dd8cf77bb6f7567c27e9972f62515ec0f2
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920483"
---
# <a name="net-core-cli-overview"></a>Przegląd interfejs wiersza polecenia platformy .NET Core

Interfejs wiersza polecenia (CLI) platformy .NET Core to Międzyplatformowy łańcucha narzędzi służący do tworzenia, kompilowania, uruchamiania i publikowania aplikacji platformy .NET Core.

Interfejs wiersza polecenia platformy .NET Core jest dołączona do [zestaw .NET Core SDK](../sdk.md). Aby dowiedzieć się, jak zainstalować zestaw .NET Core SDK, zobacz [Install the zestaw .NET Core SDK](../install/sdk.md).

## <a name="cli-commands"></a>Poleceń interfejsu wiersza polecenia

Następujące polecenia są instalowane domyślnie:

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**Polecenia podstawowe**

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [utworzenia](dotnet-build.md)
- [publish](dotnet-publish.md)
- [run](dotnet-run.md)
- [badan](dotnet-test.md)
- [VSTest](dotnet-vstest.md)
- [pakiet](dotnet-pack.md)
- [dokonać](dotnet-migrate.md)
- [czyst](dotnet-clean.md)
- [sln](dotnet-sln.md)
- [Pomoc](dotnet-help.md)
- [zachować](dotnet-store.md)

**Polecenia modyfikacji projektu**

- [Dodaj pakiet](dotnet-add-package.md)
- [Dodaj odwołanie](dotnet-add-reference.md)
- [Usuń pakiet](dotnet-remove-package.md)
- [Usuń odwołanie](dotnet-remove-reference.md)
- [odwołanie do listy](dotnet-list-reference.md)

**Polecenia Zaawansowane**

- [Usuwanie NuGet](dotnet-nuget-delete.md)
- [Ustawienia regionalne NuGet](dotnet-nuget-locals.md)
- [wypychanie NuGet](dotnet-nuget-push.md)
- [msbuild](dotnet-msbuild.md)
- [skrypt instalacji dotnet](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**Polecenia podstawowe**

- [new](dotnet-new.md)
- [restore](dotnet-restore.md)
- [utworzenia](dotnet-build.md)
- [publish](dotnet-publish.md)
- [run](dotnet-run.md)
- [badan](dotnet-test.md)
- [VSTest](dotnet-vstest.md)
- [pakiet](dotnet-pack.md)
- [dokonać](dotnet-migrate.md)
- [czyst](dotnet-clean.md)
- [sln](dotnet-sln.md)

**Polecenia modyfikacji projektu**

- [Dodaj pakiet](dotnet-add-package.md)
- [Dodaj odwołanie](dotnet-add-reference.md)
- [Usuń pakiet](dotnet-remove-package.md)
- [Usuń odwołanie](dotnet-remove-reference.md)
- [odwołanie do listy](dotnet-list-reference.md)

**Polecenia Zaawansowane**

- [Usuwanie NuGet](dotnet-nuget-delete.md)
- [Ustawienia regionalne NuGet](dotnet-nuget-locals.md)
- [wypychanie NuGet](dotnet-nuget-push.md)
- [msbuild](dotnet-msbuild.md)
- [skrypt instalacji dotnet](dotnet-install-script.md)

---

Interfejs wiersza polecenia przyjmuje model rozszerzalności, który pozwala określić dodatkowe narzędzia dla projektów. Aby uzyskać więcej informacji, zobacz temat dotyczący [modelu rozszerzalności interfejs wiersza polecenia platformy .NET Core](extensibility.md) .

## <a name="command-structure"></a>Struktura poleceń

Struktura poleceń interfejsu wiersza polecenia składa się ze [sterownika ("dotnet")](#driver), [polecenia](#command)oraz możliwych [argumentów](#arguments) i [opcji](#options)polecenia. Ten wzorzec jest widoczny w większości operacji interfejsu wiersza polecenia, takich jak tworzenie nowej aplikacji konsolowej i uruchamianie jej z poziomu wiersza poleceń, ponieważ następujące polecenia pokazują, że są wykonywane z katalogu o nazwie *my_app*:

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a>Sterownik

Sterownik nosi nazwę [dotnet](dotnet.md) i ma dwie obowiązki, uruchamiają [aplikację zależną od platformy](../deploying/index.md) lub wykonując polecenie. 

Aby uruchomić aplikację zależną od platformy, należy określić aplikację po sterowniku, na przykład `dotnet /path/to/my_app.dll`. Podczas wykonywania polecenia z folderu, w którym znajduje się biblioteka DLL aplikacji, wystarczy wykonać `dotnet my_app.dll`. Jeśli chcesz użyć określonej wersji środowiska uruchomieniowego platformy .NET Core, użyj opcji `--fx-version <VERSION>` (zobacz informacje dotyczące [polecenia dotnet](dotnet.md) ).

Gdy podasz polecenie do sterownika, `dotnet.exe` uruchamia proces wykonywania polecenia interfejsu CLI. Na przykład:

```dotnetcli
dotnet build
```

Najpierw sterownik Określa wersję zestawu SDK do użycia. Jeśli nie ma pliku ["Global. JSON"](global-json.md), używana jest Najnowsza wersja zestawu SDK. Może to być wersja zapoznawcza lub stabilna, w zależności od tego, co jest najnowsze na komputerze.  Po ustaleniu wersji zestawu SDK wykonuje polecenie.

### <a name="command"></a>Polecenie

Polecenie wykonuje akcję. Na przykład `dotnet build` kompiluje kod. `dotnet publish` publikuje kod. Polecenia są implementowane jako Aplikacja konsolowa przy użyciu konwencji `dotnet {command}`.

### <a name="arguments"></a>Argumenty

Argumenty przekazywane do wiersza polecenia są argumentami wywoływanego polecenia. Na przykład podczas wykonywania `dotnet publish my_app.csproj`argument `my_app.csproj` wskazuje projekt do opublikowania i jest przesyłany do polecenia `publish`.

### <a name="options"></a>Opcje

Opcje, które są przekazywane w wierszu polecenia są opcje wywoływanego polecenia. Na przykład podczas wykonywania `dotnet publish --output /build_output`opcja `--output` i jej wartość są przesyłane do polecenia `publish`.

## <a name="migration-from-projectjson"></a>Migracja z pliku Project. JSON

Jeśli użyto narzędzi w wersji zapoznawczej 2 do tworzenia projektów opartych na pliku *Project. JSON*, zapoznaj się z tematem Migrowanie środowiska [dotnet](dotnet-migrate.md) , aby uzyskać informacje na temat migrowania projektu do programu MSBuild/ *. csproj* do użytku z narzędziami Release. W przypadku projektów .NET Core utworzonych przed udostępnieniem narzędzi wersji zapoznawczej 2 należy ręcznie zaktualizować projekt zgodnie ze wskazówkami zawartymi w sekcji [Migrowanie z środowiska DNX do interfejs wiersza polecenia platformy .NET Core (Project. JSON)](../migration/from-dnx.md) , a następnie użyć `dotnet migrate` lub bezpośrednio uaktualnić projekty.

## <a name="see-also"></a>Zobacz także

- [repozytorium usługi dotnet/zestawu SDK usługi GitHub](https://github.com/dotnet/sdk/)
- [Przewodnik instalacji programu .NET Core](https://aka.ms/dotnetcoregs)
