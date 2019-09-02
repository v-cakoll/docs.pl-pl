---
title: Narzędzia globalne platformy .NET Core
description: Omówienie narzędzi globalnych platformy .NET Core i dostępnych dla nich poleceń interfejs wiersza polecenia platformy .NET Core.
author: KathleenDollard
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 9ff7e33a50eb0c5fb649b44dda6d72412a134584
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202593"
---
# <a name="net-core-global-tools-overview"></a>Globalne narzędzia platformy .NET Core — Omówienie

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

Narzędzie globalne platformy .NET Core jest specjalnym pakietem NuGet, który zawiera aplikację konsolową. Narzędzie globalne można zainstalować na komputerze w lokalizacji domyślnej, która jest uwzględniona w zmiennej środowiskowej PATH lub w lokalizacji niestandardowej.

Jeśli chcesz użyć globalnego narzędzia platformy .NET Core:

* Znajdź informacje o narzędziu (zazwyczaj witryna sieci Web lub GitHub).
* Sprawdź autora i statystyki na stronie głównej kanału informacyjnego (zwykle NuGet.org).
* Zainstaluj narzędzie.
* Wywoływanie narzędzia.
* Zaktualizuj narzędzie.
* Odinstaluj narzędzie.

> [!IMPORTANT]
> Narzędzia globalne platformy .NET Core są wyświetlane na ścieżce i działają w trybie pełnego zaufania. Nie instaluj podstawowych narzędzi platformy .NET Core, chyba że ufasz autorowi.

## <a name="find-a-net-core-global-tool"></a>Znajdź narzędzie globalne platformy .NET Core

Obecnie nie istnieje funkcja globalnego wyszukiwania narzędzi w interfejsie wiersza polecenia (CLI) platformy .NET Core.

