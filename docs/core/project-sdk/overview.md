---
title: Omówienie zestawu SDK programu .NET Core
titleSuffix: ''
description: Dowiedz się więcej o zestawach SDK projektu .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 9db62ab7774e3dd71412fa346d78ae0c62a2f81f
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803044"
---
# <a name="net-core-project-sdks"></a>Zestawy SDK projektu .NET Core

Projekty .NET Core są skojarzone z zestawem SDK (Software Development Kit). Każdy *zestaw SDK projektu* to zestaw [obiektów docelowych](/visualstudio/msbuild/msbuild-targets) programu MSBuild i skojarzonych [zadań](/visualstudio/msbuild/msbuild-tasks) , które są odpowiedzialne za kompilowanie, pakowanie i publikowanie kodu. Projekt, który odwołuje się do zestawu SDK projektu, jest czasami określany jako *projekt w stylu zestawu SDK*.

## <a name="available-sdks"></a>Dostępne zestawy SDK

Dostępne są następujące zestawy SDK dla platformy .NET Core:

| ID | Opis | Repozytorium|
| - | - | - |
| `Microsoft.NET.Sdk` | Zestaw .NET Core SDK | <https://github.com/dotnet/sdk> |
| `Microsoft.NET.Sdk.Web` | [Zestaw SDK sieci Web](/aspnet/core/razor-pages/web-sdk) platformy .NET Core | <https://github.com/aspnet/websdk> |
| `Microsoft.NET.Sdk.Razor` | [Zestaw SDK](/aspnet/core/razor-pages/sdk) programu .NET Core Razor |
| `Microsoft.NET.Sdk.Worker` | Zestaw SDK usługi procesu roboczego platformy .NET Core |
| `Microsoft.NET.Sdk.WindowsDesktop` | Podstawowe WinForms i zestaw WPF SDK platformy .NET |

Zestaw .NET Core SDK jest podstawowym zestawem SDK dla platformy .NET Core. Inne zestawy SDK odwołują się do zestaw .NET Core SDK i projekty, które są skojarzone z innymi zestawami SDK, mają dostępne wszystkie właściwości zestaw .NET Core SDK. Zestaw SDK sieci Web, na przykład, zależy od zestaw .NET Core SDK i zestawu Razor SDK.

Możesz również utworzyć własny zestaw SDK, który może być dystrybuowany za pośrednictwem programu NuGet.

## <a name="project-files"></a>Pliki projektu

Projekty .NET Core są oparte na formacie programu [MSBuild](/visualstudio/msbuild/msbuild) . Pliki projektu, które mają rozszerzenia, takie jak *. csproj* dla projektów C# i *. fsproj* dla projektów F #, są w formacie XML. Głównym elementem pliku projektu MSBuild jest element [projektu](/visualstudio/msbuild/project-element-msbuild) . `Project`Element ma opcjonalny `Sdk` atrybut, który określa zestaw SDK (i wersję) do użycia. Aby użyć narzędzi .NET Core i skompilować swój kod, należy ustawić `Sdk` atrybut na jeden z identyfikatorów w tabeli [dostępnych zestawów SDK](#available-sdks) .

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

Aby określić zestaw SDK pochodzący z programu NuGet, należy dołączyć wersję na końcu nazwy lub określić nazwę i wersję w *global.js* pliku.

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

Odwołujące się do zestawu SDK w jednym z tych sposobów znacznie upraszczają pliki projektu dla platformy .NET Core. Podczas oceniania projektu, MSBuild dodaje niejawne Importy w `Sdk.props` górnej części pliku projektu i `Sdk.targets` w dolnej części.

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
> Na komputerze z systemem Windows pliki *SDK. props* i *SDK. targets* można znaleźć w folderze *%ProgramFiles%\dotnet\sdk \\ [wersja] \Sdks\Microsoft.NET.Sdk\Sdk* .

### <a name="preprocess-the-project-file"></a>Wstępnie przetwórz plik projektu

