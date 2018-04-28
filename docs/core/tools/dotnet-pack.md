---
title: polecenie Pakiet DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie Pakiet dotnet tworzy pakietów NuGet dla projektu platformy .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 03/10/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: fdbf3b23813f09ad9902f6b0457f176139b405a4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-pack"></a><span data-ttu-id="7e004-103">Pakiet DotNet</span><span class="sxs-lookup"><span data-stu-id="7e004-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="7e004-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7e004-104">Name</span></span>

<span data-ttu-id="7e004-105">`dotnet pack` -Pakietów kodu do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="7e004-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7e004-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="7e004-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7e004-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7e004-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7e004-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7e004-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="7e004-109">Opis</span><span class="sxs-lookup"><span data-stu-id="7e004-109">Description</span></span>

<span data-ttu-id="7e004-110">`dotnet pack` Polecenie kompilacji projektu i tworzy pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="7e004-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="7e004-111">Wynik tego polecenia jest pakietem NuGet.</span><span class="sxs-lookup"><span data-stu-id="7e004-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="7e004-112">Jeśli `--include-symbols` opcji, jest tworzony przez inny pakiet zawierający symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="7e004-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="7e004-113">Zależności NuGet spakowana projektu są dodawane do *.nuspec* plików, dzięki czemu są poprawnie rozpoznać po zainstalowaniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="7e004-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="7e004-114">Odwołania projektu do projektu nie są umieszczone wewnątrz projektu.</span><span class="sxs-lookup"><span data-stu-id="7e004-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="7e004-115">Obecnie musi mieć pakiet w projekcie, jeśli masz zależności projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="7e004-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="7e004-116">Domyślnie `dotnet pack` najpierw tworzy projekt.</span><span class="sxs-lookup"><span data-stu-id="7e004-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="7e004-117">Jeśli chcesz uniknąć tego zachowania, należy przekazać `--no-build` opcji.</span><span class="sxs-lookup"><span data-stu-id="7e004-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="7e004-118">Często jest to przydatne w scenariuszach kompilacji ciągłej integracji (CI), gdy wiesz, że kod został wcześniej utworzony.</span><span class="sxs-lookup"><span data-stu-id="7e004-118">This is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="7e004-119">Możesz podać właściwości programu MSBuild do `dotnet pack` polecenia procesu pakowania.</span><span class="sxs-lookup"><span data-stu-id="7e004-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="7e004-120">Aby uzyskać więcej informacji, zobacz [właściwości metadanych NuGet](csproj.md#nuget-metadata-properties) i [dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="7e004-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="7e004-121">[Przykłady](#examples) sekcji przedstawia sposób użycia przełącznika MSBuild z kilku różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="7e004-121">The [Examples](#examples) section shows how to use the MSBuild /p switch for a couple of different scenarios.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="7e004-122">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7e004-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="7e004-123">Projekt do pakietu.</span><span class="sxs-lookup"><span data-stu-id="7e004-123">The project to pack.</span></span> <span data-ttu-id="7e004-124">Jest ścieżką do [plik csproj](csproj.md) lub w katalogu.</span><span class="sxs-lookup"><span data-stu-id="7e004-124">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="7e004-125">W przypadku jego pominięcia domyślnie do bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="7e004-125">If omitted, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="7e004-126">Opcje</span><span class="sxs-lookup"><span data-stu-id="7e004-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7e004-127">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7e004-127">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="7e004-128">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7e004-128">Defines the build configuration.</span></span> <span data-ttu-id="7e004-129">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="7e004-129">The default value is `Debug`.</span></span>

<span data-ttu-id="7e004-130">`--force` Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7e004-130">`--force` Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="7e004-131">Jest to równoważne usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="7e004-131">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="7e004-132">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="7e004-132">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="7e004-133">Zawiera pliki źródłowe pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="7e004-133">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="7e004-134">Pliki źródłowe znajdują się w `src` folder w `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="7e004-134">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="7e004-135">Generuje symbole `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="7e004-135">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="7e004-136">Nie Skompiluj projekt przed pakowania.</span><span class="sxs-lookup"><span data-stu-id="7e004-136">Doesn't build the project before packing.</span></span>

`--no-dependencies`

<span data-ttu-id="7e004-137">Ignoruje odwołania projektu do projektu i przywraca tylko projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="7e004-137">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="7e004-138">Nie wykonać przywracanie niejawne, podczas uruchamiania polecenia.</span><span class="sxs-lookup"><span data-stu-id="7e004-138">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="7e004-139">Umieszcza pakiety wbudowanych w katalogu określonym.</span><span class="sxs-lookup"><span data-stu-id="7e004-139">Places the built packages in the directory specified.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="7e004-140">Określa docelowe środowisko uruchomieniowe pod kątem przywracania pakietów dla.</span><span class="sxs-lookup"><span data-stu-id="7e004-140">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="7e004-141">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="7e004-141">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-s|--serviceable`

<span data-ttu-id="7e004-142">Ustawia flagę obsługiwanych w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="7e004-142">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="7e004-143">Aby uzyskać więcej informacji, zobacz [blogu .NET: platforma .NET 4.5.1 zabezpieczeń firmy Microsoft obsługuje aktualizacje programu .NET NuGet biblioteki](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="7e004-143">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="7e004-144">Definiuje wartość dla `$(VersionSuffix)` właściwości programu MSBuild w projekcie.</span><span class="sxs-lookup"><span data-stu-id="7e004-144">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="7e004-145">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="7e004-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7e004-146">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="7e004-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7e004-147">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7e004-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="7e004-148">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7e004-148">Defines the build configuration.</span></span> <span data-ttu-id="7e004-149">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="7e004-149">The default value is `Debug`.</span></span>

`-h|--help`

<span data-ttu-id="7e004-150">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="7e004-150">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="7e004-151">Zawiera pliki źródłowe pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="7e004-151">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="7e004-152">Pliki źródłowe znajdują się w `src` folder w `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="7e004-152">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="7e004-153">Generuje symbole `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="7e004-153">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="7e004-154">Nie Skompiluj projekt przed pakowania.</span><span class="sxs-lookup"><span data-stu-id="7e004-154">Doesn't build the project before packing.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="7e004-155">Umieszcza pakiety wbudowanych w katalogu określonym.</span><span class="sxs-lookup"><span data-stu-id="7e004-155">Places the built packages in the directory specified.</span></span>

`-s|--serviceable`

<span data-ttu-id="7e004-156">Ustawia flagę obsługiwanych w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="7e004-156">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="7e004-157">Aby uzyskać więcej informacji, zobacz [blogu .NET: platforma .NET 4.5.1 zabezpieczeń firmy Microsoft obsługuje aktualizacje programu .NET NuGet biblioteki](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="7e004-157">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="7e004-158">Definiuje wartość dla `$(VersionSuffix)` właściwości programu MSBuild w projekcie.</span><span class="sxs-lookup"><span data-stu-id="7e004-158">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="7e004-159">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="7e004-159">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7e004-160">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="7e004-160">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="7e004-161">Przykłady</span><span class="sxs-lookup"><span data-stu-id="7e004-161">Examples</span></span>

<span data-ttu-id="7e004-162">Pakiet projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="7e004-162">Pack the project in the current directory:</span></span>

`dotnet pack`

<span data-ttu-id="7e004-163">Pakiet `app1` projektu:</span><span class="sxs-lookup"><span data-stu-id="7e004-163">Pack the `app1` project:</span></span>

`dotnet pack ~/projects/app1/project.csproj`

<span data-ttu-id="7e004-164">Pakiet projektu w bieżącym katalogu i umieszczenie wynikowy pakietów do `nupkgs` folderu:</span><span class="sxs-lookup"><span data-stu-id="7e004-164">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

`dotnet pack --output nupkgs`

<span data-ttu-id="7e004-165">Pakiet projektu w bieżącym katalogu do `nupkgs` folderu i Pomiń krok kompilacji:</span><span class="sxs-lookup"><span data-stu-id="7e004-165">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

`dotnet pack --no-build --output nupkgs`

<span data-ttu-id="7e004-166">W projekcie sufiks wersji skonfigurowana jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` w *.csproj* pliku, pakiet bieżącego projektu i zaktualizować wynikowy wersja pakietu z danego sufiksu:</span><span class="sxs-lookup"><span data-stu-id="7e004-166">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

`dotnet pack --version-suffix "ci-1234"`

<span data-ttu-id="7e004-167">Ustaw wersję pakietu do `2.1.0` z `PackageVersion` właściwości programu MSBuild:</span><span class="sxs-lookup"><span data-stu-id="7e004-167">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

`dotnet pack /p:PackageVersion=2.1.0`

<span data-ttu-id="7e004-168">Projekt dla określonego pakietu [platformy docelowej](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="7e004-168">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

`dotnet pack /p:TargetFrameworks=net45`

<span data-ttu-id="7e004-169">Pakiet projektu i użyć określonego środowiska wykonawczego (systemu Windows Windows 10) dla operacji przywracania (.NET Core SDK 2.0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="7e004-169">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet pack --runtime win10-x64`