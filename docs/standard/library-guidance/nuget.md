---
title: Biblioteki NuGet i platformy .NET
description: Zalecane najlepsze dla pakietu nuget biblioteki .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 8ac01046f25176b781240baeba8bf1efb9376689
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129613"
---
# <a name="nuget"></a><span data-ttu-id="1adf6-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="1adf6-103">NuGet</span></span>

<span data-ttu-id="1adf6-104">NuGet to Menedżer pakietów dla ekosystemu .NET i deweloperów podstawowym sposobem odnajdywanie i nabyć bibliotek typu open source platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="1adf6-104">NuGet is a package manager for the .NET ecosystem and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="1adf6-105">[NuGet.org](https://www.nuget.org/), bezpłatna usługa udostępniana przez firmę Microsoft do obsługi pakietów NuGet jest hostem głównym publicznych pakietów NuGet, ale możesz opublikować niestandardowych usług NuGet, takich jak [MyGet](https://www.myget.org/) i [artefaktów platformy Azure ](https://azure.microsoft.com/services/devops/artifacts/).</span><span class="sxs-lookup"><span data-stu-id="1adf6-105">[NuGet.org](https://www.nuget.org/), a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages, but you can publish to custom NuGet services like [MyGet](https://www.myget.org/) and [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span></span>

<span data-ttu-id="1adf6-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="1adf6-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="1adf6-107">Utwórz pakiet NuGet</span><span class="sxs-lookup"><span data-stu-id="1adf6-107">Create a NuGet package</span></span>

<span data-ttu-id="1adf6-108">Pakiet NuGet (`*.nupkg`) jest plikiem zip, zawierający zestawy .NET oraz skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="1adf6-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="1adf6-109">Istnieją dwa główne sposoby, aby utworzyć pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="1adf6-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="1adf6-110">Sposobem nowszej i zalecane jest utworzenie pakietu z projektu zestawu SDK stylu (plik projektu, którego zawartość rozpoczyna się od `<Project Sdk="Microsoft.NET.Sdk">`).</span><span class="sxs-lookup"><span data-stu-id="1adf6-110">The newer and recommended way is to create a package from a SDK-style project (project file whose content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="1adf6-111">Zespoły i elementy docelowe są automatycznie dodawane do pakietu, a pozostałe metadanych jest dodawany do pliku programu MSBuild, takich jak numer nazwą i wersją pakietu.</span><span class="sxs-lookup"><span data-stu-id="1adf6-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="1adf6-112">Kompilowanie przy użyciu [ `dotnet pack` ](../../core/tools/dotnet-pack.md) dane wyjściowe polecenia `*.nupkg` pliku zamiast zestawów.</span><span class="sxs-lookup"><span data-stu-id="1adf6-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <AssemblyName>Contoso.Api</AssemblyName>
    <PackageVersion>1.1.0</PackageVersion>
    <Authors>John Doe</Authors>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="1adf6-113">Starszy sposób tworzenia pakietu NuGet jest `*.nuspec` pliku i `nuget.exe` narzędzie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1adf6-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="1adf6-114">Soubor nuspec zapewnia dużą kontrolę, ale należy określić dokładnie do końcowego pakietu NuGet, jakie zestawy i elementy docelowe.</span><span class="sxs-lookup"><span data-stu-id="1adf6-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="1adf6-115">Łatwo popełnienia błędu lub niepowołanym zapomnij zaktualizować nuspec podczas wprowadzania zmian.</span><span class="sxs-lookup"><span data-stu-id="1adf6-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="1adf6-116">Ma tę zaletę nuspec umożliwia tworzenie pakietów NuGet, struktur, które nie obsługują pliku projektu zestawu SDK stylu.</span><span class="sxs-lookup"><span data-stu-id="1adf6-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="1adf6-117">**ROZWAŻ ✔️** przy użyciu zestawu SDK stylu pliku projektu do utworzenia pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="1adf6-117">**✔️ CONSIDER** using an SDK-style project file to create the NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="1adf6-118">Zależności pakietów</span><span class="sxs-lookup"><span data-stu-id="1adf6-118">Package dependencies</span></span>

<span data-ttu-id="1adf6-119">Zależności pakietów NuGet są tu szczegółowo [zależności](./dependencies.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="1adf6-119">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="1adf6-120">Ważne metadane pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="1adf6-120">Important NuGet package metadata</span></span>

<span data-ttu-id="1adf6-121">Pakiet NuGet obsługuje wiele [właściwości metadanych](/nuget/reference/nuspec).</span><span class="sxs-lookup"><span data-stu-id="1adf6-121">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="1adf6-122">Poniższa tabela zawiera metadane podstawowe, zapewniające każdy projekt typu open-source:</span><span class="sxs-lookup"><span data-stu-id="1adf6-122">The following table contains the core metadata that every open-source project should provide:</span></span>

| <span data-ttu-id="1adf6-123">Nazwa właściwości programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="1adf6-123">MSBuild Property name</span></span>              | <span data-ttu-id="1adf6-124">Nazwa Nuspec</span><span class="sxs-lookup"><span data-stu-id="1adf6-124">Nuspec name</span></span>              | <span data-ttu-id="1adf6-125">Opis</span><span class="sxs-lookup"><span data-stu-id="1adf6-125">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="1adf6-126">Identyfikator pakietu.</span><span class="sxs-lookup"><span data-stu-id="1adf6-126">The package identifier.</span></span> <span data-ttu-id="1adf6-127">Jeśli dana jednostka spełnia można zarezerwować prefiksu z identyfikatorem [kryteria](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="1adf6-127">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="1adf6-128">Wersja pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="1adf6-128">NuGet package version.</span></span> <span data-ttu-id="1adf6-129">Aby uzyskać więcej informacji, zobacz [pakietu NuGet w wersji](./versioning.md#nuget-package-version).</span><span class="sxs-lookup"><span data-stu-id="1adf6-129">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="1adf6-130">Przyjazne dla człowieka tytuł pakietu.</span><span class="sxs-lookup"><span data-stu-id="1adf6-130">A human-friendly title of the package.</span></span> <span data-ttu-id="1adf6-131">Jego wartość domyślna to `PackageId`.</span><span class="sxs-lookup"><span data-stu-id="1adf6-131">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="1adf6-132">Długi opis pakietu, wyświetlana w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1adf6-132">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="1adf6-133">Rozdzielana przecinkami lista autorów pakietów, pasujące nazwy profilu w witrynie nuget.org.</span><span class="sxs-lookup"><span data-stu-id="1adf6-133">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="1adf6-134">Rozdzielany spacjami lista tagów i słów kluczowych, które opisują pakietu.</span><span class="sxs-lookup"><span data-stu-id="1adf6-134">A space-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="1adf6-135">Znaczniki są używane podczas wyszukiwania dla pakietów.</span><span class="sxs-lookup"><span data-stu-id="1adf6-135">Tags are used when searching for packages.</span></span>             |
| `PackageIconUrl`                   | `iconUrl`                  | <span data-ttu-id="1adf6-136">Adres URL obrazu do użycia jako ikona dla pakietu.</span><span class="sxs-lookup"><span data-stu-id="1adf6-136">A URL for an image to use as the icon for the package.</span></span> <span data-ttu-id="1adf6-137">Adres URL powinien być schemat HTTPS i obraz, który powinien być 64 x 64 i mieć przezroczyste tło.</span><span class="sxs-lookup"><span data-stu-id="1adf6-137">URL should be HTTPS and the image should be 64x64 and have a transparent background.</span></span>             |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="1adf6-138">Adres URL strony głównej lub źródło repozytorium projektu.</span><span class="sxs-lookup"><span data-stu-id="1adf6-138">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseUrl`                | `licenseUrl`               | <span data-ttu-id="1adf6-139">Adres URL, aby uzyskać licencję projektu.</span><span class="sxs-lookup"><span data-stu-id="1adf6-139">A URL to the project license.</span></span> <span data-ttu-id="1adf6-140">Może być adres URL do `LICENSE` plików w kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="1adf6-140">Can be the URL to the `LICENSE` file in source control.</span></span>             |

<span data-ttu-id="1adf6-141">**ROZWAŻ ✔️** Wybieranie nazwy pakietów NuGet z prefiksem, który spełnia rezerwowanie prefiksów identyfikatorów NuGet [kryteria](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="1adf6-141">**✔️ CONSIDER** choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="1adf6-142">**ROZWAŻ ✔️** przy użyciu `LICENSE` plików w kontroli źródła, ponieważ `LicenseUrl`.</span><span class="sxs-lookup"><span data-stu-id="1adf6-142">**✔️ CONSIDER** using the `LICENSE` file in source control as the `LicenseUrl`.</span></span> <span data-ttu-id="1adf6-143">Na przykład [LICENSE.md](https://github.com/JamesNK/Newtonsoft.Json/blob/c4af75c8e91ca0d75aa6c335e8c106780c4f7712/LICENSE.md).</span><span class="sxs-lookup"><span data-stu-id="1adf6-143">For example, [LICENSE.md](https://github.com/JamesNK/Newtonsoft.Json/blob/c4af75c8e91ca0d75aa6c335e8c106780c4f7712/LICENSE.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1adf6-144">Projekt bez licencji, wartość domyślna to [wyłącznych praw autorskich](https://choosealicense.com/no-permission/), uniemożliwiając innym użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="1adf6-144">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it impossible for other people to use.</span></span>

<span data-ttu-id="1adf6-145">**CZY ✔️** Użyj href HTTPS, aby ikona pakietu.</span><span class="sxs-lookup"><span data-stu-id="1adf6-145">**✔️ DO** use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="1adf6-146">Witryn, takich jak NuGet.org Uruchom przy użyciu protokołu HTTPS jest włączone, a następnie wyświetlanie obrazu innych niż HTTPS utworzy ostrzeżenie zawartości mieszanej.</span><span class="sxs-lookup"><span data-stu-id="1adf6-146">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="1adf6-147">**CZY ✔️** za pomocą pakietu obrazu ikony, 64 x 64 z przezroczystym tłem, aby uzyskać najlepszy wygląd.</span><span class="sxs-lookup"><span data-stu-id="1adf6-147">**✔️ DO** use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

<span data-ttu-id="1adf6-148">**ROZWAŻ ✔️** Konfigurowanie [SourceLink](./sourcelink.md) do dodawania metadanych do kontroli źródła do zestawów i pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="1adf6-148">**✔️ CONSIDER** setting up [SourceLink](./sourcelink.md) to add source control metadata to your assemblies and NuGet package.</span></span>

> <span data-ttu-id="1adf6-149">Automatycznie dodaje SourceLink `RepositoryUrl` i `RepositoryType` metadanych do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="1adf6-149">SourceLink automatically adds `RepositoryUrl` and `RepositoryType` metadata to the NuGet package.</span></span>
> <span data-ttu-id="1adf6-150">SourceLink dodaje również, że informacje o kodzie źródłowym dokładnie pakiet został zbudowany z.</span><span class="sxs-lookup"><span data-stu-id="1adf6-150">SourceLink also adds information about the exact source code the package was built from.</span></span>
> <span data-ttu-id="1adf6-151">Na przykład pakiet utworzony na podstawie repozytorium Git będzie mieć skrót zatwierdzenia dodać jako metadane.</span><span class="sxs-lookup"><span data-stu-id="1adf6-151">For example, a package created from a Git repository will have the commit hash added as metadata.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="1adf6-152">Pakiety w wersji wstępnej</span><span class="sxs-lookup"><span data-stu-id="1adf6-152">Pre-release packages</span></span>

<span data-ttu-id="1adf6-153">Pakiety NuGet za pomocą sufiksu wersji są traktowane jako [wersji wstępnej](/nuget/create-packages/prerelease-packages).</span><span class="sxs-lookup"><span data-stu-id="1adf6-153">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="1adf6-154">Domyślnie interfejs użytkownika Menedżera pakietów NuGet zawiera stabilnej wersji, chyba że użytkownik zdecyduje się na do wersji wstępnej pakietów, dzięki czemu pakiety w wersji wstępnej niezwykle przydatna przy testowaniu użytkownika z ograniczonymi.</span><span class="sxs-lookup"><span data-stu-id="1adf6-154">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="1adf6-155">Stabilny pakiet nie mogą być zależne od pakietu wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="1adf6-155">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="1adf6-156">Możesz utworzyć własny pakiet wersji wstępnej lub są zależne od starsze stabilnej wersji.</span><span class="sxs-lookup"><span data-stu-id="1adf6-156">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="1adf6-157">![Zależność wersji wstępnej pakietu NuGet](./media/nuget/nuget-prerelease-package.png "zależność wersji wstępnej pakietu NuGet")</span><span class="sxs-lookup"><span data-stu-id="1adf6-157">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="1adf6-158">**CZY ✔️** publikowanie pakietu wersji wstępnej podczas testowania, Podgląd lub eksperymentowania.</span><span class="sxs-lookup"><span data-stu-id="1adf6-158">**✔️ DO** publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="1adf6-159">**CZY ✔️** publikowania stabilny pakiet, gdy jego gotowe więc inne stabilne pakiety można odwoływać się do niego.</span><span class="sxs-lookup"><span data-stu-id="1adf6-159">**✔️ DO** publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="1adf6-160">Pakiety symboli</span><span class="sxs-lookup"><span data-stu-id="1adf6-160">Symbol packages</span></span>

<span data-ttu-id="1adf6-161">Pliki symboli (`*.pdb`) są produkowane przez kompilator platformy .NET, wraz z zestawów.</span><span class="sxs-lookup"><span data-stu-id="1adf6-161">Symbol files (`*.pdb`) are produced by the .NET compiler alongside assemblies.</span></span> <span data-ttu-id="1adf6-162">Lokalizacje wykonywania mapy plików symboli do oryginalnego kodu źródłowego, dzięki czemu możesz przejrzeć kod źródłowy w postaci, w jakiej jest uruchomiona, przy użyciu debugera.</span><span class="sxs-lookup"><span data-stu-id="1adf6-162">Symbol files map execution locations to the original source code so you can step through source code as it is running using a debugger.</span></span> <span data-ttu-id="1adf6-163">Obsługuje NuGet [generowania pakietu oddzielne symbol (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) zawierający pliki symboli, wraz z pakietu głównego zawierającego zestawy .NET.</span><span class="sxs-lookup"><span data-stu-id="1adf6-163">NuGet supports [generating a separate symbol package (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) containing symbol files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="1adf6-164">Koncepcja pakiety symboli jest one hostowane na serwerze symboli i są pobierane tylko wtedy, narzędzia, takiego jak Visual Studio na żądanie.</span><span class="sxs-lookup"><span data-stu-id="1adf6-164">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="1adf6-165">NuGet.org znajduje się własną [repozytorium serwera symboli](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server).</span><span class="sxs-lookup"><span data-stu-id="1adf6-165">NuGet.org hosts its own [symbols server repository](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server).</span></span> <span data-ttu-id="1adf6-166">Deweloperzy mogą używać symbole opublikowane na serwerze symboli NuGet.org, dodając `https://symbols.nuget.org/download/symbols` do ich [symboli źródła w programie Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span><span class="sxs-lookup"><span data-stu-id="1adf6-166">Developers can use the symbols published to the NuGet.org symbol server by adding `https://symbols.nuget.org/download/symbols` to their [symbol sources in Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1adf6-167">Serwer symboli NuGet.org obsługuje tylko nowe [pliki symboli przenośne](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) utworzone przez projektów w stylu zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="1adf6-167">The NuGet.org symbol server only supports the new [portable symbol files](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) created by SDK-style projects.</span></span>

<span data-ttu-id="1adf6-168">Alternatywą dla tworzenia pakietu symboli jest osadzanie plików symboli w głównym pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="1adf6-168">An alternative to creating a symbol package is embedding symbol files in the main NuGet package.</span></span> <span data-ttu-id="1adf6-169">Głównym pakietu NuGet jest większy, ale osadzone symboli plików oznacza, że deweloperzy nie muszą skonfigurować serwer symboli NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="1adf6-169">The main NuGet package will be larger, but the embedded symbol files means developers don't need to configure the NuGet.org symbol server.</span></span> <span data-ttu-id="1adf6-170">Jeśli tworzysz pakiet NuGet za pomocą zestawu SDK stylu projektu, a następnie umożliwia osadzanie plików symboli, ustawiając `AllowedOutputExtensionsInPackageBuildOutputFolder` właściwości:</span><span class="sxs-lookup"><span data-stu-id="1adf6-170">If you're building your NuGet package using an SDK-style project, then you can embed symbol files by setting the `AllowedOutputExtensionsInPackageBuildOutputFolder` property:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="1adf6-171">**ROZWAŻ ✔️** osadzanie plików symboli w głównym pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="1adf6-171">**✔️ CONSIDER** embedding symbol files in the main NuGet package.</span></span>

> <span data-ttu-id="1adf6-172">Osadzanie plików symboli w głównym pakietu NuGet daje deweloperom to lepszy proces debugowania domyślnie.</span><span class="sxs-lookup"><span data-stu-id="1adf6-172">Embedding symbol files in the main NuGet package gives developers a better debugging experience by default.</span></span> <span data-ttu-id="1adf6-173">Nie muszą znaleźć i skonfigurować serwer symboli NuGet w ich środowisku IDE, aby pobrać pliki symboli.</span><span class="sxs-lookup"><span data-stu-id="1adf6-173">They don't need to find and configure the NuGet symbol server in their IDE to get symbol files.</span></span>
>
> <span data-ttu-id="1adf6-174">Wadą plików symboli osadzony jest zwiększają rozmiar pakietu przez około 30% do bibliotek .NET skompilowanych przy użyciu zestawu SDK stylu projektów.</span><span class="sxs-lookup"><span data-stu-id="1adf6-174">The downside to embedded symbol files is they increase the package size by about 30% for .NET libraries compiled using SDK-style projects.</span></span> <span data-ttu-id="1adf6-175">Jeśli rozmiar pakietu jest istotna, należy zamiast tego opublikować symbole w pakietach symboli.</span><span class="sxs-lookup"><span data-stu-id="1adf6-175">If package size is a concern, you should publish symbols in a symbol package instead.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1adf6-176">[Poprzednie](strong-naming.md)
>[dalej](dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="1adf6-176">[Previous](strong-naming.md)
[Next](dependencies.md)</span></span>