---
title: Magazyn pakietu środowiska uruchomieniowego
description: Dowiedz się, jak używać Magazyn pakietu środowiska uruchomieniowego do manifesty docelowy używany przez platformy .NET Core.
author: bleroy
ms.date: 08/12/2017
ms.custom: seodec18
ms.openlocfilehash: 2f37e0de4b6fcb1b2047470b0a9df3753fe87d71
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614365"
---
# <a name="runtime-package-store"></a><span data-ttu-id="c9e7c-103">Magazyn pakietu środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c9e7c-103">Runtime package store</span></span>

<span data-ttu-id="c9e7c-104">Począwszy od programu .NET Core 2.0, istnieje możliwość pakować i wdrażać aplikacje przed znanych zestaw pakietów, które istnieją w środowisku docelowym.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-104">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="c9e7c-105">Korzyści są szybsze wdrożenia, niższe użycie miejsca na dysku i wydajności uruchamiania ulepszone w niektórych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-105">The benefits are faster deployments, lower disk space usage, and improved startup performance in some cases.</span></span>

<span data-ttu-id="c9e7c-106">Ta funkcja jest implementowany jako *Magazyn pakietu środowiska uruchomieniowego*, który jest katalogiem na dysku, na którym przechowywane są pakiety (zwykle znajduje się w */usr/local/share/dotnet/store* w systemie macOS/Linux i *C: / Program plików/dotnet/store* na Windows).</span><span class="sxs-lookup"><span data-stu-id="c9e7c-106">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="c9e7c-107">W tym katalogu istnieją podkatalogów dla architektury i [ustalać platformy docelowe](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="c9e7c-107">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="c9e7c-108">Układ pliku jest podobny sposób, który [NuGet zasoby są ułożone w na dysku](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span><span class="sxs-lookup"><span data-stu-id="c9e7c-108">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

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

<span data-ttu-id="c9e7c-109">A *target manifestem* plik listy pakietów w Magazyn pakietu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-109">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="c9e7c-110">Deweloperzy mogą kierować tego manifestu, podczas publikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-110">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="c9e7c-111">Manifest docelowy jest zwykle zapewniany przez właściciela w środowisku produkcyjnym docelowych.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-111">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="c9e7c-112">Przygotowywanie środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="c9e7c-112">Preparing a runtime environment</span></span>

<span data-ttu-id="c9e7c-113">Administrator środowiska uruchomieniowego, można zoptymalizować aplikacje dla wdrożeń szybciej i niższym użycie miejsca na dysku, tworząc Magazyn pakietu środowiska uruchomieniowego i odpowiedniego manifestu docelowego.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-113">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="c9e7c-114">Pierwszym krokiem jest utworzenie *manifestu sklepu pakietu* , zawiera listę pakietów, które tworzą magazyn pakietu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-114">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="c9e7c-115">Ten format jest zgodny z formatem pliku projektu (*csproj*).</span><span class="sxs-lookup"><span data-stu-id="c9e7c-115">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="c9e7c-116">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c9e7c-116">**Example**</span></span>

<span data-ttu-id="c9e7c-117">Poniższy przykład pakietów manifestu Sklepu (*packages.csproj*) służy do dodawania [ `Newtonsoft.Json` ](https://www.nuget.org/packages/Newtonsoft.Json/) i [ `Moq` ](https://www.nuget.org/packages/moq/) do Magazyn pakietu środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="c9e7c-117">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="c9e7c-118">Aprowizuj Magazyn pakietu środowiska uruchomieniowego, wykonując `dotnet store` z manifestu Magazyn pakietu środowiska uruchomieniowego i framework:</span><span class="sxs-lookup"><span data-stu-id="c9e7c-118">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```console
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="c9e7c-119">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c9e7c-119">**Example**</span></span>

```console
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="c9e7c-120">Wiele ścieżek manifestu pakietu magazynu docelowego można przekazać do pojedynczego [ `dotnet store` ](../tools/dotnet-store.md) polecenia, powtarzając opcja i ścieżki w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-120">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="c9e7c-121">Domyślnie dane wyjściowe polecenia jest Magazyn pakietu, w obszarze *.dotnet/store* podkatalogu profilu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-121">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="c9e7c-122">Możesz określić inną lokalizację, w którym używana jest `--output <OUTPUT_DIRECTORY>` opcji.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-122">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="c9e7c-123">Katalog główny magazyn zawiera manifest docelowej *artifact.xml* pliku.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-123">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="c9e7c-124">Ten plik może być udostępniane do pobrania i używane przez autorów aplikacji, którzy ma pod kątem tego magazynu podczas publikowania.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-124">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="c9e7c-125">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c9e7c-125">**Example**</span></span>

<span data-ttu-id="c9e7c-126">Następujące *artifact.xml* po uruchomieniu w poprzednim przykładzie jest tworzony plik.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-126">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="c9e7c-127">Należy pamiętać, że [ `Castle.Core` ](https://www.nuget.org/packages/Castle.Core/) zależą od elementu `Moq`, więc jest automatycznie włączone i pojawia się w *artifacts.xml* pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-127">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="c9e7c-128">Publikowanie aplikacji względem manifest docelowej</span><span class="sxs-lookup"><span data-stu-id="c9e7c-128">Publishing an app against a target manifest</span></span>

<span data-ttu-id="c9e7c-129">Jeśli masz plik manifestu docelowego na dysku, określ ścieżkę do pliku podczas publikowania aplikacji za pomocą [ `dotnet publish` ](../tools/dotnet-publish.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="c9e7c-129">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```console
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="c9e7c-130">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="c9e7c-130">**Example**</span></span>

```console
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="c9e7c-131">Możesz wdrożyć wynikowy opublikowanej aplikacji w środowisku, który zawiera pakiety, opisane w manifeście docelowego.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-131">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="c9e7c-132">Powoduje niepowodzenie w tym aplikacji, nie można uruchomić.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-132">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="c9e7c-133">Określ wiele manifesty docelowego podczas publikowania aplikacji, powtarzając opcji i ścieżki (na przykład `--manifest manifest1.xml --manifest manifest2.xml`).</span><span class="sxs-lookup"><span data-stu-id="c9e7c-133">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="c9e7c-134">Jeśli tak zrobisz, aplikacja są spacje dla Unii pakiety określone w plikach manifestu docelowej dostarczane do polecenia.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-134">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="c9e7c-135">Określanie manifesty docelowy w pliku projektu</span><span class="sxs-lookup"><span data-stu-id="c9e7c-135">Specifying target manifests in the project file</span></span>

<span data-ttu-id="c9e7c-136">Zamiast określania docelowej manifesty za pomocą [ `dotnet publish` ](../tools/dotnet-publish.md) ma je określić w pliku projektu jako Rozdzielana średnikami lista ścieżek w obszarze polecenie  **\<TargetManifestFiles >** tagu.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-136">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="c9e7c-137">Manifesty docelowego należy określić w pliku projektu tylko wtedy, gdy środowisko docelowe dla aplikacji jest dobrze znanych, takich jak dla projektów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-137">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="c9e7c-138">Nie jest to w przypadku projektów typu open source.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-138">This isn't the case for open-source projects.</span></span> <span data-ttu-id="c9e7c-139">Użytkownicy projektu open-source zazwyczaj wdrożyć ją na środowisko produkcyjne różne.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-139">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="c9e7c-140">Tych środowisk produkcyjnych zazwyczaj mają różne zestawy wstępnie zainstalowane pakiety.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-140">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="c9e7c-141">Nie możesz wprowadzać założeń dotyczących manifestu docelowego w takich środowiskach, więc zaleca się użycie `--manifest` opcji [ `dotnet publish` ](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="c9e7c-141">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store"></a><span data-ttu-id="c9e7c-142">Niejawne magazynu platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c9e7c-142">ASP.NET Core implicit store</span></span>

<span data-ttu-id="c9e7c-143">Magazyn niejawne platformy ASP.NET Core dotyczy tylko programu ASP.NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-143">The ASP.NET Core implicit store applies only to ASP.NET Core 2.0.</span></span> <span data-ttu-id="c9e7c-144">Zdecydowanie zalecamy aplikacje używają platformy ASP.NET Core 2.1 lub nowszą wersją, która obsługuje **nie** Użycie niejawnej magazynu.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-144">We strongly recommend applications use ASP.NET Core 2.1 and later, which does **not** use the implicit store.</span></span> <span data-ttu-id="c9e7c-145">I późniejszego użycia udostępnionej platformy ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-145">ASP.NET Core 2.1 and later use the shared framework.</span></span>

<span data-ttu-id="c9e7c-146">Funkcja Magazyn pakietu środowiska uruchomieniowego jest używany niejawnie przez aplikację ASP.NET Core gdy aplikacja jest wdrożona jako [zależny od struktury wdrożenia (stacje)](index.md#framework-dependent-deployments-fdd) aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-146">The runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [framework-dependent deployment (FDD)](index.md#framework-dependent-deployments-fdd) app.</span></span> <span data-ttu-id="c9e7c-147">Obiekty docelowe w [ `Microsoft.NET.Sdk.Web` ](https://github.com/aspnet/websdk) obejmują manifesty odwołujące się do niejawnego Magazyn pakietu w systemie docelowym.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-147">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="c9e7c-148">Ponadto żadnej aplikacji Dyskietki, która jest zależna od `Microsoft.AspNetCore.All` pakietu wyniki w opublikowanej aplikacji, która zawiera tylko aplikacji i jej zasoby i nie pakiety, które zostały wymienione w `Microsoft.AspNetCore.All` meta Microsoft.aspnetcore.all.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-148">Additionally, any FDD app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="c9e7c-149">Zakłada się, że te pakiety są obecne w systemie docelowym.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-149">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="c9e7c-150">Magazyn pakietu środowiska uruchomieniowego jest zainstalowany na hoście, gdy jest zainstalowany zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-150">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="c9e7c-151">Inne pliki instalacyjne może udostępnić Magazyn pakietu środowiska uruchomieniowego, w tym pliku Zip/tar instalacji programu .NET Core SDK `apt-get`, Red Hat Yum, pakiet .NET Core systemu Windows serwer obsługujący i instalacje Magazyn pakietu środowiska uruchomieniowego ręczne.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-151">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="c9e7c-152">W przypadku wdrażania [zależny od struktury wdrożenia (stacje)](index.md#framework-dependent-deployments-fdd) aplikacji, upewnij się, że środowisko docelowe ma zainstalowany zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-152">When deploying a [framework-dependent deployment (FDD)](index.md#framework-dependent-deployments-fdd) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="c9e7c-153">Jeśli aplikacja jest wdrażana w środowisku, który nie zawiera programu ASP.NET Core, można zrezygnować z niejawne magazynu, określając  **\<PublishWithAspNetCoreTargetManifest >** równa `false` w pliku projektu, podobnie jak w Poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="c9e7c-153">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="c9e7c-154">Aby uzyskać [niezależna wdrożenia (— SCD)](index.md#self-contained-deployments-scd) aplikacji, zakłada się, że w systemie docelowym musi nie zawiera wymaganych pakietów manifestu.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-154">For [self-contained deployment (SCD)](index.md#self-contained-deployments-scd) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="c9e7c-155">W związku z tym  **\<PublishWithAspNetCoreTargetManifest >** nie można ustawić `true` — SCD aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-155">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an SCD app.</span></span>

<span data-ttu-id="c9e7c-156">W przypadku wdrożenia aplikacji za pomocą zależności manifestu, który znajduje się we wdrożeniu (zestawu znajduje się w *bin* folderu), Magazyn pakietu środowiska uruchomieniowego *nie jest używany* na hoście dla tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-156">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="c9e7c-157">*Bin* folderu zestaw jest używany niezależnie od jego obecność w Magazyn pakietu środowiska uruchomieniowego na hoście.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-157">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="c9e7c-158">Wersja zależności wskazane w manifeście musi odpowiadać wersji zależności w Magazyn pakietu środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-158">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="c9e7c-159">Jeśli istnieje niezgodność wersji między zależności w manifeście docelowej i wersję, która znajduje się w Magazyn pakietu środowiska uruchomieniowego i aplikacja nie obejmuje wymagana wersja pakietu w jej wdrożenia, jej uruchomienie nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-159">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="c9e7c-160">Wyjątek zawiera nazwę manifest docelowego, który wywołał dla zestawu Magazyn pakietu środowiska uruchomieniowego, która pomaga w rozwiązywaniu problemów niezgodność.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-160">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="c9e7c-161">Po wdrożeniu *spacje* przy publikowaniu, tylko określone wersje manifestu pakietów, możesz wskazać zostały wstrzymane z opublikowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-161">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="c9e7c-162">Pakiety w wersjach wskazane musi być obecny na hoście dla aplikacji, aby rozpocząć.</span><span class="sxs-lookup"><span data-stu-id="c9e7c-162">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="see-also"></a><span data-ttu-id="c9e7c-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9e7c-163">See also</span></span>

- [<span data-ttu-id="c9e7c-164">dotnet-publish</span><span class="sxs-lookup"><span data-stu-id="c9e7c-164">dotnet-publish</span></span>](../tools/dotnet-publish.md)
- [<span data-ttu-id="c9e7c-165">dotnet-store</span><span class="sxs-lookup"><span data-stu-id="c9e7c-165">dotnet-store</span></span>](../tools/dotnet-store.md)
