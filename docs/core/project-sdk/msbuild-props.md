---
title: Właściwości programu MSBuild dla Microsoft. NET. Sdk
description: Odwołanie do właściwości programu MSBuild, które są zrozumiałe dla zestaw .NET Core SDK.
ms.date: 02/02/2020
ms.topic: reference
ms.openlocfilehash: f5dc2079bc313b8dd9fa5556cd941521a597ae38
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453812"
---
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>Właściwości programu MSBuild dla projektów zestaw .NET Core SDK

Na tej stronie opisano właściwości programu MSBuild służące do konfigurowania projektów platformy .NET Core.

> [!NOTE]
> Ta strona jest w toku i nie wyświetla wszystkich przydatnych właściwości programu MSBuild dla zestaw .NET Core SDK. Aby zapoznać się z listą typowych właściwości programu MSBuild, zobacz [typowe właściwości programu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Właściwości struktury

- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)
- [TargetFramework](#targetframework)
- [TargetFrameworks](#targetframeworks)

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> Ta właściwość ma zastosowanie tylko do projektów korzystających z `netstandard1.x`. Nie dotyczy to projektów, które używają `netstandard2` i nowszych.

Użyj właściwości `NetStandardImplicitPackageVersion`, aby określić wersję platformy, która jest starsza niż wersja [pakietu](../packages.md#metapackages) . Plik projektu w poniższym przykładzie jest docelowy `netstandard1.3` ale używa wersji 1.6.0 `NETStandard.Library`.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

### <a name="targetframework"></a>TargetFramework

Właściwość `TargetFramework` określa wersję platformy docelowej dla aplikacji, która niejawnie odwołuje się do [pakietu](../packages.md#metapackages). Aby zapoznać się z listą prawidłowych monikerów platformy docelowej, zobacz [platformę docelową w projektach w stylu zestawu SDK](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Aby uzyskać więcej informacji, zobacz [Platformy docelowe w projektach w stylu zestawu SDK](../../standard/frameworks.md).

### <a name="targetframeworks"></a>TargetFrameworks

Użyj właściwości `TargetFrameworks`, jeśli chcesz, aby aplikacja była przeznaczona dla wielu platform. Aby zapoznać się z listą prawidłowych monikerów platformy docelowej, zobacz [platformę docelową w projektach w stylu zestawu SDK](../../standard/frameworks.md#supported-target-framework-versions).

> [!NOTE]
> Ta właściwość jest ignorowana, jeśli określono `TargetFramework` (pojedynczą).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

Aby uzyskać więcej informacji, zobacz [Platformy docelowe w projektach w stylu zestawu SDK](../../standard/frameworks.md).

## <a name="publish-properties"></a>Właściwości publikowania

- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>RuntimeIdentifier

Właściwość `RuntimeIdentifier` umożliwia określenie pojedynczego [identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu. Identyfikator RID umożliwia publikowanie samodzielnego wdrożenia.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

Właściwość `RuntimeIdentifiers` pozwala określić rozdzielaną średnikami listę [identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu. Użyj tej właściwości, jeśli chcesz opublikować dla wielu środowisk uruchomieniowych. `RuntimeIdentifiers` jest używany podczas przywracania, aby upewnić się, że odpowiednie zasoby znajdują się na wykresie.

> [!TIP]
> `RuntimeIdentifier` (pojedyncze) może zapewnić szybsze kompilacje, gdy wymagane jest tylko jedno środowisko uruchomieniowe.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a>UseAppHost

Właściwość `UseAppHost` została wprowadzona w wersji 2.1.400 zestaw .NET Core SDK. Określa, czy dla wdrożenia jest tworzony natywny plik wykonywalny. Natywny plik wykonywalny jest wymagany w przypadku wdrożeń samodzielnych.

W programie .NET Core 3,0 i jego nowszych wersjach domyślnie tworzony jest plik wykonywalny zależny od platformy. Ustaw właściwość `UseAppHost` na `false`, aby wyłączyć generowanie pliku wykonywalnego.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

Aby uzyskać więcej informacji na temat wdrażania, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).

## <a name="compile-properties"></a>Kompiluj właściwości

### <a name="langversion"></a>LangVersion

Właściwość `LangVersion` umożliwia określenie konkretnej wersji języka programowania. Na przykład jeśli chcesz uzyskać dostęp do C# funkcji w wersji zapoznawczej, ustaw `LangVersion` na `preview`.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

Aby uzyskać więcej informacji, zobacz [ C# przechowywanie wersji języka](../../csharp/language-reference/configure-language-version.md#override-a-default).

## <a name="nuget-packages"></a>Pakiety NuGet

- [PackageReference](#packagereference)

### <a name="packagereference"></a>PackageReference

Element `PackageReference` pozwala określić zależność NuGet. Na przykład możesz chcieć odwołać się do pojedynczego pakietu zamiast [pakietu](../packages.md#metapackages). Atrybut `Include` określa identyfikator pakietu. Fragment pliku projektu w poniższym przykładzie odwołuje się do pakietu [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

Aby uzyskać więcej informacji, zobacz [odwołania do pakietów w plikach projektu](/nuget/consume-packages/package-references-in-project-files).

### <a name="pack-and-restore-targets"></a>Elementy docelowe pakietów i przywracania

Program MSBuild 15,1 wprowadził `pack` i `restore` elementy docelowe do tworzenia i przywracania pakietów NuGet w ramach kompilacji. Aby uzyskać informacje na temat właściwości programu MSBuild dla tych obiektów docelowych, w tym `PackageTargetFallback`, zobacz [pakiet NuGet i przywracanie jako elementy docelowe programu MSBuild](/nuget/reference/msbuild-targets).

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu programu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Typowe właściwości programu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties)
- [Właściwości programu MSBuild dla pakietu NuGet](/nuget/reference/msbuild-targets#pack-target)
- [Właściwości programu MSBuild do przywracania NuGet](/nuget/reference/msbuild-targets#restore-properties)
- [Dostosuj kompilację](/visualstudio/msbuild/customize-your-build)
