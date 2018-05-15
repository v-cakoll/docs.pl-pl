---
title: Modelu rozszerzalności .NET core interfejsu wiersza polecenia
description: Dowiedz się, jak można rozszerzyć narzędzi interfejsu wiersza polecenia (CLI).
author: blackdwarf
ms.author: mairaw
ms.date: 04/12/2017
ms.openlocfilehash: 6cabd3959a29878788916ae26589be408c12e0ca
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="net-core-cli-tools-extensibility-model"></a><span data-ttu-id="c7661-103">Modelu rozszerzalności narzędzi interfejsu wiersza polecenia platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="c7661-103">.NET Core CLI tools extensibility model</span></span>

<span data-ttu-id="c7661-104">W tym dokumencie opisano różne sposoby, można rozszerzyć narzędzia .NET Core interfejsu wiersza polecenia (CLI) i opisano scenariusze, które dysków w każdej z nich z nich.</span><span class="sxs-lookup"><span data-stu-id="c7661-104">This document covers the different ways you can extend the .NET Core Command-line Interface (CLI) tools and explain the scenarios that drive each one of them.</span></span>
<span data-ttu-id="c7661-105">Zobaczysz, jak korzystać z narzędzia, a także sposób tworzenia różnych typów narzędzi.</span><span class="sxs-lookup"><span data-stu-id="c7661-105">You'll see how to consume the tools as well as how to build the different types of tools.</span></span>

## <a name="how-to-extend-cli-tools"></a><span data-ttu-id="c7661-106">Jak rozszerzyć narzędzi interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="c7661-106">How to extend CLI tools</span></span>
<span data-ttu-id="c7661-107">Narzędzi interfejsu wiersza polecenia można ją rozszerzyć, przede wszystkim na trzy sposoby:</span><span class="sxs-lookup"><span data-stu-id="c7661-107">The CLI tools can be extended in three main ways:</span></span>

