---
title: dotnet — polecenie
description: Dowiedz się więcej na temat polecenia dotnet (sterownika generycznego dla interfejs wiersza polecenia platformy .NET Core) i jego użycia.
ms.date: 02/13/2020
ms.openlocfilehash: da37c5cc3b019851e245fa3f65ae9dfb8a3fef54
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240873"
---
# <a name="dotnet-command"></a>dotnet — polecenie

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

## <a name="name"></a>Name (Nazwa)

`dotnet` — sterownik ogólny interfejs wiersza polecenia platformy .NET Core.

## <a name="synopsis"></a>Streszczenie

Aby uzyskać informacje na temat dostępnych poleceń i środowiska:

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

`--roll-forward` jest dostępna od platformy .NET Core 3. x. Użyj `--roll-forward-on-no-candidate-fx` dla platformy .NET Core 2. x.

## <a name="description"></a>Opis

Polecenie `dotnet` ma dwie funkcje:

- Zawiera polecenia umożliwiające pracę z projektami .NET Core.

  Na przykład [`dotnet build`](dotnet-build.md) kompiluje projekt. Każde polecenie definiuje własne opcje i argumenty. Wszystkie polecenia obsługują opcję `--help` do drukowania krótkiej dokumentacji dotyczącej sposobu korzystania z polecenia.

- Uruchamia aplikacje platformy .NET Core.

  Należy określić ścieżkę do pliku `.dll` aplikacji, aby uruchomić aplikację. Na przykład `dotnet myapp.dll` uruchamia aplikację `myapp`. Zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) , aby dowiedzieć się więcej na temat opcji wdrażania.

## <a name="options"></a>Opcje

Różne opcje są dostępne dla `dotnet` samodzielne, na potrzeby uruchamiania polecenia i uruchamiania aplikacji.

### <a name="options-for-dotnet-by-itself"></a>Opcje dla dotnet

Poniższe opcje są przeznaczone dla `dotnet`. Na przykład `dotnet --info`. Drukują informacje o środowisku.

- **`--info`**

  Drukuje szczegółowe informacje na temat instalacji programu .NET Core i środowiska maszynowego, takiego jak bieżący system operacyjny, i zatwierdzania SHA dla wersji .NET Core.

- **`--version`**

  Drukuje używaną wersję zestaw .NET Core SDK.

- **`--list-runtimes`**

  Drukuje listę zainstalowanych środowiska uruchomieniowego platformy .NET Core.

- **`--list-sdks`**

  Drukuje listę zainstalowanych zestawów SDK platformy .NET Core.

- **`-h|--help`**

  Drukuje listę dostępnych poleceń.

### <a name="sdk-options-for-running-a-command"></a>Opcje zestawu SDK do uruchamiania polecenia

Poniższe opcje dotyczą `dotnet` z poleceniem. Na przykład `dotnet build --help`.

