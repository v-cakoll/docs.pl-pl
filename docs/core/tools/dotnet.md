---
title: dotnet — polecenie
description: Dowiedz się więcej na temat polecenia dotnet (sterownika generycznego dla interfejs wiersza polecenia platformy .NET Core) i jego użycia.
ms.date: 02/13/2020
ms.openlocfilehash: 88e92b3ff5e8f68b980015a817434dd2d67df93a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378841"
---
# <a name="dotnet-command"></a>dotnet — polecenie

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet`— Sterownik generyczny dla interfejs wiersza polecenia platformy .NET Core.

## <a name="synopsis"></a>Streszczenie

Aby uzyskać informacje na temat dostępnych poleceń i środowiska:

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

Aby uruchomić polecenie (wymaga instalacji zestawu SDK):

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

`--roll-forward`jest dostępny od wersji .NET Core 3. x. Używany `--roll-forward-on-no-candidate-fx` dla platformy .NET Core 2. x.

## <a name="description"></a>Opis

`dotnet`Polecenie ma dwie funkcje:

- Zawiera polecenia umożliwiające pracę z projektami .NET Core.

  Na przykład [`dotnet build`](dotnet-build.md) kompiluje projekt. Każde polecenie definiuje własne opcje i argumenty. Wszystkie polecenia obsługują `--help` opcję drukowania krótkiej dokumentacji dotyczącej sposobu korzystania z polecenia.

- Uruchamia aplikacje platformy .NET Core.

  Należy określić ścieżkę do pliku aplikacji, `.dll` Aby uruchomić aplikację.  Aby uruchomić aplikację, należy znaleźć i wykonać punkt wejścia, który w przypadku aplikacji konsolowych jest `Main` metodą. Na przykład `dotnet myapp.dll` uruchamia `myapp` aplikację. Zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) , aby dowiedzieć się więcej na temat opcji wdrażania.

## <a name="options"></a>Opcje

Różne opcje są dostępne dla `dotnet` siebie, na potrzeby uruchamiania polecenia i uruchamiania aplikacji.

### <a name="options-for-dotnet-by-itself"></a>Opcje dla dotnet

Poniższe opcje są odpowiednie dla `dotnet` siebie. Na przykład `dotnet --info`. Drukują informacje o środowisku.

- **`--info`**

  Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.

- **`--version`**

  Drukuje używaną wersję zestaw .NET Core SDK.

- **`--list-runtimes`**

  Drukuje listę zainstalowanych środowiska uruchomieniowego platformy .NET Core. Wersja x86 zestawu SDK zawiera tylko środowiska uruchomieniowe x86, a wersja x64 zestawu SDK zawiera tylko środowiska uruchomieniowe x64.

- **`--list-sdks`**

  Drukuje listę zainstalowanych zestawów SDK platformy .NET Core.

- **`-h|--help`**

  Drukuje listę dostępnych poleceń.

### <a name="sdk-options-for-running-a-command"></a>Opcje zestawu SDK do uruchamiania polecenia

Następujące opcje są przeznaczone dla `dotnet` polecenia. Na przykład `dotnet build --help`.

- **`-d|--diagnostics`**

  Włącza diagnostykę danych wyjściowych.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` . Nieobsługiwane w każdym poleceniu. Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.

- **`-h|--help`**

  Drukuje dokumentację dla danego polecenia, na przykład `dotnet build --help` .

- **`command options`**

  Każde polecenie definiuje opcje specyficzne dla tego polecenia. Listę dostępnych opcji można znaleźć na stronie z konkretnym poleceniem.

### <a name="runtime-options"></a>Opcje środowiska uruchomieniowego

Poniższe opcje są dostępne podczas `dotnet` uruchamiania aplikacji. Na przykład `dotnet myapp.dll --roll-forward Major`.

- **`--additionalprobingpath <PATH>`**

  Ścieżka zawierająca zasady i zestawy do sondowania.

- **`--additional-deps <PATH>`**

  Ścieżka do dodatkowego pliku *. deps. JSON* . Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) w serwisie GitHub.

- **`--depsfile <PATH_TO_DEPSFILE>`**

  Ścieżka do pliku *deps. JSON* . Plik *deps. JSON* to plik konfiguracji, który zawiera informacje o zależnościach niezbędnych do uruchomienia aplikacji. Ten plik jest generowany przez zestaw .NET Core SDK.