1. [<span data-ttu-id="c7661-108">Za pomocą pakietów NuGet dla projektu</span><span class="sxs-lookup"><span data-stu-id="c7661-108">Via NuGet packages on a per-project basis</span></span>](#per-project-based-extensibility)

   <span data-ttu-id="c7661-109">-Projekt narzędzia są dostępne w kontekście projektu, ale pozwalają łatwo instalacji przez Przywracanie.</span><span class="sxs-lookup"><span data-stu-id="c7661-109">Per-project tools are contained within the project's context, but they allow easy installation through restoration.</span></span>

2. [<span data-ttu-id="c7661-110">Za pomocą pakietów NuGet z niestandardowych elementów docelowych</span><span class="sxs-lookup"><span data-stu-id="c7661-110">Via NuGet packages with custom targets</span></span>](#custom-targets)

   <span data-ttu-id="c7661-111">Niestandardowe elementy docelowe pozwalają łatwo rozszerzyć proces kompilacji z niestandardowych zadań.</span><span class="sxs-lookup"><span data-stu-id="c7661-111">Custom targets allow you to easily extend the build process with custom tasks.</span></span>

3. [<span data-ttu-id="c7661-112">Za pomocą ścieżki systemu</span><span class="sxs-lookup"><span data-stu-id="c7661-112">Via the system's PATH</span></span>](#path-based-extensibility)

   <span data-ttu-id="c7661-113">Narzędzia oparte na ŚCIEŻCE są odpowiednie w ogólne, między projektami narzędzia, której można używać na jednym komputerze.</span><span class="sxs-lookup"><span data-stu-id="c7661-113">PATH-based tools are good for general, cross-project tools that are usable on a single machine.</span></span>

<span data-ttu-id="c7661-114">Trzy mechanizmy rozszerzania opisanych powyżej nie są wyłączne.</span><span class="sxs-lookup"><span data-stu-id="c7661-114">The three extensibility mechanisms outlined above are not exclusive.</span></span> <span data-ttu-id="c7661-115">Można użyć jednego lub wszystkich, lub ich kombinacji.</span><span class="sxs-lookup"><span data-stu-id="c7661-115">You can use one, or all, or a combination of them.</span></span> <span data-ttu-id="c7661-116">Która z nich do pobrania zależy przede wszystkim od cel, który chcesz osiągnąć z rozszerzeniem.</span><span class="sxs-lookup"><span data-stu-id="c7661-116">Which one to pick depends largely on the goal you are trying to achieve with your extension.</span></span>

## <a name="per-project-based-extensibility"></a><span data-ttu-id="c7661-117">Na podstawie rozszerzalność projektu</span><span class="sxs-lookup"><span data-stu-id="c7661-117">Per-project based extensibility</span></span>
<span data-ttu-id="c7661-118">Narzędzia dla projektu są [wdrożeń zależne od framework](../deploying/index.md#framework-dependent-deployments-fdd) dystrybuowanych jako pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="c7661-118">Per-project tools are [framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) that are distributed as NuGet packages.</span></span> <span data-ttu-id="c7661-119">Narzędzia są dostępne tylko w kontekście projektu, który odwołuje się do nich i dla których zostaną przywrócone.</span><span class="sxs-lookup"><span data-stu-id="c7661-119">Tools are only available in the context of the project that references them and for which they are restored.</span></span> <span data-ttu-id="c7661-120">Wywołanie poza kontekstem projektu (na przykład spoza katalogu, który zawiera projekt) zakończy się niepowodzeniem, ponieważ nie można odnaleźć polecenia.</span><span class="sxs-lookup"><span data-stu-id="c7661-120">Invocation outside of the context of the project (for example, outside of the directory that contains the project) will fail because the command cannot be found.</span></span>

<span data-ttu-id="c7661-121">Te narzędzia są idealne w przypadku serwerów kompilacji, ponieważ nic poza pliku projektu jest potrzebny.</span><span class="sxs-lookup"><span data-stu-id="c7661-121">These tools are perfect for build servers, since nothing outside of the project file is needed.</span></span> <span data-ttu-id="c7661-122">Uruchamia proces kompilacji projektu go przywrócić kompilacji i narzędzi będzie dostępna.</span><span class="sxs-lookup"><span data-stu-id="c7661-122">The build process runs restore for the project it builds and tools will be available.</span></span> <span data-ttu-id="c7661-123">Projekty języka, takie jak F # są również w tej kategorii, ponieważ każdego projektu można zapisywać tylko w jednym języku określonych.</span><span class="sxs-lookup"><span data-stu-id="c7661-123">Language projects, such as F#, are also in this category since each project can only be written in one specific language.</span></span>

<span data-ttu-id="c7661-124">Na koniec tego modelu rozszerzalności zapewnia obsługę tworzenia narzędzi, które wymagają dostępu do skompilowanych danych wyjściowych projektu.</span><span class="sxs-lookup"><span data-stu-id="c7661-124">Finally, this extensibility model provides support for creation of tools that need access to the built output of the project.</span></span> <span data-ttu-id="c7661-125">Na przykład widoku Razor różnych narzędzi w [ASP.NET](https://www.asp.net/) aplikacji MVC należą do tej kategorii.</span><span class="sxs-lookup"><span data-stu-id="c7661-125">For instance, various Razor view tools in [ASP.NET](https://www.asp.net/) MVC applications fall into this category.</span></span>

### <a name="consuming-per-project-tools"></a><span data-ttu-id="c7661-126">Korzystanie z narzędzia — projekt</span><span class="sxs-lookup"><span data-stu-id="c7661-126">Consuming per-project tools</span></span>
<span data-ttu-id="c7661-127">Korzystanie z tych narzędzi, musisz dodać `<DotNetCliToolReference>` elementu do pliku projektu dla każdego narzędzia, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="c7661-127">Consuming these tools requires you to add a `<DotNetCliToolReference>` element to your project file for each tool you want to use.</span></span> <span data-ttu-id="c7661-128">Wewnątrz `<DotNetCliToolReference>` element, należy odwołują się do pakietu, w której znajduje się narzędzie i określ wersję należy.</span><span class="sxs-lookup"><span data-stu-id="c7661-128">Inside the `<DotNetCliToolReference>` element, you reference the package in which the tool resides and specify the version you need.</span></span> <span data-ttu-id="c7661-129">Po uruchomieniu [ `dotnet restore` ](dotnet-restore.md), narzędzia i jego zależności są przywracane.</span><span class="sxs-lookup"><span data-stu-id="c7661-129">After running [`dotnet restore`](dotnet-restore.md), the tool and its dependencies are restored.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="c7661-130">Narzędzia, które należy załadować danych wyjściowych kompilacji projektu do wykonania jest zazwyczaj innego zależności, która jest wyświetlana w obszarze regularne zależności w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c7661-130">For tools that need to load the build output of the project for execution, there is usually another dependency which is listed under the regular dependencies in the project file.</span></span> <span data-ttu-id="c7661-131">Ponieważ interfejsu wiersza polecenia używa MSBuild jako jego aparatu kompilacji, zaleca się te części narzędzie mieć postać MSBuild niestandardowych [elementy docelowe](/visualstudio/msbuild/msbuild-targets) i [zadania](/visualstudio/msbuild/msbuild-tasks), ponieważ ich mogą następnie skorzystać całego procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c7661-131">Since CLI uses MSBuild as its build engine, we recommend that these parts of the tool be written as custom MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and [tasks](/visualstudio/msbuild/msbuild-tasks), since they can then take part in the overall build process.</span></span> <span data-ttu-id="c7661-132">Ponadto może uzyskać wszystkie dane, łatwo utworzonym za pomocą kompilacji, takie jak lokalizacja plików wyjściowych bieżącej konfiguracji konstruowany itp. Wszystkie te informacje będą zbiór właściwości programu MSBuild, które mogą być odczytywane z dowolnego miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="c7661-132">Also, they can get any and all data easily that is produced via the build, such as the location of the output files, the current configuration being built, etc. All this information becomes a set of MSBuild properties that can be read from any target.</span></span> <span data-ttu-id="c7661-133">Jak dodać element docelowy niestandardowych przy użyciu narzędzia NuGet w dalszej części tego dokumentu jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="c7661-133">You can see how to add a custom target using NuGet later in this document.</span></span>

<span data-ttu-id="c7661-134">Umożliwia przeglądanie przykład dodawania prostego narzędzia tylko narzędzia do prostego projektu.</span><span class="sxs-lookup"><span data-stu-id="c7661-134">Let's review an example of adding a simple tools-only tool to a simple project.</span></span> <span data-ttu-id="c7661-135">Podano przykładowe polecenie o nazwie `dotnet-api-search` umożliwiają wyszukiwanie za pomocą pakietów NuGet dla określonego interfejsu API, w tym miejscu to pliku projektu aplikacji konsoli, która używa tego narzędzia:</span><span class="sxs-lookup"><span data-stu-id="c7661-135">Given an example command called `dotnet-api-search` that allows you to search through the NuGet packages for the specified API, here is a console application's project file that uses that tool:</span></span>

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

<span data-ttu-id="c7661-136">`<DotNetCliToolReference>` Elementów ma strukturę w podobny sposób jak `<PackageReference>` elementu.</span><span class="sxs-lookup"><span data-stu-id="c7661-136">The `<DotNetCliToolReference>` element is structured in a similar way as the `<PackageReference>` element.</span></span> <span data-ttu-id="c7661-137">Musi on identyfikator pakietu pakietu zawierającego narzędzie oraz jego wersję, można go przywrócić.</span><span class="sxs-lookup"><span data-stu-id="c7661-137">It needs the package ID of the package containing the tool and its version to be able to restore.</span></span>

### <a name="building-tools"></a><span data-ttu-id="c7661-138">Narzędzia do budowania</span><span class="sxs-lookup"><span data-stu-id="c7661-138">Building tools</span></span>
<span data-ttu-id="c7661-139">Jak wspomniano, narzędzia są aplikacje konsoli po prostu przenośnej.</span><span class="sxs-lookup"><span data-stu-id="c7661-139">As mentioned, tools are just portable console applications.</span></span> <span data-ttu-id="c7661-140">Narzędzi kompilacji, podczas tworzenia czy inna aplikacja konsoli.</span><span class="sxs-lookup"><span data-stu-id="c7661-140">You build tools as you would build any other console application.</span></span>
<span data-ttu-id="c7661-141">Po jego tworzenia, należy użyć [ `dotnet pack` ](dotnet-pack.md) polecenie, aby utworzyć pakiet NuGet (pliku .nupkg), który zawiera kod, informacje o jego zależności itd.</span><span class="sxs-lookup"><span data-stu-id="c7661-141">After you build it, you use the [`dotnet pack`](dotnet-pack.md) command to create a NuGet package (.nupkg file) that contains your code, information about its dependencies, and so on.</span></span> <span data-ttu-id="c7661-142">Można przekazać dowolną nazwę pakietu, ale aplikacja wewnątrz narzędzie rzeczywiste binarnego, musi być zgodne z Konwencją `dotnet-<command>` aby `dotnet` aby można było ją wywołać.</span><span class="sxs-lookup"><span data-stu-id="c7661-142">You can give any name to the package, but the application inside, the actual tool binary, has to conform to the convention of `dotnet-<command>` in order for `dotnet` to be able to invoke it.</span></span>

> [!NOTE]
> <span data-ttu-id="c7661-143">W wersji pre-RC3 narzędzi wiersza polecenia platformy .NET Core `dotnet pack` polecenia miał usterkę, która spowodowała `runtime.config.json` nie pakowane za pomocą narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c7661-143">In pre-RC3 versions of the .NET Core command-line tools, the `dotnet pack` command had a bug that caused the `runtime.config.json` to not be packed with the tool.</span></span> <span data-ttu-id="c7661-144">Brak wyników tego pliku błędy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c7661-144">Lacking that file results in errors at runtime.</span></span> <span data-ttu-id="c7661-145">Jeśli wystąpi ten problem, należy zaktualizować najnowsze narzędzia i spróbuj `dotnet pack` ponownie.</span><span class="sxs-lookup"><span data-stu-id="c7661-145">If you encounter this behavior, be sure to update to the latest tooling and try the `dotnet pack` again.</span></span>

<span data-ttu-id="c7661-146">Ponieważ narzędzia przenośnych aplikacji, użytkowników korzystających z narzędzia musi mieć wersję biblioteki .NET Core, w których narzędzie został utworzony przed uruchomienie tego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="c7661-146">Since tools are portable applications, the user consuming the tool must have the version of the .NET Core libraries that the tool was built against in order to run the tool.</span></span> <span data-ttu-id="c7661-147">Inne zależności, czy używane narzędzie i który nie jest zawarty w bibliotek .NET Core jest przywrócona i umieszczane w pamięci podręcznej NuGet.</span><span class="sxs-lookup"><span data-stu-id="c7661-147">Any other dependency that the tool uses and that is not contained within the .NET Core libraries is restored and placed in the NuGet cache.</span></span> <span data-ttu-id="c7661-148">Cały dlatego uruchomienie narzędzia przy użyciu zestawów z bibliotek .NET Core, a także zestawy z pamięci podręcznej NuGet.</span><span class="sxs-lookup"><span data-stu-id="c7661-148">The entire tool is, therefore, run using the assemblies from the .NET Core libraries as well as assemblies from the NuGet cache.</span></span>

<span data-ttu-id="c7661-149">Tego rodzaju narzędzia ma wykres zależności, który jest całkowicie niezależna od na wykresie zależności projektu, który używa tych.</span><span class="sxs-lookup"><span data-stu-id="c7661-149">These kinds of tools have a dependency graph that is completely separate from the dependency graph of the project that uses them.</span></span> <span data-ttu-id="c7661-150">Proces przywracania najpierw przywraca zależności projektu i następnie przywrócenie wszystkich narzędzi oraz ich zależności.</span><span class="sxs-lookup"><span data-stu-id="c7661-150">The restore process first restores the project's dependencies and then restores each of the tools and their dependencies.</span></span>

<span data-ttu-id="c7661-151">Można znaleźć przykłady bardziej zaawansowane funkcje i to w różnych kombinacji [repozytorium interfejsu wiersza polecenia platformy .NET Core](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).</span><span class="sxs-lookup"><span data-stu-id="c7661-151">You can find richer examples and different combinations of this in the [.NET Core CLI repo](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).</span></span>
<span data-ttu-id="c7661-152">Możesz również sprawdzić [implementacji narzędzia używane](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) w tym samym repozytorium.</span><span class="sxs-lookup"><span data-stu-id="c7661-152">You can also see the [implementation of tools used](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) in the same repo.</span></span>

### <a name="custom-targets"></a><span data-ttu-id="c7661-153">Niestandardowe elementy docelowe</span><span class="sxs-lookup"><span data-stu-id="c7661-153">Custom targets</span></span>
<span data-ttu-id="c7661-154">NuGet ma możliwość [pakiet niestandardowy MSBuild cele i pliki właściwości](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package).</span><span class="sxs-lookup"><span data-stu-id="c7661-154">NuGet has the capability to [package custom MSBuild targets and props files](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package).</span></span> <span data-ttu-id="c7661-155">Wraz z przejściem z narzędzi .NET Core interfejsu wiersza polecenia, użyj programu MSBuild sam mechanizm rozszerzalności teraz ma zastosowanie do projektów platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c7661-155">With the move of the .NET Core CLI tools to use MSBuild, the same mechanism of extensibility now applies to .NET Core projects.</span></span> <span data-ttu-id="c7661-156">Czy używać tego typu rozszerzeń, gdy chcesz rozszerzyć procesu kompilacji lub chcesz uzyskać dostępu do żadnego artefaktów w procesie kompilacji, takich jak pliki generowane lub chcesz sprawdzić konfigurację, pod którą jest wywoływany kompilacji , itp.</span><span class="sxs-lookup"><span data-stu-id="c7661-156">You would use this type of extensibility when you want to extend the build process, or when you want to access any of the artifacts in the build process, such as generated files, or you want to inspect the configuration under which the build is invoked, etc.</span></span>

<span data-ttu-id="c7661-157">W poniższym przykładzie widać projektu docelowego pliku przy użyciu `csproj` składni.</span><span class="sxs-lookup"><span data-stu-id="c7661-157">In the following example, you can see the target's project file using the `csproj` syntax.</span></span> <span data-ttu-id="c7661-158">To powoduje, że [ `dotnet pack` ](dotnet-pack.md) polecenia wybierania elementów do pakietu, umieszczenie plików elementy docelowe, a także zestawów do *kompilacji* folderu w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="c7661-158">This instructs the [`dotnet pack`](dotnet-pack.md) command what to package, placing the targets files as well as the assemblies into the *build* folder inside the package.</span></span> <span data-ttu-id="c7661-159">Powiadomienie `<ItemGroup>` element, który ma `Label` ustawioną właściwość `dotnet pack instructions`, i element docelowy zdefiniowana poniżej.</span><span class="sxs-lookup"><span data-stu-id="c7661-159">Notice the `<ItemGroup>` element that has the `Label` property set to `dotnet pack instructions`, and the Target defined beneath it.</span></span>

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

<span data-ttu-id="c7661-160">Korzystanie z niestandardowych elementów docelowych to zrobić, podając `<PackageReference>` wskazującego pakiet i jego wersja wewnątrz projektu, który zostanie rozszerzone.</span><span class="sxs-lookup"><span data-stu-id="c7661-160">Consuming custom targets is done by providing a `<PackageReference>` that points to the package and its version inside the project that is being extended.</span></span> <span data-ttu-id="c7661-161">W przeciwieństwie do narzędzia ujęte pakietu niestandardowe obiekty docelowe do zamknięcia zależności projektu odbierającą.</span><span class="sxs-lookup"><span data-stu-id="c7661-161">Unlike the tools, the custom targets package does get included into the consuming project's dependency closure.</span></span>

<span data-ttu-id="c7661-162">Przy użyciu niestandardowych docelowych zależy od wyłącznie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c7661-162">Using the custom target depends solely on how you configure it.</span></span> <span data-ttu-id="c7661-163">Ponieważ jest element docelowy programu MSBuild, może zależeć na dany obiekt docelowy, uruchom po inny element docelowy i może również być ręcznie wywoływane przy użyciu `dotnet msbuild /t:<target-name>` polecenia.</span><span class="sxs-lookup"><span data-stu-id="c7661-163">Since it's an MSBuild target, it can depend on a given target, run after another target and can also be manually invoked using the `dotnet msbuild /t:<target-name>` command.</span></span>

<span data-ttu-id="c7661-164">Jednak jeśli chcesz zapewnić lepsze środowisko dla użytkowników, możesz łączyć narzędzia na projekt i niestandardowych obiektów docelowych.</span><span class="sxs-lookup"><span data-stu-id="c7661-164">However, if you want to provide a better user experience to your users, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="c7661-165">W tym scenariuszu narzędzie-projekt będzie zasadniczo wystarczy zaakceptować wymagane parametry i przekłada który do wymaganych [ `dotnet msbuild` ](dotnet-msbuild.md) wywołanie, którego elementem docelowym jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="c7661-165">In this scenario, the per-project tool would essentially just accept whatever needed parameters and would translate that into the required [`dotnet msbuild`](dotnet-msbuild.md) invocation that would execute the target.</span></span> <span data-ttu-id="c7661-166">Można wyświetlić na przykład tego rodzaju współdziałania [przykłady MVP szczytu 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) repozytorium w [ `dotnet-packer` ](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) projektu.</span><span class="sxs-lookup"><span data-stu-id="c7661-166">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

### <a name="path-based-extensibility"></a><span data-ttu-id="c7661-167">Na podstawie ścieżki rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="c7661-167">PATH-based extensibility</span></span>
<span data-ttu-id="c7661-168">Rozszerzalność na podstawie ścieżki jest zazwyczaj używane do tworzenia maszyn wymagających narzędziem koncepcyjnie obejmuje więcej niż jednego projektu.</span><span class="sxs-lookup"><span data-stu-id="c7661-168">PATH-based extensibility is usually used for development machines where you need a tool that conceptually covers more than a single project.</span></span> <span data-ttu-id="c7661-169">Główną wadą tego mechanizmu rozszerzenia jest, że zostały powiązane z maszyną gdzie narzędzie istnieje.</span><span class="sxs-lookup"><span data-stu-id="c7661-169">The main drawback of this extension mechanism is that it's tied to the machine where the tool exists.</span></span> <span data-ttu-id="c7661-170">Jeśli potrzebujesz go na innym komputerze, trzeba jej wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="c7661-170">If you need it on another machine, you would have to deploy it.</span></span>

<span data-ttu-id="c7661-171">Ten wzorzec rozszerzalność narzędzi interfejsu wiersza polecenia jest bardzo prosty.</span><span class="sxs-lookup"><span data-stu-id="c7661-171">This pattern of CLI toolset extensibility is very simple.</span></span> <span data-ttu-id="c7661-172">Jak opisano w [omówienie interfejsu wiersza polecenia platformy .NET Core](index.md), `dotnet` sterownik można uruchomić z dowolnego polecenia o nazwie po `dotnet-<command>` Konwencji.</span><span class="sxs-lookup"><span data-stu-id="c7661-172">As covered in the [.NET Core CLI overview](index.md), `dotnet` driver can run any command that is named after the `dotnet-<command>` convention.</span></span> <span data-ttu-id="c7661-173">Domyślna logika rozpoznawania najpierw sondy w kilku lokalizacjach, a na koniec przechodzi do systemowej PATH.</span><span class="sxs-lookup"><span data-stu-id="c7661-173">The default resolution logic first probes several locations and finally falls back to the system PATH.</span></span> <span data-ttu-id="c7661-174">Jeśli żądanego polecenia w systemie ŚCIEŻKA istnieje i jest plikiem binarnym, która może zostać wywołana, `dotnet` sterownik wywoła go.</span><span class="sxs-lookup"><span data-stu-id="c7661-174">If the requested command exists in the system PATH and is a binary that can be invoked, `dotnet` driver will invoke it.</span></span>

<span data-ttu-id="c7661-175">Plik musi być wykonywalne.</span><span class="sxs-lookup"><span data-stu-id="c7661-175">The file must be executable.</span></span> <span data-ttu-id="c7661-176">W systemach Unix, oznacza to wszystko, co ma ustawiony bit execute za pośrednictwem `chmod +x`.</span><span class="sxs-lookup"><span data-stu-id="c7661-176">On Unix systems, this means anything that has the execute bit set via `chmod +x`.</span></span> <span data-ttu-id="c7661-177">W systemie Windows, można użyć *cmd* plików.</span><span class="sxs-lookup"><span data-stu-id="c7661-177">On Windows, you can use *cmd* files.</span></span>

<span data-ttu-id="c7661-178">Spójrzmy na bardzo prosta implementacja narzędzia "Hello World".</span><span class="sxs-lookup"><span data-stu-id="c7661-178">Let's take a look at the very simple implementation of a "Hello World" tool.</span></span> <span data-ttu-id="c7661-179">Używamy zarówno `bash` i `cmd` w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="c7661-179">We will use both `bash` and `cmd` on Windows.</span></span>
<span data-ttu-id="c7661-180">Następujące polecenie spowoduje po prostu echo "Hello World" w konsoli.</span><span class="sxs-lookup"><span data-stu-id="c7661-180">The following command will simply echo "Hello World" to the console.</span></span>

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

<span data-ttu-id="c7661-181">Na macOS, można zapisać ten skrypt jako `dotnet-hello` i ustawić jej bit pliku wykonywalnego z `chmod +x dotnet-hello`.</span><span class="sxs-lookup"><span data-stu-id="c7661-181">On macOS, we can save this script as `dotnet-hello` and set its executable bit with `chmod +x dotnet-hello`.</span></span> <span data-ttu-id="c7661-182">Następnie można utworzyć łącze symboliczne do niej w `/usr/local/bin` za pomocą polecenia `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span><span class="sxs-lookup"><span data-stu-id="c7661-182">We can then create a symbolic link to it in `/usr/local/bin` using the command `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span></span> <span data-ttu-id="c7661-183">To umożliwi można wywołać za pomocą polecenia `dotnet hello` składni.</span><span class="sxs-lookup"><span data-stu-id="c7661-183">This will make it possible to invoke the command using the `dotnet hello` syntax.</span></span>

<span data-ttu-id="c7661-184">W systemie Windows, można zapisać ten skrypt jako `dotnet-hello.cmd` i umieszcza je w lokalizacji, która znajduje się w ścieżce systemowej (lub można dodać go do folderu, który już znajduje się w ścieżce).</span><span class="sxs-lookup"><span data-stu-id="c7661-184">On Windows, we can save this script as `dotnet-hello.cmd` and put it in a location that is in a system path (or you can add it to a folder that is already in the path).</span></span> <span data-ttu-id="c7661-185">Następnie można użyć `dotnet hello` do uruchomienia tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="c7661-185">After this, you can just use `dotnet hello` to run this example.</span></span>
