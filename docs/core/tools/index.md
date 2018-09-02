---
title: Narzędzia programu .NET core interfejsu wiersza polecenia (CLI)
description: Przegląd funkcji i narzędzi .NET Core interfejsu wiersza polecenia (CLI).
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.openlocfilehash: 0ef69f98171da98b50aae4cdd2f5f88f37ad0c63
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43403409"
---
# <a name="net-core-command-line-interface-cli-tools"></a>Narzędzia interfejsu wiersza polecenia (CLI) platformy .NET core

Interfejsu wiersza polecenia (CLI) platformy .NET Core to nowe łańcucha narzędzi i platform do tworzenia aplikacji .NET. Interfejs wiersza polecenia jest podstawę, na które narzędzia wyższego poziomu, takie jak umieścić zintegrowanych środowisk projektowych (IDE), edytory i koordynatorów kompilacji.

## <a name="installation"></a>Instalacja

Użyj natywnych instalatorów lub za pomocą skryptów powłoki instalacji:

* Natywnych instalatorów są używane przede wszystkim na maszynach dewelopera i natywne za każdym obsługiwanych platform Zainstaluj mechanizm, na przykład DEB pakiety na pakiety MSI lub Ubuntu na Windows. Te pliki instalacyjne zainstalować i skonfigurować środowisko do użycia przez dewelopera, ale wymagają uprawnień administratora na komputerze. Możesz wyświetlić instrukcje dotyczące instalacji w [Przewodnik instalacji platformy .NET Core](https://aka.ms/dotnetcoregs).
* Skrypty powłoki są głównie używane do konfigurowania serwerów kompilacji lub gdy chcesz zainstalować narzędzia bez uprawnień administracyjnych. Zainstaluj skrypty wymagań wstępnych nie należy instalować na komputerze, który musi zostać zainstalowany ręcznie. Aby uzyskać więcej informacji, zobacz [zainstalować temat referencyjny skryptu](dotnet-install-script.md). Aby uzyskać informacji na temat sposobu konfigurowania interfejsu wiersza polecenia na serwerze kompilacji ciągłej integracji (CI), zobacz [przy użyciu zestawu .NET Core SDK i narzędzia w ciągłej integracji (CI)](using-ci-with-cli.md).

Domyślnie interfejs wiersza polecenia instaluje w sposób side-by-side (SxS) tak wielu wersji narzędzi interfejsu wiersza polecenia mogą współistnieć na jednym komputerze. Określenie, która wersja jest używana na komputerze, gdzie jest zainstalowanych wiele wersji zostało wyjaśnione bardziej szczegółowo w [sterownika](#driver) sekcji.

## <a name="cli-commands"></a>Polecenia interfejsu wiersza polecenia

Następujące polecenia są instalowane domyślnie:

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

**Podstawowe polecenia**

* [new](dotnet-new.md)
* [restore](dotnet-restore.md)
* [Kompilacja](dotnet-build.md)
* [publish](dotnet-publish.md)
* [run](dotnet-run.md)
* [Test](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [pakiet](dotnet-pack.md)
* [Migracja](dotnet-migrate.md)
* [czyszczenie](dotnet-clean.md)
* [sln](dotnet-sln.md)
* [Pomoc](dotnet-help.md)
* [Store](dotnet-store.md)

**Polecenia modyfikacji projektu**

* [Dodaj pakiet](dotnet-add-package.md)
* [Dodawanie odwołania](dotnet-add-reference.md)
* [Usuń pakiet](dotnet-remove-package.md)
* [Usuwanie odwołań](dotnet-remove-reference.md)
* [Odwołanie do listy](dotnet-list-reference.md)

**Zaawansowane polecenia**

* [Usuń nuget](dotnet-nuget-delete.md)
* [Zmienne lokalne nuget](dotnet-nuget-locals.md)
* [nuget wypychania](dotnet-nuget-push.md)
* [msbuild](dotnet-msbuild.md)
* [skrypt instalacji DotNet](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

**Podstawowe polecenia**

* [new](dotnet-new.md)
* [restore](dotnet-restore.md)
* [Kompilacja](dotnet-build.md)
* [publish](dotnet-publish.md)
* [run](dotnet-run.md)
* [Test](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [pakiet](dotnet-pack.md)
* [Migracja](dotnet-migrate.md)
* [czyszczenie](dotnet-clean.md)
* [sln](dotnet-sln.md)

**Polecenia modyfikacji projektu**

* [Dodaj pakiet](dotnet-add-package.md)
* [Dodawanie odwołania](dotnet-add-reference.md)
* [Usuń pakiet](dotnet-remove-package.md)
* [Usuwanie odwołań](dotnet-remove-reference.md)
* [Odwołanie do listy](dotnet-list-reference.md)

**Zaawansowane polecenia**

* [Usuń nuget](dotnet-nuget-delete.md)
* [Zmienne lokalne nuget](dotnet-nuget-locals.md)
* [nuget wypychania](dotnet-nuget-push.md)
* [msbuild](dotnet-msbuild.md)
* [skrypt instalacji DotNet](dotnet-install-script.md)

---

Interfejs wiersza polecenia przyjmuje model rozszerzeń, który umożliwia określenie dodatkowych narzędzi dla projektów. Aby uzyskać więcej informacji, zobacz [modelu rozszerzeń interfejsu wiersza polecenia platformy .NET Core](extensibility.md) tematu.

## <a name="command-structure"></a>Struktura polecenia

Struktura polecenia interfejsu wiersza polecenia składa się z [sterownika ("dotnet")](#driver), [polecenie (lub "verb")](#command-verb)i ewentualnie polecenia [argumenty](#arguments) i [opcje](#options). Zostanie wyświetlony ten wzorzec w przypadku większości operacji interfejsu wiersza polecenia, takie jak tworzenie nowej aplikacji konsoli i uruchamiając go z poziomu wiersza polecenia jako następujące polecenia, Pokaż podczas wykonywania z katalogu o nazwie *moja_aplikacja*:

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

Nosi nazwę sterownika [dotnet](dotnet.md) i ma dwa odpowiedzialności, albo uruchamianie [zależny od struktury aplikacji](../deploying/index.md) lub wykonywania polecenia. Jedyną sytuacją `dotnet` jest używany bez jest poleceniem, gdy jest używany do uruchomienia aplikacji.

Uruchamianie aplikacji zależny od struktury, na przykład określić aplikację po sterownika, `dotnet /path/to/my_app.dll`. Podczas wykonywania polecenia z folderu, w którym znajduje się biblioteki DLL z aplikacji, po prostu wykonaj `dotnet my_app.dll`.

Podczas dostarczania polecenia do sterownika, `dotnet.exe` rozpoczyna się proces wykonywania polecenia interfejsu wiersza polecenia. Po pierwsze sterownik Określa wersję zestawu SDK do użycia. Jeśli wersja nie jest określona w opcji polecenia, sterownik używa najnowsza dostępna wersja. Aby określić wersję innego niż jego Najnowsza zainstalowana wersja, należy użyć `--fx-version <VERSION>` opcji (zobacz [polecenia dotnet](dotnet.md) odwołania). Po określeniu wersji zestawu SDK sterownik wykonuje polecenie.

### <a name="command-verb"></a>Polecenie ("verb")

Polecenie (lub "verb") jest po prostu polecenie, które wykonują akcję. Na przykład `dotnet build` kompiluje kod. `dotnet publish` publikuje swój kod. Polecenia są implementowane jako aplikacji konsoli za pomocą `dotnet {verb}` Konwencji.

### <a name="arguments"></a>Argumenty

Argumenty, które należy przekazać w wierszu polecenia są argumenty polecenia wywoływane. Na przykład podczas wykonywania `dotnet publish my_app.csproj`, `my_app.csproj` argument określa projekt do publikowania i jest przekazywany do `publish` polecenia.

### <a name="options"></a>Opcje

Opcje, które należy przekazać w wierszu polecenia są opcje polecenia wywoływane. Na przykład podczas wykonywania `dotnet publish --output /build_output`, `--output` opcję i jej wartość są przekazywane do `publish` polecenia.

## <a name="migration-from-projectjson"></a>Migracja z pliku project.json

Jeśli używasz narzędzia do tworzenia w wersji 2 *project.json*— na podstawie projektów, zapoznaj się z [migracji dotnet](dotnet-migrate.md) zawiera informacje na temat migracji projektu do programu MSBuild /*.csproj*do użytku z wersji narzędzia. Dla platformy .NET Core projektów utworzonych przed wydaniem narzędzi w wersji 2, ręcznie zaktualizować projekt, postępując zgodnie ze wskazówkami w [migrowanie ze środowiska DNX, .NET Core interfejsu wiersza polecenia (project.json)](../migration/from-dnx.md) , a następnie użyj `dotnet migrate` lub bezpośrednio uaktualnienia Twoich projektów.

## <a name="see-also"></a>Zobacz także

* [/ interfejsu wiersza polecenia DotNet repozytorium GitHub](https://github.com/dotnet/cli/)  
* [Przewodnik instalacji platformy .NET core](https://aka.ms/dotnetcoregs)  
