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
# <a name="net-core-cli-tools-extensibility-model"></a><span data-ttu-id="31d26-103">Model rozszerzalności narzędzi interfejsu wiersza polecenia platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="31d26-103">.NET Core CLI tools extensibility model</span></span>

<span data-ttu-id="31d26-104">W tym dokumencie opisano różne sposoby, można rozszerzyć narzędzia .NET Core interfejsu wiersza polecenia (CLI) i opisano scenariusze, które dysków z każdej z nich z nich.</span><span class="sxs-lookup"><span data-stu-id="31d26-104">This document covers the different ways you can extend the .NET Core Command-line Interface (CLI) tools and explain the scenarios that drive each one of them.</span></span>
<span data-ttu-id="31d26-105">Zobaczysz, jak używać narzędzi, a także jak tworzyć różne typy narzędzi.</span><span class="sxs-lookup"><span data-stu-id="31d26-105">You'll see how to consume the tools as well as how to build the different types of tools.</span></span>

## <a name="how-to-extend-cli-tools"></a><span data-ttu-id="31d26-106">Jak rozszerzyć narzędzi interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="31d26-106">How to extend CLI tools</span></span>
<span data-ttu-id="31d26-107">Narzędzia interfejsu wiersza polecenia można rozszerzyć na trzy sposoby:</span><span class="sxs-lookup"><span data-stu-id="31d26-107">The CLI tools can be extended in three main ways:</span></span>

