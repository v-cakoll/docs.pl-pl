---
title: Dodatki do formatu csproj dla platformy .NET Core
description: Dowiedz się więcej o różnicach między istniejące i pliki csproj .NET Core
ms.date: 09/22/2017
ms.openlocfilehash: 49a7198dc593708abaa83e65af463ea0a7571a55
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481317"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="2e988-103">Dodatki do formatu csproj dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="2e988-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="2e988-104">W tym dokumencie opisano zmiany, które zostały dodane w plikach projektu jako część przeniesienia z *project.json* do *csproj* i [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="2e988-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="2e988-105">Aby uzyskać więcej informacji na temat składni pliku ogólnego projektu i odwołania, zobacz [plik projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="2e988-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="2e988-106">Odwołania do pakietu niejawne</span><span class="sxs-lookup"><span data-stu-id="2e988-106">Implicit package references</span></span>

<span data-ttu-id="2e988-107">Metapakiety niejawnie są określone w oparciu o framework(s) docelowej, określone w `<TargetFramework>` lub `<TargetFrameworks>` właściwości pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="2e988-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> `<TargetFrameworks>` <span data-ttu-id="2e988-108">jest ignorowana, jeśli `<TargetFramework>` jest określony, niezależnie od kolejności.</span><span class="sxs-lookup"><span data-stu-id="2e988-108">is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp2.1</TargetFramework>
 </PropertyGroup>
 ```

 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp2.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a><span data-ttu-id="2e988-109">Zalecenia</span><span class="sxs-lookup"><span data-stu-id="2e988-109">Recommendations</span></span>

<span data-ttu-id="2e988-110">Ponieważ `Microsoft.NETCore.App` lub `NetStandard.Library` metapakiety niejawnie są wywoływane, Oto nasze zalecane najlepsze rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="2e988-110">Since `Microsoft.NETCore.App` or `NetStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="2e988-111">Podczas określania wartości docelowej platformy .NET Core lub .NET Standard, nigdy nie mają wyraźne odniesienie do `Microsoft.NETCore.App` lub `NetStandard.Library` metapakiety za pośrednictwem `<PackageReference>` elementu w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="2e988-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NetStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="2e988-112">Jeśli potrzebujesz określonej wersji środowiska uruchomieniowego podczas określania wartości docelowej platformy .NET Core, należy użyć `<RuntimeFrameworkVersion>` właściwość w projekcie (na przykład `1.0.4`) zamiast odwoływać się do meta Microsoft.aspnetcore.all.</span><span class="sxs-lookup"><span data-stu-id="2e988-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  * <span data-ttu-id="2e988-113">Może się to zdarzyć, jeśli używasz [niezależna wdrożeń](../deploying/index.md#self-contained-deployments-scd) i należy określona poprawka wersję 1.0.0 LTS środowiska uruchomieniowego, na przykład.</span><span class="sxs-lookup"><span data-stu-id="2e988-113">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="2e988-114">Jeśli potrzebujesz określonej wersji `NetStandard.Library` meta Microsoft.aspnetcore.all podczas przeznaczonych dla platformy .NET Standard, możesz użyć `<NetStandardImplicitPackageVersion>` właściwości i wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="2e988-114">If you need a specific version of the `NetStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="2e988-115">Nie jawnie dodać lub zaktualizować odwołania do albo `Microsoft.NETCore.App` lub `NetStandard.Library` meta Microsoft.aspnetcore.all w projektach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2e988-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NetStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="2e988-116">Jeśli jakakolwiek wersja `NetStandard.Library` jest wymagana, gdy przy użyciu pakietu NuGet oparte na .NET Standard, NuGet automatycznie instaluje tę wersję.</span><span class="sxs-lookup"><span data-stu-id="2e988-116">If any version of `NetStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="2e988-117">Kompilacja domyślna obejmuje w projektach .NET Core</span><span class="sxs-lookup"><span data-stu-id="2e988-117">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="2e988-118">Wraz z przejściem do *csproj* format w najnowszych wersjach zestawu SDK, zmieniliśmy domyślnie zawiera i nie obejmuje elementy kompilacji i zasoby osadzone pliki właściwości zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="2e988-118">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="2e988-119">Oznacza to, że nie należy określić te elementy w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="2e988-119">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="2e988-120">Głównym powodem w ten sposób jest zaśmiecać w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="2e988-120">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="2e988-121">Wartości domyślne, które znajdują się w zestawie SDK obejmuje najbardziej typowe przypadki użycia, więc nie ma potrzeby powtarzanie ich każdego projektu, które tworzysz.</span><span class="sxs-lookup"><span data-stu-id="2e988-121">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="2e988-122">Prowadzi to do mniejsze pliki projektu, które są znacznie łatwiejsze do zrozumienia, jak również edytować ręcznie, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="2e988-122">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="2e988-123">W poniższej tabeli przedstawiono, które element oraz tych, które [elementy globalne](https://en.wikipedia.org/wiki/Glob_(programming)) zarówno uwzględniać i wykluczone w zestawie SDK:</span><span class="sxs-lookup"><span data-stu-id="2e988-123">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="2e988-124">Element</span><span class="sxs-lookup"><span data-stu-id="2e988-124">Element</span></span>           | <span data-ttu-id="2e988-125">Obejmują glob</span><span class="sxs-lookup"><span data-stu-id="2e988-125">Include glob</span></span>                              | <span data-ttu-id="2e988-126">Wyklucz glob</span><span class="sxs-lookup"><span data-stu-id="2e988-126">Exclude glob</span></span>                                                  | <span data-ttu-id="2e988-127">Usuń glob</span><span class="sxs-lookup"><span data-stu-id="2e988-127">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="2e988-128">Kompilacji</span><span class="sxs-lookup"><span data-stu-id="2e988-128">Compile</span></span>           | <span data-ttu-id="2e988-129">\*\*/\*CS (lub inne rozszerzenia językowe)</span><span class="sxs-lookup"><span data-stu-id="2e988-129">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="2e988-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="2e988-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="2e988-131">Brak</span><span class="sxs-lookup"><span data-stu-id="2e988-131">N/A</span></span>                      |
| <span data-ttu-id="2e988-132">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="2e988-132">EmbeddedResource</span></span>  | <span data-ttu-id="2e988-133">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="2e988-133">\*\*/\*.resx</span></span>                              | <span data-ttu-id="2e988-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="2e988-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="2e988-135">Brak</span><span class="sxs-lookup"><span data-stu-id="2e988-135">N/A</span></span>                      |
| <span data-ttu-id="2e988-136">Brak</span><span class="sxs-lookup"><span data-stu-id="2e988-136">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="2e988-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span><span class="sxs-lookup"><span data-stu-id="2e988-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="2e988-138">\*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="2e988-138">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="2e988-139">**Wyklucz glob** zawsze wyklucza `./bin` i `./obj` foldery, które są reprezentowane przez `$(BaseOutputPath)` i `$(BaseIntermediateOutputPath)` właściwości programu MSBuild, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="2e988-139">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="2e988-140">Podsumowując, wyklucza wszystkie są reprezentowane przez `$(DefaultItemExcludes)`.</span><span class="sxs-lookup"><span data-stu-id="2e988-140">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="2e988-141">Jeśli podczas próby utworzenia go za pomocą zestawu SDK najnowsze elementy globalne są zdefiniowane w projekcie, otrzymasz następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="2e988-141">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="2e988-142">Zduplikowane elementy kompilacji zostaną uwzględnione.</span><span class="sxs-lookup"><span data-stu-id="2e988-142">Duplicate Compile items were included.</span></span> <span data-ttu-id="2e988-143">Zestaw SDK platformy .NET obejmuje elementy kompilacji z katalogu projektu domyślnie.</span><span class="sxs-lookup"><span data-stu-id="2e988-143">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="2e988-144">Możesz usunąć te elementy z pliku projektu lub ustaw właściwość "EnableDefaultCompileItems", "false", jeśli chcesz jawnie umieszczone w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="2e988-144">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="2e988-145">Aby obejść ten błąd, można usunąć jawne `Compile` elementy, które są zgodne z typami wymienionych w powyższej tabeli, można także ustawić `<EnableDefaultCompileItems>` właściwości `false`, podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="2e988-145">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="2e988-146">Ustawienie tej właściwości na `false` spowoduje wyłączenie włączenia niejawne, przywrócenie zachowania poprzedniego zestawów SDK, który wymagał określić elementy domyślne globalne w projekcie.</span><span class="sxs-lookup"><span data-stu-id="2e988-146">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="2e988-147">Ta zmiana nie powoduje modyfikacji głównego zawiera mechanika innych.</span><span class="sxs-lookup"><span data-stu-id="2e988-147">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="2e988-148">Jednak jeśli chcesz określić, na przykład, niektóre pliki na publikowaniu z Twoją aplikacją, nadal można znanych mechanizmów w *csproj* do tego (na przykład `<Content>` elementu).</span><span class="sxs-lookup"><span data-stu-id="2e988-148">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

`<EnableDefaultCompileItems>` <span data-ttu-id="2e988-149">powoduje wyłączenie tylko `Compile` elementy globalne, ale nie ma wpływu na inne elementy globalne, takich jak niejawny `None` glob, która ma zastosowanie również do \*.cs elementów.</span><span class="sxs-lookup"><span data-stu-id="2e988-149">only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="2e988-150">Z tego powodu **Eksploratora rozwiązań** będą nadal show \*.cs elementy w ramach projektu, dołączone jako `None` elementów.</span><span class="sxs-lookup"><span data-stu-id="2e988-150">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="2e988-151">W podobny sposób można ustawić `<EnableDefaultNoneItems>` wartość false, aby wyłączyć niejawny `None` glob w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2e988-151">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="2e988-152">Aby wyłączyć **wszystkie niejawne elementy globalne**, można ustawić `<EnableDefaultItems>` właściwość `false` jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2e988-152">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="2e988-153">Jak wyświetlić całego projektu, jak MSBuild widzi on</span><span class="sxs-lookup"><span data-stu-id="2e988-153">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="2e988-154">Chociaż te zmiany w pliku csproj znacznie upraszczają pliki projektu, możesz chcieć wyświetlaną w pełni rozwinięte projektu MSBuild widzi on po zestawie SDK i jego obiekty docelowe są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="2e988-154">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="2e988-155">Przetwarzanie wstępne projektu z [ `/pp` Przełącz](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) z [ `dotnet msbuild` ](dotnet-msbuild.md) polecenia, które pokazują, które pliki są importowane, ich źródła i materiały przekazywane do kompilacji bez faktycznego Tworzenie projektu:</span><span class="sxs-lookup"><span data-stu-id="2e988-155">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="2e988-156">Jeśli projekt zawiera wiele platform docelowych, wyniki polecenia powinna zostać zwrócona na tylko jeden z nich, określając ją jako właściwość narzędzia MSBuild:</span><span class="sxs-lookup"><span data-stu-id="2e988-156">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="2e988-157">Dodatki</span><span class="sxs-lookup"><span data-stu-id="2e988-157">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="2e988-158">Atrybutu zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="2e988-158">Sdk attribute</span></span>

<span data-ttu-id="2e988-159">Katalog główny `<Project>` elementu *.csproj* plik ma nowy atrybut o nazwie `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="2e988-159">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> `Sdk` <span data-ttu-id="2e988-160">Określa zestaw SDK będzie używane przez projekt.</span><span class="sxs-lookup"><span data-stu-id="2e988-160">specifies which SDK will be used by the project.</span></span> <span data-ttu-id="2e988-161">Zestaw SDK, jako [dokumentu warstwowe](cli-msbuild-architecture.md) opisuje, to zbiór MSBuild [zadania](/visualstudio/msbuild/msbuild-tasks) i [cele](/visualstudio/msbuild/msbuild-targets) , można tworzyć kod platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2e988-161">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="2e988-162">Publikujemy trzech głównych zestawów SDK z narzędziami .NET Core:</span><span class="sxs-lookup"><span data-stu-id="2e988-162">We ship three main SDKs with the .NET Core tools:</span></span>

1. <span data-ttu-id="2e988-163">.NET Core SDK o identyfikatorze</span><span class="sxs-lookup"><span data-stu-id="2e988-163">The .NET Core SDK with the ID of</span></span> `Microsoft.NET.Sdk`
2. <span data-ttu-id="2e988-164">.NET Core web SDK o identyfikatorze</span><span class="sxs-lookup"><span data-stu-id="2e988-164">The .NET Core web SDK with the ID of</span></span> `Microsoft.NET.Sdk.Web`
3. <span data-ttu-id="2e988-165">Biblioteki klas Razor platformy .NET Core SDK z Identyfikatorem programu</span><span class="sxs-lookup"><span data-stu-id="2e988-165">The .NET Core Razor Class Library SDK with the ID of</span></span> `Microsoft.NET.Sdk.Razor`

<span data-ttu-id="2e988-166">Musisz mieć `Sdk` atrybut do jednego z tych identyfikatorów w `<Project>` element, aby użyć narzędzi .NET Core i kompilowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="2e988-166">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="2e988-167">PackageReference</span><span class="sxs-lookup"><span data-stu-id="2e988-167">PackageReference</span></span>

<span data-ttu-id="2e988-168">A `<PackageReference>` określa elementu [zależności NuGet w projekcie](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="2e988-168">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="2e988-169">`Include` Atrybut określa identyfikator pakietu.</span><span class="sxs-lookup"><span data-stu-id="2e988-169">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="2e988-170">Wersja</span><span class="sxs-lookup"><span data-stu-id="2e988-170">Version</span></span>

<span data-ttu-id="2e988-171">Wymagane `Version` atrybut określa numer wersji pakietu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="2e988-171">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="2e988-172">Ten atrybut przestrzega zasad [wersji NuGet](/nuget/reference/package-versioning#version-ranges-and-wildcards) schematu.</span><span class="sxs-lookup"><span data-stu-id="2e988-172">The attribute respects the rules of the [NuGet versioning](/nuget/reference/package-versioning#version-ranges-and-wildcards) scheme.</span></span> <span data-ttu-id="2e988-173">Domyślnym zachowaniem jest dokładna wersja dopasowania.</span><span class="sxs-lookup"><span data-stu-id="2e988-173">The default behavior is an exact version match.</span></span> <span data-ttu-id="2e988-174">Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji NuGet `[1.2.3]` dla 1.2.3 dokładną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="2e988-174">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="2e988-175">IncludeAssets, ExcludeAssets i PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="2e988-175">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>

`IncludeAssets` <span data-ttu-id="2e988-176">atrybut określa, które zasoby należące do pakietu określony przez `<PackageReference>` powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="2e988-176">attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="2e988-177">Domyślnie uwzględniane są wszystkie zasoby pakietu.</span><span class="sxs-lookup"><span data-stu-id="2e988-177">By default, all package assets are included.</span></span>

`ExcludeAssets` <span data-ttu-id="2e988-178">atrybut określa, które zasoby należące do pakietu określony przez `<PackageReference>` nie powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="2e988-178">attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

`PrivateAssets` <span data-ttu-id="2e988-179">atrybut określa, które zasoby należące do pakietu określony przez `<PackageReference>` powinny być używane, ale nie przepływać do następnego projektu.</span><span class="sxs-lookup"><span data-stu-id="2e988-179">attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="2e988-180">`Analyzers`, `Build` i `ContentFiles` zasoby są domyślnie prywatne, gdy ten atrybut nie jest obecny.</span><span class="sxs-lookup"><span data-stu-id="2e988-180">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> `PrivateAssets` <span data-ttu-id="2e988-181">jest odpowiednikiem *project.json*/*xproj* `SuppressParent` elementu.</span><span class="sxs-lookup"><span data-stu-id="2e988-181">is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="2e988-182">Tych atrybutów może zawierać jeden lub więcej z poniższych elementów oddzielonych średnikami `;` znak, jeśli więcej niż jeden znajduje się na liście:</span><span class="sxs-lookup"><span data-stu-id="2e988-182">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

* `Compile` <span data-ttu-id="2e988-183">— zawartość folderu biblioteki są dostępne kompilowanie z użyciem.</span><span class="sxs-lookup"><span data-stu-id="2e988-183">– the contents of the lib folder are available to compile against.</span></span>
* `Runtime` <span data-ttu-id="2e988-184">— zawartość folderu środowiska uruchomieniowego są dystrybuowane.</span><span class="sxs-lookup"><span data-stu-id="2e988-184">– the contents of the runtime folder are distributed.</span></span>
* `ContentFiles` <span data-ttu-id="2e988-185">— zawartość *contentfiles* folderu są używane.</span><span class="sxs-lookup"><span data-stu-id="2e988-185">– the contents of the *contentfiles* folder are used.</span></span>
* `Build` <span data-ttu-id="2e988-186">— właściwości/elementów docelowych, w folderze kompilacji są używane.</span><span class="sxs-lookup"><span data-stu-id="2e988-186">– the props/targets in the build folder are used.</span></span>
* `Native` <span data-ttu-id="2e988-187">— zawartość z zasobów natywnych są kopiowane do folderu wyjściowego dla środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2e988-187">– the contents from native assets are copied to the output folder for runtime.</span></span>
* `Analyzers` <span data-ttu-id="2e988-188">— są używane analizatory.</span><span class="sxs-lookup"><span data-stu-id="2e988-188">– the analyzers are used.</span></span>

<span data-ttu-id="2e988-189">Alternatywnie ten atrybut może zawierać:</span><span class="sxs-lookup"><span data-stu-id="2e988-189">Alternatively, the attribute can contain:</span></span>

* `None` <span data-ttu-id="2e988-190">— zasoby są używane.</span><span class="sxs-lookup"><span data-stu-id="2e988-190">– none of the assets are used.</span></span>
* `All` <span data-ttu-id="2e988-191">— wszystkie zasoby są używane.</span><span class="sxs-lookup"><span data-stu-id="2e988-191">– all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="2e988-192">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="2e988-192">DotNetCliToolReference</span></span>
<span data-ttu-id="2e988-193">Element `<DotNetCliToolReference>` elementu określa narzędzie interfejsu wiersza polecenia, które użytkownik chce przywrócić w kontekście projektu.</span><span class="sxs-lookup"><span data-stu-id="2e988-193">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="2e988-194">Jest zamiennikiem `tools` w węźle *project.json*.</span><span class="sxs-lookup"><span data-stu-id="2e988-194">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="2e988-195">Wersja</span><span class="sxs-lookup"><span data-stu-id="2e988-195">Version</span></span>

`Version` <span data-ttu-id="2e988-196">Określa numer wersji pakietu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="2e988-196">specifies the version of the package to restore.</span></span> <span data-ttu-id="2e988-197">Ten atrybut przestrzega zasad [wersji NuGet](/nuget/create-packages/dependency-versions#version-ranges) schematu.</span><span class="sxs-lookup"><span data-stu-id="2e988-197">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="2e988-198">Domyślnym zachowaniem jest dokładna wersja dopasowania.</span><span class="sxs-lookup"><span data-stu-id="2e988-198">The default behavior is an exact version match.</span></span> <span data-ttu-id="2e988-199">Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji NuGet `[1.2.3]` dla 1.2.3 dokładną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="2e988-199">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="2e988-200">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="2e988-200">RuntimeIdentifiers</span></span>

<span data-ttu-id="2e988-201">`<RuntimeIdentifiers>` Property — element umożliwia określenie rozdzieloną średnikami listę [identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu.</span><span class="sxs-lookup"><span data-stu-id="2e988-201">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="2e988-202">RID włączyć publikowanie niezależne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="2e988-202">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="2e988-203">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="2e988-203">RuntimeIdentifier</span></span>

<span data-ttu-id="2e988-204">`<RuntimeIdentifier>` Element właściwości można określić tylko jeden [identyfikator środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu.</span><span class="sxs-lookup"><span data-stu-id="2e988-204">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="2e988-205">Identyfikator RID umożliwia publikowanie niezależne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="2e988-205">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="2e988-206">Użyj `<RuntimeIdentifiers>` (liczba mnoga) zamiast Jeśli potrzebujesz do opublikowania dla wielu modułów wykonawczych.</span><span class="sxs-lookup"><span data-stu-id="2e988-206">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> `<RuntimeIdentifier>` <span data-ttu-id="2e988-207">zapewnia szybsze kompilacje, gdy tylko jednego środowiska wykonawczego jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="2e988-207">can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="2e988-208">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="2e988-208">PackageTargetFallback</span></span>

<span data-ttu-id="2e988-209">`<PackageTargetFallback>` Element właściwości można określić zestaw zgodnych elementów docelowych do użycia podczas przywracania pakietów.</span><span class="sxs-lookup"><span data-stu-id="2e988-209">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="2e988-210">Został zaprojektowany tak, aby zezwolić na pakiety, które używają dotnet [TxM (krótkiej nazwy docelowej x)](/nuget/schema/target-frameworks) do pracy z pakietami, które nie deklarują dotnet TxM.</span><span class="sxs-lookup"><span data-stu-id="2e988-210">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="2e988-211">Jeśli projekt używa dotnet TxM, a następnie wszystkich pakietów to zależy od musi również mieć dotnet TxM, chyba że dodasz `<PackageTargetFallback>` do swojego projektu, aby umożliwić-dotnet platform zapewnić ich zgodność za pomocą polecenia dotnet.</span><span class="sxs-lookup"><span data-stu-id="2e988-211">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="2e988-212">W poniższym przykładzie przedstawiono przejścia dla wszystkich obiektów docelowych w projekcie:</span><span class="sxs-lookup"><span data-stu-id="2e988-212">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="2e988-213">W poniższym przykładzie określono planów awaryjnych tylko w przypadku `netcoreapp2.1` docelowej:</span><span class="sxs-lookup"><span data-stu-id="2e988-213">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="2e988-214">Właściwości metadanych NuGet</span><span class="sxs-lookup"><span data-stu-id="2e988-214">NuGet metadata properties</span></span>

<span data-ttu-id="2e988-215">Wraz z przejściem do programu MSBuild, przenieśliśmy metadanych wejściowych, który jest używany podczas pakowania pakietów NuGet, od *project.json* do *.csproj* plików.</span><span class="sxs-lookup"><span data-stu-id="2e988-215">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="2e988-216">Dane wejściowe są właściwości programu MSBuild, aby musieli przejść w ramach `<PropertyGroup>` grupy.</span><span class="sxs-lookup"><span data-stu-id="2e988-216">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="2e988-217">Poniżej przedstawiono listę właściwości, które są używane jako dane wejściowe, aby proces pakowania, korzystając z `dotnet pack` polecenia lub `Pack` MSBuild docelowa to znaczy częścią zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="2e988-217">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span>

### <a name="ispackable"></a><span data-ttu-id="2e988-218">IsPackable</span><span class="sxs-lookup"><span data-stu-id="2e988-218">IsPackable</span></span>

<span data-ttu-id="2e988-219">Wartość logiczna określająca, czy można będzie bogatymi w projekcie.</span><span class="sxs-lookup"><span data-stu-id="2e988-219">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="2e988-220">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="2e988-220">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="2e988-221">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="2e988-221">PackageVersion</span></span>

<span data-ttu-id="2e988-222">Określa wersję tego pakietu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="2e988-222">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="2e988-223">Akceptuje wszystkie formularze ciąg wersji NuGet.</span><span class="sxs-lookup"><span data-stu-id="2e988-223">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="2e988-224">Wartością domyślną jest wartość z `$(Version)`, oznacza to, że właściwości `Version` w projekcie.</span><span class="sxs-lookup"><span data-stu-id="2e988-224">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="2e988-225">PackageId</span><span class="sxs-lookup"><span data-stu-id="2e988-225">PackageId</span></span>

<span data-ttu-id="2e988-226">Określa nazwę pakietu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="2e988-226">Specifies the name for the resulting package.</span></span> <span data-ttu-id="2e988-227">Jeśli nie zostanie określony, `pack` operacji będą domyślnie używają `AssemblyName` lub nazwę katalogu jako nazwę pakietu.</span><span class="sxs-lookup"><span data-stu-id="2e988-227">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="2e988-228">Tytuł</span><span class="sxs-lookup"><span data-stu-id="2e988-228">Title</span></span>

<span data-ttu-id="2e988-229">Tytuł przyjaznego dla człowieka pakietu, zwykle używanych w interfejsie użytkownika wyświetla w witrynach nuget.org i Menedżera pakietów w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2e988-229">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="2e988-230">Jeśli nie zostanie określony, identyfikator pakietu jest używana zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="2e988-230">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="2e988-231">Autorzy</span><span class="sxs-lookup"><span data-stu-id="2e988-231">Authors</span></span>

<span data-ttu-id="2e988-232">Rozdzielana średnikami lista autorów pakietów, pasujące nazwy profilu w witrynie nuget.org. Te są wyświetlane w galerii pakietów NuGet w witrynie nuget.org i są odwoływania się do pakietów przez ten sam autorów.</span><span class="sxs-lookup"><span data-stu-id="2e988-232">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="2e988-233">PackageDescription</span><span class="sxs-lookup"><span data-stu-id="2e988-233">PackageDescription</span></span>

<span data-ttu-id="2e988-234">Długi opis pakietu do wyświetlania w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2e988-234">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="2e988-235">Opis</span><span class="sxs-lookup"><span data-stu-id="2e988-235">Description</span></span>

<span data-ttu-id="2e988-236">Długi opis zestawu.</span><span class="sxs-lookup"><span data-stu-id="2e988-236">A long description for the assembly.</span></span> <span data-ttu-id="2e988-237">Jeśli `PackageDescription` nie zostanie określony, a następnie ta właściwość jest również używany jako opis pakietu.</span><span class="sxs-lookup"><span data-stu-id="2e988-237">If `PackageDescription` is not specified then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="2e988-238">Prawa autorskie</span><span class="sxs-lookup"><span data-stu-id="2e988-238">Copyright</span></span>

<span data-ttu-id="2e988-239">Szczegóły dotyczące praw autorskich dla pakietu.</span><span class="sxs-lookup"><span data-stu-id="2e988-239">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="2e988-240">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="2e988-240">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="2e988-241">Wartość logiczna określająca, czy klient musi monitować konsumenta o zaakceptowanie licencji pakietu przed zainstalowaniem pakietu.</span><span class="sxs-lookup"><span data-stu-id="2e988-241">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="2e988-242">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="2e988-242">The default is `false`.</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="2e988-243">PackageLicenseExpression</span><span class="sxs-lookup"><span data-stu-id="2e988-243">PackageLicenseExpression</span></span>

<span data-ttu-id="2e988-244">[Identyfikatora licencji SPDX](https://spdx.org/licenses/) lub wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="2e988-244">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="2e988-245">Na przykład `Apache-2.0`.</span><span class="sxs-lookup"><span data-stu-id="2e988-245">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="2e988-246">Oto Pełna lista [identyfikatory licencji SPDX](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="2e988-246">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="2e988-247">NuGet.org akceptuje tylko OSI lub licencji FSF zatwierdzone, korzystając z licencji wyrażenie typu.</span><span class="sxs-lookup"><span data-stu-id="2e988-247">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="2e988-248">Dokładna składnia wyrażeń licencji jest opisane poniżej w [ABNF](https://tools.ietf.org/html/rfc5234).</span><span class="sxs-lookup"><span data-stu-id="2e988-248">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

```cli
license-id            = <short form license identifier from https://spdx.org/spdx-specification-21-web-version#h.luq9dgcle9mo>

license-exception-id  = <short form license exception identifier from https://spdx.org/spdx-specification-21-web-version#h.ruv3yl8g6czd>

simple-expression = license-id / license-id”+”

compound-expression =  1*1(simple-expression /
                simple-expression "WITH" license-exception-id /
                compound-expression "AND" compound-expression /
                compound-expression "OR" compound-expression ) /
                "(" compound-expression ")" )

license-expression =  1*1(simple-expression / compound-expression / UNLICENSED)
```

> [!NOTE]
> <span data-ttu-id="2e988-249">Tylko jeden z `PackageLicenseExpression`, `PackageLicenseFile` i `PackageLicenseUrl` można określić jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="2e988-249">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="2e988-250">PackageLicenseFile</span><span class="sxs-lookup"><span data-stu-id="2e988-250">PackageLicenseFile</span></span>

<span data-ttu-id="2e988-251">Ścieżka do pliku licencji w ramach pakietu, jeśli używasz licencji, w której nie przypisano identyfikator SPDX lub jest ona niestandardowe licencji (przeciwnym `PackageLicenseExpression` jest preferowana)</span><span class="sxs-lookup"><span data-stu-id="2e988-251">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is prefered)</span></span>

<span data-ttu-id="2e988-252">Zastępuje `PackageLicenseUrl`, nie można połączyć z `PackageLicenseExpression` i wymaga programu Visual Studio 15.9.4, zestaw SDK platformy .NET 2.1.502 lub 2.2.101, lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="2e988-252">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression` and requires Visual Studio 15.9.4, .NET SDK 2.1.502 or 2.2.101, or newer.</span></span>

<span data-ttu-id="2e988-253">Należy upewnić się, że plik licencji jest pakowany, jawnie dodając ją do projektu, na przykład użycia:</span><span class="sxs-lookup"><span data-stu-id="2e988-253">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="2e988-254">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="2e988-254">PackageLicenseUrl</span></span>

<span data-ttu-id="2e988-255">Adres URL licencji, która ma zastosowanie do pakietu.</span><span class="sxs-lookup"><span data-stu-id="2e988-255">An URL to the license that is applicable to the package.</span></span> <span data-ttu-id="2e988-256">(_przestarzały począwszy od programu Visual Studio 15.9.4, zestaw SDK platformy .NET 2.1.502 i 2.2.101_)</span><span class="sxs-lookup"><span data-stu-id="2e988-256">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="2e988-257">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="2e988-257">PackageIconUrl</span></span>

<span data-ttu-id="2e988-258">Adres URL obrazu 64 x 64 z przezroczystym tłem do użycia jako ikona dla pakietu wyświetlania w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2e988-258">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="2e988-259">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="2e988-259">PackageReleaseNotes</span></span>

<span data-ttu-id="2e988-260">Informacje o wersji dla pakietu.</span><span class="sxs-lookup"><span data-stu-id="2e988-260">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="2e988-261">PackageTags</span><span class="sxs-lookup"><span data-stu-id="2e988-261">PackageTags</span></span>

<span data-ttu-id="2e988-262">Rozdzielaną średnikami listę znaczników, który wyznacza pakietu.</span><span class="sxs-lookup"><span data-stu-id="2e988-262">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="2e988-263">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="2e988-263">PackageOutputPath</span></span>

<span data-ttu-id="2e988-264">Określa ścieżkę wyjściową, w którym spakowany pakiet zostanie porzucony.</span><span class="sxs-lookup"><span data-stu-id="2e988-264">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="2e988-265">Wartość domyślna to `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="2e988-265">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="2e988-266">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="2e988-266">IncludeSymbols</span></span>

<span data-ttu-id="2e988-267">Ta wartość logiczna wskazuje, czy pakiet powinien Utwórz pakiet dodatkowych symboli, gdy projekt jest pakowany.</span><span class="sxs-lookup"><span data-stu-id="2e988-267">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="2e988-268">Ten pakiet będzie miał *. symbols.nupkg* rozszerzenia i skopiuje pliki PDB wraz z biblioteki DLL i inne pliki wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="2e988-268">This package will have a *.symbols.nupkg* extension and will copy the PDB files along with the DLL and other output files.</span></span>

### <a name="includesource"></a><span data-ttu-id="2e988-269">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="2e988-269">IncludeSource</span></span>

<span data-ttu-id="2e988-270">Ta wartość logiczna wskazuje, czy Proces pakietu należy utworzyć pakiet "source".</span><span class="sxs-lookup"><span data-stu-id="2e988-270">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="2e988-271">Źródłowy pakiet zawiera biblioteki kodu źródłowego oraz pliki PDB.</span><span class="sxs-lookup"><span data-stu-id="2e988-271">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="2e988-272">Pliki źródłowe są umieszczane w `src/ProjectName` katalogu w powstałym pliku pakietu.</span><span class="sxs-lookup"><span data-stu-id="2e988-272">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="2e988-273">IsTool</span><span class="sxs-lookup"><span data-stu-id="2e988-273">IsTool</span></span>

<span data-ttu-id="2e988-274">Określa, czy wszystkie pliki wyjściowe są kopiowane do *narzędzia* folderu zamiast *lib* folderu.</span><span class="sxs-lookup"><span data-stu-id="2e988-274">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="2e988-275">Należy pamiętać, że to różni się od `DotNetCliTool` określić, ustawiając `PackageType` w *.csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="2e988-275">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="2e988-276">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="2e988-276">RepositoryUrl</span></span>

<span data-ttu-id="2e988-277">Określa adres URL repozytorium, gdzie znajduje się kod źródłowy dla pakietu i/lub z którego jest ona kompilowana.</span><span class="sxs-lookup"><span data-stu-id="2e988-277">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="2e988-278">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="2e988-278">RepositoryType</span></span>

<span data-ttu-id="2e988-279">Określa typ repozytorium.</span><span class="sxs-lookup"><span data-stu-id="2e988-279">Specifies the type of the repository.</span></span> <span data-ttu-id="2e988-280">Wartością domyślną jest "git".</span><span class="sxs-lookup"><span data-stu-id="2e988-280">Default is "git".</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="2e988-281">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="2e988-281">NoPackageAnalysis</span></span>

<span data-ttu-id="2e988-282">Określa, że pakiet nie należy uruchamiać analizy pakietu po utworzeniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="2e988-282">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="2e988-283">MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="2e988-283">MinClientVersion</span></span>

<span data-ttu-id="2e988-284">Określa minimalną wersję klienta NuGet, który można zainstalować ten pakiet, wymuszane przez nuget.exe oraz Menedżera pakietów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2e988-284">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="2e988-285">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="2e988-285">IncludeBuildOutput</span></span>

<span data-ttu-id="2e988-286">Tej wartości logicznych Określa, czy zestawy danych wyjściowych kompilacji powinien pakowane w *.nupkg* plików lub nie.</span><span class="sxs-lookup"><span data-stu-id="2e988-286">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="2e988-287">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="2e988-287">IncludeContentInPack</span></span>

<span data-ttu-id="2e988-288">Ta wartość logiczna określa, czy wszystkie elementy, mają typ `Content` zostanie automatycznie dołączony do pakietu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="2e988-288">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="2e988-289">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="2e988-289">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="2e988-290">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="2e988-290">BuildOutputTargetFolder</span></span>

<span data-ttu-id="2e988-291">Określa folder, gdzie umieścić zestawy danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="2e988-291">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="2e988-292">Zestawy danych wyjściowych (i inne pliki wyjściowe) są kopiowane do ich odpowiednich ramach folderów.</span><span class="sxs-lookup"><span data-stu-id="2e988-292">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="2e988-293">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="2e988-293">ContentTargetFolders</span></span>

<span data-ttu-id="2e988-294">Ta właściwość określa domyślną lokalizację kogo powinno zwrócić wszystkie pliki zawartości, gdy `PackagePath` nie określono dla nich.</span><span class="sxs-lookup"><span data-stu-id="2e988-294">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="2e988-295">Wartość domyślna to "zawartość; pliki".</span><span class="sxs-lookup"><span data-stu-id="2e988-295">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="2e988-296">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="2e988-296">NuspecFile</span></span>

<span data-ttu-id="2e988-297">Względna lub bezwzględna ścieżka do *.nuspec* plików używanych na potrzeby pakowania.</span><span class="sxs-lookup"><span data-stu-id="2e988-297">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="2e988-298">Jeśli *.nuspec* pliku jest określona, jest on używany **wyłącznie** pakowanie informacji i wszelkie informacje zawarte w projektów nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="2e988-298">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="2e988-299">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="2e988-299">NuspecBasePath</span></span>

<span data-ttu-id="2e988-300">Podstawową ścieżkę dla *.nuspec* pliku.</span><span class="sxs-lookup"><span data-stu-id="2e988-300">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="2e988-301">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="2e988-301">NuspecProperties</span></span>

<span data-ttu-id="2e988-302">Rozdzielana średnikami lista klucz = wartość pary.</span><span class="sxs-lookup"><span data-stu-id="2e988-302">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="2e988-303">Właściwości AssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="2e988-303">AssemblyInfo properties</span></span>

<span data-ttu-id="2e988-304">[Atrybuty zestawu](../../framework/app-domains/set-assembly-attributes.md) , które były w *AssemblyInfo* pliku są teraz automatycznie generowane na podstawie właściwości.</span><span class="sxs-lookup"><span data-stu-id="2e988-304">[Assembly attributes](../../framework/app-domains/set-assembly-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="2e988-305">Właściwości dla atrybutu</span><span class="sxs-lookup"><span data-stu-id="2e988-305">Properties per attribute</span></span>

<span data-ttu-id="2e988-306">Każdy atrybut ma właściwości, które sterują jej zawartość i innej, aby wyłączyć jej generacji, jak pokazano w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="2e988-306">Each attribute has a property that control its content and another to disable its generation as shown in the following table:</span></span>

| <span data-ttu-id="2e988-307">Atrybut</span><span class="sxs-lookup"><span data-stu-id="2e988-307">Attribute</span></span>                                                      | <span data-ttu-id="2e988-308">Właściwość</span><span class="sxs-lookup"><span data-stu-id="2e988-308">Property</span></span>               | <span data-ttu-id="2e988-309">Właściwość, która wyłącza</span><span class="sxs-lookup"><span data-stu-id="2e988-309">Property to disable</span></span>                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

<span data-ttu-id="2e988-310">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="2e988-310">Notes:</span></span>

* `AssemblyVersion` <span data-ttu-id="2e988-311">i `FileVersion` domyślny ma wartość `$(Version)` bez sufiksu.</span><span class="sxs-lookup"><span data-stu-id="2e988-311">and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="2e988-312">Na przykład jeśli `$(Version)` jest `1.2.3-beta.4`, a następnie wartość będzie wynosić `1.2.3`.</span><span class="sxs-lookup"><span data-stu-id="2e988-312">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
* `InformationalVersion` <span data-ttu-id="2e988-313">Wartością domyślną jest wartość `$(Version)`.</span><span class="sxs-lookup"><span data-stu-id="2e988-313">defaults to the value of `$(Version)`.</span></span>
* `InformationalVersion` <span data-ttu-id="2e988-314">ma `$(SourceRevisionId)` dołączona, jeśli właściwość jest obecny.</span><span class="sxs-lookup"><span data-stu-id="2e988-314">has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="2e988-315">Można je wyłączyć, używając `IncludeSourceRevisionInInformationalVersion`.</span><span class="sxs-lookup"><span data-stu-id="2e988-315">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
* `Copyright` <span data-ttu-id="2e988-316">i `Description` właściwości są używane również do metadanych NuGet.</span><span class="sxs-lookup"><span data-stu-id="2e988-316">and `Description` properties are also used for NuGet metadata.</span></span>
* `Configuration` <span data-ttu-id="2e988-317">jest współużytkowany z procesu kompilacji i ustawić za pomocą `--configuration` parametru `dotnet` poleceń.</span><span class="sxs-lookup"><span data-stu-id="2e988-317">is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="2e988-318">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="2e988-318">GenerateAssemblyInfo</span></span>

<span data-ttu-id="2e988-319">Wartość logiczna, która włącza lub wyłącza Generowanie AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="2e988-319">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="2e988-320">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="2e988-320">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="2e988-321">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="2e988-321">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="2e988-322">Ścieżka pliku z informacjami wygenerowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="2e988-322">The path of the generated assembly info file.</span></span> <span data-ttu-id="2e988-323">Domyślnie plik w `$(IntermediateOutputPath)` katalogu (obj).</span><span class="sxs-lookup"><span data-stu-id="2e988-323">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
