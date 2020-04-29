---
title: Właściwości programu MSBuild dla Microsoft. NET. Sdk
description: Odwołanie do właściwości programu MSBuild, które są zrozumiałe dla zestaw .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 105b7d67ea24515ea88481cb4a4fe42d2a03cfd0
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82506794"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="e49e1-103">Właściwości programu MSBuild dla projektów zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="e49e1-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="e49e1-104">Na tej stronie opisano właściwości programu MSBuild służące do konfigurowania projektów platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e49e1-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="e49e1-105">Ta strona jest w toku i nie wyświetla wszystkich przydatnych właściwości programu MSBuild dla zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e49e1-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="e49e1-106">Aby zapoznać się z listą typowych właściwości programu MSBuild, zobacz [typowe właściwości programu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="e49e1-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="e49e1-107">Właściwości struktury</span><span class="sxs-lookup"><span data-stu-id="e49e1-107">Framework properties</span></span>

- [<span data-ttu-id="e49e1-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="e49e1-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="e49e1-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="e49e1-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="e49e1-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="e49e1-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="e49e1-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="e49e1-111">TargetFramework</span></span>

<span data-ttu-id="e49e1-112">`TargetFramework` Właściwość określa wersję platformy docelowej dla aplikacji, która niejawnie odwołuje się do [pakietu](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="e49e1-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="e49e1-113">Aby zapoznać się z listą prawidłowych monikerów platformy docelowej, zobacz [platformę docelową w projektach w stylu zestawu SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="e49e1-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="e49e1-114">Aby uzyskać więcej informacji, zobacz [Platformy docelowe w projektach w stylu zestawu SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e49e1-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="e49e1-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="e49e1-115">TargetFrameworks</span></span>

<span data-ttu-id="e49e1-116">Użyj właściwości `TargetFrameworks` , jeśli chcesz, aby aplikacja była przeznaczona dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="e49e1-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="e49e1-117">Aby zapoznać się z listą prawidłowych monikerów platformy docelowej, zobacz [platformę docelową w projektach w stylu zestawu SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="e49e1-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="e49e1-118">Ta właściwość jest ignorowana `TargetFramework` , jeśli określono (pojedynczo).</span><span class="sxs-lookup"><span data-stu-id="e49e1-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="e49e1-119">Aby uzyskać więcej informacji, zobacz [Platformy docelowe w projektach w stylu zestawu SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e49e1-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="e49e1-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="e49e1-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="e49e1-121">Ta właściwość ma zastosowanie tylko do projektów `netstandard1.x`korzystających z programu.</span><span class="sxs-lookup"><span data-stu-id="e49e1-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="e49e1-122">Nie dotyczy to projektów, które używają `netstandard2.x`.</span><span class="sxs-lookup"><span data-stu-id="e49e1-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="e49e1-123">Użyj `NetStandardImplicitPackageVersion` właściwości, aby określić wersję platformy, która jest starsza niż wersja [pakietu](../packages.md#metapackages) .</span><span class="sxs-lookup"><span data-stu-id="e49e1-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="e49e1-124">Plik projektu w poniższym przykładzie docelowym `netstandard1.3` , ale używa wersji 1.6.0. `NETStandard.Library`</span><span class="sxs-lookup"><span data-stu-id="e49e1-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="e49e1-125">Właściwości publikowania</span><span class="sxs-lookup"><span data-stu-id="e49e1-125">Publish properties</span></span>

- [<span data-ttu-id="e49e1-126">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="e49e1-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="e49e1-127">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="e49e1-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="e49e1-128">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="e49e1-128">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="e49e1-129">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="e49e1-129">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="e49e1-130">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="e49e1-130">RuntimeIdentifier</span></span>

<span data-ttu-id="e49e1-131">`RuntimeIdentifier` Właściwość umożliwia określenie pojedynczego [identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu.</span><span class="sxs-lookup"><span data-stu-id="e49e1-131">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="e49e1-132">Identyfikator RID umożliwia publikowanie samodzielnego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="e49e1-132">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="e49e1-133">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="e49e1-133">RuntimeIdentifiers</span></span>

<span data-ttu-id="e49e1-134">`RuntimeIdentifiers` Właściwość pozwala określić rozdzielaną średnikami listę [identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu.</span><span class="sxs-lookup"><span data-stu-id="e49e1-134">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="e49e1-135">Użyj tej właściwości, jeśli chcesz opublikować dla wielu środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="e49e1-135">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="e49e1-136">`RuntimeIdentifiers`jest używany podczas przywracania, aby upewnić się, że odpowiednie zasoby znajdują się na wykresie.</span><span class="sxs-lookup"><span data-stu-id="e49e1-136">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="e49e1-137">`RuntimeIdentifier`(pojedyncze) może zapewnić szybsze kompilacje, gdy wymagane jest tylko jedno środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="e49e1-137">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="e49e1-138">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="e49e1-138">TrimmerRootAssembly</span></span>

<span data-ttu-id="e49e1-139">`TrimmerRootAssembly` Element umożliwia wykluczenie zestawu z [*przycinania*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="e49e1-139">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="e49e1-140">Przycinanie jest procesem usuwania nieużywanych części środowiska uruchomieniowego z spakowanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e49e1-140">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="e49e1-141">W niektórych przypadkach przycinanie może niepoprawnie usunąć wymagane odwołania.</span><span class="sxs-lookup"><span data-stu-id="e49e1-141">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="e49e1-142">Poniższy kod XML wyklucza `System.Security` zestaw z przycinania.</span><span class="sxs-lookup"><span data-stu-id="e49e1-142">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="e49e1-143">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="e49e1-143">UseAppHost</span></span>

<span data-ttu-id="e49e1-144">`UseAppHost` Właściwość została wprowadzona w wersji 2.1.400 zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e49e1-144">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="e49e1-145">Określa, czy dla wdrożenia jest tworzony natywny plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="e49e1-145">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="e49e1-146">Natywny plik wykonywalny jest wymagany w przypadku wdrożeń samodzielnych.</span><span class="sxs-lookup"><span data-stu-id="e49e1-146">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="e49e1-147">W programie .NET Core 3,0 i jego nowszych wersjach domyślnie tworzony jest plik wykonywalny zależny od platformy.</span><span class="sxs-lookup"><span data-stu-id="e49e1-147">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="e49e1-148">Ustaw `UseAppHost` właściwość na `false` , aby wyłączyć generowanie pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="e49e1-148">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="e49e1-149">Aby uzyskać więcej informacji na temat wdrażania, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="e49e1-149">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="e49e1-150">Kompiluj właściwości</span><span class="sxs-lookup"><span data-stu-id="e49e1-150">Compile properties</span></span>

- [<span data-ttu-id="e49e1-151">LangVersion</span><span class="sxs-lookup"><span data-stu-id="e49e1-151">LangVersion</span></span>](#langversion)

### <a name="langversion"></a><span data-ttu-id="e49e1-152">LangVersion</span><span class="sxs-lookup"><span data-stu-id="e49e1-152">LangVersion</span></span>

<span data-ttu-id="e49e1-153">`LangVersion` Właściwość umożliwia określenie konkretnej wersji języka programowania.</span><span class="sxs-lookup"><span data-stu-id="e49e1-153">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="e49e1-154">Na przykład jeśli chcesz uzyskać dostęp do funkcji wersji zapoznawczej języka `LangVersion` C# `preview`, ustaw wartość.</span><span class="sxs-lookup"><span data-stu-id="e49e1-154">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="e49e1-155">Aby uzyskać więcej informacji, zobacz [wersja języka C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="e49e1-155">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="e49e1-156">Właściwości konfiguracji czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="e49e1-156">Run-time configuration properties</span></span>

<span data-ttu-id="e49e1-157">Niektóre zachowania w czasie wykonywania można skonfigurować, określając właściwości programu MSBuild w pliku projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e49e1-157">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="e49e1-158">Aby uzyskać informacje na temat innych sposobów konfigurowania zachowania w czasie wykonywania, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="e49e1-158">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="e49e1-159">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="e49e1-159">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="e49e1-160">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="e49e1-160">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="e49e1-161">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="e49e1-161">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="e49e1-162">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="e49e1-162">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="e49e1-163">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="e49e1-163">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="e49e1-164">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="e49e1-164">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="e49e1-165">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="e49e1-165">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="e49e1-166">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="e49e1-166">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="e49e1-167">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="e49e1-167">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="e49e1-168">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="e49e1-168">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="e49e1-169">Właściwość `ConcurrentGarbageCollection` określa, czy jest włączone [wyrzucanie elementów bezużytecznych w tle](../../standard/garbage-collection/background-gc.md) .</span><span class="sxs-lookup"><span data-stu-id="e49e1-169">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="e49e1-170">Ustaw wartość na `false` , aby wyłączyć wyrzucanie elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="e49e1-170">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="e49e1-171">Aby uzyskać więcej informacji, zobacz [System. GC. współbieżne/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span><span class="sxs-lookup"><span data-stu-id="e49e1-171">For more information, see [System.GC.Concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="invariantglobalization"></a><span data-ttu-id="e49e1-172">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="e49e1-172">InvariantGlobalization</span></span>

<span data-ttu-id="e49e1-173">`InvariantGlobalization` Właściwość określa, czy aplikacja jest uruchamiana w trybie *globalizacji-niezmiennym* , co oznacza, że nie ma dostępu do danych specyficznych dla kultury.</span><span class="sxs-lookup"><span data-stu-id="e49e1-173">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="e49e1-174">Ustaw wartość tak, `true` aby była uruchamiana w trybie niezmiennym globalizacji.</span><span class="sxs-lookup"><span data-stu-id="e49e1-174">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="e49e1-175">Aby uzyskać więcej informacji, zobacz [tryb niezmienny](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="e49e1-175">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>
</Project>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="e49e1-176">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="e49e1-176">RetainVMGarbageCollection</span></span>

<span data-ttu-id="e49e1-177">`RetainVMGarbageCollection` Właściwość konfiguruje moduł wyrzucania elementów bezużytecznych w celu umieszczenia usuniętych segmentów pamięci na liście gotowości do użycia w przyszłości lub zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="e49e1-177">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="e49e1-178">Ustawienie wartości `true` informującej Moduł wyrzucania elementów bezużytecznych w celu umieszczenia segmentów na liście gotowości.</span><span class="sxs-lookup"><span data-stu-id="e49e1-178">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="e49e1-179">Aby uzyskać więcej informacji, zobacz [System. GC. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span><span class="sxs-lookup"><span data-stu-id="e49e1-179">For more information, see [System.GC.RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="e49e1-180">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="e49e1-180">ServerGarbageCollection</span></span>

<span data-ttu-id="e49e1-181">Właściwość `ServerGarbageCollection` określa, czy aplikacja używa [wyrzucania elementów bezużytecznych stacji roboczej lub odzyskiwania pamięci serwera](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="e49e1-181">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="e49e1-182">Ustaw wartość `true` na, aby użyć wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="e49e1-182">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="e49e1-183">Aby uzyskać więcej informacji, zobacz [System. GC. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span><span class="sxs-lookup"><span data-stu-id="e49e1-183">For more information, see [System.GC.Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="e49e1-184">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="e49e1-184">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="e49e1-185">`ThreadPoolMaxThreads` Właściwość określa maksymalną liczbę wątków dla puli wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="e49e1-185">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="e49e1-186">Aby uzyskać więcej informacji, zobacz [maksymalne wątki](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="e49e1-186">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="e49e1-187">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="e49e1-187">ThreadPoolMinThreads</span></span>

<span data-ttu-id="e49e1-188">`ThreadPoolMinThreads` Właściwość konfiguruje minimalną liczbę wątków dla puli wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="e49e1-188">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="e49e1-189">Aby uzyskać więcej informacji, zobacz [minimalna liczba wątków](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="e49e1-189">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilation"></a><span data-ttu-id="e49e1-190">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="e49e1-190">TieredCompilation</span></span>

<span data-ttu-id="e49e1-191">`TieredCompilation` Właściwość określa, czy kompilator just in Time (JIT) używa [kompilacji warstwowej](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="e49e1-191">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="e49e1-192">Ustaw wartość `false` na, aby wyłączyć kompilację warstwową.</span><span class="sxs-lookup"><span data-stu-id="e49e1-192">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="e49e1-193">Aby uzyskać więcej informacji, zobacz temat [kompilacja warstwowa](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="e49e1-193">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="e49e1-194">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="e49e1-194">TieredCompilationQuickJit</span></span>

<span data-ttu-id="e49e1-195">`TieredCompilationQuickJit` Właściwość określa, czy kompilator JIT używa szybkiej JIT.</span><span class="sxs-lookup"><span data-stu-id="e49e1-195">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="e49e1-196">Ustaw wartość na `false` , aby wyłączyć szybkie JIT.</span><span class="sxs-lookup"><span data-stu-id="e49e1-196">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="e49e1-197">Aby uzyskać więcej informacji, zobacz [szybkie JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="e49e1-197">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="e49e1-198">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="e49e1-198">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="e49e1-199">`TieredCompilationQuickJitForLoops` Właściwość określa, czy kompilator JIT używa szybkiej JIT metod, które zawierają pętle.</span><span class="sxs-lookup"><span data-stu-id="e49e1-199">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="e49e1-200">Ustaw wartość `true` na, aby włączyć funkcję szybkiego JIT dla metod, które zawierają pętle.</span><span class="sxs-lookup"><span data-stu-id="e49e1-200">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="e49e1-201">Aby uzyskać więcej informacji, zobacz [szybkie JIT dla pętli](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="e49e1-201">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>
</Project>
```

## <a name="nuget-packages"></a><span data-ttu-id="e49e1-202">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="e49e1-202">NuGet packages</span></span>

- [<span data-ttu-id="e49e1-203">PackageReference</span><span class="sxs-lookup"><span data-stu-id="e49e1-203">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="e49e1-204">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="e49e1-204">AssetTargetFallback</span></span>](#assettargetfallback)

### <a name="packagereference"></a><span data-ttu-id="e49e1-205">PackageReference</span><span class="sxs-lookup"><span data-stu-id="e49e1-205">PackageReference</span></span>

<span data-ttu-id="e49e1-206">`PackageReference` Element pozwala określić zależność NuGet.</span><span class="sxs-lookup"><span data-stu-id="e49e1-206">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="e49e1-207">Na przykład możesz chcieć odwołać się do pojedynczego pakietu zamiast [pakietu](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="e49e1-207">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="e49e1-208">Ten `Include` ATRYBUT określa identyfikator pakietu.</span><span class="sxs-lookup"><span data-stu-id="e49e1-208">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="e49e1-209">Fragment pliku projektu w poniższym przykładzie odwołuje się do pakietu [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="e49e1-209">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="e49e1-210">Aby uzyskać więcej informacji, zobacz [odwołania do pakietów w plikach projektu](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="e49e1-210">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="assettargetfallback"></a><span data-ttu-id="e49e1-211">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="e49e1-211">AssetTargetFallback</span></span>

<span data-ttu-id="e49e1-212">`AssetTargetFallback` Właściwość pozwala określić dodatkowe zgodne wersje platformy dla projektów, do których odwołuje się projekt, oraz pakietów NuGet, które są używane w projekcie.</span><span class="sxs-lookup"><span data-stu-id="e49e1-212">The `AssetTargetFallback` property lets you specify additional compatible framework versions for projects that your project references and NuGet packages that your project consumes.</span></span> <span data-ttu-id="e49e1-213">Na przykład, jeśli określisz zależność pakietu przy użyciu `PackageReference` programu `TargetFramework`, ale ten pakiet nie zawiera zasobów, które są zgodne z projektem, `AssetTargetFallback` właściwość jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="e49e1-213">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="e49e1-214">Zgodność przywoływanego pakietu jest ponownie sprawdzana przy użyciu każdej platformy docelowej określonej w `AssetTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="e49e1-214">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="e49e1-215">Można ustawić `AssetTargetFallback` właściwość na co najmniej jedną [docelową wersję platformy](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="e49e1-215">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a><span data-ttu-id="e49e1-216">Elementy docelowe pakietów i przywracania</span><span class="sxs-lookup"><span data-stu-id="e49e1-216">Pack and restore targets</span></span>

<span data-ttu-id="e49e1-217">Program MSBuild 15,1 `pack` wprowadził `restore` i ma cele tworzenia i przywracania pakietów NuGet w ramach kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e49e1-217">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="e49e1-218">Aby uzyskać informacje na temat właściwości programu MSBuild dla tych obiektów `PackageTargetFallback`docelowych, w tym, zobacz [pakiet NuGet i przywracanie jako elementy docelowe programu MSBuild](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="e49e1-218">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="e49e1-219">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e49e1-219">See also</span></span>

- [<span data-ttu-id="e49e1-220">Odwołanie do schematu programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="e49e1-220">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="e49e1-221">Typowe właściwości programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="e49e1-221">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="e49e1-222">Właściwości programu MSBuild dla pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="e49e1-222">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="e49e1-223">Właściwości programu MSBuild do przywracania NuGet</span><span class="sxs-lookup"><span data-stu-id="e49e1-223">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="e49e1-224">Dostosuj kompilację</span><span class="sxs-lookup"><span data-stu-id="e49e1-224">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
