---
title: Ustawienia konfiguracji modułu zbierającego elementy bezużyteczne
description: Dowiedz się więcej o ustawieniach czasu wykonywania do konfigurowania sposobu zarządzania pamięcią przez moduł zbierający elementy bezużyteczne dla aplikacji .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 044083d69601f5092724a46d358b2ee5673d428d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733518"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="929bf-103">Opcje konfiguracji w czasie wykonywania dla wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="929bf-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="929bf-104">Ta strona zawiera informacje o ustawieniach modułu odśmiecania pamięci (GC), które można zmienić w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="929bf-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="929bf-105">Jeśli próbujesz osiągnąć najwyższą wydajność uruchomionej aplikacji, rozważ użycie tych ustawień.</span><span class="sxs-lookup"><span data-stu-id="929bf-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="929bf-106">Jednak wartości domyślne zapewniają optymalną wydajność dla większości aplikacji w typowych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="929bf-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="929bf-107">Ustawienia są rozmieszczone w grupach na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="929bf-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="929bf-108">Ustawienia w każdej grupie są powszechnie używane w połączeniu ze sobą w celu osiągnięcia określonego wyniku.</span><span class="sxs-lookup"><span data-stu-id="929bf-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="929bf-109">Te ustawienia mogą być również zmieniane dynamicznie przez aplikację, ponieważ jest uruchomiona, więc wszystkie ustawienia czasu wykonywania, które ustawisz, mogą zostać zastąpione.</span><span class="sxs-lookup"><span data-stu-id="929bf-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="929bf-110">Niektóre ustawienia, takie jak [poziom opóźnienia,](../../standard/garbage-collection/latency.md)są zazwyczaj ustawiane tylko za pośrednictwem interfejsu API w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="929bf-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="929bf-111">Takie ustawienia są pomijane na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="929bf-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="929bf-112">W przypadku wartości liczbowych należy użyć notacji dziesiętnej dla ustawień w pliku *runtimeconfig.json* i notacji szesnastkowej dla ustawień zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="929bf-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="929bf-113">W przypadku wartości szesnastkowych można określić je z prefiksem "0x" lub bez nich.</span><span class="sxs-lookup"><span data-stu-id="929bf-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="929bf-114">Smaki wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="929bf-114">Flavors of garbage collection</span></span>

<span data-ttu-id="929bf-115">Dwa główne smaki wyrzucania elementów bezużytecznych to stacja robocza GC i gc serwera.</span><span class="sxs-lookup"><span data-stu-id="929bf-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="929bf-116">Aby uzyskać więcej informacji na temat różnic między tymi dwoma, zobacz [podstawy wyrzucania elementów bezużytecznych](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="929bf-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="929bf-117">Podsmaki wyrzucania elementów bezużytecznych są tła i nierównoczesnych.</span><span class="sxs-lookup"><span data-stu-id="929bf-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="929bf-118">Użyj następujących ustawień, aby wybrać smaki wyrzucania elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="929bf-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="929bf-119">System.GC.Serwer/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="929bf-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="929bf-120">Określa, czy aplikacja używa wyrzucania elementów bezużytecznych stacji roboczej, czy wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="929bf-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="929bf-121">Domyślnie: Wyrzucanie elementów`false`bezużytecznych stacji roboczej ( ).</span><span class="sxs-lookup"><span data-stu-id="929bf-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="929bf-122">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="929bf-122">Setting name</span></span> | <span data-ttu-id="929bf-123">Wartości</span><span class="sxs-lookup"><span data-stu-id="929bf-123">Values</span></span> | <span data-ttu-id="929bf-124">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="929bf-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="929bf-125">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="929bf-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="929bf-126">`false`- stacja robocza</span><span class="sxs-lookup"><span data-stu-id="929bf-126">`false` - workstation</span></span><br/><span data-ttu-id="929bf-127">`true`- serwer</span><span class="sxs-lookup"><span data-stu-id="929bf-127">`true` - server</span></span> | <span data-ttu-id="929bf-128">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="929bf-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="929bf-129">**MSBuild, właściwość**</span><span class="sxs-lookup"><span data-stu-id="929bf-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="929bf-130">`false`- stacja robocza</span><span class="sxs-lookup"><span data-stu-id="929bf-130">`false` - workstation</span></span><br/><span data-ttu-id="929bf-131">`true`- serwer</span><span class="sxs-lookup"><span data-stu-id="929bf-131">`true` - server</span></span> | <span data-ttu-id="929bf-132">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="929bf-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="929bf-133">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="929bf-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="929bf-134">`0`- stacja robocza</span><span class="sxs-lookup"><span data-stu-id="929bf-134">`0` - workstation</span></span><br/><span data-ttu-id="929bf-135">`1`- serwer</span><span class="sxs-lookup"><span data-stu-id="929bf-135">`1` - server</span></span> | <span data-ttu-id="929bf-136">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="929bf-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="929bf-137">**App.config dla platformy .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="929bf-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="929bf-138">Serwer GC</span><span class="sxs-lookup"><span data-stu-id="929bf-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="929bf-139">`false`- stacja robocza</span><span class="sxs-lookup"><span data-stu-id="929bf-139">`false` - workstation</span></span><br/><span data-ttu-id="929bf-140">`true`- serwer</span><span class="sxs-lookup"><span data-stu-id="929bf-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="929bf-141">Przykłady</span><span class="sxs-lookup"><span data-stu-id="929bf-141">Examples</span></span>

