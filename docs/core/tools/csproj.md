---
title: Dodatki do formatu csproj dla platformy .NET Core
description: Więcej informacji na temat różnic między istniejących i pliki csproj .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 09/22/2017
ms.openlocfilehash: 1e356d0123328fe703f672c38cb5ee7799cb574c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218235"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="278fa-103">Dodatki do formatu csproj dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="278fa-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="278fa-104">W tym dokumencie przedstawiono zmiany, które zostały dodane do plików projektu jako część przejście od *project.json* do *csproj* i [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="278fa-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="278fa-105">Aby uzyskać więcej informacji o składni pliku ogólnego projektu i odwołania, zobacz [pliku projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="278fa-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>  

## <a name="implicit-package-references"></a><span data-ttu-id="278fa-106">Odwołania do pakietu niejawne</span><span class="sxs-lookup"><span data-stu-id="278fa-106">Implicit package references</span></span>
<span data-ttu-id="278fa-107">Metapackages są niejawne odwołania w oparciu framework(s) docelowych określonych w `<TargetFramework>` lub `<TargetFrameworks>` właściwości pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="278fa-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="278fa-108">`<TargetFrameworks>` jest ignorowana, jeśli `<TargetFramework>` jest określony, niezależnie od kolejności.</span><span class="sxs-lookup"><span data-stu-id="278fa-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp1.1</TargetFramework>
 </PropertyGroup>
 ```
 
 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp1.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a><span data-ttu-id="278fa-109">Zalecenia</span><span class="sxs-lookup"><span data-stu-id="278fa-109">Recommendations</span></span>
<span data-ttu-id="278fa-110">Ponieważ `Microsoft.NETCore.App` lub `NetStandard.Library` metapackages niejawne są odwołania, Oto nasze najlepsze rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="278fa-110">Since `Microsoft.NETCore.App` or `NetStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="278fa-111">Jeśli oprogramowanie .NET Core lub .NET Standard, nigdy nie ma jawnego odwołania do `Microsoft.NETCore.App` lub `NetStandard.Library` metapackages za pośrednictwem `<PackageReference>` elementu w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="278fa-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NetStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="278fa-112">Jeśli potrzebujesz określonej wersji środowiska uruchomieniowego podczas określania wartości docelowej platformy .NET Core, należy użyć `<RuntimeFrameworkVersion>` właściwości projektu (na przykład `1.0.4`) zamiast odwołania do metapackage.</span><span class="sxs-lookup"><span data-stu-id="278fa-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
    * <span data-ttu-id="278fa-113">Taka sytuacja może wystąpić, jeśli używasz [niezależne wdrożeń](../deploying/index.md#self-contained-deployments-scd) i wymagają poprawek określonych wersji 1.0.0 środowiska uruchomieniowego LTS, na przykład.</span><span class="sxs-lookup"><span data-stu-id="278fa-113">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="278fa-114">Jeśli potrzebujesz określonej wersji `NetStandard.Library` metapackage podczas określania wartości docelowej platformy .NET Standard, można użyć `<NetStandardImplicitPackageVersion>` właściwości i ustaw wersję.</span><span class="sxs-lookup"><span data-stu-id="278fa-114">If you need a specific version of the `NetStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="278fa-115">Nie jawnie dodać lub zaktualizować odwołania do albo `Microsoft.NETCore.App` lub `NetStandard.Library` metapackage w projektach platformy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="278fa-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NetStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="278fa-116">Jeśli jakakolwiek wersja `NetStandard.Library` potrzebne w przypadku, gdy przy użyciu pakietu NuGet .NET Standard na podstawie, NuGet automatycznie instaluje tę wersję.</span><span class="sxs-lookup"><span data-stu-id="278fa-116">If any version of `NetStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="278fa-117">Zawiera domyślne kompilacji w projektach platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="278fa-117">Default compilation includes in .NET Core projects</span></span>
<span data-ttu-id="278fa-118">Wraz z przejściem do *csproj* format w najnowszej wersji zestawu SDK, Przeprowadziliśmy domyślna obejmuje i wyklucza elementów kompilacji i zasoby osadzone w plikach właściwości zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="278fa-118">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="278fa-119">Oznacza to, że nie należy określić te elementy w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="278fa-119">This means that you no longer need to specify these items in your project file.</span></span> 

<span data-ttu-id="278fa-120">Głównym celem tej czynności jest aby zwiększyć czytelność w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="278fa-120">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="278fa-121">Wartości domyślne, które znajdują się w zestawie SDK obejmuje najbardziej typowe przypadki użycia, więc nie trzeba powtórzyć je w każdym projekcie, który utworzono.</span><span class="sxs-lookup"><span data-stu-id="278fa-121">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="278fa-122">Prowadzi to do mniejsze pliki projektu, które są znacznie łatwiejsze do zrozumienia, jak również edytować ręcznie, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="278fa-122">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span> 

<span data-ttu-id="278fa-123">W poniższej tabeli przedstawiono, który element i które [globs](https://en.wikipedia.org/wiki/Glob_(programming)) zarówno uwzględniać i wykluczone w zestawie SDK:</span><span class="sxs-lookup"><span data-stu-id="278fa-123">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span> 

| <span data-ttu-id="278fa-124">Element</span><span class="sxs-lookup"><span data-stu-id="278fa-124">Element</span></span>           | <span data-ttu-id="278fa-125">Obejmują glob</span><span class="sxs-lookup"><span data-stu-id="278fa-125">Include glob</span></span>                              | <span data-ttu-id="278fa-126">Wyklucz glob</span><span class="sxs-lookup"><span data-stu-id="278fa-126">Exclude glob</span></span>                                                  | <span data-ttu-id="278fa-127">Usuń glob</span><span class="sxs-lookup"><span data-stu-id="278fa-127">Remove glob</span></span>                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="278fa-128">Kompilacji</span><span class="sxs-lookup"><span data-stu-id="278fa-128">Compile</span></span>           | <span data-ttu-id="278fa-129">\*\*/\*.cs (lub inne rozszerzenia językowe)</span><span class="sxs-lookup"><span data-stu-id="278fa-129">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="278fa-130">\*\*/\*.user;  \*\*/\*.\* Proj;  \* \* / \*.sln;  \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="278fa-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="278fa-131">Brak</span><span class="sxs-lookup"><span data-stu-id="278fa-131">N/A</span></span>                        |
| <span data-ttu-id="278fa-132">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="278fa-132">EmbeddedResource</span></span>  | <span data-ttu-id="278fa-133">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="278fa-133">\*\*/\*.resx</span></span>                              | <span data-ttu-id="278fa-134">\*\*/\*.user; \*\*/\*.\* Proj; \* \* / \*.sln; \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="278fa-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="278fa-135">Brak</span><span class="sxs-lookup"><span data-stu-id="278fa-135">N/A</span></span>                        |
| <span data-ttu-id="278fa-136">Brak</span><span class="sxs-lookup"><span data-stu-id="278fa-136">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="278fa-137">\*\*/\*.user; \*\*/\*.\* Proj; \* \* / \*.sln; \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="278fa-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="278fa-138">- \*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="278fa-138">- \*\*/\*.cs; \*\*/\*.resx</span></span> |

<span data-ttu-id="278fa-139">Jeśli masz globs w projekcie i zostanie podjęta próba skompiluj go przy użyciu najnowszego zestawu SDK, zostanie wyświetlony następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="278fa-139">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="278fa-140">Zduplikowane elementy kompilacji nie został dołączony.</span><span class="sxs-lookup"><span data-stu-id="278fa-140">Duplicate Compile items were included.</span></span> <span data-ttu-id="278fa-141">Domyślnie zestawu .NET SDK zawiera elementy kompilacji z katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="278fa-141">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="278fa-142">Możesz usunąć te elementy z pliku projektu lub ustaw właściwość "EnableDefaultCompileItems" na "fałsz", aby jawnie umieszczone w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="278fa-142">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span> 

<span data-ttu-id="278fa-143">Aby uzyskać uniknąć tego błędu, można usunąć jawnych `Compile` elementy, które są zgodne z typami wymienione w powyższej tabeli, lub możesz ustawić `<EnableDefaultCompileItems>` właściwości `false`, podobnie do następującej:</span><span class="sxs-lookup"><span data-stu-id="278fa-143">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
<span data-ttu-id="278fa-144">Ustawienie tej właściwości na `false` spowoduje zastąpienie niejawnego dołączania i zachowanie zostanie przywrócona do poprzedniego zestawów SDK, który wymagał Określ globs domyślne w projekcie.</span><span class="sxs-lookup"><span data-stu-id="278fa-144">Setting this property to `false` will override implicit inclusion and the behavior will revert back to the previous SDKs where you had to specify the default globs in your project.</span></span> 

<span data-ttu-id="278fa-145">Ta zmiana nie modyfikuje głównym obejmuje mechanika innych.</span><span class="sxs-lookup"><span data-stu-id="278fa-145">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="278fa-146">Jednak jeśli chcesz określić, na przykład niektóre pliki do opublikowany z aplikacji, nadal można znane mechanizmów w *csproj* tego (na przykład `<Content>` elementu).</span><span class="sxs-lookup"><span data-stu-id="278fa-146">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="278fa-147">`<EnableDefaultCompileItems>` powoduje wyłączenie `Compile` globs, ale nie ma wpływu na inne globs, takich jak niejawne `None` glob, które mają zastosowanie również do \*.cs elementów.</span><span class="sxs-lookup"><span data-stu-id="278fa-147">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="278fa-148">Z tego powodu **Eksploratora rozwiązań** będzie Pokaż \*elementów .cs w ramach projektu, zawarty jako `None` elementów.</span><span class="sxs-lookup"><span data-stu-id="278fa-148">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="278fa-149">W podobny sposób można użyć `<EnableDefaultNoneItems>` wyłączyć niejawne `None` glob.</span><span class="sxs-lookup"><span data-stu-id="278fa-149">In a similar way, you can use `<EnableDefaultNoneItems>` to disable the implicit `None` glob.</span></span>

<span data-ttu-id="278fa-150">Aby wyłączyć **wszystkie niejawne globs**, można ustawić `<EnableDefaultItems>` właściwości `false` jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="278fa-150">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="recommendation"></a><span data-ttu-id="278fa-151">Zalecenia</span><span class="sxs-lookup"><span data-stu-id="278fa-151">Recommendation</span></span>
<span data-ttu-id="278fa-152">Z csproj zaleca się, usuń domyślne globs z projektu i dodawać tylko ścieżki plików z globs tych artefaktów potrzebnych aplikacji/biblioteki dla różnych scenariuszy (na przykład środowiska uruchomieniowego i tworzenia pakietów NuGet).</span><span class="sxs-lookup"><span data-stu-id="278fa-152">With csproj, we recommend that you remove the default globs from your project and only add file paths with globs for those artifacts that your app/library needs for various scenarios (for example, runtime and NuGet packaging).</span></span>

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="278fa-153">Jak wyświetlać całego projektu MSBuild widzi ona</span><span class="sxs-lookup"><span data-stu-id="278fa-153">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="278fa-154">Podczas zmiany csproj znacznego uproszczenia pliki projektu, można zobaczyć rozwinięty projektu MSBuild go widzi, gdy zestaw SDK i obiekty docelowe są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="278fa-154">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="278fa-155">Przetwarzanie wstępne projektu z [ `/pp` przełącznika](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) z [ `dotnet msbuild` ](dotnet-msbuild.md) polecenia, która zawiera pliki, które zostaną zaimportowane, ich źródła, a ich wkład do kompilacji bez rzeczywistego Tworzenie projektu:</span><span class="sxs-lookup"><span data-stu-id="278fa-155">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild /pp:fullproject.xml`

<span data-ttu-id="278fa-156">Jeśli projekt zawiera wiele platform docelowych, wyniki polecenia powinna zostać zwrócona na tylko jeden z nich, określając jako właściwość MSBuild:</span><span class="sxs-lookup"><span data-stu-id="278fa-156">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild /p:TargetFramework=netcoreapp2.0 /pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="278fa-157">Dodatki</span><span class="sxs-lookup"><span data-stu-id="278fa-157">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="278fa-158">Atrybut zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="278fa-158">Sdk attribute</span></span> 
<span data-ttu-id="278fa-159">`<Project>` Elementu *.csproj* plik ma nowy atrybut o nazwie `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="278fa-159">The `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="278fa-160">`Sdk` Określa, która zestawu SDK będą używane przez projekt.</span><span class="sxs-lookup"><span data-stu-id="278fa-160">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="278fa-161">Zestaw SDK, jako [dokumentu Tworzenie warstw](cli-msbuild-architecture.md) opisuje, to zbiór MSBuild [zadania](/visualstudio/msbuild/msbuild-tasks) i [cele](/visualstudio/msbuild/msbuild-targets) który kompilacji kodu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="278fa-161">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="278fa-162">Możemy wysłać dwóch głównych zestawów SDK przy użyciu narzędzi platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="278fa-162">We ship two main SDKs with the .NET Core tools:</span></span>

1. <span data-ttu-id="278fa-163">.NET Core SDK o identyfikatorze `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="278fa-163">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="278fa-164">Zestaw SDK o identyfikatorze sieci web .NET Core `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="278fa-164">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>

<span data-ttu-id="278fa-165">Musisz mieć `Sdk` atrybutu zestawu do jednego z tych identyfikatorów `<Project>` element, aby można było używać narzędzi platformy .NET Core i kompilacji kodu.</span><span class="sxs-lookup"><span data-stu-id="278fa-165">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span> 

### <a name="packagereference"></a><span data-ttu-id="278fa-166">PackageReference</span><span class="sxs-lookup"><span data-stu-id="278fa-166">PackageReference</span></span>
<span data-ttu-id="278fa-167">Element, który określa zależności NuGet w projekcie.</span><span class="sxs-lookup"><span data-stu-id="278fa-167">Item that specifies a NuGet dependency in the project.</span></span> <span data-ttu-id="278fa-168">`Include` Atrybut określa identyfikator pakietu.</span><span class="sxs-lookup"><span data-stu-id="278fa-168">The `Include` attribute specifies the package ID.</span></span> 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="278fa-169">Wersja</span><span class="sxs-lookup"><span data-stu-id="278fa-169">Version</span></span>
<span data-ttu-id="278fa-170">`Version` Określa wersję pakietu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="278fa-170">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="278fa-171">Atrybut przestrzega zasad [wersji NuGet](/nuget/create-packages/dependency-versions#version-ranges) schematu.</span><span class="sxs-lookup"><span data-stu-id="278fa-171">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="278fa-172">Domyślnym zachowaniem jest dopasowanie dokładnej wersji.</span><span class="sxs-lookup"><span data-stu-id="278fa-172">The default behavior is an exact version match.</span></span> <span data-ttu-id="278fa-173">Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji NuGet `[1.2.3]` dla 1.2.3 dokładną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="278fa-173">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="278fa-174">IncludeAssets, ExcludeAssets i PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="278fa-174">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>
<span data-ttu-id="278fa-175">`IncludeAssets` atrybut określa zasoby należące do pakietu określony przez `<PackageReference>` powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="278fa-175">`IncludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> 

<span data-ttu-id="278fa-176">`ExcludeAssets` atrybut określa zasoby należące do pakietu określony przez `<PackageReference>` nie powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="278fa-176">`ExcludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="278fa-177">`PrivateAssets` atrybut określa zasoby należące do pakietu określony przez `<PackageReference>` powinny być używane, ale ten powinien przechodzi do następnego projektu.</span><span class="sxs-lookup"><span data-stu-id="278fa-177">`PrivateAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed but that they should not flow to the next project.</span></span> 

> [!NOTE]
> <span data-ttu-id="278fa-178">`PrivateAssets` jest odpowiednikiem *project.json*/*xproj* `SuppressParent` elementu.</span><span class="sxs-lookup"><span data-stu-id="278fa-178">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="278fa-179">Te atrybuty może zawierać jeden lub więcej z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="278fa-179">These attributes can contain one or more of the following items:</span></span>

* <span data-ttu-id="278fa-180">`Compile` — zawartość folderu lib są dostępne do skompilowania przed.</span><span class="sxs-lookup"><span data-stu-id="278fa-180">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="278fa-181">`Runtime` — są dystrybuowane zawartość folderu środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="278fa-181">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="278fa-182">`ContentFiles` — zawartość *pliki* folderu są używane.</span><span class="sxs-lookup"><span data-stu-id="278fa-182">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="278fa-183">`Build` — właściwości/cele w folderze kompilacji są używane.</span><span class="sxs-lookup"><span data-stu-id="278fa-183">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="278fa-184">`Native` — zawartość z zasobów natywnych są kopiowane do folderu wyjściowego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="278fa-184">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="278fa-185">`Analyzers` — analizatorów są używane.</span><span class="sxs-lookup"><span data-stu-id="278fa-185">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="278fa-186">Alternatywnie może zawierać atrybutu:</span><span class="sxs-lookup"><span data-stu-id="278fa-186">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="278fa-187">`None` — nie zasoby zostały użyte.</span><span class="sxs-lookup"><span data-stu-id="278fa-187">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="278fa-188">`All` — wszystkie zasoby są używane.</span><span class="sxs-lookup"><span data-stu-id="278fa-188">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="278fa-189">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="278fa-189">DotNetCliToolReference</span></span>
<span data-ttu-id="278fa-190">`<DotNetCliToolReference>` element elementu określa narzędzie interfejsu wiersza polecenia, które użytkownik chce przywrócić w kontekście projektu.</span><span class="sxs-lookup"><span data-stu-id="278fa-190">`<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="278fa-191">Nie zastępuje `tools` w węźle *project.json*.</span><span class="sxs-lookup"><span data-stu-id="278fa-191">It's a replacement for the `tools` node in *project.json*.</span></span> 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="278fa-192">Wersja</span><span class="sxs-lookup"><span data-stu-id="278fa-192">Version</span></span>
<span data-ttu-id="278fa-193">`Version` Określa wersję pakietu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="278fa-193">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="278fa-194">Atrybut przestrzega zasad [wersji NuGet](/nuget/create-packages/dependency-versions#version-ranges) schematu.</span><span class="sxs-lookup"><span data-stu-id="278fa-194">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="278fa-195">Domyślnym zachowaniem jest dopasowanie dokładnej wersji.</span><span class="sxs-lookup"><span data-stu-id="278fa-195">The default behavior is an exact version match.</span></span> <span data-ttu-id="278fa-196">Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji NuGet `[1.2.3]` dla 1.2.3 dokładną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="278fa-196">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="278fa-197">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="278fa-197">RuntimeIdentifiers</span></span>
<span data-ttu-id="278fa-198">`<RuntimeIdentifiers>` Element umożliwia określenie Rozdzielana średnikami lista [identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu.</span><span class="sxs-lookup"><span data-stu-id="278fa-198">The `<RuntimeIdentifiers>` element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="278fa-199">Włącz RID publikowania niezależne wdrożeń.</span><span class="sxs-lookup"><span data-stu-id="278fa-199">RIDs enable publishing a self-contained deployments.</span></span> 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="278fa-200">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="278fa-200">RuntimeIdentifier</span></span>
<span data-ttu-id="278fa-201">`<RuntimeIdentifier>` Elementu można określić tylko jeden [identyfikatora środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu.</span><span class="sxs-lookup"><span data-stu-id="278fa-201">The `<RuntimeIdentifier>` element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="278fa-202">Włącz RID publikowania niezależne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="278fa-202">RIDs enable publishing a self-contained deployment.</span></span> 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a><span data-ttu-id="278fa-203">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="278fa-203">PackageTargetFallback</span></span> 
<span data-ttu-id="278fa-204">`<PackageTargetFallback>` Element służy do określenia zestawu zgodne cele, które mają być użyte podczas przywracania pakietów.</span><span class="sxs-lookup"><span data-stu-id="278fa-204">The `<PackageTargetFallback>` element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="278fa-205">Został zaprojektowany tak, aby umożliwić pakiety, które używają dotnet [TxM (Moniker docelowej x)](/nuget/schema/target-frameworks) do pracy z pakietami, które nie deklaruje dotnet TxM.</span><span class="sxs-lookup"><span data-stu-id="278fa-205">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="278fa-206">Jeśli projekt używa dotnet TxM, a następnie wszystkie pakiety zależy on od musi również mieć dotnet TxM, chyba że dodasz `<PackageTargetFallback>` do projektu, aby umożliwić platformy dotnet z systemem innym niż był zgodny z dotnet.</span><span class="sxs-lookup"><span data-stu-id="278fa-206">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span> 

<span data-ttu-id="278fa-207">W poniższym przykładzie przedstawiono przejścia dla wszystkich obiektów docelowych w projekcie:</span><span class="sxs-lookup"><span data-stu-id="278fa-207">The following example provides the fallbacks for all targets in your project:</span></span> 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="278fa-208">W poniższym przykładzie przejścia tylko w przypadku `netcoreapp1.0` docelowych:</span><span class="sxs-lookup"><span data-stu-id="278fa-208">The following example specifies the fallbacks only for the `netcoreapp1.0` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp1.0'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="278fa-209">Właściwości metadanych NuGet</span><span class="sxs-lookup"><span data-stu-id="278fa-209">NuGet metadata properties</span></span>
<span data-ttu-id="278fa-210">Wraz z przejściem do MSbuild został przeniesiony wejściowych metadanych, które jest używany podczas pakowania pakietu NuGet z *project.json* do *.csproj* plików.</span><span class="sxs-lookup"><span data-stu-id="278fa-210">With the move to MSbuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="278fa-211">Dane wejściowe są właściwości programu MSBuild, więc Przejdź w `<PropertyGroup>` grupy.</span><span class="sxs-lookup"><span data-stu-id="278fa-211">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="278fa-212">Poniżej przedstawiono listę właściwości, które są używane jako dane wejściowe do procesu pakowania, korzystając z `dotnet pack` polecenia lub `Pack` MSBuild będący celem część zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="278fa-212">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span> 

### <a name="ispackable"></a><span data-ttu-id="278fa-213">IsPackable</span><span class="sxs-lookup"><span data-stu-id="278fa-213">IsPackable</span></span>
<span data-ttu-id="278fa-214">Wartość logiczna określająca, czy można zapakować projektu.</span><span class="sxs-lookup"><span data-stu-id="278fa-214">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="278fa-215">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="278fa-215">The default value is `true`.</span></span> 

### <a name="packageversion"></a><span data-ttu-id="278fa-216">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="278fa-216">PackageVersion</span></span>
<span data-ttu-id="278fa-217">Określa wersję mające wynikowy pakiet.</span><span class="sxs-lookup"><span data-stu-id="278fa-217">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="278fa-218">Akceptuje wszystkie formularze ciąg wersji NuGet.</span><span class="sxs-lookup"><span data-stu-id="278fa-218">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="278fa-219">Domyślnie jest wartość `$(Version)`, która jest właściwości `Version` w projekcie.</span><span class="sxs-lookup"><span data-stu-id="278fa-219">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span> 

### <a name="packageid"></a><span data-ttu-id="278fa-220">PackageId</span><span class="sxs-lookup"><span data-stu-id="278fa-220">PackageId</span></span>
<span data-ttu-id="278fa-221">Określa nazwę pakietu wynikowy.</span><span class="sxs-lookup"><span data-stu-id="278fa-221">Specifies the name for the resulting package.</span></span> <span data-ttu-id="278fa-222">Jeśli nie zostanie określony, `pack` operacji domyślnie zostanie ustawiona przy użyciu `AssemblyName` lub nazwa katalogu jako nazwę pakietu.</span><span class="sxs-lookup"><span data-stu-id="278fa-222">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span> 

### <a name="title"></a><span data-ttu-id="278fa-223">Tytuł</span><span class="sxs-lookup"><span data-stu-id="278fa-223">Title</span></span>
<span data-ttu-id="278fa-224">Tytuł przyjaznych dla człowieka pakietu, zwykle używanych w wyświetla interfejsu użytkownika na nuget.org i Menedżera pakietów w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="278fa-224">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="278fa-225">Jeśli nie zostanie określony, zamiast niego jest używana identyfikator pakietu.</span><span class="sxs-lookup"><span data-stu-id="278fa-225">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="278fa-226">Autorzy</span><span class="sxs-lookup"><span data-stu-id="278fa-226">Authors</span></span>
<span data-ttu-id="278fa-227">Rozdzielana średnikami lista autorzy pakietów, zgodne z nazwami profilu na nuget.org. Te są wyświetlane w galerii NuGet w nuget.org i są odwoływania się do pakietów przez tego samego autorów.</span><span class="sxs-lookup"><span data-stu-id="278fa-227">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="description"></a><span data-ttu-id="278fa-228">Opis</span><span class="sxs-lookup"><span data-stu-id="278fa-228">Description</span></span>
<span data-ttu-id="278fa-229">Długi opis pakietu do wyświetlenia interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="278fa-229">A long description of the package for UI display.</span></span>

### <a name="copyright"></a><span data-ttu-id="278fa-230">Prawa autorskie</span><span class="sxs-lookup"><span data-stu-id="278fa-230">Copyright</span></span>
<span data-ttu-id="278fa-231">Praw autorskich szczegóły pakietu.</span><span class="sxs-lookup"><span data-stu-id="278fa-231">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="278fa-232">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="278fa-232">PackageRequireLicenseAcceptance</span></span>
<span data-ttu-id="278fa-233">Wartość logiczna określająca, czy klient musi monitować o konsumenta, aby zaakceptować licencji pakietu przed zainstalowaniem pakietu.</span><span class="sxs-lookup"><span data-stu-id="278fa-233">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="278fa-234">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="278fa-234">The default is `false`.</span></span>

### <a name="packagelicenseurl"></a><span data-ttu-id="278fa-235">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="278fa-235">PackageLicenseUrl</span></span>
<span data-ttu-id="278fa-236">Adres URL licencji, która ma zastosowanie do pakietu.</span><span class="sxs-lookup"><span data-stu-id="278fa-236">An URL to the license that is applicable to the package.</span></span>

### <a name="packageprojecturl"></a><span data-ttu-id="278fa-237">PackageProjectUrl</span><span class="sxs-lookup"><span data-stu-id="278fa-237">PackageProjectUrl</span></span>
<span data-ttu-id="278fa-238">Wyświetla adres URL strony głównej pakietu, często są wyświetlane w interfejsie użytkownika oraz nuget.org.</span><span class="sxs-lookup"><span data-stu-id="278fa-238">A URL for the package's home page, often shown in UI displays as well as nuget.org.</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="278fa-239">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="278fa-239">PackageIconUrl</span></span>
<span data-ttu-id="278fa-240">Adres URL obrazu 64 x 64 z przezroczyste tło do użycia jako ikonę pakietu w wyświetlania interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="278fa-240">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="278fa-241">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="278fa-241">PackageReleaseNotes</span></span>
<span data-ttu-id="278fa-242">Informacje o wersji dla pakietu.</span><span class="sxs-lookup"><span data-stu-id="278fa-242">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="278fa-243">PackageTags</span><span class="sxs-lookup"><span data-stu-id="278fa-243">PackageTags</span></span>
<span data-ttu-id="278fa-244">Rozdzielaną średnikami listę znaczników, który wyznacza pakietu.</span><span class="sxs-lookup"><span data-stu-id="278fa-244">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="278fa-245">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="278fa-245">PackageOutputPath</span></span>
<span data-ttu-id="278fa-246">Określa ścieżki wyjściowej, w którym spakowany pakiet zostanie porzucony.</span><span class="sxs-lookup"><span data-stu-id="278fa-246">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="278fa-247">Wartość domyślna to `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="278fa-247">Default is `$(OutputPath)`.</span></span> 

### <a name="includesymbols"></a><span data-ttu-id="278fa-248">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="278fa-248">IncludeSymbols</span></span>
<span data-ttu-id="278fa-249">Ta wartość logiczna wskazuje, czy pakiet należy utworzyć pakiet symboli dodatkowych podczas spakowane projektu.</span><span class="sxs-lookup"><span data-stu-id="278fa-249">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="278fa-250">Ten pakiet będzie mieć *. symbols.nupkg* rozszerzenia i skopiuje pliki PDB wraz z biblioteki DLL i inne pliki danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="278fa-250">This package will have a *.symbols.nupkg* extension and will copy the PDB files along with the DLL and other output files.</span></span>

### <a name="includesource"></a><span data-ttu-id="278fa-251">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="278fa-251">IncludeSource</span></span>
<span data-ttu-id="278fa-252">Ta wartość logiczna wskazuje, czy Proces pakietu należy utworzyć pakiet źródła.</span><span class="sxs-lookup"><span data-stu-id="278fa-252">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="278fa-253">Źródłowy pakiet zawiera biblioteki kodu źródłowego oraz pliki PDB.</span><span class="sxs-lookup"><span data-stu-id="278fa-253">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="278fa-254">Pliki źródłowe są umieszczane w obszarze `src/ProjectName` katalogu w wynikowym pliku pakietu.</span><span class="sxs-lookup"><span data-stu-id="278fa-254">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span> 

### <a name="istool"></a><span data-ttu-id="278fa-255">IsTool</span><span class="sxs-lookup"><span data-stu-id="278fa-255">IsTool</span></span>
<span data-ttu-id="278fa-256">Określa, czy wszystkie pliki wyjściowe są kopiowane do *narzędzia* folder zamiast *lib* folderu.</span><span class="sxs-lookup"><span data-stu-id="278fa-256">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="278fa-257">Należy pamiętać, że jest inny niż `DotNetCliTool` który jest określany przez ustawienie `PackageType` w *.csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="278fa-257">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="278fa-258">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="278fa-258">RepositoryUrl</span></span>
<span data-ttu-id="278fa-259">Określa adres URL repozytorium, gdzie znajduje się kod źródłowy dla pakietu i/lub z którego jest ona kompilowana.</span><span class="sxs-lookup"><span data-stu-id="278fa-259">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span> 

### <a name="repositorytype"></a><span data-ttu-id="278fa-260">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="278fa-260">RepositoryType</span></span>
<span data-ttu-id="278fa-261">Określa typ repozytorium.</span><span class="sxs-lookup"><span data-stu-id="278fa-261">Specifies the type of the repository.</span></span> <span data-ttu-id="278fa-262">Domyślna to "git".</span><span class="sxs-lookup"><span data-stu-id="278fa-262">Default is "git".</span></span> 

### <a name="nopackageanalysis"></a><span data-ttu-id="278fa-263">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="278fa-263">NoPackageAnalysis</span></span>
<span data-ttu-id="278fa-264">Określa, że pakiet nie należy uruchamiać analizy pakietu po utworzeniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="278fa-264">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="278fa-265">Element MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="278fa-265">MinClientVersion</span></span>
<span data-ttu-id="278fa-266">Określa minimalną wersję klienta NuGet, który można zainstalować ten pakiet, wymuszane przez nuget.exe i Menedżer pakietów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="278fa-266">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="278fa-267">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="278fa-267">IncludeBuildOutput</span></span>
<span data-ttu-id="278fa-268">Tej wartości logiczna określa, czy zestawy danych wyjściowych kompilacji powinien zapewniać do *.nupkg* pliku lub nie.</span><span class="sxs-lookup"><span data-stu-id="278fa-268">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="278fa-269">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="278fa-269">IncludeContentInPack</span></span>
<span data-ttu-id="278fa-270">Ta wartość logiczna określa, czy wszystkie elementy które mają typ `Content` zostaną uwzględnione w pakiecie wynikowy automatycznie.</span><span class="sxs-lookup"><span data-stu-id="278fa-270">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="278fa-271">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="278fa-271">The default is `true`.</span></span> 

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="278fa-272">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="278fa-272">BuildOutputTargetFolder</span></span>
<span data-ttu-id="278fa-273">Określa folder, gdzie umieścić zestawy danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="278fa-273">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="278fa-274">Zestawy danych wyjściowych (i inne pliki wyjściowe) są kopiowane do ich odpowiednich framework folderów.</span><span class="sxs-lookup"><span data-stu-id="278fa-274">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="278fa-275">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="278fa-275">ContentTargetFolders</span></span>
<span data-ttu-id="278fa-276">Ta właściwość określa domyślną lokalizację gdzie powinien pojawiać wszystkie pliki zawartości, jeśli `PackagePath` nie jest określony dla nich.</span><span class="sxs-lookup"><span data-stu-id="278fa-276">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="278fa-277">Wartość domyślna to "zawartość; pliki".</span><span class="sxs-lookup"><span data-stu-id="278fa-277">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="278fa-278">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="278fa-278">NuspecFile</span></span>
<span data-ttu-id="278fa-279">Ścieżka względna lub bezwzględna do *.nuspec* pliku używany na potrzeby pakowania.</span><span class="sxs-lookup"><span data-stu-id="278fa-279">Relative or absolute path to the *.nuspec* file being used for packing.</span></span> 

> [!NOTE]
> <span data-ttu-id="278fa-280">Jeśli *.nuspec* określony plik, jest on używany **wyłącznie** dla pakowania informacji i informacje w projektach nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="278fa-280">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span> 

### <a name="nuspecbasepath"></a><span data-ttu-id="278fa-281">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="278fa-281">NuspecBasePath</span></span>
<span data-ttu-id="278fa-282">Podstawowa ścieżka dla *.nuspec* pliku.</span><span class="sxs-lookup"><span data-stu-id="278fa-282">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="278fa-283">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="278fa-283">NuspecProperties</span></span>
<span data-ttu-id="278fa-284">Rozdzielana średnikami lista kluczy = pary wartości.</span><span class="sxs-lookup"><span data-stu-id="278fa-284">Semicolon separated list of key=value pairs.</span></span>
