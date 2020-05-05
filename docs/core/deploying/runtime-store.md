---
title: Magazyn pakietu środowiska uruchomieniowego
description: Dowiedz się, jak używać magazynu pakietów środowiska uruchomieniowego do manifestów docelowych używanych przez platformę .NET Core.
ms.date: 08/12/2017
ms.openlocfilehash: 4395370c3bb2d97511d549a63813022fb8cac4b7
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158296"
---
# <a name="runtime-package-store"></a><span data-ttu-id="1d4bf-103">Magazyn pakietu środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="1d4bf-103">Runtime package store</span></span>

<span data-ttu-id="1d4bf-104">Począwszy od platformy .NET Core 2,0, możliwe jest pakowanie i wdrażanie aplikacji względem znanego zestawu pakietów istniejących w środowisku docelowym.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-104">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="1d4bf-105">Korzyści to szybsze wdrożenia, mniejsze użycie miejsca na dysku i Ulepszona wydajność uruchamiania w niektórych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-105">The benefits are faster deployments, lower disk space usage, and improved startup performance in some cases.</span></span>

<span data-ttu-id="1d4bf-106">Ta funkcja jest zaimplementowana jako *Magazyn pakietów środowiska uruchomieniowego*, który jest katalogiem na dysku, na którym są przechowywane pakiety (zwykle w */usr/local/share/dotnet/Store* na macOS/Linux i *C:/pliki programu/dotnet/sklep* w systemie Windows).</span><span class="sxs-lookup"><span data-stu-id="1d4bf-106">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="1d4bf-107">W tym katalogu znajdują się podkatalogi dla architektury i [platform docelowych](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="1d4bf-107">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="1d4bf-108">Układ pliku jest podobny do sposobu, w jaki [zasoby programu NuGet są wdrożone na dysku](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span><span class="sxs-lookup"><span data-stu-id="1d4bf-108">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

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

<span data-ttu-id="1d4bf-109">*Docelowy plik manifestu* zawiera listę pakietów w magazynie pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-109">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="1d4bf-110">Deweloperzy mogą wskazywać ten manifest podczas publikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-110">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="1d4bf-111">Manifest docelowy jest zwykle dostarczany przez właściciela docelowego środowiska produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-111">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="1d4bf-112">Przygotowywanie środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="1d4bf-112">Preparing a runtime environment</span></span>

<span data-ttu-id="1d4bf-113">Administrator środowiska uruchomieniowego może zoptymalizować aplikacje dla szybszych wdrożeń i zmniejszyć użycie miejsca na dysku przez utworzenie magazynu pakietów środowiska uruchomieniowego i odpowiedniego manifestu docelowego.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-113">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="1d4bf-114">Pierwszym krokiem jest utworzenie *manifestu magazynu pakietów* zawierającego listę pakietów, które tworzą magazyn pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-114">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="1d4bf-115">Ten format pliku jest zgodny z formatem pliku projektu (*csproj*).</span><span class="sxs-lookup"><span data-stu-id="1d4bf-115">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="NUGET_PACKAGE" Version="VERSION" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="1d4bf-116">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1d4bf-116">**Example**</span></span>

<span data-ttu-id="1d4bf-117">Następujący przykładowy manifest magazynu pakietów (*Packages. csproj*) służy do dodawania [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) i [`Moq`](https://www.nuget.org/packages/moq/) do magazynu pakietów środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="1d4bf-117">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="1d4bf-118">Zainicjuj obsługę magazynu pakietów środowiska uruchomieniowego, wykonując `dotnet store` z manifestem magazynu pakietów, środowiskiem uruchomieniowym i strukturą:</span><span class="sxs-lookup"><span data-stu-id="1d4bf-118">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="1d4bf-119">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1d4bf-119">**Example**</span></span>

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="1d4bf-120">Istnieje możliwość przekazania wielu ścieżek manifestu magazynu pakietów docelowych do jednego [`dotnet store`](../tools/dotnet-store.md) polecenia przez powtórzenie opcji i ścieżki w poleceniu.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-120">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="1d4bf-121">Domyślnie dane wyjściowe polecenia są magazynem pakietów w podkatalogu *. dotnet/Store* w profilu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-121">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="1d4bf-122">Możesz określić inną lokalizację przy użyciu `--output <OUTPUT_DIRECTORY>` opcji.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-122">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="1d4bf-123">Katalog główny magazynu zawiera docelowy plik *artefaktu* manifestu.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-123">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="1d4bf-124">Ten plik można udostępnić do pobrania i będzie używany przez autorów aplikacji, którzy chcą wskazać ten magazyn podczas publikowania.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-124">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="1d4bf-125">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1d4bf-125">**Example**</span></span>

<span data-ttu-id="1d4bf-126">Następujący plik *artefaktu. XML* jest generowany po uruchomieniu poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-126">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="1d4bf-127">Należy pamiętać [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) `Moq`, że jest to zależność, dlatego jest dołączona automatycznie i pojawia się w pliku manifestu *artefakts. XML* .</span><span class="sxs-lookup"><span data-stu-id="1d4bf-127">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="1d4bf-128">Publikowanie aplikacji w manifeście docelowym</span><span class="sxs-lookup"><span data-stu-id="1d4bf-128">Publishing an app against a target manifest</span></span>

<span data-ttu-id="1d4bf-129">Jeśli na dysku znajduje się docelowy plik manifestu, należy określić ścieżkę do pliku podczas publikowania aplikacji za pomocą [`dotnet publish`](../tools/dotnet-publish.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="1d4bf-129">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="1d4bf-130">**Przykład**</span><span class="sxs-lookup"><span data-stu-id="1d4bf-130">**Example**</span></span>

```dotnetcli
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="1d4bf-131">Opublikowana aplikacja jest wdrażana w środowisku z pakietami opisanymi w manifeście docelowym.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-131">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="1d4bf-132">Wykonanie tej czynności spowoduje niepowodzenie uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-132">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="1d4bf-133">Określ wiele manifestów docelowych podczas publikowania aplikacji przez powtórzenie opcji i ścieżki (na przykład `--manifest manifest1.xml --manifest manifest2.xml`).</span><span class="sxs-lookup"><span data-stu-id="1d4bf-133">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="1d4bf-134">Gdy to zrobisz, aplikacja zostanie przycięta dla związku z pakietami określonymi w docelowym pliku manifestu dostarczanym do polecenia.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-134">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

<span data-ttu-id="1d4bf-135">W przypadku wdrożenia aplikacji z zależnością manifestu, która znajduje się we wdrożeniu (zestaw jest obecny w folderze *bin* ), magazyn pakietów środowiska uruchomieniowego *nie jest używany* na hoście dla tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-135">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="1d4bf-136">Zestaw folderu *bin* jest używany niezależnie od jego obecności w magazynie pakietów środowiska uruchomieniowego na hoście.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-136">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="1d4bf-137">Wersja zależności wskazanej w manifeście musi być zgodna z wersją zależności w magazynie pakietów środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-137">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="1d4bf-138">Jeśli masz niezgodność wersji między zależnością w manifeście docelowym a wersją, która istnieje w magazynie pakietów środowiska uruchomieniowego, a aplikacja nie zawiera wymaganej wersji pakietu w jej wdrożeniu, uruchomienie aplikacji nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-138">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="1d4bf-139">Wyjątek zawiera nazwę manifestu docelowego, który został wywołany dla zestawu magazynu pakietów środowiska uruchomieniowego, co pomaga w rozwiązywaniu problemów z niezgodnością.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-139">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="1d4bf-140">Gdy wdrożenie zostanie *przycięte* po opublikowaniu, tylko określone wersje pakietów manifestu są potrącane z publikowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-140">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="1d4bf-141">Pakiety na wskazanych wersjach muszą być obecne na hoście, aby można było uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-141">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="1d4bf-142">Określanie manifestów docelowych w pliku projektu</span><span class="sxs-lookup"><span data-stu-id="1d4bf-142">Specifying target manifests in the project file</span></span>

<span data-ttu-id="1d4bf-143">Alternatywą dla określenia manifestów docelowych za pomocą [`dotnet publish`](../tools/dotnet-publish.md) polecenia jest określenie ich w pliku projektu jako listę ścieżek rozdzielonych średnikami pod tagiem \*\* \<TargetManifestFiles>\*\* .</span><span class="sxs-lookup"><span data-stu-id="1d4bf-143">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="1d4bf-144">Określ docelowe manifesty w pliku projektu tylko wtedy, gdy Środowisko docelowe dla aplikacji jest dobrze znane, na przykład w przypadku projektów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-144">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="1d4bf-145">Nie jest to przypadek dla projektów open source.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-145">This isn't the case for open-source projects.</span></span> <span data-ttu-id="1d4bf-146">Użytkownicy projektu typu open source zwykle wdrażają je w różnych środowiskach produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-146">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="1d4bf-147">W tych środowiskach produkcyjnych ogólnie zainstalowano różne zestawy pakietów.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-147">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="1d4bf-148">Nie można tworzyć założeń dotyczących manifestu docelowego w takich środowiskach, dlatego należy użyć `--manifest` opcji. [`dotnet publish`](../tools/dotnet-publish.md)</span><span class="sxs-lookup"><span data-stu-id="1d4bf-148">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store-net-core-20-only"></a><span data-ttu-id="1d4bf-149">Niejawny magazyn ASP.NET Core (tylko w przypadku programu .NET Core 2,0)</span><span class="sxs-lookup"><span data-stu-id="1d4bf-149">ASP.NET Core implicit store (.NET Core 2.0 only)</span></span>

<span data-ttu-id="1d4bf-150">Niejawny magazyn ASP.NET Core ma zastosowanie tylko do ASP.NET Core 2,0.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-150">The ASP.NET Core implicit store applies only to ASP.NET Core 2.0.</span></span> <span data-ttu-id="1d4bf-151">Zdecydowanie zalecamy stosowanie aplikacji ASP.NET Core 2,1 i nowszych, które **nie** korzystają z magazynu niejawnego.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-151">We strongly recommend applications use ASP.NET Core 2.1 and later, which does **not** use the implicit store.</span></span> <span data-ttu-id="1d4bf-152">ASP.NET Core 2,1 i później używają udostępnionej platformy.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-152">ASP.NET Core 2.1 and later use the shared framework.</span></span>

<span data-ttu-id="1d4bf-153">W przypadku platformy .NET Core 2,0 funkcja magazynu pakietów środowiska uruchomieniowego jest używana niejawnie przez aplikację ASP.NET Core, gdy aplikacja jest wdrażana jako aplikacja [wdrożenia zależna od środowiska uruchomieniowego](index.md#publish-runtime-dependent) .</span><span class="sxs-lookup"><span data-stu-id="1d4bf-153">For .NET Core 2.0, the runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [runtime-dependent deployment](index.md#publish-runtime-dependent) app.</span></span> <span data-ttu-id="1d4bf-154">Elementy docelowe w [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) programie zawierają manifesty odwołujące się do niejawnego magazynu pakietów w systemie docelowym.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-154">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="1d4bf-155">Ponadto wszystkie aplikacje zależne od środowiska uruchomieniowego, które są `Microsoft.AspNetCore.All` zależne od pakietu, mają opublikowaną aplikację, która zawiera tylko aplikację i jej zasoby, a nie pakiety `Microsoft.AspNetCore.All` wymienione w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-155">Additionally, any runtime-dependent app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="1d4bf-156">Przyjęto założenie, że te pakiety znajdują się w systemie docelowym.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-156">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="1d4bf-157">Magazyn pakietów środowiska uruchomieniowego jest instalowany na hoście, gdy zainstalowano zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-157">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="1d4bf-158">Inne Instalatory mogą dostarczyć magazyn pakietów środowiska uruchomieniowego, w tym instalacje zip/plik tar zestaw .NET Core SDK, `apt-get`Red Hat yum, pakiet hostingu platformy .NET Core z systemem Windows Server i ręczne instalacje magazynu pakietów w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-158">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="1d4bf-159">Podczas wdrażania aplikacji [wdrożenia zależnej od środowiska uruchomieniowego](index.md#publish-runtime-dependent) upewnij się, że środowisko docelowe ma zainstalowaną zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-159">When deploying a [runtime-dependent deployment](index.md#publish-runtime-dependent) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="1d4bf-160">Jeśli aplikacja jest wdrażana w środowisku, które nie zawiera ASP.NET Core, można zrezygnować z niejawnego magazynu przez określenie \*\* \<PublishWithAspNetCoreTargetManifest>\*\* ustawionej `false` na wartość w pliku projektu, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1d4bf-160">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="1d4bf-161">W przypadku aplikacji do [samodzielnego wdrażania](index.md#publish-self-contained) zakłada się, że system docelowy nie musi zawierać wymaganych pakietów manifestu.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-161">For [self-contained deployment](index.md#publish-self-contained) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="1d4bf-162">W związku z tym \*\* \<PublishWithAspNetCoreTargetManifest>\*\* nie można `true` ustawić na dla aplikacji samodzielnej.</span><span class="sxs-lookup"><span data-stu-id="1d4bf-162">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an self-contained app.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d4bf-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d4bf-163">See also</span></span>

- [<span data-ttu-id="1d4bf-164">dotnet — publikowanie</span><span class="sxs-lookup"><span data-stu-id="1d4bf-164">dotnet-publish</span></span>](../tools/dotnet-publish.md)
- [<span data-ttu-id="1d4bf-165">dotnet — sklep</span><span class="sxs-lookup"><span data-stu-id="1d4bf-165">dotnet-store</span></span>](../tools/dotnet-store.md)
