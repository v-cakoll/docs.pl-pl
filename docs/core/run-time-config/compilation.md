---
title: Ustawienia konfiguracji kompilacji
description: Informacje o ustawieniach czasu wykonywania, które konfigurują sposób działania kompilatora JIT dla aplikacji platformy .NET Core.
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: cfcf9b5fc8d11a4ae35ab9b152f32133cd6930bf
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762009"
---
# <a name="run-time-configuration-options-for-compilation"></a><span data-ttu-id="92546-103">Opcje konfiguracji czasu wykonywania dla kompilacji</span><span class="sxs-lookup"><span data-stu-id="92546-103">Run-time configuration options for compilation</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="92546-104">Kompilacja warstwowa</span><span class="sxs-lookup"><span data-stu-id="92546-104">Tiered compilation</span></span>

- <span data-ttu-id="92546-105">Określa, czy kompilator just-in-Time (JIT) używa [kompilacji warstwowej](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="92546-105">Configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="92546-106">Warstwy z przechodzeniem warstwowym w ramach dwóch warstw:</span><span class="sxs-lookup"><span data-stu-id="92546-106">Tiered compilation transitions methods through two tiers:</span></span>
  - <span data-ttu-id="92546-107">Pierwsza warstwa generuje kod szybciej (szybko[JIT](#quick-jit)) lub ładuje wstępnie skompilowany kod ([ReadyToRun](#readytorun)).</span><span class="sxs-lookup"><span data-stu-id="92546-107">The first tier generates code more quickly ([quick JIT](#quick-jit)) or loads pre-compiled code ([ReadyToRun](#readytorun)).</span></span>
  - <span data-ttu-id="92546-108">Druga warstwa generuje zoptymalizowany kod w tle ("Optymalizacja JIT").</span><span class="sxs-lookup"><span data-stu-id="92546-108">The second tier generates optimized code in the background ("optimizing JIT").</span></span>
- <span data-ttu-id="92546-109">W programie .NET Core 3,0 i nowszych kompilacja warstwowa jest domyślnie włączona.</span><span class="sxs-lookup"><span data-stu-id="92546-109">In .NET Core 3.0 and later, tiered compilation is enabled by default.</span></span>
- <span data-ttu-id="92546-110">W przypadku oprogramowania .NET Core 2,1 i 2,2 kompilacja warstwowa jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="92546-110">In .NET Core 2.1 and 2.2, tiered compilation is disabled by default.</span></span>
- <span data-ttu-id="92546-111">Aby uzyskać więcej informacji, zobacz [Przewodnik po kompilacji warstwowej](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span><span class="sxs-lookup"><span data-stu-id="92546-111">For more information, see the [Tiered compilation guide](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md).</span></span>

| | <span data-ttu-id="92546-112">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="92546-112">Setting name</span></span> | <span data-ttu-id="92546-113">Wartości</span><span class="sxs-lookup"><span data-stu-id="92546-113">Values</span></span> |
| - | - | - |
| <span data-ttu-id="92546-114">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="92546-114">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation` | <span data-ttu-id="92546-115">`true`-włączone</span><span class="sxs-lookup"><span data-stu-id="92546-115">`true` - enabled</span></span><br/><span data-ttu-id="92546-116">`false`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="92546-116">`false` - disabled</span></span> |
| <span data-ttu-id="92546-117">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="92546-117">**MSBuild property**</span></span> | `TieredCompilation` | <span data-ttu-id="92546-118">`true`-włączone</span><span class="sxs-lookup"><span data-stu-id="92546-118">`true` - enabled</span></span><br/><span data-ttu-id="92546-119">`false`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="92546-119">`false` - disabled</span></span> |
| <span data-ttu-id="92546-120">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="92546-120">**Environment variable**</span></span> | `COMPlus_TieredCompilation` | <span data-ttu-id="92546-121">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="92546-121">`1` - enabled</span></span><br/><span data-ttu-id="92546-122">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="92546-122">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="92546-123">Przykłady</span><span class="sxs-lookup"><span data-stu-id="92546-123">Examples</span></span>

<span data-ttu-id="92546-124">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="92546-124">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation": false
      }
   }
}
```

<span data-ttu-id="92546-125">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="92546-125">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit"></a><span data-ttu-id="92546-126">Szybka JIT</span><span class="sxs-lookup"><span data-stu-id="92546-126">Quick JIT</span></span>

- <span data-ttu-id="92546-127">Określa, czy kompilator JIT używa *szybkiej JIT*.</span><span class="sxs-lookup"><span data-stu-id="92546-127">Configures whether the JIT compiler uses *quick JIT*.</span></span> <span data-ttu-id="92546-128">W przypadku metod, które nie zawierają pętli i dla których wstępnie skompilowany kod jest niedostępny, szybka JIT kompiluje je szybciej, ale bez optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="92546-128">For methods that don't contain loops and for which pre-compiled code is not available, quick JIT compiles them more quickly but without optimizations.</span></span>
- <span data-ttu-id="92546-129">Włączenie szybkiej JIT skraca czas uruchamiania, ale może generować kod o obniżonej wydajności.</span><span class="sxs-lookup"><span data-stu-id="92546-129">Enabling quick JIT decreases startup time but can produce code with degraded performance characteristics.</span></span> <span data-ttu-id="92546-130">Na przykład kod może używać większej ilości miejsca, przydzielać więcej pamięci i działać wolniej.</span><span class="sxs-lookup"><span data-stu-id="92546-130">For example, the code may use more stack space, allocate more memory, and run slower.</span></span>
- <span data-ttu-id="92546-131">Jeśli szybka JIT jest wyłączona, ale [kompilacja warstwowa](#tiered-compilation) jest włączona, tylko wstępnie skompilowany kod uczestniczy w kompilacji warstwowej.</span><span class="sxs-lookup"><span data-stu-id="92546-131">If quick JIT is disabled but [tiered compilation](#tiered-compilation) is enabled, only pre-compiled code participates in tiered compilation.</span></span> <span data-ttu-id="92546-132">Jeśli metoda nie jest wstępnie skompilowana za pomocą [ReadyToRun](#readytorun), zachowanie JIT jest takie samo, jakby była wyłączona [kompilacja warstwowa](#tiered-compilation) .</span><span class="sxs-lookup"><span data-stu-id="92546-132">If a method is not pre-compiled with [ReadyToRun](#readytorun), the JIT behavior is the same as if [tiered compilation](#tiered-compilation) were disabled.</span></span>
- <span data-ttu-id="92546-133">W przypadku platformy .NET Core 3,0 i nowszych tryb szybkiej JIT jest domyślnie włączony.</span><span class="sxs-lookup"><span data-stu-id="92546-133">In .NET Core 3.0 and later, quick JIT is enabled by default.</span></span>
- <span data-ttu-id="92546-134">W przypadku programów .NET Core 2,1 i 2,2 Szybka metoda JIT jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="92546-134">In .NET Core 2.1 and 2.2, quick JIT is disabled by default.</span></span>

| | <span data-ttu-id="92546-135">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="92546-135">Setting name</span></span> | <span data-ttu-id="92546-136">Wartości</span><span class="sxs-lookup"><span data-stu-id="92546-136">Values</span></span> |
| - | - | - |
| <span data-ttu-id="92546-137">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="92546-137">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJit` | <span data-ttu-id="92546-138">`true`-włączone</span><span class="sxs-lookup"><span data-stu-id="92546-138">`true` - enabled</span></span><br/><span data-ttu-id="92546-139">`false`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="92546-139">`false` - disabled</span></span> |
| <span data-ttu-id="92546-140">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="92546-140">**MSBuild property**</span></span> | `TieredCompilationQuickJit` | <span data-ttu-id="92546-141">`true`-włączone</span><span class="sxs-lookup"><span data-stu-id="92546-141">`true` - enabled</span></span><br/><span data-ttu-id="92546-142">`false`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="92546-142">`false` - disabled</span></span> |
| <span data-ttu-id="92546-143">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="92546-143">**Environment variable**</span></span> | `COMPlus_TC_QuickJit` | <span data-ttu-id="92546-144">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="92546-144">`1` - enabled</span></span><br/><span data-ttu-id="92546-145">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="92546-145">`0` - disabled</span></span> |

### <a name="examples"></a><span data-ttu-id="92546-146">Przykłady</span><span class="sxs-lookup"><span data-stu-id="92546-146">Examples</span></span>

<span data-ttu-id="92546-147">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="92546-147">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJit": false
      }
   }
}
```

<span data-ttu-id="92546-148">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="92546-148">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>

</Project>
```

## <a name="quick-jit-for-loops"></a><span data-ttu-id="92546-149">Szybka JIT dla pętli</span><span class="sxs-lookup"><span data-stu-id="92546-149">Quick JIT for loops</span></span>

- <span data-ttu-id="92546-150">Określa, czy kompilator JIT używa szybkiej JIT metod, które zawierają pętle.</span><span class="sxs-lookup"><span data-stu-id="92546-150">Configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span>
- <span data-ttu-id="92546-151">Włączenie szybkiej JIT dla pętli może poprawić wydajność uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="92546-151">Enabling quick JIT for loops may improve startup performance.</span></span> <span data-ttu-id="92546-152">Jednak długotrwałe pętle mogą być zablokowane w niezoptymalizowanym kodzie przez długi czas.</span><span class="sxs-lookup"><span data-stu-id="92546-152">However, long-running loops can get stuck in less-optimized code for long periods.</span></span>
- <span data-ttu-id="92546-153">Jeśli [szybka JIT](#quick-jit) jest wyłączona, to ustawienie nie ma żadnego wpływu.</span><span class="sxs-lookup"><span data-stu-id="92546-153">If [quick JIT](#quick-jit) is disabled, this setting has no effect.</span></span>
- <span data-ttu-id="92546-154">W przypadku pominięcia tego ustawienia szybka JIT nie jest używana dla metod, które zawierają pętle.</span><span class="sxs-lookup"><span data-stu-id="92546-154">If you omit this setting, quick JIT is not used for methods that contain loops.</span></span> <span data-ttu-id="92546-155">Jest to równoznaczne z ustawieniem wartości `false` .</span><span class="sxs-lookup"><span data-stu-id="92546-155">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="92546-156">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="92546-156">Setting name</span></span> | <span data-ttu-id="92546-157">Wartości</span><span class="sxs-lookup"><span data-stu-id="92546-157">Values</span></span> |
| - | - | - |
| <span data-ttu-id="92546-158">**runtimeconfig. JSON**</span><span class="sxs-lookup"><span data-stu-id="92546-158">**runtimeconfig.json**</span></span> | `System.Runtime.TieredCompilation.QuickJitForLoops` | <span data-ttu-id="92546-159">`false`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="92546-159">`false` - disabled</span></span><br/><span data-ttu-id="92546-160">`true`-włączone</span><span class="sxs-lookup"><span data-stu-id="92546-160">`true` - enabled</span></span> |
| <span data-ttu-id="92546-161">**Właściwość programu MSBuild**</span><span class="sxs-lookup"><span data-stu-id="92546-161">**MSBuild property**</span></span> | `TieredCompilationQuickJitForLoops` | <span data-ttu-id="92546-162">`false`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="92546-162">`false` - disabled</span></span><br/><span data-ttu-id="92546-163">`true`-włączone</span><span class="sxs-lookup"><span data-stu-id="92546-163">`true` - enabled</span></span> |
| <span data-ttu-id="92546-164">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="92546-164">**Environment variable**</span></span> | `COMPlus_TC_QuickJitForLoops` | <span data-ttu-id="92546-165">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="92546-165">`0` - disabled</span></span><br/><span data-ttu-id="92546-166">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="92546-166">`1` - enabled</span></span> |

### <a name="examples"></a><span data-ttu-id="92546-167">Przykłady</span><span class="sxs-lookup"><span data-stu-id="92546-167">Examples</span></span>

<span data-ttu-id="92546-168">plik *runtimeconfig. JSON* :</span><span class="sxs-lookup"><span data-stu-id="92546-168">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Runtime.TieredCompilation.QuickJitForLoops": false
      }
   }
}
```

<span data-ttu-id="92546-169">Plik projektu:</span><span class="sxs-lookup"><span data-stu-id="92546-169">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>

</Project>
```

## <a name="readytorun"></a><span data-ttu-id="92546-170">ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="92546-170">ReadyToRun</span></span>

- <span data-ttu-id="92546-171">Określa, czy środowisko uruchomieniowe programu .NET Core używa wstępnie skompilowanego kodu dla obrazów z dostępnymi danymi ReadyToRun.</span><span class="sxs-lookup"><span data-stu-id="92546-171">Configures whether the .NET Core runtime uses pre-compiled code for images with available ReadyToRun data.</span></span> <span data-ttu-id="92546-172">Wyłączenie tej opcji zmusza środowisko uruchomieniowe do kompilowania kodu struktury JIT.</span><span class="sxs-lookup"><span data-stu-id="92546-172">Disabling this option forces the runtime to JIT-compile framework code.</span></span>
- <span data-ttu-id="92546-173">Aby uzyskać więcej informacji, zobacz [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="92546-173">For more information, see [ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span>
- <span data-ttu-id="92546-174">W przypadku pominięcia tego ustawienia platforma .NET będzie używać danych ReadyToRun, gdy jest ona dostępna.</span><span class="sxs-lookup"><span data-stu-id="92546-174">If you omit this setting, .NET uses ReadyToRun data when it's available.</span></span> <span data-ttu-id="92546-175">Jest to równoznaczne z ustawieniem wartości `1` .</span><span class="sxs-lookup"><span data-stu-id="92546-175">This is equivalent to setting the value to `1`.</span></span>

| | <span data-ttu-id="92546-176">Nazwa ustawienia</span><span class="sxs-lookup"><span data-stu-id="92546-176">Setting name</span></span> | <span data-ttu-id="92546-177">Wartości</span><span class="sxs-lookup"><span data-stu-id="92546-177">Values</span></span> |
| - | - | - |
| <span data-ttu-id="92546-178">**Zmienna środowiskowa**</span><span class="sxs-lookup"><span data-stu-id="92546-178">**Environment variable**</span></span> | `COMPlus_ReadyToRun` | <span data-ttu-id="92546-179">`1`-włączone</span><span class="sxs-lookup"><span data-stu-id="92546-179">`1` - enabled</span></span><br/><span data-ttu-id="92546-180">`0`-wyłączone</span><span class="sxs-lookup"><span data-stu-id="92546-180">`0` - disabled</span></span> |
