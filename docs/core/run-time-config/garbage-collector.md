---
title: Ustawienia konfiguracji modułu zbierającego elementy bezużyteczne
description: Dowiedz się więcej o ustawieniach czasu wykonywania konfigurowania sposobu zarządzania pamięcią dla aplikacji .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: dfb641eeda03d1acaa4771bd6253fcb33c4082a6
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607813"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="a97e6-103">Opcje konfiguracji w czasie wykonywania wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="a97e6-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="a97e6-104">Ta strona zawiera informacje o ustawieniach modułu zbierającego elementy bezużyteczne (GC), które można zmienić w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a97e6-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="a97e6-105">Jeśli próbujesz osiągnąć maksymalną wydajność uruchomionej aplikacji, rozważ użycie tych ustawień.</span><span class="sxs-lookup"><span data-stu-id="a97e6-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="a97e6-106">Jednak wartości domyślne zapewniają optymalną wydajność dla większości aplikacji w typowych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="a97e6-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="a97e6-107">Ustawienia są podzielone na grupy na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="a97e6-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="a97e6-108">Ustawienia w każdej grupie są powszechnie używane w połączeniu ze sobą w celu osiągnięcia określonego wyniku.</span><span class="sxs-lookup"><span data-stu-id="a97e6-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="a97e6-109">Te ustawienia mogą być również zmieniane dynamicznie przez aplikację, ponieważ jest uruchomiona, więc wszystkie ustawienia czasu wykonywania, które można ustawić, mogą zostać zastąpione.</span><span class="sxs-lookup"><span data-stu-id="a97e6-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="a97e6-110">Niektóre ustawienia, takie jak [poziom opóźnienia,](../../standard/garbage-collection/latency.md)są zazwyczaj ustawiane tylko za pośrednictwem interfejsu API w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="a97e6-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="a97e6-111">Takie ustawienia są pomijane na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="a97e6-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="a97e6-112">W przypadku wartości liczbowych należy użyć notacji dziesiętnej dla ustawień w pliku *runtimeconfig.json* i notacji szesnastowej dla ustawień zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="a97e6-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="a97e6-113">Dla wartości szesnastkowych można je określić z prefiksem "0x" lub bez niego.</span><span class="sxs-lookup"><span data-stu-id="a97e6-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="a97e6-114">Smaki wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="a97e6-114">Flavors of garbage collection</span></span>

<span data-ttu-id="a97e6-115">Dwa główne smaki wyrzucania elementów bezużytecznych są gc stacji roboczej i serwera GC.</span><span class="sxs-lookup"><span data-stu-id="a97e6-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="a97e6-116">Aby uzyskać więcej informacji na temat różnic między tymi dwoma, zobacz [Podstawy wyrzucania elementów bezużytecznych](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="a97e6-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="a97e6-117">Podpochrozumia wyrzucania elementów bezużytecznych są tła i nie jednobieżne.</span><span class="sxs-lookup"><span data-stu-id="a97e6-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="a97e6-118">Użyj następujących ustawień, aby wybrać smaki wyrzucania elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="a97e6-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="a97e6-119">System.GC.Serwer/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="a97e6-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="a97e6-120">Konfiguruje, czy aplikacja używa wyrzucania elementów bezużytecznych stacji roboczej lub modułu wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="a97e6-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="a97e6-121">Domyślnie: Wyrzucanie`false`elementów bezużytecznych na stacji roboczej ( ).</span><span class="sxs-lookup"><span data-stu-id="a97e6-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="a97e6-122">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a97e6-122">Setting name</span></span> | <span data-ttu-id="a97e6-123">Wartości</span><span class="sxs-lookup"><span data-stu-id="a97e6-123">Values</span></span> | <span data-ttu-id="a97e6-124">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="a97e6-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="a97e6-125">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a97e6-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="a97e6-126">`false`- stacja robocza</span><span class="sxs-lookup"><span data-stu-id="a97e6-126">`false` - workstation</span></span><br/><span data-ttu-id="a97e6-127">`true`- serwer</span><span class="sxs-lookup"><span data-stu-id="a97e6-127">`true` - server</span></span> | <span data-ttu-id="a97e6-128">.NET Rdzeń 1.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="a97e6-129">**Właściwość MSBuild**</span><span class="sxs-lookup"><span data-stu-id="a97e6-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="a97e6-130">`false`- stacja robocza</span><span class="sxs-lookup"><span data-stu-id="a97e6-130">`false` - workstation</span></span><br/><span data-ttu-id="a97e6-131">`true`- serwer</span><span class="sxs-lookup"><span data-stu-id="a97e6-131">`true` - server</span></span> | <span data-ttu-id="a97e6-132">.NET Rdzeń 1.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="a97e6-133">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a97e6-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="a97e6-134">`0`- stacja robocza</span><span class="sxs-lookup"><span data-stu-id="a97e6-134">`0` - workstation</span></span><br/><span data-ttu-id="a97e6-135">`1`- serwer</span><span class="sxs-lookup"><span data-stu-id="a97e6-135">`1` - server</span></span> | <span data-ttu-id="a97e6-136">.NET Rdzeń 1.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="a97e6-137">**app.config dla programu .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="a97e6-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="a97e6-138">Serwer GCServer</span><span class="sxs-lookup"><span data-stu-id="a97e6-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="a97e6-139">`false`- stacja robocza</span><span class="sxs-lookup"><span data-stu-id="a97e6-139">`false` - workstation</span></span><br/><span data-ttu-id="a97e6-140">`true`- serwer</span><span class="sxs-lookup"><span data-stu-id="a97e6-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="a97e6-141">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a97e6-141">Examples</span></span>

