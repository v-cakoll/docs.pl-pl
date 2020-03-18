---
title: Właściwości MSBuild dla pliku Microsoft.NET.Sdk
description: Odwołanie do właściwości MSBuild, które są rozumiane przez .NET Core SDK.
ms.date: 02/14/2020
ms.topic: reference
ms.openlocfilehash: d4a204a1e0216313418d278ec3bd333f72db8751
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399183"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a><span data-ttu-id="5d9b8-103">Właściwości MSBuild dla projektów SDK .NET Core</span><span class="sxs-lookup"><span data-stu-id="5d9b8-103">MSBuild properties for .NET Core SDK projects</span></span>

<span data-ttu-id="5d9b8-104">Na tej stronie opisano właściwości MSBuild do konfigurowania projektów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-104">This page describes MSBuild properties for configuring .NET Core projects.</span></span>

> [!NOTE]
> <span data-ttu-id="5d9b8-105">Ta strona jest w toku i nie zawiera wszystkich przydatnych właściwości MSBuild dla .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-105">This page is a work in progress and does not list all of the useful MSBuild properties for the .NET Core SDK.</span></span> <span data-ttu-id="5d9b8-106">Aby uzyskać listę typowych właściwości MSBuild, zobacz [Typowe właściwości MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).</span><span class="sxs-lookup"><span data-stu-id="5d9b8-106">For a list of common MSBuild properties, see [Common MSBuild properties](/visualstudio/msbuild/common-msbuild-project-properties).</span></span>

## <a name="framework-properties"></a><span data-ttu-id="5d9b8-107">Właściwości frameworka</span><span class="sxs-lookup"><span data-stu-id="5d9b8-107">Framework properties</span></span>

