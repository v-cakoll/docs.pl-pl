---
title: Debuguj samouczek przeciekać pamięci
description: Dowiedz się, jak debugować przeciek pamięci w .NET Core.
ms.topic: tutorial
ms.date: 12/17/2019
ms.openlocfilehash: 014945394f87edd02c94f7c3b28043bd07470d8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737730"
---
# <a name="tutorial-debug-a-memory-leak-in-net-core"></a><span data-ttu-id="c44a2-103">Samouczek: Debugowanie przecieku pamięci w .NET Core</span><span class="sxs-lookup"><span data-stu-id="c44a2-103">Tutorial: Debug a memory leak in .NET Core</span></span>

<span data-ttu-id="c44a2-104">**Ten artykuł dotyczy:** ✔️ .NET Core 3.0 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="c44a2-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="c44a2-105">W tym samouczku przedstawiono narzędzia do analizowania przeciekpamięci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c44a2-105">This tutorial demonstrates the tools to analyze a .NET Core memory leak.</span></span>

<span data-ttu-id="c44a2-106">Ten samouczek używa przykładowej aplikacji, która została zaprojektowana do celowo przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="c44a2-106">This tutorial uses a sample app, which is designed to intentionally leak memory.</span></span> <span data-ttu-id="c44a2-107">Próbka jest dostarczana jako ćwiczenie.</span><span class="sxs-lookup"><span data-stu-id="c44a2-107">The sample is provided as an exercise.</span></span> <span data-ttu-id="c44a2-108">Można analizować aplikację, która jest przypadkowo przecieka pamięci zbyt.</span><span class="sxs-lookup"><span data-stu-id="c44a2-108">You can analyze an app that is unintentionally leaking memory too.</span></span>

<span data-ttu-id="c44a2-109">W tym samouczku zostaną wykonane następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c44a2-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="c44a2-110">Sprawdź użycie pamięci zarządzanej za pomocą [liczników dotnet .](dotnet-counters.md)</span><span class="sxs-lookup"><span data-stu-id="c44a2-110">Examine managed memory usage with [dotnet-counters](dotnet-counters.md).</span></span>
> - <span data-ttu-id="c44a2-111">Generowanie pliku zrzutu.</span><span class="sxs-lookup"><span data-stu-id="c44a2-111">Generate a dump file.</span></span>
> - <span data-ttu-id="c44a2-112">Analizowanie użycia pamięci przy użyciu pliku zrzutu.</span><span class="sxs-lookup"><span data-stu-id="c44a2-112">Analyze the memory usage using the dump file.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c44a2-113">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c44a2-113">Prerequisites</span></span>

<span data-ttu-id="c44a2-114">Samouczek używa:</span><span class="sxs-lookup"><span data-stu-id="c44a2-114">The tutorial uses:</span></span>

- <span data-ttu-id="c44a2-115">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) lub nowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="c44a2-115">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="c44a2-116">[dotnet-trace](dotnet-trace.md) do procesów listy.</span><span class="sxs-lookup"><span data-stu-id="c44a2-116">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
- <span data-ttu-id="c44a2-117">[dotnet-liczniki](dotnet-counters.md) do sprawdzania użycia pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="c44a2-117">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
- <span data-ttu-id="c44a2-118">[dotnet-dump](dotnet-dump.md) do zbierania i analizowania pliku zrzutu.</span><span class="sxs-lookup"><span data-stu-id="c44a2-118">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
- <span data-ttu-id="c44a2-119">Przykładowa aplikacja [docelowa debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) do zdiagnozowania.</span><span class="sxs-lookup"><span data-stu-id="c44a2-119">A [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) app to diagnose.</span></span>

<span data-ttu-id="c44a2-120">Samouczek zakłada, że przykład i narzędzia są zainstalowane i gotowe do użycia.</span><span class="sxs-lookup"><span data-stu-id="c44a2-120">The tutorial assumes the sample and tools are installed and ready to use.</span></span>

