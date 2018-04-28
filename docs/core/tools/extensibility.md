---
title: Modelu rozszerzalności .NET core interfejsu wiersza polecenia
description: Dowiedz się, jak można rozszerzyć narzędzi interfejsu wiersza polecenia (CLI).
author: blackdwarf
ms.author: mairaw
ms.date: 04/12/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 11cf9843f5c10ed7114d45a8c6be0ffeff2b6bad
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="net-core-cli-tools-extensibility-model"></a>Modelu rozszerzalności narzędzi interfejsu wiersza polecenia platformy .NET core

W tym dokumencie opisano różne sposoby, można rozszerzyć narzędzia .NET Core interfejsu wiersza polecenia (CLI) i opisano scenariusze, które dysków w każdej z nich z nich.
Zobaczysz, jak korzystać z narzędzia, a także sposób tworzenia różnych typów narzędzi.

## <a name="how-to-extend-cli-tools"></a>Jak rozszerzyć narzędzi interfejsu wiersza polecenia
Narzędzi interfejsu wiersza polecenia można ją rozszerzyć, przede wszystkim na trzy sposoby:

1. [Za pomocą pakietów NuGet dla projektu](#per-project-based-extensibility)

  -Projekt narzędzia są dostępne w kontekście projektu, ale pozwalają łatwo instalacji przez Przywracanie.

2. [Za pomocą pakietów NuGet z niestandardowych elementów docelowych](#custom-targets)

  Niestandardowe elementy docelowe pozwalają łatwo rozszerzyć proces kompilacji z niestandardowych zadań.

3. [Za pomocą ścieżki systemu](#path-based-extensibility)

  Narzędzia oparte na ŚCIEŻCE są odpowiednie w ogólne, między projektami narzędzia, której można używać na jednym komputerze.

Trzy mechanizmy rozszerzania opisanych powyżej nie są wyłączne. Można użyć jednego lub wszystkich, lub ich kombinacji. Która z nich do pobrania zależy przede wszystkim od cel, który chcesz osiągnąć z rozszerzeniem.

## <a name="per-project-based-extensibility"></a>Na podstawie rozszerzalność projektu
Narzędzia dla projektu są [wdrożeń zależne od framework](../deploying/index.md#framework-dependent-deployments-fdd) dystrybuowanych jako pakietów NuGet. Narzędzia są dostępne tylko w kontekście projektu, który odwołuje się do nich i dla których zostaną przywrócone. Wywołanie poza kontekstem projektu (na przykład spoza katalogu, który zawiera projekt) zakończy się niepowodzeniem, ponieważ nie można odnaleźć polecenia.

Te narzędzia są idealne w przypadku serwerów kompilacji, ponieważ nic poza pliku projektu jest potrzebny. Uruchamia proces kompilacji projektu go przywrócić kompilacji i narzędzi będzie dostępna. Projekty języka, takie jak F # są również w tej kategorii, ponieważ każdego projektu można zapisywać tylko w jednym języku określonych.

Na koniec tego modelu rozszerzalności zapewnia obsługę tworzenia narzędzi, które wymagają dostępu do skompilowanych danych wyjściowych projektu. Na przykład widoku Razor różnych narzędzi w [ASP.NET](https://www.asp.net/) aplikacji MVC należą do tej kategorii.

### <a name="consuming-per-project-tools"></a>Korzystanie z narzędzia — projekt
Korzystanie z tych narzędzi, musisz dodać `<DotNetCliToolReference>` elementu do pliku projektu dla każdego narzędzia, którego chcesz użyć. Wewnątrz `<DotNetCliToolReference>` element, należy odwołują się do pakietu, w której znajduje się narzędzie i określ wersję należy. Po uruchomieniu [ `dotnet restore` ](dotnet-restore.md), narzędzia i jego zależności są przywracane.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Narzędzia, które należy załadować danych wyjściowych kompilacji projektu do wykonania jest zazwyczaj innego zależności, która jest wyświetlana w obszarze regularne zależności w pliku projektu. Ponieważ interfejsu wiersza polecenia używa MSBuild jako jego aparatu kompilacji, zaleca się te części narzędzie mieć postać MSBuild niestandardowych [elementy docelowe](/visualstudio/msbuild/msbuild-targets) i [zadania](/visualstudio/msbuild/msbuild-tasks), ponieważ ich mogą następnie skorzystać całego procesu kompilacji. Ponadto może uzyskać wszystkie dane, łatwo utworzonym za pomocą kompilacji, takie jak lokalizacja plików wyjściowych bieżącej konfiguracji konstruowany itp. Wszystkie te informacje będą zbiór właściwości programu MSBuild, które mogą być odczytywane z dowolnego miejsca docelowego. Jak dodać element docelowy niestandardowych przy użyciu narzędzia NuGet w dalszej części tego dokumentu jest widoczny.

Umożliwia przeglądanie przykład dodawania prostego narzędzia tylko narzędzia do prostego projektu. Podano przykładowe polecenie o nazwie `dotnet-api-search` umożliwiają wyszukiwanie za pomocą pakietów NuGet dla określonego interfejsu API, w tym miejscu to pliku projektu aplikacji konsoli, która używa tego narzędzia:

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

`<DotNetCliToolReference>` Elementów ma strukturę w podobny sposób jak `<PackageReference>` elementu. Musi on identyfikator pakietu pakietu zawierającego narzędzie oraz jego wersję, można go przywrócić.

### <a name="building-tools"></a>Narzędzia do budowania
Jak wspomniano, narzędzia są aplikacje konsoli po prostu przenośnej. Narzędzi kompilacji, podczas tworzenia czy inna aplikacja konsoli.
Po jego tworzenia, należy użyć [ `dotnet pack` ](dotnet-pack.md) polecenie, aby utworzyć pakiet NuGet (pliku .nupkg), który zawiera kod, informacje o jego zależności itd. Można przekazać dowolną nazwę pakietu, ale aplikacja wewnątrz narzędzie rzeczywiste binarnego, musi być zgodne z Konwencją `dotnet-<command>` aby `dotnet` aby można było ją wywołać.

> [!NOTE]
> W wersji pre-RC3 narzędzi wiersza polecenia platformy .NET Core `dotnet pack` polecenia miał usterkę, która spowodowała `runtime.config.json` nie pakowane za pomocą narzędzia. Brak wyników tego pliku błędy w czasie wykonywania. Jeśli wystąpi ten problem, należy zaktualizować najnowsze narzędzia i spróbuj `dotnet pack` ponownie.

Ponieważ narzędzia przenośnych aplikacji, użytkowników korzystających z narzędzia musi mieć wersję biblioteki .NET Core, w których narzędzie został utworzony przed uruchomienie tego narzędzia. Inne zależności, czy używane narzędzie i który nie jest zawarty w bibliotek .NET Core jest przywrócona i umieszczane w pamięci podręcznej NuGet. Cały dlatego uruchomienie narzędzia przy użyciu zestawów z bibliotek .NET Core, a także zestawy z pamięci podręcznej NuGet.

Tego rodzaju narzędzia ma wykres zależności, który jest całkowicie niezależna od na wykresie zależności projektu, który używa tych. Proces przywracania najpierw przywraca zależności projektu i następnie przywrócenie wszystkich narzędzi oraz ich zależności.

Można znaleźć przykłady bardziej zaawansowane funkcje i to w różnych kombinacji [repozytorium interfejsu wiersza polecenia platformy .NET Core](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).
Możesz również sprawdzić [implementacji narzędzia używane](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) w tym samym repozytorium.

### <a name="custom-targets"></a>Niestandardowe elementy docelowe
NuGet ma możliwość [pakiet niestandardowy MSBuild cele i pliki właściwości](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package). Wraz z przejściem z narzędzi .NET Core interfejsu wiersza polecenia, użyj programu MSBuild sam mechanizm rozszerzalności teraz ma zastosowanie do projektów platformy .NET Core. Czy używać tego typu rozszerzeń, gdy chcesz rozszerzyć procesu kompilacji lub chcesz uzyskać dostępu do żadnego artefaktów w procesie kompilacji, takich jak pliki generowane lub chcesz sprawdzić konfigurację, pod którą jest wywoływany kompilacji , itp.

W poniższym przykładzie widać projektu docelowego pliku przy użyciu `csproj` składni. To powoduje, że [ `dotnet pack` ](dotnet-pack.md) polecenia wybierania elementów do pakietu, umieszczenie plików elementy docelowe, a także zestawów do *kompilacji* folderu w pakiecie. Powiadomienie `<ItemGroup>` element, który ma `Label` ustawioną właściwość `dotnet pack instructions`, i element docelowy zdefiniowana poniżej.

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

Korzystanie z niestandardowych elementów docelowych to zrobić, podając `<PackageReference>` wskazującego pakiet i jego wersja wewnątrz projektu, który zostanie rozszerzone. W przeciwieństwie do narzędzia ujęte pakietu niestandardowe obiekty docelowe do zamknięcia zależności projektu odbierającą.

Przy użyciu niestandardowych docelowych zależy od wyłącznie konfiguracji. Ponieważ jest element docelowy programu MSBuild, może zależeć na dany obiekt docelowy, uruchom po inny element docelowy i może również być ręcznie wywoływane przy użyciu `dotnet msbuild /t:<target-name>` polecenia.

Jednak jeśli chcesz zapewnić lepsze środowisko dla użytkowników, możesz łączyć narzędzia na projekt i niestandardowych obiektów docelowych. W tym scenariuszu narzędzie-projekt będzie zasadniczo wystarczy zaakceptować wymagane parametry i przekłada który do wymaganych [ `dotnet msbuild` ](dotnet-msbuild.md) wywołanie, którego elementem docelowym jest wykonywany. Można wyświetlić na przykład tego rodzaju współdziałania [przykłady MVP szczytu 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) repozytorium w [ `dotnet-packer` ](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) projektu.

### <a name="path-based-extensibility"></a>Na podstawie ścieżki rozszerzalności
Rozszerzalność na podstawie ścieżki jest zazwyczaj używane do tworzenia maszyn wymagających narzędziem koncepcyjnie obejmuje więcej niż jednego projektu. Główną wadą tego mechanizmu rozszerzenia jest, że zostały powiązane z maszyną gdzie narzędzie istnieje. Jeśli potrzebujesz go na innym komputerze, trzeba jej wdrożenia.

Ten wzorzec rozszerzalność narzędzi interfejsu wiersza polecenia jest bardzo prosty. Jak opisano w [omówienie interfejsu wiersza polecenia platformy .NET Core](index.md), `dotnet` sterownik można uruchomić z dowolnego polecenia o nazwie po `dotnet-<command>` Konwencji. Domyślna logika rozpoznawania najpierw sondy w kilku lokalizacjach, a na koniec przechodzi do systemowej PATH. Jeśli żądanego polecenia w systemie ŚCIEŻKA istnieje i jest plikiem binarnym, która może zostać wywołana, `dotnet` sterownik wywoła go.

Plik musi być wykonywalne. W systemach Unix, oznacza to wszystko, co ma ustawiony bit execute za pośrednictwem `chmod +x`. W systemie Windows, można użyć *cmd* plików.

Spójrzmy na bardzo prosta implementacja narzędzia "Hello World". Używamy zarówno `bash` i `cmd` w systemie Windows.
Następujące polecenie spowoduje po prostu echo "Hello World" w konsoli.

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

Na macOS, można zapisać ten skrypt jako `dotnet-hello` i ustawić jej bit pliku wykonywalnego z `chmod +x dotnet-hello`. Następnie można utworzyć łącze symboliczne do niej w `/usr/local/bin` za pomocą polecenia `ln -s <full_path>/dotnet-hello /usr/local/bin/`. To umożliwi można wywołać za pomocą polecenia `dotnet hello` składni.

W systemie Windows, można zapisać ten skrypt jako `dotnet-hello.cmd` i umieszcza je w lokalizacji, która znajduje się w ścieżce systemowej (lub można dodać go do folderu, który już znajduje się w ścieżce). Następnie można użyć `dotnet hello` do uruchomienia tego przykładu.