Można zobaczyć w pełni rozwinięty projekt, gdy program MSBuild widzi go po zestawie SDK i jego obiektach docelowych za pomocą `dotnet msbuild -preprocess` polecenia. Przełącznik [preprocesora](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) [`dotnet msbuild`](../tools/dotnet-msbuild.md) polecenia pokazuje, które pliki są importowane, ich źródła i ich wkłady do kompilacji bez faktycznego kompilowania projektu.

Jeśli projekt ma wiele platform docelowych, należy skoncentrować wyniki polecenia tylko dla jednej struktury, określając ją jako właściwość programu MSBuild. Przykład:

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>Domyślna kompilacja obejmuje

Wartość domyślna to include i Exclude dla elementów kompilowania, zasobów osadzonych i `None` elementów zdefiniowanych w zestawie SDK. W przeciwieństwie do projektów .NET Framework nie należących do zestawu SDK, nie trzeba określać tych elementów w pliku projektu, ponieważ ustawienia domyślne obejmują najczęściej spotykane przypadki użycia. Sprawia to, że plik projektu jest mniejszy i łatwiejszy do zrozumienia i edycji, w razie potrzeby.

W poniższej tabeli pokazano, które elementy i które [elementy globalne](https://en.wikipedia.org/wiki/Glob_(programming)) są uwzględnione i wykluczone w zestaw .NET Core SDK:

| Element           | Uwzględnij globalizowania                              | Wyklucz globalizowania                                                  | Usuń globalizowania              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Opracowania           | \*\*/\*. cs (lub inne rozszerzenia językowe) | \*\*/\*Użytkownicy  \*\*/\*.\* proj  \*\*/\*. sln  \*\*/\*. vssscc  | Nie dotyczy                      |
| EmbeddedResource  | \*\*/\*. resx                              | \*\*/\*Użytkownicy \*\*/\*.\* proj \*\*/\*. sln \*\*/\*. vssscc     | Nie dotyczy                      |
| Brak              | \*\*/\*                                   | \*\*/\*Użytkownicy \*\*/\*.\* proj \*\*/\*. sln \*\*/\*. vssscc     | \*\*/\*Rejestr \*\*/\*. resx |

> [!NOTE]
> `./bin`Foldery i `./obj` , które są reprezentowane przez `$(BaseOutputPath)` właściwości i programu `$(BaseIntermediateOutputPath)` MSBuild, są domyślnie wykluczone z elementy globalne. Wykluczenia są reprezentowane przez właściwość `$(DefaultItemExcludes)` .

#### <a name="build-errors"></a>Błędy kompilacji

Jeśli jawnie zdefiniujesz dowolny z tych elementów w pliku projektu, możesz uzyskać błąd kompilacji "NETSDK1022" podobny do poniższego:

  > Uwzględniono zduplikowane elementy "Kompiluj". Zestaw SDK platformy .NET domyślnie zawiera elementy "Kompiluj" z katalogu projektu. Możesz usunąć te elementy z pliku projektu lub ustawić właściwość "EnableDefaultCompileItems" na wartość "false", jeśli chcesz jawnie uwzględnić je w pliku projektu.

  > Uwzględniono zduplikowane elementy "EmbeddedResource". Zestaw SDK platformy .NET domyślnie zawiera elementy "EmbeddedResource" z katalogu projektu. Możesz usunąć te elementy z pliku projektu lub ustawić właściwość "EnableDefaultEmbeddedResourceItems" na wartość "false", jeśli chcesz jawnie uwzględnić je w pliku projektu.

Aby rozwiązać te błędy, wykonaj jedną z następujących czynności:

- Usuń jawne `Compile` , `EmbeddedResource` lub elementy, `None` które są zgodne z niejawnymi wymienionymi w poprzedniej tabeli.

- Ustaw `EnableDefaultItems` Właściwość na `false` , aby wyłączyć wszystkie niejawne dołączenie do pliku:

  ```xml
  <PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
  </PropertyGroup>
  ```

  Jeśli chcesz określić pliki do opublikowania w aplikacji, nadal możesz użyć znanych mechanizmów programu MSBuild dla tego elementu, na przykład `Content` .

- Selektywnie Wyłącz tylko `Compile` , `EmbeddedResource` lub `None` elementy globalne, ustawiając `EnableDefaultCompileItems` Właściwość, `EnableDefaultEmbeddedResourceItems` , lub `EnableDefaultNoneItems` na `false` :

  ```xml
  <PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
    <EnableDefaultEmbeddedResourceItems>false</EnableDefaultEmbeddedResourceItems>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
  </PropertyGroup>
  ```

  Jeśli wyłączysz tylko `Compile` elementy globalne, Eksplorator rozwiązań w programie Visual Studio nadal pokazuje \* elementy CS jako część projektu, uwzględnione jako `None` elementy. Aby wyłączyć niejawną `None` globalizowania, ustaw `EnableDefaultNoneItems` ją na wartość `false` .

## <a name="customize-the-build"></a>Dostosuj kompilację

Istnieją różne sposoby [dostosowywania kompilacji](/visualstudio/msbuild/customize-your-build). Możesz chcieć przesłonić Właściwość przez przekazanie jej jako argumentu do polecenia [MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) lub [dotnet](../tools/index.md) . Możesz również dodać właściwość do pliku projektu lub do pliku *Directory. Build. props* . Aby uzyskać listę przydatnych właściwości projektów .NET Core, zobacz [Dokumentacja programu MSBuild dla projektów zestaw .NET Core SDK](msbuild-props.md).

### <a name="custom-targets"></a>Niestandardowe elementy docelowe

Projekty .NET Core mogą spakować niestandardowe cele programu MSBuild i właściwości do użycia przez projekty korzystające z pakietu. Użyj tego typu rozszerzalności, gdy chcesz:

- Rozwiń proces kompilacji.
- Dostęp do artefaktów procesu kompilacji, takich jak wygenerowane pliki.
- Sprawdź konfigurację, pod którą jest wywoływana kompilacja.

Dodawanie niestandardowych elementów docelowych kompilacji lub właściwości przez umieszczenie plików w formularzu `<package_id>.targets` lub `<package_id>.props` (na przykład `Contoso.Utility.UsefulStuff.targets` ) w folderze *Build* projektu.

Poniższy kod XML to fragment z pliku *. csproj* , który instruuje [`dotnet pack`](../tools/dotnet-pack.md) polecenie do pakowania. `<ItemGroup Label="dotnet pack instructions">`Element umieszcza pliki docelowe w folderze *kompilacji* wewnątrz pakietu. `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">`Element umieszcza zestawy i pliki *JSON* w folderze *Build* .

```xml
<Project Sdk="Microsoft.NET.Sdk">

  ...
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  ...
  
</Project>
```

Aby użyć niestandardowego obiektu docelowego w projekcie, Dodaj element wskazujący `PackageReference` pakiet i jego wersję. W przeciwieństwie do narzędzi, pakiet Custom targets jest uwzględniany w zamknięciu zależności projektu zużywanego.

Można skonfigurować sposób używania niestandardowego obiektu docelowego. Ponieważ jest to element docelowy programu MSBuild, może on zależeć od danego elementu docelowego, działać po innym elemencie docelowym lub być wywoływana ręcznie przy użyciu `dotnet msbuild -t:<target-name>` polecenia. Aby jednak zapewnić lepsze środowisko użytkownika, można połączyć narzędzia dla poszczególnych projektów i niestandardowe elementy docelowe. W tym scenariuszu narzędzie dla projektu akceptuje wszelkie parametry, które są potrzebne, i tłumaczy je na wymagane [`dotnet msbuild`](../tools/dotnet-msbuild.md) wywołanie, które wykonuje miejsce docelowe. Możesz zobaczyć przykład tego rodzaju synergii w repozytorium [przykładów Hackathonych](https://github.com/dotnet/MVPSummitHackathon2016) w projekcie programu 2016 MVP [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) .

## <a name="see-also"></a>Zobacz także

- [Instalowanie programu .NET Core](../install/index.yml)
- [Jak używać zestawów SDK projektu MSBuild](/visualstudio/msbuild/how-to-use-project-sdk)
- [Pakowanie niestandardowych elementów docelowych programu MSBuild i ich właściwości przy użyciu narzędzia NuGet](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
