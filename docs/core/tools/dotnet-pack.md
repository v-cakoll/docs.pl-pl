---
title: dotnet pack, polecenie
description: Polecenie dotnet pack tworzy pakiety NuGet dla projektu .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 3b9c46ecd5d67519728896b0018e27fb41ebd861
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463510"
---
# <a name="dotnet-pack"></a><span data-ttu-id="d60b2-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d60b2-103">dotnet pack</span></span>

<span data-ttu-id="d60b2-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="d60b2-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d60b2-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d60b2-105">Name</span></span>

<span data-ttu-id="d60b2-106">`dotnet pack`- Pakuje kod do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="d60b2-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d60b2-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="d60b2-107">Synopsis</span></span>

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output <OUTPUT_DIRECTORY>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--serviceable] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet pack -h|--help
```

## <a name="description"></a><span data-ttu-id="d60b2-108">Opis</span><span class="sxs-lookup"><span data-stu-id="d60b2-108">Description</span></span>

<span data-ttu-id="d60b2-109">Polecenie `dotnet pack` tworzy projekt i tworzy pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="d60b2-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="d60b2-110">Wynikiem tego polecenia jest pakiet NuGet (czyli plik *nupkg).*</span><span class="sxs-lookup"><span data-stu-id="d60b2-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span>

<span data-ttu-id="d60b2-111">Jeśli chcesz wygenerować pakiet, który zawiera symbole debugowania, masz dwie opcje dostępne:</span><span class="sxs-lookup"><span data-stu-id="d60b2-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="d60b2-112">`--include-symbols`- tworzy pakiet symboli.</span><span class="sxs-lookup"><span data-stu-id="d60b2-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="d60b2-113">`--include-source`- tworzy pakiet symboli `src` z folderem wewnątrz zawierającym pliki źródłowe.</span><span class="sxs-lookup"><span data-stu-id="d60b2-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="d60b2-114">Zależności NuGet spakowanego projektu są dodawane do pliku *nuspec,* więc są poprawnie rozpoznawane po zainstalowaniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="d60b2-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="d60b2-115">Odwołania do projektu nie są pakowane wewnątrz projektu.</span><span class="sxs-lookup"><span data-stu-id="d60b2-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="d60b2-116">Obecnie musisz mieć pakiet na projekt, jeśli masz zależności między projektem.</span><span class="sxs-lookup"><span data-stu-id="d60b2-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="d60b2-117">Domyślnie `dotnet pack` najpierw tworzy projekt.</span><span class="sxs-lookup"><span data-stu-id="d60b2-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="d60b2-118">Jeśli chcesz uniknąć tego zachowania, `--no-build` przekaż tę opcję.</span><span class="sxs-lookup"><span data-stu-id="d60b2-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="d60b2-119">Ta opcja jest często przydatne w scenariuszach kompilacji ciągłej integracji (CI), w których wiesz, że kod został wcześniej skompilowany.</span><span class="sxs-lookup"><span data-stu-id="d60b2-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

> [!NOTE]
> <span data-ttu-id="d60b2-120">W niektórych przypadkach nie można wykonać kompilacji niejawnej.</span><span class="sxs-lookup"><span data-stu-id="d60b2-120">In some cases, the implicit build cannot be performed.</span></span> <span data-ttu-id="d60b2-121">Może to `GeneratePackageOnBuild` nastąpić, gdy jest ustawiona, aby uniknąć cyklicznej zależności między kompilacji i pack obiektów docelowych.</span><span class="sxs-lookup"><span data-stu-id="d60b2-121">This can occur when `GeneratePackageOnBuild` is set, to avoid a cyclic dependency between build and pack targets.</span></span> <span data-ttu-id="d60b2-122">Kompilacja może również zakończyć się niepowodzeniem, jeśli istnieje zablokowany plik lub inny problem.</span><span class="sxs-lookup"><span data-stu-id="d60b2-122">The build can also fail if there is a locked file or other issue.</span></span>

<span data-ttu-id="d60b2-123">Właściwości MSBuild można podać `dotnet pack` do polecenia dla procesu pakowania.</span><span class="sxs-lookup"><span data-stu-id="d60b2-123">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="d60b2-124">Aby uzyskać więcej informacji, zobacz [Właściwości metadanych NuGet](csproj.md#nuget-metadata-properties) i [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="d60b2-124">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="d60b2-125">[Przykłady](#examples) sekcja pokazuje, jak używać przełącznika MSBuild -p dla kilku różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="d60b2-125">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="d60b2-126">Projekty sieci Web nie są domyślnie spakowane.</span><span class="sxs-lookup"><span data-stu-id="d60b2-126">Web projects aren't packable by default.</span></span> <span data-ttu-id="d60b2-127">Aby zastąpić zachowanie domyślne, dodaj następującą właściwość do pliku *csproj:*</span><span class="sxs-lookup"><span data-stu-id="d60b2-127">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="d60b2-128">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d60b2-128">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="d60b2-129">Projekt lub rozwiązanie do spakowania.</span><span class="sxs-lookup"><span data-stu-id="d60b2-129">The project or solution to pack.</span></span> <span data-ttu-id="d60b2-130">Jest to ścieżka do [pliku csproj](csproj.md), pliku rozwiązania lub do katalogu.</span><span class="sxs-lookup"><span data-stu-id="d60b2-130">It's either a path to a [csproj file](csproj.md), a solution file, or to a directory.</span></span> <span data-ttu-id="d60b2-131">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog dla pliku projektu lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="d60b2-131">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="d60b2-132">Opcje</span><span class="sxs-lookup"><span data-stu-id="d60b2-132">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="d60b2-133">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d60b2-133">Defines the build configuration.</span></span> <span data-ttu-id="d60b2-134">Wartość domyślna dla `Debug`większości projektów to , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="d60b2-134">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`--force`**

  <span data-ttu-id="d60b2-135">Wymusza wszystkie zależności do rozwiązania, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="d60b2-135">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="d60b2-136">Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="d60b2-136">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d60b2-137">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="d60b2-137">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="d60b2-138">Zawiera symbole debugowania Pakiety NuGet oprócz zwykłych pakietów NuGet w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="d60b2-138">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="d60b2-139">Pliki źródeł są zawarte w `src` folderze w pakiecie symboli.</span><span class="sxs-lookup"><span data-stu-id="d60b2-139">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="d60b2-140">Zawiera symbole debugowania Pakiety NuGet oprócz zwykłych pakietów NuGet w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="d60b2-140">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="d60b2-141">Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="d60b2-141">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="d60b2-142">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d60b2-142">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="d60b2-143">Nie buduje projektu przed pakowanie.</span><span class="sxs-lookup"><span data-stu-id="d60b2-143">Doesn't build the project before packing.</span></span> <span data-ttu-id="d60b2-144">Również niejawnie `--no-restore` ustawia flagę.</span><span class="sxs-lookup"><span data-stu-id="d60b2-144">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="d60b2-145">Ignoruje odwołania do projektu i przywraca tylko projekt główny.</span><span class="sxs-lookup"><span data-stu-id="d60b2-145">Ignores project-to-project references and only restores the root project.</span></span>

- **`--no-restore`**

  <span data-ttu-id="d60b2-146">Nie wykonuje niejawnego przywracania podczas uruchamiania polecenia.</span><span class="sxs-lookup"><span data-stu-id="d60b2-146">Doesn't execute an implicit restore when running the command.</span></span>

- **`--nologo`**

  <span data-ttu-id="d60b2-147">Nie wyświetla banera startowego ani wiadomości o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="d60b2-147">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="d60b2-148">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="d60b2-148">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="d60b2-149">Umieszcza wbudowane pakiety w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d60b2-149">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="d60b2-150">Określa docelowy czas wykonywania do przywrócenia pakietów dla.</span><span class="sxs-lookup"><span data-stu-id="d60b2-150">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="d60b2-151">Aby uzyskać listę identyfikatorów środowiska wykonawczego (RID), zobacz [katalog RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d60b2-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="d60b2-152">Ustawia flagę z obsługą w pakiecie.</span><span class="sxs-lookup"><span data-stu-id="d60b2-152">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="d60b2-153">Aby uzyskać więcej informacji, zobacz [blog platformy .NET: .NET 4.5.1 obsługuje aktualizacje zabezpieczeń firmy Microsoft dla bibliotek nugetów .NET](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="d60b2-153">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="d60b2-154">Definiuje wartość właściwości `$(VersionSuffix)` MSBuild w projekcie.</span><span class="sxs-lookup"><span data-stu-id="d60b2-154">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="d60b2-155">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="d60b2-155">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d60b2-156">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="d60b2-156">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="d60b2-157">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d60b2-157">Examples</span></span>

- <span data-ttu-id="d60b2-158">Zapakuj projekt do bieżącego katalogu:</span><span class="sxs-lookup"><span data-stu-id="d60b2-158">Pack the project in the current directory:</span></span>

  ```dotnetcli
  dotnet pack
  ```

- <span data-ttu-id="d60b2-159">Zapakuj `app1` projekt:</span><span class="sxs-lookup"><span data-stu-id="d60b2-159">Pack the `app1` project:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="d60b2-160">Zapakuj projekt do bieżącego katalogu i `nupkgs` umieść powstałe pakiety w folderze:</span><span class="sxs-lookup"><span data-stu-id="d60b2-160">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="d60b2-161">Zapakuj projekt w bieżącym `nupkgs` katalogu do folderu i pomiń krok kompilacji:</span><span class="sxs-lookup"><span data-stu-id="d60b2-161">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="d60b2-162">Za pomocą sufiksu wersji `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` projektu skonfigurowanym tak jak w pliku *csproj,* zapakuj bieżący projekt i zaktualizuj wynikową wersję pakietu z danym sufiksem:</span><span class="sxs-lookup"><span data-stu-id="d60b2-162">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="d60b2-163">Ustaw wersję pakietu `2.1.0` z `PackageVersion` właściwością MSBuild:</span><span class="sxs-lookup"><span data-stu-id="d60b2-163">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="d60b2-164">Zapakuj projekt do określonej [ramy docelowej:](../../standard/frameworks.md)</span><span class="sxs-lookup"><span data-stu-id="d60b2-164">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="d60b2-165">Zapakuj projekt i użyj określonego środowiska uruchomieniowego (Windows 10) do operacji przywracania:</span><span class="sxs-lookup"><span data-stu-id="d60b2-165">Pack the project and use a specific runtime (Windows 10) for the restore operation:</span></span>

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="d60b2-166">Zapakuj projekt za pomocą [pliku nuspec:](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)</span><span class="sxs-lookup"><span data-stu-id="d60b2-166">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
