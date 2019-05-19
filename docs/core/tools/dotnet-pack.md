---
title: polecenie pakietu DotNet
description: Polecenie pakietu dotnet tworzy pakiety NuGet do projektu .NET Core.
ms.date: 12/04/2018
ms.openlocfilehash: 5d48e5957e8095cc9ef4eaca2e1e1746c25a2a88
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65876044"
---
# <a name="dotnet-pack"></a><span data-ttu-id="cf090-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="cf090-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="cf090-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="cf090-104">Name</span></span>

<span data-ttu-id="cf090-105">`dotnet pack` -Pakiety kodu do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf090-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cf090-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="cf090-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="cf090-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="cf090-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cf090-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="cf090-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="cf090-109">Opis</span><span class="sxs-lookup"><span data-stu-id="cf090-109">Description</span></span>

<span data-ttu-id="cf090-110">`dotnet pack` Polecenie tworzy projekt i tworzy pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf090-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="cf090-111">Wynik tego polecenia jest pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf090-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="cf090-112">Jeśli `--include-symbols` opcji, jest tworzony inny pakiet zawierający symboli debugowania.</span><span class="sxs-lookup"><span data-stu-id="cf090-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="cf090-113">Zależności NuGet upakowaną projektu zostaną dodane do *.nuspec* pliku, dzięki czemu są one prawidłowo rozwiązany po zainstalowaniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="cf090-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="cf090-114">Odwołania projekt projekt nie są spakowane w projekcie.</span><span class="sxs-lookup"><span data-stu-id="cf090-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="cf090-115">Obecnie konieczne jest posiadanie pakietu dla projektu w przypadku zależności projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="cf090-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="cf090-116">Domyślnie `dotnet pack` najpierw tworzy projekt.</span><span class="sxs-lookup"><span data-stu-id="cf090-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="cf090-117">Jeśli chcesz uniknąć tego zachowania, należy przekazać `--no-build` opcji.</span><span class="sxs-lookup"><span data-stu-id="cf090-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="cf090-118">Ta opcja jest często przydatne w scenariuszach kompilacji ciągłej integracji (CI), gdy wiesz, że kod została wcześniej skompilowana.</span><span class="sxs-lookup"><span data-stu-id="cf090-118">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="cf090-119">Możesz podać właściwości programu MSBuild do `dotnet pack` polecenie, aby uzyskać proces pakowania.</span><span class="sxs-lookup"><span data-stu-id="cf090-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="cf090-120">Aby uzyskać więcej informacji, zobacz [właściwości metadanych NuGet](csproj.md#nuget-metadata-properties) i [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="cf090-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="cf090-121">[Przykłady](#examples) sekcja przedstawia sposób użycia przełącznika -p MSBuild z kilku różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="cf090-121">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="cf090-122">Projekty sieci Web nie są packable domyślnie.</span><span class="sxs-lookup"><span data-stu-id="cf090-122">Web projects aren't packable by default.</span></span> <span data-ttu-id="cf090-123">Aby zastąpić domyślne zachowanie, dodaj następującą właściwość do Twojej *.csproj* pliku:</span><span class="sxs-lookup"><span data-stu-id="cf090-123">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="cf090-124">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cf090-124">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="cf090-125">Projekt do pakietu.</span><span class="sxs-lookup"><span data-stu-id="cf090-125">The project to pack.</span></span> <span data-ttu-id="cf090-126">Jest ścieżką do [pliku csproj](csproj.md) lub w katalogu.</span><span class="sxs-lookup"><span data-stu-id="cf090-126">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="cf090-127">Jeśli nie zostanie określony, jego wartość domyślna w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cf090-127">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="cf090-128">Opcje</span><span class="sxs-lookup"><span data-stu-id="cf090-128">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="cf090-129">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="cf090-129">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="cf090-130">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cf090-130">Defines the build configuration.</span></span> <span data-ttu-id="cf090-131">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="cf090-131">The default value is `Debug`.</span></span>

* **`--force`**

  <span data-ttu-id="cf090-132">Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cf090-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="cf090-133">Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="cf090-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

* **`-h|--help`**

  <span data-ttu-id="cf090-134">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="cf090-134">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="cf090-135">Zawiera pliki źródłowe pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf090-135">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="cf090-136">Pliki źródłowe znajdują się w `src` folder wewnątrz `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="cf090-136">The sources files are included in the `src` folder within the `nupkg`.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="cf090-137">Generuje symbole `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="cf090-137">Generates the symbols `nupkg`.</span></span>

* **`--no-build`**

  <span data-ttu-id="cf090-138">Nie da się skompilować projektu przed pakowania.</span><span class="sxs-lookup"><span data-stu-id="cf090-138">Doesn't build the project before packing.</span></span> <span data-ttu-id="cf090-139">Ustawia również niejawnie `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="cf090-139">It also implicitly sets the `--no-restore` flag.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="cf090-140">Ignoruje odwołania projekt projekt i przywraca jedynie projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="cf090-140">Ignores project-to-project references and only restores the root project.</span></span>

* **`--no-restore`**

  <span data-ttu-id="cf090-141">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="cf090-141">Doesn't execute an implicit restore when running the command.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="cf090-142">Pakiety utworzone w katalogu wskazanym miejsca.</span><span class="sxs-lookup"><span data-stu-id="cf090-142">Places the built packages in the directory specified.</span></span>

* **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="cf090-143">Określa docelowe środowisko uruchomieniowe w celu przywrócenia pakietów dla.</span><span class="sxs-lookup"><span data-stu-id="cf090-143">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="cf090-144">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="cf090-144">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="cf090-145">Ustawia flagę zdatne do użytku w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="cf090-145">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="cf090-146">Aby uzyskać więcej informacji, zobacz [bloga platformy .NET: .NET 4.5.1 zabezpieczeń firmy Microsoft obsługuje aktualizacje programu .NET NuGet biblioteki](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="cf090-146">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="cf090-147">Definiuje wartość dla `$(VersionSuffix)` właściwości programu MSBuild w projekcie.</span><span class="sxs-lookup"><span data-stu-id="cf090-147">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="cf090-148">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="cf090-148">Sets the verbosity level of the command.</span></span> <span data-ttu-id="cf090-149">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="cf090-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="cf090-150">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="cf090-150">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="cf090-151">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cf090-151">Defines the build configuration.</span></span> <span data-ttu-id="cf090-152">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="cf090-152">The default value is `Debug`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="cf090-153">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="cf090-153">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="cf090-154">Zawiera pliki źródłowe pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf090-154">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="cf090-155">Pliki źródłowe znajdują się w `src` folder wewnątrz `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="cf090-155">The sources files are included in the `src` folder within the `nupkg`.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="cf090-156">Generuje symbole `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="cf090-156">Generates the symbols `nupkg`.</span></span>

* **`--no-build`**

  <span data-ttu-id="cf090-157">Nie da się skompilować projektu przed pakowania.</span><span class="sxs-lookup"><span data-stu-id="cf090-157">Doesn't build the project before packing.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="cf090-158">Pakiety utworzone w katalogu wskazanym miejsca.</span><span class="sxs-lookup"><span data-stu-id="cf090-158">Places the built packages in the directory specified.</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="cf090-159">Ustawia flagę zdatne do użytku w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="cf090-159">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="cf090-160">Aby uzyskać więcej informacji, zobacz [bloga platformy .NET: .NET 4.5.1 zabezpieczeń firmy Microsoft obsługuje aktualizacje programu .NET NuGet biblioteki](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="cf090-160">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="cf090-161">Definiuje wartość dla `$(VersionSuffix)` właściwości programu MSBuild w projekcie.</span><span class="sxs-lookup"><span data-stu-id="cf090-161">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="cf090-162">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="cf090-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="cf090-163">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="cf090-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="cf090-164">Przykłady</span><span class="sxs-lookup"><span data-stu-id="cf090-164">Examples</span></span>

* <span data-ttu-id="cf090-165">Pakiet projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="cf090-165">Pack the project in the current directory:</span></span>

  ```console
  dotnet pack
  ```

* <span data-ttu-id="cf090-166">Pakiet `app1` projektu:</span><span class="sxs-lookup"><span data-stu-id="cf090-166">Pack the `app1` project:</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

* <span data-ttu-id="cf090-167">Pakowanie projekt w bieżącym katalogu i umieścić wynikowy pakietów do `nupkgs` folderu:</span><span class="sxs-lookup"><span data-stu-id="cf090-167">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```console
  dotnet pack --output nupkgs
  ```

* <span data-ttu-id="cf090-168">Pakiet projektu w bieżącym katalogu do `nupkgs` folder i Pomiń krok kompilacji:</span><span class="sxs-lookup"><span data-stu-id="cf090-168">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```console
  dotnet pack --no-build --output nupkgs
  ```

* <span data-ttu-id="cf090-169">Z projektem sufiks wersji skonfigurowana jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` w *.csproj* pliku, pakiet bieżącego projektu i zaktualizuj wynikowy wersja pakietu przy użyciu danego sufiksu:</span><span class="sxs-lookup"><span data-stu-id="cf090-169">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

* <span data-ttu-id="cf090-170">Ustaw wersję pakietu `2.1.0` z `PackageVersion` właściwości MSBuild:</span><span class="sxs-lookup"><span data-stu-id="cf090-170">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

* <span data-ttu-id="cf090-171">Projekt dla określonego pakietu [platformę docelową](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="cf090-171">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

* <span data-ttu-id="cf090-172">Pakowanie projektu i użyć określonego środowiska uruchomieniowego (system Windows 10) dla operacji przywracania (.NET Core SDK 2.0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="cf090-172">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

  ```console
  dotnet pack --runtime win10-x64
  ```

* <span data-ttu-id="cf090-173">Pakiet projekt za pomocą [pliku .nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span><span class="sxs-lookup"><span data-stu-id="cf090-173">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj /p:NuspecFile=~/projects/app1/project.nuspec /p:NuspecBasePath=~/projects/app1/nuget
  ```
