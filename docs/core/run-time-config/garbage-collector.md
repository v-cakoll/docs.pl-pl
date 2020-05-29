---
title: Ustawienia konfiguracji modułu wyrzucania elementów bezużytecznych
description: Informacje o ustawieniach czasu wykonywania w celu skonfigurowania sposobu, w jaki moduł zbierający elementy bezużyteczne zarządza pamięcią dla aplikacji platformy .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 0ce2f70204463c1525ef7d29de21ddf5384d0238
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202099"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="12647-103">Opcje konfiguracji czasu wykonywania dla wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="12647-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="12647-104">Ta strona zawiera informacje na temat ustawień modułu zbierającego elementy bezużyteczne (GC), które można zmienić w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="12647-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="12647-105">Jeśli próbujesz osiągnąć szczytową wydajność uruchomionej aplikacji, rozważ użycie tych ustawień.</span><span class="sxs-lookup"><span data-stu-id="12647-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="12647-106">Jednak wartości domyślne zapewniają optymalną wydajność większości aplikacji w typowych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="12647-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="12647-107">Ustawienia są ułożone w grupach na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="12647-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="12647-108">Ustawienia w ramach każdej grupy są często używane w połączeniu ze sobą, aby osiągnąć konkretny wynik.</span><span class="sxs-lookup"><span data-stu-id="12647-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="12647-109">Te ustawienia mogą być również dynamicznie zmieniane przez aplikację w trakcie działania, więc wszystkie ustawione ustawienia czasu wykonywania mogą zostać zastąpione.</span><span class="sxs-lookup"><span data-stu-id="12647-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="12647-110">Niektóre ustawienia, takie jak [poziom opóźnienia](../../standard/garbage-collection/latency.md), są zazwyczaj ustawiane tylko za pomocą interfejsu API w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="12647-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="12647-111">Takie ustawienia zostały pominięte na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="12647-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="12647-112">W przypadku wartości liczbowych Użyj notacji dziesiętnej dla ustawień w pliku *runtimeconfig. JSON* i notacji szesnastkowej dla ustawień zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="12647-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="12647-113">W przypadku wartości szesnastkowych można je określić z prefiksem "0x" lub bez niego.</span><span class="sxs-lookup"><span data-stu-id="12647-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="12647-114">Typy wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="12647-114">Flavors of garbage collection</span></span>

<span data-ttu-id="12647-115">Dwa główne typy wyrzucania elementów bezużytecznych to stacja robocza i serwer GC.</span><span class="sxs-lookup"><span data-stu-id="12647-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="12647-116">Aby uzyskać więcej informacji o różnicach między tymi dwoma, zobacz [stacja robocza i odzyskiwanie pamięci serwera](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="12647-116">For more information about differences between the two, see [Workstation and server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span>

<span data-ttu-id="12647-117">Podelementy wyrzucania elementów bezużytecznych są tła i niewspółbieżne.</span><span class="sxs-lookup"><span data-stu-id="12647-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="12647-118">Użyj następujących ustawień, aby wybrać typy wyrzucania elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="12647-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="12647-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="12647-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="12647-120">Określa, czy aplikacja używa wyrzucania elementów bezużytecznych stacji roboczej lub odzyskiwania pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="12647-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="12647-121">Domyślnie: wyrzucanie elementów bezużytecznych stacji roboczej.</span><span class="sxs-lookup"><span data-stu-id="12647-121">Default: Workstation garbage collection.</span></span> <span data-ttu-id="12647-122">Jest to równoznaczne z ustawieniem wartości `false` .</span><span class="sxs-lookup"><span data-stu-id="12647-122">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="12647-123">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="12647-123">Setting name</span></span> | <span data-ttu-id="12647-124">Wartości</span><span class="sxs-lookup"><span data-stu-id="12647-124">Values</span></span> | <span data-ttu-id="12647-125">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12647-125">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="12647-126">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="12647-126">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="12647-127">`false`-Stacja robocza</span><span class="sxs-lookup"><span data-stu-id="12647-127">`false` - workstation</span></span><br/><span data-ttu-id="12647-128">`true`— serwer</span><span class="sxs-lookup"><span data-stu-id="12647-128">`true` - server</span></span> | <span data-ttu-id="12647-129">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="12647-129">.NET Core 1.0</span></span> |
| <span data-ttu-id="12647-130">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="12647-130">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="12647-131">`false`-Stacja robocza</span><span class="sxs-lookup"><span data-stu-id="12647-131">`false` - workstation</span></span><br/><span data-ttu-id="12647-132">`true`— serwer</span><span class="sxs-lookup"><span data-stu-id="12647-132">`true` - server</span></span> | <span data-ttu-id="12647-133">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="12647-133">.NET Core 1.0</span></span> |
| <span data-ttu-id="12647-134">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="12647-134">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="12647-135">`0`-Stacja robocza</span><span class="sxs-lookup"><span data-stu-id="12647-135">`0` - workstation</span></span><br/><span data-ttu-id="12647-136">`1`— serwer</span><span class="sxs-lookup"><span data-stu-id="12647-136">`1` - server</span></span> | <span data-ttu-id="12647-137">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="12647-137">.NET Core 1.0</span></span> |
| <span data-ttu-id="12647-138">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="12647-138">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="12647-139">GCServer</span><span class="sxs-lookup"><span data-stu-id="12647-139">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="12647-140">`false`-Stacja robocza</span><span class="sxs-lookup"><span data-stu-id="12647-140">`false` - workstation</span></span><br/><span data-ttu-id="12647-141">`true`— serwer</span><span class="sxs-lookup"><span data-stu-id="12647-141">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="12647-142">Przykłady</span><span class="sxs-lookup"><span data-stu-id="12647-142">Examples</span></span>

