---
title: polecenie wypychania nuget DotNet
description: Polecenie wypychania nuget dotnet wypycha pakietu do serwera i publikuje go.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: 4f0d127d8b9f37b1c381d8981f54035a2fc3b0e5
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169355"
---
# <a name="dotnet-nuget-push"></a>wypychane nuget DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet nuget push` -Wypycha pakietu do serwera i publikuje go.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)
```
dotnet nuget push [<ROOT>] [-d|--disable-buffering] [--force-english-output] [--interactive] [-k|--api-key] [-n|--no-symbols]
    [--no-service-endpoint] [-s|--source] [-sk|--symbol-api-key] [-ss|--symbol-source] [-t|--timeout]
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

* **`ROOT`**

  Określa ścieżkę pliku do pakietu, który ma zostać wypchnięty.

## <a name="options"></a>Opcje

# <a name="net-core-2xtabnetcore2x"></a>[.NET Core 2.x](#tab/netcore2x)

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

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

* **`-d|--disable-buffering`**

  Wyłącza buforowanie podczas wypychania do serwera HTTP (S), aby zmniejszyć użycie pamięci.

* **`--force-english-output`**

  Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.

* **`-h|--help`**

  Drukuje krótki pomoc dotyczącą polecenia.

* **`-k|--api-key <API_KEY>`**

  Klucz interfejsu API dla serwera.

* **`-n|--no-symbols`**

  Nie wypychania symbole (nawet jeśli istnieje).

* **`-s|--source <SOURCE>`**

  Określa adres URL serwera. Ta opcja jest wymagana, chyba że `DefaultPushSource` wartość konfiguracji jest ustawiana w pliku konfiguracyjnym NuGet.

* **`-sk|--symbol-api-key <API_KEY>`**

  Klucz interfejsu API serwera symboli.

* **`-ss|--symbol-source <SOURCE>`**

  Określa adres URL serwera symboli.

* **`-t|--timeout <TIMEOUT>`**

  Określa limit czasu Wypychanie do serwera w ciągu kilku sekund. Wartość domyślna to 300 sekund (5 minut). Określanie 0 (zero sekund) stosuje się wartością domyślną.

---

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