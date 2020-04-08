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
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="881a7-103">narzędzie do analizy wydajności śledzenia dotnet</span><span class="sxs-lookup"><span data-stu-id="881a7-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="881a7-104">**Ten artykuł dotyczy:** ✔️.NET Core 3.0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="881a7-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="881a7-105">Instalowanie dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="881a7-105">Install dotnet-trace</span></span>

<span data-ttu-id="881a7-106">Zainstaluj `dotnet-trace` [pakiet NuGet](https://www.nuget.org/packages/dotnet-trace) za pomocą polecenia [instalacji narzędzia dotnet:](../tools/dotnet-tool-install.md)</span><span class="sxs-lookup"><span data-stu-id="881a7-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="881a7-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="881a7-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="881a7-108">Opis</span><span class="sxs-lookup"><span data-stu-id="881a7-108">Description</span></span>

<span data-ttu-id="881a7-109">Narzędzie: `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="881a7-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="881a7-110">Jest wieloplatformowym narzędziem .NET Core.</span><span class="sxs-lookup"><span data-stu-id="881a7-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="881a7-111">Umożliwia zbieranie śladów .NET Core uruchomionego procesu bez natywnego profilera.</span><span class="sxs-lookup"><span data-stu-id="881a7-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="881a7-112">Jest zbudowany wokół technologii `EventPipe` międzyplatformowej środowiska uruchomieniowego .NET Core.</span><span class="sxs-lookup"><span data-stu-id="881a7-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="881a7-113">Zapewnia takie samo środowisko w systemach Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="881a7-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="881a7-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="881a7-114">Options</span></span>

- **`--version`**

  <span data-ttu-id="881a7-115">Wyświetla wersję narzędzia dotnet-trace.</span><span class="sxs-lookup"><span data-stu-id="881a7-115">Displays the version of the dotnet-trace utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="881a7-116">Pokazuje pomoc wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="881a7-116">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="881a7-117">Polecenia</span><span class="sxs-lookup"><span data-stu-id="881a7-117">Commands</span></span>

| <span data-ttu-id="881a7-118">Polecenie</span><span class="sxs-lookup"><span data-stu-id="881a7-118">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="881a7-119">zbieranie śladów dotnet</span><span class="sxs-lookup"><span data-stu-id="881a7-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="881a7-120">konwersja śledzenia dotnet</span><span class="sxs-lookup"><span data-stu-id="881a7-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="881a7-121">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="881a7-121">dotnet-trace ps</span></span>](#dotnet-trace-ps) |
| [<span data-ttu-id="881a7-122">profile list śledzenia dotnet</span><span class="sxs-lookup"><span data-stu-id="881a7-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="881a7-123">zbieranie śladów dotnet</span><span class="sxs-lookup"><span data-stu-id="881a7-123">dotnet-trace collect</span></span>

<span data-ttu-id="881a7-124">Zbiera śledzenia diagnostycznego z uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="881a7-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="881a7-125">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="881a7-125">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="881a7-126">Opcje</span><span class="sxs-lookup"><span data-stu-id="881a7-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="881a7-127">Proces zbierania śledzenia z.</span><span class="sxs-lookup"><span data-stu-id="881a7-127">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="881a7-128">Ustawia rozmiar buforu kołowego w pamięci w megabajtach.</span><span class="sxs-lookup"><span data-stu-id="881a7-128">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="881a7-129">Domyślnie 256 MB.</span><span class="sxs-lookup"><span data-stu-id="881a7-129">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="881a7-130">Ścieżka wyjściowa dla zebranych danych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="881a7-130">The output path for the collected trace data.</span></span> <span data-ttu-id="881a7-131">Jeśli nie określono, `trace.nettrace`domyślnie jest to .</span><span class="sxs-lookup"><span data-stu-id="881a7-131">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="881a7-132">Lista dostawców oddzielona `EventPipe` przecinkami ma być włączona.</span><span class="sxs-lookup"><span data-stu-id="881a7-132">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="881a7-133">Dostawcy ci uzupełniają `--profile <profile-name>`wszelkie dostawców dorozumianych przez .</span><span class="sxs-lookup"><span data-stu-id="881a7-133">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="881a7-134">Jeśli istnieje jakakolwiek niespójność dla określonego dostawcy, ta konfiguracja ma pierwszeństwo przed niejawną konfiguracją z profilu.</span><span class="sxs-lookup"><span data-stu-id="881a7-134">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="881a7-135">Ta lista dostawców jest w formie:</span><span class="sxs-lookup"><span data-stu-id="881a7-135">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="881a7-136">`Provider`jest w formie: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span><span class="sxs-lookup"><span data-stu-id="881a7-136">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="881a7-137">`KeyValueArgs`jest w formie: `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="881a7-137">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="881a7-138">Nazwany wstępnie zdefiniowany zestaw konfiguracji dostawcy, który umożliwia typowe scenariusze śledzenia, które mają być określone zwięźle.</span><span class="sxs-lookup"><span data-stu-id="881a7-138">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format {NetTrace|Speedscope}`**

  <span data-ttu-id="881a7-139">Ustawia format danych wyjściowych dla konwersji pliku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="881a7-139">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="881a7-140">Wartość domyślna to `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="881a7-140">The default is `NetTrace`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="881a7-141">konwersja śledzenia dotnet</span><span class="sxs-lookup"><span data-stu-id="881a7-141">dotnet-trace convert</span></span>

<span data-ttu-id="881a7-142">Konwertuje ślady `nettrace` na alternatywne formaty do użycia z alternatywnymi narzędziami analizy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="881a7-142">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="881a7-143">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="881a7-143">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="881a7-144">Argumenty</span><span class="sxs-lookup"><span data-stu-id="881a7-144">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="881a7-145">Wejściowy plik śledzenia do konwersji.</span><span class="sxs-lookup"><span data-stu-id="881a7-145">Input trace file to be converted.</span></span> <span data-ttu-id="881a7-146">Wartość domyślna *trace.nettrace*.</span><span class="sxs-lookup"><span data-stu-id="881a7-146">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="881a7-147">Opcje</span><span class="sxs-lookup"><span data-stu-id="881a7-147">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="881a7-148">Ustawia format danych wyjściowych dla konwersji pliku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="881a7-148">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="881a7-149">Wyjściowa nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="881a7-149">Output filename.</span></span> <span data-ttu-id="881a7-150">Zostanie dodane rozszerzenie formatu docelowego.</span><span class="sxs-lookup"><span data-stu-id="881a7-150">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="881a7-151">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="881a7-151">dotnet-trace ps</span></span>

<span data-ttu-id="881a7-152">Wyświetla listę procesów dotnet, do których można dołączyć.</span><span class="sxs-lookup"><span data-stu-id="881a7-152">Lists dotnet processes that can be attached to.</span></span>

### <a name="synopsis"></a><span data-ttu-id="881a7-153">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="881a7-153">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="881a7-154">profile list śledzenia dotnet</span><span class="sxs-lookup"><span data-stu-id="881a7-154">dotnet-trace list-profiles</span></span>

<span data-ttu-id="881a7-155">Wyświetla listę wstępnie utworzonych profili śledzenia z opisem dostawców i filtrów w każdym profilu.</span><span class="sxs-lookup"><span data-stu-id="881a7-155">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="881a7-156">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="881a7-156">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="881a7-157">Zbieranie śladu za pomocą śledzenia dotnet</span><span class="sxs-lookup"><span data-stu-id="881a7-157">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="881a7-158">Aby zebrać `dotnet-trace`ślady za pomocą:</span><span class="sxs-lookup"><span data-stu-id="881a7-158">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="881a7-159">Pobierz identyfikator procesu (PID) aplikacji .NET Core do zbierania śladów.</span><span class="sxs-lookup"><span data-stu-id="881a7-159">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="881a7-160">W systemie Windows można na `tasklist` przykład użyć Menedżera zadań lub polecenia.</span><span class="sxs-lookup"><span data-stu-id="881a7-160">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="881a7-161">Na przykład w `ps` systemie Linux polecenie.</span><span class="sxs-lookup"><span data-stu-id="881a7-161">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="881a7-162">dotnet-trace ps</span><span class="sxs-lookup"><span data-stu-id="881a7-162">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="881a7-163">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="881a7-163">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="881a7-164">Poprzednie polecenie generuje dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="881a7-164">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="881a7-165">Zatrzymaj zbieranie, `<Enter>` naciskając klawisz.</span><span class="sxs-lookup"><span data-stu-id="881a7-165">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="881a7-166">`dotnet-trace`zakończy rejestrowanie zdarzeń do pliku *trace.nettrace.*</span><span class="sxs-lookup"><span data-stu-id="881a7-166">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="881a7-167">Wyświetlanie śladu przechwyconego z dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="881a7-167">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="881a7-168">W systemie Windows pliki *.nettrace* można wyświetlać na [PerfView](https://github.com/microsoft/perfview) do analizy: W przypadku śladów zebranych na innych platformach plik śledzenia można przenieść do komputera z systemem Windows, który ma być oglądany na PerfView.</span><span class="sxs-lookup"><span data-stu-id="881a7-168">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="881a7-169">W systemie Linux można wyświetlić śledzenie, zmieniając `dotnet-trace` `speedscope`format wyjściowy na .</span><span class="sxs-lookup"><span data-stu-id="881a7-169">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="881a7-170">Format pliku wyjściowego można `-f|--format` zmienić `-f speedscope` za `dotnet-trace` pomocą `speedscope` opcji - spowoduje, że plik zostanie wyprodukowany.</span><span class="sxs-lookup"><span data-stu-id="881a7-170">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="881a7-171">Można wybrać `nettrace` opcję (opcja domyślna) i `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="881a7-171">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="881a7-172">`Speedscope`można otworzyć w <https://www.speedscope.app>pliku .</span><span class="sxs-lookup"><span data-stu-id="881a7-172">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="881a7-173">Środowisko uruchomieniowe .NET Core generuje `nettrace` ślady w formacie.</span><span class="sxs-lookup"><span data-stu-id="881a7-173">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="881a7-174">Ślady są konwertowane na speedscope (jeśli określono) po zakończeniu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="881a7-174">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="881a7-175">Ponieważ niektóre konwersje mogą spowodować utratę `nettrace` danych, oryginalny plik jest zachowywany obok przekonwertowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="881a7-175">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="881a7-176">Zbieranie wartości liczników za pomocą śledzenia dotnetu w czasie</span><span class="sxs-lookup"><span data-stu-id="881a7-176">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="881a7-177">`dotnet-trace`Cna:</span><span class="sxs-lookup"><span data-stu-id="881a7-177">`dotnet-trace` can:</span></span>

* <span data-ttu-id="881a7-178">Służy `EventCounter` do podstawowego monitorowania kondycji w środowiskach wrażliwych na wydajność.</span><span class="sxs-lookup"><span data-stu-id="881a7-178">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="881a7-179">Na przykład w produkcji.</span><span class="sxs-lookup"><span data-stu-id="881a7-179">For example, in production.</span></span>
* <span data-ttu-id="881a7-180">Zbieraj ślady, aby nie trzeba było ich oglądać w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="881a7-180">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="881a7-181">Na przykład, aby zebrać wartości licznika wydajności środowiska uruchomieniowego, należy użyć następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="881a7-181">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="881a7-182">Poprzednie polecenie informuje liczniki środowiska wykonawczego do raportowania raz na sekundę dla monitorowania kondycji w stanie lekkim.</span><span class="sxs-lookup"><span data-stu-id="881a7-182">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="881a7-183">Zastąpienie `EventCounterIntervalSec=1` wyższą wartością (na przykład 60) umożliwia zbieranie mniejszego śledzenia o mniejszej szczegółowości w danych licznika.</span><span class="sxs-lookup"><span data-stu-id="881a7-183">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="881a7-184">Następujące polecenie zmniejsza obciążenie i rozmiar śledzenia więcej niż poprzedni:</span><span class="sxs-lookup"><span data-stu-id="881a7-184">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="881a7-185">Poprzednie polecenie wyłącza zdarzenia środowiska uruchomieniowego i profiler zarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="881a7-185">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="881a7-186">Dostawcy platformy .NET</span><span class="sxs-lookup"><span data-stu-id="881a7-186">.NET Providers</span></span>

<span data-ttu-id="881a7-187">Środowisko uruchomieniowe .NET Core obsługuje następujących dostawców platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="881a7-187">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="881a7-188">.NET Core używa tych samych `Event Tracing for Windows (ETW)` słów `EventPipe` kluczowych, aby włączyć zarówno i ślady.</span><span class="sxs-lookup"><span data-stu-id="881a7-188">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="881a7-189">Nazwa dostawcy</span><span class="sxs-lookup"><span data-stu-id="881a7-189">Provider name</span></span>                            | <span data-ttu-id="881a7-190">Informacje</span><span class="sxs-lookup"><span data-stu-id="881a7-190">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="881a7-191">Dostawca środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="881a7-191">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="881a7-192">Słowa kluczowe środowiska wykonawczego CLR</span><span class="sxs-lookup"><span data-stu-id="881a7-192">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="881a7-193">Dostawca wybiegiem</span><span class="sxs-lookup"><span data-stu-id="881a7-193">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="881a7-194">Clr Rundown Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="881a7-194">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="881a7-195">Włącza profiler próbki.</span><span class="sxs-lookup"><span data-stu-id="881a7-195">Enables the sample profiler.</span></span> |
