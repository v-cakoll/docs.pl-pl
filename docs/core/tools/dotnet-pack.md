---
title: polecenie dotnet Pack
description: Polecenie programu dotnet Pack tworzy pakiety NuGet dla projektu .NET Core.
ms.date: 12/04/2018
ms.openlocfilehash: c5c00f3bb06e5bc5579c0d3d6bdd39fbdf3db656
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202842"
---
# <a name="dotnet-pack"></a><span data-ttu-id="7f48b-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="7f48b-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="7f48b-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7f48b-104">Name</span></span>

<span data-ttu-id="7f48b-105">`dotnet pack`-Pakuje kod do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="7f48b-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7f48b-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="7f48b-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7f48b-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7f48b-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```console
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7f48b-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7f48b-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="7f48b-109">Opis</span><span class="sxs-lookup"><span data-stu-id="7f48b-109">Description</span></span>

<span data-ttu-id="7f48b-110">`dotnet pack` Polecenie kompiluje projekt i tworzy pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="7f48b-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="7f48b-111">Wynikiem tego polecenia jest pakiet NuGet.</span><span class="sxs-lookup"><span data-stu-id="7f48b-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="7f48b-112">Jeśli ta `--include-symbols` opcja jest obecna, tworzony jest inny pakiet zawierający symbole debugowania.</span><span class="sxs-lookup"><span data-stu-id="7f48b-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="7f48b-113">Zależności NuGet spakowanego projektu są dodawane do pliku *. nuspec* , więc są one poprawnie rozwiązane po zainstalowaniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="7f48b-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="7f48b-114">Odwołania projektu do projektu nie są spakowane w projekcie.</span><span class="sxs-lookup"><span data-stu-id="7f48b-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="7f48b-115">Obecnie należy mieć pakiet dla każdego projektu, jeśli istnieją zależności między projektami.</span><span class="sxs-lookup"><span data-stu-id="7f48b-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="7f48b-116">Domyślnie program `dotnet pack` kompiluje projekt.</span><span class="sxs-lookup"><span data-stu-id="7f48b-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="7f48b-117">Jeśli chcesz uniknąć tego zachowania, Przekaż `--no-build` opcję.</span><span class="sxs-lookup"><span data-stu-id="7f48b-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="7f48b-118">Ta opcja jest często przydatna w scenariuszach kompilacji ciągłej integracji (CI), w których wiadomo, że kod został wcześniej skompilowany.</span><span class="sxs-lookup"><span data-stu-id="7f48b-118">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="7f48b-119">Można podać właściwości programu MSBuild do `dotnet pack` polecenia dla procesu pakowania.</span><span class="sxs-lookup"><span data-stu-id="7f48b-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="7f48b-120">Aby uzyskać więcej informacji, zobacz [właściwości metadanych NuGet](csproj.md#nuget-metadata-properties) i [Dokumentacja wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="7f48b-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="7f48b-121">W sekcji [przykłady](#examples) pokazano, jak używać przełącznika MSBuild-p w przypadku kilku różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="7f48b-121">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="7f48b-122">Projekty sieci Web nie są domyślnie objęte pakietem.</span><span class="sxs-lookup"><span data-stu-id="7f48b-122">Web projects aren't packable by default.</span></span> <span data-ttu-id="7f48b-123">Aby zastąpić zachowanie domyślne, Dodaj następującą właściwość do pliku *. csproj* :</span><span class="sxs-lookup"><span data-stu-id="7f48b-123">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="7f48b-124">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7f48b-124">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="7f48b-125">Projekt do spakowania.</span><span class="sxs-lookup"><span data-stu-id="7f48b-125">The project to pack.</span></span> <span data-ttu-id="7f48b-126">Jest to ścieżka do [pliku csproj](csproj.md) lub katalogu.</span><span class="sxs-lookup"><span data-stu-id="7f48b-126">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="7f48b-127">Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="7f48b-127">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="7f48b-128">Opcje</span><span class="sxs-lookup"><span data-stu-id="7f48b-128">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="7f48b-129">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="7f48b-129">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="7f48b-130">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7f48b-130">Defines the build configuration.</span></span> <span data-ttu-id="7f48b-131">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="7f48b-131">The default value is `Debug`.</span></span>

* **`--force`**

  <span data-ttu-id="7f48b-132">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7f48b-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="7f48b-133">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="7f48b-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

* **`-h|--help`**

  <span data-ttu-id="7f48b-134">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="7f48b-134">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="7f48b-135">Zawiera pliki źródłowe w pakiecie NuGet.</span><span class="sxs-lookup"><span data-stu-id="7f48b-135">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="7f48b-136">Pliki źródeł znajdują się w `src` folderze programu. `nupkg`</span><span class="sxs-lookup"><span data-stu-id="7f48b-136">The sources files are included in the `src` folder within the `nupkg`.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="7f48b-137">Generuje symbole `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="7f48b-137">Generates the symbols `nupkg`.</span></span>

* **`--no-build`**

  <span data-ttu-id="7f48b-138">Nie kompiluje projektu przed opakowaniem.</span><span class="sxs-lookup"><span data-stu-id="7f48b-138">Doesn't build the project before packing.</span></span> <span data-ttu-id="7f48b-139">Również niejawnie ustawia `--no-restore` flagę.</span><span class="sxs-lookup"><span data-stu-id="7f48b-139">It also implicitly sets the `--no-restore` flag.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="7f48b-140">Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.</span><span class="sxs-lookup"><span data-stu-id="7f48b-140">Ignores project-to-project references and only restores the root project.</span></span>

