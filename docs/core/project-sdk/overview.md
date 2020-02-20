---
title: Omówienie zestawu SDK programu .NET Core
description: Dowiedz się więcej o zestawach SDK projektu .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: b1b839f81b1b4a8d20dbb34d3d2fc000c64acb8a
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453805"
---
# <a name="net-core-project-sdks"></a>Zestawy SDK projektu .NET Core

Projekty .NET Core są skojarzone z zestawem SDK (Software Development Kit). Każdy zestaw SDK projektu to zestaw [obiektów docelowych](/visualstudio/msbuild/msbuild-targets) programu MSBuild i skojarzonych [zadań](/visualstudio/msbuild/msbuild-tasks) , które są odpowiedzialne za kompilowanie, pakowanie i publikowanie kodu.

## <a name="available-sdks"></a>Dostępne zestawy SDK

Dostępne są następujące zestawy SDK dla platformy .NET Core:

| ID | Opis | Repo|
| - | - | - |
| `Microsoft.NET.Sdk` | Zestaw .NET Core SDK | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | [Zestaw SDK sieci Web](/aspnet/core/razor-pages/web-sdk) platformy .NET Core | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | [Zestaw SDK](/aspnet/core/razor-pages/sdk) programu .NET Core Razor |
| `Microsoft.NET.Sdk.Worker` | Zestaw SDK usługi procesu roboczego platformy .NET Core |
| `Microsoft.NET.Sdk.WindowsDesktop` | Podstawowe WinForms i zestaw WPF SDK platformy .NET |

Zestaw .NET Core SDK jest podstawowym zestawem SDK dla platformy .NET Core. Inne zestawy SDK odwołują się do zestaw .NET Core SDK i projekty, które są skojarzone z innymi zestawami SDK, mają dostępne wszystkie właściwości zestaw .NET Core SDK. Zestaw SDK sieci Web, na przykład, zależy od zestaw .NET Core SDK i zestawu Razor SDK.

Możesz również utworzyć własny zestaw SDK, który może być dystrybuowany za pośrednictwem programu NuGet.

## <a name="project-files"></a>Pliki projektu

Projekty .NET Core są oparte na formacie programu [MSBuild](/visualstudio/msbuild/msbuild) . Pliki projektu, które mają rozszerzenia, takie jak *. csproj* dla C# projektów i *. fsproj* dla F# projektów, są w formacie XML. Głównym elementem pliku projektu MSBuild jest element [projektu](/msbuild/project-element-msbuild) . Element `Project` ma opcjonalny atrybut `Sdk`, który określa zestaw SDK (i wersję), który ma być używany. Aby użyć narzędzi .NET Core i skompilować swój kod, ustaw atrybut `Sdk` na jeden z identyfikatorów w tabeli [dostępnych zestawów SDK](#available-sdks) .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

Aby określić zestaw SDK pochodzący z programu NuGet, należy dołączyć wersję na końcu nazwy lub określić nazwę i wersję w pliku *Global. JSON* .

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

Innym sposobem określenia zestawu SDK jest element najwyższego poziomu [zestawu SDK](/visualstudio/msbuild/sdk-element-msbuild) :

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

Odwołujące się do zestawu SDK w jednym z tych sposobów znacznie upraszczają pliki projektu dla platformy .NET Core. Podczas oceniania projektu, MSBuild dodaje niejawne Importy dla `Sdk.props` w górnej części pliku projektu i `Sdk.targets` na dole.

