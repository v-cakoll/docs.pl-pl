---
title: Narzędzia globalnej platformy .NET core
description: Omówienie narzędzia globalnej platformy .NET Core i dostępne dla nich polecenia interfejsu wiersza polecenia platformy .NET Core.
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 29499d28629e483d66e25b8ecdbd5817effba439
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631745"
---
# <a name="net-core-global-tools-overview"></a>Omówienie narzędzia globalnej platformy .NET core

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

.NET Core globalnego narzędzie to specjalne pakietu NuGet, który zawiera aplikację konsolową w języku. Narzędzie globalne można zainstalować na komputerze w domyślnej lokalizacji, która jest dostępna w zmiennej środowiskowej PATH lub w lokalizacji niestandardowej.

Jeśli chcesz użyć narzędzia globalnego .NET Core:

* Zawiera informacje o narzędziu (zazwyczaj witryny sieci Web lub w witrynie github).
* Sprawdź, autora i statystyki w miejsce, w którym dla źródła danych (zwykle NuGet.org).
* Zainstaluj narzędzie.
* Wywołuje narzędzie.
* Zaktualizuj narzędzie.
* Odinstaluj narzędzie.

> [!IMPORTANT]
> Narzędzia globalnej platformy .NET core są wyświetlane w zmiennej path i uruchamiać w trybie pełnego zaufania. Nie należy instalować narzędzia globalnej platformy .NET Core, chyba że zaufania do autora.

## <a name="find-a-net-core-global-tool"></a>Znajdź narzędzie globalne podstawowych platformy .NET

Obecnie nie ma funkcji wyszukiwania globalnego narzędzia w konsoli .NET Core interfejsu wiersza polecenia (CLI).

