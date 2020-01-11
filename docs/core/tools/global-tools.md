---
title: Narzędzia globalne platformy .NET Core
description: Omówienie narzędzi globalnych platformy .NET Core i dostępnych dla nich poleceń interfejs wiersza polecenia platformy .NET Core.
author: KathleenDollard
ms.date: 05/29/2018
ms.openlocfilehash: 0df3c1b615adfeaaf41542dc8252a8f14f49f6f9
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899864"
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

Obecnie nie istnieje funkcja globalnego wyszukiwania narzędzi w interfejsie wiersza polecenia (CLI) platformy .NET Core. Poniżej przedstawiono kilka zaleceń dotyczących znajdowania narzędzi:

* Narzędzia platformy .NET Core można znaleźć na platformie [NuGet](https://www.nuget.org). Jednak pakiet NuGet nie zezwala jeszcze na wyszukiwanie dla narzędzi globalnych platformy .NET Core.
* Zalecenia dotyczące narzędzi można znaleźć w wpisach w blogu lub w repozytorium GitHub [natemcmaster/dotnet-Tools](https://github.com/natemcmaster/dotnet-tools) .
* Kod źródłowy dla narzędzi globalnych utworzonych przez zespół ASP.NET można zobaczyć w repozytorium GitHub [/aspnetcore](https://github.com/dotnet/aspnetcore/tree/master/src/Tools) w programie dotnet.
* Informacje o narzędziach diagnostycznych można znaleźć w [narzędziach diagnostycznych diagnostyki dotnet programu .NET Core](../diagnostics/index.md#net-core-dotnet-diagnostic-global-tools).

## <a name="check-the-author-and-statistics"></a>Sprawdź autora i statystyki

Ponieważ globalne narzędzia platformy .NET Core działają w pełni zaufane i są zwykle instalowane na ścieżce, mogą być bardzo wydajne. Nie pobieraj narzędzi z osób, które nie są zaufane.

Jeśli narzędzie jest hostowane w usłudze NuGet, można sprawdzić autora i statystyk, wyszukując narzędzie.

## <a name="install-a-global-tool"></a>Instalowanie narzędzia globalnego

Aby zainstalować narzędzie globalne, należy użyć [Narzędzia dotnet zainstaluj](dotnet-tool-install.md) interfejs wiersza polecenia platformy .NET Core polecenie. Poniższy przykład pokazuje, jak zainstalować narzędzie globalne w lokalizacji domyślnej:

```dotnetcli
dotnet tool install -g dotnetsay
```

Jeśli nie można zainstalować narzędzia, zostaną wyświetlone komunikaty o błędach. Sprawdź, czy wybrane źródła danych są sprawdzane.

Jeśli próbujesz zainstalować wersję wstępną lub określoną wersję narzędzia, możesz określić numer wersji w następującym formacie:

```dotnetcli
dotnet tool install -g <package-name> --version <version-number>
```

Jeśli instalacja zakończy się pomyślnie, zostanie wyświetlony komunikat z poleceniem, które służy do wywoływania narzędzia i zainstalowanej wersji, podobnie jak w poniższym przykładzie:

```output
You can invoke the tool using the following command: dotnetsay
Tool 'dotnetsay' (version '2.0.0') was successfully installed.
```

Narzędzia globalne można zainstalować w katalogu domyślnym lub w określonej lokalizacji. Domyślne katalogi są następujące:

| System operacyjny          | Ścieżka                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| Windows     | `%USERPROFILE%\.dotnet\tools` |

Te lokalizacje są dodawane do ścieżki użytkownika podczas pierwszego uruchomienia zestawu SDK, dzięki czemu globalne narzędzia mogą być wywoływane bezpośrednio.

Należy pamiętać, że globalne narzędzia to specyficzne dla użytkownika, a nie globalne maszyny. Specyficzne dla użytkownika oznacza, że nie można zainstalować narzędzia globalnego, które jest dostępne dla wszystkich użytkowników komputera. Narzędzie jest dostępne tylko dla każdego profilu użytkownika, w którym zainstalowano narzędzie.

Narzędzia globalne można także zainstalować w określonym katalogu. Po zainstalowaniu w określonym katalogu użytkownik musi upewnić się, że polecenie jest dostępne, dołączając ten katalog w ścieżce, wywołując polecenie z określonym katalogiem lub wywołując narzędzie z w określonym katalogu.
W takim przypadku interfejs wiersza polecenia platformy .NET Core nie dodaje automatycznie tej lokalizacji do zmiennej środowiskowej PATH.

## <a name="use-the-tool"></a>Korzystanie z narzędzia

Po zainstalowaniu narzędzia można wywołać je za pomocą polecenia. Należy pamiętać, że polecenie nie może być takie samo jak nazwa pakietu.

Jeśli polecenie jest `dotnetsay`, nastąpi wywołanie:

```console
dotnetsay
```

Jeśli narzędzie ma być wyświetlane w kontekście monitu `dotnet`, nastąpiło zapisanie go w taki sposób, że jest on wywoływany jako `dotnet <command>`, na przykład:

```dotnetcli
dotnet doc
```

Aby znaleźć narzędzia dołączone do zainstalowanego pakietu narzędzi globalnych, należy wyświetlić listę zainstalowanych pakietów przy użyciu polecenia programu [dotnet](dotnet-tool-list.md) .

Możesz również wyszukać instrukcje dotyczące użycia w witrynie sieci Web narzędzia lub wpisując jedno z następujących poleceń:

```console
<command> --help
dotnet <command> --help
```

## <a name="other-cli-commands"></a>Inne polecenia interfejsu CLI

Zestaw .NET Core SDK zawiera inne polecenia, które obsługują narzędzia platformy .NET Core. Użyj dowolnego z `dotnet tool` poleceń z jedną z następujących opcji:

* `--global` lub `-g` określa, że polecenie ma zastosowanie do narzędzi globalnych dostępnych dla użytkownika.
* `--tool-path` określa niestandardową lokalizację dla narzędzi globalnych.

Aby dowiedzieć się, które polecenia są dostępne dla narzędzi globalnych:

```dotnetcli
dotnet tool --help
```

Aktualizacja narzędzia globalnego polega na odinstalowaniu i ponownym zainstalowaniu programu z najnowszą stabilną wersją. Aby zaktualizować narzędzie globalne, użyj polecenia [aktualizacji narzędzia dotnet](dotnet-tool-update.md) :

```dotnetcli
dotnet tool update -g <packagename>
```

Usuń narzędzie globalne przy użyciu [Narzędzia dotnet Uninstall](dotnet-tool-uninstall.md):

```dotnetcli
dotnet tool uninstall -g <packagename>
```

Aby wyświetlić wszystkie narzędzia globalne aktualnie zainstalowane na komputerze wraz z ich wersjami i poleceniami, użyj polecenia z [listy narzędzi dotnet](dotnet-tool-list.md) :

```dotnetcli
dotnet tool list -g
```

## <a name="see-also"></a>Zobacz także

* [Rozwiązywanie problemów z użyciem narzędzia .NET Core](troubleshoot-usage-issues.md)
