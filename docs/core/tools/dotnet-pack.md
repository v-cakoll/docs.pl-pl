---
title: polecenie dotnet pack
description: Polecenie dotnet pack tworzy pakiety NuGet dla projektu .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 865262f1eb314f9b7e8ee713c573a965e89ded93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503644"
---
# <a name="dotnet-pack"></a><span data-ttu-id="37d42-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="37d42-103">dotnet pack</span></span>

<span data-ttu-id="37d42-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="37d42-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="37d42-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="37d42-105">Name</span></span>

<span data-ttu-id="37d42-106">`dotnet pack`- Pakuje kod do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="37d42-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="37d42-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="37d42-107">Synopsis</span></span>

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo] [-o|--output] [--runtime] [-s|--serviceable]
    [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

## <a name="description"></a><span data-ttu-id="37d42-108">Opis</span><span class="sxs-lookup"><span data-stu-id="37d42-108">Description</span></span>

<span data-ttu-id="37d42-109">Polecenie `dotnet pack` tworzy projekt i tworzy pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="37d42-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="37d42-110">Wynikiem tego polecenia jest pakiet NuGet (czyli plik *.nupkg).*</span><span class="sxs-lookup"><span data-stu-id="37d42-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span>

<span data-ttu-id="37d42-111">Jeśli chcesz wygenerować pakiet zawierający symbole debugowania, dostępne są dwie opcje:</span><span class="sxs-lookup"><span data-stu-id="37d42-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="37d42-112">`--include-symbols`- tworzy pakiet symboli.</span><span class="sxs-lookup"><span data-stu-id="37d42-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="37d42-113">`--include-source`- tworzy pakiet symboli `src` z folderem wewnątrz zawierającym pliki źródłowe.</span><span class="sxs-lookup"><span data-stu-id="37d42-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="37d42-114">NuGet zależności spakowanego projektu są dodawane do pliku *nuspec,* więc są one poprawnie rozwiązane po zainstalowaniu pakietu.</span><span class="sxs-lookup"><span data-stu-id="37d42-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="37d42-115">Odwołania do projektu nie są pakowane wewnątrz projektu.</span><span class="sxs-lookup"><span data-stu-id="37d42-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="37d42-116">Obecnie musisz mieć pakiet na projekt, jeśli masz zależności projektu do projektu.</span><span class="sxs-lookup"><span data-stu-id="37d42-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="37d42-117">Domyślnie `dotnet pack` najpierw tworzy projekt.</span><span class="sxs-lookup"><span data-stu-id="37d42-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="37d42-118">Jeśli chcesz uniknąć tego zachowania, `--no-build` przekaż tę opcję.</span><span class="sxs-lookup"><span data-stu-id="37d42-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="37d42-119">Ta opcja jest często przydatne w scenariuszach kompilacji ciągłej integracji (CI), gdzie wiadomo, że kod został wcześniej zbudowany.</span><span class="sxs-lookup"><span data-stu-id="37d42-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="37d42-120">Można podać msbuild właściwości `dotnet pack` do polecenia dla procesu pakowania.</span><span class="sxs-lookup"><span data-stu-id="37d42-120">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="37d42-121">Aby uzyskać więcej informacji, zobacz [NuGet właściwości metadanych](csproj.md#nuget-metadata-properties) i [MSBuild command-line odwołania](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="37d42-121">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="37d42-122">Przykłady [Examples](#examples) sekcji pokazuje, jak używać przełącznika MSBuild -p dla kilku różnych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="37d42-122">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="37d42-123">Projekty sieci Web nie są domyślnie pakowane.</span><span class="sxs-lookup"><span data-stu-id="37d42-123">Web projects aren't packable by default.</span></span> <span data-ttu-id="37d42-124">Aby zastąpić zachowanie domyślne, dodaj następującą właściwość do pliku *csproj:*</span><span class="sxs-lookup"><span data-stu-id="37d42-124">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="37d42-125">Argumenty</span><span class="sxs-lookup"><span data-stu-id="37d42-125">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="37d42-126">Projekt lub rozwiązanie do spakowania.</span><span class="sxs-lookup"><span data-stu-id="37d42-126">The project or solution to pack.</span></span> <span data-ttu-id="37d42-127">Jest to albo ścieżka do [pliku csproj](csproj.md), pliku rozwiązania, albo do katalogu.</span><span class="sxs-lookup"><span data-stu-id="37d42-127">It's either a path to a [csproj file](csproj.md), a solution file, or to a directory.</span></span> <span data-ttu-id="37d42-128">Jeśli nie zostanie określony, polecenie przeszukuje bieżący katalog w poszukiwaniu pliku projektu lub rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="37d42-128">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="37d42-129">Opcje</span><span class="sxs-lookup"><span data-stu-id="37d42-129">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="37d42-130">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="37d42-130">Defines the build configuration.</span></span> <span data-ttu-id="37d42-131">Wartość domyślna dla `Debug`większości projektów jest , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="37d42-131">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`--force`**

  <span data-ttu-id="37d42-132">Wymusza rozwiązywanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="37d42-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="37d42-133">Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="37d42-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="37d42-134">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="37d42-134">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="37d42-135">Zawiera symbole debugowania Pakiety NuGet oprócz zwykłych pakietów NuGet w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="37d42-135">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="37d42-136">Pliki źródeł znajdują się `src` w folderze w pakiecie symboli.</span><span class="sxs-lookup"><span data-stu-id="37d42-136">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="37d42-137">Zawiera symbole debugowania Pakiety NuGet oprócz zwykłych pakietów NuGet w katalogu wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="37d42-137">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="37d42-138">Umożliwia polecenie, aby zatrzymać i czekać na dane wejściowe użytkownika lub akcji (na przykład, aby zakończyć uwierzytelnianie).</span><span class="sxs-lookup"><span data-stu-id="37d42-138">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="37d42-139">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="37d42-139">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="37d42-140">Nie tworzy projektu przed pakowaniem.</span><span class="sxs-lookup"><span data-stu-id="37d42-140">Doesn't build the project before packing.</span></span> <span data-ttu-id="37d42-141">To również niejawnie ustawia `--no-restore` flagę.</span><span class="sxs-lookup"><span data-stu-id="37d42-141">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="37d42-142">Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.</span><span class="sxs-lookup"><span data-stu-id="37d42-142">Ignores project-to-project references and only restores the root project.</span></span>

- **`--no-restore`**

  <span data-ttu-id="37d42-143">Nie wykonuje przywracania niejawnego podczas uruchamiania polecenia.</span><span class="sxs-lookup"><span data-stu-id="37d42-143">Doesn't execute an implicit restore when running the command.</span></span>

- **`--nologo`**

  <span data-ttu-id="37d42-144">Nie wyświetla banera startowego ani wiadomości o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="37d42-144">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="37d42-145">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="37d42-145">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="37d42-146">Umieszcza wbudowane pakiety w określonym katalogu.</span><span class="sxs-lookup"><span data-stu-id="37d42-146">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="37d42-147">Określa docelowy czas wykonywania, dla której ma zostać przywrócony pakiety.</span><span class="sxs-lookup"><span data-stu-id="37d42-147">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="37d42-148">Aby uzyskać listę identyfikatorów runtime (RID), zobacz [katalog RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="37d42-148">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="37d42-149">Ustawia w pakiecie flagę z możliwością serwisowania.</span><span class="sxs-lookup"><span data-stu-id="37d42-149">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="37d42-150">Aby uzyskać więcej informacji, zobacz [.NET Blog: .NET 4.5.1 Obsługuje aktualizacje zabezpieczeń firmy Microsoft dla bibliotek .NET NuGet](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="37d42-150">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="37d42-151">Definiuje wartość właściwości `$(VersionSuffix)` MSBuild w projekcie.</span><span class="sxs-lookup"><span data-stu-id="37d42-151">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="37d42-152">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="37d42-152">Sets the verbosity level of the command.</span></span> <span data-ttu-id="37d42-153">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="37d42-153">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="37d42-154">Przykłady</span><span class="sxs-lookup"><span data-stu-id="37d42-154">Examples</span></span>

- <span data-ttu-id="37d42-155">Zapakuj projekt w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="37d42-155">Pack the project in the current directory:</span></span>

  ```dotnetcli
  dotnet pack
  ```

- <span data-ttu-id="37d42-156">Zapakuj `app1` projekt:</span><span class="sxs-lookup"><span data-stu-id="37d42-156">Pack the `app1` project:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="37d42-157">Zapakuj projekt w bieżącym katalogu i `nupkgs` umieść powstałe pakiety w folderze:</span><span class="sxs-lookup"><span data-stu-id="37d42-157">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="37d42-158">Spakować projekt w bieżącym `nupkgs` katalogu do folderu i pominąć krok kompilacji:</span><span class="sxs-lookup"><span data-stu-id="37d42-158">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="37d42-159">Z sufiksem wersji projektu `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` skonfigurowanym jak w pliku *csproj,* zapakuj bieżący projekt i zaktualizuj wynikową wersję pakietu z danym sufiksem:</span><span class="sxs-lookup"><span data-stu-id="37d42-159">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="37d42-160">Ustaw wersję pakietu `2.1.0` za `PackageVersion` pomocą właściwości MSBuild:</span><span class="sxs-lookup"><span data-stu-id="37d42-160">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="37d42-161">Spakować projekt dla określonych [ram docelowych:](../../standard/frameworks.md)</span><span class="sxs-lookup"><span data-stu-id="37d42-161">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="37d42-162">Spakować projekt i użyć określonego środowiska uruchomieniowego (Windows 10) dla operacji przywracania:</span><span class="sxs-lookup"><span data-stu-id="37d42-162">Pack the project and use a specific runtime (Windows 10) for the restore operation:</span></span>

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="37d42-163">Spakować projekt przy użyciu [pliku nuspec:](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec)</span><span class="sxs-lookup"><span data-stu-id="37d42-163">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
