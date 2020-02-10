---
title: Ustawienia konfiguracji kompilacji
description: Informacje o ustawieniach czasu wykonywania, które konfigurują sposób działania kompilatora JIT dla aplikacji platformy .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: adf1f01dba7387b89ee56784e33653d6a132c0e3
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092892"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="265c9-103">Opcje konfiguracji czasu wykonywania dla kompilacji</span><span class="sxs-lookup"><span data-stu-id="265c9-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="265c9-104">Kompilacja warstwowa</span><span class="sxs-lookup"><span data-stu-id="265c9-104">Tiered compilation</span></span>

- <span data-ttu-id="265c9-105">Określa, czy kompilator just-in-Time (JIT) używa [kompilacji warstwowej](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="265c9-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="265c9-106">Warstwy z przechodzeniem warstwowym w ramach dwóch warstw:</span><span class="sxs-lookup"><span data-stu-id="265c9-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="265c9-107">Pierwsza warstwa generuje kod szybciej (szybko[JIT](#quick-jit)) lub ładuje wstępnie skompilowany kod ([ReadyToRun](#readytorun)).</span><span class="sxs-lookup"><span data-stu-id="265c9-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="265c9-108">Druga warstwa generuje zoptymalizowany kod w tle ("Optymalizacja JIT").</span><span class="sxs-lookup"><span data-stu-id="265c9-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="265c9-109">W programie .NET Core 3,0 i nowszych kompilacja warstwowa jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="265c9-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="265c9-110">W przypadku oprogramowania .NET Core 2,1 i 2,2 kompilacja warstwowa jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="265c9-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="265c9-111">Aby uzyskać więcej informacji, zobacz [Przewodnik po kompilacji warstwowej](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span><span class="sxs-lookup"><span data-stu-id="265c9-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span></span>

| | <span data-ttu-id="265c9-112">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="265c9-112">Setting name</span></span> | <span data-ttu-id="265c9-113">Wartości</span><span class="sxs-lookup"><span data-stu-id="265c9-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="265c9-114">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="265c9-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="265c9-115">`true` — włączono</span><span class="sxs-lookup"><span data-stu-id="265c9-115">`true` - enabled</span></span><br/><span data-ttu-id="265c9-116">`false` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="265c9-116">`false` - disabled</span></span> |
| <span data-ttu-id="265c9-117">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="265c9-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="265c9-118">`true` — włączono</span><span class="sxs-lookup"><span data-stu-id="265c9-118">`true` - enabled</span></span><br/><span data-ttu-id="265c9-119">`false` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="265c9-119">`false` - disabled</span></span> |
| <span data-ttu-id="265c9-120">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="265c9-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="265c9-121">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="265c9-121">`1` - enabled</span></span><br/><span data-ttu-id="265c9-122">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="265c9-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="265c9-123">Przykłady</span><span class="sxs-lookup"><span data-stu-id="265c9-123">Examples</span></span>

<span data-ttu-id="265c9-124">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="265c9-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="265c9-125">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="265c9-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="265c9-126">Szybka JIT</span><span class="sxs-lookup"><span data-stu-id="265c9-126">Quick JIT</span></span>

- <span data-ttu-id="265c9-127">Określa, czy kompilator JIT używa *szybkiej JIT*.</span><span class="sxs-lookup"><span data-stu-id="265c9-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="265c9-128">W przypadku metod, które nie zawierają pętli i dla których wstępnie skompilowany kod jest niedostępny, szybka JIT kompiluje je szybciej, ale bez optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="265c9-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="265c9-129">Włączenie szybkiej JIT skraca czas uruchamiania, ale może generować kod o obniżonej wydajności.</span><span class="sxs-lookup"><span data-stu-id="265c9-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="265c9-130">Na przykład kod może używać większej ilości miejsca, przydzielać więcej pamięci i działać wolniej.</span><span class="sxs-lookup"><span data-stu-id="265c9-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="265c9-131">Jeśli szybka JIT jest wyłączona, ale [kompilacja warstwowa](#tiered-compilation) jest włączona, tylko wstępnie skompilowany kod uczestniczy w kompilacji warstwowej.</span><span class="sxs-lookup"><span data-stu-id="265c9-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="265c9-132">Jeśli metoda nie jest wstępnie skompilowana za pomocą [ReadyToRun](#readytorun), zachowanie JIT jest takie samo, jakby była wyłączona [kompilacja warstwowa](#tiered-compilation) .</span><span class="sxs-lookup"><span data-stu-id="265c9-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="265c9-133">W przypadku platformy .NET Core 3,0 i nowszych tryb szybkiej JIT jest domyślnie włączony.</span><span class="sxs-lookup"><span data-stu-id="265c9-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="265c9-134">W przypadku programów .NET Core 2,1 i 2,2 Szybka metoda JIT jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="265c9-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="265c9-135">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="265c9-135">Setting name</span></span> | <span data-ttu-id="265c9-136">Wartości</span><span class="sxs-lookup"><span data-stu-id="265c9-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="265c9-137">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="265c9-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="265c9-138">`true` — włączono</span><span class="sxs-lookup"><span data-stu-id="265c9-138">`true` - enabled</span></span><br/><span data-ttu-id="265c9-139">`false` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="265c9-139">`false` - disabled</span></span> |
| <span data-ttu-id="265c9-140">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="265c9-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="265c9-141">`true` — włączono</span><span class="sxs-lookup"><span data-stu-id="265c9-141">`true` - enabled</span></span><br/><span data-ttu-id="265c9-142">`false` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="265c9-142">`false` - disabled</span></span> |
| <span data-ttu-id="265c9-143">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="265c9-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="265c9-144">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="265c9-144">`1` - enabled</span></span><br/><span data-ttu-id="265c9-145">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="265c9-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="265c9-146">Przykłady</span><span class="sxs-lookup"><span data-stu-id="265c9-146">Examples</span></span>

<span data-ttu-id="265c9-147">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="265c9-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="265c9-148">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="265c9-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="265c9-149">Szybka JIT dla pętli</span><span class="sxs-lookup"><span data-stu-id="265c9-149">Quick JIT for loops</span></span>

- <span data-ttu-id="265c9-150">Określa, czy kompilator JIT używa szybkiej JIT metod, które zawierają pętle.</span><span class="sxs-lookup"><span data-stu-id="265c9-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="265c9-151">Włączenie szybkiej JIT dla pętli może poprawić wydajność uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="265c9-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="265c9-152">Jednak długotrwałe pętle mogą być zablokowane w niezoptymalizowanym kodzie przez długi czas.</span><span class="sxs-lookup"><span data-stu-id="265c9-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="265c9-153">Jeśli [szybka JIT](#quick-jit) jest wyłączona, to ustawienie nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="265c9-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="265c9-154">Domyślnie: wyłączone (`false`).</span><span class="sxs-lookup"><span data-stu-id="265c9-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="265c9-155">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="265c9-155">Setting name</span></span> | <span data-ttu-id="265c9-156">Wartości</span><span class="sxs-lookup"><span data-stu-id="265c9-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="265c9-157">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="265c9-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="265c9-158">`false` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="265c9-158">`false` - disabled</span></span><br/><span data-ttu-id="265c9-159">`true` — włączono</span><span class="sxs-lookup"><span data-stu-id="265c9-159">`true` - enabled</span></span> |
| <span data-ttu-id="265c9-160">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="265c9-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="265c9-161">`false` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="265c9-161">`false` - disabled</span></span><br/><span data-ttu-id="265c9-162">`true` — włączono</span><span class="sxs-lookup"><span data-stu-id="265c9-162">`true` - enabled</span></span> |
| <span data-ttu-id="265c9-163">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="265c9-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="265c9-164">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="265c9-164">`0` - disabled</span></span><br/><span data-ttu-id="265c9-165">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="265c9-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="265c9-166">Przykłady</span><span class="sxs-lookup"><span data-stu-id="265c9-166">Examples</span></span>

<span data-ttu-id="265c9-167">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="265c9-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="265c9-168">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="265c9-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="265c9-169">ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="265c9-169">ReadyToRun</span></span>

- <span data-ttu-id="265c9-170">Określa, czy środowisko uruchomieniowe programu .NET Core używa wstępnie skompilowanego kodu dla obrazów z dostępnymi danymi ReadyToRun.</span><span class="sxs-lookup"><span data-stu-id="265c9-170">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="265c9-171">Wyłączenie tej opcji zmusza środowisko uruchomieniowe do kompilowania kodu struktury JIT.</span><span class="sxs-lookup"><span data-stu-id="265c9-171">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="265c9-172">Aby uzyskać więcej informacji, zobacz [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="265c9-172">For more information, see [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span>
- <span data-ttu-id="265c9-173">Wartość domyślna: włączone (`1`).</span><span class="sxs-lookup"><span data-stu-id="265c9-173">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="265c9-174">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="265c9-174">Setting name</span></span> | <span data-ttu-id="265c9-175">Wartości</span><span class="sxs-lookup"><span data-stu-id="265c9-175">Values</span></span> |
| - | - | - |
| <span data-ttu-id="265c9-176">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="265c9-176">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="265c9-177">`1` — włączono</span><span class="sxs-lookup"><span data-stu-id="265c9-177">`1` - enabled</span></span><br/><span data-ttu-id="265c9-178">`0` — wyłączone</span><span class="sxs-lookup"><span data-stu-id="265c9-178">`0` - disabled</span></span> |
