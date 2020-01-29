---
title: Ustawienia konfiguracji modułu wyrzucania elementów bezużytecznych
description: Informacje o ustawieniach czasu wykonywania w celu skonfigurowania sposobu, w jaki moduł zbierający elementy bezużyteczne zarządza pamięcią dla aplikacji platformy .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 044083d69601f5092724a46d358b2ee5673d428d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733518"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="2bdb7-103">Opcje konfiguracji czasu wykonywania dla wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="2bdb7-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="2bdb7-104">Ta strona zawiera informacje na temat ustawień modułu zbierającego elementy bezużyteczne (GC), które można zmienić w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="2bdb7-105">Jeśli próbujesz osiągnąć szczytową wydajność uruchomionej aplikacji, rozważ użycie tych ustawień.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="2bdb7-106">Jednak wartości domyślne zapewniają optymalną wydajność większości aplikacji w typowych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="2bdb7-107">Ustawienia są ułożone w grupach na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="2bdb7-108">Ustawienia w ramach każdej grupy są często używane w połączeniu ze sobą, aby osiągnąć konkretny wynik.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="2bdb7-109">Te ustawienia mogą być również dynamicznie zmieniane przez aplikację w trakcie działania, więc wszystkie ustawione ustawienia czasu wykonywania mogą zostać zastąpione.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="2bdb7-110">Niektóre ustawienia, takie jak [poziom opóźnienia](../../standard/garbage-collection/latency.md), są zazwyczaj ustawiane tylko za pomocą interfejsu API w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="2bdb7-111">Takie ustawienia zostały pominięte na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="2bdb7-112">W przypadku wartości liczbowych Użyj notacji dziesiętnej dla ustawień w pliku *runtimeconfig. JSON* i notacji szesnastkowej dla ustawień zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="2bdb7-113">W przypadku wartości szesnastkowych można je określić z prefiksem "0x" lub bez niego.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="2bdb7-114">Typy wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="2bdb7-114">Flavors of garbage collection</span></span>