Narzędzia platformy .NET Core można znaleźć na platformie [NuGet](https://www.nuget.org). Jednak pakiet NuGet nie zezwala jeszcze na wyszukiwanie dla narzędzi globalnych platformy .NET Core.

Zalecenia dotyczące narzędzi można także znaleźć w wpisach w blogu lub w repozytorium GitHub [natemcmaster/dotnet-Tools](https://github.com/natemcmaster/dotnet-tools) .

Możesz również wyświetlić kod źródłowy narzędzi globalnych utworzonych przez zespół ASP.NET w repozytorium GitHub [/DotNetTools](https://github.com/aspnet/DotNetTools/) .

## <a name="check-the-author-and-statistics"></a>Sprawdź autora i statystyki

Ponieważ globalne narzędzia platformy .NET Core działają w pełni zaufane i są zwykle instalowane na ścieżce, mogą być bardzo wydajne. Nie pobieraj narzędzi z osób, które nie są zaufane.

Jeśli narzędzie jest hostowane w usłudze NuGet, można sprawdzić autora i statystyk, wyszukując narzędzie.

## <a name="install-a-global-tool"></a>Instalowanie narzędzia globalnego

Aby zainstalować narzędzie globalne, należy użyć [Narzędzia dotnet zainstaluj](dotnet-tool-install.md) interfejs wiersza polecenia platformy .NET Core polecenie. Poniższy przykład pokazuje, jak zainstalować narzędzie globalne w lokalizacji domyślnej:

```console
dotnet tool install -g dotnetsay
```

Jeśli nie można zainstalować narzędzia, zostaną wyświetlone komunikaty o błędach. Sprawdź, czy wybrane źródła danych są sprawdzane.

Jeśli próbujesz zainstalować wersję wstępną lub określoną wersję narzędzia, możesz określić numer wersji w następującym formacie:

```console
dotnet tool install -g <package-name> --version <version-number>
```

Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat z poleceniem, które służy do wywoływania narzędzia i zainstalowanej wersji, podobnie jak w poniższym przykładzie:

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

Narzędzia globalne można zainstalować w katalogu domyślnym lub w określonej lokalizacji. Domyślne katalogi są następujące:

| OS          | Ścieżka                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Te lokalizacje są dodawane do ścieżki użytkownika podczas pierwszego uruchomienia zestawu SDK, dzięki czemu globalne narzędzia mogą być wywoływane bezpośrednio.

Należy pamiętać, że globalne narzędzia to specyficzne dla użytkownika, a nie globalne maszyny. Specyficzne dla użytkownika oznacza, że nie można zainstalować narzędzia globalnego, które jest dostępne dla wszystkich użytkowników komputera. Narzędzie jest dostępne tylko dla każdego profilu użytkownika, w którym zainstalowano narzędzie.

Narzędzia globalne można także zainstalować w określonym katalogu. Po zainstalowaniu w określonym katalogu użytkownik musi upewnić się, że polecenie jest dostępne, dołączając ten katalog w ścieżce, wywołując polecenie z określonym katalogiem lub wywołując narzędzie z w określonym katalogu.
W takim przypadku interfejs wiersza polecenia platformy .NET Core nie dodaje automatycznie tej lokalizacji do zmiennej środowiskowej PATH.

## <a name="use-the-tool"></a>Korzystanie z narzędzia

Po zainstalowaniu narzędzia można wywołać je za pomocą polecenia. Należy pamiętać, że polecenie nie może być takie samo jak nazwa pakietu.

Jeśli polecenie jest `dotnetsay`, należy je wywołać z:

```console
dotnetsay
```

Jeśli narzędzie ma być wyświetlane w kontekście `dotnet` monitu, może napisać je w taki sposób, aby była wywoływana `dotnet <command>`w taki sposób, jak:

```console
dotnet doc
```

Aby znaleźć narzędzia dołączone do zainstalowanego pakietu narzędzi globalnych, należy wyświetlić listę zainstalowanych pakietów przy użyciu polecenia programu [dotnet](dotnet-tool-list.md) .

Możesz również wyszukać instrukcje dotyczące użycia w witrynie sieci Web narzędzia lub wpisując jedno z następujących poleceń:

```console
<command> --help
dotnet <command> --help
```

### <a name="what-could-go-wrong"></a>Co się stało

Narzędzia globalne są [aplikacjami zależnymi od platformy](../deploying/index.md#framework-dependent-deployments-fdd), co oznacza, że korzystają z środowiska uruchomieniowego .NET Core zainstalowanego na komputerze. Jeśli nie odnaleziono oczekiwanego środowiska uruchomieniowego, są one zgodne z normalnymi regułami przetaczania w czasie wykonywania platformy .NET Core, takimi jak:

* Aplikacja przenosi do przodu do najwyższej wersji poprawki określonej głównej i pomocniczej.
* Jeśli nie ma pasującego środowiska uruchomieniowego z odpowiadającym mu numerem wersji głównej i pomocniczej, używana jest kolejna wyższa wersja pomocnicza.
* Przewinięcie do przodu nie występuje między wersjami w wersji zapoznawczej środowiska uruchomieniowego a wersjami zapoznawczymi i wersjami. W tym celu narzędzia globalne utworzone przy użyciu wersji zapoznawczej muszą zostać odbudowane i ponownie opublikowane przez autora oraz ponowne zainstalowanie.
* Dodatkowe problemy mogą wystąpić w przypadku narzędzi globalnych utworzonych w programie .NET Core 2,1 w wersji zapoznawczej 1. Aby uzyskać więcej informacji, zobacz temat [znane problemy w programie .NET Core 2,1 (wersja zapoznawcza 2](https://github.com/dotnet/core/blob/master/release-notes/2.1/Preview/2.1.0-preview2-known-issues.md)).

Jeśli aplikacja nie może znaleźć odpowiedniego środowiska uruchomieniowego, jego uruchomienie nie powiedzie się i zgłosi błąd.

Innym problemem, który może się zdarzyć, jest to, że narzędzie globalne, które zostało utworzone podczas wcześniejszej wersji zapoznawczej, może nie działać z aktualnie zainstalowanymi środowiskami uruchomieniowymi platformy .NET Core. Możesz zobaczyć, które środowiska uruchomieniowe są zainstalowane na maszynie, za pomocą następującego polecenia:

```console
dotnet --list-runtimes
```

Skontaktuj się z autorem narzędzia globalnego i sprawdź, czy można ponownie skompilować pakiet narzędzi do narzędzia NuGet przy użyciu zaktualizowanego numeru wersji. Po zaktualizowaniu pakietu w pakiecie NuGet możesz zaktualizować swoją kopię.

Interfejs wiersza polecenia platformy .NET Core próbuje dodać domyślne lokalizacje do zmiennej środowiskowej PATH przy pierwszym użyciu. Istnieje jednak kilka scenariuszy, w których lokalizacja nie może być automatycznie dodawana do ścieżki, na przykład:

* W `DOTNET_SKIP_FIRST_TIME_EXPERIENCE` przypadku ustawienia zmiennej środowiskowej.
* W systemie macOS, jeśli zainstalowano zestaw .NET Core SDK przy użyciu plików *tar. gz* , a nie *. pkg*.
* W systemie Linux należy edytować plik środowiska powłoki, aby skonfigurować ścieżkę.

## <a name="other-cli-commands"></a>Inne polecenia interfejsu CLI

Zestaw .NET Core SDK zawiera inne polecenia, które obsługują narzędzia platformy .NET Core. Użyj dowolnego `dotnet tool` polecenia z jedną z następujących opcji:

* `--global`lub `-g` określa, że polecenie ma zastosowanie do narzędzi globalnych na poziomie użytkownika.
* `--tool-path`Określa niestandardową lokalizację dla narzędzi globalnych.

Aby dowiedzieć się, które polecenia są dostępne dla narzędzi globalnych:

```console
dotnet tool --help
```

Aktualizacja narzędzia globalnego polega na odinstalowaniu i ponownym zainstalowaniu programu z najnowszą stabilną wersją. Aby zaktualizować narzędzie globalne, użyj polecenia [aktualizacji narzędzia dotnet](dotnet-tool-update.md) :

```console
dotnet tool update -g <packagename>
```

Usuń narzędzie globalne przy użyciu [Narzędzia dotnet Uninstall](dotnet-tool-uninstall.md):

```console
dotnet tool uninstall -g <packagename>
```

Aby wyświetlić wszystkie narzędzia globalne aktualnie zainstalowane na komputerze wraz z ich wersjami i poleceniami, użyj polecenia z [listy narzędzi dotnet](dotnet-tool-list.md) :

```console
dotnet tool list -g
```
