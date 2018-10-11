---
title: Biblioteki NuGet i platformy .NET
description: Zalecane najlepsze dla pakietu nuget biblioteki .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 845af3b34827e1f284bb52e040f9de09f22baf37
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087872"
---
# <a name="nuget"></a><span data-ttu-id="96503-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="96503-103">NuGet</span></span>

<span data-ttu-id="96503-104">NuGet to Menedżer pakietów dla ekosystemu .NET i deweloperów podstawowym sposobem odnajdywanie i nabyć bibliotek typu open source platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="96503-104">NuGet is a package manager for the .NET eco-system and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="96503-105">NuGet.org, bezpłatna usługa udostępniana przez firmę Microsoft do obsługi pakietów NuGet jest hostem głównym publicznych pakietów NuGet, ale możesz opublikować niestandardowych usług NuGet, takich jak MyGet i DevOps platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="96503-105">NuGet.org, a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages but you can publish to custom NuGet services like MyGet and Azure DevOps.</span></span>

<span data-ttu-id="96503-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="96503-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="96503-107">Utwórz pakiet NuGet</span><span class="sxs-lookup"><span data-stu-id="96503-107">Create a NuGet package</span></span>

<span data-ttu-id="96503-108">Pakiet NuGet (`*.nupkg`) jest plikiem zip, zawierający zestawy .NET oraz skojarzone metadane.</span><span class="sxs-lookup"><span data-stu-id="96503-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="96503-109">Istnieją dwa główne sposoby, aby utworzyć pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="96503-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="96503-110">Sposobem nowszej i zalecane jest utworzenie pakietu z projektu zestawu SDK stylu (plik projektu zawartości rozpoczyna się od `<Project Sdk="Microsoft.NET.Sdk">`).</span><span class="sxs-lookup"><span data-stu-id="96503-110">The newer and recommended way is to create a package from a SDK-style project (project file the content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="96503-111">Zespoły i elementy docelowe są automatycznie dodawane do pakietu, a pozostałe metadanych jest dodawany do pliku programu MSBuild, takich jak numer nazwą i wersją pakietu.</span><span class="sxs-lookup"><span data-stu-id="96503-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="96503-112">Kompilowanie przy użyciu [ `dotnet pack` ](../../core/tools/dotnet-pack.md) dane wyjściowe polecenia `*.nupkg` pliku zamiast zestawów.</span><span class="sxs-lookup"><span data-stu-id="96503-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

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

<span data-ttu-id="96503-113">Starszy sposób tworzenia pakietu NuGet jest `*.nuspec` pliku i `nuget.exe` narzędzie wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="96503-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="96503-114">Soubor nuspec zapewnia dużą kontrolę, ale należy określić dokładnie do końcowego pakietu NuGet, jakie zestawy i elementy docelowe.</span><span class="sxs-lookup"><span data-stu-id="96503-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="96503-115">Łatwo popełnienia błędu lub niepowołanym zapomnij zaktualizować nuspec podczas wprowadzania zmian.</span><span class="sxs-lookup"><span data-stu-id="96503-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="96503-116">Ma tę zaletę nuspec umożliwia tworzenie pakietów NuGet, struktur, które nie obsługują pliku projektu zestawu SDK stylu.</span><span class="sxs-lookup"><span data-stu-id="96503-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="96503-117">**ROZWAŻ ✔️** przy użyciu zestawu SDK stylu pliku projektu do utworzenia pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="96503-117">**✔️ CONSIDER** using an SDK-style project file to create the NuGet package.</span></span>

<span data-ttu-id="96503-118">**ROZWAŻ ✔️** ustawienie SourceLink do dodawania metadanych do kontroli źródła do zestawów i pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="96503-118">**✔️ CONSIDER** setting up SourceLink to add source control metadata to your assemblies and NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="96503-119">Zależności pakietów</span><span class="sxs-lookup"><span data-stu-id="96503-119">Package dependencies</span></span>

<span data-ttu-id="96503-120">Zależności pakietów NuGet są tu szczegółowo [zależności](./dependencies.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="96503-120">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="96503-121">Ważne metadane pakietu NuGet</span><span class="sxs-lookup"><span data-stu-id="96503-121">Important NuGet package metadata</span></span>

<span data-ttu-id="96503-122">Pakiet NuGet obsługuje wiele [właściwości metadanych](/nuget/reference/nuspec).</span><span class="sxs-lookup"><span data-stu-id="96503-122">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="96503-123">Poniższa tabela zawiera metadane podstawowe, zapewniające każdy projekt typu open-source:</span><span class="sxs-lookup"><span data-stu-id="96503-123">The following table contains the core metadata that every open-source project should provide:</span></span>

| <span data-ttu-id="96503-124">Nazwa właściwości programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="96503-124">MSBuild Property name</span></span>              | <span data-ttu-id="96503-125">Nazwa Nuspec</span><span class="sxs-lookup"><span data-stu-id="96503-125">Nuspec name</span></span>              | <span data-ttu-id="96503-126">Opis</span><span class="sxs-lookup"><span data-stu-id="96503-126">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="96503-127">Identyfikator pakietu.</span><span class="sxs-lookup"><span data-stu-id="96503-127">The package identifier.</span></span> <span data-ttu-id="96503-128">Jeśli dana jednostka spełnia można zarezerwować prefiksu z identyfikatorem [kryteria](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="96503-128">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="96503-129">Wersja pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="96503-129">NuGet package version.</span></span> <span data-ttu-id="96503-130">Aby uzyskać więcej informacji, zobacz [pakietu NuGet w wersji](./versioning.md#nuget-package-version).</span><span class="sxs-lookup"><span data-stu-id="96503-130">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="96503-131">Przyjazne dla człowieka tytuł pakietu.</span><span class="sxs-lookup"><span data-stu-id="96503-131">A human-friendly title of the package.</span></span> <span data-ttu-id="96503-132">Jego wartość domyślna to `PackageId`.</span><span class="sxs-lookup"><span data-stu-id="96503-132">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="96503-133">Długi opis pakietu, wyświetlana w interfejsie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="96503-133">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="96503-134">Rozdzielana przecinkami lista autorów pakietów, pasujące nazwy profilu w witrynie nuget.org.</span><span class="sxs-lookup"><span data-stu-id="96503-134">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="96503-135">Rozdzielany spacjami lista tagów i słów kluczowych, które opisują pakietu.</span><span class="sxs-lookup"><span data-stu-id="96503-135">A space-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="96503-136">Znaczniki są używane podczas wyszukiwania dla pakietów.</span><span class="sxs-lookup"><span data-stu-id="96503-136">Tags are used when searching for packages.</span></span>             |
| `PackageIconUrl`                   | `iconUrl`                  | <span data-ttu-id="96503-137">Adres URL obrazu do użycia jako ikona dla pakietu.</span><span class="sxs-lookup"><span data-stu-id="96503-137">A URL for an image to use as the icon for the package.</span></span> <span data-ttu-id="96503-138">Adres URL powinien być schemat HTTPS i obraz, który powinien być 64 x 64 i mieć przezroczyste tło.</span><span class="sxs-lookup"><span data-stu-id="96503-138">URL should be HTTPS and the image should be 64x64 and have a transparent background.</span></span>             |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="96503-139">Adres URL strony głównej lub źródło repozytorium projektu.</span><span class="sxs-lookup"><span data-stu-id="96503-139">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseUrl`                | `licenseUrl`               | <span data-ttu-id="96503-140">Adres URL, aby uzyskać licencję projektu.</span><span class="sxs-lookup"><span data-stu-id="96503-140">A URL to the project license.</span></span> <span data-ttu-id="96503-141">Może być adres URL do `LICENSE` plików w kontroli źródła.</span><span class="sxs-lookup"><span data-stu-id="96503-141">Can be the URL to the `LICENSE` file in source control.</span></span>             |

<span data-ttu-id="96503-142">**ROZWAŻ ✔️** Wybieranie nazwy pakietów NuGet z prefiksem, który spełnia rezerwowanie prefiksów identyfikatorów NuGet [kryteria](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="96503-142">**✔️ CONSIDER** choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="96503-143">**ROZWAŻ ✔️** przy użyciu `LICENSE` plików w kontroli źródła, ponieważ `LicenseUrl`.</span><span class="sxs-lookup"><span data-stu-id="96503-143">**✔️ CONSIDER** using the `LICENSE` file in source control as the `LicenseUrl`.</span></span> <span data-ttu-id="96503-144">Na przykład:https://github.com/JamesNK/Newtonsoft.Json/blob/master/LICENSE.md</span><span class="sxs-lookup"><span data-stu-id="96503-144">For example, https://github.com/JamesNK/Newtonsoft.Json/blob/master/LICENSE.md</span></span>

> [!IMPORTANT]
> <span data-ttu-id="96503-145">Projekt bez licencji, wartość domyślna to [wyłącznych praw autorskich](https://choosealicense.com/no-permission/), uniemożliwiając innym użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="96503-145">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it impossible for other people to use.</span></span>

<span data-ttu-id="96503-146">**CZY ✔️** Użyj href HTTPS, aby ikona pakietu.</span><span class="sxs-lookup"><span data-stu-id="96503-146">**✔️ DO** use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="96503-147">Witryn, takich jak NuGet.org Uruchom przy użyciu protokołu HTTPS jest włączone, a następnie wyświetlanie obrazu innych niż HTTPS utworzy ostrzeżenie zawartości mieszanej.</span><span class="sxs-lookup"><span data-stu-id="96503-147">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="96503-148">**CZY ✔️** za pomocą pakietu obrazu ikony, 64 x 64 z przezroczystym tłem, aby uzyskać najlepszy wygląd.</span><span class="sxs-lookup"><span data-stu-id="96503-148">**✔️ DO** use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="96503-149">Pakiety w wersji wstępnej</span><span class="sxs-lookup"><span data-stu-id="96503-149">Pre-release packages</span></span>

<span data-ttu-id="96503-150">Pakiety NuGet za pomocą sufiksu wersji są traktowane jako [wersji wstępnej](/nuget/create-packages/prerelease-packages).</span><span class="sxs-lookup"><span data-stu-id="96503-150">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="96503-151">Domyślnie interfejs użytkownika Menedżera pakietów NuGet zawiera stabilnej wersji, chyba że użytkownik zdecyduje się na do wersji wstępnej pakietów, dzięki czemu pakiety w wersji wstępnej niezwykle przydatna przy testowaniu użytkownika z ograniczonymi.</span><span class="sxs-lookup"><span data-stu-id="96503-151">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="96503-152">Stabilny pakiet nie mogą być zależne od pakietu wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="96503-152">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="96503-153">Możesz utworzyć własny pakiet wersji wstępnej lub są zależne od starsze stabilnej wersji.</span><span class="sxs-lookup"><span data-stu-id="96503-153">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="96503-154">![Zależność wersji wstępnej pakietu NuGet](./media/nuget/nuget-prerelease-package.png "zależność wersji wstępnej pakietu NuGet")</span><span class="sxs-lookup"><span data-stu-id="96503-154">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="96503-155">**CZY ✔️** publikowanie pakietu wersji wstępnej podczas testowania, Podgląd lub eksperymentowania.</span><span class="sxs-lookup"><span data-stu-id="96503-155">**✔️ DO** publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="96503-156">**CZY ✔️** publikowania stabilny pakiet, gdy jego gotowe więc inne stabilne pakiety można odwoływać się do niego.</span><span class="sxs-lookup"><span data-stu-id="96503-156">**✔️ DO** publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="96503-157">Pakiety symboli</span><span class="sxs-lookup"><span data-stu-id="96503-157">Symbol packages</span></span>

<span data-ttu-id="96503-158">Obsługuje NuGet [generowania pakietu oddzielne symbol](/nuget/create-packages/symbol-packages) zawierający debugowania plików PDB obok pakietu głównego zawierającego zestawy .NET.</span><span class="sxs-lookup"><span data-stu-id="96503-158">NuGet supports [generating a separate symbol package](/nuget/create-packages/symbol-packages) containing debug PDB files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="96503-159">Koncepcja pakiety symboli jest one hostowane na serwerze symboli i są pobierane tylko wtedy, narzędzia, takiego jak Visual Studio na żądanie.</span><span class="sxs-lookup"><span data-stu-id="96503-159">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="96503-160">Obecnie głównym gospodarzem publicznego symboli - [SymbolSource](http://www.symbolsource.org/) — nie obsługuje plików przenośnych PDB, utworzone przez zestaw SDK stylu projektów i pakiety symboli nie są użyteczne.</span><span class="sxs-lookup"><span data-stu-id="96503-160">Currently the main public host for symbols - [SymbolSource](http://www.symbolsource.org/) - doesn't support the portable PDBs created by SDK-style projects and symbol packages aren't useful.</span></span>

<span data-ttu-id="96503-161">**ROZWAŻ ✔️** osadzanie plików PDB w głównym pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="96503-161">**✔️ CONSIDER** embedding PDBs in the main NuGet package.</span></span>

<span data-ttu-id="96503-162">**Należy UNIKAĆ ❌** tworzenie symbole pakietu zawierającego pliki PDB.</span><span class="sxs-lookup"><span data-stu-id="96503-162">**❌ AVOID** creating a symbols package containing PDBs.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="96503-163">[Poprzednie](./strong-naming.md)
[dalej](./dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="96503-163">[Previous](./strong-naming.md)
[Next](./dependencies.md)</span></span>
