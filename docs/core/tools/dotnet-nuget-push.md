---
title: polecenie wypychania nuget DotNet - .NET Core interfejsu wiersza polecenia
description: "Polecenie wypychania nuget dotnet wypchnięcia pakietu na serwerze i publikuje ją."
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 52aac5ff1862397616287a77eac063582703d509
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-nuget-push"></a>wypychania nuget DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet nuget push`-Wypychanie pakietu do serwera i publikuje ją.

## <a name="synopsis"></a>Streszczenie

`dotnet nuget push [<ROOT>] [-s|--source] [-ss|--symbol-source] [-t|--timeout] [-k|--api-key] [-sk|--symbol-api-key] [-d|--disable-buffering] [-n|--no-symbols] [--force-english-output] [-h|--help]`

## <a name="description"></a>Opis

`dotnet nuget push` Polecenia wypchnięcia pakietu na serwerze i publikuje ją. Polecenie wypychania używa serwera i szczegółów poświadczeń znalezionych w pliku konfiguracyjnym NuGet systemu lub łańcucha plików konfiguracji. Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [Konfigurowanie zachowania NuGet](/nuget/consume-packages/configuring-nuget-behavior). Konfiguracja domyślna NuGet są uzyskiwane przez ładowanie *%AppData%\NuGet\NuGet.config* (system Windows) lub *$HOME/.local/share* (Linux/macOS), następnie ładowania *nuget.config*lub *.nuget\nuget.config* rozpoczyna się od katalogu głównego dysku i kończy się w bieżącym katalogu.

## <a name="arguments"></a>Argumenty

`ROOT`

Określ ścieżkę do pakietu i klucz interfejsu API do dystrybuowania pakietu do serwera.

## <a name="options"></a>Opcje

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`-s|--source <SOURCE>`

Określa adres URL serwera. Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.

`--symbol-source <SOURCE>`

Określa adres URL serwera symboli.

`-t|--timeout <TIMEOUT>`

Określa limit czasu dla Wypychanie do serwera w sekundach. Wartość domyślna to 300 sekund (5 minut). Określanie 0 (zero sekund) jest stosowana wartość domyślna.

`-k|--api-key <API_KEY>`

Klucz interfejsu API dla serwera.

`--symbol-api-key <API_KEY>`

Klucz interfejsu API serwera symboli.

`-d|--disable-buffering`

Wyłącza buforowanie przypadku wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.

`-n|--no-symbols`

Nie push symboli (nawet, jeśli istnieje).

`--force-english-output`

Wymusza rejestrowane dane wyjściowe w języku angielskim.

## <a name="examples"></a>Przykłady

Wypchnięcia *foo.nupkg* źródłem wypychania domyślne, zapewniając klucz interfejsu API:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a`

Wypychania *foo.nupkg* do źródła niestandardowego wypychania `http://customsource`, zapewniając klucz interfejsu API:

`dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s http://customsource/`

Wypchnięcia *foo.nupkg* źródłem wypychania domyślne:

`dotnet nuget push foo.nupkg`

Wypchnięcia *foo.symbols.nupkg* do domyślnego źródła symboli:

`dotnet nuget push foo.symbols.nupkg`

Wypchnięcia *foo.nupkg* w źródle wypychania domyślne Określanie 360 drugi limitu czasu:

`dotnet nuget push foo.nupkg --timeout 360`

Umieszcza wszystkie *.nupkg* plików w bieżącym katalogu w źródle wypychania domyślne:

`dotnet nuget push *.nupkg`

Umieszcza wszystkie *.nupkg* plików w bieżącym katalogu w źródle wypychania domyślne określenie pliku konfiguracji niestandardowej *./config/My.Config*:

`dotnet nuget push *.nupkg --config-file ./config/My.Config`