## <a name="examine-managed-memory-usage"></a><span data-ttu-id="c44a2-121">Sprawdź użycie pamięci zarządzanej</span><span class="sxs-lookup"><span data-stu-id="c44a2-121">Examine managed memory usage</span></span>

<span data-ttu-id="c44a2-122">Przed rozpoczęciem zbierania danych diagnostycznych, aby pomóc nam spowodować ten scenariusz, należy upewnić się, że rzeczywiście widzisz przeciek pamięci (wzrost pamięci).</span><span class="sxs-lookup"><span data-stu-id="c44a2-122">Before you start collecting diagnostics data to help us root cause this scenario, you need to make sure you're actually seeing a memory leak (memory growth).</span></span> <span data-ttu-id="c44a2-123">Aby to potwierdzić, można użyć narzędzia [liczniki dotnet.](dotnet-counters.md)</span><span class="sxs-lookup"><span data-stu-id="c44a2-123">You can use the [dotnet-counters](dotnet-counters.md) tool to confirm that.</span></span>

<span data-ttu-id="c44a2-124">Otwórz okno konsoli i przejdź do katalogu, w którym pobrano, i rozpakuj [przykładowy obiekt docelowy debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span><span class="sxs-lookup"><span data-stu-id="c44a2-124">Open a console window and navigate to the directory where you downloaded and unzipped the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/).</span></span> <span data-ttu-id="c44a2-125">Uruchom obiekt docelowy:</span><span class="sxs-lookup"><span data-stu-id="c44a2-125">Run the target:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="c44a2-126">Z oddzielnej konsoli znajdź identyfikator procesu za pomocą narzędzia [dotnet-trace:](dotnet-trace.md)</span><span class="sxs-lookup"><span data-stu-id="c44a2-126">From a separate console, find the process ID using the [dotnet-trace](dotnet-trace.md) tool:</span></span>

```console
dotnet-trace ps
```

<span data-ttu-id="c44a2-127">Dane wyjściowe powinny być podobne do:</span><span class="sxs-lookup"><span data-stu-id="c44a2-127">The output should be similar to:</span></span>

```console
4807 DiagnosticScena /home/user/git/samples/core/diagnostics/DiagnosticScenarios/bin/Debug/netcoreapp3.0/DiagnosticScenarios
```

<span data-ttu-id="c44a2-128">Teraz sprawdź użycie pamięci zarządzanej za pomocą narzędzia [liczników dotnet.](dotnet-counters.md)</span><span class="sxs-lookup"><span data-stu-id="c44a2-128">Now, check managed memory usage with the [dotnet-counters](dotnet-counters.md) tool.</span></span> <span data-ttu-id="c44a2-129">Określa `--refresh-interval` liczbę sekund między odświeżeniami:</span><span class="sxs-lookup"><span data-stu-id="c44a2-129">The `--refresh-interval` specifies the number of seconds between refreshes:</span></span>

```console
dotnet-counters monitor --refresh-interval 1 -p 4807
```

<span data-ttu-id="c44a2-130">Dane wyjściowe na żywo powinny być podobne do:</span><span class="sxs-lookup"><span data-stu-id="c44a2-130">The live output should be similar to:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[System.Runtime]
    # of Assemblies Loaded                           118
    % Time in GC (since last GC)                       0
    Allocation Rate (Bytes / sec)                 37,896
    CPU Usage (%)                                      0
    Exceptions / sec                                   0
    GC Heap Size (MB)                                  4
    Gen 0 GC / sec                                     0
    Gen 0 Size (B)                                     0
    Gen 1 GC / sec                                     0
    Gen 1 Size (B)                                     0
    Gen 2 GC / sec                                     0
    Gen 2 Size (B)                                     0
    LOH Size (B)                                       0
    Monitor Lock Contention Count / sec                0
    Number of Active Timers                            1
    ThreadPool Completed Work Items / sec             10
    ThreadPool Queue Length                            0
    ThreadPool Threads Count                           1
    Working Set (MB)                                  83
