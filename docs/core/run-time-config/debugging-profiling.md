---
title: Debugowanie ustawień konfiguracji profilowania
description: Informacje o ustawieniach czasu wykonywania, które konfigurują debugowanie i profilowanie dla aplikacji platformy .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802800"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="59d56-103">Opcje konfiguracji czasu wykonywania na potrzeby debugowania i profilowania</span><span class="sxs-lookup"><span data-stu-id="59d56-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="59d56-104">Włączanie diagnostyki</span><span class="sxs-lookup"><span data-stu-id="59d56-104">Enable diagnostics</span></span>

- <span data-ttu-id="59d56-105">Określa, czy debuger, profiler i Diagnostyka EventPipe są włączone lub wyłączone.</span><span class="sxs-lookup"><span data-stu-id="59d56-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="59d56-106">Wartość domyślna: włączone (`1`).</span><span class="sxs-lookup"><span data-stu-id="59d56-106">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="59d56-107">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="59d56-107">Setting name</span></span> | <span data-ttu-id="59d56-108">Wartości</span><span class="sxs-lookup"><span data-stu-id="59d56-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="59d56-109">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="59d56-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="59d56-110">N/D</span><span class="sxs-lookup"><span data-stu-id="59d56-110">N/A</span></span> | <span data-ttu-id="59d56-111">N/D</span><span class="sxs-lookup"><span data-stu-id="59d56-111">N/A</span></span> |
| <span data-ttu-id="59d56-112">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="59d56-112">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="59d56-113">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="59d56-113">`1` - enabled</span></span><br/><span data-ttu-id="59d56-114">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="59d56-114">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="59d56-115">Włącz profilowanie</span><span class="sxs-lookup"><span data-stu-id="59d56-115">Enable profiling</span></span>

- <span data-ttu-id="59d56-116">Określa, czy profilowanie jest włączone dla aktualnie uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="59d56-116">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="59d56-117">Domyślnie: wyłączone (`0`).</span><span class="sxs-lookup"><span data-stu-id="59d56-117">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="59d56-118">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="59d56-118">Setting name</span></span> | <span data-ttu-id="59d56-119">Wartości</span><span class="sxs-lookup"><span data-stu-id="59d56-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="59d56-120">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="59d56-120">**runtimeconfig.json**</span></span> | <span data-ttu-id="59d56-121">N/D</span><span class="sxs-lookup"><span data-stu-id="59d56-121">N/A</span></span> | <span data-ttu-id="59d56-122">N/D</span><span class="sxs-lookup"><span data-stu-id="59d56-122">N/A</span></span> |
| <span data-ttu-id="59d56-123">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="59d56-123">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="59d56-124">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="59d56-124">`0` - disabled</span></span><br/><span data-ttu-id="59d56-125">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="59d56-125">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="59d56-126">Identyfikator GUID profilera</span><span class="sxs-lookup"><span data-stu-id="59d56-126">Profiler GUID</span></span>

- <span data-ttu-id="59d56-127">Określa identyfikator GUID profilera do załadowania do aktualnie uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="59d56-127">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="59d56-128">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="59d56-128">Setting name</span></span> | <span data-ttu-id="59d56-129">Wartości</span><span class="sxs-lookup"><span data-stu-id="59d56-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="59d56-130">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="59d56-130">**runtimeconfig.json**</span></span> | <span data-ttu-id="59d56-131">N/D</span><span class="sxs-lookup"><span data-stu-id="59d56-131">N/A</span></span> | <span data-ttu-id="59d56-132">N/D</span><span class="sxs-lookup"><span data-stu-id="59d56-132">N/A</span></span> |
| <span data-ttu-id="59d56-133">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="59d56-133">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="59d56-134">*ciąg — identyfikator GUID*</span><span class="sxs-lookup"><span data-stu-id="59d56-134">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="59d56-135">Lokalizacja profilera</span><span class="sxs-lookup"><span data-stu-id="59d56-135">Profiler location</span></span>

