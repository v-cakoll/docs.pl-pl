---
title: polecenie kompilacji DotNet
description: Dotnet kompilacji polecenia kompilacji w projekt i wszystkie jego zależności.
ms.date: 04/24/2019
ms.openlocfilehash: 6564aacbe520797b47095929cfe72c6b180b99a7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632136"
---
# <a name="dotnet-build"></a><span data-ttu-id="519d1-103">Kompilacja DotNet</span><span class="sxs-lookup"><span data-stu-id="519d1-103">dotnet build</span></span>

<span data-ttu-id="519d1-104">**Ten artykuł dotyczy: ✓** platformy .NET Core SDK w wersji 1.x i nowszymi wersjami</span><span class="sxs-lookup"><span data-stu-id="519d1-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="519d1-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="519d1-105">Name</span></span>

<span data-ttu-id="519d1-106">`dotnet build` -Kompiluje projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="519d1-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="519d1-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="519d1-107">Synopsis</span></span>

```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--nologo] [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="519d1-108">Opis</span><span class="sxs-lookup"><span data-stu-id="519d1-108">Description</span></span>

<span data-ttu-id="519d1-109">`dotnet build` Polecenie kompiluje projekt i jego zależności do zestawu plików binarnych.</span><span class="sxs-lookup"><span data-stu-id="519d1-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="519d1-110">Pliki binarne obejmują kodu projektu w plikach języka pośredniego (IL) z *.dll* plików symboli i rozszerzenia, które są używane do debugowania za pomocą *.pdb* rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="519d1-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="519d1-111">Plik JSON zależności (*\*. deps.json*) jest generowany, znajduje się wykaz zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="519d1-111">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="519d1-112">A  *\*. runtimeconfig.json* generowany jest plik, który określa udostępnionego środowiska uruchomieniowego i jego wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="519d1-112">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="519d1-113">Jeśli projekt zawiera zależności innych firm, takich jak biblioteki z pakietów NuGet, jest rozwiązany z pamięcią podręczną programu NuGet i nie są dostępne w skompilowanych danych wyjściowych projektu.</span><span class="sxs-lookup"><span data-stu-id="519d1-113">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="519d1-114">Mając to na uwadze, wynikiem `dotnet build` nie jest gotowa do przeniesienia do innego komputera do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="519d1-114">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="519d1-115">Jest to w przeciwieństwie do zachowania programu .NET Framework w budynku, które projekt wykonywalny (aplikacji) generuje dane wyjściowe, który jest możliwy do uruchomienia na dowolnym komputerze, gdzie .NET Framework jest zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="519d1-115">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="519d1-116">Aby podobnie środowisko z platformą .NET Core, musisz użyć [publikowania dotnet](dotnet-publish.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="519d1-116">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="519d1-117">Aby uzyskać więcej informacji, zobacz [wdrożenie aplikacji programu .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="519d1-117">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="519d1-118">Kompilowanie wymaga *project.assets.json* pliku, który znajduje się wykaz zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="519d1-118">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="519d1-119">Plik jest tworzony, gdy [ `dotnet restore` ](dotnet-restore.md) jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="519d1-119">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="519d1-120">Bez pliku zasobów w miejscu narzędzi nie można rozpoznać zestawy odwołań, co powoduje błędy.</span><span class="sxs-lookup"><span data-stu-id="519d1-120">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="519d1-121">Za pomocą programu .NET Core 1.x SDK wymagane do uruchamiania jawnie `dotnet restore` przed uruchomieniem `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="519d1-121">With .NET Core 1.x SDK, you needed to explicitly run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="519d1-122">Począwszy od programu .NET Core 2.0 SDK, `dotnet restore` uruchamia się domyślnie po uruchomieniu `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="519d1-122">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="519d1-123">Jeśli chcesz wyłączyć niejawne przywracania, podczas uruchamiania polecenia kompilacji, można przekazać `--no-restore` opcji.</span><span class="sxs-lookup"><span data-stu-id="519d1-123">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="519d1-124">Projekt jest wykonywalny lub nie jest określana przez `<OutputType>` właściwość w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="519d1-124">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="519d1-125">Poniższy przykład przedstawia projekt, który generuje kod wykonywalny:</span><span class="sxs-lookup"><span data-stu-id="519d1-125">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="519d1-126">Aby wygenerować bibliotekę, Pomiń `<OutputType>` właściwości.</span><span class="sxs-lookup"><span data-stu-id="519d1-126">To produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="519d1-127">Główną różnicą w skompilowanych danych wyjściowych jest, że biblioteki DLL IL nie zawiera punkty wejścia i nie można wykonać.</span><span class="sxs-lookup"><span data-stu-id="519d1-127">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="519d1-128">MSBuild</span><span class="sxs-lookup"><span data-stu-id="519d1-128">MSBuild</span></span>

<span data-ttu-id="519d1-129">`dotnet build` używa programu MSBuild do kompilowania projektu, więc obsługują równoległych oraz przyrostowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="519d1-129">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="519d1-130">Aby uzyskać więcej informacji, zobacz [kompilacje przyrostowe](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="519d1-130">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="519d1-131">Oprócz jej opcji `dotnet build` polecenie akceptuje opcje programu MSBuild `-p` do ustawiania właściwości lub `-l` do definiowania rejestrator.</span><span class="sxs-lookup"><span data-stu-id="519d1-131">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="519d1-132">Aby uzyskać więcej informacji o tych opcjach, zobacz [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="519d1-132">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="519d1-133">Lub możesz również użyć [dotnet msbuild](dotnet-msbuild.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="519d1-133">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="519d1-134">Uruchamianie `dotnet build` jest odpowiednikiem `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="519d1-134">Running `dotnet build` is equivalent to `dotnet msbuild -restore -target:Build`.</span></span>

