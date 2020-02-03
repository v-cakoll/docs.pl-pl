---
title: Ustawienia konfiguracji kompilacji
description: Informacje o ustawieniach czasu wykonywania, które konfigurują sposób działania kompilatora JIT dla aplikacji platformy .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: 0dab3b7b7726a232cf293e338308cf898b370759
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733540"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="d9490-103">Opcje konfiguracji czasu wykonywania dla kompilacji</span><span class="sxs-lookup"><span data-stu-id="d9490-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="d9490-104">Kompilacja warstwowa</span><span class="sxs-lookup"><span data-stu-id="d9490-104">Tiered compilation</span></span>

- <span data-ttu-id="d9490-105">Określa, czy kompilator just-in-Time (JIT) używa [kompilacji warstwowej](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="d9490-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="d9490-106">Warstwy z przechodzeniem warstwowym w ramach dwóch warstw:</span><span class="sxs-lookup"><span data-stu-id="d9490-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="d9490-107">Pierwsza warstwa generuje kod szybciej (szybko[JIT](#quick-jit)) lub ładuje wstępnie skompilowany kod ([ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images)).</span><span class="sxs-lookup"><span data-stu-id="d9490-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images)).</span></span>
  - <span data-ttu-id="d9490-108">Druga warstwa generuje zoptymalizowany kod w tle ("Optymalizacja JIT").</span><span class="sxs-lookup"><span data-stu-id="d9490-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="d9490-109">W programie .NET Core 3,0 i nowszych kompilacja warstwowa jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="d9490-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="d9490-110">W przypadku oprogramowania .NET Core 2,1 i 2,2 kompilacja warstwowa jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="d9490-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="d9490-111">Aby uzyskać więcej informacji, zobacz [Przewodnik po kompilacji warstwowej](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span><span class="sxs-lookup"><span data-stu-id="d9490-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span></span>

| | <span data-ttu-id="d9490-112">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="d9490-112">Setting name</span></span> | <span data-ttu-id="d9490-113">Wartości</span><span class="sxs-lookup"><span data-stu-id="d9490-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="d9490-114">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="d9490-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="d9490-115">`true` — włączono</span><span class="sxs-lookup"><span data-stu-id="d9490-115">`true` - enabled</span></span><br/><span data-ttu-id="d9490-116">`false` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="d9490-116">`false` - disabled</span></span> |
| <span data-ttu-id="d9490-117">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="d9490-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="d9490-118">`true` — włączono</span><span class="sxs-lookup"><span data-stu-id="d9490-118">`true` - enabled</span></span><br/><span data-ttu-id="d9490-119">`false` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="d9490-119">`false` - disabled</span></span> |
| <span data-ttu-id="d9490-120">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="d9490-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="d9490-121">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="d9490-121">`1` - enabled</span></span><br/><span data-ttu-id="d9490-122">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="d9490-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="d9490-123">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d9490-123">Examples</span></span>

<span data-ttu-id="d9490-124">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="d9490-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="d9490-125">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="d9490-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="d9490-126">Szybka JIT</span><span class="sxs-lookup"><span data-stu-id="d9490-126">Quick JIT</span></span>

- <span data-ttu-id="d9490-127">Określa, czy kompilator JIT używa *szybkiej JIT*.</span><span class="sxs-lookup"><span data-stu-id="d9490-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="d9490-128">W przypadku metod, które nie zawierają pętli i dla których wstępnie skompilowany kod jest niedostępny, szybka JIT kompiluje je szybciej, ale bez optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="d9490-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="d9490-129">Włączenie szybkiej JIT skraca czas uruchamiania, ale może generować kod o obniżonej wydajności.</span><span class="sxs-lookup"><span data-stu-id="d9490-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="d9490-130">Na przykład kod może używać większej ilości miejsca, przydzielać więcej pamięci i działać wolniej.</span><span class="sxs-lookup"><span data-stu-id="d9490-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="d9490-131">Jeśli szybka JIT jest wyłączona, ale [kompilacja warstwowa](#tiered-compilation) jest włączona, tylko wstępnie skompilowany kod uczestniczy w kompilacji warstwowej.</span><span class="sxs-lookup"><span data-stu-id="d9490-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="d9490-132">Jeśli metoda nie jest wstępnie skompilowana za pomocą [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images), zachowanie JIT jest takie samo, jakby była wyłączona [kompilacja warstwowa](#tiered-compilation) .</span><span class="sxs-lookup"><span data-stu-id="d9490-132">If a method is not pre-compiled with [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="d9490-133">W przypadku platformy .NET Core 3,0 i nowszych tryb szybkiej JIT jest domyślnie włączony.</span><span class="sxs-lookup"><span data-stu-id="d9490-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="d9490-134">W przypadku programów .NET Core 2,1 i 2,2 Szybka metoda JIT jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="d9490-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="d9490-135">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="d9490-135">Setting name</span></span> | <span data-ttu-id="d9490-136">Wartości</span><span class="sxs-lookup"><span data-stu-id="d9490-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="d9490-137">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="d9490-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="d9490-138">`true` — włączono</span><span class="sxs-lookup"><span data-stu-id="d9490-138">`true` - enabled</span></span><br/><span data-ttu-id="d9490-139">`false` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="d9490-139">`false` - disabled</span></span> |
| <span data-ttu-id="d9490-140">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="d9490-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="d9490-141">`true` — włączono</span><span class="sxs-lookup"><span data-stu-id="d9490-141">`true` - enabled</span></span><br/><span data-ttu-id="d9490-142">`false` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="d9490-142">`false` - disabled</span></span> |
| <span data-ttu-id="d9490-143">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="d9490-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="d9490-144">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="d9490-144">`1` - enabled</span></span><br/><span data-ttu-id="d9490-145">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="d9490-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="d9490-146">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d9490-146">Examples</span></span>

<span data-ttu-id="d9490-147">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="d9490-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="d9490-148">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="d9490-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="d9490-149">Szybka JIT dla pętli</span><span class="sxs-lookup"><span data-stu-id="d9490-149">Quick JIT for loops</span></span>

- <span data-ttu-id="d9490-150">Określa, czy kompilator JIT używa szybkiej JIT metod, które zawierają pętle.</span><span class="sxs-lookup"><span data-stu-id="d9490-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="d9490-151">Włączenie szybkiej JIT dla pętli może poprawić wydajność uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="d9490-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="d9490-152">Jednak długotrwałe pętle mogą być zablokowane w niezoptymalizowanym kodzie przez długi czas.</span><span class="sxs-lookup"><span data-stu-id="d9490-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="d9490-153">Jeśli [szybka JIT](#quick-jit) jest wyłączona, to ustawienie nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="d9490-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="d9490-154">Domyślnie: wyłączone (`false`).</span><span class="sxs-lookup"><span data-stu-id="d9490-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="d9490-155">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="d9490-155">Setting name</span></span> | <span data-ttu-id="d9490-156">Wartości</span><span class="sxs-lookup"><span data-stu-id="d9490-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="d9490-157">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="d9490-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="d9490-158">`false` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="d9490-158">`false` - disabled</span></span><br/><span data-ttu-id="d9490-159">`true` — włączono</span><span class="sxs-lookup"><span data-stu-id="d9490-159">`true` - enabled</span></span> |
| <span data-ttu-id="d9490-160">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="d9490-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="d9490-161">`false` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="d9490-161">`false` - disabled</span></span><br/><span data-ttu-id="d9490-162">`true` — włączono</span><span class="sxs-lookup"><span data-stu-id="d9490-162">`true` - enabled</span></span> |
| <span data-ttu-id="d9490-163">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="d9490-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="d9490-164">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="d9490-164">`0` - disabled</span></span><br/><span data-ttu-id="d9490-165">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="d9490-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="d9490-166">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d9490-166">Examples</span></span>

<span data-ttu-id="d9490-167">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="d9490-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="d9490-168">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="d9490-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```