<span data-ttu-id="2bdb7-115">Dwa główne typy wyrzucania elementów bezużytecznych to stacja robocza i serwer GC.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="2bdb7-116">Aby uzyskać więcej informacji o różnicach między tymi dwoma, zobacz podstawowe informacje dotyczące [wyrzucania elementów bezużytecznych](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="2bdb7-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="2bdb7-117">Podelementy wyrzucania elementów bezużytecznych są tła i niewspółbieżne.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="2bdb7-118">Użyj następujących ustawień, aby wybrać typy wyrzucania elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="2bdb7-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="2bdb7-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="2bdb7-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="2bdb7-120">Określa, czy aplikacja używa wyrzucania elementów bezużytecznych stacji roboczej lub odzyskiwania pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="2bdb7-121">Domyślnie: wyrzucanie elementów bezużytecznych stacji roboczej (`false`).</span><span class="sxs-lookup"><span data-stu-id="2bdb7-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="2bdb7-122">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2bdb7-122">Setting name</span></span> | <span data-ttu-id="2bdb7-123">Wartości</span><span class="sxs-lookup"><span data-stu-id="2bdb7-123">Values</span></span> | <span data-ttu-id="2bdb7-124">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2bdb7-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="2bdb7-125">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="2bdb7-126">`false` — stacja robocza</span><span class="sxs-lookup"><span data-stu-id="2bdb7-126">`false` - workstation</span></span><br/><span data-ttu-id="2bdb7-127">`true` — serwer</span><span class="sxs-lookup"><span data-stu-id="2bdb7-127">`true` - server</span></span> | <span data-ttu-id="2bdb7-128">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="2bdb7-129">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-129">**MSBuild property**</span></span> | `ServerGarbageCollection` | <span data-ttu-id="2bdb7-130">`false` — stacja robocza</span><span class="sxs-lookup"><span data-stu-id="2bdb7-130">`false` - workstation</span></span><br/><span data-ttu-id="2bdb7-131">`true` — serwer</span><span class="sxs-lookup"><span data-stu-id="2bdb7-131">`true` - server</span></span> | <span data-ttu-id="2bdb7-132">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="2bdb7-133">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-133">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="2bdb7-134">`0` — stacja robocza</span><span class="sxs-lookup"><span data-stu-id="2bdb7-134">`0` - workstation</span></span><br/><span data-ttu-id="2bdb7-135">`1` — serwer</span><span class="sxs-lookup"><span data-stu-id="2bdb7-135">`1` - server</span></span> | <span data-ttu-id="2bdb7-136">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-136">.NET Core 1.0</span></span> |
| <span data-ttu-id="2bdb7-137">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-137">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="2bdb7-138">GCServer</span><span class="sxs-lookup"><span data-stu-id="2bdb7-138">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="2bdb7-139">`false` — stacja robocza</span><span class="sxs-lookup"><span data-stu-id="2bdb7-139">`false` - workstation</span></span><br/><span data-ttu-id="2bdb7-140">`true` — serwer</span><span class="sxs-lookup"><span data-stu-id="2bdb7-140">`true` - server</span></span> |  |

### <a name="examples"></a><span data-ttu-id="2bdb7-141">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2bdb7-141">Examples</span></span>

<span data-ttu-id="2bdb7-142">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="2bdb7-142">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

<span data-ttu-id="2bdb7-143">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="2bdb7-143">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>

</Project>
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="2bdb7-144">System. GC. współbieżne/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="2bdb7-144">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="2bdb7-145">Określa, czy jest włączone wyrzucanie elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-145">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="2bdb7-146">Wartość domyślna: włączone (`true`).</span><span class="sxs-lookup"><span data-stu-id="2bdb7-146">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="2bdb7-147">Aby uzyskać więcej informacji, zobacz [zbieranie elementów bezużytecznych w tle](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) i [odzyskiwanie pamięci serwera w tle](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="2bdb7-147">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="2bdb7-148">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2bdb7-148">Setting name</span></span> | <span data-ttu-id="2bdb7-149">Wartości</span><span class="sxs-lookup"><span data-stu-id="2bdb7-149">Values</span></span> | <span data-ttu-id="2bdb7-150">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2bdb7-150">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="2bdb7-151">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-151">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="2bdb7-152">`true` — w tle GC</span><span class="sxs-lookup"><span data-stu-id="2bdb7-152">`true` - background GC</span></span><br/><span data-ttu-id="2bdb7-153">`false` — niewspółbieżne GC</span><span class="sxs-lookup"><span data-stu-id="2bdb7-153">`false` - non-concurrent GC</span></span> | <span data-ttu-id="2bdb7-154">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-154">.NET Core 1.0</span></span> |
| <span data-ttu-id="2bdb7-155">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-155">**MSBuild property**</span></span> | `ConcurrentGarbageCollection` | <span data-ttu-id="2bdb7-156">`true` — w tle GC</span><span class="sxs-lookup"><span data-stu-id="2bdb7-156">`true` - background GC</span></span><br/><span data-ttu-id="2bdb7-157">`false` — niewspółbieżne GC</span><span class="sxs-lookup"><span data-stu-id="2bdb7-157">`false` - non-concurrent GC</span></span> | <span data-ttu-id="2bdb7-158">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-158">.NET Core 1.0</span></span> |
| <span data-ttu-id="2bdb7-159">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-159">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="2bdb7-160">`true` — w tle GC</span><span class="sxs-lookup"><span data-stu-id="2bdb7-160">`true` - background GC</span></span><br/><span data-ttu-id="2bdb7-161">`false` — niewspółbieżne GC</span><span class="sxs-lookup"><span data-stu-id="2bdb7-161">`false` - non-concurrent GC</span></span> | <span data-ttu-id="2bdb7-162">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-162">.NET Core 1.0</span></span> |
| <span data-ttu-id="2bdb7-163">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-163">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="2bdb7-164">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="2bdb7-164">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="2bdb7-165">`true` — w tle GC</span><span class="sxs-lookup"><span data-stu-id="2bdb7-165">`true` - background GC</span></span><br/><span data-ttu-id="2bdb7-166">`false` — niewspółbieżne GC</span><span class="sxs-lookup"><span data-stu-id="2bdb7-166">`false` - non-concurrent GC</span></span> |  |

### <a name="examples"></a><span data-ttu-id="2bdb7-167">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2bdb7-167">Examples</span></span>

<span data-ttu-id="2bdb7-168">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="2bdb7-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

<span data-ttu-id="2bdb7-169">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="2bdb7-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="manage-resource-usage"></a><span data-ttu-id="2bdb7-170">Zarządzanie użyciem zasobów</span><span class="sxs-lookup"><span data-stu-id="2bdb7-170">Manage resource usage</span></span>

<span data-ttu-id="2bdb7-171">Ustawienia opisane w tej sekcji służą do zarządzania użyciem pamięci i procesora modułu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-171">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="2bdb7-172">Aby uzyskać więcej informacji na temat niektórych z tych ustawień, zapoznaj się z wpisem na blogu centrum [robocze i serwer GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .</span><span class="sxs-lookup"><span data-stu-id="2bdb7-172">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="2bdb7-173">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="2bdb7-173">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="2bdb7-174">Ogranicza liczbę stert utworzonych przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-174">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="2bdb7-175">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-175">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="2bdb7-176">Jeśli koligacja procesora GC jest włączona, co jest ustawieniem domyślnym, licznik sterty skoligacony `n` GC sterty/wątki z pierwszymi procesorami `n`.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-176">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="2bdb7-177">(Użyj koligacji maska lub ustawienia zakresów koligacji, aby określić, które procesory mają być koligacji).</span><span class="sxs-lookup"><span data-stu-id="2bdb7-177">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="2bdb7-178">Jeśli koligacja procesora GC jest wyłączona, to ustawienie ogranicza liczbę stert GC.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-178">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="2bdb7-179">Aby uzyskać więcej informacji, zobacz [uwagi GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="2bdb7-179">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="2bdb7-180">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2bdb7-180">Setting name</span></span> | <span data-ttu-id="2bdb7-181">Wartości</span><span class="sxs-lookup"><span data-stu-id="2bdb7-181">Values</span></span> | <span data-ttu-id="2bdb7-182">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2bdb7-182">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="2bdb7-183">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-183">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="2bdb7-184">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="2bdb7-184">*decimal value*</span></span> | <span data-ttu-id="2bdb7-185">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-185">.NET Core 3.0</span></span> |
| <span data-ttu-id="2bdb7-186">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-186">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="2bdb7-187">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="2bdb7-187">*hexadecimal value*</span></span> | <span data-ttu-id="2bdb7-188">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-188">.NET Core 3.0</span></span> |
| <span data-ttu-id="2bdb7-189">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-189">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="2bdb7-190">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="2bdb7-190">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="2bdb7-191">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="2bdb7-191">*decimal value*</span></span> | <span data-ttu-id="2bdb7-192">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="2bdb7-192">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="2bdb7-193">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2bdb7-193">Example:</span></span>

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
> <span data-ttu-id="2bdb7-194">Jeśli ustawiasz opcję w *runtimeconfig. JSON*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-194">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="2bdb7-195">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-195">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="2bdb7-196">Na przykład aby ograniczyć liczbę stert do 16, wartości dla pliku JSON i 0x10 lub 10 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-196">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="2bdb7-197">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="2bdb7-197">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="2bdb7-198">Określa dokładne procesory, które powinny być używane przez wątki modułu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-198">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="2bdb7-199">Jeśli Koligacja procesorów jest wyłączona przez ustawienie `System.GC.NoAffinitize` do `true`, to ustawienie zostanie zignorowane.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-199">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="2bdb7-200">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-200">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="2bdb7-201">Wartość jest maską bitową, która definiuje procesory, które są dostępne dla procesu.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-201">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="2bdb7-202">Na przykład wartość dziesiętna 1023 (lub wartość szesnastkowa 0x3FF lub 3FF, jeśli używana jest zmienna środowiskowa) to 0011 1111 1111 w notacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-202">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="2bdb7-203">Oznacza to, że pierwsze 10 procesorów ma być używany.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-203">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="2bdb7-204">Aby określić następne 10 procesorów, czyli procesorów 10-19, określ wartość dziesiętną 1047552 (lub wartość szesnastkową 0xFFC00 lub FFC00), która jest równoważna z wartością binarną 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-204">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="2bdb7-205">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2bdb7-205">Setting name</span></span> | <span data-ttu-id="2bdb7-206">Wartości</span><span class="sxs-lookup"><span data-stu-id="2bdb7-206">Values</span></span> | <span data-ttu-id="2bdb7-207">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2bdb7-207">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="2bdb7-208">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-208">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="2bdb7-209">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="2bdb7-209">*decimal value*</span></span> | <span data-ttu-id="2bdb7-210">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-210">.NET Core 3.0</span></span> |
| <span data-ttu-id="2bdb7-211">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-211">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="2bdb7-212">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="2bdb7-212">*hexadecimal value*</span></span> | <span data-ttu-id="2bdb7-213">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-213">.NET Core 3.0</span></span> |
| <span data-ttu-id="2bdb7-214">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-214">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="2bdb7-215">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="2bdb7-215">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="2bdb7-216">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="2bdb7-216">*decimal value*</span></span> | <span data-ttu-id="2bdb7-217">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="2bdb7-217">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="2bdb7-218">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2bdb7-218">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="2bdb7-219">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="2bdb7-219">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="2bdb7-220">Określa listę procesorów, które mają być używane na potrzeby wątków modułu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-220">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="2bdb7-221">To ustawienie jest podobne do `System.GC.HeapAffinitizeMask`, z tą różnicą, że pozwala określić więcej niż 64 procesorów.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-221">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="2bdb7-222">W przypadku systemów operacyjnych Windows należy prefiksować numer procesora lub zakres z odpowiednią [grupą procesorów CPU](/windows/win32/procthread/processor-groups), na przykład "0:1-10, 0:12, 1:50-52, 1:70".</span><span class="sxs-lookup"><span data-stu-id="2bdb7-222">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="2bdb7-223">Jeśli Koligacja procesorów jest wyłączona przez ustawienie `System.GC.NoAffinitize` do `true`, to ustawienie zostanie zignorowane.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-223">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="2bdb7-224">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-224">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="2bdb7-225">Aby uzyskać więcej informacji, zobacz temat [Zapewnianie lepszej konfiguracji procesora dla GC na maszynach z > 64 procesorów CPU](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-225">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="2bdb7-226">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2bdb7-226">Setting name</span></span> | <span data-ttu-id="2bdb7-227">Wartości</span><span class="sxs-lookup"><span data-stu-id="2bdb7-227">Values</span></span> | <span data-ttu-id="2bdb7-228">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2bdb7-228">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="2bdb7-229">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-229">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="2bdb7-230">Rozdzielana przecinkami lista numerów procesorów lub zakresów numerów procesorów.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-230">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="2bdb7-231">Przykład UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="2bdb7-231">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="2bdb7-232">Przykład systemu Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="2bdb7-232">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="2bdb7-233">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-233">.NET Core 3.0</span></span> |
| <span data-ttu-id="2bdb7-234">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-234">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="2bdb7-235">Rozdzielana przecinkami lista numerów procesorów lub zakresów numerów procesorów.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-235">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="2bdb7-236">Przykład UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="2bdb7-236">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="2bdb7-237">Przykład systemu Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="2bdb7-237">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="2bdb7-238">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-238">.NET Core 3.0</span></span> |

<span data-ttu-id="2bdb7-239">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2bdb7-239">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="2bdb7-240">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="2bdb7-240">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="2bdb7-241">Określa, czy moduł wyrzucania elementów bezużytecznych używa [grup CPU](/windows/win32/procthread/processor-groups) , czy nie.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-241">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="2bdb7-242">Gdy 64-bitowy komputer z systemem Windows ma wiele grup CPU, oznacza to, że istnieje więcej niż 64 procesorów, włączając ten element rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach CPU.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-242">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="2bdb7-243">Moduł wyrzucania elementów bezużytecznych używa wszystkich rdzeni do tworzenia i równoważenia sterty.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-243">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="2bdb7-244">Stosuje się do wyrzucania elementów bezużytecznych serwera w 64-bitowych systemach operacyjnych Windows.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-244">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="2bdb7-245">Domyślnie: wyłączone (`0`).</span><span class="sxs-lookup"><span data-stu-id="2bdb7-245">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="2bdb7-246">Aby uzyskać więcej informacji, zobacz temat [Zapewnianie lepszej konfiguracji procesora dla GC na maszynach z > 64 procesorów CPU](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-246">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="2bdb7-247">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2bdb7-247">Setting name</span></span> | <span data-ttu-id="2bdb7-248">Wartości</span><span class="sxs-lookup"><span data-stu-id="2bdb7-248">Values</span></span> | <span data-ttu-id="2bdb7-249">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2bdb7-249">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="2bdb7-250">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-250">**runtimeconfig.json**</span></span> | <span data-ttu-id="2bdb7-251">N/D</span><span class="sxs-lookup"><span data-stu-id="2bdb7-251">N/A</span></span> | <span data-ttu-id="2bdb7-252">N/D</span><span class="sxs-lookup"><span data-stu-id="2bdb7-252">N/A</span></span> | <span data-ttu-id="2bdb7-253">N/D</span><span class="sxs-lookup"><span data-stu-id="2bdb7-253">N/A</span></span> |
| <span data-ttu-id="2bdb7-254">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-254">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="2bdb7-255">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="2bdb7-255">`0` - disabled</span></span><br/><span data-ttu-id="2bdb7-256">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="2bdb7-256">`1` - enabled</span></span> | <span data-ttu-id="2bdb7-257">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-257">.NET Core 1.0</span></span> |
| <span data-ttu-id="2bdb7-258">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-258">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="2bdb7-259">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="2bdb7-259">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="2bdb7-260">`false` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="2bdb7-260">`false` - disabled</span></span><br/><span data-ttu-id="2bdb7-261">`true` — włączono</span><span class="sxs-lookup"><span data-stu-id="2bdb7-261">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="2bdb7-262">Aby skonfigurować środowisko uruchomieniowe języka wspólnego (CLR) do dystrybucji wątków z puli wątków we wszystkich grupach procesora, Włącz opcję [Thread_UseAllCpuGroups elementu](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="2bdb7-262">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="2bdb7-263">W przypadku aplikacji platformy .NET Core można włączyć tę opcję, ustawiając wartość zmiennej środowiskowej `COMPlus_Thread_UseAllCpuGroups` na `1`.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-263">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="2bdb7-264">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="2bdb7-264">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="2bdb7-265">Określa, czy *koligacji* wątki odzyskiwania pamięci z procesorami.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-265">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="2bdb7-266">Aby koligacji wątek GC, oznacza to, że można go uruchomić tylko w określonym procesorze CPU.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-266">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="2bdb7-267">Sterta jest tworzona dla każdego wątku GC.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-267">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="2bdb7-268">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-268">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="2bdb7-269">Domyślnie: koligacji wątki odzyskiwania pamięci z procesorami (`false`).</span><span class="sxs-lookup"><span data-stu-id="2bdb7-269">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="2bdb7-270">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2bdb7-270">Setting name</span></span> | <span data-ttu-id="2bdb7-271">Wartości</span><span class="sxs-lookup"><span data-stu-id="2bdb7-271">Values</span></span> | <span data-ttu-id="2bdb7-272">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2bdb7-272">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="2bdb7-273">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-273">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="2bdb7-274">`false` — koligacji</span><span class="sxs-lookup"><span data-stu-id="2bdb7-274">`false` - affinitize</span></span><br/><span data-ttu-id="2bdb7-275">`true` — nie koligacji</span><span class="sxs-lookup"><span data-stu-id="2bdb7-275">`true` - don't affinitize</span></span> | <span data-ttu-id="2bdb7-276">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-276">.NET Core 3.0</span></span> |
| <span data-ttu-id="2bdb7-277">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-277">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="2bdb7-278">`0` — koligacji</span><span class="sxs-lookup"><span data-stu-id="2bdb7-278">`0` - affinitize</span></span><br/><span data-ttu-id="2bdb7-279">`1` — nie koligacji</span><span class="sxs-lookup"><span data-stu-id="2bdb7-279">`1` - don't affinitize</span></span> | <span data-ttu-id="2bdb7-280">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-280">.NET Core 3.0</span></span> |
| <span data-ttu-id="2bdb7-281">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-281">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="2bdb7-282">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="2bdb7-282">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="2bdb7-283">`false` — koligacji</span><span class="sxs-lookup"><span data-stu-id="2bdb7-283">`false` - affinitize</span></span><br/><span data-ttu-id="2bdb7-284">`true` — nie koligacji</span><span class="sxs-lookup"><span data-stu-id="2bdb7-284">`true` - don't affinitize</span></span> | <span data-ttu-id="2bdb7-285">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="2bdb7-285">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="2bdb7-286">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2bdb7-286">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="2bdb7-287">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="2bdb7-287">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="2bdb7-288">Określa maksymalny rozmiar zatwierdzeń w bajtach dla sterty GC i księgowości GC.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-288">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="2bdb7-289">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2bdb7-289">Setting name</span></span> | <span data-ttu-id="2bdb7-290">Wartości</span><span class="sxs-lookup"><span data-stu-id="2bdb7-290">Values</span></span> | <span data-ttu-id="2bdb7-291">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2bdb7-291">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="2bdb7-292">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-292">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="2bdb7-293">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="2bdb7-293">*decimal value*</span></span> | <span data-ttu-id="2bdb7-294">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-294">.NET Core 3.0</span></span> |
| <span data-ttu-id="2bdb7-295">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-295">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="2bdb7-296">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="2bdb7-296">*hexadecimal value*</span></span> | <span data-ttu-id="2bdb7-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-297">.NET Core 3.0</span></span> |

<span data-ttu-id="2bdb7-298">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2bdb7-298">Example:</span></span>

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
> <span data-ttu-id="2bdb7-299">Jeśli ustawiasz opcję w *runtimeconfig. JSON*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-299">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="2bdb7-300">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-300">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="2bdb7-301">Na przykład aby określić stały limit sterty wynoszący 200 mebibytes (MiB), wartości byłyby 209715200 dla pliku JSON i 0xC800000 lub C800000 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-301">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="2bdb7-302">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="2bdb7-302">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="2bdb7-303">Określa użycie sterty GC jako procent całkowitej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-303">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="2bdb7-304">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2bdb7-304">Setting name</span></span> | <span data-ttu-id="2bdb7-305">Wartości</span><span class="sxs-lookup"><span data-stu-id="2bdb7-305">Values</span></span> | <span data-ttu-id="2bdb7-306">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2bdb7-306">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="2bdb7-307">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-307">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="2bdb7-308">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="2bdb7-308">*decimal value*</span></span> | <span data-ttu-id="2bdb7-309">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-309">.NET Core 3.0</span></span> |
| <span data-ttu-id="2bdb7-310">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-310">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="2bdb7-311">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="2bdb7-311">*hexadecimal value*</span></span> | <span data-ttu-id="2bdb7-312">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-312">.NET Core 3.0</span></span> |

<span data-ttu-id="2bdb7-313">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2bdb7-313">Example:</span></span>

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
> <span data-ttu-id="2bdb7-314">Jeśli ustawiasz opcję w *runtimeconfig. JSON*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-314">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="2bdb7-315">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-315">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="2bdb7-316">Na przykład aby ograniczyć użycie sterty do 30%, wartości byłyby 30 dla pliku JSON i 0x1E lub 1E dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-316">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="2bdb7-317">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="2bdb7-317">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="2bdb7-318">Określa, czy segmenty, które mają zostać usunięte, są umieszczane na liście gotowości do użycia w przyszłości lub są wyłączane z powrotem do systemu operacyjnego (OS).</span><span class="sxs-lookup"><span data-stu-id="2bdb7-318">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="2bdb7-319">Domyślnie: segmenty wydań z powrotem do systemu operacyjnego (`false`).</span><span class="sxs-lookup"><span data-stu-id="2bdb7-319">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="2bdb7-320">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2bdb7-320">Setting name</span></span> | <span data-ttu-id="2bdb7-321">Wartości</span><span class="sxs-lookup"><span data-stu-id="2bdb7-321">Values</span></span> | <span data-ttu-id="2bdb7-322">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2bdb7-322">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="2bdb7-323">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-323">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="2bdb7-324">`false` — wydanie do systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="2bdb7-324">`false` - release to OS</span></span><br/><span data-ttu-id="2bdb7-325">`true` — Umieść w stanie wstrzymania</span><span class="sxs-lookup"><span data-stu-id="2bdb7-325">`true` - put on standby</span></span> | <span data-ttu-id="2bdb7-326">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-326">.NET Core 1.0</span></span> |
| <span data-ttu-id="2bdb7-327">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-327">**MSBuild property**</span></span> | `RetainVMGarbageCollection` | <span data-ttu-id="2bdb7-328">`false` — wydanie do systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="2bdb7-328">`false` - release to OS</span></span><br/><span data-ttu-id="2bdb7-329">`true` — Umieść w stanie wstrzymania</span><span class="sxs-lookup"><span data-stu-id="2bdb7-329">`true` - put on standby</span></span> | <span data-ttu-id="2bdb7-330">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-330">.NET Core 1.0</span></span> |
| <span data-ttu-id="2bdb7-331">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-331">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="2bdb7-332">`0` — wydanie do systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="2bdb7-332">`0` - release to OS</span></span><br/><span data-ttu-id="2bdb7-333">`1` — Umieść w stanie wstrzymania</span><span class="sxs-lookup"><span data-stu-id="2bdb7-333">`1` - put on standby</span></span> | <span data-ttu-id="2bdb7-334">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-334">.NET Core 1.0</span></span> |

### <a name="examples"></a><span data-ttu-id="2bdb7-335">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2bdb7-335">Examples</span></span>

<span data-ttu-id="2bdb7-336">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="2bdb7-336">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

<span data-ttu-id="2bdb7-337">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="2bdb7-337">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>

</Project>
```

## <a name="large-pages"></a><span data-ttu-id="2bdb7-338">Duże strony</span><span class="sxs-lookup"><span data-stu-id="2bdb7-338">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="2bdb7-339">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="2bdb7-339">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="2bdb7-340">Określa, czy mają być używane duże strony, gdy jest ustawiony limit sztywny sterty.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-340">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="2bdb7-341">Domyślnie: wyłączone (`0`).</span><span class="sxs-lookup"><span data-stu-id="2bdb7-341">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="2bdb7-342">Jest to ustawienie eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-342">This is an experimental setting.</span></span>

| | <span data-ttu-id="2bdb7-343">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2bdb7-343">Setting name</span></span> | <span data-ttu-id="2bdb7-344">Wartości</span><span class="sxs-lookup"><span data-stu-id="2bdb7-344">Values</span></span> | <span data-ttu-id="2bdb7-345">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2bdb7-345">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="2bdb7-346">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-346">**runtimeconfig.json**</span></span> | <span data-ttu-id="2bdb7-347">N/D</span><span class="sxs-lookup"><span data-stu-id="2bdb7-347">N/A</span></span> | <span data-ttu-id="2bdb7-348">N/D</span><span class="sxs-lookup"><span data-stu-id="2bdb7-348">N/A</span></span> | <span data-ttu-id="2bdb7-349">N/D</span><span class="sxs-lookup"><span data-stu-id="2bdb7-349">N/A</span></span> |
| <span data-ttu-id="2bdb7-350">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-350">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="2bdb7-351">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="2bdb7-351">`0` - disabled</span></span><br/><span data-ttu-id="2bdb7-352">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="2bdb7-352">`1` - enabled</span></span> | <span data-ttu-id="2bdb7-353">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-353">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="2bdb7-354">Duże obiekty</span><span class="sxs-lookup"><span data-stu-id="2bdb7-354">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="2bdb7-355">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="2bdb7-355">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="2bdb7-356">Konfiguruje obsługę modułu wyrzucania elementów bezużytecznych na platformach 64-bitowych dla tablic, które są większe niż 2 gigabajty (GB) w łącznym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-356">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="2bdb7-357">Wartość domyślna: włączone (`1`).</span><span class="sxs-lookup"><span data-stu-id="2bdb7-357">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="2bdb7-358">Ta opcja może stać się przestarzała w przyszłej wersji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-358">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="2bdb7-359">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2bdb7-359">Setting name</span></span> | <span data-ttu-id="2bdb7-360">Wartości</span><span class="sxs-lookup"><span data-stu-id="2bdb7-360">Values</span></span> | <span data-ttu-id="2bdb7-361">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2bdb7-361">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="2bdb7-362">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-362">**runtimeconfig.json**</span></span> | <span data-ttu-id="2bdb7-363">N/D</span><span class="sxs-lookup"><span data-stu-id="2bdb7-363">N/A</span></span> | <span data-ttu-id="2bdb7-364">N/D</span><span class="sxs-lookup"><span data-stu-id="2bdb7-364">N/A</span></span> | <span data-ttu-id="2bdb7-365">N/D</span><span class="sxs-lookup"><span data-stu-id="2bdb7-365">N/A</span></span> |
| <span data-ttu-id="2bdb7-366">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-366">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="2bdb7-367">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="2bdb7-367">`1` - enabled</span></span><br/> <span data-ttu-id="2bdb7-368">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="2bdb7-368">`0` - disabled</span></span> | <span data-ttu-id="2bdb7-369">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-369">.NET Core 1.0</span></span> |
| <span data-ttu-id="2bdb7-370">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-370">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="2bdb7-371">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="2bdb7-371">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="2bdb7-372">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="2bdb7-372">`1` - enabled</span></span><br/> <span data-ttu-id="2bdb7-373">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="2bdb7-373">`0` - disabled</span></span> | <span data-ttu-id="2bdb7-374">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="2bdb7-374">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="2bdb7-375">Próg sterty dla dużego obiektu</span><span class="sxs-lookup"><span data-stu-id="2bdb7-375">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="2bdb7-376">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="2bdb7-376">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="2bdb7-377">Określa rozmiar progu (w bajtach), który powoduje, że obiekty są na stosie dużego obiektu (LOH).</span><span class="sxs-lookup"><span data-stu-id="2bdb7-377">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="2bdb7-378">Domyślny próg to 85 000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-378">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="2bdb7-379">Określona wartość musi być większa niż wartość progu domyślnego.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-379">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="2bdb7-380">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2bdb7-380">Setting name</span></span> | <span data-ttu-id="2bdb7-381">Wartości</span><span class="sxs-lookup"><span data-stu-id="2bdb7-381">Values</span></span> | <span data-ttu-id="2bdb7-382">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2bdb7-382">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="2bdb7-383">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-383">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="2bdb7-384">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="2bdb7-384">*decimal value*</span></span> | <span data-ttu-id="2bdb7-385">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-385">.NET Core 1.0</span></span> |
| <span data-ttu-id="2bdb7-386">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-386">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="2bdb7-387">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="2bdb7-387">*hexadecimal value*</span></span> | <span data-ttu-id="2bdb7-388">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-388">.NET Core 1.0</span></span> |
| <span data-ttu-id="2bdb7-389">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-389">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="2bdb7-390">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="2bdb7-390">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="2bdb7-391">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="2bdb7-391">*decimal value*</span></span> | <span data-ttu-id="2bdb7-392">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="2bdb7-392">.NET Framework 4.8</span></span> |

<span data-ttu-id="2bdb7-393">Przykład:</span><span class="sxs-lookup"><span data-stu-id="2bdb7-393">Example:</span></span>

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
> <span data-ttu-id="2bdb7-394">Jeśli ustawiasz opcję w *runtimeconfig. JSON*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-394">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="2bdb7-395">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-395">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="2bdb7-396">Na przykład, aby ustawić rozmiar progu 120 000 bajtów, wartości byłyby 120000 dla pliku JSON oraz 0x1D4C0 lub 1D4C0 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-396">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="2bdb7-397">Autonomiczna GC</span><span class="sxs-lookup"><span data-stu-id="2bdb7-397">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="2bdb7-398">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="2bdb7-398">COMPlus_GCName</span></span>

- <span data-ttu-id="2bdb7-399">Określa ścieżkę do biblioteki zawierającej Moduł wyrzucania elementów bezużytecznych, który środowisko uruchomieniowe zamierza załadować.</span><span class="sxs-lookup"><span data-stu-id="2bdb7-399">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="2bdb7-400">Aby uzyskać więcej informacji, zobacz [prekonstrukcja modułu ładującego GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="2bdb7-400">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="2bdb7-401">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="2bdb7-401">Setting name</span></span> | <span data-ttu-id="2bdb7-402">Wartości</span><span class="sxs-lookup"><span data-stu-id="2bdb7-402">Values</span></span> | <span data-ttu-id="2bdb7-403">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="2bdb7-403">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="2bdb7-404">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-404">**runtimeconfig.json**</span></span> | <span data-ttu-id="2bdb7-405">N/D</span><span class="sxs-lookup"><span data-stu-id="2bdb7-405">N/A</span></span> | <span data-ttu-id="2bdb7-406">N/D</span><span class="sxs-lookup"><span data-stu-id="2bdb7-406">N/A</span></span> | <span data-ttu-id="2bdb7-407">N/D</span><span class="sxs-lookup"><span data-stu-id="2bdb7-407">N/A</span></span> |
| <span data-ttu-id="2bdb7-408">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="2bdb7-408">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="2bdb7-409">*string_path*</span><span class="sxs-lookup"><span data-stu-id="2bdb7-409">*string_path*</span></span> | <span data-ttu-id="2bdb7-410">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="2bdb7-410">.NET Core 2.0</span></span> |