<span data-ttu-id="a97e6-142">*runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="a97e6-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="a97e6-143">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="a97e6-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="a97e6-144">System.GC.Równoczesne/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="a97e6-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="a97e6-145">Konfiguruje, czy tło (równoczesnych) wyrzucanie elementów bezużytecznych jest włączone.</span><span class="sxs-lookup"><span data-stu-id="a97e6-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="a97e6-146">Domyślnie: Włączone`true`( ).</span><span class="sxs-lookup"><span data-stu-id="a97e6-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="a97e6-147">Aby uzyskać więcej informacji, zobacz [Tło wyrzucania elementów bezużytecznych](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) i [wyrzucania elementów bezużytecznych serwera w tle](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="a97e6-147">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="a97e6-148">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a97e6-148">Setting name</span></span> | <span data-ttu-id="a97e6-149">Wartości</span><span class="sxs-lookup"><span data-stu-id="a97e6-149">Values</span></span> | <span data-ttu-id="a97e6-150">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="a97e6-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="a97e6-151">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a97e6-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="a97e6-152">`true`- tło GC</span><span class="sxs-lookup"><span data-stu-id="a97e6-152">`true` - background GC</span></span><br/><span data-ttu-id="a97e6-153">`false`- niebieżne GC</span><span class="sxs-lookup"><span data-stu-id="a97e6-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="a97e6-154">.NET Rdzeń 1.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="a97e6-155">**Właściwość MSBuild**</span><span class="sxs-lookup"><span data-stu-id="a97e6-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="a97e6-156">`true`- tło GC</span><span class="sxs-lookup"><span data-stu-id="a97e6-156">`true` - background GC</span></span><br/><span data-ttu-id="a97e6-157">`false`- niebieżne GC</span><span class="sxs-lookup"><span data-stu-id="a97e6-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="a97e6-158">.NET Rdzeń 1.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="a97e6-159">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a97e6-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="a97e6-160">`true`- tło GC</span><span class="sxs-lookup"><span data-stu-id="a97e6-160">`true` - background GC</span></span><br/><span data-ttu-id="a97e6-161">`false`- niebieżne GC</span><span class="sxs-lookup"><span data-stu-id="a97e6-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="a97e6-162">.NET Rdzeń 1.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="a97e6-163">**app.config dla programu .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="a97e6-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="a97e6-164">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="a97e6-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="a97e6-165">`true`- tło GC</span><span class="sxs-lookup"><span data-stu-id="a97e6-165">`true` - background GC</span></span><br/><span data-ttu-id="a97e6-166">`false`- niebieżne GC</span><span class="sxs-lookup"><span data-stu-id="a97e6-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="a97e6-167">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a97e6-167">Examples</span></span>

<span data-ttu-id="a97e6-168">*runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="a97e6-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="a97e6-169">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="a97e6-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="a97e6-170">Zarządzanie użyciem zasobów</span><span class="sxs-lookup"><span data-stu-id="a97e6-170">Manage resource usage</span></span>

