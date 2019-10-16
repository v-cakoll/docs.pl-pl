---
title: dotnet-Trace — .NET Core
description: Instalowanie i używanie narzędzia wiersza polecenia do śledzenia dotnet.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: 6513cf63070bc1984006da75313e9912d76a6c95
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321583"
---
# <a name="trace-for-performance-analysis-utility-dotnet-trace"></a>Śledzenie dla narzędzia do analizy wydajności (`dotnet-trace`)

**Ten artykuł dotyczy:** .net Core 3,0 SDK i nowszych wersji

## <a name="installing-dotnet-trace"></a>Instalowanie `dotnet-trace`

Aby zainstalować najnowszą wersję [pakietu NuGet](https://www.nuget.org/packages/dotnet-trace)`dotnet-trace`, należy użyć polecenia [Install narzędzia dotnet](../tools/dotnet-tool-install.md) :

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>Streszczenie

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Opis

Narzędzie `dotnet-trace` to międzyplatformowe narzędzie globalne interfejsu wiersza polecenia, które umożliwia zbieranie śladów programu .NET Core działającego procesu bez żadnego z natywnych profilerów. Jest ona oparta na wielu platformach technologii `EventPipe` środowiska uruchomieniowego platformy .NET Core. `dotnet-trace` zapewnia takie samo środowisko w systemie Windows, Linux lub macOS.

## <a name="options"></a>Opcje

- **`--version`**

Wyświetla wersję narzędzia dotnet-Counters.

- **`-h|--help`**

Pokaż pomoc wiersza polecenia.

## <a name="commands"></a>Polecenia

| Polecenie                                                     |
| ----------------------------------------------------------- |
| [zbieranie danych śledzenia dotnet](#dotnet-trace-collect)               |
| [Konwersja dotnet-Trace](#dotnet-trace-convert)               |
| [dotnet-Trace list-processs](#dotnet-trace-list-processes) |
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

  Ścieżka wyjściowa zebranych danych śledzenia. Jeśli nie zostanie określony, wartość domyślna to `trace.nettrace`.

- **`--providers <list-of-comma-separated-providers>`**

  Rozdzielana przecinkami lista dostawców `EventPipe` do włączenia. Tacy dostawcy uzupełniają dostawców implikowaną przez `--profile <profile-name>`. W przypadku niespójności określonego dostawcy konfiguracja ma pierwszeństwo przed niejawną konfiguracją w profilu.

  Ta lista dostawców ma postać:

  - `Provider[,Provider]`
  - `Provider` ma postać: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.
  - `KeyValueArgs` ma postać: `[key1=value1][;key2=value2]`.

- **`--profile <profile-name>`**

  Nazwany wstępnie zdefiniowany zestaw konfiguracji dostawcy, który umożliwia zwięzłe Określanie typowych scenariuszy śledzenia.

- **`--format <NetTrace|Speedscope>`**

  Ustawia format danych wyjściowych dla konwersji pliku śledzenia.

## <a name="dotnet-trace-convert"></a>Konwersja dotnet-Trace

Konwertuje ślady `nettrace` na formaty alternatywne do użycia z alternatywnymi narzędziami do analizy śledzenia.

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

## <a name="dotnet-trace-list-processes"></a>dotnet-Trace list-processs

Wyświetla listę procesów dotnet, które mogą być śledzone.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-trace list-processes [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>dotnet-lista śledzenia — profile

Wyświetla wstępnie skompilowane profile śledzenia z opisem dostawców i filtrów w poszczególnych profilach.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Zbierz ślad z `dotnet-trace`

- Aby zebrać ślady przy użyciu `dotnet-trace`, należy najpierw sprawdzić identyfikator procesu (PID) aplikacji .NET Core w celu zebrania śladów.

  - W systemie Windows dostępne są opcje, takie jak użycie Menedżera zadań lub polecenia `tasklist`.
  - W systemie Linux prosta opcja może używać `ps` polecenie.

Możesz również użyć polecenia programu [dotnet-Trace list-processs](#dotnet-trace-list-processes) , aby dowiedzieć się, jakie procesy .NET Core są uruchomione, wraz z ich numerami PID.

- Następnie uruchom następujące polecenie:

```console
> dotnet-trace collect --process-id <PID>

Press <Enter> to exit...
Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
```

- Na koniec Zatrzymaj zbieranie, naciskając klawisz `<Enter>`, a `dotnet-trace` spowoduje zakończenie rejestrowania zdarzeń w pliku `trace.nettrace`.

## <a name="viewing-the-trace-captured-from-dotnet-trace"></a>Wyświetlanie śladu przechwytywanego z `dotnet-trace`

W systemie Windows pliki `.nettrace` mogą być wyświetlane w [Narzędzia PerfView](https://github.com/microsoft/perfview) na potrzeby analizy, podobnie jak ślady zbierane z użyciem ETW lub LTTng. W przypadku śladów zebranych w systemie Linux można przenieść ślad do komputera z systemem Windows, aby był wyświetlany w witrynie narzędzia PerfView.

Możesz również wyświetlić ślad na komputerze z systemem Linux, zmieniając format danych wyjściowych `dotnet-trace` na `speedscope`. Można zmienić format pliku wyjściowego przy użyciu opcji `-f|--format`-`-f speedscope` spowoduje, że `dotnet-trace` będzie generował plik `speedscope`. Obecnie można wybrać między `nettrace` (opcja domyślna) i `speedscope`. Pliki `Speedscope` można otwierać w <https://www.speedscope.app>.

> [!NOTE]
> Środowisko uruchomieniowe programu .NET Core generuje ślady w formacie `nettrace` i są konwertowane na speedscope (jeśli zostały określone) po zakończeniu śledzenia. Ponieważ niektóre Konwersje mogą spowodować utratę danych, oryginalny plik `nettrace` jest zachowywany obok skonwertowanego pliku.

## <a name="using-dotnet-trace-to-collect-counter-values-over-time"></a>Używanie `dotnet-trace` do zbierania wartości licznika w czasie

Jeśli próbujesz użyć `EventCounter` do podstawowego monitorowania kondycji w ustawieniach z uwzględnieniem wydajności, takich jak środowiska produkcyjne i chcesz zbierać ślady zamiast oglądać je w czasie rzeczywistym, możesz to zrobić przy użyciu również `dotnet-trace`.

Jeśli na przykład chcesz zbierać wartości liczników wydajności środowiska uruchomieniowego, możesz użyć następującego polecenia:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

To polecenie informuje, że liczniki środowiska uruchomieniowego są raportowane co sekundę na potrzeby uproszczonego monitorowania kondycji. Zastępowanie `EventCounterIntervalSec=1` wyższą wartością (na przykład 60) umożliwia zebranie mniejszego śladu o mniejszej szczegółowości danych licznika.

Aby wyłączyć zdarzenia środowiska uruchomieniowego w celu zmniejszenia obciążenia (i rozmiaru śledzenia), możesz użyć następującego polecenia, aby wyłączyć zdarzenia środowiska uruchomieniowego i zarządzanego profilera stosu.

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

## <a name="net-providers"></a>Dostawcy .NET

Środowisko uruchomieniowe platformy .NET Core obsługuje następujących dostawców platformy .NET. Program .NET Core używa tych samych słów kluczowych, aby umożliwić śledzenie `Event Tracing for Windows (ETW)` i `EventPipe`.

| Nazwa dostawcy                            | Informacje |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [Dostawca środowiska uruchomieniowego](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[Słowa kluczowe środowiska uruchomieniowego CLR](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [Dostawca uwalniania](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[Słowa kluczowe uwalniania CLR](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Włącza przykładowy Profiler. |
