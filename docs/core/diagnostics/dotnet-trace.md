---
title: dotnet-Trace Tool-.NET Core
description: Instalowanie i używanie narzędzia wiersza polecenia do śledzenia dotnet.
ms.date: 11/21/2019
ms.openlocfilehash: 64c931db5a18659707e832aaca910cfbbd6823c0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714436"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="486a7-103">Narzędzie do analizy wydajności śledzenia dotnet</span><span class="sxs-lookup"><span data-stu-id="486a7-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="486a7-104">**Ten artykuł dotyczy:** ✓ .net Core 3,0 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="486a7-104">**This article applies to:** ✓ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="486a7-105">Zainstaluj program dotnet-Trace</span><span class="sxs-lookup"><span data-stu-id="486a7-105">Install dotnet-trace</span></span>

<span data-ttu-id="486a7-106">Zainstaluj `dotnet-trace` [pakiet NuGet](https://www.nuget.org/packages/dotnet-trace) za pomocą polecenia [instalacji narzędzia dotnet](../tools/dotnet-tool-install.md) :</span><span class="sxs-lookup"><span data-stu-id="486a7-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="486a7-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="486a7-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="486a7-108">Opis</span><span class="sxs-lookup"><span data-stu-id="486a7-108">Description</span></span>

<span data-ttu-id="486a7-109">Narzędzie `dotnet-trace`:</span><span class="sxs-lookup"><span data-stu-id="486a7-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="486a7-110">Program to międzyplatformowe narzędzie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="486a7-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="486a7-111">Włącza zbieranie śladów .NET Core działającego procesu bez natywnego profilera.</span><span class="sxs-lookup"><span data-stu-id="486a7-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="486a7-112">Jest zbudowany wokół międzyplatformowej technologii `EventPipe` środowiska uruchomieniowego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="486a7-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="486a7-113">Zapewnia takie samo środowisko w systemach Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="486a7-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="486a7-114">Opcje</span><span class="sxs-lookup"><span data-stu-id="486a7-114">Options</span></span>

- **`--version`**  

  <span data-ttu-id="486a7-115">Wyświetla wersję narzędzia dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="486a7-115">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="486a7-116">Wyświetla pomoc w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="486a7-116">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="486a7-117">Polecenia</span><span class="sxs-lookup"><span data-stu-id="486a7-117">Commands</span></span>

| <span data-ttu-id="486a7-118">Polecenie</span><span class="sxs-lookup"><span data-stu-id="486a7-118">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="486a7-119">zbieranie danych śledzenia dotnet</span><span class="sxs-lookup"><span data-stu-id="486a7-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="486a7-120">Konwersja dotnet-Trace</span><span class="sxs-lookup"><span data-stu-id="486a7-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="486a7-121">dotnet-Trace — śledzenie</span><span class="sxs-lookup"><span data-stu-id="486a7-121">dotnet-trace ps</span></span>](#dotnet-trace-ps) |
| [<span data-ttu-id="486a7-122">dotnet-lista śledzenia — profile</span><span class="sxs-lookup"><span data-stu-id="486a7-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="486a7-123">zbieranie danych śledzenia dotnet</span><span class="sxs-lookup"><span data-stu-id="486a7-123">dotnet-trace collect</span></span>

<span data-ttu-id="486a7-124">Zbiera dane śledzenia diagnostycznego z uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="486a7-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="486a7-125">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="486a7-125">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="486a7-126">Opcje</span><span class="sxs-lookup"><span data-stu-id="486a7-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="486a7-127">Proces zbierania danych śledzenia z programu.</span><span class="sxs-lookup"><span data-stu-id="486a7-127">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="486a7-128">Ustawia rozmiar buforu cyklicznego w pamięci (w megabajtach).</span><span class="sxs-lookup"><span data-stu-id="486a7-128">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="486a7-129">Wartość domyślna to 256 MB.</span><span class="sxs-lookup"><span data-stu-id="486a7-129">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="486a7-130">Ścieżka wyjściowa zebranych danych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="486a7-130">The output path for the collected trace data.</span></span> <span data-ttu-id="486a7-131">Jeśli nie zostanie określony, wartością domyślną będzie `trace.nettrace`.</span><span class="sxs-lookup"><span data-stu-id="486a7-131">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="486a7-132">Rozdzielana przecinkami lista dostawców `EventPipe`, które mają być włączone.</span><span class="sxs-lookup"><span data-stu-id="486a7-132">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="486a7-133">Tacy dostawcy uzupełniają dostawców implikowaną przez `--profile <profile-name>`.</span><span class="sxs-lookup"><span data-stu-id="486a7-133">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="486a7-134">W przypadku niespójności określonego dostawcy ta konfiguracja ma pierwszeństwo przed niejawną konfiguracją w profilu.</span><span class="sxs-lookup"><span data-stu-id="486a7-134">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="486a7-135">Ta lista dostawców ma postać:</span><span class="sxs-lookup"><span data-stu-id="486a7-135">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="486a7-136">`Provider` ma postać: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span><span class="sxs-lookup"><span data-stu-id="486a7-136">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="486a7-137">`KeyValueArgs` ma postać: `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="486a7-137">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="486a7-138">Nazwany wstępnie zdefiniowany zestaw konfiguracji dostawcy, który umożliwia zwięzłe Określanie typowych scenariuszy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="486a7-138">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format {NetTrace|Speedscope}`**

  <span data-ttu-id="486a7-139">Ustawia format danych wyjściowych dla konwersji pliku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="486a7-139">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="486a7-140">Wartość domyślna to `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="486a7-140">The default is `NetTrace`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="486a7-141">Konwersja dotnet-Trace</span><span class="sxs-lookup"><span data-stu-id="486a7-141">dotnet-trace convert</span></span>

<span data-ttu-id="486a7-142">Konwertuje `nettrace` ślady na formaty alternatywne do użycia z alternatywnymi narzędziami do analizy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="486a7-142">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="486a7-143">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="486a7-143">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="486a7-144">Argumenty</span><span class="sxs-lookup"><span data-stu-id="486a7-144">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="486a7-145">Wejściowy plik śledzenia do przekonwertowania.</span><span class="sxs-lookup"><span data-stu-id="486a7-145">Input trace file to be converted.</span></span> <span data-ttu-id="486a7-146">Wartość domyślna to *Trace. Trace*.</span><span class="sxs-lookup"><span data-stu-id="486a7-146">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="486a7-147">Opcje</span><span class="sxs-lookup"><span data-stu-id="486a7-147">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="486a7-148">Ustawia format danych wyjściowych dla konwersji pliku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="486a7-148">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="486a7-149">Nazwa pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="486a7-149">Output filename.</span></span> <span data-ttu-id="486a7-150">Rozszerzenie formatu docelowego zostanie dodane.</span><span class="sxs-lookup"><span data-stu-id="486a7-150">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="486a7-151">dotnet-Trace — śledzenie</span><span class="sxs-lookup"><span data-stu-id="486a7-151">dotnet-trace ps</span></span>

<span data-ttu-id="486a7-152">Wyświetla listę procesów dotnet, które mogą być dołączone do programu.</span><span class="sxs-lookup"><span data-stu-id="486a7-152">Lists dotnet processes that can be attached to.</span></span>

### <a name="synopsis"></a><span data-ttu-id="486a7-153">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="486a7-153">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="486a7-154">dotnet-lista śledzenia — profile</span><span class="sxs-lookup"><span data-stu-id="486a7-154">dotnet-trace list-profiles</span></span>

<span data-ttu-id="486a7-155">Wyświetla wstępnie skompilowane profile śledzenia z opisem dostawców i filtrów w poszczególnych profilach.</span><span class="sxs-lookup"><span data-stu-id="486a7-155">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="486a7-156">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="486a7-156">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="486a7-157">Zbieranie śledzenia przy użyciu funkcji monitorowania dotnet</span><span class="sxs-lookup"><span data-stu-id="486a7-157">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="486a7-158">Aby zebrać ślady przy użyciu `dotnet-trace`:</span><span class="sxs-lookup"><span data-stu-id="486a7-158">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="486a7-159">Pobierz identyfikator procesu (PID) aplikacji .NET Core, aby zebrać ślady z programu.</span><span class="sxs-lookup"><span data-stu-id="486a7-159">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="486a7-160">W systemie Windows można użyć Menedżera zadań lub polecenia `tasklist`, na przykład.</span><span class="sxs-lookup"><span data-stu-id="486a7-160">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="486a7-161">Na przykład w systemie Linux polecenie `ps`.</span><span class="sxs-lookup"><span data-stu-id="486a7-161">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="486a7-162">dotnet-Trace — śledzenie</span><span class="sxs-lookup"><span data-stu-id="486a7-162">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="486a7-163">Uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="486a7-163">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="486a7-164">Poprzednie polecenie generuje dane wyjściowe podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="486a7-164">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="486a7-165">Zatrzymaj zbieranie, naciskając klawisz `<Enter>`.</span><span class="sxs-lookup"><span data-stu-id="486a7-165">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="486a7-166">`dotnet-trace` zakończy rejestrowanie zdarzeń w pliku *Trace. webtrace* .</span><span class="sxs-lookup"><span data-stu-id="486a7-166">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="486a7-167">Wyświetl śledzenie przechwycone przez śledzenie dotnet</span><span class="sxs-lookup"><span data-stu-id="486a7-167">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="486a7-168">W systemie Windows można przeglądać pliki *śledzenia* w usłudze [Narzędzia PerfView](https://github.com/microsoft/perfview) for Analysis: w przypadku śladów zebranych na innych platformach plik śledzenia można przenieść na komputer z systemem Windows, który ma być wyświetlany na narzędzia PerfView.</span><span class="sxs-lookup"><span data-stu-id="486a7-168">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="486a7-169">W systemie Linux śledzenie można wyświetlić, zmieniając format danych wyjściowych `dotnet-trace` na `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="486a7-169">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="486a7-170">Format pliku wyjściowego można zmienić przy użyciu opcji `-f|--format` — `-f speedscope` `dotnet-trace` utworzyć plik `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="486a7-170">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="486a7-171">Można wybrać między `nettrace` (opcja domyślna) i `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="486a7-171">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="486a7-172">Pliki `Speedscope` można otwierać w <https://www.speedscope.app>.</span><span class="sxs-lookup"><span data-stu-id="486a7-172">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="486a7-173">Środowisko uruchomieniowe programu .NET Core generuje ślady w formacie `nettrace`.</span><span class="sxs-lookup"><span data-stu-id="486a7-173">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="486a7-174">Ślady są konwertowane na speedscope (jeśli zostaną określone) po zakończeniu śledzenia.</span><span class="sxs-lookup"><span data-stu-id="486a7-174">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="486a7-175">Ponieważ niektóre Konwersje mogą spowodować utratę danych, oryginalny plik `nettrace` zostanie zachowany obok skonwertowanego pliku.</span><span class="sxs-lookup"><span data-stu-id="486a7-175">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="486a7-176">Używanie funkcji monitorowania dotnet do zbierania wartości licznika w czasie</span><span class="sxs-lookup"><span data-stu-id="486a7-176">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="486a7-177">`dotnet-trace` może:</span><span class="sxs-lookup"><span data-stu-id="486a7-177">`dotnet-trace` can:</span></span>

* <span data-ttu-id="486a7-178">Użyj `EventCounter` na potrzeby podstawowego monitorowania kondycji w środowiskach z uwzględnieniem wydajności.</span><span class="sxs-lookup"><span data-stu-id="486a7-178">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="486a7-179">Na przykład w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="486a7-179">For example, in production.</span></span>
* <span data-ttu-id="486a7-180">Zbieraj ślady, aby nie trzeba było ich wyświetlać w czasie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="486a7-180">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="486a7-181">Na przykład, aby zbierać wartości liczników wydajności środowiska uruchomieniowego, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="486a7-181">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="486a7-182">Poprzednie polecenie instruuje liczniki środowiska uruchomieniowego do raportowania co sekundę w przypadku uproszczonego monitorowania kondycji.</span><span class="sxs-lookup"><span data-stu-id="486a7-182">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="486a7-183">Zastępowanie `EventCounterIntervalSec=1` wartością wyższą (na przykład 60) umożliwia zbieranie mniejszych śladów o mniejszej szczegółowości danych licznika.</span><span class="sxs-lookup"><span data-stu-id="486a7-183">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="486a7-184">Następujące polecenie zmniejsza obciążenie i rozmiar śladu więcej niż poprzedni:</span><span class="sxs-lookup"><span data-stu-id="486a7-184">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="486a7-185">Poprzednie polecenie powoduje wyłączenie zdarzeń środowiska uruchomieniowego i zarządzanego profilera stosu.</span><span class="sxs-lookup"><span data-stu-id="486a7-185">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="486a7-186">Dostawcy .NET</span><span class="sxs-lookup"><span data-stu-id="486a7-186">.NET Providers</span></span>

<span data-ttu-id="486a7-187">Środowisko uruchomieniowe platformy .NET Core obsługuje następujących dostawców platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="486a7-187">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="486a7-188">Program .NET Core używa tych samych słów kluczowych, aby umożliwić śledzenie zarówno `Event Tracing for Windows (ETW)`, jak i `EventPipe`.</span><span class="sxs-lookup"><span data-stu-id="486a7-188">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="486a7-189">Nazwa dostawcy</span><span class="sxs-lookup"><span data-stu-id="486a7-189">Provider name</span></span>                            | <span data-ttu-id="486a7-190">Informacje programu</span><span class="sxs-lookup"><span data-stu-id="486a7-190">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="486a7-191">Dostawca środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="486a7-191">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="486a7-192">Słowa kluczowe środowiska uruchomieniowego CLR</span><span class="sxs-lookup"><span data-stu-id="486a7-192">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="486a7-193">Dostawca uwalniania</span><span class="sxs-lookup"><span data-stu-id="486a7-193">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="486a7-194">Słowa kluczowe uwalniania CLR</span><span class="sxs-lookup"><span data-stu-id="486a7-194">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="486a7-195">Włącza przykładowy Profiler.</span><span class="sxs-lookup"><span data-stu-id="486a7-195">Enables the sample profiler.</span></span> |