* **`--no-restore`**

  <span data-ttu-id="7f48b-141">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="7f48b-141">Doesn't execute an implicit restore when running the command.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="7f48b-142">Umieszcza skompilowane pakiety w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7f48b-142">Places the built packages in the directory specified.</span></span>

* **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="7f48b-143">Określa docelowy środowisko uruchomieniowe, dla którego mają zostać przywrócone pakiety.</span><span class="sxs-lookup"><span data-stu-id="7f48b-143">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="7f48b-144">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="7f48b-144">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="7f48b-145">Ustawia flagę obsługi w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="7f48b-145">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="7f48b-146">Aby uzyskać więcej informacji, zobacz [blog platformy .NET: .NET 4.5.1 obsługuje aktualizacje zabezpieczeń firmy Microsoft dla bibliotek NuGet programu .NET](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="7f48b-146">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="7f48b-147">Definiuje wartość `$(VersionSuffix)` właściwości programu MSBuild w projekcie.</span><span class="sxs-lookup"><span data-stu-id="7f48b-147">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="7f48b-148">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="7f48b-148">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7f48b-149">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="7f48b-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="7f48b-150">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="7f48b-150">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="7f48b-151">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7f48b-151">Defines the build configuration.</span></span> <span data-ttu-id="7f48b-152">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="7f48b-152">The default value is `Debug`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="7f48b-153">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="7f48b-153">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="7f48b-154">Zawiera pliki źródłowe w pakiecie NuGet.</span><span class="sxs-lookup"><span data-stu-id="7f48b-154">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="7f48b-155">Pliki źródeł znajdują się w `src` folderze programu. `nupkg`</span><span class="sxs-lookup"><span data-stu-id="7f48b-155">The sources files are included in the `src` folder within the `nupkg`.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="7f48b-156">Generuje symbole `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="7f48b-156">Generates the symbols `nupkg`.</span></span>

* **`--no-build`**

  <span data-ttu-id="7f48b-157">Nie kompiluje projektu przed opakowaniem.</span><span class="sxs-lookup"><span data-stu-id="7f48b-157">Doesn't build the project before packing.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="7f48b-158">Umieszcza skompilowane pakiety w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="7f48b-158">Places the built packages in the directory specified.</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="7f48b-159">Ustawia flagę obsługi w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="7f48b-159">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="7f48b-160">Aby uzyskać więcej informacji, zobacz [blog platformy .NET: .NET 4.5.1 obsługuje aktualizacje zabezpieczeń firmy Microsoft dla bibliotek NuGet programu .NET](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="7f48b-160">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="7f48b-161">Definiuje wartość `$(VersionSuffix)` właściwości programu MSBuild w projekcie.</span><span class="sxs-lookup"><span data-stu-id="7f48b-161">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="7f48b-162">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="7f48b-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7f48b-163">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="7f48b-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="7f48b-164">Przykłady</span><span class="sxs-lookup"><span data-stu-id="7f48b-164">Examples</span></span>

* <span data-ttu-id="7f48b-165">Pakowanie projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="7f48b-165">Pack the project in the current directory:</span></span>

  ```console
  dotnet pack
  ```

* <span data-ttu-id="7f48b-166">`app1` Pakowanie projektu:</span><span class="sxs-lookup"><span data-stu-id="7f48b-166">Pack the `app1` project:</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

* <span data-ttu-id="7f48b-167">Pakowanie projektu w bieżącym katalogu i umieszczenie w nim pakietów `nupkgs` powstających:</span><span class="sxs-lookup"><span data-stu-id="7f48b-167">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```console
  dotnet pack --output nupkgs
  ```

* <span data-ttu-id="7f48b-168">Pakowanie projektu w bieżącym katalogu do `nupkgs` folderu i pomijanie kroku kompilacji:</span><span class="sxs-lookup"><span data-stu-id="7f48b-168">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```console
  dotnet pack --no-build --output nupkgs
  ```

* <span data-ttu-id="7f48b-169">Przy użyciu sufiksu wersji projektu skonfigurowanego `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` jako w pliku *. csproj* należy spakować bieżący projekt i zaktualizować uzyskaną wersję pakietu przy użyciu danego sufiksu:</span><span class="sxs-lookup"><span data-stu-id="7f48b-169">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

* <span data-ttu-id="7f48b-170">Ustaw wersję pakietu na `2.1.0` `PackageVersion` za pomocą właściwości MSBuild:</span><span class="sxs-lookup"><span data-stu-id="7f48b-170">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

* <span data-ttu-id="7f48b-171">Pakowanie projektu dla konkretnej [platformy docelowej](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="7f48b-171">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

* <span data-ttu-id="7f48b-172">Pakowanie projektu i użycie określonego środowiska uruchomieniowego (Windows 10) dla operacji przywracania (zestaw .NET Core SDK 2,0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="7f48b-172">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

  ```console
  dotnet pack --runtime win10-x64
  ```

* <span data-ttu-id="7f48b-173">Pakowanie projektu przy użyciu [pliku. nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span><span class="sxs-lookup"><span data-stu-id="7f48b-173">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj /p:NuspecFile=~/projects/app1/project.nuspec /p:NuspecBasePath=~/projects/app1/nuget
  ```
