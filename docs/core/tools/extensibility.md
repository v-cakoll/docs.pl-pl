---
title: Interfejs wiersza polecenia platformy .NET Core model rozszerzalności
description: Dowiedz się, w jaki sposób można rozciągnąć interfejs wiersza polecenia platformy .NET Core.
ms.date: 04/12/2017
ms.openlocfilehash: 74da895fb3a3f6c77640a2b9a64acdb2894a954b
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920516"
---
# <a name="net-core-cli-extensibility-model"></a><span data-ttu-id="34ca7-103">Interfejs wiersza polecenia platformy .NET Core model rozszerzalności</span><span class="sxs-lookup"><span data-stu-id="34ca7-103">.NET Core CLI extensibility model</span></span>

<span data-ttu-id="34ca7-104">W tym artykule opisano różne sposoby, w których można zwiększyć interfejs wiersza polecenia platformy .NET Core i wyjaśnić scenariusze, które obejmują każdy z nich.</span><span class="sxs-lookup"><span data-stu-id="34ca7-104">This article covers the different ways you can extend the .NET Core CLI and explain the scenarios that drive each one of them.</span></span>
<span data-ttu-id="34ca7-105">Zobaczysz, jak korzystać z narzędzi, a także jak tworzyć różne typy narzędzi.</span><span class="sxs-lookup"><span data-stu-id="34ca7-105">You'll see how to consume the tools as well as how to build the different types of tools.</span></span>

## <a name="how-to-extend-the-cli"></a><span data-ttu-id="34ca7-106">Jak zwiększyć interfejs wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="34ca7-106">How to extend the CLI</span></span>
<span data-ttu-id="34ca7-107">Interfejs wiersza polecenia można rozszerzyć na trzy główne sposoby:</span><span class="sxs-lookup"><span data-stu-id="34ca7-107">The CLI can be extended in three main ways:</span></span>