<span data-ttu-id="929bf-142">*plik runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="929bf-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="929bf-143">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="929bf-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="929bf-144">System.GC.Jednobieżny/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="929bf-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="929bf-145">Konfiguruje, czy w tle (równoczesne) wyrzucanie elementów bezużytecznych jest włączone.</span><span class="sxs-lookup"><span data-stu-id="929bf-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="929bf-146">Domyślnie: Włączone`true`( ).</span><span class="sxs-lookup"><span data-stu-id="929bf-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="929bf-147">Aby uzyskać więcej informacji, zobacz [Wyrzucanie elementów bezużytecznych w tle](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) i [wyrzucanie elementów bezużytecznych serwera w tle](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="929bf-147">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="929bf-148">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="929bf-148">Setting name</span></span> | <span data-ttu-id="929bf-149">Wartości</span><span class="sxs-lookup"><span data-stu-id="929bf-149">Values</span></span> | <span data-ttu-id="929bf-150">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="929bf-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="929bf-151">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="929bf-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="929bf-152">`true`- tło GC</span><span class="sxs-lookup"><span data-stu-id="929bf-152">`true` - background GC</span></span><br/><span data-ttu-id="929bf-153">`false`- niewspółbieżny GC</span><span class="sxs-lookup"><span data-stu-id="929bf-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="929bf-154">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="929bf-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="929bf-155">**MSBuild, właściwość**</span><span class="sxs-lookup"><span data-stu-id="929bf-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="929bf-156">`true`- tło GC</span><span class="sxs-lookup"><span data-stu-id="929bf-156">`true` - background GC</span></span><br/><span data-ttu-id="929bf-157">`false`- niewspółbieżny GC</span><span class="sxs-lookup"><span data-stu-id="929bf-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="929bf-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="929bf-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="929bf-159">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="929bf-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="929bf-160">`true`- tło GC</span><span class="sxs-lookup"><span data-stu-id="929bf-160">`true` - background GC</span></span><br/><span data-ttu-id="929bf-161">`false`- niewspółbieżny GC</span><span class="sxs-lookup"><span data-stu-id="929bf-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="929bf-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="929bf-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="929bf-163">**App.config dla platformy .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="929bf-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="929bf-164">gcPrąd jednobieżny</span><span class="sxs-lookup"><span data-stu-id="929bf-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="929bf-165">`true`- tło GC</span><span class="sxs-lookup"><span data-stu-id="929bf-165">`true` - background GC</span></span><br/><span data-ttu-id="929bf-166">`false`- niewspółbieżny GC</span><span class="sxs-lookup"><span data-stu-id="929bf-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="929bf-167">Przykłady</span><span class="sxs-lookup"><span data-stu-id="929bf-167">Examples</span></span>

<span data-ttu-id="929bf-168">*plik runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="929bf-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="929bf-169">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="929bf-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="929bf-170">Zarządzanie zużyciem zasobów</span><span class="sxs-lookup"><span data-stu-id="929bf-170">Manage resource usage</span></span>

