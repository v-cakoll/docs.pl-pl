---
title: Ustawienia konfiguracji modułu wyrzucania elementów bezużytecznych
description: Informacje o ustawieniach czasu wykonywania w celu skonfigurowania sposobu, w jaki moduł zbierający elementy bezużyteczne zarządza pamięcią dla aplikacji platformy .NET Core.
ms.date: 01/09/2020
ms.topic: reference
ms.openlocfilehash: 24e5c47de781e7eed5f76d2c551cac2dce1e8f05
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900093"
---
# <a name="run-time-configuration-options-for-garbage-collection"></a><span data-ttu-id="da0a1-103">Opcje konfiguracji czasu wykonywania dla wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="da0a1-103">Run-time configuration options for garbage collection</span></span>

<span data-ttu-id="da0a1-104">Ta strona zawiera informacje na temat ustawień modułu zbierającego elementy bezużyteczne (GC), które można zmienić w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="da0a1-104">This page contains information about garbage collector (GC) settings that can be changed at run time.</span></span> <span data-ttu-id="da0a1-105">Jeśli próbujesz osiągnąć szczytową wydajność uruchomionej aplikacji, rozważ użycie tych ustawień.</span><span class="sxs-lookup"><span data-stu-id="da0a1-105">If you're trying to achieve peak performance of a running app, consider using these settings.</span></span> <span data-ttu-id="da0a1-106">Jednak wartości domyślne zapewniają optymalną wydajność większości aplikacji w typowych sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="da0a1-106">However, the defaults provide optimum performance for most applications in typical situations.</span></span>

<span data-ttu-id="da0a1-107">Ustawienia są ułożone w grupach na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="da0a1-107">Settings are arranged into groups on this page.</span></span> <span data-ttu-id="da0a1-108">Ustawienia w ramach każdej grupy są często używane w połączeniu ze sobą, aby osiągnąć konkretny wynik.</span><span class="sxs-lookup"><span data-stu-id="da0a1-108">The settings within each group are commonly used in conjunction with each other to achieve a specific result.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="da0a1-109">Te ustawienia mogą być również dynamicznie zmieniane przez aplikację w trakcie działania, więc wszystkie ustawione ustawienia czasu wykonywania mogą zostać zastąpione.</span><span class="sxs-lookup"><span data-stu-id="da0a1-109">These settings can also be changed dynamically by the app as it's running, so any run-time settings you set may be overridden.</span></span>
> - <span data-ttu-id="da0a1-110">Niektóre ustawienia, takie jak [poziom opóźnienia](../../standard/garbage-collection/latency.md), są zazwyczaj ustawiane tylko za pomocą interfejsu API w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="da0a1-110">Some settings, such as [latency level](../../standard/garbage-collection/latency.md), are typically set only through the API at design time.</span></span> <span data-ttu-id="da0a1-111">Takie ustawienia zostały pominięte na tej stronie.</span><span class="sxs-lookup"><span data-stu-id="da0a1-111">Such settings are omitted from this page.</span></span>
> - <span data-ttu-id="da0a1-112">W przypadku wartości liczbowych Użyj notacji dziesiętnej dla ustawień w pliku *runtimeconfig. JSON* i notacji szesnastkowej dla ustawień zmiennych środowiskowych.</span><span class="sxs-lookup"><span data-stu-id="da0a1-112">For number values, use decimal notation for settings in the *runtimeconfig.json* file and hexadecimal notation for environment variable settings.</span></span> <span data-ttu-id="da0a1-113">W przypadku wartości szesnastkowych można je określić z prefiksem "0x" lub bez niego.</span><span class="sxs-lookup"><span data-stu-id="da0a1-113">For hexadecimal values, you can specify them with or without the "0x" prefix.</span></span>

## <a name="flavors-of-garbage-collection"></a><span data-ttu-id="da0a1-114">Typy wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="da0a1-114">Flavors of garbage collection</span></span>

<span data-ttu-id="da0a1-115">Dwa główne typy wyrzucania elementów bezużytecznych to stacja robocza i serwer GC.</span><span class="sxs-lookup"><span data-stu-id="da0a1-115">The two main flavors of garbage collection are workstation GC and server GC.</span></span> <span data-ttu-id="da0a1-116">Aby uzyskać więcej informacji o różnicach między tymi dwoma, zobacz podstawowe informacje dotyczące [wyrzucania elementów bezużytecznych](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="da0a1-116">For more information about differences between the two, see [Fundamentals of garbage collection](../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection).</span></span>

<span data-ttu-id="da0a1-117">Podelementy wyrzucania elementów bezużytecznych są tła i niewspółbieżne.</span><span class="sxs-lookup"><span data-stu-id="da0a1-117">The subflavors of garbage collection are background and non-concurrent.</span></span>

<span data-ttu-id="da0a1-118">Użyj następujących ustawień, aby wybrać typy wyrzucania elementów bezużytecznych:</span><span class="sxs-lookup"><span data-stu-id="da0a1-118">Use the following settings to select flavors of garbage collection:</span></span>

### <a name="systemgcservercomplus_gcserver"></a><span data-ttu-id="da0a1-119">System. GC. Server/COMPlus_gcServer</span><span class="sxs-lookup"><span data-stu-id="da0a1-119">System.GC.Server/COMPlus_gcServer</span></span>

- <span data-ttu-id="da0a1-120">Określa, czy aplikacja używa wyrzucania elementów bezużytecznych stacji roboczej lub odzyskiwania pamięci serwera.</span><span class="sxs-lookup"><span data-stu-id="da0a1-120">Configures whether the application uses workstation garbage collection or server garbage collection.</span></span>
- <span data-ttu-id="da0a1-121">Domyślnie: wyrzucanie elementów bezużytecznych stacji roboczej (`false`).</span><span class="sxs-lookup"><span data-stu-id="da0a1-121">Default: Workstation garbage collection (`false`).</span></span>

| | <span data-ttu-id="da0a1-122">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="da0a1-122">Setting name</span></span> | <span data-ttu-id="da0a1-123">Wartości</span><span class="sxs-lookup"><span data-stu-id="da0a1-123">Values</span></span> | <span data-ttu-id="da0a1-124">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="da0a1-124">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="da0a1-125">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="da0a1-125">**runtimeconfig.json**</span></span> | `System.GC.Server` | <span data-ttu-id="da0a1-126">`false` — stacja robocza</span><span class="sxs-lookup"><span data-stu-id="da0a1-126">`false` - workstation</span></span><br/><span data-ttu-id="da0a1-127">`true` — serwer</span><span class="sxs-lookup"><span data-stu-id="da0a1-127">`true` - server</span></span> | <span data-ttu-id="da0a1-128">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-128">.NET Core 1.0</span></span> |
| <span data-ttu-id="da0a1-129">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="da0a1-129">**Environment variable**</span></span> | `COMPlus_gcServer` | <span data-ttu-id="da0a1-130">`0` — stacja robocza</span><span class="sxs-lookup"><span data-stu-id="da0a1-130">`0` - workstation</span></span><br/><span data-ttu-id="da0a1-131">`1` — serwer</span><span class="sxs-lookup"><span data-stu-id="da0a1-131">`1` - server</span></span> | <span data-ttu-id="da0a1-132">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-132">.NET Core 1.0</span></span> |
| <span data-ttu-id="da0a1-133">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="da0a1-133">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="da0a1-134">GCServer</span><span class="sxs-lookup"><span data-stu-id="da0a1-134">GCServer</span></span>](../../framework/configure-apps/file-schema/runtime/gcserver-element.md) | <span data-ttu-id="da0a1-135">`false` — stacja robocza</span><span class="sxs-lookup"><span data-stu-id="da0a1-135">`false` - workstation</span></span><br/><span data-ttu-id="da0a1-136">`true` — serwer</span><span class="sxs-lookup"><span data-stu-id="da0a1-136">`true` - server</span></span> |  |

