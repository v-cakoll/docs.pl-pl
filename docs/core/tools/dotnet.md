---
title: dotnet — polecenie
description: Dowiedz się więcej na temat polecenia dotnet (sterownika generycznego dla narzędzi interfejs wiersza polecenia platformy .NET Core) i jego użycia.
ms.date: 06/04/2018
ms.openlocfilehash: 8de6a6f7e584dc472dc23d60f113b03610abb3ef
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926225"
---
# <a name="dotnet-command"></a>dotnet — polecenie

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Nazwa

`dotnet`-Narzędzie do zarządzania kodem źródłowym i plikami binarnymi platformy .NET.

## <a name="synopsis"></a>Streszczenie

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```console
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a>Opis

`dotnet`jest narzędziem do zarządzania kodem źródłowym i plikami binarnymi platformy .NET. Udostępnia polecenia wykonujące określone zadania, takie jak [`dotnet build`](dotnet-build.md) i. [`dotnet run`](dotnet-run.md) Każde polecenie definiuje własne argumenty. Wpisz `--help` po każdym poleceniu, aby uzyskać dostęp do krótkiej dokumentacji pomocy.

`dotnet`może służyć do uruchamiania aplikacji przez określenie biblioteki DLL aplikacji, takiej jak `dotnet myapp.dll`. Zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) w celu uzyskania informacji na temat opcji wdrażania.

## <a name="options"></a>Opcje

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--additional-deps <PATH>`

Ścieżka do dodatkowego pliku *. deps. JSON* .

`--additionalprobingpath <PATH>`

Ścieżka zawierająca zasady i zestawy do sondowania.

`--depsfile`

Ścieżka do pliku *deps. JSON* .

Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów. Aby uzyskać więcej informacji na temat tego pliku, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) w serwisie GitHub.

`-d|--diagnostics`

Włącza diagnostykę danych wyjściowych.

`--fx-version <VERSION>`

Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.

`-h|--help`

Drukuje dokumentację dla danego polecenia, na przykład `dotnet build --help`. `dotnet --help`Drukuje listę dostępnych poleceń.

`--info`

Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.

`--list-runtimes`

Wyświetla zainstalowane środowiska uruchomieniowe platformy .NET Core.

`--list-sdks`

Wyświetla zainstalowane zestawy SDK platformy .NET Core.

`--roll-forward-on-no-candidate-fx <N>`

Definiuje zachowanie, gdy wymagana architektura udostępniona jest niedostępna. `N` może być:

- `0`-Wyłącz parzystą wersję pomocniczą do przodu.
- `1`— Przewinięcie do wersji pomocniczej, ale nie w wersji głównej. Jest to zachowanie domyślne.
- `2`— Przewinięcie do przodu w wersjach pomocniczych i głównych.

 Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).

`--runtimeconfig`

Ścieżka do pliku *runtimeconfig. JSON* .

Plik *runtimeconfig. JSON* to plik konfiguracji zawierający ustawienia konfiguracji środowiska uruchomieniowego. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) w serwisie GitHub.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]` Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.

`--version`

Drukuje używaną wersję zestaw .NET Core SDK.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--additional-deps <PATH>`

Ścieżka do dodatkowego pliku *. deps. JSON* .

`--additionalprobingpath <PATH>`

Ścieżka zawierająca zasady i zestawy do sondowania.

`--depsfile`

Ścieżka do pliku *deps. JSON* .

Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów. Aby uzyskać więcej informacji na temat tego pliku, zobacz [pliki konfiguracji środowiska uruchomieniowego w serwisie GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

`-d|--diagnostics`

Włącza diagnostykę danych wyjściowych.

`--fx-version <VERSION>`

Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.

`-h|--help`

Drukuje dokumentację dla danego polecenia, na przykład `dotnet build --help`. `dotnet --help`Drukuje listę dostępnych poleceń.

`--info`

Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.

`--roll-forward-on-no-candidate-fx`

 Wyłącza dodatkową wersję do przodu, jeśli jest ustawiona `0`na. Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).