- **`--runtimeconfig`**

  Ścieżka do pliku *runtimeconfig. JSON* . Plik *runtimeconfig. JSON* to plik konfiguracji, który zawiera ustawienia czasu wykonywania. Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).

- **`--roll-forward <SETTING>`****Dostępne począwszy od zestaw .NET Core SDK 3,0.**

  Kontroluje sposób, w jaki do aplikacji jest stosowane przewinięcie do przodu. `SETTING`Może to być jedna z następujących wartości. Jeśli nie zostanie określony, `Minor` jest wartością domyślną.

  - `LatestPatch`— Przewinięcie do najwyższej wersji poprawki. Spowoduje to wyłączenie wycofywania wersji pomocniczej.
  - `Minor`— Przewinięcie do najmniejszej wyższej wersji pomocniczej, jeśli brakuje wymaganej wersji pomocniczej. Jeśli jest obecna żądana wersja pomocnicza, zostaną użyte zasady LatestPatch.
  - `Major`-Przewinięcie do najmniejszej wyższej wersji głównej i najniższej wersji pomocniczej, jeśli brakuje wersji głównej. Jeśli jest obecna żądana wersja główna, są używane zasady pomocnicze.
  - `LatestMinor`— Przewinięcie do najnowszej wersji pomocniczej, nawet jeśli jest obecna żądana wersja pomocnicza. Przeznaczone do scenariuszy hostingu składników.
  - `LatestMajor`— Przewinięcie do przodu do najwyższej głównej i najwyższej wersji pomocniczej, nawet jeśli zażądano obecności głównej. Przeznaczone do scenariuszy hostingu składników.
  - `Disable`— Nie przetaczaj dalej. Powiąż tylko z określoną wersją. Te zasady nie są zalecane do użytku ogólnego, ponieważ uniemożliwiają one przekazanie do najnowszych poprawek. Ta wartość jest zalecana tylko do celów testowych.

  Z wyjątkiem programu `Disable` , wszystkie ustawienia będą używać najwyższej dostępnej wersji poprawki.

  Zachowanie przewinięcie do przodu można także skonfigurować we właściwościach pliku projektu, właściwości pliku konfiguracji czasu wykonywania i zmiennej środowiskowej. Aby uzyskać więcej informacji, zobacz [wersja główna środowiska uruchomieniowego do przodu](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).

- **`--roll-forward-on-no-candidate-fx <N>`****Dostępne w zestawie SDK platformy .NET Core 2. x.**

  Definiuje zachowanie, gdy wymagana architektura udostępniona jest niedostępna. `N`może to być:

  - `0`-Wyłącz parzystą wersję pomocniczą do przodu.
  - `1`— Przewinięcie do wersji pomocniczej, ale nie w wersji głównej. Jest to zachowanie domyślne.
  - `2`— Przewinięcie do przodu w wersjach pomocniczych i głównych.

  Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).

  Począwszy od platformy .NET Core 3,0, ta opcja jest zastępowana przez `--roll-forward` , a ta opcja powinna być używana zamiast tego.

- **`--fx-version <VERSION>`**

  Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.

  Ta opcja zastępuje wersję pierwszego odniesienia struktury w `.runtimeconfig.json` pliku aplikacji. Oznacza to, że działa tylko zgodnie z oczekiwaniami, jeśli istnieje tylko jedno odwołanie do struktury. Jeśli aplikacja ma więcej niż jedno odwołanie do platformy, użycie tej opcji może spowodować błędy.

## <a name="dotnet-commands"></a>Polecenia dotnet

### <a name="general"></a>Ogólne

