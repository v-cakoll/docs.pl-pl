---
title: Właściwości programu MSBuild dla Microsoft. NET. Sdk
description: Odwołanie do właściwości programu MSBuild, które są zrozumiałe dla zestaw .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: 00d9152d864ac0727a511f4c3c15abba82aab904
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503812"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="0bec6-103">Właściwości programu MSBuild dla projektów zestaw .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="0bec6-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="0bec6-104">Na tej stronie opisano właściwości programu MSBuild służące do konfigurowania projektów platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0bec6-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="0bec6-105">Ta strona jest w toku i nie wyświetla wszystkich przydatnych właściwości programu MSBuild dla zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="0bec6-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="0bec6-106">Aby zapoznać się z listą typowych właściwości programu MSBuild, zobacz [typowe właściwości programu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="0bec6-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="0bec6-107">Właściwości struktury</span><span class="sxs-lookup"><span data-stu-id="0bec6-107">Framework properties</span></span>

- [<span data-ttu-id="0bec6-108">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="0bec6-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="0bec6-109">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="0bec6-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="0bec6-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="0bec6-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="0bec6-111">TargetFramework</span><span class="sxs-lookup"><span data-stu-id="0bec6-111">TargetFramework</span></span>

<span data-ttu-id="0bec6-112">Właściwość `TargetFramework` określa wersję platformy docelowej dla aplikacji, która niejawnie odwołuje się do [pakietu](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="0bec6-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="0bec6-113">Aby zapoznać się z listą prawidłowych monikerów platformy docelowej, zobacz [platformę docelową w projektach w stylu zestawu SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="0bec6-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="0bec6-114">Aby uzyskać więcej informacji, zobacz [Platformy docelowe w projektach w stylu zestawu SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0bec6-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="0bec6-115">TargetFrameworks</span><span class="sxs-lookup"><span data-stu-id="0bec6-115">TargetFrameworks</span></span>

<span data-ttu-id="0bec6-116">Użyj właściwości `TargetFrameworks`, jeśli chcesz, aby aplikacja była przeznaczona dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="0bec6-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="0bec6-117">Aby zapoznać się z listą prawidłowych monikerów platformy docelowej, zobacz [platformę docelową w projektach w stylu zestawu SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="0bec6-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="0bec6-118">Ta właściwość jest ignorowana, jeśli określono `TargetFramework` (pojedynczą).</span><span class="sxs-lookup"><span data-stu-id="0bec6-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="0bec6-119">Aby uzyskać więcej informacji, zobacz [Platformy docelowe w projektach w stylu zestawu SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="0bec6-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="0bec6-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="0bec6-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="0bec6-121">Ta właściwość ma zastosowanie tylko do projektów korzystających z `netstandard1.x`.</span><span class="sxs-lookup"><span data-stu-id="0bec6-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="0bec6-122">Nie dotyczy to projektów, które używają `netstandard2.x`.</span><span class="sxs-lookup"><span data-stu-id="0bec6-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="0bec6-123">Użyj właściwości `NetStandardImplicitPackageVersion`, aby określić wersję platformy, która jest starsza niż wersja [pakietu](../packages.md#metapackages) .</span><span class="sxs-lookup"><span data-stu-id="0bec6-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="0bec6-124">Plik projektu w poniższym przykładzie jest docelowy `netstandard1.3` ale używa wersji 1.6.0 `NETStandard.Library`.</span><span class="sxs-lookup"><span data-stu-id="0bec6-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="0bec6-125">Właściwości publikowania</span><span class="sxs-lookup"><span data-stu-id="0bec6-125">Publish properties</span></span>

- [<span data-ttu-id="0bec6-126">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="0bec6-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="0bec6-127">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="0bec6-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="0bec6-128">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="0bec6-128">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="0bec6-129">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="0bec6-129">RuntimeIdentifier</span></span>

<span data-ttu-id="0bec6-130">Właściwość `RuntimeIdentifier` umożliwia określenie pojedynczego [identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu.</span><span class="sxs-lookup"><span data-stu-id="0bec6-130">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="0bec6-131">Identyfikator RID umożliwia publikowanie samodzielnego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="0bec6-131">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="0bec6-132">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="0bec6-132">RuntimeIdentifiers</span></span>

<span data-ttu-id="0bec6-133">Właściwość `RuntimeIdentifiers` pozwala określić rozdzielaną średnikami listę [identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu.</span><span class="sxs-lookup"><span data-stu-id="0bec6-133">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="0bec6-134">Użyj tej właściwości, jeśli chcesz opublikować dla wielu środowisk uruchomieniowych.</span><span class="sxs-lookup"><span data-stu-id="0bec6-134">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="0bec6-135">`RuntimeIdentifiers` jest używany podczas przywracania, aby upewnić się, że odpowiednie zasoby znajdują się na wykresie.</span><span class="sxs-lookup"><span data-stu-id="0bec6-135">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="0bec6-136">`RuntimeIdentifier` (pojedyncze) może zapewnić szybsze kompilacje, gdy wymagane jest tylko jedno środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="0bec6-136">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="0bec6-137">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="0bec6-137">UseAppHost</span></span>

<span data-ttu-id="0bec6-138">Właściwość `UseAppHost` została wprowadzona w wersji 2.1.400 zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="0bec6-138">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="0bec6-139">Określa, czy dla wdrożenia jest tworzony natywny plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="0bec6-139">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="0bec6-140">Natywny plik wykonywalny jest wymagany w przypadku wdrożeń samodzielnych.</span><span class="sxs-lookup"><span data-stu-id="0bec6-140">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="0bec6-141">W programie .NET Core 3,0 i jego nowszych wersjach domyślnie tworzony jest plik wykonywalny zależny od platformy.</span><span class="sxs-lookup"><span data-stu-id="0bec6-141">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="0bec6-142">Ustaw właściwość `UseAppHost` na `false`, aby wyłączyć generowanie pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="0bec6-142">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="0bec6-143">Aby uzyskać więcej informacji na temat wdrażania, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="0bec6-143">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="0bec6-144">Kompiluj właściwości</span><span class="sxs-lookup"><span data-stu-id="0bec6-144">Compile properties</span></span>

### <a name="langversion"></a><span data-ttu-id="0bec6-145">LangVersion</span><span class="sxs-lookup"><span data-stu-id="0bec6-145">LangVersion</span></span>

<span data-ttu-id="0bec6-146">Właściwość `LangVersion` umożliwia określenie konkretnej wersji języka programowania.</span><span class="sxs-lookup"><span data-stu-id="0bec6-146">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="0bec6-147">Na przykład jeśli chcesz uzyskać dostęp do C# funkcji w wersji zapoznawczej, ustaw `LangVersion` na `preview`.</span><span class="sxs-lookup"><span data-stu-id="0bec6-147">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="0bec6-148">Aby uzyskać więcej informacji, zobacz [ C# przechowywanie wersji języka](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="0bec6-148">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="nuget-packages"></a><span data-ttu-id="0bec6-149">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="0bec6-149">NuGet packages</span></span>

- [<span data-ttu-id="0bec6-150">PackageReference</span><span class="sxs-lookup"><span data-stu-id="0bec6-150">PackageReference</span></span>](#packagereference)

### <a name="packagereference"></a><span data-ttu-id="0bec6-151">PackageReference</span><span class="sxs-lookup"><span data-stu-id="0bec6-151">PackageReference</span></span>

<span data-ttu-id="0bec6-152">Element `PackageReference` pozwala określić zależność NuGet.</span><span class="sxs-lookup"><span data-stu-id="0bec6-152">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="0bec6-153">Na przykład możesz chcieć odwołać się do pojedynczego pakietu zamiast [pakietu](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="0bec6-153">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="0bec6-154">Atrybut `Include` określa identyfikator pakietu.</span><span class="sxs-lookup"><span data-stu-id="0bec6-154">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="0bec6-155">Fragment pliku projektu w poniższym przykładzie odwołuje się do pakietu [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .</span><span class="sxs-lookup"><span data-stu-id="0bec6-155">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="0bec6-156">Aby uzyskać więcej informacji, zobacz [odwołania do pakietów w plikach projektu](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="0bec6-156">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="pack-and-restore-targets"></a><span data-ttu-id="0bec6-157">Elementy docelowe pakietów i przywracania</span><span class="sxs-lookup"><span data-stu-id="0bec6-157">Pack and restore targets</span></span>

<span data-ttu-id="0bec6-158">Program MSBuild 15,1 wprowadził `pack` i `restore` elementy docelowe do tworzenia i przywracania pakietów NuGet w ramach kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0bec6-158">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="0bec6-159">Aby uzyskać informacje na temat właściwości programu MSBuild dla tych obiektów docelowych, w tym `PackageTargetFallback`, zobacz [pakiet NuGet i przywracanie jako elementy docelowe programu MSBuild](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="0bec6-159">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="0bec6-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0bec6-160">See also</span></span>

- [<span data-ttu-id="0bec6-161">Odwołanie do schematu programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="0bec6-161">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="0bec6-162">Typowe właściwości programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="0bec6-162">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="0bec6-163">Właściwości programu MSBuild dla pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="0bec6-163">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="0bec6-164">Właściwości programu MSBuild do przywracania NuGet</span><span class="sxs-lookup"><span data-stu-id="0bec6-164">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="0bec6-165">Dostosuj kompilację</span><span class="sxs-lookup"><span data-stu-id="0bec6-165">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
