---
title: porównanie project.json i csproj
description: Zobacz mapowanie między project.json i csproj elementów.
author: natemcmaster
ms.date: 03/13/2017
ms.openlocfilehash: abe515007b47b415ac33e3350a29edced1784d68
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451108"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a><span data-ttu-id="8b654-103">Mapowanie między project.json i csproj właściwości</span><span class="sxs-lookup"><span data-stu-id="8b654-103">A mapping between project.json and csproj properties</span></span>

<span data-ttu-id="8b654-104">Przez [Nate McMaster](https://github.com/natemcmaster)</span><span class="sxs-lookup"><span data-stu-id="8b654-104">By [Nate McMaster](https://github.com/natemcmaster)</span></span>

<span data-ttu-id="8b654-105">Podczas opracowywania narzędzi .NET Core, ważną zmianę projektu została wdrożena, aby nie obsługiwać już plików *project.json* i zamiast tego przenieść projekty .NET Core do formatu MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="8b654-105">During the development of the .NET Core tooling, an important design change was made to no longer support *project.json* files and instead move the .NET Core projects to the MSBuild/csproj format.</span></span>

<span data-ttu-id="8b654-106">W tym artykule pokazano, jak ustawienia w *programie project.json* są reprezentowane w formacie MSBuild/csproj, dzięki czemu można dowiedzieć się, jak korzystać z nowego formatu i zrozumieć zmiany wprowadzone przez narzędzia migracji podczas uaktualniania projektu do najnowszej wersji narzędzi.</span><span class="sxs-lookup"><span data-stu-id="8b654-106">This article shows how the settings in *project.json* are represented in the MSBuild/csproj format so you can learn how to use the new format and understand the changes made by the migration tools when you're upgrading your project to the latest version of the tooling.</span></span>

## <a name="the-csproj-format"></a><span data-ttu-id="8b654-107">Format csproj</span><span class="sxs-lookup"><span data-stu-id="8b654-107">The csproj format</span></span>

<span data-ttu-id="8b654-108">Nowy format, \*.csproj, jest formatem opartym na XML.</span><span class="sxs-lookup"><span data-stu-id="8b654-108">The new format, \*.csproj, is an XML-based format.</span></span> <span data-ttu-id="8b654-109">W poniższym przykładzie przedstawiono węzeł główny projektu .NET Core przy użyciu `Microsoft.NET.Sdk`pliku .</span><span class="sxs-lookup"><span data-stu-id="8b654-109">The following example shows the root node of a .NET Core project using the `Microsoft.NET.Sdk`.</span></span> <span data-ttu-id="8b654-110">W przypadku projektów internetowych używany `Microsoft.NET.Sdk.Web`jest zestaw SDK .</span><span class="sxs-lookup"><span data-stu-id="8b654-110">For web projects, the SDK used is `Microsoft.NET.Sdk.Web`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a><span data-ttu-id="8b654-111">Typowe właściwości najwyższego poziomu</span><span class="sxs-lookup"><span data-stu-id="8b654-111">Common top-level properties</span></span>

### <a name="name"></a><span data-ttu-id="8b654-112">name</span><span class="sxs-lookup"><span data-stu-id="8b654-112">name</span></span>

```json
{
  "name": "MyProjectName"
}
```

<span data-ttu-id="8b654-113">Nie jest już obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="8b654-113">No longer supported.</span></span> <span data-ttu-id="8b654-114">W csproj jest to określane przez nazwę pliku projektu, która zwykle pasuje do nazwy katalogu.</span><span class="sxs-lookup"><span data-stu-id="8b654-114">In csproj, this is determined by the project filename, which usually matches the directory name.</span></span> <span data-ttu-id="8b654-115">Na przykład `MyProjectName.csproj`.</span><span class="sxs-lookup"><span data-stu-id="8b654-115">For example, `MyProjectName.csproj`.</span></span>

<span data-ttu-id="8b654-116">Domyślnie nazwa pliku projektu określa również wartość `<AssemblyName>` `<PackageId>` i właściwości.</span><span class="sxs-lookup"><span data-stu-id="8b654-116">By default, the project filename also specifies the value of the `<AssemblyName>` and `<PackageId>` properties.</span></span>

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

<span data-ttu-id="8b654-117">Będzie `<AssemblyName>` miał inną wartość `<PackageId>` `buildOptions\outputName` niż jeśli właściwość została zdefiniowana w project.json.</span><span class="sxs-lookup"><span data-stu-id="8b654-117">The `<AssemblyName>` will have a different value than `<PackageId>` if `buildOptions\outputName` property was defined in project.json.</span></span>
<span data-ttu-id="8b654-118">Aby uzyskać więcej informacji, zobacz [Inne typowe opcje kompilacji](#other-common-build-options).</span><span class="sxs-lookup"><span data-stu-id="8b654-118">For more information, see [Other common build options](#other-common-build-options).</span></span>

### <a name="version"></a><span data-ttu-id="8b654-119">version</span><span class="sxs-lookup"><span data-stu-id="8b654-119">version</span></span>

```json
{
  "version": "1.0.0-alpha-*"
}
```

<span data-ttu-id="8b654-120">Użyj `VersionPrefix` właściwości `VersionSuffix` i właściwości:</span><span class="sxs-lookup"><span data-stu-id="8b654-120">Use the `VersionPrefix` and `VersionSuffix` properties:</span></span>

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

<span data-ttu-id="8b654-121">Można również użyć `Version` tej właściwości, ale może to zastąpić ustawienia wersji podczas pakowania:</span><span class="sxs-lookup"><span data-stu-id="8b654-121">You can also use the `Version` property, but this may override version settings during packaging:</span></span>

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a><span data-ttu-id="8b654-122">Inne typowe opcje na poziomie głównym</span><span class="sxs-lookup"><span data-stu-id="8b654-122">Other common root-level options</span></span>

```json
{
  "authors": [ "Anne", "Bob" ],
  "company": "Contoso",
  "language": "en-US",
  "title": "My library",
  "description": "This is my library.\r\nAnd it's really great!",
  "copyright": "Nugetizer 3000",
  "userSecretsId": "xyz123"
}
```

```xml
<PropertyGroup>
  <Authors>Anne;Bob</Authors>
  <Company>Contoso</Company>
  <NeutralLanguage>en-US</NeutralLanguage>
  <AssemblyTitle>My library</AssemblyTitle>
  <Description>This is my library.
And it's really great!</Description>
  <Copyright>Nugetizer 3000</Copyright>
  <UserSecretsId>xyz123</UserSecretsId>
</PropertyGroup>
```

## <a name="frameworks"></a><span data-ttu-id="8b654-123">Ram</span><span class="sxs-lookup"><span data-stu-id="8b654-123">frameworks</span></span>

### <a name="one-target-framework"></a><span data-ttu-id="8b654-124">Jedna rama docelowa</span><span class="sxs-lookup"><span data-stu-id="8b654-124">One target framework</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {}
  }
}
```

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp1.0</TargetFramework>
</PropertyGroup>
```