## <a name="arguments"></a><span data-ttu-id="519d1-135">Argumenty</span><span class="sxs-lookup"><span data-stu-id="519d1-135">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="519d1-136">Plik projektu lub rozwiązania do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="519d1-136">The project or solution file to build.</span></span> <span data-ttu-id="519d1-137">Jeśli nie określono pliku projektu lub rozwiązania, MSBuild przeszukuje bieżącego katalogu roboczego dla pliku, który ma rozszerzenie pliku, który kończy się w jednym *proj* lub *sln* i używa tego pliku.</span><span class="sxs-lookup"><span data-stu-id="519d1-137">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="519d1-138">Opcje</span><span class="sxs-lookup"><span data-stu-id="519d1-138">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="519d1-139">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="519d1-139">Defines the build configuration.</span></span> <span data-ttu-id="519d1-140">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="519d1-140">The default value is `Debug`.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="519d1-141">Kompiluje dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="519d1-141">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="519d1-142">Struktura musi być zdefiniowany w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="519d1-142">The framework must be defined in the [project file](csproj.md).</span></span>

* **`--force`**

  <span data-ttu-id="519d1-143">Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="519d1-143">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="519d1-144">Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="519d1-144">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="519d1-145">Dostępne, ponieważ .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="519d1-145">Available since .NET Core 2.0 SDK.</span></span>

* **`-h|--help`**

  <span data-ttu-id="519d1-146">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="519d1-146">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="519d1-147">Umożliwia polecenie, aby zatrzymać i czeka na dane wejściowe użytkownika lub akcji.</span><span class="sxs-lookup"><span data-stu-id="519d1-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="519d1-148">Na przykład w celu ukończenia uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="519d1-148">For example, to complete authentication.</span></span> <span data-ttu-id="519d1-149">Dostępne, ponieważ .NET Core SDK w wersji 3.0.</span><span class="sxs-lookup"><span data-stu-id="519d1-149">Available since .NET Core 3.0 SDK.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="519d1-150">Ignoruje odwołania do projektu do projektu (P2P) i tylko kompilacje określonym katalogu głównym projektu.</span><span class="sxs-lookup"><span data-stu-id="519d1-150">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="519d1-151">Oznaczenie kompilacji jako niebezpieczny dla kompilacji przyrostowej.</span><span class="sxs-lookup"><span data-stu-id="519d1-151">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="519d1-152">Ta flaga powoduje wyłączenie kompilacji przyrostowej i wymusza czyste odbudowania tego wykresu zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="519d1-152">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`--no-logo`**

  <span data-ttu-id="519d1-153">Nie wyświetla transparentu lub komunikat o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="519d1-153">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="519d1-154">Dostępne, ponieważ .NET Core SDK w wersji 3.0.</span><span class="sxs-lookup"><span data-stu-id="519d1-154">Available since .NET Core 3.0 SDK.</span></span>

