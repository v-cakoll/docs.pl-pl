---
title: Magazyn pakietu środowiska uruchomieniowego
description: Dowiedz się, jak używać magazynu pakietów środowiska wykonawczego do określania manifestów używanych przez program .NET Core.
ms.date: 08/12/2017
ms.openlocfilehash: ba3182b682e8a47397ac09ed46afe25190d34e5f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134272"
---
# <a name="runtime-package-store"></a><span data-ttu-id="aacb3-103">Magazyn pakietu środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="aacb3-103">Runtime package store</span></span>

<span data-ttu-id="aacb3-104">Począwszy od platformy .NET Core 2.0, można spakować i wdrożyć aplikacje względem znanego zestawu pakietów, które istnieją w środowisku docelowym.</span><span class="sxs-lookup"><span data-stu-id="aacb3-104">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="aacb3-105">Korzyści to szybsze wdrożenia, mniejsze użycie miejsca na dysku i zwiększona wydajność uruchamiania w niektórych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="aacb3-105">The benefits are faster deployments, lower disk space usage, and improved startup performance in some cases.</span></span>

<span data-ttu-id="aacb3-106">Ta funkcja jest implementowana jako *magazyn pakietów środowiska wykonawczego,* który jest katalogiem na dysku, na którym przechowywane są pakiety (zazwyczaj w */usr/local/share/dotnet/store* w systemie macOS/Linux i *C:/Program Files/dotnet/store* w systemie Windows).</span><span class="sxs-lookup"><span data-stu-id="aacb3-106">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="aacb3-107">W tym katalogu istnieją podkatalogi dla architektur i [struktur docelowych](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="aacb3-107">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="aacb3-108">Układ pliku jest podobny do sposobu, w jaki [zasoby NuGet są rozmieszczone na dysku:](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure)</span><span class="sxs-lookup"><span data-stu-id="aacb3-108">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

```
\dotnet
    \store
        \x64
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
        \x86
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
```

<span data-ttu-id="aacb3-109">Docelowy plik *manifestu* zawiera listę pakietów w magazynie pakietów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="aacb3-109">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="aacb3-110">Deweloperzy mogą kierować ten manifest podczas publikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aacb3-110">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="aacb3-111">Manifest docelowy jest zazwyczaj dostarczany przez właściciela docelowego środowiska produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="aacb3-111">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="aacb3-112">Przygotowywanie środowiska wykonawczego</span><span class="sxs-lookup"><span data-stu-id="aacb3-112">Preparing a runtime environment</span></span>

<span data-ttu-id="aacb3-113">Administrator środowiska wykonawczego może zoptymalizować aplikacje pod kątem szybszych wdrożeń i mniejszego wykorzystania miejsca na dysku, tworząc magazyn pakietów środowiska wykonawczego i odpowiedni manifest docelowy.</span><span class="sxs-lookup"><span data-stu-id="aacb3-113">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="aacb3-114">Pierwszym krokiem jest utworzenie *manifestu magazynu pakietów,* który zawiera listę pakietów, które tworzą magazyn pakietów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="aacb3-114">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="aacb3-115">Ten format pliku jest zgodny z formatem pliku projektu (*csproj*).</span><span class="sxs-lookup"><span data-stu-id="aacb3-115">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="NUGET_PACKAGE" Version="VERSION" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="aacb3-116">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="aacb3-116">**Example**</span></span>

<span data-ttu-id="aacb3-117">Następujące przykładowe manifest magazynu pakietu (*packages.csproj*) służy do dodawania [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) i [`Moq`](https://www.nuget.org/packages/moq/) do magazynu pakietów środowiska wykonawczego:</span><span class="sxs-lookup"><span data-stu-id="aacb3-117">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="aacb3-118">Aprowizuj magazyn pakietów środowiska wykonawczego, wykonując `dotnet store` z manifestem magazynu pakietów, środowiska wykonawczego i struktury:</span><span class="sxs-lookup"><span data-stu-id="aacb3-118">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="aacb3-119">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="aacb3-119">**Example**</span></span>

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="aacb3-120">Można przekazać wiele ścieżek manifestu magazynu [`dotnet store`](../tools/dotnet-store.md) pakietów docelowych do pojedynczego polecenia, powtarzając opcję i ścieżkę w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="aacb3-120">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="aacb3-121">Domyślnie dane wyjściowe polecenia jest magazyn pakietów w podkatalogu *.dotnet/store* profilu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="aacb3-121">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="aacb3-122">Za pomocą `--output <OUTPUT_DIRECTORY>` tej opcji można określić inną lokalizację.</span><span class="sxs-lookup"><span data-stu-id="aacb3-122">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="aacb3-123">Katalog główny magazynu zawiera docelowy plik *artifact.xml* manifestu.</span><span class="sxs-lookup"><span data-stu-id="aacb3-123">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="aacb3-124">Ten plik może być dostępny do pobrania i być używany przez autorów aplikacji, którzy chcą kierować ten magazyn podczas publikowania.</span><span class="sxs-lookup"><span data-stu-id="aacb3-124">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="aacb3-125">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="aacb3-125">**Example**</span></span>

<span data-ttu-id="aacb3-126">Następujący plik *artifact.xml* jest produkowany po uruchomieniu poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="aacb3-126">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="aacb3-127">Należy [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) zauważyć, że `Moq`jest zależność , więc jest automatycznie uwzględniane i pojawia się w pliku manifestu *artifacts.xml.*</span><span class="sxs-lookup"><span data-stu-id="aacb3-127">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="aacb3-128">Publikowanie aplikacji względem manifestu docelowego</span><span class="sxs-lookup"><span data-stu-id="aacb3-128">Publishing an app against a target manifest</span></span>

<span data-ttu-id="aacb3-129">Jeśli masz docelowy plik manifestu na dysku, należy określić ścieżkę do pliku podczas publikowania aplikacji za pomocą [`dotnet publish`](../tools/dotnet-publish.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="aacb3-129">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="aacb3-130">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="aacb3-130">**Example**</span></span>

```dotnetcli
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="aacb3-131">Można wdrożyć wynikową opublikowaną aplikację do środowiska, które ma pakiety opisane w manifeście docelowym.</span><span class="sxs-lookup"><span data-stu-id="aacb3-131">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="aacb3-132">W przeciwnym razie powoduje, że aplikacja nie może się uruchomić.</span><span class="sxs-lookup"><span data-stu-id="aacb3-132">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="aacb3-133">Określ wiele manifestów docelowych podczas publikowania aplikacji, powtarzając `--manifest manifest1.xml --manifest manifest2.xml`opcję i ścieżkę (na przykład ).</span><span class="sxs-lookup"><span data-stu-id="aacb3-133">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="aacb3-134">Po wykonaniu tej sprawy aplikacja jest przycinana dla unii pakietów określonych w plikach manifestu docelowego dostarczonych do polecenia.</span><span class="sxs-lookup"><span data-stu-id="aacb3-134">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="aacb3-135">Określanie manifestów docelowych w pliku projektu</span><span class="sxs-lookup"><span data-stu-id="aacb3-135">Specifying target manifests in the project file</span></span>

<span data-ttu-id="aacb3-136">Alternatywą dla określania manifestów [`dotnet publish`](../tools/dotnet-publish.md) docelowych za pomocą polecenia jest określenie ich w pliku projektu jako listy ścieżek oddzielonych średnikami pod tagiem \*\* \<targetmanifestfiles>.\*\*</span><span class="sxs-lookup"><span data-stu-id="aacb3-136">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="aacb3-137">Określ manifesty docelowe w pliku projektu tylko wtedy, gdy środowisko docelowe dla aplikacji jest dobrze znane, na przykład dla projektów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="aacb3-137">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="aacb3-138">Nie dotyczy to projektów typu open source.</span><span class="sxs-lookup"><span data-stu-id="aacb3-138">This isn't the case for open-source projects.</span></span> <span data-ttu-id="aacb3-139">Użytkownicy projektu typu open source zazwyczaj wdrażają go w różnych środowiskach produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="aacb3-139">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="aacb3-140">Te środowiska produkcyjne zazwyczaj mają różne zestawy pakietów wstępnie zainstalowanych.</span><span class="sxs-lookup"><span data-stu-id="aacb3-140">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="aacb3-141">Nie można zakładać manifestu docelowego w takich środowiskach, `--manifest` więc [`dotnet publish`](../tools/dotnet-publish.md)należy użyć opcji .</span><span class="sxs-lookup"><span data-stu-id="aacb3-141">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store"></a><span data-ttu-id="aacb3-142">ASP.NET Magazyn niejawny Core</span><span class="sxs-lookup"><span data-stu-id="aacb3-142">ASP.NET Core implicit store</span></span>

<span data-ttu-id="aacb3-143">Magazyn niejawny ASP.NET Core ma zastosowanie tylko do ASP.NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="aacb3-143">The ASP.NET Core implicit store applies only to ASP.NET Core 2.0.</span></span> <span data-ttu-id="aacb3-144">Zdecydowanie zaleca się aplikacje używać ASP.NET Core 2.1 i nowsze, który **nie** używa magazynu niejawne.</span><span class="sxs-lookup"><span data-stu-id="aacb3-144">We strongly recommend applications use ASP.NET Core 2.1 and later, which does **not** use the implicit store.</span></span> <span data-ttu-id="aacb3-145">ASP.NET Core 2.1 i nowszych korzystać z udostępnionej struktury.</span><span class="sxs-lookup"><span data-stu-id="aacb3-145">ASP.NET Core 2.1 and later use the shared framework.</span></span>

<span data-ttu-id="aacb3-146">Funkcja magazynu pakietów środowiska uruchomieniowego jest używana niejawnie przez aplikację ASP.NET Core, gdy aplikacja jest wdrażana jako aplikacja [wdrożenia zależnego od struktury (FDD).](index.md#publish-runtime-dependent)</span><span class="sxs-lookup"><span data-stu-id="aacb3-146">The runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [framework-dependent deployment (FDD)](index.md#publish-runtime-dependent) app.</span></span> <span data-ttu-id="aacb3-147">Obiekty docelowe obejmują [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) manifesty odwołujące się do magazynu pakietów niejawnych w systemie docelowym.</span><span class="sxs-lookup"><span data-stu-id="aacb3-147">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="aacb3-148">Ponadto każda aplikacja FDD, która `Microsoft.AspNetCore.All` zależy od pakietu powoduje, że opublikowana aplikacja, która zawiera tylko `Microsoft.AspNetCore.All` aplikację i jej zasoby, a nie pakiety wymienione w metapakiet.</span><span class="sxs-lookup"><span data-stu-id="aacb3-148">Additionally, any FDD app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="aacb3-149">Zakłada się, że te pakiety są obecne w systemie docelowym.</span><span class="sxs-lookup"><span data-stu-id="aacb3-149">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="aacb3-150">Magazyn pakietów środowiska wykonawczego jest instalowany na hoście po zainstalowaniu zestawu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="aacb3-150">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="aacb3-151">Inni instalatorzy mogą udostępniać magazyn pakietów środowiska wykonawczego, w tym instalacje `apt-get`zip/tarball zestawu .NET Core SDK, Red Hat Yum, pakiet hostingu systemu .NET Core Windows Server i ręczne instalacje magazynu pakietów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="aacb3-151">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="aacb3-152">Podczas wdrażania aplikacji [wdrożenia zależnego od struktury (FDD)](index.md#publish-runtime-dependent) upewnij się, że środowisko docelowe ma zainstalowany pakiet .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="aacb3-152">When deploying a [framework-dependent deployment (FDD)](index.md#publish-runtime-dependent) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="aacb3-153">Jeśli aplikacja jest wdrażana w środowisku, które nie zawiera ASP.NET Core, można zrezygnować z magazynu niejawnego, określając \*\* \<PublishWithAspNetCoreTargetManifest>\*\* ustawiona `false` w pliku projektu, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="aacb3-153">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="aacb3-154">W przypadku aplikacji [niezależnego wdrażania (SCD)](index.md#publish-self-contained) zakłada się, że system docelowy nie musi zawierać wymaganych pakietów manifestu.</span><span class="sxs-lookup"><span data-stu-id="aacb3-154">For [self-contained deployment (SCD)](index.md#publish-self-contained) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="aacb3-155">W związku z tym \*\* \<PublishWithAspNetCoreTargetManifest\*\*>`true` nie można ustawić dla aplikacji SCD.</span><span class="sxs-lookup"><span data-stu-id="aacb3-155">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an SCD app.</span></span>

<span data-ttu-id="aacb3-156">Jeśli wdrożysz aplikację z zależnością manifestu, która jest obecna we wdrożeniu (zestaw jest obecny w folderze *bin),* magazyn pakietów środowiska wykonawczego *nie jest używany* na hoście dla tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="aacb3-156">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="aacb3-157">Zestaw folderów *pojemnika* jest używany niezależnie od jego obecności w magazynie pakietów środowiska wykonawczego na hoście.</span><span class="sxs-lookup"><span data-stu-id="aacb3-157">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="aacb3-158">Wersja zależności wskazana w manifeście musi być zgodna z wersją zależności w magazynie pakietów środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="aacb3-158">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="aacb3-159">Jeśli masz niezgodność wersji między zależności w manifeście docelowym i wersji, która istnieje w magazynie pakietów środowiska wykonawczego i aplikacja nie zawiera wymaganej wersji pakietu w jego wdrożeniu, aplikacja nie można uruchomić.</span><span class="sxs-lookup"><span data-stu-id="aacb3-159">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="aacb3-160">Wyjątek zawiera nazwę manifestu docelowego, który jest wywoływany dla zestawu magazynu pakietów środowiska wykonawczego, co ułatwia rozwiązywanie problemów z niezgodnością.</span><span class="sxs-lookup"><span data-stu-id="aacb3-160">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="aacb3-161">Gdy wdrożenie jest *przycinane* na publikowanie, tylko określone wersje pakietów manifestu, które wskazujesz, są wstrzymane z opublikowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="aacb3-161">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="aacb3-162">Pakiety w wskazanych wersjach muszą być obecne na hoście, aby aplikacja została uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="aacb3-162">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="see-also"></a><span data-ttu-id="aacb3-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aacb3-163">See also</span></span>

- [<span data-ttu-id="aacb3-164">dotnet-publikować</span><span class="sxs-lookup"><span data-stu-id="aacb3-164">dotnet-publish</span></span>](../tools/dotnet-publish.md)
- [<span data-ttu-id="aacb3-165">sklep dotnet</span><span class="sxs-lookup"><span data-stu-id="aacb3-165">dotnet-store</span></span>](../tools/dotnet-store.md)
