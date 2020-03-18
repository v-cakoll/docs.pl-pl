---
title: Omówienie narzędzi diagnostycznych - .NET Core
description: Omówienie narzędzi i technik dostępnych do diagnozowania aplikacji .NET Core.
ms.date: 12/17/2019
ms.topic: overview
ms.openlocfilehash: 0a78ec6c88f5323104277cddea4480a5e13b4e41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79399050"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a><span data-ttu-id="ff7ac-103">Jakie narzędzia diagnostyczne są dostępne w .NET Core?</span><span class="sxs-lookup"><span data-stu-id="ff7ac-103">What diagnostic tools are available in .NET Core?</span></span>

<span data-ttu-id="ff7ac-104">Oprogramowanie nie zawsze zachowuje się tak, jak można się spodziewać, ale program .NET Core ma narzędzia i interfejsy API, które pomogą ci szybko i skutecznie zdiagnozować te problemy.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-104">Software doesn't always behave as you would expect, but .NET Core has tools and APIs that will help you diagnose these issues quickly and effectively.</span></span>

<span data-ttu-id="ff7ac-105">Ten artykuł pomoże Ci znaleźć różne narzędzia, których potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-105">This article helps you find the various tools you need.</span></span>

## <a name="managed-debuggers"></a><span data-ttu-id="ff7ac-106">Debugery zarządzane</span><span class="sxs-lookup"><span data-stu-id="ff7ac-106">Managed debuggers</span></span>

<span data-ttu-id="ff7ac-107">[Zarządzane debugerzki](managed-debuggers.md) umożliwiają interakcję z programem.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-107">[Managed debuggers](managed-debuggers.md) allow you to interact with your program.</span></span> <span data-ttu-id="ff7ac-108">Wstrzymywanie, stopniowe wykonywanie, badanie i wznawianie zapewnia wgląd w zachowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-108">Pausing, incrementally executing, examining,  and resuming gives you insight into the behavior of your code.</span></span> <span data-ttu-id="ff7ac-109">Debuger jest pierwszym wyborem do diagnozowania problemów funkcjonalnych, które można łatwo odtworzyć.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-109">A debugger is the first choice for diagnosing functional problems that can be easily reproduced.</span></span>

## <a name="logging-and-tracing"></a><span data-ttu-id="ff7ac-110">Rejestrowanie i śledzenie</span><span class="sxs-lookup"><span data-stu-id="ff7ac-110">Logging and tracing</span></span>

<span data-ttu-id="ff7ac-111">[Rejestrowanie i śledzenie](logging-tracing.md) są powiązanymi technikami.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-111">[Logging and tracing](logging-tracing.md) are related techniques.</span></span> <span data-ttu-id="ff7ac-112">Odnoszą się one do kodu instrumentastru, aby utworzyć pliki dziennika.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-112">They refer to instrumenting code to create log files.</span></span> <span data-ttu-id="ff7ac-113">Pliki rejestrują szczegóły tego, co robi program.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-113">The files record the details of what a program does.</span></span> <span data-ttu-id="ff7ac-114">Szczegóły te mogą być wykorzystane do diagnozowania najbardziej złożonych problemów.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-114">These details can be used to diagnose the most complex problems.</span></span> <span data-ttu-id="ff7ac-115">W połączeniu z znacznikami czasu techniki te są również cenne w badaniach wydajności.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-115">When combined with time stamps, these techniques are also valuable in performance investigations.</span></span>

## <a name="unit-testing"></a><span data-ttu-id="ff7ac-116">Testy jednostkowe</span><span class="sxs-lookup"><span data-stu-id="ff7ac-116">Unit testing</span></span>

<span data-ttu-id="ff7ac-117">[Testowanie jednostkowe](../testing/index.md) jest kluczowym elementem ciągłej integracji i wdrażania wysokiej jakości oprogramowania.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-117">[Unit testing](../testing/index.md) is a key component of continuous integration and deployment of high-quality software.</span></span> <span data-ttu-id="ff7ac-118">Testy jednostkowe mają na celu zapewnienie wczesnego ostrzegania po złamaniu czegoś.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-118">Unit tests are designed to give you an early warning when you break something.</span></span>

