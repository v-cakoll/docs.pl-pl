---
title: Debugowanie wysokiego użycia procesora CPU — .NET Core
description: Samouczek, który przeprowadzi Cię przez debugowanie wysokiego użycia procesora CPU w programie .NET Core.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: e69585d0eb6f04bf37d0c023a1956be62c2a1cf3
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86926418"
---
# <a name="debug-high-cpu-usage-in-net-core"></a><span data-ttu-id="5f208-103">Debugowanie wysokiego użycia procesora CPU w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="5f208-103">Debug high CPU usage in .NET Core</span></span>

<span data-ttu-id="5f208-104">**Ten artykuł ma zastosowanie do: ✔️** .net Core 3,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="5f208-104">**This article applies to: ✔️** .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="5f208-105">W tym samouczku dowiesz się, jak debugować nadmierne scenariusze użycia procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="5f208-105">In this tutorial, you'll learn how to debug an excessive CPU usage scenario.</span></span> <span data-ttu-id="5f208-106">Korzystając z podanego ASP.NET Core przykładowego repozytorium kodu źródłowego [aplikacji sieci Web](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) , można przypadkowo zaistnieć zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="5f208-106">Using the provided example [ASP.NET Core web app](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) source code repository, you can cause a deadlock intentionally.</span></span> <span data-ttu-id="5f208-107">Punkt końcowy będzie miał Rozwieszanie i kumulację wątków.</span><span class="sxs-lookup"><span data-stu-id="5f208-107">The endpoint will experience a hang and thread accumulation.</span></span> <span data-ttu-id="5f208-108">Dowiesz się, jak za pomocą różnych narzędzi można zdiagnozować ten scenariusz za pomocą kilku kluczowych fragmentów danych diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="5f208-108">You'll learn how you can use various tools to diagnose this scenario with several key pieces of diagnostics data.</span></span>

<span data-ttu-id="5f208-109">W tym samouczku wykonasz następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5f208-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="5f208-110">Zbadaj duże użycie procesora CPU</span><span class="sxs-lookup"><span data-stu-id="5f208-110">Investigate high CPU usage</span></span>
> - <span data-ttu-id="5f208-111">Określanie użycia procesora przy użyciu [liczników dotnet](dotnet-counters.md)</span><span class="sxs-lookup"><span data-stu-id="5f208-111">Determine CPU usage with [dotnet-counters](dotnet-counters.md)</span></span>
> - <span data-ttu-id="5f208-112">Użyj [śledzenia dotnet](dotnet-trace.md) do generowania śladu</span><span class="sxs-lookup"><span data-stu-id="5f208-112">Use [dotnet-trace](dotnet-trace.md) for trace generation</span></span>
> - <span data-ttu-id="5f208-113">Wydajność profilowania w programie narzędzia PerfView</span><span class="sxs-lookup"><span data-stu-id="5f208-113">Profile performance in PerfView</span></span>
> - <span data-ttu-id="5f208-114">Diagnozowanie i rozwiązywanie nadmiernego użycia procesora CPU</span><span class="sxs-lookup"><span data-stu-id="5f208-114">Diagnose and solve excessive CPU usage</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5f208-115">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="5f208-115">Prerequisites</span></span>

<span data-ttu-id="5f208-116">Samouczek używa:</span><span class="sxs-lookup"><span data-stu-id="5f208-116">The tutorial uses:</span></span>

- <span data-ttu-id="5f208-117">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) lub nowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="5f208-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="5f208-118">[Przykładowy obiekt docelowy debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) , aby wyzwolić scenariusz.</span><span class="sxs-lookup"><span data-stu-id="5f208-118">[Sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) to trigger the scenario.</span></span>
- <span data-ttu-id="5f208-119">[dotnet-Trace](dotnet-trace.md) do wyświetlania listy procesów i generowania profilu.</span><span class="sxs-lookup"><span data-stu-id="5f208-119">[dotnet-trace](dotnet-trace.md) to list processes and generate a profile.</span></span>
- <span data-ttu-id="5f208-120">[dotnet-Counters](dotnet-counters.md) do monitorowania użycia procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="5f208-120">[dotnet-counters](dotnet-counters.md) to monitor cpu usage.</span></span>

