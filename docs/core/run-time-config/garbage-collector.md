---
title: Ustawienia konfiguracji modułu wyrzucania elementów bezużytecznych
description: Informacje o ustawieniach czasu wykonywania w celu skonfigurowania sposobu, w jaki moduł zbierający elementy bezużyteczne zarządza pamięcią dla aplikacji platformy .NET Core.
ms.date: 07/10/2020
ms.topic: reference
ms.openlocfilehash: 6ae5b7447fb0df4978ea9dcaa5e76fcc7a6cc4ca
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441413"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="e368c-103">Opcje konfiguracji czasu wykonywania dla wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="e368c-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="e368c-104">Ta strona zawiera informacje na temat ustawień modułu zbierającego elementy bezużyteczne (GC), które można zmienić w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e368c-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="e368c-105">Jeśli próbujesz osiągnąć szczytową wydajność uruchomionej aplikacji, rozważ użycie tych ustawień.</span><span class="sxs-lookup"><span data-stu-id="e368c-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="e368c-106">Jednak wartości domyślne zapewniają optymalną wydajność większości aplikacji w typowych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="e368c-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="e368c-107">Ustawienia są ułożone w grupach na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="e368c-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="e368c-108">Ustawienia w ramach każdej grupy są często używane w połączeniu ze sobą, aby osiągnąć konkretny wynik.</span><span class="sxs-lookup"><span data-stu-id="e368c-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="e368c-109">Te ustawienia mogą być również dynamicznie zmieniane przez aplikację w trakcie działania, więc wszystkie ustawione ustawienia czasu wykonywania mogą zostać zastąpione.</span><span class="sxs-lookup"><span data-stu-id="e368c-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="e368c-110">Niektóre ustawienia, takie jak [poziom opóźnienia](../../standard/garbage-collection/latency.md), są zazwyczaj ustawiane tylko za pomocą interfejsu API w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="e368c-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="e368c-111">Takie ustawienia zostały pominięte na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="e368c-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="e368c-112">W przypadku wartości liczbowych Użyj notacji dziesiętnej dla ustawień w *runtimeconfig.jsw* notacji plik i szesnastkowy dla ustawień zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="e368c-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="e368c-113">W przypadku wartości szesnastkowych można je określić z prefiksem "0x" lub bez niego.</span><span class="sxs-lookup"><span data-stu-id="e368c-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="e368c-114">Typy wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="e368c-114">Flavors of garbage collection</span></span>

<span data-ttu-id="e368c-115">Dwa główne typy wyrzucania elementów bezużytecznych to stacja robocza i serwer GC.</span><span class="sxs-lookup"><span data-stu-id="e368c-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="e368c-116">Aby uzyskać więcej informacji o różnicach między tymi dwoma, zobacz [stacja robocza i odzyskiwanie pamięci serwera](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="e368c-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="e368c-117">Podelementy wyrzucania elementów bezużytecznych są tła i niewspółbieżne.</span><span class="sxs-lookup"><span data-stu-id="e368c-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="e368c-118">Użyj następujących ustawień, aby wybrać typy wyrzucania elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="e368c-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="e368c-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="e368c-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="e368c-120">Określa, czy aplikacja używa wyrzucania elementów bezużytecznych stacji roboczej lub odzyskiwania pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="e368c-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="e368c-121">Domyślnie: wyrzucanie elementów bezużytecznych stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="e368c-121">Default: Workstation garbage collection.</span></span> <span data-ttu-id="e368c-122">Jest to równoznaczne z ustawieniem wartości `false` .</span><span class="sxs-lookup"><span data-stu-id="e368c-122">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="e368c-123">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="e368c-123">Setting name</span></span> | <span data-ttu-id="e368c-124">Wartości</span><span class="sxs-lookup"><span data-stu-id="e368c-124">Values</span></span> | <span data-ttu-id="e368c-125">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e368c-125">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e368c-126">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e368c-126">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="e368c-127">`false`-Stacja robocza</span><span class="sxs-lookup"><span data-stu-id="e368c-127">`false` - workstation</span></span><br/><span data-ttu-id="e368c-128">`true`— serwer</span><span class="sxs-lookup"><span data-stu-id="e368c-128">`true` - server</span></span> | <span data-ttu-id="e368c-129">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e368c-129">.NET Core 1.0</span></span> |
| <span data-ttu-id="e368c-130">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="e368c-130">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="e368c-131">`false`-Stacja robocza</span><span class="sxs-lookup"><span data-stu-id="e368c-131">`false` - workstation</span></span><br/><span data-ttu-id="e368c-132">`true`— serwer</span><span class="sxs-lookup"><span data-stu-id="e368c-132">`true` - server</span></span> | <span data-ttu-id="e368c-133">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e368c-133">.NET Core 1.0</span></span> |
| <span data-ttu-id="e368c-134">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-134">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="e368c-135">`0`-Stacja robocza</span><span class="sxs-lookup"><span data-stu-id="e368c-135">`0` - workstation</span></span><br/><span data-ttu-id="e368c-136">`1`— serwer</span><span class="sxs-lookup"><span data-stu-id="e368c-136">`1` - server</span></span> | <span data-ttu-id="e368c-137">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e368c-137">.NET Core 1.0</span></span> |
| <span data-ttu-id="e368c-138">**app.config .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e368c-138">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e368c-139">GCServer</span><span class="sxs-lookup"><span data-stu-id="e368c-139">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="e368c-140">`false`-Stacja robocza</span><span class="sxs-lookup"><span data-stu-id="e368c-140">`false` - workstation</span></span><br/><span data-ttu-id="e368c-141">`true`— serwer</span><span class="sxs-lookup"><span data-stu-id="e368c-141">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="e368c-142">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e368c-142">Examples</span></span>

