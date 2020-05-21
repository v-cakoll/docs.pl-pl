---
title: Debugowanie ustawień konfiguracji profilowania
description: Informacje o ustawieniach czasu wykonywania, które konfigurują debugowanie i profilowanie dla aplikacji platformy .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 5efd0f776da4b7ce6ff7f3bdfda24feec6e00f79
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761996"
---
# <a name="run-time-configuration-options-for-debugging-and-profiling"></a><span data-ttu-id="53f3f-103">Opcje konfiguracji czasu wykonywania na potrzeby debugowania i profilowania</span><span class="sxs-lookup"><span data-stu-id="53f3f-103">Run-time configuration options for debugging and profiling</span></span>

## <a name="enable-diagnostics"></a><span data-ttu-id="53f3f-104">Włączanie diagnostyki</span><span class="sxs-lookup"><span data-stu-id="53f3f-104">Enable diagnostics</span></span>

- <span data-ttu-id="53f3f-105">Określa, czy debuger, profiler i Diagnostyka EventPipe są włączone lub wyłączone.</span><span class="sxs-lookup"><span data-stu-id="53f3f-105">Configures whether the debugger, the profiler, and EventPipe diagnostics are enabled or disabled.</span></span>
- <span data-ttu-id="53f3f-106">W przypadku pominięcia tego ustawienia Diagnostyka zostanie włączona.</span><span class="sxs-lookup"><span data-stu-id="53f3f-106">If you omit this setting, diagnostics are enabled.</span></span> <span data-ttu-id="53f3f-107">Jest to równoznaczne z ustawieniem wartości `1` .</span><span class="sxs-lookup"><span data-stu-id="53f3f-107">This is equivalent to setting the value to `1`.</span></span>

| | <span data-ttu-id="53f3f-108">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="53f3f-108">Setting name</span></span> | <span data-ttu-id="53f3f-109">Wartości</span><span class="sxs-lookup"><span data-stu-id="53f3f-109">Values</span></span> |
| - | - | - |
| <span data-ttu-id="53f3f-110">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="53f3f-110">**runtimeconfig.json**</span></span> | <span data-ttu-id="53f3f-111">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="53f3f-111">N/A</span></span> | <span data-ttu-id="53f3f-112">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="53f3f-112">N/A</span></span> |
| <span data-ttu-id="53f3f-113">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="53f3f-113">**Environment variable**</span></span> | `COMPlus_EnableDiagnostics` | <span data-ttu-id="53f3f-114">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="53f3f-114">`1` - enabled</span></span><br/><span data-ttu-id="53f3f-115">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="53f3f-115">`0` - disabled</span></span> |

## <a name="enable-profiling"></a><span data-ttu-id="53f3f-116">Włącz profilowanie</span><span class="sxs-lookup"><span data-stu-id="53f3f-116">Enable profiling</span></span>

- <span data-ttu-id="53f3f-117">Określa, czy profilowanie jest włączone dla aktualnie uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="53f3f-117">Configures whether profiling is enabled for the currently running process.</span></span>
- <span data-ttu-id="53f3f-118">Jeśli pominięto to ustawienie, profilowanie jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="53f3f-118">If you omit this setting, profiling is disabled.</span></span> <span data-ttu-id="53f3f-119">Jest to równoznaczne z ustawieniem wartości `0` .</span><span class="sxs-lookup"><span data-stu-id="53f3f-119">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="53f3f-120">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="53f3f-120">Setting name</span></span> | <span data-ttu-id="53f3f-121">Wartości</span><span class="sxs-lookup"><span data-stu-id="53f3f-121">Values</span></span> |
| - | - | - |
| <span data-ttu-id="53f3f-122">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="53f3f-122">**runtimeconfig.json**</span></span> | <span data-ttu-id="53f3f-123">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="53f3f-123">N/A</span></span> | <span data-ttu-id="53f3f-124">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="53f3f-124">N/A</span></span> |
| <span data-ttu-id="53f3f-125">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="53f3f-125">**Environment variable**</span></span> | `CORECLR_ENABLE_PROFILING` | <span data-ttu-id="53f3f-126">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="53f3f-126">`0` - disabled</span></span><br/><span data-ttu-id="53f3f-127">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="53f3f-127">`1` - enabled</span></span> |