<span data-ttu-id="da0a1-137">Przykład:</span><span class="sxs-lookup"><span data-stu-id="da0a1-137">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Server": true
      }
   }
}
```

### <a name="systemgcconcurrentcomplus_gcconcurrent"></a><span data-ttu-id="da0a1-138">System. GC. współbieżne/COMPlus_gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="da0a1-138">System.GC.Concurrent/COMPlus_gcConcurrent</span></span>

- <span data-ttu-id="da0a1-139">Określa, czy jest włączone wyrzucanie elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="da0a1-139">Configures whether background (concurrent) garbage collection is enabled.</span></span>
- <span data-ttu-id="da0a1-140">Wartość domyślna: włączone (`true`).</span><span class="sxs-lookup"><span data-stu-id="da0a1-140">Default: Enabled (`true`).</span></span>
- <span data-ttu-id="da0a1-141">Aby uzyskać więcej informacji, zobacz [zbieranie elementów bezużytecznych w tle](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) i [odzyskiwanie pamięci serwera w tle](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span><span class="sxs-lookup"><span data-stu-id="da0a1-141">For more information, see [Background garbage collection](../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection) and [Background server garbage collection](../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection).</span></span>

| | <span data-ttu-id="da0a1-142">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="da0a1-142">Setting name</span></span> | <span data-ttu-id="da0a1-143">Wartości</span><span class="sxs-lookup"><span data-stu-id="da0a1-143">Values</span></span> | <span data-ttu-id="da0a1-144">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="da0a1-144">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="da0a1-145">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="da0a1-145">**runtimeconfig.json**</span></span> | `System.GC.Concurrent` | <span data-ttu-id="da0a1-146">`true` — w tle GC</span><span class="sxs-lookup"><span data-stu-id="da0a1-146">`true` - background GC</span></span><br/><span data-ttu-id="da0a1-147">`false` — niewspółbieżne GC</span><span class="sxs-lookup"><span data-stu-id="da0a1-147">`false` - non-concurrent GC</span></span> | <span data-ttu-id="da0a1-148">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-148">.NET Core 1.0</span></span> |
| <span data-ttu-id="da0a1-149">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="da0a1-149">**Environment variable**</span></span> | `COMPlus_gcConcurrent` | <span data-ttu-id="da0a1-150">`true` — w tle GC</span><span class="sxs-lookup"><span data-stu-id="da0a1-150">`true` - background GC</span></span><br/><span data-ttu-id="da0a1-151">`false` — niewspółbieżne GC</span><span class="sxs-lookup"><span data-stu-id="da0a1-151">`false` - non-concurrent GC</span></span> | <span data-ttu-id="da0a1-152">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-152">.NET Core 1.0</span></span> |
| <span data-ttu-id="da0a1-153">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="da0a1-153">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="da0a1-154">gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="da0a1-154">gcConcurrent</span></span>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) | <span data-ttu-id="da0a1-155">`true` — w tle GC</span><span class="sxs-lookup"><span data-stu-id="da0a1-155">`true` - background GC</span></span><br/><span data-ttu-id="da0a1-156">`false` — niewspółbieżne GC</span><span class="sxs-lookup"><span data-stu-id="da0a1-156">`false` - non-concurrent GC</span></span> |  |

<span data-ttu-id="da0a1-157">Przykład:</span><span class="sxs-lookup"><span data-stu-id="da0a1-157">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": false
      }
   }
}
```

## <a name="manage-resource-usage"></a><span data-ttu-id="da0a1-158">Zarządzanie użyciem zasobów</span><span class="sxs-lookup"><span data-stu-id="da0a1-158">Manage resource usage</span></span>

<span data-ttu-id="da0a1-159">Ustawienia opisane w tej sekcji służą do zarządzania użyciem pamięci i procesora modułu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="da0a1-159">Use the settings described in this section to manage the garbage collector's memory and processor usage.</span></span>

