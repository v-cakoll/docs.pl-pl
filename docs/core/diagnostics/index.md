---
title: Omówienie narzędzi diagnostycznych — .NET Core
description: Przegląd narzędzi i technik dostępnych do diagnozowania aplikacji .NET Core.
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: dc64c03ee9c8cee6a5b3c5cc089b4a1a2c27f84a
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924785"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="64378-103">Jakie narzędzia diagnostyczne są dostępne w środowisku .NET Core?</span><span class="sxs-lookup"><span data-stu-id="64378-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="64378-104">Oprogramowanie nie zawsze zachowuje się w oczekiwany sposób, ale .NET Core ma narzędzia i interfejsy API, które ułatwią zdiagnozowanie tych problemów szybko i efektywnie.</span><span class="sxs-lookup"><span data-stu-id="64378-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="64378-105">Ten artykuł ułatwia znalezienie różnych potrzebnych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="64378-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="64378-106">Debugery zarządzane</span><span class="sxs-lookup"><span data-stu-id="64378-106">Managed debuggers</span></span>

<span data-ttu-id="64378-107">[Zarządzane debugery](managed-debuggers.md) umożliwiają korzystanie z programu.</span><span class="sxs-lookup"><span data-stu-id="64378-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="64378-108">Wstrzymywanie, przyrostowe wykonywanie, badanie i wznawianie zawiera szczegółowe informacje o zachowaniu kodu.</span><span class="sxs-lookup"><span data-stu-id="64378-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="64378-109">Debuger to pierwszy wybór służący do diagnozowania problemów funkcjonalnych, które można łatwo odtworzyć.</span><span class="sxs-lookup"><span data-stu-id="64378-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="64378-110">Rejestrowanie i śledzenie</span><span class="sxs-lookup"><span data-stu-id="64378-110">Logging and tracing</span></span>

<span data-ttu-id="64378-111">[Rejestrowanie i śledzenie](logging-tracing.md) to powiązane techniki.</span><span class="sxs-lookup"><span data-stu-id="64378-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="64378-112">Odnoszą się one do kodu instrumentacji do tworzenia plików dziennika.</span><span class="sxs-lookup"><span data-stu-id="64378-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="64378-113">Pliki rejestrują szczegóły działania programu.</span><span class="sxs-lookup"><span data-stu-id="64378-113">The files record the details of what a program does.</span></span> <span data-ttu-id="64378-114">Te szczegółowe informacje mogą służyć do diagnozowania najbardziej złożonych problemów.</span><span class="sxs-lookup"><span data-stu-id="64378-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="64378-115">W połączeniu z sygnaturami czasowymi te techniki są również przydatne w badaniach wydajności.</span><span class="sxs-lookup"><span data-stu-id="64378-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="64378-116">Testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="64378-116">Unit testing</span></span>

<span data-ttu-id="64378-117">[Testowanie jednostkowe](../testing/index.md) to kluczowy składnik ciągłej integracji i wdrażania wysokiej jakości oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="64378-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="64378-118">Testy jednostkowe zostały zaprojektowane w celu zapewnienia wczesnego ostrzegania w przypadku wystąpienia elementu.</span><span class="sxs-lookup"><span data-stu-id="64378-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="net-core-dotnet-diagnostic-global-tools"></a><span data-ttu-id="64378-119">Narzędzia diagnostyczne programu .NET Core dotnet Diagnostic</span><span class="sxs-lookup"><span data-stu-id="64378-119">.NET Core dotnet diagnostic Global Tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="64378-120">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="64378-120">dotnet-counters</span></span>

