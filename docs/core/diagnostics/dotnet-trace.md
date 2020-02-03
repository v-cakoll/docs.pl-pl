---
title: dotnet-Trace Tool-.NET Core
description: Instalowanie i używanie narzędzia wiersza polecenia do śledzenia dotnet.
ms.date: 11/21/2019
ms.openlocfilehash: b19b159636fbf57fa2d461b398fcf9234aab491c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737647"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>Narzędzie do analizy wydajności śledzenia dotnet

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 3,0 SDK i nowszych wersjach

## <a name="install-dotnet-trace"></a>Zainstaluj program dotnet-Trace

Zainstaluj `dotnet-trace` [pakiet NuGet](https://www.nuget.org/packages/dotnet-trace) za pomocą polecenia [instalacji narzędzia dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>Streszczenie

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Opis

Narzędzie `dotnet-trace`:

* Program to międzyplatformowe narzędzie .NET Core.
* Włącza zbieranie śladów .NET Core działającego procesu bez natywnego profilera.
* Jest zbudowany wokół międzyplatformowej technologii `EventPipe` środowiska uruchomieniowego platformy .NET Core.
* Zapewnia takie samo środowisko w systemach Windows, Linux lub macOS.

## <a name="options"></a>Opcje

- **`--version`**

  Wyświetla wersję narzędzia dotnet-Counters.

- **`-h|--help`**

  Wyświetla pomoc w wierszu polecenia.

## <a name="commands"></a>Polecenia

| Polecenie                                                     |
| ----------------------------------------------------------- |
| [zbieranie danych śledzenia dotnet](#dotnet-trace-collect)               |
| [Konwersja dotnet-Trace](#dotnet-trace-convert)               |
| [dotnet-Trace — śledzenie](#dotnet-trace-ps) |
| [dotnet-lista śledzenia — profile](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a>zbieranie danych śledzenia dotnet

Zbiera dane śledzenia diagnostycznego z uruchomionego procesu.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a>Opcje

- **`-p|--process-id <PID>`**

  Proces zbierania danych śledzenia z programu.

- **`--buffersize <size>`**

  Ustawia rozmiar buforu cyklicznego w pamięci (w megabajtach). Wartość domyślna to 256 MB.

- **`-o|--output <trace-file-path>`**

  Ścieżka wyjściowa zebranych danych śledzenia. Jeśli nie zostanie określony, wartością domyślną będzie `trace.nettrace`.

- **`--providers <list-of-comma-separated-providers>`**

  Rozdzielana przecinkami lista dostawców `EventPipe`, które mają być włączone. Tacy dostawcy uzupełniają dostawców implikowaną przez `--profile <profile-name>`. W przypadku niespójności określonego dostawcy ta konfiguracja ma pierwszeństwo przed niejawną konfiguracją w profilu.

  Ta lista dostawców ma postać:

  - `Provider[,Provider]`
  - `Provider` ma postać: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.
  - `KeyValueArgs` ma postać: `[key1=value1][;key2=value2]`.

- **`--profile <profile-name>`**

  Nazwany wstępnie zdefiniowany zestaw konfiguracji dostawcy, który umożliwia zwięzłe Określanie typowych scenariuszy śledzenia.

- **`--format {NetTrace|Speedscope}`**

  Ustawia format danych wyjściowych dla konwersji pliku śledzenia. Wartość domyślna to `NetTrace`.

## <a name="dotnet-trace-convert"></a>Konwersja dotnet-Trace

Konwertuje `nettrace` ślady na formaty alternatywne do użycia z alternatywnymi narzędziami do analizy śledzenia.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>Argumenty

- **`<input-filename>`**

  Wejściowy plik śledzenia do przekonwertowania. Wartość domyślna to *Trace. Trace*.

### <a name="options"></a>Opcje

- **`--format <NetTrace|Speedscope>`**

  Ustawia format danych wyjściowych dla konwersji pliku śledzenia.

- **`-o|--output <output-filename>`**

  Nazwa pliku wyjściowego. Rozszerzenie formatu docelowego zostanie dodane.

## <a name="dotnet-trace-ps"></a>dotnet-Trace — śledzenie

Wyświetla listę procesów dotnet, które mogą być dołączone do programu.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>dotnet-lista śledzenia — profile

Wyświetla wstępnie skompilowane profile śledzenia z opisem dostawców i filtrów w poszczególnych profilach.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Zbieranie śledzenia przy użyciu funkcji monitorowania dotnet

Aby zebrać ślady przy użyciu `dotnet-trace`:

- Pobierz identyfikator procesu (PID) aplikacji .NET Core, aby zebrać ślady z programu.

  - W systemie Windows można użyć Menedżera zadań lub polecenia `tasklist`, na przykład.
  - Na przykład w systemie Linux polecenie `ps`.
  - [dotnet-Trace — śledzenie](#dotnet-trace-ps)

- Uruchom następujące polecenie:

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  Poprzednie polecenie generuje dane wyjściowe podobne do następujących:

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- Zatrzymaj zbieranie, naciskając klawisz `<Enter>`. `dotnet-trace` zakończy rejestrowanie zdarzeń w pliku *Trace. webtrace* .

## <a name="view-the-trace-captured-from-dotnet-trace"></a>Wyświetl śledzenie przechwycone przez śledzenie dotnet

W systemie Windows można przeglądać pliki *śledzenia* w usłudze [Narzędzia PerfView](https://github.com/microsoft/perfview) for Analysis: w przypadku śladów zebranych na innych platformach plik śledzenia można przenieść na komputer z systemem Windows, który ma być wyświetlany na narzędzia PerfView.

W systemie Linux śledzenie można wyświetlić, zmieniając format danych wyjściowych `dotnet-trace` na `speedscope`. Format pliku wyjściowego można zmienić przy użyciu opcji `-f|--format` — `-f speedscope` `dotnet-trace` utworzyć plik `speedscope`. Można wybrać między `nettrace` (opcja domyślna) i `speedscope`. Pliki `Speedscope` można otwierać w <https://www.speedscope.app>.

> [!NOTE]
> Środowisko uruchomieniowe programu .NET Core generuje ślady w formacie `nettrace`. Ślady są konwertowane na speedscope (jeśli zostaną określone) po zakończeniu śledzenia. Ponieważ niektóre Konwersje mogą spowodować utratę danych, oryginalny plik `nettrace` zostanie zachowany obok skonwertowanego pliku.

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>Używanie funkcji monitorowania dotnet do zbierania wartości licznika w czasie

`dotnet-trace` może:

* Użyj `EventCounter` na potrzeby podstawowego monitorowania kondycji w środowiskach z uwzględnieniem wydajności. Na przykład w środowisku produkcyjnym.
* Zbieraj ślady, aby nie trzeba było ich wyświetlać w czasie rzeczywistym.

Na przykład, aby zbierać wartości liczników wydajności środowiska uruchomieniowego, użyj następującego polecenia:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

Poprzednie polecenie instruuje liczniki środowiska uruchomieniowego do raportowania co sekundę w przypadku uproszczonego monitorowania kondycji. Zastępowanie `EventCounterIntervalSec=1` wartością wyższą (na przykład 60) umożliwia zbieranie mniejszych śladów o mniejszej szczegółowości danych licznika.

Następujące polecenie zmniejsza obciążenie i rozmiar śladu więcej niż poprzedni:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

Poprzednie polecenie powoduje wyłączenie zdarzeń środowiska uruchomieniowego i zarządzanego profilera stosu.

## <a name="net-providers"></a>Dostawcy .NET

Środowisko uruchomieniowe platformy .NET Core obsługuje następujących dostawców platformy .NET. Program .NET Core używa tych samych słów kluczowych, aby umożliwić śledzenie zarówno `Event Tracing for Windows (ETW)`, jak i `EventPipe`.

| Nazwa dostawcy                            | Informacje |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [Dostawca środowiska uruchomieniowego](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[Słowa kluczowe środowiska uruchomieniowego CLR](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [Dostawca uwalniania](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[Słowa kluczowe uwalniania CLR](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Włącza przykładowy Profiler. |