`--runtimeconfig`

Ścieżka do pliku *runtimeconfig. JSON* .

Plik *runtimeconfig. JSON* to plik konfiguracji zawierający ustawienia konfiguracji środowiska uruchomieniowego. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego w serwisie GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]` Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.

`--version`

Drukuje używaną wersję zestaw .NET Core SDK.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--additionalprobingpath <PATH>`

Ścieżka zawierająca zasady i zestawy do sondowania.

`--depsfile`

Ścieżka do pliku *deps. JSON* .

Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów. Aby uzyskać więcej informacji na temat tego pliku, zobacz [pliki konfiguracji środowiska uruchomieniowego w serwisie GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

`-d|--diagnostics`

Włącza diagnostykę danych wyjściowych.

`--fx-version <VERSION>`

Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.

`-h|--help`

Drukuje dokumentację dla danego polecenia, na przykład `dotnet build --help`. `dotnet --help`Drukuje listę dostępnych poleceń.

`--info`

Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.

`--runtimeconfig`

Ścieżka do pliku *runtimeconfig. JSON* .

Plik *runtimeconfig. JSON* to plik konfiguracji zawierający ustawienia konfiguracji środowiska uruchomieniowego. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego w serwisie GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]` Nieobsługiwane w każdym poleceniu; Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.

`--version`

Drukuje używaną wersję zestaw .NET Core SDK.

---

## <a name="dotnet-commands"></a>Polecenia dotnet

### <a name="general"></a>Ogólne

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

| Polecenie                                       | Funkcja                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | Kompiluje aplikację platformy .NET Core.                                     |
| [dotnet build-server](dotnet-build-server.md) | Współdziała z serwerami uruchomionymi przez kompilację.                          |
| [dotnet clean](dotnet-clean.md)               | Czyste dane wyjściowe kompilacji.                                                |
| [dotnet help](dotnet-help.md)                 | Przedstawia bardziej szczegółową dokumentację dla polecenia w trybie online.           |
| [dotnet migrate](dotnet-migrate.md)           | Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.  |
| [dotnet msbuild](dotnet-msbuild.md)           | Zapewnia dostęp do wiersza polecenia programu MSBuild.                        |
| [dotnet new](dotnet-new.md)                   | Inicjuje projekt C# lub F# dla danego szablonu.                |
| [dotnet pack](dotnet-pack.md)                 | Tworzy pakiet NuGet kodu.                               |
| [dotnet publish](dotnet-publish.md)           | Publikuje zależne od programu .NET Framework lub samodzielną aplikację. |
| [dotnet restore](dotnet-restore.md)           | Przywraca zależności dla danej aplikacji.                  |
| [dotnet run](dotnet-run.md)                   | Uruchamia aplikację ze źródła.                                   |
| [dotnet sln](dotnet-sln.md)                   | Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.       |
| [dotnet store](dotnet-store.md)               | Przechowuje zestawy w magazynie pakietów środowiska uruchomieniowego.                     |
| [dotnet test](dotnet-test.md)                 | Uruchamia testy przy użyciu modułu uruchamiającego testy.                                     |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

| Polecenie                             | Funkcja                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Kompiluje aplikację platformy .NET Core.                                     |
| [dotnet clean](dotnet-clean.md)     | Czyste dane wyjściowe kompilacji.                                              |
| [dotnet help](dotnet-help.md)       | Przedstawia bardziej szczegółową dokumentację dla polecenia w trybie online.           |
| [dotnet migrate](dotnet-migrate.md) | Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.  |
| [dotnet msbuild](dotnet-msbuild.md) | Zapewnia dostęp do wiersza polecenia programu MSBuild.                        |
| [dotnet new](dotnet-new.md)         | Inicjuje projekt C# lub F# dla danego szablonu.                |
| [dotnet pack](dotnet-pack.md)       | Tworzy pakiet NuGet kodu.                               |
| [dotnet publish](dotnet-publish.md) | Publikuje zależne od programu .NET Framework lub samodzielną aplikację. |
| [dotnet restore](dotnet-restore.md) | Przywraca zależności dla danej aplikacji.                  |
| [dotnet run](dotnet-run.md)         | Uruchamia aplikację ze źródła.                                   |
| [dotnet sln](dotnet-sln.md)         | Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.       |
| [dotnet store](dotnet-store.md)     | Przechowuje zestawy w magazynie pakietów środowiska uruchomieniowego.                     |
| [dotnet test](dotnet-test.md)       | Uruchamia testy przy użyciu modułu uruchamiającego testy.                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

| Polecenie                             | Funkcja                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Kompiluje aplikację platformy .NET Core.                                     |
| [dotnet clean](dotnet-clean.md)     | Czyste dane wyjściowe kompilacji.                                              |
| [dotnet migrate](dotnet-migrate.md) | Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.  |
| [dotnet msbuild](dotnet-msbuild.md) | Zapewnia dostęp do wiersza polecenia programu MSBuild.                        |
| [dotnet new](dotnet-new.md)         | Inicjuje projekt C# lub F# dla danego szablonu.                |
| [dotnet pack](dotnet-pack.md)       | Tworzy pakiet NuGet kodu.                               |
| [dotnet publish](dotnet-publish.md) | Publikuje zależne od programu .NET Framework lub samodzielną aplikację. |
| [dotnet restore](dotnet-restore.md) | Przywraca zależności dla danej aplikacji.                  |
| [dotnet run](dotnet-run.md)         | Uruchamia aplikację ze źródła.                                   |
| [dotnet sln](dotnet-sln.md)         | Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.       |
| [dotnet test](dotnet-test.md)       | Uruchamia testy przy użyciu modułu uruchamiającego testy.                                     |

---

### <a name="project-references"></a>Odwołania projektu

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
[dotnet nuget delete](dotnet-nuget-delete.md) | Usuwa pakiet z serwera lub go wystawia.
[dotnet nuget locals](dotnet-nuget-locals.md) | Czyści lub wyświetla lokalne zasoby NuGet, takie jak pamięć podręczna żądań HTTP, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.
[dotnet nuget push](dotnet-nuget-push.md) | Wypchnij pakiet na serwer i opublikuje go.

### <a name="global-tools-commands"></a>Polecenia narzędzi globalnych

[Narzędzia globalne platformy .NET Core](global-tools.md) są dostępne począwszy od zestaw .NET Core SDK 2.1.300:

Polecenie | Funkcja
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Instaluje narzędzie globalne na komputerze.
[dotnet tool list](dotnet-tool-list.md) | Wyświetla listę wszystkich narzędzi globalnych aktualnie zainstalowanych w domyślnym katalogu na komputerze lub w określonej ścieżce.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Odinstalowuje narzędzie globalne z komputera.
[dotnet tool update](dotnet-tool-update.md) | Aktualizuje narzędzie globalne na komputerze.

### <a name="additional-tools"></a>Dodatkowe narzędzia

Począwszy od zestaw .NET Core SDK 2.1.300, wiele narzędzi, które były dostępne tylko dla każdego projektu, przy użyciu `DotnetCliToolReference` , jest teraz dostępne jako część zestaw .NET Core SDK. Te narzędzia są wymienione w poniższej tabeli:

| Narzędzie                                              | Funkcja                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | Tworzy i zarządza certyfikatami deweloperskimi.                |
| [bieżąco](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core narzędzia wiersza polecenia.                    |
| SQL-pamięć podręczna                                         | SQL Server narzędzia wiersza polecenia pamięci podręcznej.                         |
| [wpisy tajne użytkownika](/aspnet/core/security/app-secrets) | Zarządza kluczami tajnymi użytkowników deweloperskich.                            |
| [Obejrzyj](/aspnet/core/tutorials/dotnet-watch)      | Uruchamia obserwatora plików, który uruchamia polecenie, gdy pliki zmienią się. |

Aby uzyskać więcej informacji na temat każdego narzędzia `dotnet <tool-name> --help`, wpisz.

## <a name="examples"></a>Przykłady

Tworzy nową aplikację konsolową platformy .NET Core:

`dotnet new console`

Przywróć zależności dla danej aplikacji:

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Kompiluj projekt i jego zależności w danym katalogu:

`dotnet build`

Uruchom bibliotekę DLL aplikacji, na `myapp.dll`przykład:

`dotnet myapp.dll`

## <a name="environment-variables"></a>Zmienne środowiskowe

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`DOTNET_PACKAGES`

Folder pakiety globalne. Jeśli nie jest ustawiona, zostanie ona `~/.nuget/packages` domyślnie włączona w `%userprofile%\.nuget\packages` systemie UNIX lub w systemie Windows.

`DOTNET_SERVICING`

Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft. Ustaw, `true` aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptować). W przeciwnym razie ustaw `false` opcję, aby można było wybrać funkcje telemetrii ( `no` wartości `false`, `0`lub zaakceptowane). Jeśli nie zostanie ustawiona, wartość domyślna `false` to i aktywna funkcja telemetrii.

`DOTNET_MULTILEVEL_LOOKUP`

Określa, czy środowisko uruchomieniowe programu .NET Core, udostępnione środowisko lub zestaw SDK są rozpoznawane z lokalizacji globalnej. Jeśli nie zostanie ustawiona, domyślnie `true`jest to. Ustawiona na `false` wartość nie jest rozpoznawana z lokalizacji globalnej i ma wyizolowane instalacje .NET `0` Core `false` (wartości lub są akceptowane). Aby uzyskać więcej informacji o wyszukiwaniu wielu poziomów, zobacz [SharedFX wyszukiwanie na wielu poziomach](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

Wyłącza dodatkową wersję do przodu, jeśli jest ustawiona `0`na. Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`DOTNET_PACKAGES`

Podstawowa pamięć podręczna pakietu. Jeśli nie jest ustawiona, zostanie ona `$HOME/.nuget/packages` domyślnie włączona w `%userprofile%\.nuget\packages` systemie UNIX lub w systemie Windows.

`DOTNET_SERVICING`

Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft. Ustaw, `true` aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptować). W przeciwnym razie ustaw `false` opcję, aby można było wybrać funkcje telemetrii ( `no` wartości `false`, `0`lub zaakceptowane). Jeśli nie zostanie ustawiona, wartość domyślna `false` to i aktywna funkcja telemetrii.

`DOTNET_MULTILEVEL_LOOKUP`

Określa, czy środowisko uruchomieniowe programu .NET Core, udostępnione środowisko lub zestaw SDK są rozpoznawane z lokalizacji globalnej. Jeśli nie zostanie ustawiona, domyślnie `true`jest to. Ustawiona na `false` wartość nie jest rozpoznawana z lokalizacji globalnej i ma wyizolowane instalacje .NET `0` Core `false` (wartości lub są akceptowane). Aby uzyskać więcej informacji o wyszukiwaniu wielu poziomów, zobacz [SharedFX wyszukiwanie na wielu poziomach](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`DOTNET_PACKAGES`

Podstawowa pamięć podręczna pakietu. Jeśli nie jest ustawiona, zostanie ona `$HOME/.nuget/packages` domyślnie włączona w `%userprofile%\.nuget\packages` systemie UNIX lub w systemie Windows.

`DOTNET_SERVICING`

Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft. Ustaw, `true` aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptować). W przeciwnym razie ustaw `false` opcję, aby można było wybrać funkcje telemetrii ( `no` wartości `false`, `0`lub zaakceptowane). Jeśli nie zostanie ustawiona, wartość domyślna `false` to i aktywna funkcja telemetrii.

---

## <a name="see-also"></a>Zobacz także

- [Pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
