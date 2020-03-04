---
title: dotnet-Counters — .NET Core
description: Dowiedz się, jak zainstalować i użyć narzędzia wiersza polecenia programu dotnet-Counter.
ms.date: 02/26/2020
ms.openlocfilehash: 88f701a60d0ee03dd0236ae54c57679943e14939
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157885"
---
# <a name="dotnet-counters"></a><span data-ttu-id="88bd0-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="88bd0-103">dotnet-counters</span></span>

<span data-ttu-id="88bd0-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 3,0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="88bd0-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="88bd0-105">Zainstaluj dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="88bd0-105">Install dotnet-counters</span></span>

<span data-ttu-id="88bd0-106">Aby zainstalować najnowszą wersję wydania [pakietu NuGet](https://www.nuget.org/packages/dotnet-counters)`dotnet-counters`, użyj [Narzędzia dotnet Install](../tools/dotnet-tool-install.md) Command:</span><span class="sxs-lookup"><span data-stu-id="88bd0-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="88bd0-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="88bd0-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="88bd0-108">Opis</span><span class="sxs-lookup"><span data-stu-id="88bd0-108">Description</span></span>

<span data-ttu-id="88bd0-109">`dotnet-counters` to narzędzie do monitorowania wydajności dla monitorowania kondycji ad hoc i badania wydajności pierwszego poziomu.</span><span class="sxs-lookup"><span data-stu-id="88bd0-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="88bd0-110">Może obserwować wartości liczników wydajności, które są publikowane za pośrednictwem interfejsu API <xref:System.Diagnostics.Tracing.EventCounter>.</span><span class="sxs-lookup"><span data-stu-id="88bd0-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="88bd0-111">Można na przykład szybko monitorować elementy, takie jak użycie procesora CPU lub częstotliwość zgłaszania wyjątków w aplikacji .NET Core, aby sprawdzić, czy istnieją jakieś podejrzane informacje przed uzyskaniem większej wydajności, przy użyciu `PerfView` lub `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="88bd0-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="88bd0-112">Opcje</span><span class="sxs-lookup"><span data-stu-id="88bd0-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="88bd0-113">Wyświetla wersję narzędzia dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="88bd0-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="88bd0-114">Wyświetla pomoc w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="88bd0-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="88bd0-115">Polecenia</span><span class="sxs-lookup"><span data-stu-id="88bd0-115">Commands</span></span>

| <span data-ttu-id="88bd0-116">Polecenie</span><span class="sxs-lookup"><span data-stu-id="88bd0-116">Command</span></span>                                             |
| --------------------------------------------------- |
| [<span data-ttu-id="88bd0-117">dotnet — Zbieranie liczników</span><span class="sxs-lookup"><span data-stu-id="88bd0-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="88bd0-118">dotnet-lista liczników</span><span class="sxs-lookup"><span data-stu-id="88bd0-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="88bd0-119">Monitor dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="88bd0-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="88bd0-120">dotnet-liczniki PS</span><span class="sxs-lookup"><span data-stu-id="88bd0-120">dotnet-counters ps</span></span>](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="88bd0-121">dotnet — Zbieranie liczników</span><span class="sxs-lookup"><span data-stu-id="88bd0-121">dotnet-counters collect</span></span>

<span data-ttu-id="88bd0-122">Okresowo Zbieraj wybrane wartości licznika i Eksportuj je do określonego formatu pliku na potrzeby przetwarzania końcowego.</span><span class="sxs-lookup"><span data-stu-id="88bd0-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="88bd0-123">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="88bd0-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a><span data-ttu-id="88bd0-124">Opcje</span><span class="sxs-lookup"><span data-stu-id="88bd0-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="88bd0-125">Identyfikator procesu, który ma być monitorowany.</span><span class="sxs-lookup"><span data-stu-id="88bd0-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="88bd0-126">Liczba sekund opóźnienia między aktualizacją wyświetlanych liczników</span><span class="sxs-lookup"><span data-stu-id="88bd0-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="88bd0-127">Rozdzielana spacjami lista liczników.</span><span class="sxs-lookup"><span data-stu-id="88bd0-127">A space separated list of counters.</span></span> <span data-ttu-id="88bd0-128">Liczniki można określić `provider_name[:counter_name]`.</span><span class="sxs-lookup"><span data-stu-id="88bd0-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="88bd0-129">Jeśli `provider_name` jest używany bez kwalifikowania `counter_name`, zostaną wyświetlone wszystkie liczniki.</span><span class="sxs-lookup"><span data-stu-id="88bd0-129">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="88bd0-130">Aby odnaleźć nazwy dostawcy i licznika, użyj polecenia [dotnet-Counters](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="88bd0-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="88bd0-131">Format tnie do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="88bd0-131">TThe format to be exported.</span></span> <span data-ttu-id="88bd0-132">Obecnie dostępne: CSV, JSON.</span><span class="sxs-lookup"><span data-stu-id="88bd0-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="88bd0-133">Nazwa pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="88bd0-133">The name of the output file.</span></span>

### <a name="examples"></a><span data-ttu-id="88bd0-134">Przykłady</span><span class="sxs-lookup"><span data-stu-id="88bd0-134">Examples</span></span>

- <span data-ttu-id="88bd0-135">Zbieraj wszystkie liczniki z interwałem odświeżania równym 3 sekund i Generuj wolumin CSV jako dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="88bd0-135">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="88bd0-136">dotnet-lista liczników</span><span class="sxs-lookup"><span data-stu-id="88bd0-136">dotnet-counters list</span></span>

<span data-ttu-id="88bd0-137">Wyświetla listę nazw liczników i opisów pogrupowanych według dostawcy.</span><span class="sxs-lookup"><span data-stu-id="88bd0-137">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="88bd0-138">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="88bd0-138">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="88bd0-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="88bd0-139">Example</span></span>

```console
> dotnet-counters list

    Showing well-known counters only. Specific processes may support additional counters.
    System.Runtime
        cpu-usage                    Amount of time the process has utilized the CPU (ms)
        working-set                  Amount of working set used by the process (MB)
        gc-heap-size                 Total heap size reported by the GC (MB)
        gen-0-gc-count               Number of Gen 0 GCs / sec
        gen-1-gc-count               Number of Gen 1 GCs / sec
        gen-2-gc-count               Number of Gen 2 GCs / sec
        exception-count              Number of Exceptions / sec
```

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="88bd0-140">Monitor dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="88bd0-140">dotnet-counters monitor</span></span>

<span data-ttu-id="88bd0-141">Wyświetla okresowe odświeżanie wartości wybranych liczników.</span><span class="sxs-lookup"><span data-stu-id="88bd0-141">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="88bd0-142">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="88bd0-142">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="88bd0-143">Opcje</span><span class="sxs-lookup"><span data-stu-id="88bd0-143">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="88bd0-144">Identyfikator procesu, który ma być monitorowany.</span><span class="sxs-lookup"><span data-stu-id="88bd0-144">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="88bd0-145">Liczba sekund opóźnienia między aktualizacją wyświetlanych liczników</span><span class="sxs-lookup"><span data-stu-id="88bd0-145">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="88bd0-146">Rozdzielana spacjami lista liczników.</span><span class="sxs-lookup"><span data-stu-id="88bd0-146">A space separated list of counters.</span></span> <span data-ttu-id="88bd0-147">Liczniki można określić `provider_name[:counter_name]`.</span><span class="sxs-lookup"><span data-stu-id="88bd0-147">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="88bd0-148">Jeśli `provider_name` jest używany bez kwalifikowania `counter_name`, zostaną wyświetlone wszystkie liczniki.</span><span class="sxs-lookup"><span data-stu-id="88bd0-148">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="88bd0-149">Aby odnaleźć nazwy dostawcy i licznika, użyj polecenia [dotnet-Counters](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="88bd0-149">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="88bd0-150">Przykłady</span><span class="sxs-lookup"><span data-stu-id="88bd0-150">Examples</span></span>

- <span data-ttu-id="88bd0-151">Monitoruj wszystkie liczniki z `System.Runtime` w interwałie odświeżania równym 3 sekund:</span><span class="sxs-lookup"><span data-stu-id="88bd0-151">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 System.Runtime

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      Working Set (MB)                            1982
      GC Heap Size (MB)                            811
      Gen 0 GC / second                             20
      Gen 1 GC / second                              4
      Gen 2 GC / second                              1
      Number of Exceptions / sec                     4
  ```

- <span data-ttu-id="88bd0-152">Monitoruj tylko użycie procesora CPU i rozmiar sterty GC na podstawie `System.Runtime`:</span><span class="sxs-lookup"><span data-stu-id="88bd0-152">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="88bd0-153">Monitoruj wartości `EventCounter` z `EventSource`zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="88bd0-153">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="88bd0-154">Aby uzyskać więcej informacji, zobacz [Samouczek: jak mierzyć wydajność dla bardzo częstych zdarzeń przy użyciu EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span><span class="sxs-lookup"><span data-stu-id="88bd0-154">For more information, see [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a><span data-ttu-id="88bd0-155">dotnet-liczniki PS</span><span class="sxs-lookup"><span data-stu-id="88bd0-155">dotnet-counters ps</span></span> 

<span data-ttu-id="88bd0-156">Wyświetl listę procesów dotnet, które mogą być monitorowane.</span><span class="sxs-lookup"><span data-stu-id="88bd0-156">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="88bd0-157">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="88bd0-157">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="88bd0-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="88bd0-158">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
