---
title: polecenie dotnet Pack
description: Polecenie programu dotnet Pack tworzy pakiety NuGet dla projektu .NET Core.
ms.date: 08/08/2019
ms.openlocfilehash: 99dd8e35601f82adf2a3101121028f191a4c3da4
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117655"
---
# <a name="dotnet-pack"></a><span data-ttu-id="043c9-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="043c9-103">dotnet pack</span></span>

<span data-ttu-id="043c9-104">**Ten temat dotyczy: ✓** .NET Core 1. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="043c9-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="043c9-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="043c9-105">Name</span></span>

<span data-ttu-id="043c9-106">`dotnet pack`-Pakuje kod do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="043c9-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="043c9-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="043c9-107">Synopsis</span></span>

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive] 
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable] 
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a><span data-ttu-id="043c9-108">Opis</span><span class="sxs-lookup"><span data-stu-id="043c9-108">Description</span></span>

<span data-ttu-id="043c9-109">`dotnet pack` Polecenie kompiluje projekt i tworzy pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="043c9-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="043c9-110">Wynikiem tego polecenia jest pakiet NuGet (czyli plik *. nupkg* ).</span><span class="sxs-lookup"><span data-stu-id="043c9-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span> 

<span data-ttu-id="043c9-111">Jeśli chcesz wygenerować pakiet zawierający symbole debugowania, dostępne są dwie opcje:</span><span class="sxs-lookup"><span data-stu-id="043c9-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="043c9-112">`--include-symbols`— tworzy pakiet symboli.</span><span class="sxs-lookup"><span data-stu-id="043c9-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="043c9-113">`--include-source`— tworzy pakiet symboli z `src` folderem zawierającym pliki źródłowe.</span><span class="sxs-lookup"><span data-stu-id="043c9-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="043c9-114">Zależności NuGet spakowanego projektu są dodawane do pliku *. nuspec* , więc są one poprawnie rozwiązane po zainstalowaniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="043c9-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="043c9-115">Odwołania projektu do projektu nie są spakowane w projekcie.</span><span class="sxs-lookup"><span data-stu-id="043c9-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="043c9-116">Obecnie należy mieć pakiet dla każdego projektu, jeśli istnieją zależności między projektami.</span><span class="sxs-lookup"><span data-stu-id="043c9-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="043c9-117">Domyślnie program `dotnet pack` kompiluje projekt.</span><span class="sxs-lookup"><span data-stu-id="043c9-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="043c9-118">Jeśli chcesz uniknąć tego zachowania, Przekaż `--no-build` opcję.</span><span class="sxs-lookup"><span data-stu-id="043c9-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="043c9-119">Ta opcja jest często przydatna w scenariuszach kompilacji ciągłej integracji (CI), w których wiadomo, że kod został wcześniej skompilowany.</span><span class="sxs-lookup"><span data-stu-id="043c9-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="043c9-120">Można podać właściwości programu MSBuild do `dotnet pack` polecenia dla procesu pakowania.</span><span class="sxs-lookup"><span data-stu-id="043c9-120">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="043c9-121">Aby uzyskać więcej informacji, zobacz [właściwości metadanych NuGet](csproj.md#nuget-metadata-properties) i [Dokumentacja wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="043c9-121">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="043c9-122">W sekcji [przykłady](#examples) pokazano, jak używać przełącznika MSBuild-p w przypadku kilku różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="043c9-122">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="043c9-123">Projekty sieci Web nie są domyślnie objęte pakietem.</span><span class="sxs-lookup"><span data-stu-id="043c9-123">Web projects aren't packable by default.</span></span> <span data-ttu-id="043c9-124">Aby zastąpić zachowanie domyślne, Dodaj następującą właściwość do pliku *. csproj* :</span><span class="sxs-lookup"><span data-stu-id="043c9-124">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="043c9-125">Argumenty</span><span class="sxs-lookup"><span data-stu-id="043c9-125">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="043c9-126">Projekt lub rozwiązanie do spakowania.</span><span class="sxs-lookup"><span data-stu-id="043c9-126">The project or solution to pack.</span></span> <span data-ttu-id="043c9-127">Jest to ścieżka do [pliku csproj](csproj.md), pliku rozwiązania lub do katalogu.</span><span class="sxs-lookup"><span data-stu-id="043c9-127">It's either a path to a [csproj file](csproj.md), a solution file, or to a directory.</span></span> <span data-ttu-id="043c9-128">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla pliku projektu lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="043c9-128">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="043c9-129">Opcje</span><span class="sxs-lookup"><span data-stu-id="043c9-129">Options</span></span>

- **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="043c9-130">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="043c9-130">Defines the build configuration.</span></span> <span data-ttu-id="043c9-131">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="043c9-131">The default value is `Debug`.</span></span>