## <a name="cpu-counters"></a><span data-ttu-id="5f208-121">Liczniki procesora CPU</span><span class="sxs-lookup"><span data-stu-id="5f208-121">CPU counters</span></span>

<span data-ttu-id="5f208-122">Przed próbą zebrania danych diagnostycznych należy obserwować wysoki poziom procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="5f208-122">Before attempting to collect diagnostics data, you need to observe a high CPU condition.</span></span> <span data-ttu-id="5f208-123">Uruchom [przykładową aplikację](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) przy użyciu następującego polecenia w katalogu głównym projektu.</span><span class="sxs-lookup"><span data-stu-id="5f208-123">Run the [sample application](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) using the following command from the project root directory.</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="5f208-124">Aby znaleźć identyfikator procesu, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="5f208-124">To find the process ID, use the following command:</span></span>

```dotnetcli
dotnet-trace ps
```

<span data-ttu-id="5f208-125">Zanotuj identyfikator procesu z danych wyjściowych polecenia.</span><span class="sxs-lookup"><span data-stu-id="5f208-125">Take note of the process ID from your command output.</span></span> <span data-ttu-id="5f208-126">Nasz identyfikator procesu został utworzony `22884` , ale będzie się różnić.</span><span class="sxs-lookup"><span data-stu-id="5f208-126">Our process ID was `22884`, but yours will be different.</span></span> <span data-ttu-id="5f208-127">Aby sprawdzić bieżące użycie procesora, użyj polecenia narzędzia [dotnet-Counters](dotnet-counters.md) :</span><span class="sxs-lookup"><span data-stu-id="5f208-127">To check the current CPU usage, use the [dotnet-counters](dotnet-counters.md) tool command:</span></span>

```dotnetcli
dotnet-counters monitor --refresh-interval 1 -p 22884
```

<span data-ttu-id="5f208-128">`refresh-interval`Jest to liczba sekund między wartościami procesora sondowania licznika.</span><span class="sxs-lookup"><span data-stu-id="5f208-128">The `refresh-interval` is the number of seconds between the counter polling CPU values.</span></span> <span data-ttu-id="5f208-129">Dane wyjściowe będą podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="5f208-129">The output should be similar to the following:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    % Time in GC since last GC (%)                         0
    Allocation Rate / 1 sec (B)                            0
    CPU Usage (%)                                          0
    Exception Count / 1 sec                                0
    GC Heap Size (MB)                                      4
    Gen 0 GC Count / 60 sec                                0
    Gen 0 Size (B)                                         0
    Gen 1 GC Count / 60 sec                                0
    Gen 1 Size (B)                                         0
    Gen 2 GC Count / 60 sec                                0
    Gen 2 Size (B)                                         0
    LOH Size (B)                                           0
    Monitor Lock Contention Count / 1 sec                  0
    Number of Active Timers                                1
    Number of Assemblies Loaded                          140
    ThreadPool Completed Work Item Count / 1 sec           3
    ThreadPool Queue Length                                0
    ThreadPool Thread Count                                7
    Working Set (MB)                                      63
