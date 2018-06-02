---
title: Narzędzia globalne .NET core
description: Omówienie narzędzia globalne .NET Core i dostępne dla nich polecenia interfejsu wiersza polecenia platformy .NET Core.
author: KathleenDollard
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 077ffd53f1ba2988c80a637aaa109a66139736b0
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34697095"
---
# <a name="net-core-global-tools-overview"></a>Omówienie narzędzia globalne .NET core

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

Narzędzie globalne .NET Core to specjalne pakietu NuGet, który zawiera aplikację konsoli. Narzędzie globalne można zainstalować na komputerze w domyślnej lokalizacji, która jest zawarta w zmiennej środowiskowej PATH lub w lokalizacji niestandardowej.

Jeśli chcesz użyć narzędzia globalne .NET Core:

* Informacje o narzędziu (zazwyczaj witryny sieci Web lub stronie GitHub).
* Sprawdź autora i statystyki w domu dla źródła danych (zazwyczaj NuGet.org).
* Zainstaluj narzędzie.
* Wywołuje narzędzie.
* Zaktualizuj narzędzia.
* Odinstaluj narzędzie.

> [!IMPORTANT]
> Narzędzia globalne .NET core pojawiają się na ścieżce i uruchom w trybie pełnego zaufania. Nie należy instalować narzędzia globalne .NET Core, chyba że zaufania do autora.

## <a name="find-a-net-core-global-tool"></a>Znajdowanie narzędzia globalne .NET Core

Obecnie nie ma funkcji wyszukiwania globalnego narzędzia w .NET Core interfejsu wiersza polecenia (CLI).

