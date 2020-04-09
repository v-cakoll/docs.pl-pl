---
title: Ustawienia konfiguracji kompilacji
description: Dowiedz się więcej o ustawieniach czasu wykonywania, które konfigurują sposób działania kompilatora JIT dla aplikacji .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: ac51aa13254b2f2b1fdd8d1dd9c52559831a1659
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989119"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="a6f63-103">Opcje konfiguracji w czasie wykonywania kompilacji</span><span class="sxs-lookup"><span data-stu-id="a6f63-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="a6f63-104">Kompilacja warstwowa</span><span class="sxs-lookup"><span data-stu-id="a6f63-104">Tiered compilation</span></span>

- <span data-ttu-id="a6f63-105">Konfiguruje, czy kompilator just-in-time (JIT) używa [kompilacji warstwowej.](../whats-new/dotnet-core-3-0.md#tiered-compilation)</span><span class="sxs-lookup"><span data-stu-id="a6f63-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="a6f63-106">Metody przejścia kompilacji warstwowej za pośrednictwem dwóch warstw:</span><span class="sxs-lookup"><span data-stu-id="a6f63-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="a6f63-107">Pierwsza warstwa generuje kod szybciej[(szybki JIT)](#quick-jit)lub ładuje wstępnie skompilowany kod ([ReadyToRun](#readytorun)).</span><span class="sxs-lookup"><span data-stu-id="a6f63-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="a6f63-108">Druga warstwa generuje zoptymalizowany kod w tle ("optymalizacja JIT").</span><span class="sxs-lookup"><span data-stu-id="a6f63-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="a6f63-109">W .NET Core 3.0 i nowszych kompilacja warstwowa jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="a6f63-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="a6f63-110">W .NET Core 2.1 i 2.2 kompilacja warstwowa jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="a6f63-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="a6f63-111">Aby uzyskać więcej informacji, zobacz [przewodnik kompilacji warstwowej](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="a6f63-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span></span>

| | <span data-ttu-id="a6f63-112">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a6f63-112">Setting name</span></span> | <span data-ttu-id="a6f63-113">Wartości</span><span class="sxs-lookup"><span data-stu-id="a6f63-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a6f63-114">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a6f63-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="a6f63-115">`true`- włączone</span><span class="sxs-lookup"><span data-stu-id="a6f63-115">`true` - enabled</span></span><br/><span data-ttu-id="a6f63-116">`false`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="a6f63-116">`false` - disabled</span></span> |
| <span data-ttu-id="a6f63-117">**Właściwość MSBuild**</span><span class="sxs-lookup"><span data-stu-id="a6f63-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="a6f63-118">`true`- włączone</span><span class="sxs-lookup"><span data-stu-id="a6f63-118">`true` - enabled</span></span><br/><span data-ttu-id="a6f63-119">`false`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="a6f63-119">`false` - disabled</span></span> |
| <span data-ttu-id="a6f63-120">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a6f63-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="a6f63-121">`1`- włączone</span><span class="sxs-lookup"><span data-stu-id="a6f63-121">`1` - enabled</span></span><br/><span data-ttu-id="a6f63-122">`0`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="a6f63-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="a6f63-123">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a6f63-123">Examples</span></span>

<span data-ttu-id="a6f63-124">*runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="a6f63-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="a6f63-125">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="a6f63-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="a6f63-126">Szybki JIT</span><span class="sxs-lookup"><span data-stu-id="a6f63-126">Quick JIT</span></span>

- <span data-ttu-id="a6f63-127">Konfiguruje, czy kompilator JIT używa *szybkiego JIT*.</span><span class="sxs-lookup"><span data-stu-id="a6f63-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="a6f63-128">Dla metod, które nie zawierają pętli i dla których wstępnie skompilowany kod nie jest dostępny, szybkie JIT kompiluje je szybciej, ale bez optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="a6f63-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="a6f63-129">Włączenie szybkiego JIT skracają czas uruchamiania, ale mogą tworzyć kod o obniżonej wydajności.</span><span class="sxs-lookup"><span data-stu-id="a6f63-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="a6f63-130">Na przykład kod może użyć więcej miejsca na stosie, przydzielić więcej pamięci i działać wolniej.</span><span class="sxs-lookup"><span data-stu-id="a6f63-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="a6f63-131">Jeśli szybkie JIT jest wyłączona, ale [kompilacja warstwowa](#tiered-compilation) jest włączona, tylko wstępnie skompilowany kod uczestniczy w kompilacji warstwowej.</span><span class="sxs-lookup"><span data-stu-id="a6f63-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="a6f63-132">Jeśli metoda nie jest wstępnie skompilowana z [ReadyToRun](#readytorun), zachowanie JIT jest takie samo, jak gdyby [kompilacja warstwowa](#tiered-compilation) została wyłączona.</span><span class="sxs-lookup"><span data-stu-id="a6f63-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="a6f63-133">W .NET Core 3.0 lub nowszych, szybkie JIT jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="a6f63-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="a6f63-134">W .NET Core 2.1 i 2.2 szybkie JIT jest domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="a6f63-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="a6f63-135">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a6f63-135">Setting name</span></span> | <span data-ttu-id="a6f63-136">Wartości</span><span class="sxs-lookup"><span data-stu-id="a6f63-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a6f63-137">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a6f63-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="a6f63-138">`true`- włączone</span><span class="sxs-lookup"><span data-stu-id="a6f63-138">`true` - enabled</span></span><br/><span data-ttu-id="a6f63-139">`false`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="a6f63-139">`false` - disabled</span></span> |
| <span data-ttu-id="a6f63-140">**Właściwość MSBuild**</span><span class="sxs-lookup"><span data-stu-id="a6f63-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="a6f63-141">`true`- włączone</span><span class="sxs-lookup"><span data-stu-id="a6f63-141">`true` - enabled</span></span><br/><span data-ttu-id="a6f63-142">`false`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="a6f63-142">`false` - disabled</span></span> |
| <span data-ttu-id="a6f63-143">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a6f63-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="a6f63-144">`1`- włączone</span><span class="sxs-lookup"><span data-stu-id="a6f63-144">`1` - enabled</span></span><br/><span data-ttu-id="a6f63-145">`0`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="a6f63-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="a6f63-146">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a6f63-146">Examples</span></span>

<span data-ttu-id="a6f63-147">*runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="a6f63-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="a6f63-148">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="a6f63-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="a6f63-149">Szybki JIT dla pętli</span><span class="sxs-lookup"><span data-stu-id="a6f63-149">Quick JIT for loops</span></span>

- <span data-ttu-id="a6f63-150">Konfiguruje, czy kompilator JIT używa szybkiego JIT na metodach, które zawierają pętle.</span><span class="sxs-lookup"><span data-stu-id="a6f63-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="a6f63-151">Włączenie szybkiego JIT dla pętli może poprawić wydajność uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="a6f63-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="a6f63-152">Jednak długotrwałe pętle mogą utknąć w mniej zoptymalizowanym kodzie przez długi czas.</span><span class="sxs-lookup"><span data-stu-id="a6f63-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="a6f63-153">Jeśli [szybkie JIT](#quick-jit) jest wyłączone, to ustawienie nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="a6f63-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="a6f63-154">Domyślnie:`false`Wyłączone ( ).</span><span class="sxs-lookup"><span data-stu-id="a6f63-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="a6f63-155">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a6f63-155">Setting name</span></span> | <span data-ttu-id="a6f63-156">Wartości</span><span class="sxs-lookup"><span data-stu-id="a6f63-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a6f63-157">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="a6f63-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="a6f63-158">`false`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="a6f63-158">`false` - disabled</span></span><br/><span data-ttu-id="a6f63-159">`true`- włączone</span><span class="sxs-lookup"><span data-stu-id="a6f63-159">`true` - enabled</span></span> |
| <span data-ttu-id="a6f63-160">**Właściwość MSBuild**</span><span class="sxs-lookup"><span data-stu-id="a6f63-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="a6f63-161">`false`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="a6f63-161">`false` - disabled</span></span><br/><span data-ttu-id="a6f63-162">`true`- włączone</span><span class="sxs-lookup"><span data-stu-id="a6f63-162">`true` - enabled</span></span> |
| <span data-ttu-id="a6f63-163">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a6f63-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="a6f63-164">`0`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="a6f63-164">`0` - disabled</span></span><br/><span data-ttu-id="a6f63-165">`1`- włączone</span><span class="sxs-lookup"><span data-stu-id="a6f63-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="a6f63-166">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a6f63-166">Examples</span></span>

<span data-ttu-id="a6f63-167">*runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="a6f63-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="a6f63-168">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="a6f63-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="a6f63-169">ReadyToRun (ReadyToRun)</span><span class="sxs-lookup"><span data-stu-id="a6f63-169">ReadyToRun</span></span>

- <span data-ttu-id="a6f63-170">Konfiguruje, czy środowisko uruchomieniowe .NET Core używa wstępnie skompilowanego kodu dla obrazów z dostępnymi danymi ReadyToRun.</span><span class="sxs-lookup"><span data-stu-id="a6f63-170">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="a6f63-171">Wyłączenie tej opcji wymusza środowisko uruchomieniowe do kodu struktury kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="a6f63-171">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="a6f63-172">Aby uzyskać więcej informacji, zobacz [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="a6f63-172">For more information, see [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span>
- <span data-ttu-id="a6f63-173">Domyślnie: Włączone`1`( ).</span><span class="sxs-lookup"><span data-stu-id="a6f63-173">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="a6f63-174">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="a6f63-174">Setting name</span></span> | <span data-ttu-id="a6f63-175">Wartości</span><span class="sxs-lookup"><span data-stu-id="a6f63-175">Values</span></span> |
| - | - | - |
| <span data-ttu-id="a6f63-176">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="a6f63-176">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="a6f63-177">`1`- włączone</span><span class="sxs-lookup"><span data-stu-id="a6f63-177">`1` - enabled</span></span><br/><span data-ttu-id="a6f63-178">`0`- niepełnosprawnych</span><span class="sxs-lookup"><span data-stu-id="a6f63-178">`0` - disabled</span></span> |
