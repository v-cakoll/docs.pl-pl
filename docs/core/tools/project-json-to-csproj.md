---
title: Porównanie Project. JSON i csproj
description: Zobacz mapowanie między elementami Project. JSON i csproj.
author: natemcmaster
ms.date: 03/13/2017
ms.openlocfilehash: abe515007b47b415ac33e3350a29edced1784d68
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451108"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a><span data-ttu-id="10508-103">Mapowanie między właściwościami Project. JSON i csproj</span><span class="sxs-lookup"><span data-stu-id="10508-103">A mapping between project.json and csproj properties</span></span>

<span data-ttu-id="10508-104">Według [McMaster](https://github.com/natemcmaster)</span><span class="sxs-lookup"><span data-stu-id="10508-104">By [Nate McMaster](https://github.com/natemcmaster)</span></span>

<span data-ttu-id="10508-105">Podczas opracowywania narzędzi programu .NET Core wprowadzono ważną zmianę projektową, która nie obsługuje już plików *Project. JSON* , a zamiast tego przenosi projekty .NET Core do formatu MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="10508-105">During the development of the .NET Core tooling, an important design change was made to no longer support *project.json* files and instead move the .NET Core projects to the MSBuild/csproj format.</span></span>

<span data-ttu-id="10508-106">W tym artykule przedstawiono sposób, w jaki ustawienia w pliku *Project. JSON* są reprezentowane w formacie MSBuild/csproj, dzięki czemu można dowiedzieć się, jak używać nowego formatu i zrozumieć zmiany wprowadzone przez narzędzia migracji w przypadku uaktualniania projektu do najnowszej wersji narzędzi.</span><span class="sxs-lookup"><span data-stu-id="10508-106">This article shows how the settings in *project.json* are represented in the MSBuild/csproj format so you can learn how to use the new format and understand the changes made by the migration tools when you're upgrading your project to the latest version of the tooling.</span></span>

## <a name="the-csproj-format"></a><span data-ttu-id="10508-107">Format csproj</span><span class="sxs-lookup"><span data-stu-id="10508-107">The csproj format</span></span>

<span data-ttu-id="10508-108">Nowy format, \*. csproj, jest formatem opartym na formacie XML.</span><span class="sxs-lookup"><span data-stu-id="10508-108">The new format, \*.csproj, is an XML-based format.</span></span> <span data-ttu-id="10508-109">Poniższy przykład przedstawia węzeł główny projektu .NET Core przy użyciu `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="10508-109">The following example shows the root node of a .NET Core project using the `Microsoft.NET.Sdk`.</span></span> <span data-ttu-id="10508-110">W przypadku projektów sieci Web używany zestaw SDK jest `Microsoft.NET.Sdk.Web`.</span><span class="sxs-lookup"><span data-stu-id="10508-110">For web projects, the SDK used is `Microsoft.NET.Sdk.Web`.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a><span data-ttu-id="10508-111">Wspólne właściwości najwyższego poziomu</span><span class="sxs-lookup"><span data-stu-id="10508-111">Common top-level properties</span></span>

### <a name="name"></a><span data-ttu-id="10508-112">name</span><span class="sxs-lookup"><span data-stu-id="10508-112">name</span></span>

```json
{
  "name": "MyProjectName"
}
```

<span data-ttu-id="10508-113">Nie jest już obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="10508-113">No longer supported.</span></span> <span data-ttu-id="10508-114">W csproj jest to określane przez nazwę pliku projektu, która zwykle jest zgodna z nazwą katalogu.</span><span class="sxs-lookup"><span data-stu-id="10508-114">In csproj, this is determined by the project filename, which usually matches the directory name.</span></span> <span data-ttu-id="10508-115">Na przykład `MyProjectName.csproj`.</span><span class="sxs-lookup"><span data-stu-id="10508-115">For example, `MyProjectName.csproj`.</span></span>

<span data-ttu-id="10508-116">Domyślnie nazwa pliku projektu określa również wartość właściwości `<AssemblyName>` i `<PackageId>`.</span><span class="sxs-lookup"><span data-stu-id="10508-116">By default, the project filename also specifies the value of the `<AssemblyName>` and `<PackageId>` properties.</span></span>

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

<span data-ttu-id="10508-117">`<AssemblyName>` będzie miała inną wartość niż `<PackageId>`, jeśli właściwość `buildOptions\outputName` została zdefiniowana w pliku Project. JSON.</span><span class="sxs-lookup"><span data-stu-id="10508-117">The `<AssemblyName>` will have a different value than `<PackageId>` if `buildOptions\outputName` property was defined in project.json.</span></span>
<span data-ttu-id="10508-118">Aby uzyskać więcej informacji, zobacz [inne typowe opcje kompilacji](#other-common-build-options).</span><span class="sxs-lookup"><span data-stu-id="10508-118">For more information, see [Other common build options](#other-common-build-options).</span></span>

### <a name="version"></a><span data-ttu-id="10508-119">version</span><span class="sxs-lookup"><span data-stu-id="10508-119">version</span></span>

```json
{
  "version": "1.0.0-alpha-*"
}
```

<span data-ttu-id="10508-120">Użyj właściwości `VersionPrefix` i `VersionSuffix`:</span><span class="sxs-lookup"><span data-stu-id="10508-120">Use the `VersionPrefix` and `VersionSuffix` properties:</span></span>

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

<span data-ttu-id="10508-121">Można również użyć właściwości `Version`, ale może to spowodować zastąpienie ustawień wersji podczas pakowania:</span><span class="sxs-lookup"><span data-stu-id="10508-121">You can also use the `Version` property, but this may override version settings during packaging:</span></span>

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a><span data-ttu-id="10508-122">Inne typowe opcje poziomu głównego</span><span class="sxs-lookup"><span data-stu-id="10508-122">Other common root-level options</span></span>

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

## <a name="frameworks"></a><span data-ttu-id="10508-123">platform</span><span class="sxs-lookup"><span data-stu-id="10508-123">frameworks</span></span>

### <a name="one-target-framework"></a><span data-ttu-id="10508-124">Jedna platforma docelowa</span><span class="sxs-lookup"><span data-stu-id="10508-124">One target framework</span></span>

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

### <a name="multiple-target-frameworks"></a><span data-ttu-id="10508-125">Wiele platform docelowych</span><span class="sxs-lookup"><span data-stu-id="10508-125">Multiple target frameworks</span></span>

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

<span data-ttu-id="10508-126">Użyj właściwości `TargetFrameworks`, aby zdefiniować listę platform docelowych.</span><span class="sxs-lookup"><span data-stu-id="10508-126">Use the `TargetFrameworks` property to define your list of target frameworks.</span></span> <span data-ttu-id="10508-127">Użyj średnika, aby oddzielić wiele wartości struktury.</span><span class="sxs-lookup"><span data-stu-id="10508-127">Use semi-colon to separate multiple framework values.</span></span>

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a><span data-ttu-id="10508-128">zależności</span><span class="sxs-lookup"><span data-stu-id="10508-128">dependencies</span></span>

> [!IMPORTANT]
> <span data-ttu-id="10508-129">Jeśli zależność jest **projektem** , a nie pakietem, format jest inny.</span><span class="sxs-lookup"><span data-stu-id="10508-129">If the dependency is a **project** and not a package, the format is different.</span></span>
> <span data-ttu-id="10508-130">Aby uzyskać więcej informacji, zobacz sekcję [Typ zależności](#dependency-type) .</span><span class="sxs-lookup"><span data-stu-id="10508-130">For more information, see the [dependency type](#dependency-type) section.</span></span>

### <a name="netstandardlibrary-metapackage"></a><span data-ttu-id="10508-131">Biblioteka servicepackage. Library</span><span class="sxs-lookup"><span data-stu-id="10508-131">NETStandard.Library metapackage</span></span>

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

### <a name="microsoftnetcoreapp-metapackage"></a><span data-ttu-id="10508-132">Pakiet Microsoft. servicecore. App</span><span class="sxs-lookup"><span data-stu-id="10508-132">Microsoft.NETCore.App metapackage</span></span>

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

<span data-ttu-id="10508-133">Należy zauważyć, że wartość `<RuntimeFrameworkVersion>` w migrowanym projekcie jest określona przez zainstalowaną wersję zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="10508-133">Note that the `<RuntimeFrameworkVersion>` value in the migrated project is determined by the version of the SDK you have installed.</span></span>

### <a name="top-level-dependencies"></a><span data-ttu-id="10508-134">Zależności najwyższego poziomu</span><span class="sxs-lookup"><span data-stu-id="10508-134">Top-level dependencies</span></span>

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

### <a name="per-framework-dependencies"></a><span data-ttu-id="10508-135">Zależności dla architektury</span><span class="sxs-lookup"><span data-stu-id="10508-135">Per-framework dependencies</span></span>

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

### <a name="imports"></a><span data-ttu-id="10508-136">importy</span><span class="sxs-lookup"><span data-stu-id="10508-136">imports</span></span>

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

### <a name="dependency-type"></a><span data-ttu-id="10508-137">Typ zależności</span><span class="sxs-lookup"><span data-stu-id="10508-137">dependency type</span></span>

#### <a name="type-project"></a><span data-ttu-id="10508-138">Typ: projekt</span><span class="sxs-lookup"><span data-stu-id="10508-138">type: project</span></span>

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
> <span data-ttu-id="10508-139">Spowoduje to przerwanie sposobu, w jaki `dotnet pack --version-suffix $suffix` określa wersję zależności odwołania do projektu.</span><span class="sxs-lookup"><span data-stu-id="10508-139">This will break the way that `dotnet pack --version-suffix $suffix` determines the dependency version of a project reference.</span></span>

#### <a name="type-build"></a><span data-ttu-id="10508-140">Typ: kompilacja</span><span class="sxs-lookup"><span data-stu-id="10508-140">type: build</span></span>

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

#### <a name="type-platform"></a><span data-ttu-id="10508-141">Typ: platforma</span><span class="sxs-lookup"><span data-stu-id="10508-141">type: platform</span></span>

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

<span data-ttu-id="10508-142">Nie ma odpowiednika w csproj.</span><span class="sxs-lookup"><span data-stu-id="10508-142">There is no equivalent in csproj.</span></span>

## <a name="runtimes"></a><span data-ttu-id="10508-143">Runtime</span><span class="sxs-lookup"><span data-stu-id="10508-143">runtimes</span></span>

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

### <a name="standalone-apps-self-contained-deployment"></a><span data-ttu-id="10508-144">Aplikacje autonomiczne (wdrażanie samodzielne)</span><span class="sxs-lookup"><span data-stu-id="10508-144">Standalone apps (self-contained deployment)</span></span>

<span data-ttu-id="10508-145">W pliku Project. JSON Definiowanie `runtimes` sekcji oznacza, że aplikacja była autonomiczna podczas kompilowania i publikowania.</span><span class="sxs-lookup"><span data-stu-id="10508-145">In project.json, defining a `runtimes` section means the app was standalone during build and publish.</span></span>
<span data-ttu-id="10508-146">W programie MSBuild wszystkie projekty są *przenośne* podczas kompilacji, ale można je opublikować jako autonomiczną.</span><span class="sxs-lookup"><span data-stu-id="10508-146">In MSBuild, all projects are *portable* during build, but can be published as standalone.</span></span>

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

<span data-ttu-id="10508-147">Aby uzyskać więcej informacji, zobacz artykuły [z obsługą prewartą (SCD)](../deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="10508-147">For more information, see [Self-contained deployments (SCD)](../deploying/index.md#publish-self-contained).</span></span>

## <a name="tools"></a><span data-ttu-id="10508-148">narzędzia</span><span class="sxs-lookup"><span data-stu-id="10508-148">tools</span></span>

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
> <span data-ttu-id="10508-149">`imports` w narzędziach nie są obsługiwane w csproj.</span><span class="sxs-lookup"><span data-stu-id="10508-149">`imports` on tools are not supported in csproj.</span></span> <span data-ttu-id="10508-150">Narzędzia, które wymagają importu, nie będą działały z nowym `Microsoft.NET.Sdk`.</span><span class="sxs-lookup"><span data-stu-id="10508-150">Tools that need imports will not work with the new `Microsoft.NET.Sdk`.</span></span>

## <a name="buildoptions"></a><span data-ttu-id="10508-151">buildOptions</span><span class="sxs-lookup"><span data-stu-id="10508-151">buildOptions</span></span>

<span data-ttu-id="10508-152">Zobacz również [pliki](#files).</span><span class="sxs-lookup"><span data-stu-id="10508-152">See also [Files](#files).</span></span>

### <a name="emitentrypoint"></a><span data-ttu-id="10508-153">emitEntryPoint</span><span class="sxs-lookup"><span data-stu-id="10508-153">emitEntryPoint</span></span>

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

<span data-ttu-id="10508-154">Jeśli `emitEntryPoint` było `false`, wartość `OutputType` jest konwertowana na `Library`, która jest wartością domyślną:</span><span class="sxs-lookup"><span data-stu-id="10508-154">If `emitEntryPoint` was `false`, the value of `OutputType` is converted to `Library`, which is the default value:</span></span>

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

### <a name="keyfile"></a><span data-ttu-id="10508-155">keyFile</span><span class="sxs-lookup"><span data-stu-id="10508-155">keyFile</span></span>

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

<span data-ttu-id="10508-156">Element `keyFile` rozwija do trzech właściwości w programie MSBuild:</span><span class="sxs-lookup"><span data-stu-id="10508-156">The `keyFile` element expands to three properties in MSBuild:</span></span>

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a><span data-ttu-id="10508-157">Inne typowe opcje kompilacji</span><span class="sxs-lookup"><span data-stu-id="10508-157">Other common build options</span></span>

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

## <a name="packoptions"></a><span data-ttu-id="10508-158">packOptions</span><span class="sxs-lookup"><span data-stu-id="10508-158">packOptions</span></span>

<span data-ttu-id="10508-159">Zobacz również [pliki](#files).</span><span class="sxs-lookup"><span data-stu-id="10508-159">See also [Files](#files).</span></span>

### <a name="common-pack-options"></a><span data-ttu-id="10508-160">Opcje wspólnego pakietu</span><span class="sxs-lookup"><span data-stu-id="10508-160">Common pack options</span></span>

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

<span data-ttu-id="10508-161">Nie ma odpowiednika dla elementu `owners` w programie MSBuild.</span><span class="sxs-lookup"><span data-stu-id="10508-161">There is no equivalent for the `owners` element in MSBuild.</span></span>
<span data-ttu-id="10508-162">W przypadku `summary`można użyć właściwości `<Description>` MSBuild, nawet jeśli wartość `summary` nie jest automatycznie migrowana do tej właściwości, ponieważ ta właściwość jest zamapowana na element [`description`](#other-common-root-level-options) .</span><span class="sxs-lookup"><span data-stu-id="10508-162">For `summary`, you can use the MSBuild `<Description>` property, even though the value of `summary` is not migrated automatically to that property, since that property is mapped to the [`description`](#other-common-root-level-options) element.</span></span>

## <a name="scripts"></a><span data-ttu-id="10508-163">skrypty</span><span class="sxs-lookup"><span data-stu-id="10508-163">scripts</span></span>

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

<span data-ttu-id="10508-164">Ich odpowiednik w programie MSBuild jest [obiektem docelowym](/visualstudio/msbuild/msbuild-targets):</span><span class="sxs-lookup"><span data-stu-id="10508-164">Their equivalent in MSBuild are [targets](/visualstudio/msbuild/msbuild-targets):</span></span>

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```

## <a name="runtimeoptions"></a><span data-ttu-id="10508-165">runtimeOptions</span><span class="sxs-lookup"><span data-stu-id="10508-165">runtimeOptions</span></span>

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

<span data-ttu-id="10508-166">Wszystkie ustawienia w tej grupie, z wyjątkiem właściwości "System. GC. Server", są umieszczane w pliku o nazwie *runtimeconfig. Template. JSON* w folderze projektu, z opcjami podniesionymi do obiektu głównego podczas procesu migracji:</span><span class="sxs-lookup"><span data-stu-id="10508-166">All settings in this group, except for the "System.GC.Server" property, are placed into a file called *runtimeconfig.template.json* in the project folder, with options lifted to the root object during the migration process:</span></span>

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

<span data-ttu-id="10508-167">Właściwość "System. GC. Server" jest migrowana do pliku CSPROJ:</span><span class="sxs-lookup"><span data-stu-id="10508-167">The "System.GC.Server" property is migrated into the csproj file:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

<span data-ttu-id="10508-168">Można jednak ustawić wszystkie te wartości w csproj, a także właściwości programu MSBuild:</span><span class="sxs-lookup"><span data-stu-id="10508-168">However, you can set all those values in the csproj as well as MSBuild properties:</span></span>

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a><span data-ttu-id="10508-169">udostępnione</span><span class="sxs-lookup"><span data-stu-id="10508-169">shared</span></span>

```json
{
  "shared": "shared/**/*.cs"
}
```

<span data-ttu-id="10508-170">Nieobsługiwane w csproj.</span><span class="sxs-lookup"><span data-stu-id="10508-170">Not supported in csproj.</span></span> <span data-ttu-id="10508-171">Zamiast tego należy utworzyć Dołączanie plików zawartości w pliku *. nuspec* .</span><span class="sxs-lookup"><span data-stu-id="10508-171">You must instead create include content files in your *.nuspec* file.</span></span>
<span data-ttu-id="10508-172">Aby uzyskać więcej informacji, zobacz [Dołączanie plików zawartości](/nuget/schema/nuspec#including-content-files).</span><span class="sxs-lookup"><span data-stu-id="10508-172">For more information, see [Including content files](/nuget/schema/nuspec#including-content-files).</span></span>

## <a name="files"></a><span data-ttu-id="10508-173">files</span><span class="sxs-lookup"><span data-stu-id="10508-173">files</span></span>

<span data-ttu-id="10508-174">W pliku *Project. JSON*można rozszerzyć kompilację i pakiet, aby kompilować i osadzać z różnych folderów.</span><span class="sxs-lookup"><span data-stu-id="10508-174">In *project.json*, build and pack could be extended to compile and embed from different folders.</span></span>
<span data-ttu-id="10508-175">W programie MSBuild odbywa się to za pomocą [elementów](/visualstudio/msbuild/common-msbuild-project-items).</span><span class="sxs-lookup"><span data-stu-id="10508-175">In MSBuild, this is done using [items](/visualstudio/msbuild/common-msbuild-project-items).</span></span> <span data-ttu-id="10508-176">Poniższy przykład jest wspólną konwersją:</span><span class="sxs-lookup"><span data-stu-id="10508-176">The following example is a common conversion:</span></span>

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
> <span data-ttu-id="10508-177">Wiele domyślnych [wzorców obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) są automatycznie dodawane przez zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="10508-177">Many of the default [globbing patterns](https://en.wikipedia.org/wiki/Glob_(programming)) are added automatically by the .NET Core SDK.</span></span>
> <span data-ttu-id="10508-178">Aby uzyskać więcej informacji, zobacz [domyślne wartości elementu kompilowania](https://aka.ms/sdkimplicititems).</span><span class="sxs-lookup"><span data-stu-id="10508-178">For more information, see [Default Compile Item Values](https://aka.ms/sdkimplicititems).</span></span>

<span data-ttu-id="10508-179">Wszystkie elementy `ItemGroup` MSBuild obsługują `Include`, `Exclude`i `Remove`.</span><span class="sxs-lookup"><span data-stu-id="10508-179">All MSBuild `ItemGroup` elements support `Include`, `Exclude`, and `Remove`.</span></span>

<span data-ttu-id="10508-180">Układ pakietu wewnątrz. nupkg można modyfikować za pomocą `PackagePath="path"`.</span><span class="sxs-lookup"><span data-stu-id="10508-180">Package layout inside the .nupkg can be modified with `PackagePath="path"`.</span></span>

<span data-ttu-id="10508-181">Z wyjątkiem `Content`, większość grup elementów wymaga jawnie dodania `Pack="true"` do uwzględnienia w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="10508-181">Except for `Content`, most item groups require explicitly adding `Pack="true"` to be included in the package.</span></span> <span data-ttu-id="10508-182">`Content` zostanie umieszczony w folderze *zawartości* w pakiecie, ponieważ właściwość `<IncludeContentInPack>` programu MSBuild jest domyślnie ustawiona na `true`.</span><span class="sxs-lookup"><span data-stu-id="10508-182">`Content` will be put in the *content* folder in a package since the MSBuild `<IncludeContentInPack>` property is set to `true` by default.</span></span>
<span data-ttu-id="10508-183">Aby uzyskać więcej informacji, zobacz temat [uwzględnianie zawartości w pakiecie](/nuget/schema/msbuild-targets#including-content-in-a-package).</span><span class="sxs-lookup"><span data-stu-id="10508-183">For more information, see [Including content in a package](/nuget/schema/msbuild-targets#including-content-in-a-package).</span></span>

<span data-ttu-id="10508-184">`PackagePath="%(Identity)"` jest krótkim sposobem ustawiania ścieżki pakietu do ścieżki pliku względnej dla projektu.</span><span class="sxs-lookup"><span data-stu-id="10508-184">`PackagePath="%(Identity)"` is a short way of setting package path to the project-relative file path.</span></span>

## <a name="testrunner"></a><span data-ttu-id="10508-185">testRunner</span><span class="sxs-lookup"><span data-stu-id="10508-185">testRunner</span></span>

### <a name="xunit"></a><span data-ttu-id="10508-186">xUnit</span><span class="sxs-lookup"><span data-stu-id="10508-186">xUnit</span></span>

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

### <a name="mstest"></a><span data-ttu-id="10508-187">MSTest</span><span class="sxs-lookup"><span data-stu-id="10508-187">MSTest</span></span>

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

## <a name="see-also"></a><span data-ttu-id="10508-188">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10508-188">See also</span></span>

- [<span data-ttu-id="10508-189">Ogólne omówienie zmian w interfejsie wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="10508-189">High-level overview of changes in CLI</span></span>](../tools/cli-msbuild-architecture.md)
