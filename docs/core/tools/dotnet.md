---
title: polecenie DotNet - .NET Core interfejsu wiersza polecenia
description: "Informacje o poleceniu dotnet (ogólnego sterownik narzędzi interfejsu wiersza polecenia platformy .NET Core) i jej użycia."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: bba8d77cda7538bf008dc0f510f9279d3c695c3d
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2017
---
# <a name="dotnet-command"></a>polecenie DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet`-Ogólne sterownik do uruchamiania polecenia wiersza polecenia.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbose] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [-v|--verbose] [--version]
```
---

## <a name="description"></a>Opis

`dotnet`jest ogólny sterownik łańcuch narzędzi interfejsu wiersza polecenia (CLI). Wywoływane na jego własnej, zapewnia użycia krótkie instrukcje.

Każdej z funkcji jest implementowany jako polecenia. Aby można było użyć funkcji, polecenie określono po `dotnet`, takich jak [ `dotnet build` ](dotnet-build.md). Wszystkie argumenty następujące polecenie to własną argumentów.

Tylko `dotnet` jest używany jako polecenia samodzielnie [aplikacje zależne od framework](../deploying/index.md). Określ aplikację DLL po `dotnet` zlecenie do wykonywania aplikacji (na przykład `dotnet myapp.dll`).

## <a name="options"></a>Opcje

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

`--additionaldeps <PATH>`

Ścieżka do dodatkowych *deps.json* pliku.

`--additionalprobingpath <PATH>`

Ścieżka zawierające sondowania zasad i zestawów do sondowania.

`-d|--diagnostics`

Umożliwia wyjście diagnostyczne.

`--fx-version <VERSION>`

Wersja zainstalowanego środowiska uruchomieniowego .NET Core służące do uruchamiania aplikacji.

`-h|--help`

Drukuje krótkich pomocy dla polecenia. Jeśli używany z `dotnet`, również Wyświetla listę dostępnych poleceń.

`--info`

Drukuje szczegółowe informacje na temat narzędzi interfejsu wiersza polecenia i środowiska, takich jak bieżący system operacyjny, Zatwierdź SHA dla wersji i innych informacji.

`--roll-forward-on-no-candidate-fx`

 Przedstawia przekazywania na ma kandydata framework udostępnionego.

`-v|--verbose`

Włącza pełne dane wyjściowe.

`--version`

Drukuje wersji programu .NET Core SDK w użyciu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

`--additionalprobingpath <PATH>`

Ścieżka zawierające sondowania zasad i zestawów do sondowania.

`-d|--diagnostics`

Umożliwia wyjście diagnostyczne.

`--fx-version <VERSION>`

Wersja zainstalowanego środowiska uruchomieniowego .NET Core służące do uruchamiania aplikacji.

`-h|--help`

Drukuje krótkich pomocy dla polecenia. Jeśli używany z `dotnet`, również Wyświetla listę dostępnych poleceń.

`--info`

Drukuje szczegółowe informacje na temat narzędzi interfejsu wiersza polecenia i środowiska, takich jak bieżący system operacyjny, Zatwierdź SHA dla wersji i innych informacji.

`-v|--verbose`

Włącza pełne dane wyjściowe.

`--version`

Drukuje wersji programu .NET Core SDK w użyciu.

---

## <a name="dotnet-commands"></a>polecenia DotNet

### <a name="general"></a>Ogólne

# <a name="net-core-2xtabnetcore2x"></a>[.NET core 2.x](#tab/netcore2x)

| Polecenie                             | Funkcja                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [Kompilacja DotNet](dotnet-build.md)     | Tworzy aplikacji .NET Core.                                     |
| [Wyczyść DotNet](dotnet-clean.md)     | Wyczyść wyniki do kompilacji.                                              |
| [Pomoc DotNet](dotnet-help.md)       | Przedstawia szczegółowe dokumentacji online dla polecenia.           |
| [Migrowanie DotNet](dotnet-migrate.md) | Wykonuje migrację prawidłowy projekt Preview 2 projektu .NET Core SDK 1.0.  |
| [DotNet msbuild](dotnet-msbuild.md) | Zapewnia dostęp do wiersza polecenia programu MSBuild.                        |
| [nowe DotNet](dotnet-new.md)         | Inicjuje języka C# lub projektów F # dla danego szablonu.                |
| [Pakiet DotNet](dotnet-pack.md)       | Tworzy pakiet NuGet kodu.                               |
| [Publikowanie DotNet](dotnet-publish.md) | Publikowanie aplikacji .NET framework zależne lub niezależne. |
| [Przywracanie DotNet](dotnet-restore.md) | Przywraca zależności dla danej aplikacji.                  |
| [Uruchom DotNet](dotnet-run.md)         | Aplikacja jest uruchamiana ze źródła.                                   |
| [DotNet sln](dotnet-sln.md)         | Opcje do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.       |
| [Magazyn DotNet](dotnet-store.md)     | Przechowuje zestawy w magazynie pakietów środowiska wykonawczego.                     |
| [DotNet test](dotnet-test.md)       | Uruchamia testy przy użyciu runner testu.                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET core 1.x](#tab/netcore1x)

| Polecenie                             | Funkcja                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [Kompilacja DotNet](dotnet-build.md)     | Tworzy aplikacji .NET Core.                                     |
| [Wyczyść DotNet](dotnet-clean.md)     | Wyczyść wyniki do kompilacji.                                              |
| [Migrowanie DotNet](dotnet-migrate.md) | Wykonuje migrację prawidłowy projekt Preview 2 projektu .NET Core SDK 1.0.  |
| [DotNet msbuild](dotnet-msbuild.md) | Zapewnia dostęp do wiersza polecenia programu MSBuild.                        |
| [nowe DotNet](dotnet-new.md)         | Inicjuje języka C# lub projektów F # dla danego szablonu.                |
| [Pakiet DotNet](dotnet-pack.md)       | Tworzy pakiet NuGet kodu.                               |
| [Publikowanie DotNet](dotnet-publish.md) | Publikowanie aplikacji .NET framework zależne lub niezależne. |
| [Przywracanie DotNet](dotnet-restore.md) | Przywraca zależności dla danej aplikacji.                  |
| [Uruchom DotNet](dotnet-run.md)         | Aplikacja jest uruchamiana ze źródła.                                   |
| [DotNet sln](dotnet-sln.md)         | Opcje do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.       |
| [DotNet test](dotnet-test.md)       | Uruchamia testy przy użyciu runner testu.                                     |

---

### <a name="project-references"></a>Odwołania do projektu

Polecenie | Funkcja
--- | ---
[DotNet Dodaj odwołanie](dotnet-add-reference.md) | Dodaj odwołanie do projektu.
[Odwołanie do listy DotNet](dotnet-list-reference.md) | Lista odwołań do projektu.
[DotNet Usuń odwołanie](dotnet-remove-reference.md) | Usuń odwołanie do projektu.

### <a name="nuget-packages"></a>Pakiety NuGet

Polecenie | Funkcja
--- | ---
[DotNet Dodaj pakiet](dotnet-add-package.md) | Dodaj pakiet NuGet.
[Pakiet Usuń DotNet](dotnet-remove-package.md) | Usunięcie pakietu NuGet.

### <a name="nuget-commands"></a>Polecenia NuGet

Polecenie | Funkcja
--- | ---
[Usuń nuget DotNet](dotnet-nuget-delete.md) | Usuwa lub unlists pakietu z serwera.
[Zmienne lokalne nuget DotNet](dotnet-nuget-locals.md) | Czyści lub wyświetla ich listę zasobów lokalnych NuGet np. pamięci podręcznej żądania http, tymczasowego pamięci podręcznej lub folderu packages globalne dla komputera.
[wypychania nuget DotNet](dotnet-nuget-push.md) | Wypychanie pakietu do serwera i publikuje ją.

## <a name="examples"></a>Przykłady

Inicjowanie przykładowej aplikacji konsoli .NET Core, który można skompilować i uruchomić:

`dotnet new console`

Przywróć zależności dla danej aplikacji:

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Tworzenie projektu i jego zależności w podanym katalogu:

`dotnet build`

Uruchamianie aplikacji zależnych od framework o nazwie `myapp.dll`:

`dotnet myapp.dll`

## <a name="environment-variables"></a>Zmienne środowiskowe

`DOTNET_PACKAGES`

Pakiet główny pamięci podręcznej. Jeśli nie został ustawiony, domyślnie `$HOME/.nuget/packages` w systemie Unix lub `%HOME%\NuGet\Packages` w systemie Windows.

`DOTNET_SERVICING`

Określa lokalizację obsługi indeksu jest używany przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Określa, czy dane dotyczące użycia narzędzia .NET Core został zebrany i wysyłany do firmy Microsoft. Ustaw `true` Aby zrezygnować z funkcji telemetrii (wartości `true`, `1`, lub `yes` zaakceptowane), w przeciwnym razie należy ustawić `false` w funkcji telemetrii (wartości `false`, `0`, lub `no` akceptowane). Jeśli nie jest ustawiony, wartości domyślne jest `false`, i funkcja telemetrii jest aktywna.
