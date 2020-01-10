---
title: Porównanie Project. JSON i csproj
description: Zobacz mapowanie między elementami Project. JSON i csproj.
author: natemcmaster
ms.date: 03/13/2017
ms.openlocfilehash: c31590cf34990867b81af4d073846c2952928798
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714131"
---
# <a name="a-mapping-between-projectjson-and-csproj-properties"></a>Mapowanie między właściwościami Project. JSON i csproj

Według [McMaster](https://github.com/natemcmaster)

Podczas opracowywania narzędzi programu .NET Core wprowadzono ważną zmianę projektową, która nie obsługuje już plików *Project. JSON* , a zamiast tego przenosi projekty .NET Core do formatu MSBuild/csproj.

W tym artykule przedstawiono sposób, w jaki ustawienia w pliku *Project. JSON* są reprezentowane w formacie MSBuild/csproj, dzięki czemu można dowiedzieć się, jak używać nowego formatu i zrozumieć zmiany wprowadzone przez narzędzia migracji w przypadku uaktualniania projektu do najnowszej wersji narzędzi.

## <a name="the-csproj-format"></a>Format csproj

Nowy format, \*. csproj, jest formatem opartym na formacie XML. Poniższy przykład przedstawia węzeł główny projektu .NET Core przy użyciu `Microsoft.NET.Sdk`. W przypadku projektów sieci Web używany zestaw SDK jest `Microsoft.NET.Sdk.Web`.

```xml
<Project Sdk="Microsoft.NET.Sdk">
...
</Project>
```

## <a name="common-top-level-properties"></a>Wspólne właściwości najwyższego poziomu

### <a name="name"></a>{1&gt;nazwa&lt;1}

```json
{
  "name": "MyProjectName"
}
```

Nie jest już obsługiwane. W csproj jest to określane przez nazwę pliku projektu, która zwykle jest zgodna z nazwą katalogu. Na przykład `MyProjectName.csproj`.

Domyślnie nazwa pliku projektu określa również wartość właściwości `<AssemblyName>` i `<PackageId>`.

```xml
<PropertyGroup>
  <AssemblyName>MyProjectName</AssemblyName>
  <PackageId>MyProjectName</PackageId>
</PropertyGroup>
```

`<AssemblyName>` będzie miała inną wartość niż `<PackageId>`, jeśli właściwość `buildOptions\outputName` została zdefiniowana w pliku Project. JSON.
Aby uzyskać więcej informacji, zobacz [inne typowe opcje kompilacji](#other-common-build-options).

### <a name="version"></a>Wersja programu

```json
{
  "version": "1.0.0-alpha-*"
}
```

Użyj właściwości `VersionPrefix` i `VersionSuffix`:

```xml
<PropertyGroup>
  <VersionPrefix>1.0.0</VersionPrefix>
  <VersionSuffix>alpha</VersionSuffix>
</PropertyGroup>
```

Można również użyć właściwości `Version`, ale może to spowodować zastąpienie ustawień wersji podczas pakowania:

```xml
<PropertyGroup>
  <Version>1.0.0-alpha</Version>
</PropertyGroup>
```

### <a name="other-common-root-level-options"></a>Inne typowe opcje poziomu głównego

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

## <a name="frameworks"></a>platform

### <a name="one-target-framework"></a>Jedna platforma docelowa

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

### <a name="multiple-target-frameworks"></a>Wiele platform docelowych

```json
{
  "frameworks": {
    "netcoreapp1.0": {},
    "net451": {}
  }
}
```

Użyj właściwości `TargetFrameworks`, aby zdefiniować listę platform docelowych. Użyj średnika, aby oddzielić wiele wartości struktury.

```xml
<PropertyGroup>
  <TargetFrameworks>netcoreapp1.0;net451</TargetFrameworks>
</PropertyGroup>
```

## <a name="dependencies"></a>zależności

> [!IMPORTANT]
> Jeśli zależność jest **projektem** , a nie pakietem, format jest inny.
> Aby uzyskać więcej informacji, zobacz sekcję [Typ zależności](#dependency-type) .

### <a name="netstandardlibrary-metapackage"></a>Biblioteka servicepackage. Library

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

### <a name="microsoftnetcoreapp-metapackage"></a>Pakiet Microsoft. servicecore. App

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

Należy zauważyć, że wartość `<RuntimeFrameworkVersion>` w migrowanym projekcie jest określona przez zainstalowaną wersję zestawu SDK.

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

### <a name="per-framework-dependencies"></a>Zależności dla architektury

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

### <a name="dependency-type"></a>Typ zależności

#### <a name="type-project"></a>Typ: projekt

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
> Spowoduje to przerwanie sposobu, w jaki `dotnet pack --version-suffix $suffix` określa wersję zależności odwołania do projektu.

#### <a name="type-build"></a>Typ: kompilacja

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

#### <a name="type-platform"></a>Typ: platforma

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

## <a name="runtimes"></a>Runtime

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

### <a name="standalone-apps-self-contained-deployment"></a>Aplikacje autonomiczne (wdrażanie samodzielne)

W pliku Project. JSON Definiowanie `runtimes` sekcji oznacza, że aplikacja była autonomiczna podczas kompilowania i publikowania.
W programie MSBuild wszystkie projekty są *przenośne* podczas kompilacji, ale można je opublikować jako autonomiczną.

`dotnet publish --framework netcoreapp1.0 --runtime osx.10.11-x64`

Aby uzyskać więcej informacji, zobacz artykuły [z obsługą prewartą (SCD)](../deploying/index.md#self-contained-deployments-scd).

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
> `imports` w narzędziach nie są obsługiwane w csproj. Narzędzia, które wymagają importu, nie będą działały z nowym `Microsoft.NET.Sdk`.

## <a name="buildoptions"></a>buildOptions

Zobacz również [pliki](#files).

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

Jeśli `emitEntryPoint` było `false`, wartość `OutputType` jest konwertowana na `Library`, która jest wartością domyślną:

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

### <a name="keyfile"></a>keyFile

```json
{
  "buildOptions": {
    "keyFile": "MyKey.snk"
  }
}
```

Element `keyFile` rozwija do trzech właściwości w programie MSBuild:

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

## <a name="packoptions"></a>packOptions

Zobacz również [pliki](#files).

### <a name="common-pack-options"></a>Opcje wspólnego pakietu

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

Nie ma odpowiednika dla elementu `owners` w programie MSBuild.
W przypadku `summary`można użyć właściwości `<Description>` MSBuild, nawet jeśli wartość `summary` nie jest automatycznie migrowana do tej właściwości, ponieważ ta właściwość jest zamapowana na element [`description`](#other-common-root-level-options) .

## <a name="scripts"></a>skrypty

```json
{
  "scripts": {
    "precompile": "generateCode.cmd",
    "postpublish": [ "obfuscate.cmd", "removeTempFiles.cmd" ]
  }
}
```

Ich odpowiednik w programie MSBuild jest [obiektem docelowym](/visualstudio/msbuild/msbuild-targets):

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="generateCode.cmd" />
</Target>

<Target Name="MyPostCompileTarget" AfterTargets="Publish">
  <Exec Command="obfuscate.cmd" />
  <Exec Command="removeTempFiles.cmd" />
</Target>
```

## <a name="runtimeoptions"></a>runtimeOptions

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

Wszystkie ustawienia w tej grupie, z wyjątkiem właściwości "System. GC. Server", są umieszczane w pliku o nazwie *runtimeconfig. Template. JSON* w folderze projektu, z opcjami podniesionymi do obiektu głównego podczas procesu migracji:

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

Właściwość "System. GC. Server" jest migrowana do pliku CSPROJ:

```xml
<PropertyGroup>
  <ServerGarbageCollection>true</ServerGarbageCollection>
</PropertyGroup>
```

Można jednak ustawić wszystkie te wartości w csproj, a także właściwości programu MSBuild:

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

Nieobsługiwane w csproj. Zamiast tego należy utworzyć Dołączanie plików zawartości w pliku *. nuspec* .
Aby uzyskać więcej informacji, zobacz [Dołączanie plików zawartości](/nuget/schema/nuspec#including-content-files).

## <a name="files"></a>— pliki

W pliku *Project. JSON*można rozszerzyć kompilację i pakiet, aby kompilować i osadzać z różnych folderów.
W programie MSBuild odbywa się to za pomocą [elementów](/visualstudio/msbuild/common-msbuild-project-items). Poniższy przykład jest wspólną konwersją:

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
> Wiele domyślnych [wzorców obsługi symboli wieloznacznych](https://en.wikipedia.org/wiki/Glob_(programming)) są automatycznie dodawane przez zestaw .NET Core SDK.
> Aby uzyskać więcej informacji, zobacz [domyślne wartości elementu kompilowania](https://aka.ms/sdkimplicititems).

Wszystkie elementy `ItemGroup` MSBuild obsługują `Include`, `Exclude`i `Remove`.

Układ pakietu wewnątrz. nupkg można modyfikować za pomocą `PackagePath="path"`.

Z wyjątkiem `Content`, większość grup elementów wymaga jawnie dodania `Pack="true"` do uwzględnienia w pakiecie. `Content` zostanie umieszczony w folderze *zawartości* w pakiecie, ponieważ właściwość `<IncludeContentInPack>` programu MSBuild jest domyślnie ustawiona na `true`.
Aby uzyskać więcej informacji, zobacz temat [uwzględnianie zawartości w pakiecie](/nuget/schema/msbuild-targets#including-content-in-a-package).

`PackagePath="%(Identity)"` jest krótkim sposobem ustawiania ścieżki pakietu do ścieżki pliku względnej dla projektu.

## <a name="testrunner"></a>testRunner

### <a name="xunit"></a>xUnit

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

## <a name="see-also"></a>Zobacz także

- [Ogólne omówienie zmian w interfejsie wiersza polecenia](../tools/cli-msbuild-architecture.md)
