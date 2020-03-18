---
title: Ustawienia konfiguracji kompilacji
description: Dowiedz się więcej o ustawieniach czasu wykonywania, które konfigurują działanie kompilatora JIT dla aplikacji .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: adf1f01dba7387b89ee56784e33653d6a132c0e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092892"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="0a19e-103">Opcje konfiguracji w czasie wykonywania kompilacji</span><span class="sxs-lookup"><span data-stu-id="0a19e-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="0a19e-104">Kompilacja warstwowa</span><span class="sxs-lookup"><span data-stu-id="0a19e-104">Tiered compilation</span></span>

- <span data-ttu-id="0a19e-105">Konfiguruje, czy kompilator just-in-time (JIT) używa [kompilacji warstwowej](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="0a19e-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="0a19e-106">Warstwowe metody przejścia kompilacji za pośrednictwem dwóch warstw:</span><span class="sxs-lookup"><span data-stu-id="0a19e-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="0a19e-107">Pierwsza warstwa generuje kod szybciej[(szybkie JIT)](#quick-jit)lub ładuje wstępnie skompilowany kod ([ReadyToRun](#readytorun)).</span><span class="sxs-lookup"><span data-stu-id="0a19e-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="0a19e-108">Druga warstwa generuje zoptymalizowany kod w tle ("optymalizacja JIT").</span><span class="sxs-lookup"><span data-stu-id="0a19e-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="0a19e-109">W .NET Core 3.0 i nowszych kompilacji warstwowej jest włączona domyślnie.</span><span class="sxs-lookup"><span data-stu-id="0a19e-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="0a19e-110">W .NET Core 2.1 i 2.2 kompilacja warstwowa jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="0a19e-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="0a19e-111">Aby uzyskać więcej informacji, zobacz [przewodnik kompilacji warstwowej](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span><span class="sxs-lookup"><span data-stu-id="0a19e-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md).</span></span>

| | <span data-ttu-id="0a19e-112">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="0a19e-112">Setting name</span></span> | <span data-ttu-id="0a19e-113">Wartości</span><span class="sxs-lookup"><span data-stu-id="0a19e-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0a19e-114">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0a19e-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="0a19e-115">`true`- włączona</span><span class="sxs-lookup"><span data-stu-id="0a19e-115">`true` - enabled</span></span><br/><span data-ttu-id="0a19e-116">`false`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="0a19e-116">`false` - disabled</span></span> |
| <span data-ttu-id="0a19e-117">**MSBuild, właściwość**</span><span class="sxs-lookup"><span data-stu-id="0a19e-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="0a19e-118">`true`- włączona</span><span class="sxs-lookup"><span data-stu-id="0a19e-118">`true` - enabled</span></span><br/><span data-ttu-id="0a19e-119">`false`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="0a19e-119">`false` - disabled</span></span> |
| <span data-ttu-id="0a19e-120">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="0a19e-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="0a19e-121">`1`- włączona</span><span class="sxs-lookup"><span data-stu-id="0a19e-121">`1` - enabled</span></span><br/><span data-ttu-id="0a19e-122">`0`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="0a19e-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="0a19e-123">Przykłady</span><span class="sxs-lookup"><span data-stu-id="0a19e-123">Examples</span></span>

<span data-ttu-id="0a19e-124">*plik runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="0a19e-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="0a19e-125">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="0a19e-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="0a19e-126">Szybkie JIT</span><span class="sxs-lookup"><span data-stu-id="0a19e-126">Quick JIT</span></span>

- <span data-ttu-id="0a19e-127">Konfiguruje, czy kompilator JIT używa *szybkiego JIT*.</span><span class="sxs-lookup"><span data-stu-id="0a19e-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="0a19e-128">W przypadku metod, które nie zawierają pętli i dla których wstępnie skompilowany kod nie jest dostępny, szybki JIT kompiluje je szybciej, ale bez optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="0a19e-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="0a19e-129">Włączenie szybkiego JIT skraca czas uruchamiania, ale może generować kod o obniżonych właściwościach wydajności.</span><span class="sxs-lookup"><span data-stu-id="0a19e-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="0a19e-130">Na przykład kod może używać więcej miejsca na stosie, przydzielić więcej pamięci i działać wolniej.</span><span class="sxs-lookup"><span data-stu-id="0a19e-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="0a19e-131">Jeśli szybki JIT jest wyłączony, ale [kompilacja warstwowa](#tiered-compilation) jest włączona, tylko wstępnie skompilowany kod uczestniczy w kompilacji warstwowej.</span><span class="sxs-lookup"><span data-stu-id="0a19e-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="0a19e-132">Jeśli metoda nie jest wstępnie skompilowany z [ReadyToRun](#readytorun), zachowanie JIT jest taka sama, jak gdyby [warstwowe kompilacji](#tiered-compilation) zostały wyłączone.</span><span class="sxs-lookup"><span data-stu-id="0a19e-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="0a19e-133">W .NET Core 3.0 i nowszych, szybkie JIT jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="0a19e-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="0a19e-134">W programach .NET Core 2.1 i 2.2 szybkie jit jest domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="0a19e-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="0a19e-135">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="0a19e-135">Setting name</span></span> | <span data-ttu-id="0a19e-136">Wartości</span><span class="sxs-lookup"><span data-stu-id="0a19e-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0a19e-137">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0a19e-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="0a19e-138">`true`- włączona</span><span class="sxs-lookup"><span data-stu-id="0a19e-138">`true` - enabled</span></span><br/><span data-ttu-id="0a19e-139">`false`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="0a19e-139">`false` - disabled</span></span> |
| <span data-ttu-id="0a19e-140">**MSBuild, właściwość**</span><span class="sxs-lookup"><span data-stu-id="0a19e-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="0a19e-141">`true`- włączona</span><span class="sxs-lookup"><span data-stu-id="0a19e-141">`true` - enabled</span></span><br/><span data-ttu-id="0a19e-142">`false`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="0a19e-142">`false` - disabled</span></span> |
| <span data-ttu-id="0a19e-143">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="0a19e-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="0a19e-144">`1`- włączona</span><span class="sxs-lookup"><span data-stu-id="0a19e-144">`1` - enabled</span></span><br/><span data-ttu-id="0a19e-145">`0`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="0a19e-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="0a19e-146">Przykłady</span><span class="sxs-lookup"><span data-stu-id="0a19e-146">Examples</span></span>

<span data-ttu-id="0a19e-147">*plik runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="0a19e-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="0a19e-148">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="0a19e-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="0a19e-149">Szybki JIT do pętli</span><span class="sxs-lookup"><span data-stu-id="0a19e-149">Quick JIT for loops</span></span>

- <span data-ttu-id="0a19e-150">Konfiguruje, czy kompilator JIT używa szybkiego JIT na metody, które zawierają pętle.</span><span class="sxs-lookup"><span data-stu-id="0a19e-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="0a19e-151">Włączenie szybkiego JIT dla pętli może zwiększyć wydajność uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="0a19e-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="0a19e-152">Jednak długotrwałe pętle mogą utknąć w mniej zoptymalizowanym kodzie przez długi czas.</span><span class="sxs-lookup"><span data-stu-id="0a19e-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="0a19e-153">Jeśli [szybkie JIT](#quick-jit) jest wyłączone, to ustawienie nie ma wpływu.</span><span class="sxs-lookup"><span data-stu-id="0a19e-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="0a19e-154">Domyślnie: Wyłączone`false`( ).</span><span class="sxs-lookup"><span data-stu-id="0a19e-154">Default: Disabled (`false`).</span></span>

| | <span data-ttu-id="0a19e-155">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="0a19e-155">Setting name</span></span> | <span data-ttu-id="0a19e-156">Wartości</span><span class="sxs-lookup"><span data-stu-id="0a19e-156">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0a19e-157">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="0a19e-157">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="0a19e-158">`false`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="0a19e-158">`false` - disabled</span></span><br/><span data-ttu-id="0a19e-159">`true`- włączona</span><span class="sxs-lookup"><span data-stu-id="0a19e-159">`true` - enabled</span></span> |
| <span data-ttu-id="0a19e-160">**MSBuild, właściwość**</span><span class="sxs-lookup"><span data-stu-id="0a19e-160">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="0a19e-161">`false`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="0a19e-161">`false` - disabled</span></span><br/><span data-ttu-id="0a19e-162">`true`- włączona</span><span class="sxs-lookup"><span data-stu-id="0a19e-162">`true` - enabled</span></span> |
| <span data-ttu-id="0a19e-163">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="0a19e-163">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="0a19e-164">`0`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="0a19e-164">`0` - disabled</span></span><br/><span data-ttu-id="0a19e-165">`1`- włączona</span><span class="sxs-lookup"><span data-stu-id="0a19e-165">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="0a19e-166">Przykłady</span><span class="sxs-lookup"><span data-stu-id="0a19e-166">Examples</span></span>

<span data-ttu-id="0a19e-167">*plik runtimeconfig.json:*</span><span class="sxs-lookup"><span data-stu-id="0a19e-167">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="0a19e-168">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="0a19e-168">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>false</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="0a19e-169">Readytorun (Gotowy)</span><span class="sxs-lookup"><span data-stu-id="0a19e-169">ReadyToRun</span></span>

- <span data-ttu-id="0a19e-170">Konfiguruje, czy program .NET Core używa wstępnie skompilowanego kodu dla obrazów z dostępnymi danymi ReadyToRun.</span><span class="sxs-lookup"><span data-stu-id="0a19e-170">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="0a19e-171">Wyłączenie tej opcji wymusza, że program runtime jest kodem frameworkkompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="0a19e-171">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="0a19e-172">Aby uzyskać więcej informacji, zobacz [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="0a19e-172">For more information, see [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span>
- <span data-ttu-id="0a19e-173">Domyślnie: Włączone`1`( ).</span><span class="sxs-lookup"><span data-stu-id="0a19e-173">Default: Enabled (`1`).</span></span>

| | <span data-ttu-id="0a19e-174">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="0a19e-174">Setting name</span></span> | <span data-ttu-id="0a19e-175">Wartości</span><span class="sxs-lookup"><span data-stu-id="0a19e-175">Values</span></span> |
| - | - | - |
| <span data-ttu-id="0a19e-176">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="0a19e-176">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="0a19e-177">`1`- włączona</span><span class="sxs-lookup"><span data-stu-id="0a19e-177">`1` - enabled</span></span><br/><span data-ttu-id="0a19e-178">`0`- wyłączone</span><span class="sxs-lookup"><span data-stu-id="0a19e-178">`0` - disabled</span></span> |
