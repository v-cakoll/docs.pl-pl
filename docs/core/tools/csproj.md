---
title: Dodatki do formatu csproj dla .NET Core
description: Dowiedz się więcej o różnicach między istniejącymi plikami csproj firmy .NET Core
ms.date: 04/08/2019
ms.openlocfilehash: 2fb00e830380c5c4cbf7b6dcd2c8a585e1617b4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398994"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a><span data-ttu-id="c38f1-103">Dodatki do formatu csproj dla .NET Core</span><span class="sxs-lookup"><span data-stu-id="c38f1-103">Additions to the csproj format for .NET Core</span></span>

<span data-ttu-id="c38f1-104">Ten dokument przedstawia zmiany, które zostały dodane do plików projektu w ramach przejścia z *project.json* do *csproj* i [MSBuild](https://github.com/Microsoft/MSBuild).</span><span class="sxs-lookup"><span data-stu-id="c38f1-104">This document outlines the changes that were added to the project files as part of the move from *project.json* to *csproj* and [MSBuild](https://github.com/Microsoft/MSBuild).</span></span> <span data-ttu-id="c38f1-105">Aby uzyskać więcej informacji na temat ogólnej składni pliku projektu i odwołania, zobacz [dokumentację pliku projektu MSBuild.](/visualstudio/msbuild/msbuild-project-file-schema-reference)</span><span class="sxs-lookup"><span data-stu-id="c38f1-105">For more information about general project file syntax and reference, see [the MSBuild project file](/visualstudio/msbuild/msbuild-project-file-schema-reference) documentation.</span></span>

## <a name="implicit-package-references"></a><span data-ttu-id="c38f1-106">Niejawne odwołania do pakietów</span><span class="sxs-lookup"><span data-stu-id="c38f1-106">Implicit package references</span></span>

<span data-ttu-id="c38f1-107">Metapakiety są niejawnie odwołuje się na podstawie platform `<TargetFramework>` docelowych określonych w lub `<TargetFrameworks>` właściwości pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-107">Metapackages are implicitly referenced based on the target framework(s) specified in the `<TargetFramework>` or `<TargetFrameworks>` property of your project file.</span></span> <span data-ttu-id="c38f1-108">`<TargetFrameworks>`jest ignorowana, jeśli `<TargetFramework>` jest określona, niezależnie od kolejności.</span><span class="sxs-lookup"><span data-stu-id="c38f1-108">`<TargetFrameworks>` is ignored if `<TargetFramework>` is specified, independent of order.</span></span> <span data-ttu-id="c38f1-109">Aby uzyskać więcej informacji, zobacz [Pakiety, metapakiety i struktury](../packages.md).</span><span class="sxs-lookup"><span data-stu-id="c38f1-109">For more information, see [Packages, metapackages, and frameworks](../packages.md).</span></span>

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

### <a name="recommendations"></a><span data-ttu-id="c38f1-110">Zalecenia</span><span class="sxs-lookup"><span data-stu-id="c38f1-110">Recommendations</span></span>

<span data-ttu-id="c38f1-111">Ponieważ `Microsoft.NETCore.App` `NETStandard.Library` lub metapackages są niejawnie odwołuje się, następujące są nasze zalecane najlepsze rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="c38f1-111">Since `Microsoft.NETCore.App` or `NETStandard.Library` metapackages are implicitly referenced, the following are our recommended best practices:</span></span>

- <span data-ttu-id="c38f1-112">Podczas określania wartości docelowej .NET Core lub `Microsoft.NETCore.App` .NET Standard nigdy nie ma jawnego odwołania do lub `NETStandard.Library` metapakietów za pośrednictwem `<PackageReference>` elementu w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-112">When targeting .NET Core or .NET Standard, never have an explicit reference to the `Microsoft.NETCore.App` or `NETStandard.Library` metapackages via a `<PackageReference>` item in your project file.</span></span>
- <span data-ttu-id="c38f1-113">Jeśli potrzebujesz określonej wersji czasu wykonywania podczas określania wartości `<RuntimeFrameworkVersion>` docelowej .NET Core, `1.0.4`należy użyć właściwości w projekcie (na przykład) zamiast odwoływać się do metapakietu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-113">If you need a specific version of the runtime when targeting .NET Core, you should use the `<RuntimeFrameworkVersion>` property in your project (for example, `1.0.4`) instead of referencing the metapackage.</span></span>
  - <span data-ttu-id="c38f1-114">Może się tak zdarzyć, jeśli używasz [wdrożeń samodzielnych](../deploying/index.md#publish-self-contained) i potrzebujesz określonej wersji poprawki 1.0.0 LTS, na przykład.</span><span class="sxs-lookup"><span data-stu-id="c38f1-114">This might happen if you are using [self-contained deployments](../deploying/index.md#publish-self-contained) and you need a specific patch version of 1.0.0 LTS runtime, for example.</span></span>
- <span data-ttu-id="c38f1-115">Jeśli potrzebujesz określonej wersji `NETStandard.Library` metapakietu podczas określania wartości docelowej `<NetStandardImplicitPackageVersion>` .NET Standard, możesz użyć tej właściwości i ustawić potrzebną wersję.</span><span class="sxs-lookup"><span data-stu-id="c38f1-115">If you need a specific version of the `NETStandard.Library` metapackage when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set the version you need.</span></span>
- <span data-ttu-id="c38f1-116">Nie należy jawnie dodawać ani aktualizować odwołania do `Microsoft.NETCore.App` lub `NETStandard.Library` metapackage w projektach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c38f1-116">Don't explicitly add or update references to either the `Microsoft.NETCore.App` or `NETStandard.Library` metapackage in .NET Framework projects.</span></span> <span data-ttu-id="c38f1-117">Jeśli dowolna `NETStandard.Library` wersja jest potrzebna podczas korzystania z pakietu NuGet opartego na standardzie .NET, NuGet automatycznie instaluje tę wersję.</span><span class="sxs-lookup"><span data-stu-id="c38f1-117">If any version of `NETStandard.Library` is needed when using a .NET Standard-based NuGet package, NuGet automatically installs that version.</span></span>

## <a name="implicit-version-for-some-package-references"></a><span data-ttu-id="c38f1-118">Wersja niejawna dla niektórych odwołań do pakietów</span><span class="sxs-lookup"><span data-stu-id="c38f1-118">Implicit version for some package references</span></span>

<span data-ttu-id="c38f1-119">Większość użycia [`<PackageReference>`](#packagereference) wymagają ustawienie `Version` atrybutu, aby określić wersję pakietu NuGet, które mają być używane.</span><span class="sxs-lookup"><span data-stu-id="c38f1-119">Most usages of [`<PackageReference>`](#packagereference) require setting the `Version` attribute to specify the NuGet package version to be used.</span></span> <span data-ttu-id="c38f1-120">W przypadku korzystania z .NET Core 2.1 lub 2.2 i odwoływania się [do microsoft.aspNetCore.App](/aspnet/core/fundamentals/metapackage-app) lub [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage)atrybut jest jednak niepotrzebne.</span><span class="sxs-lookup"><span data-stu-id="c38f1-120">When using .NET Core 2.1 or 2.2 and referencing [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) or [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), however, the  attribute is unnecessary.</span></span> <span data-ttu-id="c38f1-121">Zestaw SDK .NET Core może automatycznie wybrać wersję tych pakietów, która powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="c38f1-121">The .NET Core SDK can automatically select the version of these packages that should be used.</span></span>

### <a name="recommendation"></a><span data-ttu-id="c38f1-122">Zalecenie</span><span class="sxs-lookup"><span data-stu-id="c38f1-122">Recommendation</span></span>

<span data-ttu-id="c38f1-123">Podczas odwoływania `Microsoft.AspNetCore.App` się `Microsoft.AspNetCore.All` do lub pakietów, nie należy określać ich wersji.</span><span class="sxs-lookup"><span data-stu-id="c38f1-123">When referencing the `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` packages, do not specify their version.</span></span> <span data-ttu-id="c38f1-124">Jeśli określono wersję, zestaw SDK może generować ostrzeżenie NETSDK1071.</span><span class="sxs-lookup"><span data-stu-id="c38f1-124">If a version is specified, the SDK may produce warning NETSDK1071.</span></span> <span data-ttu-id="c38f1-125">Aby rozwiązać ten problem, usuń wersję pakietu, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c38f1-125">To fix this warning, remove the package version like in the following example:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> <span data-ttu-id="c38f1-126">Znany problem: zestaw SDK .NET Core 2.1 obsługiwał tę składnię tylko wtedy, gdy projekt korzysta również z witryny Microsoft.NET.Sdk.Web.</span><span class="sxs-lookup"><span data-stu-id="c38f1-126">Known issue: the .NET Core 2.1 SDK only supported this syntax when the project also uses Microsoft.NET.Sdk.Web.</span></span> <span data-ttu-id="c38f1-127">Rozwiązanie tego problemu zostało rozwiązane w sdku .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="c38f1-127">This is resolved in the .NET Core 2.2 SDK.</span></span>

<span data-ttu-id="c38f1-128">Te odwołania do ASP.NET core metapackages mają nieco inne zachowanie od większości zwykłych pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="c38f1-128">These references to ASP.NET Core metapackages have a slightly different behavior from most normal NuGet packages.</span></span> <span data-ttu-id="c38f1-129">[Wdrożenia zależne od struktury](../deploying/index.md#publish-runtime-dependent) aplikacji korzystających z tych metapakietów automatycznie korzystają z ASP.NET podstawowej struktury udostępnionej.</span><span class="sxs-lookup"><span data-stu-id="c38f1-129">[Framework-dependent deployments](../deploying/index.md#publish-runtime-dependent) of applications that use these metapackages automatically take advantage of the ASP.NET Core shared framework.</span></span> <span data-ttu-id="c38f1-130">Korzystając z metapakietów, **żadne** zasoby z ASP.NET pakietów Core NuGet są wdrażane z aplikacją — ASP.NET framework udostępniony Core zawiera te zasoby.</span><span class="sxs-lookup"><span data-stu-id="c38f1-130">When you use the metapackages, **no** assets from the referenced ASP.NET Core NuGet packages are deployed with the application—the ASP.NET Core shared framework contains these assets.</span></span> <span data-ttu-id="c38f1-131">Zasoby w ramach udostępnionych są zoptymalizowane dla platformy docelowej, aby skrócić czas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c38f1-131">The assets in the shared framework are optimized for the target platform to improve application startup time.</span></span> <span data-ttu-id="c38f1-132">Aby uzyskać więcej informacji na temat udostępnionych ram, zobacz [.NET Core distribution packaging](../distribution-packaging.md).</span><span class="sxs-lookup"><span data-stu-id="c38f1-132">For more information about shared framework, see [.NET Core distribution packaging](../distribution-packaging.md).</span></span>

<span data-ttu-id="c38f1-133">Jeśli wersja *jest* określona, jest traktowana jako *minimalna* wersja ASP.NET core udostępnionej struktury dla wdrożeń zależnych od struktury i jako *dokładna* wersja dla wdrożeń samodzielnych.</span><span class="sxs-lookup"><span data-stu-id="c38f1-133">If a version *is* specified, it's treated as the *minimum* version of ASP.NET Core shared framework for framework-dependent deployments and as an *exact* version for self-contained deployments.</span></span> <span data-ttu-id="c38f1-134">Może to mieć następujące konsekwencje:</span><span class="sxs-lookup"><span data-stu-id="c38f1-134">This can have the following consequences:</span></span>

- <span data-ttu-id="c38f1-135">Jeśli wersja ASP.NET Core zainstalowana na serwerze jest mniejsza niż wersja określona w PackageReference, nie można uruchomić procesu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c38f1-135">If the version of ASP.NET Core installed on the server is less than the version specified on the PackageReference, the .NET Core process fails to launch.</span></span> <span data-ttu-id="c38f1-136">Aktualizacje metapakietu są często dostępne na NuGet.org przed udostępnieniem aktualizacji w środowiskach hostingu, takich jak Azure.</span><span class="sxs-lookup"><span data-stu-id="c38f1-136">Updates to the metapackage are often available on NuGet.org before updates have been made available in hosting environments such as Azure.</span></span> <span data-ttu-id="c38f1-137">Aktualizowanie wersji w packagereference do ASP.NET Core może spowodować niepowodzenie wdrożonej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c38f1-137">Updating the version on the PackageReference to ASP.NET Core could cause a deployed application to fail.</span></span>
- <span data-ttu-id="c38f1-138">Jeśli aplikacja jest wdrażana jako [samodzielne wdrożenie,](../deploying/index.md#publish-self-contained)aplikacja może nie zawierać najnowszych aktualizacji zabezpieczeń .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c38f1-138">If the application is deployed as a [self-contained deployment](../deploying/index.md#publish-self-contained), the application may not contain the latest security updates to .NET Core.</span></span> <span data-ttu-id="c38f1-139">Jeśli wersja nie jest określona, zestaw SDK może automatycznie dołączyć najnowszą wersję ASP.NET Core do samodzielnego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="c38f1-139">When a version isn't specified, the SDK can automatically include the newest version of ASP.NET Core in the self-contained deployment.</span></span>

## <a name="default-compilation-includes-in-net-core-projects"></a><span data-ttu-id="c38f1-140">Kompilacja domyślna zawiera projekty programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="c38f1-140">Default compilation includes in .NET Core projects</span></span>

<span data-ttu-id="c38f1-141">Wraz z przejściem do formatu *csproj* w najnowszych wersjach sdk, przenieśliśmy domyślne zawiera i wyklucza dla elementów kompilacji i osadzonych zasobów do plików właściwości SDK.</span><span class="sxs-lookup"><span data-stu-id="c38f1-141">With the move to the *csproj* format in the latest SDK versions, we've moved the default includes and excludes for compile items and embedded resources to the SDK properties files.</span></span> <span data-ttu-id="c38f1-142">Oznacza to, że nie trzeba już określać tych elementów w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-142">This means that you no longer need to specify these items in your project file.</span></span>

<span data-ttu-id="c38f1-143">Głównym powodem tego jest zmniejszenie bałaganu w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-143">The main reason for doing this is to reduce the clutter in your project file.</span></span> <span data-ttu-id="c38f1-144">Wartości domyślne, które są obecne w kiwce SDK powinny obejmować najczęstsze przypadki użycia, więc nie ma potrzeby, aby powtórzyć je w każdym projekcie, który tworzysz.</span><span class="sxs-lookup"><span data-stu-id="c38f1-144">The defaults that are present in the SDK should cover most common use cases, so there is no need to repeat them in every project that you create.</span></span> <span data-ttu-id="c38f1-145">Prowadzi to do mniejszych plików projektu, które są znacznie łatwiejsze do zrozumienia, a także edytować ręcznie, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="c38f1-145">This leads to smaller project files that are much easier to understand as well as edit by hand, if needed.</span></span>

<span data-ttu-id="c38f1-146">Poniższa tabela pokazuje, który element i [które globy](https://en.wikipedia.org/wiki/Glob_(programming)) są włączone i wyłączone w zestawie SDK:</span><span class="sxs-lookup"><span data-stu-id="c38f1-146">The following table shows which element and which [globs](https://en.wikipedia.org/wiki/Glob_(programming)) are both included and excluded in the SDK:</span></span>

| <span data-ttu-id="c38f1-147">Element</span><span class="sxs-lookup"><span data-stu-id="c38f1-147">Element</span></span>           | <span data-ttu-id="c38f1-148">Uwzględnij glob</span><span class="sxs-lookup"><span data-stu-id="c38f1-148">Include glob</span></span>                              | <span data-ttu-id="c38f1-149">Wykluczyć glob</span><span class="sxs-lookup"><span data-stu-id="c38f1-149">Exclude glob</span></span>                                                  | <span data-ttu-id="c38f1-150">Usuń glob</span><span class="sxs-lookup"><span data-stu-id="c38f1-150">Remove glob</span></span>              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| <span data-ttu-id="c38f1-151">Skompilować</span><span class="sxs-lookup"><span data-stu-id="c38f1-151">Compile</span></span>           | <span data-ttu-id="c38f1-152">\*\*/\*.cs (lub rozszerzenia innych języków)</span><span class="sxs-lookup"><span data-stu-id="c38f1-152">\*\*/\*.cs (or other language extensions)</span></span> | <span data-ttu-id="c38f1-153">\*\*/\*.user;  \*\*/\*. \*proj;  \* \* / \*  \* \* /.vssscc \*(vssscc)</span><span class="sxs-lookup"><span data-stu-id="c38f1-153">\*\*/\*.user;  \*\*/\*.\*proj;  \*\*/\*.sln;  \*\*/\*.vssscc</span></span>  | <span data-ttu-id="c38f1-154">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="c38f1-154">N/A</span></span>                      |
| <span data-ttu-id="c38f1-155">Osadzony zasób</span><span class="sxs-lookup"><span data-stu-id="c38f1-155">EmbeddedResource</span></span>  | <span data-ttu-id="c38f1-156">\*\*/\*.resx</span><span class="sxs-lookup"><span data-stu-id="c38f1-156">\*\*/\*.resx</span></span>                              | <span data-ttu-id="c38f1-157">\*\*/\*.user; \*\*/\*. \*proj; \* \* / \* \* \* /.vssscc \*(vssscc)</span><span class="sxs-lookup"><span data-stu-id="c38f1-157">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="c38f1-158">Nie dotyczy</span><span class="sxs-lookup"><span data-stu-id="c38f1-158">N/A</span></span>                      |
| <span data-ttu-id="c38f1-159">Brak</span><span class="sxs-lookup"><span data-stu-id="c38f1-159">None</span></span>              | \*\*/\*                                   | <span data-ttu-id="c38f1-160">\*\*/\*.user; \*\*/\*. \*proj; \* \* / \* \* \* /.vssscc \*(vssscc)</span><span class="sxs-lookup"><span data-stu-id="c38f1-160">\*\*/\*.user; \*\*/\*.\*proj; \*\*/\*.sln; \*\*/\*.vssscc</span></span>     | <span data-ttu-id="c38f1-161">\*\*/\*.cs; \* \* /.resx \*(resx)</span><span class="sxs-lookup"><span data-stu-id="c38f1-161">\*\*/\*.cs; \*\*/\*.resx</span></span>   |

> [!NOTE]
> <span data-ttu-id="c38f1-162">**Wyklucz glob** `./bin` zawsze `./obj` wyklucza i foldery, `$(BaseOutputPath)` które `$(BaseIntermediateOutputPath)` są reprezentowane przez i MSBuild właściwości, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="c38f1-162">**Exclude glob** always excludes the `./bin` and `./obj` folders, which are represented by the `$(BaseOutputPath)` and `$(BaseIntermediateOutputPath)` MSBuild properties, respectively.</span></span> <span data-ttu-id="c38f1-163">Jako całość, wszystkie wykluczenia `$(DefaultItemExcludes)`są reprezentowane przez .</span><span class="sxs-lookup"><span data-stu-id="c38f1-163">As a whole, all excludes are represented by `$(DefaultItemExcludes)`.</span></span>

<span data-ttu-id="c38f1-164">Jeśli masz globs w projekcie i spróbuj zbudować go przy użyciu najnowszego sdk, pojawi się następujący błąd:</span><span class="sxs-lookup"><span data-stu-id="c38f1-164">If you have globs in your project and you try to build it using the newest SDK, you'll get the following error:</span></span>

> <span data-ttu-id="c38f1-165">Zduplikowane elementy kompilacji zostały uwzględnione.</span><span class="sxs-lookup"><span data-stu-id="c38f1-165">Duplicate Compile items were included.</span></span> <span data-ttu-id="c38f1-166">Zestaw SDK .NET domyślnie zawiera elementy kompilacji z katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-166">The .NET SDK includes Compile items from your project directory by default.</span></span> <span data-ttu-id="c38f1-167">Można usunąć te elementy z pliku projektu lub ustawić właściwość "EnableDefaultCompileItems" na "false", jeśli chcesz jawnie uwzględnić je w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-167">You can either remove these items from your project file, or set the 'EnableDefaultCompileItems' property to 'false' if you want to explicitly include them in your project file.</span></span>

<span data-ttu-id="c38f1-168">Aby obejść ten błąd, można usunąć `Compile` elementy jawne, które pasują do elementów wymienionych w `<EnableDefaultCompileItems>` poprzedniej tabeli, lub ustawić właściwość na `false`, w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="c38f1-168">In order to get around this error, you can either remove the explicit `Compile` items that match the ones listed on the previous table, or you can set the `<EnableDefaultCompileItems>` property to `false`, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

<span data-ttu-id="c38f1-169">Ustawienie tej `false` właściwości spowoduje wyłączenie niejawnego włączenia, powracając do zachowania poprzednich zestawów SDK, w których trzeba było określić domyślne globy w projekcie.</span><span class="sxs-lookup"><span data-stu-id="c38f1-169">Setting this property to `false` will disable implicit inclusion, reverting to the behavior of previous SDKs where you had to specify the default globs in your project.</span></span>

<span data-ttu-id="c38f1-170">Ta zmiana nie modyfikuje głównej mechaniki innych obejmuje.</span><span class="sxs-lookup"><span data-stu-id="c38f1-170">This change does not modify the main mechanics of other includes.</span></span> <span data-ttu-id="c38f1-171">Jednak jeśli chcesz określić, na przykład, niektóre pliki, aby uzyskać opublikowane z aplikacją, nadal można użyć znanych `<Content>` mechanizmów w *csproj* do tego (na przykład element).</span><span class="sxs-lookup"><span data-stu-id="c38f1-171">However, if you wish to specify, for example, some files to get published with your app, you can still use the known mechanisms in *csproj* for that (for example, the `<Content>` element).</span></span>

<span data-ttu-id="c38f1-172">`<EnableDefaultCompileItems>`wyłącza tylko `Compile` globs, ale nie ma wpływu na `None` inne globs, \*jak niejawne glob, który odnosi się również do .cs elementów.</span><span class="sxs-lookup"><span data-stu-id="c38f1-172">`<EnableDefaultCompileItems>` only disables `Compile` globs but doesn't affect other globs, like the implicit `None` glob, which also applies to \*.cs items.</span></span> <span data-ttu-id="c38f1-173">Z tego powodu **Eksplorator rozwiązań** będzie nadal wyświetlał \*elementy .cs jako część projektu, uwzględnione jako `None` elementy.</span><span class="sxs-lookup"><span data-stu-id="c38f1-173">Because of that, **Solution Explorer** will continue show \*.cs items as part of the project, included as `None` items.</span></span> <span data-ttu-id="c38f1-174">W podobny sposób można `<EnableDefaultNoneItems>` ustawić false, aby `None` wyłączyć niejawny glob, w podobny sposób:</span><span class="sxs-lookup"><span data-stu-id="c38f1-174">In a similar way, you can set `<EnableDefaultNoneItems>` to false to disable the implicit `None` glob, like this:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

<span data-ttu-id="c38f1-175">Aby wyłączyć **wszystkie niejawne globs**, można ustawić `<EnableDefaultItems>` właściwość, `false` jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="c38f1-175">To disable **all implicit globs**, you can set the `<EnableDefaultItems>` property to `false` as in the following example:</span></span>

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a><span data-ttu-id="c38f1-176">Jak zobaczyć cały projekt jako MSBuild widzi go</span><span class="sxs-lookup"><span data-stu-id="c38f1-176">How to see the whole project as MSBuild sees it</span></span>

<span data-ttu-id="c38f1-177">Podczas gdy te zmiany csproj znacznie upraszczają pliki projektu, możesz chcieć zobaczyć w pełni rozwinięty projekt, ponieważ MSBuild widzi go po uwzględnieniu sdk i jego celów.</span><span class="sxs-lookup"><span data-stu-id="c38f1-177">While those csproj changes greatly simplify project files, you might want to see the fully expanded project as MSBuild sees it once the SDK and its targets are included.</span></span> <span data-ttu-id="c38f1-178">Wstępnie przetwórz projekt za [`dotnet msbuild`](dotnet-msbuild.md) pomocą [ `/pp` przełącznika](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) polecenia, które pokazuje, które pliki są importowane, ich źródła i ich wkład w budowę bez tworzenia projektu:</span><span class="sxs-lookup"><span data-stu-id="c38f1-178">Preprocess the project with [the `/pp` switch](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) of the [`dotnet msbuild`](dotnet-msbuild.md) command, which shows which files are imported, their sources, and their contributions to the build without actually building the project:</span></span>

`dotnet msbuild -pp:fullproject.xml`

<span data-ttu-id="c38f1-179">Jeśli projekt ma wiele struktur docelowych, wyniki polecenia powinny koncentrować się tylko na jednym z nich, określając go jako właściwość MSBuild:</span><span class="sxs-lookup"><span data-stu-id="c38f1-179">If the project has multiple target frameworks, the results of the command should be focused on only one of them by specifying it as an MSBuild property:</span></span>

`dotnet msbuild -p:TargetFramework=netcoreapp2.0 -pp:fullproject.xml`

## <a name="additions"></a><span data-ttu-id="c38f1-180">Dodatki</span><span class="sxs-lookup"><span data-stu-id="c38f1-180">Additions</span></span>

### <a name="sdk-attribute"></a><span data-ttu-id="c38f1-181">Atrybut Sdk</span><span class="sxs-lookup"><span data-stu-id="c38f1-181">Sdk attribute</span></span>

<span data-ttu-id="c38f1-182">Element `<Project>` główny pliku *csproj* ma nowy atrybut `Sdk`o nazwie .</span><span class="sxs-lookup"><span data-stu-id="c38f1-182">The root `<Project>` element of the *.csproj* file has a new attribute called `Sdk`.</span></span> <span data-ttu-id="c38f1-183">`Sdk`określa, który zestaw SDK będzie używany przez projekt.</span><span class="sxs-lookup"><span data-stu-id="c38f1-183">`Sdk` specifies which SDK will be used by the project.</span></span> <span data-ttu-id="c38f1-184">Zestaw SDK, jak [opisano w dokumencie warstwowym,](cli-msbuild-architecture.md) jest zestawem [zadań](/visualstudio/msbuild/msbuild-tasks) i [obiektów docelowych](/visualstudio/msbuild/msbuild-targets) MSBuild, które mogą tworzyć kod .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c38f1-184">The SDK, as the [layering document](cli-msbuild-architecture.md) describes, is a set of MSBuild [tasks](/visualstudio/msbuild/msbuild-tasks) and [targets](/visualstudio/msbuild/msbuild-targets) that can build .NET Core code.</span></span> <span data-ttu-id="c38f1-185">Dla programu .NET Core dostępne są następujące zestawy SDK:</span><span class="sxs-lookup"><span data-stu-id="c38f1-185">The following SDKs are available for .NET Core:</span></span>

1. <span data-ttu-id="c38f1-186">Zestaw SDK .NET Core o identyfikatorze`Microsoft.NET.Sdk`</span><span class="sxs-lookup"><span data-stu-id="c38f1-186">The .NET Core SDK with the ID of `Microsoft.NET.Sdk`</span></span>
2. <span data-ttu-id="c38f1-187">Internetowy zestaw SDK .NET Core o identyfikatorze`Microsoft.NET.Sdk.Web`</span><span class="sxs-lookup"><span data-stu-id="c38f1-187">The .NET Core web SDK with the ID of `Microsoft.NET.Sdk.Web`</span></span>
3. <span data-ttu-id="c38f1-188">Zestaw SDK biblioteki brzytwy .NET Core z identyfikatorem`Microsoft.NET.Sdk.Razor`</span><span class="sxs-lookup"><span data-stu-id="c38f1-188">The .NET Core Razor Class Library SDK with the ID of `Microsoft.NET.Sdk.Razor`</span></span>
4. <span data-ttu-id="c38f1-189">Usługa procesu roboczego .NET Core `Microsoft.NET.Sdk.Worker` o identyfikatorze (od .NET Core 3.0)</span><span class="sxs-lookup"><span data-stu-id="c38f1-189">The .NET Core Worker Service with the ID of `Microsoft.NET.Sdk.Worker` (since .NET Core 3.0)</span></span>
5. <span data-ttu-id="c38f1-190">.NET Core WinForms i WPF z `Microsoft.NET.Sdk.WindowsDesktop` identyfikatorem (od .NET Core 3.0)</span><span class="sxs-lookup"><span data-stu-id="c38f1-190">The .NET Core WinForms and WPF with the ID of `Microsoft.NET.Sdk.WindowsDesktop` (since .NET Core 3.0)</span></span>

<span data-ttu-id="c38f1-191">Aby użyć narzędzi `Sdk` .NET Core i utworzyć kod, należy ustawić atrybut do `<Project>` jednego z tych identyfikatorów elementu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-191">You need to have the `Sdk` attribute set to one of those IDs on the `<Project>` element in order to use the .NET Core tools and build your code.</span></span>

### <a name="packagereference"></a><span data-ttu-id="c38f1-192">Odwołanie do pakietu</span><span class="sxs-lookup"><span data-stu-id="c38f1-192">PackageReference</span></span>

<span data-ttu-id="c38f1-193">Element `<PackageReference>` określa zależność [NuGet w projekcie](/nuget/consume-packages/package-references-in-project-files).</span><span class="sxs-lookup"><span data-stu-id="c38f1-193">A `<PackageReference>` item element specifies a [NuGet dependency in the project](/nuget/consume-packages/package-references-in-project-files).</span></span> <span data-ttu-id="c38f1-194">Atrybut `Include` określa identyfikator pakietu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-194">The `Include` attribute specifies the package ID.</span></span>

```xml
<PackageReference Include="<package-id>" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a><span data-ttu-id="c38f1-195">Wersja</span><span class="sxs-lookup"><span data-stu-id="c38f1-195">Version</span></span>

<span data-ttu-id="c38f1-196">Wymagany `Version` atrybut określa wersję pakietu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="c38f1-196">The required `Version` attribute specifies the version of the package to restore.</span></span> <span data-ttu-id="c38f1-197">Atrybut jest zgodny z regułami schematu [przechowywanie wersji NuGet.](/nuget/reference/package-versioning#version-ranges-and-wildcards)</span><span class="sxs-lookup"><span data-stu-id="c38f1-197">The attribute respects the rules of the [NuGet versioning](/nuget/reference/package-versioning#version-ranges-and-wildcards) scheme.</span></span> <span data-ttu-id="c38f1-198">Zachowanie domyślne jest minimalna wersja, dopasowanie włącznie.</span><span class="sxs-lookup"><span data-stu-id="c38f1-198">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="c38f1-199">Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji `[1.2.3, )` NuGet i oznacza, że rozwiązany pakiet będzie miał wersję 1.2.3, jeśli jest dostępny lub większy w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="c38f1-199">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

#### <a name="includeassets-excludeassets-and-privateassets"></a><span data-ttu-id="c38f1-200">IncludeAssets, ExcludeAssets i PrivateAssets</span><span class="sxs-lookup"><span data-stu-id="c38f1-200">IncludeAssets, ExcludeAssets, and PrivateAssets</span></span>

<span data-ttu-id="c38f1-201">`IncludeAssets`atrybut określa, które zasoby należące `<PackageReference>` do pakietu określone przez powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="c38f1-201">`IncludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed.</span></span> <span data-ttu-id="c38f1-202">Domyślnie wszystkie zasoby pakietu są uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="c38f1-202">By default, all package assets are included.</span></span>

<span data-ttu-id="c38f1-203">`ExcludeAssets`atrybut określa, które zasoby należące `<PackageReference>` do pakietu określone przez nie powinny być używane.</span><span class="sxs-lookup"><span data-stu-id="c38f1-203">`ExcludeAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should not be consumed.</span></span>

<span data-ttu-id="c38f1-204">`PrivateAssets`atrybut określa, które zasoby należące `<PackageReference>` do pakietu określone przez powinny być zużyte, ale nie przepływają do następnego projektu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-204">`PrivateAssets` attribute specifies which assets belonging to the package specified by `<PackageReference>` should be consumed but not flow to the next project.</span></span> <span data-ttu-id="c38f1-205">Program `Analyzers` `Build` , `ContentFiles` i zasoby są domyślnie prywatne, gdy ten atrybut nie jest obecny.</span><span class="sxs-lookup"><span data-stu-id="c38f1-205">The `Analyzers`, `Build` and `ContentFiles` assets are private by default when this attribute is not present.</span></span>

> [!NOTE]
> <span data-ttu-id="c38f1-206">`PrivateAssets`jest odpowiednikiem *elementu project.json*/*xproj.* `SuppressParent`</span><span class="sxs-lookup"><span data-stu-id="c38f1-206">`PrivateAssets` is equivalent to the *project.json*/*xproj* `SuppressParent` element.</span></span>

<span data-ttu-id="c38f1-207">Atrybuty te mogą zawierać jeden lub więcej z następujących `;` elementów, oddzielonych znakiem średnika, jeśli na liście znajduje się więcej niż jeden:</span><span class="sxs-lookup"><span data-stu-id="c38f1-207">These attributes can contain one or more of the following items, separated by the semicolon `;` character if more than one is listed:</span></span>

- <span data-ttu-id="c38f1-208">`Compile`– zawartość folderu *lib* są dostępne do kompilacji przeciwko.</span><span class="sxs-lookup"><span data-stu-id="c38f1-208">`Compile` – the contents of the *lib* folder are available to compile against.</span></span>
- <span data-ttu-id="c38f1-209">`Runtime`– zawartość folderu *runtime* są dystrybuowane.</span><span class="sxs-lookup"><span data-stu-id="c38f1-209">`Runtime` – the contents of the *runtime* folder are distributed.</span></span>
- <span data-ttu-id="c38f1-210">`ContentFiles`– zawartość folderu *contentfiles* są używane.</span><span class="sxs-lookup"><span data-stu-id="c38f1-210">`ContentFiles` – the contents of the *contentfiles* folder are used.</span></span>
- <span data-ttu-id="c38f1-211">`Build`– używane są rekwizyty/obiekty docelowe w folderze *kompilacji.*</span><span class="sxs-lookup"><span data-stu-id="c38f1-211">`Build` – the props/targets in the *build* folder are used.</span></span>
- <span data-ttu-id="c38f1-212">`Native`– zawartość z zasobów macierzystych są kopiowane do folderu *wyjściowego* dla czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c38f1-212">`Native` – the contents from native assets are copied to the *output* folder for runtime.</span></span>
- <span data-ttu-id="c38f1-213">`Analyzers`– używane są analizatory.</span><span class="sxs-lookup"><span data-stu-id="c38f1-213">`Analyzers` – the analyzers are used.</span></span>

<span data-ttu-id="c38f1-214">Alternatywnie atrybut może zawierać:</span><span class="sxs-lookup"><span data-stu-id="c38f1-214">Alternatively, the attribute can contain:</span></span>

- <span data-ttu-id="c38f1-215">`None`– żaden z aktywów nie jest wykorzystywany.</span><span class="sxs-lookup"><span data-stu-id="c38f1-215">`None` – none of the assets are used.</span></span>
- <span data-ttu-id="c38f1-216">`All`– wszystkie aktywa są wykorzystywane.</span><span class="sxs-lookup"><span data-stu-id="c38f1-216">`All` – all assets are used.</span></span>

### <a name="dotnetclitoolreference"></a><span data-ttu-id="c38f1-217">DotNetCliToolOdwołanie</span><span class="sxs-lookup"><span data-stu-id="c38f1-217">DotNetCliToolReference</span></span>

<span data-ttu-id="c38f1-218">Element `<DotNetCliToolReference>` określa narzędzie CLI, które użytkownik chce przywrócić w kontekście projektu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-218">A `<DotNetCliToolReference>` item element specifies the CLI tool that the user wants to restore in the context of the project.</span></span> <span data-ttu-id="c38f1-219">Jest to zamiennik węzła w `tools` *project.json*.</span><span class="sxs-lookup"><span data-stu-id="c38f1-219">It's a replacement for the `tools` node in *project.json*.</span></span>

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

<span data-ttu-id="c38f1-220">Należy `DotNetCliToolReference` zauważyć, że jest [teraz przestarzałe](https://github.com/dotnet/announcements/issues/107) na rzecz [.NET Core Local Tools](https://aka.ms/local-tools).</span><span class="sxs-lookup"><span data-stu-id="c38f1-220">Note that `DotNetCliToolReference` is [now deprecated](https://github.com/dotnet/announcements/issues/107) in favor of [.NET Core Local Tools](https://aka.ms/local-tools).</span></span>

#### <a name="version"></a><span data-ttu-id="c38f1-221">Wersja</span><span class="sxs-lookup"><span data-stu-id="c38f1-221">Version</span></span>

<span data-ttu-id="c38f1-222">`Version`określa wersję pakietu do przywrócenia.</span><span class="sxs-lookup"><span data-stu-id="c38f1-222">`Version` specifies the version of the package to restore.</span></span> <span data-ttu-id="c38f1-223">Atrybut jest zgodny z regułami schematu [przechowywanie wersji NuGet.](/nuget/create-packages/dependency-versions#version-ranges)</span><span class="sxs-lookup"><span data-stu-id="c38f1-223">The attribute respects the rules of the [NuGet versioning](/nuget/create-packages/dependency-versions#version-ranges) scheme.</span></span> <span data-ttu-id="c38f1-224">Zachowanie domyślne jest minimalna wersja, dopasowanie włącznie.</span><span class="sxs-lookup"><span data-stu-id="c38f1-224">The default behavior is a minimum version, inclusive match.</span></span> <span data-ttu-id="c38f1-225">Na przykład określenie `Version="1.2.3"` jest odpowiednikiem notacji `[1.2.3, )` NuGet i oznacza, że rozwiązany pakiet będzie miał wersję 1.2.3, jeśli jest dostępny lub większy w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="c38f1-225">For example, specifying `Version="1.2.3"` is equivalent to NuGet notation `[1.2.3, )` and means the resolved package will have the version 1.2.3 if available or greater otherwise.</span></span>

### <a name="runtimeidentifiers"></a><span data-ttu-id="c38f1-226">Identyfikatory runtimeidentifiers</span><span class="sxs-lookup"><span data-stu-id="c38f1-226">RuntimeIdentifiers</span></span>

<span data-ttu-id="c38f1-227">Element `<RuntimeIdentifiers>` właściwości umożliwia określenie listy identyfikatorów czasu wykonywania [(RID)](../rid-catalog.md) rozdzielanych średnikami dla projektu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-227">The `<RuntimeIdentifiers>` property element lets you specify a semicolon-delimited list of [Runtime Identifiers (RIDs)](../rid-catalog.md) for the project.</span></span>
<span data-ttu-id="c38f1-228">IDENTYFIKATORY IDENTYFIKATORY umożliwiają publikowanie wdrożeń samodzielnych.</span><span class="sxs-lookup"><span data-stu-id="c38f1-228">RIDs enable publishing self-contained deployments.</span></span>

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a><span data-ttu-id="c38f1-229">Identyfikator czasu wykonywania</span><span class="sxs-lookup"><span data-stu-id="c38f1-229">RuntimeIdentifier</span></span>

<span data-ttu-id="c38f1-230">Element `<RuntimeIdentifier>` właściwości umożliwia określenie tylko jednego [identyfikatora wykonywania (RID)](../rid-catalog.md) dla projektu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-230">The `<RuntimeIdentifier>` property element allows you to specify only one [Runtime Identifier (RID)](../rid-catalog.md) for the project.</span></span> <span data-ttu-id="c38f1-231">RID umożliwia publikowanie niezależnego wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="c38f1-231">The RID enables publishing a self-contained deployment.</span></span>

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

<span data-ttu-id="c38f1-232">Użyj `<RuntimeIdentifiers>` (liczba mnoga) zamiast tego, jeśli trzeba opublikować dla wielu runii.</span><span class="sxs-lookup"><span data-stu-id="c38f1-232">Use `<RuntimeIdentifiers>` (plural) instead if you need to publish for multiple runtimes.</span></span> <span data-ttu-id="c38f1-233">`<RuntimeIdentifier>`może zapewnić szybsze kompilacje, gdy wymagany jest tylko jeden czas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c38f1-233">`<RuntimeIdentifier>` can provide faster builds when only a single runtime is required.</span></span>

### <a name="packagetargetfallback"></a><span data-ttu-id="c38f1-234">PackageTargetFallback (PackageTargetFallback)</span><span class="sxs-lookup"><span data-stu-id="c38f1-234">PackageTargetFallback</span></span>

<span data-ttu-id="c38f1-235">Element `<PackageTargetFallback>` właściwości umożliwia określenie zestawu zgodnych obiektów docelowych, które mają być używane podczas przywracania pakietów.</span><span class="sxs-lookup"><span data-stu-id="c38f1-235">The `<PackageTargetFallback>` property element allows you to specify a set of compatible targets to be used when restoring packages.</span></span> <span data-ttu-id="c38f1-236">Jest przeznaczony do zezwalania na pakiety, które używają dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) do pracy z pakietami, które nie deklarują dotnet TxM.</span><span class="sxs-lookup"><span data-stu-id="c38f1-236">It's designed to allow packages that use the dotnet [TxM (Target x Moniker)](/nuget/schema/target-frameworks) to operate with packages that don't declare a dotnet TxM.</span></span> <span data-ttu-id="c38f1-237">Jeśli projekt używa dotnet TxM, a następnie wszystkie pakiety, od których zależy, muszą mieć `<PackageTargetFallback>` również dotnet TxM, chyba że dodasz do projektu, aby umożliwić platformy inne niż dotnet być zgodne z dotnet.</span><span class="sxs-lookup"><span data-stu-id="c38f1-237">If your project uses the dotnet TxM, then all the packages it depends on must also have a dotnet TxM, unless you add the `<PackageTargetFallback>` to your project in order to allow non-dotnet platforms to be compatible with dotnet.</span></span>

<span data-ttu-id="c38f1-238">Poniższy przykład zawiera rezerwowe dla wszystkich obiektów docelowych w projekcie:</span><span class="sxs-lookup"><span data-stu-id="c38f1-238">The following example provides the fallbacks for all targets in your project:</span></span>

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

<span data-ttu-id="c38f1-239">W poniższym przykładzie określono rezerwowe `netcoreapp2.1` tylko dla obiektu docelowego:</span><span class="sxs-lookup"><span data-stu-id="c38f1-239">The following example specifies the fallbacks only for the `netcoreapp2.1` target:</span></span>

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp2.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a><span data-ttu-id="c38f1-240">Tworzenie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="c38f1-240">Build events</span></span>

<span data-ttu-id="c38f1-241">Sposób, w jaki zdarzenia pre-build i post-build są określone w pliku projektu został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="c38f1-241">The way that pre-build and post-build events are specified in the project file has changed.</span></span> <span data-ttu-id="c38f1-242">Właściwości PreBuildEvent i PostBuildEvent nie są zalecane w formacie projektu w stylu SDK, ponieważ makra, takie jak $(ProjectDir) nie są rozpoznawane.</span><span class="sxs-lookup"><span data-stu-id="c38f1-242">The properties PreBuildEvent and PostBuildEvent are not recommended in the SDK-style project format, because macros such as $(ProjectDir) are not resolved.</span></span> <span data-ttu-id="c38f1-243">Na przykład następujący kod nie jest już obsługiwany:</span><span class="sxs-lookup"><span data-stu-id="c38f1-243">For example, the following code is no longer supported:</span></span>

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

<span data-ttu-id="c38f1-244">W projektach w stylu zestawu SDK `PreBuild` `PostBuild` użyj obiektu `BeforeTargets` docelowego `PreBuild` MSBuild o nazwie lub ustaw właściwość dla lub `AfterTargets` właściwość dla `PostBuild`.</span><span class="sxs-lookup"><span data-stu-id="c38f1-244">In SDK-style projects, use an MSBuild target named `PreBuild` or `PostBuild` and set the `BeforeTargets` property for `PreBuild` or the `AfterTargets` property for `PostBuild`.</span></span> <span data-ttu-id="c38f1-245">W poprzednim przykładzie należy użyć następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="c38f1-245">For the preceding example, use the following code:</span></span>

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
><span data-ttu-id="c38f1-246">Można użyć dowolnej nazwy dla obiektów docelowych MSBuild, `PreBuild` `PostBuild` ale IDE programu Visual Studio rozpoznaje i cele, więc zaleca się przy użyciu tych nazw, dzięki czemu można edytować polecenia w programie Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="c38f1-246">You can use any name for the MSBuild targets, but the Visual Studio IDE recognizes `PreBuild` and `PostBuild` targets, so we recommend using those names so that you can edit the commands in the Visual Studio IDE.</span></span>

## <a name="nuget-metadata-properties"></a><span data-ttu-id="c38f1-247">NuGet właściwości metadanych</span><span class="sxs-lookup"><span data-stu-id="c38f1-247">NuGet metadata properties</span></span>

<span data-ttu-id="c38f1-248">Po przejściu do MSBuild przenieśliśmy metadane wejściowe, które są używane podczas pakowania pakietu NuGet z *project.json* do plików *.csproj.*</span><span class="sxs-lookup"><span data-stu-id="c38f1-248">With the move to MSBuild, we have moved the input metadata that is used when packing a NuGet package from *project.json* to *.csproj* files.</span></span> <span data-ttu-id="c38f1-249">Dane wejściowe są MSBuild właściwości, więc muszą `<PropertyGroup>` przejść w grupie.</span><span class="sxs-lookup"><span data-stu-id="c38f1-249">The inputs are MSBuild properties so they have to go within a `<PropertyGroup>` group.</span></span> <span data-ttu-id="c38f1-250">Poniżej przedstawiono listę właściwości, które są używane jako dane wejściowe `dotnet pack` do procesu `Pack` pakowania podczas korzystania z polecenia lub msbuild obiektu docelowego, który jest częścią sdk:</span><span class="sxs-lookup"><span data-stu-id="c38f1-250">The following is the list of properties that are used as inputs to the packing process when using the `dotnet pack` command or the `Pack` MSBuild target that is part of the SDK:</span></span>

### <a name="ispackable"></a><span data-ttu-id="c38f1-251">IsPackable (IsPackable)</span><span class="sxs-lookup"><span data-stu-id="c38f1-251">IsPackable</span></span>

<span data-ttu-id="c38f1-252">Wartość logiczna, która określa, czy projekt może być spakowany.</span><span class="sxs-lookup"><span data-stu-id="c38f1-252">A Boolean value that specifies whether the project can be packed.</span></span> <span data-ttu-id="c38f1-253">Wartością domyślną jest `true`.</span><span class="sxs-lookup"><span data-stu-id="c38f1-253">The default value is `true`.</span></span>

### <a name="packageversion"></a><span data-ttu-id="c38f1-254">PackageVersion</span><span class="sxs-lookup"><span data-stu-id="c38f1-254">PackageVersion</span></span>

<span data-ttu-id="c38f1-255">Określa wersję, którą będzie miał pakiet wynikowy.</span><span class="sxs-lookup"><span data-stu-id="c38f1-255">Specifies the version that the resulting package will have.</span></span> <span data-ttu-id="c38f1-256">Akceptuje wszystkie formy nuget ciąg wersji.</span><span class="sxs-lookup"><span data-stu-id="c38f1-256">Accepts all forms of NuGet version string.</span></span> <span data-ttu-id="c38f1-257">Domyślnie jest `$(Version)`wartość , czyli właściwości `Version` w projekcie.</span><span class="sxs-lookup"><span data-stu-id="c38f1-257">Default is the value of `$(Version)`, that is, of the property `Version` in the project.</span></span>

### <a name="packageid"></a><span data-ttu-id="c38f1-258">PackageId</span><span class="sxs-lookup"><span data-stu-id="c38f1-258">PackageId</span></span>

<span data-ttu-id="c38f1-259">Określa nazwę pakietu wynikowego.</span><span class="sxs-lookup"><span data-stu-id="c38f1-259">Specifies the name for the resulting package.</span></span> <span data-ttu-id="c38f1-260">Jeśli nie zostanie `pack` określony, operacja będzie `AssemblyName` domyślnie przy użyciu nazwy katalogu lub jako nazwy pakietu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-260">If not specified, the `pack` operation will default to using the `AssemblyName` or directory name as the name of the package.</span></span>

### <a name="title"></a><span data-ttu-id="c38f1-261">Tytuł</span><span class="sxs-lookup"><span data-stu-id="c38f1-261">Title</span></span>

<span data-ttu-id="c38f1-262">Przyjazny dla człowieka tytuł pakietu, zwykle używany w monitorach interfejsu użytkownika, jak na nuget.org i Menedżera pakietów w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c38f1-262">A human-friendly title of the package, typically used in UI displays as on nuget.org and the Package Manager in Visual Studio.</span></span> <span data-ttu-id="c38f1-263">Jeśli nie zostanie określony, zamiast tego używany jest identyfikator pakietu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-263">If not specified, the package ID is used instead.</span></span>

### <a name="authors"></a><span data-ttu-id="c38f1-264">Autorzy</span><span class="sxs-lookup"><span data-stu-id="c38f1-264">Authors</span></span>

<span data-ttu-id="c38f1-265">Oddzielona średnikami lista autorów pakietów, odpowiadająca nazwom profilów w nuget.org. Są one wyświetlane w galerii NuGet na nuget.org i są używane do pakietów odsyłaczy przez tych samych autorów.</span><span class="sxs-lookup"><span data-stu-id="c38f1-265">A semicolon-separated list of packages authors, matching the profile names on nuget.org. These are displayed in the NuGet Gallery on nuget.org and are used to cross-reference packages by the same authors.</span></span>

### <a name="packagedescription"></a><span data-ttu-id="c38f1-266">Opis pakietu</span><span class="sxs-lookup"><span data-stu-id="c38f1-266">PackageDescription</span></span>

<span data-ttu-id="c38f1-267">Długi opis pakietu dla wyświetlania interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c38f1-267">A long description of the package for UI display.</span></span>

### <a name="description"></a><span data-ttu-id="c38f1-268">Opis</span><span class="sxs-lookup"><span data-stu-id="c38f1-268">Description</span></span>

<span data-ttu-id="c38f1-269">Długi opis złożenia.</span><span class="sxs-lookup"><span data-stu-id="c38f1-269">A long description for the assembly.</span></span> <span data-ttu-id="c38f1-270">Jeśli `PackageDescription` nie zostanie określony, ta właściwość jest również używany jako opis pakietu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-270">If `PackageDescription` is not specified, then this property is also used as the description of the package.</span></span>

### <a name="copyright"></a><span data-ttu-id="c38f1-271">Prawa autorskie</span><span class="sxs-lookup"><span data-stu-id="c38f1-271">Copyright</span></span>

<span data-ttu-id="c38f1-272">Szczegóły dotyczące praw autorskich do pakietu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-272">Copyright details for the package.</span></span>

### <a name="packagerequirelicenseacceptance"></a><span data-ttu-id="c38f1-273">PackageRequireLicenseAkceptacja</span><span class="sxs-lookup"><span data-stu-id="c38f1-273">PackageRequireLicenseAcceptance</span></span>

<span data-ttu-id="c38f1-274">Wartość logiczna określająca, czy klient musi monitować konsumenta o zaakceptowanie licencji pakietu przed zainstalowaniem pakietu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-274">A Boolean value that specifies whether the client must prompt the consumer to accept the package license before installing the package.</span></span> <span data-ttu-id="c38f1-275">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="c38f1-275">The default is `false`.</span></span>

### <a name="developmentdependency"></a><span data-ttu-id="c38f1-276">Zależność rozwojowa</span><span class="sxs-lookup"><span data-stu-id="c38f1-276">DevelopmentDependency</span></span>

<span data-ttu-id="c38f1-277">Wartość logiczna, która określa, czy pakiet jest oznaczony jako zależność tylko do rozwoju, co uniemożliwia pakiet jest uwzględniany jako zależność w innych pakietach.</span><span class="sxs-lookup"><span data-stu-id="c38f1-277">A Boolean value that specifies whether the package is marked as a development-only dependency, which prevents the package from being included as a dependency in other packages.</span></span> <span data-ttu-id="c38f1-278">Z PackageReference (NuGet 4.8+), ta flaga oznacza również, że zasoby czasu kompilacji są wyłączone z kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c38f1-278">With PackageReference (NuGet 4.8+), this flag also means that compile-time assets are excluded from compilation.</span></span> <span data-ttu-id="c38f1-279">Aby uzyskać więcej informacji, zobacz [DevelopmentDependency support for PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span><span class="sxs-lookup"><span data-stu-id="c38f1-279">For more information, see [DevelopmentDependency support for PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).</span></span>

### <a name="packagelicenseexpression"></a><span data-ttu-id="c38f1-280">PackageLicenseExpression (Ekspresja license akce</span><span class="sxs-lookup"><span data-stu-id="c38f1-280">PackageLicenseExpression</span></span>

<span data-ttu-id="c38f1-281">Identyfikator lub wyrażenie [licencji SPDX.](https://spdx.org/licenses/)</span><span class="sxs-lookup"><span data-stu-id="c38f1-281">An [SPDX license identifier](https://spdx.org/licenses/) or expression.</span></span> <span data-ttu-id="c38f1-282">Na przykład `Apache-2.0`.</span><span class="sxs-lookup"><span data-stu-id="c38f1-282">For example, `Apache-2.0`.</span></span>

<span data-ttu-id="c38f1-283">Oto pełna lista [identyfikatorów licencji SPDX](https://spdx.org/licenses/).</span><span class="sxs-lookup"><span data-stu-id="c38f1-283">Here is the complete list of [SPDX license identifiers](https://spdx.org/licenses/).</span></span> <span data-ttu-id="c38f1-284">NuGet.org akceptuje tylko licencje zatwierdzone przez OSI lub FSF podczas korzystania z wyrażenia typu licencji.</span><span class="sxs-lookup"><span data-stu-id="c38f1-284">NuGet.org accepts only OSI or FSF approved licenses when using license type expression.</span></span>

<span data-ttu-id="c38f1-285">Dokładna składnia wyrażeń licencji jest opisana poniżej w [ABNF](https://tools.ietf.org/html/rfc5234).</span><span class="sxs-lookup"><span data-stu-id="c38f1-285">The exact syntax of the license expressions is described below in [ABNF](https://tools.ietf.org/html/rfc5234).</span></span>

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
> <span data-ttu-id="c38f1-286">Tylko jeden `PackageLicenseExpression` `PackageLicenseFile` z `PackageLicenseUrl` , i może być określony w czasie.</span><span class="sxs-lookup"><span data-stu-id="c38f1-286">Only one of `PackageLicenseExpression`, `PackageLicenseFile` and `PackageLicenseUrl` can be specified at a time.</span></span>

### <a name="packagelicensefile"></a><span data-ttu-id="c38f1-287">Plik LicenseFile packagelicense</span><span class="sxs-lookup"><span data-stu-id="c38f1-287">PackageLicenseFile</span></span>

<span data-ttu-id="c38f1-288">Ścieżka do pliku licencji w pakiecie, jeśli używasz licencji, której nie przypisano identyfikatora SPDX `PackageLicenseExpression` lub jest to licencja niestandardowa (w przeciwnym razie jest preferowana)</span><span class="sxs-lookup"><span data-stu-id="c38f1-288">Path to a license file within the package if you are using a license that hasn’t been assigned an SPDX identifier, or it is a custom license (Otherwise `PackageLicenseExpression` is preferred)</span></span>

<span data-ttu-id="c38f1-289">Zastępuje `PackageLicenseUrl`, nie można łączyć `PackageLicenseExpression`z , i wymaga programu Visual Studio w wersji 15.9.4 i .NET SDK 2.1.502 lub 2.2.101 lub nowsze.</span><span class="sxs-lookup"><span data-stu-id="c38f1-289">Replaces `PackageLicenseUrl`, can't be combined with `PackageLicenseExpression`, and requires Visual Studio version 15.9.4 and .NET SDK 2.1.502 or 2.2.101 or newer.</span></span>

<span data-ttu-id="c38f1-290">Należy upewnić się, że plik licencji jest spakowany przez dodanie go jawnie do projektu, przykład użycia:</span><span class="sxs-lookup"><span data-stu-id="c38f1-290">You will need to ensure the license file is packed by adding it explicitly to the project, example usage:</span></span>

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a><span data-ttu-id="c38f1-291">PackageLicenseUrl</span><span class="sxs-lookup"><span data-stu-id="c38f1-291">PackageLicenseUrl</span></span>

<span data-ttu-id="c38f1-292">Adres URL licencji, który ma zastosowanie do pakietu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-292">A URL to the license that is applicable to the package.</span></span> <span data-ttu-id="c38f1-293">(_przestarzałe od programu Visual Studio 15.9.4, .NET SDK 2.1.502 i 2.2.101_)</span><span class="sxs-lookup"><span data-stu-id="c38f1-293">(_deprecated since Visual Studio 15.9.4, .NET SDK 2.1.502 and 2.2.101_)</span></span>

### <a name="packageiconurl"></a><span data-ttu-id="c38f1-294">PackageIconUrl</span><span class="sxs-lookup"><span data-stu-id="c38f1-294">PackageIconUrl</span></span>

<span data-ttu-id="c38f1-295">Adres URL obrazu 64x64 z przezroczystym tłem do użycia jako ikony pakietu w wyświetlaczu interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c38f1-295">A URL for a 64x64 image with transparent background to use as the icon for the package in UI display.</span></span>

### <a name="packagereleasenotes"></a><span data-ttu-id="c38f1-296">PackageReleaseNotes (Informacje o wydaniu pakietów)</span><span class="sxs-lookup"><span data-stu-id="c38f1-296">PackageReleaseNotes</span></span>

<span data-ttu-id="c38f1-297">Zwolnij uwagi dotyczące pakietu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-297">Release notes for the package.</span></span>

### <a name="packagetags"></a><span data-ttu-id="c38f1-298">Tagi pakietów</span><span class="sxs-lookup"><span data-stu-id="c38f1-298">PackageTags</span></span>

<span data-ttu-id="c38f1-299">Rozdzielona średnikami lista znaczników wyznaczania pakietu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-299">A semicolon-delimited list of tags that designates the package.</span></span>

### <a name="packageoutputpath"></a><span data-ttu-id="c38f1-300">PackageOutputPath (PackageOutputPath)</span><span class="sxs-lookup"><span data-stu-id="c38f1-300">PackageOutputPath</span></span>

<span data-ttu-id="c38f1-301">Określa ścieżkę danych wyjściowych, w której pakiet zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="c38f1-301">Determines the output path in which the packed package will be dropped.</span></span> <span data-ttu-id="c38f1-302">Wartość domyślna to `$(OutputPath)`.</span><span class="sxs-lookup"><span data-stu-id="c38f1-302">Default is `$(OutputPath)`.</span></span>

### <a name="includesymbols"></a><span data-ttu-id="c38f1-303">Symbole includesymbole</span><span class="sxs-lookup"><span data-stu-id="c38f1-303">IncludeSymbols</span></span>
<span data-ttu-id="c38f1-304">Ta wartość logiczna wskazuje, czy pakiet powinien utworzyć pakiet dodatkowych symboli, gdy projekt jest pakowany.</span><span class="sxs-lookup"><span data-stu-id="c38f1-304">This Boolean value indicates whether the package should create an additional symbols package when the project is packed.</span></span> <span data-ttu-id="c38f1-305">Format pakietu symboli jest kontrolowany przez `SymbolPackageFormat` właściwość.</span><span class="sxs-lookup"><span data-stu-id="c38f1-305">The symbols package's format is controlled by the `SymbolPackageFormat` property.</span></span>

### <a name="symbolpackageformat"></a><span data-ttu-id="c38f1-306">SymbolPackageFormat</span><span class="sxs-lookup"><span data-stu-id="c38f1-306">SymbolPackageFormat</span></span>
<span data-ttu-id="c38f1-307">Określa format pakietu symboli.</span><span class="sxs-lookup"><span data-stu-id="c38f1-307">Specifies the format of the symbols package.</span></span> <span data-ttu-id="c38f1-308">Jeśli "symbols.nupkg", zostanie utworzony starszy pakiet symboli z rozszerzeniem *.symbols.nupkg* zawierającym pliki PDB, Biblioteki DLL i inne pliki wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="c38f1-308">If "symbols.nupkg", a legacy symbols package will be created with a *.symbols.nupkg* extension containing PDBs, DLLs, and other output files.</span></span> <span data-ttu-id="c38f1-309">Jeśli "snupkg", zostanie utworzony pakiet symbolu snupkg zawierający przenośne pdb.</span><span class="sxs-lookup"><span data-stu-id="c38f1-309">If "snupkg", a snupkg symbol package will be created containing the portable PDBs.</span></span> <span data-ttu-id="c38f1-310">Domyślnie jest to "symbols.nupkg".</span><span class="sxs-lookup"><span data-stu-id="c38f1-310">Default is "symbols.nupkg".</span></span>

### <a name="includesource"></a><span data-ttu-id="c38f1-311">Źródło include</span><span class="sxs-lookup"><span data-stu-id="c38f1-311">IncludeSource</span></span>

<span data-ttu-id="c38f1-312">Ta wartość logiczna wskazuje, czy proces pakowania powinien utworzyć pakiet źródłowy.</span><span class="sxs-lookup"><span data-stu-id="c38f1-312">This Boolean value indicates whether the pack process should create a source package.</span></span> <span data-ttu-id="c38f1-313">Pakiet źródłowy zawiera kod źródłowy biblioteki, a także pliki PDB.</span><span class="sxs-lookup"><span data-stu-id="c38f1-313">The source package contains the library's source code as well as PDB files.</span></span> <span data-ttu-id="c38f1-314">Pliki źródłowe są `src/ProjectName` umieszczane w katalogu w wynikowym pliku pakietu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-314">Source files are put under the `src/ProjectName` directory in the resulting package file.</span></span>

### <a name="istool"></a><span data-ttu-id="c38f1-315">Istool (Narzędzie IsTool)</span><span class="sxs-lookup"><span data-stu-id="c38f1-315">IsTool</span></span>

<span data-ttu-id="c38f1-316">Określa, czy wszystkie pliki wyjściowe są kopiowane do folderu *narzędzi* zamiast do folderu *lib.*</span><span class="sxs-lookup"><span data-stu-id="c38f1-316">Specifies whether all output files are copied to the *tools* folder instead of the *lib* folder.</span></span> <span data-ttu-id="c38f1-317">Różni się `DotNetCliTool`to od , który jest `PackageType` określony przez ustawienie w pliku *csproj.*</span><span class="sxs-lookup"><span data-stu-id="c38f1-317">This is different from a `DotNetCliTool`, which is specified by setting the `PackageType` in the *.csproj* file.</span></span>

### <a name="repositoryurl"></a><span data-ttu-id="c38f1-318">Adres repositoryurl</span><span class="sxs-lookup"><span data-stu-id="c38f1-318">RepositoryUrl</span></span>

<span data-ttu-id="c38f1-319">Określa adres URL repozytorium, w którym znajduje się kod źródłowy pakietu i/lub z którego jest on budowany.</span><span class="sxs-lookup"><span data-stu-id="c38f1-319">Specifies the URL for the repository where the source code for the package resides and/or from which it's being built.</span></span>

### <a name="repositorytype"></a><span data-ttu-id="c38f1-320">Typ repozytorium</span><span class="sxs-lookup"><span data-stu-id="c38f1-320">RepositoryType</span></span>

<span data-ttu-id="c38f1-321">Określa typ repozytorium.</span><span class="sxs-lookup"><span data-stu-id="c38f1-321">Specifies the type of the repository.</span></span> <span data-ttu-id="c38f1-322">Domyślnie jest "git".</span><span class="sxs-lookup"><span data-stu-id="c38f1-322">Default is "git".</span></span>

### <a name="repositorybranch"></a><span data-ttu-id="c38f1-323">Oddział repozytorium</span><span class="sxs-lookup"><span data-stu-id="c38f1-323">RepositoryBranch</span></span>
<span data-ttu-id="c38f1-324">Określa nazwę gałęzi źródłowej w repozytorium.</span><span class="sxs-lookup"><span data-stu-id="c38f1-324">Specifies the name of the source branch in the repository.</span></span> <span data-ttu-id="c38f1-325">Gdy projekt jest pakowany w pakiecie NuGet, jest dodawany do metadanych pakietu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-325">When the project is packaged in a NuGet package, it's added to the package metadata.</span></span>

### <a name="repositorycommit"></a><span data-ttu-id="c38f1-326">RepositoryCommit</span><span class="sxs-lookup"><span data-stu-id="c38f1-326">RepositoryCommit</span></span>
<span data-ttu-id="c38f1-327">Opcjonalne zatwierdzanie repozytorium lub zestaw zmian, aby wskazać, które źródło pakiet został zbudowany przeciwko.</span><span class="sxs-lookup"><span data-stu-id="c38f1-327">Optional repository commit or changeset to indicate which source the package was built against.</span></span> <span data-ttu-id="c38f1-328">`RepositoryUrl`należy również określić, aby ta właściwość została uwzględniona.</span><span class="sxs-lookup"><span data-stu-id="c38f1-328">`RepositoryUrl` must also be specified for this property to be included.</span></span> <span data-ttu-id="c38f1-329">Gdy projekt jest spakowany w pakiecie NuGet, to zatwierdzenie lub zestaw zmian jest dodawany do metadanych pakietu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-329">When the project is packaged in a NuGet package, this commit or changeset is added to the package metadata.</span></span>

### <a name="nopackageanalysis"></a><span data-ttu-id="c38f1-330">NoPackageAnalysis (Analiza bez pakietu)</span><span class="sxs-lookup"><span data-stu-id="c38f1-330">NoPackageAnalysis</span></span>

<span data-ttu-id="c38f1-331">Określa, że pakiet nie powinien uruchamiać analizy pakietu po utworzeniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-331">Specifies that pack should not run package analysis after building the package.</span></span>

### <a name="minclientversion"></a><span data-ttu-id="c38f1-332">MinClientVersion (Wersja MinClientVersion)</span><span class="sxs-lookup"><span data-stu-id="c38f1-332">MinClientVersion</span></span>

<span data-ttu-id="c38f1-333">Określa minimalną wersję klienta NuGet, który można zainstalować ten pakiet, wymuszane przez nuget.exe i Visual Studio Package Manager.</span><span class="sxs-lookup"><span data-stu-id="c38f1-333">Specifies the minimum version of the NuGet client that can install this package, enforced by nuget.exe and the Visual Studio Package Manager.</span></span>

### <a name="includebuildoutput"></a><span data-ttu-id="c38f1-334">IncludeBuildWyjście</span><span class="sxs-lookup"><span data-stu-id="c38f1-334">IncludeBuildOutput</span></span>

<span data-ttu-id="c38f1-335">Ta wartość logiczna określa, czy zestawy wyjściowe kompilacji powinny być pakowane do pliku *.nupkg,* czy nie.</span><span class="sxs-lookup"><span data-stu-id="c38f1-335">This Boolean value specifies whether the build output assemblies should be packed into the *.nupkg* file or not.</span></span>

### <a name="includecontentinpack"></a><span data-ttu-id="c38f1-336">Pakiet includecontentinpack</span><span class="sxs-lookup"><span data-stu-id="c38f1-336">IncludeContentInPack</span></span>

<span data-ttu-id="c38f1-337">Ta wartość logiczna określa, czy wszystkie `Content` elementy, które mają typ zostaną uwzględnione w pakiecie wynikowym automatycznie.</span><span class="sxs-lookup"><span data-stu-id="c38f1-337">This Boolean value specifies whether any items that have a type of `Content` will be included in the resulting package automatically.</span></span> <span data-ttu-id="c38f1-338">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="c38f1-338">The default is `true`.</span></span>

### <a name="buildoutputtargetfolder"></a><span data-ttu-id="c38f1-339">BuildOutputTargetFolder (Folder docelowy danych wyjściowych kompilacji)</span><span class="sxs-lookup"><span data-stu-id="c38f1-339">BuildOutputTargetFolder</span></span>

<span data-ttu-id="c38f1-340">Określa folder, w którym mają być umieszczane zestawy wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="c38f1-340">Specifies the folder where to place the output assemblies.</span></span> <span data-ttu-id="c38f1-341">Zestawy wyjściowe (i inne pliki wyjściowe) są kopiowane do odpowiednich folderów framework.</span><span class="sxs-lookup"><span data-stu-id="c38f1-341">The output assemblies (and other output files) are copied into their respective framework folders.</span></span>

### <a name="contenttargetfolders"></a><span data-ttu-id="c38f1-342">Foldery ContentTargetfolders</span><span class="sxs-lookup"><span data-stu-id="c38f1-342">ContentTargetFolders</span></span>

<span data-ttu-id="c38f1-343">Ta właściwość określa domyślną lokalizację, gdzie wszystkie `PackagePath` pliki zawartości powinny iść, jeśli nie jest określony dla nich.</span><span class="sxs-lookup"><span data-stu-id="c38f1-343">This property specifies the default location of where all the content files should go if `PackagePath` is not specified for them.</span></span> <span data-ttu-id="c38f1-344">Wartością domyślną jest "content;contentFiles".</span><span class="sxs-lookup"><span data-stu-id="c38f1-344">The default value is "content;contentFiles".</span></span>

### <a name="nuspecfile"></a><span data-ttu-id="c38f1-345">Plik NuspecFile</span><span class="sxs-lookup"><span data-stu-id="c38f1-345">NuspecFile</span></span>

<span data-ttu-id="c38f1-346">Ścieżka względna lub bezwzględna do pliku *nuspec* używanego do pakowania.</span><span class="sxs-lookup"><span data-stu-id="c38f1-346">Relative or absolute path to the *.nuspec* file being used for packing.</span></span>

> [!NOTE]
> <span data-ttu-id="c38f1-347">Jeśli plik *nuspec* jest określony, jest używany **wyłącznie** do pakowania informacji i wszelkie informacje w projektach nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="c38f1-347">If the *.nuspec* file is specified, it's used **exclusively** for packaging information and any information in the projects is not used.</span></span>

### <a name="nuspecbasepath"></a><span data-ttu-id="c38f1-348">Ścieżka NuspecBasePath</span><span class="sxs-lookup"><span data-stu-id="c38f1-348">NuspecBasePath</span></span>

<span data-ttu-id="c38f1-349">Ścieżka podstawowa dla pliku *nuspec.*</span><span class="sxs-lookup"><span data-stu-id="c38f1-349">Base path for the *.nuspec* file.</span></span>

### <a name="nuspecproperties"></a><span data-ttu-id="c38f1-350">Właściwości NuspecProperties</span><span class="sxs-lookup"><span data-stu-id="c38f1-350">NuspecProperties</span></span>

<span data-ttu-id="c38f1-351">Dwuśrednik oddzielona lista par klucz=wartość.</span><span class="sxs-lookup"><span data-stu-id="c38f1-351">Semicolon separated list of key=value pairs.</span></span>

## <a name="assemblyinfo-properties"></a><span data-ttu-id="c38f1-352">Właściwości AssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="c38f1-352">AssemblyInfo properties</span></span>

<span data-ttu-id="c38f1-353">[Atrybuty zestawu,](../../standard/assembly/set-attributes.md) które były zwykle obecne w pliku *AssemblyInfo* są teraz automatycznie generowane z właściwości.</span><span class="sxs-lookup"><span data-stu-id="c38f1-353">[Assembly attributes](../../standard/assembly/set-attributes.md) that were typically present in an *AssemblyInfo* file are now automatically generated from properties.</span></span>

### <a name="properties-per-attribute"></a><span data-ttu-id="c38f1-354">Właściwości na atrybut</span><span class="sxs-lookup"><span data-stu-id="c38f1-354">Properties per attribute</span></span>

<span data-ttu-id="c38f1-355">Jak pokazano w poniższej tabeli, każdy atrybut ma właściwość, która kontroluje jego zawartość, a inny, który wyłącza jego generacji:</span><span class="sxs-lookup"><span data-stu-id="c38f1-355">As shown in the following table, each attribute has a property that controls its content and another that disables its generation:</span></span>

| <span data-ttu-id="c38f1-356">Atrybut</span><span class="sxs-lookup"><span data-stu-id="c38f1-356">Attribute</span></span>                                                      | <span data-ttu-id="c38f1-357">Właściwość</span><span class="sxs-lookup"><span data-stu-id="c38f1-357">Property</span></span>               | <span data-ttu-id="c38f1-358">Właściwość do wyłączenia</span><span class="sxs-lookup"><span data-stu-id="c38f1-358">Property to disable</span></span>                             |
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

<span data-ttu-id="c38f1-359">Uwagi:</span><span class="sxs-lookup"><span data-stu-id="c38f1-359">Notes:</span></span>

- <span data-ttu-id="c38f1-360">`AssemblyVersion`i `FileVersion` domyślnie jest podjęcie `$(Version)` wartości bez sufiksu.</span><span class="sxs-lookup"><span data-stu-id="c38f1-360">`AssemblyVersion` and `FileVersion` default is to take the value of `$(Version)` without suffix.</span></span> <span data-ttu-id="c38f1-361">Na przykład, `$(Version)` `1.2.3-beta.4`jeśli jest , `1.2.3`a następnie wartość będzie .</span><span class="sxs-lookup"><span data-stu-id="c38f1-361">For example, if `$(Version)` is `1.2.3-beta.4`, then the value would be `1.2.3`.</span></span>
- <span data-ttu-id="c38f1-362">`InformationalVersion`domyślnie wartość . `$(Version)`</span><span class="sxs-lookup"><span data-stu-id="c38f1-362">`InformationalVersion` defaults to the value of `$(Version)`.</span></span>
- <span data-ttu-id="c38f1-363">`InformationalVersion`został `$(SourceRevisionId)` dołączony, jeśli nieruchomość jest obecna.</span><span class="sxs-lookup"><span data-stu-id="c38f1-363">`InformationalVersion` has `$(SourceRevisionId)` appended if the property is present.</span></span> <span data-ttu-id="c38f1-364">Można go wyłączyć `IncludeSourceRevisionInInformationalVersion`za pomocą .</span><span class="sxs-lookup"><span data-stu-id="c38f1-364">It can be disabled using `IncludeSourceRevisionInInformationalVersion`.</span></span>
- <span data-ttu-id="c38f1-365">`Copyright`i `Description` właściwości są również używane dla metadanych NuGet.</span><span class="sxs-lookup"><span data-stu-id="c38f1-365">`Copyright` and `Description` properties are also used for NuGet metadata.</span></span>
- <span data-ttu-id="c38f1-366">`Configuration`jest współużytkowany przez cały proces `--configuration` kompilacji i ustawiany za pomocą parametru `dotnet` poleceń.</span><span class="sxs-lookup"><span data-stu-id="c38f1-366">`Configuration` is shared with all the build process and set via the `--configuration` parameter of `dotnet` commands.</span></span>

### <a name="generateassemblyinfo"></a><span data-ttu-id="c38f1-367">Generuj informacje o zestawie</span><span class="sxs-lookup"><span data-stu-id="c38f1-367">GenerateAssemblyInfo</span></span>

<span data-ttu-id="c38f1-368">Wartość logiczna, która włącza lub wyłącza wszystkie generowanie AssemblyInfo.</span><span class="sxs-lookup"><span data-stu-id="c38f1-368">A Boolean that enable or disable all the AssemblyInfo generation.</span></span> <span data-ttu-id="c38f1-369">Wartością domyślną jest `true`.</span><span class="sxs-lookup"><span data-stu-id="c38f1-369">The default value is `true`.</span></span>

### <a name="generatedassemblyinfofile"></a><span data-ttu-id="c38f1-370">Wygenerowanyplik InfoAssembly</span><span class="sxs-lookup"><span data-stu-id="c38f1-370">GeneratedAssemblyInfoFile</span></span>

<span data-ttu-id="c38f1-371">Ścieżka wygenerowanego pliku informacji o zestawie.</span><span class="sxs-lookup"><span data-stu-id="c38f1-371">The path of the generated assembly info file.</span></span> <span data-ttu-id="c38f1-372">Domyślnie plik w `$(IntermediateOutputPath)` katalogu (obj).</span><span class="sxs-lookup"><span data-stu-id="c38f1-372">Default to a file in the `$(IntermediateOutputPath)` (obj) directory.</span></span>