```xml
<Project>
  <!-- Implicit top import -->
  <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />
  ...
  <!-- Implicit bottom import -->
  <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

> [!TIP]
> Na komputerze z systemem Windows pliki *SDK. props* i *SDK. targets* znajdują się w folderze *%ProgramFiles%\dotnet\sdk\\[wersja] \Sdks\Microsoft.NET.Sdk\Sdk* .

### <a name="preprocess-the-project-file"></a>Wstępnie przetwórz plik projektu

Można zobaczyć w pełni rozwinięty projekt, gdy program MSBuild widzi go po zestawie SDK i jego obiektach docelowych za pomocą polecenia `dotnet msbuild -preprocess`. Przełącznik [preprocesora](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) polecenia [`dotnet msbuild`](../tools/dotnet-msbuild.md) pokazuje, które pliki są importowane, ich źródła i ich wkłady do kompilacji bez faktycznego kompilowania projektu.

Jeśli projekt ma wiele platform docelowych, należy skoncentrować wyniki polecenia tylko dla jednej struktury, określając ją jako właściwość programu MSBuild. Na przykład:

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>Domyślna kompilacja obejmuje

Wartość domyślna obejmuje i wyklucza elementy kompilowania oraz osadzone zasoby są zdefiniowane w zestawie SDK. W przeciwieństwie do projektów .NET Framework nie należących do zestawu SDK, nie trzeba określać tych elementów w pliku projektu, ponieważ ustawienia domyślne obejmują najczęściej spotykane przypadki użycia. Prowadzi to do mniejszych plików projektu, które są łatwiejsze do zrozumienia, a także do edycji, w razie potrzeby.

W poniższej tabeli przedstawiono, który element i które [elementy globalne](https://en.wikipedia.org/wiki/Glob_(programming)) są uwzględnione i wykluczone w zestaw .NET Core SDK:

| Element           | Uwzględnij globalizowania                              | Wyklucz globalizowania                                                  | Usuń globalizowania              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Kompilacji           | \*\*/\*. cs (lub inne rozszerzenia językowe) | \*\*/\*. User;  \*\*/\*.\*proj;  \*\*/\*. sln;  \*\*/\*. VSSSCC  | Nie dotyczy                      |
| EmbeddedResource  | \*\*/\*. resx                              | \*\*/\*. User; \*\*/\*.\*proj; \*\*/\*. sln; \*\*/\*. VSSSCC     | Nie dotyczy                      |
| None              | \*\*/\*                                   | \*\*/\*. User; \*\*/\*.\*proj; \*\*/\*. sln; \*\*/\*. VSSSCC     | \*\*/\*. cs; \*\*/\*. resx |

> [!NOTE]
> Foldery `./bin` i `./obj`, które są reprezentowane przez `$(BaseOutputPath)` i `$(BaseIntermediateOutputPath)` właściwości programu MSBuild, są domyślnie wyłączone z elementy globalne. Wykluczenia są reprezentowane przez właściwość `$(DefaultItemExcludes)`.

Jeśli jawnie zdefiniujesz te elementy w pliku projektu, może wystąpić następujący błąd:

**Uwzględniono zduplikowane elementy kompilacji. Zestaw SDK platformy .NET domyślnie zawiera elementy kompilacji z katalogu projektu. Możesz usunąć te elementy z pliku projektu lub ustawić właściwość "EnableDefaultCompileItems" na wartość "false", jeśli chcesz jawnie uwzględnić je w pliku projektu.**

Aby rozwiązać ten problem, Usuń jawne `Compile` elementy, które pasują do niejawnych wymienionych w poprzedniej tabeli, lub ustaw właściwość `EnableDefaultCompileItems` na `false`, która wyłącza niejawne dołączanie:

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Jeśli chcesz określić, na przykład niektóre pliki do opublikowania w aplikacji, nadal możesz używać znanych mechanizmów programu MSBuild dla tego, na przykład, elementu `Content`.

`EnableDefaultCompileItems` wyłącza tylko `Compile` elementy globalne, ale nie wpływa na inne elementy globalne, takie jak niejawne `None` globalizowania, które również dotyczą elementów \*. cs. Z tego powodu Eksplorator rozwiązań w programie Visual Studio pokazuje elementy \*. cs jako część projektu, zawarte jako elementy `None`. Aby wyłączyć niejawną `None` globalizowania, ustaw `EnableDefaultNoneItems` na `false`:

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Aby wyłączyć *wszystkie* niejawne elementy globalne, ustaw właściwość `EnableDefaultItems` na `false`:

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a>Dostosuj kompilację

Istnieją różne sposoby [dostosowywania kompilacji](/visualstudio/msbuild/customize-your-build). Możesz chcieć przesłonić Właściwość przez przekazanie jej jako argumentu do polecenia [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) lub [dotnet](../tools/index.md) . Możesz również dodać właściwość do pliku projektu lub do pliku *Directory. Build. props* . Aby uzyskać listę przydatnych właściwości projektów .NET Core, zobacz [Właściwości programu MSBuild dla projektów zestaw .NET Core SDK](msbuild-props.md).

## <a name="see-also"></a>Zobacz też

- [Zainstaluj program .NET Core](../install/index.md)
- [Jak używać zestawów SDK projektu MSBuild](/visualstudio/msbuild/how-to-use-project-sdk)
