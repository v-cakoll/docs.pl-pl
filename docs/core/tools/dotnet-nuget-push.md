---
title: dotnet nuget push, polecenie
description: Polecenie dotnet nuget push wypycha pakiet do serwera i publikuje go.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 96f8d008c8306a0782d5149360a24bb4097a1ec4
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463518"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet nuget push`- Wciska paczkę na serwer i go publikuje.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source <SOURCE>] [--skip-duplicate]
    [-sk|--symbol-api-key <API_KEY>] [-ss|--symbol-source <SOURCE>]
    [-t|--timeout <TIMEOUT>]

dotnet nuget push -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet nuget push` wypycha pakiet do serwera i publikuje go. Polecenie wypychania używa szczegółów serwera i poświadczeń znalezionych w pliku konfiguracyjnym nuget systemu lub łańcuchu plików konfiguracyjnych. Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [Konfigurowanie zachowania nuget .](/nuget/consume-packages/configuring-nuget-behavior) Domyślną konfigurację NuGet uzyskuje się przez załadowanie *%AppData%\NuGet\NuGet.config* (Windows) lub *$HOME/.local/share* (Linux/macOS), a następnie załadowanie *dowolnego nuget.config* lub *.nuget\nuget.config,* zaczynając od katalogu głównego dysku, a kończąc na bieżącym katalogu.

## <a name="arguments"></a>Argumenty

- **`ROOT`**

  Określa ścieżkę pliku do pakietu, który ma zostać wypchnięty.

## <a name="options"></a>Opcje

- **`-d|--disable-buffering`**

  Wyłącza buforowanie podczas wypychania na serwer HTTP(S) w celu zmniejszenia użycia pamięci.

- **`--force-english-output`**

  Wymusza uruchamianie aplikacji przy użyciu niezmiennej kultury opartej na języku angielskim.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Umożliwia zablokowanie polecenia i wymaga ręcznej akcji dla operacji, takich jak uwierzytelnianie. Opcja dostępna od pliku .NET Core 2.2 SDK.

- **`-k|--api-key <API_KEY>`**

  Klucz interfejsu API serwera.

- **`-n|--no-symbols`**

  Nie wypycha symboli (nawet jeśli są obecne).

- **`--no-service-endpoint`**

  Nie dołącza "api/v2/package" do źródłowego adresu URL. Opcja dostępna od pliku .NET Core 2.1 SDK.

- **`-s|--source <SOURCE>`**

  Określa adres URL serwera. Ta opcja jest `DefaultPushSource` wymagana, chyba że wartość konfiguracyjny jest ustawiona w pliku konfiguracyjnym NuGet.

- **`--skip-duplicate`**

  Podczas wypychania wielu pakietów na serwer HTTP(S) traktuje dowolną odpowiedź konfliktu 409 jako ostrzeżenie, aby wypychanie było kontynuowane. Dostępne od .NET Core 3.1 SDK.

- **`-sk|--symbol-api-key <API_KEY>`**

  Klucz interfejsu API serwera symboli.

- **`-ss|--symbol-source <SOURCE>`**

  Określa adres URL serwera symboli.

- **`-t|--timeout <TIMEOUT>`**

  Określa limit czasu do wypychania do serwera w sekundach. Wartość domyślna to 300 sekund (5 minut). Określenie wartości 0 (zero sekund) powoduje zastosowanie wartości domyślnej.

## <a name="examples"></a>Przykłady

- Wypycha *foo.nupkg* do domyślnego źródła wypychania, określając klucz interfejsu API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- Wypychaj *foo.nupkg* do oficjalnego serwera NuGet, określając klucz interfejsu API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * Wypychanie *foo.nupkg* do `https://customsource`niestandardowego źródła wypychania , określając klucz interfejsu API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- Popycha *foo.nupkg* do domyślnego źródła wypychania:

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- Popycha *foo.symbols.nupkg* do domyślnego źródła symboli:

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- Wypycha *foo.nupkg* do domyślnego źródła wypychania, określając 360-sekundowy limit czasu:

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- Wypycha wszystkie pliki *nupkg* w bieżącym katalogu do domyślnego źródła wypychania:

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > Jeśli to polecenie nie działa, może to być spowodowane błędem, który istniał w starszych wersjach SDK (.NET Core 2.1 SDK i wcześniejszych wersjach).
  > Aby rozwiązać ten problem, należy uaktualnić wersję SDK lub zamiast tego uruchomić następujące polecenie:`dotnet nuget push **/*.nupkg`

- Wypycha wszystkie pliki nupkg, nawet jeśli odpowiedź na konflikt 409 jest zwracana przez serwer HTTP(S):Pushes all *.nupkg* files even if a 409 Conflict response is returned by an HTTP(S) server:

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```