<span data-ttu-id="929bf-171">Użyj ustawień opisanych w tej sekcji, aby zarządzać pamięcimodułu modułu zbierającego elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="929bf-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="929bf-172">Aby uzyskać więcej informacji na temat niektórych z tych ustawień, zobacz [środkowy grunt między stacją roboczą a wpisem](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blogu GC serwera.</span><span class="sxs-lookup"><span data-stu-id="929bf-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="929bf-173">System.GC.HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="929bf-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="929bf-174">Ogranicza liczbę stert utworzonych przez moduł zbierający elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="929bf-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="929bf-175">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="929bf-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="929bf-176">Jeśli koligacja procesora GC jest włączona, co jest ustawieniem domyślnym, ustawienie liczby sterty animuje sterty/wątki `n` GC do pierwszych `n` procesorów.</span><span class="sxs-lookup"><span data-stu-id="929bf-176">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="929bf-177">(Użyj ustawienia maski afinitizu lub affinitize zakresów, aby dokładnie określić, które procesory mają się affinitize).)</span><span class="sxs-lookup"><span data-stu-id="929bf-177">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="929bf-178">Jeśli koligacja procesora GC jest wyłączona, to ustawienie ogranicza liczbę stert GC.</span><span class="sxs-lookup"><span data-stu-id="929bf-178">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="929bf-179">Aby uzyskać więcej informacji, zobacz [GCHeapCount uwagi](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="929bf-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="929bf-180">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="929bf-180">Setting name</span></span> | <span data-ttu-id="929bf-181">Wartości</span><span class="sxs-lookup"><span data-stu-id="929bf-181">Values</span></span> | <span data-ttu-id="929bf-182">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="929bf-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="929bf-183">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="929bf-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="929bf-184">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="929bf-184">*decimal value*</span></span> | <span data-ttu-id="929bf-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="929bf-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="929bf-186">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="929bf-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="929bf-187">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="929bf-187">*hexadecimal value*</span></span> | <span data-ttu-id="929bf-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="929bf-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="929bf-189">**App.config dla platformy .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="929bf-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="929bf-190">Liczba osób gcheap</span><span class="sxs-lookup"><span data-stu-id="929bf-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="929bf-191">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="929bf-191">*decimal value*</span></span> | <span data-ttu-id="929bf-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="929bf-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="929bf-193">Przykład:</span><span class="sxs-lookup"><span data-stu-id="929bf-193">Example:</span></span>

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
> <span data-ttu-id="929bf-194">Jeśli ustawiasz tę opcję w *runtimeconfig.json*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="929bf-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="929bf-195">Jeśli opcja jest ustawiana jako zmienna środowiskowa, należy określić wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="929bf-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="929bf-196">Na przykład, aby ograniczyć liczbę stert do 16, wartości będą wynosić 16 dla pliku JSON i 0x10 lub 10 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="929bf-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="929bf-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="929bf-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="929bf-198">Określa dokładne procesory, które powinny używać wątków modułu odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="929bf-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="929bf-199">Jeśli koligacja procesora jest `System.GC.NoAffinitize` `true`wyłączona przez ustawienie , to ustawienie jest ignorowane.</span><span class="sxs-lookup"><span data-stu-id="929bf-199">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="929bf-200">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="929bf-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="929bf-201">Wartość jest maską bitową, która definiuje procesory, które są dostępne dla procesu.</span><span class="sxs-lookup"><span data-stu-id="929bf-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="929bf-202">Na przykład wartość dziesiętna 1023 (lub wartość szesnastkowa 0x3FF lub 3FF, jeśli używasz zmiennej środowiskowej) jest 0011 1111 1111 w notacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="929bf-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="929bf-203">Określa, że ma być używanych pierwszych procesorów 10.</span><span class="sxs-lookup"><span data-stu-id="929bf-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="929bf-204">Aby określić następne procesory 10, czyli procesory 10-19, należy określić wartość dziesiętną 1047552 (lub wartość szesnastkową 0xFFC00 lub FFC00), która jest równoważna wartości binarnej 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="929bf-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="929bf-205">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="929bf-205">Setting name</span></span> | <span data-ttu-id="929bf-206">Wartości</span><span class="sxs-lookup"><span data-stu-id="929bf-206">Values</span></span> | <span data-ttu-id="929bf-207">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="929bf-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="929bf-208">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="929bf-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="929bf-209">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="929bf-209">*decimal value*</span></span> | <span data-ttu-id="929bf-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="929bf-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="929bf-211">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="929bf-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="929bf-212">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="929bf-212">*hexadecimal value*</span></span> | <span data-ttu-id="929bf-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="929bf-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="929bf-214">**App.config dla platformy .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="929bf-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="929bf-215">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="929bf-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="929bf-216">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="929bf-216">*decimal value*</span></span> | <span data-ttu-id="929bf-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="929bf-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="929bf-218">Przykład:</span><span class="sxs-lookup"><span data-stu-id="929bf-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="929bf-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="929bf-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="929bf-220">Określa listę procesorów do użycia dla wątków modułu odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="929bf-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="929bf-221">To ustawienie jest `System.GC.HeapAffinitizeMask`podobne do , z wyjątkiem pozwala określić więcej niż 64 procesorów.</span><span class="sxs-lookup"><span data-stu-id="929bf-221">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="929bf-222">W przypadku systemów operacyjnych Windows prefiks numeru procesora lub zakresu z odpowiednią [grupą procesora](/windows/win32/procthread/processor-groups), na przykład "0:1-10,0:12,1:50-52,1:70".</span><span class="sxs-lookup"><span data-stu-id="929bf-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="929bf-223">Jeśli koligacja procesora jest `System.GC.NoAffinitize` `true`wyłączona przez ustawienie , to ustawienie jest ignorowane.</span><span class="sxs-lookup"><span data-stu-id="929bf-223">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="929bf-224">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="929bf-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="929bf-225">Aby uzyskać więcej informacji, zobacz [Ulepszanie konfiguracji procesora DLA GC na komputerach z procesorami > 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="929bf-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="929bf-226">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="929bf-226">Setting name</span></span> | <span data-ttu-id="929bf-227">Wartości</span><span class="sxs-lookup"><span data-stu-id="929bf-227">Values</span></span> | <span data-ttu-id="929bf-228">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="929bf-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="929bf-229">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="929bf-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="929bf-230">Oddzielona przecinkami lista numerów procesorów lub zakresów numerów procesorów.</span><span class="sxs-lookup"><span data-stu-id="929bf-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="929bf-231">Przykład Uniksa: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="929bf-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="929bf-232">Przykład systemu Windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="929bf-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="929bf-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="929bf-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="929bf-234">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="929bf-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="929bf-235">Oddzielona przecinkami lista numerów procesorów lub zakresów numerów procesorów.</span><span class="sxs-lookup"><span data-stu-id="929bf-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="929bf-236">Przykład Uniksa: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="929bf-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="929bf-237">Przykład systemu Windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="929bf-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="929bf-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="929bf-238">.NET Core 3.0</span></span> |

<span data-ttu-id="929bf-239">Przykład:</span><span class="sxs-lookup"><span data-stu-id="929bf-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="929bf-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="929bf-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="929bf-241">Konfiguruje, czy moduł zbierający elementy bezużyteczne używa [grup procesora CPU,](/windows/win32/procthread/processor-groups) czy nie.</span><span class="sxs-lookup"><span data-stu-id="929bf-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="929bf-242">Gdy 64-bitowy komputer z systemem Windows ma wiele grup procesora CPU, oznacza to, że istnieje więcej niż 64 procesorów, włączenie tego elementu rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="929bf-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="929bf-243">Moduł zbierający elementy bezużyteczne używa wszystkich rdzeni do tworzenia i równoważenia stert.</span><span class="sxs-lookup"><span data-stu-id="929bf-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="929bf-244">Dotyczy wyrzucania elementów bezużytecznych serwera tylko w 64-bitowych systemach operacyjnych Windows.</span><span class="sxs-lookup"><span data-stu-id="929bf-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="929bf-245">Domyślnie: Wyłączone`0`( ).</span><span class="sxs-lookup"><span data-stu-id="929bf-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="929bf-246">Aby uzyskać więcej informacji, zobacz [Ulepszanie konfiguracji procesora DLA GC na komputerach z procesorami > 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="929bf-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="929bf-247">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="929bf-247">Setting name</span></span> | <span data-ttu-id="929bf-248">Wartości</span><span class="sxs-lookup"><span data-stu-id="929bf-248">Values</span></span> | <span data-ttu-id="929bf-249">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="929bf-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="929bf-250">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="929bf-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="929bf-251">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="929bf-251">N/A</span></span> | <span data-ttu-id="929bf-252">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="929bf-252">N/A</span></span> | <span data-ttu-id="929bf-253">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="929bf-253">N/A</span></span> |
| <span data-ttu-id="929bf-254">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="929bf-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="929bf-255">`0`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="929bf-255">`0` - disabled</span></span><br/><span data-ttu-id="929bf-256">`1`- włączona</span><span class="sxs-lookup"><span data-stu-id="929bf-256">`1` - enabled</span></span> | <span data-ttu-id="929bf-257">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="929bf-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="929bf-258">**App.config dla platformy .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="929bf-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="929bf-259">Grupa GCCpu</span><span class="sxs-lookup"><span data-stu-id="929bf-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="929bf-260">`false`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="929bf-260">`false` - disabled</span></span><br/><span data-ttu-id="929bf-261">`true`- włączona</span><span class="sxs-lookup"><span data-stu-id="929bf-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="929bf-262">Aby skonfigurować program CLR (Common Language runtime) do dystrybucji wątków z puli wątków we wszystkich grupach procesorów, włącz opcję [elementu Thread_UseAllCpuGroups.](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)</span><span class="sxs-lookup"><span data-stu-id="929bf-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="929bf-263">W przypadku aplikacji .NET Core tę opcję można `COMPlus_Thread_UseAllCpuGroups` włączyć, `1`ustawiając wartość zmiennej środowiskowej na .</span><span class="sxs-lookup"><span data-stu-id="929bf-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="929bf-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="929bf-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="929bf-265">Określa, czy *affinitize* wątków wyrzucania elementów bezużytecznych z procesorów.</span><span class="sxs-lookup"><span data-stu-id="929bf-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="929bf-266">Affinitize wątku GC oznacza, że można uruchomić tylko na jego określonego procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="929bf-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="929bf-267">Sterta jest tworzona dla każdego wątku GC.</span><span class="sxs-lookup"><span data-stu-id="929bf-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="929bf-268">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="929bf-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="929bf-269">Domyślnie: Affinitize wątków wyrzucania`false`elementów bezużytecznych z procesorów ( ).</span><span class="sxs-lookup"><span data-stu-id="929bf-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="929bf-270">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="929bf-270">Setting name</span></span> | <span data-ttu-id="929bf-271">Wartości</span><span class="sxs-lookup"><span data-stu-id="929bf-271">Values</span></span> | <span data-ttu-id="929bf-272">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="929bf-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="929bf-273">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="929bf-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="929bf-274">`false`- affinitize</span><span class="sxs-lookup"><span data-stu-id="929bf-274">`false` - affinitize</span></span><br/><span data-ttu-id="929bf-275">`true`- nie affinitize</span><span class="sxs-lookup"><span data-stu-id="929bf-275">`true` - don't affinitize</span></span> | <span data-ttu-id="929bf-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="929bf-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="929bf-277">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="929bf-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="929bf-278">`0`- affinitize</span><span class="sxs-lookup"><span data-stu-id="929bf-278">`0` - affinitize</span></span><br/><span data-ttu-id="929bf-279">`1`- nie affinitize</span><span class="sxs-lookup"><span data-stu-id="929bf-279">`1` - don't affinitize</span></span> | <span data-ttu-id="929bf-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="929bf-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="929bf-281">**App.config dla platformy .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="929bf-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="929bf-282">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="929bf-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="929bf-283">`false`- affinitize</span><span class="sxs-lookup"><span data-stu-id="929bf-283">`false` - affinitize</span></span><br/><span data-ttu-id="929bf-284">`true`- nie affinitize</span><span class="sxs-lookup"><span data-stu-id="929bf-284">`true` - don't affinitize</span></span> | <span data-ttu-id="929bf-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="929bf-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="929bf-286">Przykład:</span><span class="sxs-lookup"><span data-stu-id="929bf-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="929bf-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="929bf-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="929bf-288">Określa maksymalny rozmiar zatwierdzenia w bajtach dla księgowości GC i księgowości GC.</span><span class="sxs-lookup"><span data-stu-id="929bf-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="929bf-289">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="929bf-289">Setting name</span></span> | <span data-ttu-id="929bf-290">Wartości</span><span class="sxs-lookup"><span data-stu-id="929bf-290">Values</span></span> | <span data-ttu-id="929bf-291">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="929bf-291">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="929bf-292">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="929bf-292">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="929bf-293">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="929bf-293">*decimal value*</span></span> | <span data-ttu-id="929bf-294">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="929bf-294">.NET Core 3.0</span></span> |
| <span data-ttu-id="929bf-295">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="929bf-295">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="929bf-296">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="929bf-296">*hexadecimal value*</span></span> | <span data-ttu-id="929bf-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="929bf-297">.NET Core 3.0</span></span> |

<span data-ttu-id="929bf-298">Przykład:</span><span class="sxs-lookup"><span data-stu-id="929bf-298">Example:</span></span>

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
> <span data-ttu-id="929bf-299">Jeśli ustawiasz tę opcję w *runtimeconfig.json*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="929bf-299">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="929bf-300">Jeśli opcja jest ustawiana jako zmienna środowiskowa, należy określić wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="929bf-300">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="929bf-301">Na przykład, aby określić limit twardy sterty 200 mebibajtów (MiB), wartości będą 209715200 dla pliku JSON i 0xC800000 lub C800000 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="929bf-301">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="929bf-302">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="929bf-302">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="929bf-303">Określa użycie sterty GC jako procent całkowitej pamięci.</span><span class="sxs-lookup"><span data-stu-id="929bf-303">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="929bf-304">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="929bf-304">Setting name</span></span> | <span data-ttu-id="929bf-305">Wartości</span><span class="sxs-lookup"><span data-stu-id="929bf-305">Values</span></span> | <span data-ttu-id="929bf-306">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="929bf-306">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="929bf-307">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="929bf-307">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="929bf-308">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="929bf-308">*decimal value*</span></span> | <span data-ttu-id="929bf-309">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="929bf-309">.NET Core 3.0</span></span> |
| <span data-ttu-id="929bf-310">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="929bf-310">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="929bf-311">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="929bf-311">*hexadecimal value*</span></span> | <span data-ttu-id="929bf-312">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="929bf-312">.NET Core 3.0</span></span> |

<span data-ttu-id="929bf-313">Przykład:</span><span class="sxs-lookup"><span data-stu-id="929bf-313">Example:</span></span>

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
> <span data-ttu-id="929bf-314">Jeśli ustawiasz tę opcję w *runtimeconfig.json*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="929bf-314">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="929bf-315">Jeśli opcja jest ustawiana jako zmienna środowiskowa, należy określić wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="929bf-315">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="929bf-316">Na przykład, aby ograniczyć użycie sterty do 30%, wartości będą 30 dla pliku JSON i 0x1E lub 1E dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="929bf-316">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="929bf-317">System.GC.RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="929bf-317">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="929bf-318">Określa, czy segmenty, które mają zostać usunięte, są umieszczane na liście gotowości do wykorzystania w przyszłości, czy też są zwalniane z powrotem do systemu operacyjnego(OS).</span><span class="sxs-lookup"><span data-stu-id="929bf-318">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="929bf-319">Domyślnie: Zwalnianie segmentów z`false`powrotem do systemu operacyjnego ( ).</span><span class="sxs-lookup"><span data-stu-id="929bf-319">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="929bf-320">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="929bf-320">Setting name</span></span> | <span data-ttu-id="929bf-321">Wartości</span><span class="sxs-lookup"><span data-stu-id="929bf-321">Values</span></span> | <span data-ttu-id="929bf-322">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="929bf-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="929bf-323">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="929bf-323">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="929bf-324">`false`- zwolnienie do os</span><span class="sxs-lookup"><span data-stu-id="929bf-324">`false` - release to OS</span></span><br/><span data-ttu-id="929bf-325">`true`- umieścić w trybie gotowości</span><span class="sxs-lookup"><span data-stu-id="929bf-325">`true` - put on standby</span></span> | <span data-ttu-id="929bf-326">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="929bf-326">.NET Core 1.0</span></span> |
| <span data-ttu-id="929bf-327">**MSBuild, właściwość**</span><span class="sxs-lookup"><span data-stu-id="929bf-327">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="929bf-328">`false`- zwolnienie do os</span><span class="sxs-lookup"><span data-stu-id="929bf-328">`false` - release to OS</span></span><br/><span data-ttu-id="929bf-329">`true`- umieścić w trybie gotowości</span><span class="sxs-lookup"><span data-stu-id="929bf-329">`true` - put on standby</span></span> | <span data-ttu-id="929bf-330">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="929bf-330">.NET Core 1.0</span></span> |
| <span data-ttu-id="929bf-331">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="929bf-331">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="929bf-332">`0`- zwolnienie do os</span><span class="sxs-lookup"><span data-stu-id="929bf-332">`0` - release to OS</span></span><br/><span data-ttu-id="929bf-333">`1`- umieścić w trybie gotowości</span><span class="sxs-lookup"><span data-stu-id="929bf-333">`1` - put on standby</span></span> | <span data-ttu-id="929bf-334">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="929bf-334">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="929bf-335">Przykłady</span><span class="sxs-lookup"><span data-stu-id="929bf-335">Examples</span></span>

<span data-ttu-id="929bf-336">*plik runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="929bf-336">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="929bf-337">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="929bf-337">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="929bf-338">Duże strony</span><span class="sxs-lookup"><span data-stu-id="929bf-338">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="929bf-339">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="929bf-339">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="929bf-340">Określa, czy duże strony mają być używane, gdy ustawiono twardy limit sterty.</span><span class="sxs-lookup"><span data-stu-id="929bf-340">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="929bf-341">Domyślnie: Wyłączone`0`( ).</span><span class="sxs-lookup"><span data-stu-id="929bf-341">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="929bf-342">Jest to ustawienie eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="929bf-342">This is an experimental setting.</span></span>

| | <span data-ttu-id="929bf-343">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="929bf-343">Setting name</span></span> | <span data-ttu-id="929bf-344">Wartości</span><span class="sxs-lookup"><span data-stu-id="929bf-344">Values</span></span> | <span data-ttu-id="929bf-345">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="929bf-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="929bf-346">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="929bf-346">**runtimeconfig.json**</span></span> | <span data-ttu-id="929bf-347">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="929bf-347">N/A</span></span> | <span data-ttu-id="929bf-348">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="929bf-348">N/A</span></span> | <span data-ttu-id="929bf-349">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="929bf-349">N/A</span></span> |
| <span data-ttu-id="929bf-350">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="929bf-350">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="929bf-351">`0`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="929bf-351">`0` - disabled</span></span><br/><span data-ttu-id="929bf-352">`1`- włączona</span><span class="sxs-lookup"><span data-stu-id="929bf-352">`1` - enabled</span></span> | <span data-ttu-id="929bf-353">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="929bf-353">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="929bf-354">Duże obiekty</span><span class="sxs-lookup"><span data-stu-id="929bf-354">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="929bf-355">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="929bf-355">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="929bf-356">Konfiguruje obsługę modułów zbierających elementy bezużyteczne na platformach 64-bitowych dla macierzy o rozmiarze większym niż 2 gigabajty (GB) w całkowitym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="929bf-356">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="929bf-357">Domyślnie: Włączone`1`( ).</span><span class="sxs-lookup"><span data-stu-id="929bf-357">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="929bf-358">Ta opcja może stać się przestarzała w przyszłej wersji .NET.</span><span class="sxs-lookup"><span data-stu-id="929bf-358">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="929bf-359">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="929bf-359">Setting name</span></span> | <span data-ttu-id="929bf-360">Wartości</span><span class="sxs-lookup"><span data-stu-id="929bf-360">Values</span></span> | <span data-ttu-id="929bf-361">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="929bf-361">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="929bf-362">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="929bf-362">**runtimeconfig.json**</span></span> | <span data-ttu-id="929bf-363">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="929bf-363">N/A</span></span> | <span data-ttu-id="929bf-364">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="929bf-364">N/A</span></span> | <span data-ttu-id="929bf-365">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="929bf-365">N/A</span></span> |
| <span data-ttu-id="929bf-366">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="929bf-366">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="929bf-367">`1`- włączona</span><span class="sxs-lookup"><span data-stu-id="929bf-367">`1` - enabled</span></span><br/> <span data-ttu-id="929bf-368">`0`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="929bf-368">`0` - disabled</span></span> | <span data-ttu-id="929bf-369">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="929bf-369">.NET Core 1.0</span></span> |
| <span data-ttu-id="929bf-370">**App.config dla platformy .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="929bf-370">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="929bf-371">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="929bf-371">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="929bf-372">`1`- włączona</span><span class="sxs-lookup"><span data-stu-id="929bf-372">`1` - enabled</span></span><br/> <span data-ttu-id="929bf-373">`0`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="929bf-373">`0` - disabled</span></span> | <span data-ttu-id="929bf-374">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="929bf-374">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="929bf-375">Próg sterty dużych obiektów</span><span class="sxs-lookup"><span data-stu-id="929bf-375">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="929bf-376">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="929bf-376">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="929bf-377">Określa rozmiar progu w bajtach, który powoduje, że obiekty są na stercie dużych obiektów (LOH).</span><span class="sxs-lookup"><span data-stu-id="929bf-377">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="929bf-378">Domyślny próg to 85 000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="929bf-378">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="929bf-379">Określona wartość musi być większa niż próg domyślny.</span><span class="sxs-lookup"><span data-stu-id="929bf-379">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="929bf-380">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="929bf-380">Setting name</span></span> | <span data-ttu-id="929bf-381">Wartości</span><span class="sxs-lookup"><span data-stu-id="929bf-381">Values</span></span> | <span data-ttu-id="929bf-382">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="929bf-382">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="929bf-383">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="929bf-383">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="929bf-384">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="929bf-384">*decimal value*</span></span> | <span data-ttu-id="929bf-385">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="929bf-385">.NET Core 1.0</span></span> |
| <span data-ttu-id="929bf-386">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="929bf-386">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="929bf-387">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="929bf-387">*hexadecimal value*</span></span> | <span data-ttu-id="929bf-388">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="929bf-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="929bf-389">**App.config dla platformy .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="929bf-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="929bf-390">Próg GCLOH</span><span class="sxs-lookup"><span data-stu-id="929bf-390">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="929bf-391">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="929bf-391">*decimal value*</span></span> | <span data-ttu-id="929bf-392"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="929bf-392">.NET Framework 4.8</span></span> |

<span data-ttu-id="929bf-393">Przykład:</span><span class="sxs-lookup"><span data-stu-id="929bf-393">Example:</span></span>

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
> <span data-ttu-id="929bf-394">Jeśli ustawiasz tę opcję w *runtimeconfig.json*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="929bf-394">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="929bf-395">Jeśli opcja jest ustawiana jako zmienna środowiskowa, należy określić wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="929bf-395">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="929bf-396">Na przykład, aby ustawić rozmiar progu 120 000 bajtów, wartości będą wynosić 120000 dla pliku JSON i 0x1D4C0 lub 1D4C0 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="929bf-396">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="929bf-397">Samodzielny GC</span><span class="sxs-lookup"><span data-stu-id="929bf-397">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="929bf-398">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="929bf-398">COMPlus_GCName</span></span>

- <span data-ttu-id="929bf-399">Określa ścieżkę do biblioteki zawierającej moduł odśmiecania pamięci, który program runtime zamierza załadować.</span><span class="sxs-lookup"><span data-stu-id="929bf-399">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="929bf-400">Aby uzyskać więcej informacji, zobacz [Samodzielny projekt modułu ładującego GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="929bf-400">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="929bf-401">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="929bf-401">Setting name</span></span> | <span data-ttu-id="929bf-402">Wartości</span><span class="sxs-lookup"><span data-stu-id="929bf-402">Values</span></span> | <span data-ttu-id="929bf-403">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="929bf-403">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="929bf-404">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="929bf-404">**runtimeconfig.json**</span></span> | <span data-ttu-id="929bf-405">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="929bf-405">N/A</span></span> | <span data-ttu-id="929bf-406">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="929bf-406">N/A</span></span> | <span data-ttu-id="929bf-407">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="929bf-407">N/A</span></span> |
| <span data-ttu-id="929bf-408">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="929bf-408">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="929bf-409">*string_path*</span><span class="sxs-lookup"><span data-stu-id="929bf-409">*string_path*</span></span> | <span data-ttu-id="929bf-410">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="929bf-410">.NET Core 2.0</span></span> |
