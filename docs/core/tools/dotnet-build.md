---
title: polecenia DotNet kompilacji polecenia — interfejs wiersza polecenia platformy .NET Core
description: Dotnet kompilacji polecenia kompilacji w projekt i wszystkie jego zależności.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: c9d1478e3d3e298b01e707242cc7ad5cd924a9b3
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200558"
---
# <a name="dotnet-build"></a><span data-ttu-id="3b915-103">Kompilacja DotNet</span><span class="sxs-lookup"><span data-stu-id="3b915-103">dotnet build</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="3b915-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3b915-104">Name</span></span>

<span data-ttu-id="3b915-105">`dotnet build` -Kompiluje projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="3b915-105">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3b915-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="3b915-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3b915-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="3b915-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3b915-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3b915-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="3b915-109">Opis</span><span class="sxs-lookup"><span data-stu-id="3b915-109">Description</span></span>

<span data-ttu-id="3b915-110">`dotnet build` Polecenie kompiluje projekt i jego zależności do zestawu plików binarnych.</span><span class="sxs-lookup"><span data-stu-id="3b915-110">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="3b915-111">Pliki binarne obejmują kodu projektu w plikach języka pośredniego (IL) z *.dll* plików symboli i rozszerzenia, które są używane do debugowania za pomocą *.pdb* rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="3b915-111">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="3b915-112">Plik JSON zależności (*\*. deps.json*) jest generowany, znajduje się wykaz zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b915-112">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="3b915-113">A  *\*. runtimeconfig.json* generowany jest plik, który określa udostępnionego środowiska uruchomieniowego i jego wersję aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b915-113">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="3b915-114">Jeśli projekt zawiera zależności innych firm, takich jak biblioteki z pakietów NuGet, jest rozwiązany z pamięcią podręczną programu NuGet i nie są dostępne w skompilowanych danych wyjściowych projektu.</span><span class="sxs-lookup"><span data-stu-id="3b915-114">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="3b915-115">Mając to na uwadze, wynikiem `dotnet build` nie jest gotowa do przeniesienia do innego komputera do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="3b915-115">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="3b915-116">Jest to w przeciwieństwie do zachowania programu .NET Framework w budynku, które projekt wykonywalny (aplikacji) generuje dane wyjściowe, który jest możliwy do uruchomienia na dowolnym komputerze, gdzie .NET Framework jest zainstalowana.</span><span class="sxs-lookup"><span data-stu-id="3b915-116">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="3b915-117">Aby podobnie środowisko z platformą .NET Core, musisz użyć [publikowania dotnet](dotnet-publish.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="3b915-117">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="3b915-118">Aby uzyskać więcej informacji, zobacz [wdrożenie aplikacji programu .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="3b915-118">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="3b915-119">Kompilowanie wymaga *project.assets.json* pliku, który znajduje się wykaz zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3b915-119">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="3b915-120">Plik jest tworzony, gdy [ `dotnet restore` ](dotnet-restore.md) jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="3b915-120">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="3b915-121">Bez pliku zasobów w miejscu narzędzi nie można rozpoznać zestawy odwołań, co powoduje błędy.</span><span class="sxs-lookup"><span data-stu-id="3b915-121">Without the assets file in place, the tooling cannot resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="3b915-122">Za pomocą programu .NET Core 1.x SDK wymagane do uruchamiania jawnie `dotnet restore` przed uruchomieniem `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="3b915-122">With .NET Core 1.x SDK, you needed to explicitly run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="3b915-123">Począwszy od programu .NET Core 2.0 SDK, `dotnet restore` uruchamia się domyślnie po uruchomieniu `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="3b915-123">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="3b915-124">Jeśli chcesz wyłączyć niejawne przywracania, podczas uruchamiania polecenia kompilacji, można przekazać `--no-restore` opcji.</span><span class="sxs-lookup"><span data-stu-id="3b915-124">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="3b915-125">`dotnet build` używa programu MSBuild do kompilowania projektu, więc obsługują równoległych oraz przyrostowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3b915-125">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="3b915-126">Aby uzyskać więcej informacji, zobacz [kompilacje przyrostowe](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="3b915-126">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="3b915-127">Oprócz jej opcji `dotnet build` polecenie akceptuje opcje programu MSBuild `-p` do ustawiania właściwości lub `-l` do definiowania rejestrator.</span><span class="sxs-lookup"><span data-stu-id="3b915-127">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="3b915-128">Aby uzyskać więcej informacji o tych opcjach, zobacz [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="3b915-128">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="3b915-129">Projekt jest wykonywalny lub nie jest określana przez `<OutputType>` właściwość w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="3b915-129">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="3b915-130">Poniższy przykład przedstawia projekt, który generuje kod wykonywalny:</span><span class="sxs-lookup"><span data-stu-id="3b915-130">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="3b915-131">Aby wygenerować bibliotekę, Pomiń `<OutputType>` właściwości.</span><span class="sxs-lookup"><span data-stu-id="3b915-131">In order to produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="3b915-132">Główną różnicą w skompilowanych danych wyjściowych jest, że biblioteki DLL IL nie zawiera punkty wejścia i nie można wykonać.</span><span class="sxs-lookup"><span data-stu-id="3b915-132">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

## <a name="arguments"></a><span data-ttu-id="3b915-133">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3b915-133">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="3b915-134">Plik projektu lub rozwiązania do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3b915-134">The project or solution file to build.</span></span> <span data-ttu-id="3b915-135">Jeśli nie określono pliku projektu lub rozwiązania, MSBuild przeszukuje bieżącego katalogu roboczego dla pliku, który ma rozszerzenie pliku, który kończy się w jednym *proj* lub *sln* i używa tego pliku.</span><span class="sxs-lookup"><span data-stu-id="3b915-135">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="3b915-136">Opcje</span><span class="sxs-lookup"><span data-stu-id="3b915-136">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="3b915-137">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="3b915-137">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="3b915-138">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3b915-138">Defines the build configuration.</span></span> <span data-ttu-id="3b915-139">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="3b915-139">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="3b915-140">Kompiluje dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="3b915-140">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="3b915-141">Struktura musi być zdefiniowany w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="3b915-141">The framework must be defined in the [project file](csproj.md).</span></span>

`--force`

<span data-ttu-id="3b915-142">Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="3b915-142">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="3b915-143">Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="3b915-143">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="3b915-144">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="3b915-144">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="3b915-145">Ignoruje odwołania do projektu do projektu (P2P) i tylko kompilacje określonym katalogu głównym projektu.</span><span class="sxs-lookup"><span data-stu-id="3b915-145">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

`--no-incremental`

<span data-ttu-id="3b915-146">Oznaczenie kompilacji jako niebezpieczny dla kompilacji przyrostowej.</span><span class="sxs-lookup"><span data-stu-id="3b915-146">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="3b915-147">Ta flaga powoduje wyłączenie kompilacji przyrostowej i wymusza czyste odbudowania tego wykresu zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="3b915-147">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`--no-restore`

<span data-ttu-id="3b915-148">Nie jest wykonywana niejawna przywracania, podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3b915-148">Doesn't execute an implicit restore during build.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="3b915-149">Katalog, w której chcesz umieścić skompilowane pliki binarne.</span><span class="sxs-lookup"><span data-stu-id="3b915-149">Directory in which to place the built binaries.</span></span> <span data-ttu-id="3b915-150">Musisz również zdefiniować `--framework` po określeniu tej opcji.</span><span class="sxs-lookup"><span data-stu-id="3b915-150">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="3b915-151">Określa docelowe środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="3b915-151">Specifies the target runtime.</span></span> <span data-ttu-id="3b915-152">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="3b915-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="3b915-153">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="3b915-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3b915-154">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="3b915-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="3b915-155">Określa sufiks wersji znak gwiazdki (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="3b915-155">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="3b915-156">Format jest zgodny wskazówki wersji NuGet.</span><span class="sxs-lookup"><span data-stu-id="3b915-156">The format follows NuGet's version guidelines.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="3b915-157">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="3b915-157">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="3b915-158">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3b915-158">Defines the build configuration.</span></span> <span data-ttu-id="3b915-159">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="3b915-159">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="3b915-160">Kompiluje dla określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="3b915-160">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="3b915-161">Struktura musi być zdefiniowany w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="3b915-161">The framework must be defined in the [project file](csproj.md).</span></span>

`-h|--help`

<span data-ttu-id="3b915-162">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="3b915-162">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="3b915-163">Ignoruje odwołania do projektu do projektu (P2P) i tylko kompilacje określonym katalogu głównym projektu.</span><span class="sxs-lookup"><span data-stu-id="3b915-163">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

`--no-incremental`

<span data-ttu-id="3b915-164">Oznaczenie kompilacji jako niebezpieczny dla kompilacji przyrostowej.</span><span class="sxs-lookup"><span data-stu-id="3b915-164">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="3b915-165">Ta flaga powoduje wyłączenie kompilacji przyrostowej i wymusza czyste odbudowania tego wykresu zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="3b915-165">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="3b915-166">Katalog, w której chcesz umieścić skompilowane pliki binarne.</span><span class="sxs-lookup"><span data-stu-id="3b915-166">Directory in which to place the built binaries.</span></span> <span data-ttu-id="3b915-167">Musisz również zdefiniować `--framework` po określeniu tej opcji.</span><span class="sxs-lookup"><span data-stu-id="3b915-167">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="3b915-168">Określa docelowe środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="3b915-168">Specifies the target runtime.</span></span> <span data-ttu-id="3b915-169">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="3b915-169">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="3b915-170">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="3b915-170">Sets the verbosity level of the command.</span></span> <span data-ttu-id="3b915-171">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="3b915-171">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="3b915-172">Określa sufiks wersji znak gwiazdki (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="3b915-172">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="3b915-173">Format jest zgodny wskazówki wersji NuGet.</span><span class="sxs-lookup"><span data-stu-id="3b915-173">The format follows NuGet's version guidelines.</span></span>

---

## <a name="examples"></a><span data-ttu-id="3b915-174">Przykłady</span><span class="sxs-lookup"><span data-stu-id="3b915-174">Examples</span></span>

<span data-ttu-id="3b915-175">Tworzenie projektu i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="3b915-175">Build a project and its dependencies:</span></span>

`dotnet build`

<span data-ttu-id="3b915-176">Tworzenie projektu i jego zależności za pomocą wersji konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="3b915-176">Build a project and its dependencies using Release configuration:</span></span>

`dotnet build --configuration Release`

<span data-ttu-id="3b915-177">Tworzenie projektu i jego zależności dla określonego środowiska uruchomieniowego (w tym przykładzie Ubuntu 16.04):</span><span class="sxs-lookup"><span data-stu-id="3b915-177">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 16.04):</span></span>

`dotnet build --runtime ubuntu.16.04-x64`

<span data-ttu-id="3b915-178">Skompiluj projekt, a następnie użyj określonego źródła pakietu NuGet podczas operacji przywracania (.NET Core SDK 2.0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="3b915-178">Build the project and use the specified NuGet package source during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet build --source c:\packages\mypackages`