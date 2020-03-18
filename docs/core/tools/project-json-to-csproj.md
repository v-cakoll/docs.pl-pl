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
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a>Mapowanie między project.json i csproj właściwości

Przez [Nate McMaster](https://github.com/natemcmaster)

Podczas opracowywania narzędzi .NET Core, ważną zmianę projektu została wdrożena, aby nie obsługiwać już plików *project.json* i zamiast tego przenieść projekty .NET Core do formatu MSBuild/csproj.

W tym artykule pokazano, jak ustawienia w *programie project.json* są reprezentowane w formacie MSBuild/csproj, dzięki czemu można dowiedzieć się, jak korzystać z nowego formatu i zrozumieć zmiany wprowadzone przez narzędzia migracji podczas uaktualniania projektu do najnowszej wersji narzędzi.

## <a name="the-csproj-format"></a>Format csproj

Nowy format, \*.csproj, jest formatem opartym na XML. W poniższym przykładzie przedstawiono węzeł główny projektu .NET Core przy użyciu `Microsoft.NET.Sdk`pliku . W przypadku projektów internetowych używany `Microsoft.NET.Sdk.Web`jest zestaw SDK .

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a>Typowe właściwości najwyższego poziomu

### <a name="name"></a>name

```json
{
  "name": "MyProjectName"
}
```

Nie jest już obsługiwany. W csproj jest to określane przez nazwę pliku projektu, która zwykle pasuje do nazwy katalogu. Na przykład `MyProjectName.csproj`.

Domyślnie nazwa pliku projektu określa również wartość `<AssemblyName>` `<PackageId>` i właściwości.

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

Będzie `<AssemblyName>` miał inną wartość `<PackageId>` `buildOptions\outputName` niż jeśli właściwość została zdefiniowana w project.json.
Aby uzyskać więcej informacji, zobacz [Inne typowe opcje kompilacji](#other-common-build-options).

### <a name="version"></a>version

```json
{
  "version": "1.0.0-alpha-*"
}
```

Użyj `VersionPrefix` właściwości `VersionSuffix` i właściwości:

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

Można również użyć `Version` tej właściwości, ale może to zastąpić ustawienia wersji podczas pakowania:

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a>Inne typowe opcje na poziomie głównym

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

## <a name="frameworks"></a>Ram

### <a name="one-target-framework"></a>Jedna rama docelowa

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

### <a name="multiple-target-frameworks"></a>Wiele struktur docelowych

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

Użyj `TargetFrameworks` właściwości, aby zdefiniować listę struktur docelowych. Użyj średnika, aby oddzielić wiele wartości framework.

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a>zależności

> [!IMPORTANT]
> Jeśli zależność jest **projektem,** a nie pakietem, format jest inny.
> Aby uzyskać więcej informacji, zobacz sekcję [typu zależności.](#dependency-type)

### <a name="netstandardlibrary-metapackage"></a>Pakiet metazawartości NETStandard.Library

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

### <a name="microsoftnetcoreapp-metapackage"></a>Pakiet metapakowań microsoft.NETCore.App

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

Należy zauważyć, że `<RuntimeFrameworkVersion>` wartość w zmigrowanym projekcie jest określana przez zainstalowaną wersję sdk.

### <a name="top-level-dependencies"></a>Zależności najwyższego poziomu

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

### <a name="per-framework-dependencies"></a>Zależności na framework

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

### <a name="imports"></a>importy

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

### <a name="dependency-type"></a>typ zależności

#### <a name="type-project"></a>typ: projekt

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
> Spowoduje to przerwanie `dotnet pack --version-suffix $suffix` sposobu, który określa wersję zależności odwołania do projektu.

#### <a name="type-build"></a>typ: kompilacja

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

#### <a name="type-platform"></a>typ: platforma

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

Nie ma odpowiednika w csproj.

## <a name="runtimes"></a>czas pracy

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

### <a name="standalone-apps-self-contained-deployment"></a>Aplikacje autonomiczne (wdrożenie autonomiczne)

W programie project.json `runtimes` definiowanie sekcji oznacza, że aplikacja była samodzielna podczas tworzenia i publikowania.
W MSBuild wszystkie projekty są *przenośne* podczas kompilacji, ale mogą być publikowane jako autonomiczne.

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

Aby uzyskać więcej informacji, zobacz [Samodzielne wdrożenia (SCD)](../deploying/index.md#publish-self-contained).

## <a name="tools"></a>narzędzia

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
> `imports`na narzędzia nie są obsługiwane w csproj. Narzędzia wymagające importu nie będą działać z nowym `Microsoft.NET.Sdk`.

## <a name="buildoptions"></a>opcje kompilacji

Zobacz też [Pliki](#files).

### <a name="emitentrypoint"></a>emitEntryPoint

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

Jeśli `emitEntryPoint` `false`był , `OutputType` wartość jest `Library`konwertowana na , która jest wartością domyślną:

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

### <a name="keyfile"></a>Keyfile

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

Element `keyFile` rozszerza się do trzech właściwości w MSBuild:

```xml
<PropertyGroup>
  <AssemblyOriginatorKeyFile>MyKey.snk</AssemblyOriginatorKeyFile>
  <SignAssembly>true</SignAssembly>
  <PublicSign Condition="'$(OS)' != 'Windows_NT'">true</PublicSign>
</PropertyGroup>
```

### <a name="other-common-build-options"></a>Inne typowe opcje kompilacji

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

## <a name="packoptions"></a>opcje pakietów

Zobacz też [Pliki](#files).

### <a name="common-pack-options"></a>Typowe opcje pakietów

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

Nie ma odpowiednika `owners` dla elementu w MSBuild.
Dla `summary`, można użyć `<Description>` MSBuild właściwości, mimo `summary` że wartość nie jest migrowana automatycznie do tej [`description`](#other-common-root-level-options) właściwości, ponieważ ta właściwość jest mapowana do elementu.

## <a name="scripts"></a>skrypty

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

Ich odpowiednikiem w MSBuild są [cele:](/visualstudio/msbuild/msbuild-targets)

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```

## <a name="runtimeoptions"></a>opcje czasu wykonywania

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

Wszystkie ustawienia w tej grupie, z wyjątkiem właściwości "System.GC.Server", są umieszczane w pliku o nazwie *runtimeconfig.template.json* w folderze projektu, z opcjami podniesionymi do obiektu głównego podczas procesu migracji:

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

Właściwość "System.GC.Server" jest migrowana do pliku csproj:

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

Można jednak ustawić wszystkie te wartości w csproj, a także właściwości MSBuild:

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
  <ConcurrentGarbageCollection>true</ConcurrentGarbageCollection>
  <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  <ThreadPoolMaxThreads>25</ThreadPoolMaxThreads>
</PropertyGroup>
```

## <a name="shared"></a>udostępnione

```json
{
  "shared": "shared/**/*.cs"
}
```

Nie obsługiwane w csproj. Zamiast tego należy utworzyć pliki zawartości dołączane w pliku *nuspec.*
Aby uzyskać więcej informacji, zobacz [Dołączanie plików zawartości](/nuget/schema/nuspec#including-content-files).

## <a name="files"></a>files

W *programie project.json*kompilacja i pakiet można rozszerzyć na kompilację i osadzanie z różnych folderów.
W MSBuild odbywa się to przy użyciu [elementów](/visualstudio/msbuild/common-msbuild-project-items). Poniższy przykład jest wspólną konwersją:

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
> Wiele domyślnych [wzorców globbing](https://en.wikipedia.org/wiki/Glob_(programming)) ulatniania jest dodawanych automatycznie przez zestaw SDK .NET Core.
> Aby uzyskać więcej informacji, zobacz [Domyślne kompilowanie wartości elementów](https://aka.ms/sdkimplicititems).

Wszystkie elementy `ItemGroup` MSBuild `Exclude`obsługują `Remove` `Include`, i .

Układ pakietu wewnątrz .nupkg można `PackagePath="path"`modyfikować za pomocą .

Z `Content`wyjątkiem , większość grup `Pack="true"` elementów wymaga jawnego dodawania, aby zostać uwzględnionymi w pakiecie. `Content`zostaną wprowadzone do folderu *zawartości* w pakiecie, ponieważ właściwość MSBuild `<IncludeContentInPack>` jest `true` ustawiona domyślnie.
Aby uzyskać więcej informacji, zobacz [Dołączanie zawartości do pakietu](/nuget/schema/msbuild-targets#including-content-in-a-package).

`PackagePath="%(Identity)"`jest krótki sposób ustawiania ścieżki pakietu do ścieżki pliku względnej projektu.

## <a name="testrunner"></a>testRunner

### <a name="xunit"></a>Xunit

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

### <a name="mstest"></a>MSTest

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

## <a name="see-also"></a>Zobacz też

- [Ogólny przegląd zmian w cli](../tools/cli-msbuild-architecture.md)
