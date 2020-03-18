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
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>Właściwości MSBuild dla projektów SDK .NET Core

Na tej stronie opisano właściwości MSBuild do konfigurowania projektów .NET Core.

> [!NOTE]
> Ta strona jest w toku i nie zawiera wszystkich przydatnych właściwości MSBuild dla .NET Core SDK. Aby uzyskać listę typowych właściwości MSBuild, zobacz [Typowe właściwości MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Właściwości frameworka

- [Platforma docelowa](#targetframework)
- [Platformy docelowe](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>Platforma docelowa

Właściwość `TargetFramework` określa wersję platformy docelowej dla aplikacji, która niejawnie odwołuje się do [metapakietu](../packages.md#metapackages). Aby uzyskać listę prawidłowych monikerów platform [docelowych, zobacz Platformy docelowe w projektach w stylu SDK](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Aby uzyskać więcej informacji, zobacz [Platformy docelowe w projektach w stylu SDK](../../standard/frameworks.md).

### <a name="targetframeworks"></a>Platformy docelowe

Użyj `TargetFrameworks` tej właściwości, gdy chcesz, aby aplikacja była skierowana na wiele platform. Aby uzyskać listę prawidłowych monikerów platform [docelowych, zobacz Platformy docelowe w projektach w stylu SDK](../../standard/frameworks.md#supported-target-framework-versions).

> [!NOTE]
> Ta właściwość jest `TargetFramework` ignorowana, jeśli określono (liczba pojedyncza).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

Aby uzyskać więcej informacji, zobacz [Platformy docelowe w projektach w stylu SDK](../../standard/frameworks.md).

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> Ta właściwość ma zastosowanie `netstandard1.x`tylko do projektów korzystających z programu . Nie ma zastosowania do projektów, które używają `netstandard2.x`.

Użyj `NetStandardImplicitPackageVersion` właściwości, gdy chcesz określić wersję framework, która jest niższa niż wersja [metapackage.](../packages.md#metapackages) Plik projektu w poniższym `netstandard1.3` przykładzie obiektów docelowych, ale `NETStandard.Library`używa wersji 1.6.0 .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a>Publikowanie właściwości

- [Identyfikator czasu wykonywania](#runtimeidentifier)
- [Identyfikatory runtimeidentifiers](#runtimeidentifiers)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>Identyfikator czasu wykonywania

Właściwość `RuntimeIdentifier` umożliwia określenie pojedynczego [identyfikatora wykonywania (RID)](../rid-catalog.md) dla projektu. RID umożliwia publikowanie niezależnego wdrożenia.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>Identyfikatory runtimeidentifiers

Właściwość `RuntimeIdentifiers` umożliwia określenie delimitowanej średnikami listy [identyfikatorów czasu wykonywania (IDENTYFIKATORY)](../rid-catalog.md) dla projektu. Użyj tej właściwości, jeśli trzeba opublikować dla wielu uruchomiń. `RuntimeIdentifiers`jest używany w czasie przywracania, aby upewnić się, że odpowiednie zasoby znajdują się na wykresie.

> [!TIP]
> `RuntimeIdentifier`(w liczbie pojedynczej) może zapewnić szybsze kompilacje, gdy wymagany jest tylko jeden czas wykonywania.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="useapphost"></a>UseAppHost

Właściwość `UseAppHost` została wprowadzona w wersji 2.1.400 .NET Core SDK. Kontroluje, czy natywny plik wykonywalny jest tworzony dla wdrożenia. Natywny plik wykonywalny jest wymagany dla wdrożeń samodzielnych.

W .NET Core 3.0 i nowszych wersjach plik wykonywalny zależny od struktury jest tworzony domyślnie. Ustaw `UseAppHost` właściwość, `false` aby wyłączyć generowanie pliku wykonywalnego.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

Aby uzyskać więcej informacji na temat wdrażania, zobacz [.NET Core application deployment](../deploying/index.md).

## <a name="compile-properties"></a>Kompilowanie właściwości

### <a name="langversion"></a>Wersja LangVersion

Właściwość `LangVersion` umożliwia określenie określonej wersji językowej programowania. Na przykład, jeśli chcesz uzyskać dostęp do `LangVersion` `preview`funkcji podglądu języka C#, ustaw na .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

Aby uzyskać więcej informacji, zobacz [C# language versioning](../../csharp/language-reference/configure-language-version.md#override-a-default).

## <a name="nuget-packages"></a>Pakiety NuGet

- [Odwołanie do pakietu](#packagereference)
- [AssetTargetFallback](#assettargetfallback)

### <a name="packagereference"></a>Odwołanie do pakietu

Element `PackageReference` umożliwia określenie zależności NuGet. Na przykład można odwołać się do pojedynczego pakietu zamiast [metapakietu](../packages.md#metapackages). Atrybut `Include` określa identyfikator pakietu. Fragment kodu pliku projektu w poniższym przykładzie odwołuje się do pakietu [System.Runtime.](https://www.nuget.org/packages/System.Runtime/)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

Aby uzyskać więcej informacji, zobacz [Odwołania do pakietów w plikach projektu](/nuget/consume-packages/package-references-in-project-files).

### <a name="assettargetfallback"></a>AssetTargetFallback

Właściwość `AssetTargetFallback` umożliwia określenie dodatkowych wersji zgodnych framework dla projektów, które odwołuje się do projektu i pakietów NuGet, które zużywa projekt. Na przykład jeśli określisz `PackageReference` zależność pakietu przy użyciu, ale ten pakiet nie `TargetFramework`zawiera `AssetTargetFallback` zasobów, które są zgodne z projektów , właściwość wchodzi w grę. Zgodność pakietu, do którego istnieje odwołanie, jest ponownie sprawdzana `AssetTargetFallback`przy użyciu każdej platformy docelowej określonej w pliku .

Właściwość można `AssetTargetFallback` ustawić na jedną lub więcej [wersji platformy docelowej](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a>Pakuj i przywracaj cele

MSBuild 15.1 `pack` `restore` wprowadzone i cele do tworzenia i przywracania pakietów NuGet jako część kompilacji. Aby uzyskać informacje o właściwościach MSBuild `PackageTargetFallback`dla tych obiektów docelowych, w tym , zobacz [NuGet pack i przywracanie jako cele MSBuild](/nuget/reference/msbuild-targets).

## <a name="see-also"></a>Zobacz też

- [Odwołanie do schematu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Typowe właściwości MSBuild](/visualstudio/msbuild/common-msbuild-project-properties)
- [Właściwości MSBuild dla pakietu NuGet](/nuget/reference/msbuild-targets#pack-target)
- [MsBuild właściwości przywracania NuGet](/nuget/reference/msbuild-targets#restore-properties)
- [Dostosowywanie kompilacji](/visualstudio/msbuild/customize-your-build)
