---
title: DotNet kompilacji command - .NET Core interfejsu wiersza polecenia
description: "Dotnet kompilacji polecenie kompilacji projektu i wszystkie jego zależności."
author: mairaw
ms.author: mairaw
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: b2b625729b5db22bc7b69194f20963857004e3e7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-build"></a><span data-ttu-id="db836-103">Kompilacja DotNet</span><span class="sxs-lookup"><span data-stu-id="db836-103">dotnet-build</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="db836-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="db836-104">Name</span></span>

<span data-ttu-id="db836-105">`dotnet build`-Tworzy projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="db836-105">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="db836-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="db836-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="db836-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="db836-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental] [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="db836-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="db836-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="db836-109">Opis</span><span class="sxs-lookup"><span data-stu-id="db836-109">Description</span></span>

<span data-ttu-id="db836-110">`dotnet build` Polecenie kompilacji projektu i jego zależności do zestawu plików binarnych.</span><span class="sxs-lookup"><span data-stu-id="db836-110">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="db836-111">Pliki binarne zawiera kod projektu w języku pośrednim (IL) pliki z *.dll* plików symboli i rozszerzenia, które są używane do debugowania z *.pdb* rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="db836-111">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="db836-112">Plik JSON zależności (*\*. deps.json*) jest tworzony który znajduje się wykaz zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="db836-112">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="db836-113">A  *\*. runtimeconfig.json* jest generowany, określającej udostępnionego środowiska uruchomieniowego i wersja aplikacji.</span><span class="sxs-lookup"><span data-stu-id="db836-113">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="db836-114">Jeśli projekt zawiera zależności innych firm, takich jak biblioteki z pakietu NuGet, jest rozwiązany z pamięci podręcznej NuGet i nie są dostępne z skompilowanych danych wyjściowych projektu.</span><span class="sxs-lookup"><span data-stu-id="db836-114">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="db836-115">Z tym pamiętać iloczyn `dotnet build` nie jest gotowa do przeniesienia na inny komputer, aby uruchomić.</span><span class="sxs-lookup"><span data-stu-id="db836-115">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="db836-116">Dzięki temu nie trzeba zachowanie programu .NET Framework w budynku, który projekt wykonywalny (aplikacja) tworzy dane wyjściowe do uruchomienia na dowolnym komputerze z zainstalowanym programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="db836-116">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="db836-117">Aby podobne możliwości z platformą .NET Core, musisz użyć [publikowania dotnet](dotnet-publish.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="db836-117">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="db836-118">Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="db836-118">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="db836-119">Kompilowanie wymaga *project.assets.json* pliku, który zawiera listę zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="db836-119">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="db836-120">Podczas tworzenia pliku [ `dotnet restore` ](dotnet-restore.md) jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="db836-120">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="db836-121">Bez miejscowej pliku zasobów narzędzia nie można rozpoznać zestawy referencyjne zakończyło się z błędami.</span><span class="sxs-lookup"><span data-stu-id="db836-121">Without the assets file in place, the tooling cannot resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="db836-122">Z platformą .NET Core uruchom 1.x zestawu SDK, trzeba było explicitily `dotnet restore` przed uruchomieniem `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="db836-122">With .NET Core 1.x SDK, you needed to explicitily run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="db836-123">Począwszy od platformy .NET Core SDK 2.0, `dotnet restore` uruchamia implicitily po uruchomieniu `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="db836-123">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitily when you run `dotnet build`.</span></span> <span data-ttu-id="db836-124">Jeśli chcesz wyłączyć niejawne przywracania podczas wykonywania poleceń kompilacji, można przekazać `--no-restore` opcji.</span><span class="sxs-lookup"><span data-stu-id="db836-124">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="db836-125">`dotnet build`korzysta z programu MSBuild w celu skompilowania projektu; w związku z tym obsługuje ona zarówno równoległe, jak i przyrostowe kompilacji.</span><span class="sxs-lookup"><span data-stu-id="db836-125">`dotnet build` uses MSBuild to build the project; thus, it supports both parallel and incremental builds.</span></span> <span data-ttu-id="db836-126">Zapoznaj się [kompilacje przyrostowe](/visualstudio/msbuild/incremental-builds) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="db836-126">Refer to [Incremental Builds](/visualstudio/msbuild/incremental-builds) for more information.</span></span>

<span data-ttu-id="db836-127">Oprócz jego opcje `dotnet build` polecenie akceptuje opcje MSBuild `/p` do ustawiania właściwości lub `/l` do definiowania rejestrator.</span><span class="sxs-lookup"><span data-stu-id="db836-127">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `/p` for setting properties or `/l` to define a logger.</span></span> <span data-ttu-id="db836-128">Dowiedz się więcej o tych opcjach w [dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="db836-128">Learn more about these options in the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> 

<span data-ttu-id="db836-129">Określa, czy projekt jest wykonywalne, lub nie jest określany przez `<OutputType>` właściwość w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="db836-129">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="db836-130">W poniższym przykładzie przedstawiono projekt, który utworzy kodu wykonywalnego:</span><span class="sxs-lookup"><span data-stu-id="db836-130">The following example shows a project that will produce executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="db836-131">Aby można było utworzyć bibliotekę, Pomiń `<OutputType>` właściwości.</span><span class="sxs-lookup"><span data-stu-id="db836-131">In order to produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="db836-132">Główna różnica w skompilowanych danych wyjściowych jest nie zawiera punktów wejścia biblioteki DLL IL dla biblioteki oraz nie może zostać wykonana.</span><span class="sxs-lookup"><span data-stu-id="db836-132">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span> 

## <a name="arguments"></a><span data-ttu-id="db836-133">Argumenty</span><span class="sxs-lookup"><span data-stu-id="db836-133">Arguments</span></span>

`PROJECT`

<span data-ttu-id="db836-134">Plik projektu do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="db836-134">The project file to build.</span></span> <span data-ttu-id="db836-135">Jeśli nie określono pliku projektu, MSBuild wyszukuje bieżącego katalogu roboczego dla pliku, który ma rozszerzenie pliku, który kończy się *proj* i używa tego pliku.</span><span class="sxs-lookup"><span data-stu-id="db836-135">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="db836-136">Opcje</span><span class="sxs-lookup"><span data-stu-id="db836-136">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="db836-137">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="db836-137">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="db836-138">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="db836-138">Defines the build configuration.</span></span> <span data-ttu-id="db836-139">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="db836-139">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="db836-140">Kompiluje z określonym [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="db836-140">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="db836-141">Platformę musi być zdefiniowana w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="db836-141">The framework must be defined in the [project file](csproj.md).</span></span>

`--force`

 <span data-ttu-id="db836-142">Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="db836-142">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="db836-143">Jest to równoważne usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="db836-143">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="db836-144">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="db836-144">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="db836-145">Ignoruje odwołuje się do projektu do projektu (P2P) i tylko kompilacje główny projekt określony do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="db836-145">Ignores project-to-project (P2P) references and only builds the root project specified to build.</span></span>

`--no-incremental`

<span data-ttu-id="db836-146">Oznaczenie kompilacji jako niebezpieczny dla kompilacji przyrostowej.</span><span class="sxs-lookup"><span data-stu-id="db836-146">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="db836-147">To powoduje wyłączenie kompilacji przyrostowej i wymusza czystą kompilowania wykresu zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="db836-147">This turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`--no-restore`

<span data-ttu-id="db836-148">Nie wykonać przywracanie niejawne podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="db836-148">Doesn't perform an implicit restore during build.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="db836-149">Katalog, w którym można umieścić skompilowanych plików binarnych.</span><span class="sxs-lookup"><span data-stu-id="db836-149">Directory in which to place the built binaries.</span></span> <span data-ttu-id="db836-150">Należy również określić `--framework` po określeniu tej opcji.</span><span class="sxs-lookup"><span data-stu-id="db836-150">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="db836-151">Określa docelowe środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="db836-151">Specifies the target runtime.</span></span> <span data-ttu-id="db836-152">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="db836-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="db836-153">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="db836-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="db836-154">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="db836-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="db836-155">Określa sufiks wersji gwiazdkę (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="db836-155">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="db836-156">Format jest zgodny wytyczne wersja narzędzia NuGet.</span><span class="sxs-lookup"><span data-stu-id="db836-156">The format follows NuGet's version guidelines.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="db836-157">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="db836-157">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="db836-158">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="db836-158">Defines the build configuration.</span></span> <span data-ttu-id="db836-159">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="db836-159">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="db836-160">Kompiluje z określonym [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="db836-160">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="db836-161">Platformę musi być zdefiniowana w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="db836-161">The framework must be defined in the [project file](csproj.md).</span></span>

`-h|--help`

<span data-ttu-id="db836-162">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="db836-162">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="db836-163">Ignoruje odwołuje się do projektu do projektu (P2P) i tylko kompilacje główny projekt określony do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="db836-163">Ignores project-to-project (P2P) references and only builds the root project specified to build.</span></span>

`--no-incremental`

<span data-ttu-id="db836-164">Oznaczenie kompilacji jako niebezpieczny dla kompilacji przyrostowej.</span><span class="sxs-lookup"><span data-stu-id="db836-164">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="db836-165">To powoduje wyłączenie kompilacji przyrostowej i wymusza czystą kompilowania wykresu zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="db836-165">This turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="db836-166">Katalog, w którym można umieścić skompilowanych plików binarnych.</span><span class="sxs-lookup"><span data-stu-id="db836-166">Directory in which to place the built binaries.</span></span> <span data-ttu-id="db836-167">Należy również określić `--framework` po określeniu tej opcji.</span><span class="sxs-lookup"><span data-stu-id="db836-167">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="db836-168">Określa docelowe środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="db836-168">Specifies the target runtime.</span></span> <span data-ttu-id="db836-169">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="db836-169">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="db836-170">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="db836-170">Sets the verbosity level of the command.</span></span> <span data-ttu-id="db836-171">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="db836-171">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="db836-172">Określa sufiks wersji gwiazdkę (`*`) w polu wersja pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="db836-172">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="db836-173">Format jest zgodny wytyczne wersja narzędzia NuGet.</span><span class="sxs-lookup"><span data-stu-id="db836-173">The format follows NuGet's version guidelines.</span></span>

---

## <a name="examples"></a><span data-ttu-id="db836-174">Przykłady</span><span class="sxs-lookup"><span data-stu-id="db836-174">Examples</span></span>

<span data-ttu-id="db836-175">Tworzenie projektu i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="db836-175">Build a project and its dependencies:</span></span>

`dotnet build`

<span data-ttu-id="db836-176">Tworzenie projektu i jego zależności za pomocą wersji konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="db836-176">Build a project and its dependencies using Release configuration:</span></span>

`dotnet build --configuration Release`

<span data-ttu-id="db836-177">Tworzenie projektu i jego zależności dla określonego środowiska uruchomieniowego (w tym przykładzie Ubuntu 16.04):</span><span class="sxs-lookup"><span data-stu-id="db836-177">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 16.04):</span></span>

`dotnet build --runtime ubuntu.16.04-x64`