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
# <a name="trace-for-performance-analysis-utility-dotnet-trace"></a><span data-ttu-id="9c42c-103">Śledzenie dla narzędzia do analizy wydajności (`dotnet-trace`)</span><span class="sxs-lookup"><span data-stu-id="9c42c-103">Trace for performance analysis utility (`dotnet-trace`)</span></span>

<span data-ttu-id="9c42c-104">**Ten artykuł dotyczy:** .net Core 3,0 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="9c42c-104">**This article applies to:** .NET Core 3.0 SDK and later versions</span></span>

## <a name="installing-dotnet-trace"></a><span data-ttu-id="9c42c-105">Instalowanie `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="9c42c-105">Installing `dotnet-trace`</span></span>

<span data-ttu-id="9c42c-106">Aby zainstalować najnowszą wersję [pakietu NuGet](https://www.nuget.org/packages/dotnet-trace)`dotnet-trace`, należy użyć polecenia [Install narzędzia dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="9c42c-106">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="9c42c-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="9c42c-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="9c42c-108">Opis</span><span class="sxs-lookup"><span data-stu-id="9c42c-108">Description</span></span>

<span data-ttu-id="9c42c-109">Narzędzie `dotnet-trace` to międzyplatformowe narzędzie globalne interfejsu wiersza polecenia, które umożliwia zbieranie śladów programu .NET Core działającego procesu bez żadnego z natywnych profilerów.</span><span class="sxs-lookup"><span data-stu-id="9c42c-109">The `dotnet-trace` tool is a cross-platform CLI global tool that enables the collection of .NET Core traces of a running process without any native profiler involved.</span></span> <span data-ttu-id="9c42c-110">Jest ona oparta na wielu platformach technologii `EventPipe` środowiska uruchomieniowego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c42c-110">It's built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span> <span data-ttu-id="9c42c-111">`dotnet-trace` zapewnia takie samo środowisko w systemie Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="9c42c-111">`dotnet-trace` delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="9c42c-112">Opcje</span><span class="sxs-lookup"><span data-stu-id="9c42c-112">Options</span></span>

- **`--version`**

<span data-ttu-id="9c42c-113">Wyświetla wersję narzędzia dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="9c42c-113">Display the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

<span data-ttu-id="9c42c-114">Pokaż pomoc wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="9c42c-114">Show command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="9c42c-115">Polecenia</span><span class="sxs-lookup"><span data-stu-id="9c42c-115">Commands</span></span>

| <span data-ttu-id="9c42c-116">Polecenie</span><span class="sxs-lookup"><span data-stu-id="9c42c-116">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="9c42c-117">zbieranie danych śledzenia dotnet</span><span class="sxs-lookup"><span data-stu-id="9c42c-117">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="9c42c-118">Konwersja dotnet-Trace</span><span class="sxs-lookup"><span data-stu-id="9c42c-118">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="9c42c-119">dotnet-Trace list-processs</span><span class="sxs-lookup"><span data-stu-id="9c42c-119">dotnet-trace list-processes</span></span>](#dotnet-trace-list-processes) |
| [<span data-ttu-id="9c42c-120">dotnet-lista śledzenia — profile</span><span class="sxs-lookup"><span data-stu-id="9c42c-120">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="9c42c-121">zbieranie danych śledzenia dotnet</span><span class="sxs-lookup"><span data-stu-id="9c42c-121">dotnet-trace collect</span></span>

<span data-ttu-id="9c42c-122">Zbiera dane śledzenia diagnostycznego z uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="9c42c-122">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9c42c-123">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="9c42c-123">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="9c42c-124">Opcje</span><span class="sxs-lookup"><span data-stu-id="9c42c-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="9c42c-125">Proces zbierania danych śledzenia z programu.</span><span class="sxs-lookup"><span data-stu-id="9c42c-125">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="9c42c-126">Ustawia rozmiar buforu cyklicznego w pamięci (w megabajtach).</span><span class="sxs-lookup"><span data-stu-id="9c42c-126">Sets the size of the in-memory circular buffer in megabytes.</span></span> <span data-ttu-id="9c42c-127">Wartość domyślna to 256 MB.</span><span class="sxs-lookup"><span data-stu-id="9c42c-127">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="9c42c-128">Ścieżka wyjściowa zebranych danych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9c42c-128">The output path for the collected trace data.</span></span> <span data-ttu-id="9c42c-129">Jeśli nie zostanie określony, wartość domyślna to `trace.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="9c42c-129">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="9c42c-130">Rozdzielana przecinkami lista dostawców `EventPipe` do włączenia.</span><span class="sxs-lookup"><span data-stu-id="9c42c-130">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="9c42c-131">Tacy dostawcy uzupełniają dostawców implikowaną przez `--profile <profile-name>`.</span><span class="sxs-lookup"><span data-stu-id="9c42c-131">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="9c42c-132">W przypadku niespójności określonego dostawcy konfiguracja ma pierwszeństwo przed niejawną konfiguracją w profilu.</span><span class="sxs-lookup"><span data-stu-id="9c42c-132">If there's any inconsistency for a particular provider, the configuration here takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="9c42c-133">Ta lista dostawców ma postać:</span><span class="sxs-lookup"><span data-stu-id="9c42c-133">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="9c42c-134">`Provider` ma postać: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span><span class="sxs-lookup"><span data-stu-id="9c42c-134">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="9c42c-135">`KeyValueArgs` ma postać: `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="9c42c-135">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="9c42c-136">Nazwany wstępnie zdefiniowany zestaw konfiguracji dostawcy, który umożliwia zwięzłe Określanie typowych scenariuszy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9c42c-136">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="9c42c-137">Ustawia format danych wyjściowych dla konwersji pliku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9c42c-137">Sets the output format for the trace file conversion.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="9c42c-138">Konwersja dotnet-Trace</span><span class="sxs-lookup"><span data-stu-id="9c42c-138">dotnet-trace convert</span></span>

<span data-ttu-id="9c42c-139">Konwertuje ślady `nettrace` na formaty alternatywne do użycia z alternatywnymi narzędziami do analizy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9c42c-139">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9c42c-140">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="9c42c-140">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="9c42c-141">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9c42c-141">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="9c42c-142">Wejściowy plik śledzenia do przekonwertowania.</span><span class="sxs-lookup"><span data-stu-id="9c42c-142">Input trace file to be converted.</span></span> <span data-ttu-id="9c42c-143">Wartość domyślna to *Trace. Trace*.</span><span class="sxs-lookup"><span data-stu-id="9c42c-143">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="9c42c-144">Opcje</span><span class="sxs-lookup"><span data-stu-id="9c42c-144">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="9c42c-145">Ustawia format danych wyjściowych dla konwersji pliku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9c42c-145">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="9c42c-146">Nazwa pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="9c42c-146">Output filename.</span></span> <span data-ttu-id="9c42c-147">Rozszerzenie formatu docelowego zostanie dodane.</span><span class="sxs-lookup"><span data-stu-id="9c42c-147">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-list-processes"></a><span data-ttu-id="9c42c-148">dotnet-Trace list-processs</span><span class="sxs-lookup"><span data-stu-id="9c42c-148">dotnet-trace list-processes</span></span>

<span data-ttu-id="9c42c-149">Wyświetla listę procesów dotnet, które mogą być śledzone.</span><span class="sxs-lookup"><span data-stu-id="9c42c-149">Lists dotnet processes that can be traced.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9c42c-150">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="9c42c-150">Synopsis</span></span>

```console
dotnet-trace list-processes [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="9c42c-151">dotnet-lista śledzenia — profile</span><span class="sxs-lookup"><span data-stu-id="9c42c-151">dotnet-trace list-profiles</span></span>

<span data-ttu-id="9c42c-152">Wyświetla wstępnie skompilowane profile śledzenia z opisem dostawców i filtrów w poszczególnych profilach.</span><span class="sxs-lookup"><span data-stu-id="9c42c-152">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9c42c-153">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="9c42c-153">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="9c42c-154">Zbierz ślad z `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="9c42c-154">Collect a trace with `dotnet-trace`</span></span>

- <span data-ttu-id="9c42c-155">Aby zebrać ślady przy użyciu `dotnet-trace`, należy najpierw sprawdzić identyfikator procesu (PID) aplikacji .NET Core w celu zebrania śladów.</span><span class="sxs-lookup"><span data-stu-id="9c42c-155">To collect traces using `dotnet-trace`, you'll need to first, find out the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="9c42c-156">W systemie Windows dostępne są opcje, takie jak użycie Menedżera zadań lub polecenia `tasklist`.</span><span class="sxs-lookup"><span data-stu-id="9c42c-156">On Windows, there are options such as using the task manager or the `tasklist` command.</span></span>
  - <span data-ttu-id="9c42c-157">W systemie Linux prosta opcja może używać `ps` polecenie.</span><span class="sxs-lookup"><span data-stu-id="9c42c-157">On Linux, the trivial option could be using `ps` command.</span></span>

<span data-ttu-id="9c42c-158">Możesz również użyć polecenia programu [dotnet-Trace list-processs](#dotnet-trace-list-processes) , aby dowiedzieć się, jakie procesy .NET Core są uruchomione, wraz z ich numerami PID.</span><span class="sxs-lookup"><span data-stu-id="9c42c-158">You may also use the [dotnet-trace list-processes](#dotnet-trace-list-processes) command to find out what .NET Core processes are running, along with their PIDs.</span></span>

- <span data-ttu-id="9c42c-159">Następnie uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="9c42c-159">Then, run the following command:</span></span>

```console
> dotnet-trace collect --process-id <PID>

Press <Enter> to exit...
Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
```

- <span data-ttu-id="9c42c-160">Na koniec Zatrzymaj zbieranie, naciskając klawisz `<Enter>`, a `dotnet-trace` spowoduje zakończenie rejestrowania zdarzeń w pliku `trace.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="9c42c-160">Finally, stop collection by pressing the `<Enter>` key, and `dotnet-trace` will finish logging events to `trace.nettrace` file.</span></span>

## <a name="viewing-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="9c42c-161">Wyświetlanie śladu przechwytywanego z `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="9c42c-161">Viewing the trace captured from `dotnet-trace`</span></span>

<span data-ttu-id="9c42c-162">W systemie Windows pliki `.nettrace` mogą być wyświetlane w [Narzędzia PerfView](https://github.com/microsoft/perfview) na potrzeby analizy, podobnie jak ślady zbierane z użyciem ETW lub LTTng.</span><span class="sxs-lookup"><span data-stu-id="9c42c-162">On Windows, `.nettrace` files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis, just like traces collected with ETW or LTTng.</span></span> <span data-ttu-id="9c42c-163">W przypadku śladów zebranych w systemie Linux można przenieść ślad do komputera z systemem Windows, aby był wyświetlany w witrynie narzędzia PerfView.</span><span class="sxs-lookup"><span data-stu-id="9c42c-163">For traces collected on Linux, you can move the trace to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="9c42c-164">Możesz również wyświetlić ślad na komputerze z systemem Linux, zmieniając format danych wyjściowych `dotnet-trace` na `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="9c42c-164">You may also view the trace on a Linux machine by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="9c42c-165">Można zmienić format pliku wyjściowego przy użyciu opcji `-f|--format`-`-f speedscope` spowoduje, że `dotnet-trace` będzie generował plik `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="9c42c-165">You can change the output file format using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` to produce a `speedscope` file.</span></span> <span data-ttu-id="9c42c-166">Obecnie można wybrać między `nettrace` (opcja domyślna) i `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="9c42c-166">You can currently choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="9c42c-167">Pliki `Speedscope` można otwierać w <https://www.speedscope.app>.</span><span class="sxs-lookup"><span data-stu-id="9c42c-167">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="9c42c-168">Środowisko uruchomieniowe programu .NET Core generuje ślady w formacie `nettrace` i są konwertowane na speedscope (jeśli zostały określone) po zakończeniu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="9c42c-168">The .NET Core runtime generates traces in the `nettrace` format, and they're converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="9c42c-169">Ponieważ niektóre Konwersje mogą spowodować utratę danych, oryginalny plik `nettrace` jest zachowywany obok skonwertowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="9c42c-169">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="using-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="9c42c-170">Używanie `dotnet-trace` do zbierania wartości licznika w czasie</span><span class="sxs-lookup"><span data-stu-id="9c42c-170">Using `dotnet-trace` to collect counter values over time</span></span>

<span data-ttu-id="9c42c-171">Jeśli próbujesz użyć `EventCounter` do podstawowego monitorowania kondycji w ustawieniach z uwzględnieniem wydajności, takich jak środowiska produkcyjne i chcesz zbierać ślady zamiast oglądać je w czasie rzeczywistym, możesz to zrobić przy użyciu również `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="9c42c-171">If you're trying to use `EventCounter` for basic health monitoring in  performance-sensitive settings like production environments and you want to collect traces instead of watching them in real time, you can do that with `dotnet-trace` as well.</span></span>

<span data-ttu-id="9c42c-172">Jeśli na przykład chcesz zbierać wartości liczników wydajności środowiska uruchomieniowego, możesz użyć następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="9c42c-172">For example, if you want to collect runtime performance counter values, you can use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="9c42c-173">To polecenie informuje, że liczniki środowiska uruchomieniowego są raportowane co sekundę na potrzeby uproszczonego monitorowania kondycji.</span><span class="sxs-lookup"><span data-stu-id="9c42c-173">This command tells the runtime counters to be reported once every second for lightweight health monitoring.</span></span> <span data-ttu-id="9c42c-174">Zastępowanie `EventCounterIntervalSec=1` wyższą wartością (na przykład 60) umożliwia zebranie mniejszego śladu o mniejszej szczegółowości danych licznika.</span><span class="sxs-lookup"><span data-stu-id="9c42c-174">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows you to collect a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="9c42c-175">Aby wyłączyć zdarzenia środowiska uruchomieniowego w celu zmniejszenia obciążenia (i rozmiaru śledzenia), możesz użyć następującego polecenia, aby wyłączyć zdarzenia środowiska uruchomieniowego i zarządzanego profilera stosu.</span><span class="sxs-lookup"><span data-stu-id="9c42c-175">If you want to disable runtime events to reduce the overhead (and trace size) even further, you can use the following command to disable runtime events and managed stack profiler.</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

## <a name="net-providers"></a><span data-ttu-id="9c42c-176">Dostawcy .NET</span><span class="sxs-lookup"><span data-stu-id="9c42c-176">.NET Providers</span></span>

<span data-ttu-id="9c42c-177">Środowisko uruchomieniowe platformy .NET Core obsługuje następujących dostawców platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="9c42c-177">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="9c42c-178">Program .NET Core używa tych samych słów kluczowych, aby umożliwić śledzenie `Event Tracing for Windows (ETW)` i `EventPipe`.</span><span class="sxs-lookup"><span data-stu-id="9c42c-178">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="9c42c-179">Nazwa dostawcy</span><span class="sxs-lookup"><span data-stu-id="9c42c-179">Provider name</span></span>                            | <span data-ttu-id="9c42c-180">Informacje</span><span class="sxs-lookup"><span data-stu-id="9c42c-180">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="9c42c-181">Dostawca środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="9c42c-181">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="9c42c-182">Słowa kluczowe środowiska uruchomieniowego CLR</span><span class="sxs-lookup"><span data-stu-id="9c42c-182">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="9c42c-183">Dostawca uwalniania</span><span class="sxs-lookup"><span data-stu-id="9c42c-183">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="9c42c-184">Słowa kluczowe uwalniania CLR</span><span class="sxs-lookup"><span data-stu-id="9c42c-184">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="9c42c-185">Włącza przykładowy Profiler.</span><span class="sxs-lookup"><span data-stu-id="9c42c-185">Enables the sample profiler.</span></span> |
