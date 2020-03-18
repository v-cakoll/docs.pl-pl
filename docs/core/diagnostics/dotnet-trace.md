---
title: narzędzie dotnet-trace - .NET Core
description: Instalowanie i używanie narzędzia wiersza polecenia dotnet-trace.
ms.date: 11/21/2019
ms.openlocfilehash: b19b159636fbf57fa2d461b398fcf9234aab491c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737647"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>narzędzie dotnet-trace performance analysis utility

**Ten artykuł dotyczy:** ✔️ .NET Core 3.0 SDK i nowszych wersji

## <a name="install-dotnet-trace"></a>Instalowanie śledzenia dotnet

Zainstaluj `dotnet-trace` [pakiet NuGet](https://www.nuget.org/packages/dotnet-trace) za pomocą polecenia [instalacji narzędzia dotnet:](../tools/dotnet-tool-install.md)

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>Streszczenie

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>Opis

Narzędzie: `dotnet-trace`

* Jest narzędziem .NET Core dla wielu platform.
* Włącza kolekcję .NET Core ślady uruchomionego procesu bez profilera macierzystego.
* Jest zbudowany wokół technologii `EventPipe` wieloplatformowej w czasie wykonywania .NET Core.
* Zapewnia takie samo środowisko w systemie Windows, Linux lub macOS.

## <a name="options"></a>Opcje

- **`--version`**

  Wyświetla wersję narzędzia dotnet-counters.

- **`-h|--help`**

  Pokazuje pomoc wiersza polecenia.

## <a name="commands"></a>Polecenia

| Polecenie                                                     |
| ----------------------------------------------------------- |
| [dotnet-trace zbierać](#dotnet-trace-collect)               |
| [konwersja dotnet-trace](#dotnet-trace-convert)               |
| [dotnet-trace ps](#dotnet-trace-ps) |
| [profile listy śladów dotnet](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a>dotnet-trace zbierać

Zbiera śledzenia diagnostycznego z uruchomionego procesu.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a>Opcje

- **`-p|--process-id <PID>`**

  Proces zbierania śladu z.

- **`--buffersize <size>`**

  Ustawia rozmiar buforu kołowego w pamięci w megabajtach. Domyślnie 256 MB.

- **`-o|--output <trace-file-path>`**

  Ścieżka danych wyjściowych dla zebranych danych śledzenia. Jeśli nie określono, domyślnie . `trace.nettrace`

- **`--providers <list-of-comma-separated-providers>`**

  Lista `EventPipe` dostawców oddzielonych przecinkami, która ma być włączona. Dostawcy ci uzupełniają dostawców `--profile <profile-name>`dorozumianych przez . Jeśli istnieje jakakolwiek niespójność dla określonego dostawcy, ta konfiguracja ma pierwszeństwo przed niejawną konfiguracją z profilu.

  Ta lista dostawców jest w formie:

  - `Provider[,Provider]`
  - `Provider`jest w formie: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.
  - `KeyValueArgs`jest w formie: `[key1=value1][;key2=value2]`.

- **`--profile <profile-name>`**

  Nazwany wstępnie zdefiniowany zestaw konfiguracji dostawcy, który umożliwia typowe scenariusze śledzenia, które mają być określone zwięźle.

- **`--format {NetTrace|Speedscope}`**

  Ustawia format wyjściowy konwersji pliku śledzenia. Wartość domyślna to `NetTrace`.

## <a name="dotnet-trace-convert"></a>konwersja dotnet-trace

Konwertuje `nettrace` ślady na alternatywne formaty do użytku z alternatywnymi narzędziami do analizy śladów.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>Argumenty

- **`<input-filename>`**

  Wejściowy plik śledzenia do przekonwertowania. Domyślnie *trace.nettrace*.

### <a name="options"></a>Opcje

- **`--format <NetTrace|Speedscope>`**

  Ustawia format wyjściowy konwersji pliku śledzenia.

- **`-o|--output <output-filename>`**

  Nazwa pliku wyjściowego. Zostanie dodane rozszerzenie formatu docelowego.

## <a name="dotnet-trace-ps"></a>dotnet-trace ps

Wyświetla listę procesów dotnet, do których można dołączyć.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>profile listy śladów dotnet

Wyświetla listę wstępnie utworzonych profili śledzenia z opisem dostawców i filtrów w każdym profilu.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Zbieranie śladu za pomocą śladu dotnet

Aby zebrać `dotnet-trace`ślady za pomocą:

- Pobierz identyfikator procesu (PID) aplikacji .NET Core, aby zbierać ślady.

  - W systemie Windows można na `tasklist` przykład użyć Menedżera zadań lub polecenia.
  - Na przykład w `ps` systemie Linux polecenie.
  - [dotnet-trace ps](#dotnet-trace-ps)

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

- Zatrzymaj zbieranie, `<Enter>` naciskając klawisz. `dotnet-trace`zakończy rejestrowanie zdarzeń do pliku *trace.nettrace.*

## <a name="view-the-trace-captured-from-dotnet-trace"></a>Wyświetlanie śledzenia przechwyconego ze śledzenia dotnetu

W systemie Windows pliki *.nettrace* można przeglądać na [PerfView](https://github.com/microsoft/perfview) do analizy: W przypadku śladów zebranych na innych platformach plik śledzenia można przenieść na komputer z systemem Windows, który ma być oglądany na PerfView.

W systemie Linux śledzenie można wyświetlić, zmieniając `dotnet-trace` `speedscope`format wyjściowy na . Format pliku wyjściowego można `-f|--format` zmienić `-f speedscope` za `dotnet-trace` pomocą `speedscope` opcji - spowoduje, że stworzy plik. Możesz wybrać `nettrace` między (opcja domyślna) i `speedscope`. `Speedscope`pliki można otworzyć <https://www.speedscope.app>w .

> [!NOTE]
> Program runtime .NET Core generuje `nettrace` ślady w formacie. Ślady są konwertowane na speedscope (jeśli określono) po zakończeniu śledzenia. Ponieważ niektóre konwersje mogą spowodować utratę `nettrace` danych, oryginalny plik jest zachowywany obok przekonwertowanego pliku.

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>Użyj śledzenia dotnetdo zbierania wartości liczników w czasie

`dotnet-trace`Cna:

* Służy `EventCounter` do podstawowego monitorowania kondycji w środowiskach wrażliwych na wydajność. Na przykład w produkcji.
* Zbieraj ślady, aby nie były oglądane w czasie rzeczywistym.

Na przykład, aby zbierać wartości licznika wydajności czasu wykonywania, użyj następującego polecenia:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

Poprzednie polecenie informuje liczniki czasu wykonywania do raportowania raz na sekundę do monitorowania kondycji lekki. Zastąpienie `EventCounterIntervalSec=1` wyższą wartością (na przykład 60) umożliwia zbieranie mniejszego śledzenia o mniejszej szczegółowości w danych licznika.

Następujące polecenie zmniejsza obciążenie i rozmiar śledzenia większy niż poprzedni:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

Poprzednie polecenie wyłącza zdarzenia w czasie wykonywania i zarządzany profiler stosu.

## <a name="net-providers"></a>Dostawcy .NET

Program runtime .NET Core obsługuje następujących dostawców .NET. .NET Core używa tych samych `Event Tracing for Windows (ETW)` `EventPipe` słów kluczowych, aby włączyć zarówno i śledzenia.

| Nazwa dostawcy                            | Informacje |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [Dostawca czasu wykonywania](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[Słowa kluczowe w czasie wykonywania CLR](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [Dostawca wybiegu](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[Słowa kluczowe rozkładu CLR](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Włącza profiler próbki. |
