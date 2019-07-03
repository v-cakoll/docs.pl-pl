---
title: polecenie wypychania nuget DotNet
description: Polecenie wypychania nuget dotnet wypycha pakietu do serwera i publikuje go.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 4d5efa94c6a4494158aea447be98256d2a307cd6
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539132"
---
# <a name="dotnet-nuget-push"></a>dotnet nuget push

**Ten temat dotyczy: ✓** platformy .NET Core SDK w wersji 1.x i nowszymi wersjami

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet nuget push` -Wypycha pakietu do serwera i publikuje go.

## <a name="synopsis"></a>Streszczenie

```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
dotnet nuget push [-h|--help]
```

## <a name="description"></a>Opis

`dotnet nuget push` Polecenie wypycha pakietu do serwera i publikuje go. Używa polecenia push serwera i szczegóły poświadczeń znalezionych w pliku config NuGet systemu lub łańcucha plików konfiguracji. Aby uzyskać więcej informacji na temat plików konfiguracyjnych, zobacz [Konfigurowanie zachowania pakietu NuGet](/nuget/consume-packages/configuring-nuget-behavior). Konfiguracja domyślna NuGet uzyskuje się przez ładowanie *%AppData%\NuGet\NuGet.config* (Windows) lub *$HOME/.local/share* (Linux/macOS), następnie ładowania *nuget.config*lub *.nuget\nuget.config* od katalogu głównego dysku i kończący się w bieżącym katalogu.

## <a name="arguments"></a>Argumenty

* **`ROOT`**

  Określa ścieżkę pliku do pakietu, który ma zostać wypchnięty.

## <a name="options"></a>Opcje

* **`-d|--disable-buffering`**

  Wyłącza buforowanie podczas wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.

* **`--force-english-output`**

  Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.

* **`-h|--help`**

Drukuje krótki pomoc dotyczącą polecenia.

* **`--interactive`**

  Umożliwia polecenie, aby zablokować i wymaga ręcznej akcji dla operacji, takich jak uwierzytelnianie. Opcja dostępna od zestawu SDK programu .NET Core 2.2.

* **`-k|--api-key <API_KEY>`**

  Klucz interfejsu API dla serwera.

* **`-n|--no-symbols`**

  Nie wypychania symbole (nawet jeśli istnieje).

* **`--no-service-endpoint`**

  Nie dołącza "interfejsu api w wersji 2/pakiet" adres URL źródła. Opcja dostępna od zestawu SDK programu .NET Core 2.1.

* **`-s|--source <SOURCE>`**

  Określa adres URL serwera. Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.

* **`-sk|--symbol-api-key <API_KEY>`**

  Klucz interfejsu API serwera symboli.

* **`-ss|--symbol-source <SOURCE>`**

  Określa adres URL serwera symboli.

* **`-t|--timeout <TIMEOUT>`**

  Określa limit czasu Wypychanie do serwera w ciągu kilku sekund. Wartość domyślna to 300 sekund (5 minut). Określanie 0 (zero sekund) stosuje się wartością domyślną.

## <a name="examples"></a>Przykłady

* Wypycha *foo.nupkg* do domyślnego źródła wypychania, określając klucz interfejsu API:

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a
  ```

* Wypychania *foo.nupkg* do źródła niestandardowego wypychania `https://customsource`, określając klucz interfejsu API:

  ```console
  dotnet nuget push foo.nupkg -k 4003d786-cc37-4004-bfdf-c4f3e8ef9b3a -s https://customsource/
  ```

* Wypycha *foo.nupkg* do domyślnego źródła push:

  ```console
  dotnet nuget push foo.nupkg
  ```

* Wypycha *foo.symbols.nupkg* do domyślnego źródła symboli:

  ```console
  dotnet nuget push foo.symbols.nupkg
  ```

* Wypycha *foo.nupkg* do domyślnego źródła wypychania, określając 360-sekundowy limit:

  ```console
  dotnet nuget push foo.nupkg --timeout 360
  ```

* Wypychanie wszystkich *.nupkg* plików w bieżącym katalogu, do domyślnego źródła push:

  ```console
  dotnet nuget push *.nupkg
  ```
  
  > [!NOTE]
  > To polecenie nie działa, prawdopodobnie z powodu błędów, które istniały w starszych wersjach zestawu SDK (zestaw SDK programu .NET Core 2.1 i wcześniejszych wersjach).
  > Aby rozwiązać ten problem, Uaktualnij używanej wersji zestawu SDK lub zamiast tego uruchom następujące polecenie: `dotnet nuget push **/*.nupkg`
