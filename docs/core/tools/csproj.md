---
title: Dodatki do formatu csproj dla platformy .NET Core
description: Dowiedz się więcej o różnicach między istniejące i pliki csproj .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 09/22/2017
ms.openlocfilehash: 1fd264da2863fbeb88900be0f6fe000acac08a09
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47216919"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="b5552-103">Dodatki do formatu csproj dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="b5552-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="b5552-104">W tym dokumencie opisano zmiany, które zostały dodane w plikach projektu jako część przeniesienia z *project.json* do *csproj* i [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="b5552-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="b5552-105">Aby uzyskać więcej informacji na temat składni pliku ogólnego projektu i odwołania, zobacz [plik projektu MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference) dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="b5552-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>  

## <a name="implicit-package-references"></a><span data-ttu-id="b5552-106">Odwołania do pakietu niejawne</span><span class="sxs-lookup"><span data-stu-id="b5552-106">Implicit package references</span></span>
<span data-ttu-id="b5552-107">Metapakiety niejawnie są określone w oparciu o framework(s) docelowej, określone w `<TargetFramework>` lub `<TargetFrameworks>` właściwości pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="b5552-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="b5552-108">`<TargetFrameworks>` jest ignorowana, jeśli `<TargetFramework>` jest określony, niezależnie od kolejności.</span><span class="sxs-lookup"><span data-stu-id="b5552-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span>

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

### <a name="recommendations"></a><span data-ttu-id="b5552-109">Zalecenia</span><span class="sxs-lookup"><span data-stu-id="b5552-109">Recommendations</span></span>
<span data-ttu-id="b5552-110">Ponieważ `Microsoft.NETCore.App` lub `NetStandard.Library` metapakiety niejawnie są wywoływane, Oto nasze zalecane najlepsze rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="b5552-110">Since `Microsoft.NETCore.App` or `NetStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

* <span data-ttu-id="b5552-111">Podczas określania wartości docelowej platformy .NET Core lub .NET Standard, nigdy nie mają wyraźne odniesienie do `Microsoft.NETCore.App` lub `NetStandard.Library` metapakiety za pośrednictwem `<PackageReference>` elementu w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="b5552-111">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NetStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
* <span data-ttu-id="b5552-112">Jeśli potrzebujesz określonej wersji środowiska uruchomieniowego podczas określania wartości docelowej platformy .NET Core, należy użyć `<RuntimeFrameworkVersion>` właściwość w projekcie (na przykład `1.0.4`) zamiast odwoływać się do meta Microsoft.aspnetcore.all.</span><span class="sxs-lookup"><span data-stu-id="b5552-112">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
    * <span data-ttu-id="b5552-113">Może się to zdarzyć, jeśli używasz [niezależna wdrożeń](../deploying/index.md#self-contained-deployments-scd) i należy określona poprawka wersję 1.0.0 LTS środowiska uruchomieniowego, na przykład.</span><span class="sxs-lookup"><span data-stu-id="b5552-113">This might happen if you are using [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
* <span data-ttu-id="b5552-114">Jeśli potrzebujesz określonej wersji `NetStandard.Library` meta Microsoft.aspnetcore.all podczas przeznaczonych dla platformy .NET Standard, możesz użyć `<NetStandardImplicitPackageVersion>` właściwości i wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="b5552-114">If you need a specific version of the `NetStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
* <span data-ttu-id="b5552-115">Nie jawnie dodać lub zaktualizować odwołania do albo `Microsoft.NETCore.App` lub `NetStandard.Library` meta Microsoft.aspnetcore.all w projektach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5552-115">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NetStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="b5552-116">Jeśli jakakolwiek wersja `NetStandard.Library` jest wymagana, gdy przy użyciu pakietu NuGet oparte na .NET Standard, NuGet automatycznie instaluje tę wersję.</span><span class="sxs-lookup"><span data-stu-id="b5552-116">If any version of `NetStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="b5552-117">Kompilacja domyślna obejmuje w projektach .NET Core</span><span class="sxs-lookup"><span data-stu-id="b5552-117">Default compilation includes in .NET Core projects</span></span>
<span data-ttu-id="b5552-118">Wraz z przejściem do *csproj* format w najnowszych wersjach zestawu SDK, zmieniliśmy domyślnie zawiera i nie obejmuje elementy kompilacji i zasoby osadzone pliki właściwości zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="b5552-118">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="b5552-119">Oznacza to, że nie należy określić te elementy w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="b5552-119">This means that you no longer need to specify these items in your project file.</span></span> 

<span data-ttu-id="b5552-120">Głównym powodem w ten sposób jest zaśmiecać w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="b5552-120">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="b5552-121">Wartości domyślne, które znajdują się w zestawie SDK obejmuje najbardziej typowe przypadki użycia, więc nie ma potrzeby powtarzanie ich każdego projektu, które tworzysz.</span><span class="sxs-lookup"><span data-stu-id="b5552-121">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="b5552-122">Prowadzi to do mniejsze pliki projektu, które są znacznie łatwiejsze do zrozumienia, jak również edytować ręcznie, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="b5552-122">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span> 

<span data-ttu-id="b5552-123">W poniższej tabeli przedstawiono, które element oraz tych, które [elementy globalne](https://en.wikipedia.org/wiki/Glob_(programming)) zarówno uwzględniać i wykluczone w zestawie SDK:</span><span class="sxs-lookup"><span data-stu-id="b5552-123">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span> 

| <span data-ttu-id="b5552-124">Element</span><span class="sxs-lookup"><span data-stu-id="b5552-124">Element</span></span>           | <span data-ttu-id="b5552-125">Obejmują glob</span><span class="sxs-lookup"><span data-stu-id="b5552-125">Include glob</span></span>                              | <span data-ttu-id="b5552-126">Wyklucz glob</span><span class="sxs-lookup"><span data-stu-id="b5552-126">Exclude glob</span></span>                                                  | <span data-ttu-id="b5552-127">Usuń glob</span><span class="sxs-lookup"><span data-stu-id="b5552-127">Remove glob</span></span>                |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="b5552-128">Kompilacji</span><span class="sxs-lookup"><span data-stu-id="b5552-128">Compile</span></span>           | <span data-ttu-id="b5552-129">\*\*/\*CS (lub inne rozszerzenia językowe)</span><span class="sxs-lookup"><span data-stu-id="b5552-129">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="b5552-130">\*\*/\*.user;  \*\*/\*.\* Proj;  \* \* / \*.sln;  \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="b5552-130">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="b5552-131">Brak</span><span class="sxs-lookup"><span data-stu-id="b5552-131">N/A</span></span>                        |
| <span data-ttu-id="b5552-132">EmbeddedResource</span><span class="sxs-lookup"><span data-stu-id="b5552-132">EmbeddedResource</span></span>  | <span data-ttu-id="b5552-133">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="b5552-133">\*\*/\*.resx</span></span>                              | <span data-ttu-id="b5552-134">\*\*/\*.user; \*\*/\*.\* Proj; \* \* / \*.sln; \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="b5552-134">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="b5552-135">Brak</span><span class="sxs-lookup"><span data-stu-id="b5552-135">N/A</span></span>                        |
| <span data-ttu-id="b5552-136">Brak</span><span class="sxs-lookup"><span data-stu-id="b5552-136">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="b5552-137">\*\*/\*.user; \*\*/\*.\* Proj; \* \* / \*.sln; \* \* / \*.vssscc</span><span class="sxs-lookup"><span data-stu-id="b5552-137">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="b5552-138">- \*\*/\*.cs; \*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="b5552-138">- \*\*/\*.cs; \*\*/\*.resx</span></span> |

<span data-ttu-id="b5552-139">Jeśli podczas próby utworzenia go za pomocą zestawu SDK najnowsze elementy globalne są zdefiniowane w projekcie, otrzymasz następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="b5552-139">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="b5552-140">Zduplikowane elementy kompilacji zostaną uwzględnione.</span><span class="sxs-lookup"><span data-stu-id="b5552-140">Duplicate Compile items were included.</span></span> <span data-ttu-id="b5552-141">Zestaw SDK platformy .NET obejmuje elementy kompilacji z katalogu projektu domyślnie.</span><span class="sxs-lookup"><span data-stu-id="b5552-141">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="b5552-142">Możesz usunąć te elementy z pliku projektu lub ustaw właściwość "EnableDefaultCompileItems", "false", jeśli chcesz jawnie umieszczone w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="b5552-142">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span> 

<span data-ttu-id="b5552-143">Aby obejść ten błąd, można usunąć jawne `Compile` elementy, które są zgodne z typami wymienionych w powyższej tabeli, można także ustawić `<EnableDefaultCompileItems>` właściwości `false`, podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="b5552-143">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```
<span data-ttu-id="b5552-144">Ustawienie tej właściwości na `false` spowoduje przesłonięcie niejawne dołączania i zachowanie zostaną przywrócone poprzednie zestawów SDK, który wymagał określić elementy domyślne globalne w projekcie.</span><span class="sxs-lookup"><span data-stu-id="b5552-144">Setting this property to `false` will override implicit inclusion and the behavior will revert back to the previous SDKs where you had to specify the default globs in your project.</span></span> 

<span data-ttu-id="b5552-145">Ta zmiana nie powoduje modyfikacji głównego zawiera mechanika innych.</span><span class="sxs-lookup"><span data-stu-id="b5552-145">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="b5552-146">Jednak jeśli chcesz określić, na przykład, niektóre pliki na publikowaniu z Twoją aplikacją, nadal można znanych mechanizmów w *csproj* do tego (na przykład `<Content>` elementu).</span><span class="sxs-lookup"><span data-stu-id="b5552-146">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="b5552-147">`<EnableDefaultCompileItems>` powoduje wyłączenie tylko `Compile` elementy globalne, ale nie ma wpływu na inne elementy globalne, takich jak niejawny `None` glob, która ma zastosowanie również do \*.cs elementów.</span><span class="sxs-lookup"><span data-stu-id="b5552-147">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="b5552-148">Z tego powodu **Eksploratora rozwiązań** będą nadal show \*.cs elementy w ramach projektu, dołączone jako `None` elementów.</span><span class="sxs-lookup"><span data-stu-id="b5552-148">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="b5552-149">W podobny sposób można użyć `<EnableDefaultNoneItems>` wyłączyć niejawny `None` glob.</span><span class="sxs-lookup"><span data-stu-id="b5552-149">In a similar way, you can use `<EnableDefaultNoneItems>` to disable the implicit `None` glob.</span></span>

<span data-ttu-id="b5552-150">Aby wyłączyć **wszystkie niejawne elementy globalne**, można ustawić `<EnableDefaultItems>` właściwość `false` jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b5552-150">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>
```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

### <a name="recommendation"></a><span data-ttu-id="b5552-151">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="b5552-151">Recommendation</span></span>
<span data-ttu-id="b5552-152">Za pomocą pliku csproj zaleca się, usuń elementy domyślne globalne z projektu i dodać tylko ścieżki do plików za pomocą elementy globalne dla tych artefaktów, których potrzebuje aplikacja/biblioteka, dla różnych scenariuszy (na przykład, środowisko uruchomieniowe i obsługi pakietów NuGet).</span><span class="sxs-lookup"><span data-stu-id="b5552-152">With csproj, we recommend that you remove the default globs from your project and only add file paths with globs for those artifacts that your app/library needs for various scenarios (for example, runtime and NuGet packaging).</span></span>

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="b5552-153">Jak wyświetlić całego projektu, jak MSBuild widzi on</span><span class="sxs-lookup"><span data-stu-id="b5552-153">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="b5552-154">Chociaż te zmiany w pliku csproj znacznie upraszczają pliki projektu, możesz chcieć wyświetlaną w pełni rozwinięte projektu MSBuild widzi on po zestawie SDK i jego obiekty docelowe są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="b5552-154">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="b5552-155">Przetwarzanie wstępne projektu z [ `/pp` Przełącz](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) z [ `dotnet msbuild` ](dotnet-msbuild.md) polecenia, które pokazują, które pliki są importowane, ich źródła i materiały przekazywane do kompilacji bez faktycznego Tworzenie projektu:</span><span class="sxs-lookup"><span data-stu-id="b5552-155">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="b5552-156">Jeśli projekt zawiera wiele platform docelowych, wyniki polecenia powinna zostać zwrócona na tylko jeden z nich, określając ją jako właściwość narzędzia MSBuild:</span><span class="sxs-lookup"><span data-stu-id="b5552-156">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="b5552-157">Dodatki</span><span class="sxs-lookup"><span data-stu-id="b5552-157">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="b5552-158">Atrybutu zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="b5552-158">Sdk attribute</span></span> 
<span data-ttu-id="b5552-159">`<Project>` Elementu *.csproj* plik ma nowy atrybut o nazwie `Sdk`.</span><span class="sxs-lookup"><span data-stu-id="b5552-159">The `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="b5552-160">`Sdk` Określa zestaw SDK będzie używane przez projekt.</span><span class="sxs-lookup"><span data-stu-id="b5552-160">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="b5552-161">Zestaw SDK, jako [dokumentu warstwowe](cli-msbuild-architecture.md) opisuje, to zbiór MSBuild [zadania](/visualstudio/msbuild/msbuild-tasks) i [cele](/visualstudio/msbuild/msbuild-targets) , można tworzyć kod platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b5552-161">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="b5552-162">Publikujemy dwóch głównych zestawów SDK z narzędziami .NET Core:</span><span class="sxs-lookup"><span data-stu-id="b5552-162">We ship two main SDKs with the .NET Core tools:</span></span>

1. <span data-ttu-id="b5552-163">.NET Core SDK o identyfikatorze `Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="b5552-163">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="b5552-164">.NET Core web SDK o identyfikatorze `Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="b5552-164">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>

<span data-ttu-id="b5552-165">Musisz mieć `Sdk` atrybut do jednego z tych identyfikatorów w `<Project>` element, aby użyć narzędzi .NET Core i kompilowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="b5552-165">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span> 

### <a name="packagereference"></a><span data-ttu-id="b5552-166">PackageReference</span><span class="sxs-lookup"><span data-stu-id="b5552-166">PackageReference</span></span>
<span data-ttu-id="b5552-167">Element, który określa zależność NuGet w projekcie.</span><span class="sxs-lookup"><span data-stu-id="b5552-167">Item that specifies a NuGet dependency in the project.</span></span> <span data-ttu-id="b5552-168">`Include` Atrybut określa identyfikator pakietu.</span><span class="sxs-lookup"><span data-stu-id="b5552-168">The `Include` attribute specifies the package ID.</span></span> 

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="b5552-169">Wersja</span><span class="sxs-lookup"><span data-stu-id="b5552-169">Version</span></span>
<span data-ttu-id="b5552-170">`Version` Określa numer wersji pakietu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="b5552-170">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="b5552-171">Ten atrybut przestrzega zasad [wersji NuGet](/nuget/create-packages/dependency-versions#version-ranges) schematu.</span><span class="sxs-lookup"><span data-stu-id="b5552-171">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="b5552-172">Domyślnym zachowaniem jest dokładna wersja dopasowania.</span><span class="sxs-lookup"><span data-stu-id="b5552-172">The default behavior is an exact version match.</span></span> <span data-ttu-id="b5552-173">Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji NuGet `[1.2.3]` dla 1.2.3 dokładną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="b5552-173">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="b5552-174">IncludeAssets, ExcludeAssets i PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="b5552-174">IncludeAssets, ExcludeAssets and PrivateAssets</span></span>
<span data-ttu-id="b5552-175">`IncludeAssets` atrybut określa zasoby należące do pakietu określony przez `<PackageReference>` powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="b5552-175">`IncludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> 

<span data-ttu-id="b5552-176">`ExcludeAssets` atrybut określa zasoby należące do pakietu określony przez `<PackageReference>` nie powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="b5552-176">`ExcludeAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="b5552-177">`PrivateAssets` atrybut określa zasoby należące do pakietu określony przez `<PackageReference>` powinny być używane jednak, że nie powinna przepływać do następnego projektu.</span><span class="sxs-lookup"><span data-stu-id="b5552-177">`PrivateAssets` attribute specifies what assets belonging to the package specified by `<PackageReference>` should be consumed but that they should not flow to the next project.</span></span> 

> [!NOTE]
> <span data-ttu-id="b5552-178">`PrivateAssets` jest odpowiednikiem *project.json*/*xproj* `SuppressParent` elementu.</span><span class="sxs-lookup"><span data-stu-id="b5552-178">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="b5552-179">Tych atrybutów może zawierać co najmniej jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="b5552-179">These attributes can contain one or more of the following items:</span></span>

* <span data-ttu-id="b5552-180">`Compile` — zawartość folderu biblioteki są dostępne kompilowanie z użyciem.</span><span class="sxs-lookup"><span data-stu-id="b5552-180">`Compile` – the contents of the lib folder are available to compile against.</span></span>
* <span data-ttu-id="b5552-181">`Runtime` — zawartość folderu środowiska uruchomieniowego są dystrybuowane.</span><span class="sxs-lookup"><span data-stu-id="b5552-181">`Runtime` – the contents of the runtime folder are distributed.</span></span>
* <span data-ttu-id="b5552-182">`ContentFiles` — zawartość *contentfiles* folderu są używane.</span><span class="sxs-lookup"><span data-stu-id="b5552-182">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
* <span data-ttu-id="b5552-183">`Build` — właściwości/elementów docelowych, w folderze kompilacji są używane.</span><span class="sxs-lookup"><span data-stu-id="b5552-183">`Build` – the props/targets in the build folder are used.</span></span>
* <span data-ttu-id="b5552-184">`Native` — zawartość z zasobów natywnych są kopiowane do folderu wyjściowego dla środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b5552-184">`Native` – the contents from native assets are copied to the output folder for runtime.</span></span>
* <span data-ttu-id="b5552-185">`Analyzers` — są używane analizatory.</span><span class="sxs-lookup"><span data-stu-id="b5552-185">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="b5552-186">Alternatywnie ten atrybut może zawierać:</span><span class="sxs-lookup"><span data-stu-id="b5552-186">Alternatively, the attribute can contain:</span></span>

* <span data-ttu-id="b5552-187">`None` — zasoby są używane.</span><span class="sxs-lookup"><span data-stu-id="b5552-187">`None` – none of the assets are used.</span></span>
* <span data-ttu-id="b5552-188">`All` — wszystkie zasoby są używane.</span><span class="sxs-lookup"><span data-stu-id="b5552-188">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="b5552-189">DotNetCliToolReference</span><span class="sxs-lookup"><span data-stu-id="b5552-189">DotNetCliToolReference</span></span>
<span data-ttu-id="b5552-190">`<DotNetCliToolReference>` elementu określa narzędzie interfejsu wiersza polecenia, które użytkownik chce przywrócić w kontekście projektu.</span><span class="sxs-lookup"><span data-stu-id="b5552-190">`<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="b5552-191">Jest zamiennikiem `tools` w węźle *project.json*.</span><span class="sxs-lookup"><span data-stu-id="b5552-191">It's a replacement for the `tools` node in *project.json*.</span></span> 

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

#### <a name="version"></a><span data-ttu-id="b5552-192">Wersja</span><span class="sxs-lookup"><span data-stu-id="b5552-192">Version</span></span>
<span data-ttu-id="b5552-193">`Version` Określa numer wersji pakietu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="b5552-193">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="b5552-194">Ten atrybut przestrzega zasad [wersji NuGet](/nuget/create-packages/dependency-versions#version-ranges) schematu.</span><span class="sxs-lookup"><span data-stu-id="b5552-194">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="b5552-195">Domyślnym zachowaniem jest dokładna wersja dopasowania.</span><span class="sxs-lookup"><span data-stu-id="b5552-195">The default behavior is an exact version match.</span></span> <span data-ttu-id="b5552-196">Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji NuGet `[1.2.3]` dla 1.2.3 dokładną wersję pakietu.</span><span class="sxs-lookup"><span data-stu-id="b5552-196">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3]` for the exact 1.2.3 version of the package.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="b5552-197">RuntimeIdentifiers</span><span class="sxs-lookup"><span data-stu-id="b5552-197">RuntimeIdentifiers</span></span>
<span data-ttu-id="b5552-198">`<RuntimeIdentifiers>` Element umożliwia określenie rozdzieloną średnikami listę [identyfikatorów środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu.</span><span class="sxs-lookup"><span data-stu-id="b5552-198">The `<RuntimeIdentifiers>` element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="b5552-199">Włącz identyfikatorów RID, publikowanie niezależne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="b5552-199">RIDs enable publishing a self-contained deployments.</span></span> 

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="b5552-200">RuntimeIdentifier</span><span class="sxs-lookup"><span data-stu-id="b5552-200">RuntimeIdentifier</span></span>
<span data-ttu-id="b5552-201">`<RuntimeIdentifier>` Element można określić tylko jeden [identyfikator środowiska uruchomieniowego (RID)](../rid-catalog.md) dla projektu.</span><span class="sxs-lookup"><span data-stu-id="b5552-201">The `<RuntimeIdentifier>` element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="b5552-202">Włącz identyfikatorów RID, publikowanie niezależne wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="b5552-202">RIDs enable publishing a self-contained deployment.</span></span> 

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

### <a name="packagetargetfallback"></a><span data-ttu-id="b5552-203">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="b5552-203">PackageTargetFallback</span></span> 
<span data-ttu-id="b5552-204">`<PackageTargetFallback>` Element umożliwia określenie zestawu zgodnych elementów docelowych do użycia podczas przywracania pakietów.</span><span class="sxs-lookup"><span data-stu-id="b5552-204">The `<PackageTargetFallback>` element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="b5552-205">Został zaprojektowany tak, aby zezwolić na pakiety, które używają dotnet [TxM (krótkiej nazwy docelowej x)](/nuget/schema/target-frameworks) do pracy z pakietami, które nie deklarują dotnet TxM.</span><span class="sxs-lookup"><span data-stu-id="b5552-205">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="b5552-206">Jeśli projekt używa dotnet TxM, a następnie wszystkich pakietów to zależy od musi również mieć dotnet TxM, chyba że dodasz `<PackageTargetFallback>` do swojego projektu, aby umożliwić-dotnet platform zapewnić ich zgodność za pomocą polecenia dotnet.</span><span class="sxs-lookup"><span data-stu-id="b5552-206">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span> 

<span data-ttu-id="b5552-207">W poniższym przykładzie przedstawiono przejścia dla wszystkich obiektów docelowych w projekcie:</span><span class="sxs-lookup"><span data-stu-id="b5552-207">The following example provides the fallbacks for all targets in your project:</span></span> 

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="b5552-208">W poniższym przykładzie określono planów awaryjnych tylko w przypadku `netcoreapp2.1` docelowej:</span><span class="sxs-lookup"><span data-stu-id="b5552-208">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="nuget-metadata-properties"></a><span data-ttu-id="b5552-209">Właściwości metadanych NuGet</span><span class="sxs-lookup"><span data-stu-id="b5552-209">NuGet metadata properties</span></span>
<span data-ttu-id="b5552-210">Wraz z przejściem do programu MSbuild, przenieśliśmy metadanych wejściowych, który jest używany podczas pakowania pakietów NuGet, od *project.json* do *.csproj* plików.</span><span class="sxs-lookup"><span data-stu-id="b5552-210">With the move to MSbuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="b5552-211">Dane wejściowe są właściwości programu MSBuild, aby musieli przejść w ramach `<PropertyGroup>` grupy.</span><span class="sxs-lookup"><span data-stu-id="b5552-211">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="b5552-212">Poniżej przedstawiono listę właściwości, które są używane jako dane wejściowe, aby proces pakowania, korzystając z `dotnet pack` polecenia lub `Pack` MSBuild docelowa to znaczy częścią zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="b5552-212">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK.</span></span> 

### <a name="ispackable"></a><span data-ttu-id="b5552-213">IsPackable</span><span class="sxs-lookup"><span data-stu-id="b5552-213">IsPackable</span></span>
<span data-ttu-id="b5552-214">Wartość logiczna określająca, czy można będzie bogatymi w projekcie.</span><span class="sxs-lookup"><span data-stu-id="b5552-214">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="b5552-215">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="b5552-215">The default value is `true`.</span></span> 

### <a name="packageversion"></a><span data-ttu-id="b5552-216">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="b5552-216">PackageVersion</span></span>
<span data-ttu-id="b5552-217">Określa wersję tego pakietu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="b5552-217">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="b5552-218">Akceptuje wszystkie formularze ciąg wersji NuGet.</span><span class="sxs-lookup"><span data-stu-id="b5552-218">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="b5552-219">Wartością domyślną jest wartość z `$(Version)`, oznacza to, że właściwości `Version` w projekcie.</span><span class="sxs-lookup"><span data-stu-id="b5552-219">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span> 

### <a name="packageid"></a><span data-ttu-id="b5552-220">PackageId</span><span class="sxs-lookup"><span data-stu-id="b5552-220">PackageId</span></span>
<span data-ttu-id="b5552-221">Określa nazwę pakietu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="b5552-221">Specifies the name for the resulting package.</span></span> <span data-ttu-id="b5552-222">Jeśli nie zostanie określony, `pack` operacji będą domyślnie używają `AssemblyName` lub nazwę katalogu jako nazwę pakietu.</span><span class="sxs-lookup"><span data-stu-id="b5552-222">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span> 

### <a name="title"></a><span data-ttu-id="b5552-223">Tytuł</span><span class="sxs-lookup"><span data-stu-id="b5552-223">Title</span></span>
<span data-ttu-id="b5552-224">Tytuł przyjaznego dla człowieka pakietu, zwykle używanych w interfejsie użytkownika wyświetla w witrynach nuget.org i Menedżera pakietów w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b5552-224">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="b5552-225">Jeśli nie zostanie określony, identyfikator pakietu jest używana zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="b5552-225">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="b5552-226">Autorzy</span><span class="sxs-lookup"><span data-stu-id="b5552-226">Authors</span></span>
<span data-ttu-id="b5552-227">Rozdzielana średnikami lista autorów pakietów, pasujące nazwy profilu w witrynie nuget.org. Te są wyświetlane w galerii pakietów NuGet w witrynie nuget.org i są odwoływania się do pakietów przez ten sam autorów.</span><span class="sxs-lookup"><span data-stu-id="b5552-227">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="description"></a><span data-ttu-id="b5552-228">Opis</span><span class="sxs-lookup"><span data-stu-id="b5552-228">Description</span></span>
<span data-ttu-id="b5552-229">Długi opis pakietu do wyświetlania w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b5552-229">A long description of the package for UI display.</span></span>

### <a name="copyright"></a><span data-ttu-id="b5552-230">Prawa autorskie</span><span class="sxs-lookup"><span data-stu-id="b5552-230">Copyright</span></span>
<span data-ttu-id="b5552-231">Szczegóły dotyczące praw autorskich dla pakietu.</span><span class="sxs-lookup"><span data-stu-id="b5552-231">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="b5552-232">PackageRequireLicenseAcceptance</span><span class="sxs-lookup"><span data-stu-id="b5552-232">PackageRequireLicenseAcceptance</span></span>
<span data-ttu-id="b5552-233">Wartość logiczna określająca, czy klient musi monitować konsumenta o zaakceptowanie licencji pakietu przed zainstalowaniem pakietu.</span><span class="sxs-lookup"><span data-stu-id="b5552-233">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="b5552-234">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="b5552-234">The default is `false`.</span></span>

### <a name="packagelicenseurl"></a><span data-ttu-id="b5552-235">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="b5552-235">PackageLicenseUrl</span></span>
<span data-ttu-id="b5552-236">Adres URL licencji, która ma zastosowanie do pakietu.</span><span class="sxs-lookup"><span data-stu-id="b5552-236">An URL to the license that is applicable to the package.</span></span>

### <a name="packageprojecturl"></a><span data-ttu-id="b5552-237">PackageProjectUrl</span><span class="sxs-lookup"><span data-stu-id="b5552-237">PackageProjectUrl</span></span>
<span data-ttu-id="b5552-238">Adres URL strony głównej pakietu, często wyświetlany w użytkownika, jak również adres nuget.org.</span><span class="sxs-lookup"><span data-stu-id="b5552-238">A URL for the package's home page, often shown in UI displays as well as nuget.org.</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="b5552-239">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="b5552-239">PackageIconUrl</span></span>
<span data-ttu-id="b5552-240">Adres URL obrazu 64 x 64 z przezroczystym tłem do użycia jako ikona dla pakietu wyświetlania w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b5552-240">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="b5552-241">PackageReleaseNotes</span><span class="sxs-lookup"><span data-stu-id="b5552-241">PackageReleaseNotes</span></span>
<span data-ttu-id="b5552-242">Informacje o wersji dla pakietu.</span><span class="sxs-lookup"><span data-stu-id="b5552-242">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="b5552-243">PackageTags</span><span class="sxs-lookup"><span data-stu-id="b5552-243">PackageTags</span></span>
<span data-ttu-id="b5552-244">Rozdzielaną średnikami listę znaczników, który wyznacza pakietu.</span><span class="sxs-lookup"><span data-stu-id="b5552-244">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="b5552-245">PackageOutputPath</span><span class="sxs-lookup"><span data-stu-id="b5552-245">PackageOutputPath</span></span>
<span data-ttu-id="b5552-246">Określa ścieżkę wyjściową, w którym spakowany pakiet zostanie porzucony.</span><span class="sxs-lookup"><span data-stu-id="b5552-246">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="b5552-247">Wartość domyślna to `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="b5552-247">Default is `$(OutputPath)`.</span></span> 

### <a name="includesymbols"></a><span data-ttu-id="b5552-248">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="b5552-248">IncludeSymbols</span></span>
<span data-ttu-id="b5552-249">Ta wartość logiczna wskazuje, czy pakiet powinien Utwórz pakiet dodatkowych symboli, gdy projekt jest pakowany.</span><span class="sxs-lookup"><span data-stu-id="b5552-249">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="b5552-250">Ten pakiet będzie miał *. symbols.nupkg* rozszerzenia i skopiuje pliki PDB wraz z biblioteki DLL i inne pliki wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="b5552-250">This package will have a *.symbols.nupkg* extension and will copy the PDB files along with the DLL and other output files.</span></span>

### <a name="includesource"></a><span data-ttu-id="b5552-251">IncludeSource</span><span class="sxs-lookup"><span data-stu-id="b5552-251">IncludeSource</span></span>
<span data-ttu-id="b5552-252">Ta wartość logiczna wskazuje, czy Proces pakietu należy utworzyć pakiet "source".</span><span class="sxs-lookup"><span data-stu-id="b5552-252">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="b5552-253">Źródłowy pakiet zawiera biblioteki kodu źródłowego oraz pliki PDB.</span><span class="sxs-lookup"><span data-stu-id="b5552-253">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="b5552-254">Pliki źródłowe są umieszczane w `src/ProjectName` katalogu w powstałym pliku pakietu.</span><span class="sxs-lookup"><span data-stu-id="b5552-254">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span> 

### <a name="istool"></a><span data-ttu-id="b5552-255">IsTool</span><span class="sxs-lookup"><span data-stu-id="b5552-255">IsTool</span></span>
<span data-ttu-id="b5552-256">Określa, czy wszystkie pliki wyjściowe są kopiowane do *narzędzia* folderu zamiast *lib* folderu.</span><span class="sxs-lookup"><span data-stu-id="b5552-256">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="b5552-257">Należy pamiętać, że to różni się od `DotNetCliTool` określić, ustawiając `PackageType` w *.csproj* pliku.</span><span class="sxs-lookup"><span data-stu-id="b5552-257">Note that this is different from a `DotNetCliTool` which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="b5552-258">RepositoryUrl</span><span class="sxs-lookup"><span data-stu-id="b5552-258">RepositoryUrl</span></span>
<span data-ttu-id="b5552-259">Określa adres URL repozytorium, gdzie znajduje się kod źródłowy dla pakietu i/lub z którego jest ona kompilowana.</span><span class="sxs-lookup"><span data-stu-id="b5552-259">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span> 

### <a name="repositorytype"></a><span data-ttu-id="b5552-260">RepositoryType</span><span class="sxs-lookup"><span data-stu-id="b5552-260">RepositoryType</span></span>
<span data-ttu-id="b5552-261">Określa typ repozytorium.</span><span class="sxs-lookup"><span data-stu-id="b5552-261">Specifies the type of the repository.</span></span> <span data-ttu-id="b5552-262">Wartością domyślną jest "git".</span><span class="sxs-lookup"><span data-stu-id="b5552-262">Default is "git".</span></span> 

### <a name="nopackageanalysis"></a><span data-ttu-id="b5552-263">NoPackageAnalysis</span><span class="sxs-lookup"><span data-stu-id="b5552-263">NoPackageAnalysis</span></span>
<span data-ttu-id="b5552-264">Określa, że pakiet nie należy uruchamiać analizy pakietu po utworzeniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="b5552-264">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="b5552-265">Atrybut MinClientVersion</span><span class="sxs-lookup"><span data-stu-id="b5552-265">MinClientVersion</span></span>
<span data-ttu-id="b5552-266">Określa minimalną wersję klienta NuGet, który można zainstalować ten pakiet, wymuszane przez nuget.exe oraz Menedżera pakietów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b5552-266">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="b5552-267">IncludeBuildOutput</span><span class="sxs-lookup"><span data-stu-id="b5552-267">IncludeBuildOutput</span></span>
<span data-ttu-id="b5552-268">Tej wartości logicznych Określa, czy zestawy danych wyjściowych kompilacji powinien pakowane w *.nupkg* plików lub nie.</span><span class="sxs-lookup"><span data-stu-id="b5552-268">This Boolean values specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="b5552-269">IncludeContentInPack</span><span class="sxs-lookup"><span data-stu-id="b5552-269">IncludeContentInPack</span></span>
<span data-ttu-id="b5552-270">Ta wartość logiczna określa, czy wszystkie elementy, mają typ `Content` zostanie automatycznie dołączony do pakietu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="b5552-270">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="b5552-271">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="b5552-271">The default is `true`.</span></span> 

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="b5552-272">BuildOutputTargetFolder</span><span class="sxs-lookup"><span data-stu-id="b5552-272">BuildOutputTargetFolder</span></span>
<span data-ttu-id="b5552-273">Określa folder, gdzie umieścić zestawy danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="b5552-273">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="b5552-274">Zestawy danych wyjściowych (i inne pliki wyjściowe) są kopiowane do ich odpowiednich ramach folderów.</span><span class="sxs-lookup"><span data-stu-id="b5552-274">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="b5552-275">ContentTargetFolders</span><span class="sxs-lookup"><span data-stu-id="b5552-275">ContentTargetFolders</span></span>
<span data-ttu-id="b5552-276">Ta właściwość określa domyślną lokalizację kogo powinno zwrócić wszystkie pliki zawartości, gdy `PackagePath` nie określono dla nich.</span><span class="sxs-lookup"><span data-stu-id="b5552-276">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="b5552-277">Wartość domyślna to "zawartość; pliki".</span><span class="sxs-lookup"><span data-stu-id="b5552-277">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="b5552-278">NuspecFile</span><span class="sxs-lookup"><span data-stu-id="b5552-278">NuspecFile</span></span>
<span data-ttu-id="b5552-279">Względna lub bezwzględna ścieżka do *.nuspec* plików używanych na potrzeby pakowania.</span><span class="sxs-lookup"><span data-stu-id="b5552-279">Relative or absolute path to the *.nuspec* file being used for packing.</span></span> 

> [!NOTE]
> <span data-ttu-id="b5552-280">Jeśli *.nuspec* pliku jest określona, jest on używany **wyłącznie** pakowanie informacji i wszelkie informacje zawarte w projektów nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="b5552-280">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span> 

### <a name="nuspecbasepath"></a><span data-ttu-id="b5552-281">NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="b5552-281">NuspecBasePath</span></span>
<span data-ttu-id="b5552-282">Podstawową ścieżkę dla *.nuspec* pliku.</span><span class="sxs-lookup"><span data-stu-id="b5552-282">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="b5552-283">NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="b5552-283">NuspecProperties</span></span>
<span data-ttu-id="b5552-284">Rozdzielana średnikami lista klucz = wartość pary.</span><span class="sxs-lookup"><span data-stu-id="b5552-284">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="b5552-285">Właściwości AssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="b5552-285">AssemblyInfo properties</span></span>
<span data-ttu-id="b5552-286">[Atrybuty zestawu](../../framework/app-domains/set-assembly-attributes.md) , które były w *AssemblyInfo* pliku są teraz automatycznie generowane na podstawie właściwości.</span><span class="sxs-lookup"><span data-stu-id="b5552-286">[Assembly attributes](../../framework/app-domains/set-assembly-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="b5552-287">Właściwości dla atrybutu</span><span class="sxs-lookup"><span data-stu-id="b5552-287">Properties per attribute</span></span>

<span data-ttu-id="b5552-288">Każdy atrybut ma właściwości, które sterują jej zawartość i innej, aby wyłączyć jej generacji, jak pokazano w poniższej tabeli:</span><span class="sxs-lookup"><span data-stu-id="b5552-288">Each attribute has a property that control its content and another to disable its generation as shown in the following table:</span></span>

| <span data-ttu-id="b5552-289">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b5552-289">Attribute</span></span>                                                      | <span data-ttu-id="b5552-290">Właściwość</span><span class="sxs-lookup"><span data-stu-id="b5552-290">Property</span></span>               | <span data-ttu-id="b5552-291">Właściwość, która wyłącza</span><span class="sxs-lookup"><span data-stu-id="b5552-291">Property to disable</span></span>                             |
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

<span data-ttu-id="b5552-292">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="b5552-292">Notes:</span></span>

* <span data-ttu-id="b5552-293">`AssemblyVersion` i `FileVersion` domyślny ma wartość `$(Version)` bez sufiksu.</span><span class="sxs-lookup"><span data-stu-id="b5552-293">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="b5552-294">Na przykład jeśli `$(Version)` jest `1.2.3-beta.4`, a następnie wartość będzie wynosić `1.2.3`.</span><span class="sxs-lookup"><span data-stu-id="b5552-294">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
* <span data-ttu-id="b5552-295">`InformationalVersion` Wartość domyślna to wartość `$(Version)`.</span><span class="sxs-lookup"><span data-stu-id="b5552-295">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
* <span data-ttu-id="b5552-296">`InformationalVersion` ma `$(SourceRevisionId)` dołączona, jeśli właściwość jest obecny.</span><span class="sxs-lookup"><span data-stu-id="b5552-296">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="b5552-297">Można je wyłączyć, używając `IncludeSourceRevisionInInformationalVersion`.</span><span class="sxs-lookup"><span data-stu-id="b5552-297">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
* <span data-ttu-id="b5552-298">`Copyright` i `Description` właściwości są używane również do metadanych NuGet.</span><span class="sxs-lookup"><span data-stu-id="b5552-298">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
* <span data-ttu-id="b5552-299">`Configuration` jest współużytkowany z procesu kompilacji i ustawić za pomocą `--configuration` parametru `dotnet` poleceń.</span><span class="sxs-lookup"><span data-stu-id="b5552-299">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="b5552-300">GenerateAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="b5552-300">GenerateAssemblyInfo</span></span> 
<span data-ttu-id="b5552-301">Wartość logiczna, która włącza lub wyłącza Generowanie AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="b5552-301">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="b5552-302">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="b5552-302">The default value is `true`.</span></span> 

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="b5552-303">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="b5552-303">GeneratedAssemblyInfoFile</span></span> 
<span data-ttu-id="b5552-304">Ścieżka pliku z informacjami wygenerowanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="b5552-304">The path of the generated assembly info file.</span></span> <span data-ttu-id="b5552-305">Domyślnie plik w `$(IntermediateOutputPath)` katalogu (obj).</span><span class="sxs-lookup"><span data-stu-id="b5552-305">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