```

<span data-ttu-id="c44a2-131">Koncentrując się na tej linii:</span><span class="sxs-lookup"><span data-stu-id="c44a2-131">Focusing on this line:</span></span>

```console
    GC Heap Size (MB)                                  4
```

<span data-ttu-id="c44a2-132">Widać, że zarządzana pamięć sterty wynosi 4 MB zaraz po uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="c44a2-132">You can see that the managed heap memory is 4 MB right after startup.</span></span>

<span data-ttu-id="c44a2-133">Teraz naciśnij adres `http://localhost:5000/api/diagscenario/memleak/20000`URL .</span><span class="sxs-lookup"><span data-stu-id="c44a2-133">Now, hit the URL `http://localhost:5000/api/diagscenario/memleak/20000`.</span></span>

<span data-ttu-id="c44a2-134">Należy zauważyć, że użycie pamięci wzrosła do 30 MB.</span><span class="sxs-lookup"><span data-stu-id="c44a2-134">Observe that the memory usage has grown to 30 MB.</span></span>

```console
    GC Heap Size (MB)                                 30
```

<span data-ttu-id="c44a2-135">Obserwując użycie pamięci, można śmiało powiedzieć, że pamięć rośnie lub przecieka.</span><span class="sxs-lookup"><span data-stu-id="c44a2-135">By watching the memory usage, you can safely say that memory is growing or leaking.</span></span> <span data-ttu-id="c44a2-136">Następnym krokiem jest zebranie odpowiednich danych do analizy pamięci.</span><span class="sxs-lookup"><span data-stu-id="c44a2-136">The next step is to collect the right data for memory analysis.</span></span>

### <a name="generate-memory-dump"></a><span data-ttu-id="c44a2-137">Generowanie zrzutu pamięci</span><span class="sxs-lookup"><span data-stu-id="c44a2-137">Generate memory dump</span></span>

<span data-ttu-id="c44a2-138">Podczas analizowania możliwych przecieków pamięci potrzebny jest dostęp do sterty pamięci aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c44a2-138">When analyzing possible memory leaks, you need access to the app's memory heap.</span></span> <span data-ttu-id="c44a2-139">Następnie można analizować zawartość pamięci.</span><span class="sxs-lookup"><span data-stu-id="c44a2-139">Then you can analyze the memory contents.</span></span> <span data-ttu-id="c44a2-140">Patrząc na relacje między obiektami, można tworzyć teorie na temat dlaczego pamięć nie jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="c44a2-140">Looking at relationships between objects, you create theories on why memory isn't being freed.</span></span> <span data-ttu-id="c44a2-141">Typowym źródłem danych diagnostyki jest zrzut pamięci w systemie Windows lub równoważne zrzut rdzenia w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="c44a2-141">A common diagnostics data source is a memory dump on Windows or the equivalent core dump on Linux.</span></span> <span data-ttu-id="c44a2-142">Aby wygenerować zrzut aplikacji .NET Core, można użyć narzędzia [dotnet-dump).](dotnet-dump.md)</span><span class="sxs-lookup"><span data-stu-id="c44a2-142">To generate a dump of a .NET Core application, you can use the [dotnet-dump)](dotnet-dump.md) tool.</span></span>

<span data-ttu-id="c44a2-143">Przy użyciu [próbnego obiektu docelowego debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) wcześniej uruchomione, uruchom następujące polecenie, aby wygenerować zrzut rdzenia systemu Linux:</span><span class="sxs-lookup"><span data-stu-id="c44a2-143">Using the [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) previously started, run the following command to generate a Linux core dump:</span></span>

```dotnetcli
dotnet-dump collect -p 4807
```

<span data-ttu-id="c44a2-144">Wynik jest zrzut rdzenia znajduje się w tym samym folderze.</span><span class="sxs-lookup"><span data-stu-id="c44a2-144">The result is a core dump located in the same folder.</span></span>

```console
Writing minidump with heap to ./core_20190430_185145
Complete
```

### <a name="restart-the-failed-process"></a><span data-ttu-id="c44a2-145">Ponowne uruchomienie nieudanego procesu</span><span class="sxs-lookup"><span data-stu-id="c44a2-145">Restart the failed process</span></span>

