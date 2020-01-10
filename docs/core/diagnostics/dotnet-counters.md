---
title: dotnet-Counters — .NET Core
description: Dowiedz się, jak zainstalować i użyć narzędzia wiersza polecenia programu dotnet-Counter.
ms.date: 10/14/2019
ms.openlocfilehash: 10af451a8b1b4d8b27da1490b99b19a4359c860f
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740804"
---
# <a name="dotnet-counters"></a><span data-ttu-id="5b5ae-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="5b5ae-103">dotnet-counters</span></span>

<span data-ttu-id="5b5ae-104">**Ten artykuł dotyczy: ✓** .net Core 3,0 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="5b5ae-104">**This article applies to: ✓** .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="5b5ae-105">Zainstaluj dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="5b5ae-105">Install dotnet-counters</span></span>

<span data-ttu-id="5b5ae-106">Aby zainstalować najnowszą wersję wydania [pakietu NuGet](https://www.nuget.org/packages/dotnet-counters)`dotnet-counters`, użyj [Narzędzia dotnet Install](../tools/dotnet-tool-install.md) Command:</span><span class="sxs-lookup"><span data-stu-id="5b5ae-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="5b5ae-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="5b5ae-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="5b5ae-108">Opis</span><span class="sxs-lookup"><span data-stu-id="5b5ae-108">Description</span></span>

<span data-ttu-id="5b5ae-109">`dotnet-counters` to narzędzie do monitorowania wydajności dla monitorowania kondycji ad hoc i badania wydajności pierwszego poziomu.</span><span class="sxs-lookup"><span data-stu-id="5b5ae-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="5b5ae-110">Może obserwować wartości liczników wydajności, które są publikowane za pośrednictwem interfejsu API <xref:System.Diagnostics.Tracing.EventCounter>.</span><span class="sxs-lookup"><span data-stu-id="5b5ae-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="5b5ae-111">Można na przykład szybko monitorować elementy, takie jak użycie procesora CPU lub częstotliwość zgłaszania wyjątków w aplikacji .NET Core, aby sprawdzić, czy istnieją jakieś podejrzane informacje przed uzyskaniem większej wydajności, przy użyciu `PerfView` lub `dotnet-trace`.</span><span class="sxs-lookup"><span data-stu-id="5b5ae-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="5b5ae-112">Opcje</span><span class="sxs-lookup"><span data-stu-id="5b5ae-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="5b5ae-113">Wyświetla wersję narzędzia dotnet-Counters.</span><span class="sxs-lookup"><span data-stu-id="5b5ae-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="5b5ae-114">Wyświetla pomoc w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="5b5ae-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="5b5ae-115">Polecenia</span><span class="sxs-lookup"><span data-stu-id="5b5ae-115">Commands</span></span>

| <span data-ttu-id="5b5ae-116">Polecenie</span><span class="sxs-lookup"><span data-stu-id="5b5ae-116">Command</span></span>                                             |
| --------------------------------------------------- |
| [<span data-ttu-id="5b5ae-117">dotnet-lista liczników</span><span class="sxs-lookup"><span data-stu-id="5b5ae-117">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="5b5ae-118">Monitor dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="5b5ae-118">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |

## <a name="dotnet-counters-list"></a><span data-ttu-id="5b5ae-119">dotnet-lista liczników</span><span class="sxs-lookup"><span data-stu-id="5b5ae-119">dotnet-counters list</span></span>

<span data-ttu-id="5b5ae-120">Wyświetla listę nazw liczników i opisów pogrupowanych według dostawcy.</span><span class="sxs-lookup"><span data-stu-id="5b5ae-120">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="5b5ae-121">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="5b5ae-121">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="5b5ae-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b5ae-122">Example</span></span>

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

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="5b5ae-123">Monitor dotnet-Counters</span><span class="sxs-lookup"><span data-stu-id="5b5ae-123">dotnet-counters monitor</span></span>

<span data-ttu-id="5b5ae-124">Wyświetla okresowe odświeżanie wartości wybranych liczników.</span><span class="sxs-lookup"><span data-stu-id="5b5ae-124">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="5b5ae-125">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="5b5ae-125">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="5b5ae-126">Opcje</span><span class="sxs-lookup"><span data-stu-id="5b5ae-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="5b5ae-127">Identyfikator procesu, który ma być monitorowany.</span><span class="sxs-lookup"><span data-stu-id="5b5ae-127">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="5b5ae-128">Liczba sekund opóźnienia między aktualizacją wyświetlanych liczników</span><span class="sxs-lookup"><span data-stu-id="5b5ae-128">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="5b5ae-129">Rozdzielana spacjami lista liczników.</span><span class="sxs-lookup"><span data-stu-id="5b5ae-129">A space separated list of counters.</span></span> <span data-ttu-id="5b5ae-130">Liczniki można określić `provider_name[:counter_name]`.</span><span class="sxs-lookup"><span data-stu-id="5b5ae-130">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="5b5ae-131">Jeśli `provider_name` jest używany bez kwalifikowania `counter_name`, zostaną wyświetlone wszystkie liczniki.</span><span class="sxs-lookup"><span data-stu-id="5b5ae-131">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="5b5ae-132">Aby odnaleźć nazwy dostawcy i licznika, użyj polecenia [dotnet-Counters](#dotnet-counters-list) .</span><span class="sxs-lookup"><span data-stu-id="5b5ae-132">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="5b5ae-133">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5b5ae-133">Examples</span></span>

- <span data-ttu-id="5b5ae-134">Monitoruj wszystkie liczniki z `System.Runtime` w interwałie odświeżania równym 3 sekund:</span><span class="sxs-lookup"><span data-stu-id="5b5ae-134">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="5b5ae-135">Monitoruj tylko użycie procesora CPU i rozmiar sterty GC na podstawie `System.Runtime`:</span><span class="sxs-lookup"><span data-stu-id="5b5ae-135">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="5b5ae-136">Monitoruj wartości `EventCounter` z `EventSource`zdefiniowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="5b5ae-136">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="5b5ae-137">Aby uzyskać więcej informacji, zobacz [Samouczek: jak mierzyć wydajność dla bardzo częstych zdarzeń przy użyciu EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span><span class="sxs-lookup"><span data-stu-id="5b5ae-137">For more information, see [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
