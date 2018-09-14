---
title: polecenia DotNet do wypychania nuget — interfejs wiersza polecenia platformy .NET Core
description: Polecenie wypychania nuget dotnet wypycha pakietu do serwera i publikuje go.
author: karann-msft
ms.author: mairaw
ms.date: 09/04/2018
ms.openlocfilehash: 23d27cef29008955850f9ed9f4a8baed9e7ad982
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45610012"
---
# <a name="dotnet-nuget-push"></a>wypychane nuget DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet nuget push` -Wypycha pakietu do serwera i publikuje go.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [-k|--api-key] [-n|--no-symbols]
    [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```
---

## <a name="description"></a>Opis

`dotnet nuget push` Polecenie wypycha pakietu do serwera i publikuje go. Używa polecenia push serwera i szczegóły poświadczeń znalezionych w pliku config NuGet systemu lub łańcucha plików konfiguracji. Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [Konfigurowanie zachowania pakietu NuGet](/nuget/consume-packages/configuring-nuget-behavior). Konfiguracja domyślna NuGet uzyskuje się przez ładowanie *%AppData%\NuGet\NuGet.config* (Windows) lub *$HOME/.local/share* (Linux/macOS), następnie ładowania *nuget.config*lub *.nuget\nuget.config* od katalogu głównego dysku i kończący się w bieżącym katalogu.

## <a name="arguments"></a>Argumenty

`ROOT`

Określa ścieżkę pliku do pakietu, który ma zostać wypchnięty.

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[.NET core 2.1](#tab/netcore21)

`-d|--disable-buffering`

Wyłącza buforowanie podczas wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.

`--force-english-output`

Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`-k|--api-key <API_KEY>`

Klucz interfejsu API dla serwera.

`-n|--no-symbols`

Nie wypychania symbole (nawet jeśli istnieje).

`--no-service-endpoint`

Nie dołącza "interfejsu api w wersji 2/pakiet" adres URL źródła.

`-s|--source <SOURCE>`

Określa adres URL serwera. Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.

`-sk|--symbol-api-key <API_KEY>`

Klucz interfejsu API serwera symboli.

`-ss|--symbol-source <SOURCE>`

Określa adres URL serwera symboli.

`-t|--timeout <TIMEOUT>`

Określa limit czasu Wypychanie do serwera w ciągu kilku sekund. Wartość domyślna to 300 sekund (5 minut). Określanie 0 (zero sekund) stosuje się wartością domyślną.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`-d|--disable-buffering`

Wyłącza buforowanie podczas wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.

`--force-english-output`

Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`-k|--api-key <API_KEY>`

Klucz interfejsu API dla serwera.

`-n|--no-symbols`

Nie wypychania symbole (nawet jeśli istnieje).

`-s|--source <SOURCE>`

Określa adres URL serwera. Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.

`-sk|--symbol-api-key <API_KEY>`

Klucz interfejsu API serwera symboli.

`-ss|--symbol-source <SOURCE>`

Określa adres URL serwera symboli.

`-t|--timeout <TIMEOUT>`

Określa limit czasu Wypychanie do serwera w ciągu kilku sekund. Wartość domyślna to 300 sekund (5 minut). Określanie 0 (zero sekund) stosuje się wartością domyślną.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-d|--disable-buffering`

Wyłącza buforowanie podczas wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.

`--force-english-output`

Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`-k|--api-key <API_KEY>`

Klucz interfejsu API dla serwera.

`-n|--no-symbols`

Nie wypychania symbole (nawet jeśli istnieje).

`-s|--source <SOURCE>`

Określa adres URL serwera. Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.

`-sk|--symbol-api-key <API_KEY>`

Klucz interfejsu API serwera symboli.

`-ss|--symbol-source <SOURCE>`

Określa adres URL serwera symboli.

`-t|--timeout <TIMEOUT>`

Określa limit czasu Wypychanie do serwera w ciągu kilku sekund. Wartość domyślna to 300 sekund (5 minut). Określanie 0 (zero sekund) stosuje się wartością domyślną.

---

## <a name="examples"></a>Przykłady

Wypycha *foo.nupkg* do domyślnego źródła wypychania, określając klucz interfejsu API:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

Wypychania *foo.nupkg* do źródła niestandardowego wypychania `http://customsource`, określając klucz interfejsu API:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

Wypycha *foo.nupkg* do domyślnego źródła push:

`dotnet nuget push foo.nupkg`

Wypycha *foo.symbols.nupkg* do domyślnego źródła symboli:

`dotnet nuget push foo.symbols.nupkg`

Wypycha *foo.nupkg* do domyślnego źródła wypychania, określając 360-sekundowy limit:

`dotnet nuget push foo.nupkg --timeout 360`

Wypychanie wszystkich *.nupkg* plików w bieżącym katalogu, do domyślnego źródła push:

`dotnet nuget push *.nupkg`