- [<span data-ttu-id="5d9b8-108">Platforma docelowa</span><span class="sxs-lookup"><span data-stu-id="5d9b8-108">TargetFramework</span></span>](#targetframework)
- [<span data-ttu-id="5d9b8-109">Platformy docelowe</span><span class="sxs-lookup"><span data-stu-id="5d9b8-109">TargetFrameworks</span></span>](#targetframeworks)
- [<span data-ttu-id="5d9b8-110">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="5d9b8-110">NetStandardImplicitPackageVersion</span></span>](#netstandardimplicitpackageversion)

### <a name="targetframework"></a><span data-ttu-id="5d9b8-111">Platforma docelowa</span><span class="sxs-lookup"><span data-stu-id="5d9b8-111">TargetFramework</span></span>

<span data-ttu-id="5d9b8-112">Właściwość `TargetFramework` określa wersję platformy docelowej dla aplikacji, która niejawnie odwołuje się do [metapakietu](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="5d9b8-112">The `TargetFramework` property specifies the target framework version for the app, which implicitly references a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="5d9b8-113">Aby uzyskać listę prawidłowych monikerów platform [docelowych, zobacz Platformy docelowe w projektach w stylu SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="5d9b8-113">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="5d9b8-114">Aby uzyskać więcej informacji, zobacz [Platformy docelowe w projektach w stylu SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="5d9b8-114">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="targetframeworks"></a><span data-ttu-id="5d9b8-115">Platformy docelowe</span><span class="sxs-lookup"><span data-stu-id="5d9b8-115">TargetFrameworks</span></span>

<span data-ttu-id="5d9b8-116">Użyj `TargetFrameworks` tej właściwości, gdy chcesz, aby aplikacja była skierowana na wiele platform.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-116">Use the `TargetFrameworks` property when you want your app to target multiple platforms.</span></span> <span data-ttu-id="5d9b8-117">Aby uzyskać listę prawidłowych monikerów platform [docelowych, zobacz Platformy docelowe w projektach w stylu SDK](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="5d9b8-117">For a list of valid target framework monikers, see [Target frameworks in SDK-style projects](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

> [!NOTE]
> <span data-ttu-id="5d9b8-118">Ta właściwość jest `TargetFramework` ignorowana, jeśli określono (liczba pojedyncza).</span><span class="sxs-lookup"><span data-stu-id="5d9b8-118">This property is ignored if `TargetFramework` (singular) is specified.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="5d9b8-119">Aby uzyskać więcej informacji, zobacz [Platformy docelowe w projektach w stylu SDK](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="5d9b8-119">For more information, see [Target frameworks in SDK-style projects](../../standard/frameworks.md).</span></span>

### <a name="netstandardimplicitpackageversion"></a><span data-ttu-id="5d9b8-120">NetStandardImplicitPackageVersion</span><span class="sxs-lookup"><span data-stu-id="5d9b8-120">NetStandardImplicitPackageVersion</span></span>

> [!NOTE]
> <span data-ttu-id="5d9b8-121">Ta właściwość ma zastosowanie `netstandard1.x`tylko do projektów korzystających z programu .</span><span class="sxs-lookup"><span data-stu-id="5d9b8-121">This property only applies to projects using `netstandard1.x`.</span></span> <span data-ttu-id="5d9b8-122">Nie ma zastosowania do projektów, które używają `netstandard2.x`.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-122">It doesn't apply to projects that use `netstandard2.x`.</span></span>

<span data-ttu-id="5d9b8-123">Użyj `NetStandardImplicitPackageVersion` właściwości, gdy chcesz określić wersję framework, która jest niższa niż wersja [metapackage.](../packages.md#metapackages)</span><span class="sxs-lookup"><span data-stu-id="5d9b8-123">Use the `NetStandardImplicitPackageVersion` property when you want to specify a framework version that's lower than the [metapackage](../packages.md#metapackages) version.</span></span> <span data-ttu-id="5d9b8-124">Plik projektu w poniższym `netstandard1.3` przykładzie obiektów docelowych, ale `NETStandard.Library`używa wersji 1.6.0 .</span><span class="sxs-lookup"><span data-stu-id="5d9b8-124">The project file in the following example targets `netstandard1.3` but uses the 1.6.0 version of `NETStandard.Library`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a><span data-ttu-id="5d9b8-125">Publikowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="5d9b8-125">Publish properties</span></span>

- [<span data-ttu-id="5d9b8-126">Identyfikator czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="5d9b8-126">RuntimeIdentifier</span></span>](#runtimeidentifier)
- [<span data-ttu-id="5d9b8-127">Identyfikatory runtimeidentifiers</span><span class="sxs-lookup"><span data-stu-id="5d9b8-127">RuntimeIdentifiers</span></span>](#runtimeidentifiers)
- [<span data-ttu-id="5d9b8-128">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="5d9b8-128">UseAppHost</span></span>](#useapphost)

### <a name="runtimeidentifier"></a><span data-ttu-id="5d9b8-129">Identyfikator czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="5d9b8-129">RuntimeIdentifier</span></span>

<span data-ttu-id="5d9b8-130">Właściwość `RuntimeIdentifier` umożliwia określenie pojedynczego [identyfikatora wykonywania (RID)](../rid-catalog.md) dla projektu.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-130">The `RuntimeIdentifier` property lets you specify a single [runtime identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="5d9b8-131">RID umożliwia publikowanie niezależnego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-131">The RID enables publishing a self-contained deployment.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a><span data-ttu-id="5d9b8-132">Identyfikatory runtimeidentifiers</span><span class="sxs-lookup"><span data-stu-id="5d9b8-132">RuntimeIdentifiers</span></span>

<span data-ttu-id="5d9b8-133">Właściwość `RuntimeIdentifiers` umożliwia określenie delimitowanej średnikami listy [identyfikatorów czasu wykonywania (IDENTYFIKATORY)](../rid-catalog.md) dla projektu.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-133">The `RuntimeIdentifiers` property lets you specify a semicolon-delimited list of [runtime identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="5d9b8-134">Użyj tej właściwości, jeśli trzeba opublikować dla wielu uruchomiń.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-134">Use this property if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="5d9b8-135">`RuntimeIdentifiers`jest używany w czasie przywracania, aby upewnić się, że odpowiednie zasoby znajdują się na wykresie.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-135">`RuntimeIdentifiers` is used at restore time to ensure the right assets are in the graph.</span></span>

> [!TIP]
> <span data-ttu-id="5d9b8-136">`RuntimeIdentifier`(w liczbie pojedynczej) może zapewnić szybsze kompilacje, gdy wymagany jest tylko jeden czas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-136">`RuntimeIdentifier` (singular) can provide faster builds when only a single runtime is required.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a><span data-ttu-id="5d9b8-137">UseAppHost</span><span class="sxs-lookup"><span data-stu-id="5d9b8-137">UseAppHost</span></span>

<span data-ttu-id="5d9b8-138">Właściwość `UseAppHost` została wprowadzona w wersji 2.1.400 .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-138">The `UseAppHost` property was introduced in the 2.1.400 version of the .NET Core SDK.</span></span> <span data-ttu-id="5d9b8-139">Kontroluje, czy natywny plik wykonywalny jest tworzony dla wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-139">It controls whether or not a native executable is created for a deployment.</span></span> <span data-ttu-id="5d9b8-140">Natywny plik wykonywalny jest wymagany dla wdrożeń samodzielnych.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-140">A native executable is required for self-contained deployments.</span></span>

<span data-ttu-id="5d9b8-141">W .NET Core 3.0 i nowszych wersjach plik wykonywalny zależny od struktury jest tworzony domyślnie.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-141">In .NET Core 3.0 and later versions, a framework-dependent executable is created by default.</span></span> <span data-ttu-id="5d9b8-142">Ustaw `UseAppHost` właściwość, `false` aby wyłączyć generowanie pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-142">Set the `UseAppHost` property to `false` to disable generation of the executable.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="5d9b8-143">Aby uzyskać więcej informacji na temat wdrażania, zobacz [.NET Core application deployment](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="5d9b8-143">For more information about deployment, see [.NET Core application deployment](../deploying/index.md).</span></span>

## <a name="compile-properties"></a><span data-ttu-id="5d9b8-144">Kompilowanie właściwości</span><span class="sxs-lookup"><span data-stu-id="5d9b8-144">Compile properties</span></span>

### <a name="langversion"></a><span data-ttu-id="5d9b8-145">Wersja LangVersion</span><span class="sxs-lookup"><span data-stu-id="5d9b8-145">LangVersion</span></span>

<span data-ttu-id="5d9b8-146">Właściwość `LangVersion` umożliwia określenie określonej wersji językowej programowania.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-146">The `LangVersion` property lets you specify a specific programming language version.</span></span> <span data-ttu-id="5d9b8-147">Na przykład, jeśli chcesz uzyskać dostęp do `LangVersion` `preview`funkcji podglądu języka C#, ustaw na .</span><span class="sxs-lookup"><span data-stu-id="5d9b8-147">For example, if you want access to C# preview features, set `LangVersion` to `preview`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="5d9b8-148">Aby uzyskać więcej informacji, zobacz [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span><span class="sxs-lookup"><span data-stu-id="5d9b8-148">For more information, see [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).</span></span>

## <a name="nuget-packages"></a><span data-ttu-id="5d9b8-149">Pakiety NuGet</span><span class="sxs-lookup"><span data-stu-id="5d9b8-149">NuGet packages</span></span>

- [<span data-ttu-id="5d9b8-150">Odwołanie do pakietu</span><span class="sxs-lookup"><span data-stu-id="5d9b8-150">PackageReference</span></span>](#packagereference)
- [<span data-ttu-id="5d9b8-151">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="5d9b8-151">AssetTargetFallback</span></span>](#assettargetfallback)

### <a name="packagereference"></a><span data-ttu-id="5d9b8-152">Odwołanie do pakietu</span><span class="sxs-lookup"><span data-stu-id="5d9b8-152">PackageReference</span></span>

<span data-ttu-id="5d9b8-153">Element `PackageReference` umożliwia określenie zależności NuGet.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-153">The `PackageReference` item lets you specify a NuGet dependency.</span></span> <span data-ttu-id="5d9b8-154">Na przykład można odwołać się do pojedynczego pakietu zamiast [metapakietu](../packages.md#metapackages).</span><span class="sxs-lookup"><span data-stu-id="5d9b8-154">For example, you may want to reference a single package instead of a [metapackage](../packages.md#metapackages).</span></span> <span data-ttu-id="5d9b8-155">Atrybut `Include` określa identyfikator pakietu.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-155">The `Include` attribute specifies the package ID.</span></span> <span data-ttu-id="5d9b8-156">Fragment kodu pliku projektu w poniższym przykładzie odwołuje się do pakietu [System.Runtime.](https://www.nuget.org/packages/System.Runtime/)</span><span class="sxs-lookup"><span data-stu-id="5d9b8-156">The project file snippet in the following example references the [System.Runtime](https://www.nuget.org/packages/System.Runtime/) package.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="5d9b8-157">Aby uzyskać więcej informacji, zobacz [Odwołania do pakietów w plikach projektu](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="5d9b8-157">For more information, see [Package references in project files](/nuget/consume-packages/package-references-in-project-files).</span></span>

### <a name="assettargetfallback"></a><span data-ttu-id="5d9b8-158">AssetTargetFallback</span><span class="sxs-lookup"><span data-stu-id="5d9b8-158">AssetTargetFallback</span></span>

<span data-ttu-id="5d9b8-159">Właściwość `AssetTargetFallback` umożliwia określenie dodatkowych wersji zgodnych framework dla projektów, które odwołuje się do projektu i pakietów NuGet, które zużywa projekt.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-159">The `AssetTargetFallback` property lets you specify additional compatible framework versions for projects that your project references and NuGet packages that your project consumes.</span></span> <span data-ttu-id="5d9b8-160">Na przykład jeśli określisz `PackageReference` zależność pakietu przy użyciu, ale ten pakiet nie `TargetFramework`zawiera `AssetTargetFallback` zasobów, które są zgodne z projektów , właściwość wchodzi w grę.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-160">For example, if you specify a package dependency using `PackageReference` but that package doesn't contain assets that are compatible with your projects's `TargetFramework`, the `AssetTargetFallback` property comes into play.</span></span> <span data-ttu-id="5d9b8-161">Zgodność pakietu, do którego istnieje odwołanie, jest ponownie sprawdzana `AssetTargetFallback`przy użyciu każdej platformy docelowej określonej w pliku .</span><span class="sxs-lookup"><span data-stu-id="5d9b8-161">The compatibility of the referenced package is rechecked using each target framework that's specified in `AssetTargetFallback`.</span></span>

<span data-ttu-id="5d9b8-162">Właściwość można `AssetTargetFallback` ustawić na jedną lub więcej [wersji platformy docelowej](../../standard/frameworks.md#supported-target-framework-versions).</span><span class="sxs-lookup"><span data-stu-id="5d9b8-162">You can set the `AssetTargetFallback` property to one or more [target framework versions](../../standard/frameworks.md#supported-target-framework-versions).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a><span data-ttu-id="5d9b8-163">Pakuj i przywracaj cele</span><span class="sxs-lookup"><span data-stu-id="5d9b8-163">Pack and restore targets</span></span>

<span data-ttu-id="5d9b8-164">MSBuild 15.1 `pack` `restore` wprowadzone i cele do tworzenia i przywracania pakietów NuGet jako część kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5d9b8-164">MSBuild 15.1 introduced `pack` and `restore` targets for creating and restoring NuGet packages as part of a build.</span></span> <span data-ttu-id="5d9b8-165">Aby uzyskać informacje o właściwościach MSBuild `PackageTargetFallback`dla tych obiektów docelowych, w tym , zobacz [NuGet pack i przywracanie jako cele MSBuild](/nuget/reference/msbuild-targets).</span><span class="sxs-lookup"><span data-stu-id="5d9b8-165">For information about the MSBuild properties for these targets, including `PackageTargetFallback`, see [NuGet pack and restore as MSBuild targets](/nuget/reference/msbuild-targets).</span></span>

## <a name="see-also"></a><span data-ttu-id="5d9b8-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d9b8-166">See also</span></span>

- [<span data-ttu-id="5d9b8-167">Odwołanie do schematu MSBuild</span><span class="sxs-lookup"><span data-stu-id="5d9b8-167">MSBuild schema reference</span></span>](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [<span data-ttu-id="5d9b8-168">Typowe właściwości MSBuild</span><span class="sxs-lookup"><span data-stu-id="5d9b8-168">Common MSBuild properties</span></span>](/visualstudio/msbuild/common-msbuild-project-properties)
- [<span data-ttu-id="5d9b8-169">Właściwości MSBuild dla pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="5d9b8-169">MSBuild properties for NuGet pack</span></span>](/nuget/reference/msbuild-targets#pack-target)
- [<span data-ttu-id="5d9b8-170">MsBuild właściwości przywracania NuGet</span><span class="sxs-lookup"><span data-stu-id="5d9b8-170">MSBuild properties for NuGet restore</span></span>](/nuget/reference/msbuild-targets#restore-properties)
- [<span data-ttu-id="5d9b8-171">Dostosowywanie kompilacji</span><span class="sxs-lookup"><span data-stu-id="5d9b8-171">Customize a build</span></span>](/visualstudio/msbuild/customize-your-build)
