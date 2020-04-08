---
title: narzędzie dotnet-trace - .NET Core
description: Instalowanie i używanie narzędzia wiersza polecenia dotnet-trace.
ms.date: 11/21/2019
ms.openlocfilehash: 6880c3721e4cab12677bd02c82ca944cc9812670
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888088"
---
# <a name="dotnet-trace-performance-analysis-utility"></a>narzędzie do analizy wydajności śledzenia dotnet

**Ten artykuł dotyczy:** ✔️.NET Core 3.0 SDK i nowszych wersjach

## <a name="install-dotnet-trace"></a>Instalowanie dotnet-trace

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

* Jest wieloplatformowym narzędziem .NET Core.
* Umożliwia zbieranie śladów .NET Core uruchomionego procesu bez natywnego profilera.
* Jest zbudowany wokół technologii `EventPipe` międzyplatformowej środowiska uruchomieniowego .NET Core.
* Zapewnia takie samo środowisko w systemach Windows, Linux lub macOS.

## <a name="options"></a>Opcje

- **`--version`**

  Wyświetla wersję narzędzia dotnet-trace.

- **`-h|--help`**

  Pokazuje pomoc wiersza polecenia.

## <a name="commands"></a>Polecenia

| Polecenie                                                     |
| ----------------------------------------------------------- |
| [zbieranie śladów dotnet](#dotnet-trace-collect)               |
| [konwersja śledzenia dotnet](#dotnet-trace-convert)               |
| [dotnet-trace ps](#dotnet-trace-ps) |
| [profile list śledzenia dotnet](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a>zbieranie śladów dotnet

Zbiera śledzenia diagnostycznego z uruchomionego procesu.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a>Opcje

- **`-p|--process-id <PID>`**

  Proces zbierania śledzenia z.

- **`--buffersize <size>`**

  Ustawia rozmiar buforu kołowego w pamięci w megabajtach. Domyślnie 256 MB.

- **`-o|--output <trace-file-path>`**

  Ścieżka wyjściowa dla zebranych danych śledzenia. Jeśli nie określono, `trace.nettrace`domyślnie jest to .

- **`--providers <list-of-comma-separated-providers>`**

  Lista dostawców oddzielona `EventPipe` przecinkami ma być włączona. Dostawcy ci uzupełniają `--profile <profile-name>`wszelkie dostawców dorozumianych przez . Jeśli istnieje jakakolwiek niespójność dla określonego dostawcy, ta konfiguracja ma pierwszeństwo przed niejawną konfiguracją z profilu.

  Ta lista dostawców jest w formie:

  - `Provider[,Provider]`
  - `Provider`jest w formie: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.
  - `KeyValueArgs`jest w formie: `[key1=value1][;key2=value2]`.

- **`--profile <profile-name>`**

  Nazwany wstępnie zdefiniowany zestaw konfiguracji dostawcy, który umożliwia typowe scenariusze śledzenia, które mają być określone zwięźle.

- **`--format {NetTrace|Speedscope}`**

  Ustawia format danych wyjściowych dla konwersji pliku śledzenia. Wartość domyślna to `NetTrace`.

## <a name="dotnet-trace-convert"></a>konwersja śledzenia dotnet

Konwertuje ślady `nettrace` na alternatywne formaty do użycia z alternatywnymi narzędziami analizy śledzenia.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>Argumenty

- **`<input-filename>`**

  Wejściowy plik śledzenia do konwersji. Wartość domyślna *trace.nettrace*.

### <a name="options"></a>Opcje

- **`--format <NetTrace|Speedscope>`**

  Ustawia format danych wyjściowych dla konwersji pliku śledzenia.

- **`-o|--output <output-filename>`**

  Wyjściowa nazwa pliku. Zostanie dodane rozszerzenie formatu docelowego.

## <a name="dotnet-trace-ps"></a>dotnet-trace ps

Wyświetla listę procesów dotnet, do których można dołączyć.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>profile list śledzenia dotnet

Wyświetla listę wstępnie utworzonych profili śledzenia z opisem dostawców i filtrów w każdym profilu.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>Zbieranie śladu za pomocą śledzenia dotnet

Aby zebrać `dotnet-trace`ślady za pomocą:

- Pobierz identyfikator procesu (PID) aplikacji .NET Core do zbierania śladów.

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

## <a name="view-the-trace-captured-from-dotnet-trace"></a>Wyświetlanie śladu przechwyconego z dotnet-trace

W systemie Windows pliki *.nettrace* można wyświetlać na [PerfView](https://github.com/microsoft/perfview) do analizy: W przypadku śladów zebranych na innych platformach plik śledzenia można przenieść do komputera z systemem Windows, który ma być oglądany na PerfView.

W systemie Linux można wyświetlić śledzenie, zmieniając `dotnet-trace` `speedscope`format wyjściowy na . Format pliku wyjściowego można `-f|--format` zmienić `-f speedscope` za `dotnet-trace` pomocą `speedscope` opcji - spowoduje, że plik zostanie wyprodukowany. Można wybrać `nettrace` opcję (opcja domyślna) i `speedscope`. `Speedscope`można otworzyć w <https://www.speedscope.app>pliku .

> [!NOTE]
> Środowisko uruchomieniowe .NET Core generuje `nettrace` ślady w formacie. Ślady są konwertowane na speedscope (jeśli określono) po zakończeniu śledzenia. Ponieważ niektóre konwersje mogą spowodować utratę `nettrace` danych, oryginalny plik jest zachowywany obok przekonwertowanego pliku.

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a>Zbieranie wartości liczników za pomocą śledzenia dotnetu w czasie

`dotnet-trace`Cna:

* Służy `EventCounter` do podstawowego monitorowania kondycji w środowiskach wrażliwych na wydajność. Na przykład w produkcji.
* Zbieraj ślady, aby nie trzeba było ich oglądać w czasie rzeczywistym.

Na przykład, aby zebrać wartości licznika wydajności środowiska uruchomieniowego, należy użyć następującego polecenia:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

Poprzednie polecenie informuje liczniki środowiska wykonawczego do raportowania raz na sekundę dla monitorowania kondycji w stanie lekkim. Zastąpienie `EventCounterIntervalSec=1` wyższą wartością (na przykład 60) umożliwia zbieranie mniejszego śledzenia o mniejszej szczegółowości w danych licznika.

Następujące polecenie zmniejsza obciążenie i rozmiar śledzenia więcej niż poprzedni:

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

Poprzednie polecenie wyłącza zdarzenia środowiska uruchomieniowego i profiler zarządzanego stosu.

## <a name="net-providers"></a>Dostawcy platformy .NET

Środowisko uruchomieniowe .NET Core obsługuje następujących dostawców platformy .NET. .NET Core używa tych samych `Event Tracing for Windows (ETW)` słów `EventPipe` kluczowych, aby włączyć zarówno i ślady.

| Nazwa dostawcy                            | Informacje |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [Dostawca środowiska wykonawczego](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[Słowa kluczowe środowiska wykonawczego CLR](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [Dostawca wybiegiem](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[Clr Rundown Słowa kluczowe](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | Włącza profiler próbki. |