## <a name="profiler-guid"></a><span data-ttu-id="53f3f-128">Identyfikator GUID profilera</span><span class="sxs-lookup"><span data-stu-id="53f3f-128">Profiler GUID</span></span>

- <span data-ttu-id="53f3f-129">Określa identyfikator GUID profilera do załadowania do aktualnie uruchomionego procesu.</span><span class="sxs-lookup"><span data-stu-id="53f3f-129">Specifies the GUID of the profiler to load into the currently running process.</span></span>

| | <span data-ttu-id="53f3f-130">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="53f3f-130">Setting name</span></span> | <span data-ttu-id="53f3f-131">Wartości</span><span class="sxs-lookup"><span data-stu-id="53f3f-131">Values</span></span> |
| - | - | - |
| <span data-ttu-id="53f3f-132">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="53f3f-132">**runtimeconfig.json**</span></span> | <span data-ttu-id="53f3f-133">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="53f3f-133">N/A</span></span> | <span data-ttu-id="53f3f-134">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="53f3f-134">N/A</span></span> |
| <span data-ttu-id="53f3f-135">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="53f3f-135">**Environment variable**</span></span> | `CORECLR_PROFILER` | <span data-ttu-id="53f3f-136">*ciąg — identyfikator GUID*</span><span class="sxs-lookup"><span data-stu-id="53f3f-136">*string-guid*</span></span> |

## <a name="profiler-location"></a><span data-ttu-id="53f3f-137">Lokalizacja profilera</span><span class="sxs-lookup"><span data-stu-id="53f3f-137">Profiler location</span></span>