1. [<span data-ttu-id="31d26-108">Za pomocą pakietów NuGet w poszczególnych projektów</span><span class="sxs-lookup"><span data-stu-id="31d26-108">Via NuGet packages on a per-project basis</span></span>](#per-project-based-extensibility)

   <span data-ttu-id="31d26-109">Narzędzia dla projektu są zawarte w kontekście projektu, ale pozwalają łatwej instalacji przy użyciu przywracania.</span><span class="sxs-lookup"><span data-stu-id="31d26-109">Per-project tools are contained within the project's context, but they allow easy installation through restoration.</span></span>

2. [<span data-ttu-id="31d26-110">Za pomocą pakietów NuGet z niestandardowych elementów docelowych</span><span class="sxs-lookup"><span data-stu-id="31d26-110">Via NuGet packages with custom targets</span></span>](#custom-targets)

   <span data-ttu-id="31d26-111">Niestandardowe obiekty docelowe pozwalają w prosty sposób rozszerzyć proces kompilacji przy użyciu niestandardowych zadań.</span><span class="sxs-lookup"><span data-stu-id="31d26-111">Custom targets allow you to easily extend the build process with custom tasks.</span></span>

3. [<span data-ttu-id="31d26-112">Za pomocą ścieżki systemowej</span><span class="sxs-lookup"><span data-stu-id="31d26-112">Via the system's PATH</span></span>](#path-based-extensibility)

   <span data-ttu-id="31d26-113">Narzędzia oparte na ŚCIEŻCE dla zastosowań dobre są ogólne, między projektami narzędzia, które można używać na jednym komputerze.</span><span class="sxs-lookup"><span data-stu-id="31d26-113">PATH-based tools are good for general, cross-project tools that are usable on a single machine.</span></span>

<span data-ttu-id="31d26-114">Trzy mechanizmy rozszerzania opisanych powyżej, nie są wyłączne.</span><span class="sxs-lookup"><span data-stu-id="31d26-114">The three extensibility mechanisms outlined above are not exclusive.</span></span> <span data-ttu-id="31d26-115">Można użyć jednego lub wszystkich, lub ich kombinacji.</span><span class="sxs-lookup"><span data-stu-id="31d26-115">You can use one, or all, or a combination of them.</span></span> <span data-ttu-id="31d26-116">Który z nich do wybrania zależy od większości cel, który próbujesz osiągnąć za pomocą rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="31d26-116">Which one to pick depends largely on the goal you are trying to achieve with your extension.</span></span>

## <a name="per-project-based-extensibility"></a><span data-ttu-id="31d26-117">Na podstawie rozszerzalność projektu</span><span class="sxs-lookup"><span data-stu-id="31d26-117">Per-project based extensibility</span></span>
<span data-ttu-id="31d26-118">Narzędzia dla projektu są [wdrożeń zależny od struktury](../deploying/index.md#framework-dependent-deployments-fdd) dystrybuowanych jako pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="31d26-118">Per-project tools are [framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) that are distributed as NuGet packages.</span></span> <span data-ttu-id="31d26-119">Narzędzia są dostępne tylko w kontekście projektu, który odwołuje się do nich i dla których zostaną przywrócone.</span><span class="sxs-lookup"><span data-stu-id="31d26-119">Tools are only available in the context of the project that references them and for which they are restored.</span></span> <span data-ttu-id="31d26-120">Wywołanie poza kontekstem projektu (na przykład spoza katalogu, który zawiera projekt) zakończy się niepowodzeniem, ponieważ nie można odnaleźć polecenia.</span><span class="sxs-lookup"><span data-stu-id="31d26-120">Invocation outside of the context of the project (for example, outside of the directory that contains the project) will fail because the command cannot be found.</span></span>

<span data-ttu-id="31d26-121">Te narzędzia są doskonałe dla serwerów kompilacji, ponieważ nic nie poza plik projektu jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="31d26-121">These tools are perfect for build servers, since nothing outside of the project file is needed.</span></span> <span data-ttu-id="31d26-122">Uruchamia proces kompilacji dla projektu go przywrócić kompilacje i narzędzia będą dostępne.</span><span class="sxs-lookup"><span data-stu-id="31d26-122">The build process runs restore for the project it builds and tools will be available.</span></span> <span data-ttu-id="31d26-123">Projekty języka, takie jak F # są również w tej kategorii, ponieważ każdy projekt może być zapisany tylko w jednym języku określonych.</span><span class="sxs-lookup"><span data-stu-id="31d26-123">Language projects, such as F#, are also in this category since each project can only be written in one specific language.</span></span>

<span data-ttu-id="31d26-124">Na koniec tego modelu rozszerzalności zapewnia obsługę tworzenia narzędzi, które muszą mieć dostęp do skompilowanych danych wyjściowych projektu.</span><span class="sxs-lookup"><span data-stu-id="31d26-124">Finally, this extensibility model provides support for creation of tools that need access to the built output of the project.</span></span> <span data-ttu-id="31d26-125">Na przykład widoku Razor dla różnych narzędzi w [ASP.NET](https://www.asp.net/) aplikacji MVC należą do tej kategorii.</span><span class="sxs-lookup"><span data-stu-id="31d26-125">For instance, various Razor view tools in [ASP.NET](https://www.asp.net/) MVC applications fall into this category.</span></span>

### <a name="consuming-per-project-tools"></a><span data-ttu-id="31d26-126">Korzystanie z narzędzi dla projektów</span><span class="sxs-lookup"><span data-stu-id="31d26-126">Consuming per-project tools</span></span>
<span data-ttu-id="31d26-127">Korzystanie z tych narzędzi, musisz dodać `<DotNetCliToolReference>` element do pliku projektu dla każdego narzędzia, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="31d26-127">Consuming these tools requires you to add a `<DotNetCliToolReference>` element to your project file for each tool you want to use.</span></span> <span data-ttu-id="31d26-128">Wewnątrz `<DotNetCliToolReference>` elementu, należy odwołują się do pakietu, w której znajduje się narzędzie i określić wersji, potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="31d26-128">Inside the `<DotNetCliToolReference>` element, you reference the package in which the tool resides and specify the version you need.</span></span> <span data-ttu-id="31d26-129">Po uruchomieniu [ `dotnet restore` ](dotnet-restore.md), narzędzie i jego zależności zostaną przywrócone.</span><span class="sxs-lookup"><span data-stu-id="31d26-129">After running [`dotnet restore`](dotnet-restore.md), the tool and its dependencies are restored.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="31d26-130">Narzędzia, które należy załadować dane wyjściowe kompilacji projektu do wykonania jest zazwyczaj inny współzależność, która znajduje się w obszarze regularne zależności w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="31d26-130">For tools that need to load the build output of the project for execution, there is usually another dependency which is listed under the regular dependencies in the project file.</span></span> <span data-ttu-id="31d26-131">Ponieważ interfejs wiersza polecenia używa programu MSBuild jako jego aparatu kompilacji, zaleca się zapisać te elementy narzędzia w postaci niestandardowych MSBuild [cele](/visualstudio/msbuild/msbuild-targets) i [zadania](/visualstudio/msbuild/msbuild-tasks), ponieważ są one następnie wzięcia udziału w całego procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="31d26-131">Since CLI uses MSBuild as its build engine, we recommend that these parts of the tool be written as custom MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and [tasks](/visualstudio/msbuild/msbuild-tasks), since they can then take part in the overall build process.</span></span> <span data-ttu-id="31d26-132">Ponadto otrzymują wszystkie dane, łatwo utworzonym za pomocą kompilacji, takie jak lokalizacja plików wyjściowych bieżącej konfiguracji kompilowanego na bieżąco, itd. Wszystkie te informacje będą zbiór właściwości programu MSBuild, które mogą być odczytywane z dowolnej docelowej.</span><span class="sxs-lookup"><span data-stu-id="31d26-132">Also, they can get any and all data easily that is produced via the build, such as the location of the output files, the current configuration being built, etc. All this information becomes a set of MSBuild properties that can be read from any target.</span></span> <span data-ttu-id="31d26-133">Możesz dowiedzieć się, jak dodać niestandardowe obiekty docelowe, za pomocą narzędzia NuGet w dalszej części tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="31d26-133">You can see how to add a custom target using NuGet later in this document.</span></span>

<span data-ttu-id="31d26-134">Omówmy teraz przykład dodawania proste narzędzie tylko do narzędzia do prostego projektu.</span><span class="sxs-lookup"><span data-stu-id="31d26-134">Let's review an example of adding a simple tools-only tool to a simple project.</span></span> <span data-ttu-id="31d26-135">Biorąc pod uwagę przykładowe polecenie o nazwie `dotnet-api-search` dzięki niemu można będzie przeszukiwać pakietów NuGet dla określonego interfejsu API, w tym miejscu jest plik projektu aplikacji konsoli, który korzysta z tego narzędzia:</span><span class="sxs-lookup"><span data-stu-id="31d26-135">Given an example command called `dotnet-api-search` that allows you to search through the NuGet packages for the specified API, here is a console application's project file that uses that tool:</span></span>

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

<span data-ttu-id="31d26-136">`<DotNetCliToolReference>` Elementu są skonstruowane w podobny sposób jak `<PackageReference>` elementu.</span><span class="sxs-lookup"><span data-stu-id="31d26-136">The `<DotNetCliToolReference>` element is structured in a similar way as the `<PackageReference>` element.</span></span> <span data-ttu-id="31d26-137">Musi ona identyfikator pakietu pakiet zawierający narzędzia i jego wersji, można przywrócić.</span><span class="sxs-lookup"><span data-stu-id="31d26-137">It needs the package ID of the package containing the tool and its version to be able to restore.</span></span>

### <a name="building-tools"></a><span data-ttu-id="31d26-138">Narzędzia do konstruowania</span><span class="sxs-lookup"><span data-stu-id="31d26-138">Building tools</span></span>
<span data-ttu-id="31d26-139">Jak wspomniano, narzędzia są aplikacje konsoli po prostu przenośnej.</span><span class="sxs-lookup"><span data-stu-id="31d26-139">As mentioned, tools are just portable console applications.</span></span> <span data-ttu-id="31d26-140">Możesz tworzyć narzędzi, jak tworzysz czy inna aplikacja konsoli.</span><span class="sxs-lookup"><span data-stu-id="31d26-140">You build tools as you would build any other console application.</span></span>
<span data-ttu-id="31d26-141">Po jego tworzenia, należy użyć [ `dotnet pack` ](dotnet-pack.md) polecenie, aby utworzyć pakiet NuGet (plik .nupkg), który zawiera kod, informacje o jego zależności i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="31d26-141">After you build it, you use the [`dotnet pack`](dotnet-pack.md) command to create a NuGet package (.nupkg file) that contains your code, information about its dependencies, and so on.</span></span> <span data-ttu-id="31d26-142">Można nadać dowolną nazwę pakietu, ale aplikacji w narzędziu rzeczywiste binarne, musi być zgodna z Konwencją `dotnet-<command>` aby `dotnet` aby można było ją wywołać.</span><span class="sxs-lookup"><span data-stu-id="31d26-142">You can give any name to the package, but the application inside, the actual tool binary, has to conform to the convention of `dotnet-<command>` in order for `dotnet` to be able to invoke it.</span></span>

> [!NOTE]
> <span data-ttu-id="31d26-143">W wersji pre-RC3 narzędzia wiersza polecenia platformy .NET Core `dotnet pack` polecenia miał usterkę powodującą `runtime.config.json` nie będzie bogatymi w narzędziu.</span><span class="sxs-lookup"><span data-stu-id="31d26-143">In pre-RC3 versions of the .NET Core command-line tools, the `dotnet pack` command had a bug that caused the `runtime.config.json` to not be packed with the tool.</span></span> <span data-ttu-id="31d26-144">Brak wyników tego pliku, błędy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="31d26-144">Lacking that file results in errors at runtime.</span></span> <span data-ttu-id="31d26-145">Jeśli wystąpi ten problem, należy zaktualizować do najnowszych narzędzi i spróbuj `dotnet pack` ponownie.</span><span class="sxs-lookup"><span data-stu-id="31d26-145">If you encounter this behavior, be sure to update to the latest tooling and try the `dotnet pack` again.</span></span>

<span data-ttu-id="31d26-146">Narzędzia są aplikacje przenośne, użytkowników, korzystanie z narzędzia musi mieć wersję biblioteki .NET Core, które narzędzie została skompilowana, aby można było uruchomić narzędzie.</span><span class="sxs-lookup"><span data-stu-id="31d26-146">Since tools are portable applications, the user consuming the tool must have the version of the .NET Core libraries that the tool was built against in order to run the tool.</span></span> <span data-ttu-id="31d26-147">Wszelkich innych zależności, że używa narzędzie i który nie jest zawarty w biblioteki .NET Core jest przywracane i umieszczane w pamięci podręcznej narzędzia NuGet.</span><span class="sxs-lookup"><span data-stu-id="31d26-147">Any other dependency that the tool uses and that is not contained within the .NET Core libraries is restored and placed in the NuGet cache.</span></span> <span data-ttu-id="31d26-148">Cały dlatego uruchomienie narzędzia przy użyciu zestawów z biblioteki .NET Core, a także zestawy z pamięcią podręczną programu NuGet.</span><span class="sxs-lookup"><span data-stu-id="31d26-148">The entire tool is, therefore, run using the assemblies from the .NET Core libraries as well as assemblies from the NuGet cache.</span></span>

<span data-ttu-id="31d26-149">Tego rodzaju narzędzia ma wykres zależności, które łączą się z wykresu zależności projektu, który używa ich.</span><span class="sxs-lookup"><span data-stu-id="31d26-149">These kinds of tools have a dependency graph that is completely separate from the dependency graph of the project that uses them.</span></span> <span data-ttu-id="31d26-150">Proces przywracania najpierw przywraca zależności projektu, a następnie przywrócenie wszystkich narzędzi i ich zależności.</span><span class="sxs-lookup"><span data-stu-id="31d26-150">The restore process first restores the project's dependencies and then restores each of the tools and their dependencies.</span></span>

<span data-ttu-id="31d26-151">Można znaleźć przykłady bardziej rozbudowane i różnych kombinacji w [repozytorium interfejsu wiersza polecenia platformy .NET Core](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).</span><span class="sxs-lookup"><span data-stu-id="31d26-151">You can find richer examples and different combinations of this in the [.NET Core CLI repo](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).</span></span>
<span data-ttu-id="31d26-152">Można również wyświetlić [implementacji narzędzia używane](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) w tym samym repozytorium.</span><span class="sxs-lookup"><span data-stu-id="31d26-152">You can also see the [implementation of tools used](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) in the same repo.</span></span>

### <a name="custom-targets"></a><span data-ttu-id="31d26-153">Niestandardowe obiekty docelowe</span><span class="sxs-lookup"><span data-stu-id="31d26-153">Custom targets</span></span>
<span data-ttu-id="31d26-154">NuGet ma możliwość [pakiet niestandardowego programu MSBuild cele i pliki właściwości](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package).</span><span class="sxs-lookup"><span data-stu-id="31d26-154">NuGet has the capability to [package custom MSBuild targets and props files](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package).</span></span> <span data-ttu-id="31d26-155">Wraz z przejściem narzędzi interfejsu wiersza polecenia platformy .NET Core, za pomocą programu MSBuild ten sam mechanizm rozszerzalności teraz ma zastosowanie do projektów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="31d26-155">With the move of the .NET Core CLI tools to use MSBuild, the same mechanism of extensibility now applies to .NET Core projects.</span></span> <span data-ttu-id="31d26-156">Będzie używać tego typu rozszerzeń, gdy chcesz rozszerzyć proces kompilacji lub chcesz uzyskać dostęp do dowolnego z artefaktów w procesie kompilacji, takie jak wygenerowanych plików lub chcesz sprawdzić konfigurację w ramach której zostanie wywołana kompilacji , itp.</span><span class="sxs-lookup"><span data-stu-id="31d26-156">You would use this type of extensibility when you want to extend the build process, or when you want to access any of the artifacts in the build process, such as generated files, or you want to inspect the configuration under which the build is invoked, etc.</span></span>

<span data-ttu-id="31d26-157">W poniższym przykładzie można zobaczyć projekt docelowy plik za pomocą `csproj` składni.</span><span class="sxs-lookup"><span data-stu-id="31d26-157">In the following example, you can see the target's project file using the `csproj` syntax.</span></span> <span data-ttu-id="31d26-158">To powoduje, że [ `dotnet pack` ](dotnet-pack.md) polecenia wybierania elementów do pakietu, umieszczania plików obiektów docelowych, a także zestawy w *kompilacji* folder wewnątrz pakietu.</span><span class="sxs-lookup"><span data-stu-id="31d26-158">This instructs the [`dotnet pack`](dotnet-pack.md) command what to package, placing the targets files as well as the assemblies into the *build* folder inside the package.</span></span> <span data-ttu-id="31d26-159">Zwróć uwagę `<ItemGroup>` element, który ma `Label` właściwością `dotnet pack instructions`, i docelowy zdefiniowane poniżej.</span><span class="sxs-lookup"><span data-stu-id="31d26-159">Notice the `<ItemGroup>` element that has the `Label` property set to `dotnet pack instructions`, and the Target defined beneath it.</span></span>

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

<span data-ttu-id="31d26-160">Korzystanie z niestandardowych elementów docelowych to zrobić, podając `<PackageReference>` wskazującego na pakiet i jego wersji wewnątrz projektu, który jest rozszerzany.</span><span class="sxs-lookup"><span data-stu-id="31d26-160">Consuming custom targets is done by providing a `<PackageReference>` that points to the package and its version inside the project that is being extended.</span></span> <span data-ttu-id="31d26-161">W przeciwieństwie do narzędzia ujęte pakietu niestandardowe obiekty docelowe do zamknięcia zależności projektu odbierająca komunikaty.</span><span class="sxs-lookup"><span data-stu-id="31d26-161">Unlike the tools, the custom targets package does get included into the consuming project's dependency closure.</span></span>

<span data-ttu-id="31d26-162">Przy użyciu niestandardowe obiekty docelowe zależy wyłącznie od konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="31d26-162">Using the custom target depends solely on how you configure it.</span></span> <span data-ttu-id="31d26-163">Ponieważ jest obiekt docelowy programu MSBuild, może zależeć na danym obiektem docelowym Uruchom po innym elementem docelowym i może również być ręcznego wywołania odbywa się przy użyciu `dotnet msbuild -t:<target-name>` polecenia.</span><span class="sxs-lookup"><span data-stu-id="31d26-163">Since it's an MSBuild target, it can depend on a given target, run after another target and can also be manually invoked using the `dotnet msbuild -t:<target-name>` command.</span></span>

<span data-ttu-id="31d26-164">Jednak jeśli chcesz zapewnić lepsze środowisko użytkownika do użytkowników, można połączyć narzędzi dla projektów i niestandardowych elementów docelowych.</span><span class="sxs-lookup"><span data-stu-id="31d26-164">However, if you want to provide a better user experience to your users, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="31d26-165">W tym scenariuszu narzędzie-projekt będzie zasadniczo wystarczy zaakceptować dowolnie wymagane parametry i czy tłumaczenie, wymagane [ `dotnet msbuild` ](dotnet-msbuild.md) wywołania, które element docelowy jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="31d26-165">In this scenario, the per-project tool would essentially just accept whatever needed parameters and would translate that into the required [`dotnet msbuild`](dotnet-msbuild.md) invocation that would execute the target.</span></span> <span data-ttu-id="31d26-166">Przykład tego rodzaju synergii może zobaczyć na [przykłady MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) repozytorium w [ `dotnet-packer` ](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) projektu.</span><span class="sxs-lookup"><span data-stu-id="31d26-166">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

### <a name="path-based-extensibility"></a><span data-ttu-id="31d26-167">Rozszerzalność opartego na ŚCIEŻKACH</span><span class="sxs-lookup"><span data-stu-id="31d26-167">PATH-based extensibility</span></span>
<span data-ttu-id="31d26-168">Rozszerzalność opartego na ŚCIEŻKACH jest zazwyczaj używane do tworzenia maszyn wymagających to narzędzie, które pod względem koncepcyjnym obejmuje więcej niż jednego projektu.</span><span class="sxs-lookup"><span data-stu-id="31d26-168">PATH-based extensibility is usually used for development machines where you need a tool that conceptually covers more than a single project.</span></span> <span data-ttu-id="31d26-169">Główną wadą tego mechanizmu rozszerzenia jest, że jest powiązany z maszyną której istnieje narzędzie.</span><span class="sxs-lookup"><span data-stu-id="31d26-169">The main drawback of this extension mechanism is that it's tied to the machine where the tool exists.</span></span> <span data-ttu-id="31d26-170">Jeśli potrzebujesz jej na innym komputerze, trzeba ją wdrożyć.</span><span class="sxs-lookup"><span data-stu-id="31d26-170">If you need it on another machine, you would have to deploy it.</span></span>

<span data-ttu-id="31d26-171">Ten wzorzec rozszerzalności narzędzi interfejsu wiersza polecenia jest bardzo proste.</span><span class="sxs-lookup"><span data-stu-id="31d26-171">This pattern of CLI toolset extensibility is very simple.</span></span> <span data-ttu-id="31d26-172">Zgodnie z opisem w [omówienie interfejsu wiersza polecenia platformy .NET Core](index.md), `dotnet` sterownik można uruchomić dowolne polecenie, który nosi nazwę po `dotnet-<command>` Konwencji.</span><span class="sxs-lookup"><span data-stu-id="31d26-172">As covered in the [.NET Core CLI overview](index.md), `dotnet` driver can run any command that is named after the `dotnet-<command>` convention.</span></span> <span data-ttu-id="31d26-173">Domyślnej logiki rozpoznawania najpierw sondy w kilku lokalizacjach, a na koniec przechodzi do ścieżki systemu.</span><span class="sxs-lookup"><span data-stu-id="31d26-173">The default resolution logic first probes several locations and finally falls back to the system PATH.</span></span> <span data-ttu-id="31d26-174">Jeśli żądane polecenie w systemie ŚCIEŻKA istnieje i jest plik binarny, który może być wywołana, `dotnet` sterowników będzie go wywoływać.</span><span class="sxs-lookup"><span data-stu-id="31d26-174">If the requested command exists in the system PATH and is a binary that can be invoked, `dotnet` driver will invoke it.</span></span>

<span data-ttu-id="31d26-175">Plik musi być pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="31d26-175">The file must be executable.</span></span> <span data-ttu-id="31d26-176">W systemach Unix, oznacza to wszystko, co ma ustawiony bit wykonania za pośrednictwem `chmod +x`.</span><span class="sxs-lookup"><span data-stu-id="31d26-176">On Unix systems, this means anything that has the execute bit set via `chmod +x`.</span></span> <span data-ttu-id="31d26-177">Windows, mogą używać *cmd* plików.</span><span class="sxs-lookup"><span data-stu-id="31d26-177">On Windows, you can use *cmd* files.</span></span>

<span data-ttu-id="31d26-178">Spójrzmy na bardzo proste Wdrażanie narzędzia "Hello World".</span><span class="sxs-lookup"><span data-stu-id="31d26-178">Let's take a look at the very simple implementation of a "Hello World" tool.</span></span> <span data-ttu-id="31d26-179">Będziemy używać zarówno `bash` i `cmd` na Windows.</span><span class="sxs-lookup"><span data-stu-id="31d26-179">We will use both `bash` and `cmd` on Windows.</span></span>
<span data-ttu-id="31d26-180">Następujące polecenie będzie po prostu echo "Hello World" do konsoli.</span><span class="sxs-lookup"><span data-stu-id="31d26-180">The following command will simply echo "Hello World" to the console.</span></span>

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

<span data-ttu-id="31d26-181">W systemie macOS można zapisać skrypt jako `dotnet-hello` i ustaw jego bit pliku wykonywalnego z `chmod +x dotnet-hello`.</span><span class="sxs-lookup"><span data-stu-id="31d26-181">On macOS, we can save this script as `dotnet-hello` and set its executable bit with `chmod +x dotnet-hello`.</span></span> <span data-ttu-id="31d26-182">Następnie możemy utworzyć łącze symboliczne do niego w `/usr/local/bin` za pomocą polecenia `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span><span class="sxs-lookup"><span data-stu-id="31d26-182">We can then create a symbolic link to it in `/usr/local/bin` using the command `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span></span> <span data-ttu-id="31d26-183">Umożliwi to można wywołać za pomocą polecenia `dotnet hello` składni.</span><span class="sxs-lookup"><span data-stu-id="31d26-183">This will make it possible to invoke the command using the `dotnet hello` syntax.</span></span>

<span data-ttu-id="31d26-184">W systemie Windows, firma Microsoft można zapisać skrypt jako `dotnet-hello.cmd` i umieścić go w lokalizacji, która znajduje się w ścieżce systemu (lub można dodać go do folderu, który już znajduje się w ścieżce).</span><span class="sxs-lookup"><span data-stu-id="31d26-184">On Windows, we can save this script as `dotnet-hello.cmd` and put it in a location that is in a system path (or you can add it to a folder that is already in the path).</span></span> <span data-ttu-id="31d26-185">Dzięki temu wystarczy użyć `dotnet hello` do uruchomienia tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="31d26-185">After this, you can just use `dotnet hello` to run this example.</span></span>
