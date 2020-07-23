---
title: Zakleszczenie debugowania — .NET Core
description: Samouczek, który przeprowadzi Cię przez debugowanie problemu blokowania w programie .NET Core.
ms.topic: tutorial
ms.date: 07/20/2020
ms.openlocfilehash: 247521176297254180d794d4d4fc850f30e343b0
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86926421"
---
# <a name="debug-a-deadlock-in-net-core"></a><span data-ttu-id="7f1ac-103">Debugowanie zakleszczenia w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="7f1ac-103">Debug a deadlock in .NET Core</span></span>

<span data-ttu-id="7f1ac-104">**Ten artykuł ma zastosowanie do: ✔️** .net Core 3,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="7f1ac-104">**This article applies to: ✔️** .NET Core 3.1 SDK and later versions</span></span>

<span data-ttu-id="7f1ac-105">W tym samouczku dowiesz się, jak debugować scenariusz zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-105">In this tutorial, you'll learn how to debug a deadlock scenario.</span></span> <span data-ttu-id="7f1ac-106">Korzystając z podanego ASP.NET Core przykładowego repozytorium kodu źródłowego [aplikacji sieci Web](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) , można przypadkowo zaistnieć zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-106">Using the provided example [ASP.NET Core web app](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) source code repository, you can cause a deadlock intentionally.</span></span> <span data-ttu-id="7f1ac-107">Punkt końcowy będzie miał Rozwieszanie i kumulację wątków.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-107">The endpoint will experience a hang and thread accumulation.</span></span> <span data-ttu-id="7f1ac-108">Dowiesz się, jak można użyć różnych narzędzi do analizowania problemu, takiego jak zrzuty podstawowe, analiza zrzutów podstawowych i śledzenie procesów.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-108">You'll learn how you can use various tools to analyze the problem, such as core dumps, core dump analysis, and process tracing.</span></span>

<span data-ttu-id="7f1ac-109">W tym samouczku wykonasz następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="7f1ac-109">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="7f1ac-110">Badanie zawieszenia aplikacji</span><span class="sxs-lookup"><span data-stu-id="7f1ac-110">Investigate an app hang</span></span>
> - <span data-ttu-id="7f1ac-111">Generuj podstawowy plik zrzutu</span><span class="sxs-lookup"><span data-stu-id="7f1ac-111">Generate a core dump file</span></span>
> - <span data-ttu-id="7f1ac-112">Analizuj wątki procesu w pliku zrzutu</span><span class="sxs-lookup"><span data-stu-id="7f1ac-112">Analyze process threads in the dump file</span></span>
> - <span data-ttu-id="7f1ac-113">Analizowanie bloków stosy wywołań i Sync</span><span class="sxs-lookup"><span data-stu-id="7f1ac-113">Analyze callstacks and sync blocks</span></span>
> - <span data-ttu-id="7f1ac-114">Diagnozowanie i rozwiązywanie zakleszczenia</span><span class="sxs-lookup"><span data-stu-id="7f1ac-114">Diagnose and solve a deadlock</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7f1ac-115">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="7f1ac-115">Prerequisites</span></span>

<span data-ttu-id="7f1ac-116">Samouczek używa:</span><span class="sxs-lookup"><span data-stu-id="7f1ac-116">The tutorial uses:</span></span>

- <span data-ttu-id="7f1ac-117">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) lub nowsza wersja</span><span class="sxs-lookup"><span data-stu-id="7f1ac-117">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version</span></span>
- <span data-ttu-id="7f1ac-118">[Przykładowy element docelowy debugowania — aplikacja internetowa](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) do wyzwolenia scenariusza</span><span class="sxs-lookup"><span data-stu-id="7f1ac-118">[Sample debug target - web app](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) to trigger the scenario</span></span>
- <span data-ttu-id="7f1ac-119">[dotnet-Trace](dotnet-trace.md) do procesów list</span><span class="sxs-lookup"><span data-stu-id="7f1ac-119">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="7f1ac-120">[dotnet-dump](dotnet-dump.md) do zbierania i analizowania pliku zrzutu</span><span class="sxs-lookup"><span data-stu-id="7f1ac-120">[dotnet-dump](dotnet-dump.md) to collect, and analyze a dump file</span></span>