<span data-ttu-id="a97e6-171">Użyj ustawień opisanych w tej sekcji, aby zarządzać pamięcią i użyciem procesora modułu zbierającego elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="a97e6-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="a97e6-172">Aby uzyskać więcej informacji na temat niektórych z tych ustawień, zobacz [Środkowy grunt między stacją roboczą a](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) wpisem blogu GC serwera.</span><span class="sxs-lookup"><span data-stu-id="a97e6-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="a97e6-173">System.GC.HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="a97e6-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="a97e6-174">Ogranicza liczbę stert utworzonych przez moduł zbierający elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="a97e6-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="a97e6-175">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="a97e6-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="a97e6-176">Jeśli [koligacja procesora GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) jest włączona, co jest ustawieniem domyślnym, ustawienie liczby stert affinitizes `n` GC sterty/wątki do pierwszych `n` procesorów.</span><span class="sxs-lookup"><span data-stu-id="a97e6-176">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="a97e6-177">(Użyj [affinitize maski](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) lub [affinitize ustawienia zakresów,](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) aby określić dokładnie, które procesory do affinitize.)</span><span class="sxs-lookup"><span data-stu-id="a97e6-177">(Use the [affinitize mask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask) or [affinitize ranges](#systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges) settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="a97e6-178">Jeśli [koligacja procesora GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) jest wyłączona, to ustawienie ogranicza liczbę stert GC.</span><span class="sxs-lookup"><span data-stu-id="a97e6-178">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="a97e6-179">Aby uzyskać więcej informacji, zobacz [uwagi GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="a97e6-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="a97e6-180">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a97e6-180">Setting name</span></span> | <span data-ttu-id="a97e6-181">Wartości</span><span class="sxs-lookup"><span data-stu-id="a97e6-181">Values</span></span> | <span data-ttu-id="a97e6-182">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="a97e6-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="a97e6-183">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a97e6-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="a97e6-184">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="a97e6-184">*decimal value*</span></span> | <span data-ttu-id="a97e6-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="a97e6-186">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a97e6-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="a97e6-187">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="a97e6-187">*hexadecimal value*</span></span> | <span data-ttu-id="a97e6-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="a97e6-189">**app.config dla programu .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="a97e6-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="a97e6-190">GCHeapCount (GCHeapCount)</span><span class="sxs-lookup"><span data-stu-id="a97e6-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="a97e6-191">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="a97e6-191">*decimal value*</span></span> | <span data-ttu-id="a97e6-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="a97e6-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="a97e6-193">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a97e6-193">Example:</span></span>

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
> <span data-ttu-id="a97e6-194">Jeśli ustawiasz opcję w *pliku runtimeconfig.json,* określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="a97e6-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="a97e6-195">Jeśli ustawiasz tę opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="a97e6-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="a97e6-196">Na przykład, aby ograniczyć liczbę stert do 16, wartości będą 16 dla pliku JSON i 0x10 lub 10 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="a97e6-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="a97e6-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="a97e6-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="a97e6-198">Określa dokładne procesory, które powinny być używane przez wątki modułu zbierającego elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="a97e6-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="a97e6-199">Jeśli [koligacja procesora GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) jest wyłączona, to ustawienie jest ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a97e6-199">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="a97e6-200">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="a97e6-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="a97e6-201">Wartość jest maską bitową definiującą procesory, które są dostępne dla procesu.</span><span class="sxs-lookup"><span data-stu-id="a97e6-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="a97e6-202">Na przykład wartość dziesiętna 1023 (lub wartość szesnastkowa 0x3FF lub 3FF, jeśli używasz zmiennej środowiskowej) jest 0011 1111 1111 w notacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="a97e6-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="a97e6-203">Określa to, że pierwsze procesory 10 mają być używane.</span><span class="sxs-lookup"><span data-stu-id="a97e6-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="a97e6-204">Aby określić następne 10 procesorów, czyli procesory 10-19, należy określić wartość dziesiętną 1047552 (lub wartość szesnastową 0xFFC00 lub FFC00), która jest równoważna wartości binarnej 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="a97e6-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="a97e6-205">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a97e6-205">Setting name</span></span> | <span data-ttu-id="a97e6-206">Wartości</span><span class="sxs-lookup"><span data-stu-id="a97e6-206">Values</span></span> | <span data-ttu-id="a97e6-207">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="a97e6-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="a97e6-208">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a97e6-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="a97e6-209">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="a97e6-209">*decimal value*</span></span> | <span data-ttu-id="a97e6-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="a97e6-211">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a97e6-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="a97e6-212">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="a97e6-212">*hexadecimal value*</span></span> | <span data-ttu-id="a97e6-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="a97e6-214">**app.config dla programu .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="a97e6-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="a97e6-215">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="a97e6-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="a97e6-216">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="a97e6-216">*decimal value*</span></span> | <span data-ttu-id="a97e6-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="a97e6-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="a97e6-218">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a97e6-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="a97e6-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="a97e6-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="a97e6-220">Określa listę procesorów, które mają być używane dla wątków modułu zbierającego elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="a97e6-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="a97e6-221">To ustawienie jest podobne do [systema.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), z tą różnicą, że umożliwia określenie więcej niż 64 procesorów.</span><span class="sxs-lookup"><span data-stu-id="a97e6-221">This setting is similar to [System.GC.HeapAffinitizeMask](#systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask), except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="a97e6-222">W przypadku systemów operacyjnych Windows prefiksuje numer procesora lub zakres z odpowiednią [grupą procesorów](/windows/win32/procthread/processor-groups), na przykład "0:1-10,0:12,1:50-52,1:70".</span><span class="sxs-lookup"><span data-stu-id="a97e6-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="a97e6-223">Jeśli [koligacja procesora GC](#systemgcnoaffinitizecomplus_gcnoaffinitize) jest wyłączona, to ustawienie jest ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a97e6-223">If [GC processor affinity](#systemgcnoaffinitizecomplus_gcnoaffinitize) is disabled, this setting is ignored.</span></span>
- <span data-ttu-id="a97e6-224">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="a97e6-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="a97e6-225">Aby uzyskać więcej informacji, zobacz [Ulepszanie konfiguracji procesora dla GC na komputerach z procesorami > 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="a97e6-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="a97e6-226">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a97e6-226">Setting name</span></span> | <span data-ttu-id="a97e6-227">Wartości</span><span class="sxs-lookup"><span data-stu-id="a97e6-227">Values</span></span> | <span data-ttu-id="a97e6-228">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="a97e6-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="a97e6-229">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a97e6-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="a97e6-230">Oddzielona przecinkami lista numerów procesorów lub zakresów numerów procesorów.</span><span class="sxs-lookup"><span data-stu-id="a97e6-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="a97e6-231">Przykład Uniksa: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="a97e6-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="a97e6-232">Przykład systemu Windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="a97e6-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="a97e6-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="a97e6-234">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a97e6-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="a97e6-235">Oddzielona przecinkami lista numerów procesorów lub zakresów numerów procesorów.</span><span class="sxs-lookup"><span data-stu-id="a97e6-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="a97e6-236">Przykład Uniksa: "1-10,12,50-52,70"</span><span class="sxs-lookup"><span data-stu-id="a97e6-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="a97e6-237">Przykład systemu Windows: "0:1-10,0:12,1:50-52,1:70"</span><span class="sxs-lookup"><span data-stu-id="a97e6-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="a97e6-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-238">.NET Core 3.0</span></span> |

<span data-ttu-id="a97e6-239">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a97e6-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="a97e6-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="a97e6-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="a97e6-241">Konfiguruje, czy moduł zbierający elementy bezużyteczne używa [grup procesora CPU,](/windows/win32/procthread/processor-groups) czy nie.</span><span class="sxs-lookup"><span data-stu-id="a97e6-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="a97e6-242">Gdy 64-bitowy komputer z systemem Windows ma wiele grup procesorów, oznacza to, że istnieje więcej niż 64 procesory, włączając ten element rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="a97e6-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="a97e6-243">Moduł zbierający elementy bezużyteczne używa wszystkich rdzeni do tworzenia i równoważenia sterty.</span><span class="sxs-lookup"><span data-stu-id="a97e6-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="a97e6-244">Dotyczy wyrzucania elementów bezużytecznych serwera tylko w 64-bitowych systemach operacyjnych systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a97e6-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="a97e6-245">Domyślnie:`0`Wyłączone ( ).</span><span class="sxs-lookup"><span data-stu-id="a97e6-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="a97e6-246">Aby uzyskać więcej informacji, zobacz [Ulepszanie konfiguracji procesora dla GC na komputerach z procesorami > 64](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="a97e6-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="a97e6-247">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a97e6-247">Setting name</span></span> | <span data-ttu-id="a97e6-248">Wartości</span><span class="sxs-lookup"><span data-stu-id="a97e6-248">Values</span></span> | <span data-ttu-id="a97e6-249">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="a97e6-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="a97e6-250">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a97e6-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="a97e6-251">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="a97e6-251">N/A</span></span> | <span data-ttu-id="a97e6-252">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="a97e6-252">N/A</span></span> | <span data-ttu-id="a97e6-253">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="a97e6-253">N/A</span></span> |
| <span data-ttu-id="a97e6-254">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a97e6-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="a97e6-255">`0`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="a97e6-255">`0` - disabled</span></span><br/><span data-ttu-id="a97e6-256">`1`- włączone</span><span class="sxs-lookup"><span data-stu-id="a97e6-256">`1` - enabled</span></span> | <span data-ttu-id="a97e6-257">.NET Rdzeń 1.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="a97e6-258">**app.config dla programu .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="a97e6-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="a97e6-259">Grupa GCCpu</span><span class="sxs-lookup"><span data-stu-id="a97e6-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="a97e6-260">`false`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="a97e6-260">`false` - disabled</span></span><br/><span data-ttu-id="a97e6-261">`true`- włączone</span><span class="sxs-lookup"><span data-stu-id="a97e6-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="a97e6-262">Aby skonfigurować środowisko uruchomieniowe języka wspólnego (CLR), aby również dystrybuować wątki z puli wątków we wszystkich grupach procesora CPU, włącz opcję [Thread_UseAllCpuGroups elementu.](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)</span><span class="sxs-lookup"><span data-stu-id="a97e6-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="a97e6-263">W przypadku aplikacji .NET Core można włączyć tę `COMPlus_Thread_UseAllCpuGroups` opcję, `1`ustawiając wartość zmiennej środowiskowej na .</span><span class="sxs-lookup"><span data-stu-id="a97e6-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="a97e6-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="a97e6-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="a97e6-265">Określa, czy *affinitize* wątków wyrzucania elementów bezużytecznych z procesorami.</span><span class="sxs-lookup"><span data-stu-id="a97e6-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="a97e6-266">Aby affinitize wątku GC oznacza, że można go uruchomić tylko na jego określonego procesora CPU.</span><span class="sxs-lookup"><span data-stu-id="a97e6-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="a97e6-267">Sterta jest tworzony dla każdego wątku GC.</span><span class="sxs-lookup"><span data-stu-id="a97e6-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="a97e6-268">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="a97e6-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="a97e6-269">Domyślnie: Affinitize wątków wyrzucania`false`elementów bezużytecznych z procesorami ( ).</span><span class="sxs-lookup"><span data-stu-id="a97e6-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="a97e6-270">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a97e6-270">Setting name</span></span> | <span data-ttu-id="a97e6-271">Wartości</span><span class="sxs-lookup"><span data-stu-id="a97e6-271">Values</span></span> | <span data-ttu-id="a97e6-272">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="a97e6-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="a97e6-273">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a97e6-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="a97e6-274">`false`- affinitize</span><span class="sxs-lookup"><span data-stu-id="a97e6-274">`false` - affinitize</span></span><br/><span data-ttu-id="a97e6-275">`true`- nie affinitize</span><span class="sxs-lookup"><span data-stu-id="a97e6-275">`true` - don't affinitize</span></span> | <span data-ttu-id="a97e6-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="a97e6-277">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a97e6-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="a97e6-278">`0`- affinitize</span><span class="sxs-lookup"><span data-stu-id="a97e6-278">`0` - affinitize</span></span><br/><span data-ttu-id="a97e6-279">`1`- nie affinitize</span><span class="sxs-lookup"><span data-stu-id="a97e6-279">`1` - don't affinitize</span></span> | <span data-ttu-id="a97e6-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="a97e6-281">**app.config dla programu .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="a97e6-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="a97e6-282">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="a97e6-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="a97e6-283">`false`- affinitize</span><span class="sxs-lookup"><span data-stu-id="a97e6-283">`false` - affinitize</span></span><br/><span data-ttu-id="a97e6-284">`true`- nie affinitize</span><span class="sxs-lookup"><span data-stu-id="a97e6-284">`true` - don't affinitize</span></span> | <span data-ttu-id="a97e6-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="a97e6-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="a97e6-286">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a97e6-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="a97e6-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="a97e6-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="a97e6-288">Określa maksymalny rozmiar zatwierdzenia w bajtach dla sterty GC i księgowego GC.</span><span class="sxs-lookup"><span data-stu-id="a97e6-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>
- <span data-ttu-id="a97e6-289">To ustawienie dotyczy tylko komputerów 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="a97e6-289">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="a97e6-290">Wartość domyślna, która ma zastosowanie tylko w niektórych przypadkach, jest mniejsza z 20 MB lub 75% limitu pamięci w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="a97e6-290">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="a97e6-291">Wartość domyślna ma zastosowanie, jeśli:</span><span class="sxs-lookup"><span data-stu-id="a97e6-291">The default value applies if:</span></span>

  - <span data-ttu-id="a97e6-292">Proces jest uruchomiony wewnątrz kontenera, który ma określony limit pamięci.</span><span class="sxs-lookup"><span data-stu-id="a97e6-292">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="a97e6-293">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) nie jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="a97e6-293">[System.GC.HeapHardLimitPercent](#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) is not set.</span></span>

| | <span data-ttu-id="a97e6-294">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a97e6-294">Setting name</span></span> | <span data-ttu-id="a97e6-295">Wartości</span><span class="sxs-lookup"><span data-stu-id="a97e6-295">Values</span></span> | <span data-ttu-id="a97e6-296">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="a97e6-296">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="a97e6-297">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a97e6-297">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="a97e6-298">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="a97e6-298">*decimal value*</span></span> | <span data-ttu-id="a97e6-299">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-299">.NET Core 3.0</span></span> |
| <span data-ttu-id="a97e6-300">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a97e6-300">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="a97e6-301">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="a97e6-301">*hexadecimal value*</span></span> | <span data-ttu-id="a97e6-302">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-302">.NET Core 3.0</span></span> |

<span data-ttu-id="a97e6-303">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a97e6-303">Example:</span></span>

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
> <span data-ttu-id="a97e6-304">Jeśli ustawiasz opcję w *pliku runtimeconfig.json,* określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="a97e6-304">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="a97e6-305">Jeśli ustawiasz tę opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="a97e6-305">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="a97e6-306">Na przykład, aby określić limit twardy sterty 200 mebibajtów (MiB), wartości będą 209715200 dla pliku JSON i 0xC8000000 lub C8000000 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="a97e6-306">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="a97e6-307">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="a97e6-307">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="a97e6-308">Określa dopuszczalne użycie sterty GC jako procent całkowitej pamięci fizycznej.</span><span class="sxs-lookup"><span data-stu-id="a97e6-308">Specifies the allowable GC heap usage as a percentage of the total physical memory.</span></span>
- <span data-ttu-id="a97e6-309">Jeśli [system.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) jest również ustawiony, to ustawienie jest ignorowane.</span><span class="sxs-lookup"><span data-stu-id="a97e6-309">If [System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is also set, this setting is ignored.</span></span>
- <span data-ttu-id="a97e6-310">To ustawienie dotyczy tylko komputerów 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="a97e6-310">This setting only applies to 64-bit computers.</span></span>
- <span data-ttu-id="a97e6-311">Jeśli proces jest uruchomiony wewnątrz kontenera, który ma określony limit pamięci, wartość procentowa jest obliczana jako procent tego limitu pamięci.</span><span class="sxs-lookup"><span data-stu-id="a97e6-311">If the process is running inside a container that has a specified memory limit, the percentage is calculated as a percentage of that memory limit.</span></span>
- <span data-ttu-id="a97e6-312">Wartość domyślna, która ma zastosowanie tylko w niektórych przypadkach, jest mniejsza z 20 MB lub 75% limitu pamięci w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="a97e6-312">The default value, which only applies in certain cases, is the lesser of 20 MB or 75% of the memory limit on the container.</span></span> <span data-ttu-id="a97e6-313">Wartość domyślna ma zastosowanie, jeśli:</span><span class="sxs-lookup"><span data-stu-id="a97e6-313">The default value applies if:</span></span>

  - <span data-ttu-id="a97e6-314">Proces jest uruchomiony wewnątrz kontenera, który ma określony limit pamięci.</span><span class="sxs-lookup"><span data-stu-id="a97e6-314">The process is running inside a container that has a specified memory limit.</span></span>
  - <span data-ttu-id="a97e6-315">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) nie jest ustawiony.</span><span class="sxs-lookup"><span data-stu-id="a97e6-315">[System.GC.HeapHardLimit](#systemgcheaphardlimitcomplus_gcheaphardlimit) is not set.</span></span>

| | <span data-ttu-id="a97e6-316">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a97e6-316">Setting name</span></span> | <span data-ttu-id="a97e6-317">Wartości</span><span class="sxs-lookup"><span data-stu-id="a97e6-317">Values</span></span> | <span data-ttu-id="a97e6-318">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="a97e6-318">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="a97e6-319">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a97e6-319">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="a97e6-320">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="a97e6-320">*decimal value*</span></span> | <span data-ttu-id="a97e6-321">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-321">.NET Core 3.0</span></span> |
| <span data-ttu-id="a97e6-322">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a97e6-322">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="a97e6-323">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="a97e6-323">*hexadecimal value*</span></span> | <span data-ttu-id="a97e6-324">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-324">.NET Core 3.0</span></span> |

<span data-ttu-id="a97e6-325">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a97e6-325">Example:</span></span>

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
> <span data-ttu-id="a97e6-326">Jeśli ustawiasz opcję w *pliku runtimeconfig.json,* określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="a97e6-326">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="a97e6-327">Jeśli ustawiasz tę opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="a97e6-327">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="a97e6-328">Na przykład, aby ograniczyć użycie sterty do 30%, wartości będą 30 dla pliku JSON i 0x1E lub 1E dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="a97e6-328">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="a97e6-329">System.GC.RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="a97e6-329">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="a97e6-330">Konfiguruje, czy segmenty, które powinny zostać usunięte, są umieszczane na liście wstrzymania do wykorzystania w przyszłości, czy są zwalniane z powrotem do systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a97e6-330">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="a97e6-331">Domyślnie: Zwolnij segmenty z`false`powrotem do systemu operacyjnego ( ).</span><span class="sxs-lookup"><span data-stu-id="a97e6-331">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="a97e6-332">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a97e6-332">Setting name</span></span> | <span data-ttu-id="a97e6-333">Wartości</span><span class="sxs-lookup"><span data-stu-id="a97e6-333">Values</span></span> | <span data-ttu-id="a97e6-334">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="a97e6-334">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="a97e6-335">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a97e6-335">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="a97e6-336">`false`- zwolnienie do systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="a97e6-336">`false` - release to OS</span></span><br/><span data-ttu-id="a97e6-337">`true`- umieścić w trybie gotowości</span><span class="sxs-lookup"><span data-stu-id="a97e6-337">`true` - put on standby</span></span> | <span data-ttu-id="a97e6-338">.NET Rdzeń 1.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-338">.NET Core 1.0</span></span> |
| <span data-ttu-id="a97e6-339">**Właściwość MSBuild**</span><span class="sxs-lookup"><span data-stu-id="a97e6-339">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="a97e6-340">`false`- zwolnienie do systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="a97e6-340">`false` - release to OS</span></span><br/><span data-ttu-id="a97e6-341">`true`- umieścić w trybie gotowości</span><span class="sxs-lookup"><span data-stu-id="a97e6-341">`true` - put on standby</span></span> | <span data-ttu-id="a97e6-342">.NET Rdzeń 1.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-342">.NET Core 1.0</span></span> |
| <span data-ttu-id="a97e6-343">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a97e6-343">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="a97e6-344">`0`- zwolnienie do systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="a97e6-344">`0` - release to OS</span></span><br/><span data-ttu-id="a97e6-345">`1`- umieścić w trybie gotowości</span><span class="sxs-lookup"><span data-stu-id="a97e6-345">`1` - put on standby</span></span> | <span data-ttu-id="a97e6-346">.NET Rdzeń 1.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-346">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="a97e6-347">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a97e6-347">Examples</span></span>

<span data-ttu-id="a97e6-348">*runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="a97e6-348">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="a97e6-349">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="a97e6-349">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="a97e6-350">Duże strony</span><span class="sxs-lookup"><span data-stu-id="a97e6-350">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="a97e6-351">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="a97e6-351">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="a97e6-352">Określa, czy duże strony mają być używane po ustawieniu limitu twardego sterty.</span><span class="sxs-lookup"><span data-stu-id="a97e6-352">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="a97e6-353">Domyślnie:`0`Wyłączone ( ).</span><span class="sxs-lookup"><span data-stu-id="a97e6-353">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="a97e6-354">Jest to ustawienie eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="a97e6-354">This is an experimental setting.</span></span>

| | <span data-ttu-id="a97e6-355">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a97e6-355">Setting name</span></span> | <span data-ttu-id="a97e6-356">Wartości</span><span class="sxs-lookup"><span data-stu-id="a97e6-356">Values</span></span> | <span data-ttu-id="a97e6-357">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="a97e6-357">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="a97e6-358">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a97e6-358">**runtimeconfig.json**</span></span> | <span data-ttu-id="a97e6-359">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="a97e6-359">N/A</span></span> | <span data-ttu-id="a97e6-360">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="a97e6-360">N/A</span></span> | <span data-ttu-id="a97e6-361">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="a97e6-361">N/A</span></span> |
| <span data-ttu-id="a97e6-362">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a97e6-362">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="a97e6-363">`0`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="a97e6-363">`0` - disabled</span></span><br/><span data-ttu-id="a97e6-364">`1`- włączone</span><span class="sxs-lookup"><span data-stu-id="a97e6-364">`1` - enabled</span></span> | <span data-ttu-id="a97e6-365">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-365">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="a97e6-366">Duże obiekty</span><span class="sxs-lookup"><span data-stu-id="a97e6-366">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="a97e6-367">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="a97e6-367">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="a97e6-368">Konfiguruje obsługę modułów zbierających elementy bezużyteczne na platformach 64-bitowych dla macierzy o całkowitym rozmiarze większym niż 2 gigabajty (GB).</span><span class="sxs-lookup"><span data-stu-id="a97e6-368">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="a97e6-369">Domyślnie: Włączone`1`( ).</span><span class="sxs-lookup"><span data-stu-id="a97e6-369">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="a97e6-370">Ta opcja może stać się przestarzała w przyszłej wersji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="a97e6-370">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="a97e6-371">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a97e6-371">Setting name</span></span> | <span data-ttu-id="a97e6-372">Wartości</span><span class="sxs-lookup"><span data-stu-id="a97e6-372">Values</span></span> | <span data-ttu-id="a97e6-373">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="a97e6-373">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="a97e6-374">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a97e6-374">**runtimeconfig.json**</span></span> | <span data-ttu-id="a97e6-375">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="a97e6-375">N/A</span></span> | <span data-ttu-id="a97e6-376">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="a97e6-376">N/A</span></span> | <span data-ttu-id="a97e6-377">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="a97e6-377">N/A</span></span> |
| <span data-ttu-id="a97e6-378">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a97e6-378">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="a97e6-379">`1`- włączone</span><span class="sxs-lookup"><span data-stu-id="a97e6-379">`1` - enabled</span></span><br/> <span data-ttu-id="a97e6-380">`0`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="a97e6-380">`0` - disabled</span></span> | <span data-ttu-id="a97e6-381">.NET Rdzeń 1.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-381">.NET Core 1.0</span></span> |
| <span data-ttu-id="a97e6-382">**app.config dla programu .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="a97e6-382">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="a97e6-383">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="a97e6-383">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="a97e6-384">`1`- włączone</span><span class="sxs-lookup"><span data-stu-id="a97e6-384">`1` - enabled</span></span><br/> <span data-ttu-id="a97e6-385">`0`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="a97e6-385">`0` - disabled</span></span> | <span data-ttu-id="a97e6-386">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="a97e6-386">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="a97e6-387">Próg sterty dużych obiektów</span><span class="sxs-lookup"><span data-stu-id="a97e6-387">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="a97e6-388">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="a97e6-388">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="a97e6-389">Określa rozmiar progu w bajtach, który powoduje, że obiekty, aby przejść na stercie dużych obiektów (LOH).</span><span class="sxs-lookup"><span data-stu-id="a97e6-389">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="a97e6-390">Domyślny próg wynosi 85 000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="a97e6-390">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="a97e6-391">Określona wartość musi być większa niż próg domyślny.</span><span class="sxs-lookup"><span data-stu-id="a97e6-391">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="a97e6-392">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a97e6-392">Setting name</span></span> | <span data-ttu-id="a97e6-393">Wartości</span><span class="sxs-lookup"><span data-stu-id="a97e6-393">Values</span></span> | <span data-ttu-id="a97e6-394">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="a97e6-394">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="a97e6-395">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a97e6-395">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="a97e6-396">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="a97e6-396">*decimal value*</span></span> | <span data-ttu-id="a97e6-397">.NET Rdzeń 1.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-397">.NET Core 1.0</span></span> |
| <span data-ttu-id="a97e6-398">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a97e6-398">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="a97e6-399">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="a97e6-399">*hexadecimal value*</span></span> | <span data-ttu-id="a97e6-400">.NET Rdzeń 1.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-400">.NET Core 1.0</span></span> |
| <span data-ttu-id="a97e6-401">**app.config dla programu .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="a97e6-401">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="a97e6-402">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="a97e6-402">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="a97e6-403">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="a97e6-403">*decimal value*</span></span> | <span data-ttu-id="a97e6-404"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="a97e6-404">.NET Framework 4.8</span></span> |

<span data-ttu-id="a97e6-405">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a97e6-405">Example:</span></span>

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
> <span data-ttu-id="a97e6-406">Jeśli ustawiasz opcję w *pliku runtimeconfig.json,* określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="a97e6-406">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="a97e6-407">Jeśli ustawiasz tę opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="a97e6-407">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="a97e6-408">Na przykład, aby ustawić rozmiar progu 120 000 bajtów, wartości będą 120000 dla pliku JSON i 0x1D4C0 lub 1D4C0 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="a97e6-408">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="a97e6-409">Samodzielny GC</span><span class="sxs-lookup"><span data-stu-id="a97e6-409">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="a97e6-410">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="a97e6-410">COMPlus_GCName</span></span>

- <span data-ttu-id="a97e6-411">Określa ścieżkę do biblioteki zawierającej moduł zbierający elementy bezużyteczne, które środowisko wykonawcze zamierza załadować.</span><span class="sxs-lookup"><span data-stu-id="a97e6-411">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="a97e6-412">Aby uzyskać więcej informacji, zobacz [Samodzielny projekt ładowarki GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="a97e6-412">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="a97e6-413">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a97e6-413">Setting name</span></span> | <span data-ttu-id="a97e6-414">Wartości</span><span class="sxs-lookup"><span data-stu-id="a97e6-414">Values</span></span> | <span data-ttu-id="a97e6-415">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="a97e6-415">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="a97e6-416">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a97e6-416">**runtimeconfig.json**</span></span> | <span data-ttu-id="a97e6-417">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="a97e6-417">N/A</span></span> | <span data-ttu-id="a97e6-418">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="a97e6-418">N/A</span></span> | <span data-ttu-id="a97e6-419">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="a97e6-419">N/A</span></span> |
| <span data-ttu-id="a97e6-420">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a97e6-420">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="a97e6-421">*string_path*</span><span class="sxs-lookup"><span data-stu-id="a97e6-421">*string_path*</span></span> | <span data-ttu-id="a97e6-422">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a97e6-422">.NET Core 2.0</span></span> |