* **`--no-restore`**

  <span data-ttu-id="519d1-155">Nie jest wykonywana niejawna przywracania, podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="519d1-155">Doesn't execute an implicit restore during build.</span></span> <span data-ttu-id="519d1-156">Dostępne, ponieważ .NET Core 2.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="519d1-156">Available since .NET Core 2.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="519d1-157">Katalog, w której chcesz umieścić skompilowane pliki binarne.</span><span class="sxs-lookup"><span data-stu-id="519d1-157">Directory in which to place the built binaries.</span></span> <span data-ttu-id="519d1-158">Musisz również zdefiniować `--framework` po określeniu tej opcji.</span><span class="sxs-lookup"><span data-stu-id="519d1-158">You also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="519d1-159">Jeśli nie zostanie określony, domyślna ścieżka to `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="519d1-159">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="519d1-160">Określa docelowe środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="519d1-160">Specifies the target runtime.</span></span> <span data-ttu-id="519d1-161">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="519d1-161">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="519d1-162">Ustawia poziom szczegółowości MSBuild.</span><span class="sxs-lookup"><span data-stu-id="519d1-162">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="519d1-163">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="519d1-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="519d1-164">Wartość domyślna to `minimal`.</span><span class="sxs-lookup"><span data-stu-id="519d1-164">The default is `minimal`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="519d1-165">Ustawia wartość `$(VersionSuffix)` właściwość do użycia podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="519d1-165">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="519d1-166">To tylko wtedy, gdy `$(Version)` nie jest właściwością.</span><span class="sxs-lookup"><span data-stu-id="519d1-166">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="519d1-167">Następnie `$(Version)` ustawiono `$(VersionPrefix)` w połączeniu z `$(VersionSuffix)`, oddzielone kreską.</span><span class="sxs-lookup"><span data-stu-id="519d1-167">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="519d1-168">Przykłady</span><span class="sxs-lookup"><span data-stu-id="519d1-168">Examples</span></span>

* <span data-ttu-id="519d1-169">Tworzenie projektu i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="519d1-169">Build a project and its dependencies:</span></span>

  ```console
  dotnet build
  ```

* <span data-ttu-id="519d1-170">Tworzenie projektu i jego zależności za pomocą wersji konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="519d1-170">Build a project and its dependencies using Release configuration:</span></span>

  ```console
  dotnet build --configuration Release
  ```

* <span data-ttu-id="519d1-171">Tworzenie projektu i jego zależności dla określonego środowiska uruchomieniowego (w tym przykładzie Ubuntu 18.04):</span><span class="sxs-lookup"><span data-stu-id="519d1-171">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```console
  dotnet build --runtime ubuntu.18.04-x64
  ```

* <span data-ttu-id="519d1-172">Skompiluj projekt, a następnie użyj określonego źródła pakietu NuGet podczas operacji przywracania (.NET Core 2.0 SDK i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="519d1-172">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* <span data-ttu-id="519d1-173">Skompilować projekt i ustawić 1.2.3.4 wersji jako parametr kompilacji:</span><span class="sxs-lookup"><span data-stu-id="519d1-173">Build the project and set 1.2.3.4 version as a build parameter:</span></span>

  ```console
  dotnet build -p:Version=1.2.3.4
  ```
