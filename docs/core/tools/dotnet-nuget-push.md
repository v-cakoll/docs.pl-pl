---
title: polecenie wypychania dotnet nuget
description: Polecenie wypychania dotnet nuget wypycha pakiet do serwera i publikuje go.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: d4ef8e58908fe488c712debff3b313ac0908b43e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503662"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet nuget push`- Wypycha paczkę na serwer i publikuje go.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [--skip-duplicate] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet nuget push` wypycha pakiet do serwera i publikuje go. Polecenie push używa danych serwera i poświadczeń znalezionych w pliku konfiguracyjnym NuGet systemu lub łańcuchu plików konfiguracyjnych. Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [Konfigurowanie zachowania NuGet](/nuget/consume-packages/configuring-nuget-behavior). Domyślną konfigurację NuGet uzyskuje się przez wczytanie *%AppData%\NuGet\NuGet.config* (Windows) lub *$HOME/.local/share* (Linux/macOS), a następnie ładowanie *dowolnego nuget.config* lub *.nuget\nuget.config,* zaczynając od katalogu głównego dysku, a kończąc w bieżącym katalogu.

## <a name="arguments"></a>Argumenty

- **`ROOT`**

  Określa ścieżkę pliku do pakietu, który ma zostać wypchnięty.

## <a name="options"></a>Opcje

- **`-d|--disable-buffering`**

  Wyłącza buforowanie podczas wypychania do serwera HTTP(S), aby zmniejszyć użycie pamięci.

- **`--force-english-output`**

  Wymusza uruchamianie aplikacji przy użyciu niezmiennej kultury opartej na języku angielskim.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--interactive`**

  Umożliwia blokowanie polecenia i wymaga ręcznego działania dla operacji, takich jak uwierzytelnianie. Opcja dostępna od sdk .NET Core 2.2.

- **`-k|--api-key <API_KEY>`**

  Klucz interfejsu API dla serwera.

- **`-n|--no-symbols`**

  Nie wciska symboli (nawet jeśli są obecne).

- **`--no-service-endpoint`**

  Nie dołącza "api/v2/package" do źródłowego adresu URL. Opcja dostępna od sdk .NET Core 2.1.

- **`-s|--source <SOURCE>`**

  Określa adres URL serwera. Ta opcja jest wymagana, chyba `DefaultPushSource` że wartość konfiguratowa jest ustawiona w pliku konfiguracyjnym NuGet.

- **`--skip-duplicate`**

  Podczas wypychania wielu pakietów do serwera HTTP(S) traktuje dowolną odpowiedź 409 Konflikt jako ostrzeżenie, dzięki czemu wypychanie można kontynuować. Dostępne od sdk .NET Core 3.1.

- **`-sk|--symbol-api-key <API_KEY>`**

  Klucz interfejsu API serwera symboli.

- **`-ss|--symbol-source <SOURCE>`**

  Określa adres URL serwera symboli.

- **`-t|--timeout <TIMEOUT>`**

  Określa uchył czasu wypychania do serwera w ciągu kilku sekund. Domyślnie 300 sekund (5 minut). Określenie 0 (zero sekund) jest stosowane wartość domyślną.

## <a name="examples"></a>Przykłady

- Wypycha *foo.nupkg* do domyślnego źródła wypychania, określając klucz interfejsu API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

- Wypchnij *foo.nupkg* do oficjalnego serwera NuGet, określając klucz interfejsu API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://api.nuget.org/v3/index.json
  ```
  
  * Wypchnij *foo.nupkg* do niestandardowego źródła `https://customsource`wypychania, określając klucz interfejsu API:

  ```dotnetcli
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

- Popycha *foo.nupkg* do domyślnego źródła wypychania:

  ```dotnetcli
  dotnet nuget push foo.nupkg
  ```

- Wypycha *foo.symbols.nupkg* do domyślnego źródła symboli:

  ```dotnetcli
  dotnet nuget push foo.symbols.nupkg
  ```

- Popycha *foo.nupkg* do domyślnego źródła wypychania, określając 360-sekundowy timeout:

  ```dotnetcli
  dotnet nuget push foo.nupkg --timeout 360
  ```

- Wypycha wszystkie pliki *nupkg* w bieżącym katalogu do domyślnego źródła wypychania:

  ```dotnetcli
  dotnet nuget push *.nupkg
  ```

  > [!NOTE]
  > Jeśli to polecenie nie działa, może to być spowodowane błędem, który istniał w starszych wersjach sdk (.NET Core 2.1 SDK i wcześniejszych wersjach).
  > Aby rozwiązać ten problem, uaktualnij wersję sdk lub zamiast tego uruchom następujące polecenie:`dotnet nuget push **/*.nupkg`

- Wypycha wszystkie pliki *.nupkg,* nawet jeśli odpowiedź na konflikt 409 jest zwracana przez serwer HTTP(S):Pushes all .nupkg files even if a 409 Conflict response is returned by an HTTP(S) server:

  ```dotnetcli
  dotnet nuget push *.nupkg --skip-duplicate
  ```