- **`--force`**

  <span data-ttu-id="043c9-132">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="043c9-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="043c9-133">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="043c9-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="043c9-134">Opcja dostępna od wersji .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="043c9-134">Option available since .NET Core 2.0 SDK.</span></span>

- **`-h|--help`**

  <span data-ttu-id="043c9-135">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="043c9-135">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="043c9-136">Obejmuje pakiety NuGet symboli debugowania oprócz zwykłych pakietów NuGet w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="043c9-136">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="043c9-137">Pliki źródeł są dołączone `src` do folderu w pakiecie symboli.</span><span class="sxs-lookup"><span data-stu-id="043c9-137">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="043c9-138">Obejmuje pakiety NuGet symboli debugowania oprócz zwykłych pakietów NuGet w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="043c9-138">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="043c9-139">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="043c9-139">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="043c9-140">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="043c9-140">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="043c9-141">Nie kompiluje projektu przed opakowaniem.</span><span class="sxs-lookup"><span data-stu-id="043c9-141">Doesn't build the project before packing.</span></span> <span data-ttu-id="043c9-142">Również niejawnie ustawia `--no-restore` flagę.</span><span class="sxs-lookup"><span data-stu-id="043c9-142">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="043c9-143">Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.</span><span class="sxs-lookup"><span data-stu-id="043c9-143">Ignores project-to-project references and only restores the root project.</span></span> <span data-ttu-id="043c9-144">Opcja dostępna od wersji .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="043c9-144">Option available since .NET Core 2.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="043c9-145">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="043c9-145">Doesn't execute an implicit restore when running the command.</span></span> <span data-ttu-id="043c9-146">Opcja dostępna od wersji .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="043c9-146">Option available since .NET Core 2.0 SDK.</span></span>

- **`--nologo`**

  <span data-ttu-id="043c9-147">Nie wyświetla transparentu początkowego ani komunikatu o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="043c9-147">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="043c9-148">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="043c9-148">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="043c9-149">Umieszcza skompilowane pakiety w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="043c9-149">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="043c9-150">Określa docelowy środowisko uruchomieniowe, dla którego mają zostać przywrócone pakiety.</span><span class="sxs-lookup"><span data-stu-id="043c9-150">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="043c9-151">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="043c9-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="043c9-152">Opcja dostępna od wersji .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="043c9-152">Option available since .NET Core 2.0 SDK.</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="043c9-153">Ustawia flagę obsługi w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="043c9-153">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="043c9-154">Aby uzyskać więcej informacji, zobacz [blog platformy .NET: .NET 4.5.1 obsługuje aktualizacje zabezpieczeń firmy Microsoft dla bibliotek NuGet programu .NET](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="043c9-154">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="043c9-155">Definiuje wartość `$(VersionSuffix)` właściwości programu MSBuild w projekcie.</span><span class="sxs-lookup"><span data-stu-id="043c9-155">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="043c9-156">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="043c9-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="043c9-157">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="043c9-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="043c9-158">Przykłady</span><span class="sxs-lookup"><span data-stu-id="043c9-158">Examples</span></span>

- <span data-ttu-id="043c9-159">Pakowanie projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="043c9-159">Pack the project in the current directory:</span></span>

  ```dotnetcli
  dotnet pack
  ```

- <span data-ttu-id="043c9-160">`app1` Pakowanie projektu:</span><span class="sxs-lookup"><span data-stu-id="043c9-160">Pack the `app1` project:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="043c9-161">Pakowanie projektu w bieżącym katalogu i umieszczenie w nim pakietów `nupkgs` powstających:</span><span class="sxs-lookup"><span data-stu-id="043c9-161">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="043c9-162">Pakowanie projektu w bieżącym katalogu do `nupkgs` folderu i pomijanie kroku kompilacji:</span><span class="sxs-lookup"><span data-stu-id="043c9-162">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="043c9-163">Przy użyciu sufiksu wersji projektu skonfigurowanego `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` jako w pliku *. csproj* należy spakować bieżący projekt i zaktualizować uzyskaną wersję pakietu przy użyciu danego sufiksu:</span><span class="sxs-lookup"><span data-stu-id="043c9-163">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="043c9-164">Ustaw wersję pakietu na `2.1.0` `PackageVersion` za pomocą właściwości MSBuild:</span><span class="sxs-lookup"><span data-stu-id="043c9-164">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="043c9-165">Pakowanie projektu dla konkretnej [platformy docelowej](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="043c9-165">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="043c9-166">Pakowanie projektu i użycie określonego środowiska uruchomieniowego (Windows 10) dla operacji przywracania (zestaw .NET Core SDK 2,0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="043c9-166">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="043c9-167">Pakowanie projektu przy użyciu [pliku. nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span><span class="sxs-lookup"><span data-stu-id="043c9-167">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
