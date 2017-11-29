---
title: "Narzędzia programu .NET core interfejsu wiersza polecenia (CLI)"
description: "Przegląd funkcji i narzędzi .NET Core interfejsu wiersza polecenia (CLI)."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: d66738593a1542affc956e08bbc38a3b2b1841b9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="net-core-command-line-interface-cli-tools"></a>Oprogramowanie .NET core narzędzi interfejsu wiersza polecenia (CLI)

Oprogramowanie .NET Core interfejsu wiersza polecenia (CLI) jest nowy łańcuch między platformami narzędzi do tworzenia aplikacji .NET. Interfejsu wiersza polecenia jest foundation na narzędzia wyższego poziomu, takie jak zintegrowane środowisk deweloperskich (IDE), edytory i orchestrators kompilacji można rest.

## <a name="installation"></a>Instalacja

Użyj natywnego instalatorów lub korzystać ze skryptów powłoki instalacji:

* Natywnego pliki instalacyjne są używane przede wszystkim na komputerach deweloperów i natywnego za każdym obsługiwane platformy Zainstaluj mechanizm, na przykład DEB pakietów na funkcji MSI lub Ubuntu pakietów w systemie Windows. Te pliki instalacyjne zainstalować i skonfigurować środowisko do użycia przez dewelopera, ale wymagają uprawnień administratora na komputerze. Można wyświetlić w instrukcjach dotyczących instalacji w [Przewodnik instalacji platformy .NET Core](https://aka.ms/dotnetcoregs).
* Skryptów powłoki są używane przede wszystkim dotyczące konfigurowania serwery kompilacji lub gdy chcesz zainstalować narzędzia bez uprawnień administracyjnych. Zainstaluj skrypty wymagania wstępne nie należy instalować na komputerze, który należy zainstalować ręcznie. Aby uzyskać więcej informacji, zobacz [zainstalować temat referencyjny skryptu](dotnet-install-script.md). Aby uzyskać informacje na temat Konfigurowanie interfejsu wiersza polecenia na serwerze kompilacji ciągłej integracji (CI), zobacz [przy użyciu programu .NET Core SDK i narzędzia w ciągłej integracji (CI)](using-ci-with-cli.md).

Domyślnie interfejsu wiersza polecenia instalacji w sposób side-by-side (SxS) tak wielu wersji narzędzi interfejsu wiersza polecenia mogą współistnieć na jednym komputerze. Określanie, która wersja jest używana na komputerze, którym zainstalowano kilka wersji to co omówiono bardziej szczegółowo w [sterownika](#driver) sekcji.

## <a name="cli-commands"></a>Polecenia interfejsu wiersza polecenia

Domyślnie instalowane są następujące polecenia:

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

**Podstawowe polecenia**

* [Nowy](dotnet-new.md)
* [Przywracanie](dotnet-restore.md)
* [kompilacji](dotnet-build.md)
* [Publikowanie](dotnet-publish.md)
* [Uruchom](dotnet-run.md)
* [Test](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [pakiet](dotnet-pack.md)
* [Migracja](dotnet-migrate.md)
* [czyszczenie](dotnet-clean.md)
* [SLN](dotnet-sln.md)
* [Pomoc](dotnet-help.md)
* [Magazyn](dotnet-store.md)

**Polecenia modyfikacji projektu**

* [Dodaj pakiet](dotnet-add-package.md)
* [Dodaj odwołanie](dotnet-add-reference.md)
* [Usunięcie pakietu](dotnet-remove-package.md)
* [Usuwanie odwołań](dotnet-remove-reference.md)
* [Odwołanie do listy](dotnet-list-reference.md)

**Zaawansowane poleceń**

* [Usuń nuget](dotnet-nuget-delete.md)
* [Zmienne lokalne nuget](dotnet-nuget-locals.md)
* [wypychania nuget](dotnet-nuget-push.md)
* [MSBUILD](dotnet-msbuild.md)
* [skrypt instalacji DotNet](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

**Podstawowe polecenia**

* [Nowy](dotnet-new.md)
* [Przywracanie](dotnet-restore.md)
* [kompilacji](dotnet-build.md)
* [Publikowanie](dotnet-publish.md)
* [Uruchom](dotnet-run.md)
* [Test](dotnet-test.md)
* [vstest](dotnet-vstest.md)
* [pakiet](dotnet-pack.md)
* [Migracja](dotnet-migrate.md)
* [czyszczenie](dotnet-clean.md)
* [SLN](dotnet-sln.md)

**Polecenia modyfikacji projektu**

* [Dodaj pakiet](dotnet-add-package.md)
* [Dodaj odwołanie](dotnet-add-reference.md)
* [Usunięcie pakietu](dotnet-remove-package.md)
* [Usuwanie odwołań](dotnet-remove-reference.md)
* [Odwołanie do listy](dotnet-list-reference.md)

**Zaawansowane poleceń**

* [Usuń nuget](dotnet-nuget-delete.md)
* [Zmienne lokalne nuget](dotnet-nuget-locals.md)
* [wypychania nuget](dotnet-nuget-push.md)
* [MSBUILD](dotnet-msbuild.md)
* [skrypt instalacji DotNet](dotnet-install-script.md)

---

Interfejsu wiersza polecenia przyjmuje modelu rozszerzalności, która pozwala na określenie dodatkowych narzędzi dla projektów. Aby uzyskać więcej informacji, zobacz [modelu rozszerzalności interfejsu wiersza polecenia platformy .NET Core](extensibility.md) tematu.

## <a name="command-structure"></a>Polecenie — struktura

Struktura polecenia interfejsu wiersza polecenia składa się z [sterownika ("dotnet")](#driver), [polecenia (lub "zlecenie")](#command-verb)oraz prawdopodobnie poleceń [argumenty](#arguments) i [opcje](#options). Zobacz tego wzorca w większości operacji interfejsu wiersza polecenia, takie jak tworzenie nowej aplikacji konsoli i uruchomiony z wiersza polecenia jako następujące polecenia, Pokaż podczas wykonywania z katalogu o nazwie *moja_aplikacja*:

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

```console
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```


---

### <a name="driver"></a>Sterownik

O nazwie sterownik [dotnet](dotnet.md) i ma dwa obowiązki, każda uruchomiona [aplikacji zależnych od framework](../deploying/index.md) lub wykonywania polecenia. Tylko `dotnet` jest używana bez jest polecenie, gdy jest używany do uruchomienia aplikacji.

Uruchamianie aplikacji zależnych od framework, należy określić aplikację po sterowników, na przykład `dotnet /path/to/my_app.dll`. Podczas wykonywania polecenia z folderu, w którym znajduje się aplikacji DLL, po prostu wykonać `dotnet my_app.dll`.

Jeśli podasz polecenia do sterownika, `dotnet.exe` rozpoczyna się proces wykonywania polecenia interfejsu wiersza polecenia. Po pierwsze sterownika Określa wersję zestawu SDK do użycia. Jeśli wersja nie jest określona w opcji polecenia, sterownik używa najnowszej dostępnej wersji. Aby określić wersję niż najnowszej zainstalowanej wersji, użyj `--fx-version <VERSION>` opcji (zobacz [polecenia dotnet](dotnet.md) odwołania). Po określeniu zestawu SDK w wersji sterownika wykonuje polecenie.

### <a name="command-verb"></a>Polecenie ("zlecenie")

Polecenie (lub "zlecenie") jest po prostu polecenie, które wykonuje akcję. Na przykład `dotnet build` kompilacji kodu. `dotnet publish`publikuje kodu. Polecenia są zaimplementowane jako aplikacji konsoli przy użyciu `dotnet {verb}` Konwencji.

### <a name="arguments"></a>Argumenty

Argumenty przekazywane w wierszu polecenia są argumenty polecenia wywoływane. Na przykład podczas wykonywania `dotnet publish my_app.csproj`, `my_app.csproj` argument wskazuje projektu do publikowania i jest przekazywana do `publish` polecenia.

### <a name="options"></a>Opcje

Opcje do polecenia wywoływane są opcje przebiegu w wierszu polecenia. Na przykład podczas wykonywania `dotnet publish --output /build_output`, `--output` opcji i jej wartość są przekazywane do `publish` polecenia. 

## <a name="migration-from-projectjson"></a>Migracja z pliku project.json

Jeśli używana wersja zapoznawcza 2 narzędzi do tworzenia *project.json*— na podstawie projektów, zapoznaj się [migracji dotnet](dotnet-migrate.md) tematu zawiera informacje na temat migracji projektu do MSBuild /*.csproj*do użytku z wersji narzędzi. Dla projektów .NET Core utworzone przed w wersji Preview 2 narzędzi, albo ręcznie zaktualizować projektu, postępując zgodnie ze wskazówkami w [migracji ze środowiska DNX .NET Core interfejsu wiersza polecenia (project.json)](../migration/from-dnx.md) , a następnie użyj `dotnet migrate` lub bezpośrednio Uaktualnij swoje projekty.

## <a name="see-also"></a>Zobacz także

 [DotNet/CLI repozytorium GitHub](https://github.com/dotnet/cli/)  
 [Przewodnik instalacji platformy .NET core](https://aka.ms/dotnetcoregs)  