- **`-d|--diagnostics`**

  Włącza diagnostykę danych wyjściowych.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`. Nieobsługiwane w każdym poleceniu. Aby określić, czy ta opcja jest dostępna, zobacz określoną stronę poleceń.

- **`-h|--help`**

  Drukuje dokumentację dla danego polecenia, taką jak `dotnet build --help`.

- **`command options`**

  Każde polecenie definiuje opcje specyficzne dla tego polecenia. Listę dostępnych opcji można znaleźć na stronie z konkretnym poleceniem.

### <a name="runtime-options"></a>Opcje środowiska uruchomieniowego

Poniższe opcje są dostępne, gdy `dotnet` uruchamia aplikację. Na przykład `dotnet myapp.dll --fx-version 3.1.1`.

- **`--additionalprobingpath <PATH>`**

  Ścieżka zawierająca zasady i zestawy do sondowania.

- **`--additional-deps <PATH>`**

  Ścieżka do dodatkowego pliku *. deps. JSON* . Plik *deps. JSON* zawiera listę zależności, zależności kompilacji i informacje o wersji używane do rozwiązywania konfliktów zestawów. Aby uzyskać więcej informacji, zobacz [pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) w serwisie GitHub.

- **`--fx-version <VERSION>`**

  Wersja środowiska uruchomieniowego platformy .NET Core do użycia w celu uruchomienia aplikacji.

- **`--runtimeconfig`**

  Ścieżka do pliku *runtimeconfig. JSON* . Plik *runtimeconfig. JSON* to plik konfiguracji, który zawiera ustawienia czasu wykonywania. Aby uzyskać więcej informacji, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md#runtimeconfigjson).

- **`--roll-forward-on-no-candidate-fx <N>`** **dostępne w zestawie SDK platformy .NET Core 2. x.**

  Definiuje zachowanie, gdy wymagana architektura udostępniona jest niedostępna. `N` mogą być następujące:

  - `0` — Wyłącz nawet dodatkową wersję pomocniczą.
  - `1` — przewinięcie do wersji pomocniczej, ale nie w wersji głównej. Jest to zachowanie domyślne.
  - `2` — przewinięcie w przód do wersji pomocniczych i głównych.

   Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).

- **`--roll-forward <SETTING>`** **dostępne od zestaw .NET Core SDK 3,0.**

  Kontroluje sposób, w jaki do aplikacji jest stosowane przewinięcie do przodu. `SETTING` może być jedną z następujących wartości. Jeśli nie zostanie określony, `Minor` jest wartością domyślną.

  - `LatestPatch` — przewinięcie do najwyższej wersji poprawki. Spowoduje to wyłączenie wycofywania wersji pomocniczej.
  - `Minor` — przewinięcie do najmniejszej wyższej wersji pomocniczej, jeśli brakuje wymaganej wersji pomocniczej. Jeśli jest obecna żądana wersja pomocnicza, zostaną użyte zasady LatestPatch.
  - `Major` — przewinięcie do najmniejszej wyższej wersji głównej i najniższej wersji pomocniczej, jeśli brakuje żądanej wersji głównej. Jeśli jest obecna żądana wersja główna, są używane zasady pomocnicze.
  - `LatestMinor` — przewinięcie do najnowszej wersji pomocniczej, nawet jeśli jest obecna żądana wersja pomocnicza. Przeznaczone do scenariuszy hostingu składników.
  - `LatestMajor` — przewinięcie do przodu do najwyższej głównej i najwyższej wersji pomocniczej, nawet jeśli zażądana główna wersja jest obecna. Przeznaczone do scenariuszy hostingu składników.
  - `Disable` — nie przetaczaj dalej. Powiąż tylko z określoną wersją. Te zasady nie są zalecane do użytku ogólnego, ponieważ uniemożliwiają one przekazanie do najnowszych poprawek. Ta wartość jest zalecana tylko do celów testowych.

Z wyjątkiem `Disable`, wszystkie ustawienia będą używać najwyższej dostępnej wersji poprawki.

Zachowanie przewinięcie do przodu można także skonfigurować we właściwościach pliku projektu, właściwości pliku konfiguracji czasu wykonywania i zmiennej środowiskowej. Aby uzyskać więcej informacji, zobacz [wersja główna środowiska uruchomieniowego do przodu](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).

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
| [dotnet new](dotnet-new.md)                   | Inicjuje projekt C# lub F# dla danego szablonu.                |
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
[dotnet nuget locals](dotnet-nuget-locals.md) | Czyści lub wyświetla lokalne zasoby NuGet, takie jak pamięć podręczna żądań HTTP, tymczasowa pamięć podręczna lub folder pakietów globalnych dla całego komputera.
[dotnet nuget push](dotnet-nuget-push.md) | Wypchnij pakiet na serwer i opublikuje go.

### <a name="global-tool-path-and-local-tools-commands"></a>Globalne, ścieżki narzędziowe i polecenia narzędzi lokalnych

Narzędzia są aplikacjami konsolowymi, które są instalowane z pakietów NuGet i są wywoływane z wiersza polecenia. Narzędzia można pisać samodzielnie lub instalować Narzędzia zapisane przez inne firmy. Narzędzia są również nazywane narzędziami globalnymi, narzędziami ścieżki narzędzi i narzędziami lokalnymi. Aby uzyskać więcej informacji, zobacz [Narzędzia platformy .NET Core — Omówienie](global-tools.md). Narzędzia globalne i ścieżki narzędzi są dostępne począwszy od zestaw .NET Core SDK 2,1. Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.

Polecenie | Funkcja
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Instaluje narzędzie na komputerze.
[dotnet tool list](dotnet-tool-list.md) | Wyświetla listę wszystkich globalnych narzędzi, ścieżek narzędziowych lub lokalnych zainstalowanych obecnie na komputerze.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Odinstalowuje narzędzie z komputera.
[dotnet tool update](dotnet-tool-update.md) | Aktualizuje narzędzie zainstalowane na komputerze.

### <a name="additional-tools"></a>Dodatkowe narzędzia

Począwszy od zestaw .NET Core SDK 2.1.300, wiele narzędzi, które były dostępne tylko dla poszczególnych projektów, przy użyciu `DotnetCliToolReference`, są teraz dostępne jako część zestaw .NET Core SDK. Te narzędzia są wymienione w poniższej tabeli:

| Narzędzie                                              | Funkcja                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | Tworzy i zarządza certyfikatami deweloperskimi.                |
| [bieżąco](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core narzędzia wiersza polecenia.                    |
| SQL-pamięć podręczna                                         | SQL Server narzędzia wiersza polecenia pamięci podręcznej.                         |
| [wpisy tajne użytkownika](/aspnet/core/security/app-secrets) | Zarządza kluczami tajnymi użytkowników deweloperskich.                            |
| [Obejrzyj](/aspnet/core/tutorials/dotnet-watch)      | Uruchamia obserwatora plików, który uruchamia polecenie, gdy pliki zmienią się. |

Aby uzyskać więcej informacji na temat każdego narzędzia, wpisz `dotnet <tool-name> --help`.

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

  Określa lokalizację środowiska uruchomieniowego programu .NET Core, jeśli nie są one zainstalowane w domyślnej lokalizacji. Domyślną lokalizacją w systemie Windows jest `C:\Program Files\dotnet`. Domyślną lokalizacją w systemie Linux i macOS jest `/usr/share/dotnet`. Ta zmienna środowiskowa jest używana tylko w przypadku uruchamiania aplikacji za pośrednictwem wygenerowanych plików wykonywalnych (apphosts). Zamiast tego użyto `DOTNET_ROOT(x86)` w przypadku uruchamiania 32-bitowego pliku wykonywalnego na 64-bitowym systemie operacyjnym.

- `DOTNET_PACKAGES`

  Folder pakiety globalne. Jeśli nie zostanie ustawiona, domyślnie jest `~/.nuget/packages` w systemie UNIX lub `%userprofile%\.nuget\packages` na komputerze z systemem Windows.

- `DOTNET_SERVICING`

  Określa lokalizację indeksu obsługi, który ma być używany przez host udostępniony podczas ładowania środowiska uruchomieniowego.

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  Określa, czy dane dotyczące użycia narzędzi .NET Core są zbierane i wysyłane do firmy Microsoft. Ustaw `true`, aby zrezygnować z funkcji telemetrii (wartości `true`, `1`lub `yes` zaakceptowane). W przeciwnym razie ustaw wartość `false`, aby zrezygnować z funkcji telemetrii (wartości `false`, `0`lub `no` zaakceptowane). Jeśli nie zostanie ustawiona, wartość domyślna to `false` i aktywna jest funkcja telemetrii.

- `DOTNET_MULTILEVEL_LOOKUP`

  Określa, czy środowisko uruchomieniowe programu .NET Core, udostępnione środowisko lub zestaw SDK są rozpoznawane z lokalizacji globalnej. Jeśli nie zostanie ustawiona, wartość domyślna to 1 (`true`logiczna). Ustaw wartość 0 (logiczne `false`), aby nie rozwiązać z lokalizacji globalnej i uzyskać izolowanych instalacji platformy .NET Core. Aby uzyskać więcej informacji o wyszukiwaniu wielu poziomów, zobacz [SharedFX wyszukiwanie na wielu poziomach](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

- `DOTNET_ROLL_FORWARD` **dostępne począwszy od zestawu .NET Core 3. x SDK.**

  Określa zachowanie funkcji przyciągania do przodu. Aby uzyskać więcej informacji, zobacz opcję `--roll-forward` wcześniej w tym artykule.

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **dostępne w zestawie SDK platformy .NET Core 2. x.**

  Wyłącza opcję wycofywania wersji pomocniczej, jeśli jest ustawiona na `0`. Aby uzyskać więcej informacji, zobacz [przewinięcie do przodu](../whats-new/dotnet-core-2-1.md#roll-forward).

- `DOTNET_CLI_UI_LANGUAGE`

  Ustawia język interfejsu użytkownika CLI przy użyciu wartości ustawień regionalnych, takich jak `en-us`. Obsługiwane wartości są takie same jak w przypadku programu Visual Studio. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą zmiany języka Instalatora w [dokumentacji instalacyjnej programu Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019). Reguły Menedżera zasobów platformy .NET mają zastosowanie, więc nie trzeba wybierać dokładnego dopasowania&mdash;można również wybrać elementy podrzędne w drzewie `CultureInfo`. Na przykład jeśli ustawisz ją na `fr-CA`, interfejs wiersza polecenia znajdzie i użyje tłumaczeń `fr`. Jeśli ustawisz go na język, który nie jest obsługiwany, interfejs wiersza polecenia powróci do języka angielskiego.

- `DOTNET_DISABLE_GUI_ERRORS`

  Dla plików wykonywalnych z włączoną obsługą graficznego interfejsu użytkownika — wyłącza okno podręczne, które zwykle jest wyświetlane dla niektórych klas błędów. Zapisuje tylko dane do `stderr` i opuszcza w tych przypadkach.
  
- `DOTNET_ADDITIONAL_DEPS`

  Odpowiednik opcji interfejsu wiersza polecenia `--additional-deps`.

- `DOTNET_RUNTIME_ID`

  Zastępuje wykrytego identyfikatora RID.

- `DOTNET_SHARED_STORE`

  Lokalizacja "udostępnionego magazynu", do którego w niektórych przypadkach jest powracana rozdzielczość zestawu.

- `DOTNET_STARTUP_HOOKS`

  Lista zestawów, z których mają zostać załadowane i wykonane uruchomienia.

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  Steruje śledzeniem diagnostyki ze składników hostingowych, takich jak `dotnet.exe`, `hostfxr`i `hostpolicy`.

## <a name="see-also"></a>Zobacz też

- [Pliki konfiguracji środowiska uruchomieniowego](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md)
