---
title: polecenia DotNet
description: Więcej informacji na temat polecenia dotnet (ogólny sterownik dla narzędzi interfejsu wiersza polecenia platformy .NET Core) i sposób jej użycia.
ms.date: 06/04/2018
ms.openlocfilehash: 107a529952cce62dac840874fa5d6d8986376adf
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185639"
---
# <a name="dotnet-command"></a>polecenia DotNet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet` — Narzędzie służące do zarządzania kodu źródłowego .NET i plikach binarnych.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)
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

`dotnet` to narzędzie do zarządzania kodu źródłowego .NET i pliki binarne. Udostępnia ona polecenia, które wykonują określone zadania, takie jak [ `dotnet build` ](dotnet-build.md) i [ `dotnet run` ](dotnet-run.md). Każde polecenie definiuje swój własny argumentów. Typ `--help` zatwierdzając każde z nich do dostępu krótki opis dokumentacji pomocy.

`dotnet` może służyć do uruchamiania aplikacji, określając aplikacji biblioteki DLL, takie jak `dotnet myapp.dll`. Zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) dla Aby dowiedzieć się więcej o opcjach wdrażania.

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--additional-deps <PATH>`

Ścieżka do dodatkowych *deps.json* pliku.

`--additionalprobingpath <PATH>`

Ścieżki zawierające sondowania zasad i zestawy do sondowania.

`-d|--diagnostics`

Umożliwia diagnostyczne dane wyjściowe.

`--fx-version <VERSION>`

Wersja środowiska uruchomieniowego .NET Core do użycia, aby uruchomić aplikację.

`-h|--help`

Wyświetla dokumentację dotyczącą danego polecenia, takie jak `dotnet build --help`. `dotnet --help` Wyświetla listę dostępnych poleceń.

`--info`

Drukuje szczegółowe informacje dotyczące instalacji platformy .NET Core i środowiska maszyny, takich jak bieżący system operacyjny i zatwierdzenie SHA wersji platformy .NET Core.

`--list-runtimes`

Wyświetla zainstalowane środowiska uruchomieniowe platformy .NET Core.

`--list-sdks`

Wyświetla zainstalowanych zestawów .NET Core SDK.

`--roll-forward-on-no-candidate-fx <N>`

Definiuje zachowanie, gdy wymaganej struktury udostępnionego nie jest dostępna. `N` może być:
* `0` -Wyłącz nawet podverze przenoszenia do przodu.
* `1` -Uaktualniane w wersji pomocniczej, ale nie w wersji głównej. Jest to zachowanie domyślne.
* `2` -Uaktualniane na wersje pomocnicze, jak i głównej.

 Aby uzyskać więcej informacji, zobacz [uaktualniane](../whats-new/dotnet-core-2-1.md#roll-forward).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`. Nie jest obsługiwana w każdym poleceniu; zobacz stronę określone polecenie, aby określić, jeśli ta opcja jest dostępna.

`--version`

Drukuje wersję zestawu .NET Core SDK w użyciu.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--additional-deps <PATH>`

Ścieżka do dodatkowych *deps.json* pliku.

`--additionalprobingpath <PATH>`

Ścieżki zawierające sondowania zasad i zestawy do sondowania.

`-d|--diagnostics`

Umożliwia diagnostyczne dane wyjściowe.

`--fx-version <VERSION>`

Wersja środowiska uruchomieniowego .NET Core do użycia, aby uruchomić aplikację.

`-h|--help`

Wyświetla dokumentację dotyczącą danego polecenia, takie jak `dotnet build --help`. `dotnet --help` Wyświetla listę dostępnych poleceń.

`--info`

Drukuje szczegółowe informacje dotyczące instalacji platformy .NET Core i środowiska maszyny, takich jak bieżący system operacyjny i zatwierdzenie SHA wersji platformy .NET Core.

`--roll-forward-on-no-candidate-fx`

 Wyłącza wersja pomocnicza przenoszenie do przodu, jeśli ustawiono `0`. Aby uzyskać więcej informacji, zobacz [uaktualniane](../whats-new/dotnet-core-2-1.md#roll-forward).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`. Nie jest obsługiwana w każdym poleceniu; zobacz stronę określone polecenie, aby określić, jeśli ta opcja jest dostępna.

