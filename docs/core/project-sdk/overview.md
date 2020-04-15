---
title: Omówienie zestawie SDK projektu .NET Core
description: Dowiedz się więcej o sdkach projektu .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: d0ac01dca31dffea482745126e00c34b1da20774
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389667"
---
# <a name="net-core-project-sdks"></a>SDK projektu .NET Core

Projekty .NET Core są skojarzone z zestawem do tworzenia oprogramowania (SDK). Każdy *zestaw SDK projektu* jest zestawem obiektów [docelowych](/visualstudio/msbuild/msbuild-targets) MSBuild i [skojarzonych zadań,](/visualstudio/msbuild/msbuild-tasks) które są odpowiedzialne za kompilowanie, pakowanie i publikowanie kodu. Projekt, który odwołuje się do sdk projektu jest czasami określany jako *projekt w stylu SDK*.

## <a name="available-sdks"></a>Dostępne sdk

Dla platformy .NET Core dostępne są następujące skomuniky SDK:

| ID | Opis | Repo|
| - | - | - |
| `Microsoft.NET.Sdk` | Podstawowy sdk .NET | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | Podstawowy identyfikator [SDK sieci Web](/aspnet/core/razor-pages/web-sdk) .NET | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | SDK [do golenia](/aspnet/core/razor-pages/sdk) .NET Core |
| `Microsoft.NET.Sdk.Worker` | Podstawowy plik SDK usługi pracownika .NET |
| `Microsoft.NET.Sdk.WindowsDesktop` | .NET Core WinForms i WPF SDK |

Core SDK .NET jest podstawowym SDK dla .NET Core. Inne sdks odwołać .NET Core SDK i projekty, które są skojarzone z innymi SDK mają wszystkie właściwości .NET Core SDK dostępne dla nich. Na przykład składnik SDK sieci Web zależy zarówno od sdk .NET Core, jak i SDK razor.

Można również tworzyć własne SDK, które mogą być dystrybuowane za pośrednictwem NuGet.

## <a name="project-files"></a>Pliki projektu

Projekty .NET Core są oparte na formacie [MSBuild.](/visualstudio/msbuild/msbuild) Pliki projektu, które mają rozszerzenia, takie jak *.csproj* dla projektów C# i *.fsproj* dla projektów F#, są w formacie XML. Głównym elementem pliku projektu MSBuild jest [element projektu.](/visualstudio/msbuild/project-element-msbuild) Element `Project` ma opcjonalny `Sdk` atrybut, który określa, który zestaw SDK (i wersja) do użycia. Aby użyć narzędzi .NET Core i utworzyć `Sdk` kod, ustaw atrybut na jeden z identyfikatorów w tabeli [Dostępne zestawy SDK.](#available-sdks)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

Aby określić SDK, który pochodzi z NuGet, dołącz wersję na końcu nazwy lub określ nazwę i wersję w pliku *global.json.*

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

Innym sposobem określenia SDK jest element [Sdk](/visualstudio/msbuild/sdk-element-msbuild) najwyższego poziomu:

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

Odwoływanie się do sdk w jeden z tych sposobów znacznie upraszcza pliki projektu dla .NET Core. Podczas oceny projektu MSBuild dodaje niejawne importy w `Sdk.props` górnej `Sdk.targets` części pliku projektu i na dole.

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
> Na komputerze z systemem Windows pliki *Sdk.props* i *Sdk.targets* można znaleźć w folderze *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk\Sdk* folder.

### <a name="preprocess-the-project-file"></a>Wstępne przetwarzanie pliku projektu

Możesz zobaczyć w pełni rozwinięty projekt, jak MSBuild widzi go po SDK i jego cele są uwzględniane za pomocą `dotnet msbuild -preprocess` polecenia. Przełącznik [przetwarzania wstępnego](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) [`dotnet msbuild`](../tools/dotnet-msbuild.md) polecenia pokazuje, które pliki są importowane, ich źródła i ich wkład do kompilacji bez faktycznego budowania projektu.

Jeśli projekt ma wiele struktur docelowych, skoncentruj wyniki polecenia tylko na jednej platformie, określając ją jako właściwość MSBuild. Przykład:

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>Domyślna kompilacja obejmuje

Domyślne obejmuje i wyklucza dla elementów kompilacji i osadzone zasoby są zdefiniowane w zestawie SDK. W przeciwieństwie do projektów innych niż SDK .NET Framework, nie trzeba określać te elementy w pliku projektu, ponieważ domyślne obejmują najczęstsze przypadki użycia. Prowadzi to do mniejszych plików projektu, które są łatwiejsze do zrozumienia, a także edytować ręcznie, w razie potrzeby.

