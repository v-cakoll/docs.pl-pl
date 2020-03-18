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
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="a3279-103">narzędzie dotnet-trace performance analysis utility</span><span class="sxs-lookup"><span data-stu-id="a3279-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="a3279-104">**Ten artykuł dotyczy:** ✔️ .NET Core 3.0 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="a3279-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="a3279-105">Instalowanie śledzenia dotnet</span><span class="sxs-lookup"><span data-stu-id="a3279-105">Install dotnet-trace</span></span>

<span data-ttu-id="a3279-106">Zainstaluj `dotnet-trace` [pakiet NuGet](https://www.nuget.org/packages/dotnet-trace) za pomocą polecenia [instalacji narzędzia dotnet:](../tools/dotnet-tool-install.md)</span><span class="sxs-lookup"><span data-stu-id="a3279-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="a3279-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a3279-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="a3279-108">Opis</span><span class="sxs-lookup"><span data-stu-id="a3279-108">Description</span></span>

<span data-ttu-id="a3279-109">Narzędzie: `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="a3279-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="a3279-110">Jest narzędziem .NET Core dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="a3279-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="a3279-111">Włącza kolekcję .NET Core ślady uruchomionego procesu bez profilera macierzystego.</span><span class="sxs-lookup"><span data-stu-id="a3279-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="a3279-112">Jest zbudowany wokół technologii `EventPipe` wieloplatformowej w czasie wykonywania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a3279-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="a3279-113">Zapewnia takie samo środowisko w systemie Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="a3279-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="a3279-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="a3279-114">Options</span></span>

- **`--version`**

  <span data-ttu-id="a3279-115">Wyświetla wersję narzędzia dotnet-counters.</span><span class="sxs-lookup"><span data-stu-id="a3279-115">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="a3279-116">Pokazuje pomoc wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="a3279-116">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="a3279-117">Polecenia</span><span class="sxs-lookup"><span data-stu-id="a3279-117">Commands</span></span>

| <span data-ttu-id="a3279-118">Polecenie</span><span class="sxs-lookup"><span data-stu-id="a3279-118">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="a3279-119">dotnet-trace zbierać</span><span class="sxs-lookup"><span data-stu-id="a3279-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="a3279-120">konwersja dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="a3279-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="a3279-121">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="a3279-121">dotnet-trace ps</span></span>](#dotnet-trace-ps) |
| [<span data-ttu-id="a3279-122">profile listy śladów dotnet</span><span class="sxs-lookup"><span data-stu-id="a3279-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="a3279-123">dotnet-trace zbierać</span><span class="sxs-lookup"><span data-stu-id="a3279-123">dotnet-trace collect</span></span>

<span data-ttu-id="a3279-124">Zbiera śledzenia diagnostycznego z uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="a3279-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="a3279-125">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a3279-125">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="a3279-126">Opcje</span><span class="sxs-lookup"><span data-stu-id="a3279-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="a3279-127">Proces zbierania śladu z.</span><span class="sxs-lookup"><span data-stu-id="a3279-127">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="a3279-128">Ustawia rozmiar buforu kołowego w pamięci w megabajtach.</span><span class="sxs-lookup"><span data-stu-id="a3279-128">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="a3279-129">Domyślnie 256 MB.</span><span class="sxs-lookup"><span data-stu-id="a3279-129">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="a3279-130">Ścieżka danych wyjściowych dla zebranych danych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a3279-130">The output path for the collected trace data.</span></span> <span data-ttu-id="a3279-131">Jeśli nie określono, domyślnie . `trace.nettrace`</span><span class="sxs-lookup"><span data-stu-id="a3279-131">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="a3279-132">Lista `EventPipe` dostawców oddzielonych przecinkami, która ma być włączona.</span><span class="sxs-lookup"><span data-stu-id="a3279-132">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="a3279-133">Dostawcy ci uzupełniają dostawców `--profile <profile-name>`dorozumianych przez .</span><span class="sxs-lookup"><span data-stu-id="a3279-133">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="a3279-134">Jeśli istnieje jakakolwiek niespójność dla określonego dostawcy, ta konfiguracja ma pierwszeństwo przed niejawną konfiguracją z profilu.</span><span class="sxs-lookup"><span data-stu-id="a3279-134">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="a3279-135">Ta lista dostawców jest w formie:</span><span class="sxs-lookup"><span data-stu-id="a3279-135">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="a3279-136">`Provider`jest w formie: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span><span class="sxs-lookup"><span data-stu-id="a3279-136">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="a3279-137">`KeyValueArgs`jest w formie: `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="a3279-137">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="a3279-138">Nazwany wstępnie zdefiniowany zestaw konfiguracji dostawcy, który umożliwia typowe scenariusze śledzenia, które mają być określone zwięźle.</span><span class="sxs-lookup"><span data-stu-id="a3279-138">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format {NetTrace|Speedscope}`**

  <span data-ttu-id="a3279-139">Ustawia format wyjściowy konwersji pliku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a3279-139">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="a3279-140">Wartość domyślna to `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="a3279-140">The default is `NetTrace`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="a3279-141">konwersja dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="a3279-141">dotnet-trace convert</span></span>

<span data-ttu-id="a3279-142">Konwertuje `nettrace` ślady na alternatywne formaty do użytku z alternatywnymi narzędziami do analizy śladów.</span><span class="sxs-lookup"><span data-stu-id="a3279-142">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="a3279-143">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a3279-143">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="a3279-144">Argumenty</span><span class="sxs-lookup"><span data-stu-id="a3279-144">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="a3279-145">Wejściowy plik śledzenia do przekonwertowania.</span><span class="sxs-lookup"><span data-stu-id="a3279-145">Input trace file to be converted.</span></span> <span data-ttu-id="a3279-146">Domyślnie *trace.nettrace*.</span><span class="sxs-lookup"><span data-stu-id="a3279-146">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="a3279-147">Opcje</span><span class="sxs-lookup"><span data-stu-id="a3279-147">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="a3279-148">Ustawia format wyjściowy konwersji pliku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a3279-148">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="a3279-149">Nazwa pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="a3279-149">Output filename.</span></span> <span data-ttu-id="a3279-150">Zostanie dodane rozszerzenie formatu docelowego.</span><span class="sxs-lookup"><span data-stu-id="a3279-150">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="a3279-151">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="a3279-151">dotnet-trace ps</span></span>

<span data-ttu-id="a3279-152">Wyświetla listę procesów dotnet, do których można dołączyć.</span><span class="sxs-lookup"><span data-stu-id="a3279-152">Lists dotnet processes that can be attached to.</span></span>

### <a name="synopsis"></a><span data-ttu-id="a3279-153">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a3279-153">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="a3279-154">profile listy śladów dotnet</span><span class="sxs-lookup"><span data-stu-id="a3279-154">dotnet-trace list-profiles</span></span>

<span data-ttu-id="a3279-155">Wyświetla listę wstępnie utworzonych profili śledzenia z opisem dostawców i filtrów w każdym profilu.</span><span class="sxs-lookup"><span data-stu-id="a3279-155">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="a3279-156">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a3279-156">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="a3279-157">Zbieranie śladu za pomocą śladu dotnet</span><span class="sxs-lookup"><span data-stu-id="a3279-157">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="a3279-158">Aby zebrać `dotnet-trace`ślady za pomocą:</span><span class="sxs-lookup"><span data-stu-id="a3279-158">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="a3279-159">Pobierz identyfikator procesu (PID) aplikacji .NET Core, aby zbierać ślady.</span><span class="sxs-lookup"><span data-stu-id="a3279-159">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="a3279-160">W systemie Windows można na `tasklist` przykład użyć Menedżera zadań lub polecenia.</span><span class="sxs-lookup"><span data-stu-id="a3279-160">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="a3279-161">Na przykład w `ps` systemie Linux polecenie.</span><span class="sxs-lookup"><span data-stu-id="a3279-161">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="a3279-162">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="a3279-162">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="a3279-163">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="a3279-163">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="a3279-164">Poprzednie polecenie generuje dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="a3279-164">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="a3279-165">Zatrzymaj zbieranie, `<Enter>` naciskając klawisz.</span><span class="sxs-lookup"><span data-stu-id="a3279-165">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="a3279-166">`dotnet-trace`zakończy rejestrowanie zdarzeń do pliku *trace.nettrace.*</span><span class="sxs-lookup"><span data-stu-id="a3279-166">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="a3279-167">Wyświetlanie śledzenia przechwyconego ze śledzenia dotnetu</span><span class="sxs-lookup"><span data-stu-id="a3279-167">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="a3279-168">W systemie Windows pliki *.nettrace* można przeglądać na [PerfView](https://github.com/microsoft/perfview) do analizy: W przypadku śladów zebranych na innych platformach plik śledzenia można przenieść na komputer z systemem Windows, który ma być oglądany na PerfView.</span><span class="sxs-lookup"><span data-stu-id="a3279-168">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="a3279-169">W systemie Linux śledzenie można wyświetlić, zmieniając `dotnet-trace` `speedscope`format wyjściowy na .</span><span class="sxs-lookup"><span data-stu-id="a3279-169">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="a3279-170">Format pliku wyjściowego można `-f|--format` zmienić `-f speedscope` za `dotnet-trace` pomocą `speedscope` opcji - spowoduje, że stworzy plik.</span><span class="sxs-lookup"><span data-stu-id="a3279-170">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="a3279-171">Możesz wybrać `nettrace` między (opcja domyślna) i `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="a3279-171">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="a3279-172">`Speedscope`pliki można otworzyć <https://www.speedscope.app>w .</span><span class="sxs-lookup"><span data-stu-id="a3279-172">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="a3279-173">Program runtime .NET Core generuje `nettrace` ślady w formacie.</span><span class="sxs-lookup"><span data-stu-id="a3279-173">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="a3279-174">Ślady są konwertowane na speedscope (jeśli określono) po zakończeniu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a3279-174">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="a3279-175">Ponieważ niektóre konwersje mogą spowodować utratę `nettrace` danych, oryginalny plik jest zachowywany obok przekonwertowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="a3279-175">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="a3279-176">Użyj śledzenia dotnetdo zbierania wartości liczników w czasie</span><span class="sxs-lookup"><span data-stu-id="a3279-176">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="a3279-177">`dotnet-trace`Cna:</span><span class="sxs-lookup"><span data-stu-id="a3279-177">`dotnet-trace` can:</span></span>

* <span data-ttu-id="a3279-178">Służy `EventCounter` do podstawowego monitorowania kondycji w środowiskach wrażliwych na wydajność.</span><span class="sxs-lookup"><span data-stu-id="a3279-178">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="a3279-179">Na przykład w produkcji.</span><span class="sxs-lookup"><span data-stu-id="a3279-179">For example, in production.</span></span>
* <span data-ttu-id="a3279-180">Zbieraj ślady, aby nie były oglądane w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="a3279-180">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="a3279-181">Na przykład, aby zbierać wartości licznika wydajności czasu wykonywania, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="a3279-181">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="a3279-182">Poprzednie polecenie informuje liczniki czasu wykonywania do raportowania raz na sekundę do monitorowania kondycji lekki.</span><span class="sxs-lookup"><span data-stu-id="a3279-182">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="a3279-183">Zastąpienie `EventCounterIntervalSec=1` wyższą wartością (na przykład 60) umożliwia zbieranie mniejszego śledzenia o mniejszej szczegółowości w danych licznika.</span><span class="sxs-lookup"><span data-stu-id="a3279-183">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="a3279-184">Następujące polecenie zmniejsza obciążenie i rozmiar śledzenia większy niż poprzedni:</span><span class="sxs-lookup"><span data-stu-id="a3279-184">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="a3279-185">Poprzednie polecenie wyłącza zdarzenia w czasie wykonywania i zarządzany profiler stosu.</span><span class="sxs-lookup"><span data-stu-id="a3279-185">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="a3279-186">Dostawcy .NET</span><span class="sxs-lookup"><span data-stu-id="a3279-186">.NET Providers</span></span>

<span data-ttu-id="a3279-187">Program runtime .NET Core obsługuje następujących dostawców .NET.</span><span class="sxs-lookup"><span data-stu-id="a3279-187">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="a3279-188">.NET Core używa tych samych `Event Tracing for Windows (ETW)` `EventPipe` słów kluczowych, aby włączyć zarówno i śledzenia.</span><span class="sxs-lookup"><span data-stu-id="a3279-188">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="a3279-189">Nazwa dostawcy</span><span class="sxs-lookup"><span data-stu-id="a3279-189">Provider name</span></span>                            | <span data-ttu-id="a3279-190">Informacje</span><span class="sxs-lookup"><span data-stu-id="a3279-190">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="a3279-191">Dostawca czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="a3279-191">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="a3279-192">Słowa kluczowe w czasie wykonywania CLR</span><span class="sxs-lookup"><span data-stu-id="a3279-192">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="a3279-193">Dostawca wybiegu</span><span class="sxs-lookup"><span data-stu-id="a3279-193">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="a3279-194">Słowa kluczowe rozkładu CLR</span><span class="sxs-lookup"><span data-stu-id="a3279-194">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="a3279-195">Włącza profiler próbki.</span><span class="sxs-lookup"><span data-stu-id="a3279-195">Enables the sample profiler.</span></span> |