`--version`

Drukuje wersję zestawu .NET Core SDK w użyciu.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--additionalprobingpath <PATH>`

Ścieżki zawierające sondowania zasad i zestawy do sondowania.

`-d|--diagnostics`

Umożliwia diagnostyczne dane wyjściowe.

`--fx-version <VERSION>`

Wersja środowiska uruchomieniowego .NET Core do użycia, aby uruchomić aplikację.

`-h|--help`

Wyświetla dokumentację dotyczącą danego polecenia, takie jak `dotnet build --help`. `dotnet --help` Wyświetla listę dostępnych poleceń.

`--info`

Drukuje szczegółowe informacje dotyczące instalacji platformy .NET Core i środowiska maszyny, takich jak bieżący system operacyjny i zatwierdzenie SHA wersji platformy .NET Core.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`. Nie jest obsługiwana w każdym poleceniu; zobacz stronę określone polecenie, aby określić, jeśli ta opcja jest dostępna.

`--version`

Drukuje wersję zestawu .NET Core SDK w użyciu.

---

## <a name="dotnet-commands"></a>polecenia DotNet

### <a name="general"></a>Ogólne

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

| Polecenie                                       | Funkcja                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | Tworzy aplikację .NET Core.                                     |
| [dotnet build-server](dotnet-build-server.md) | Wchodzi w interakcję z serwerami, uruchomione przez kompilację.                          |
| [dotnet clean](dotnet-clean.md)               | Czysta kompilacja danych wyjściowych.                                                |
| [dotnet help](dotnet-help.md)                 | Zawiera bardziej szczegółowe dokumentację online dla polecenia.           |
| [dotnet migrate](dotnet-migrate.md)           | Prawidłowy projekt w wersji 2 jest migrowana do projektu .NET Core SDK 1.0.  |
| [dotnet msbuild](dotnet-msbuild.md)           | Zapewnia dostęp do wiersza polecenia programu MSBuild.                        |
| [dotnet new](dotnet-new.md)                   | Inicjuje C# lub F# projektu dla danego szablonu.                |
| [dotnet pack](dotnet-pack.md)                 | Tworzy pakiet NuGet kodu.                               |
| [dotnet publish](dotnet-publish.md)           | Publikuje aplikacji autonomicznej .NET framework-zależnych od ustawień lokalnych lub niezależna. |
| [dotnet restore](dotnet-restore.md)           | Przywraca zależności dla danej aplikacji.                  |
| [dotnet run](dotnet-run.md)                   | Ze źródła do uruchamiania aplikacji.                                   |
| [dotnet sln](dotnet-sln.md)                   | Opcje służące do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.       |
| [dotnet store](dotnet-store.md)               | Przechowuje zestawy w Magazyn pakietu środowiska uruchomieniowego.                     |
| [dotnet test](dotnet-test.md)                 | Uruchamia testy za pomocą narzędzia test runner.                                     |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

| Polecenie                             | Funkcja                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Tworzy aplikację .NET Core.                                     |
| [dotnet clean](dotnet-clean.md)     | Czysta kompilacja danych wyjściowych.                                              |
| [dotnet help](dotnet-help.md)       | Zawiera bardziej szczegółowe dokumentację online dla polecenia.           |
| [dotnet migrate](dotnet-migrate.md) | Prawidłowy projekt w wersji 2 jest migrowana do projektu .NET Core SDK 1.0.  |
| [dotnet msbuild](dotnet-msbuild.md) | Zapewnia dostęp do wiersza polecenia programu MSBuild.                        |
| [dotnet new](dotnet-new.md)         | Inicjuje C# lub F# projektu dla danego szablonu.                |
| [dotnet pack](dotnet-pack.md)       | Tworzy pakiet NuGet kodu.                               |
| [dotnet publish](dotnet-publish.md) | Publikuje aplikacji autonomicznej .NET framework-zależnych od ustawień lokalnych lub niezależna. |
| [dotnet restore](dotnet-restore.md) | Przywraca zależności dla danej aplikacji.                  |
| [dotnet run](dotnet-run.md)         | Ze źródła do uruchamiania aplikacji.                                   |
| [dotnet sln](dotnet-sln.md)         | Opcje służące do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.       |
| [dotnet store](dotnet-store.md)     | Przechowuje zestawy w Magazyn pakietu środowiska uruchomieniowego.                     |
| [dotnet test](dotnet-test.md)       | Uruchamia testy za pomocą narzędzia test runner.                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