### <a name="multiple-target-frameworks"></a><span data-ttu-id="8b654-125">Wiele struktur docelowych</span><span class="sxs-lookup"><span data-stu-id="8b654-125">Multiple target frameworks</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

<span data-ttu-id="8b654-126">Użyj `TargetFrameworks` właściwości, aby zdefiniować listę struktur docelowych.</span><span class="sxs-lookup"><span data-stu-id="8b654-126">Use the `TargetFrameworks` property to define your list of target frameworks.</span></span> <span data-ttu-id="8b654-127">Użyj średnika, aby oddzielić wiele wartości framework.</span><span class="sxs-lookup"><span data-stu-id="8b654-127">Use semi-colon to separate multiple framework values.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a><span data-ttu-id="8b654-128">zależności</span><span class="sxs-lookup"><span data-stu-id="8b654-128">dependencies</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8b654-129">Jeśli zależność jest **projektem,** a nie pakietem, format jest inny.</span><span class="sxs-lookup"><span data-stu-id="8b654-129">If the dependency is a **project** and not a package, the format is different.</span></span>
> <span data-ttu-id="8b654-130">Aby uzyskać więcej informacji, zobacz sekcję [typu zależności.](#dependency-type)</span><span class="sxs-lookup"><span data-stu-id="8b654-130">For more information, see the [dependency type](#dependency-type) section.</span></span>

### <a name="netstandardlibrary-metapackage"></a><span data-ttu-id="8b654-131">Pakiet metazawartości NETStandard.Library</span><span class="sxs-lookup"><span data-stu-id="8b654-131">NETStandard.Library metapackage</span></span>

```json
{
  "dependencies": {
    "NETStandard.Library": "1.6.0"
  }
}
```

```xml
<PropertyGroup>
  <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
</PropertyGroup>
```

### <a name="microsoftnetcoreapp-metapackage"></a><span data-ttu-id="8b654-132">Pakiet metapakowań microsoft.NETCore.App</span><span class="sxs-lookup"><span data-stu-id="8b654-132">Microsoft.NETCore.App metapackage</span></span>

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": "1.0.0"
  }
}
```

```xml
<PropertyGroup>
  <RuntimeFrameworkVersion>1.0.3</RuntimeFrameworkVersion>
