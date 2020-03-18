---
title: Debugowanie ustawień konfiguracji profilowania
description: Dowiedz się więcej o ustawieniach czasu wykonywania, które konfigurują debugowanie i profilowanie aplikacji .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: c57cfa7233f48def890ded3c9d589b7f268147df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74802800"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="ba4b9-103">Opcje konfiguracji w czasie wykonywania do debugowania i profilowania</span><span class="sxs-lookup"><span data-stu-id="ba4b9-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="ba4b9-104">Włączanie diagnostyki</span><span class="sxs-lookup"><span data-stu-id="ba4b9-104">Enable diagnostics</span></span>

- <span data-ttu-id="ba4b9-105">Konfiguruje, czy debuger, profiler i diagnostyka EventPipe są włączone lub wyłączone.</span><span class="sxs-lookup"><span data-stu-id="ba4b9-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="ba4b9-106">Domyślnie: Włączone`1`( ).</span><span class="sxs-lookup"><span data-stu-id="ba4b9-106">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="ba4b9-107">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="ba4b9-107">Setting name</span></span> | <span data-ttu-id="ba4b9-108">Wartości</span><span class="sxs-lookup"><span data-stu-id="ba4b9-108">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ba4b9-109">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba4b9-109">**runtimeconfig.json**</span></span> | <span data-ttu-id="ba4b9-110">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ba4b9-110">N/A</span></span> | <span data-ttu-id="ba4b9-111">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ba4b9-111">N/A</span></span> |
| <span data-ttu-id="ba4b9-112">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="ba4b9-112">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="ba4b9-113">`1`- włączona</span><span class="sxs-lookup"><span data-stu-id="ba4b9-113">`1` - enabled</span></span><br/><span data-ttu-id="ba4b9-114">`0`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="ba4b9-114">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="ba4b9-115">Włącz profilowanie</span><span class="sxs-lookup"><span data-stu-id="ba4b9-115">Enable profiling</span></span>

- <span data-ttu-id="ba4b9-116">Konfiguruje, czy profilowanie jest włączone dla aktualnie uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="ba4b9-116">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="ba4b9-117">Domyślnie: Wyłączone`0`( ).</span><span class="sxs-lookup"><span data-stu-id="ba4b9-117">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="ba4b9-118">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="ba4b9-118">Setting name</span></span> | <span data-ttu-id="ba4b9-119">Wartości</span><span class="sxs-lookup"><span data-stu-id="ba4b9-119">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ba4b9-120">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba4b9-120">**runtimeconfig.json**</span></span> | <span data-ttu-id="ba4b9-121">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ba4b9-121">N/A</span></span> | <span data-ttu-id="ba4b9-122">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ba4b9-122">N/A</span></span> |
| <span data-ttu-id="ba4b9-123">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="ba4b9-123">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="ba4b9-124">`0`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="ba4b9-124">`0` - disabled</span></span><br/><span data-ttu-id="ba4b9-125">`1`- włączona</span><span class="sxs-lookup"><span data-stu-id="ba4b9-125">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="ba4b9-126">Identyfikator GUID profilera</span><span class="sxs-lookup"><span data-stu-id="ba4b9-126">Profiler GUID</span></span>

- <span data-ttu-id="ba4b9-127">Określa identyfikator GUID profilera do załadowania do aktualnie uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="ba4b9-127">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="ba4b9-128">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="ba4b9-128">Setting name</span></span> | <span data-ttu-id="ba4b9-129">Wartości</span><span class="sxs-lookup"><span data-stu-id="ba4b9-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ba4b9-130">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba4b9-130">**runtimeconfig.json**</span></span> | <span data-ttu-id="ba4b9-131">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ba4b9-131">N/A</span></span> | <span data-ttu-id="ba4b9-132">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ba4b9-132">N/A</span></span> |
| <span data-ttu-id="ba4b9-133">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="ba4b9-133">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="ba4b9-134">*string-guid*</span><span class="sxs-lookup"><span data-stu-id="ba4b9-134">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="ba4b9-135">Lokalizacja profilera</span><span class="sxs-lookup"><span data-stu-id="ba4b9-135">Profiler location</span></span>

