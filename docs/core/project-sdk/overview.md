---
title: Omówienie sdk projektu .NET Core
description: Dowiedz się więcej o zestawach SDK projektu .NET Core.
ms.date: 02/02/2020
ms.topic: conceptual
ms.openlocfilehash: 32e14993326c6f17d6470249fe5a545180348631
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399176"
---
# <a name="net-core-project-sdks"></a>Zestawy SDK projektu .NET Core

Projekty .NET Core są skojarzone z zestawem sdk (Software Development Kit). Każdy zestaw SDK projektu jest [zestawem obiektów docelowych](/visualstudio/msbuild/msbuild-targets) MSBuild i skojarzonych [zadań,](/visualstudio/msbuild/msbuild-tasks) które są odpowiedzialne za kompilowanie, pakowanie i publikowanie kodu.

## <a name="available-sdks"></a>Dostępne zestawy SDK

Dla programu .NET Core dostępne są następujące zestawy SDK:

| ID | Opis | Repo|
| - | - | - |
| `Microsoft.NET.Sdk` | Zestaw SDK rdzenia .NET | https://github.com/dotnet/sdk |
| `Microsoft.NET.Sdk.Web` | Zestaw [SDK sieci Web](/aspnet/core/razor-pages/web-sdk) .NET Core | https://github.com/aspnet/websdk |
| `Microsoft.NET.Sdk.Razor` | Zestaw [SDK do golenia](/aspnet/core/razor-pages/sdk) .NET Core |
| `Microsoft.NET.Sdk.Worker` | Zestaw SDK usługi podstawowego procesu roboczego .NET |
| `Microsoft.NET.Sdk.WindowsDesktop` | Zestaw SDK winforms programu .NET Core i WPF |

Zestaw SDK .NET Core jest podstawowym zestawem SDK dla programu .NET Core. Inne zestawy SDK odwołują się do sdk .NET Core, a projekty skojarzone z innymi zestawami SDK mają wszystkie dostępne właściwości sdk .NET Core. Na przykład zestaw Web SDK zależy zarówno od sdk .NET Core, jak i zestaw SDK razor.

Można również autora własnego sdk, które mogą być dystrybuowane za pośrednictwem NuGet.

## <a name="project-files"></a>Pliki projektu

Projekty .NET Core są oparte na formacie [MSBuild.](/visualstudio/msbuild/msbuild) Pliki projektu, które mają rozszerzenia, takie jak *.csproj* dla projektów C# i *.fsproj* dla projektów F#, są w formacie XML. Elementem głównym pliku projektu MSBuild jest [element projektu.](/visualstudio/msbuild/project-element-msbuild) Element `Project` ma opcjonalny `Sdk` atrybut, który określa, który zestaw SDK (i wersja) do użycia. Aby użyć narzędzi .NET Core i utworzyć `Sdk` kod, ustaw atrybut na jeden z identyfikatorów w tabeli [Dostępne zestawy SDK.](#available-sdks)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  ...
</Project>
```

Aby określić zestaw SDK, który pochodzi z NuGet, dołącz wersję na końcu nazwy lub określ nazwę i wersję w pliku *global.json.*

```xml
<Project Sdk="MSBuild.Sdk.Extras/2.0.54">
  ...
</Project>
```

Innym sposobem określenia sdk jest z najwyższego poziomu [Sdk](/visualstudio/msbuild/sdk-element-msbuild) element:

```xml
<Project>
  <Sdk Name="Microsoft.NET.Sdk" />
  ...