## <a name="core-dump-generation"></a><span data-ttu-id="7f1ac-121">Generowanie zrzutu rdzeni</span><span class="sxs-lookup"><span data-stu-id="7f1ac-121">Core dump generation</span></span>

<span data-ttu-id="7f1ac-122">Aby zbadać czas braku odpowiedzi aplikacji, zrzut rdzenia lub zrzut pamięci umożliwia sprawdzenie stanu wątków i ewentualnych blokad, które mogą mieć problemy z rywalizacją.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-122">To investigate application unresponsiveness, a core dump or memory dump allows you to inspect the state of its threads and any possible locks that may have contention issues.</span></span> <span data-ttu-id="7f1ac-123">Uruchom [przykładową](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) aplikację do debugowania przy użyciu następującego polecenia z przykładowego katalogu głównego:</span><span class="sxs-lookup"><span data-stu-id="7f1ac-123">Run the [sample debug](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) application using the following command from the sample root directory:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="7f1ac-124">Aby znaleźć identyfikator procesu, użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="7f1ac-124">To find the process ID, use the following command:</span></span>

```dotnetcli
dotnet-trace ps
```

<span data-ttu-id="7f1ac-125">Zanotuj identyfikator procesu z danych wyjściowych polecenia.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-125">Take note of the process ID from your command output.</span></span> <span data-ttu-id="7f1ac-126">Nasz identyfikator procesu został utworzony `4807` , ale będzie się różnić.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-126">Our process ID was `4807`, but yours will be different.</span></span> <span data-ttu-id="7f1ac-127">Przejdź do następującego adresu URL, który jest punktem końcowym interfejsu API w witrynie przykładowej:</span><span class="sxs-lookup"><span data-stu-id="7f1ac-127">Navigate to the following URL, which is an API endpoint on the sample site:</span></span>

