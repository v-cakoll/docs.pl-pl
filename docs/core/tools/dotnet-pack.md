---
title: polecenie pakietu DotNet - interfejsu wiersza polecenia platformy .NET Core
description: Polecenie pakietu dotnet tworzy pakiety NuGet do projektu .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 8c2569ec7598b21fe9b673176143d0e54b9eb065
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204854"
---
# <a name="dotnet-pack"></a><span data-ttu-id="ee88f-103">pakietu DotNet</span><span class="sxs-lookup"><span data-stu-id="ee88f-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ee88f-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="ee88f-104">Name</span></span>

<span data-ttu-id="ee88f-105">`dotnet pack` -Pakiety kodu do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="ee88f-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ee88f-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="ee88f-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ee88f-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ee88f-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ee88f-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ee88f-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="ee88f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="ee88f-109">Description</span></span>

<span data-ttu-id="ee88f-110">`dotnet pack` Polecenie tworzy projekt i tworzy pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="ee88f-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="ee88f-111">Wynik tego polecenia jest pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="ee88f-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="ee88f-112">Jeśli `--include-symbols` opcji, jest tworzony inny pakiet zawierający symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="ee88f-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="ee88f-113">Zależności NuGet upakowaną projektu zostaną dodane do *.nuspec* pliku, dzięki czemu są one prawidłowo rozwiązany po zainstalowaniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="ee88f-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="ee88f-114">Odwołania projekt projekt nie są spakowane w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ee88f-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="ee88f-115">Obecnie konieczne jest posiadanie pakietu dla projektu w przypadku zależności projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="ee88f-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="ee88f-116">Domyślnie `dotnet pack` najpierw tworzy projekt.</span><span class="sxs-lookup"><span data-stu-id="ee88f-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="ee88f-117">Jeśli chcesz uniknąć tego zachowania, należy przekazać `--no-build` opcji.</span><span class="sxs-lookup"><span data-stu-id="ee88f-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="ee88f-118">Ta opcja jest często przydatne w scenariuszach kompilacji ciągłej integracji (CI), gdy wiesz, że kod została wcześniej skompilowana.</span><span class="sxs-lookup"><span data-stu-id="ee88f-118">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="ee88f-119">Możesz podać właściwości programu MSBuild do `dotnet pack` polecenie, aby uzyskać proces pakowania.</span><span class="sxs-lookup"><span data-stu-id="ee88f-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="ee88f-120">Aby uzyskać więcej informacji, zobacz [właściwości metadanych NuGet](csproj.md#nuget-metadata-properties) i [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="ee88f-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="ee88f-121">[Przykłady](#examples) sekcja przedstawia sposób użycia przełącznika MSBuild z kilku różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="ee88f-121">The [Examples](#examples) section shows how to use the MSBuild /p switch for a couple of different scenarios.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="ee88f-122">Argumenty</span><span class="sxs-lookup"><span data-stu-id="ee88f-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="ee88f-123">Projekt do pakietu.</span><span class="sxs-lookup"><span data-stu-id="ee88f-123">The project to pack.</span></span> <span data-ttu-id="ee88f-124">Jest ścieżką do [pliku csproj](csproj.md) lub w katalogu.</span><span class="sxs-lookup"><span data-stu-id="ee88f-124">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="ee88f-125">Jeśli nie zostanie określony, jego wartość domyślna w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ee88f-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="ee88f-126">Opcje</span><span class="sxs-lookup"><span data-stu-id="ee88f-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="ee88f-127">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="ee88f-127">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="ee88f-128">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ee88f-128">Defines the build configuration.</span></span> <span data-ttu-id="ee88f-129">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="ee88f-129">The default value is `Debug`.</span></span>

`--force`

<span data-ttu-id="ee88f-130">Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="ee88f-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="ee88f-131">Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="ee88f-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="ee88f-132">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="ee88f-132">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="ee88f-133">Zawiera pliki źródłowe pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="ee88f-133">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="ee88f-134">Pliki źródłowe znajdują się w `src` folder wewnątrz `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="ee88f-134">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="ee88f-135">Generuje symbole `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="ee88f-135">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="ee88f-136">Nie da się skompilować projektu przed pakowania.</span><span class="sxs-lookup"><span data-stu-id="ee88f-136">Doesn't build the project before packing.</span></span> <span data-ttu-id="ee88f-137">Ustawia ona również niejawne `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="ee88f-137">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="ee88f-138">Ignoruje odwołania projekt projekt i przywraca jedynie projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="ee88f-138">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="ee88f-139">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="ee88f-139">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ee88f-140">Pakiety utworzone w katalogu wskazanym miejsca.</span><span class="sxs-lookup"><span data-stu-id="ee88f-140">Places the built packages in the directory specified.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="ee88f-141">Określa docelowe środowisko uruchomieniowe w celu przywrócenia pakietów dla.</span><span class="sxs-lookup"><span data-stu-id="ee88f-141">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="ee88f-142">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="ee88f-142">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-s|--serviceable`

<span data-ttu-id="ee88f-143">Ustawia flagę zdatne do użytku w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="ee88f-143">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="ee88f-144">Aby uzyskać więcej informacji, zobacz [bloga platformy .NET: .NET 4.5.1 zabezpieczeń firmy Microsoft obsługuje aktualizacje programu .NET NuGet biblioteki](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="ee88f-144">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="ee88f-145">Definiuje wartość dla `$(VersionSuffix)` właściwości programu MSBuild w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ee88f-145">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ee88f-146">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="ee88f-146">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ee88f-147">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ee88f-147">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="ee88f-148">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="ee88f-148">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="ee88f-149">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ee88f-149">Defines the build configuration.</span></span> <span data-ttu-id="ee88f-150">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="ee88f-150">The default value is `Debug`.</span></span>

`-h|--help`

<span data-ttu-id="ee88f-151">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="ee88f-151">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="ee88f-152">Zawiera pliki źródłowe pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="ee88f-152">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="ee88f-153">Pliki źródłowe znajdują się w `src` folder wewnątrz `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="ee88f-153">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="ee88f-154">Generuje symbole `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="ee88f-154">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="ee88f-155">Nie da się skompilować projektu przed pakowania.</span><span class="sxs-lookup"><span data-stu-id="ee88f-155">Doesn't build the project before packing.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="ee88f-156">Pakiety utworzone w katalogu wskazanym miejsca.</span><span class="sxs-lookup"><span data-stu-id="ee88f-156">Places the built packages in the directory specified.</span></span>

`-s|--serviceable`

<span data-ttu-id="ee88f-157">Ustawia flagę zdatne do użytku w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="ee88f-157">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="ee88f-158">Aby uzyskać więcej informacji, zobacz [bloga platformy .NET: .NET 4.5.1 zabezpieczeń firmy Microsoft obsługuje aktualizacje programu .NET NuGet biblioteki](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="ee88f-158">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="ee88f-159">Definiuje wartość dla `$(VersionSuffix)` właściwości programu MSBuild w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ee88f-159">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ee88f-160">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="ee88f-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ee88f-161">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ee88f-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="ee88f-162">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ee88f-162">Examples</span></span>

<span data-ttu-id="ee88f-163">Pakiet projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="ee88f-163">Pack the project in the current directory:</span></span>

`dotnet pack`

<span data-ttu-id="ee88f-164">Pakiet `app1` projektu:</span><span class="sxs-lookup"><span data-stu-id="ee88f-164">Pack the `app1` project:</span></span>

`dotnet pack ~/projects/app1/project.csproj`

<span data-ttu-id="ee88f-165">Pakowanie projekt w bieżącym katalogu i umieścić wynikowy pakietów do `nupkgs` folderu:</span><span class="sxs-lookup"><span data-stu-id="ee88f-165">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

`dotnet pack --output nupkgs`

<span data-ttu-id="ee88f-166">Pakiet projektu w bieżącym katalogu do `nupkgs` folder i Pomiń krok kompilacji:</span><span class="sxs-lookup"><span data-stu-id="ee88f-166">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

`dotnet pack --no-build --output nupkgs`

<span data-ttu-id="ee88f-167">Z projektem sufiks wersji skonfigurowana jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` w *.csproj* pliku, pakiet bieżącego projektu i zaktualizuj wynikowy wersja pakietu przy użyciu danego sufiksu:</span><span class="sxs-lookup"><span data-stu-id="ee88f-167">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

`dotnet pack --version-suffix "ci-1234"`

<span data-ttu-id="ee88f-168">Ustaw wersję pakietu `2.1.0` z `PackageVersion` właściwości MSBuild:</span><span class="sxs-lookup"><span data-stu-id="ee88f-168">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

`dotnet pack /p:PackageVersion=2.1.0`

<span data-ttu-id="ee88f-169">Projekt dla określonego pakietu [platformę docelową](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="ee88f-169">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

`dotnet pack /p:TargetFrameworks=net45`

<span data-ttu-id="ee88f-170">Pakowanie projektu i użyć określonego środowiska uruchomieniowego (system Windows 10) dla operacji przywracania (.NET Core SDK 2.0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="ee88f-170">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet pack --runtime win10-x64`