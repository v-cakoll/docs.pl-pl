---
title: polecenie dotnet publish
description: Dotnet publish polecenie publikuje projekt .NET Core lub rozwiązanie w katalogu.
ms.date: 02/24/2020
ms.openlocfilehash: 697746291a8b34a856433049fe7264ad0ea4af7a
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761905"
---
# <a name="dotnet-publish"></a><span data-ttu-id="788fa-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="788fa-103">dotnet publish</span></span>

<span data-ttu-id="788fa-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="788fa-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="788fa-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="788fa-105">Name</span></span>

<span data-ttu-id="788fa-106">`dotnet publish`-Publikuje aplikację i jej zależności do folderu wdrożenia w systemie hostingu.</span><span class="sxs-lookup"><span data-stu-id="788fa-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="788fa-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="788fa-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive]
    [--manifest <PATH_TO_MANIFEST_FILE>] [--no-build] [--no-dependencies]
    [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-p:PublishReadyToRun=true] [-p:PublishSingleFile=true] [-p:PublishTrimmed=true]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--self-contained [true|false]]
    [--no-self-contained] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet publish -h|--help
```

## <a name="description"></a><span data-ttu-id="788fa-108">Opis</span><span class="sxs-lookup"><span data-stu-id="788fa-108">Description</span></span>

<span data-ttu-id="788fa-109">`dotnet publish`kompiluje aplikację, odczytuje ją z zależności określonych w pliku projektu i publikuje zestaw plików w katalogu.</span><span class="sxs-lookup"><span data-stu-id="788fa-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="788fa-110">Dane wyjściowe obejmują następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="788fa-110">The output includes the following assets:</span></span>

- <span data-ttu-id="788fa-111">Kod języka pośredniego (IL) w zestawie z rozszerzeniem *dll* .</span><span class="sxs-lookup"><span data-stu-id="788fa-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="788fa-112">Plik *. deps. JSON* , który zawiera wszystkie zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="788fa-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="788fa-113">Plik *. runtimeconfig. JSON* , który określa udostępnione środowisko uruchomieniowe oczekiwane przez aplikację, a także inne opcje konfiguracji środowiska uruchomieniowego (na przykład typ wyrzucania elementów bezużytecznych).</span><span class="sxs-lookup"><span data-stu-id="788fa-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="788fa-114">Zależności aplikacji, które są kopiowane z pamięci podręcznej NuGet do folderu danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="788fa-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="788fa-115">`dotnet publish`Dane wyjściowe polecenia są gotowe do wdrożenia w systemie hostingu (na przykład na serwerze, komputerze, Mac, laptopie) do wykonania.</span><span class="sxs-lookup"><span data-stu-id="788fa-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="788fa-116">Jest to jedyna oficjalnie obsługiwana metoda przygotowania aplikacji do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="788fa-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="788fa-117">W zależności od typu wdrożenia, który jest określany przez projekt, system hostingu może lub nie ma zainstalowanego udostępnionego środowiska uruchomieniowego platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="788fa-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="788fa-118">Aby uzyskać więcej informacji, zobacz [publikowanie aplikacji .NET Core za pomocą interfejs wiersza polecenia platformy .NET Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="788fa-118">For more information, see [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="788fa-119">Przywracanie niejawne</span><span class="sxs-lookup"><span data-stu-id="788fa-119">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

### <a name="msbuild"></a><span data-ttu-id="788fa-120">MSBuild</span><span class="sxs-lookup"><span data-stu-id="788fa-120">MSBuild</span></span>

<span data-ttu-id="788fa-121">`dotnet publish`Polecenie wywołuje program MSBuild, który wywołuje `Publish` element docelowy.</span><span class="sxs-lookup"><span data-stu-id="788fa-121">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="788fa-122">Wszystkie parametry przesłane do `dotnet publish` są przesyłane do programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="788fa-122">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="788fa-123">`-c`Parametry i są `-o` mapowane odpowiednio do programu MSBuild `Configuration` i `OutputPath` właściwości.</span><span class="sxs-lookup"><span data-stu-id="788fa-123">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `OutputPath` properties, respectively.</span></span>

<span data-ttu-id="788fa-124">`dotnet publish`Polecenie akceptuje Opcje programu MSBuild, takie jak `-p` Ustawienia właściwości i `-l` definiowania rejestratora.</span><span class="sxs-lookup"><span data-stu-id="788fa-124">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="788fa-125">Na przykład można ustawić właściwość programu MSBuild przy użyciu formatu: `-p:<NAME>=<VALUE>` .</span><span class="sxs-lookup"><span data-stu-id="788fa-125">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span> <span data-ttu-id="788fa-126">Można również ustawić właściwości związane z publikowaniem, odwołując się do pliku *. pubxml* , na przykład:</span><span class="sxs-lookup"><span data-stu-id="788fa-126">You can also set publish-related properties by referring to a *.pubxml* file, for example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

<span data-ttu-id="788fa-127">Więcej informacji zawierają następujące zasoby:</span><span class="sxs-lookup"><span data-stu-id="788fa-127">For more information, see the following resources:</span></span>

- [<span data-ttu-id="788fa-128">Dokumentacja wiersza polecenia programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="788fa-128">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="788fa-129">Profile publikacji programu Visual Studio (. pubxml) dla wdrożenia aplikacji ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="788fa-129">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="788fa-130">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="788fa-130">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="788fa-131">Argumenty</span><span class="sxs-lookup"><span data-stu-id="788fa-131">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="788fa-132">Projekt lub rozwiązanie do opublikowania.</span><span class="sxs-lookup"><span data-stu-id="788fa-132">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="788fa-133">`PROJECT`jest ścieżką i nazwą pliku projektu [c#](csproj.md), f # lub Visual Basic lub ścieżką do katalogu, który zawiera plik projektu C#, f # lub Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="788fa-133">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="788fa-134">Jeśli katalog nie jest określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="788fa-134">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="788fa-135">`SOLUTION`jest ścieżką i nazwą pliku rozwiązania (rozszerzeniem*sln* ) lub ścieżką do katalogu zawierającego plik rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="788fa-135">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="788fa-136">Jeśli katalog nie jest określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="788fa-136">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="788fa-137">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="788fa-137">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="788fa-138">Opcje</span><span class="sxs-lookup"><span data-stu-id="788fa-138">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="788fa-139">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="788fa-139">Defines the build configuration.</span></span> <span data-ttu-id="788fa-140">Wartością domyślną dla większości projektów jest `Debug` , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="788fa-140">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="788fa-141">Publikuje aplikację dla określonej [platformy docelowej](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="788fa-141">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="788fa-142">Należy określić platformę docelową w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="788fa-142">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="788fa-143">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="788fa-143">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="788fa-144">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="788fa-144">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="788fa-145">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="788fa-145">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="788fa-146">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję.</span><span class="sxs-lookup"><span data-stu-id="788fa-146">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="788fa-147">Na przykład, aby ukończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="788fa-147">For example, to complete authentication.</span></span> <span data-ttu-id="788fa-148">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="788fa-148">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="788fa-149">Określa jeden lub kilka [docelowych manifestów](../deploying/runtime-store.md) , które mają być używane do przycinania zestawu pakietów opublikowanych w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="788fa-149">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="788fa-150">Plik manifestu jest częścią danych wyjściowych [ `dotnet store` polecenia](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="788fa-150">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="788fa-151">Aby określić wiele manifestów, Dodaj `--manifest` opcję dla każdego manifestu.</span><span class="sxs-lookup"><span data-stu-id="788fa-151">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="788fa-152">Nie kompiluje projektu przed opublikowaniem.</span><span class="sxs-lookup"><span data-stu-id="788fa-152">Doesn't build the project before publishing.</span></span> <span data-ttu-id="788fa-153">Również niejawnie ustawia `--no-restore` flagę.</span><span class="sxs-lookup"><span data-stu-id="788fa-153">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="788fa-154">Ignoruje odwołania projektu do projektu i przywraca tylko projekt główny.</span><span class="sxs-lookup"><span data-stu-id="788fa-154">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="788fa-155">Nie wyświetla transparentu początkowego ani komunikatu o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="788fa-155">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="788fa-156">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="788fa-156">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="788fa-157">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="788fa-157">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="788fa-158">Określa ścieżkę do katalogu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="788fa-158">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="788fa-159">Jeśli nie zostanie określony, domyślna wartość to *[project_file_folder]./bin/[Konfiguracja]/[Framework]/Publish/* dla plików binarnych zależnych od środowiska uruchomieniowego i dla wielu platform.</span><span class="sxs-lookup"><span data-stu-id="788fa-159">If not specified, it defaults to *[project_file_folder]./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="788fa-160">Wartość domyślna to *[project_file_folder]/bin/[Konfiguracja]/[Framework]/[Runtime]/Publish/* dla samodzielnego pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="788fa-160">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="788fa-161">W projekcie sieci Web, jeśli folder wyjściowy znajduje się w folderze projektu, kolejne `dotnet publish` polecenia powodują zagnieżdżone foldery wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="788fa-161">In a web project, if the output folder is in the project folder, successive `dotnet publish` commands result in nested output folders.</span></span> <span data-ttu-id="788fa-162">Na przykład, jeśli folder projektu jest typu moje *projekty*, a folder danych wyjściowych publikowanie jest w *projekcie/publikacji*i uruchamiasz `dotnet publish` dwa razy, drugi przebieg umieszcza pliki zawartości, takie jak pliki *config* i *JSON* w programie *WebProject/Publish/Publish*.</span><span class="sxs-lookup"><span data-stu-id="788fa-162">For example, if the project folder is *myproject*, and the publish output folder is *myproject/publish*, and you run `dotnet publish` twice, the second run puts content files such as *.config* and *.json* files in *myproject/publish/publish*.</span></span> <span data-ttu-id="788fa-163">Aby uniknąć zagnieżdżania folderów publikowania, określ folder publikowania, który nie znajduje się **bezpośrednio** w folderze projektu, lub wyklucz folder publikacji z projektu.</span><span class="sxs-lookup"><span data-stu-id="788fa-163">To avoid nesting publish folders, specify a publish folder that is not **directly** under the project folder, or exclude the publish folder from the project.</span></span> <span data-ttu-id="788fa-164">Aby wykluczyć folder publikacji o nazwie *publishoutput*, Dodaj następujący element do `PropertyGroup` elementu w pliku *. csproj* :</span><span class="sxs-lookup"><span data-stu-id="788fa-164">To exclude a publish folder named *publishoutput*, add the following element to a `PropertyGroup` element in the *.csproj* file:</span></span>

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - <span data-ttu-id="788fa-165">.NET Core 3. x SDK i nowsze</span><span class="sxs-lookup"><span data-stu-id="788fa-165">.NET Core 3.x SDK and later</span></span>
  
    <span data-ttu-id="788fa-166">Jeśli ścieżka względna jest określona podczas publikowania projektu, wygenerowany katalog wyjściowy jest względem bieżącego katalogu roboczego, a nie lokalizacji pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="788fa-166">If a relative path is specified when publishing a project, the output directory generated is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="788fa-167">Jeśli ścieżka względna zostanie określona podczas publikowania rozwiązania, wszystkie dane wyjściowe dla wszystkich projektów przechodzą do określonego folderu względem bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="788fa-167">If a relative path is specified when publishing a solution, all output for all projects goes into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="788fa-168">Aby opublikować dane wyjściowe, przejdź do oddzielnych folderów dla każdego projektu, określ ścieżkę względną przy użyciu `PublishDir` właściwości MSBuild zamiast `--output` opcji.</span><span class="sxs-lookup"><span data-stu-id="788fa-168">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="788fa-169">Na przykład program `dotnet publish -p:PublishDir=.\publish` wysyła dane wyjściowe publikowania dla każdego projektu do `publish` folderu znajdującego się w folderze, który zawiera plik projektu.</span><span class="sxs-lookup"><span data-stu-id="788fa-169">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="788fa-170">Zestaw SDK platformy .NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="788fa-170">.NET Core 2.x SDK</span></span>
  
    <span data-ttu-id="788fa-171">Jeśli ścieżka względna jest określona podczas publikowania projektu, wygenerowany katalog wyjściowy jest względem lokalizacji pliku projektu, a nie do bieżącego katalogu roboczego.</span><span class="sxs-lookup"><span data-stu-id="788fa-171">If a relative path is specified when publishing a project, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="788fa-172">Jeśli ścieżka względna zostanie określona podczas publikowania rozwiązania, dane wyjściowe każdego projektu są umieszczane w oddzielnym folderze względem lokalizacji pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="788fa-172">If a relative path is specified when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="788fa-173">Jeśli ścieżka bezwzględna zostanie określona podczas publikowania rozwiązania, wszystkie dane wyjściowe publikowania dla wszystkich projektów przechodzą do określonego folderu.</span><span class="sxs-lookup"><span data-stu-id="788fa-173">If an absolute path is specified when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`-p:PublishReadyToRun=true`**

  <span data-ttu-id="788fa-174">Kompiluje zestawy aplikacji jako format ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="788fa-174">Compiles application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="788fa-175">R2R to forma kompilacji z wyprzedzeniem (AOT).</span><span class="sxs-lookup"><span data-stu-id="788fa-175">R2R is a form of ahead-of-time (AOT) compilation.</span></span> <span data-ttu-id="788fa-176">Aby uzyskać więcej informacji, zobacz [ReadyToRun images](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="788fa-176">For more information, see [ReadyToRun images](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span> <span data-ttu-id="788fa-177">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="788fa-177">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="788fa-178">Zalecamy określenie tej opcji w profilu publikowania, a nie w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="788fa-178">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="788fa-179">Aby uzyskać więcej informacji, zobacz [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="788fa-179">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishSingleFile=true`**

  <span data-ttu-id="788fa-180">Pakuje aplikację do pliku wykonywalnego określonego dla konkretnej platformy.</span><span class="sxs-lookup"><span data-stu-id="788fa-180">Packages the app into a platform-specific single-file executable.</span></span> <span data-ttu-id="788fa-181">Plik wykonywalny jest samowyodrębniający się i zawiera wszystkie zależności (w tym natywne) wymagane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="788fa-181">The executable is self-extracting and contains all dependencies (including native) that are required to run the app.</span></span> <span data-ttu-id="788fa-182">Gdy aplikacja jest uruchamiana po raz pierwszy, aplikacja zostanie wyodrębniona do katalogu na podstawie nazwy aplikacji i identyfikatora kompilacji.</span><span class="sxs-lookup"><span data-stu-id="788fa-182">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="788fa-183">Uruchamianie jest szybsze, gdy aplikacja jest uruchamiana ponownie.</span><span class="sxs-lookup"><span data-stu-id="788fa-183">Startup is faster when the application is run again.</span></span> <span data-ttu-id="788fa-184">Aplikacja nie musi wyodrębniać siebie po raz drugi, chyba że jest używana nowa wersja.</span><span class="sxs-lookup"><span data-stu-id="788fa-184">The application doesn't need to extract itself a second time unless a new version is used.</span></span> <span data-ttu-id="788fa-185">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="788fa-185">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="788fa-186">Aby uzyskać więcej informacji o publikowaniu jednoplikowym, zapoznaj się z [dokumentem projektu pakietu pojedynczego pliku](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="788fa-186">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span></span>

  <span data-ttu-id="788fa-187">Zalecamy określenie tej opcji w profilu publikowania, a nie w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="788fa-187">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="788fa-188">Aby uzyskać więcej informacji, zobacz [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="788fa-188">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishTrimmed=true`**

  <span data-ttu-id="788fa-189">Przycina nieużywane biblioteki, aby zmniejszyć rozmiar wdrożenia aplikacji podczas publikowania samodzielnego pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="788fa-189">Trims unused libraries to reduce the deployment size of an app when publishing a self-contained executable.</span></span> <span data-ttu-id="788fa-190">Aby uzyskać więcej informacji, zobacz sekcję [przycinanie wdrożeń samodzielnych i plików wykonywalnych](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="788fa-190">For more information, see [Trim self-contained deployments and executables](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="788fa-191">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="788fa-191">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="788fa-192">Zalecamy określenie tej opcji w profilu publikowania, a nie w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="788fa-192">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="788fa-193">Aby uzyskać więcej informacji, zobacz [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="788fa-193">For more information, see [MSBuild](#msbuild).</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="788fa-194">Publikuje środowisko uruchomieniowe platformy .NET Core przy użyciu aplikacji, aby nie trzeba było instalować środowiska uruchomieniowego na komputerze docelowym.</span><span class="sxs-lookup"><span data-stu-id="788fa-194">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="788fa-195">Wartość domyślna to `true` Jeśli określono identyfikator środowiska uruchomieniowego, a projekt jest projektem wykonywalnym (a nie projektem biblioteki).</span><span class="sxs-lookup"><span data-stu-id="788fa-195">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="788fa-196">Aby uzyskać więcej informacji, zobacz Aplikacje [.NET Core](../deploying/index.md) i publikowanie aplikacji [platformy .net core za pomocą interfejs wiersza polecenia platformy .NET Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="788fa-196">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="788fa-197">Jeśli ta opcja jest używana bez określenia `true` lub `false` , wartość domyślna to `true` .</span><span class="sxs-lookup"><span data-stu-id="788fa-197">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="788fa-198">W takim przypadku nie należy umieszczać rozwiązania ani argumentu projektu bezpośrednio po `--self-contained` , ponieważ `true` lub `false` jest oczekiwany w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="788fa-198">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="788fa-199">Odpowiednik `--self-contained false` .</span><span class="sxs-lookup"><span data-stu-id="788fa-199">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="788fa-200">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="788fa-200">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="788fa-201">Publikuje aplikację dla danego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="788fa-201">Publishes the application for a given runtime.</span></span> <span data-ttu-id="788fa-202">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="788fa-202">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="788fa-203">Aby uzyskać więcej informacji, zobacz Aplikacje [.NET Core](../deploying/index.md) i publikowanie aplikacji [platformy .net core za pomocą interfejs wiersza polecenia platformy .NET Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="788fa-203">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="788fa-204">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="788fa-204">Sets the verbosity level of the command.</span></span> <span data-ttu-id="788fa-205">Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="788fa-205">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="788fa-206">Wartość domyślna to `minimal` .</span><span class="sxs-lookup"><span data-stu-id="788fa-206">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="788fa-207">Definiuje sufiks wersji, aby zastąpić gwiazdkę ( `*` ) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="788fa-207">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="788fa-208">Przykłady</span><span class="sxs-lookup"><span data-stu-id="788fa-208">Examples</span></span>

- <span data-ttu-id="788fa-209">Utwórz [Międzyplatformowy plik binarny zależny od środowiska uruchomieniowego](../deploying/index.md#produce-a-cross-platform-binary) dla projektu w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="788fa-209">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="788fa-210">Począwszy od zestawu SDK platformy .NET Core 3,0, w tym przykładzie tworzony jest również [plik wykonywalny zależny od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) dla bieżącej platformy.</span><span class="sxs-lookup"><span data-stu-id="788fa-210">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="788fa-211">Utwórz [własny plik wykonywalny](../deploying/index.md#publish-self-contained) dla projektu w bieżącym katalogu dla określonego środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="788fa-211">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="788fa-212">Identyfikator RID musi znajdować się w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="788fa-212">The RID must be in the project file.</span></span>

- <span data-ttu-id="788fa-213">Utwórz [plik wykonywalny zależny od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) dla projektu w bieżącym katalogu dla określonej platformy:</span><span class="sxs-lookup"><span data-stu-id="788fa-213">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="788fa-214">Identyfikator RID musi znajdować się w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="788fa-214">The RID must be in the project file.</span></span> <span data-ttu-id="788fa-215">Ten przykład dotyczy zestawu .NET Core 3,0 SDK i nowszych wersji.</span><span class="sxs-lookup"><span data-stu-id="788fa-215">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="788fa-216">Opublikuj projekt w bieżącym katalogu dla określonego środowiska uruchomieniowego i platformy docelowej:</span><span class="sxs-lookup"><span data-stu-id="788fa-216">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="788fa-217">Publikuj określony plik projektu:</span><span class="sxs-lookup"><span data-stu-id="788fa-217">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="788fa-218">Opublikuj bieżącą aplikację, ale nie przywracaj odwołań z projektu do projektu (P2P), tylko projekt główny podczas operacji przywracania:</span><span class="sxs-lookup"><span data-stu-id="788fa-218">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="788fa-219">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="788fa-219">See also</span></span>

- [<span data-ttu-id="788fa-220">Omówienie publikowania aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="788fa-220">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="788fa-221">Publikowanie aplikacji platformy .NET Core za pomocą interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="788fa-221">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="788fa-222">Platformy docelowe</span><span class="sxs-lookup"><span data-stu-id="788fa-222">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="788fa-223">Wykaz identyfikatorów środowiska uruchomieniowego (RID)</span><span class="sxs-lookup"><span data-stu-id="788fa-223">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="788fa-224">Praca z macOS Catalina Notarization</span><span class="sxs-lookup"><span data-stu-id="788fa-224">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="788fa-225">Struktura katalogów opublikowanej aplikacji</span><span class="sxs-lookup"><span data-stu-id="788fa-225">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="788fa-226">Dokumentacja wiersza polecenia programu MSBuild</span><span class="sxs-lookup"><span data-stu-id="788fa-226">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="788fa-227">Profile publikacji programu Visual Studio (. pubxml) dla wdrożenia aplikacji ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="788fa-227">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="788fa-228">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="788fa-228">dotnet msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="788fa-229">ILLInk. Tasks</span><span class="sxs-lookup"><span data-stu-id="788fa-229">ILLInk.Tasks</span></span>](https://aka.ms/dotnet-illink)