<span data-ttu-id="da0a1-160">Aby uzyskać więcej informacji na temat niektórych z tych ustawień, zapoznaj się z wpisem na blogu centrum [robocze i serwer GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) .</span><span class="sxs-lookup"><span data-stu-id="da0a1-160">For more information about some of these settings, see the [Middle ground between workstation and server GC](https://devblogs.microsoft.com/dotnet/middle-ground-between-server-and-workstation-gc/) blog entry.</span></span>

### <a name="systemgcheapcountcomplus_gcheapcount"></a><span data-ttu-id="da0a1-161">System. GC. HeapCount/COMPlus_GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="da0a1-161">System.GC.HeapCount/COMPlus_GCHeapCount</span></span>

- <span data-ttu-id="da0a1-162">Ogranicza liczbę stert utworzonych przez moduł wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="da0a1-162">Limits the number of heaps created by the garbage collector.</span></span>
- <span data-ttu-id="da0a1-163">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="da0a1-163">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="da0a1-164">Jeśli koligacja procesora GC jest włączona, co jest ustawieniem domyślnym, licznik sterty skoligacony `n` GC sterty/wątki z pierwszymi procesorami `n`.</span><span class="sxs-lookup"><span data-stu-id="da0a1-164">If GC processor affinity is enabled, which is the default, the heap count setting affinitizes `n` GC heaps/threads to the first `n` processors.</span></span> <span data-ttu-id="da0a1-165">(Użyj koligacji maska lub ustawienia zakresów koligacji, aby określić, które procesory mają być koligacji).</span><span class="sxs-lookup"><span data-stu-id="da0a1-165">(Use the affinitize mask or affinitize ranges settings to specify exactly which processors to affinitize.)</span></span>
- <span data-ttu-id="da0a1-166">Jeśli koligacja procesora GC jest wyłączona, to ustawienie ogranicza liczbę stert GC.</span><span class="sxs-lookup"><span data-stu-id="da0a1-166">If GC processor affinity is disabled, this setting limits the number of GC heaps.</span></span>
- <span data-ttu-id="da0a1-167">Aby uzyskać więcej informacji, zobacz [uwagi GCHeapCount](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span><span class="sxs-lookup"><span data-stu-id="da0a1-167">For more information, see the [GCHeapCount remarks](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md#remarks).</span></span>

| | <span data-ttu-id="da0a1-168">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="da0a1-168">Setting name</span></span> | <span data-ttu-id="da0a1-169">Wartości</span><span class="sxs-lookup"><span data-stu-id="da0a1-169">Values</span></span> | <span data-ttu-id="da0a1-170">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="da0a1-170">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="da0a1-171">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="da0a1-171">**runtimeconfig.json**</span></span> | `System.GC.HeapCount` | <span data-ttu-id="da0a1-172">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="da0a1-172">*decimal value*</span></span> | <span data-ttu-id="da0a1-173">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-173">.NET Core 3.0</span></span> |
| <span data-ttu-id="da0a1-174">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="da0a1-174">**Environment variable**</span></span> | `COMPlus_GCHeapCount` | <span data-ttu-id="da0a1-175">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="da0a1-175">*hexadecimal value*</span></span> | <span data-ttu-id="da0a1-176">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-176">.NET Core 3.0</span></span> |
| <span data-ttu-id="da0a1-177">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="da0a1-177">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="da0a1-178">GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="da0a1-178">GCHeapCount</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapcount-element.md) | <span data-ttu-id="da0a1-179">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="da0a1-179">*decimal value*</span></span> | <span data-ttu-id="da0a1-180">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="da0a1-180">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="da0a1-181">Przykład:</span><span class="sxs-lookup"><span data-stu-id="da0a1-181">Example:</span></span>

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
> <span data-ttu-id="da0a1-182">Jeśli ustawiasz opcję w *runtimeconfig. JSON*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="da0a1-182">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="da0a1-183">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="da0a1-183">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="da0a1-184">Na przykład aby ograniczyć liczbę stert do 16, wartości dla pliku JSON i 0x10 lub 10 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="da0a1-184">For example, to limit the number of heaps to 16, the values would be 16 for the JSON file and 0x10 or 10 for the environment variable.</span></span>

### <a name="systemgcheapaffinitizemaskcomplus_gcheapaffinitizemask"></a><span data-ttu-id="da0a1-185">System. GC. HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="da0a1-185">System.GC.HeapAffinitizeMask/COMPlus_GCHeapAffinitizeMask</span></span>

- <span data-ttu-id="da0a1-186">Określa dokładne procesory, które powinny być używane przez wątki modułu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="da0a1-186">Specifies the exact processors that garbage collector threads should use.</span></span>
- <span data-ttu-id="da0a1-187">Jeśli Koligacja procesorów jest wyłączona przez ustawienie `System.GC.NoAffinitize` do `true`, to ustawienie zostanie zignorowane.</span><span class="sxs-lookup"><span data-stu-id="da0a1-187">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="da0a1-188">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="da0a1-188">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="da0a1-189">Wartość jest maską bitową, która definiuje procesory, które są dostępne dla procesu.</span><span class="sxs-lookup"><span data-stu-id="da0a1-189">The value is a bit mask that defines the processors that are available to the process.</span></span> <span data-ttu-id="da0a1-190">Na przykład wartość dziesiętna 1023 (lub wartość szesnastkowa 0x3FF lub 3FF, jeśli używana jest zmienna środowiskowa) to 0011 1111 1111 w notacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="da0a1-190">For example, a decimal value of 1023 (or a hexadecimal value of 0x3FF or 3FF if you're using the environment variable) is 0011 1111 1111 in binary notation.</span></span> <span data-ttu-id="da0a1-191">Oznacza to, że pierwsze 10 procesorów ma być używany.</span><span class="sxs-lookup"><span data-stu-id="da0a1-191">This specifies that the first 10 processors are to be used.</span></span> <span data-ttu-id="da0a1-192">Aby określić następne 10 procesorów, czyli procesorów 10-19, określ wartość dziesiętną 1047552 (lub wartość szesnastkową 0xFFC00 lub FFC00), która jest równoważna z wartością binarną 1111 1111 1100 0000 0000.</span><span class="sxs-lookup"><span data-stu-id="da0a1-192">To specify the next 10 processors, that is, processors 10-19, specify a decimal value of 1047552 (or a hexadecimal value of 0xFFC00 or FFC00), which is equivalent to a binary value of 1111 1111 1100 0000 0000.</span></span>

| | <span data-ttu-id="da0a1-193">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="da0a1-193">Setting name</span></span> | <span data-ttu-id="da0a1-194">Wartości</span><span class="sxs-lookup"><span data-stu-id="da0a1-194">Values</span></span> | <span data-ttu-id="da0a1-195">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="da0a1-195">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="da0a1-196">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="da0a1-196">**runtimeconfig.json**</span></span> | `System.GC.HeapAffinitizeMask` | <span data-ttu-id="da0a1-197">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="da0a1-197">*decimal value*</span></span> | <span data-ttu-id="da0a1-198">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-198">.NET Core 3.0</span></span> |
| <span data-ttu-id="da0a1-199">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="da0a1-199">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeMask` | <span data-ttu-id="da0a1-200">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="da0a1-200">*hexadecimal value*</span></span> | <span data-ttu-id="da0a1-201">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-201">.NET Core 3.0</span></span> |
| <span data-ttu-id="da0a1-202">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="da0a1-202">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="da0a1-203">GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="da0a1-203">GCHeapAffinitizeMask</span></span>](../../framework/configure-apps/file-schema/runtime/gcheapaffinitizemask-element.md) | <span data-ttu-id="da0a1-204">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="da0a1-204">*decimal value*</span></span> | <span data-ttu-id="da0a1-205">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="da0a1-205">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="da0a1-206">Przykład:</span><span class="sxs-lookup"><span data-stu-id="da0a1-206">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.HeapAffinitizeMask": 1023
      }
   }
}
```

### <a name="systemgcgcheapaffinitizerangescomplus_gcheapaffinitizeranges"></a><span data-ttu-id="da0a1-207">System. GC. GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span><span class="sxs-lookup"><span data-stu-id="da0a1-207">System.GC.GCHeapAffinitizeRanges/COMPlus_GCHeapAffinitizeRanges</span></span>

- <span data-ttu-id="da0a1-208">Określa listę procesorów, które mają być używane na potrzeby wątków modułu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="da0a1-208">Specifies the list of processors to use for garbage collector threads.</span></span>
- <span data-ttu-id="da0a1-209">To ustawienie jest podobne do `System.GC.HeapAffinitizeMask`, z tą różnicą, że pozwala określić więcej niż 64 procesorów.</span><span class="sxs-lookup"><span data-stu-id="da0a1-209">This setting is similar to `System.GC.HeapAffinitizeMask`, except it allows you to specify more than 64 processors.</span></span>
- <span data-ttu-id="da0a1-210">W przypadku systemów operacyjnych Windows należy prefiksować numer procesora lub zakres z odpowiednią [grupą procesorów CPU](/windows/win32/procthread/processor-groups), na przykład "0:1-10, 0:12, 1:50-52, 1:70".</span><span class="sxs-lookup"><span data-stu-id="da0a1-210">For Windows operating systems, prefix the processor number or range with the corresponding [CPU group](/windows/win32/procthread/processor-groups), for example, "0:1-10,0:12,1:50-52,1:70".</span></span>
- <span data-ttu-id="da0a1-211">Jeśli Koligacja procesorów jest wyłączona przez ustawienie `System.GC.NoAffinitize` do `true`, to ustawienie zostanie zignorowane.</span><span class="sxs-lookup"><span data-stu-id="da0a1-211">If processor affinity is disabled by setting `System.GC.NoAffinitize` to `true`, this setting is ignored.</span></span>
- <span data-ttu-id="da0a1-212">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="da0a1-212">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="da0a1-213">Aby uzyskać więcej informacji, zobacz temat [Zapewnianie lepszej konfiguracji procesora dla GC na maszynach z > 64 procesorów CPU](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="da0a1-213">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="da0a1-214">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="da0a1-214">Setting name</span></span> | <span data-ttu-id="da0a1-215">Wartości</span><span class="sxs-lookup"><span data-stu-id="da0a1-215">Values</span></span> | <span data-ttu-id="da0a1-216">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="da0a1-216">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="da0a1-217">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="da0a1-217">**runtimeconfig.json**</span></span> | `System.GC.GCHeapAffinitizeRanges` | <span data-ttu-id="da0a1-218">Rozdzielana przecinkami lista numerów procesorów lub zakresów numerów procesorów.</span><span class="sxs-lookup"><span data-stu-id="da0a1-218">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="da0a1-219">Przykład UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="da0a1-219">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="da0a1-220">Przykład systemu Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="da0a1-220">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="da0a1-221">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-221">.NET Core 3.0</span></span> |
| <span data-ttu-id="da0a1-222">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="da0a1-222">**Environment variable**</span></span> | `COMPlus_GCHeapAffinitizeRanges` | <span data-ttu-id="da0a1-223">Rozdzielana przecinkami lista numerów procesorów lub zakresów numerów procesorów.</span><span class="sxs-lookup"><span data-stu-id="da0a1-223">Comma-separated list of processor numbers or ranges of processor numbers.</span></span><br/><span data-ttu-id="da0a1-224">Przykład UNIX: "1-10, 12, 50-52, 70"</span><span class="sxs-lookup"><span data-stu-id="da0a1-224">Unix example: "1-10,12,50-52,70"</span></span><br/><span data-ttu-id="da0a1-225">Przykład systemu Windows: "0:1-10, 0:12, 1:50-52, 1:70"</span><span class="sxs-lookup"><span data-stu-id="da0a1-225">Windows example: "0:1-10,0:12,1:50-52,1:70"</span></span> | <span data-ttu-id="da0a1-226">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-226">.NET Core 3.0</span></span> |

<span data-ttu-id="da0a1-227">Przykład:</span><span class="sxs-lookup"><span data-stu-id="da0a1-227">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.GCHeapAffinitizeRanges": "0:1-10,0:12,1:50-52,1:70"
      }
   }
}
```

### <a name="complus_gccpugroup"></a><span data-ttu-id="da0a1-228">COMPlus_GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="da0a1-228">COMPlus_GCCpuGroup</span></span>

- <span data-ttu-id="da0a1-229">Określa, czy moduł wyrzucania elementów bezużytecznych używa [grup CPU](/windows/win32/procthread/processor-groups) , czy nie.</span><span class="sxs-lookup"><span data-stu-id="da0a1-229">Configures whether the garbage collector uses [CPU groups](/windows/win32/procthread/processor-groups) or not.</span></span>

  <span data-ttu-id="da0a1-230">Gdy 64-bitowy komputer z systemem Windows ma wiele grup CPU, oznacza to, że istnieje więcej niż 64 procesorów, włączając ten element rozszerza wyrzucanie elementów bezużytecznych we wszystkich grupach CPU.</span><span class="sxs-lookup"><span data-stu-id="da0a1-230">When a 64-bit Windows computer has multiple CPU groups, that is, there are more than 64 processors, enabling this element extends garbage collection across all CPU groups.</span></span> <span data-ttu-id="da0a1-231">Moduł wyrzucania elementów bezużytecznych używa wszystkich rdzeni do tworzenia i równoważenia sterty.</span><span class="sxs-lookup"><span data-stu-id="da0a1-231">The garbage collector uses all cores to create and balance heaps.</span></span>

- <span data-ttu-id="da0a1-232">Stosuje się do wyrzucania elementów bezużytecznych serwera w 64-bitowych systemach operacyjnych Windows.</span><span class="sxs-lookup"><span data-stu-id="da0a1-232">Applies to server garbage collection on 64-bit Windows operation systems only.</span></span>
- <span data-ttu-id="da0a1-233">Domyślnie: wyłączone (`0`).</span><span class="sxs-lookup"><span data-stu-id="da0a1-233">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="da0a1-234">Aby uzyskać więcej informacji, zobacz temat [Zapewnianie lepszej konfiguracji procesora dla GC na maszynach z > 64 procesorów CPU](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) na blogu Maoni Stephens.</span><span class="sxs-lookup"><span data-stu-id="da0a1-234">For more information, see [Making CPU configuration better for GC on machines with > 64 CPUs](https://devblogs.microsoft.com/dotnet/making-cpu-configuration-better-for-gc-on-machines-with-64-cpus/) on Maoni Stephens' blog.</span></span>

| | <span data-ttu-id="da0a1-235">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="da0a1-235">Setting name</span></span> | <span data-ttu-id="da0a1-236">Wartości</span><span class="sxs-lookup"><span data-stu-id="da0a1-236">Values</span></span> | <span data-ttu-id="da0a1-237">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="da0a1-237">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="da0a1-238">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="da0a1-238">**runtimeconfig.json**</span></span> | <span data-ttu-id="da0a1-239">N/D</span><span class="sxs-lookup"><span data-stu-id="da0a1-239">N/A</span></span> | <span data-ttu-id="da0a1-240">N/D</span><span class="sxs-lookup"><span data-stu-id="da0a1-240">N/A</span></span> | <span data-ttu-id="da0a1-241">N/D</span><span class="sxs-lookup"><span data-stu-id="da0a1-241">N/A</span></span> |
| <span data-ttu-id="da0a1-242">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="da0a1-242">**Environment variable**</span></span> | `COMPlus_GCCpuGroup` | <span data-ttu-id="da0a1-243">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="da0a1-243">`0` - disabled</span></span><br/><span data-ttu-id="da0a1-244">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="da0a1-244">`1` - enabled</span></span> | <span data-ttu-id="da0a1-245">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-245">.NET Core 1.0</span></span> |
| <span data-ttu-id="da0a1-246">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="da0a1-246">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="da0a1-247">GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="da0a1-247">GCCpuGroup</span></span>](../../framework/configure-apps/file-schema/runtime/gccpugroup-element.md) | <span data-ttu-id="da0a1-248">`false` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="da0a1-248">`false` - disabled</span></span><br/><span data-ttu-id="da0a1-249">`true` — włączono</span><span class="sxs-lookup"><span data-stu-id="da0a1-249">`true` - enabled</span></span> |  |

> [!NOTE]
> <span data-ttu-id="da0a1-250">Aby skonfigurować środowisko uruchomieniowe języka wspólnego (CLR) do dystrybucji wątków z puli wątków we wszystkich grupach procesora, Włącz opcję [Thread_UseAllCpuGroups elementu](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="da0a1-250">To configure the common language runtime (CLR) to also distribute threads from the thread pool across all CPU groups, enable the [Thread_UseAllCpuGroups element](../../framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) option.</span></span> <span data-ttu-id="da0a1-251">W przypadku aplikacji platformy .NET Core można włączyć tę opcję, ustawiając wartość zmiennej środowiskowej `COMPlus_Thread_UseAllCpuGroups` na `1`.</span><span class="sxs-lookup"><span data-stu-id="da0a1-251">For .NET Core apps, you can enable this option by setting the value of the `COMPlus_Thread_UseAllCpuGroups` environment variable to `1`.</span></span>

### <a name="systemgcnoaffinitizecomplus_gcnoaffinitize"></a><span data-ttu-id="da0a1-252">System. GC. NoAffinitize/COMPlus_GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="da0a1-252">System.GC.NoAffinitize/COMPlus_GCNoAffinitize</span></span>

- <span data-ttu-id="da0a1-253">Określa, czy *koligacji* wątki odzyskiwania pamięci z procesorami.</span><span class="sxs-lookup"><span data-stu-id="da0a1-253">Specifies whether to *affinitize* garbage collection threads with processors.</span></span> <span data-ttu-id="da0a1-254">Aby koligacji wątek GC, oznacza to, że można go uruchomić tylko w określonym procesorze CPU.</span><span class="sxs-lookup"><span data-stu-id="da0a1-254">To affinitize a GC thread means that it can only run on its specific CPU.</span></span> <span data-ttu-id="da0a1-255">Sterta jest tworzona dla każdego wątku GC.</span><span class="sxs-lookup"><span data-stu-id="da0a1-255">A heap is created for each GC thread.</span></span>
- <span data-ttu-id="da0a1-256">Dotyczy tylko wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="da0a1-256">Applies to server garbage collection only.</span></span>
- <span data-ttu-id="da0a1-257">Domyślnie: koligacji wątki odzyskiwania pamięci z procesorami (`false`).</span><span class="sxs-lookup"><span data-stu-id="da0a1-257">Default: Affinitize garbage collection threads with processors (`false`).</span></span>

| | <span data-ttu-id="da0a1-258">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="da0a1-258">Setting name</span></span> | <span data-ttu-id="da0a1-259">Wartości</span><span class="sxs-lookup"><span data-stu-id="da0a1-259">Values</span></span> | <span data-ttu-id="da0a1-260">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="da0a1-260">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="da0a1-261">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="da0a1-261">**runtimeconfig.json**</span></span> | `System.GC.NoAffinitize` | <span data-ttu-id="da0a1-262">`false` — koligacji</span><span class="sxs-lookup"><span data-stu-id="da0a1-262">`false` - affinitize</span></span><br/><span data-ttu-id="da0a1-263">`true` — nie koligacji</span><span class="sxs-lookup"><span data-stu-id="da0a1-263">`true` - don't affinitize</span></span> | <span data-ttu-id="da0a1-264">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-264">.NET Core 3.0</span></span> |
| <span data-ttu-id="da0a1-265">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="da0a1-265">**Environment variable**</span></span> | `COMPlus_GCNoAffinitize` | <span data-ttu-id="da0a1-266">`0` — koligacji</span><span class="sxs-lookup"><span data-stu-id="da0a1-266">`0` - affinitize</span></span><br/><span data-ttu-id="da0a1-267">`1` — nie koligacji</span><span class="sxs-lookup"><span data-stu-id="da0a1-267">`1` - don't affinitize</span></span> | <span data-ttu-id="da0a1-268">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-268">.NET Core 3.0</span></span> |
| <span data-ttu-id="da0a1-269">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="da0a1-269">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="da0a1-270">GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="da0a1-270">GCNoAffinitize</span></span>](../../framework/configure-apps/file-schema/runtime/gcnoaffinitize-element.md) | <span data-ttu-id="da0a1-271">`false` — koligacji</span><span class="sxs-lookup"><span data-stu-id="da0a1-271">`false` - affinitize</span></span><br/><span data-ttu-id="da0a1-272">`true` — nie koligacji</span><span class="sxs-lookup"><span data-stu-id="da0a1-272">`true` - don't affinitize</span></span> | <span data-ttu-id="da0a1-273">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="da0a1-273">.NET Framework 4.6.2</span></span> |

<span data-ttu-id="da0a1-274">Przykład:</span><span class="sxs-lookup"><span data-stu-id="da0a1-274">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.NoAffinitize": true
      }
   }
}
```

### <a name="systemgcheaphardlimitcomplus_gcheaphardlimit"></a><span data-ttu-id="da0a1-275">System. GC. HeapHardLimit/COMPlus_GCHeapHardLimit</span><span class="sxs-lookup"><span data-stu-id="da0a1-275">System.GC.HeapHardLimit/COMPlus_GCHeapHardLimit</span></span>

- <span data-ttu-id="da0a1-276">Określa maksymalny rozmiar zatwierdzeń w bajtach dla sterty GC i księgowości GC.</span><span class="sxs-lookup"><span data-stu-id="da0a1-276">Specifies the maximum commit size, in bytes, for the GC heap and GC bookkeeping.</span></span>

| | <span data-ttu-id="da0a1-277">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="da0a1-277">Setting name</span></span> | <span data-ttu-id="da0a1-278">Wartości</span><span class="sxs-lookup"><span data-stu-id="da0a1-278">Values</span></span> | <span data-ttu-id="da0a1-279">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="da0a1-279">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="da0a1-280">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="da0a1-280">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimit` | <span data-ttu-id="da0a1-281">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="da0a1-281">*decimal value*</span></span> | <span data-ttu-id="da0a1-282">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-282">.NET Core 3.0</span></span> |
| <span data-ttu-id="da0a1-283">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="da0a1-283">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimit` | <span data-ttu-id="da0a1-284">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="da0a1-284">*hexadecimal value*</span></span> | <span data-ttu-id="da0a1-285">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-285">.NET Core 3.0</span></span> |

<span data-ttu-id="da0a1-286">Przykład:</span><span class="sxs-lookup"><span data-stu-id="da0a1-286">Example:</span></span>

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
> <span data-ttu-id="da0a1-287">Jeśli ustawiasz opcję w *runtimeconfig. JSON*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="da0a1-287">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="da0a1-288">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="da0a1-288">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="da0a1-289">Na przykład aby określić stały limit sterty wynoszący 200 mebibytes (MiB), wartości byłyby 209715200 dla pliku JSON i 0xC800000 lub C800000 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="da0a1-289">For example, to specify a heap hard limit of 200 mebibytes (MiB), the values would be 209715200 for the JSON file and 0xC800000 or C800000 for the environment variable.</span></span>

### <a name="systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent"></a><span data-ttu-id="da0a1-290">System. GC. HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span><span class="sxs-lookup"><span data-stu-id="da0a1-290">System.GC.HeapHardLimitPercent/COMPlus_GCHeapHardLimitPercent</span></span>

- <span data-ttu-id="da0a1-291">Określa użycie sterty GC jako procent całkowitej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="da0a1-291">Specifies the GC heap usage as a percentage of the total memory.</span></span>

| | <span data-ttu-id="da0a1-292">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="da0a1-292">Setting name</span></span> | <span data-ttu-id="da0a1-293">Wartości</span><span class="sxs-lookup"><span data-stu-id="da0a1-293">Values</span></span> | <span data-ttu-id="da0a1-294">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="da0a1-294">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="da0a1-295">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="da0a1-295">**runtimeconfig.json**</span></span> | `System.GC.HeapHardLimitPercent` | <span data-ttu-id="da0a1-296">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="da0a1-296">*decimal value*</span></span> | <span data-ttu-id="da0a1-297">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-297">.NET Core 3.0</span></span> |
| <span data-ttu-id="da0a1-298">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="da0a1-298">**Environment variable**</span></span> | `COMPlus_GCHeapHardLimitPercent` | <span data-ttu-id="da0a1-299">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="da0a1-299">*hexadecimal value*</span></span> | <span data-ttu-id="da0a1-300">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-300">.NET Core 3.0</span></span> |

<span data-ttu-id="da0a1-301">Przykład:</span><span class="sxs-lookup"><span data-stu-id="da0a1-301">Example:</span></span>

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
> <span data-ttu-id="da0a1-302">Jeśli ustawiasz opcję w *runtimeconfig. JSON*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="da0a1-302">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="da0a1-303">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="da0a1-303">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="da0a1-304">Na przykład aby ograniczyć użycie sterty do 30%, wartości byłyby 30 dla pliku JSON i 0x1E lub 1E dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="da0a1-304">For example, to limit the heap usage to 30%, the values would be 30 for the JSON file and 0x1E or 1E for the environment variable.</span></span>

### <a name="systemgcretainvmcomplus_gcretainvm"></a><span data-ttu-id="da0a1-305">System. GC. RetainVM/COMPlus_GCRetainVM</span><span class="sxs-lookup"><span data-stu-id="da0a1-305">System.GC.RetainVM/COMPlus_GCRetainVM</span></span>

- <span data-ttu-id="da0a1-306">Określa, czy segmenty, które mają zostać usunięte, są umieszczane na liście gotowości do użycia w przyszłości lub są wyłączane z powrotem do systemu operacyjnego (OS).</span><span class="sxs-lookup"><span data-stu-id="da0a1-306">Configures whether segments that should be deleted are put on a standby list for future use or are released back to the operating system (OS).</span></span>
- <span data-ttu-id="da0a1-307">Domyślnie: segmenty wydań z powrotem do systemu operacyjnego (`false`).</span><span class="sxs-lookup"><span data-stu-id="da0a1-307">Default: Release segments back to the operating system (`false`).</span></span>

| | <span data-ttu-id="da0a1-308">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="da0a1-308">Setting name</span></span> | <span data-ttu-id="da0a1-309">Wartości</span><span class="sxs-lookup"><span data-stu-id="da0a1-309">Values</span></span> | <span data-ttu-id="da0a1-310">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="da0a1-310">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="da0a1-311">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="da0a1-311">**runtimeconfig.json**</span></span> | `System.GC.RetainVM` | <span data-ttu-id="da0a1-312">`false` — wydanie do systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="da0a1-312">`false` - release to OS</span></span><br/><span data-ttu-id="da0a1-313">`true` — Umieść w stanie wstrzymania</span><span class="sxs-lookup"><span data-stu-id="da0a1-313">`true` - put on standby</span></span>| <span data-ttu-id="da0a1-314">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-314">.NET Core 1.0</span></span> |
| <span data-ttu-id="da0a1-315">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="da0a1-315">**Environment variable**</span></span> | `COMPlus_GCRetainVM` | <span data-ttu-id="da0a1-316">`0` — wydanie do systemu operacyjnego</span><span class="sxs-lookup"><span data-stu-id="da0a1-316">`0` - release to OS</span></span><br/><span data-ttu-id="da0a1-317">`1` — Umieść w stanie wstrzymania</span><span class="sxs-lookup"><span data-stu-id="da0a1-317">`1` - put on standby</span></span> | <span data-ttu-id="da0a1-318">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-318">.NET Core 1.0</span></span> |

<span data-ttu-id="da0a1-319">Przykład:</span><span class="sxs-lookup"><span data-stu-id="da0a1-319">Example:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.RetainVM": true
      }
   }
}
```

## <a name="large-pages"></a><span data-ttu-id="da0a1-320">Duże strony</span><span class="sxs-lookup"><span data-stu-id="da0a1-320">Large pages</span></span>

### <a name="complus_gclargepages"></a><span data-ttu-id="da0a1-321">COMPlus_GCLargePages</span><span class="sxs-lookup"><span data-stu-id="da0a1-321">COMPlus_GCLargePages</span></span>

- <span data-ttu-id="da0a1-322">Określa, czy mają być używane duże strony, gdy jest ustawiony limit sztywny sterty.</span><span class="sxs-lookup"><span data-stu-id="da0a1-322">Specifies whether large pages should be used when a heap hard limit is set.</span></span>
- <span data-ttu-id="da0a1-323">Domyślnie: wyłączone (`0`).</span><span class="sxs-lookup"><span data-stu-id="da0a1-323">Default: Disabled (`0`).</span></span>
- <span data-ttu-id="da0a1-324">Jest to ustawienie eksperymentalne.</span><span class="sxs-lookup"><span data-stu-id="da0a1-324">This is an experimental setting.</span></span>

| | <span data-ttu-id="da0a1-325">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="da0a1-325">Setting name</span></span> | <span data-ttu-id="da0a1-326">Wartości</span><span class="sxs-lookup"><span data-stu-id="da0a1-326">Values</span></span> | <span data-ttu-id="da0a1-327">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="da0a1-327">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="da0a1-328">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="da0a1-328">**runtimeconfig.json**</span></span> | <span data-ttu-id="da0a1-329">N/D</span><span class="sxs-lookup"><span data-stu-id="da0a1-329">N/A</span></span> | <span data-ttu-id="da0a1-330">N/D</span><span class="sxs-lookup"><span data-stu-id="da0a1-330">N/A</span></span> | <span data-ttu-id="da0a1-331">N/D</span><span class="sxs-lookup"><span data-stu-id="da0a1-331">N/A</span></span> |
| <span data-ttu-id="da0a1-332">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="da0a1-332">**Environment variable**</span></span> | `COMPlus_GCLargePages` | <span data-ttu-id="da0a1-333">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="da0a1-333">`0` - disabled</span></span><br/><span data-ttu-id="da0a1-334">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="da0a1-334">`1` - enabled</span></span> | <span data-ttu-id="da0a1-335">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-335">.NET Core 3.0</span></span> |

## <a name="large-objects"></a><span data-ttu-id="da0a1-336">Duże obiekty</span><span class="sxs-lookup"><span data-stu-id="da0a1-336">Large objects</span></span>

### <a name="complus_gcallowverylargeobjects"></a><span data-ttu-id="da0a1-337">COMPlus_gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="da0a1-337">COMPlus_gcAllowVeryLargeObjects</span></span>

- <span data-ttu-id="da0a1-338">Konfiguruje obsługę modułu wyrzucania elementów bezużytecznych na platformach 64-bitowych dla tablic, które są większe niż 2 gigabajty (GB) w łącznym rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="da0a1-338">Configures garbage collector support on 64-bit platforms for arrays that are greater than 2 gigabytes (GB) in total size.</span></span>
- <span data-ttu-id="da0a1-339">Wartość domyślna: włączone (`1`).</span><span class="sxs-lookup"><span data-stu-id="da0a1-339">Default: Enabled (`1`).</span></span>
- <span data-ttu-id="da0a1-340">Ta opcja może stać się przestarzała w przyszłej wersji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="da0a1-340">This option may become obsolete in a future version of .NET.</span></span>

| | <span data-ttu-id="da0a1-341">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="da0a1-341">Setting name</span></span> | <span data-ttu-id="da0a1-342">Wartości</span><span class="sxs-lookup"><span data-stu-id="da0a1-342">Values</span></span> | <span data-ttu-id="da0a1-343">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="da0a1-343">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="da0a1-344">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="da0a1-344">**runtimeconfig.json**</span></span> | <span data-ttu-id="da0a1-345">N/D</span><span class="sxs-lookup"><span data-stu-id="da0a1-345">N/A</span></span> | <span data-ttu-id="da0a1-346">N/D</span><span class="sxs-lookup"><span data-stu-id="da0a1-346">N/A</span></span> | <span data-ttu-id="da0a1-347">N/D</span><span class="sxs-lookup"><span data-stu-id="da0a1-347">N/A</span></span> |
| <span data-ttu-id="da0a1-348">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="da0a1-348">**Environment variable**</span></span> | `COMPlus_gcAllowVeryLargeObjects` | <span data-ttu-id="da0a1-349">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="da0a1-349">`1` - enabled</span></span><br/> <span data-ttu-id="da0a1-350">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="da0a1-350">`0` - disabled</span></span> | <span data-ttu-id="da0a1-351">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-351">.NET Core 1.0</span></span> |
| <span data-ttu-id="da0a1-352">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="da0a1-352">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="da0a1-353">gcAllowVeryLargeObjects</span><span class="sxs-lookup"><span data-stu-id="da0a1-353">gcAllowVeryLargeObjects</span></span>](../../framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md) | <span data-ttu-id="da0a1-354">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="da0a1-354">`1` - enabled</span></span><br/> <span data-ttu-id="da0a1-355">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="da0a1-355">`0` - disabled</span></span> | <span data-ttu-id="da0a1-356">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="da0a1-356">.NET Framework 4.5</span></span> |

## <a name="large-object-heap-threshold"></a><span data-ttu-id="da0a1-357">Próg sterty dla dużego obiektu</span><span class="sxs-lookup"><span data-stu-id="da0a1-357">Large object heap threshold</span></span>

### <a name="systemgclohthresholdcomplus_gclohthreshold"></a><span data-ttu-id="da0a1-358">System. GC. LOHThreshold/COMPlus_GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="da0a1-358">System.GC.LOHThreshold/COMPlus_GCLOHThreshold</span></span>

- <span data-ttu-id="da0a1-359">Określa rozmiar progu (w bajtach), który powoduje, że obiekty są na stosie dużego obiektu (LOH).</span><span class="sxs-lookup"><span data-stu-id="da0a1-359">Specifies the threshold size, in bytes, that causes objects to go on the large object heap (LOH).</span></span>
- <span data-ttu-id="da0a1-360">Domyślny próg to 85 000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="da0a1-360">The default threshold is 85,000 bytes.</span></span>
- <span data-ttu-id="da0a1-361">Określona wartość musi być większa niż wartość progu domyślnego.</span><span class="sxs-lookup"><span data-stu-id="da0a1-361">The value you specify must be larger than the default threshold.</span></span>

| | <span data-ttu-id="da0a1-362">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="da0a1-362">Setting name</span></span> | <span data-ttu-id="da0a1-363">Wartości</span><span class="sxs-lookup"><span data-stu-id="da0a1-363">Values</span></span> | <span data-ttu-id="da0a1-364">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="da0a1-364">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="da0a1-365">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="da0a1-365">**runtimeconfig.json**</span></span> | `System.GC.LOHThreshold` | <span data-ttu-id="da0a1-366">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="da0a1-366">*decimal value*</span></span> | <span data-ttu-id="da0a1-367">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-367">.NET Core 1.0</span></span> |
| <span data-ttu-id="da0a1-368">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="da0a1-368">**Environment variable**</span></span> | `COMPlus_GCLOHThreshold` | <span data-ttu-id="da0a1-369">*wartość szesnastkowa*</span><span class="sxs-lookup"><span data-stu-id="da0a1-369">*hexadecimal value*</span></span> | <span data-ttu-id="da0a1-370">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-370">.NET Core 1.0</span></span> |
| <span data-ttu-id="da0a1-371">**App. config dla .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="da0a1-371">**app.config for .NET Framework**</span></span> | [<span data-ttu-id="da0a1-372">GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="da0a1-372">GCLOHThreshold</span></span>](../../framework/configure-apps/file-schema/runtime/gclohthreshold-element.md) | <span data-ttu-id="da0a1-373">*wartość dziesiętna*</span><span class="sxs-lookup"><span data-stu-id="da0a1-373">*decimal value*</span></span> | <span data-ttu-id="da0a1-374">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="da0a1-374">.NET Framework 4.8</span></span> |

<span data-ttu-id="da0a1-375">Przykład:</span><span class="sxs-lookup"><span data-stu-id="da0a1-375">Example:</span></span>

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
> <span data-ttu-id="da0a1-376">Jeśli ustawiasz opcję w *runtimeconfig. JSON*, określ wartość dziesiętną.</span><span class="sxs-lookup"><span data-stu-id="da0a1-376">If you're setting the option in *runtimeconfig.json*, specify a decimal value.</span></span> <span data-ttu-id="da0a1-377">Jeśli ustawiasz opcję jako zmienną środowiskową, określ wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="da0a1-377">If you're setting the option as an environment variable, specify a hexadecimal value.</span></span> <span data-ttu-id="da0a1-378">Na przykład, aby ustawić rozmiar progu 120 000 bajtów, wartości byłyby 120000 dla pliku JSON oraz 0x1D4C0 lub 1D4C0 dla zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="da0a1-378">For example, to set a threshold size of 120,000 bytes, the values would be 120000 for the JSON file and 0x1D4C0 or 1D4C0 for the environment variable.</span></span>

## <a name="standalone-gc"></a><span data-ttu-id="da0a1-379">Autonomiczna GC</span><span class="sxs-lookup"><span data-stu-id="da0a1-379">Standalone GC</span></span>

### <a name="complus_gcname"></a><span data-ttu-id="da0a1-380">COMPlus_GCName</span><span class="sxs-lookup"><span data-stu-id="da0a1-380">COMPlus_GCName</span></span>

- <span data-ttu-id="da0a1-381">Określa ścieżkę do biblioteki zawierającej Moduł wyrzucania elementów bezużytecznych, który środowisko uruchomieniowe zamierza załadować.</span><span class="sxs-lookup"><span data-stu-id="da0a1-381">Specifies a path to the library containing the garbage collector that the runtime intends to load.</span></span>
- <span data-ttu-id="da0a1-382">Aby uzyskać więcej informacji, zobacz [prekonstrukcja modułu ładującego GC](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span><span class="sxs-lookup"><span data-stu-id="da0a1-382">For more information, see [Standalone GC loader design](https://github.com/dotnet/runtime/blob/master/docs/design/features/standalone-gc-loading.md).</span></span>

| | <span data-ttu-id="da0a1-383">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="da0a1-383">Setting name</span></span> | <span data-ttu-id="da0a1-384">Wartości</span><span class="sxs-lookup"><span data-stu-id="da0a1-384">Values</span></span> | <span data-ttu-id="da0a1-385">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="da0a1-385">Version introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="da0a1-386">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="da0a1-386">**runtimeconfig.json**</span></span> | <span data-ttu-id="da0a1-387">N/D</span><span class="sxs-lookup"><span data-stu-id="da0a1-387">N/A</span></span> | <span data-ttu-id="da0a1-388">N/D</span><span class="sxs-lookup"><span data-stu-id="da0a1-388">N/A</span></span> | <span data-ttu-id="da0a1-389">N/D</span><span class="sxs-lookup"><span data-stu-id="da0a1-389">N/A</span></span> |
| <span data-ttu-id="da0a1-390">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="da0a1-390">**Environment variable**</span></span> | `COMPlus_GCName` | <span data-ttu-id="da0a1-391">*string_path*</span><span class="sxs-lookup"><span data-stu-id="da0a1-391">*string_path*</span></span> | <span data-ttu-id="da0a1-392">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="da0a1-392">.NET Core 2.0</span></span> |