<span data-ttu-id="c44a2-146">Po zebraniu zrzutu należy mieć wystarczające informacje, aby zdiagnozować proces, który nie powiódł się.</span><span class="sxs-lookup"><span data-stu-id="c44a2-146">Once the dump is collected, you should have sufficient information to diagnose the failed process.</span></span> <span data-ttu-id="c44a2-147">Jeśli proces nie powiodło się jest uruchomiony na serwerze produkcyjnym, teraz jest to idealny czas na krótkoterminowe korygowania przez ponowne uruchomienie procesu.</span><span class="sxs-lookup"><span data-stu-id="c44a2-147">If the failed process is running on a production server, now it's the ideal time for short-term remediation by restarting the process.</span></span>

<span data-ttu-id="c44a2-148">W tym samouczku gotowe są [przykładowe miejsce docelowe debugowania](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) i można go zamknąć.</span><span class="sxs-lookup"><span data-stu-id="c44a2-148">In this tutorial, you're now done with the [Sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios/) and you can close it.</span></span> <span data-ttu-id="c44a2-149">Przejdź do terminalu, który `Control-C`uruchomił serwer i naciśnij klawisz .</span><span class="sxs-lookup"><span data-stu-id="c44a2-149">Navigate to the terminal that started the server and press `Control-C`.</span></span>

### <a name="analyze-the-core-dump"></a><span data-ttu-id="c44a2-150">Analizowanie zrzutu rdzenia</span><span class="sxs-lookup"><span data-stu-id="c44a2-150">Analyze the core dump</span></span>

<span data-ttu-id="c44a2-151">Teraz, gdy masz wygenerowany zrzut rdzenia, użyj narzędzia [dotnet-dump),](dotnet-dump.md) aby przeanalizować zrzut:</span><span class="sxs-lookup"><span data-stu-id="c44a2-151">Now that you have a core dump generated, use the [dotnet-dump)](dotnet-dump.md) tool to analyze the dump:</span></span>

```dotnetcli
dotnet-dump analyze core_20190430_185145
```

<span data-ttu-id="c44a2-152">Gdzie `core_20190430_185145` jest nazwa zrzutu rdzenia, który chcesz przeanalizować.</span><span class="sxs-lookup"><span data-stu-id="c44a2-152">Where `core_20190430_185145` is the name of the core dump you want to analyze.</span></span>

