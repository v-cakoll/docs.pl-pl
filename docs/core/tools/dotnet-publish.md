---
title: polecenie publikowania dotnetu
description: Polecenie publikowania dotnet publikuje projekt .NET Core lub rozwiązanie do katalogu.
ms.date: 02/24/2020
ms.openlocfilehash: 0e18220443f3713c86c257fcf401b98ddd716ebc
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588265"
---
# <a name="dotnet-publish"></a><span data-ttu-id="dc2a6-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="dc2a6-103">dotnet publish</span></span>

<span data-ttu-id="dc2a6-104">**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="dc2a6-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="dc2a6-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="dc2a6-105">Name</span></span>

<span data-ttu-id="dc2a6-106">`dotnet publish`- Publikuje aplikację i jej zależności do folderu do wdrożenia w systemie hostingowym.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dc2a6-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="dc2a6-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a><span data-ttu-id="dc2a6-108">Opis</span><span class="sxs-lookup"><span data-stu-id="dc2a6-108">Description</span></span>

<span data-ttu-id="dc2a6-109">`dotnet publish`kompiluje aplikację, odczytuje za pośrednictwem jej zależności określonych w pliku projektu i publikuje wynikowy zestaw plików do katalogu.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="dc2a6-110">Dane wyjściowe obejmują następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="dc2a6-110">The output includes the following assets:</span></span>

