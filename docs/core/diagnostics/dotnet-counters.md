---
title: dotnet-liczniki - .NET Core
description: Dowiedz się, jak zainstalować narzędzie wiersza polecenia dotnet-counter i używać go.
ms.date: 02/26/2020
ms.openlocfilehash: dc95297478784ca06fe442a939f8489a40b29da7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147181"
---
# <a name="dotnet-counters"></a><span data-ttu-id="55722-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="55722-103">dotnet-counters</span></span>

<span data-ttu-id="55722-104">**Ten artykuł dotyczy:** ✔️ .NET Core 3.0 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="55722-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="55722-105">Instalowanie liczników dotnet</span><span class="sxs-lookup"><span data-stu-id="55722-105">Install dotnet-counters</span></span>

<span data-ttu-id="55722-106">Aby zainstalować najnowszą `dotnet-counters` wersję [pakietu NuGet,](https://www.nuget.org/packages/dotnet-counters)użyj polecenia [instalacji narzędzia dotnet:](../tools/dotnet-tool-install.md)</span><span class="sxs-lookup"><span data-stu-id="55722-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="55722-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="55722-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="55722-108">Opis</span><span class="sxs-lookup"><span data-stu-id="55722-108">Description</span></span>

<span data-ttu-id="55722-109">`dotnet-counters`jest narzędziem monitorowania wydajności do monitorowania stanu zdrowia ad hoc i badania wydajności pierwszego poziomu.</span><span class="sxs-lookup"><span data-stu-id="55722-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="55722-110">Można obserwować wartości licznika wydajności, <xref:System.Diagnostics.Tracing.EventCounter> które są publikowane za pośrednictwem interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="55722-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="55722-111">Na przykład można szybko monitorować takie rzeczy, jak użycie procesora CPU lub szybkość wyjątków zgłaszanych w aplikacji .NET Core, aby sprawdzić, czy jest coś podejrzanego przed przejściem do poważniejszego badania wydajności przy użyciu `PerfView` lub `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="55722-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="55722-112">Opcje</span><span class="sxs-lookup"><span data-stu-id="55722-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="55722-113">Wyświetla wersję narzędzia dotnet-counters.</span><span class="sxs-lookup"><span data-stu-id="55722-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="55722-114">Pokazuje pomoc wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="55722-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="55722-115">Polecenia</span><span class="sxs-lookup"><span data-stu-id="55722-115">Commands</span></span>

| <span data-ttu-id="55722-116">Polecenie</span><span class="sxs-lookup"><span data-stu-id="55722-116">Command</span></span>                                             |
| --------------------------------------------------- |
| [<span data-ttu-id="55722-117">dotnet-liczniki zbierają</span><span class="sxs-lookup"><span data-stu-id="55722-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="55722-118">lista liczników dotnet</span><span class="sxs-lookup"><span data-stu-id="55722-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="55722-119">monitor dotnet-liczników</span><span class="sxs-lookup"><span data-stu-id="55722-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="55722-120">dotnet-liczniki ps</span><span class="sxs-lookup"><span data-stu-id="55722-120">dotnet-counters ps</span></span>](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="55722-121">dotnet-liczniki zbierają</span><span class="sxs-lookup"><span data-stu-id="55722-121">dotnet-counters collect</span></span>

<span data-ttu-id="55722-122">Okresowo zbieraj wybrane wartości liczników i eksportuj je do określonego formatu pliku do przetwarzania końcowego.</span><span class="sxs-lookup"><span data-stu-id="55722-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="55722-123">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="55722-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a><span data-ttu-id="55722-124">Opcje</span><span class="sxs-lookup"><span data-stu-id="55722-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="55722-125">Identyfikator procesu, który ma być monitorowany.</span><span class="sxs-lookup"><span data-stu-id="55722-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="55722-126">Liczba sekund opóźnienia między aktualizacją wyświetlanych liczników</span><span class="sxs-lookup"><span data-stu-id="55722-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="55722-127">Oddzielona spacjami lista liczników.</span><span class="sxs-lookup"><span data-stu-id="55722-127">A space separated list of counters.</span></span> <span data-ttu-id="55722-128">Można określić liczniki `provider_name[:counter_name]`.</span><span class="sxs-lookup"><span data-stu-id="55722-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="55722-129">Jeśli `provider_name` jest używany bez `counter_name`kwalifikacji, wyświetlane są wszystkie liczniki.</span><span class="sxs-lookup"><span data-stu-id="55722-129">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="55722-130">Aby odnaleźć nazwy dostawcy i liczników, użyj polecenia [listy liczników dotnet.](#dotnet-counters-list)</span><span class="sxs-lookup"><span data-stu-id="55722-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="55722-131">TFormat do wyeksportowania.</span><span class="sxs-lookup"><span data-stu-id="55722-131">TThe format to be exported.</span></span> <span data-ttu-id="55722-132">Obecnie dostępne: csv, json.</span><span class="sxs-lookup"><span data-stu-id="55722-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="55722-133">Nazwa pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="55722-133">The name of the output file.</span></span>

### <a name="examples"></a><span data-ttu-id="55722-134">Przykłady</span><span class="sxs-lookup"><span data-stu-id="55722-134">Examples</span></span>

- <span data-ttu-id="55722-135">Zbierz wszystkie liczniki w interwale odświeżania 3 sekund i wygeneruj csv jako wyjście:</span><span class="sxs-lookup"><span data-stu-id="55722-135">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="55722-136">lista liczników dotnet</span><span class="sxs-lookup"><span data-stu-id="55722-136">dotnet-counters list</span></span>

<span data-ttu-id="55722-137">Wyświetla listę nazw liczników i opisów pogrupowanych według dostawcy.</span><span class="sxs-lookup"><span data-stu-id="55722-137">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="55722-138">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="55722-138">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="55722-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="55722-139">Example</span></span>

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

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="55722-140">monitor dotnet-liczników</span><span class="sxs-lookup"><span data-stu-id="55722-140">dotnet-counters monitor</span></span>

<span data-ttu-id="55722-141">Wyświetla okresowo odświeżające wartości wybranych liczników.</span><span class="sxs-lookup"><span data-stu-id="55722-141">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="55722-142">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="55722-142">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="55722-143">Opcje</span><span class="sxs-lookup"><span data-stu-id="55722-143">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="55722-144">Identyfikator procesu, który ma być monitorowany.</span><span class="sxs-lookup"><span data-stu-id="55722-144">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="55722-145">Liczba sekund opóźnienia między aktualizacją wyświetlanych liczników</span><span class="sxs-lookup"><span data-stu-id="55722-145">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="55722-146">Oddzielona spacjami lista liczników.</span><span class="sxs-lookup"><span data-stu-id="55722-146">A space separated list of counters.</span></span> <span data-ttu-id="55722-147">Można określić liczniki `provider_name[:counter_name]`.</span><span class="sxs-lookup"><span data-stu-id="55722-147">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="55722-148">Jeśli `provider_name` jest używany bez `counter_name`kwalifikacji, wyświetlane są wszystkie liczniki.</span><span class="sxs-lookup"><span data-stu-id="55722-148">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="55722-149">Aby odnaleźć nazwy dostawcy i liczników, użyj polecenia [listy liczników dotnet.](#dotnet-counters-list)</span><span class="sxs-lookup"><span data-stu-id="55722-149">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="55722-150">Przykłady</span><span class="sxs-lookup"><span data-stu-id="55722-150">Examples</span></span>

- <span data-ttu-id="55722-151">Monitoruj wszystkie `System.Runtime` liczniki z 3-sekundowym interwałem odświeżania:</span><span class="sxs-lookup"><span data-stu-id="55722-151">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="55722-152">Monitoruj tylko użycie procesora `System.Runtime`i rozmiar sterty GC od:</span><span class="sxs-lookup"><span data-stu-id="55722-152">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="55722-153">Monitorowanie `EventCounter` wartości zdefiniowanych `EventSource`przez użytkownika .</span><span class="sxs-lookup"><span data-stu-id="55722-153">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="55722-154">Aby uzyskać więcej informacji, zobacz [Samouczek: Jak mierzyć wydajność bardzo częstych zdarzeń przy użyciu EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span><span class="sxs-lookup"><span data-stu-id="55722-154">For more information, see [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a><span data-ttu-id="55722-155">dotnet-liczniki ps</span><span class="sxs-lookup"><span data-stu-id="55722-155">dotnet-counters ps</span></span>

<span data-ttu-id="55722-156">Wyświetla listę procesów dotnet, które mogą być monitorowane.</span><span class="sxs-lookup"><span data-stu-id="55722-156">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="55722-157">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="55722-157">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="55722-158">Przykład</span><span class="sxs-lookup"><span data-stu-id="55722-158">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