Narzędzia programu .NET Core globalnej można znaleźć na [NuGet](https://www.nuget.org). Jednak NuGet jeszcze nie dopuszcza do wyszukiwania w szczególności narzędzia globalnej platformy .NET Core.

Można również znaleźć zaleceń dotyczących narzędzi do wpisów w blogu lub w [natemcmaster/dotnet-tools](https://github.com/natemcmaster/dotnet-tools) repozytorium GitHub.

Widać również kod źródłowy dla globalnych narzędzi utworzonych przez zespół programu ASP.NET w [aspnet/DotNetTools](https://github.com/aspnet/DotNetTools/) repozytorium GitHub.

## <a name="check-the-author-and-statistics"></a>Sprawdź, autora i statystyk

Ponieważ narzędzia globalnej platformy .NET Core uruchamianie w trybie pełnego zaufania i zwykle są zainstalowane w zmiennej path, może być bardzo wydajne. Nie można pobrać narzędzia od osób, którym nie ufasz.

Jeśli narzędzie jest obsługiwana dla narzędzia NuGet, możesz sprawdzić autora i statystyki, wyszukując narzędzie.

## <a name="install-a-global-tool"></a>Zainstaluj narzędzie globalne

Aby zainstalować narzędzie globalne, należy użyć [instalacji narzędzi dotnet](dotnet-tool-install.md) polecenia interfejsu wiersza polecenia platformy .NET Core. Poniższy przykład pokazuje, jak zainstalować narzędzie do globalnego w lokalizacji domyślnej:

```console
dotnet tool install -g dotnetsay
```

Jeśli nie można zainstalować narzędzia, komunikaty o błędach są wyświetlane. Sprawdź, że źródła danych, które miały są sprawdzane.

Jeśli próbujesz zainstalować wersję wstępną lub określoną wersję narzędzia, można określić numeru wersji w następującym formacie:

```console
dotnet tool install -g <package-name> --version <version-number>
```

Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat przedstawiający polecenia używane do wywoływania narzędzia i wersją zainstalowaną, podobny do poniższego przykładu:

```
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

Globalne narzędzia można zainstalować w domyślnym katalogu lub w określonej lokalizacji. Domyślne katalogi są następujące:

| System operacyjny          | Ścieżka                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Te lokalizacje są dodawane do ścieżki użytkownika podczas pierwszego uruchomienia zestaw SDK, więc globalnego narzędzia są zainstalowane, może być wywoływana bezpośrednio.

Należy zauważyć, że globalne narzędzia specyficzne dla użytkownika, nie machine globalnego. Są specyficzne dla użytkownika oznacza, że nie można zainstalować narzędzie globalne, która jest dostępna dla wszystkich użytkowników komputera. Narzędzie jest dostępne tylko dla każdego profilu użytkownika którym zostało zainstalowane narzędzie.

Można również zainstalować narzędzia globalnej w określonym katalogu. Podczas instalowania w określonym katalogu, użytkownik musi upewnić się polecenie jest dostępne, umieszczając tego katalogu w ścieżce, wywołując polecenie z katalogu, który został określony, lub podczas wywoływania narzędzia z w określonym katalogu.
W tym przypadku interfejsu wiersza polecenia platformy .NET Core nie powoduje dodania tej lokalizacji automatycznie do zmiennej środowiskowej PATH.

## <a name="use-the-tool"></a>Za pomocą narzędzia

Po zainstalowaniu narzędzia można wywoływać ją za pomocą polecenia. Należy zauważyć, że polecenie nie może być taka sama jak nazwa pakietu.

Jeśli polecenie jest `dotnetsay`, należy wywołać za pomocą:

```console
dotnetsay
```

Jeśli autor narzędzie potrzebowała narzędzie, które pojawią się w kontekście `dotnet` wierszu one napisał ją w taki sposób, nadaj mu `dotnet <command>`, takich jak:

```console
dotnet doc
```

Możesz znaleźć, jakie narzędzia są objęte zainstalowanego pakietu narzędzie globalne, wyświetlając listę zainstalowanych pakietów przy użyciu [lista narzędzi dotnet](dotnet-tool-list.md) polecenia.

Można także wyszukać instrukcje użycia w witrynie sieci Web narzędzia lub wpisując jedno z następujących poleceń:

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a>Co można pójdzie nie tak

Narzędzia globalne są [zależny od struktury aplikacji](../deploying/index.md#framework-dependent-deployments-fdd), co oznacza, że opierają się na środowisko uruchomieniowe platformy .NET Core zainstalowana na tym komputerze. Oczekiwany czas działania nie zostanie znaleziony, należy wykonać normalnego reguły przodu środowisko uruchomieniowe platformy .NET Core takich jak:

* Aplikacja przenosi do przodu do najwyższej wersji poprawki określonej wersji głównych i pomocniczych.
* Jeśli nie ma żadnych pasujących aparatu plików wykonywalnych dopasowania główne i pomocniczy numer wersji, dalej wyższa wersja pomocnicza jest używany.
* Przenoszenia do przodu nie zachodzi między wersji zapoznawczych środowiska uruchomieniowego lub wersji zapoznawczych i wersji. W związku z tym, globalne narzędzia utworzone za pomocą wersji zapoznawczych musi być odbudować i ponowne opublikowanie przez autora i ponownej instalacji.
* Dodatkowe problemy dotyczące za pomocą narzędzi globalnego utworzone w .NET Core 2.1 w wersji zapoznawczej 1. Aby uzyskać więcej informacji, zobacz [.NET Core 2.1 w wersji zapoznawczej 2 — znane problemy](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md).

Jeśli aplikacja nie może znaleźć odpowiedniego środowiska uruchomieniowego, uruchomienie nie powiedzie się i zgłasza błąd.

Inny problem, który może się zdarzyć, to narzędzie globalne, który został utworzony w starszej wersji zapoznawczej może nie działać z Twojego aktualnie zainstalowanego środowiska uruchomieniowe platformy .NET Core. Możesz zobaczyć, które środowiska uruchomieniowe są zainstalowane na komputerze przy użyciu następującego polecenia:

```console
dotnet --list-runtimes
```

Skontaktuj się z autorem narzędzie globalne i czy można ponownie skompilować i ponownie opublikować ich pakiet narzędzi do narzędzia NuGet ze zaktualizowanym numerem wersji. Po zaktualizowaniu one pakietów dla narzędzia NuGet, należy zaktualizować kopii.

Interfejs wiersza polecenia platformy .NET Core próbuje dodać domyślne lokalizacje do zmiennej środowiskowej PATH na pierwszego użycia. Jednak istnieje kilka scenariuszy, w których lokalizacja może nie można dodać do ścieżki automatycznie, takich jak:

* Jeśli ustawiono `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` zmiennej środowiskowej.
* W systemie macOS, jeśli została zainstalowana przy użyciu zestawu .NET Core SDK *. tar.gz* plików i nie *.pkg*.
* W systemie Linux należy edytować plik środowiska powłoki, aby skonfigurować ŚCIEŻKĘ.

## <a name="other-cli-commands"></a>Inne polecenia interfejsu wiersza polecenia

.NET Core SDK zawiera innych poleceń, które obsługują narzędzia globalnej platformy .NET Core. Użyć dowolnej z `dotnet tool` poleceń przy użyciu jednego z następujących opcji:

* `--global` lub `-g` Określa, że polecenie jest zastosowanie do całej użytkownika narzędzia globalnej.
* `--tool-path` Określa niestandardową lokalizację dla narzędzia globalnej.

Aby dowiedzieć się, jakie polecenia są dostępne dla narzędzia globalnej:

```console
dotnet tool --help
```

Aktualizowanie narzędzie globalne obejmuje odinstalowanie i ponowne zainstalowanie go za pomocą najnowszej stabilnej wersji. Aby zaktualizować narzędzie globalne, użyj [aktualizacji narzędzi dotnet](dotnet-tool-update.md) polecenia:

```console
dotnet tool update -g <packagename>
```

Usuń narzędzie globalne przy użyciu [narzędzia dotnet odinstalowania](dotnet-tool-uninstall.md):

```console
dotnet tool uninstall -g <packagename>
```

Aby wyświetlić wszystkie narzędzia globalnej aktualnie jest zainstalowana na komputerze, wraz z ich wersji i poleceń, użyj [lista narzędzi dotnet](dotnet-tool-list.md) polecenia:

```console
dotnet tool list -g
```