```

<span data-ttu-id="5f208-130">Gdy aplikacja sieci Web działa natychmiast po uruchomieniu, procesor CPU nie jest zużywany w ogóle i jest raportowany pod adresem `0%` .</span><span class="sxs-lookup"><span data-stu-id="5f208-130">With the web app running, immediately after startup, the CPU isn't being consumed at all and is reported at `0%`.</span></span> <span data-ttu-id="5f208-131">Przejdź do `api/diagscenario/highcpu` trasy `60000` jako parametr trasy:</span><span class="sxs-lookup"><span data-stu-id="5f208-131">Navigate to the `api/diagscenario/highcpu` route with `60000` as the route parameter:</span></span>

[https://localhost:5001/api/diagscenario/highcpu/60000](https://localhost:5001/api/diagscenario/highcpu/60000)

<span data-ttu-id="5f208-132">Teraz ponownie uruchom polecenie [dotnet-Counters](dotnet-counters.md) .</span><span class="sxs-lookup"><span data-stu-id="5f208-132">Now, rerun the [dotnet-counters](dotnet-counters.md) command.</span></span> <span data-ttu-id="5f208-133">Aby monitorować tylko `cpu-usage` , określ `System.Runtime[cpu-usage]` jako część polecenia.</span><span class="sxs-lookup"><span data-stu-id="5f208-133">To monitor just the `cpu-usage`, specify `System.Runtime[cpu-usage]` as part of the command.</span></span>

```dotnetcli
dotnet-counters monitor System.Runtime[cpu-usage] -p 22884 --refresh-interval 1
```

<span data-ttu-id="5f208-134">Powinno zostać wyświetlone zwiększenie użycia procesora CPU, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="5f208-134">You should see an increase in CPU usage as shown below:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    CPU Usage (%)                                         25
```

<span data-ttu-id="5f208-135">Przez cały czas trwania żądania użycie procesora CPU zostanie aktywowane na około 25%.</span><span class="sxs-lookup"><span data-stu-id="5f208-135">Throughout the duration of the request, the CPU usage will hover around 25% .</span></span> <span data-ttu-id="5f208-136">W zależności od komputera hosta należy oczekiwać różnego użycia procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="5f208-136">Depending on the host machine, expect varying CPU usage.</span></span>

> [!TIP]
> <span data-ttu-id="5f208-137">Aby wizualizować nawet wyższe użycie procesora CPU, można jednocześnie korzystać z tego punktu końcowego na wielu kartach przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="5f208-137">To visualize an even higher CPU usage, you can exercise this endpoint in multiple browser tabs simultaneously.</span></span>

<span data-ttu-id="5f208-138">W tym momencie można bezpiecznie wypowiedzieć, że procesor CPU jest uruchomiony na wyższym poziomie niż oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="5f208-138">At this point, you can safely say the CPU is running higher than you expect.</span></span>

## <a name="trace-generation"></a><span data-ttu-id="5f208-139">Generowanie śladu</span><span class="sxs-lookup"><span data-stu-id="5f208-139">Trace generation</span></span>

<span data-ttu-id="5f208-140">Podczas analizowania powolnego żądania potrzebne jest narzędzie diagnostyczne, które może zapewnić wgląd w to, co robi kod.</span><span class="sxs-lookup"><span data-stu-id="5f208-140">When analyzing a slow request, you need a diagnostics tool that can provide insights into what the code is doing.</span></span> <span data-ttu-id="5f208-141">Typowym wyborem jest Profiler, a istnieją różne opcje profilera do wyboru.</span><span class="sxs-lookup"><span data-stu-id="5f208-141">The usual choice is a profiler, and there are different profiler options to choose from.</span></span>

### <a name="linux"></a>[<span data-ttu-id="5f208-142">Linux</span><span class="sxs-lookup"><span data-stu-id="5f208-142">Linux</span></span>](#tab/linux)

<span data-ttu-id="5f208-143">Za `perf` pomocą tego narzędzia można generować profile aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5f208-143">The `perf` tool can be used to generate .NET Core app profiles.</span></span> <span data-ttu-id="5f208-144">Wyjdź z poprzedniego wystąpienia [przykładowego celu debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios).</span><span class="sxs-lookup"><span data-stu-id="5f208-144">Exit the previous instance of the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios).</span></span>

