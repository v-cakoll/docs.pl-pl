---
title: polecenie kompilacji dotnet
description: Polecenie kompilacji dotnet kompiluje projekt i wszystkie jego zależności.
ms.date: 04/24/2019
ms.openlocfilehash: db2c859529d3dd21d2cd43445419b99a4256b42e
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331059"
---
# <a name="dotnet-build"></a><span data-ttu-id="dd370-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="dd370-103">dotnet build</span></span>

<span data-ttu-id="dd370-104">**Ten artykuł dotyczy: ✓** .NET Core 1. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="dd370-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="dd370-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="dd370-105">Name</span></span>

<span data-ttu-id="dd370-106">`dotnet build`-Kompiluje projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="dd370-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dd370-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="dd370-107">Synopsis</span></span>

```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--nologo] [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="dd370-108">Opis</span><span class="sxs-lookup"><span data-stu-id="dd370-108">Description</span></span>

<span data-ttu-id="dd370-109">`dotnet build` Polecenie kompiluje projekt i jego zależności do zestawu plików binarnych.</span><span class="sxs-lookup"><span data-stu-id="dd370-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="dd370-110">Pliki binarne zawierają kod projektu w plikach języka pośredniego (IL) z rozszerzeniem *. dll* i plikami symboli używanymi do debugowania z rozszerzeniem *. pdb* .</span><span class="sxs-lookup"><span data-stu-id="dd370-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="dd370-111">Tworzony jest plik JSON zależności ( *. deps. JSON*), który zawiera listę zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dd370-111">A dependencies JSON file (*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="dd370-112">Tworzony jest plik *. runtimeconfig. JSON* , który określa udostępnione środowisko uruchomieniowe i jego wersję dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dd370-112">A *.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="dd370-113">Jeśli projekt zawiera zależności innych firm, takie jak biblioteki z NuGet, są one rozpoznawane z pamięci podręcznej NuGet i nie są dostępne z skompilowanymi danymi wyjściowymi projektu.</span><span class="sxs-lookup"><span data-stu-id="dd370-113">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="dd370-114">Z tego względu `dotnet build` produkt nie jest gotowy do przeniesienia na inną maszynę do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="dd370-114">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="dd370-115">Jest to w przeciwieństwie do zachowania .NET Framework, w którym Kompilowanie projektu wykonywalnego (aplikacji) generuje dane wyjściowe, które są możliwy do uruchomienia na dowolnym komputerze, na którym zainstalowano .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dd370-115">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="dd370-116">Aby korzystać z podobnego środowiska z platformą .NET Core, należy użyć polecenia [dotnet Publish](dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="dd370-116">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="dd370-117">Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="dd370-117">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="dd370-118">Kompilowanie wymaga pliku *Project. assets. JSON* , który zawiera listę zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dd370-118">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="dd370-119">Plik jest tworzony, gdy [`dotnet restore`](dotnet-restore.md) jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="dd370-119">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="dd370-120">Bez pliku zasobów na miejscu narzędzia nie mogą rozpoznać zestawów referencyjnych, które powodują błędy.</span><span class="sxs-lookup"><span data-stu-id="dd370-120">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="dd370-121">Przy użyciu zestawu SDK platformy .NET Core 1. x należy jawnie uruchomić `dotnet restore` program przed uruchomieniem. `dotnet build`</span><span class="sxs-lookup"><span data-stu-id="dd370-121">With .NET Core 1.x SDK, you needed to explicitly run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="dd370-122">Począwszy od zestawu SDK platformy .NET Core `dotnet restore` 2,0, jest uruchamiany niejawnie podczas uruchamiania. `dotnet build`</span><span class="sxs-lookup"><span data-stu-id="dd370-122">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="dd370-123">Aby wyłączyć niejawne przywracanie podczas wykonywania polecenia Build, można przekazać `--no-restore` opcję.</span><span class="sxs-lookup"><span data-stu-id="dd370-123">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="dd370-124">Czy projekt jest plikiem wykonywalnym, czy nie jest określony `<OutputType>` przez właściwość w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="dd370-124">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="dd370-125">W poniższym przykładzie przedstawiono projekt tworzący kod wykonywalny:</span><span class="sxs-lookup"><span data-stu-id="dd370-125">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="dd370-126">Aby utworzyć bibliotekę, należy pominąć `<OutputType>` właściwość.</span><span class="sxs-lookup"><span data-stu-id="dd370-126">To produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="dd370-127">Główną różnicą w skompilowanych danych wyjściowych jest to, że biblioteka IL DLL biblioteki nie zawiera punktów wejścia i nie można jej wykonać.</span><span class="sxs-lookup"><span data-stu-id="dd370-127">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="dd370-128">MSBuild</span><span class="sxs-lookup"><span data-stu-id="dd370-128">MSBuild</span></span>

<span data-ttu-id="dd370-129">`dotnet build`używa programu MSBuild do skompilowania projektu, aby obsługiwał kompilacje równoległe i przyrostowe.</span><span class="sxs-lookup"><span data-stu-id="dd370-129">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="dd370-130">Aby uzyskać więcej informacji, [](/visualstudio/msbuild/incremental-builds)Zobacz Kompilacje przyrostowe.</span><span class="sxs-lookup"><span data-stu-id="dd370-130">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="dd370-131">Oprócz opcji, `dotnet build` polecenie akceptuje Opcje programu MSBuild, takie jak `-p` właściwości ustawienia lub `-l` definiowania rejestratora.</span><span class="sxs-lookup"><span data-stu-id="dd370-131">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="dd370-132">Aby uzyskać więcej informacji na temat tych opcji, zobacz [informacje dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="dd370-132">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="dd370-133">Lub można również użyć polecenia programu [dotnet MSBuild](dotnet-msbuild.md) .</span><span class="sxs-lookup"><span data-stu-id="dd370-133">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="dd370-134">Uruchomiona `dotnet build` jest równoważna `dotnet msbuild -restore -target:Build`z.</span><span class="sxs-lookup"><span data-stu-id="dd370-134">Running `dotnet build` is equivalent to `dotnet msbuild -restore -target:Build`.</span></span>

## <a name="arguments"></a><span data-ttu-id="dd370-135">Argumenty</span><span class="sxs-lookup"><span data-stu-id="dd370-135">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="dd370-136">Plik projektu lub rozwiązania do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="dd370-136">The project or solution file to build.</span></span> <span data-ttu-id="dd370-137">Jeśli plik projektu lub rozwiązania nie zostanie określony, program MSBuild przeszukuje bieżący katalog roboczy dla pliku, który ma rozszerzenie pliku, które kończy się w *proj* lub *sln* i używa tego pliku.</span><span class="sxs-lookup"><span data-stu-id="dd370-137">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="dd370-138">Opcje</span><span class="sxs-lookup"><span data-stu-id="dd370-138">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="dd370-139">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="dd370-139">Defines the build configuration.</span></span> <span data-ttu-id="dd370-140">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="dd370-140">The default value is `Debug`.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="dd370-141">Kompiluje dla określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="dd370-141">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="dd370-142">Struktura musi być zdefiniowana w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="dd370-142">The framework must be defined in the [project file](csproj.md).</span></span>

* **`--force`**

  <span data-ttu-id="dd370-143">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="dd370-143">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="dd370-144">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="dd370-144">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="dd370-145">Dostępne od wersji .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="dd370-145">Available since .NET Core 2.0 SDK.</span></span>

* **`-h|--help`**

  <span data-ttu-id="dd370-146">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="dd370-146">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="dd370-147">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję.</span><span class="sxs-lookup"><span data-stu-id="dd370-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="dd370-148">Na przykład, aby ukończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="dd370-148">For example, to complete authentication.</span></span> <span data-ttu-id="dd370-149">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="dd370-149">Available since .NET Core 3.0 SDK.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="dd370-150">Ignoruje odwołania między projektami i projektami (P2P) i kompiluje tylko określony projekt główny.</span><span class="sxs-lookup"><span data-stu-id="dd370-150">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="dd370-151">Oznacza kompilację jako niebezpieczną dla kompilacji przyrostowej.</span><span class="sxs-lookup"><span data-stu-id="dd370-151">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="dd370-152">Ta flaga powoduje wyłączenie kompilacji przyrostowej i wymuszenie czystej odbudowy wykresu zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="dd370-152">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`--no-logo`**

  <span data-ttu-id="dd370-153">Nie wyświetla transparentu początkowego ani komunikatu o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="dd370-153">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="dd370-154">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="dd370-154">Available since .NET Core 3.0 SDK.</span></span>

* **`--no-restore`**

  <span data-ttu-id="dd370-155">Nie wykonuje przywracania niejawnego podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="dd370-155">Doesn't execute an implicit restore during build.</span></span> <span data-ttu-id="dd370-156">Dostępne od wersji .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="dd370-156">Available since .NET Core 2.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="dd370-157">Katalog, w którym mają zostać umieszczone skompilowane pliki binarne.</span><span class="sxs-lookup"><span data-stu-id="dd370-157">Directory in which to place the built binaries.</span></span> <span data-ttu-id="dd370-158">Należy również zdefiniować `--framework` po określeniu tej opcji.</span><span class="sxs-lookup"><span data-stu-id="dd370-158">You also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="dd370-159">Jeśli nie zostanie określony, ścieżka domyślna to `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="dd370-159">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="dd370-160">Określa docelowy środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="dd370-160">Specifies the target runtime.</span></span> <span data-ttu-id="dd370-161">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="dd370-161">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="dd370-162">Ustawia poziom szczegółowości programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="dd370-162">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="dd370-163">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="dd370-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="dd370-164">Wartość domyślna to `minimal`.</span><span class="sxs-lookup"><span data-stu-id="dd370-164">The default is `minimal`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="dd370-165">Ustawia wartość `$(VersionSuffix)` właściwości, która ma być używana podczas kompilowania projektu.</span><span class="sxs-lookup"><span data-stu-id="dd370-165">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="dd370-166">Działa to tylko wtedy, `$(Version)` gdy właściwość nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="dd370-166">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="dd370-167">Następnie jest ustawiona `$(VersionPrefix)` na połączone z `$(VersionSuffix)`, oddzielone kreską. `$(Version)`</span><span class="sxs-lookup"><span data-stu-id="dd370-167">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="dd370-168">Przykłady</span><span class="sxs-lookup"><span data-stu-id="dd370-168">Examples</span></span>

