---
title: polecenie dotnet
description: Dowiedz się więcej o komendzie dotnet (sterownik ogólny dla wiersza wiersza polecenia .NET Core) i jego użyciu.
ms.date: 02/13/2020
ms.openlocfilehash: da37c5cc3b019851e245fa3f65ae9dfb8a3fef54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398896"
---
# <a name="dotnet-command"></a>polecenie dotnet

**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet`- Ogólny sterownik dla .NET Core CLI.

## <a name="synopsis"></a>Streszczenie

Aby uzyskać informacje o dostępnych poleceniach i środowisku:

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

Aby uruchomić polecenie (wymaga instalacji zestawu SDK):

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

Aby uruchomić aplikację:

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

`--roll-forward`jest dostępna od .NET Core 3.x. Użyj `--roll-forward-on-no-candidate-fx` dla .NET Core 2.x.

## <a name="description"></a>Opis

Polecenie `dotnet` ma dwie funkcje:

- Zawiera polecenia do pracy z projektami .NET Core.

  Na przykład [`dotnet build`](dotnet-build.md) tworzy projekt. Każde polecenie definiuje własne opcje i argumenty. Wszystkie polecenia obsługują `--help` opcję drukowania krótkiej dokumentacji dotyczącej używania polecenia.

- Uruchamia aplikacje .NET Core.

  Należy określić ścieżkę `.dll` do pliku aplikacji, aby uruchomić aplikację. Na przykład `dotnet myapp.dll` uruchamia `myapp` aplikację. Zobacz [.NET Core wdrożenia aplikacji,](../deploying/index.md) aby dowiedzieć się więcej o opcjach wdrażania.

## <a name="options"></a>Opcje

Różne opcje są `dotnet` dostępne dla siebie, do uruchamiania polecenia i uruchamiania aplikacji.

### <a name="options-for-dotnet-by-itself"></a>Opcje dotnet usiebie

Następujące opcje są `dotnet` same w sobie. Na przykład `dotnet --info`. Drukują informacje o środowisku.

- **`--info`**

  Drukuje szczegółowe informacje o instalacji .NET Core i środowisku komputera, takie jak bieżący system operacyjny, i zatwierdza sha wersji .NET Core.

- **`--version`**

  Drukuje używana wersja programu .NET Core SDK.

- **`--list-runtimes`**

  Drukuje listę zainstalowanych uruchomień programu .NET Core.

- **`--list-sdks`**

  Drukuje listę zainstalowanych zestawów SDK .NET Core.

- **`-h|--help`**

  Drukuje listę dostępnych poleceń.

### <a name="sdk-options-for-running-a-command"></a>Opcje sdk uruchamiania polecenia

Następujące opcje są `dotnet` dla z poleceniem. Na przykład `dotnet build --help`.

- **`-d|--diagnostics`**

  Umożliwia wyjście diagnostyczne.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i . Nie jest obsługiwany w każdym poleceniu. Zobacz określoną stronę polecenia, aby ustalić, czy ta opcja jest dostępna.

- **`-h|--help`**

  Drukuje dokumentację dla danego polecenia, na przykład `dotnet build --help`.

- **`command options`**

  Każde polecenie definiuje opcje specyficzne dla tego polecenia. Zobacz konkretną stronę polecenia, aby uzyskać listę dostępnych opcji.

### <a name="runtime-options"></a>Opcje czasu wykonywania

Następujące opcje są `dotnet` dostępne po uruchomieniu aplikacji. Na przykład `dotnet myapp.dll --fx-version 3.1.1`.

- **`--additionalprobingpath <PATH>`**

  Ścieżka zawierająca zasady sondowania i zestawy do sondowania.

- **`--additional-deps <PATH>`**

  Ścieżka do dodatkowego pliku *.deps.json.* Plik *deps.json* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów. Aby uzyskać więcej informacji, zobacz [Pliki konfiguracyjne w czasie wykonywania](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) w usteercie GitHub.

- **`--fx-version <VERSION>`**

  Wersja programu runtime .NET Core do użycia do uruchamiania aplikacji.

- **`--runtimeconfig`**

  Ścieżka do pliku *runtimeconfig.json.* Plik *runtimeconfig.json* to plik konfiguracyjny zawierający ustawienia czasu wykonywania. Aby uzyskać więcej informacji, zobacz [ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).

- **`--roll-forward-on-no-candidate-fx <N>`****Dostępne w sdk .NET Core 2.x.**

  Definiuje zachowanie, gdy wymagana struktura współużytkowana nie jest dostępna. `N`może być:

  - `0`- Wyłącz nawet drobne wersji roll do przodu.
  - `1`- Przewiń do przodu na wersji pomocniczej, ale nie w wersji głównej. Jest to zachowanie domyślne.
  - `2`- Przewiń do przodu na mniejszych i głównych wersjach.

   Aby uzyskać więcej informacji, zobacz [Przewijanie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).

- **`--roll-forward <SETTING>`****Dostępne od .NET Core SDK 3.0.**

  Określa sposób stosowania rolowania do przodu aplikacji. Może `SETTING` być jedną z następujących wartości. Jeśli nie zostanie `Minor` określony, jest ustawieniem domyślnym.

  - `LatestPatch`- Przewiń do przodu do najwyższej wersji poprawki. Spowoduje to wyłączenie pomocniczej wersji przewijania do przodu.
  - `Minor`- Przewiń do przodu do najniższej wyższej wersji pomocniczej, jeśli brakuje żądanej wersji pomocniczej. Jeśli występuje żądana wersja pomocnicza, używana jest zasada LatestPatch.
  - `Major`- Przewiń do przodu do najniższej wyższej wersji głównej i najniższej wersji pomocniczej, jeśli nie ma żądanej wersji głównej. Jeśli występuje żądana wersja główna, używana jest zasada pomocnicza.
  - `LatestMinor`- Przewiń do najwyższej wersji pomocniczej, nawet jeśli wymagana wersja pomocnicza jest obecna. Przeznaczone dla scenariuszy hostingu składników.
  - `LatestMajor`- Przewiń do najwyższej wersji głównej i najwyższej wersji pomocniczej, nawet jeśli wymagane jest poważne. Przeznaczone dla scenariuszy hostingu składników.
  - `Disable`- Nie przewracaj się do przodu. Powiąż tylko określoną wersję. Ta zasada nie jest zalecane do ogólnego użytku, ponieważ wyłącza możliwość przewijania do przodu do najnowszych poprawek. Ta wartość jest zalecana tylko do testowania.

Z wyjątkiem `Disable`, wszystkie ustawienia będą korzystać z najwyższej dostępnej wersji poprawki.

Zachowanie do przodu można również skonfigurować we właściwości pliku projektu, właściwości pliku konfiguracyjnego w czasie wykonywania i zmiennej środowiskowej. Aby uzyskać więcej informacji, zobacz [Główne wersje uruchomieniowej do przodu](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).

## <a name="dotnet-commands"></a>Polecenia dotnet

### <a name="general"></a>Ogólne

| Polecenie                                       | Funkcja                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | Tworzy aplikację .NET Core.                                     |
| [dotnet build-server](dotnet-build-server.md) | Współdziała z serwerami uruchomionymi przez kompilację.                          |
| [dotnet clean](dotnet-clean.md)               | Czyste wyjścia kompilacji.                                                |
| [dotnet help](dotnet-help.md)                 | Pokazuje bardziej szczegółową dokumentację w trybie online dla polecenia.           |
| [dotnet migrate](dotnet-migrate.md)           | Migracja prawidłowego projektu podglądu 2 do projektu .NET Core SDK 1.0.  |
| [dotnet msbuild](dotnet-msbuild.md)           | Zapewnia dostęp do wiersza polecenia MSBuild.                        |
| [dotnet new](dotnet-new.md)                   | Inicjuje projekt języka C# lub F# dla danego szablonu.                |
| [dotnet pack](dotnet-pack.md)                 | Tworzy pakiet NuGet kodu.                               |
| [dotnet publish](dotnet-publish.md)           | Publikuje aplikację zależną od platformy .NET lub niezależną. |
| [dotnet restore](dotnet-restore.md)           | Przywraca zależności dla danej aplikacji.                  |
| [dotnet run](dotnet-run.md)                   | Uruchamia aplikację ze źródła.                                   |
| [dotnet sln](dotnet-sln.md)                   | Opcje dodawania, usuwania i wystawiania projektów w pliku rozwiązania.       |
| [dotnet store](dotnet-store.md)               | Przechowuje zestawy w magazynie pakietów w czasie wykonywania.                     |
| [dotnet test](dotnet-test.md)                 | Uruchamia testy przy użyciu biegacza testowego.                                     |

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
[dotnet nuget delete](dotnet-nuget-delete.md) | Usuwa lub usuwa listę pakietu z serwera.
[dotnet nuget locals](dotnet-nuget-locals.md) | Czyści lub wyświetla listę lokalnych zasobów NuGet, takich jak pamięć podręczna żądań http, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.
[dotnet nuget push](dotnet-nuget-push.md) | Wypycha pakiet do serwera i publikuje go.

### <a name="global-tool-path-and-local-tools-commands"></a>Polecenia narzędzia globalnego, ścieżki narzędzia i narzędzia lokalne

Narzędzia są aplikacje konsoli, które są instalowane z pakietów NuGet i są wywoływane z wiersza polecenia. Możesz samodzielnie pisać narzędzia lub instalować narzędzia napisane przez osoby trzecie. Narzędzia są również znane jako narzędzia globalne, narzędzia ścieżki narzędziowej i narzędzia lokalne. Aby uzyskać więcej informacji, zobacz [omówienie narzędzi .NET Core](global-tools.md). Globalne i narzędzia ścieżki są dostępne począwszy od .NET Core SDK 2.1. Lokalne narzędzia są dostępne począwszy od .NET Core SDK 3.0.

Polecenie | Funkcja
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Instaluje narzędzie na komputerze.
[dotnet tool list](dotnet-tool-list.md) | Wyświetla listę wszystkich narzędzi globalnych, ścieżki narzędziowej lub lokalnych aktualnie zainstalowanych na komputerze.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Odinstalowuje narzędzie z komputera.
[dotnet tool update](dotnet-tool-update.md) | Aktualizuje narzędzie zainstalowane na komputerze.

### <a name="additional-tools"></a>Dodatkowe narzędzia

Począwszy od .NET Core SDK 2.1.300, liczba narzędzi, które `DotnetCliToolReference` były dostępne tylko na podstawie projektu przy użyciu są teraz dostępne jako część .NET Core SDK. Narzędzia te są wymienione w poniższej tabeli:

| Narzędzie                                              | Funkcja                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | Tworzy certyfikaty deweloperów i zarządza nimi.                |
| [Ef](/ef/core/miscellaneous/cli/dotnet)           | Narzędzia wiersza polecenia Entity Framework Core.                    |
| sql-cache                                         | Narzędzia wiersza polecenia pamięci podręcznej programu SQL Server.                         |
| [tajemnice użytkownika](/aspnet/core/security/app-secrets) | Zarządza wtajemnicami użytkowników deweloperskich.                            |
| [Oglądać](/aspnet/core/tutorials/dotnet-watch)      | Uruchamia obserwatora plików, który uruchamia polecenie po zmianie plików. |

Aby uzyskać więcej informacji `dotnet <tool-name> --help`na temat każdego narzędzia, wpisz .

## <a name="examples"></a>Przykłady

Utwórz nową aplikację konsoli .NET Core:

```dotnetcli
dotnet new console
```

Tworzenie projektu i jego zależności w danym katalogu:

```dotnetcli
dotnet build
```

Uruchom aplikację:

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a>Zmienne środowiskowe

- `DOTNET_ROOT`, `DOTNET_ROOT(x86)`

  Określa lokalizację runii programu .NET Core, jeśli nie są one zainstalowane w lokalizacji domyślnej. Domyślną lokalizacją `C:\Program Files\dotnet`w systemie Windows jest . Domyślną lokalizacją w systemach `/usr/share/dotnet`Linux i macOS jest . Ta zmienna środowiskowa jest używana tylko podczas uruchamiania aplikacji za pośrednictwem wygenerowanych plików wykonywalnych (hostów aplikacji). `DOTNET_ROOT(x86)`jest używany zamiast tego podczas uruchamiania 32-bitowego pliku wykonywalnego w 64-bitowym os.

- `DOTNET_PACKAGES`

  Folder pakietów globalnych. Jeśli nie jest ustawiona, `~/.nuget/packages` domyślnie `%userprofile%\.nuget\packages` w systemie Unix lub w systemie Windows.

- `DOTNET_SERVICING`

  Określa lokalizację indeksu obsługi, który ma być używany przez hosta udostępnionego podczas ładowania czasu wykonywania.

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  Określa, czy dane dotyczące użycia narzędzi programu .NET Core są zbierane i wysyłane do firmy Microsoft. Ustaw, `true` aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptowane). W przeciwnym `false` razie ustaw, aby zdecydować `false` `0`się `no` na funkcje telemetrii (wartości , lub zaakceptowane). Jeśli nie jest ustawiona, domyślnie jest `false` i funkcja telemetrii jest aktywny.

- `DOTNET_MULTILEVEL_LOOKUP`

  Określa, czy program .NET Core, framework udostępniony lub SDK są rozpoznawani z lokalizacji globalnej. Jeśli nie jest ustawiona, domyślnie `true`jest ustawiona na 1 (logiczna ). Ustaw wartość 0 `false`(logiczną), aby nie rozpoznawać z lokalizacji globalnej i mieć izolowane instalacje .NET Core. Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowego, zobacz [Wielopoziomowe wyszukiwania SharedFX](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

- `DOTNET_ROLL_FORWARD`**Dostępne od .NET Core 3.x SDK.**

  Określa zachowanie rzutdo przodu. Aby uzyskać więcej `--roll-forward` informacji, zobacz opcję wcześniej w tym artykule.

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Dostępne w sdk .NET Core 2.x.**

  Wyłącza pomocnicze juz rolki `0`wersji do przodu, jeśli jest ustawiona na . Aby uzyskać więcej informacji, zobacz [Przewijanie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).

- `DOTNET_CLI_UI_LANGUAGE`

  Sets the language of the CLI UI using a locale value such as `en-us`. Obsługiwane wartości są takie same jak w programie Visual Studio. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą zmiany języka instalatora w [dokumentacji instalacyjnej programu Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019). Reguły Menedżera zasobów .NET mają zastosowanie, więc nie trzeba&mdash;wybrać dokładne dopasowanie można `CultureInfo` również wybrać elementy podrzędne w drzewie. Na przykład, jeśli ustawisz go na `fr-CA`, `fr` CLI znajdzie i użyje tłumaczenia. Jeśli ustawisz go na język, który nie jest obsługiwany, cli wraca do języka angielskiego.

- `DOTNET_DISABLE_GUI_ERRORS`

  Dla pliku plików wykonywalnych generowanych przez gui - wyłącza okno podręczne okna dialogowego, które zwykle pokazuje dla niektórych klas błędów. W takich przypadkach `stderr` pisze tylko do i wychodzi.
  
- `DOTNET_ADDITIONAL_DEPS`

  Odpowiednik opcji `--additional-deps`CLI .

- `DOTNET_RUNTIME_ID`

  Zastępuje wykryty identyfikator RID.

- `DOTNET_SHARED_STORE`

  Lokalizacja "magazynu udostępnionego", do którego w niektórych przypadkach powraca rozdzielczość zestawu.

- `DOTNET_STARTUP_HOOKS`

  Lista zestawów do ładowania i wykonywania haków startowych z.

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  Steruje śledzeniem diagnostycznym ze `dotnet.exe`składników `hostfxr`hostingu, takich jak , , i `hostpolicy`.

## <a name="see-also"></a>Zobacz też

- [Pliki konfiguracyjne czasu wykonywania](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [Ustawienia konfiguracji środowiska .NET Core w czasie wykonywania](../run-time-config/index.md)
