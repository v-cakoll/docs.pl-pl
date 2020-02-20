---
title: polecenie dotnet Pack
description: Polecenie programu dotnet Pack tworzy pakiety NuGet dla projektu .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 865262f1eb314f9b7e8ee713c573a965e89ded93
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503644"
---
# <a name="dotnet-pack"></a><span data-ttu-id="cbeb8-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="cbeb8-103">dotnet pack</span></span>

<span data-ttu-id="cbeb8-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 2. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="cbeb8-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cbeb8-105">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="cbeb8-105">Name</span></span>

<span data-ttu-id="cbeb8-106">`dotnet pack` — pakuje kod do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cbeb8-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="cbeb8-107">Synopsis</span></span>

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable]
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a><span data-ttu-id="cbeb8-108">Opis</span><span class="sxs-lookup"><span data-stu-id="cbeb8-108">Description</span></span>

<span data-ttu-id="cbeb8-109">`dotnet pack` polecenie kompiluje projekt i tworzy pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="cbeb8-110">Wynikiem tego polecenia jest pakiet NuGet (czyli plik *. nupkg* ).</span><span class="sxs-lookup"><span data-stu-id="cbeb8-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span>

<span data-ttu-id="cbeb8-111">Jeśli chcesz wygenerować pakiet zawierający symbole debugowania, dostępne są dwie opcje:</span><span class="sxs-lookup"><span data-stu-id="cbeb8-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="cbeb8-112">`--include-symbols` — tworzy pakiet symboli.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="cbeb8-113">`--include-source` — tworzy pakiet symboli z folderem `src` wewnątrz zawierającym pliki źródłowe.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="cbeb8-114">Zależności NuGet spakowanego projektu są dodawane do pliku *. nuspec* , więc są one poprawnie rozwiązane po zainstalowaniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="cbeb8-115">Odwołania projektu do projektu nie są spakowane w projekcie.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="cbeb8-116">Obecnie należy mieć pakiet dla każdego projektu, jeśli istnieją zależności między projektami.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="cbeb8-117">Domyślnie `dotnet pack` kompiluje projekt.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="cbeb8-118">Aby uniknąć tego zachowania, należy przekazać opcję `--no-build`.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="cbeb8-119">Ta opcja jest często przydatna w scenariuszach kompilacji ciągłej integracji (CI), w których wiadomo, że kod został wcześniej skompilowany.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="cbeb8-120">Można podać właściwości programu MSBuild w `dotnet pack` polecenie dla procesu pakowania.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-120">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="cbeb8-121">Aby uzyskać więcej informacji, zobacz [właściwości metadanych NuGet](csproj.md#nuget-metadata-properties) i [Dokumentacja wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="cbeb8-121">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="cbeb8-122">W sekcji [przykłady](#examples) pokazano, jak używać przełącznika MSBuild-p w przypadku kilku różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-122">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="cbeb8-123">Projekty sieci Web nie są domyślnie objęte pakietem.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-123">Web projects aren't packable by default.</span></span> <span data-ttu-id="cbeb8-124">Aby zastąpić zachowanie domyślne, Dodaj następującą właściwość do pliku *. csproj* :</span><span class="sxs-lookup"><span data-stu-id="cbeb8-124">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="cbeb8-125">Argumenty</span><span class="sxs-lookup"><span data-stu-id="cbeb8-125">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="cbeb8-126">Projekt lub rozwiązanie do spakowania.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-126">The project or solution to pack.</span></span> <span data-ttu-id="cbeb8-127">Jest to ścieżka do [pliku csproj](csproj.md), pliku rozwiązania lub do katalogu.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-127">It's either a path to a [csproj file](csproj.md), a solution file, or to a directory.</span></span> <span data-ttu-id="cbeb8-128">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla pliku projektu lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-128">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="cbeb8-129">Opcje</span><span class="sxs-lookup"><span data-stu-id="cbeb8-129">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="cbeb8-130">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-130">Defines the build configuration.</span></span> <span data-ttu-id="cbeb8-131">Wartość domyślna dla większości projektów jest `Debug`, ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-131">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`--force`**

  <span data-ttu-id="cbeb8-132">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="cbeb8-133">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="cbeb8-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="cbeb8-134">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-134">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="cbeb8-135">Obejmuje pakiety NuGet symboli debugowania oprócz zwykłych pakietów NuGet w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-135">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="cbeb8-136">Pliki źródeł znajdują się w folderze `src` w pakiecie symboli.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-136">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="cbeb8-137">Obejmuje pakiety NuGet symboli debugowania oprócz zwykłych pakietów NuGet w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-137">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="cbeb8-138">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="cbeb8-138">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="cbeb8-139">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-139">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="cbeb8-140">Nie kompiluje projektu przed opakowaniem.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-140">Doesn't build the project before packing.</span></span> <span data-ttu-id="cbeb8-141">Niejawnie ustawia również flagę `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-141">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="cbeb8-142">Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-142">Ignores project-to-project references and only restores the root project.</span></span>

- **`--no-restore`**

  <span data-ttu-id="cbeb8-143">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-143">Doesn't execute an implicit restore when running the command.</span></span>

- **`--nologo`**

  <span data-ttu-id="cbeb8-144">Nie wyświetla transparentu początkowego ani komunikatu o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-144">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="cbeb8-145">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-145">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="cbeb8-146">Umieszcza skompilowane pakiety w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-146">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="cbeb8-147">Określa docelowy środowisko uruchomieniowe, dla którego mają zostać przywrócone pakiety.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-147">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="cbeb8-148">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="cbeb8-148">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="cbeb8-149">Ustawia flagę obsługi w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-149">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="cbeb8-150">Aby uzyskać więcej informacji, zobacz [blog platformy .NET: .NET 4.5.1 obsługuje aktualizacje zabezpieczeń firmy Microsoft dla bibliotek NuGet programu .NET](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="cbeb8-150">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="cbeb8-151">Definiuje wartość właściwości `$(VersionSuffix)` MSBuild w projekcie.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-151">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="cbeb8-152">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-152">Sets the verbosity level of the command.</span></span> <span data-ttu-id="cbeb8-153">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="cbeb8-153">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="cbeb8-154">Przykłady</span><span class="sxs-lookup"><span data-stu-id="cbeb8-154">Examples</span></span>

- <span data-ttu-id="cbeb8-155">Pakowanie projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="cbeb8-155">Pack the project in the current directory:</span></span>

  ```dotnetcli
  dotnet pack
  ```

- <span data-ttu-id="cbeb8-156">Pakowanie projektu `app1`:</span><span class="sxs-lookup"><span data-stu-id="cbeb8-156">Pack the `app1` project:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="cbeb8-157">Pakowanie projektu w bieżącym katalogu i umieszczenie pakietów powstających w folderze `nupkgs`:</span><span class="sxs-lookup"><span data-stu-id="cbeb8-157">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="cbeb8-158">Pakowanie projektu w bieżącym katalogu do folderu `nupkgs` i pomijanie kroku kompilacji:</span><span class="sxs-lookup"><span data-stu-id="cbeb8-158">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="cbeb8-159">Przy użyciu sufiksu wersji projektu skonfigurowanego jako `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` w pliku *csproj* należy spakować bieżący projekt i zaktualizować uzyskaną wersję pakietu przy użyciu danego sufiksu:</span><span class="sxs-lookup"><span data-stu-id="cbeb8-159">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="cbeb8-160">Ustaw wersję pakietu na `2.1.0` przy użyciu `PackageVersion` właściwości programu MSBuild:</span><span class="sxs-lookup"><span data-stu-id="cbeb8-160">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="cbeb8-161">Pakowanie projektu dla konkretnej [platformy docelowej](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="cbeb8-161">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="cbeb8-162">Pakowanie projektu i użycie określonego środowiska uruchomieniowego (Windows 10) dla operacji przywracania:</span><span class="sxs-lookup"><span data-stu-id="cbeb8-162">Pack the project and use a specific runtime (Windows 10) for the restore operation:</span></span>

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="cbeb8-163">Pakowanie projektu przy użyciu [pliku. nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span><span class="sxs-lookup"><span data-stu-id="cbeb8-163">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
