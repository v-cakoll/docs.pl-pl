---
title: polecenia wypychania NuGet dotnet
description: Polecenie polecenia push NuGet narzędzia dotnet wypycha pakiet do serwera i opublikuje go.
author: karann-msft
ms.date: 12/04/2019
ms.openlocfilehash: a352120efa199b871e67eb8ba2442bd69a9fc4ed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789883"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 1. x SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet nuget push` — wypchnij pakiet do serwera i opublikuje go.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [--skip-duplicate] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a>Opis

`dotnet nuget push` polecenie wypycha pakiet do serwera i opublikuje go. Polecenie push używa informacji o serwerze i poświadczeniach znajdujących się w pliku konfiguracyjnym NuGet systemu lub w łańcuchu plików konfiguracji. Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Konfigurowanie zachowania NuGet](/nuget/consume-packages/configuring-nuget-behavior). Domyślna konfiguracja narzędzia NuGet jest uzyskiwana przez załadowanie *%AppData%\NuGet\NuGet.config* (Windows) lub *$Home/.local/share* (Linux/macOS), a następnie załadowanie jakichkolwiek *NuGet. config* lub *. NuGet\NuGet.config* , począwszy od katalogu głównego dysku i kończącego się w bieżącym katalogu.

## <a name="arguments"></a>Argumenty

* **`ROOT`**

  Określa ścieżkę pliku do pakietu do wypchnięcia.

## <a name="options"></a>Opcje

* **`-d|--disable-buffering`**

  Wyłącza buforowanie podczas wypychania do serwera HTTP (S) w celu zmniejszenia użycia pamięci.

* **`--force-english-output`**

  Wymusza uruchomienie aplikacji przy użyciu niezmiennej, opartej na języku angielskim kultury.

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

* **`--interactive`**

  Umożliwia zablokowanie polecenia i wymaga ręcznej akcji dla operacji takich jak uwierzytelnianie. Opcja dostępna od wersji .NET Core 2,2 SDK.

* **`-k|--api-key <API_KEY>`**

  Klucz interfejsu API dla serwera programu.

* **`-n|--no-symbols`**

  Nie Wypychaj symboli (nawet jeśli istnieją).

* **`--no-service-endpoint`**

  Nie dołącza "API/v2/Package" do źródłowego adresu URL. Opcja dostępna od wersji .NET Core 2,1 SDK.

* **`-s|--source <SOURCE>`**

  Określa adres URL serwera. Ta opcja jest wymagana, chyba że w pliku konfiguracyjnym NuGet zostanie ustawiona wartość `DefaultPushSource` konfiguracja.

* **`--skip-duplicate`**

  Podczas wypychania wielu pakietów do serwera HTTP (S) program traktuje wszystkie 409 odpowiedzi w konflikcie jako ostrzeżenie, aby można było kontynuować wypychanie. Dostępne od wersji .NET Core 3,1 SDK.

* **`-sk|--symbol-api-key <API_KEY>`**

  Klucz interfejsu API dla serwera symboli.

* **`-ss|--symbol-source <SOURCE>`**

  Określa adres URL serwera symboli.

* **`-t|--timeout <TIMEOUT>`**

  Określa limit czasu wypychania do serwera w sekundach. Wartość domyślna to 300 sekund (5 minut). Wartość domyślna to 0 (zero sekund).

## <a name="examples"></a>Przykłady

* Wypchnięcie *foo. nupkg* do domyślnego źródła push, określając klucz interfejsu API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* Wypychanie *foo. nupkg* do oficjalnego serwera NuGet, określając klucz interfejsu API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * Wypchnij *foo. nupkg* do niestandardowego źródła push `https://customsource`, określając klucz interfejsu API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* Wypchnięcie *foo. nupkg* do domyślnego źródła push:

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

* Wypchnięcie *foo. Symbols. nupkg* do domyślnego źródła symboli:

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

* Wypchnięcie *foo. nupkg* do domyślnego źródła push, określając 360-sekundowy limit czasu:

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

* Wypycha wszystkie pliki *. nupkg* w bieżącym katalogu do domyślnego źródła push:

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > Jeśli to polecenie nie działa, może to być spowodowane usterką, która istniała we wcześniejszych wersjach zestawu SDK (zestaw SDK programu .NET Core 2,1 i wcześniejsze wersje).
  > Aby rozwiązać ten problem, Uaktualnij wersję zestawu SDK lub zamiast tego Uruchom następujące polecenie: `dotnet nuget push **/*.nupkg`

* Wypychanie wszystkich plików *. nupkg* , nawet jeśli odpowiedź na 409 jest zwracana przez serwer http (S):

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```
