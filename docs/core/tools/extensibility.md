---
title: Model rozszerzalności interfejsu wiersza polecenia platformy .NET core
description: Dowiedz się, jak można je rozszerzyć narzędzi interfejsu wiersza polecenia (CLI).
author: blackdwarf
ms.author: mairaw
ms.date: 04/12/2017
ms.openlocfilehash: 9f54479704f547ada567619a82b24a47a0b104c4
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47078054"
---
# <a name="net-core-cli-tools-extensibility-model"></a>Model rozszerzalności narzędzi interfejsu wiersza polecenia platformy .NET core

W tym dokumencie opisano różne sposoby, można rozszerzyć narzędzia .NET Core interfejsu wiersza polecenia (CLI) i opisano scenariusze, które dysków z każdej z nich z nich.
Zobaczysz, jak używać narzędzi, a także jak tworzyć różne typy narzędzi.

## <a name="how-to-extend-cli-tools"></a>Jak rozszerzyć narzędzi interfejsu wiersza polecenia
Narzędzia interfejsu wiersza polecenia można rozszerzyć na trzy sposoby:

1. [Za pomocą pakietów NuGet w poszczególnych projektów](#per-project-based-extensibility)

   Narzędzia dla projektu są zawarte w kontekście projektu, ale pozwalają łatwej instalacji przy użyciu przywracania.

2. [Za pomocą pakietów NuGet z niestandardowych elementów docelowych](#custom-targets)

   Niestandardowe obiekty docelowe pozwalają w prosty sposób rozszerzyć proces kompilacji przy użyciu niestandardowych zadań.

3. [Za pomocą ścieżki systemowej](#path-based-extensibility)

   Narzędzia oparte na ŚCIEŻCE dla zastosowań dobre są ogólne, między projektami narzędzia, które można używać na jednym komputerze.

Trzy mechanizmy rozszerzania opisanych powyżej, nie są wyłączne. Można użyć jednego lub wszystkich, lub ich kombinacji. Który z nich do wybrania zależy od większości cel, który próbujesz osiągnąć za pomocą rozszerzenia.

## <a name="per-project-based-extensibility"></a>Na podstawie rozszerzalność projektu
Narzędzia dla projektu są [wdrożeń zależny od struktury](../deploying/index.md#framework-dependent-deployments-fdd) dystrybuowanych jako pakiety NuGet. Narzędzia są dostępne tylko w kontekście projektu, który odwołuje się do nich i dla których zostaną przywrócone. Wywołanie poza kontekstem projektu (na przykład spoza katalogu, który zawiera projekt) zakończy się niepowodzeniem, ponieważ nie można odnaleźć polecenia.

Te narzędzia są doskonałe dla serwerów kompilacji, ponieważ nic nie poza plik projektu jest wymagana. Uruchamia proces kompilacji dla projektu go przywrócić kompilacje i narzędzia będą dostępne. Projekty języka, takie jak F # są również w tej kategorii, ponieważ każdy projekt może być zapisany tylko w jednym języku określonych.

Na koniec tego modelu rozszerzalności zapewnia obsługę tworzenia narzędzi, które muszą mieć dostęp do skompilowanych danych wyjściowych projektu. Na przykład widoku Razor dla różnych narzędzi w [ASP.NET](https://www.asp.net/) aplikacji MVC należą do tej kategorii.

### <a name="consuming-per-project-tools"></a>Korzystanie z narzędzi dla projektów
Korzystanie z tych narzędzi, musisz dodać `<DotNetCliToolReference>` element do pliku projektu dla każdego narzędzia, którego chcesz użyć. Wewnątrz `<DotNetCliToolReference>` elementu, należy odwołują się do pakietu, w której znajduje się narzędzie i określić wersji, potrzebujesz. Po uruchomieniu [ `dotnet restore` ](dotnet-restore.md), narzędzie i jego zależności zostaną przywrócone.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Narzędzia, które należy załadować dane wyjściowe kompilacji projektu do wykonania jest zazwyczaj inny współzależność, która znajduje się w obszarze regularne zależności w pliku projektu. Ponieważ interfejs wiersza polecenia używa programu MSBuild jako jego aparatu kompilacji, zaleca się zapisać te elementy narzędzia w postaci niestandardowych MSBuild [cele](/visualstudio/msbuild/msbuild-targets) i [zadania](/visualstudio/msbuild/msbuild-tasks), ponieważ są one następnie wzięcia udziału w całego procesu kompilacji. Ponadto otrzymują wszystkie dane, łatwo utworzonym za pomocą kompilacji, takie jak lokalizacja plików wyjściowych bieżącej konfiguracji kompilowanego na bieżąco, itd. Wszystkie te informacje będą zbiór właściwości programu MSBuild, które mogą być odczytywane z dowolnej docelowej. Możesz dowiedzieć się, jak dodać niestandardowe obiekty docelowe, za pomocą narzędzia NuGet w dalszej części tego dokumentu.

Omówmy teraz przykład dodawania proste narzędzie tylko do narzędzia do prostego projektu. Biorąc pod uwagę przykładowe polecenie o nazwie `dotnet-api-search` dzięki niemu można będzie przeszukiwać pakietów NuGet dla określonego interfejsu API, w tym miejscu jest plik projektu aplikacji konsoli, który korzysta z tego narzędzia:

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

`<DotNetCliToolReference>` Elementu są skonstruowane w podobny sposób jak `<PackageReference>` elementu. Musi ona identyfikator pakietu pakiet zawierający narzędzia i jego wersji, można przywrócić.

### <a name="building-tools"></a>Narzędzia do konstruowania
Jak wspomniano, narzędzia są aplikacje konsoli po prostu przenośnej. Możesz tworzyć narzędzi, jak tworzysz czy inna aplikacja konsoli.
Po jego tworzenia, należy użyć [ `dotnet pack` ](dotnet-pack.md) polecenie, aby utworzyć pakiet NuGet (plik .nupkg), który zawiera kod, informacje o jego zależności i tak dalej. Można nadać dowolną nazwę pakietu, ale aplikacji w narzędziu rzeczywiste binarne, musi być zgodna z Konwencją `dotnet-<command>` aby `dotnet` aby można było ją wywołać.

> [!NOTE]
> W wersji pre-RC3 narzędzia wiersza polecenia platformy .NET Core `dotnet pack` polecenia miał usterkę powodującą `runtime.config.json` nie będzie bogatymi w narzędziu. Brak wyników tego pliku, błędy w czasie wykonywania. Jeśli wystąpi ten problem, należy zaktualizować do najnowszych narzędzi i spróbuj `dotnet pack` ponownie.

Narzędzia są aplikacje przenośne, użytkowników, korzystanie z narzędzia musi mieć wersję biblioteki .NET Core, które narzędzie została skompilowana, aby można było uruchomić narzędzie. Wszelkich innych zależności, że używa narzędzie i który nie jest zawarty w biblioteki .NET Core jest przywracane i umieszczane w pamięci podręcznej narzędzia NuGet. Cały dlatego uruchomienie narzędzia przy użyciu zestawów z biblioteki .NET Core, a także zestawy z pamięcią podręczną programu NuGet.

Tego rodzaju narzędzia ma wykres zależności, które łączą się z wykresu zależności projektu, który używa ich. Proces przywracania najpierw przywraca zależności projektu, a następnie przywrócenie wszystkich narzędzi i ich zależności.

Można znaleźć przykłady bardziej rozbudowane i różnych kombinacji w [repozytorium interfejsu wiersza polecenia platformy .NET Core](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).
Można również wyświetlić [implementacji narzędzia używane](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) w tym samym repozytorium.

### <a name="custom-targets"></a>Niestandardowe obiekty docelowe
NuGet ma możliwość [pakiet niestandardowego programu MSBuild cele i pliki właściwości](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package). Wraz z przejściem narzędzi interfejsu wiersza polecenia platformy .NET Core, za pomocą programu MSBuild ten sam mechanizm rozszerzalności teraz ma zastosowanie do projektów .NET Core. Będzie używać tego typu rozszerzeń, gdy chcesz rozszerzyć proces kompilacji lub chcesz uzyskać dostęp do dowolnego z artefaktów w procesie kompilacji, takie jak wygenerowanych plików lub chcesz sprawdzić konfigurację w ramach której zostanie wywołana kompilacji , itp.

W poniższym przykładzie można zobaczyć projekt docelowy plik za pomocą `csproj` składni. To powoduje, że [ `dotnet pack` ](dotnet-pack.md) polecenia wybierania elementów do pakietu, umieszczania plików obiektów docelowych, a także zestawy w *kompilacji* folder wewnątrz pakietu. Zwróć uwagę `<ItemGroup>` element, który ma `Label` właściwością `dotnet pack instructions`, i docelowy zdefiniowane poniżej.

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

Korzystanie z niestandardowych elementów docelowych to zrobić, podając `<PackageReference>` wskazującego na pakiet i jego wersji wewnątrz projektu, który jest rozszerzany. W przeciwieństwie do narzędzia ujęte pakietu niestandardowe obiekty docelowe do zamknięcia zależności projektu odbierająca komunikaty.

Przy użyciu niestandardowe obiekty docelowe zależy wyłącznie od konfiguracji. Ponieważ jest obiekt docelowy programu MSBuild, może zależeć na danym obiektem docelowym Uruchom po innym elementem docelowym i może również być ręcznego wywołania odbywa się przy użyciu `dotnet msbuild -t:<target-name>` polecenia.

Jednak jeśli chcesz zapewnić lepsze środowisko użytkownika do użytkowników, można połączyć narzędzi dla projektów i niestandardowych elementów docelowych. W tym scenariuszu narzędzie-projekt będzie zasadniczo wystarczy zaakceptować dowolnie wymagane parametry i czy tłumaczenie, wymagane [ `dotnet msbuild` ](dotnet-msbuild.md) wywołania, które element docelowy jest wykonywany. Przykład tego rodzaju synergii może zobaczyć na [przykłady MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) repozytorium w [ `dotnet-packer` ](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) projektu.

### <a name="path-based-extensibility"></a>Rozszerzalność opartego na ŚCIEŻKACH
Rozszerzalność opartego na ŚCIEŻKACH jest zazwyczaj używane do tworzenia maszyn wymagających to narzędzie, które pod względem koncepcyjnym obejmuje więcej niż jednego projektu. Główną wadą tego mechanizmu rozszerzenia jest, że jest powiązany z maszyną której istnieje narzędzie. Jeśli potrzebujesz jej na innym komputerze, trzeba ją wdrożyć.

Ten wzorzec rozszerzalności narzędzi interfejsu wiersza polecenia jest bardzo proste. Zgodnie z opisem w [omówienie interfejsu wiersza polecenia platformy .NET Core](index.md), `dotnet` sterownik można uruchomić dowolne polecenie, który nosi nazwę po `dotnet-<command>` Konwencji. Domyślnej logiki rozpoznawania najpierw sondy w kilku lokalizacjach, a na koniec przechodzi do ścieżki systemu. Jeśli żądane polecenie w systemie ŚCIEŻKA istnieje i jest plik binarny, który może być wywołana, `dotnet` sterowników będzie go wywoływać.

Plik musi być pliku wykonywalnego. W systemach Unix, oznacza to wszystko, co ma ustawiony bit wykonania za pośrednictwem `chmod +x`. Windows, mogą używać *cmd* plików.

Spójrzmy na bardzo proste Wdrażanie narzędzia "Hello World". Będziemy używać zarówno `bash` i `cmd` na Windows.
Następujące polecenie będzie po prostu echo "Hello World" do konsoli.

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

W systemie macOS można zapisać skrypt jako `dotnet-hello` i ustaw jego bit pliku wykonywalnego z `chmod +x dotnet-hello`. Następnie możemy utworzyć łącze symboliczne do niego w `/usr/local/bin` za pomocą polecenia `ln -s <full_path>/dotnet-hello /usr/local/bin/`. Umożliwi to można wywołać za pomocą polecenia `dotnet hello` składni.

W systemie Windows, firma Microsoft można zapisać skrypt jako `dotnet-hello.cmd` i umieścić go w lokalizacji, która znajduje się w ścieżce systemu (lub można dodać go do folderu, który już znajduje się w ścieżce). Dzięki temu wystarczy użyć `dotnet hello` do uruchomienia tego przykładu.
