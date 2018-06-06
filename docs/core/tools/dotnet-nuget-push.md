---
title: polecenie wypychania nuget DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie wypychania nuget dotnet wypchnięcia pakietu na serwerze i publikuje ją.
author: karann-msft
ms.author: mairaw
ms.date: 06/01/2018
ms.openlocfilehash: 8a64f9cdc11d03bed82a132265c3b4e1de290807
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728579"
---
# <a name="dotnet-nuget-push"></a>wypychania nuget DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet nuget push` -Wypychanie pakietu do serwera i publikuje ją.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-21tabnetcore21"></a>[Oprogramowanie .NET core 2.1](#tab/netcore21)
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

`dotnet nuget push` Polecenia wypchnięcia pakietu na serwerze i publikuje ją. Polecenie wypychania używa serwera i szczegółów poświadczeń znalezionych w pliku konfiguracyjnym NuGet systemu lub łańcucha plików konfiguracji. Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [Konfigurowanie zachowania NuGet](/nuget/consume-packages/configuring-nuget-behavior). Konfiguracja domyślna NuGet są uzyskiwane przez ładowanie *%AppData%\NuGet\NuGet.config* (system Windows) lub *$HOME/.local/share* (Linux/macOS), następnie ładowania *nuget.config*lub *.nuget\nuget.config* rozpoczyna się od katalogu głównego dysku i kończy się w bieżącym katalogu.

## <a name="arguments"></a>Argumenty

`ROOT`

Określa ścieżkę pliku do pakietu, który ma zostać przeniesiony.

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[Oprogramowanie .NET core 2.1](#tab/netcore21)

`-d|--disable-buffering`

Wyłącza buforowanie przypadku wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.

`--force-english-output`

Wymusza aplikacji do uruchamiania przy użyciu opartego na język angielski, niezmienna kultura.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-k|--api-key <API_KEY>`

Klucz interfejsu API dla serwera.

`-n|--no-symbols`

Nie push symboli (nawet, jeśli istnieje).

`--no-service-endpoint`

Nie dołącza "interfejsu api w wersji 2/pakietu" adres URL źródła.

`-s|--source <SOURCE>`

Określa adres URL serwera. Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.

`-sk|--symbol-api-key <API_KEY>`

Klucz interfejsu API serwera symboli.

`-ss|--symbol-source <SOURCE>`

Określa adres URL serwera symboli.

`-t|--timeout <TIMEOUT>`

Określa limit czasu dla Wypychanie do serwera w sekundach. Wartość domyślna to 300 sekund (5 minut). Określanie 0 (zero sekund) jest stosowana wartość domyślna.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`-d|--disable-buffering`

Wyłącza buforowanie przypadku wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.

`--force-english-output`

Wymusza aplikacji do uruchamiania przy użyciu opartego na język angielski, niezmienna kultura.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-k|--api-key <API_KEY>`

Klucz interfejsu API dla serwera.

`-n|--no-symbols`

Nie push symboli (nawet, jeśli istnieje).

`-s|--source <SOURCE>`

Określa adres URL serwera. Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.

`-sk|--symbol-api-key <API_KEY>`

Klucz interfejsu API serwera symboli.

`-ss|--symbol-source <SOURCE>`

Określa adres URL serwera symboli.

`-t|--timeout <TIMEOUT>`

Określa limit czasu dla Wypychanie do serwera w sekundach. Wartość domyślna to 300 sekund (5 minut). Określanie 0 (zero sekund) jest stosowana wartość domyślna.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`-d|--disable-buffering`

Wyłącza buforowanie przypadku wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.

`--force-english-output`

Wymusza aplikacji do uruchamiania przy użyciu opartego na język angielski, niezmienna kultura.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-k|--api-key <API_KEY>`

Klucz interfejsu API dla serwera.

`-n|--no-symbols`

Nie push symboli (nawet, jeśli istnieje).

`-s|--source <SOURCE>`

Określa adres URL serwera. Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.

`-sk|--symbol-api-key <API_KEY>`

Klucz interfejsu API serwera symboli.

`-ss|--symbol-source <SOURCE>`

Określa adres URL serwera symboli.

`-t|--timeout <TIMEOUT>`

Określa limit czasu dla Wypychanie do serwera w sekundach. Wartość domyślna to 300 sekund (5 minut). Określanie 0 (zero sekund) jest stosowana wartość domyślna.

---

## <a name="examples"></a>Przykłady

Wypchnięcia *foo.nupkg* źródłem wypychania domyślne, określając klucz interfejsu API:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

Wypychania *foo.nupkg* do źródła niestandardowego wypychania `http://customsource`, określając klucz interfejsu API:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

Wypchnięcia *foo.nupkg* źródłem wypychania domyślne:

`dotnet nuget push foo.nupkg`

Wypchnięcia *foo.symbols.nupkg* do domyślnego źródła symboli:

`dotnet nuget push foo.symbols.nupkg`

Wypchnięcia *foo.nupkg* w źródle wypychania domyślne Określanie sekundę 360 przekroczenie limitu czasu:

`dotnet nuget push foo.nupkg --timeout 360`

Umieszcza wszystkie *.nupkg* plików w bieżącym katalogu w źródle wypychania domyślne:

`dotnet nuget push *.nupkg`

Umieszcza wszystkie *.nupkg* plików w bieżącym katalogu w źródle wypychania domyślne określenie pliku konfiguracji niestandardowej *./config/My.Config*:

`dotnet nuget push *.nupkg --config-file ./config/My.Config`