| Polecenie                             | Funkcja                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Tworzy aplikację .NET Core.                                     |
| [dotnet clean](dotnet-clean.md)     | Czysta kompilacja danych wyjściowych.                                              |
| [dotnet migrate](dotnet-migrate.md) | Prawidłowy projekt w wersji 2 jest migrowana do projektu .NET Core SDK 1.0.  |
| [dotnet msbuild](dotnet-msbuild.md) | Zapewnia dostęp do wiersza polecenia programu MSBuild.                        |
| [dotnet new](dotnet-new.md)         | Inicjuje C# lub F# projektu dla danego szablonu.                |
| [dotnet pack](dotnet-pack.md)       | Tworzy pakiet NuGet kodu.                               |
| [dotnet publish](dotnet-publish.md) | Publikuje aplikacji autonomicznej .NET framework-zależnych od ustawień lokalnych lub niezależna. |
| [dotnet restore](dotnet-restore.md) | Przywraca zależności dla danej aplikacji.                  |
| [dotnet run](dotnet-run.md)         | Ze źródła do uruchamiania aplikacji.                                   |
| [dotnet sln](dotnet-sln.md)         | Opcje służące do dodawania, usuwania i wyświetlić listę projektów w pliku rozwiązania.       |
| [dotnet test](dotnet-test.md)       | Uruchamia testy za pomocą narzędzia test runner.                                     |

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
[dotnet nuget locals](dotnet-nuget-locals.md) | Usuwa lub wyświetla ich listę zasobów lokalnych NuGet, takie jak pamięć podręczna żądań http, tymczasowej pamięci podręcznej lub folder komputera globalnymi pakietami.
[dotnet nuget push](dotnet-nuget-push.md) | Wypychanie pakietu do serwera i publikuje go.

### <a name="global-tools-commands"></a>Polecenia narzędzia globalne

[Narzędzia programu .NET core globalnego](global-tools.md) są dostępne, począwszy od programu .NET Core SDK 2.1.300:

Polecenie | Funkcja
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Instaluje narzędzie globalne na komputerze.
[dotnet tool list](dotnet-tool-list.md) | Wyświetla listę wszystkich narzędzi globalnego aktualnie zainstalowane w domyślnym katalogu na komputerze lub w określonej ścieżce.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Odinstalowuje narzędzie globalne z Twojego komputera.
[dotnet tool update](dotnet-tool-update.md) | Aktualizuje narzędzie globalne na swojej maszynie.

### <a name="additional-tools"></a>Dodatkowe narzędzia

Począwszy od programu .NET Core SDK 2.1.300, wiele narzędzi, które były dostępne tylko na podstawę projektu przy użyciu `DotnetCliToolReference` są teraz dostępne jako część zestawu .NET Core SDK. Te narzędzia są wymienione w poniższej tabeli:

| Narzędzie                                              | Funkcja                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | Tworzy i zarządza certyfikatami rozwoju.                |
| [EF](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core narzędzia wiersza polecenia.                    |
| sql-cache                                         | Narzędzia wiersza polecenia pamięci podręcznej programu SQL Server.                         |
| [user-secrets](/aspnet/core/security/app-secrets) | Umożliwia zarządzanie wpisami tajnymi użytkowników rozwoju.                            |
| [watch](/aspnet/core/tutorials/dotnet-watch)      | Uruchamia obserwatora pliku, który uruchamia polecenie, gdy zmienią się pliki. |

Aby uzyskać więcej informacji na temat każdego z narzędzi, wpisz `dotnet <tool-name> --help`.

## <a name="examples"></a>Przykłady

Tworzy nową aplikację konsoli .NET Core:

`dotnet new console`

Przywróć zależności dla danej aplikacji:

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Tworzenie projektu i jego zależności w danym katalogu:

`dotnet build`

Uruchamianie aplikacji biblioteki DLL, takich jak `myapp.dll`:

`dotnet myapp.dll`

## <a name="environment-variables"></a>Zmienne środowiskowe

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`DOTNET_PACKAGES`

Pakiet główny pamięci podręcznej. Jeśli nie został ustawiony, jego wartość domyślna to `$HOME/.nuget/packages` w systemach Unix lub `%HOME%\NuGet\Packages` na Windows.

`DOTNET_SERVICING`

Określa lokalizację obsługi indeksu do użycia przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Określa, czy dane dotyczące użycia narzędzia .NET Core jest zbierane i przesyłane do firmy Microsoft. Ustaw `true` można zrezygnować z funkcji danych telemetrycznych (wartości `true`, `1`, lub `yes` zaakceptowane). W przeciwnym wypadku ustaw `false` można zdecydować się na funkcje telemetrii (wartości `false`, `0`, lub `no` zaakceptowane). Jeśli nie jest ustawiona, wartość domyślna to `false` i funkcja telemetrii jest aktywna.

`DOTNET_MULTILEVEL_LOOKUP`

Określa, czy środowiska uruchomieniowego, udostępnionej platformy lub zestawu SDK platformy .NET Core nie są rozwiązane z globalnej lokalizacji. Jeśli nie został ustawiony, jego wartość domyślna to `true`. Ustaw `false` rozwiązania z globalnej lokalizacji i izolowanych instalacji platformy .NET Core (wartości `0` lub `false` są akceptowane). Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowe zobacz [wyszukiwania SharedFX wielopoziomowymi](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

Wyłącza wersja pomocnicza przenoszenie do przodu, jeśli ustawiono `0`. Aby uzyskać więcej informacji, zobacz [uaktualniane](../whats-new/dotnet-core-2-1.md#roll-forward).

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`DOTNET_PACKAGES`

Pakiet główny pamięci podręcznej. Jeśli nie został ustawiony, jego wartość domyślna to `$HOME/.nuget/packages` w systemach Unix lub `%HOME%\NuGet\Packages` na Windows.

`DOTNET_SERVICING`

Określa lokalizację obsługi indeksu do użycia przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Określa, czy dane dotyczące użycia narzędzia .NET Core jest zbierane i przesyłane do firmy Microsoft. Ustaw `true` można zrezygnować z funkcji danych telemetrycznych (wartości `true`, `1`, lub `yes` zaakceptowane). W przeciwnym wypadku ustaw `false` można zdecydować się na funkcje telemetrii (wartości `false`, `0`, lub `no` zaakceptowane). Jeśli nie jest ustawiona, wartość domyślna to `false` i funkcja telemetrii jest aktywna.

`DOTNET_MULTILEVEL_LOOKUP`

Określa, czy środowiska uruchomieniowego, udostępnionej platformy lub zestawu SDK platformy .NET Core nie są rozwiązane z globalnej lokalizacji. Jeśli nie został ustawiony, jego wartość domyślna to `true`. Ustaw `false` rozwiązania z globalnej lokalizacji i izolowanych instalacji platformy .NET Core (wartości `0` lub `false` są akceptowane). Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowe zobacz [wyszukiwania SharedFX wielopoziomowymi](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`DOTNET_PACKAGES`

Pakiet główny pamięci podręcznej. Jeśli nie został ustawiony, jego wartość domyślna to `$HOME/.nuget/packages` w systemach Unix lub `%HOME%\NuGet\Packages` na Windows.

`DOTNET_SERVICING`

Określa lokalizację obsługi indeksu do użycia przez hosta udostępnionych podczas ładowania środowiska uruchomieniowego.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Określa, czy dane dotyczące użycia narzędzia .NET Core jest zbierane i przesyłane do firmy Microsoft. Ustaw `true` można zrezygnować z funkcji danych telemetrycznych (wartości `true`, `1`, lub `yes` zaakceptowane). W przeciwnym wypadku ustaw `false` można zdecydować się na funkcje telemetrii (wartości `false`, `0`, lub `no` zaakceptowane). Jeśli nie jest ustawiona, wartość domyślna to `false` i funkcja telemetrii jest aktywna.

---