## <a name="net-core-dotnet-diagnostic-global-tools"></a><span data-ttu-id="ff7ac-119">Narzędzia globalne diagnostyki .NET Core dotnet</span><span class="sxs-lookup"><span data-stu-id="ff7ac-119">.NET Core dotnet diagnostic Global Tools</span></span>

### <a name="dotnet-counters"></a><span data-ttu-id="ff7ac-120">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="ff7ac-120">dotnet-counters</span></span>

<span data-ttu-id="ff7ac-121">[dotnet-counters](dotnet-counters.md) jest narzędziem do monitorowania wydajności do monitorowania kondycji pierwszego poziomu i badania wydajności.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-121">[dotnet-counters](dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span> <span data-ttu-id="ff7ac-122">Obserwuje wartości licznika wydajności opublikowane <xref:System.Diagnostics.Tracing.EventCounter> za pośrednictwem interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-122">It observes performance counter values published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="ff7ac-123">Na przykład można szybko monitorować takie rzeczy, jak użycie procesora CPU lub szybkość wyjątków zgłaszanych w aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-123">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application.</span></span>

### <a name="dotnet-dump"></a><span data-ttu-id="ff7ac-124">dotnet-dump</span><span class="sxs-lookup"><span data-stu-id="ff7ac-124">dotnet-dump</span></span>

<span data-ttu-id="ff7ac-125">Narzędzie [dotnet-dump](dotnet-dump.md) jest sposobem zbierania i analizowania zrzutów rdzenia systemu Windows i Linux bez natywnego debugera.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-125">The [dotnet-dump](dotnet-dump.md) tool is a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

### <a name="dotnet-trace"></a><span data-ttu-id="ff7ac-126">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="ff7ac-126">dotnet-trace</span></span>

<span data-ttu-id="ff7ac-127">.NET Core zawiera to, co nazywa się, `EventPipe` za pośrednictwem którego dane diagnostyczne są udostępniane.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-127">.NET Core includes what is called the `EventPipe` through which diagnostics data is exposed.</span></span> <span data-ttu-id="ff7ac-128">Narzędzie [dotnet-trace](dotnet-trace.md) umożliwia korzystanie z interesujących danych profilowania z aplikacji, które mogą pomóc w scenariuszach, w których należy roots powodować aplikacje działa wolno.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-128">The [dotnet-trace](dotnet-trace.md) tool allows you to consume interesting profiling data from your app that can help in scenarios where you need to root cause apps running slow.</span></span>

## <a name="net-core-diagnostics-tutorials"></a><span data-ttu-id="ff7ac-129">Samouczki dotyczące diagnostyki platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ff7ac-129">.NET Core diagnostics tutorials</span></span>

### <a name="debug-a-memory-leak"></a><span data-ttu-id="ff7ac-130">Debugowanie przecieku pamięci</span><span class="sxs-lookup"><span data-stu-id="ff7ac-130">Debug a memory leak</span></span>

<span data-ttu-id="ff7ac-131">[Samouczek: Debugowanie przeciek pamięci](debug-memory-leak.md) przechodzi przez znalezienie przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-131">[Tutorial: Debug a memory leak](debug-memory-leak.md) walks through finding a memory leak.</span></span> <span data-ttu-id="ff7ac-132">Narzędzie [dotnet-liczniki](dotnet-counters.md) służy do potwierdzenia wycieku i narzędzie [dotnet-dump](dotnet-dump.md) służy do diagnozowania wycieku.</span><span class="sxs-lookup"><span data-stu-id="ff7ac-132">The [dotnet-counters](dotnet-counters.md) tool is used to confirm the leak and the [dotnet-dump](dotnet-dump.md) tool is used to diagnose the leak.</span></span>