> [!NOTE]
> <span data-ttu-id="c44a2-153">Jeśli widzisz błąd narzekający, że nie można odnaleźć *libdl.so,* może być trzeba zainstalować pakiet *libc6-dev.*</span><span class="sxs-lookup"><span data-stu-id="c44a2-153">If you see an error complaining that *libdl.so* cannot be found, you may have to install the *libc6-dev* package.</span></span> <span data-ttu-id="c44a2-154">Aby uzyskać więcej informacji, zobacz [Wymagania wstępne dotyczące programu .NET Core w systemie Linux](../linux-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="c44a2-154">For more information, see [Prerequisites for .NET Core on Linux](../linux-prerequisites.md).</span></span>

<span data-ttu-id="c44a2-155">Zostanie wyświetlony monit, w którym można wprowadzić polecenia SOS.</span><span class="sxs-lookup"><span data-stu-id="c44a2-155">You'll be presented with a prompt where you can enter SOS commands.</span></span> <span data-ttu-id="c44a2-156">Często pierwszą rzeczą, na którą chcesz spojrzeć, jest ogólny stan zarządzanej sterty:</span><span class="sxs-lookup"><span data-stu-id="c44a2-156">Commonly, the first thing you want to look at is the overall state of the managed heap:</span></span>

```console
> dumpheap -stat

Statistics:
              MT    Count    TotalSize Class Name
...
00007f6c1eeefba8      576        59904 System.Reflection.RuntimeMethodInfo
00007f6c1dc021c8     1749        95696 System.SByte[]
00000000008c9db0     3847       116080      Free
00007f6c1e784a18      175       128640 System.Char[]
00007f6c1dbf5510      217       133504 System.Object[]
00007f6c1dc014c0      467       416464 System.Byte[]
00007f6c21625038        6      4063376 testwebapi.Controllers.Customer[]
00007f6c20a67498   200000      4800000 testwebapi.Controllers.Customer
00007f6c1dc00f90   206770     19494060 System.String
Total 428516 objects
```

<span data-ttu-id="c44a2-157">W tym miejscu można zobaczyć, że większość obiektów są albo `String` lub `Customer` obiektów.</span><span class="sxs-lookup"><span data-stu-id="c44a2-157">Here you can see that most objects are either `String` or `Customer` objects.</span></span>

<span data-ttu-id="c44a2-158">Za pomocą `dumpheap` polecenia można ponownie użyć tabeli metod (MT), `String` aby uzyskać listę wszystkich wystąpień:</span><span class="sxs-lookup"><span data-stu-id="c44a2-158">You can use the `dumpheap` command again with the method table (MT) to get a list of all the `String` instances:</span></span>

```console
> dumpheap -mt 00007faddaa50f90

         Address               MT     Size
...
00007f6ad09421f8 00007faddaa50f90       94
...
00007f6ad0965b20 00007f6c1dc00f90       80
00007f6ad0965c10 00007f6c1dc00f90       80
00007f6ad0965d00 00007f6c1dc00f90       80
00007f6ad0965df0 00007f6c1dc00f90       80
00007f6ad0965ee0 00007f6c1dc00f90       80

Statistics:
              MT    Count    TotalSize Class Name
00007f6c1dc00f90   206770     19494060 System.String
Total 206770 objects
```

<span data-ttu-id="c44a2-159">Teraz można użyć `gcroot` polecenia `System.String` w wystąpieniu, aby zobaczyć, jak i dlaczego obiekt jest zakorzeniony.</span><span class="sxs-lookup"><span data-stu-id="c44a2-159">You can now use the `gcroot` command on a `System.String` instance to see how and why the object is rooted.</span></span> <span data-ttu-id="c44a2-160">Bądź cierpliwy, ponieważ to polecenie trwa kilka minut ze stertą 30 MB:</span><span class="sxs-lookup"><span data-stu-id="c44a2-160">Be patient because this command takes several minutes with a 30-MB heap:</span></span>

```console
> gcroot -all 00007f6ad09421f8

Thread 3f68:
    00007F6795BB58A0 00007F6C1D7D0745 System.Diagnostics.Tracing.CounterGroup.PollForValues() [/_/src/System.Private.CoreLib/shared/System/Diagnostics/Tracing/CounterGroup.cs @ 260]
        rbx:  (interior)
            ->  00007F6BDFFFF038 System.Object[]
            ->  00007F69D0033570 testwebapi.Controllers.Processor
            ->  00007F69D0033588 testwebapi.Controllers.CustomerCache
            ->  00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
            ->  00007F6C000148A0 testwebapi.Controllers.Customer[]
            ->  00007F6AD0942258 testwebapi.Controllers.Customer
            ->  00007F6AD09421F8 System.String

HandleTable:
    00007F6C98BB15F8 (pinned handle)
    -> 00007F6BDFFFF038 System.Object[]
    -> 00007F69D0033570 testwebapi.Controllers.Processor
    -> 00007F69D0033588 testwebapi.Controllers.CustomerCache
    -> 00007F69D00335A0 System.Collections.Generic.List`1[[testwebapi.Controllers.Customer, DiagnosticScenarios]]
    -> 00007F6C000148A0 testwebapi.Controllers.Customer[]
    -> 00007F6AD0942258 testwebapi.Controllers.Customer
    -> 00007F6AD09421F8 System.String

Found 2 roots.
```

<span data-ttu-id="c44a2-161">Widać, że `String` jest bezpośrednio w `Customer` posiadaniu obiektu i `CustomerCache` pośrednio posiadanych przez obiekt.</span><span class="sxs-lookup"><span data-stu-id="c44a2-161">You can see that the `String` is directly held by the `Customer` object and indirectly held by a `CustomerCache` object.</span></span>

<span data-ttu-id="c44a2-162">Można kontynuować dumpingu obecnie obiektów, aby zobaczyć, że większość `String` obiektów po podobny wzorzec.</span><span class="sxs-lookup"><span data-stu-id="c44a2-162">You can continue dumping out objects to see that most `String` objects follow a similar pattern.</span></span> <span data-ttu-id="c44a2-163">W tym momencie dochodzenie dostarczyło wystarczających informacji, aby zidentyfikować główną przyczynę w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c44a2-163">At this point, the investigation provided sufficient information to identify the root cause in your code.</span></span>

<span data-ttu-id="c44a2-164">Ta ogólna procedura pozwala zidentyfikować źródło głównych przecieków pamięci.</span><span class="sxs-lookup"><span data-stu-id="c44a2-164">This general procedure allows you to identify the source of major memory leaks.</span></span>

## <a name="clean-up-resources"></a><span data-ttu-id="c44a2-165">Oczyszczanie zasobów</span><span class="sxs-lookup"><span data-stu-id="c44a2-165">Clean up resources</span></span>

<span data-ttu-id="c44a2-166">W tym samouczku uruchomiono przykładowy serwer sieci Web.</span><span class="sxs-lookup"><span data-stu-id="c44a2-166">In this tutorial, you started a sample web server.</span></span> <span data-ttu-id="c44a2-167">Ten serwer powinien zostać zamknięty, jak [wyjaśniono](#restart-the-failed-process) w sekcji Uruchom ponownie proces nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="c44a2-167">This server should have been shut down as explained in the [Restart the failed process](#restart-the-failed-process) section.</span></span>

<span data-ttu-id="c44a2-168">Można również usunąć utworzony plik zrzutu.</span><span class="sxs-lookup"><span data-stu-id="c44a2-168">You can also delete the dump file that was created.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c44a2-169">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="c44a2-169">Next steps</span></span>

<span data-ttu-id="c44a2-170">Gratulujemy ukończenia tego samouczka.</span><span class="sxs-lookup"><span data-stu-id="c44a2-170">Congratulations on completing this tutorial.</span></span>

<span data-ttu-id="c44a2-171">Nadal publikujemy więcej samouczków diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="c44a2-171">We're still publishing more diagnostic tutorials.</span></span> <span data-ttu-id="c44a2-172">Wersje robocze można odczytać w repozytorium [dotnet/diagnostics.](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)</span><span class="sxs-lookup"><span data-stu-id="c44a2-172">You can read the draft versions on the [dotnet/diagnostics](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial) repository.</span></span>

<span data-ttu-id="c44a2-173">W tym samouczku omówiono podstawy kluczowych narzędzi diagnostycznych .NET.</span><span class="sxs-lookup"><span data-stu-id="c44a2-173">This tutorial covered the basics of key .NET diagnostic tools.</span></span> <span data-ttu-id="c44a2-174">Aby uzyskać informacje o zaawansowanym użyciu, zobacz następującą dokumentację referencyjną:</span><span class="sxs-lookup"><span data-stu-id="c44a2-174">For advanced usage, see the following reference documentation:</span></span>

* <span data-ttu-id="c44a2-175">[dotnet-trace](dotnet-trace.md) do procesów listy.</span><span class="sxs-lookup"><span data-stu-id="c44a2-175">[dotnet-trace](dotnet-trace.md) to list processes.</span></span>
* <span data-ttu-id="c44a2-176">[dotnet-liczniki](dotnet-counters.md) do sprawdzania użycia pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="c44a2-176">[dotnet-counters](dotnet-counters.md) to check managed memory usage.</span></span>
* <span data-ttu-id="c44a2-177">[dotnet-dump](dotnet-dump.md) do zbierania i analizowania pliku zrzutu.</span><span class="sxs-lookup"><span data-stu-id="c44a2-177">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file.</span></span>