* <span data-ttu-id="dd370-169">Kompiluj projekt i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="dd370-169">Build a project and its dependencies:</span></span>

  ```console
  dotnet build
  ```

* <span data-ttu-id="dd370-170">Kompilowanie projektu i jego zależności przy użyciu konfiguracji wydania:</span><span class="sxs-lookup"><span data-stu-id="dd370-170">Build a project and its dependencies using Release configuration:</span></span>

  ```console
  dotnet build --configuration Release
  ```

* <span data-ttu-id="dd370-171">Kompiluj projekt i jego zależności dla określonego środowiska uruchomieniowego (w tym przykładzie Ubuntu 18,04):</span><span class="sxs-lookup"><span data-stu-id="dd370-171">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```console
  dotnet build --runtime ubuntu.18.04-x64
  ```

* <span data-ttu-id="dd370-172">Kompiluj projekt i Użyj określonego źródła pakietu NuGet podczas operacji przywracania (zestaw .NET Core 2,0 SDK i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="dd370-172">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* <span data-ttu-id="dd370-173">Skompiluj projekt i ustaw wersję 1.2.3.4 jako parametr kompilacji przy użyciu `-p` [opcji MSBuild](#msbuild):</span><span class="sxs-lookup"><span data-stu-id="dd370-173">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```console
  dotnet build -p:Version=1.2.3.4
  ```