<span data-ttu-id="5f208-145">Ustaw `COMPlus_PerfMapEnabled` zmienną środowiskową, aby spowodować, że aplikacja .NET Core utworzy `map` plik w `/tmp` katalogu.</span><span class="sxs-lookup"><span data-stu-id="5f208-145">Set the `COMPlus_PerfMapEnabled` environment variable to cause the .NET Core app to create a `map` file in the `/tmp` directory.</span></span> <span data-ttu-id="5f208-146">Ten `map` plik jest używany przez program `perf` do mapowania adresu procesora CPU na funkcje generowane przez JIT według nazwy.</span><span class="sxs-lookup"><span data-stu-id="5f208-146">This `map` file is used by `perf` to map CPU address to JIT-generated functions by name.</span></span> <span data-ttu-id="5f208-147">Aby uzyskać więcej informacji, zobacz [Zapisywanie mapy wydajności](../run-time-config/debugging-profiling.md#write-perf-map).</span><span class="sxs-lookup"><span data-stu-id="5f208-147">For more information, see [Write perf map](../run-time-config/debugging-profiling.md#write-perf-map).</span></span>

<span data-ttu-id="5f208-148">Uruchom [przykładowy cel debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) w tej samej sesji terminala.</span><span class="sxs-lookup"><span data-stu-id="5f208-148">Run the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) in the same terminal session.</span></span>

```dotnetcli
export COMPlus_PerfMapEnabled=1
dotnet run
```

