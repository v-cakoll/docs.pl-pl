---
title: Dodatki do formatu csproj dla .NET Core
description: Dowiedz się więcej o różnicach między istniejącymi i net-core csproj plików
ms.date: 04/08/2019
ms.openlocfilehash: 9d9e212c9531828a8c2dd51fdd7488c17be41ba2
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134068"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="9a73f-103">Dodatki do formatu csproj dla .NET Core</span><span class="sxs-lookup"><span data-stu-id="9a73f-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="9a73f-104">W tym dokumencie opisano zmiany, które zostały dodane do plików projektu w ramach przejścia z *project.json* do *csproj* i [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="9a73f-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="9a73f-105">Aby uzyskać więcej informacji na temat ogólnej składni pliku projektu i odwołania, zobacz [dokumentację pliku projektu MSBuild.](/visualstudio/msbuild/msbuild-project-file-schema-reference)</span><span class="sxs-lookup"><span data-stu-id="9a73f-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="9a73f-106">Odwołania do pakietu niejawnego</span><span class="sxs-lookup"><span data-stu-id="9a73f-106">Implicit package references</span></span>

<span data-ttu-id="9a73f-107">Do metapakietów niejawnie odwoływane są na podstawie `<TargetFramework>` `<TargetFrameworks>` ram docelowych określonych w pliku projektu lub ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="9a73f-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="9a73f-108">`<TargetFrameworks>`jest ignorowana, jeśli `<TargetFramework>` jest określona, niezależnie od kolejności.</span><span class="sxs-lookup"><span data-stu-id="9a73f-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span> <span data-ttu-id="9a73f-109">Aby uzyskać więcej informacji, zobacz [Pakiety, metapakiety i struktury](../packages.md).</span><span class="sxs-lookup"><span data-stu-id="9a73f-109">For more information, see [Packages, metapackages, and frameworks](../packages.md).</span></span>

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

### <a name="recommendations"></a><span data-ttu-id="9a73f-110">Zalecenia</span><span class="sxs-lookup"><span data-stu-id="9a73f-110">Recommendations</span></span>

<span data-ttu-id="9a73f-111">Ponieważ `Microsoft.NETCore.App` `NETStandard.Library` lub metapakiety są niejawnie odwoływane, oto nasze zalecane najlepsze rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="9a73f-111">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

- <span data-ttu-id="9a73f-112">Podczas kierowania .NET Core lub .NET Standard, nigdy `Microsoft.NETCore.App` `NETStandard.Library` nie mają jawne `<PackageReference>` odwołanie do lub metapakiety za pośrednictwem elementu w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-112">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
- <span data-ttu-id="9a73f-113">Jeśli potrzebujesz określonej wersji środowiska wykonawczego podczas kierowania .NET Core, należy użyć `<RuntimeFrameworkVersion>` właściwości `1.0.4`w projekcie (na przykład ) zamiast odwoływać się do metapakiety.</span><span class="sxs-lookup"><span data-stu-id="9a73f-113">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  - <span data-ttu-id="9a73f-114">Może się tak zdarzyć, jeśli używasz [samodzielnych wdrożeń](../deploying/index.md#publish-self-contained) i potrzebujesz określonej wersji poprawki środowiska wykonawczego 1.0.0 LTS, na przykład.</span><span class="sxs-lookup"><span data-stu-id="9a73f-114">This might happen if you are using [self-contained deployments](../deploying/index.md#publish-self-contained) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
- <span data-ttu-id="9a73f-115">Jeśli potrzebujesz określonej wersji `NETStandard.Library` metapakiety podczas kierowania .NET Standard, możesz użyć `<NetStandardImplicitPackageVersion>` właściwości i ustawić wersję, której potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="9a73f-115">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
- <span data-ttu-id="9a73f-116">Nie jawnie dodawać lub aktualizować odwołania `Microsoft.NETCore.App` `NETStandard.Library` do lub metapakiet w projektach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9a73f-116">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="9a73f-117">Jeśli dowolna `NETStandard.Library` wersja jest potrzebna podczas korzystania z pakietu NuGet opartego na systemie .NET Standard, nuget automatycznie instaluje tę wersję.</span><span class="sxs-lookup"><span data-stu-id="9a73f-117">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="9a73f-118">Wersja niejawna dla niektórych odwołań do pakietu</span><span class="sxs-lookup"><span data-stu-id="9a73f-118">Implicit version for some package references</span></span>

<span data-ttu-id="9a73f-119">Większość użycia [`<PackageReference>`](#packagereference) wymaga ustawienia `Version` atrybutu, aby określić wersję pakietu NuGet, która ma być używana.</span><span class="sxs-lookup"><span data-stu-id="9a73f-119">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="9a73f-120">W przypadku korzystania z platformy .NET Core 2.1 lub 2.2 i odwoływania się do [aplikacji Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) lub [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), jednak ten atrybut jest zbędny.</span><span class="sxs-lookup"><span data-stu-id="9a73f-120">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="9a73f-121">Pakiet .NET Core SDK może automatycznie wybrać wersję tych pakietów, które powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="9a73f-121">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="9a73f-122">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="9a73f-122">Recommendation</span></span>

<span data-ttu-id="9a73f-123">Podczas odwoływania `Microsoft.AspNetCore.App` `Microsoft.AspNetCore.All` się do lub pakietów, nie należy określać ich wersji.</span><span class="sxs-lookup"><span data-stu-id="9a73f-123">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="9a73f-124">Jeśli określono wersję, SDK może wywołać ostrzeżenie NETSDK1071.</span><span class="sxs-lookup"><span data-stu-id="9a73f-124">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="9a73f-125">Aby rozwiązać to ostrzeżenie, usuń wersję pakietu, tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9a73f-125">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="9a73f-126">Znany problem: pakiet .NET Core 2.1 SDK obsługiwał tę składnię tylko wtedy, gdy projekt używa również pliku Microsoft.NET.Sdk.Web.</span><span class="sxs-lookup"><span data-stu-id="9a73f-126">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="9a73f-127">Ta wartość jest rozpoznawana w sdku .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="9a73f-127">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="9a73f-128">Te odwołania do ASP.NET Core metapackages mają nieco inne zachowanie od większości normalnych pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="9a73f-128">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="9a73f-129">[Wdrożenia zależne od struktury](../deploying/index.md#publish-runtime-dependent) aplikacji korzystających z tych metapakietów automatycznie korzystają z udostępnionej struktury ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a73f-129">[Framework-dependent deployments](../deploying/index.md#publish-runtime-dependent) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="9a73f-130">Podczas korzystania z metapakietów nie ma żadnych zasobów z pakietów Core NuGet, do których odwołuje się odwołuje się ASP.NET Core NuGet, **nie** są wdrażane z aplikacją — wspólna struktura ASP.NET Core zawiera te zasoby.</span><span class="sxs-lookup"><span data-stu-id="9a73f-130">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="9a73f-131">Zasoby w udostępnionej ramach są zoptymalizowane pod kątem platformy docelowej, aby skrócić czas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a73f-131">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="9a73f-132">Aby uzyskać więcej informacji na temat udostępnionej struktury, zobacz [.NET Core distribution packaging](../distribution-packaging.md).</span><span class="sxs-lookup"><span data-stu-id="9a73f-132">For more information about shared framework, see [.NET Core distribution packaging](../distribution-packaging.md).</span></span>

<span data-ttu-id="9a73f-133">Jeśli wersja *jest* określona, jest traktowana jako *minimalna* wersja ASP.NET core udostępnionej struktury dla wdrożeń zależnych od struktury i jako *dokładna* wersja dla wdrożeń samodzielnych.</span><span class="sxs-lookup"><span data-stu-id="9a73f-133">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="9a73f-134">Może to mieć następujące konsekwencje:</span><span class="sxs-lookup"><span data-stu-id="9a73f-134">This can have the following consequences:</span></span>

- <span data-ttu-id="9a73f-135">Jeśli wersja ASP.NET Core zainstalowana na serwerze jest mniejsza niż wersja określona w PackageReference, nie można uruchomić procesu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a73f-135">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="9a73f-136">Aktualizacje metapakietu są często dostępne w NuGet.org przed udostępnieniem aktualizacji w środowiskach hostingowych, takich jak Azure.</span><span class="sxs-lookup"><span data-stu-id="9a73f-136">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="9a73f-137">Aktualizowanie wersji na PackageReference do ASP.NET Core może spowodować niepowodzenie wdrożonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9a73f-137">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
- <span data-ttu-id="9a73f-138">Jeśli aplikacja jest wdrażana jako [samodzielne wdrożenie,](../deploying/index.md#publish-self-contained)aplikacja może nie zawierać najnowszych aktualizacji zabezpieczeń do platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a73f-138">If the application is deployed as a [self-contained deployment](../deploying/index.md#publish-self-contained), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="9a73f-139">Gdy wersja nie jest określona, SDK może automatycznie dołączyć najnowszą wersję ASP.NET Core w samodzielnym wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-139">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="9a73f-140">Domyślna kompilacja obejmuje projekty .NET Core</span><span class="sxs-lookup"><span data-stu-id="9a73f-140">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="9a73f-141">Wraz z przejściem do formatu *csproj* w najnowszych wersjach SDK przenieśliśmy domyślne elementy zawiera i wyklucza dla elementów kompilacji i osadzonych zasobów do plików właściwości SDK.</span><span class="sxs-lookup"><span data-stu-id="9a73f-141">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="9a73f-142">Oznacza to, że nie trzeba już określać tych elementów w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-142">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="9a73f-143">Głównym powodem tego jest zmniejszenie bałaganu w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-143">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="9a73f-144">Wartości domyślne, które są obecne w SDK powinny obejmować najczęstsze przypadki użycia, więc nie ma potrzeby powtarzania ich w każdym projekcie, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="9a73f-144">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="9a73f-145">Prowadzi to do mniejszych plików projektu, które są znacznie łatwiejsze do zrozumienia, a także edytować ręcznie, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="9a73f-145">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="9a73f-146">W poniższej tabeli przedstawiono, który element i które [globy](https://en.wikipedia.org/wiki/Glob_(programming)) są uwzględniane i wykluczane w zestawie SDK:</span><span class="sxs-lookup"><span data-stu-id="9a73f-146">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="9a73f-147">Element</span><span class="sxs-lookup"><span data-stu-id="9a73f-147">Element</span></span>           | <span data-ttu-id="9a73f-148">Uwzględnij glob</span><span class="sxs-lookup"><span data-stu-id="9a73f-148">Include glob</span></span>                              | <span data-ttu-id="9a73f-149">Wyklucz glob</span><span class="sxs-lookup"><span data-stu-id="9a73f-149">Exclude glob</span></span>                                                  | <span data-ttu-id="9a73f-150">Usuń glob</span><span class="sxs-lookup"><span data-stu-id="9a73f-150">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="9a73f-151">Skompilować</span><span class="sxs-lookup"><span data-stu-id="9a73f-151">Compile</span></span>           | <span data-ttu-id="9a73f-152">\*\*/\*.cs (lub inne rozszerzenia języka)</span><span class="sxs-lookup"><span data-stu-id="9a73f-152">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="9a73f-153">\*\*/\*.user;  \*\*/\*. \*proj ;  \* \* / \*  \* \* /.vssscc \*(vssscc)</span><span class="sxs-lookup"><span data-stu-id="9a73f-153">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="9a73f-154">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="9a73f-154">N/A</span></span>                      |
| <span data-ttu-id="9a73f-155">Zasoby wbudowaneSerekseźródło</span><span class="sxs-lookup"><span data-stu-id="9a73f-155">EmbeddedResource</span></span>  | <span data-ttu-id="9a73f-156">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="9a73f-156">\*\*/\*.resx</span></span>                              | <span data-ttu-id="9a73f-157">\*\*/\*.user; \*\*/\*. \*proj ; \* \* / \* \* \* /.vssscc \*(vssscc)</span><span class="sxs-lookup"><span data-stu-id="9a73f-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="9a73f-158">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="9a73f-158">N/A</span></span>                      |
| <span data-ttu-id="9a73f-159">Brak</span><span class="sxs-lookup"><span data-stu-id="9a73f-159">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="9a73f-160">\*\*/\*.user; \*\*/\*. \*proj ; \* \* / \* \* \* /.vssscc \*(vssscc)</span><span class="sxs-lookup"><span data-stu-id="9a73f-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="9a73f-161">\*\*/\*.cs ; \* \* /.resx \*(resx)</span><span class="sxs-lookup"><span data-stu-id="9a73f-161">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="9a73f-162">**Wyklucz glob** zawsze `./bin` wyklucza `./obj` foldery i, które `$(BaseOutputPath)` są `$(BaseIntermediateOutputPath)` reprezentowane przez i MSBuild właściwości, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="9a73f-162">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="9a73f-163">Jako całość wszystkie wykluczenia są `$(DefaultItemExcludes)`reprezentowane przez .</span><span class="sxs-lookup"><span data-stu-id="9a73f-163">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="9a73f-164">Jeśli masz globs w projekcie i spróbujesz go zbudować przy użyciu najnowszego SDK, otrzymasz następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="9a73f-164">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="9a73f-165">Zduplikowane elementy kompilacji zostały uwzględnione.</span><span class="sxs-lookup"><span data-stu-id="9a73f-165">Duplicate Compile items were included.</span></span> <span data-ttu-id="9a73f-166">Zestaw SDK platformy .NET domyślnie zawiera elementy kompilacji z katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-166">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="9a73f-167">Można usunąć te elementy z pliku projektu lub ustawić właściwość "EnableDefaultCompileItems" na "false", jeśli chcesz jawnie dołączyć je do pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="9a73f-168">Aby obejść ten błąd, można usunąć jawne `Compile` elementy, które pasują do tych wymienionych w `<EnableDefaultCompileItems>` poprzedniej `false`tabeli, lub można ustawić właściwość na , w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="9a73f-168">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="9a73f-169">Ustawienie tej `false` właściwości spowoduje wyłączenie niejawnego włączenia, przywracając zachowanie poprzednich sdków, w których trzeba było określić domyślne globs w projekcie.</span><span class="sxs-lookup"><span data-stu-id="9a73f-169">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="9a73f-170">Ta zmiana nie modyfikuje głównej mechaniki innych zawiera.</span><span class="sxs-lookup"><span data-stu-id="9a73f-170">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="9a73f-171">Jeśli jednak chcesz określić, na przykład niektóre pliki, które mają zostać opublikowane w aplikacji, nadal możesz użyć znanych `<Content>` mechanizmów w *csproj* do tego (na przykład elementu).</span><span class="sxs-lookup"><span data-stu-id="9a73f-171">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="9a73f-172">`<EnableDefaultCompileItems>`tylko wyłącza `Compile` globs, ale nie wpływa na `None` inne globs, jak \*niejawne glob, który dotyczy również .cs elementów.</span><span class="sxs-lookup"><span data-stu-id="9a73f-172">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="9a73f-173">Z tego powodu **Eksplorator rozwiązań** będzie nadal wyświetlał \*elementy `None` .cs w ramach projektu, uwzględnione jako elementy.</span><span class="sxs-lookup"><span data-stu-id="9a73f-173">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="9a73f-174">W podobny sposób można `<EnableDefaultNoneItems>` ustawić false, aby `None` wyłączyć niejawne glob, w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="9a73f-174">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="9a73f-175">Aby wyłączyć **wszystkie niejawne globy,** można ustawić właściwość tak `<EnableDefaultItems>` jak `false` w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9a73f-175">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="9a73f-176">Jak zobaczyć cały projekt, jak msBuild widzi go</span><span class="sxs-lookup"><span data-stu-id="9a73f-176">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="9a73f-177">Podczas gdy te zmiany csproj znacznie upraszczają pliki projektu, możesz chcieć zobaczyć w pełni rozwinięty projekt, ponieważ MSBuild widzi go po uwzględnieniu SDK i jego obiektów docelowych.</span><span class="sxs-lookup"><span data-stu-id="9a73f-177">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="9a73f-178">Wstępnie przetworzyć projekt z [`dotnet msbuild`](dotnet-msbuild.md) [ `/pp` przełącznikiem](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) polecenia, które pokazuje, które pliki są importowane, ich źródła i ich wkład do kompilacji bez faktycznego budowania projektu:</span><span class="sxs-lookup"><span data-stu-id="9a73f-178">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="9a73f-179">Jeśli projekt ma wiele struktur docelowych, wyniki polecenia powinny koncentrować się tylko na jednym z nich, określając go jako właściwość MSBuild:</span><span class="sxs-lookup"><span data-stu-id="9a73f-179">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="9a73f-180">Dodatki</span><span class="sxs-lookup"><span data-stu-id="9a73f-180">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="9a73f-181">Atrybut Sdk</span><span class="sxs-lookup"><span data-stu-id="9a73f-181">Sdk attribute</span></span>

<span data-ttu-id="9a73f-182">Element `<Project>` główny pliku *csproj* ma nowy atrybut `Sdk`o nazwie .</span><span class="sxs-lookup"><span data-stu-id="9a73f-182">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="9a73f-183">`Sdk`określa, który SDK będzie używany przez projekt.</span><span class="sxs-lookup"><span data-stu-id="9a73f-183">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="9a73f-184">Zestaw SDK, jak opisano [w dokumencie warstwowym,](cli-msbuild-architecture.md) to zestaw [zadań](/visualstudio/msbuild/msbuild-tasks) i [obiektów docelowych](/visualstudio/msbuild/msbuild-targets) MSBuild, które można tworzyć kod .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a73f-184">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="9a73f-185">Dla platformy .NET Core dostępne są następujące skomuniky SDK:</span><span class="sxs-lookup"><span data-stu-id="9a73f-185">The following SDKs are available for .NET Core:</span></span>

1. <span data-ttu-id="9a73f-186">Core SDK .NET z identyfikatorem`Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="9a73f-186">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="9a73f-187">Internetowy sDK .NET Core z identyfikatorem`Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="9a73f-187">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="9a73f-188">SDK biblioteki klas .NET Core Razor z identyfikatorem`Microsoft.NET.Sdk.Razor`</span><span class="sxs-lookup"><span data-stu-id="9a73f-188">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="9a73f-189">Podstawowa usługa robocza .NET `Microsoft.NET.Sdk.Worker` o identyfikatorze (od .NET Core 3.0)</span><span class="sxs-lookup"><span data-stu-id="9a73f-189">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (since .NET Core 3.0)</span></span>
5. <span data-ttu-id="9a73f-190">.NET Core WinForms i WPF z `Microsoft.NET.Sdk.WindowsDesktop` identyfikatorem (od .NET Core 3.0)</span><span class="sxs-lookup"><span data-stu-id="9a73f-190">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (since .NET Core 3.0)</span></span>

<span data-ttu-id="9a73f-191">Musisz mieć `Sdk` atrybut ustawiony na jeden z tych identyfikatorów w elemencie, `<Project>` aby użyć narzędzi .NET Core i utworzyć kod.</span><span class="sxs-lookup"><span data-stu-id="9a73f-191">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="9a73f-192">Wniosek dotyczący pakietu</span><span class="sxs-lookup"><span data-stu-id="9a73f-192">PackageReference</span></span>

<span data-ttu-id="9a73f-193">Element `<PackageReference>` elementu określa [zależność NuGet w projekcie](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="9a73f-193">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="9a73f-194">Atrybut `Include` określa identyfikator pakietu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-194">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="package-id" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="9a73f-195">Wersja</span><span class="sxs-lookup"><span data-stu-id="9a73f-195">Version</span></span>

<span data-ttu-id="9a73f-196">Wymagany `Version` atrybut określa wersję pakietu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="9a73f-196">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="9a73f-197">Atrybut jest zgodny z regułami schematu [wersji NuGet.](/nuget/reference/package-versioning#version-ranges-and-wildcards)</span><span class="sxs-lookup"><span data-stu-id="9a73f-197">The attribute respects the rules of the [NuGet versioning](/nuget/reference/package-versioning#version-ranges-and-wildcards) scheme.</span></span> <span data-ttu-id="9a73f-198">Domyślnym zachowaniem jest minimalna wersja, dopasowanie włącznie.</span><span class="sxs-lookup"><span data-stu-id="9a73f-198">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="9a73f-199">Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji `[1.2.3, )` NuGet i oznacza, że rozwiązany pakiet będzie miał wersję 1.2.3, jeśli jest dostępna lub większa w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="9a73f-199">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="9a73f-200">Zestawy includeAssets, ExcludeAssets i PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="9a73f-200">IncludeAssets, ExcludeAssets, and PrivateAssets</span></span>

<span data-ttu-id="9a73f-201">`IncludeAssets`atrybut określa, które aktywa należące do `<PackageReference>` pakietu określonego przez powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="9a73f-201">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="9a73f-202">Domyślnie wszystkie zasoby pakietu są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="9a73f-202">By default, all package assets are included.</span></span>

<span data-ttu-id="9a73f-203">`ExcludeAssets`atrybut określa, które aktywa należące do `<PackageReference>` pakietu określonego przez nie powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="9a73f-203">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="9a73f-204">`PrivateAssets`atrybut określa, które zasoby należące do `<PackageReference>` pakietu określonego przez powinny być używane, ale nie przepływ do następnego projektu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-204">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="9a73f-205">Zasoby `Analyzers` `Build` i `ContentFiles` zasoby są domyślnie prywatne, gdy ten atrybut nie jest obecny.</span><span class="sxs-lookup"><span data-stu-id="9a73f-205">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="9a73f-206">`PrivateAssets`jest odpowiednikiem *elementu project.json*/*xproj.* `SuppressParent`</span><span class="sxs-lookup"><span data-stu-id="9a73f-206">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="9a73f-207">Te atrybuty mogą zawierać jeden lub więcej z następujących `;` elementów, oddzielonych znakiem średnika, jeśli na liście znajduje się więcej niż jeden:</span><span class="sxs-lookup"><span data-stu-id="9a73f-207">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

- <span data-ttu-id="9a73f-208">`Compile`– zawartość folderu *lib* są dostępne do kompilacji przeciwko.</span><span class="sxs-lookup"><span data-stu-id="9a73f-208">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="9a73f-209">`Runtime`– zawartość folderu *środowiska wykonawczego* są dystrybuowane.</span><span class="sxs-lookup"><span data-stu-id="9a73f-209">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="9a73f-210">`ContentFiles`– zawartość folderu *contentfiles* są używane.</span><span class="sxs-lookup"><span data-stu-id="9a73f-210">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="9a73f-211">`Build`– rekwizyty/obiekty docelowe w folderze *kompilacji* są używane.</span><span class="sxs-lookup"><span data-stu-id="9a73f-211">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="9a73f-212">`Native`– zawartość zasobów natywnych są kopiowane do folderu *wyjściowego* dla środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="9a73f-212">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="9a73f-213">`Analyzers`– analizatory są używane.</span><span class="sxs-lookup"><span data-stu-id="9a73f-213">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="9a73f-214">Alternatywnie atrybut może zawierać:</span><span class="sxs-lookup"><span data-stu-id="9a73f-214">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="9a73f-215">`None`– żaden z aktywów nie jest wykorzystywany.</span><span class="sxs-lookup"><span data-stu-id="9a73f-215">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="9a73f-216">`All`– wykorzystuje się wszystkie aktywa.</span><span class="sxs-lookup"><span data-stu-id="9a73f-216">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="9a73f-217">DotNetCliToolReference (DotNetCliToolReference)</span><span class="sxs-lookup"><span data-stu-id="9a73f-217">DotNetCliToolReference</span></span>

<span data-ttu-id="9a73f-218">Element `<DotNetCliToolReference>` elementu określa narzędzie interfejsu wiersza polecenia, które użytkownik chce przywrócić w kontekście projektu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-218">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="9a73f-219">Jest to zamiennik węzła `tools` w *project.json*.</span><span class="sxs-lookup"><span data-stu-id="9a73f-219">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

<span data-ttu-id="9a73f-220">Należy `DotNetCliToolReference` zauważyć, że jest [teraz przestarzałe](https://github.com/dotnet/announcements/issues/107) na rzecz [.NET Core Local Tools](https://aka.ms/local-tools).</span><span class="sxs-lookup"><span data-stu-id="9a73f-220">Note that `DotNetCliToolReference` is [now deprecated](https://github.com/dotnet/announcements/issues/107) in favor of [.NET Core Local Tools](https://aka.ms/local-tools).</span></span>

#### <a name="version"></a><span data-ttu-id="9a73f-221">Wersja</span><span class="sxs-lookup"><span data-stu-id="9a73f-221">Version</span></span>

<span data-ttu-id="9a73f-222">`Version`określa wersję pakietu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="9a73f-222">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="9a73f-223">Atrybut jest zgodny z regułami schematu [wersji NuGet.](/nuget/create-packages/dependency-versions#version-ranges)</span><span class="sxs-lookup"><span data-stu-id="9a73f-223">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="9a73f-224">Domyślnym zachowaniem jest minimalna wersja, dopasowanie włącznie.</span><span class="sxs-lookup"><span data-stu-id="9a73f-224">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="9a73f-225">Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji `[1.2.3, )` NuGet i oznacza, że rozwiązany pakiet będzie miał wersję 1.2.3, jeśli jest dostępna lub większa w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="9a73f-225">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="9a73f-226">Identyfikatory środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="9a73f-226">RuntimeIdentifiers</span></span>

<span data-ttu-id="9a73f-227">Element `<RuntimeIdentifiers>` właściwości umożliwia określenie listy identyfikatorów [czasu wykonywania (RID)](../rid-catalog.md) rozdzielanych średnikami dla projektu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-227">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="9a73f-228">Identyfikatory RID umożliwiają publikowanie samodzielnych wdrożeń.</span><span class="sxs-lookup"><span data-stu-id="9a73f-228">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="9a73f-229">Identyfikator środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="9a73f-229">RuntimeIdentifier</span></span>

<span data-ttu-id="9a73f-230">Element `<RuntimeIdentifier>` właściwości umożliwia określenie tylko jednego [identyfikatora środowiska wykonawczego (RID)](../rid-catalog.md) dla projektu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-230">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="9a73f-231">Identyfikator RID umożliwia publikowanie samodzielnego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="9a73f-231">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="9a73f-232">Użyj `<RuntimeIdentifiers>` (liczba mnoga), jeśli chcesz opublikować dla wielu uruchomień.</span><span class="sxs-lookup"><span data-stu-id="9a73f-232">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="9a73f-233">`<RuntimeIdentifier>`może zapewnić szybsze kompilacje, gdy wymagane jest tylko jedno środowisko wykonawcze.</span><span class="sxs-lookup"><span data-stu-id="9a73f-233">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="9a73f-234">PackageTargetFallback</span><span class="sxs-lookup"><span data-stu-id="9a73f-234">PackageTargetFallback</span></span>

<span data-ttu-id="9a73f-235">Element `<PackageTargetFallback>` właściwości umożliwia określenie zestawu zgodnych obiektów docelowych, które mają być używane podczas przywracania pakietów.</span><span class="sxs-lookup"><span data-stu-id="9a73f-235">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="9a73f-236">Został zaprojektowany, aby umożliwić pakietom korzystającym z dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) działanie z pakietami, które nie deklarują dotnet TxM.</span><span class="sxs-lookup"><span data-stu-id="9a73f-236">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="9a73f-237">Jeśli projekt używa dotnet TxM, a następnie wszystkie pakiety, które zależy od musi mieć `<PackageTargetFallback>` również dotnet TxM, chyba że dodać do projektu w celu umożliwienia platform innych niż dotnet być zgodne z dotnet.</span><span class="sxs-lookup"><span data-stu-id="9a73f-237">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="9a73f-238">Poniższy przykład zawiera rezerwy dla wszystkich obiektów docelowych w projekcie:</span><span class="sxs-lookup"><span data-stu-id="9a73f-238">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="9a73f-239">Poniższy przykład określa rezerwy tylko `netcoreapp2.1` dla obiektu docelowego:</span><span class="sxs-lookup"><span data-stu-id="9a73f-239">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a><span data-ttu-id="9a73f-240">Tworzenie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="9a73f-240">Build events</span></span>

<span data-ttu-id="9a73f-241">Sposób, w jaki zdarzenia pre-build i post-build są określone w pliku projektu został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="9a73f-241">The way that pre-build and post-build events are specified in the project file has changed.</span></span> <span data-ttu-id="9a73f-242">Właściwości PreBuildEvent i PostBuildEvent nie są zalecane w formacie projektu w stylu SDK, ponieważ makra, takie jak $(ProjectDir) nie są rozpoznawane.</span><span class="sxs-lookup"><span data-stu-id="9a73f-242">The properties PreBuildEvent and PostBuildEvent are not recommended in the SDK-style project format, because macros such as $(ProjectDir) are not resolved.</span></span> <span data-ttu-id="9a73f-243">Na przykład następujący kod nie jest już obsługiwany:</span><span class="sxs-lookup"><span data-stu-id="9a73f-243">For example, the following code is no longer supported:</span></span>

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
</PropertyGroup>
```

<span data-ttu-id="9a73f-244">W projektach w stylu zestawu SDK użyj `PreBuild` `PostBuild` obiektu docelowego MSBuild o nazwie lub i ustaw `BeforeTargets` właściwość dla `PreBuild` obiektu . `AfterTargets` `PostBuild`</span><span class="sxs-lookup"><span data-stu-id="9a73f-244">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span> <span data-ttu-id="9a73f-245">W poprzednim przykładzie użyj następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="9a73f-245">For the preceding example, use the following code:</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
><span data-ttu-id="9a73f-246">Można użyć dowolnej nazwy dla obiektów docelowych MSBuild, `PreBuild` `PostBuild` ale ide programu Visual Studio rozpoznaje i obiekty docelowe, dlatego zaleca się przy użyciu tych nazw, dzięki czemu można edytować polecenia w programie Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="9a73f-246">You can use any name for the MSBuild targets, but the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so we recommend using those names so that you can edit the commands in the Visual Studio IDE.</span></span>

## <a name="nuget-metadata-properties"></a><span data-ttu-id="9a73f-247">Właściwości metadanych NuGet</span><span class="sxs-lookup"><span data-stu-id="9a73f-247">NuGet metadata properties</span></span>

<span data-ttu-id="9a73f-248">Wraz z przejściem do MSBuild przenieśliśmy metadane wejściowe, które są używane podczas pakowania pakietu NuGet z *pliku project.json* do *.csproj.*</span><span class="sxs-lookup"><span data-stu-id="9a73f-248">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="9a73f-249">Dane wejściowe są MSBuild właściwości, więc `<PropertyGroup>` muszą przejść w ramach grupy.</span><span class="sxs-lookup"><span data-stu-id="9a73f-249">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="9a73f-250">Poniżej znajduje się lista właściwości, które są używane jako dane `dotnet pack` wejściowe `Pack` do procesu pakowania podczas korzystania z polecenia lub obiektu docelowego MSBuild, który jest częścią zestawu SDK:</span><span class="sxs-lookup"><span data-stu-id="9a73f-250">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK:</span></span>

### <a name="ispackable"></a><span data-ttu-id="9a73f-251">IsPackable (Opakowanie)</span><span class="sxs-lookup"><span data-stu-id="9a73f-251">IsPackable</span></span>

<span data-ttu-id="9a73f-252">Wartość logiczna określająca, czy projekt może być spakowany.</span><span class="sxs-lookup"><span data-stu-id="9a73f-252">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="9a73f-253">Wartością domyślną jest `true`.</span><span class="sxs-lookup"><span data-stu-id="9a73f-253">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="9a73f-254">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="9a73f-254">PackageVersion</span></span>

<span data-ttu-id="9a73f-255">Określa wersję, którą będzie miał wynikowy pakiet.</span><span class="sxs-lookup"><span data-stu-id="9a73f-255">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="9a73f-256">Akceptuje wszystkie formy ciągu wersji NuGet.</span><span class="sxs-lookup"><span data-stu-id="9a73f-256">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="9a73f-257">Wartość domyślna `$(Version)`to wartość właściwości `Version` w projekcie.</span><span class="sxs-lookup"><span data-stu-id="9a73f-257">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="9a73f-258">PackageId</span><span class="sxs-lookup"><span data-stu-id="9a73f-258">PackageId</span></span>

<span data-ttu-id="9a73f-259">Określa nazwę pakietu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="9a73f-259">Specifies the name for the resulting package.</span></span> <span data-ttu-id="9a73f-260">Jeśli nie zostanie `pack` określony, operacja `AssemblyName` domyślnie będzie używać nazwy katalogu lub jako nazwy pakietu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-260">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="9a73f-261">Tytuł</span><span class="sxs-lookup"><span data-stu-id="9a73f-261">Title</span></span>

<span data-ttu-id="9a73f-262">Tytuł pakietu przyjazny dla ludzi, zwykle używany w interfejsie użytkownika wyświetla się jako na nuget.org i Menedżer pakietów w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9a73f-262">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="9a73f-263">Jeśli nie zostanie określony, zamiast tego jest używany identyfikator pakietu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-263">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="9a73f-264">Autorzy</span><span class="sxs-lookup"><span data-stu-id="9a73f-264">Authors</span></span>

<span data-ttu-id="9a73f-265">Oddzielona średnikami lista autorów pakietów, pasująca do nazw profili na nuget.org. Są one wyświetlane w Galerii NuGet na nuget.org i są używane do odsyłania pakietów przez tych samych autorów.</span><span class="sxs-lookup"><span data-stu-id="9a73f-265">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="9a73f-266">Scriptość pakietu</span><span class="sxs-lookup"><span data-stu-id="9a73f-266">PackageDescription</span></span>

<span data-ttu-id="9a73f-267">Długi opis pakietu dla wyświetlania interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9a73f-267">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="9a73f-268">Opis</span><span class="sxs-lookup"><span data-stu-id="9a73f-268">Description</span></span>

<span data-ttu-id="9a73f-269">Długi opis zespołu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-269">A long description for the assembly.</span></span> <span data-ttu-id="9a73f-270">Jeśli `PackageDescription` nie jest określony, a następnie ta właściwość jest również używany jako opis pakietu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-270">If `PackageDescription` is not specified, then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="9a73f-271">Prawa autorskie</span><span class="sxs-lookup"><span data-stu-id="9a73f-271">Copyright</span></span>

<span data-ttu-id="9a73f-272">Szczegóły dotyczące praw autorskich do pakietu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-272">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="9a73f-273">PackageRequireLicenseAkceptance</span><span class="sxs-lookup"><span data-stu-id="9a73f-273">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="9a73f-274">Wartość logiczna określająca, czy klient musi monitować konsumenta o zaakceptowanie licencji pakietu przed zainstalowaniem pakietu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-274">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="9a73f-275">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="9a73f-275">The default is `false`.</span></span>

### <a name="developmentdependency"></a><span data-ttu-id="9a73f-276">RozwójZależność</span><span class="sxs-lookup"><span data-stu-id="9a73f-276">DevelopmentDependency</span></span>

<span data-ttu-id="9a73f-277">Wartość logiczna, która określa, czy pakiet jest oznaczony jako zależność tylko dla deweloperów, co uniemożliwia uwzględnieniu pakietu jako zależności w innych pakietach.</span><span class="sxs-lookup"><span data-stu-id="9a73f-277">A Boolean value that specifies whether the package is marked as a development-only dependency, which prevents the package from being included as a dependency in other packages.</span></span> <span data-ttu-id="9a73f-278">Z PackageReference (NuGet 4.8+), ta flaga oznacza również, że zasoby w czasie kompilacji są wykluczone z kompilacji.</span><span class="sxs-lookup"><span data-stu-id="9a73f-278">With PackageReference (NuGet 4.8+), this flag also means that compile-time assets are excluded from compilation.</span></span> <span data-ttu-id="9a73f-279">Aby uzyskać więcej informacji, zobacz [RozwójZależność obsługi packagereference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span><span class="sxs-lookup"><span data-stu-id="9a73f-279">For more information, see [DevelopmentDependency support for PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="9a73f-280">PackageLicenseExpression (Wysuw czekowy)</span><span class="sxs-lookup"><span data-stu-id="9a73f-280">PackageLicenseExpression</span></span>

<span data-ttu-id="9a73f-281">Identyfikator lub wyrażenie [licencji SPDX.](https://spdx.org/licenses/)</span><span class="sxs-lookup"><span data-stu-id="9a73f-281">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="9a73f-282">Na przykład `Apache-2.0`.</span><span class="sxs-lookup"><span data-stu-id="9a73f-282">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="9a73f-283">Oto pełna lista [identyfikatorów licencji SPDX](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="9a73f-283">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="9a73f-284">NuGet.org akceptuje tylko licencje zatwierdzone przez OSI lub FSF podczas korzystania z wyrażenia typu licencji.</span><span class="sxs-lookup"><span data-stu-id="9a73f-284">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="9a73f-285">Dokładna składnia wyrażeń licencji jest opisana poniżej w [pliku ABNF](https://tools.ietf.org/html/rfc5234).</span><span class="sxs-lookup"><span data-stu-id="9a73f-285">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

```abnf
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
> <span data-ttu-id="9a73f-286">Tylko jeden `PackageLicenseExpression` `PackageLicenseFile` z `PackageLicenseUrl` , i mogą być określone w czasie.</span><span class="sxs-lookup"><span data-stu-id="9a73f-286">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="9a73f-287">Plik z ciekłą dostępem do pakietu</span><span class="sxs-lookup"><span data-stu-id="9a73f-287">PackageLicenseFile</span></span>

<span data-ttu-id="9a73f-288">Ścieżka do pliku licencji w pakiecie, jeśli używasz licencji, która nie została przypisana identyfikator SPDX `PackageLicenseExpression` lub jest to licencja niestandardowa (w przeciwnym razie jest preferowane)</span><span class="sxs-lookup"><span data-stu-id="9a73f-288">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="9a73f-289">Zastępuje `PackageLicenseUrl`, nie można połączyć z `PackageLicenseExpression`programem Visual Studio w wersji 15.9.4 i .NET SDK 2.1.502 lub 2.2.101 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="9a73f-289">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression`, and requires Visual Studio version 15.9.4 and .NET SDK 2.1.502 or 2.2.101 or newer.</span></span>

<span data-ttu-id="9a73f-290">Należy upewnić się, że plik licencji jest spakowany, dodając go jawnie do projektu, przykład użycia:</span><span class="sxs-lookup"><span data-stu-id="9a73f-290">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="9a73f-291">PakietLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="9a73f-291">PackageLicenseUrl</span></span>

<span data-ttu-id="9a73f-292">Adres URL licencji, która ma zastosowanie do pakietu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-292">A URL to the license that is applicable to the package.</span></span> <span data-ttu-id="9a73f-293">(_przestarzałe od Visual Studio 15.9.4, .NET SDK 2.1.502 i 2.2.101_)</span><span class="sxs-lookup"><span data-stu-id="9a73f-293">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="9a73f-294">PakietYkonurl</span><span class="sxs-lookup"><span data-stu-id="9a73f-294">PackageIconUrl</span></span>

<span data-ttu-id="9a73f-295">Adres URL obrazu 64x64 z przezroczystym tłem do użycia jako ikona pakietu w ekranie interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9a73f-295">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="9a73f-296">PackageReleaseNotes (Opis pakietu)</span><span class="sxs-lookup"><span data-stu-id="9a73f-296">PackageReleaseNotes</span></span>

<span data-ttu-id="9a73f-297">Informacje o wersji pakietu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-297">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="9a73f-298">Znaczniki pakietów</span><span class="sxs-lookup"><span data-stu-id="9a73f-298">PackageTags</span></span>

<span data-ttu-id="9a73f-299">Lista znaczników rozdzielanych średnikami, która wyznacza pakiet.</span><span class="sxs-lookup"><span data-stu-id="9a73f-299">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="9a73f-300">Ścieżka nakreślenia pakietu</span><span class="sxs-lookup"><span data-stu-id="9a73f-300">PackageOutputPath</span></span>

<span data-ttu-id="9a73f-301">Określa ścieżkę wyjściową, w której spakowany pakiet zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="9a73f-301">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="9a73f-302">Wartość domyślna to `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="9a73f-302">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="9a73f-303">IncludeSymbols</span><span class="sxs-lookup"><span data-stu-id="9a73f-303">IncludeSymbols</span></span>
<span data-ttu-id="9a73f-304">Ta wartość logiczna wskazuje, czy pakiet powinien utworzyć pakiet dodatkowych symboli, gdy projekt jest spakowany.</span><span class="sxs-lookup"><span data-stu-id="9a73f-304">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="9a73f-305">Format pakietu symboli jest kontrolowany `SymbolPackageFormat` przez właściwość.</span><span class="sxs-lookup"><span data-stu-id="9a73f-305">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="9a73f-306">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="9a73f-306">SymbolPackageFormat</span></span>
<span data-ttu-id="9a73f-307">Określa format pakietu symboli.</span><span class="sxs-lookup"><span data-stu-id="9a73f-307">Specifies the format of the symbols package.</span></span> <span data-ttu-id="9a73f-308">Jeśli "symbols.nupkg", pakiet symboli starszych zostanie utworzony z rozszerzeniem *.symbols.nupkg* zawierającym pliki PDB, bibliotek dll i inne pliki wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="9a73f-308">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="9a73f-309">Jeśli "snupkg", zostanie utworzony pakiet symboli snupkg zawierający przenośne pdb.</span><span class="sxs-lookup"><span data-stu-id="9a73f-309">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="9a73f-310">Wartość domyślna to "symbols.nupkg".</span><span class="sxs-lookup"><span data-stu-id="9a73f-310">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="9a73f-311">Źródło includesource</span><span class="sxs-lookup"><span data-stu-id="9a73f-311">IncludeSource</span></span>

<span data-ttu-id="9a73f-312">Ta wartość logiczna wskazuje, czy proces pakowania powinien utworzyć pakiet źródłowy.</span><span class="sxs-lookup"><span data-stu-id="9a73f-312">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="9a73f-313">Pakiet źródłowy zawiera kod źródłowy biblioteki oraz pliki PDB.</span><span class="sxs-lookup"><span data-stu-id="9a73f-313">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="9a73f-314">Pliki źródłowe są `src/ProjectName` umieszczane w katalogu w pliku pakietu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="9a73f-314">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="9a73f-315">IsTool (Niewłasce)</span><span class="sxs-lookup"><span data-stu-id="9a73f-315">IsTool</span></span>

<span data-ttu-id="9a73f-316">Określa, czy wszystkie pliki wyjściowe są kopiowane do folderu *narzędzi,* a nie do folderu *lib.*</span><span class="sxs-lookup"><span data-stu-id="9a73f-316">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="9a73f-317">Różni się to `DotNetCliTool`od pliku csproj , który jest określony przez ustawienie `PackageType` w pliku *csproj.*</span><span class="sxs-lookup"><span data-stu-id="9a73f-317">This is different from a `DotNetCliTool`, which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="9a73f-318">RepozytoriumUrl</span><span class="sxs-lookup"><span data-stu-id="9a73f-318">RepositoryUrl</span></span>

<span data-ttu-id="9a73f-319">Określa adres URL repozytorium, w którym znajduje się kod źródłowy pakietu i/lub z którego jest on budowany.</span><span class="sxs-lookup"><span data-stu-id="9a73f-319">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="9a73f-320">Rodzaj repozytorium</span><span class="sxs-lookup"><span data-stu-id="9a73f-320">RepositoryType</span></span>

<span data-ttu-id="9a73f-321">Określa typ repozytorium.</span><span class="sxs-lookup"><span data-stu-id="9a73f-321">Specifies the type of the repository.</span></span> <span data-ttu-id="9a73f-322">Wartość domyślna to "git".</span><span class="sxs-lookup"><span data-stu-id="9a73f-322">Default is "git".</span></span>

### <a name="repositorybranch"></a><span data-ttu-id="9a73f-323">RepozytoriumBranch</span><span class="sxs-lookup"><span data-stu-id="9a73f-323">RepositoryBranch</span></span>
<span data-ttu-id="9a73f-324">Określa nazwę gałęzi źródłowej w repozytorium.</span><span class="sxs-lookup"><span data-stu-id="9a73f-324">Specifies the name of the source branch in the repository.</span></span> <span data-ttu-id="9a73f-325">Gdy projekt jest pakowany w pakiecie NuGet, jest dodawany do metadanych pakietu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-325">When the project is packaged in a NuGet package, it's added to the package metadata.</span></span>

### <a name="repositorycommit"></a><span data-ttu-id="9a73f-326">Kompetencje repozytorium</span><span class="sxs-lookup"><span data-stu-id="9a73f-326">RepositoryCommit</span></span>
<span data-ttu-id="9a73f-327">Opcjonalne zatwierdzanie repozytorium lub zestaw zmian, aby wskazać, na którym źródle został zbudowany pakiet.</span><span class="sxs-lookup"><span data-stu-id="9a73f-327">Optional repository commit or changeset to indicate which source the package was built against.</span></span> <span data-ttu-id="9a73f-328">`RepositoryUrl`należy również określić, aby ta właściwość została uwzględniona.</span><span class="sxs-lookup"><span data-stu-id="9a73f-328">`RepositoryUrl` must also be specified for this property to be included.</span></span> <span data-ttu-id="9a73f-329">Gdy projekt jest pakowany w pakiecie NuGet, to zatwierdzenie lub changeset jest dodawany do metadanych pakietu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-329">When the project is packaged in a NuGet package, this commit or changeset is added to the package metadata.</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="9a73f-330">NoPackageAnalysis (Analiza NoPackage)</span><span class="sxs-lookup"><span data-stu-id="9a73f-330">NoPackageAnalysis</span></span>

<span data-ttu-id="9a73f-331">Określa, że pakiet nie powinien uruchamiać analizy pakietu po zbudowaniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="9a73f-331">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="9a73f-332">MinClientVersion (MinClientVersion)</span><span class="sxs-lookup"><span data-stu-id="9a73f-332">MinClientVersion</span></span>

<span data-ttu-id="9a73f-333">Określa minimalną wersję klienta NuGet, który można zainstalować ten pakiet, wymuszane przez nuget.exe i Visual Studio Package Manager.</span><span class="sxs-lookup"><span data-stu-id="9a73f-333">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="9a73f-334">IncludeBuildOutput (Uwzględnij Nagielek)</span><span class="sxs-lookup"><span data-stu-id="9a73f-334">IncludeBuildOutput</span></span>

<span data-ttu-id="9a73f-335">Ta wartość logiczna określa, czy zestawy wyjściowe kompilacji powinny być pakowane do pliku *nupkg,* czy nie.</span><span class="sxs-lookup"><span data-stu-id="9a73f-335">This Boolean value specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="9a73f-336">Dołącz Pakiet InPack</span><span class="sxs-lookup"><span data-stu-id="9a73f-336">IncludeContentInPack</span></span>

<span data-ttu-id="9a73f-337">Ta wartość logiczna określa, czy wszystkie `Content` elementy, które mają typ, zostaną automatycznie uwzględnione w pakiecie wynikowym.</span><span class="sxs-lookup"><span data-stu-id="9a73f-337">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="9a73f-338">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="9a73f-338">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="9a73f-339">Wykreślacz celów BuildOutput</span><span class="sxs-lookup"><span data-stu-id="9a73f-339">BuildOutputTargetFolder</span></span>

<span data-ttu-id="9a73f-340">Określa folder, w którym mają być umieszczane złoża wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="9a73f-340">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="9a73f-341">Zestawy wyjściowe (i inne pliki wyjściowe) są kopiowane do odpowiednich folderów framework.</span><span class="sxs-lookup"><span data-stu-id="9a73f-341">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="9a73f-342">ContentTargetFolders (własnomie treści)</span><span class="sxs-lookup"><span data-stu-id="9a73f-342">ContentTargetFolders</span></span>

<span data-ttu-id="9a73f-343">Ta właściwość określa domyślną lokalizację, gdzie wszystkie `PackagePath` pliki zawartości powinny iść, jeśli nie jest określony dla nich.</span><span class="sxs-lookup"><span data-stu-id="9a73f-343">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="9a73f-344">Wartością domyślną jest "content;contentFiles".</span><span class="sxs-lookup"><span data-stu-id="9a73f-344">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="9a73f-345">Plik Nuspec</span><span class="sxs-lookup"><span data-stu-id="9a73f-345">NuspecFile</span></span>

<span data-ttu-id="9a73f-346">Ścieżka względna lub bezwzględna do pliku *nuspec* używanego do pakowania.</span><span class="sxs-lookup"><span data-stu-id="9a73f-346">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="9a73f-347">Jeśli plik *.nuspec* jest określony, jest używany **wyłącznie** do informacji o pakowaniu, a wszelkie informacje w projektach nie są używane.</span><span class="sxs-lookup"><span data-stu-id="9a73f-347">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="9a73f-348">Ścieżka Bazowa</span><span class="sxs-lookup"><span data-stu-id="9a73f-348">NuspecBasePath</span></span>

<span data-ttu-id="9a73f-349">Ścieżka podstawowa dla pliku *nuspec.*</span><span class="sxs-lookup"><span data-stu-id="9a73f-349">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="9a73f-350">Właściwości NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="9a73f-350">NuspecProperties</span></span>

<span data-ttu-id="9a73f-351">Lista par kluczykowych i wartości oddzielonych średnikiem.</span><span class="sxs-lookup"><span data-stu-id="9a73f-351">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="9a73f-352">AssemblyInfo właściwości</span><span class="sxs-lookup"><span data-stu-id="9a73f-352">AssemblyInfo properties</span></span>

<span data-ttu-id="9a73f-353">[Atrybuty zestawu,](../../standard/assembly/set-attributes.md) które były zazwyczaj obecne w pliku *AssemblyInfo* są teraz automatycznie generowane z właściwości.</span><span class="sxs-lookup"><span data-stu-id="9a73f-353">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="9a73f-354">Właściwości na atrybut</span><span class="sxs-lookup"><span data-stu-id="9a73f-354">Properties per attribute</span></span>

<span data-ttu-id="9a73f-355">Jak pokazano w poniższej tabeli, każdy atrybut ma właściwość, która kontroluje jego zawartość i inny, który wyłącza jego generowania:</span><span class="sxs-lookup"><span data-stu-id="9a73f-355">As shown in the following table, each attribute has a property that controls its content and another that disables its generation:</span></span>

| <span data-ttu-id="9a73f-356">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9a73f-356">Attribute</span></span>                                                      | <span data-ttu-id="9a73f-357">Właściwość</span><span class="sxs-lookup"><span data-stu-id="9a73f-357">Property</span></span>               | <span data-ttu-id="9a73f-358">Właściwość, aby wyłączyć</span><span class="sxs-lookup"><span data-stu-id="9a73f-358">Property to disable</span></span>                             |
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

<span data-ttu-id="9a73f-359">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="9a73f-359">Notes:</span></span>

- <span data-ttu-id="9a73f-360">`AssemblyVersion`i `FileVersion` domyślnie jest podjęcie `$(Version)` wartości bez przyrostka.</span><span class="sxs-lookup"><span data-stu-id="9a73f-360">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="9a73f-361">Na przykład, `$(Version)` `1.2.3-beta.4`jeśli jest , `1.2.3`to wartość będzie .</span><span class="sxs-lookup"><span data-stu-id="9a73f-361">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="9a73f-362">`InformationalVersion`domyślnie wartość `$(Version)`.</span><span class="sxs-lookup"><span data-stu-id="9a73f-362">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="9a73f-363">`InformationalVersion`dołączona, `$(SourceRevisionId)` jeśli właściwość jest obecna.</span><span class="sxs-lookup"><span data-stu-id="9a73f-363">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="9a73f-364">Można go wyłączyć `IncludeSourceRevisionInInformationalVersion`za pomocą programu .</span><span class="sxs-lookup"><span data-stu-id="9a73f-364">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="9a73f-365">`Copyright`i `Description` właściwości są również używane dla metadanych NuGet.</span><span class="sxs-lookup"><span data-stu-id="9a73f-365">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="9a73f-366">`Configuration`jest współużytkowana z całym `--configuration` procesem `dotnet` kompilacji i ustawiana za pomocą parametru poleceń.</span><span class="sxs-lookup"><span data-stu-id="9a73f-366">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="9a73f-367">Generowanie AssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="9a73f-367">GenerateAssemblyInfo</span></span>

<span data-ttu-id="9a73f-368">Wartość logiczna, która włącza lub wyłącza wszystkie generowanie AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="9a73f-368">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="9a73f-369">Wartością domyślną jest `true`.</span><span class="sxs-lookup"><span data-stu-id="9a73f-369">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="9a73f-370">GeneratedAssemblyInfoFile</span><span class="sxs-lookup"><span data-stu-id="9a73f-370">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="9a73f-371">Ścieżka wygenerowanego pliku informacji o zestawie.</span><span class="sxs-lookup"><span data-stu-id="9a73f-371">The path of the generated assembly info file.</span></span> <span data-ttu-id="9a73f-372">Domyślnie plik w `$(IntermediateOutputPath)` katalogu (obj).</span><span class="sxs-lookup"><span data-stu-id="9a73f-372">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