| Polecenie                                       | Funkcja                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | Kompiluje aplikację platformy .NET Core.                                     |
| [dotnet build-server](dotnet-build-server.md) | Współdziała z serwerami uruchomionymi przez kompilację.                          |
| [dotnet clean](dotnet-clean.md)               | Czyste dane wyjściowe kompilacji.                                                |
| [dotnet help](dotnet-help.md)                 | Przedstawia bardziej szczegółową dokumentację dla polecenia w trybie online.           |
| [dotnet migrate](dotnet-migrate.md)           | Migruje prawidłowy projekt w wersji zapoznawczej 2 do projektu zestaw .NET Core SDK 1,0.  |
| [dotnet msbuild](dotnet-msbuild.md)           | Zapewnia dostęp do wiersza polecenia programu MSBuild.                        |
| [dotnet new](dotnet-new.md)                   | Inicjuje projekt C# lub F # dla danego szablonu.                |
| [dotnet pack](dotnet-pack.md)                 | Tworzy pakiet NuGet kodu.                               |
| [dotnet publish](dotnet-publish.md)           | Publikuje zależne od programu .NET Framework lub samodzielną aplikację. |
| [dotnet restore](dotnet-restore.md)           | Przywraca zależności dla danej aplikacji.                  |
| [dotnet run](dotnet-run.md)                   | Uruchamia aplikację ze źródła.                                   |
| [dotnet sln](dotnet-sln.md)                   | Opcje dodawania, usuwania i wyświetlania listy projektów w pliku rozwiązania.       |
| [dotnet store](dotnet-store.md)               | Przechowuje zestawy w magazynie pakietów środowiska uruchomieniowego.                     |
| [dotnet test](dotnet-test.md)                 | Uruchamia testy przy użyciu modułu uruchamiającego testy.                                     |

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
[dotnet nuget push](dotnet-nuget-push.md) | Wypchnij pakiet na serwer i opublikuje go.
[dotnet nuget locals](dotnet-nuget-locals.md) | Czyści lub wyświetla lokalne zasoby NuGet, takie jak pamięć podręczna żądań HTTP, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.
[dotnet nuget add source](dotnet-nuget-add-source.md) | Dodaje źródło NuGet.
[dotnet nuget disable source](dotnet-nuget-disable-source.md) | Wyłącza Źródło NuGet.
[dotnet nuget enable source](dotnet-nuget-enable-source.md) | Włącza Źródło NuGet.
[dotnet nuget list source](dotnet-nuget-list-source.md) | Wyświetla wszystkie skonfigurowane źródła NuGet.
[dotnet nuget remove source](dotnet-nuget-remove-source.md) | Usuwa źródło NuGet.
[dotnet nuget update source](dotnet-nuget-update-source.md) | Aktualizuje źródło narzędzia NuGet.

### <a name="global-tool-path-and-local-tools-commands"></a>Globalne, ścieżki narzędziowe i polecenia narzędzi lokalnych

Narzędzia są aplikacjami konsolowymi, które są instalowane z pakietów NuGet i są wywoływane z wiersza polecenia. Narzędzia można pisać samodzielnie lub instalować Narzędzia zapisane przez inne firmy. Narzędzia są również nazywane narzędziami globalnymi, narzędziami ścieżki narzędzi i narzędziami lokalnymi. Aby uzyskać więcej informacji, zobacz [Narzędzia platformy .NET Core — Omówienie](global-tools.md). Narzędzia globalne i ścieżki narzędzi są dostępne począwszy od zestaw .NET Core SDK 2,1. Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.

Polecenie | Funkcja
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Instaluje narzędzie na komputerze.
[dotnet tool list](dotnet-tool-list.md) | Wyświetla listę wszystkich globalnych narzędzi, ścieżek narzędziowych lub lokalnych zainstalowanych obecnie na komputerze.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Odinstalowuje narzędzie z komputera.
[dotnet tool update](dotnet-tool-update.md) | Aktualizuje narzędzie zainstalowane na komputerze.

### <a name="additional-tools"></a>Dodatkowe narzędzia

Począwszy od zestaw .NET Core SDK 2.1.300, wiele narzędzi, które były dostępne tylko dla każdego projektu, przy użyciu, `DotnetCliToolReference` jest teraz dostępne jako część zestaw .NET Core SDK. Te narzędzia są wymienione w poniższej tabeli:

| Narzędzie                                              | Funkcja                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | Tworzy i zarządza certyfikatami deweloperskimi.                |
| [bieżąco](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core narzędzia wiersza polecenia.                    |
| SQL-pamięć podręczna                                         | SQL Server narzędzia wiersza polecenia pamięci podręcznej.                         |
| [wpisy tajne użytkownika](/aspnet/core/security/app-secrets) | Zarządza kluczami tajnymi użytkowników deweloperskich.                            |
| [Obejrzyj](/aspnet/core/tutorials/dotnet-watch)      | Uruchamia obserwatora plików, który uruchamia polecenie, gdy pliki zmienią się. |

Aby uzyskać więcej informacji na temat każdego narzędzia, wpisz `dotnet <tool-name> --help` .

## <a name="examples"></a>Przykłady

Utwórz nową aplikację konsolową platformy .NET Core:

```dotnetcli
dotnet new console
```

Kompiluj projekt i jego zależności w danym katalogu:

```dotnetcli
dotnet build
```

Uruchom aplikację:

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a>Zmienne środowiskowe

- `DOTNET_ROOT`, `DOTNET_ROOT(x86)`

  Określa lokalizację środowiska uruchomieniowego programu .NET Core, jeśli nie są one zainstalowane w domyślnej lokalizacji. Domyślna lokalizacja w systemie Windows to `C:\Program Files\dotnet` . Domyślną lokalizacją w systemie Linux i macOS jest `/usr/share/dotnet` . Ta zmienna środowiskowa jest używana tylko w przypadku uruchamiania aplikacji za pośrednictwem wygenerowanych plików wykonywalnych (apphosts). `DOTNET_ROOT(x86)`jest używany zamiast w przypadku uruchamiania 32-bitowego pliku wykonywalnego w 64-bitowym systemie operacyjnym.

- `DOTNET_PACKAGES`

  Folder pakiety globalne. Jeśli nie jest ustawiona, zostanie ona domyślnie `~/.nuget/packages` włączona w systemie UNIX lub `%userprofile%\.nuget\packages` w systemie Windows.

- `DOTNET_SERVICING`

  Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.

- `DOTNET_NOLOGO`

  Określa, czy podczas pierwszego uruchomienia są wyświetlane komunikaty telemetryczne programu .NET Core i telemetrii. Ustaw, aby `true` wyciszyć te komunikaty (wartości `true` , `1` lub `yes` zaakceptować) lub ustawić na wartość `false` Zezwalaj (wartości `false` , `0` lub `no` zaakceptować). Jeśli nie zostanie ustawiona, wartość domyślna to, `false` a komunikaty będą wyświetlane po pierwszym uruchomieniu. Ta flaga nie ma wpływu na dane telemetryczne (Zobacz, `DOTNET_CLI_TELEMETRY_OPTOUT` Aby zrezygnować z wysyłania danych telemetrycznych).

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft. Ustaw `true` , aby zrezygnować z funkcji telemetrii (wartości `true` , `1` lub `yes` zaakceptować). W przeciwnym razie ustaw opcję, aby `false` można było wybrać funkcje telemetrii (wartości `false` , `0` lub `no` zaakceptowane). Jeśli nie zostanie ustawiona, wartość domyślna to `false` i aktywna funkcja telemetrii.

- `DOTNET_MULTILEVEL_LOOKUP`

  Określa, czy środowisko uruchomieniowe programu .NET Core, udostępnione środowisko lub zestaw SDK są rozpoznawane z lokalizacji globalnej. Jeśli nie zostanie ustawiona, wartość domyślna to 1 (logiczna `true` ). Ustawienie wartości 0 (logiczne `false` ) nie jest rozpoznawane z lokalizacji globalnej i ma wyizolowane instalacje .NET Core. Aby uzyskać więcej informacji o wyszukiwaniu wielu poziomów, zobacz [SharedFX wyszukiwanie na wielu poziomach](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

- `DOTNET_ROLL_FORWARD`**Dostępne począwszy od platformy .NET Core 3. x.**

  Określa zachowanie funkcji przyciągania do przodu. Aby uzyskać więcej informacji, zobacz `--roll-forward` opcję wcześniejszą w tym artykule.

- `DOTNET_ROLL_FORWARD_TO_PRERELEASE`**Dostępne począwszy od platformy .NET Core 3. x.**

  Jeśli jest ustawiona na `1` (Enabled), umożliwia przewracanie do wersji wstępnej z wersji Release. Domyślnie ( `0` -Disabled), gdy wymagana jest wydana wersja środowiska uruchomieniowego programu .NET Core, przewinięcie do przodu spowoduje uwzględnienie tylko zainstalowanych wersji.

  Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Dostępne w programie .NET Core 2. x.**

  Wyłącza dodatkową wersję do przodu, jeśli jest ustawiona na `0` . Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).

  To ustawienie jest zastępowane w programie .NET Core 3,0 przez program `DOTNET_ROLL_FORWARD` . Zamiast tego należy użyć nowych ustawień.

- `DOTNET_CLI_UI_LANGUAGE`

  Ustawia język interfejsu użytkownika CLI przy użyciu wartości ustawień regionalnych, takich jak `en-us` . Obsługiwane wartości są takie same jak w przypadku programu Visual Studio. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą zmiany języka Instalatora w [dokumentacji instalacyjnej programu Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019). Reguły Menedżera zasobów platformy .NET mają zastosowanie, więc nie trzeba wybierać dokładnego dopasowania, &mdash; które można również wybrać w `CultureInfo` drzewie. Jeśli na przykład ustawisz ją na `fr-CA` , interfejs wiersza polecenia znajdzie i użyje `fr` tłumaczeń. Jeśli ustawisz go na język, który nie jest obsługiwany, interfejs wiersza polecenia powróci do języka angielskiego.

- `DOTNET_DISABLE_GUI_ERRORS`

  W przypadku plików wykonywalnych z obsługą graficznego interfejsu użytkownika — wyłącza okno podręczne, które jest zwykle wyświetlane dla niektórych klas błędów. Tylko zapisuje `stderr` i opuszcza te przypadki.
  
- `DOTNET_ADDITIONAL_DEPS`

  Odpowiednik opcji interfejsu wiersza polecenia `--additional-deps` .

- `DOTNET_RUNTIME_ID`

  Zastępuje wykrytego identyfikatora RID.

- `DOTNET_SHARED_STORE`

  Lokalizacja "udostępnionego magazynu", do którego w niektórych przypadkach jest powracana rozdzielczość zestawu.

- `DOTNET_STARTUP_HOOKS`

  Lista zestawów, z których mają zostać załadowane i wykonane uruchomienia.

- `DOTNET_BUNDLE_EXTRACT_BASE_DIR`**Dostępne począwszy od platformy .NET Core 3. x.**

  Określa katalog, do którego zostanie wyodrębniona aplikacja Jednoplikowa przed wykonaniem.

  Aby uzyskać więcej informacji, zobacz [pliki wykonywalne pojedynczego pliku](../whats-new/dotnet-core-3-0.md#single-file-executables).

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  Steruje śledzeniem diagnostyki ze składników hostingowych, takich jak `dotnet.exe` , `hostfxr` , i `hostpolicy` .

  * `COREHOST_TRACE=[0/1]`-Domyślnie `0` — śledzenie jest wyłączone. Jeśli jest ustawiona na `1` , śledzenie diagnostyki jest włączone.
  * `COREHOST_TRACEFILE=<file path>`-działa tylko wtedy, gdy śledzenie jest włączone za pośrednictwem `COREHOST_TRACE=1` . Po ustawieniu informacje o śledzeniu są zapisywane w określonym pliku, w przeciwnym razie informacje o śledzeniu są zapisywane w `stderr` . **Dostępne począwszy od platformy .NET Core 3. x.**
  * `COREHOST_TRACE_VERBOSITY=[1/2/3/4]`-wartość domyślna to `4` . To ustawienie jest używane tylko wtedy, gdy śledzenie jest włączone za pośrednictwem `COREHOST_TRACE=1` . **Dostępne począwszy od platformy .NET Core 3. x.**
    * `4`— wszystkie informacje o śledzeniu są zapisywane
    * `3`-tylko komunikaty informacyjne, ostrzegawcze i błędów są zapisywane
    * `2`-tylko ostrzeżenia i komunikaty o błędach są zapisywane
    * `1`tylko komunikaty o błędach są zapisywane

  Typowym sposobem uzyskania szczegółowych informacji śledzenia dotyczących uruchamiania aplikacji jest ustawienie `COREHOST_TRACE=1` i `COREHOST_TRACEFILE=host_trace.txt` uruchomienie aplikacji. Nowy plik `host_trace.txt` zostanie utworzony w bieżącym katalogu ze szczegółowymi informacjami.

## <a name="see-also"></a>Zobacz też

- [Pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md)