- <span data-ttu-id="53f3f-138">Określa ścieżkę do pliku DLL profilera do załadowania do aktualnie uruchomionego procesu (lub 32-bitowego lub 64-bitowego procesu).</span><span class="sxs-lookup"><span data-stu-id="53f3f-138">Specifies the path to the profiler DLL to load into the currently running process (or 32-bit or 64-bit process).</span></span>
- <span data-ttu-id="53f3f-139">Jeśli ustawiono więcej niż jedną zmienną, pierwszeństwo mają zmienne specyficzne dla bitów.</span><span class="sxs-lookup"><span data-stu-id="53f3f-139">If more than one variable is set, the bitness-specific variables take precedence.</span></span> <span data-ttu-id="53f3f-140">Określają, która liczba bitów profilera ma zostać załadowana.</span><span class="sxs-lookup"><span data-stu-id="53f3f-140">They specify which bitness of profiler to load.</span></span>
- <span data-ttu-id="53f3f-141">Aby uzyskać więcej informacji, zobacz [Znajdowanie biblioteki profilera](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span><span class="sxs-lookup"><span data-stu-id="53f3f-141">For more information, see [Finding the profiler library](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/profiling/Profiler%20Loading.md).</span></span>

| | <span data-ttu-id="53f3f-142">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="53f3f-142">Setting name</span></span> | <span data-ttu-id="53f3f-143">Wartości</span><span class="sxs-lookup"><span data-stu-id="53f3f-143">Values</span></span> |
| - | - | - |
| <span data-ttu-id="53f3f-144">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="53f3f-144">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH` | <span data-ttu-id="53f3f-145">*ścieżka ciągu*</span><span class="sxs-lookup"><span data-stu-id="53f3f-145">*string-path*</span></span> |
| <span data-ttu-id="53f3f-146">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="53f3f-146">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_32` | <span data-ttu-id="53f3f-147">*ścieżka ciągu*</span><span class="sxs-lookup"><span data-stu-id="53f3f-147">*string-path*</span></span> |
| <span data-ttu-id="53f3f-148">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="53f3f-148">**Environment variable**</span></span> | `CORECLR_PROFILER_PATH_64` | <span data-ttu-id="53f3f-149">*ścieżka ciągu*</span><span class="sxs-lookup"><span data-stu-id="53f3f-149">*string-path*</span></span> |

## <a name="write-perf-map"></a><span data-ttu-id="53f3f-150">Zapisz mapę wydajności</span><span class="sxs-lookup"><span data-stu-id="53f3f-150">Write perf map</span></span>

- <span data-ttu-id="53f3f-151">Włącza lub wyłącza zapisywanie */tmp/perf-$PID. map* w systemach Linux.</span><span class="sxs-lookup"><span data-stu-id="53f3f-151">Enables or disables writing */tmp/perf-$pid.map* on Linux systems.</span></span>
- <span data-ttu-id="53f3f-152">Jeśli pominięto to ustawienie, zapisanie mapy wydajności jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="53f3f-152">If you omit this setting, writing the perf map is disabled.</span></span> <span data-ttu-id="53f3f-153">Jest to równoznaczne z ustawieniem wartości `0` .</span><span class="sxs-lookup"><span data-stu-id="53f3f-153">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="53f3f-154">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="53f3f-154">Setting name</span></span> | <span data-ttu-id="53f3f-155">Wartości</span><span class="sxs-lookup"><span data-stu-id="53f3f-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="53f3f-156">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="53f3f-156">**runtimeconfig.json**</span></span> | <span data-ttu-id="53f3f-157">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="53f3f-157">N/A</span></span> | <span data-ttu-id="53f3f-158">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="53f3f-158">N/A</span></span> |
| <span data-ttu-id="53f3f-159">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="53f3f-159">**Environment variable**</span></span> | `COMPlus_PerfMapEnabled` | <span data-ttu-id="53f3f-160">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="53f3f-160">`0` - disabled</span></span><br/><span data-ttu-id="53f3f-161">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="53f3f-161">`1` - enabled</span></span> |

## <a name="perf-log-markers"></a><span data-ttu-id="53f3f-162">Znaczniki dzienników wydajności</span><span class="sxs-lookup"><span data-stu-id="53f3f-162">Perf log markers</span></span>

- <span data-ttu-id="53f3f-163">Włącza lub wyłącza określony sygnał, który ma zostać zaakceptowany i zignorowany jako znacznik w dziennikach wydajności.</span><span class="sxs-lookup"><span data-stu-id="53f3f-163">Enables or disables the specified signal to be accepted and ignored as a marker in the perf logs.</span></span>
- <span data-ttu-id="53f3f-164">W przypadku pominięcia tego ustawienia określony sygnał nie zostanie zignorowany.</span><span class="sxs-lookup"><span data-stu-id="53f3f-164">If you omit this setting, the specified signal is not ignored.</span></span> <span data-ttu-id="53f3f-165">Jest to równoznaczne z ustawieniem wartości `0` .</span><span class="sxs-lookup"><span data-stu-id="53f3f-165">This is equivalent to setting the value to `0`.</span></span>

| | <span data-ttu-id="53f3f-166">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="53f3f-166">Setting name</span></span> | <span data-ttu-id="53f3f-167">Wartości</span><span class="sxs-lookup"><span data-stu-id="53f3f-167">Values</span></span> |
| - | - | - |
| <span data-ttu-id="53f3f-168">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="53f3f-168">**runtimeconfig.json**</span></span> | <span data-ttu-id="53f3f-169">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="53f3f-169">N/A</span></span> | <span data-ttu-id="53f3f-170">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="53f3f-170">N/A</span></span> |
| <span data-ttu-id="53f3f-171">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="53f3f-171">**Environment variable**</span></span> | `COMPlus_PerfMapIgnoreSignal` | <span data-ttu-id="53f3f-172">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="53f3f-172">`0` - disabled</span></span><br/><span data-ttu-id="53f3f-173">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="53f3f-173">`1` - enabled</span></span> |

> [!NOTE]
> <span data-ttu-id="53f3f-174">To ustawienie jest ignorowane, jeśli [COMPlus_PerfMapEnabled](#write-perf-map) jest pominięte lub ustawione na `0` (czyli wyłączone).</span><span class="sxs-lookup"><span data-stu-id="53f3f-174">This setting is ignored if [COMPlus_PerfMapEnabled](#write-perf-map) is omitted or set to `0` (that is, disabled).</span></span>
