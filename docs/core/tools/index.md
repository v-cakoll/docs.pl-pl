---
title: Narzędzia interfejsu wiersza polecenia (CLI) platformy .NET Core
description: Omówienie narzędzi i funkcji interfejsu wiersza polecenia (CLI) platformy .NET Core.
ms.date: 08/14/2017
ms.custom: seodec18
ms.openlocfilehash: 50d1bbdd87ecd275b97603a1b47c6f13f879365a
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70969877"
---
# <a name="net-core-command-line-interface-cli-tools"></a>Narzędzia interfejsu wiersza polecenia (CLI) platformy .NET Core

Interfejs wiersza polecenia platformy .NET Core (CLI) to nowe Międzyplatformowe łańcucha narzędzi do tworzenia aplikacji platformy .NET. Interfejs wiersza polecenia jest podstawą, na której można zawiesić narzędzia wyższego poziomu, takie jak zintegrowane środowiska deweloperskie (środowisk IDE), Edytory i koordynatorzy kompilacji.

## <a name="installation"></a>Instalacja

Użyj natywnych instalatorów lub użyj skryptów powłoki instalacji:

- Natywne Instalatory są używane przede wszystkim na maszynach deweloperskich i używają natywnego mechanizmu instalacji na platformie, na przykład DEB pakiety w pakietach Ubuntu i MSI w systemie Windows. Te Instalatory instalują i konfigurują środowisko do natychmiastowego użytku przez dewelopera, ale wymagają uprawnień administracyjnych na komputerze. Instrukcje dotyczące instalacji można wyświetlić w [podręczniku instalacji programu .NET Core](https://aka.ms/dotnetcoregs).
- Skrypty powłoki są używane głównie do konfigurowania serwerów kompilacji lub do instalowania narzędzi bez uprawnień administracyjnych. Skrypty instalacji nie instalują wstępnie wymaganych składników na komputerze, które należy zainstalować ręcznie. Aby uzyskać więcej informacji, zobacz [temat informacje o skrypcie instalacji](dotnet-install-script.md). Aby uzyskać informacje na temat sposobu konfigurowania interfejsu wiersza polecenia na serwerze kompilacji ciągłej integracji (CI), zobacz [używanie zestaw .NET Core SDK i narzędzi w ciągłej integracji (ci)](using-ci-with-cli.md).

Domyślnie interfejs wiersza polecenia jest instalowany w sposób równoległy (SxS), dzięki czemu wiele wersji narzędzi interfejsu wiersza polecenia może współistnieć na jednej maszynie. Określanie, która wersja jest używana na komputerze, na którym zainstalowano wiele wersji, wyjaśniono bardziej szczegółowo w sekcji [sterownika](#driver) .

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

```console
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a>Sterownik

Sterownik nosi nazwę [dotnet](dotnet.md) i ma dwie obowiązki, uruchamiają [aplikację zależną od platformy](../deploying/index.md) lub wykonując polecenie. 

Aby uruchomić aplikację zależną od platformy, należy określić aplikację po stronie sterownika, na przykład `dotnet /path/to/my_app.dll`. Gdy wykonujesz polecenie z folderu, w którym znajduje się biblioteka DLL aplikacji, po prostu wykonaj `dotnet my_app.dll`. Jeśli chcesz użyć określonej wersji środowiska uruchomieniowego platformy .NET Core, użyj `--fx-version <VERSION>` opcji (zobacz informacje dotyczące [polecenia dotnet](dotnet.md) ).

Po podaniu polecenia do sterownika program `dotnet.exe` uruchamia proces wykonywania poleceń interfejsu wiersza polecenia. Na przykład:

```bash
> dotnet build
```

Najpierw sterownik Określa wersję zestawu SDK do użycia. Jeśli nie ma pliku ["Global. JSON"](global-json.md), używana jest Najnowsza wersja zestawu SDK. Może to być wersja zapoznawcza lub stabilna, w zależności od tego, co jest najnowsze na komputerze.  Po ustaleniu wersji zestawu SDK wykonuje polecenie.

### <a name="command"></a>Polecenie

Polecenie wykonuje akcję. Na przykład `dotnet build` kompiluje kod. `dotnet publish`publikuje kod. Polecenia są implementowane jako Aplikacja konsolowa przy użyciu `dotnet {command}` Konwencji.

### <a name="arguments"></a>Argumenty

Argumenty przekazywane do wiersza polecenia są argumentami wywoływanego polecenia. Na przykład podczas wykonywania `dotnet publish my_app.csproj` `my_app.csproj` argument wskazuje projekt do opublikowania `publish` i jest przesyłany do polecenia.

### <a name="options"></a>Opcje

Opcje, które są przekazywane w wierszu polecenia są opcje wywoływanego polecenia. Na przykład podczas wykonywania `dotnet publish --output /build_output` `--output` , opcja i jej `publish` wartość są przesyłane do polecenia.

## <a name="migration-from-projectjson"></a>Migracja z pliku Project. JSON

Jeśli użyto narzędzi w wersji zapoznawczej 2 do tworzenia projektów opartych na pliku *Project. JSON*, zapoznaj się z tematem Migrowanie środowiska [dotnet](dotnet-migrate.md) , aby uzyskać informacje na temat migrowania projektu do programu MSBuild/ *. csproj* do użytku z narzędziami Release. W przypadku projektów .NET Core utworzonych przed wydaniem narzędzia do wersji zapoznawczej 2 należy ręcznie zaktualizować projekt zgodnie ze wskazówkami zawartymi w sekcji [Migrowanie z środowiska DNX do interfejs wiersza polecenia platformy .NET Core (Project. JSON)](../migration/from-dnx.md) , a następnie użyć `dotnet migrate` lub bezpośrednio uaktualnić projekty.

## <a name="see-also"></a>Zobacz także

- [Repozytorium dotnet/CLI usługi GitHub](https://github.com/dotnet/cli/)
- [Przewodnik instalacji programu .NET Core](https://aka.ms/dotnetcoregs)