[https://localhost:5001/api/diagscenario/deadlock](https://localhost:5001/api/diagscenario/deadlock)

<span data-ttu-id="7f1ac-128">Żądanie interfejsu API do witryny zostanie zawieszone i nie będzie odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-128">The API request to the site will hang and not respond.</span></span> <span data-ttu-id="7f1ac-129">Pozwól na uruchamianie żądania przez około 10-15 sekund.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-129">Let the request run for about 10-15 seconds.</span></span> <span data-ttu-id="7f1ac-130">Następnie Utwórz zrzut rdzenia przy użyciu następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="7f1ac-130">Then create the core dump using the following command:</span></span>

### <a name="linux"></a>[<span data-ttu-id="7f1ac-131">Linux</span><span class="sxs-lookup"><span data-stu-id="7f1ac-131">Linux</span></span>](#tab/linux)

```bash
sudo dotnet-dump collect -p 4807
```

### <a name="windows"></a>[<span data-ttu-id="7f1ac-132">Windows</span><span class="sxs-lookup"><span data-stu-id="7f1ac-132">Windows</span></span>](#tab/windows)

```console
dotnet-dump collect -p 4807
```

---

## <a name="analyze-the-core-dump"></a><span data-ttu-id="7f1ac-133">Analizowanie zrzutu rdzeni</span><span class="sxs-lookup"><span data-stu-id="7f1ac-133">Analyze the core dump</span></span>

<span data-ttu-id="7f1ac-134">Aby rozpocząć analizę podstawowego zrzutu, Otwórz zrzut rdzenia przy użyciu następującego `dotnet-dump analyze` polecenia.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-134">To start the core dump analysis, open the core dump using the following `dotnet-dump analyze` command.</span></span> <span data-ttu-id="7f1ac-135">Argument jest ścieżką do głównego pliku zrzutu, który został zebrany wcześniej.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-135">The argument is the path to the core dump file that was collected earlier.</span></span>

```dotnetcli
dotnet-dump analyze  ~/.dotnet/tools/core_20190513_143916
```

<span data-ttu-id="7f1ac-136">Ponieważ masz wrażenie potencjalnego zawieszenia, chcesz mieć ogólny wpływ na działanie wątku w procesie.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-136">Since you're looking at a potential hang, you want an overall feel for the thread activity in the process.</span></span> <span data-ttu-id="7f1ac-137">Możesz użyć `threads` polecenia, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="7f1ac-137">You can use the `threads` command as shown below:</span></span>

```console
> threads
*0 0x1DBFF (121855)
 1 0x1DC01 (121857)
 2 0x1DC02 (121858)
 3 0x1DC03 (121859)
 4 0x1DC04 (121860)
 5 0x1DC05 (121861)
 6 0x1DC06 (121862)
 7 0x1DC07 (121863)
 8 0x1DC08 (121864)
 9 0x1DC09 (121865)
 10 0x1DC0A (121866)
 11 0x1DC0D (121869)
 12 0x1DC0E (121870)
 13 0x1DC10 (121872)
 14 0x1DC11 (121873)
 15 0x1DC12 (121874)
 16 0x1DC13 (121875)
 17 0x1DC14 (121876)
 18 0x1DC15 (121877)
 19 0x1DC1C (121884)
 20 0x1DC1D (121885)
 21 0x1DC1E (121886)
 22 0x1DC21 (121889)
 23 0x1DC22 (121890)
 24 0x1DC23 (121891)
 25 0x1DC24 (121892)
 26 0x1DC25 (121893)
...
...
 317 0x1DD48 (122184)
 318 0x1DD49 (122185)
 319 0x1DD4A (122186)
 320 0x1DD4B (122187)
 321 0x1DD4C (122188)
 ```

<span data-ttu-id="7f1ac-138">W danych wyjściowych są wyświetlane wszystkie wątki aktualnie uruchomione w procesie ze skojarzonym IDENTYFIKATORem wątku debugera i IDENTYFIKATORem wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-138">The output shows all the threads currently running in the process with their associated debugger thread ID and operating system thread ID.</span></span> <span data-ttu-id="7f1ac-139">Na podstawie danych wyjściowych jest ponad 300 wątków.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-139">Based on the output, there are over 300 threads.</span></span>

<span data-ttu-id="7f1ac-140">Następnym krokiem jest uzyskanie lepszych informacji o tym, co aktualnie robi wątki, pobierając stosu wywołań każdego wątku.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-140">The next step is to get a better understanding of what the threads are currently doing by getting each thread's callstack.</span></span> <span data-ttu-id="7f1ac-141">`clrstack`Polecenie może służyć do wyprowadzania stosy wywołań.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-141">The `clrstack` command can be used to output callstacks.</span></span> <span data-ttu-id="7f1ac-142">Może on wyprowadzać pojedyncze stosu wywołań lub wszystkie stosy wywołań.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-142">It can either output a single callstack or all the callstacks.</span></span> <span data-ttu-id="7f1ac-143">Użyj poniższego polecenia, aby wyprowadzić wszystkie stosy wywołań dla wszystkich wątków w procesie:</span><span class="sxs-lookup"><span data-stu-id="7f1ac-143">Use the following command to output all the callstacks for all the threads in the process:</span></span>

```console
clrstack -all
```

<span data-ttu-id="7f1ac-144">Reprezentatywna część danych wyjściowych wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="7f1ac-144">A representative portion of the output looks like:</span></span>

```console
  ...
  ...
  ...
        Child SP               IP Call Site
00007F2AE37B5680 00007f305abc6360 [GCFrame: 00007f2ae37b5680]
00007F2AE37B5770 00007f305abc6360 [GCFrame: 00007f2ae37b5770]
00007F2AE37B57D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae37b57d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE37B5920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE37B5950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE37B5CA0 00007f30593044af [GCFrame: 00007f2ae37b5ca0]
00007F2AE37B5D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae37b5d70]
OS Thread Id: 0x1dc82
        Child SP               IP Call Site
00007F2AE2FB4680 00007f305abc6360 [GCFrame: 00007f2ae2fb4680]
00007F2AE2FB4770 00007f305abc6360 [GCFrame: 00007f2ae2fb4770]
00007F2AE2FB47D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae2fb47d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE2FB4920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE2FB4950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE2FB4CA0 00007f30593044af [GCFrame: 00007f2ae2fb4ca0]
00007F2AE2FB4D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae2fb4d70]
OS Thread Id: 0x1dc83
        Child SP               IP Call Site
00007F2AE27B3680 00007f305abc6360 [GCFrame: 00007f2ae27b3680]
00007F2AE27B3770 00007f305abc6360 [GCFrame: 00007f2ae27b3770]
00007F2AE27B37D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae27b37d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE27B3920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE27B3950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE27B3CA0 00007f30593044af [GCFrame: 00007f2ae27b3ca0]
00007F2AE27B3D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae27b3d70]
OS Thread Id: 0x1dc84
        Child SP               IP Call Site
00007F2AE1FB2680 00007f305abc6360 [GCFrame: 00007f2ae1fb2680]
00007F2AE1FB2770 00007f305abc6360 [GCFrame: 00007f2ae1fb2770]
00007F2AE1FB27D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae1fb27d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE1FB2920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE1FB2950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE1FB2CA0 00007f30593044af [GCFrame: 00007f2ae1fb2ca0]
00007F2AE1FB2D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae1fb2d70]
OS Thread Id: 0x1dc85
        Child SP               IP Call Site
00007F2AE17B1680 00007f305abc6360 [GCFrame: 00007f2ae17b1680]
00007F2AE17B1770 00007f305abc6360 [GCFrame: 00007f2ae17b1770]
00007F2AE17B17D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae17b17d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE17B1920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE17B1950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE17B1CA0 00007f30593044af [GCFrame: 00007f2ae17b1ca0]
00007F2AE17B1D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae17b1d70]
OS Thread Id: 0x1dc86
        Child SP               IP Call Site
00007F2AE0FB0680 00007f305abc6360 [GCFrame: 00007f2ae0fb0680]
00007F2AE0FB0770 00007f305abc6360 [GCFrame: 00007f2ae0fb0770]
00007F2AE0FB07D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae0fb07d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE0FB0920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE0FB0950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE0FB0CA0 00007f30593044af [GCFrame: 00007f2ae0fb0ca0]
00007F2AE0FB0D70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae0fb0d70]
OS Thread Id: 0x1dc87
        Child SP               IP Call Site
00007F2AE07AF680 00007f305abc6360 [GCFrame: 00007f2ae07af680]
00007F2AE07AF770 00007f305abc6360 [GCFrame: 00007f2ae07af770]
00007F2AE07AF7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2ae07af7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2AE07AF920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2AE07AF950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2AE07AFCA0 00007f30593044af [GCFrame: 00007f2ae07afca0]
00007F2AE07AFD70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2ae07afd70]
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
...
...
```

<span data-ttu-id="7f1ac-145">Obserwowanie stosy wywołań dla wszystkich ponad 300 wątków pokazuje wzorzec, w którym większość wątków współużytkuje wspólny stosu wywołań:</span><span class="sxs-lookup"><span data-stu-id="7f1ac-145">Observing the callstacks for all 300+ threads shows a pattern where a majority of the threads share a common callstack:</span></span>

```console
OS Thread Id: 0x1dc88
        Child SP               IP Call Site
00007F2ADFFAE680 00007f305abc6360 [GCFrame: 00007f2adffae680]
00007F2ADFFAE770 00007f305abc6360 [GCFrame: 00007f2adffae770]
00007F2ADFFAE7D0 00007f305abc6360 [HelperMethodFrame_1OBJ: 00007f2adffae7d0] System.Threading.Monitor.ReliableEnter(System.Object, Boolean ByRef)
00007F2ADFFAE920 00007F2FE392B31F testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_1() [/home/marioh/webapi/Controllers/diagscenario.cs @ 36]
00007F2ADFFAE950 00007F2FE392B46D System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/__w/3/s/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
00007F2ADFFAECA0 00007f30593044af [GCFrame: 00007f2adffaeca0]
00007F2ADFFAED70 00007f30593044af [DebuggerU2MCatchHandlerFrame: 00007f2adffaed70]
```

<span data-ttu-id="7f1ac-146">Stosu wywołań wydaje się, że żądanie dotarło do naszej metody zakleszczenia, która z kolei wywołuje wywołanie `Monitor.ReliableEnter` .</span><span class="sxs-lookup"><span data-stu-id="7f1ac-146">The callstack seems to show that the request arrived in our deadlock method that in turn makes a call to `Monitor.ReliableEnter`.</span></span> <span data-ttu-id="7f1ac-147">Ta metoda wskazuje, że wątki próbują wprowadzić blokadę monitora.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-147">This method indicates that the threads are trying to enter a monitor lock.</span></span> <span data-ttu-id="7f1ac-148">Czekają na dostępność blokady.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-148">They're waiting on the availability of the lock.</span></span> <span data-ttu-id="7f1ac-149">Prawdopodobnie jest on zablokowany przez inny wątek.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-149">It's likely locked by a different thread.</span></span>

<span data-ttu-id="7f1ac-150">Następnym krokiem jest znalezienie, który wątek rzeczywiście utrzymuje blokadę monitora.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-150">The next step then is to find out which thread is actually holding the monitor lock.</span></span> <span data-ttu-id="7f1ac-151">Ponieważ monitory zwykle przechowują informacje o blokowaniu w tabeli bloków synchronizacji, można użyć `syncblk` polecenia, aby uzyskać więcej informacji:</span><span class="sxs-lookup"><span data-stu-id="7f1ac-151">Since monitors typically store lock information in the sync block table, we can use the `syncblk` command to get more information:</span></span>

```console
> syncblk
Index         SyncBlock MonitorHeld Recursion Owning Thread Info          SyncBlock Owner
   43 00000246E51268B8          603         1 0000024B713F4E30 5634  28   00000249654b14c0 System.Object
   44 00000246E5126908            3         1 0000024B713F47E0 51d4  29   00000249654b14d8 System.Object
-----------------------------
Total           344
CCW             1
RCW             2
ComClassFactory 0
Free            0
```

<span data-ttu-id="7f1ac-152">Dwie interesujące kolumny to **MonitorHeld** i **właściciel informacji o wątkach**.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-152">The two interesting columns are **MonitorHeld** and **Owning Thread Info**.</span></span> <span data-ttu-id="7f1ac-153">Kolumna **MonitorHeld** pokazuje, czy blokada monitora jest pobierana przez wątek i liczbę oczekujących wątków.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-153">The **MonitorHeld** column shows whether a monitor lock is acquired by a thread and the number of waiting threads.</span></span> <span data-ttu-id="7f1ac-154">Kolumna **Informacje o wątkach będących właścicielem** wskazuje, który wątek jest aktualnie właścicielem blokady monitora.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-154">The **Owning Thread Info** column shows which thread currently owns the monitor lock.</span></span> <span data-ttu-id="7f1ac-155">Informacje o wątku mają trzy różne podkolumny.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-155">The thread info has three different subcolumns.</span></span> <span data-ttu-id="7f1ac-156">Druga Podkolumna zawiera identyfikator wątku systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-156">The second subcolumn shows operating system thread ID.</span></span>

<span data-ttu-id="7f1ac-157">W tym momencie wiemy, że dwa różne wątki (0x5634 i 0x51d4) przechowują blokadę monitora.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-157">At this point, we know two different threads (0x5634 and 0x51d4) hold a monitor lock.</span></span> <span data-ttu-id="7f1ac-158">Następnym krokiem jest zaplanowanie działania tych wątków.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-158">The next step is to take a look at what those threads are doing.</span></span> <span data-ttu-id="7f1ac-159">Musimy sprawdzić, czy blokada nie jest zablokowana.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-159">We need to check if they're stuck indefinitely holding the lock.</span></span> <span data-ttu-id="7f1ac-160">Użyjmy `setthread` poleceń i, `clrstack` Aby przełączyć się do każdego z wątków i wyświetlić stosy wywołań.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-160">Let's use the `setthread` and `clrstack` commands to switch to each of the threads and display the callstacks.</span></span>

<span data-ttu-id="7f1ac-161">Aby sprawdzić pierwszy wątek, uruchom `setthread` polecenie i Znajdź indeks wątku 0x5634 (nasz indeks to 28).</span><span class="sxs-lookup"><span data-stu-id="7f1ac-161">To look at the first thread, run the `setthread` command, and find the index of the 0x5634 thread (our index was 28).</span></span> <span data-ttu-id="7f1ac-162">Funkcja zakleszczenia oczekuje na uzyskanie blokady, ale jest już właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-162">The deadlock function is waiting to acquire a lock, but it already owns the lock.</span></span> <span data-ttu-id="7f1ac-163">Jest to zakleszczenie oczekujące na blokadę, która już się utrzymuje.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-163">It's in deadlock waiting for the lock it already holds.</span></span>

```console
> setthread 28
> clrstack
OS Thread Id: 0x5634 (28)
        Child SP               IP Call Site
0000004E46AFEAA8 00007fff43a5cbc4 [GCFrame: 0000004e46afeaa8]
0000004E46AFEC18 00007fff43a5cbc4 [GCFrame: 0000004e46afec18]
0000004E46AFEC68 00007fff43a5cbc4 [HelperMethodFrame_1OBJ: 0000004e46afec68] System.Threading.Monitor.Enter(System.Object)
0000004E46AFEDC0 00007FFE5EAF9C80 testwebapi.Controllers.DiagScenarioController.DeadlockFunc() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 58]
0000004E46AFEE30 00007FFE5EAF9B8C testwebapi.Controllers.DiagScenarioController.<deadlock>b__3_0() [C:\Users\dapine\Downloads\Diagnostic_scenarios_sample_debug_target\Controllers\DiagnosticScenarios.cs @ 26]
0000004E46AFEE80 00007FFEBB251A5B System.Threading.ThreadHelper.ThreadStart_Context(System.Object) [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 44]
0000004E46AFEEB0 00007FFE5EAEEEEC System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object) [/_/src/System.Private.CoreLib/shared/System/Threading/ExecutionContext.cs @ 201]
0000004E46AFEF20 00007FFEBB234EAB System.Threading.ThreadHelper.ThreadStart() [/_/src/System.Private.CoreLib/src/System/Threading/Thread.CoreCLR.cs @ 93]
0000004E46AFF138 00007ffebdcc6b63 [GCFrame: 0000004e46aff138]
0000004E46AFF3A0 00007ffebdcc6b63 [DebuggerU2MCatchHandlerFrame: 0000004e46aff3a0]
```

<span data-ttu-id="7f1ac-164">Drugi wątek jest podobny.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-164">The second thread is similar.</span></span> <span data-ttu-id="7f1ac-165">Próbuje on również uzyskać blokadę, która jest już własnością.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-165">It's also trying to acquire a lock that it already owns.</span></span> <span data-ttu-id="7f1ac-166">Pozostałe 300 wątków, które oczekują na to, najprawdopodobniej czekają na jedną z blokad, które spowodowały zakleszczenie.</span><span class="sxs-lookup"><span data-stu-id="7f1ac-166">The remaining 300+ threads that are all waiting are most likely also waiting on one of the locks that caused the deadlock.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f1ac-167">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f1ac-167">See also</span></span>

- <span data-ttu-id="7f1ac-168">[dotnet-Trace](dotnet-trace.md) do procesów list</span><span class="sxs-lookup"><span data-stu-id="7f1ac-168">[dotnet-trace](dotnet-trace.md) to list processes</span></span>
- <span data-ttu-id="7f1ac-169">[dotnet-Counters](dotnet-counters.md) , aby sprawdzić użycie pamięci zarządzanej</span><span class="sxs-lookup"><span data-stu-id="7f1ac-169">[dotnet-counters](dotnet-counters.md) to check managed memory usage</span></span>
- <span data-ttu-id="7f1ac-170">[dotnet-dump](dotnet-dump.md) aby zebrać i przeanalizować plik zrzutu</span><span class="sxs-lookup"><span data-stu-id="7f1ac-170">[dotnet-dump](dotnet-dump.md) to collect and analyze a dump file</span></span>
- [<span data-ttu-id="7f1ac-171">dotnet/Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="7f1ac-171">dotnet/diagnostics</span></span>](https://github.com/dotnet/diagnostics/tree/master/documentation/tutorial)

## <a name="next-steps"></a><span data-ttu-id="7f1ac-172">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="7f1ac-172">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7f1ac-173">Jakie narzędzia diagnostyczne są dostępne w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="7f1ac-173">What diagnostic tools are available in .NET Core</span></span>](index.md)