<span data-ttu-id="5f208-149">Ponownie Wykorzystaj wysoki punkt końcowy interfejsu API ( <https://localhost:5001/api/diagscenario/highcpu/60000> ).</span><span class="sxs-lookup"><span data-stu-id="5f208-149">Exercise the high CPU API (<https://localhost:5001/api/diagscenario/highcpu/60000>) endpoint again.</span></span> <span data-ttu-id="5f208-150">Gdy jest uruchomiona w ramach żądania 1-minutowego, uruchom `perf` polecenie z identyfikatorem procesu:</span><span class="sxs-lookup"><span data-stu-id="5f208-150">While it's running within the 1-minute request, run the `perf` command with your process ID:</span></span>

```bash
sudo perf record -p 2266 -g
```

<span data-ttu-id="5f208-151">`perf`Polecenie uruchamia proces zbierania danych o wydajności.</span><span class="sxs-lookup"><span data-stu-id="5f208-151">The `perf` command starts the performance collection process.</span></span> <span data-ttu-id="5f208-152">Pozwól na około 20-30 sekund, a następnie naciśnij <kbd>klawisze CTRL + C</kbd> , aby wyjść z procesu kolekcjonowania.</span><span class="sxs-lookup"><span data-stu-id="5f208-152">Let it run for about 20-30 seconds, then press <kbd>Ctrl+C</kbd> to exit the collection process.</span></span> <span data-ttu-id="5f208-153">Możesz użyć tego samego `perf` polecenia, aby wyświetlić dane wyjściowe śledzenia.</span><span class="sxs-lookup"><span data-stu-id="5f208-153">You can use the same `perf` command to see the output of the trace.</span></span>

```bash
sudo perf report -f
```

<span data-ttu-id="5f208-154">Możesz również generować _grafy płomieniowe_ za pomocą następujących poleceń:</span><span class="sxs-lookup"><span data-stu-id="5f208-154">You can also generate a _flame-graph_ by using the following commands:</span></span>

```bash
git clone --depth=1 https://github.com/BrendanGregg/FlameGraph
sudo perf script | FlameGraph/stackcollapse-perf.pl | FlameGraph/flamegraph.pl > flamegraph.svg
```

<span data-ttu-id="5f208-155">To polecenie spowoduje wygenerowanie elementu `flamegraph.svg` , który można wyświetlić w przeglądarce, aby zbadać problem z wydajnością:</span><span class="sxs-lookup"><span data-stu-id="5f208-155">This command generates a `flamegraph.svg` that you can view in the browser to investigate the performance problem:</span></span>

<span data-ttu-id="5f208-156">[![Obraz SVG grafu](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)</span><span class="sxs-lookup"><span data-stu-id="5f208-156">[![Flame graph SVG image](media/flamegraph.jpg)](media/flamegraph.jpg#lightbox)</span></span>

### <a name="windows"></a>[<span data-ttu-id="5f208-157">Windows</span><span class="sxs-lookup"><span data-stu-id="5f208-157">Windows</span></span>](#tab/windows)

<span data-ttu-id="5f208-158">W systemie Windows można użyć narzędzia do [śledzenia dotnet](dotnet-trace.md) jako profilera.</span><span class="sxs-lookup"><span data-stu-id="5f208-158">On Windows, you can use the [dotnet-trace](dotnet-trace.md) tool as a profiler.</span></span> <span data-ttu-id="5f208-159">Korzystając z poprzedniego [przykładowego celu debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios), należy ponownie wykonać wysoki <https://localhost:5001/api/diagscenario/highcpu/60000> punkt końcowy procesora ().</span><span class="sxs-lookup"><span data-stu-id="5f208-159">Using the previous [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios), exercise the high CPU (<https://localhost:5001/api/diagscenario/highcpu/60000>) endpoint again.</span></span> <span data-ttu-id="5f208-160">Gdy jest uruchomiona w ramach żądania 1-minutowego, użyj `collect` polecenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5f208-160">While it's running within the 1-minute request, use the `collect` command as follows:</span></span>

```dotnetcli
dotnet-trace collect -p 22884 --providers Microsoft-DotNETCore-SampleProfiler
```

<span data-ttu-id="5f208-161">Zezwól na uruchomienie programu [dotnet-Trace](dotnet-trace.md) przez około 20-30 sekund, a następnie naciśnij klawisz <kbd>Enter</kbd> , aby wyjść z kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5f208-161">Let [dotnet-trace](dotnet-trace.md) run for about 20-30 seconds, and then press the <kbd>Enter</kbd> to exit the collection.</span></span> <span data-ttu-id="5f208-162">Wynik jest `nettrace` plikiem znajdującym się w tym samym folderze.</span><span class="sxs-lookup"><span data-stu-id="5f208-162">The result is a `nettrace` file located in the same folder.</span></span> <span data-ttu-id="5f208-163">`nettrace`Pliki są świetnym sposobem korzystania z istniejących narzędzi analitycznych w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="5f208-163">The `nettrace` files are a great way to use existing analysis tools on Windows.</span></span>

<span data-ttu-id="5f208-164">Otwórz `nettrace` program, [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) tak jak pokazano poniżej.</span><span class="sxs-lookup"><span data-stu-id="5f208-164">Open the `nettrace` with [`PerfView`](https://github.com/microsoft/perfview/blob/master/documentation/Downloading.md) as shown below.</span></span>

<span data-ttu-id="5f208-165">[![Obraz narzędzia PerfView](media/perfview.jpg)](media/perfview.jpg#lightbox)</span><span class="sxs-lookup"><span data-stu-id="5f208-165">[![PerfView image](media/perfview.jpg)](media/perfview.jpg#lightbox)</span></span>

---

## <a name="see-also"></a><span data-ttu-id="5f208-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5f208-166">See also</span></span>

- <span data-ttu-id="5f208-167">[dotnet-Trace](dotnet-trace.md) do procesów list</span><span class="sxs-lookup"><span data-stu-id="5f208-167">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="5f208-168">[dotnet-Counters](dotnet-counters.md) , aby sprawdzić użycie pamięci zarządzanej</span><span class="sxs-lookup"><span data-stu-id="5f208-168">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="5f208-169">[dotnet-dump](dotnet-dump.md) aby zebrać i przeanalizować plik zrzutu</span><span class="sxs-lookup"><span data-stu-id="5f208-169">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="5f208-170">dotnet/Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="5f208-170">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="5f208-171">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="5f208-171">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5f208-172">Debugowanie zakleszczenia w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="5f208-172">Debug a deadlock in .NET Core</span></span>](debug-deadlock.md)