- <span data-ttu-id="dc2a6-111">Kod języka pośredniego (IL) w zestawie z rozszerzeniem *dll.*</span><span class="sxs-lookup"><span data-stu-id="dc2a6-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="dc2a6-112">Plik *deps.json,* który zawiera wszystkie zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="dc2a6-113">Plik *.runtimeconfig.json,* który określa udostępnione środowisko uruchomieniowe, które oczekuje aplikacja, a także inne opcje konfiguracji dla środowiska wykonawczego (na przykład typ wyrzucania elementów bezużytecznych).</span><span class="sxs-lookup"><span data-stu-id="dc2a6-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="dc2a6-114">Zależności aplikacji, które są kopiowane z pamięci podręcznej NuGet do folderu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="dc2a6-115">Dane `dotnet publish` wyjściowe polecenia są gotowe do wdrożenia w systemie hostingowym (na przykład serwerze, komputerze PC, Mac, laptopie) do wykonania.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="dc2a6-116">Jest to jedyny oficjalnie obsługiwany sposób przygotowania aplikacji do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="dc2a6-117">W zależności od typu wdrożenia, który określa projekt, system hostingu może lub nie może mieć .NET Core udostępnionego środowiska uruchomieniowego zainstalowanego na nim.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="dc2a6-118">Aby uzyskać więcej informacji, zobacz [Publikowanie aplikacji .NET Core za pomocą interfejsu wiersza polecenia .NET Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="dc2a6-118">For more information, see [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="msbuild"></a><span data-ttu-id="dc2a6-119">MSBuild</span><span class="sxs-lookup"><span data-stu-id="dc2a6-119">MSBuild</span></span>

<span data-ttu-id="dc2a6-120">Polecenie `dotnet publish` wywołuje MSBuild, który `Publish` wywołuje obiekt docelowy.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-120">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="dc2a6-121">Wszystkie parametry `dotnet publish` przekazywane do są przekazywane do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-121">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="dc2a6-122">I `-c` `-o` parametry mapują odpowiednio właściwości `Configuration` i `OutputPath` MSBuild.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-122">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `OutputPath` properties, respectively.</span></span>

<span data-ttu-id="dc2a6-123">Polecenie `dotnet publish` akceptuje opcje MSBuild, `-p` takie jak ustawienie `-l` właściwości i zdefiniowanie rejestratora.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-123">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="dc2a6-124">Na przykład można ustawić właściwość MSBuild przy `-p:<NAME>=<VALUE>`użyciu formatu: .</span><span class="sxs-lookup"><span data-stu-id="dc2a6-124">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span> <span data-ttu-id="dc2a6-125">Można również ustawić właściwości związane z publikowanie, odwołując się do pliku *pubxml,* na przykład:</span><span class="sxs-lookup"><span data-stu-id="dc2a6-125">You can also set publish-related properties by referring to a *.pubxml* file, for example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

<span data-ttu-id="dc2a6-126">Więcej informacji zawierają następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="dc2a6-126">For more information, see the following resources:</span></span>

- [<span data-ttu-id="dc2a6-127">Odwołanie do wiersza polecenia MSBuild</span><span class="sxs-lookup"><span data-stu-id="dc2a6-127">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="dc2a6-128">Profile publikowania w programie Visual Studio (pubxml) dla ASP.NET wdrożenia aplikacji Core</span><span class="sxs-lookup"><span data-stu-id="dc2a6-128">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="dc2a6-129">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="dc2a6-129">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="dc2a6-130">Argumenty</span><span class="sxs-lookup"><span data-stu-id="dc2a6-130">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="dc2a6-131">Projekt lub rozwiązanie do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-131">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="dc2a6-132">`PROJECT`jest ścieżką i nazwami plików pliku projektu [C#](csproj.md), F#lub Visual Basic lub ścieżką do katalogu zawierającego plik projektu C#, F#lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-132">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="dc2a6-133">Jeśli katalog nie jest określony, domyślnie jest to bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-133">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="dc2a6-134">`SOLUTION`jest ścieżką i nazwami pliku rozwiązania ( rozszerzenie *.sln)* lub ścieżką do katalogu zawierającego plik rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-134">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="dc2a6-135">Jeśli katalog nie jest określony, domyślnie jest to bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-135">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="dc2a6-136">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-136">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="dc2a6-137">Opcje</span><span class="sxs-lookup"><span data-stu-id="dc2a6-137">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="dc2a6-138">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-138">Defines the build configuration.</span></span> <span data-ttu-id="dc2a6-139">Wartość domyślna dla `Debug`większości projektów to , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-139">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="dc2a6-140">Publikuje aplikację dla określonej [struktury docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="dc2a6-140">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="dc2a6-141">Należy określić platformę docelową w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-141">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="dc2a6-142">Wymusza wszystkie zależności do rozwiązania, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-142">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="dc2a6-143">Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="dc2a6-143">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="dc2a6-144">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-144">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="dc2a6-145">Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-145">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="dc2a6-146">Na przykład, aby zakończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-146">For example, to complete authentication.</span></span> <span data-ttu-id="dc2a6-147">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-147">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="dc2a6-148">Określa jeden lub kilka [manifestów docelowych,](../deploying/runtime-store.md) które mają być używane do przycinania zestawu pakietów opublikowanych za pomocą aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-148">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="dc2a6-149">Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="dc2a6-149">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="dc2a6-150">Aby określić wiele manifestów, dodaj `--manifest` opcję dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-150">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="dc2a6-151">Nie tworzy projektu przed opublikowaniem.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-151">Doesn't build the project before publishing.</span></span> <span data-ttu-id="dc2a6-152">Również niejawnie `--no-restore` ustawia flagę.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-152">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="dc2a6-153">Ignoruje odwołania do projektu i przywraca tylko projekt główny.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-153">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="dc2a6-154">Nie wyświetla banera startowego ani wiadomości o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-154">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="dc2a6-155">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="dc2a6-156">Nie wykonuje niejawnego przywracania podczas uruchamiania polecenia.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-156">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="dc2a6-157">Określa ścieżkę dla katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-157">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="dc2a6-158">Jeśli nie zostanie określony, domyślnie *[project_file_folder]./bin/[konfiguracja]/[framework]/publish/* dla plików binarnych wykonywalnych zależnych od środowiska uruchomieniowego i między platformami.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-158">If not specified, it defaults to *[project_file_folder]./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="dc2a6-159">Domyślnie *[project_file_folder]/bin/[konfiguracja]/[framework]/[runtime]/publish/* dla samodzielnego pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-159">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  - <span data-ttu-id="dc2a6-160">.NET Core 3.x SDK i nowsze</span><span class="sxs-lookup"><span data-stu-id="dc2a6-160">.NET Core 3.x SDK and later</span></span>
  
    <span data-ttu-id="dc2a6-161">Jeśli ścieżka względna jest określona podczas publikowania projektu, wygenerowany katalog wyjściowy jest względem bieżącego katalogu roboczego, a nie do lokalizacji pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-161">If a relative path is specified when publishing a project, the output directory generated is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="dc2a6-162">Jeśli ścieżka względna jest określona podczas publikowania rozwiązania, wszystkie dane wyjściowe dla wszystkich projektów przechodzą do określonego folderu względem bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-162">If a relative path is specified when publishing a solution, all output for all projects go into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="dc2a6-163">Aby dane wyjściowe publikowania przejść do oddzielnych folderów dla każdego projektu, należy określić ścieżkę względną przy użyciu msbuild `PublishDir` właściwości zamiast `--output` opcji.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-163">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="dc2a6-164">Na przykład `dotnet publish -p:PublishDir=.\publish` wysyła dane wyjściowe `publish` publikowania dla każdego projektu do folderu w folderze, który zawiera plik projektu.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-164">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="dc2a6-165">.NET Core 2.x SDK</span><span class="sxs-lookup"><span data-stu-id="dc2a6-165">.NET Core 2.x SDK</span></span>
  
    <span data-ttu-id="dc2a6-166">Jeśli ścieżka względna jest określona podczas publikowania projektu, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie do bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-166">If a relative path is specified when publishing a project, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="dc2a6-167">Jeśli ścieżka względna jest określona podczas publikowania rozwiązania, dane wyjściowe każdego projektu przechodzi do oddzielnego folderu względem lokalizacji pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-167">If a relative path is specified when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="dc2a6-168">Jeśli ścieżka bezwzględna jest określona podczas publikowania rozwiązania, wszystkie dane wyjściowe publikowania dla wszystkich projektów przechodzi do określonego folderu.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-168">If an absolute path is specified when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="dc2a6-169">Publikuje środowisko uruchomieniowe .NET Core z aplikacją, więc środowisko wykonawcze nie musi być instalowane na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-169">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="dc2a6-170">Wartość `true` domyślna to pozycja, w przypadku gdy określono identyfikator środowiska uruchomieniowego, a projekt jest projektem wykonywalnym (a nie projektem biblioteki).</span><span class="sxs-lookup"><span data-stu-id="dc2a6-170">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="dc2a6-171">Aby uzyskać więcej informacji, zobacz [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="dc2a6-171">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="dc2a6-172">Jeśli ta opcja jest `true` używana `false`bez określania lub , domyślnie jest `true`.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-172">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="dc2a6-173">W takim przypadku nie należy umieszczać rozwiązania `--self-contained`lub `true` argumentu projektu natychmiast po , ponieważ lub `false` oczekuje się w tej pozycji.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-173">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="dc2a6-174">Odpowiednik `--self-contained false`.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-174">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="dc2a6-175">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-175">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="dc2a6-176">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="dc2a6-177">Aby uzyskać listę identyfikatorów środowiska wykonawczego (RID), zobacz [katalog RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="dc2a6-177">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="dc2a6-178">Aby uzyskać więcej informacji, zobacz [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="dc2a6-178">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="dc2a6-179">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-179">Sets the verbosity level of the command.</span></span> <span data-ttu-id="dc2a6-180">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="dc2a6-180">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="dc2a6-181">Wartością `minimal`domyślną jest .</span><span class="sxs-lookup"><span data-stu-id="dc2a6-181">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="dc2a6-182">Definiuje sufiks wersji, który ma`*`zastąpić gwiazdkę ( ) w polu wersji pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="dc2a6-183">Przykłady</span><span class="sxs-lookup"><span data-stu-id="dc2a6-183">Examples</span></span>

- <span data-ttu-id="dc2a6-184">Utwórz [zależne od środowiska uruchomieniowego wieloplatformowe binarne](../deploying/index.md#produce-a-cross-platform-binary) dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="dc2a6-184">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="dc2a6-185">Począwszy od .NET Core 3.0 SDK, w tym przykładzie tworzy również [plik wykonywalny zależny od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) dla bieżącej platformy.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-185">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="dc2a6-186">Utwórz [samodzielny plik wykonywalny](../deploying/index.md#publish-self-contained) dla projektu w bieżącym katalogu dla określonego środowiska wykonawczego:</span><span class="sxs-lookup"><span data-stu-id="dc2a6-186">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="dc2a6-187">Identyfikator RID musi znajdować się w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-187">The RID must be in the project file.</span></span>

- <span data-ttu-id="dc2a6-188">Utwórz [plik wykonywalny zależny od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) dla projektu w bieżącym katalogu dla określonej platformy:</span><span class="sxs-lookup"><span data-stu-id="dc2a6-188">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="dc2a6-189">Identyfikator RID musi znajdować się w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-189">The RID must be in the project file.</span></span> <span data-ttu-id="dc2a6-190">W tym przykładzie stosuje się do .NET Core 3.0 SDK i nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="dc2a6-190">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="dc2a6-191">Publikowanie projektu w bieżącym katalogu dla określonej platformy środowiska wykonawczego i docelowego:</span><span class="sxs-lookup"><span data-stu-id="dc2a6-191">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="dc2a6-192">Opublikuj określony plik projektu:</span><span class="sxs-lookup"><span data-stu-id="dc2a6-192">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="dc2a6-193">Opublikuj bieżącą aplikację, ale nie przywracaj odwołań do projektu do projektu (P2P), tylko projekt główny podczas operacji przywracania:</span><span class="sxs-lookup"><span data-stu-id="dc2a6-193">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="dc2a6-194">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc2a6-194">See also</span></span>

- [<span data-ttu-id="dc2a6-195">Omówienie publikowania aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="dc2a6-195">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="dc2a6-196">Publikowanie aplikacji .NET Core za pomocą interfejsu wiersza polecenia .NET Core</span><span class="sxs-lookup"><span data-stu-id="dc2a6-196">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="dc2a6-197">Platformy docelowe</span><span class="sxs-lookup"><span data-stu-id="dc2a6-197">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="dc2a6-198">Katalog identyfikatorów IDentifier (RID)</span><span class="sxs-lookup"><span data-stu-id="dc2a6-198">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="dc2a6-199">Praca z macOS Catalina Notarization</span><span class="sxs-lookup"><span data-stu-id="dc2a6-199">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="dc2a6-200">Struktura katalogów opublikowanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="dc2a6-200">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="dc2a6-201">Odwołanie do wiersza polecenia MSBuild</span><span class="sxs-lookup"><span data-stu-id="dc2a6-201">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="dc2a6-202">Profile publikowania w programie Visual Studio (pubxml) dla ASP.NET wdrożenia aplikacji Core</span><span class="sxs-lookup"><span data-stu-id="dc2a6-202">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="dc2a6-203">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="dc2a6-203">dotnet msbuild</span></span>](dotnet-msbuild.md)