1. [<span data-ttu-id="34ca7-108">Za pośrednictwem pakietów NuGet dla poszczególnych projektów</span><span class="sxs-lookup"><span data-stu-id="34ca7-108">Via NuGet packages on a per-project basis</span></span>](#per-project-based-extensibility)

   <span data-ttu-id="34ca7-109">Narzędzia dla poszczególnych projektów są zawarte w kontekście projektu, ale umożliwiają łatwe instalowanie poprzez przywracanie.</span><span class="sxs-lookup"><span data-stu-id="34ca7-109">Per-project tools are contained within the project's context, but they allow easy installation through restoration.</span></span>

2. [<span data-ttu-id="34ca7-110">Za pośrednictwem pakietów NuGet z niestandardowymi obiektami docelowymi</span><span class="sxs-lookup"><span data-stu-id="34ca7-110">Via NuGet packages with custom targets</span></span>](#custom-targets)

   <span data-ttu-id="34ca7-111">Niestandardowe elementy docelowe pozwalają łatwo rozwijać proces kompilacji z zadaniami niestandardowymi.</span><span class="sxs-lookup"><span data-stu-id="34ca7-111">Custom targets allow you to easily extend the build process with custom tasks.</span></span>

3. [<span data-ttu-id="34ca7-112">Za pośrednictwem ścieżki systemu</span><span class="sxs-lookup"><span data-stu-id="34ca7-112">Via the system's PATH</span></span>](#path-based-extensibility)

   <span data-ttu-id="34ca7-113">Narzędzia oparte na ścieżce są dobre dla ogólnych narzędzi do tworzenia projektów, których można użyć na pojedynczym komputerze.</span><span class="sxs-lookup"><span data-stu-id="34ca7-113">PATH-based tools are good for general, cross-project tools that are usable on a single machine.</span></span>

<span data-ttu-id="34ca7-114">Trzy opisane powyżej mechanizmy rozszerzalności nie są wyłączne.</span><span class="sxs-lookup"><span data-stu-id="34ca7-114">The three extensibility mechanisms outlined above are not exclusive.</span></span> <span data-ttu-id="34ca7-115">Można użyć jednej lub wszystkiego lub kombinacji tych elementów.</span><span class="sxs-lookup"><span data-stu-id="34ca7-115">You can use one, or all, or a combination of them.</span></span> <span data-ttu-id="34ca7-116">Który z nich należy wybrać, zależy głównie od celu, który próbujesz osiągnąć przy użyciu rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="34ca7-116">Which one to pick depends largely on the goal you are trying to achieve with your extension.</span></span>

## <a name="per-project-based-extensibility"></a><span data-ttu-id="34ca7-117">Rozszerzalność na podstawie projektu</span><span class="sxs-lookup"><span data-stu-id="34ca7-117">Per-project based extensibility</span></span>
<span data-ttu-id="34ca7-118">Narzędzia dla poszczególnych projektów są [wdrożeniami zależnymi od platformy](../deploying/index.md#framework-dependent-deployments-fdd) , które są dystrybuowane jako pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="34ca7-118">Per-project tools are [framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) that are distributed as NuGet packages.</span></span> <span data-ttu-id="34ca7-119">Narzędzia są dostępne tylko w kontekście projektu, który odwołuje się do nich i dla którego są przywracane.</span><span class="sxs-lookup"><span data-stu-id="34ca7-119">Tools are only available in the context of the project that references them and for which they are restored.</span></span> <span data-ttu-id="34ca7-120">Wywołanie poza kontekstem projektu (na przykład poza katalogiem zawierającym projekt) zakończy się niepowodzeniem, ponieważ nie można odnaleźć polecenia.</span><span class="sxs-lookup"><span data-stu-id="34ca7-120">Invocation outside of the context of the project (for example, outside of the directory that contains the project) will fail because the command cannot be found.</span></span>

<span data-ttu-id="34ca7-121">Narzędzia te są idealnym rozwiązaniem dla serwerów kompilacji, ponieważ nie jest wymagany żaden poza plikiem projektu.</span><span class="sxs-lookup"><span data-stu-id="34ca7-121">These tools are perfect for build servers, since nothing outside of the project file is needed.</span></span> <span data-ttu-id="34ca7-122">Proces kompilacji uruchamia przywracanie dla projektu, który kompiluje i dostępne są narzędzia.</span><span class="sxs-lookup"><span data-stu-id="34ca7-122">The build process runs restore for the project it builds and tools will be available.</span></span> <span data-ttu-id="34ca7-123">Projekty języka, takie jak F#, są również w tej kategorii, ponieważ każdy projekt może być zapisany tylko w jednym określonym języku.</span><span class="sxs-lookup"><span data-stu-id="34ca7-123">Language projects, such as F#, are also in this category since each project can only be written in one specific language.</span></span>

<span data-ttu-id="34ca7-124">Na koniec ten model rozszerzalności zapewnia obsługę tworzenia narzędzi, które wymagają dostępu do skompilowanych danych wyjściowych projektu.</span><span class="sxs-lookup"><span data-stu-id="34ca7-124">Finally, this extensibility model provides support for creation of tools that need access to the built output of the project.</span></span> <span data-ttu-id="34ca7-125">Na przykład różne narzędzia widoku Razor w aplikacjach [ASP.NET](https://www.asp.net/) MVC należą do tej kategorii.</span><span class="sxs-lookup"><span data-stu-id="34ca7-125">For instance, various Razor view tools in [ASP.NET](https://www.asp.net/) MVC applications fall into this category.</span></span>

### <a name="consuming-per-project-tools"></a><span data-ttu-id="34ca7-126">Zużywanie narzędzi dla projektu</span><span class="sxs-lookup"><span data-stu-id="34ca7-126">Consuming per-project tools</span></span>
<span data-ttu-id="34ca7-127">Używanie tych narzędzi wymaga dodania elementu `<DotNetCliToolReference>` do pliku projektu dla każdego narzędzia, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="34ca7-127">Consuming these tools requires you to add a `<DotNetCliToolReference>` element to your project file for each tool you want to use.</span></span> <span data-ttu-id="34ca7-128">Wewnątrz elementu `<DotNetCliToolReference>` należy odwołać się do pakietu, w którym znajduje się narzędzie i określić wymaganą wersję.</span><span class="sxs-lookup"><span data-stu-id="34ca7-128">Inside the `<DotNetCliToolReference>` element, you reference the package in which the tool resides and specify the version you need.</span></span> <span data-ttu-id="34ca7-129">Po uruchomieniu [`dotnet restore`](dotnet-restore.md)narzędzie i jego zależności są przywracane.</span><span class="sxs-lookup"><span data-stu-id="34ca7-129">After running [`dotnet restore`](dotnet-restore.md), the tool and its dependencies are restored.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="34ca7-130">W przypadku narzędzi, które wymagają załadowania danych wyjściowych kompilacji projektu do wykonania, zazwyczaj istnieje inna zależność, która jest wymieniona w ramach zwykłych zależności w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="34ca7-130">For tools that need to load the build output of the project for execution, there is usually another dependency which is listed under the regular dependencies in the project file.</span></span> <span data-ttu-id="34ca7-131">Ponieważ interfejs wiersza polecenia używa programu MSBuild jako aparatu kompilacji, zalecamy, aby te części narzędzia były zapisywane jako niestandardowe [elementy docelowe](/visualstudio/msbuild/msbuild-targets) i [zadania](/visualstudio/msbuild/msbuild-tasks)programu MSBuild, ponieważ mogą one następnie wziąć udział w ogólnym procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="34ca7-131">Since CLI uses MSBuild as its build engine, we recommend that these parts of the tool be written as custom MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and [tasks](/visualstudio/msbuild/msbuild-tasks), since they can then take part in the overall build process.</span></span> <span data-ttu-id="34ca7-132">Ponadto mogą łatwo uzyskać wszystkie dane, które są tworzone przez kompilację, takie jak lokalizacja plików wyjściowych, Bieżąca konfiguracja utworzona i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="34ca7-132">Also, they can get any and all data easily that is produced via the build, such as the location of the output files, the current configuration being built, and so on.</span></span> <span data-ttu-id="34ca7-133">Wszystkie te informacje staną się zestawem właściwości programu MSBuild, które mogą być odczytywane z dowolnego celu.</span><span class="sxs-lookup"><span data-stu-id="34ca7-133">All this information becomes a set of MSBuild properties that can be read from any target.</span></span> <span data-ttu-id="34ca7-134">Aby dowiedzieć się, jak dodać niestandardowy obiekt docelowy przy użyciu narzędzia NuGet w dalszej części tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="34ca7-134">You can see how to add a custom target using NuGet later in this document.</span></span>

<span data-ttu-id="34ca7-135">Zapoznajmy się z przykładem dodawania prostych narzędzi tylko do prostej części projektu.</span><span class="sxs-lookup"><span data-stu-id="34ca7-135">Let's review an example of adding a simple tools-only tool to a simple project.</span></span> <span data-ttu-id="34ca7-136">Dane przykładowe polecenie o nazwie `dotnet-api-search`, które pozwala wyszukiwać pakiety NuGet dla określonego interfejsu API, poniżej przedstawiono plik projektu aplikacji konsolowej, który używa tego narzędzia:</span><span class="sxs-lookup"><span data-stu-id="34ca7-136">Given an example command called `dotnet-api-search` that allows you to search through the NuGet packages for the specified API, here is a console application's project file that uses that tool:</span></span>

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

<span data-ttu-id="34ca7-137">Element `<DotNetCliToolReference>` jest strukturalny w podobny sposób, jak element `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="34ca7-137">The `<DotNetCliToolReference>` element is structured in a similar way as the `<PackageReference>` element.</span></span> <span data-ttu-id="34ca7-138">Wymaga identyfikatora pakietu zawierającego narzędzie i jego wersję, aby można było go przywrócić.</span><span class="sxs-lookup"><span data-stu-id="34ca7-138">It needs the package ID of the package containing the tool and its version to be able to restore.</span></span>

### <a name="building-tools"></a><span data-ttu-id="34ca7-139">Narzędzia do kompilowania</span><span class="sxs-lookup"><span data-stu-id="34ca7-139">Building tools</span></span>
<span data-ttu-id="34ca7-140">Jak wspomniano, narzędzia są tylko przenośnymi aplikacjami konsolowymi.</span><span class="sxs-lookup"><span data-stu-id="34ca7-140">As mentioned, tools are just portable console applications.</span></span> <span data-ttu-id="34ca7-141">Możesz tworzyć narzędzia, tak jak w przypadku tworzenia innej aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="34ca7-141">You build tools as you would build any other console application.</span></span>
<span data-ttu-id="34ca7-142">Po skompilowaniu należy użyć polecenia [`dotnet pack`](dotnet-pack.md) , aby utworzyć pakiet NuGet (plik. nupkg) zawierający kod, informacje o jego zależnościach itd.</span><span class="sxs-lookup"><span data-stu-id="34ca7-142">After you build it, you use the [`dotnet pack`](dotnet-pack.md) command to create a NuGet package (.nupkg file) that contains your code, information about its dependencies, and so on.</span></span> <span data-ttu-id="34ca7-143">Możesz nadać dowolną nazwę pakietowi, ale aplikacja wewnątrz, rzeczywiste dane binarne narzędzia, musi być zgodna z Konwencją `dotnet-<command>`, aby `dotnet` mogła ją wywołać.</span><span class="sxs-lookup"><span data-stu-id="34ca7-143">You can give any name to the package, but the application inside, the actual tool binary, has to conform to the convention of `dotnet-<command>` in order for `dotnet` to be able to invoke it.</span></span>

> [!NOTE]
> <span data-ttu-id="34ca7-144">W wersjach wstępnej RC3 narzędzi wiersza polecenia programu .NET Core polecenie `dotnet pack` miało usterkę, która spowodowała, że plik *. runtimeconfig. JSON* nie został spakowany przy użyciu narzędzia.</span><span class="sxs-lookup"><span data-stu-id="34ca7-144">In pre-RC3 versions of the .NET Core command-line tools, the `dotnet pack` command had a bug that caused the *.runtimeconfig.json* to not be packed with the tool.</span></span> <span data-ttu-id="34ca7-145">Brak tego pliku powoduje błędy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="34ca7-145">Lacking that file results in errors at runtime.</span></span> <span data-ttu-id="34ca7-146">Jeśli wystąpi takie zachowanie, pamiętaj o zaktualizowaniu do najnowszych narzędzi i spróbuj ponownie wykonać `dotnet pack`.</span><span class="sxs-lookup"><span data-stu-id="34ca7-146">If you encounter this behavior, be sure to update to the latest tooling and try the `dotnet pack` again.</span></span>

<span data-ttu-id="34ca7-147">Ponieważ narzędzia są aplikacjami przenośnymi, użytkownik korzystający z tego narzędzia musi mieć wersję bibliotek .NET Core, dla których narzędzie zostało skompilowane w celu uruchomienia narzędzia.</span><span class="sxs-lookup"><span data-stu-id="34ca7-147">Since tools are portable applications, the user consuming the tool must have the version of the .NET Core libraries that the tool was built against in order to run the tool.</span></span> <span data-ttu-id="34ca7-148">Każda inna zależność wykorzystywana przez narzędzie i, która nie jest zawarta w bibliotekach programu .NET Core, jest przywracana i umieszczana w pamięci podręcznej NuGet.</span><span class="sxs-lookup"><span data-stu-id="34ca7-148">Any other dependency that the tool uses and that is not contained within the .NET Core libraries is restored and placed in the NuGet cache.</span></span> <span data-ttu-id="34ca7-149">W związku z tym, należy uruchomić polecenie przy użyciu zestawów z bibliotek .NET Core, a także zestawów z pamięci podręcznej NuGet.</span><span class="sxs-lookup"><span data-stu-id="34ca7-149">The entire tool is, therefore, run using the assemblies from the .NET Core libraries as well as assemblies from the NuGet cache.</span></span>

<span data-ttu-id="34ca7-150">Te rodzaje narzędzi mają wykres zależności, który jest całkowicie oddzielony od wykresu zależności projektu, który z nich korzysta.</span><span class="sxs-lookup"><span data-stu-id="34ca7-150">These kinds of tools have a dependency graph that is completely separate from the dependency graph of the project that uses them.</span></span> <span data-ttu-id="34ca7-151">Proces przywracania najpierw przywraca zależności projektu, a następnie przywraca wszystkie narzędzia i ich zależności.</span><span class="sxs-lookup"><span data-stu-id="34ca7-151">The restore process first restores the project's dependencies and then restores each of the tools and their dependencies.</span></span>

<span data-ttu-id="34ca7-152">W [repozytorium interfejs wiersza polecenia platformy .NET Core](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects)można znaleźć bogatsze przykłady i różne kombinacje tych elementów.</span><span class="sxs-lookup"><span data-stu-id="34ca7-152">You can find richer examples and different combinations of this in the [.NET Core CLI repo](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).</span></span>
<span data-ttu-id="34ca7-153">Możesz również zobaczyć [implementację narzędzi używanych](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) w tym samym repozytorium.</span><span class="sxs-lookup"><span data-stu-id="34ca7-153">You can also see the [implementation of tools used](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) in the same repo.</span></span>

## <a name="custom-targets"></a><span data-ttu-id="34ca7-154">Niestandardowe elementy docelowe</span><span class="sxs-lookup"><span data-stu-id="34ca7-154">Custom targets</span></span>

<span data-ttu-id="34ca7-155">Pakiet NuGet ma możliwość [spakowania niestandardowych obiektów docelowych programu MSBuild i plików props](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package).</span><span class="sxs-lookup"><span data-stu-id="34ca7-155">NuGet has the capability to [package custom MSBuild targets and props files](/nuget/create-packages/creating-a-package#include-msbuild-props-and-targets-in-a-package).</span></span> <span data-ttu-id="34ca7-156">Po przeniesieniu środowiska .NET Core do korzystania z programu MSBuild ten sam mechanizm rozszerzania ma teraz zastosowanie do projektów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="34ca7-156">With the move of the .NET Core to use MSBuild, the same mechanism of extensibility now applies to .NET Core projects.</span></span> <span data-ttu-id="34ca7-157">Tego typu rozszerzalność należy użyć, gdy chcesz rozszerzać proces kompilacji lub Kiedy chcesz uzyskać dostęp do dowolnego artefaktu w procesie kompilacji, na przykład wygenerowanych plików, lub chcesz sprawdzić konfigurację, w której jest wywoływana kompilacja. itd.</span><span class="sxs-lookup"><span data-stu-id="34ca7-157">You would use this type of extensibility when you want to extend the build process, or when you want to access any of the artifacts in the build process, such as generated files, or you want to inspect the configuration under which the build is invoked, and so on.</span></span>

<span data-ttu-id="34ca7-158">W poniższym przykładzie można zobaczyć docelowy plik projektu przy użyciu składni `csproj`.</span><span class="sxs-lookup"><span data-stu-id="34ca7-158">In the following example, you can see the target's project file using the `csproj` syntax.</span></span> <span data-ttu-id="34ca7-159">Powoduje to nadanie [`dotnet pack`](dotnet-pack.md) polecenia do pakowania, umieszczenia plików docelowych oraz zestawów w folderze *kompilacji* wewnątrz pakietu.</span><span class="sxs-lookup"><span data-stu-id="34ca7-159">This instructs the [`dotnet pack`](dotnet-pack.md) command what to package, placing the targets files as well as the assemblies into the *build* folder inside the package.</span></span> <span data-ttu-id="34ca7-160">Zwróć uwagę na element `<ItemGroup>`, który ma właściwość `Label` ustawioną na `dotnet pack instructions`, i element docelowy zdefiniowany poniżej.</span><span class="sxs-lookup"><span data-stu-id="34ca7-160">Notice the `<ItemGroup>` element that has the `Label` property set to `dotnet pack instructions`, and the Target defined beneath it.</span></span>

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

<span data-ttu-id="34ca7-161">Używanie niestandardowych elementów docelowych odbywa się poprzez dostarczenie `<PackageReference>`, które wskazuje na pakiet i jego wersję w ramach rozszerzanego projektu.</span><span class="sxs-lookup"><span data-stu-id="34ca7-161">Consuming custom targets is done by providing a `<PackageReference>` that points to the package and its version inside the project that is being extended.</span></span> <span data-ttu-id="34ca7-162">W przeciwieństwie do narzędzi, pakiet Custom targets zostanie uwzględniony w zamknięciu zależności projektu zużywanego.</span><span class="sxs-lookup"><span data-stu-id="34ca7-162">Unlike the tools, the custom targets package does get included into the consuming project's dependency closure.</span></span>

<span data-ttu-id="34ca7-163">Użycie niestandardowego obiektu docelowego zależy wyłącznie od sposobu jego konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="34ca7-163">Using the custom target depends solely on how you configure it.</span></span> <span data-ttu-id="34ca7-164">Ponieważ jest to element docelowy programu MSBuild, może on zależeć od danego elementu docelowego, działać po innej lokalizacji docelowej i może być również ręcznie wywoływany przy użyciu polecenia `dotnet msbuild -t:<target-name>`.</span><span class="sxs-lookup"><span data-stu-id="34ca7-164">Since it's an MSBuild target, it can depend on a given target, run after another target and can also be manually invoked using the `dotnet msbuild -t:<target-name>` command.</span></span>

<span data-ttu-id="34ca7-165">Jeśli jednak chcesz zapewnić użytkownikom lepszy interfejs użytkownika, możesz połączyć narzędzia dla poszczególnych projektów i niestandardowe elementy docelowe.</span><span class="sxs-lookup"><span data-stu-id="34ca7-165">However, if you want to provide a better user experience to your users, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="34ca7-166">W tym scenariuszu narzędzie dla poszczególnych projektów zasadniczo akceptuje wszelkie wymagane parametry i tłumaczy je na wymagane [`dotnet msbuild`](dotnet-msbuild.md) wywołanie, które wykona obiekt docelowy.</span><span class="sxs-lookup"><span data-stu-id="34ca7-166">In this scenario, the per-project tool would essentially just accept whatever needed parameters and would translate that into the required [`dotnet msbuild`](dotnet-msbuild.md) invocation that would execute the target.</span></span> <span data-ttu-id="34ca7-167">Możesz zobaczyć przykład tego rodzaju synergii na repozytorium [przykładów hackathon szczytu MVP 2016](https://github.com/dotnet/MVPSummitHackathon2016) w projekcie [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) .</span><span class="sxs-lookup"><span data-stu-id="34ca7-167">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

## <a name="path-based-extensibility"></a><span data-ttu-id="34ca7-168">Rozszerzalność oparta na ścieżce</span><span class="sxs-lookup"><span data-stu-id="34ca7-168">PATH-based extensibility</span></span>
<span data-ttu-id="34ca7-169">Rozszerzalność oparta na ŚCIEŻKAch jest zwykle używana dla maszyn deweloperskich, gdzie potrzebujesz narzędzia, które koncepcyjnie omawia więcej niż jeden projekt.</span><span class="sxs-lookup"><span data-stu-id="34ca7-169">PATH-based extensibility is usually used for development machines where you need a tool that conceptually covers more than a single project.</span></span> <span data-ttu-id="34ca7-170">Główną wadą tego mechanizmu rozszerzenia jest to, że jest on powiązany z maszyną, na której znajduje się narzędzie.</span><span class="sxs-lookup"><span data-stu-id="34ca7-170">The main drawback of this extension mechanism is that it's tied to the machine where the tool exists.</span></span> <span data-ttu-id="34ca7-171">Jeśli potrzebujesz go na innym komputerze, musisz go wdrożyć.</span><span class="sxs-lookup"><span data-stu-id="34ca7-171">If you need it on another machine, you would have to deploy it.</span></span>

<span data-ttu-id="34ca7-172">Ten wzorzec rozszerzalności zestawu narzędzi interfejsu wiersza polecenia jest bardzo prosty.</span><span class="sxs-lookup"><span data-stu-id="34ca7-172">This pattern of CLI toolset extensibility is very simple.</span></span> <span data-ttu-id="34ca7-173">Jak opisano w [interfejs wiersza polecenia platformy .NET Core przegląd](index.md), `dotnet` sterownik może uruchomić dowolne polecenie o nazwie po Konwencji `dotnet-<command>`.</span><span class="sxs-lookup"><span data-stu-id="34ca7-173">As covered in the [.NET Core CLI overview](index.md), `dotnet` driver can run any command that is named after the `dotnet-<command>` convention.</span></span> <span data-ttu-id="34ca7-174">Domyślna logika rozpoznawania w pierwszej sondy kilka lokalizacji, a wreszcie powraca do ścieżki systemowej.</span><span class="sxs-lookup"><span data-stu-id="34ca7-174">The default resolution logic first probes several locations and finally falls back to the system PATH.</span></span> <span data-ttu-id="34ca7-175">Jeśli żądane polecenie istnieje w ścieżce systemowej i jest plikiem binarnym, który można wywołać, `dotnet` sterownik wywoła go.</span><span class="sxs-lookup"><span data-stu-id="34ca7-175">If the requested command exists in the system PATH and is a binary that can be invoked, `dotnet` driver will invoke it.</span></span>

<span data-ttu-id="34ca7-176">Plik musi być plikiem wykonywalnym.</span><span class="sxs-lookup"><span data-stu-id="34ca7-176">The file must be executable.</span></span> <span data-ttu-id="34ca7-177">W systemach UNIX oznacza to, że wszystkie elementy mające bit Execute są ustawiane za pośrednictwem `chmod +x`.</span><span class="sxs-lookup"><span data-stu-id="34ca7-177">On Unix systems, this means anything that has the execute bit set via `chmod +x`.</span></span> <span data-ttu-id="34ca7-178">W systemie Windows można używać plików *cmd* .</span><span class="sxs-lookup"><span data-stu-id="34ca7-178">On Windows, you can use *cmd* files.</span></span>

<span data-ttu-id="34ca7-179">Przyjrzyjmy się bardzo prostej implementacji narzędzia "Hello world".</span><span class="sxs-lookup"><span data-stu-id="34ca7-179">Let's take a look at the very simple implementation of a "Hello World" tool.</span></span> <span data-ttu-id="34ca7-180">Będziemy używać obu `bash` i `cmd` w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="34ca7-180">We will use both `bash` and `cmd` on Windows.</span></span>
<span data-ttu-id="34ca7-181">Następujące polecenie spowoduje po prostu Echo "Hello world" do konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="34ca7-181">The following command will simply echo "Hello World" to the console.</span></span>

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

<span data-ttu-id="34ca7-182">W systemie macOS można zapisać ten skrypt jako `dotnet-hello` i ustawić jego bit wykonywalny z `chmod +x dotnet-hello`.</span><span class="sxs-lookup"><span data-stu-id="34ca7-182">On macOS, we can save this script as `dotnet-hello` and set its executable bit with `chmod +x dotnet-hello`.</span></span> <span data-ttu-id="34ca7-183">Następnie możemy utworzyć symboliczny link do niego w `/usr/local/bin` przy użyciu `ln -s <full_path>/dotnet-hello /usr/local/bin/`poleceń.</span><span class="sxs-lookup"><span data-stu-id="34ca7-183">We can then create a symbolic link to it in `/usr/local/bin` using the command `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span></span> <span data-ttu-id="34ca7-184">Dzięki temu można wywołać polecenie przy użyciu składni `dotnet hello`.</span><span class="sxs-lookup"><span data-stu-id="34ca7-184">This will make it possible to invoke the command using the `dotnet hello` syntax.</span></span>

<span data-ttu-id="34ca7-185">W systemie Windows można zapisać ten skrypt jako `dotnet-hello.cmd` i umieścić go w lokalizacji, która znajduje się w ścieżce systemowej (lub można ją dodać do folderu, który znajduje się już w ścieżce).</span><span class="sxs-lookup"><span data-stu-id="34ca7-185">On Windows, we can save this script as `dotnet-hello.cmd` and put it in a location that is in a system path (or you can add it to a folder that is already in the path).</span></span> <span data-ttu-id="34ca7-186">Następnie możesz użyć `dotnet hello`, aby uruchomić ten przykład.</span><span class="sxs-lookup"><span data-stu-id="34ca7-186">After this, you can just use `dotnet hello` to run this example.</span></span>
