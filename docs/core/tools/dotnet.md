---
title: dotnet, polecenie
description: Dowiedz się więcej o poleceniu dotnet (ogólnym sterowniku interfejsu wiersza polecenia .NET Core) i jego użyciu.
ms.date: 02/13/2020
ms.openlocfilehash: 6a08297499d955db44e342dc82fed25b7b9b8171
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739080"
---
# <a name="dotnet-command"></a>dotnet, polecenie

**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet`- Ogólny sterownik dla interfejsu wiersza polecenia .NET Core.

## <a name="synopsis"></a>Streszczenie

Aby uzyskać informacje o dostępnych poleceniach i środowisku:

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

Aby uruchomić polecenie (wymaga instalacji SDK):

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

Aby uruchomić aplikację:

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

`--roll-forward`jest dostępna od platformy .NET Core 3.x. Użyj `--roll-forward-on-no-candidate-fx` dla .NET Core 2.x.

## <a name="description"></a>Opis

Polecenie `dotnet` ma dwie funkcje:

- Zapewnia polecenia do pracy z projektami .NET Core.

  Na przykład [`dotnet build`](dotnet-build.md) tworzy projekt. Każde polecenie definiuje własne opcje i argumenty. Wszystkie polecenia obsługują `--help` opcję drukowania krótkiej dokumentacji dotyczącej sposobu korzystania z polecenia.

- Uruchamia aplikacje .NET Core.

  Można określić ścieżkę `.dll` do pliku aplikacji, aby uruchomić aplikację.  Aby uruchomić aplikację oznacza, aby znaleźć i wykonać punkt wejścia, `Main` który w przypadku aplikacji konsoli jest metodą. Na przykład `dotnet myapp.dll` uruchamia `myapp` aplikację. Zobacz [wdrożenie aplikacji .NET Core,](../deploying/index.md) aby dowiedzieć się więcej o opcjach wdrażania.

## <a name="options"></a>Opcje

Różne opcje są `dotnet` dostępne dla siebie, do uruchamiania polecenia i uruchamiania aplikacji.

### <a name="options-for-dotnet-by-itself"></a>Opcje dla dotnet sam

Następujące opcje są `dotnet` dla siebie. Na przykład `dotnet --info`. Drukują informacje o środowisku.

- **`--info`**

  Drukuje szczegółowe informacje o instalacji .NET Core i środowisku komputera, takich jak bieżący system operacyjny, i zatwierdza sha wersji .NET Core.

- **`--version`**

  Drukuje używany plik.

- **`--list-runtimes`**

  Drukuje listę zainstalowanych runtimes .NET Core. Wersja x86 SDK zawiera tylko środowiska wykonawcze x86, a wersja x64 SDK wyświetla tylko środowiska wykonawcze x64.

- **`--list-sdks`**

  Drukuje listę zainstalowanych pakietów SDK .NET Core.

- **`-h|--help`**

  Drukuje listę dostępnych poleceń.

### <a name="sdk-options-for-running-a-command"></a>Opcje SDK do uruchamiania polecenia

Następujące opcje są `dotnet` dla z polecenia. Na przykład `dotnet build --help`.

- **`-d|--diagnostics`**

  Umożliwia wyjście diagnostyczne.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i . Nie jest obsługiwany w każdym poleceniu. Zobacz określoną stronę polecenia, aby ustalić, czy ta opcja jest dostępna.

- **`-h|--help`**

  Drukuje dokumentację dla danego polecenia, na przykład `dotnet build --help`.

- **`command options`**

  Każde polecenie definiuje opcje specyficzne dla tego polecenia. Zobacz stronę poleceń, aby uzyskać listę dostępnych opcji.

### <a name="runtime-options"></a>Opcje środowiska wykonawczego

Następujące opcje są `dotnet` dostępne podczas uruchamiania aplikacji. Na przykład `dotnet myapp.dll --fx-version 3.1.1`.

- **`--additionalprobingpath <PATH>`**

  Ścieżka zawierająca zasady sondowania i zestawy do sondowania.

- **`--additional-deps <PATH>`**

  Ścieżka do dodatkowego pliku *deps.json.* Plik *deps.json* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawu. Aby uzyskać więcej informacji, zobacz [Pliki konfiguracji środowiska wykonawczego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) w usłudze GitHub.

- **`--fx-version <VERSION>`**

  Wersja środowiska uruchomieniowego .NET Core do uruchomienia aplikacji.

- **`--runtimeconfig`**

  Ścieżka do pliku *runtimeconfig.json.* Plik *runtimeconfig.json* jest plikiem konfiguracyjnym zawierającym ustawienia czasu wykonywania. Aby uzyskać więcej informacji, zobacz [.NET Core ustawienia konfiguracji w czasie wykonywania](../run-time-config/index.md#runtimeconfigjson).

- **`--roll-forward-on-no-candidate-fx <N>`****Dostępne w pliku .NET Core 2.x SDK.**

  Definiuje zachowanie, gdy wymagana współużytkowana struktura nie jest dostępna. `N`może to być:

  - `0`- Wyłącz nawet wersję pomocniczą rolki do przodu.
  - `1`- Roll forward w wersji pomocniczej, ale nie w wersji głównej. Jest to zachowanie domyślne.
  - `2`- Roll forward w wersji pomocniczej i głównej.

   Aby uzyskać więcej informacji, zobacz [Przewij do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).

- **`--roll-forward <SETTING>`****Dostępne począwszy od .NET Core SDK 3.0.**

  Określa sposób przekazywania do przodu jest stosowany do aplikacji. `SETTING` Może to być jedna z następujących wartości. Jeśli nie `Minor` zostanie określony, jest wartością domyślną.

  - `LatestPatch`- Przewiń do przodu do najwyższej wersji poprawki. Spowoduje to wyłączenie wersji pomocniczej do przodu.
  - `Minor`- Przewiń do przodu do najniższej wyższej wersji pomocniczej, jeśli brakuje żądanej wersji pomocniczej. Jeśli żądana wersja pomocnicza jest obecna, używana jest zasada LatestPatch.
  - `Major`- Przewiń do przodu do najniższej wyższej wersji głównej i najniższej wersji pomocniczej, jeśli brakuje żądanej wersji głównej. Jeśli żądana wersja główna jest obecny, a następnie drobne zasady są używane.
  - `LatestMinor`- Przewiń do przodu do najwyższej wersji pomocniczej, nawet jeśli wymagana wersja pomocnicza jest obecna. Przeznaczone do scenariuszy hostingu składników.
  - `LatestMajor`- Roll forward do najwyższej wersji głównej i najwyższej wersji pomocniczej, nawet jeśli wymagane major jest obecny. Przeznaczone do scenariuszy hostingu składników.
  - `Disable`- Nie tocz do przodu. Tylko powiązanie z określoną wersją. Ta zasada nie jest zalecana do ogólnego użytku, ponieważ wyłącza możliwość przekazywania do najnowszych poprawek. Ta wartość jest zalecana tylko do testowania.

Z wyjątkiem `Disable`, wszystkie ustawienia będą korzystać z najwyższej dostępnej wersji poprawki.

Zachowanie przewijania do przodu można również skonfigurować we właściwości pliku projektu, właściwości pliku konfiguracji w czasie wykonywania i zmiennej środowiskowej. Aby uzyskać więcej informacji, zobacz [Główne wersje runtime roll do przodu](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).

## <a name="dotnet-commands"></a>Polecenia dotnet

### <a name="general"></a>Ogólne

| Polecenie                                       | Funkcja                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | Tworzy aplikację .NET Core.                                     |
| [dotnet build-server](dotnet-build-server.md) | Współdziała z serwerami uruchomionymi przez kompilację.                          |
| [dotnet clean](dotnet-clean.md)               | Czyste wyjścia kompilacji.                                                |
| [dotnet help](dotnet-help.md)                 | Pokazuje bardziej szczegółową dokumentację dla polecenia.           |
| [dotnet migrate](dotnet-migrate.md)           | Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu .NET Core SDK 1.0.  |
| [dotnet msbuild](dotnet-msbuild.md)           | Zapewnia dostęp do wiersza polecenia MSBuild.                        |
| [dotnet new](dotnet-new.md)                   | Inicjuje projekt C# lub F# dla danego szablonu.                |
| [dotnet pack](dotnet-pack.md)                 | Tworzy pakiet NuGet kodu.                               |
| [dotnet publish](dotnet-publish.md)           | Publikuje aplikację zależną od struktury .NET lub niezależną. |
| [dotnet restore](dotnet-restore.md)           | Przywraca zależności dla danej aplikacji.                  |
| [dotnet run](dotnet-run.md)                   | Uruchamia aplikację ze źródła.                                   |
| [dotnet sln](dotnet-sln.md)                   | Opcje dodawania, usuwania i listy projektów w pliku rozwiązania.       |
| [dotnet store](dotnet-store.md)               | Przechowuje zestawy w magazynie pakietów środowiska wykonawczego.                     |
| [dotnet test](dotnet-test.md)                 | Uruchamia testy przy użyciu testowej próby.                                     |

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
[dotnet nuget delete](dotnet-nuget-delete.md) | Usuwa lub usuwa listę pakiet z serwera.
[dotnet nuget push](dotnet-nuget-push.md) | Wypycha pakiet do serwera i publikuje go.
[dotnet nuget locals](dotnet-nuget-locals.md) | Czyści lub wyświetla lokalne zasoby NuGet, takie jak pamięć podręczna żądań http, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całej maszyny.
[dotnet nuget add source](dotnet-nuget-add-source.md) | Dodaje źródło NuGet.
[dotnet nuget disable source](dotnet-nuget-disable-source.md) | Wyłącza źródło NuGet.
[dotnet nuget enable source](dotnet-nuget-enable-source.md) | Włącza źródło NuGet.
[dotnet nuget list source](dotnet-nuget-list-source.md) | Wyświetla listę wszystkich skonfigurowanych źródeł NuGet.
[dotnet nuget remove source](dotnet-nuget-remove-source.md) | Usuwa źródło NuGet.
[dotnet nuget update source](dotnet-nuget-update-source.md) | Aktualizuje źródło NuGet.

### <a name="global-tool-path-and-local-tools-commands"></a>Polecenia narzędzi globalnych, ścieżki narzędzi i narzędzi lokalnych

Narzędzia są aplikacje konsoli, które są instalowane z pakietów NuGet i są wywoływane z wiersza polecenia. Możesz samodzielnie napisać narzędzia lub zainstalować narzędzia napisane przez osoby trzecie. Narzędzia są również nazywane narzędziami globalnymi, narzędziami ścieżki narzędzi i narzędziami lokalnymi. Aby uzyskać więcej informacji, zobacz [omówienie narzędzi .NET Core](global-tools.md). Globalne i narzędzia ścieżki narzędzi są dostępne począwszy od .NET Core SDK 2.1. Narzędzia lokalne są dostępne począwszy od .NET Core SDK 3.0.

Polecenie | Funkcja
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Instaluje narzędzie na komputerze.
[dotnet tool list](dotnet-tool-list.md) | Wyświetla listę wszystkich narzędzi globalnych, ścieżki narzędzi lub narzędzi lokalnych aktualnie zainstalowanych na komputerze.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Odinstalowuje narzędzie z komputera.
[dotnet tool update](dotnet-tool-update.md) | Aktualizuje narzędzie zainstalowane na komputerze.

### <a name="additional-tools"></a>Dodatkowe narzędzia

Począwszy od zestawu .NET Core SDK 2.1.300, wiele narzędzi, `DotnetCliToolReference` które były dostępne tylko na podstawie projektu, są teraz dostępne jako część zestawu .NET Core SDK. Narzędzia te są wymienione w poniższej tabeli:

| Narzędzie                                              | Funkcja                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | Tworzy certyfikaty deweloperów i zarządza nimi.                |
| [Ef](/ef/core/miscellaneous/cli/dotnet)           | Narzędzia wiersza polecenia Core entity framework.                    |
| sql-cache                                         | Narzędzia wiersza polecenia pamięci podręcznej programu SQL Server.                         |
| [tajemnice użytkownika](/aspnet/core/security/app-secrets) | Zarządza wpisami tajnymi użytkowników deweloperów.                            |
| [Oglądać](/aspnet/core/tutorials/dotnet-watch)      | Uruchamia obserwatora plików, który uruchamia polecenie po zmianie plików. |

Aby uzyskać więcej informacji `dotnet <tool-name> --help`o każdym narzędziu, wpisz .

## <a name="examples"></a>Przykłady

Utwórz nową aplikację konsoli .NET Core:

```dotnetcli
dotnet new console
```

Tworzenie projektu i jego zależności w danym katalogu:

```dotnetcli
dotnet build
```

Uruchamianie aplikacji:

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a>Zmienne środowiskowe

- `DOTNET_ROOT`, `DOTNET_ROOT(x86)`

  Określa lokalizację środowiska uruchomień .NET Core, jeśli nie są zainstalowane w lokalizacji domyślnej. Domyślną lokalizacją `C:\Program Files\dotnet`w systemie Windows jest . Domyślną lokalizacją w systemach Linux i macOS jest `/usr/share/dotnet`. Ta zmienna środowiskowa jest używana tylko podczas uruchamiania aplikacji za pośrednictwem wygenerowanych plików wykonywalnych (apphosts). `DOTNET_ROOT(x86)`jest używany podczas uruchamiania 32-bitowego pliku wykonywalnego na 64-bitowym os.

- `DOTNET_PACKAGES`

  Folder pakietów globalnych. Jeśli nie jest ustawiona, domyślnie jest to `~/.nuget/packages` w systemie Unix lub `%userprofile%\.nuget\packages` Windows.

- `DOTNET_SERVICING`

  Określa lokalizację indeksu obsługi do użycia przez hosta udostępnionego podczas ładowania środowiska wykonawczego.

- `DOTNET_NOLOGO`

  Określa, czy komunikaty powitalne .NET Core i telemetryczne są wyświetlane przy pierwszym uruchomieniu. Ustaw, `true` aby wyciszyć `true`te `1`komunikaty `yes` (wartości , `false` lub zaakceptowane) lub ustawić, aby zezwolić (wartości `false`, `0`, lub `no` akceptowane). Jeśli nie jest ustawiona, domyślna jest `false` i komunikaty będą wyświetlane przy pierwszym uruchomieniu. Ta flaga nie ma wpływu `DOTNET_CLI_TELEMETRY_OPTOUT` na dane telemetryczne (zobacz rezygnacji z wysyłania danych telemetrycznych).

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft. Ustaw `true` opcję rezygnacji z funkcji telemetrii (wartości `true`lub `1` `yes` zaakceptowane). W przeciwnym `false` razie należy ustawić opcję wyboru `false` `0`funkcji `no` telemetrycznych (wartości lub zaakceptowanych). Jeśli nie jest ustawiona, ustawieniem domyślnym jest `false` funkcja telemetrii.

- `DOTNET_MULTILEVEL_LOOKUP`

  Określa, czy środowisko uruchomieniowe .NET Core, współużytkowana struktura lub SDK są rozpoznawane z lokalizacji globalnej. Jeśli nie jest ustawiona, domyślnie `true`jest to 1 (logiczne ). Ustaw wartość 0 `false`(logiczna), aby nie rozwiązać problemu z lokalizacji globalnej i mieć izolowane instalacje .NET Core. Aby uzyskać więcej informacji na temat wyszukiwania wielopoziomowego, zobacz [Wielopoziomowe wyszukiwanie SharedFX](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

- `DOTNET_ROLL_FORWARD`**Dostępne począwszy od .NET Core 3.x SDK.**

  Określa zachowanie przewijania do przodu. Aby uzyskać więcej `--roll-forward` informacji, zobacz opcję wcześniej w tym artykule.

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Dostępne w pliku .NET Core 2.x SDK.**

  Wyłącza wersję pomocniczą do `0`przodu, jeśli jest ustawiona na . Aby uzyskać więcej informacji, zobacz [Przewij do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).

- `DOTNET_CLI_UI_LANGUAGE`

  Ustawia język interfejsu użytkownika interfejsu wiersza polecenia `en-us`przy użyciu wartości ustawień regionalnych, takich jak . Obsługiwane wartości są takie same jak w programie Visual Studio. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą zmieniania języka instalatora w [dokumentacji instalacji programu Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019). Zasady Menedżera zasobów .NET mają zastosowanie, więc nie trzeba&mdash;wybierać dopasowania dokładnego, które można również wybrać elementy podrzędne w `CultureInfo` drzewie. Na przykład, jeśli ustawisz go na `fr-CA`, `fr` CLI znajdzie i użyje tłumaczeń. Jeśli ustawisz go na język, który nie jest obsługiwany, cli powróci do języka angielskiego.

- `DOTNET_DISABLE_GUI_ERRORS`

  W przypadku generowanych plików wykonywalnych z funkcją GUI — wyłącza okno dialogowe, które zwykle jest wyświetlane dla niektórych klas błędów. To tylko zapisuje `stderr` i kończy się w tych przypadkach.
  
- `DOTNET_ADDITIONAL_DEPS`

  Odpowiednik opcji `--additional-deps`interfejsu wiersza polecenia .

- `DOTNET_RUNTIME_ID`

  Zastępuje wykryty identyfikator RID.

- `DOTNET_SHARED_STORE`

  Lokalizacja "magazynu udostępnionego", do którego rozdzielczość zestawu powraca w niektórych przypadkach.

- `DOTNET_STARTUP_HOOKS`

  Lista zestawów do załadowania i wykonania haków startowych.

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  Steruje śledzeniem diagnostyki ze składników `dotnet.exe` `hostfxr`hostingu, takich jak , i `hostpolicy`.

## <a name="see-also"></a>Zobacz też

- [Pliki konfiguracji środowiska wykonawczego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [Ustawienia konfiguracji w czasie wykonywania rdzenia .NET](../run-time-config/index.md)
