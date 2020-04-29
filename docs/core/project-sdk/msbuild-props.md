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
# <a name="msbuild-properties-for-net-core-sdk-projects"></a>Właściwości programu MSBuild dla projektów zestaw .NET Core SDK

Na tej stronie opisano właściwości programu MSBuild służące do konfigurowania projektów platformy .NET Core.

> [!NOTE]
> Ta strona jest w toku i nie wyświetla wszystkich przydatnych właściwości programu MSBuild dla zestaw .NET Core SDK. Aby zapoznać się z listą typowych właściwości programu MSBuild, zobacz [typowe właściwości programu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).

## <a name="framework-properties"></a>Właściwości struktury

- [TargetFramework](#targetframework)
- [TargetFrameworks](#targetframeworks)
- [NetStandardImplicitPackageVersion](#netstandardimplicitpackageversion)

### <a name="targetframework"></a>TargetFramework

`TargetFramework` Właściwość określa wersję platformy docelowej dla aplikacji, która niejawnie odwołuje się do [pakietu](../packages.md#metapackages). Aby zapoznać się z listą prawidłowych monikerów platformy docelowej, zobacz [platformę docelową w projektach w stylu zestawu SDK](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>
</Project>
```

Aby uzyskać więcej informacji, zobacz [Platformy docelowe w projektach w stylu zestawu SDK](../../standard/frameworks.md).

### <a name="targetframeworks"></a>TargetFrameworks

Użyj właściwości `TargetFrameworks` , jeśli chcesz, aby aplikacja była przeznaczona dla wielu platform. Aby zapoznać się z listą prawidłowych monikerów platformy docelowej, zobacz [platformę docelową w projektach w stylu zestawu SDK](../../standard/frameworks.md#supported-target-framework-versions).

> [!NOTE]
> Ta właściwość jest ignorowana `TargetFramework` , jeśli określono (pojedynczo).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
  </PropertyGroup>
</Project>
```

Aby uzyskać więcej informacji, zobacz [Platformy docelowe w projektach w stylu zestawu SDK](../../standard/frameworks.md).

### <a name="netstandardimplicitpackageversion"></a>NetStandardImplicitPackageVersion

> [!NOTE]
> Ta właściwość ma zastosowanie tylko do projektów `netstandard1.x`korzystających z programu. Nie dotyczy to projektów, które używają `netstandard2.x`.

Użyj `NetStandardImplicitPackageVersion` właściwości, aby określić wersję platformy, która jest starsza niż wersja [pakietu](../packages.md#metapackages) . Plik projektu w poniższym przykładzie docelowym `netstandard1.3` , ale używa wersji 1.6.0. `NETStandard.Library`

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

## <a name="publish-properties"></a>Właściwości publikowania

- [RuntimeIdentifier](#runtimeidentifier)
- [RuntimeIdentifiers](#runtimeidentifiers)
- [TrimmerRootAssembly](#trimmerrootassembly)
- [UseAppHost](#useapphost)

### <a name="runtimeidentifier"></a>RuntimeIdentifier

`RuntimeIdentifier` Właściwość umożliwia określenie pojedynczego [identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu. Identyfikator RID umożliwia publikowanie samodzielnego wdrożenia.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
  </PropertyGroup>
</Project>
```

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

`RuntimeIdentifiers` Właściwość pozwala określić rozdzielaną średnikami listę [identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu. Użyj tej właściwości, jeśli chcesz opublikować dla wielu środowisk uruchomieniowych. `RuntimeIdentifiers`jest używany podczas przywracania, aby upewnić się, że odpowiednie zasoby znajdują się na wykresie.

> [!TIP]
> `RuntimeIdentifier`(pojedyncze) może zapewnić szybsze kompilacje, gdy wymagane jest tylko jedno środowisko uruchomieniowe.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
  </PropertyGroup>
</Project>
```

### <a name="trimmerrootassembly"></a>TrimmerRootAssembly

`TrimmerRootAssembly` Element umożliwia wykluczenie zestawu z [*przycinania*](../deploying/trim-self-contained.md). Przycinanie jest procesem usuwania nieużywanych części środowiska uruchomieniowego z spakowanej aplikacji. W niektórych przypadkach przycinanie może niepoprawnie usunąć wymagane odwołania.

Poniższy kod XML wyklucza `System.Security` zestaw z przycinania.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
</Project>
```

### <a name="useapphost"></a>UseAppHost

`UseAppHost` Właściwość została wprowadzona w wersji 2.1.400 zestaw .NET Core SDK. Określa, czy dla wdrożenia jest tworzony natywny plik wykonywalny. Natywny plik wykonywalny jest wymagany w przypadku wdrożeń samodzielnych.

W programie .NET Core 3,0 i jego nowszych wersjach domyślnie tworzony jest plik wykonywalny zależny od platformy. Ustaw `UseAppHost` właściwość na `false` , aby wyłączyć generowanie pliku wykonywalnego.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <UseAppHost>false</UseAppHost>
  </PropertyGroup>
</Project>
```

Aby uzyskać więcej informacji na temat wdrażania, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).

## <a name="compile-properties"></a>Kompiluj właściwości

- [LangVersion](#langversion)

### <a name="langversion"></a>LangVersion

`LangVersion` Właściwość umożliwia określenie konkretnej wersji języka programowania. Na przykład jeśli chcesz uzyskać dostęp do funkcji wersji zapoznawczej języka `LangVersion` C# `preview`, ustaw wartość.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <LangVersion>preview</LangVersion>
  </PropertyGroup>
</Project>
```

Aby uzyskać więcej informacji, zobacz [wersja języka C#](../../csharp/language-reference/configure-language-version.md#override-a-default).

## <a name="run-time-configuration-properties"></a>Właściwości konfiguracji czasu wykonywania

Niektóre zachowania w czasie wykonywania można skonfigurować, określając właściwości programu MSBuild w pliku projektu aplikacji. Aby uzyskać informacje na temat innych sposobów konfigurowania zachowania w czasie wykonywania, zobacz [Ustawienia konfiguracji środowiska uruchomieniowego .NET Core](../run-time-config/index.md).

- [ConcurrentGarbageCollection](#concurrentgarbagecollection)
- [InvariantGlobalization](#invariantglobalization)
- [RetainVMGarbageCollection](#retainvmgarbagecollection)
- [ServerGarbageCollection](#servergarbagecollection)
- [ThreadPoolMaxThreads](#threadpoolmaxthreads)
- [ThreadPoolMinThreads](#threadpoolminthreads)
- [TieredCompilation](#tieredcompilation)
- [TieredCompilationQuickJit](#tieredcompilationquickjit)
- [TieredCompilationQuickJitForLoops](#tieredcompilationquickjitforloops)

### <a name="concurrentgarbagecollection"></a>ConcurrentGarbageCollection

Właściwość `ConcurrentGarbageCollection` określa, czy jest włączone [wyrzucanie elementów bezużytecznych w tle](../../standard/garbage-collection/background-gc.md) . Ustaw wartość na `false` , aby wyłączyć wyrzucanie elementów bezużytecznych w tle. Aby uzyskać więcej informacji, zobacz [System. GC. współbieżne/COMPlus_gcConcurrent](../run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ConcurrentGarbageCollection>false</ConcurrentGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="invariantglobalization"></a>InvariantGlobalization

`InvariantGlobalization` Właściwość określa, czy aplikacja jest uruchamiana w trybie *globalizacji-niezmiennym* , co oznacza, że nie ma dostępu do danych specyficznych dla kultury. Ustaw wartość tak, `true` aby była uruchamiana w trybie niezmiennym globalizacji. Aby uzyskać więcej informacji, zobacz [tryb niezmienny](../run-time-config/globalization.md#invariant-mode).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>
</Project>
```

### <a name="retainvmgarbagecollection"></a>RetainVMGarbageCollection

`RetainVMGarbageCollection` Właściwość konfiguruje moduł wyrzucania elementów bezużytecznych w celu umieszczenia usuniętych segmentów pamięci na liście gotowości do użycia w przyszłości lub zwolnienia. Ustawienie wartości `true` informującej Moduł wyrzucania elementów bezużytecznych w celu umieszczenia segmentów na liście gotowości. Aby uzyskać więcej informacji, zobacz [System. GC. RetainVM/COMPlus_GCRetainVM](../run-time-config/garbage-collector.md#systemgcretainvmcomplus_gcretainvm).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <RetainVMGarbageCollection>true</RetainVMGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="servergarbagecollection"></a>ServerGarbageCollection

Właściwość `ServerGarbageCollection` określa, czy aplikacja używa [wyrzucania elementów bezużytecznych stacji roboczej lub odzyskiwania pamięci serwera](../../standard/garbage-collection/workstation-server-gc.md). Ustaw wartość `true` na, aby użyć wyrzucania elementów bezużytecznych serwera. Aby uzyskać więcej informacji, zobacz [System. GC. Server/COMPlus_gcServer](../run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ServerGarbageCollection>true</ServerGarbageCollection>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolmaxthreads"></a>ThreadPoolMaxThreads

`ThreadPoolMaxThreads` Właściwość określa maksymalną liczbę wątków dla puli wątków roboczych. Aby uzyskać więcej informacji, zobacz [maksymalne wątki](../run-time-config/threading.md#maximum-threads).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMaxThreads>20</ThreadPoolMaxThreads>
  </PropertyGroup>
</Project>
```

### <a name="threadpoolminthreads"></a>ThreadPoolMinThreads

`ThreadPoolMinThreads` Właściwość konfiguruje minimalną liczbę wątków dla puli wątków roboczych. Aby uzyskać więcej informacji, zobacz [minimalna liczba wątków](../run-time-config/threading.md#minimum-threads).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <ThreadPoolMinThreads>4</ThreadPoolMinThreads>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilation"></a>TieredCompilation

`TieredCompilation` Właściwość określa, czy kompilator just in Time (JIT) używa [kompilacji warstwowej](../whats-new/dotnet-core-3-0.md#tiered-compilation). Ustaw wartość `false` na, aby wyłączyć kompilację warstwową. Aby uzyskać więcej informacji, zobacz temat [kompilacja warstwowa](../run-time-config/compilation.md#tiered-compilation).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilation>false</TieredCompilation>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjit"></a>TieredCompilationQuickJit

`TieredCompilationQuickJit` Właściwość określa, czy kompilator JIT używa szybkiej JIT. Ustaw wartość na `false` , aby wyłączyć szybkie JIT. Aby uzyskać więcej informacji, zobacz [szybkie JIT](../run-time-config/compilation.md#quick-jit).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
  </PropertyGroup>
</Project>
```

### <a name="tieredcompilationquickjitforloops"></a>TieredCompilationQuickJitForLoops

`TieredCompilationQuickJitForLoops` Właściwość określa, czy kompilator JIT używa szybkiej JIT metod, które zawierają pętle. Ustaw wartość `true` na, aby włączyć funkcję szybkiego JIT dla metod, które zawierają pętle. Aby uzyskać więcej informacji, zobacz [szybkie JIT dla pętli](../run-time-config/compilation.md#quick-jit-for-loops).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TieredCompilationQuickJitForLoops>true</TieredCompilationQuickJitForLoops>
  </PropertyGroup>
</Project>
```

## <a name="nuget-packages"></a>Pakiety NuGet

- [PackageReference](#packagereference)
- [AssetTargetFallback](#assettargetfallback)

### <a name="packagereference"></a>PackageReference

`PackageReference` Element pozwala określić zależność NuGet. Na przykład możesz chcieć odwołać się do pojedynczego pakietu zamiast [pakietu](../packages.md#metapackages). Ten `Include` ATRYBUT określa identyfikator pakietu. Fragment pliku projektu w poniższym przykładzie odwołuje się do pakietu [System. Runtime](https://www.nuget.org/packages/System.Runtime/) .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

Aby uzyskać więcej informacji, zobacz [odwołania do pakietów w plikach projektu](/nuget/consume-packages/package-references-in-project-files).

### <a name="assettargetfallback"></a>AssetTargetFallback

`AssetTargetFallback` Właściwość pozwala określić dodatkowe zgodne wersje platformy dla projektów, do których odwołuje się projekt, oraz pakietów NuGet, które są używane w projekcie. Na przykład, jeśli określisz zależność pakietu przy użyciu `PackageReference` programu `TargetFramework`, ale ten pakiet nie zawiera zasobów, które są zgodne z projektem, `AssetTargetFallback` właściwość jest dostępna. Zgodność przywoływanego pakietu jest ponownie sprawdzana przy użyciu każdej platformy docelowej określonej w `AssetTargetFallback`.

Można ustawić `AssetTargetFallback` właściwość na co najmniej jedną [docelową wersję platformy](../../standard/frameworks.md#supported-target-framework-versions).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
  <PropertyGroup>
    <AssetTargetFallback>net461</AssetTargetFallback>
  </PropertyGroup>
</Project>
```

### <a name="pack-and-restore-targets"></a>Elementy docelowe pakietów i przywracania

Program MSBuild 15,1 `pack` wprowadził `restore` i ma cele tworzenia i przywracania pakietów NuGet w ramach kompilacji. Aby uzyskać informacje na temat właściwości programu MSBuild dla tych obiektów `PackageTargetFallback`docelowych, w tym, zobacz [pakiet NuGet i przywracanie jako elementy docelowe programu MSBuild](/nuget/reference/msbuild-targets).

## <a name="see-also"></a>Zobacz także

- [Odwołanie do schematu programu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference)
- [Typowe właściwości programu MSBuild](/visualstudio/msbuild/common-msbuild-project-properties)
- [Właściwości programu MSBuild dla pakietu NuGet](/nuget/reference/msbuild-targets#pack-target)
- [Właściwości programu MSBuild do przywracania NuGet](/nuget/reference/msbuild-targets#restore-properties)
- [Dostosuj kompilację](/visualstudio/msbuild/customize-your-build)