Narzędzia globalne .NET Core można znaleźć na [NuGet](https://www.nuget.org). Jednak w NuGet wyszukiwania w szczególności .NET Core globalne narzędzi jeszcze nie zezwala.

Można również znaleźć zaleceniami w blogach lub w [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) repozytorium GitHub.

Można również Zobacz kod źródłowy dla globalnych narzędzi utworzone przez zespół ASP.NET [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) repozytorium GitHub.

## <a name="check-the-author-and-statistics"></a>Sprawdź autora i statystyki

Ponieważ .NET Core globalne narzędzia uruchamiania w trybie pełnego zaufania i są zazwyczaj instalowana na ścieżce, mogą być bardzo zaawansowane. Nie pobieraj narzędzia od osób, którym nie ufasz.

Narzędzie znajduje się na NuGet, wyszukując dla tego narzędzia można sprawdzić autorowi i statystyki.

## <a name="install-a-global-tool"></a>Zainstaluj narzędzie globalne

Aby zainstalować narzędzie globalne, należy użyć [instalacji narzędzi dotnet](dotnet-tool-install.md) polecenia interfejsu wiersza polecenia platformy .NET Core. Poniższy przykład pokazuje, jak zainstalować narzędzie globalne w domyślnej lokalizacji:

```console
dotnet tool install -g dotnetsay
```

Jeśli nie można zainstalować narzędzie, wyświetlane są komunikaty o błędach. Sprawdź, że źródła danych, które miały jest zaznaczone.

Jeśli próbujesz zainstalować wersji wstępnej lub określoną wersję narzędzia, można określić numeru wersji w następującym formacie:

```console
dotnet tool install -g <package-name> --version <version-number>
```

Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat przedstawiający polecenia używane do wywoływania narzędzia i wersją zainstalowaną, podobnie do poniższego przykładu:

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

Globalne narzędzia można zainstalować w domyślnym katalogiem lub w określonej lokalizacji. Domyślne katalogi są:

| SYSTEM OPERACYJNY          | Ścieżka                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Lokalizacje te są dodawane do ścieżki użytkownika po pierwszym uruchomieniu zestawu SDK, więc globalne narzędzia są zainstalowane, można wywołać bezpośrednio.

Należy pamiętać, że globalne narzędzia są specyficzne dla użytkownika, nie urządzenia globalnego. Trwa specyficzne dla użytkownika oznacza, że nie można zainstalować narzędzie globalne, które jest dostępna dla wszystkich użytkowników maszyny. Narzędzie jest dostępna tylko dla każdego profilu użytkownika którym zostało zainstalowane narzędzie.

Globalne narzędzia można również zainstalować z określonego katalogu. Podczas instalowania z określonego katalogu, użytkownik musi upewnić się, to polecenie jest dostępne, umieszczając ten katalog w ścieżce, przez wywołanie polecenia z określony katalog, lub narzędzie z określonego katalogu.
W takim przypadku .NET Core interfejsu wiersza polecenia nie automatycznie dodać tej lokalizacji, do zmiennej środowiskowej PATH.

## <a name="use-the-tool"></a>Użyj narzędzia

Po zainstalowaniu narzędzia można wywołać ją przy użyciu polecenia. Należy pamiętać, że polecenie nie może być taka sama jak nazwa pakietu.

Jeśli polecenie jest `dotnetsay`, za pomocą wywołania:

```console
dotnetsay
```

Jeśli narzędzie autora chciał narzędzia pojawią się w kontekście `dotnet` wierszu one może napisano go w sposób wywołać go jako `dotnet <command>`, takich jak:

```console
dotnet doc
```

Można znaleźć narzędzia znajdują się w zainstalowanym pakietem narzędzie globalne przez wyświetlanie listy zainstalowanych pakietów przy użyciu [lista narzędzi dotnet](dotnet-tool-list.md) polecenia.

Można także wyszukać instrukcje użycia w witrynie sieci Web narzędzia lub wpisując jedno z następujących poleceń:

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a>Co można udaje

Narzędzia globalnych są [aplikacje zależne od framework](../deploying/index.md#framework-dependent-deployments-fdd), co oznacza, że opierają się na podstawowego środowiska wykonawczego .NET zainstalowany na tym komputerze. Nie znaleziono oczekiwanego środowiska uruchomieniowego, należy wykonać normalnych reguł przewijaniem do środowiska wykonawczego platformy .NET Core takich jak:

* Aplikacja do przodu przedstawia do najwyższej wersji poprawki określonej wersji głównej i pomocniczej.
* Jeśli nie ma żadnych zgodnego środowiska uruchomieniowego z odpowiadającym głównych i podrzędny numer wersji, używana jest dalej nowszej wersji pomocniczej.
* Przenoszenia do przodu nie zachodzi między wersji zapoznawczych środowiska uruchomieniowego lub wersje Podgląd i wersje. W związku z tym globalnych narzędzi utworzone za pomocą wersji zapoznawczych musi można odbudować i ponownie opublikować przez autora i ponownej instalacji.
* Dodatkowe problemy mogą wystąpić z globalnego narzędzia utworzone w .NET Core 2.1 Preview 1. Aby uzyskać więcej informacji, zobacz [.NET Core 2.1 Preview 2 znane problemy](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).

Jeśli aplikacja nie może znaleźć odpowiedniego środowiska uruchomieniowego, kończy się niepowodzeniem i zgłosi błąd.

Innego problemu, który może się zdarzyć, jest, że narzędzie globalne, który został utworzony w starszej wersji zapoznawczej może nie działać z Twojej aktualnie zainstalowanego środowiska uruchomieniowe .NET Core. Możesz sprawdzić, które programy obsługi są zainstalowane na tym komputerze za pomocą następującego polecenia:

```console
dotnet --list-runtimes
```

Skontaktuj się z autorem narzędzie globalne i czy można ponownie skompilować i ponownie opublikować ich pakietu Narzędzia do NuGet z liczbą zaktualizowanej wersji. Po ich został zaktualizowany pakiet na NuGet, należy zaktualizować kopii.

Interfejsu wiersza polecenia platformy .NET Core próbuje dodać domyślne lokalizacje do zmiennej środowiskowej ŚCIEŻKA na pierwszego użycia. Jednak istnieje kilka scenariuszy, w którym lokalizacja może nie można dodać do ścieżki automatycznie, takich jak:

* Jeśli ustawiono `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` zmiennej środowiskowej.
* Na macOS, jeśli został zainstalowany przy użyciu zestawu SDK programu .NET Core *. tar.gz* plików i nie *.pkg*.
* W systemie Linux należy edytować plik środowiska powłoki, aby skonfigurować ŚCIEŻKĘ.

## <a name="other-cli-commands"></a>Inne polecenia interfejsu wiersza polecenia

.NET Core SDK zawiera inne polecenia, które obsługuje narzędzia globalne .NET Core. Użyć dowolnego z `dotnet tool` poleceń z jedną z następujących opcji:

* `--global` lub `-g` Określa, że polecenia mające zastosowanie do całej użytkownika narzędzia globalnego.
* `--tool-path` Określa niestandardową lokalizację dla globalnych narzędzi.

Aby dowiedzieć się, jakie polecenia są dostępne dla narzędzia globalne:

```console
dotnet tool --help
```

Aktualizowanie narzędzie globalne obejmuje odinstalowanie i ponowne zainstalowanie go przy użyciu najnowszej wersji stabilnej. Aby zaktualizować narzędzie globalne, użyj [aktualizacji narzędzi dotnet](dotnet-tool-update.md) polecenia:

```console
dotnet tool update -g <packagename>
```

Usuń narzędzie globalne przy użyciu [narzędzia dotnet odinstalowania](dotnet-tool-uninstall.md):

```console
dotnet tool uninstall -g <packagename>
```

Aby wyświetlić wszystkie narzędzia globalne aktualnie zainstalowane na komputerze, wraz z ich wersji i poleceń, należy użyć [lista narzędzi dotnet](dotnet-tool-list.md) polecenia:

```console
dotnet tool list -g
```