</Project>
```

Odwoływanie się do sdk w jeden z tych sposobów znacznie upraszcza pliki projektu dla .NET Core. Podczas oceny projektu, MSBuild dodaje niejawne importy w `Sdk.props` `Sdk.targets` górnej części pliku projektu i u dołu.

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
> Na komputerze z systemem Windows pliki *Sdk.props* i *Sdk.targets* można znaleźć w folderze *%ProgramFiles%\dotnet\sdk\\[version]\Sdks\Microsoft.NET.Sdk\Sdk.Sdk.in.*

### <a name="preprocess-the-project-file"></a>Wstępne przetwarzanie pliku projektu

Możesz zobaczyć w pełni rozwinięty projekt, jak MSBuild widzi go po sdk i jego cele są uwzględniane za pomocą `dotnet msbuild -preprocess` polecenia. Przełącznik [preprocess](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) [`dotnet msbuild`](../tools/dotnet-msbuild.md) polecenia pokazuje, które pliki są importowane, ich źródła i ich wkład do kompilacji bez faktycznie tworzenia projektu.

Jeśli projekt ma wiele struktur docelowych, skoncentruj wyniki polecenia tylko na jednej strukturze, określając go jako właściwość MSBuild. Przykład:

`dotnet msbuild -property:TargetFramework=netcoreapp2.0 -preprocess:output.xml`

### <a name="default-compilation-includes"></a>Domyślna kompilacja zawiera

Domyślne zawiera i wyklucza dla elementów kompilacji i osadzonych zasobów są zdefiniowane w zestawie SDK. W przeciwieństwie do projektów innych niż SDK .NET Framework, nie trzeba określać te elementy w pliku projektu, ponieważ wartości domyślne obejmują najbardziej typowych przypadków użycia. Prowadzi to do mniejszych plików projektu, które są łatwiejsze do zrozumienia, a także edytować ręcznie, w razie potrzeby.

W poniższej tabeli przedstawiono, który element i [które globy](https://en.wikipedia.org/wiki/Glob_(programming)) są uwzględniane i wykluczane w zestawie .NET Core SDK:

| Element           | Uwzględnij glob                              | Wykluczyć glob                                                  | Usuń glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|--------------------------|
| Skompilować           | \*\*/\*.cs (lub rozszerzenia innych języków) | \*\*/\*.user;  \*\*/\*. \*proj;  \* \* / \*  \* \* /.vssscc \*(vssscc)  | Nie dotyczy                      |
| Osadzony zasób  | \*\*/\*.resx                              | \*\*/\*.user; \*\*/\*. \*proj; \* \* / \* \* \* /.vssscc \*(vssscc)     | Nie dotyczy                      |
| Brak              | \*\*/\*                                   | \*\*/\*.user; \*\*/\*. \*proj; \* \* / \* \* \* /.vssscc \*(vssscc)     | \*\*/\*.cs; \* \* /.resx \*(resx) |

> [!NOTE]
> I `./bin` `./obj` foldery, które są reprezentowane `$(BaseOutputPath)` `$(BaseIntermediateOutputPath)` przez i MSBuild właściwości, są domyślnie wyłączone z globs. Wykluczenia są reprezentowane przez `$(DefaultItemExcludes)`właściwość .

Jeśli jawnie zdefiniujesz te elementy w pliku projektu, prawdopodobnie zostanie unikniesz następującego błędu:

**Zduplikowane elementy kompilacji zostały uwzględnione. Zestaw SDK .NET domyślnie zawiera elementy kompilacji z katalogu projektu. Można usunąć te elementy z pliku projektu lub ustawić właściwość "EnableDefaultCompileItems" na "false", jeśli chcesz jawnie uwzględnić je w pliku projektu.**

Aby rozwiązać ten błąd, `Compile` usuń jawne elementy, które pasują do niejawnych `EnableDefaultCompileItems` wymienionych `false`w poprzedniej tabeli, lub ustaw właściwość , która wyłącza niejawne włączenie:

```xml
<PropertyGroup>
  <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Jeśli chcesz określić, na przykład, niektóre pliki, aby uzyskać opublikowane z aplikacją, nadal można użyć `Content` znanych mechanizmów MSBuild dla tego, na przykład element.

