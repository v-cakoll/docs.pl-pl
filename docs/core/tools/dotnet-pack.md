---
title: polecenie Pakiet DotNet - .NET Core interfejsu wiersza polecenia
description: "Polecenie Pakiet dotnet tworzy pakietów NuGet dla projektu platformy .NET Core."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 8594c863d67baf0237b63e61f28ca9ee315eeddf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-pack"></a><span data-ttu-id="dede1-103">Pakiet DotNet</span><span class="sxs-lookup"><span data-stu-id="dede1-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="dede1-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="dede1-104">Name</span></span>

<span data-ttu-id="dede1-105">`dotnet pack`-Pakietów kodu do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="dede1-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dede1-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="dede1-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="dede1-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="dede1-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies] [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dede1-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="dede1-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="dede1-109">Opis</span><span class="sxs-lookup"><span data-stu-id="dede1-109">Description</span></span>

<span data-ttu-id="dede1-110">`dotnet pack` Polecenie kompilacji projektu i tworzy pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="dede1-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="dede1-111">Wynik tego polecenia jest pakietem NuGet.</span><span class="sxs-lookup"><span data-stu-id="dede1-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="dede1-112">Jeśli `--include-symbols` opcji, jest tworzony przez inny pakiet zawierający symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="dede1-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="dede1-113">Zależności NuGet spakowana projektu są dodawane do *.nuspec* plików, dzięki czemu są poprawnie rozpoznać po zainstalowaniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="dede1-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="dede1-114">Odwołania projektu do projektu nie są umieszczone wewnątrz projektu.</span><span class="sxs-lookup"><span data-stu-id="dede1-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="dede1-115">Obecnie musi mieć pakiet w projekcie, jeśli masz zależności projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="dede1-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="dede1-116">Domyślnie `dotnet pack` najpierw tworzy projekt.</span><span class="sxs-lookup"><span data-stu-id="dede1-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="dede1-117">Jeśli chcesz uniknąć tego zachowania, należy przekazać `--no-build` opcji.</span><span class="sxs-lookup"><span data-stu-id="dede1-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="dede1-118">Często jest to przydatne w scenariuszach kompilacji ciągłej integracji (CI), gdy wiesz, że kod został wcześniej utworzony.</span><span class="sxs-lookup"><span data-stu-id="dede1-118">This is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="dede1-119">Możesz podać właściwości programu MSBuild do `dotnet pack` polecenia procesu pakowania.</span><span class="sxs-lookup"><span data-stu-id="dede1-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="dede1-120">Aby uzyskać więcej informacji, zobacz [właściwości metadanych NuGet](csproj.md#nuget-metadata-properties) i [dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="dede1-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

## <a name="arguments"></a><span data-ttu-id="dede1-121">Argumenty</span><span class="sxs-lookup"><span data-stu-id="dede1-121">Arguments</span></span>

`PROJECT`

<span data-ttu-id="dede1-122">Projekt do pakietu.</span><span class="sxs-lookup"><span data-stu-id="dede1-122">The project to pack.</span></span> <span data-ttu-id="dede1-123">Jest ścieżką do [plik csproj](csproj.md) lub w katalogu.</span><span class="sxs-lookup"><span data-stu-id="dede1-123">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="dede1-124">W przypadku jego pominięcia domyślnie do bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="dede1-124">If omitted, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="dede1-125">Opcje</span><span class="sxs-lookup"><span data-stu-id="dede1-125">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="dede1-126">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="dede1-126">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="dede1-127">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="dede1-127">Defines the build configuration.</span></span> <span data-ttu-id="dede1-128">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="dede1-128">The default value is `Debug`.</span></span>

<span data-ttu-id="dede1-129">`--force`Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dede1-129">`--force` Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="dede1-130">Jest to równoważne usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="dede1-130">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="dede1-131">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="dede1-131">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="dede1-132">Zawiera pliki źródłowe pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="dede1-132">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="dede1-133">Pliki źródłowe znajdują się w `src` folder w `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="dede1-133">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="dede1-134">Generuje symbole `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="dede1-134">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="dede1-135">Nie Skompiluj projekt przed pakowania.</span><span class="sxs-lookup"><span data-stu-id="dede1-135">Doesn't build the project before packing.</span></span>

`--no-dependencies`

<span data-ttu-id="dede1-136">Ignoruje odwołania projektu do projektu i przywraca tylko projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="dede1-136">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="dede1-137">Nie wykonać przywracanie niejawne, podczas uruchamiania polecenia.</span><span class="sxs-lookup"><span data-stu-id="dede1-137">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="dede1-138">Umieszcza pakiety wbudowanych w katalogu określonym.</span><span class="sxs-lookup"><span data-stu-id="dede1-138">Places the built packages in the directory specified.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="dede1-139">Określa docelowe środowisko uruchomieniowe pod kątem przywracania pakietów dla.</span><span class="sxs-lookup"><span data-stu-id="dede1-139">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="dede1-140">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="dede1-140">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-s|--serviceable`

<span data-ttu-id="dede1-141">Ustawia flagę obsługiwanych w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="dede1-141">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="dede1-142">Aby uzyskać więcej informacji, zobacz [blogu .NET: platforma .NET 4.5.1 zabezpieczeń firmy Microsoft obsługuje aktualizacje programu .NET NuGet biblioteki](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="dede1-142">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="dede1-143">Definiuje wartość dla `$(VersionSuffix)` właściwości programu MSBuild w projekcie.</span><span class="sxs-lookup"><span data-stu-id="dede1-143">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="dede1-144">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="dede1-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="dede1-145">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="dede1-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="dede1-146">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="dede1-146">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="dede1-147">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="dede1-147">Defines the build configuration.</span></span> <span data-ttu-id="dede1-148">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="dede1-148">The default value is `Debug`.</span></span>

`-h|--help`

<span data-ttu-id="dede1-149">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="dede1-149">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="dede1-150">Zawiera pliki źródłowe pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="dede1-150">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="dede1-151">Pliki źródłowe znajdują się w `src` folder w `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="dede1-151">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="dede1-152">Generuje symbole `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="dede1-152">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="dede1-153">Nie Skompiluj projekt przed pakowania.</span><span class="sxs-lookup"><span data-stu-id="dede1-153">Doesn't build the project before packing.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="dede1-154">Umieszcza pakiety wbudowanych w katalogu określonym.</span><span class="sxs-lookup"><span data-stu-id="dede1-154">Places the built packages in the directory specified.</span></span>

`-s|--serviceable`

<span data-ttu-id="dede1-155">Ustawia flagę obsługiwanych w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="dede1-155">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="dede1-156">Aby uzyskać więcej informacji, zobacz [blogu .NET: platforma .NET 4.5.1 zabezpieczeń firmy Microsoft obsługuje aktualizacje programu .NET NuGet biblioteki](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="dede1-156">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="dede1-157">Definiuje wartość dla `$(VersionSuffix)` właściwości programu MSBuild w projekcie.</span><span class="sxs-lookup"><span data-stu-id="dede1-157">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="dede1-158">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="dede1-158">Sets the verbosity level of the command.</span></span> <span data-ttu-id="dede1-159">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="dede1-159">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="dede1-160">Przykłady</span><span class="sxs-lookup"><span data-stu-id="dede1-160">Examples</span></span>

<span data-ttu-id="dede1-161">Pakiet projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="dede1-161">Pack the project in the current directory:</span></span>

`dotnet pack`

<span data-ttu-id="dede1-162">Pakiet `app1` projektu:</span><span class="sxs-lookup"><span data-stu-id="dede1-162">Pack the `app1` project:</span></span>

`dotnet pack ~/projects/app1/project.csproj`
    
<span data-ttu-id="dede1-163">Pakiet projektu w bieżącym katalogu i umieszczenie wynikowy pakietów do `nupkgs` folderu:</span><span class="sxs-lookup"><span data-stu-id="dede1-163">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

`dotnet pack --output nupkgs`

<span data-ttu-id="dede1-164">Pakiet projektu w bieżącym katalogu do `nupkgs` folderu i Pomiń krok kompilacji:</span><span class="sxs-lookup"><span data-stu-id="dede1-164">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

`dotnet pack --no-build --output nupkgs`

<span data-ttu-id="dede1-165">W projekcie sufiks wersji skonfigurowana jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` w *.csproj* pliku, pakiet bieżącego projektu i zaktualizować wynikowy wersja pakietu z danego sufiksu:</span><span class="sxs-lookup"><span data-stu-id="dede1-165">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

`dotnet pack --version-suffix "ci-1234"`

<span data-ttu-id="dede1-166">Ustaw wersję pakietu do `2.1.0` z `PackageVersion` właściwości programu MSBuild:</span><span class="sxs-lookup"><span data-stu-id="dede1-166">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

`dotnet pack /p:PackageVersion=2.1.0`
