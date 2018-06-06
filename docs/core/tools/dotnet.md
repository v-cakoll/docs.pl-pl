---
title: polecenie DotNet - .NET Core interfejsu wiersza polecenia
description: Informacje o poleceniu dotnet (ogólnego sterownik narzędzi interfejsu wiersza polecenia platformy .NET Core) i jej użycia.
author: mairaw
ms.author: mairaw
ms.date: 06/04/2018
ms.openlocfilehash: 6e9f37dbbf94d56266a7b424601845d4429b4a04
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753542"
---
# <a name="dotnet-command"></a>polecenie DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet` -Ogólne sterownik do uruchamiania polecenia wiersza polecenia.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-21tabnetcore21"></a>[Oprogramowanie .NET core 2.1](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a>Opis

`dotnet` jest ogólny sterownik łańcuch narzędzi interfejsu wiersza polecenia (CLI). Wywoływane na jego własnej, zapewnia użycia krótkie instrukcje.

Każdej z funkcji jest implementowany jako polecenia. Do korzystania z funkcji określono polecenia po `dotnet`, takich jak [ `dotnet build` ](dotnet-build.md). Wszystkie argumenty następujące polecenie to własną argumentów.

Tylko `dotnet` jest używany jako polecenia samodzielnie [aplikacje zależne od framework](../deploying/index.md). Określ aplikację DLL po `dotnet` zlecenie do wykonywania aplikacji (na przykład `dotnet myapp.dll`).

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[Oprogramowanie .NET core 2.1](#tab/netcore21)

`--additional-deps <PATH>`

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

`--list-runtimes`

Wyświetla zainstalowane środowiska wykonawczego platformy .NET Core.

`--list-sdks`

Wyświetla zainstalowane zestawy SDK Core .NET.

`--roll-forward-on-no-candidate-fx`

 Przedstawia przekazywania na ma kandydata framework udostępnionego.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`. Nie są obsługiwane w każdym poleceniu; zobacz stronę danego polecenia, aby ustalić, czy ta opcja jest dostępna.

`--version`

Drukuje wersji programu .NET Core SDK w użyciu.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--additional-deps <PATH>`

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

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`. Nie są obsługiwane w każdym poleceniu; zobacz stronę danego polecenia, aby ustalić, czy ta opcja jest dostępna.

`--version`

Drukuje wersji programu .NET Core SDK w użyciu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

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

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`. Nie są obsługiwane w każdym poleceniu; zobacz stronę danego polecenia, aby ustalić, czy ta opcja jest dostępna.

`--version`

Drukuje wersji programu .NET Core SDK w użyciu.

---

## <a name="dotnet-commands"></a>polecenia DotNet

### <a name="general"></a>Ogólne

# <a name="net-core-21tabnetcore21"></a>[Oprogramowanie .NET core 2.1](#tab/netcore21)

| Polecenie                                       | Funkcja                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | Tworzy aplikacji .NET Core.                                     |
| [Serwer kompilacji DotNet](dotnet-build-server.md) | Wchodzi w interakcję z serwerami uruchomione przez kompilację.                          |
| [dotnet clean](dotnet-clean.md)               | Wyczyść wyniki do kompilacji.                                                |
| [dotnet help](dotnet-help.md)                 | Przedstawia szczegółowe dokumentacji online dla polecenia.           |
| [dotnet migrate](dotnet-migrate.md)           | Wykonuje migrację prawidłowy projekt Preview 2 projektu .NET Core SDK 1.0.  |
| [dotnet msbuild](dotnet-msbuild.md)           | Zapewnia dostęp do wiersza polecenia programu MSBuild.                        |
| [dotnet new](dotnet-new.md)                   | Inicjuje języka C# lub projektów F # dla danego szablonu.                |
| [dotnet pack](dotnet-pack.md)                 | Tworzy pakiet NuGet kodu.                               |
| [dotnet publish](dotnet-publish.md)           | Publikowanie aplikacji .NET framework zależne lub niezależne. |
| [dotnet restore](dotnet-restore.md)           | Przywraca zależności dla danej aplikacji.                  |
| [dotnet run](dotnet-run.md)                   | Aplikacja jest uruchamiana ze źródła.                                   |
| [dotnet sln](dotnet-sln.md)                   | Opcje do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.       |
| [dotnet store](dotnet-store.md)               | Przechowuje zestawy w magazynie pakietów środowiska wykonawczego.                     |
| [dotnet test](dotnet-test.md)                 | Uruchamia testy przy użyciu runner testu.                                     |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

| Polecenie                             | Funkcja                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Tworzy aplikacji .NET Core.                                     |
| [dotnet clean](dotnet-clean.md)     | Wyczyść wyniki do kompilacji.                                              |
| [dotnet help](dotnet-help.md)       | Przedstawia szczegółowe dokumentacji online dla polecenia.           |
| [dotnet migrate](dotnet-migrate.md) | Wykonuje migrację prawidłowy projekt Preview 2 projektu .NET Core SDK 1.0.  |
| [dotnet msbuild](dotnet-msbuild.md) | Zapewnia dostęp do wiersza polecenia programu MSBuild.                        |
| [dotnet new](dotnet-new.md)         | Inicjuje języka C# lub projektów F # dla danego szablonu.                |
| [dotnet pack](dotnet-pack.md)       | Tworzy pakiet NuGet kodu.                               |
| [dotnet publish](dotnet-publish.md) | Publikowanie aplikacji .NET framework zależne lub niezależne. |
| [dotnet restore](dotnet-restore.md) | Przywraca zależności dla danej aplikacji.                  |
| [dotnet run](dotnet-run.md)         | Aplikacja jest uruchamiana ze źródła.                                   |
| [dotnet sln](dotnet-sln.md)         | Opcje do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.       |
| [dotnet store](dotnet-store.md)     | Przechowuje zestawy w magazynie pakietów środowiska wykonawczego.                     |
| [dotnet test](dotnet-test.md)       | Uruchamia testy przy użyciu runner testu.                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

| Polecenie                             | Funkcja                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Tworzy aplikacji .NET Core.                                     |
| [dotnet clean](dotnet-clean.md)     | Wyczyść wyniki do kompilacji.                                              |
| [dotnet migrate](dotnet-migrate.md) | Wykonuje migrację prawidłowy projekt Preview 2 projektu .NET Core SDK 1.0.  |
| [dotnet msbuild](dotnet-msbuild.md) | Zapewnia dostęp do wiersza polecenia programu MSBuild.                        |
| [dotnet new](dotnet-new.md)         | Inicjuje języka C# lub projektów F # dla danego szablonu.                |
| [dotnet pack](dotnet-pack.md)       | Tworzy pakiet NuGet kodu.                               |
| [dotnet publish](dotnet-publish.md) | Publikowanie aplikacji .NET framework zależne lub niezależne. |
| [dotnet restore](dotnet-restore.md) | Przywraca zależności dla danej aplikacji.                  |
| [dotnet run](dotnet-run.md)         | Aplikacja jest uruchamiana ze źródła.                                   |
| [dotnet sln](dotnet-sln.md)         | Opcje do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.       |
| [dotnet test](dotnet-test.md)       | Uruchamia testy przy użyciu runner testu.                                     |

---

### <a name="project-references"></a>Odwołania do projektu

Polecenie | Funkcja
--- | ---
[dotnet add reference](dotnet-add-reference.md) | Dodaje odwołanie do projektu.
[dotnet list reference](dotnet-list-reference.md) | Wyświetla listę odwołań do projektu.
[dotnet remove reference](dotnet-remove-reference.md) | Usuwa odwołanie do projektu.

### <a name="nuget-packages"></a>Pakiety NuGet

Polecenie | Funkcja
--- | ---
[dotnet add package](dotnet-add-package.md) | Dodaje pakiet NuGet.
[dotnet remove package](dotnet-remove-package.md) | Usuwa pakiet NuGet.

### <a name="nuget-commands"></a>Polecenia NuGet

Polecenie | Funkcja
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | Usuwa lub unlists pakietu z serwera.
[dotnet nuget locals](dotnet-nuget-locals.md) | Czyści lub wyświetla ich listę zasobów lokalnych NuGet np. pamięci podręcznej żądania http, tymczasowego pamięci podręcznej lub folderu packages globalne dla komputera.
[dotnet nuget push](dotnet-nuget-push.md) | Wypychanie pakietu do serwera i publikuje ją.

### <a name="global-tools-commands"></a>Polecenia narzędzia globalne

[Narzędzia globalne .NET core](global-tools.md) są dostępne strating przy użyciu zestawu SDK .NET Core 2.1.300:

Polecenie | Funkcja
--- | ---
[Instalowanie narzędzi DotNet](dotnet-tool-install.md) | Instaluje narzędzie globalne na tym komputerze.
[Lista narzędzi DotNet](dotnet-tool-list.md) | Wyświetla wszystkie narzędzia globalne aktualnie zainstalowany domyślny katalog na komputerze lub w określonej ścieżce.
[Odinstaluj narzędzie DotNet](dotnet-tool-uninstall.md) | Odinstalowuje narzędzie globalne z komputera.
[Aktualizacja narzędzi DotNet](dotnet-tool-update.md) | Aktualizuje narzędzie globalne na tym komputerze.

### <a name="additional-tools"></a>Dodatkowe narzędzia

Począwszy od programu .NET Core SDK 2.1.300, szereg narzędzi, które były dostępne tylko na projekt na podstawie przy użyciu `DotnetCliToolReference` są teraz dostępne jako część zestawu SDK .NET Core. Narzędzia te obejmują:

| Narzędzie                                              | Funkcja                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| certyfikaty dla deweloperów                                         | Tworzy i którymi zarządza programowanie certyfikatów.                |
| [EF](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core narzędzia wiersza polecenia.                    |
| pamięć podręczna SQL                                         | Narzędzia wiersza polecenia pamięci podręcznej programu SQL Server.                         |
| [hasła użytkownika](/aspnet/core/security/app-secrets) | Zarządza programowanie hasła użytkownika.                            |
| [Czujki](/aspnet/core/tutorials/dotnet-watch)      | Uruchamia obserwatora pliku, który uruchamia polecenie zmianach plików. |

Aby uzyskać więcej informacji na temat narzędzia wykonania `dotnet <tool-name> --help`.

## <a name="examples"></a>Przykłady

Tworzy nową aplikację konsolową .NET Core:

`dotnet new console`

Przywróć zależności dla danej aplikacji:

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Tworzenie projektu i jego zależności w podanym katalogu:

`dotnet build`

Uruchamianie aplikacji zależnych od framework o nazwie `myapp.dll`:

`dotnet myapp.dll`

## <a name="environment-variables"></a>Zmienne środowiskowe

# <a name="net-core-21tabnetcore21"></a>[Oprogramowanie .NET core 2.1](#tab/netcore21)

`DOTNET_PACKAGES`

Pakiet główny pamięci podręcznej. Jeśli nie został ustawiony, domyślnie `$HOME/.nuget/packages` w systemie Unix lub `%HOME%\NuGet\Packages` w systemie Windows.

`DOTNET_SERVICING`

Określa lokalizację obsługi indeksu jest używany przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Określa, czy dane dotyczące użycia narzędzia .NET Core został zebrany i wysyłany do firmy Microsoft. Ustaw `true` Aby zrezygnować z funkcji telemetrii (wartości `true`, `1`, lub `yes` akceptowane). W przeciwnym razie wartość `false` do uczestnictwa w funkcji telemetrii (wartości `false`, `0`, lub `no` akceptowane). Jeśli nie jest ustawiona, wartością domyślną jest `false` i funkcja telemetrii jest aktywna.

`DOTNET_MULTILEVEL_LOOKUP`

Określa, czy środowiska uruchomieniowego .NET Core, udostępnionych framework lub zestawu SDK są rozpoznane w globalnej lokalizacji. Jeśli nie jest ustawiona, domyślne `true`. Ustaw `false` rozwiązania z globalnej lokalizacji i mają odizolowane instalacji platformy .NET Core (wartości `0` lub `false` są akceptowane). Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowe zobacz [wyszukiwania SharedFX wielopoziomowej](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

Wyłącza niewielkie wersji przenoszenia do przodu. Aby uzyskać więcej informacji, zobacz [przekazywane dalej](../whats-new/dotnet-core-2-1.md#roll-forward).

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`DOTNET_PACKAGES`

Pakiet główny pamięci podręcznej. Jeśli nie został ustawiony, domyślnie `$HOME/.nuget/packages` w systemie Unix lub `%HOME%\NuGet\Packages` w systemie Windows.

`DOTNET_SERVICING`

Określa lokalizację obsługi indeksu jest używany przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Określa, czy dane dotyczące użycia narzędzia .NET Core został zebrany i wysyłany do firmy Microsoft. Ustaw `true` Aby zrezygnować z funkcji telemetrii (wartości `true`, `1`, lub `yes` akceptowane). W przeciwnym razie wartość `false` do uczestnictwa w funkcji telemetrii (wartości `false`, `0`, lub `no` akceptowane). Jeśli nie jest ustawiona, wartością domyślną jest `false` i funkcja telemetrii jest aktywna.

`DOTNET_MULTILEVEL_LOOKUP`

Określa, czy środowiska uruchomieniowego .NET Core, udostępnionych framework lub zestawu SDK są rozpoznane w globalnej lokalizacji. Jeśli nie jest ustawiona, domyślne `true`. Ustaw `false` rozwiązania z globalnej lokalizacji i mają odizolowane instalacji platformy .NET Core (wartości `0` lub `false` są akceptowane). Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowe zobacz [wyszukiwania SharedFX wielopoziomowej](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`DOTNET_PACKAGES`

Pakiet główny pamięci podręcznej. Jeśli nie został ustawiony, domyślnie `$HOME/.nuget/packages` w systemie Unix lub `%HOME%\NuGet\Packages` w systemie Windows.

`DOTNET_SERVICING`

Określa lokalizację obsługi indeksu jest używany przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Określa, czy dane dotyczące użycia narzędzia .NET Core został zebrany i wysyłany do firmy Microsoft. Ustaw `true` Aby zrezygnować z funkcji telemetrii (wartości `true`, `1`, lub `yes` akceptowane). W przeciwnym razie wartość `false` do uczestnictwa w funkcji telemetrii (wartości `false`, `0`, lub `no` akceptowane). Jeśli nie jest ustawiona, wartością domyślną jest `false` i funkcja telemetrii jest aktywna.

---