`EnableDefaultCompileItems`wyłącza tylko `Compile` globs, ale nie ma wpływu na `None` inne globs, \*jak niejawny glob, który odnosi się również do elementów .cs. Z tego powodu Eksplorator rozwiązań w programie Visual Studio pokazuje \*elementy .cs jako część projektu, uwzględnione jako `None` elementy. Aby wyłączyć `None` niejawny glob, ustaw `EnableDefaultNoneItems` na `false`:

```xml
<PropertyGroup>
  <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Aby wyłączyć *wszystkie* niejawne `EnableDefaultItems` globs, należy ustawić właściwość na: `false`

```xml
<PropertyGroup>
  <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="customize-the-build"></a>Dostosowywanie kompilacji

Istnieją różne sposoby [dostosowywania kompilacji.](/visualstudio/msbuild/customize-your-build) Można zastąpić właściwość, przekazując ją jako argument do polecenia [msbuild](/visualstudio/msbuild/msbuild-command-line-reference) lub [dotnet.](../tools/index.md) Można również dodać właściwość do pliku projektu lub pliku *Directory.Build.props.* Aby uzyskać listę przydatnych właściwości dla projektów programu .NET Core, zobacz [właściwości MSBuild dla projektów SDK .NET Core](msbuild-props.md).

### <a name="custom-targets"></a>Niestandardowe cele

.NET Core projekty można spakować niestandardowe msbuild cele i właściwości do użytku przez projekty, które zużywają pakiet. Użyj tego typu rozszerzalności, jeśli chcesz:

- Rozszerz proces kompilacji.
- Dostęp artefakty procesu kompilacji, takich jak wygenerowane pliki.
- Sprawdź konfigurację, w której jest wywoływana kompilacja.

Dodaj niestandardowe obiekty docelowe kompilacji lub właściwości, `<package_id>.props` umieszczając pliki `Contoso.Utility.UsefulStuff.targets`w formularzu `<package_id>.targets` lub (na przykład) w folderze *kompilacji* projektu.

Poniższy kod XML jest urywkiem pliku *csproj,* [`dotnet pack`](../tools/dotnet-pack.md) który instruuje polecenie, co spakować. Element `<ItemGroup Label="dotnet pack instructions">` umieszcza pliki docelowe w folderze *kompilacji* wewnątrz pakietu. Element `<Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">` umieszcza zestawy i pliki *json* w folderze *kompilacji.*

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

Aby użyć niestandardowego obiektu docelowego `PackageReference` w projekcie, dodaj element, który wskazuje pakiet i jego wersję. W przeciwieństwie do narzędzi pakiet niestandardowych obiektów docelowych znajduje się w zamknięciu zależności zużywania projektu.

Można skonfigurować sposób używania niestandardowego obiektu docelowego. Ponieważ jest to obiekt docelowy MSBuild, może zależeć od danego obiektu docelowego, uruchomić `dotnet msbuild -t:<target-name>` po innym miejscu docelowym lub być wywoływane ręcznie za pomocą polecenia. Jednak aby zapewnić lepsze środowisko użytkownika, można połączyć narzędzia dla poszczególnych projektów i niestandardowe cele. W tym scenariuszu narzędzie dla projektu akceptuje wszystkie parametry są potrzebne i [`dotnet msbuild`](../tools/dotnet-msbuild.md) przekłada się na wymagane wywołanie, które wykonuje obiekt docelowy. Możesz zobaczyć próbkę tego rodzaju synergii na [MVP Summit 2016 Hackathon próbki](https://github.com/dotnet/MVPSummitHackathon2016) repo w [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) projekcie.

## <a name="see-also"></a>Zobacz też

- [Instalowanie programu .NET Core](../install/index.md)
- [Jak korzystać z zestawów SDK projektu MSBuild](/visualstudio/msbuild/how-to-use-project-sdk)
- [Pakiet niestandardowych celów MSBuild i rekwizyty z NuGet](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package)