W poniższej tabeli przedstawiono, który element i które [globy](https://en.wikipedia.org/wiki/Glob_(programming)) są uwzględniane i wykluczane w zestawie .NET Core SDK:

| Element           | Uwzględnij glob                              | Wyklucz glob                                                  | Usuń glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Skompilować           | \*\*/\*.cs (lub inne rozszerzenia języka) | \*\*/\*.user;  \*\*/\*. \*proj ;  \* \* / \*  \* \* /.vssscc \*(vssscc)  | Nie dotyczy                      |
| Zasoby wbudowaneSerekseźródło  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*. \*proj ; \* \* / \* \* \* /.vssscc \*(vssscc)     | Nie dotyczy                      |
| Brak              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*. \*proj ; \* \* / \* \* \* /.vssscc \*(vssscc)     | \*\*/\*.cs ; \* \* /.resx \*(resx) |

> [!NOTE]
> `./bin` Foldery `./obj` i foldery, które `$(BaseOutputPath)` są `$(BaseIntermediateOutputPath)` reprezentowane przez i MSBuild właściwości, są domyślnie wykluczone z globs. Wykluczenia są reprezentowane `$(DefaultItemExcludes)`przez właściwość .

Jeśli jawnie zdefiniujesz te elementy w pliku projektu, prawdopodobnie zostanie wyświetlony następujący błąd:

**Zduplikowane elementy kompilacji zostały uwzględnione. Zestaw SDK platformy .NET domyślnie zawiera elementy kompilacji z katalogu projektu. Można usunąć te elementy z pliku projektu lub ustawić właściwość "EnableDefaultCompileItems" na "false", jeśli chcesz jawnie dołączyć je do pliku projektu.**

Aby rozwiązać ten problem, usuń `Compile` jawne elementy, które pasują do niejawnych wymienionych w poprzedniej tabeli, lub ustaw `EnableDefaultCompileItems` właściwość na `false`, która wyłącza niejawne włączenie:

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Jeśli chcesz określić, na przykład niektóre pliki, aby uzyskać opublikowane w aplikacji, nadal można użyć znanych mechanizmów MSBuild do tego, na przykład `Content` elementu.

`EnableDefaultCompileItems`tylko wyłącza `Compile` globs, ale nie wpływa na `None` inne globs, \*jak niejawne glob, który ma również zastosowanie do .cs elementów. Z tego powodu Eksplorator \*rozwiązań w programie Visual Studio pokazuje `None` elementy .cs jako część projektu, zawarte jako elementy. Aby wyłączyć `None` niejawną `EnableDefaultNoneItems` `false`glob, należy ustawić na:

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Aby wyłączyć *wszystkie* niejawne `EnableDefaultItems` globy, ustaw właściwość na: `false`

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a>Dostosowywanie kompilacji

Istnieją różne sposoby [dostosowywania kompilacji.](/visualstudio/msbuild/customize-your-build) Można zastąpić właściwość, przekazując ją jako argument do [polecenia msbuild](/visualstudio/msbuild/msbuild-command-line-reference) lub [dotnet.](../tools/index.md) Można również dodać właściwość do pliku projektu lub do pliku *Directory.Build.props.* Aby uzyskać listę przydatnych właściwości dla projektów .NET Core, zobacz [Właściwości MSBuild dla projektów .NET Core SDK](msbuild-props.md).

### <a name="custom-targets"></a>Cele niestandardowe

.NET Podstawowe projekty można spakować niestandardowe obiekty docelowe MSBuild i właściwości do użycia przez projekty, które korzystają z pakietu. Użyj tego typu rozszerzalności, aby:

- Rozszerzanie procesu kompilacji.
- Dostęp do artefaktów procesu kompilacji, takich jak wygenerowane pliki.
- Sprawdź konfigurację, w ramach której jest wywoływana kompilacja.

Cele lub właściwości kompilacji niestandardowej można `<package_id>.targets` dodać, umieszczając pliki w formularzu lub `<package_id>.props` (na `Contoso.Utility.UsefulStuff.targets`przykład) w folderze *kompilacji* projektu.

Poniższy kod XML jest fragmentem kodu z pliku *csproj,* który instruuje [`dotnet pack`](../tools/dotnet-pack.md) polecenie, co spakować. Element `<ItemGroup Label="dotnet pack instructions">` umieszcza pliki obiektów docelowych w folderze *kompilacji* wewnątrz pakietu. Element `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` umieszcza zestawy i pliki *.json* w folderze *kompilacji.*

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

Aby korzystać z niestandardowego obiektu `PackageReference` docelowego w projekcie, dodaj element, który wskazuje pakiet i jego wersję. W przeciwieństwie do narzędzi pakiet niestandardowych obiektów docelowych znajduje się w zamknięciu zależności projektu zużywającego.

Można skonfigurować sposób używania niestandardowego obiektu docelowego. Ponieważ jest to obiekt docelowy MSBuild, może zależeć od danego obiektu docelowego, uruchomić `dotnet msbuild -t:<target-name>` po innym miejscu docelowym lub być wywoływane ręcznie za pomocą polecenia. Jednak aby zapewnić lepsze środowisko użytkownika, można połączyć narzędzia dla projektu i niestandardowe obiekty docelowe. W tym scenariuszu narzędzie na projekt akceptuje wszelkie parametry są potrzebne [`dotnet msbuild`](../tools/dotnet-msbuild.md) i przekłada się na wymagane wywołanie, które wykonuje obiekt docelowy. Możesz zobaczyć próbkę tego rodzaju synergii na [MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) próbki repozytorium w projekcie.

## <a name="see-also"></a>Zobacz też

- [Instalowanie programu .NET Core](../install/index.md)
- [Jak korzystać z sdk projektów MSBuild](/visualstudio/msbuild/how-to-use-project-sdk)
- [Pakiet niestandardowe obiekty docelowe i rekwizyty MSBuild za pomocą nuget](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
