---
title: Właściwości programu MSBuild dla Microsoft. NET. Sdk
description: Odwołanie do właściwości programu MSBuild, które są zrozumiałe dla zestaw .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 800ff59310d8437d7f770bf20a5bdf37714f8515
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795576"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="0460b-103">Właściwości programu MSBuild dla projektów zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="0460b-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="0460b-104">Na tej stronie opisano właściwości programu MSBuild służące do konfigurowania projektów platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0460b-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span> <span data-ttu-id="0460b-105">Można określić *metadane* dla każdej właściwości jako elementy podrzędne właściwości.</span><span class="sxs-lookup"><span data-stu-id="0460b-105">You can specify *metadata* for each property as child elements of the property.</span></span>

> [!NOTE]
> <span data-ttu-id="0460b-106">Ta strona jest w toku i nie wyświetla wszystkich przydatnych właściwości programu MSBuild dla zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="0460b-106">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="0460b-107">Aby zapoznać się z listą typowych właściwości programu MSBuild, zobacz [typowe właściwości programu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="0460b-107">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="0460b-108">Właściwości struktury</span><span class="sxs-lookup"><span data-stu-id="0460b-108">Framework properties</span></span>

- [<span data-ttu-id="0460b-109">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="0460b-109">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="0460b-110">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="0460b-110">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="0460b-111">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="0460b-111">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="0460b-112">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="0460b-112">TargetFramework</span></span>

<span data-ttu-id="0460b-113">`TargetFramework` Właściwość określa wersję platformy docelowej dla aplikacji, która niejawnie odwołuje się do [pakietu](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="0460b-113">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="0460b-114">Aby zapoznać się z listą prawidłowych monikerów platformy docelowej, zobacz [platformę docelową w projektach w stylu zestawu SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="0460b-114">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="0460b-115">Aby uzyskać więcej informacji, zobacz [Platformy docelowe w projektach w stylu zestawu SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0460b-115">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="0460b-116">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="0460b-116">TargetFrameworks</span></span>

<span data-ttu-id="0460b-117">Użyj właściwości `TargetFrameworks` , jeśli chcesz, aby aplikacja była przeznaczona dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="0460b-117">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="0460b-118">Aby zapoznać się z listą prawidłowych monikerów platformy docelowej, zobacz [platformę docelową w projektach w stylu zestawu SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="0460b-118">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="0460b-119">Ta właściwość jest ignorowana `TargetFramework` , jeśli określono (pojedynczo).</span><span class="sxs-lookup"><span data-stu-id="0460b-119">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
</PropertyGroup>
```

<span data-ttu-id="0460b-120">Aby uzyskać więcej informacji, zobacz [Platformy docelowe w projektach w stylu zestawu SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0460b-120">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="0460b-121">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="0460b-121">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="0460b-122">Ta właściwość ma zastosowanie tylko do projektów `netstandard1.x`korzystających z programu.</span><span class="sxs-lookup"><span data-stu-id="0460b-122">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="0460b-123">Nie dotyczy to projektów, które używają `netstandard2.x`.</span><span class="sxs-lookup"><span data-stu-id="0460b-123">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="0460b-124">Użyj `NetStandardImplicitPackageVersion` właściwości, aby określić wersję platformy, która jest starsza niż wersja [pakietu](../packages.md#metapackages) .</span><span class="sxs-lookup"><span data-stu-id="0460b-124">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="0460b-125">Plik projektu w poniższym przykładzie docelowym `netstandard1.3` , ale używa wersji 1.6.0. `NETStandard.Library`</span><span class="sxs-lookup"><span data-stu-id="0460b-125">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netstandard1.3</TargetFramework>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

## <a name="package-properties"></a><span data-ttu-id="0460b-126">Właściwości pakietu</span><span class="sxs-lookup"><span data-stu-id="0460b-126">Package properties</span></span>

<span data-ttu-id="0460b-127">Można określić właściwości, takie jak `PackageId`, `PackageVersion` `PackageIcon`,, `Title`i `Description` , aby opisać pakiet, który zostanie utworzony na podstawie projektu.</span><span class="sxs-lookup"><span data-stu-id="0460b-127">You can specify properties such as `PackageId`, `PackageVersion`, `PackageIcon`, `Title`, and `Description` to describe the package that gets created from your project.</span></span> <span data-ttu-id="0460b-128">Aby uzyskać informacje o tych i innych właściwościach, zobacz [pakiet Target](/nuget/reference/msbuild-targets#pack-target).</span><span class="sxs-lookup"><span data-stu-id="0460b-128">For information about these and other properties, see [pack target](/nuget/reference/msbuild-targets#pack-target).</span></span>

```xml
<PropertyGroup>
  ...
  <PackageId>ClassLibDotNetStandard</PackageId>
  <Version>1.0.0</Version>
  <Authors>John Doe</Authors>
  <Company>Contoso</Company>
</PropertyGroup>
```

## <a name="publish-properties"></a><span data-ttu-id="0460b-129">Właściwości publikowania</span><span class="sxs-lookup"><span data-stu-id="0460b-129">Publish properties</span></span>

- [<span data-ttu-id="0460b-130">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="0460b-130">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="0460b-131">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="0460b-131">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="0460b-132">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="0460b-132">TrimmerRootAssembly</span></span>](#trimmerrootassembly)
- [<span data-ttu-id="0460b-133">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="0460b-133">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="0460b-134">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="0460b-134">RuntimeIdentifier</span></span>

<span data-ttu-id="0460b-135">`RuntimeIdentifier` Właściwość umożliwia określenie pojedynczego [identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu.</span><span class="sxs-lookup"><span data-stu-id="0460b-135">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="0460b-136">Identyfikator RID umożliwia publikowanie samodzielnego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="0460b-136">The RID enables publishing a self-contained deployment.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
</PropertyGroup>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="0460b-137">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="0460b-137">RuntimeIdentifiers</span></span>

<span data-ttu-id="0460b-138">`RuntimeIdentifiers` Właściwość pozwala określić rozdzielaną średnikami listę [identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu.</span><span class="sxs-lookup"><span data-stu-id="0460b-138">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="0460b-139">Użyj tej właściwości, jeśli chcesz opublikować dla wielu środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="0460b-139">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="0460b-140">`RuntimeIdentifiers`jest używany podczas przywracania, aby upewnić się, że odpowiednie zasoby znajdują się na wykresie.</span><span class="sxs-lookup"><span data-stu-id="0460b-140">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="0460b-141">`RuntimeIdentifier`(pojedyncze) może zapewnić szybsze kompilacje, gdy wymagane jest tylko jedno środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="0460b-141">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="trimmerrootassembly"></a><span data-ttu-id="0460b-142">TrimmerRootAssembly</span><span class="sxs-lookup"><span data-stu-id="0460b-142">TrimmerRootAssembly</span></span>

<span data-ttu-id="0460b-143">`TrimmerRootAssembly` Element umożliwia wykluczenie zestawu z [*przycinania*](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="0460b-143">The `TrimmerRootAssembly` item lets you exclude an assembly from [*trimming*](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="0460b-144">Przycinanie jest procesem usuwania nieużywanych części środowiska uruchomieniowego z spakowanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0460b-144">Trimming is the process of removing unused parts of the runtime from a packaged application.</span></span> <span data-ttu-id="0460b-145">W niektórych przypadkach przycinanie może niepoprawnie usunąć wymagane odwołania.</span><span class="sxs-lookup"><span data-stu-id="0460b-145">In some cases, trimming might incorrectly remove required references.</span></span>

<span data-ttu-id="0460b-146">Poniższy kod XML wyklucza `System.Security` zestaw z przycinania.</span><span class="sxs-lookup"><span data-stu-id="0460b-146">The following XML excludes the `System.Security` assembly from trimming.</span></span>

```xml
<ItemGroup>
  <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="useapphost"></a><span data-ttu-id="0460b-147">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="0460b-147">UseAppHost</span></span>

<span data-ttu-id="0460b-148">`UseAppHost` Właściwość została wprowadzona w wersji 2.1.400 zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="0460b-148">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="0460b-149">Określa, czy dla wdrożenia jest tworzony natywny plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="0460b-149">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="0460b-150">Natywny plik wykonywalny jest wymagany w przypadku wdrożeń samodzielnych.</span><span class="sxs-lookup"><span data-stu-id="0460b-150">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="0460b-151">W programie .NET Core 3,0 i jego nowszych wersjach domyślnie tworzony jest plik wykonywalny zależny od platformy.</span><span class="sxs-lookup"><span data-stu-id="0460b-151">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="0460b-152">Ustaw `UseAppHost` właściwość na `false` , aby wyłączyć generowanie pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="0460b-152">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<PropertyGroup>
  <UseAppHost>false</UseAppHost>
</PropertyGroup>
```

<span data-ttu-id="0460b-153">Aby uzyskać więcej informacji na temat wdrażania, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="0460b-153">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="0460b-154">Kompiluj właściwości</span><span class="sxs-lookup"><span data-stu-id="0460b-154">Compile properties</span></span>

- [<span data-ttu-id="0460b-155">LangVersion</span><span class="sxs-lookup"><span data-stu-id="0460b-155">LangVersion</span></span>](#langversion)

### <a name="langversion"></a><span data-ttu-id="0460b-156">LangVersion</span><span class="sxs-lookup"><span data-stu-id="0460b-156">LangVersion</span></span>

<span data-ttu-id="0460b-157">`LangVersion` Właściwość umożliwia określenie konkretnej wersji języka programowania.</span><span class="sxs-lookup"><span data-stu-id="0460b-157">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="0460b-158">Na przykład jeśli chcesz uzyskać dostęp do funkcji wersji zapoznawczej języka `LangVersion` C# `preview`, ustaw wartość.</span><span class="sxs-lookup"><span data-stu-id="0460b-158">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<PropertyGroup>
  <LangVersion>preview</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="0460b-159">Aby uzyskać więcej informacji, zobacz [wersja języka C#](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="0460b-159">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="run-time-configuration-properties"></a><span data-ttu-id="0460b-160">Właściwości konfiguracji czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="0460b-160">Run-time configuration properties</span></span>

<span data-ttu-id="0460b-161">Niektóre zachowania w czasie wykonywania można skonfigurować, określając właściwości programu MSBuild w pliku projektu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0460b-161">You can configure some run-time behaviors by specifying MSBuild properties in the project file of the app.</span></span> <span data-ttu-id="0460b-162">Aby uzyskać informacje na temat innych sposobów konfigurowania zachowania w czasie wykonywania, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md).</span><span class="sxs-lookup"><span data-stu-id="0460b-162">For information about other ways of configuring run-time behavior, see [.NET Core run-time configuration settings](../run-time-config/index.md).</span></span>

- [<span data-ttu-id="0460b-163">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="0460b-163">ConcurrentGarbageCollection</span></span>](#concurrentgarbagecollection)
- [<span data-ttu-id="0460b-164">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="0460b-164">InvariantGlobalization</span></span>](#invariantglobalization)
- [<span data-ttu-id="0460b-165">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="0460b-165">RetainVMGarbageCollection</span></span>](#retainvmgarbagecollection)
- [<span data-ttu-id="0460b-166">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="0460b-166">ServerGarbageCollection</span></span>](#servergarbagecollection)
- [<span data-ttu-id="0460b-167">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="0460b-167">ThreadPoolMaxThreads</span></span>](#threadpoolmaxthreads)
- [<span data-ttu-id="0460b-168">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="0460b-168">ThreadPoolMinThreads</span></span>](#threadpoolminthreads)
- [<span data-ttu-id="0460b-169">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="0460b-169">TieredCompilation</span></span>](#tieredcompilation)
- [<span data-ttu-id="0460b-170">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="0460b-170">TieredCompilationQuickJit</span></span>](#tieredcompilationquickjit)
- [<span data-ttu-id="0460b-171">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="0460b-171">TieredCompilationQuickJitForLoops</span></span>](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a><span data-ttu-id="0460b-172">ConcurrentGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="0460b-172">ConcurrentGarbageCollection</span></span>

<span data-ttu-id="0460b-173">Właściwość `ConcurrentGarbageCollection` określa, czy jest włączone [wyrzucanie elementów bezużytecznych w tle](../../standard/garbage-collection/background-gc.md) .</span><span class="sxs-lookup"><span data-stu-id="0460b-173">The `ConcurrentGarbageCollection` property configures whether [background (concurrent) garbage collection](../../standard/garbage-collection/background-gc.md) is enabled.</span></span> <span data-ttu-id="0460b-174">Ustaw wartość na `false` , aby wyłączyć wyrzucanie elementów bezużytecznych w tle.</span><span class="sxs-lookup"><span data-stu-id="0460b-174">Set the value to `false` to disable background garbage collection.</span></span> <span data-ttu-id="0460b-175">Aby uzyskać więcej informacji, zobacz [System. GC. współbieżne/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span><span class="sxs-lookup"><span data-stu-id="0460b-175">For more information, see [System.GC.Concurrent/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).</span></span>

```xml
<PropertyGroup>
  <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
</PropertyGroup>
```

### <a name="invariantglobalization"></a><span data-ttu-id="0460b-176">InvariantGlobalization</span><span class="sxs-lookup"><span data-stu-id="0460b-176">InvariantGlobalization</span></span>

<span data-ttu-id="0460b-177">`InvariantGlobalization` Właściwość określa, czy aplikacja jest uruchamiana w trybie *globalizacji-niezmiennym* , co oznacza, że nie ma dostępu do danych specyficznych dla kultury.</span><span class="sxs-lookup"><span data-stu-id="0460b-177">The `InvariantGlobalization` property configures whether the app runs in *globalization-invariant* mode, which means it doesn't have access to culture-specific data.</span></span> <span data-ttu-id="0460b-178">Ustaw wartość tak, `true` aby była uruchamiana w trybie niezmiennym globalizacji.</span><span class="sxs-lookup"><span data-stu-id="0460b-178">Set the value to `true` to run in globalization-invariant mode.</span></span> <span data-ttu-id="0460b-179">Aby uzyskać więcej informacji, zobacz [tryb niezmienny](../run-time-config/globalization.md#invariant-mode).</span><span class="sxs-lookup"><span data-stu-id="0460b-179">For more information, see [Invariant mode](../run-time-config/globalization.md#invariant-mode).</span></span>

```xml
<PropertyGroup>
  <InvariantGlobalization>true</InvariantGlobalization>
</PropertyGroup>
```

### <a name="retainvmgarbagecollection"></a><span data-ttu-id="0460b-180">RetainVMGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="0460b-180">RetainVMGarbageCollection</span></span>

<span data-ttu-id="0460b-181">`RetainVMGarbageCollection` Właściwość konfiguruje moduł wyrzucania elementów bezużytecznych w celu umieszczenia usuniętych segmentów pamięci na liście gotowości do użycia w przyszłości lub zwolnienia.</span><span class="sxs-lookup"><span data-stu-id="0460b-181">The `RetainVMGarbageCollection` property configures the garbage collector to put deleted memory segments on a standby list for future use or release them.</span></span> <span data-ttu-id="0460b-182">Ustawienie wartości `true` informującej Moduł wyrzucania elementów bezużytecznych w celu umieszczenia segmentów na liście gotowości.</span><span class="sxs-lookup"><span data-stu-id="0460b-182">Setting the value to `true` tells the garbage collector to put the segments on a standby list.</span></span> <span data-ttu-id="0460b-183">Aby uzyskać więcej informacji, zobacz [System. GC. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span><span class="sxs-lookup"><span data-stu-id="0460b-183">For more information, see [System.GC.RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).</span></span>

```xml
<PropertyGroup>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
</PropertyGroup>
```

### <a name="servergarbagecollection"></a><span data-ttu-id="0460b-184">ServerGarbageCollection</span><span class="sxs-lookup"><span data-stu-id="0460b-184">ServerGarbageCollection</span></span>

<span data-ttu-id="0460b-185">Właściwość `ServerGarbageCollection` określa, czy aplikacja używa [wyrzucania elementów bezużytecznych stacji roboczej lub odzyskiwania pamięci serwera](../../standard/garbage-collection/workstation-server-gc.md).</span><span class="sxs-lookup"><span data-stu-id="0460b-185">The `ServerGarbageCollection` property configures whether the application uses [workstation garbage collection or server garbage collection](../../standard/garbage-collection/workstation-server-gc.md).</span></span> <span data-ttu-id="0460b-186">Ustaw wartość `true` na, aby użyć wyrzucania elementów bezużytecznych serwera.</span><span class="sxs-lookup"><span data-stu-id="0460b-186">Set the value to `true` to use server garbage collection.</span></span> <span data-ttu-id="0460b-187">Aby uzyskać więcej informacji, zobacz [System. GC. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span><span class="sxs-lookup"><span data-stu-id="0460b-187">For more information, see [System.GC.Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

### <a name="threadpoolmaxthreads"></a><span data-ttu-id="0460b-188">ThreadPoolMaxThreads</span><span class="sxs-lookup"><span data-stu-id="0460b-188">ThreadPoolMaxThreads</span></span>

<span data-ttu-id="0460b-189">`ThreadPoolMaxThreads` Właściwość określa maksymalną liczbę wątków dla puli wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="0460b-189">The `ThreadPoolMaxThreads` property configures the maximum number of threads for the worker thread pool.</span></span> <span data-ttu-id="0460b-190">Aby uzyskać więcej informacji, zobacz [maksymalne wątki](../run-time-config/threading.md#maximum-threads).</span><span class="sxs-lookup"><span data-stu-id="0460b-190">For more information, see [Maximum threads](../run-time-config/threading.md#maximum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
</PropertyGroup>
```

### <a name="threadpoolminthreads"></a><span data-ttu-id="0460b-191">ThreadPoolMinThreads</span><span class="sxs-lookup"><span data-stu-id="0460b-191">ThreadPoolMinThreads</span></span>

<span data-ttu-id="0460b-192">`ThreadPoolMinThreads` Właściwość konfiguruje minimalną liczbę wątków dla puli wątków roboczych.</span><span class="sxs-lookup"><span data-stu-id="0460b-192">The `ThreadPoolMinThreads` property configures the minimum number of threads for the worker thread pool.</span></span> <span data-ttu-id="0460b-193">Aby uzyskać więcej informacji, zobacz [minimalna liczba wątków](../run-time-config/threading.md#minimum-threads).</span><span class="sxs-lookup"><span data-stu-id="0460b-193">For more information, see [Minimum threads](../run-time-config/threading.md#minimum-threads).</span></span>

```xml
<PropertyGroup>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
</PropertyGroup>
```

### <a name="tieredcompilation"></a><span data-ttu-id="0460b-194">TieredCompilation</span><span class="sxs-lookup"><span data-stu-id="0460b-194">TieredCompilation</span></span>

<span data-ttu-id="0460b-195">`TieredCompilation` Właściwość określa, czy kompilator just in Time (JIT) używa [kompilacji warstwowej](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="0460b-195">The `TieredCompilation` property configures whether the just-in-time (JIT) compiler uses [tiered compilation](../whats-new/dotnet-core-3-0.md#tiered-compilation).</span></span> <span data-ttu-id="0460b-196">Ustaw wartość `false` na, aby wyłączyć kompilację warstwową.</span><span class="sxs-lookup"><span data-stu-id="0460b-196">Set the value to `false` to disable tiered compilation.</span></span> <span data-ttu-id="0460b-197">Aby uzyskać więcej informacji, zobacz temat [kompilacja warstwowa](../run-time-config/compilation.md#tiered-compilation).</span><span class="sxs-lookup"><span data-stu-id="0460b-197">For more information, see [Tiered compilation](../run-time-config/compilation.md#tiered-compilation).</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

### <a name="tieredcompilationquickjit"></a><span data-ttu-id="0460b-198">TieredCompilationQuickJit</span><span class="sxs-lookup"><span data-stu-id="0460b-198">TieredCompilationQuickJit</span></span>

<span data-ttu-id="0460b-199">`TieredCompilationQuickJit` Właściwość określa, czy kompilator JIT używa szybkiej JIT.</span><span class="sxs-lookup"><span data-stu-id="0460b-199">The `TieredCompilationQuickJit` property configures whether the JIT compiler uses quick JIT.</span></span> <span data-ttu-id="0460b-200">Ustaw wartość na `false` , aby wyłączyć szybkie JIT.</span><span class="sxs-lookup"><span data-stu-id="0460b-200">Set the value to `false` to disable quick JIT.</span></span> <span data-ttu-id="0460b-201">Aby uzyskać więcej informacji, zobacz [szybkie JIT](../run-time-config/compilation.md#quick-jit).</span><span class="sxs-lookup"><span data-stu-id="0460b-201">For more information, see [Quick JIT](../run-time-config/compilation.md#quick-jit).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

### <a name="tieredcompilationquickjitforloops"></a><span data-ttu-id="0460b-202">TieredCompilationQuickJitForLoops</span><span class="sxs-lookup"><span data-stu-id="0460b-202">TieredCompilationQuickJitForLoops</span></span>

<span data-ttu-id="0460b-203">`TieredCompilationQuickJitForLoops` Właściwość określa, czy kompilator JIT używa szybkiej JIT metod, które zawierają pętle.</span><span class="sxs-lookup"><span data-stu-id="0460b-203">The `TieredCompilationQuickJitForLoops` property configures whether the JIT compiler uses quick JIT on methods that contain loops.</span></span> <span data-ttu-id="0460b-204">Ustaw wartość `true` na, aby włączyć funkcję szybkiego JIT dla metod, które zawierają pętle.</span><span class="sxs-lookup"><span data-stu-id="0460b-204">Set the value to `true` to enable quick JIT on methods that contain loops.</span></span> <span data-ttu-id="0460b-205">Aby uzyskać więcej informacji, zobacz [szybkie JIT dla pętli](../run-time-config/compilation.md#quick-jit-for-loops).</span><span class="sxs-lookup"><span data-stu-id="0460b-205">For more information, see [Quick JIT for loops](../run-time-config/compilation.md#quick-jit-for-loops).</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
</PropertyGroup>
```

## <a name="reference-properties"></a><span data-ttu-id="0460b-206">Właściwości odwołania</span><span class="sxs-lookup"><span data-stu-id="0460b-206">Reference properties</span></span>

- [<span data-ttu-id="0460b-207">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="0460b-207">AssetTargetFallback</span></span>](#assettargetfallback)
- [<span data-ttu-id="0460b-208">PackageReference</span><span class="sxs-lookup"><span data-stu-id="0460b-208">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="0460b-209">Elementu ProjectReference</span><span class="sxs-lookup"><span data-stu-id="0460b-209">ProjectReference</span></span>](#projectreference)
- [<span data-ttu-id="0460b-210">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="0460b-210">Reference</span></span>](#reference)
- [<span data-ttu-id="0460b-211">Właściwości przywracania</span><span class="sxs-lookup"><span data-stu-id="0460b-211">Restore properties</span></span>](#restore-properties)

### <a name="assettargetfallback"></a><span data-ttu-id="0460b-212">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="0460b-212">AssetTargetFallback</span></span>

<span data-ttu-id="0460b-213">`AssetTargetFallback` Właściwość pozwala określić dodatkowe zgodne wersje architektury dla odwołań do projektu i pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="0460b-213">The `AssetTargetFallback` property lets you specify additional compatible framework versions for project references and NuGet packages.</span></span> <span data-ttu-id="0460b-214">Na przykład, jeśli określisz zależność pakietu przy użyciu `PackageReference` programu `TargetFramework`, ale ten pakiet nie zawiera zasobów, które są zgodne z projektem, `AssetTargetFallback` właściwość jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="0460b-214">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="0460b-215">Zgodność przywoływanego pakietu jest ponownie sprawdzana przy użyciu każdej platformy docelowej określonej w `AssetTargetFallback`.</span><span class="sxs-lookup"><span data-stu-id="0460b-215">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="0460b-216">Można ustawić `AssetTargetFallback` właściwość na co najmniej jedną [docelową wersję platformy](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="0460b-216">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<PropertyGroup>
  <AssetTargetFallback>net461</AssetTargetFallback>
</PropertyGroup>
```

### <a name="packagereference"></a><span data-ttu-id="0460b-217">PackageReference</span><span class="sxs-lookup"><span data-stu-id="0460b-217">PackageReference</span></span>

<span data-ttu-id="0460b-218">`PackageReference` Definiuje odwołanie do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="0460b-218">The `PackageReference` defines a reference to a NuGet package.</span></span> <span data-ttu-id="0460b-219">Na przykład możesz chcieć odwołać się do pojedynczego pakietu zamiast [pakietu](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="0460b-219">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span>

<span data-ttu-id="0460b-220">Ten `Include` ATRYBUT określa identyfikator pakietu.</span><span class="sxs-lookup"><span data-stu-id="0460b-220">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="0460b-221">Ten `Version` atrybut określa wersję lub zakres wersji.</span><span class="sxs-lookup"><span data-stu-id="0460b-221">The `Version` attribute specifies the version or version range.</span></span> <span data-ttu-id="0460b-222">Aby uzyskać informacje na temat określania minimalnej wersji, maksymalnej wersji, zakresu lub dokładnego dopasowania, zobacz [zakres wersji](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="0460b-222">For information about how to specify a minimum version, maximum version, range, or exact match, see [Version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span> <span data-ttu-id="0460b-223">Można również dodać następujące metadane do odwołania do projektu: `IncludeAssets`, `ExcludeAssets`, i. `PrivateAssets`</span><span class="sxs-lookup"><span data-stu-id="0460b-223">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="0460b-224">Fragment pliku projektu w poniższym przykładzie odwołuje się do pakietu [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="0460b-224">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<ItemGroup>
  <PackageReference Include="System.Runtime" Version="4.3.0" />
</ItemGroup>
```

<span data-ttu-id="0460b-225">Aby uzyskać więcej informacji, zobacz [odwołania do pakietów w plikach projektu](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="0460b-225">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="projectreference"></a><span data-ttu-id="0460b-226">Elementu ProjectReference</span><span class="sxs-lookup"><span data-stu-id="0460b-226">ProjectReference</span></span>

<span data-ttu-id="0460b-227">`ProjectReference` Element definiuje odwołanie do innego projektu.</span><span class="sxs-lookup"><span data-stu-id="0460b-227">The `ProjectReference` item defines a reference to another project.</span></span> <span data-ttu-id="0460b-228">Przywoływany projekt jest dodawany jako zależność pakietu NuGet, czyli jest traktowany tak samo jak `PackageReference`.</span><span class="sxs-lookup"><span data-stu-id="0460b-228">The referenced project is added as a NuGet package dependency, that is, it's treated the same as a `PackageReference`.</span></span>

<span data-ttu-id="0460b-229">Ten `Include` atrybut określa ścieżkę do projektu.</span><span class="sxs-lookup"><span data-stu-id="0460b-229">The `Include` attribute specifies the path to the project.</span></span> <span data-ttu-id="0460b-230">Można również dodać następujące metadane do odwołania do projektu: `IncludeAssets`, `ExcludeAssets`, i. `PrivateAssets`</span><span class="sxs-lookup"><span data-stu-id="0460b-230">You can also add the following metadata to a project reference: `IncludeAssets`, `ExcludeAssets`, and `PrivateAssets`.</span></span>

<span data-ttu-id="0460b-231">Fragment pliku projektu w poniższym przykładzie odwołuje się do projektu o `Project2`nazwie.</span><span class="sxs-lookup"><span data-stu-id="0460b-231">The project file snippet in the following example references a project named `Project2`.</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\Project2.csproj" />
</ItemGroup>
```

### <a name="reference"></a><span data-ttu-id="0460b-232">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="0460b-232">Reference</span></span>

<span data-ttu-id="0460b-233">`Reference` Element definiuje odwołanie do pliku zestawu.</span><span class="sxs-lookup"><span data-stu-id="0460b-233">The `Reference` item defines a reference to an assembly file.</span></span>

<span data-ttu-id="0460b-234">`Include` Atrybut określa nazwę pliku, a element `HintPath` podrzędny określa ścieżkę do zestawu.</span><span class="sxs-lookup"><span data-stu-id="0460b-234">The `Include` attribute specifies the name of the file, and the `HintPath` child element specifies the path to the assembly.</span></span>

```xml
<ItemGroup>
  <Reference Include="MyAssembly">
    <HintPath>..\..\Assemblies\MyAssembly.dll</HintPath>
  </Reference>
</ItemGroup>
```

### <a name="restore-properties"></a><span data-ttu-id="0460b-235">Właściwości przywracania</span><span class="sxs-lookup"><span data-stu-id="0460b-235">Restore properties</span></span>

<span data-ttu-id="0460b-236">Przywracanie przywoływanego pakietu instaluje wszystkie jego bezpośrednie zależności i wszystkie zależności tych zależności.</span><span class="sxs-lookup"><span data-stu-id="0460b-236">Restoring a referenced package installs all of its direct dependencies and all the dependencies of those dependencies.</span></span> <span data-ttu-id="0460b-237">Przywracanie pakietu można dostosować, określając właściwości, takie jak `RestorePackagesPath` i `RestoreIgnoreFailedSources`.</span><span class="sxs-lookup"><span data-stu-id="0460b-237">You can customize package restoration by specifying properties such as `RestorePackagesPath` and `RestoreIgnoreFailedSources`.</span></span> <span data-ttu-id="0460b-238">Aby uzyskać więcej informacji na temat tych i innych właściwości, zobacz [Restore Target](/nuget/reference/msbuild-targets#restore-target).</span><span class="sxs-lookup"><span data-stu-id="0460b-238">For more information about these and other properties, see [restore target](/nuget/reference/msbuild-targets#restore-target).</span></span>

```xml
<PropertyGroup>
  <RestoreIgnoreFailedSource>true</RestoreIgnoreFailedSource>
</PropertyGroup>
```

## <a name="see-also"></a><span data-ttu-id="0460b-239">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0460b-239">See also</span></span>

- [<span data-ttu-id="0460b-240">Odwołanie do schematu programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="0460b-240">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="0460b-241">Typowe właściwości programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="0460b-241">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="0460b-242">Właściwości programu MSBuild dla pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="0460b-242">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="0460b-243">Właściwości programu MSBuild do przywracania NuGet</span><span class="sxs-lookup"><span data-stu-id="0460b-243">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="0460b-244">Dostosuj kompilację</span><span class="sxs-lookup"><span data-stu-id="0460b-244">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
