---
title: Interfejs wiersza polecenia platformy .NET Core model rozszerzalności
description: Dowiedz się, jak można rozłożyć narzędzia interfejsu wiersza polecenia (CLI).
ms.date: 04/12/2017
ms.openlocfilehash: 4f49735fa94b2a7ee32e0d80590f9e680edeff16
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714182"
---
# <a name="net-core-cli-tools-extensibility-model"></a>Model rozszerzalności narzędzi interfejs wiersza polecenia platformy .NET Core

W tym dokumencie opisano różne sposoby rozszerzone narzędzia interfejsu wiersza polecenia (CLI) platformy .NET Core oraz wyjaśniono scenariusze, które obejmują każdy z nich.
Zobaczysz, jak korzystać z narzędzi, a także jak tworzyć różne typy narzędzi.

## <a name="how-to-extend-cli-tools"></a>Jak rozciągnąć narzędzia interfejsu wiersza polecenia
Narzędzia interfejsu wiersza polecenia można rozszerzyć na trzy główne sposoby:

1. [Za pośrednictwem pakietów NuGet dla poszczególnych projektów](#per-project-based-extensibility)

   Narzędzia dla poszczególnych projektów są zawarte w kontekście projektu, ale umożliwiają łatwe instalowanie poprzez przywracanie.

2. [Za pośrednictwem pakietów NuGet z niestandardowymi obiektami docelowymi](#custom-targets)

   Niestandardowe elementy docelowe pozwalają łatwo rozwijać proces kompilacji z zadaniami niestandardowymi.

3. [Za pośrednictwem ścieżki systemu](#path-based-extensibility)

   Narzędzia oparte na ścieżce są dobre dla ogólnych narzędzi do tworzenia projektów, których można użyć na pojedynczym komputerze.

Trzy opisane powyżej mechanizmy rozszerzalności nie są wyłączne. Można użyć jednej lub wszystkiego lub kombinacji tych elementów. Który z nich należy wybrać, zależy głównie od celu, który próbujesz osiągnąć przy użyciu rozszerzenia.

## <a name="per-project-based-extensibility"></a>Rozszerzalność na podstawie projektu
Narzędzia dla poszczególnych projektów są [wdrożeniami zależnymi od platformy](../deploying/index.md#framework-dependent-deployments-fdd) , które są dystrybuowane jako pakiety NuGet. Narzędzia są dostępne tylko w kontekście projektu, który odwołuje się do nich i dla którego są przywracane. Wywołanie poza kontekstem projektu (na przykład poza katalogiem zawierającym projekt) zakończy się niepowodzeniem, ponieważ nie można odnaleźć polecenia.

Narzędzia te są idealnym rozwiązaniem dla serwerów kompilacji, ponieważ nie jest wymagany żaden poza plikiem projektu. Proces kompilacji uruchamia przywracanie dla projektu, który kompiluje i dostępne są narzędzia. Projekty języka, takie jak F#, są również w tej kategorii, ponieważ każdy projekt może być zapisany tylko w jednym określonym języku.

Na koniec ten model rozszerzalności zapewnia obsługę tworzenia narzędzi, które wymagają dostępu do skompilowanych danych wyjściowych projektu. Na przykład różne narzędzia widoku Razor w aplikacjach [ASP.NET](https://www.asp.net/) MVC należą do tej kategorii.

### <a name="consuming-per-project-tools"></a>Zużywanie narzędzi dla projektu
Używanie tych narzędzi wymaga dodania elementu `<DotNetCliToolReference>` do pliku projektu dla każdego narzędzia, którego chcesz użyć. Wewnątrz elementu `<DotNetCliToolReference>` należy odwołać się do pakietu, w którym znajduje się narzędzie i określić wymaganą wersję. Po uruchomieniu [`dotnet restore`](dotnet-restore.md)narzędzie i jego zależności są przywracane.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

W przypadku narzędzi, które wymagają załadowania danych wyjściowych kompilacji projektu do wykonania, zazwyczaj istnieje inna zależność, która jest wymieniona w ramach zwykłych zależności w pliku projektu. Ponieważ interfejs wiersza polecenia używa programu MSBuild jako aparatu kompilacji, zalecamy, aby te części narzędzia były zapisywane jako niestandardowe [elementy docelowe](/visualstudio/msbuild/msbuild-targets) i [zadania](/visualstudio/msbuild/msbuild-tasks)programu MSBuild, ponieważ mogą one następnie wziąć udział w ogólnym procesie kompilacji. Ponadto mogą łatwo uzyskać wszystkie dane, które są tworzone przez kompilację, takie jak lokalizacja plików wyjściowych, Bieżąca konfiguracja utworzona i tak dalej. Wszystkie te informacje staną się zestawem właściwości programu MSBuild, które mogą być odczytywane z dowolnego celu. Aby dowiedzieć się, jak dodać niestandardowy obiekt docelowy przy użyciu narzędzia NuGet w dalszej części tego dokumentu.

Zapoznajmy się z przykładem dodawania prostych narzędzi tylko do prostej części projektu. Dane przykładowe polecenie o nazwie `dotnet-api-search`, które pozwala wyszukiwać pakiety NuGet dla określonego interfejsu API, poniżej przedstawiono plik projektu aplikacji konsolowej, który używa tego narzędzia:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

Element `<DotNetCliToolReference>` jest strukturalny w podobny sposób, jak element `<PackageReference>`. Wymaga identyfikatora pakietu zawierającego narzędzie i jego wersję, aby można było go przywrócić.

### <a name="building-tools"></a>Narzędzia do kompilowania
Jak wspomniano, narzędzia są tylko przenośnymi aplikacjami konsolowymi. Możesz tworzyć narzędzia, tak jak w przypadku tworzenia innej aplikacji konsolowej.
Po skompilowaniu należy użyć polecenia [`dotnet pack`](dotnet-pack.md) , aby utworzyć pakiet NuGet (plik. nupkg) zawierający kod, informacje o jego zależnościach itd. Możesz nadać dowolną nazwę pakietowi, ale aplikacja wewnątrz, rzeczywiste dane binarne narzędzia, musi być zgodna z Konwencją `dotnet-<command>`, aby `dotnet` mogła ją wywołać.

> [!NOTE]
> W wersjach wstępnej RC3 narzędzi wiersza polecenia programu .NET Core polecenie `dotnet pack` miało usterkę, która spowodowała, że plik *. runtimeconfig. JSON* nie został spakowany przy użyciu narzędzia. Brak tego pliku powoduje błędy w czasie wykonywania. Jeśli wystąpi takie zachowanie, pamiętaj o zaktualizowaniu do najnowszych narzędzi i spróbuj ponownie wykonać `dotnet pack`.

Ponieważ narzędzia są aplikacjami przenośnymi, użytkownik korzystający z tego narzędzia musi mieć wersję bibliotek .NET Core, dla których narzędzie zostało skompilowane w celu uruchomienia narzędzia. Każda inna zależność wykorzystywana przez narzędzie i, która nie jest zawarta w bibliotekach programu .NET Core, jest przywracana i umieszczana w pamięci podręcznej NuGet. W związku z tym, należy uruchomić polecenie przy użyciu zestawów z bibliotek .NET Core, a także zestawów z pamięci podręcznej NuGet.

Te rodzaje narzędzi mają wykres zależności, który jest całkowicie oddzielony od wykresu zależności projektu, który z nich korzysta. Proces przywracania najpierw przywraca zależności projektu, a następnie przywraca wszystkie narzędzia i ich zależności.

W [repozytorium interfejs wiersza polecenia platformy .NET Core](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects)można znaleźć bogatsze przykłady i różne kombinacje tych elementów.
Możesz również zobaczyć [implementację narzędzi używanych](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) w tym samym repozytorium.

## <a name="custom-targets"></a>Niestandardowe elementy docelowe

Pakiet NuGet ma możliwość [spakowania niestandardowych obiektów docelowych programu MSBuild i plików props](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package). Dzięki przenoszeniu narzędzi interfejs wiersza polecenia platformy .NET Core do korzystania z programu MSBuild ten sam mechanizm rozszerzania ma teraz zastosowanie do projektów .NET Core. Tego typu rozszerzalność należy użyć, gdy chcesz rozszerzać proces kompilacji lub Kiedy chcesz uzyskać dostęp do dowolnego artefaktu w procesie kompilacji, na przykład wygenerowanych plików, lub chcesz sprawdzić konfigurację, w której jest wywoływana kompilacja. itd.

W poniższym przykładzie można zobaczyć docelowy plik projektu przy użyciu składni `csproj`. Powoduje to nadanie [`dotnet pack`](dotnet-pack.md) polecenia do pakowania, umieszczenia plików docelowych oraz zestawów w folderze *kompilacji* wewnątrz pakietu. Zwróć uwagę na element `<ItemGroup>`, który ma właściwość `Label` ustawioną na `dotnet pack instructions`, i element docelowy zdefiniowany poniżej.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <Description>Sample Packer</Description>
    <VersionPrefix>0.1.0-preview</VersionPrefix>
    <TargetFramework>netstandard1.3</TargetFramework>
    <DebugType>portable</DebugType>
    <AssemblyName>SampleTargets.PackerTarget</AssemblyName>
  </PropertyGroup>
  <ItemGroup>
    <EmbeddedResource Include="Resources\Pkg\dist-template.xml;compiler\resources\**\*" Exclude="bin\**;obj\**;**\*.xproj;packages\**" />
    <None Include="build\SampleTargets.PackerTarget.targets" />
  </ItemGroup>
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
  <ItemGroup>
    <PackageReference Include="Microsoft.Extensions.DependencyModel" Version="1.0.1-beta-000933"/>
    <PackageReference Include="Microsoft.Build.Framework" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Microsoft.Build.Utilities.Core" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
  <ItemGroup />
  <PropertyGroup Label="Globals">
    <ProjectGuid>463c66f0-921d-4d34-8bde-7c9d0bffaf7b</ProjectGuid>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(TargetFramework)' == 'netstandard1.3' ">
    <DefineConstants>$(DefineConstants);NETSTANDARD1_3</DefineConstants>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <DefineConstants>$(DefineConstants);RELEASE</DefineConstants>
  </PropertyGroup>
</Project>
```

Używanie niestandardowych elementów docelowych odbywa się poprzez dostarczenie `<PackageReference>`, które wskazuje na pakiet i jego wersję w ramach rozszerzanego projektu. W przeciwieństwie do narzędzi, pakiet Custom targets zostanie uwzględniony w zamknięciu zależności projektu zużywanego.

Użycie niestandardowego obiektu docelowego zależy wyłącznie od sposobu jego konfiguracji. Ponieważ jest to element docelowy programu MSBuild, może on zależeć od danego elementu docelowego, działać po innej lokalizacji docelowej i może być również ręcznie wywoływany przy użyciu polecenia `dotnet msbuild -t:<target-name>`.

Jeśli jednak chcesz zapewnić użytkownikom lepszy interfejs użytkownika, możesz połączyć narzędzia dla poszczególnych projektów i niestandardowe elementy docelowe. W tym scenariuszu narzędzie dla poszczególnych projektów zasadniczo akceptuje wszelkie wymagane parametry i tłumaczy je na wymagane [`dotnet msbuild`](dotnet-msbuild.md) wywołanie, które wykona obiekt docelowy. Możesz zobaczyć przykład tego rodzaju synergii na repozytorium [przykładów hackathon szczytu MVP 2016](https://github.com/dotnet/MVPSummitHackathon2016) w projekcie [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) .

## <a name="path-based-extensibility"></a>Rozszerzalność oparta na ścieżce
Rozszerzalność oparta na ŚCIEŻKAch jest zwykle używana dla maszyn deweloperskich, gdzie potrzebujesz narzędzia, które koncepcyjnie omawia więcej niż jeden projekt. Główną wadą tego mechanizmu rozszerzenia jest to, że jest on powiązany z maszyną, na której znajduje się narzędzie. Jeśli potrzebujesz go na innym komputerze, musisz go wdrożyć.

Ten wzorzec rozszerzalności zestawu narzędzi interfejsu wiersza polecenia jest bardzo prosty. Jak opisano w [interfejs wiersza polecenia platformy .NET Core przegląd](index.md), `dotnet` sterownik może uruchomić dowolne polecenie o nazwie po Konwencji `dotnet-<command>`. Domyślna logika rozpoznawania w pierwszej sondy kilka lokalizacji, a wreszcie powraca do ścieżki systemowej. Jeśli żądane polecenie istnieje w ścieżce systemowej i jest plikiem binarnym, który można wywołać, `dotnet` sterownik wywoła go.

Plik musi być plikiem wykonywalnym. W systemach UNIX oznacza to, że wszystkie elementy mające bit Execute są ustawiane za pośrednictwem `chmod +x`. W systemie Windows można używać plików *cmd* .

Przyjrzyjmy się bardzo prostej implementacji narzędzia "Hello world". Będziemy używać obu `bash` i `cmd` w systemie Windows.
Następujące polecenie spowoduje po prostu Echo "Hello world" do konsoli programu.

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

W systemie macOS można zapisać ten skrypt jako `dotnet-hello` i ustawić jego bit wykonywalny z `chmod +x dotnet-hello`. Następnie możemy utworzyć symboliczny link do niego w `/usr/local/bin` przy użyciu `ln -s <full_path>/dotnet-hello /usr/local/bin/`poleceń. Dzięki temu można wywołać polecenie przy użyciu składni `dotnet hello`.

W systemie Windows można zapisać ten skrypt jako `dotnet-hello.cmd` i umieścić go w lokalizacji, która znajduje się w ścieżce systemowej (lub można ją dodać do folderu, który znajduje się już w ścieżce). Następnie możesz użyć `dotnet hello`, aby uruchomić ten przykład.