</PropertyGroup>
```

<span data-ttu-id="8b654-133">Należy zauważyć, że `<RuntimeFrameworkVersion>` wartość w zmigrowanym projekcie jest określana przez zainstalowaną wersję sdk.</span><span class="sxs-lookup"><span data-stu-id="8b654-133">Note that the `<RuntimeFrameworkVersion>` value in the migrated project is determined by the version of the SDK you have installed.</span></span>

### <a name="top-level-dependencies"></a><span data-ttu-id="8b654-134">Zależności najwyższego poziomu</span><span class="sxs-lookup"><span data-stu-id="8b654-134">Top-level dependencies</span></span>

```json
{
  "dependencies": {
    "Microsoft.AspNetCore": "1.1.0"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore" Version="1.1.0" />
</ItemGroup>
```

### <a name="per-framework-dependencies"></a><span data-ttu-id="8b654-135">Zależności na framework</span><span class="sxs-lookup"><span data-stu-id="8b654-135">Per-framework dependencies</span></span>

```json
{
  "framework": {
    "net451": {
      "dependencies": {
        "System.Collections.Immutable": "1.3.1"
      }
    },
    "netstandard1.5": {
      "dependencies": {
        "Newtonsoft.Json": "9.0.1"
      }
    }
  }
}
```

```xml
<ItemGroup Condition="'$(TargetFramework)'=='net451'">
  <PackageReference Include="System.Collections.Immutable" Version="1.3.1" />
</ItemGroup>

<ItemGroup Condition="'$(TargetFramework)'=='netstandard1.5'">
  <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
</ItemGroup>
```

### <a name="imports"></a><span data-ttu-id="8b654-136">importy</span><span class="sxs-lookup"><span data-stu-id="8b654-136">imports</span></span>

```json
{
  "dependencies": {
    "YamlDotNet": "4.0.1-pre309"
  },
  "frameworks": {
    "netcoreapp1.0": {
      "imports": [
        "dnxcore50",
        "dotnet"
      ]
    }
  }
}
```

```xml
<PropertyGroup>
  <PackageTargetFallback>dnxcore50;dotnet</PackageTargetFallback>
</PropertyGroup>
<ItemGroup>
  <PackageReference Include="YamlDotNet" Version="4.0.1-pre309" />
</ItemGroup>
```

### <a name="dependency-type"></a><span data-ttu-id="8b654-137">typ zależności</span><span class="sxs-lookup"><span data-stu-id="8b654-137">dependency type</span></span>

#### <a name="type-project"></a><span data-ttu-id="8b654-138">typ: projekt</span><span class="sxs-lookup"><span data-stu-id="8b654-138">type: project</span></span>

```json
{
  "dependencies": {
    "MyOtherProject": "1.0.0-*",
    "AnotherProject": {
      "type": "project"
    }
  }
}
```

```xml
<ItemGroup>
  <ProjectReference Include="..\MyOtherProject\MyOtherProject.csproj" />
  <ProjectReference Include="..\AnotherProject\AnotherProject.csproj" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="8b654-139">Spowoduje to przerwanie `dotnet pack --version-suffix $suffix` sposobu, który określa wersję zależności odwołania do projektu.</span><span class="sxs-lookup"><span data-stu-id="8b654-139">This will break the way that `dotnet pack --version-suffix $suffix` determines the dependency version of a project reference.</span></span>

#### <a name="type-build"></a><span data-ttu-id="8b654-140">typ: kompilacja</span><span class="sxs-lookup"><span data-stu-id="8b654-140">type: build</span></span>

```json
{
  "dependencies": {
    "Microsoft.EntityFrameworkCore.Design": {
      "version": "1.1.0",
      "type": "build"
    }
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="1.1.0" PrivateAssets="All" />
</ItemGroup>
```

#### <a name="type-platform"></a><span data-ttu-id="8b654-141">typ: platforma</span><span class="sxs-lookup"><span data-stu-id="8b654-141">type: platform</span></span>

```json
{
  "dependencies": {
    "Microsoft.NETCore.App": {
      "version": "1.1.0",
      "type": "platform"
    }
  }
}
```

<span data-ttu-id="8b654-142">Nie ma odpowiednika w csproj.</span><span class="sxs-lookup"><span data-stu-id="8b654-142">There is no equivalent in csproj.</span></span>

## <a name="runtimes"></a><span data-ttu-id="8b654-143">czas pracy</span><span class="sxs-lookup"><span data-stu-id="8b654-143">runtimes</span></span>

```json
{
  "runtimes": {
    "win7-x64": {},
    "osx.10.11-x64": {},
    "ubuntu.16.04-x64": {}
  }
}
```

```xml
<PropertyGroup>
  <RuntimeIdentifiers>win7-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
</PropertyGroup>
```

### <a name="standalone-apps-self-contained-deployment"></a><span data-ttu-id="8b654-144">Aplikacje autonomiczne (wdrożenie autonomiczne)</span><span class="sxs-lookup"><span data-stu-id="8b654-144">Standalone apps (self-contained deployment)</span></span>

<span data-ttu-id="8b654-145">W programie project.json `runtimes` definiowanie sekcji oznacza, że aplikacja była samodzielna podczas tworzenia i publikowania.</span><span class="sxs-lookup"><span data-stu-id="8b654-145">In project.json, defining a `runtimes` section means the app was standalone during build and publish.</span></span>
<span data-ttu-id="8b654-146">W MSBuild wszystkie projekty są *przenośne* podczas kompilacji, ale mogą być publikowane jako autonomiczne.</span><span class="sxs-lookup"><span data-stu-id="8b654-146">In MSBuild, all projects are *portable* during build, but can be published as standalone.</span></span>

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

<span data-ttu-id="8b654-147">Aby uzyskać więcej informacji, zobacz [Samodzielne wdrożenia (SCD)](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="8b654-147">For more information, see [Self-contained deployments (SCD)](../deploying/index.md#publish-self-contained).</span></span>

## <a name="tools"></a><span data-ttu-id="8b654-148">narzędzia</span><span class="sxs-lookup"><span data-stu-id="8b654-148">tools</span></span>

```json
{
  "tools": {
    "Microsoft.EntityFrameworkCore.Tools.DotNet": "1.0.0-*"
  }
}
```

```xml
<ItemGroup>
  <DotNetCliToolReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="1.0.0" />
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="8b654-149">`imports`na narzędzia nie są obsługiwane w csproj.</span><span class="sxs-lookup"><span data-stu-id="8b654-149">`imports` on tools are not supported in csproj.</span></span> <span data-ttu-id="8b654-150">Narzędzia wymagające importu nie będą działać z nowym `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="8b654-150">Tools that need imports will not work with the new `Microsoft.NET.Sdk`.</span></span>

## <a name="buildoptions"></a><span data-ttu-id="8b654-151">opcje kompilacji</span><span class="sxs-lookup"><span data-stu-id="8b654-151">buildOptions</span></span>

<span data-ttu-id="8b654-152">Zobacz też [Pliki](#files).</span><span class="sxs-lookup"><span data-stu-id="8b654-152">See also [Files](#files).</span></span>

### <a name="emitentrypoint"></a><span data-ttu-id="8b654-153">emitEntryPoint</span><span class="sxs-lookup"><span data-stu-id="8b654-153">emitEntryPoint</span></span>

```json
{
  "buildOptions": {
    "emitEntryPoint": true
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="8b654-154">Jeśli `emitEntryPoint` `false`był , `OutputType` wartość jest `Library`konwertowana na , która jest wartością domyślną:</span><span class="sxs-lookup"><span data-stu-id="8b654-154">If `emitEntryPoint` was `false`, the value of `OutputType` is converted to `Library`, which is the default value:</span></span>

```json
{
  "buildOptions": {
    "emitEntryPoint": false
  }
}
```

```xml
<PropertyGroup>
  <OutputType>Library</OutputType>
  <!-- or, omit altogether. It defaults to 'Library' -->
</PropertyGroup>
```

### <a name="keyfile"></a><span data-ttu-id="8b654-155">Keyfile</span><span class="sxs-lookup"><span data-stu-id="8b654-155">keyFile</span></span>

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

<span data-ttu-id="8b654-156">Element `keyFile` rozszerza się do trzech właściwości w MSBuild:</span><span class="sxs-lookup"><span data-stu-id="8b654-156">The `keyFile` element expands to three properties in MSBuild:</span></span>

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a><span data-ttu-id="8b654-157">Inne typowe opcje kompilacji</span><span class="sxs-lookup"><span data-stu-id="8b654-157">Other common build options</span></span>

```json
{
  "buildOptions": {
    "warningsAsErrors": true,
    "nowarn": ["CS0168", "CS0219"],
    "xmlDoc": true,
    "preserveCompilationContext": true,
    "outputName": "Different.AssemblyName",
    "debugType": "portable",
    "allowUnsafe": true,
    "define": ["TEST", "OTHERCONDITION"]
  }
}
```

```xml
<PropertyGroup>
  <TreatWarningsAsErrors>true</TreatWarningsAsErrors>
  <NoWarn>$(NoWarn);CS0168;CS0219</NoWarn>
  <GenerateDocumentationFile>true</GenerateDocumentationFile>
  <PreserveCompilationContext>true</PreserveCompilationContext>
  <AssemblyName>Different.AssemblyName</AssemblyName>
  <DebugType>portable</DebugType>
  <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  <DefineConstants>$(DefineConstants);TEST;OTHERCONDITION</DefineConstants>
</PropertyGroup>
```

## <a name="packoptions"></a><span data-ttu-id="8b654-158">opcje pakietów</span><span class="sxs-lookup"><span data-stu-id="8b654-158">packOptions</span></span>

<span data-ttu-id="8b654-159">Zobacz też [Pliki](#files).</span><span class="sxs-lookup"><span data-stu-id="8b654-159">See also [Files](#files).</span></span>

### <a name="common-pack-options"></a><span data-ttu-id="8b654-160">Typowe opcje pakietów</span><span class="sxs-lookup"><span data-stu-id="8b654-160">Common pack options</span></span>

```json
{
  "packOptions": {
    "summary": "numl is a machine learning library intended to ease the use of using standard modeling techniques for both prediction and clustering.",
    "tags": ["machine learning", "framework"],
    "releaseNotes": "Version 0.9.12-beta",
    "iconUrl": "http://numl.net/images/ico.png",
    "projectUrl": "http://numl.net",
    "licenseUrl": "https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md",
    "requireLicenseAcceptance": false,
    "repository": {
      "type": "git",
      "url": "https://raw.githubusercontent.com/sethjuarez/numl"
    },
    "owners": ["Seth Juarez"]
  }
}
```

```xml
<PropertyGroup>
  <!-- summary is not migrated from project.json, but you can use the <Description> property for that if needed. -->
  <PackageTags>machine learning;framework</PackageTags>
  <PackageReleaseNotes>Version 0.9.12-beta</PackageReleaseNotes>
  <PackageIconUrl>http://numl.net/images/ico.png</PackageIconUrl>
  <PackageProjectUrl>http://numl.net</PackageProjectUrl>
  <PackageLicenseUrl>https://raw.githubusercontent.com/sethjuarez/numl/master/LICENSE.md</PackageLicenseUrl>
  <PackageRequireLicenseAcceptance>false</PackageRequireLicenseAcceptance>
  <RepositoryType>git</RepositoryType>
  <RepositoryUrl>https://raw.githubusercontent.com/sethjuarez/numl</RepositoryUrl>
  <!-- owners is not supported in MSBuild -->
</PropertyGroup>
```

<span data-ttu-id="8b654-161">Nie ma odpowiednika `owners` dla elementu w MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8b654-161">There is no equivalent for the `owners` element in MSBuild.</span></span>
<span data-ttu-id="8b654-162">Dla `summary`, można użyć `<Description>` MSBuild właściwości, mimo `summary` że wartość nie jest migrowana automatycznie do tej [`description`](#other-common-root-level-options) właściwości, ponieważ ta właściwość jest mapowana do elementu.</span><span class="sxs-lookup"><span data-stu-id="8b654-162">For `summary`, you can use the MSBuild `<Description>` property, even though the value of `summary` is not migrated automatically to that property, since that property is mapped to the [`description`](#other-common-root-level-options) element.</span></span>

## <a name="scripts"></a><span data-ttu-id="8b654-163">skrypty</span><span class="sxs-lookup"><span data-stu-id="8b654-163">scripts</span></span>

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

<span data-ttu-id="8b654-164">Ich odpowiednikiem w MSBuild są [cele:](/visualstudio/msbuild/msbuild-targets)</span><span class="sxs-lookup"><span data-stu-id="8b654-164">Their equivalent in MSBuild are [targets](/visualstudio/msbuild/msbuild-targets):</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```

## <a name="runtimeoptions"></a><span data-ttu-id="8b654-165">opcje czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="8b654-165">runtimeOptions</span></span>

```json
{
  "runtimeOptions": {
    "configProperties": {
      "System.GC.Server": true,
      "System.GC.Concurrent": true,
      "System.GC.RetainVM": true,
      "System.Threading.ThreadPool.MinThreads": 4,
      "System.Threading.ThreadPool.MaxThreads": 25
    }
  }
}
```

<span data-ttu-id="8b654-166">Wszystkie ustawienia w tej grupie, z wyjątkiem właściwości "System.GC.Server", są umieszczane w pliku o nazwie *runtimeconfig.template.json* w folderze projektu, z opcjami podniesionymi do obiektu głównego podczas procesu migracji:</span><span class="sxs-lookup"><span data-stu-id="8b654-166">All settings in this group, except for the "System.GC.Server" property, are placed into a file called *runtimeconfig.template.json* in the project folder, with options lifted to the root object during the migration process:</span></span>

```json
{
  "configProperties": {
    "System.GC.Concurrent": true,
    "System.GC.RetainVM": true,
    "System.Threading.ThreadPool.MinThreads": 4,
    "System.Threading.ThreadPool.MaxThreads": 25
  }
}
```

<span data-ttu-id="8b654-167">Właściwość "System.GC.Server" jest migrowana do pliku csproj:</span><span class="sxs-lookup"><span data-stu-id="8b654-167">The "System.GC.Server" property is migrated into the csproj file:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

<span data-ttu-id="8b654-168">Można jednak ustawić wszystkie te wartości w csproj, a także właściwości MSBuild:</span><span class="sxs-lookup"><span data-stu-id="8b654-168">However, you can set all those values in the csproj as well as MSBuild properties:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a><span data-ttu-id="8b654-169">udostępnione</span><span class="sxs-lookup"><span data-stu-id="8b654-169">shared</span></span>

```json
{
  "shared": "shared/**/*.cs"
}
```

<span data-ttu-id="8b654-170">Nie obsługiwane w csproj.</span><span class="sxs-lookup"><span data-stu-id="8b654-170">Not supported in csproj.</span></span> <span data-ttu-id="8b654-171">Zamiast tego należy utworzyć pliki zawartości dołączane w pliku *nuspec.*</span><span class="sxs-lookup"><span data-stu-id="8b654-171">You must instead create include content files in your *.nuspec* file.</span></span>
<span data-ttu-id="8b654-172">Aby uzyskać więcej informacji, zobacz [Dołączanie plików zawartości](/nuget/schema/nuspec#including-content-files).</span><span class="sxs-lookup"><span data-stu-id="8b654-172">For more information, see [Including content files](/nuget/schema/nuspec#including-content-files).</span></span>

## <a name="files"></a><span data-ttu-id="8b654-173">files</span><span class="sxs-lookup"><span data-stu-id="8b654-173">files</span></span>

<span data-ttu-id="8b654-174">W *programie project.json*kompilacja i pakiet można rozszerzyć na kompilację i osadzanie z różnych folderów.</span><span class="sxs-lookup"><span data-stu-id="8b654-174">In *project.json*, build and pack could be extended to compile and embed from different folders.</span></span>
<span data-ttu-id="8b654-175">W MSBuild odbywa się to przy użyciu [elementów](/visualstudio/msbuild/common-msbuild-project-items).</span><span class="sxs-lookup"><span data-stu-id="8b654-175">In MSBuild, this is done using [items](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="8b654-176">Poniższy przykład jest wspólną konwersją:</span><span class="sxs-lookup"><span data-stu-id="8b654-176">The following example is a common conversion:</span></span>

```json
{
  "buildOptions": {
    "compile": {
      "copyToOutput": "notes.txt",
      "include": "../Shared/*.cs",
      "exclude": "../Shared/Not/*.cs"
    },
    "embed": {
      "include": "../Shared/*.resx"
    }
  },
  "packOptions": {
    "include": "Views/",
    "mappings": {
      "some/path/in/project.txt": "in/package.txt"
    }
  },
  "publishOptions": {
    "include": [
      "files/",
      "publishnotes.txt"
    ]
  }
}
```

```xml
<ItemGroup>
  <Compile Include="..\Shared\*.cs" Exclude="..\Shared\Not\*.cs" />
  <EmbeddedResource Include="..\Shared\*.resx" />
  <Content Include="Views\**\*" PackagePath="%(Identity)" />
  <None Include="some/path/in/project.txt" Pack="true" PackagePath="in/package.txt" />
  
  <None Include="notes.txt" CopyToOutputDirectory="Always" />
  <!-- CopyToOutputDirectory = { Always, PreserveNewest, Never } -->

  <Content Include="files\**\*" CopyToPublishDirectory="PreserveNewest" />
  <None Include="publishnotes.txt" CopyToPublishDirectory="Always" />
  <!-- CopyToPublishDirectory = { Always, PreserveNewest, Never } -->
</ItemGroup>
```

> [!NOTE]
> <span data-ttu-id="8b654-177">Wiele domyślnych [wzorców globbing](https://en.wikipedia.org/wiki/Glob_(programming)) ulatniania jest dodawanych automatycznie przez zestaw SDK .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8b654-177">Many of the default [globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are added automatically by the .NET Core SDK.</span></span>
> <span data-ttu-id="8b654-178">Aby uzyskać więcej informacji, zobacz [Domyślne kompilowanie wartości elementów](https://aka.ms/sdkimplicititems).</span><span class="sxs-lookup"><span data-stu-id="8b654-178">For more information, see [Default Compile Item Values](https://aka.ms/sdkimplicititems).</span></span>

<span data-ttu-id="8b654-179">Wszystkie elementy `ItemGroup` MSBuild `Exclude`obsługują `Remove` `Include`, i .</span><span class="sxs-lookup"><span data-stu-id="8b654-179">All MSBuild `ItemGroup` elements support `Include`, `Exclude`, and `Remove`.</span></span>

<span data-ttu-id="8b654-180">Układ pakietu wewnątrz .nupkg można `PackagePath="path"`modyfikować za pomocą .</span><span class="sxs-lookup"><span data-stu-id="8b654-180">Package layout inside the .nupkg can be modified with `PackagePath="path"`.</span></span>

<span data-ttu-id="8b654-181">Z `Content`wyjątkiem , większość grup `Pack="true"` elementów wymaga jawnego dodawania, aby zostać uwzględnionymi w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="8b654-181">Except for `Content`, most item groups require explicitly adding `Pack="true"` to be included in the package.</span></span> <span data-ttu-id="8b654-182">`Content`zostaną wprowadzone do folderu *zawartości* w pakiecie, ponieważ właściwość MSBuild `<IncludeContentInPack>` jest `true` ustawiona domyślnie.</span><span class="sxs-lookup"><span data-stu-id="8b654-182">`Content` will be put in the *content* folder in a package since the MSBuild `<IncludeContentInPack>` property is set to `true` by default.</span></span>
<span data-ttu-id="8b654-183">Aby uzyskać więcej informacji, zobacz [Dołączanie zawartości do pakietu](/nuget/schema/msbuild-targets#including-content-in-a-package).</span><span class="sxs-lookup"><span data-stu-id="8b654-183">For more information, see [Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package).</span></span>

<span data-ttu-id="8b654-184">`PackagePath="%(Identity)"`jest krótki sposób ustawiania ścieżki pakietu do ścieżki pliku względnej projektu.</span><span class="sxs-lookup"><span data-stu-id="8b654-184">`PackagePath="%(Identity)"` is a short way of setting package path to the project-relative file path.</span></span>

## <a name="testrunner"></a><span data-ttu-id="8b654-185">testRunner</span><span class="sxs-lookup"><span data-stu-id="8b654-185">testRunner</span></span>

### <a name="xunit"></a><span data-ttu-id="8b654-186">Xunit</span><span class="sxs-lookup"><span data-stu-id="8b654-186">xUnit</span></span>

```json
{
  "testRunner": "xunit",
  "dependencies": {
    "dotnet-test-xunit": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="xunit" Version="2.2.0-*" />
  <PackageReference Include="xunit.runner.visualstudio" Version="2.2.0-*" />
</ItemGroup>
```

### <a name="mstest"></a><span data-ttu-id="8b654-187">MSTest</span><span class="sxs-lookup"><span data-stu-id="8b654-187">MSTest</span></span>

```json
{
  "testRunner": "mstest",
  "dependencies": {
    "dotnet-test-mstest": "<any>"
  }
}
```

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="15.0.0-*" />
  <PackageReference Include="MSTest.TestAdapter" Version="1.1.12-*" />
  <PackageReference Include="MSTest.TestFramework" Version="1.1.11-*" />
</ItemGroup>
```

## <a name="see-also"></a><span data-ttu-id="8b654-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b654-188">See also</span></span>

- [<span data-ttu-id="8b654-189">Ogólny przegląd zmian w cli</span><span class="sxs-lookup"><span data-stu-id="8b654-189">High-level overview of changes in CLI</span></span>](../tools/cli-msbuild-architecture.md)