<span data-ttu-id="e368c-143">*runtimeconfig.js* pliku:</span><span class="sxs-lookup"><span data-stu-id="e368c-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="e368c-144">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="e368c-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="e368c-145">System. GC. współbieżne/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="e368c-145">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="e368c-146">Określa, czy jest włączone wyrzucanie elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="e368c-146">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="e368c-147">Domyślne: Użyj w tle GC.</span><span class="sxs-lookup"><span data-stu-id="e368c-147">Default: Use background GC.</span></span> <span data-ttu-id="e368c-148">Jest to równoznaczne z ustawieniem wartości `true` .</span><span class="sxs-lookup"><span data-stu-id="e368c-148">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="e368c-149">Aby uzyskać więcej informacji, zobacz [wyrzucanie elementów bezużytecznych w tle](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="e368c-149">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="e368c-150">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="e368c-150">Setting name</span></span> | <span data-ttu-id="e368c-151">Wartości</span><span class="sxs-lookup"><span data-stu-id="e368c-151">Values</span></span> | <span data-ttu-id="e368c-152">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e368c-152">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e368c-153">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e368c-153">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="e368c-154">`true`-w tle GC</span><span class="sxs-lookup"><span data-stu-id="e368c-154">`true` - background GC</span></span><br/><span data-ttu-id="e368c-155">`false`-niewspółbieżne GC</span><span class="sxs-lookup"><span data-stu-id="e368c-155">`false` - non-concurrent GC</span></span> | <span data-ttu-id="e368c-156">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e368c-156">.NET Core 1.0</span></span> |
| <span data-ttu-id="e368c-157">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="e368c-157">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="e368c-158">`true`-w tle GC</span><span class="sxs-lookup"><span data-stu-id="e368c-158">`true` - background GC</span></span><br/><span data-ttu-id="e368c-159">`false`-niewspółbieżne GC</span><span class="sxs-lookup"><span data-stu-id="e368c-159">`false` - non-concurrent GC</span></span> | <span data-ttu-id="e368c-160">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e368c-160">.NET Core 1.0</span></span> |
| <span data-ttu-id="e368c-161">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-161">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="e368c-162">`1`-w tle GC</span><span class="sxs-lookup"><span data-stu-id="e368c-162">`1` - background GC</span></span><br/><span data-ttu-id="e368c-163">`0`-niewspółbieżne GC</span><span class="sxs-lookup"><span data-stu-id="e368c-163">`0` - non-concurrent GC</span></span> | <span data-ttu-id="e368c-164">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e368c-164">.NET Core 1.0</span></span> |
| <span data-ttu-id="e368c-165">**app.config .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e368c-165">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e368c-166">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="e368c-166">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="e368c-167">`true`-w tle GC</span><span class="sxs-lookup"><span data-stu-id="e368c-167">`true` - background GC</span></span><br/><span data-ttu-id="e368c-168">`false`-niewspółbieżne GC</span><span class="sxs-lookup"><span data-stu-id="e368c-168">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="e368c-169">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e368c-169">Examples</span></span>

<span data-ttu-id="e368c-170">*runtimeconfig.js* pliku:</span><span class="sxs-lookup"><span data-stu-id="e368c-170">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="e368c-171">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="e368c-171">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="e368c-172">Zarządzanie użyciem zasobów</span><span class="sxs-lookup"><span data-stu-id="e368c-172">Manage resource usage</span></span>

<span data-ttu-id="e368c-173">Ustawienia opisane w tej sekcji służą do zarządzania użyciem pamięci i procesora modułu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e368c-173">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="e368c-174">Aby uzyskać więcej informacji na temat niektórych z tych ustawień, zapoznaj się z wpisem na blogu centrum [robocze i serwer GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .</span><span class="sxs-lookup"><span data-stu-id="e368c-174">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="e368c-175">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="e368c-175">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="e368c-176">Ogranicza liczbę stert utworzonych przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e368c-176">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="e368c-177">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="e368c-177">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="e368c-178">Jeśli [koligacja procesora GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) jest włączona, co jest ustawieniem domyślnym, licznik sterty ustawia `n` sterty/wątki skoligacony GC na pierwszy `n` procesor.</span><span class="sxs-lookup"><span data-stu-id="e368c-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="e368c-179">(Użyj [koligacji maska](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) lub ustawienia [zakresów koligacji](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) , aby określić, które procesory mają być koligacji).</span><span class="sxs-lookup"><span data-stu-id="e368c-179">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="e368c-180">Jeśli [koligacja procesora GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) jest wyłączona, to ustawienie ogranicza liczbę stert GC.</span><span class="sxs-lookup"><span data-stu-id="e368c-180">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="e368c-181">Aby uzyskać więcej informacji, zobacz [uwagi GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="e368c-181">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="e368c-182">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="e368c-182">Setting name</span></span> | <span data-ttu-id="e368c-183">Wartości</span><span class="sxs-lookup"><span data-stu-id="e368c-183">Values</span></span> | <span data-ttu-id="e368c-184">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e368c-184">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e368c-185">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e368c-185">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="e368c-186">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="e368c-186">*decimal value*</span></span> | <span data-ttu-id="e368c-187">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e368c-187">.NET Core 3.0</span></span> |
| <span data-ttu-id="e368c-188">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-188">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="e368c-189">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="e368c-189">*hexadecimal value*</span></span> | <span data-ttu-id="e368c-190">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e368c-190">.NET Core 3.0</span></span> |
| <span data-ttu-id="e368c-191">**app.config .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e368c-191">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e368c-192">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="e368c-192">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="e368c-193">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="e368c-193">*decimal value*</span></span> | <span data-ttu-id="e368c-194">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="e368c-194">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="e368c-195">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e368c-195">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapCount": 16
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="e368c-196">Jeśli ustawiasz opcję w *runtimeconfig.jsna*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="e368c-196">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="e368c-197">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="e368c-197">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="e368c-198">Na przykład aby ograniczyć liczbę stert do 16, wartości dla pliku JSON i 0x10 lub 10 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="e368c-198">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="e368c-199">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="e368c-199">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="e368c-200">Określa dokładne procesory, które powinny być używane przez wątki modułu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e368c-200">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="e368c-201">Jeśli [koligacja procesora GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) jest wyłączona, to ustawienie jest ignorowane.</span><span class="sxs-lookup"><span data-stu-id="e368c-201">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="e368c-202">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="e368c-202">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="e368c-203">Wartość jest maską bitową, która definiuje procesory, które są dostępne dla procesu.</span><span class="sxs-lookup"><span data-stu-id="e368c-203">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="e368c-204">Na przykład wartość dziesiętna 1023 (lub wartość szesnastkowa 0x3FF lub 3FF, jeśli używana jest zmienna środowiskowa) to 0011 1111 1111 w notacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="e368c-204">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="e368c-205">Oznacza to, że pierwsze 10 procesorów ma być używany.</span><span class="sxs-lookup"><span data-stu-id="e368c-205">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="e368c-206">Aby określić następne 10 procesorów, czyli procesorów 10-19, określ wartość dziesiętną 1047552 (lub wartość szesnastkową 0xFFC00 lub FFC00), która jest równoważna z wartością binarną 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="e368c-206">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="e368c-207">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="e368c-207">Setting name</span></span> | <span data-ttu-id="e368c-208">Wartości</span><span class="sxs-lookup"><span data-stu-id="e368c-208">Values</span></span> | <span data-ttu-id="e368c-209">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e368c-209">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e368c-210">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e368c-210">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="e368c-211">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="e368c-211">*decimal value*</span></span> | <span data-ttu-id="e368c-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e368c-212">.NET Core 3.0</span></span> |
| <span data-ttu-id="e368c-213">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-213">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="e368c-214">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="e368c-214">*hexadecimal value*</span></span> | <span data-ttu-id="e368c-215">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e368c-215">.NET Core 3.0</span></span> |
| <span data-ttu-id="e368c-216">**app.config .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e368c-216">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e368c-217">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="e368c-217">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="e368c-218">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="e368c-218">*decimal value*</span></span> | <span data-ttu-id="e368c-219">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="e368c-219">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="e368c-220">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e368c-220">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="e368c-221">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="e368c-221">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="e368c-222">Określa listę procesorów, które mają być używane na potrzeby wątków modułu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="e368c-222">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="e368c-223">To ustawienie jest podobne do [System. GC. HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), z tą różnicą, że umożliwia określenie więcej niż 64 procesorów.</span><span class="sxs-lookup"><span data-stu-id="e368c-223">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="e368c-224">W przypadku systemów operacyjnych Windows należy prefiksować numer procesora lub zakres z odpowiednią [grupą procesorów CPU](/windows/win32/procthread/processor-groups), na przykład "0:1-10, 0:12, 1:50-52, 1:70".</span><span class="sxs-lookup"><span data-stu-id="e368c-224">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="e368c-225">Jeśli [koligacja procesora GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) jest wyłączona, to ustawienie jest ignorowane.</span><span class="sxs-lookup"><span data-stu-id="e368c-225">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="e368c-226">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="e368c-226">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="e368c-227">Aby uzyskać więcej informacji, zobacz temat [Zapewnianie lepszej konfiguracji procesora dla GC na maszynach z > 64 procesorów CPU](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="e368c-227">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="e368c-228">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="e368c-228">Setting name</span></span> | <span data-ttu-id="e368c-229">Wartości</span><span class="sxs-lookup"><span data-stu-id="e368c-229">Values</span></span> | <span data-ttu-id="e368c-230">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e368c-230">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e368c-231">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e368c-231">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="e368c-232">Rozdzielana przecinkami lista numerów procesorów lub zakresów numerów procesorów.</span><span class="sxs-lookup"><span data-stu-id="e368c-232">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="e368c-233">Przykład UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="e368c-233">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="e368c-234">Przykład systemu Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="e368c-234">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="e368c-235">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e368c-235">.NET Core 3.0</span></span> |
| <span data-ttu-id="e368c-236">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-236">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="e368c-237">Rozdzielana przecinkami lista numerów procesorów lub zakresów numerów procesorów.</span><span class="sxs-lookup"><span data-stu-id="e368c-237">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="e368c-238">Przykład UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="e368c-238">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="e368c-239">Przykład systemu Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="e368c-239">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="e368c-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e368c-240">.NET Core 3.0</span></span> |

<span data-ttu-id="e368c-241">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e368c-241">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="e368c-242">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="e368c-242">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="e368c-243">Określa, czy moduł wyrzucania elementów bezużytecznych używa [grup CPU](/windows/win32/procthread/processor-groups) , czy nie.</span><span class="sxs-lookup"><span data-stu-id="e368c-243">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="e368c-244">Gdy 64-bitowy komputer z systemem Windows ma wiele grup CPU, oznacza to, że istnieje więcej niż 64 procesorów, włączając ten element rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach CPU.</span><span class="sxs-lookup"><span data-stu-id="e368c-244">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="e368c-245">Moduł wyrzucania elementów bezużytecznych używa wszystkich rdzeni do tworzenia i równoważenia sterty.</span><span class="sxs-lookup"><span data-stu-id="e368c-245">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="e368c-246">Stosuje się do wyrzucania elementów bezużytecznych serwera w 64-bitowych systemach operacyjnych Windows.</span><span class="sxs-lookup"><span data-stu-id="e368c-246">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="e368c-247">Domyślnie: GC nie rozciąga się między grupami CPU.</span><span class="sxs-lookup"><span data-stu-id="e368c-247">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="e368c-248">Jest to równoznaczne z ustawieniem wartości `0` .</span><span class="sxs-lookup"><span data-stu-id="e368c-248">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="e368c-249">Aby uzyskać więcej informacji, zobacz temat [Zapewnianie lepszej konfiguracji procesora dla GC na maszynach z > 64 procesorów CPU](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="e368c-249">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="e368c-250">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="e368c-250">Setting name</span></span> | <span data-ttu-id="e368c-251">Wartości</span><span class="sxs-lookup"><span data-stu-id="e368c-251">Values</span></span> | <span data-ttu-id="e368c-252">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e368c-252">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e368c-253">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e368c-253">**runtimeconfig.json**</span></span> | <span data-ttu-id="e368c-254">Brak</span><span class="sxs-lookup"><span data-stu-id="e368c-254">N/A</span></span> | <span data-ttu-id="e368c-255">Brak</span><span class="sxs-lookup"><span data-stu-id="e368c-255">N/A</span></span> | <span data-ttu-id="e368c-256">Brak</span><span class="sxs-lookup"><span data-stu-id="e368c-256">N/A</span></span> |
| <span data-ttu-id="e368c-257">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-257">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="e368c-258">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="e368c-258">`0` - disabled</span></span><br/><span data-ttu-id="e368c-259">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="e368c-259">`1` - enabled</span></span> | <span data-ttu-id="e368c-260">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e368c-260">.NET Core 1.0</span></span> |
| <span data-ttu-id="e368c-261">**app.config .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e368c-261">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e368c-262">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="e368c-262">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="e368c-263">`false`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="e368c-263">`false` - disabled</span></span><br/><span data-ttu-id="e368c-264">`true`-włączone</span><span class="sxs-lookup"><span data-stu-id="e368c-264">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="e368c-265">Aby skonfigurować środowisko uruchomieniowe języka wspólnego (CLR) do dystrybucji wątków z puli wątków we wszystkich grupach procesora, Włącz opcję [Thread_UseAllCpuGroups elementu](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="e368c-265">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="e368c-266">W przypadku aplikacji platformy .NET Core można włączyć tę opcję, ustawiając wartość `COMPlus_Thread_UseAllCpuGroups` zmiennej środowiskowej na `1` .</span><span class="sxs-lookup"><span data-stu-id="e368c-266">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="e368c-267">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="e368c-267">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="e368c-268">Określa, czy *koligacji* wątki odzyskiwania pamięci z procesorami.</span><span class="sxs-lookup"><span data-stu-id="e368c-268">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="e368c-269">Aby koligacji wątek GC, oznacza to, że można go uruchomić tylko w określonym procesorze CPU.</span><span class="sxs-lookup"><span data-stu-id="e368c-269">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="e368c-270">Sterta jest tworzona dla każdego wątku GC.</span><span class="sxs-lookup"><span data-stu-id="e368c-270">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="e368c-271">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="e368c-271">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="e368c-272">Domyślnie: koligacji wątki odzyskiwania pamięci z procesorami.</span><span class="sxs-lookup"><span data-stu-id="e368c-272">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="e368c-273">Jest to równoznaczne z ustawieniem wartości `false` .</span><span class="sxs-lookup"><span data-stu-id="e368c-273">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="e368c-274">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="e368c-274">Setting name</span></span> | <span data-ttu-id="e368c-275">Wartości</span><span class="sxs-lookup"><span data-stu-id="e368c-275">Values</span></span> | <span data-ttu-id="e368c-276">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e368c-276">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e368c-277">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e368c-277">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="e368c-278">`false`-koligacji</span><span class="sxs-lookup"><span data-stu-id="e368c-278">`false` - affinitize</span></span><br/><span data-ttu-id="e368c-279">`true`-nie koligacji</span><span class="sxs-lookup"><span data-stu-id="e368c-279">`true` - don't affinitize</span></span> | <span data-ttu-id="e368c-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e368c-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="e368c-281">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-281">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="e368c-282">`0`-koligacji</span><span class="sxs-lookup"><span data-stu-id="e368c-282">`0` - affinitize</span></span><br/><span data-ttu-id="e368c-283">`1`-nie koligacji</span><span class="sxs-lookup"><span data-stu-id="e368c-283">`1` - don't affinitize</span></span> | <span data-ttu-id="e368c-284">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e368c-284">.NET Core 3.0</span></span> |
| <span data-ttu-id="e368c-285">**app.config .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e368c-285">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e368c-286">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="e368c-286">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="e368c-287">`false`-koligacji</span><span class="sxs-lookup"><span data-stu-id="e368c-287">`false` - affinitize</span></span><br/><span data-ttu-id="e368c-288">`true`-nie koligacji</span><span class="sxs-lookup"><span data-stu-id="e368c-288">`true` - don't affinitize</span></span> | <span data-ttu-id="e368c-289">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="e368c-289">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="e368c-290">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e368c-290">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="e368c-291">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="e368c-291">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="e368c-292">Określa maksymalny rozmiar zatwierdzeń w bajtach dla sterty GC i księgowości GC.</span><span class="sxs-lookup"><span data-stu-id="e368c-292">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="e368c-293">To ustawienie dotyczy tylko komputerów 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="e368c-293">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="e368c-294">To ustawienie jest ignorowane, jeśli skonfigurowano [limity sterty dla poszczególnych obiektów](#per-object-heap-limits) .</span><span class="sxs-lookup"><span data-stu-id="e368c-294">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="e368c-295">Wartość domyślna, która stosuje się tylko w niektórych przypadkach, jest większa niż 20 MB lub 75% limitu pamięci w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="e368c-295">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="e368c-296">Wartość domyślna ma zastosowanie, jeśli:</span><span class="sxs-lookup"><span data-stu-id="e368c-296">The default value applies if:</span></span>

  - <span data-ttu-id="e368c-297">Proces jest uruchomiony wewnątrz kontenera o określonym limicie pamięci.</span><span class="sxs-lookup"><span data-stu-id="e368c-297">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="e368c-298">Nie ustawiono wartości [System. GC. HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) .</span><span class="sxs-lookup"><span data-stu-id="e368c-298">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="e368c-299">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="e368c-299">Setting name</span></span> | <span data-ttu-id="e368c-300">Wartości</span><span class="sxs-lookup"><span data-stu-id="e368c-300">Values</span></span> | <span data-ttu-id="e368c-301">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e368c-301">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e368c-302">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e368c-302">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="e368c-303">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="e368c-303">*decimal value*</span></span> | <span data-ttu-id="e368c-304">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e368c-304">.NET Core 3.0</span></span> |
| <span data-ttu-id="e368c-305">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-305">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="e368c-306">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="e368c-306">*hexadecimal value*</span></span> | <span data-ttu-id="e368c-307">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e368c-307">.NET Core 3.0</span></span> |

<span data-ttu-id="e368c-308">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e368c-308">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimit": 209715200
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="e368c-309">Jeśli ustawiasz opcję w *runtimeconfig.jsna*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="e368c-309">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="e368c-310">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="e368c-310">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="e368c-311">Na przykład aby określić stały limit sterty wynoszący 200 mebibytes (MiB), wartości byłyby 209715200 dla pliku JSON i 0xC800000 lub C800000 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="e368c-311">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="e368c-312">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="e368c-312">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="e368c-313">Określa dozwolone użycie sterty GC jako procent całkowitej ilości pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="e368c-313">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="e368c-314">Jeśli zostanie również ustawiona wartość [System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) , to ustawienie jest ignorowane.</span><span class="sxs-lookup"><span data-stu-id="e368c-314">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="e368c-315">To ustawienie dotyczy tylko komputerów 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="e368c-315">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="e368c-316">Jeśli proces jest uruchomiony wewnątrz kontenera o określonym limicie pamięci, wartość procentowa jest obliczana jako wartość procentowa tego limitu pamięci.</span><span class="sxs-lookup"><span data-stu-id="e368c-316">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="e368c-317">To ustawienie jest ignorowane, jeśli skonfigurowano [limity sterty dla poszczególnych obiektów](#per-object-heap-limits) .</span><span class="sxs-lookup"><span data-stu-id="e368c-317">This setting is ignored if the [Per-object-heap limits](#per-object-heap-limits) are configured.</span></span>
- <span data-ttu-id="e368c-318">Wartość domyślna, która jest stosowana tylko w niektórych przypadkach, jest mniejsza z 20 MB lub 75% limitu pamięci dla kontenera.</span><span class="sxs-lookup"><span data-stu-id="e368c-318">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="e368c-319">Wartość domyślna ma zastosowanie, jeśli:</span><span class="sxs-lookup"><span data-stu-id="e368c-319">The default value applies if:</span></span>

  - <span data-ttu-id="e368c-320">Proces jest uruchomiony wewnątrz kontenera o określonym limicie pamięci.</span><span class="sxs-lookup"><span data-stu-id="e368c-320">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="e368c-321">Nie ustawiono wartości [System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) .</span><span class="sxs-lookup"><span data-stu-id="e368c-321">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="e368c-322">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="e368c-322">Setting name</span></span> | <span data-ttu-id="e368c-323">Wartości</span><span class="sxs-lookup"><span data-stu-id="e368c-323">Values</span></span> | <span data-ttu-id="e368c-324">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e368c-324">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e368c-325">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e368c-325">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="e368c-326">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="e368c-326">*decimal value*</span></span> | <span data-ttu-id="e368c-327">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e368c-327">.NET Core 3.0</span></span> |
| <span data-ttu-id="e368c-328">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-328">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="e368c-329">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="e368c-329">*hexadecimal value*</span></span> | <span data-ttu-id="e368c-330">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e368c-330">.NET Core 3.0</span></span> |

<span data-ttu-id="e368c-331">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e368c-331">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapHardLimitPercent": 30
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="e368c-332">Jeśli ustawiasz opcję w *runtimeconfig.jsna*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="e368c-332">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="e368c-333">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="e368c-333">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="e368c-334">Na przykład aby ograniczyć użycie sterty do 30%, wartości byłyby 30 dla pliku JSON i 0x1E lub 1E dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="e368c-334">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="per-object-heap-limits"></a><span data-ttu-id="e368c-335">Limity sterty dla poszczególnych obiektów</span><span class="sxs-lookup"><span data-stu-id="e368c-335">Per-object-heap limits</span></span>

<span data-ttu-id="e368c-336">Można określić możliwość użycia sterty w pamięci podręcznej na podstawie sterty dla poszczególnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="e368c-336">You can specify the GC's allowable heap usage on a per-object-heap basis.</span></span> <span data-ttu-id="e368c-337">Różne sterty to sterta dużego obiektu (LOH), sterta małego obiektu (raport o niewielkich obiektach) i przypięty stos obiektów (POH).</span><span class="sxs-lookup"><span data-stu-id="e368c-337">The different heaps are the large object heap (LOH), small object heap (SOH), and pinned object heap (POH).</span></span>

#### <a name="complus_gcheaphardlimitsoh-complus_gcheaphardlimitloh-complus_gcheaphardlimitpoh"></a><span data-ttu-id="e368c-338">COMPLUS_GCHeapHardLimitSOH, COMPLUS_GCHeapHardLimitLOH, COMPLUS_GCHeapHardLimitPOH</span><span class="sxs-lookup"><span data-stu-id="e368c-338">COMPLUS_GCHeapHardLimitSOH, COMPLUS_GCHeapHardLimitLOH, COMPLUS_GCHeapHardLimitPOH</span></span>

- <span data-ttu-id="e368c-339">W przypadku określenia wartości dla dowolnego z parametrów, `COMPLUS_GCHeapHardLimitSOH` `COMPLUS_GCHeapHardLimitLOH` lub `COMPLUS_GCHeapHardLimitPOH` , należy również określić wartość dla `COMPLUS_GCHeapHardLimitSOH` i `COMPLUS_GCHeapHardLimitLOH` .</span><span class="sxs-lookup"><span data-stu-id="e368c-339">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, or `COMPLUS_GCHeapHardLimitPOH` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH`.</span></span> <span data-ttu-id="e368c-340">Jeśli tego nie zrobisz, nie będzie można zainicjować środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e368c-340">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="e368c-341">Wartość domyślna dla `COMPLUS_GCHeapHardLimitPOH` jest równa 0.</span><span class="sxs-lookup"><span data-stu-id="e368c-341">The default value for `COMPLUS_GCHeapHardLimitPOH` is 0.</span></span> <span data-ttu-id="e368c-342">`COMPLUS_GCHeapHardLimitSOH`i `COMPLUS_GCHeapHardLimitLOH` nie mają wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="e368c-342">`COMPLUS_GCHeapHardLimitSOH` and `COMPLUS_GCHeapHardLimitLOH` don't have default values.</span></span>

| | <span data-ttu-id="e368c-343">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="e368c-343">Setting name</span></span> | <span data-ttu-id="e368c-344">Wartości</span><span class="sxs-lookup"><span data-stu-id="e368c-344">Values</span></span> | <span data-ttu-id="e368c-345">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e368c-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e368c-346">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-346">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOH` | <span data-ttu-id="e368c-347">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="e368c-347">*hexadecimal value*</span></span> | <span data-ttu-id="e368c-348">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e368c-348">.NET 5.0</span></span> |
| <span data-ttu-id="e368c-349">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-349">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOH` | <span data-ttu-id="e368c-350">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="e368c-350">*hexadecimal value*</span></span> | <span data-ttu-id="e368c-351">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e368c-351">.NET 5.0</span></span> |
| <span data-ttu-id="e368c-352">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-352">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOH` | <span data-ttu-id="e368c-353">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="e368c-353">*hexadecimal value*</span></span> | <span data-ttu-id="e368c-354">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e368c-354">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="e368c-355">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="e368c-355">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="e368c-356">Na przykład, aby określić stały limit sterty wynoszący 200 mebibytes (MiB), wartość będzie 0xC800000 lub C800000.</span><span class="sxs-lookup"><span data-stu-id="e368c-356">For example, to specify a heap hard limit of 200 mebibytes (MiB), the value would be 0xC800000 or C800000.</span></span>

#### <a name="complus_gcheaphardlimitsohpercent-complus_gcheaphardlimitlohpercent-complus_gcheaphardlimitpohpercent"></a><span data-ttu-id="e368c-357">COMPLUS_GCHeapHardLimitSOHPercent, COMPLUS_GCHeapHardLimitLOHPercent, COMPLUS_GCHeapHardLimitPOHPercent</span><span class="sxs-lookup"><span data-stu-id="e368c-357">COMPLUS_GCHeapHardLimitSOHPercent, COMPLUS_GCHeapHardLimitLOHPercent, COMPLUS_GCHeapHardLimitPOHPercent</span></span>

- <span data-ttu-id="e368c-358">W przypadku określenia wartości dla dowolnego z parametrów, `COMPLUS_GCHeapHardLimitSOHPercent` `COMPLUS_GCHeapHardLimitLOHPercent` lub `COMPLUS_GCHeapHardLimitPOHPercent` , należy również określić wartość dla `COMPLUS_GCHeapHardLimitSOHPercent` i `COMPLUS_GCHeapHardLimitLOHPercent` .</span><span class="sxs-lookup"><span data-stu-id="e368c-358">If you specify a value for any of the `COMPLUS_GCHeapHardLimitSOHPercent`, `COMPLUS_GCHeapHardLimitLOHPercent`, or `COMPLUS_GCHeapHardLimitPOHPercent` settings, you must also specify a value for `COMPLUS_GCHeapHardLimitSOHPercent` and `COMPLUS_GCHeapHardLimitLOHPercent`.</span></span> <span data-ttu-id="e368c-359">Jeśli tego nie zrobisz, nie będzie można zainicjować środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e368c-359">If you don't, the runtime will fail to initialize.</span></span>
- <span data-ttu-id="e368c-360">Te ustawienia są ignorowane `COMPLUS_GCHeapHardLimitSOH` w przypadku, gdy `COMPLUS_GCHeapHardLimitLOH` `COMPLUS_GCHeapHardLimitPOH` są określone.</span><span class="sxs-lookup"><span data-stu-id="e368c-360">These settings are ignored if `COMPLUS_GCHeapHardLimitSOH`, `COMPLUS_GCHeapHardLimitLOH`, and `COMPLUS_GCHeapHardLimitPOH` are specified.</span></span>
- <span data-ttu-id="e368c-361">Wartość 1 oznacza, że GC używa 1% całkowitej pamięci fizycznej dla sterty obiektu.</span><span class="sxs-lookup"><span data-stu-id="e368c-361">A value of 1 means that GC uses 1% of total physical memory for that object heap.</span></span>
- <span data-ttu-id="e368c-362">Każda wartość musi być większa niż zero i mniejsza niż 100.</span><span class="sxs-lookup"><span data-stu-id="e368c-362">Each value must be greater than zero and less than 100.</span></span> <span data-ttu-id="e368c-363">Ponadto suma trzech wartości procentowych musi być mniejsza niż 100.</span><span class="sxs-lookup"><span data-stu-id="e368c-363">Additionally, the sum of the three percentage values must be less than 100.</span></span> <span data-ttu-id="e368c-364">W przeciwnym razie nie będzie można zainicjować środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e368c-364">Otherwise, the runtime will fail to initialize.</span></span>

| | <span data-ttu-id="e368c-365">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="e368c-365">Setting name</span></span> | <span data-ttu-id="e368c-366">Wartości</span><span class="sxs-lookup"><span data-stu-id="e368c-366">Values</span></span> | <span data-ttu-id="e368c-367">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e368c-367">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e368c-368">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-368">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitSOHPercent` | <span data-ttu-id="e368c-369">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="e368c-369">*hexadecimal value*</span></span> | <span data-ttu-id="e368c-370">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e368c-370">.NET 5.0</span></span> |
| <span data-ttu-id="e368c-371">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-371">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitLOHPercent` | <span data-ttu-id="e368c-372">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="e368c-372">*hexadecimal value*</span></span> | <span data-ttu-id="e368c-373">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e368c-373">.NET 5.0</span></span> |
| <span data-ttu-id="e368c-374">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-374">**Environment variable**</span></span> | `COMPLUS_GCHeapHardLimitPOHPercent` | <span data-ttu-id="e368c-375">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="e368c-375">*hexadecimal value*</span></span> | <span data-ttu-id="e368c-376">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="e368c-376">.NET 5.0</span></span> |

> [!TIP]
> <span data-ttu-id="e368c-377">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="e368c-377">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="e368c-378">Na przykład, aby ograniczyć użycie sterty do 30%, wartość będzie 0x1E lub 1E.</span><span class="sxs-lookup"><span data-stu-id="e368c-378">For example, to limit the heap usage to 30%, the value would be 0x1E or 1E.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="e368c-379">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="e368c-379">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="e368c-380">Określa, czy segmenty, które mają zostać usunięte, są umieszczane na liście gotowości do użycia w przyszłości lub są wyłączane z powrotem do systemu operacyjnego (OS).</span><span class="sxs-lookup"><span data-stu-id="e368c-380">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="e368c-381">Domyślnie: segmenty wydań z powrotem do systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="e368c-381">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="e368c-382">Jest to równoznaczne z ustawieniem wartości `false` .</span><span class="sxs-lookup"><span data-stu-id="e368c-382">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="e368c-383">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="e368c-383">Setting name</span></span> | <span data-ttu-id="e368c-384">Wartości</span><span class="sxs-lookup"><span data-stu-id="e368c-384">Values</span></span> | <span data-ttu-id="e368c-385">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e368c-385">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e368c-386">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e368c-386">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="e368c-387">`false`— wydanie do systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="e368c-387">`false` - release to OS</span></span><br/><span data-ttu-id="e368c-388">`true`— Umieść w stanie wstrzymania</span><span class="sxs-lookup"><span data-stu-id="e368c-388">`true` - put on standby</span></span> | <span data-ttu-id="e368c-389">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e368c-389">.NET Core 1.0</span></span> |
| <span data-ttu-id="e368c-390">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="e368c-390">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="e368c-391">`false`— wydanie do systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="e368c-391">`false` - release to OS</span></span><br/><span data-ttu-id="e368c-392">`true`— Umieść w stanie wstrzymania</span><span class="sxs-lookup"><span data-stu-id="e368c-392">`true` - put on standby</span></span> | <span data-ttu-id="e368c-393">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e368c-393">.NET Core 1.0</span></span> |
| <span data-ttu-id="e368c-394">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-394">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="e368c-395">`0`— wydanie do systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="e368c-395">`0` - release to OS</span></span><br/><span data-ttu-id="e368c-396">`1`— Umieść w stanie wstrzymania</span><span class="sxs-lookup"><span data-stu-id="e368c-396">`1` - put on standby</span></span> | <span data-ttu-id="e368c-397">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e368c-397">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="e368c-398">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e368c-398">Examples</span></span>

<span data-ttu-id="e368c-399">*runtimeconfig.js* pliku:</span><span class="sxs-lookup"><span data-stu-id="e368c-399">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="e368c-400">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="e368c-400">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="e368c-401">Duże strony</span><span class="sxs-lookup"><span data-stu-id="e368c-401">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="e368c-402">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="e368c-402">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="e368c-403">Określa, czy mają być używane duże strony, gdy jest ustawiony limit sztywny sterty.</span><span class="sxs-lookup"><span data-stu-id="e368c-403">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="e368c-404">Domyślnie: nie używaj dużych stron, gdy jest ustawiony limit sztywny sterty.</span><span class="sxs-lookup"><span data-stu-id="e368c-404">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="e368c-405">Jest to równoznaczne z ustawieniem wartości `0` .</span><span class="sxs-lookup"><span data-stu-id="e368c-405">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="e368c-406">Jest to ustawienie eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="e368c-406">This is an experimental setting.</span></span>

| | <span data-ttu-id="e368c-407">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="e368c-407">Setting name</span></span> | <span data-ttu-id="e368c-408">Wartości</span><span class="sxs-lookup"><span data-stu-id="e368c-408">Values</span></span> | <span data-ttu-id="e368c-409">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e368c-409">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e368c-410">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e368c-410">**runtimeconfig.json**</span></span> | <span data-ttu-id="e368c-411">Brak</span><span class="sxs-lookup"><span data-stu-id="e368c-411">N/A</span></span> | <span data-ttu-id="e368c-412">Brak</span><span class="sxs-lookup"><span data-stu-id="e368c-412">N/A</span></span> | <span data-ttu-id="e368c-413">Brak</span><span class="sxs-lookup"><span data-stu-id="e368c-413">N/A</span></span> |
| <span data-ttu-id="e368c-414">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-414">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="e368c-415">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="e368c-415">`0` - disabled</span></span><br/><span data-ttu-id="e368c-416">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="e368c-416">`1` - enabled</span></span> | <span data-ttu-id="e368c-417">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e368c-417">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="e368c-418">Duże obiekty</span><span class="sxs-lookup"><span data-stu-id="e368c-418">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="e368c-419">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="e368c-419">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="e368c-420">Konfiguruje obsługę modułu wyrzucania elementów bezużytecznych na platformach 64-bitowych dla tablic, które są większe niż 2 gigabajty (GB) w łącznym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="e368c-420">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="e368c-421">Domyślnie: GLOBALna obsługa tablic o pojemności większej niż 2 GB.</span><span class="sxs-lookup"><span data-stu-id="e368c-421">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="e368c-422">Jest to równoznaczne z ustawieniem wartości `1` .</span><span class="sxs-lookup"><span data-stu-id="e368c-422">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="e368c-423">Ta opcja może stać się przestarzała w przyszłej wersji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="e368c-423">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="e368c-424">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="e368c-424">Setting name</span></span> | <span data-ttu-id="e368c-425">Wartości</span><span class="sxs-lookup"><span data-stu-id="e368c-425">Values</span></span> | <span data-ttu-id="e368c-426">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e368c-426">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e368c-427">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e368c-427">**runtimeconfig.json**</span></span> | <span data-ttu-id="e368c-428">Brak</span><span class="sxs-lookup"><span data-stu-id="e368c-428">N/A</span></span> | <span data-ttu-id="e368c-429">Brak</span><span class="sxs-lookup"><span data-stu-id="e368c-429">N/A</span></span> | <span data-ttu-id="e368c-430">Brak</span><span class="sxs-lookup"><span data-stu-id="e368c-430">N/A</span></span> |
| <span data-ttu-id="e368c-431">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-431">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="e368c-432">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="e368c-432">`1` - enabled</span></span><br/> <span data-ttu-id="e368c-433">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="e368c-433">`0` - disabled</span></span> | <span data-ttu-id="e368c-434">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e368c-434">.NET Core 1.0</span></span> |
| <span data-ttu-id="e368c-435">**app.config .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e368c-435">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e368c-436">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="e368c-436">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="e368c-437">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="e368c-437">`1` - enabled</span></span><br/> <span data-ttu-id="e368c-438">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="e368c-438">`0` - disabled</span></span> | <span data-ttu-id="e368c-439">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="e368c-439">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="e368c-440">Próg sterty dla dużego obiektu</span><span class="sxs-lookup"><span data-stu-id="e368c-440">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="e368c-441">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="e368c-441">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="e368c-442">Określa rozmiar progu (w bajtach), który powoduje, że obiekty są na stosie dużego obiektu (LOH).</span><span class="sxs-lookup"><span data-stu-id="e368c-442">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="e368c-443">Domyślny próg to 85 000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="e368c-443">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="e368c-444">Określona wartość musi być większa niż wartość progu domyślnego.</span><span class="sxs-lookup"><span data-stu-id="e368c-444">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="e368c-445">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="e368c-445">Setting name</span></span> | <span data-ttu-id="e368c-446">Wartości</span><span class="sxs-lookup"><span data-stu-id="e368c-446">Values</span></span> | <span data-ttu-id="e368c-447">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e368c-447">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e368c-448">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e368c-448">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="e368c-449">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="e368c-449">*decimal value*</span></span> | <span data-ttu-id="e368c-450">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e368c-450">.NET Core 1.0</span></span> |
| <span data-ttu-id="e368c-451">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-451">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="e368c-452">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="e368c-452">*hexadecimal value*</span></span> | <span data-ttu-id="e368c-453">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="e368c-453">.NET Core 1.0</span></span> |
| <span data-ttu-id="e368c-454">**app.config .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e368c-454">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="e368c-455">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="e368c-455">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="e368c-456">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="e368c-456">*decimal value*</span></span> | <span data-ttu-id="e368c-457"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="e368c-457">.NET Framework 4.8</span></span> |

<span data-ttu-id="e368c-458">Przykład:</span><span class="sxs-lookup"><span data-stu-id="e368c-458">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.LOHThreshold": 120000
      }
   }
}
```

> [!TIP]
> <span data-ttu-id="e368c-459">Jeśli ustawiasz opcję w *runtimeconfig.jsna*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="e368c-459">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="e368c-460">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="e368c-460">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="e368c-461">Na przykład, aby ustawić rozmiar progu 120 000 bajtów, wartości byłyby 120000 dla pliku JSON oraz 0x1D4C0 lub 1D4C0 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="e368c-461">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="e368c-462">Autonomiczna GC</span><span class="sxs-lookup"><span data-stu-id="e368c-462">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="e368c-463">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="e368c-463">COMPlus_GCName</span></span>

- <span data-ttu-id="e368c-464">Określa ścieżkę do biblioteki zawierającej Moduł wyrzucania elementów bezużytecznych, który środowisko uruchomieniowe zamierza załadować.</span><span class="sxs-lookup"><span data-stu-id="e368c-464">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="e368c-465">Aby uzyskać więcej informacji, zobacz [prekonstrukcja modułu ładującego GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="e368c-465">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="e368c-466">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="e368c-466">Setting name</span></span> | <span data-ttu-id="e368c-467">Wartości</span><span class="sxs-lookup"><span data-stu-id="e368c-467">Values</span></span> | <span data-ttu-id="e368c-468">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="e368c-468">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="e368c-469">**runtimeconfig.jsna**</span><span class="sxs-lookup"><span data-stu-id="e368c-469">**runtimeconfig.json**</span></span> | <span data-ttu-id="e368c-470">Brak</span><span class="sxs-lookup"><span data-stu-id="e368c-470">N/A</span></span> | <span data-ttu-id="e368c-471">Brak</span><span class="sxs-lookup"><span data-stu-id="e368c-471">N/A</span></span> | <span data-ttu-id="e368c-472">Brak</span><span class="sxs-lookup"><span data-stu-id="e368c-472">N/A</span></span> |
| <span data-ttu-id="e368c-473">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="e368c-473">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="e368c-474">*string_path*</span><span class="sxs-lookup"><span data-stu-id="e368c-474">*string_path*</span></span> | <span data-ttu-id="e368c-475">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="e368c-475">.NET Core 2.0</span></span> |