<span data-ttu-id="12647-143">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="12647-143">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="12647-144">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="12647-144">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="12647-145">System. GC. współbieżne/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="12647-145">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="12647-146">Określa, czy jest włączone wyrzucanie elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="12647-146">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="12647-147">Domyślne: Użyj w tle GC.</span><span class="sxs-lookup"><span data-stu-id="12647-147">Default: Use background GC.</span></span> <span data-ttu-id="12647-148">Jest to równoznaczne z ustawieniem wartości `true` .</span><span class="sxs-lookup"><span data-stu-id="12647-148">This is equivalent to setting the value to `true`.</span></span>
- <span data-ttu-id="12647-149">Aby uzyskać więcej informacji, zobacz [wyrzucanie elementów bezużytecznych w tle](../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="12647-149">For more information, see [Background garbage collection](../../standard/garbage-collection/background-gc.md).</span></span>

| | <span data-ttu-id="12647-150">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="12647-150">Setting name</span></span> | <span data-ttu-id="12647-151">Wartości</span><span class="sxs-lookup"><span data-stu-id="12647-151">Values</span></span> | <span data-ttu-id="12647-152">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12647-152">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="12647-153">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="12647-153">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="12647-154">`true`-w tle GC</span><span class="sxs-lookup"><span data-stu-id="12647-154">`true` - background GC</span></span><br/><span data-ttu-id="12647-155">`false`-niewspółbieżne GC</span><span class="sxs-lookup"><span data-stu-id="12647-155">`false` - non-concurrent GC</span></span> | <span data-ttu-id="12647-156">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="12647-156">.NET Core 1.0</span></span> |
| <span data-ttu-id="12647-157">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="12647-157">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="12647-158">`true`-w tle GC</span><span class="sxs-lookup"><span data-stu-id="12647-158">`true` - background GC</span></span><br/><span data-ttu-id="12647-159">`false`-niewspółbieżne GC</span><span class="sxs-lookup"><span data-stu-id="12647-159">`false` - non-concurrent GC</span></span> | <span data-ttu-id="12647-160">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="12647-160">.NET Core 1.0</span></span> |
| <span data-ttu-id="12647-161">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="12647-161">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="12647-162">`1`-w tle GC</span><span class="sxs-lookup"><span data-stu-id="12647-162">`1` - background GC</span></span><br/><span data-ttu-id="12647-163">`0`-niewspółbieżne GC</span><span class="sxs-lookup"><span data-stu-id="12647-163">`0` - non-concurrent GC</span></span> | <span data-ttu-id="12647-164">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="12647-164">.NET Core 1.0</span></span> |
| <span data-ttu-id="12647-165">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="12647-165">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="12647-166">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="12647-166">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="12647-167">`true`-w tle GC</span><span class="sxs-lookup"><span data-stu-id="12647-167">`true` - background GC</span></span><br/><span data-ttu-id="12647-168">`false`-niewspółbieżne GC</span><span class="sxs-lookup"><span data-stu-id="12647-168">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="12647-169">Przykłady</span><span class="sxs-lookup"><span data-stu-id="12647-169">Examples</span></span>

<span data-ttu-id="12647-170">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="12647-170">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="12647-171">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="12647-171">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="12647-172">Zarządzanie użyciem zasobów</span><span class="sxs-lookup"><span data-stu-id="12647-172">Manage resource usage</span></span>

<span data-ttu-id="12647-173">Ustawienia opisane w tej sekcji służą do zarządzania użyciem pamięci i procesora modułu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="12647-173">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="12647-174">Aby uzyskać więcej informacji na temat niektórych z tych ustawień, zapoznaj się z wpisem na blogu centrum [robocze i serwer GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .</span><span class="sxs-lookup"><span data-stu-id="12647-174">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="12647-175">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="12647-175">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="12647-176">Ogranicza liczbę stert utworzonych przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="12647-176">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="12647-177">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="12647-177">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="12647-178">Jeśli [koligacja procesora GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) jest włączona, co jest ustawieniem domyślnym, licznik sterty ustawia `n` sterty/wątki skoligacony GC na pierwszy `n` procesor.</span><span class="sxs-lookup"><span data-stu-id="12647-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="12647-179">(Użyj [koligacji maska](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) lub ustawienia [zakresów koligacji](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) , aby określić, które procesory mają być koligacji).</span><span class="sxs-lookup"><span data-stu-id="12647-179">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="12647-180">Jeśli [koligacja procesora GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) jest wyłączona, to ustawienie ogranicza liczbę stert GC.</span><span class="sxs-lookup"><span data-stu-id="12647-180">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="12647-181">Aby uzyskać więcej informacji, zobacz [uwagi GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="12647-181">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="12647-182">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="12647-182">Setting name</span></span> | <span data-ttu-id="12647-183">Wartości</span><span class="sxs-lookup"><span data-stu-id="12647-183">Values</span></span> | <span data-ttu-id="12647-184">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12647-184">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="12647-185">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="12647-185">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="12647-186">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="12647-186">*decimal value*</span></span> | <span data-ttu-id="12647-187">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="12647-187">.NET Core 3.0</span></span> |
| <span data-ttu-id="12647-188">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="12647-188">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="12647-189">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="12647-189">*hexadecimal value*</span></span> | <span data-ttu-id="12647-190">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="12647-190">.NET Core 3.0</span></span> |
| <span data-ttu-id="12647-191">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="12647-191">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="12647-192">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="12647-192">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="12647-193">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="12647-193">*decimal value*</span></span> | <span data-ttu-id="12647-194">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="12647-194">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="12647-195">Przykład:</span><span class="sxs-lookup"><span data-stu-id="12647-195">Example:</span></span>

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
> <span data-ttu-id="12647-196">Jeśli ustawiasz opcję w *runtimeconfig. JSON*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="12647-196">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="12647-197">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="12647-197">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="12647-198">Na przykład aby ograniczyć liczbę stert do 16, wartości dla pliku JSON i 0x10 lub 10 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="12647-198">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="12647-199">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="12647-199">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="12647-200">Określa dokładne procesory, które powinny być używane przez wątki modułu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="12647-200">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="12647-201">Jeśli [koligacja procesora GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) jest wyłączona, to ustawienie jest ignorowane.</span><span class="sxs-lookup"><span data-stu-id="12647-201">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="12647-202">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="12647-202">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="12647-203">Wartość jest maską bitową, która definiuje procesory, które są dostępne dla procesu.</span><span class="sxs-lookup"><span data-stu-id="12647-203">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="12647-204">Na przykład wartość dziesiętna 1023 (lub wartość szesnastkowa 0x3FF lub 3FF, jeśli używana jest zmienna środowiskowa) to 0011 1111 1111 w notacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="12647-204">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="12647-205">Oznacza to, że pierwsze 10 procesorów ma być używany.</span><span class="sxs-lookup"><span data-stu-id="12647-205">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="12647-206">Aby określić następne 10 procesorów, czyli procesorów 10-19, określ wartość dziesiętną 1047552 (lub wartość szesnastkową 0xFFC00 lub FFC00), która jest równoważna z wartością binarną 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="12647-206">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="12647-207">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="12647-207">Setting name</span></span> | <span data-ttu-id="12647-208">Wartości</span><span class="sxs-lookup"><span data-stu-id="12647-208">Values</span></span> | <span data-ttu-id="12647-209">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12647-209">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="12647-210">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="12647-210">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="12647-211">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="12647-211">*decimal value*</span></span> | <span data-ttu-id="12647-212">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="12647-212">.NET Core 3.0</span></span> |
| <span data-ttu-id="12647-213">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="12647-213">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="12647-214">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="12647-214">*hexadecimal value*</span></span> | <span data-ttu-id="12647-215">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="12647-215">.NET Core 3.0</span></span> |
| <span data-ttu-id="12647-216">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="12647-216">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="12647-217">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="12647-217">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="12647-218">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="12647-218">*decimal value*</span></span> | <span data-ttu-id="12647-219">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="12647-219">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="12647-220">Przykład:</span><span class="sxs-lookup"><span data-stu-id="12647-220">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="12647-221">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="12647-221">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="12647-222">Określa listę procesorów, które mają być używane na potrzeby wątków modułu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="12647-222">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="12647-223">To ustawienie jest podobne do [System. GC. HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), z tą różnicą, że umożliwia określenie więcej niż 64 procesorów.</span><span class="sxs-lookup"><span data-stu-id="12647-223">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="12647-224">W przypadku systemów operacyjnych Windows należy prefiksować numer procesora lub zakres z odpowiednią [grupą procesorów CPU](/windows/win32/procthread/processor-groups), na przykład "0:1-10, 0:12, 1:50-52, 1:70".</span><span class="sxs-lookup"><span data-stu-id="12647-224">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="12647-225">Jeśli [koligacja procesora GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) jest wyłączona, to ustawienie jest ignorowane.</span><span class="sxs-lookup"><span data-stu-id="12647-225">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="12647-226">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="12647-226">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="12647-227">Aby uzyskać więcej informacji, zobacz temat [Zapewnianie lepszej konfiguracji procesora dla GC na maszynach z > 64 procesorów CPU](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="12647-227">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="12647-228">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="12647-228">Setting name</span></span> | <span data-ttu-id="12647-229">Wartości</span><span class="sxs-lookup"><span data-stu-id="12647-229">Values</span></span> | <span data-ttu-id="12647-230">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12647-230">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="12647-231">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="12647-231">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="12647-232">Rozdzielana przecinkami lista numerów procesorów lub zakresów numerów procesorów.</span><span class="sxs-lookup"><span data-stu-id="12647-232">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="12647-233">Przykład UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="12647-233">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="12647-234">Przykład systemu Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="12647-234">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="12647-235">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="12647-235">.NET Core 3.0</span></span> |
| <span data-ttu-id="12647-236">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="12647-236">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="12647-237">Rozdzielana przecinkami lista numerów procesorów lub zakresów numerów procesorów.</span><span class="sxs-lookup"><span data-stu-id="12647-237">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="12647-238">Przykład UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="12647-238">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="12647-239">Przykład systemu Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="12647-239">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="12647-240">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="12647-240">.NET Core 3.0</span></span> |

<span data-ttu-id="12647-241">Przykład:</span><span class="sxs-lookup"><span data-stu-id="12647-241">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="12647-242">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="12647-242">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="12647-243">Określa, czy moduł wyrzucania elementów bezużytecznych używa [grup CPU](/windows/win32/procthread/processor-groups) , czy nie.</span><span class="sxs-lookup"><span data-stu-id="12647-243">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="12647-244">Gdy 64-bitowy komputer z systemem Windows ma wiele grup CPU, oznacza to, że istnieje więcej niż 64 procesorów, włączając ten element rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach CPU.</span><span class="sxs-lookup"><span data-stu-id="12647-244">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="12647-245">Moduł wyrzucania elementów bezużytecznych używa wszystkich rdzeni do tworzenia i równoważenia sterty.</span><span class="sxs-lookup"><span data-stu-id="12647-245">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="12647-246">Stosuje się do wyrzucania elementów bezużytecznych serwera w 64-bitowych systemach operacyjnych Windows.</span><span class="sxs-lookup"><span data-stu-id="12647-246">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="12647-247">Domyślnie: GC nie rozciąga się między grupami CPU.</span><span class="sxs-lookup"><span data-stu-id="12647-247">Default: GC does not extend across CPU groups.</span></span> <span data-ttu-id="12647-248">Jest to równoznaczne z ustawieniem wartości `0` .</span><span class="sxs-lookup"><span data-stu-id="12647-248">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="12647-249">Aby uzyskać więcej informacji, zobacz temat [Zapewnianie lepszej konfiguracji procesora dla GC na maszynach z > 64 procesorów CPU](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="12647-249">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="12647-250">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="12647-250">Setting name</span></span> | <span data-ttu-id="12647-251">Wartości</span><span class="sxs-lookup"><span data-stu-id="12647-251">Values</span></span> | <span data-ttu-id="12647-252">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12647-252">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="12647-253">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="12647-253">**runtimeconfig.json**</span></span> | <span data-ttu-id="12647-254">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="12647-254">N/A</span></span> | <span data-ttu-id="12647-255">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="12647-255">N/A</span></span> | <span data-ttu-id="12647-256">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="12647-256">N/A</span></span> |
| <span data-ttu-id="12647-257">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="12647-257">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="12647-258">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="12647-258">`0` - disabled</span></span><br/><span data-ttu-id="12647-259">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="12647-259">`1` - enabled</span></span> | <span data-ttu-id="12647-260">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="12647-260">.NET Core 1.0</span></span> |
| <span data-ttu-id="12647-261">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="12647-261">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="12647-262">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="12647-262">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="12647-263">`false`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="12647-263">`false` - disabled</span></span><br/><span data-ttu-id="12647-264">`true`-włączone</span><span class="sxs-lookup"><span data-stu-id="12647-264">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="12647-265">Aby skonfigurować środowisko uruchomieniowe języka wspólnego (CLR) do dystrybucji wątków z puli wątków we wszystkich grupach procesora, Włącz opcję [Thread_UseAllCpuGroups elementu](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="12647-265">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="12647-266">W przypadku aplikacji platformy .NET Core można włączyć tę opcję, ustawiając wartość `COMPlus_Thread_UseAllCpuGroups` zmiennej środowiskowej na `1` .</span><span class="sxs-lookup"><span data-stu-id="12647-266">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="12647-267">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="12647-267">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="12647-268">Określa, czy *koligacji* wątki odzyskiwania pamięci z procesorami.</span><span class="sxs-lookup"><span data-stu-id="12647-268">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="12647-269">Aby koligacji wątek GC, oznacza to, że można go uruchomić tylko w określonym procesorze CPU.</span><span class="sxs-lookup"><span data-stu-id="12647-269">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="12647-270">Sterta jest tworzona dla każdego wątku GC.</span><span class="sxs-lookup"><span data-stu-id="12647-270">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="12647-271">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="12647-271">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="12647-272">Domyślnie: koligacji wątki odzyskiwania pamięci z procesorami.</span><span class="sxs-lookup"><span data-stu-id="12647-272">Default: Affinitize garbage collection threads with processors.</span></span> <span data-ttu-id="12647-273">Jest to równoznaczne z ustawieniem wartości `false` .</span><span class="sxs-lookup"><span data-stu-id="12647-273">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="12647-274">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="12647-274">Setting name</span></span> | <span data-ttu-id="12647-275">Wartości</span><span class="sxs-lookup"><span data-stu-id="12647-275">Values</span></span> | <span data-ttu-id="12647-276">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12647-276">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="12647-277">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="12647-277">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="12647-278">`false`-koligacji</span><span class="sxs-lookup"><span data-stu-id="12647-278">`false` - affinitize</span></span><br/><span data-ttu-id="12647-279">`true`-nie koligacji</span><span class="sxs-lookup"><span data-stu-id="12647-279">`true` - don't affinitize</span></span> | <span data-ttu-id="12647-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="12647-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="12647-281">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="12647-281">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="12647-282">`0`-koligacji</span><span class="sxs-lookup"><span data-stu-id="12647-282">`0` - affinitize</span></span><br/><span data-ttu-id="12647-283">`1`-nie koligacji</span><span class="sxs-lookup"><span data-stu-id="12647-283">`1` - don't affinitize</span></span> | <span data-ttu-id="12647-284">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="12647-284">.NET Core 3.0</span></span> |
| <span data-ttu-id="12647-285">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="12647-285">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="12647-286">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="12647-286">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="12647-287">`false`-koligacji</span><span class="sxs-lookup"><span data-stu-id="12647-287">`false` - affinitize</span></span><br/><span data-ttu-id="12647-288">`true`-nie koligacji</span><span class="sxs-lookup"><span data-stu-id="12647-288">`true` - don't affinitize</span></span> | <span data-ttu-id="12647-289">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="12647-289">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="12647-290">Przykład:</span><span class="sxs-lookup"><span data-stu-id="12647-290">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="12647-291">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="12647-291">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="12647-292">Określa maksymalny rozmiar zatwierdzeń w bajtach dla sterty GC i księgowości GC.</span><span class="sxs-lookup"><span data-stu-id="12647-292">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="12647-293">To ustawienie dotyczy tylko komputerów 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="12647-293">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="12647-294">Wartość domyślna, która stosuje się tylko w niektórych przypadkach, jest większa niż 20 MB lub 75% limitu pamięci w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="12647-294">The default value, which only applies in certain cases, is the greater of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="12647-295">Wartość domyślna ma zastosowanie, jeśli:</span><span class="sxs-lookup"><span data-stu-id="12647-295">The default value applies if:</span></span>

  - <span data-ttu-id="12647-296">Proces jest uruchomiony wewnątrz kontenera o określonym limicie pamięci.</span><span class="sxs-lookup"><span data-stu-id="12647-296">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="12647-297">Nie ustawiono wartości [System. GC. HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) .</span><span class="sxs-lookup"><span data-stu-id="12647-297">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="12647-298">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="12647-298">Setting name</span></span> | <span data-ttu-id="12647-299">Wartości</span><span class="sxs-lookup"><span data-stu-id="12647-299">Values</span></span> | <span data-ttu-id="12647-300">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12647-300">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="12647-301">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="12647-301">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="12647-302">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="12647-302">*decimal value*</span></span> | <span data-ttu-id="12647-303">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="12647-303">.NET Core 3.0</span></span> |
| <span data-ttu-id="12647-304">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="12647-304">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="12647-305">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="12647-305">*hexadecimal value*</span></span> | <span data-ttu-id="12647-306">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="12647-306">.NET Core 3.0</span></span> |

<span data-ttu-id="12647-307">Przykład:</span><span class="sxs-lookup"><span data-stu-id="12647-307">Example:</span></span>

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
> <span data-ttu-id="12647-308">Jeśli ustawiasz opcję w *runtimeconfig. JSON*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="12647-308">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="12647-309">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="12647-309">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="12647-310">Na przykład aby określić stały limit sterty wynoszący 200 mebibytes (MiB), wartości byłyby 209715200 dla pliku JSON i 0xC800000 lub C800000 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="12647-310">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="12647-311">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="12647-311">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="12647-312">Określa dozwolone użycie sterty GC jako procent całkowitej ilości pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="12647-312">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="12647-313">Jeśli zostanie również ustawiona wartość [System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) , to ustawienie jest ignorowane.</span><span class="sxs-lookup"><span data-stu-id="12647-313">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="12647-314">To ustawienie dotyczy tylko komputerów 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="12647-314">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="12647-315">Jeśli proces jest uruchomiony wewnątrz kontenera o określonym limicie pamięci, wartość procentowa jest obliczana jako wartość procentowa tego limitu pamięci.</span><span class="sxs-lookup"><span data-stu-id="12647-315">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="12647-316">Wartość domyślna, która jest stosowana tylko w niektórych przypadkach, jest mniejsza z 20 MB lub 75% limitu pamięci dla kontenera.</span><span class="sxs-lookup"><span data-stu-id="12647-316">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="12647-317">Wartość domyślna ma zastosowanie, jeśli:</span><span class="sxs-lookup"><span data-stu-id="12647-317">The default value applies if:</span></span>

  - <span data-ttu-id="12647-318">Proces jest uruchomiony wewnątrz kontenera o określonym limicie pamięci.</span><span class="sxs-lookup"><span data-stu-id="12647-318">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="12647-319">Nie ustawiono wartości [System. GC. HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) .</span><span class="sxs-lookup"><span data-stu-id="12647-319">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="12647-320">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="12647-320">Setting name</span></span> | <span data-ttu-id="12647-321">Wartości</span><span class="sxs-lookup"><span data-stu-id="12647-321">Values</span></span> | <span data-ttu-id="12647-322">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12647-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="12647-323">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="12647-323">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="12647-324">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="12647-324">*decimal value*</span></span> | <span data-ttu-id="12647-325">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="12647-325">.NET Core 3.0</span></span> |
| <span data-ttu-id="12647-326">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="12647-326">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="12647-327">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="12647-327">*hexadecimal value*</span></span> | <span data-ttu-id="12647-328">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="12647-328">.NET Core 3.0</span></span> |

<span data-ttu-id="12647-329">Przykład:</span><span class="sxs-lookup"><span data-stu-id="12647-329">Example:</span></span>

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
> <span data-ttu-id="12647-330">Jeśli ustawiasz opcję w *runtimeconfig. JSON*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="12647-330">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="12647-331">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="12647-331">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="12647-332">Na przykład aby ograniczyć użycie sterty do 30%, wartości byłyby 30 dla pliku JSON i 0x1E lub 1E dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="12647-332">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="12647-333">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="12647-333">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="12647-334">Określa, czy segmenty, które mają zostać usunięte, są umieszczane na liście gotowości do użycia w przyszłości lub są wyłączane z powrotem do systemu operacyjnego (OS).</span><span class="sxs-lookup"><span data-stu-id="12647-334">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="12647-335">Domyślnie: segmenty wydań z powrotem do systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="12647-335">Default: Release segments back to the operating system.</span></span> <span data-ttu-id="12647-336">Jest to równoznaczne z ustawieniem wartości `false` .</span><span class="sxs-lookup"><span data-stu-id="12647-336">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="12647-337">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="12647-337">Setting name</span></span> | <span data-ttu-id="12647-338">Wartości</span><span class="sxs-lookup"><span data-stu-id="12647-338">Values</span></span> | <span data-ttu-id="12647-339">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12647-339">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="12647-340">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="12647-340">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="12647-341">`false`— wydanie do systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="12647-341">`false` - release to OS</span></span><br/><span data-ttu-id="12647-342">`true`— Umieść w stanie wstrzymania</span><span class="sxs-lookup"><span data-stu-id="12647-342">`true` - put on standby</span></span> | <span data-ttu-id="12647-343">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="12647-343">.NET Core 1.0</span></span> |
| <span data-ttu-id="12647-344">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="12647-344">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="12647-345">`false`— wydanie do systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="12647-345">`false` - release to OS</span></span><br/><span data-ttu-id="12647-346">`true`— Umieść w stanie wstrzymania</span><span class="sxs-lookup"><span data-stu-id="12647-346">`true` - put on standby</span></span> | <span data-ttu-id="12647-347">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="12647-347">.NET Core 1.0</span></span> |
| <span data-ttu-id="12647-348">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="12647-348">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="12647-349">`0`— wydanie do systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="12647-349">`0` - release to OS</span></span><br/><span data-ttu-id="12647-350">`1`— Umieść w stanie wstrzymania</span><span class="sxs-lookup"><span data-stu-id="12647-350">`1` - put on standby</span></span> | <span data-ttu-id="12647-351">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="12647-351">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="12647-352">Przykłady</span><span class="sxs-lookup"><span data-stu-id="12647-352">Examples</span></span>

<span data-ttu-id="12647-353">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="12647-353">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="12647-354">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="12647-354">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="12647-355">Duże strony</span><span class="sxs-lookup"><span data-stu-id="12647-355">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="12647-356">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="12647-356">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="12647-357">Określa, czy mają być używane duże strony, gdy jest ustawiony limit sztywny sterty.</span><span class="sxs-lookup"><span data-stu-id="12647-357">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="12647-358">Domyślnie: nie używaj dużych stron, gdy jest ustawiony limit sztywny sterty.</span><span class="sxs-lookup"><span data-stu-id="12647-358">Default: Don't use large pages when a heap hard limit is set.</span></span> <span data-ttu-id="12647-359">Jest to równoznaczne z ustawieniem wartości `0` .</span><span class="sxs-lookup"><span data-stu-id="12647-359">This is equivalent to setting the value to `0`.</span></span>
- <span data-ttu-id="12647-360">Jest to ustawienie eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="12647-360">This is an experimental setting.</span></span>

| | <span data-ttu-id="12647-361">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="12647-361">Setting name</span></span> | <span data-ttu-id="12647-362">Wartości</span><span class="sxs-lookup"><span data-stu-id="12647-362">Values</span></span> | <span data-ttu-id="12647-363">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12647-363">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="12647-364">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="12647-364">**runtimeconfig.json**</span></span> | <span data-ttu-id="12647-365">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="12647-365">N/A</span></span> | <span data-ttu-id="12647-366">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="12647-366">N/A</span></span> | <span data-ttu-id="12647-367">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="12647-367">N/A</span></span> |
| <span data-ttu-id="12647-368">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="12647-368">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="12647-369">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="12647-369">`0` - disabled</span></span><br/><span data-ttu-id="12647-370">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="12647-370">`1` - enabled</span></span> | <span data-ttu-id="12647-371">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="12647-371">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="12647-372">Duże obiekty</span><span class="sxs-lookup"><span data-stu-id="12647-372">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="12647-373">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="12647-373">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="12647-374">Konfiguruje obsługę modułu wyrzucania elementów bezużytecznych na platformach 64-bitowych dla tablic, które są większe niż 2 gigabajty (GB) w łącznym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="12647-374">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="12647-375">Domyślnie: GLOBALna obsługa tablic o pojemności większej niż 2 GB.</span><span class="sxs-lookup"><span data-stu-id="12647-375">Default: GC supports arrays greater than 2-GB.</span></span> <span data-ttu-id="12647-376">Jest to równoznaczne z ustawieniem wartości `1` .</span><span class="sxs-lookup"><span data-stu-id="12647-376">This is equivalent to setting the value to `1`.</span></span>
- <span data-ttu-id="12647-377">Ta opcja może stać się przestarzała w przyszłej wersji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="12647-377">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="12647-378">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="12647-378">Setting name</span></span> | <span data-ttu-id="12647-379">Wartości</span><span class="sxs-lookup"><span data-stu-id="12647-379">Values</span></span> | <span data-ttu-id="12647-380">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12647-380">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="12647-381">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="12647-381">**runtimeconfig.json**</span></span> | <span data-ttu-id="12647-382">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="12647-382">N/A</span></span> | <span data-ttu-id="12647-383">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="12647-383">N/A</span></span> | <span data-ttu-id="12647-384">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="12647-384">N/A</span></span> |
| <span data-ttu-id="12647-385">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="12647-385">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="12647-386">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="12647-386">`1` - enabled</span></span><br/> <span data-ttu-id="12647-387">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="12647-387">`0` - disabled</span></span> | <span data-ttu-id="12647-388">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="12647-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="12647-389">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="12647-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="12647-390">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="12647-390">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="12647-391">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="12647-391">`1` - enabled</span></span><br/> <span data-ttu-id="12647-392">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="12647-392">`0` - disabled</span></span> | <span data-ttu-id="12647-393">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="12647-393">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="12647-394">Próg sterty dla dużego obiektu</span><span class="sxs-lookup"><span data-stu-id="12647-394">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="12647-395">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="12647-395">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="12647-396">Określa rozmiar progu (w bajtach), który powoduje, że obiekty są na stosie dużego obiektu (LOH).</span><span class="sxs-lookup"><span data-stu-id="12647-396">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="12647-397">Domyślny próg to 85 000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="12647-397">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="12647-398">Określona wartość musi być większa niż wartość progu domyślnego.</span><span class="sxs-lookup"><span data-stu-id="12647-398">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="12647-399">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="12647-399">Setting name</span></span> | <span data-ttu-id="12647-400">Wartości</span><span class="sxs-lookup"><span data-stu-id="12647-400">Values</span></span> | <span data-ttu-id="12647-401">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12647-401">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="12647-402">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="12647-402">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="12647-403">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="12647-403">*decimal value*</span></span> | <span data-ttu-id="12647-404">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="12647-404">.NET Core 1.0</span></span> |
| <span data-ttu-id="12647-405">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="12647-405">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="12647-406">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="12647-406">*hexadecimal value*</span></span> | <span data-ttu-id="12647-407">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="12647-407">.NET Core 1.0</span></span> |
| <span data-ttu-id="12647-408">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="12647-408">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="12647-409">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="12647-409">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="12647-410">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="12647-410">*decimal value*</span></span> | <span data-ttu-id="12647-411"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="12647-411">.NET Framework 4.8</span></span> |

<span data-ttu-id="12647-412">Przykład:</span><span class="sxs-lookup"><span data-stu-id="12647-412">Example:</span></span>

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
> <span data-ttu-id="12647-413">Jeśli ustawiasz opcję w *runtimeconfig. JSON*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="12647-413">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="12647-414">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="12647-414">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="12647-415">Na przykład, aby ustawić rozmiar progu 120 000 bajtów, wartości byłyby 120000 dla pliku JSON oraz 0x1D4C0 lub 1D4C0 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="12647-415">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="12647-416">Autonomiczna GC</span><span class="sxs-lookup"><span data-stu-id="12647-416">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="12647-417">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="12647-417">COMPlus_GCName</span></span>

- <span data-ttu-id="12647-418">Określa ścieżkę do biblioteki zawierającej Moduł wyrzucania elementów bezużytecznych, który środowisko uruchomieniowe zamierza załadować.</span><span class="sxs-lookup"><span data-stu-id="12647-418">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="12647-419">Aby uzyskać więcej informacji, zobacz [prekonstrukcja modułu ładującego GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="12647-419">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="12647-420">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="12647-420">Setting name</span></span> | <span data-ttu-id="12647-421">Wartości</span><span class="sxs-lookup"><span data-stu-id="12647-421">Values</span></span> | <span data-ttu-id="12647-422">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12647-422">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="12647-423">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="12647-423">**runtimeconfig.json**</span></span> | <span data-ttu-id="12647-424">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="12647-424">N/A</span></span> | <span data-ttu-id="12647-425">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="12647-425">N/A</span></span> | <span data-ttu-id="12647-426">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="12647-426">N/A</span></span> |
| <span data-ttu-id="12647-427">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="12647-427">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="12647-428">*string_path*</span><span class="sxs-lookup"><span data-stu-id="12647-428">*string_path*</span></span> | <span data-ttu-id="12647-429">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="12647-429">.NET Core 2.0</span></span> |