- <span data-ttu-id="59d56-136">Określa ścieżkę do pliku DLL profilera do załadowania do aktualnie uruchomionego procesu (lub 32-bitowego lub 64-bitowego procesu).</span><span class="sxs-lookup"><span data-stu-id="59d56-136">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="59d56-137">Jeśli ustawiono więcej niż jedną zmienną, pierwszeństwo mają zmienne specyficzne dla bitów.</span><span class="sxs-lookup"><span data-stu-id="59d56-137">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="59d56-138">Określają, która liczba bitów profilera ma zostać załadowana.</span><span class="sxs-lookup"><span data-stu-id="59d56-138">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="59d56-139">Aby uzyskać więcej informacji, zobacz [Znajdowanie biblioteki profilera](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span><span class="sxs-lookup"><span data-stu-id="59d56-139">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="59d56-140">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="59d56-140">Setting name</span></span> | <span data-ttu-id="59d56-141">Wartości</span><span class="sxs-lookup"><span data-stu-id="59d56-141">Values</span></span> |
| - | - | - |
| <span data-ttu-id="59d56-142">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="59d56-142">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="59d56-143">*ścieżka ciągu*</span><span class="sxs-lookup"><span data-stu-id="59d56-143">*string-path*</span></span> |
| <span data-ttu-id="59d56-144">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="59d56-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="59d56-145">*ścieżka ciągu*</span><span class="sxs-lookup"><span data-stu-id="59d56-145">*string-path*</span></span> |
| <span data-ttu-id="59d56-146">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="59d56-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="59d56-147">*ścieżka ciągu*</span><span class="sxs-lookup"><span data-stu-id="59d56-147">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="59d56-148">Zapisz mapę wydajności</span><span class="sxs-lookup"><span data-stu-id="59d56-148">Write perf map</span></span>

- <span data-ttu-id="59d56-149">Włącza lub wyłącza zapisywanie */tmp/perf-$PID. map* w systemach Linux.</span><span class="sxs-lookup"><span data-stu-id="59d56-149">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="59d56-150">Domyślnie: wyłączone (`0`).</span><span class="sxs-lookup"><span data-stu-id="59d56-150">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="59d56-151">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="59d56-151">Setting name</span></span> | <span data-ttu-id="59d56-152">Wartości</span><span class="sxs-lookup"><span data-stu-id="59d56-152">Values</span></span> |
| - | - | - |
| <span data-ttu-id="59d56-153">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="59d56-153">**runtimeconfig.json**</span></span> | <span data-ttu-id="59d56-154">N/D</span><span class="sxs-lookup"><span data-stu-id="59d56-154">N/A</span></span> | <span data-ttu-id="59d56-155">N/D</span><span class="sxs-lookup"><span data-stu-id="59d56-155">N/A</span></span> |
| <span data-ttu-id="59d56-156">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="59d56-156">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="59d56-157">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="59d56-157">`0` - disabled</span></span><br/><span data-ttu-id="59d56-158">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="59d56-158">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="59d56-159">Znaczniki dzienników wydajności</span><span class="sxs-lookup"><span data-stu-id="59d56-159">Perf log markers</span></span>

- <span data-ttu-id="59d56-160">Gdy `COMPlus_PerfMapEnabled` jest ustawiona na `1`, włącza lub wyłącza określony sygnał, który ma być akceptowany i ignorowany jako znacznik w dziennikach wydajności.</span><span class="sxs-lookup"><span data-stu-id="59d56-160">When `COMPlus_PerfMapEnabled` is set to `1`, enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="59d56-161">Domyślnie: wyłączone (`0`).</span><span class="sxs-lookup"><span data-stu-id="59d56-161">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="59d56-162">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="59d56-162">Setting name</span></span> | <span data-ttu-id="59d56-163">Wartości</span><span class="sxs-lookup"><span data-stu-id="59d56-163">Values</span></span> |
| - | - | - |
| <span data-ttu-id="59d56-164">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="59d56-164">**runtimeconfig.json**</span></span> | <span data-ttu-id="59d56-165">N/D</span><span class="sxs-lookup"><span data-stu-id="59d56-165">N/A</span></span> | <span data-ttu-id="59d56-166">N/D</span><span class="sxs-lookup"><span data-stu-id="59d56-166">N/A</span></span> |
| <span data-ttu-id="59d56-167">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="59d56-167">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="59d56-168">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="59d56-168">`0` - disabled</span></span><br/><span data-ttu-id="59d56-169">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="59d56-169">`1` - enabled</span></span> |