- <span data-ttu-id="ba4b9-136">Określa ścieżkę do dll profilera, aby załadować do aktualnie uruchomionego procesu (lub procesu 32-bitowego lub 64-bitowego).</span><span class="sxs-lookup"><span data-stu-id="ba4b9-136">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="ba4b9-137">Jeśli ustawiono więcej niż jedną zmienną, pierwszeństwo mają zmienne specyficzne dla bitness.</span><span class="sxs-lookup"><span data-stu-id="ba4b9-137">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="ba4b9-138">Określają one, która bitność profilera do załadowania.</span><span class="sxs-lookup"><span data-stu-id="ba4b9-138">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="ba4b9-139">Aby uzyskać więcej informacji, zobacz [Znajdowanie biblioteki profilerów](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span><span class="sxs-lookup"><span data-stu-id="ba4b9-139">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="ba4b9-140">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="ba4b9-140">Setting name</span></span> | <span data-ttu-id="ba4b9-141">Wartości</span><span class="sxs-lookup"><span data-stu-id="ba4b9-141">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ba4b9-142">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="ba4b9-142">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="ba4b9-143">*ścieżka ciągów*</span><span class="sxs-lookup"><span data-stu-id="ba4b9-143">*string-path*</span></span> |
| <span data-ttu-id="ba4b9-144">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="ba4b9-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="ba4b9-145">*ścieżka ciągów*</span><span class="sxs-lookup"><span data-stu-id="ba4b9-145">*string-path*</span></span> |
| <span data-ttu-id="ba4b9-146">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="ba4b9-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="ba4b9-147">*ścieżka ciągów*</span><span class="sxs-lookup"><span data-stu-id="ba4b9-147">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="ba4b9-148">Napisz mapę perf</span><span class="sxs-lookup"><span data-stu-id="ba4b9-148">Write perf map</span></span>

- <span data-ttu-id="ba4b9-149">Włącza lub wyłącza zapisywanie */tmp/perf-$pid.map* w systemach Linux.</span><span class="sxs-lookup"><span data-stu-id="ba4b9-149">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="ba4b9-150">Domyślnie: Wyłączone`0`( ).</span><span class="sxs-lookup"><span data-stu-id="ba4b9-150">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="ba4b9-151">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="ba4b9-151">Setting name</span></span> | <span data-ttu-id="ba4b9-152">Wartości</span><span class="sxs-lookup"><span data-stu-id="ba4b9-152">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ba4b9-153">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba4b9-153">**runtimeconfig.json**</span></span> | <span data-ttu-id="ba4b9-154">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ba4b9-154">N/A</span></span> | <span data-ttu-id="ba4b9-155">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ba4b9-155">N/A</span></span> |
| <span data-ttu-id="ba4b9-156">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="ba4b9-156">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="ba4b9-157">`0`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="ba4b9-157">`0` - disabled</span></span><br/><span data-ttu-id="ba4b9-158">`1`- włączona</span><span class="sxs-lookup"><span data-stu-id="ba4b9-158">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="ba4b9-159">Znaczniki dziennika Perf</span><span class="sxs-lookup"><span data-stu-id="ba4b9-159">Perf log markers</span></span>

- <span data-ttu-id="ba4b9-160">Gdy `COMPlus_PerfMapEnabled` jest `1`ustawiona na , włącza lub wyłącza określony sygnał, który ma być akceptowany i ignorowany jako znacznik w dziennikach perf.</span><span class="sxs-lookup"><span data-stu-id="ba4b9-160">When `COMPlus_PerfMapEnabled` is set to `1`, enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="ba4b9-161">Domyślnie: Wyłączone`0`( ).</span><span class="sxs-lookup"><span data-stu-id="ba4b9-161">Default: Disabled (`0`).</span></span>

| | <span data-ttu-id="ba4b9-162">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="ba4b9-162">Setting name</span></span> | <span data-ttu-id="ba4b9-163">Wartości</span><span class="sxs-lookup"><span data-stu-id="ba4b9-163">Values</span></span> |
| - | - | - |
| <span data-ttu-id="ba4b9-164">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="ba4b9-164">**runtimeconfig.json**</span></span> | <span data-ttu-id="ba4b9-165">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ba4b9-165">N/A</span></span> | <span data-ttu-id="ba4b9-166">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="ba4b9-166">N/A</span></span> |
| <span data-ttu-id="ba4b9-167">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="ba4b9-167">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="ba4b9-168">`0`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="ba4b9-168">`0` - disabled</span></span><br/><span data-ttu-id="ba4b9-169">`1`- włączona</span><span class="sxs-lookup"><span data-stu-id="ba4b9-169">`1` - enabled</span></span> |