<span data-ttu-id="64378-121">[dotnet-Counters](dotnet-counters.md) to narzędzie do monitorowania wydajności służące do monitorowania kondycji pierwszego poziomu i badania wydajności.</span><span class="sxs-lookup"><span data-stu-id="64378-121">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="64378-122">Obserwuje wartości liczników wydajności publikowane za pośrednictwem <xref:System.Diagnostics.Tracing.EventCounter> interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="64378-122">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="64378-123">Można na przykład szybko monitorować elementy, takie jak użycie procesora CPU, lub częstotliwość zgłaszania wyjątków w aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="64378-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="64378-124">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="64378-124">dotnet-dump</span></span>

<span data-ttu-id="64378-125">Narzędzie [dotnet-dump](dotnet-dump.md) to sposób zbierania i analizowania zrzutów podstawowych systemów Windows i Linux bez natywnego debugera.</span><span class="sxs-lookup"><span data-stu-id="64378-125">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="64378-126">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="64378-126">dotnet-trace</span></span>

<span data-ttu-id="64378-127">Program .NET Core zawiera informacje o tym, w jaki sposób są `EventPipe` udostępniane dane diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="64378-127">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="64378-128">Narzędzie do [śledzenia dotnet](dotnet-trace.md) umożliwia korzystanie z interesujących danych profilowania z poziomu aplikacji, które mogą pomóc w scenariuszach, w których konieczne jest powolne działanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="64378-128">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="64378-129">Samouczki dotyczące diagnostyki platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="64378-129">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="64378-130">Debugowanie przecieku pamięci</span><span class="sxs-lookup"><span data-stu-id="64378-130">Debug a memory leak</span></span>

<span data-ttu-id="64378-131">[Samouczek: debugowanie przecieku pamięci](debug-memory-leak.md) przeprowadzi przez znalezienie przecieku pamięci.</span><span class="sxs-lookup"><span data-stu-id="64378-131">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="64378-132">Narzędzie [dotnet-Counters](dotnet-counters.md) służy do potwierdzenia przecieku i narzędzia [dotnet-dump](dotnet-dump.md) służy do diagnozowania wycieku.</span><span class="sxs-lookup"><span data-stu-id="64378-132">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>

### <a name="debug-high-cpu-usage"></a><span data-ttu-id="64378-133">Debuguj wysokie użycie procesora CPU</span><span class="sxs-lookup"><span data-stu-id="64378-133">Debug high CPU usage</span></span>

<span data-ttu-id="64378-134">[Samouczek: debugowanie dużego użycia procesora CPU](debug-highcpu.md) przeprowadzi Cię przez badanie wysokiego użycia procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="64378-134">[Tutorial: Debug high CPU usage](debug-highcpu.md) walks you through investigating high CPU usage.</span></span> <span data-ttu-id="64378-135">Za pomocą narzędzia [dotnet-Counters](dotnet-counters.md) można potwierdzić duże użycie procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="64378-135">It uses the [dotnet-counters](dotnet-counters.md) tool to confirm the high CPU usage.</span></span> <span data-ttu-id="64378-136">Następnie przeprowadzi Cię przez proces [śledzenia narzędzia do analizy wydajności ( `dotnet-trace` )](dotnet-trace.md) lub systemu Linux `perf` w celu zbierania i wyświetlania profilu użycia procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="64378-136">It then walks you through using [Trace for performance analysis utility (`dotnet-trace`)](dotnet-trace.md) or Linux `perf` to collect and view CPU usage profile.</span></span>

### <a name="debug-deadlock"></a><span data-ttu-id="64378-137">Zakleszczenie debugowania</span><span class="sxs-lookup"><span data-stu-id="64378-137">Debug deadlock</span></span>

<span data-ttu-id="64378-138">[Samouczek: zakleszczenie debugowania](debug-deadlock.md) pokazuje, w jaki sposób używać narzędzia [dotnet-dump](dotnet-dump.md) do badania wątków i blokad.</span><span class="sxs-lookup"><span data-stu-id="64378-138">[Tutorial: Debug deadlock](debug-deadlock.md) shows you how to use the [dotnet-dump](dotnet-dump.md) tool to investigate threads and locks.</span></span>
