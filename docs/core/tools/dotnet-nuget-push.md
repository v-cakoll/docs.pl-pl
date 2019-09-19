---
title: polecenia wypychania NuGet dotnet
description: Polecenie polecenia push NuGet narzędzia dotnet wypycha pakiet do serwera i opublikuje go.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 3299f79ec62aebdcdbef38f1e8b09a2dc5529ec4
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117493"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

**Ten temat dotyczy: ✓** .NET Core 1. x SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet nuget push`— Wypchnij pakiet do serwera i opublikuje go.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a>Opis

`dotnet nuget push` Polecenie wypycha pakiet do serwera i opublikuje go. Polecenie push używa informacji o serwerze i poświadczeniach znajdujących się w pliku konfiguracyjnym NuGet systemu lub w łańcuchu plików konfiguracji. Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Konfigurowanie zachowania NuGet](/nuget/consume-packages/configuring-nuget-behavior). Domyślna konfiguracja narzędzia NuGet jest uzyskiwana przez załadowanie *%AppData%\NuGet\NuGet.config* (Windows) lub *$Home/.local/share* (Linux/macOS), a następnie załadowanie jakichkolwiek *NuGet. config* lub *. NuGet\NuGet.config* , począwszy od katalogu głównego dysk i zakończenie w bieżącym katalogu.

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

  Określa adres URL serwera. Ta opcja jest wymagana, `DefaultPushSource` chyba że wartość konfiguracji jest ustawiona w pliku konfiguracyjnym NuGet.

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

* Wypychanie *foo. nupkg* do niestandardowego źródła `https://customsource`wypychania, określając klucz interfejsu API:

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
  > Aby rozwiązać ten problem, Uaktualnij wersję zestawu SDK lub zamiast tego Uruchom następujące polecenie:`dotnet nuget push **/*.nupkg`
