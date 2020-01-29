---
title: polecenie kompilacji dotnet
description: Polecenie kompilacji dotnet kompiluje projekt i wszystkie jego zależności.
ms.date: 10/14/2019
ms.openlocfilehash: ec37d82c9e22a59acf7617f80a7491c0bcab89c9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734316"
---
# <a name="dotnet-build"></a><span data-ttu-id="5a2fc-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="5a2fc-103">dotnet build</span></span>

<span data-ttu-id="5a2fc-104">**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 1. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="5a2fc-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="5a2fc-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5a2fc-105">Name</span></span>

<span data-ttu-id="5a2fc-106">`dotnet build` — kompiluje projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5a2fc-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="5a2fc-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force]
    [--interactive] [--no-dependencies] [--no-incremental] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="5a2fc-108">Opis</span><span class="sxs-lookup"><span data-stu-id="5a2fc-108">Description</span></span>

<span data-ttu-id="5a2fc-109">`dotnet build` polecenie kompiluje projekt i jego zależności do zestawu plików binarnych.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="5a2fc-110">Pliki binarne zawierają kod projektu w plikach języka pośredniego (IL) z rozszerzeniem *. dll* .</span><span class="sxs-lookup"><span data-stu-id="5a2fc-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension.</span></span>  <span data-ttu-id="5a2fc-111">W zależności od typu projektu i ustawień można uwzględnić inne pliki, takie jak:</span><span class="sxs-lookup"><span data-stu-id="5a2fc-111">Depending on the project type and settings, other files may be included, such as:</span></span>

- <span data-ttu-id="5a2fc-112">Plik wykonywalny, który może służyć do uruchamiania aplikacji, jeśli typem projektu jest plik wykonywalny przeznaczony dla platformy .NET Core 3,0 lub nowszego.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-112">An executable that can be used to run the application, if the project type is an executable targeting .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="5a2fc-113">Pliki symboli używane do debugowania z rozszerzeniem *. pdb* .</span><span class="sxs-lookup"><span data-stu-id="5a2fc-113">Symbol files used for debugging with a *.pdb* extension.</span></span>
- <span data-ttu-id="5a2fc-114">Plik *. deps. JSON* , który zawiera listę zależności aplikacji lub biblioteki.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-114">A *.deps.json* file, which lists the dependencies of the application or library.</span></span>
- <span data-ttu-id="5a2fc-115">Plik *. runtimeconfig. JSON* , który określa udostępnione środowisko uruchomieniowe i jego wersję dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-115">A *.runtimeconfig.json* file, which specifies the shared runtime and its version for an application.</span></span>
- <span data-ttu-id="5a2fc-116">Inne biblioteki, od których zależy projekt (za pośrednictwem odwołań projektu lub pakietów NuGet).</span><span class="sxs-lookup"><span data-stu-id="5a2fc-116">Other libraries that the project depends on (via project references or NuGet package references).</span></span>

<span data-ttu-id="5a2fc-117">W przypadku projektów wykonywalnych przeznaczonych dla wersji wcześniejszej niż .NET Core 3,0, zależności biblioteki z NuGet nie są zwykle kopiowane do folderu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-117">For executable projects targeting versions earlier than .NET Core 3.0, library dependencies from NuGet are typically NOT copied to the output folder.</span></span>  <span data-ttu-id="5a2fc-118">Są one rozpoznawane z folderu pakietów globalnych NuGet w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-118">They're resolved from the NuGet global packages folder at run time.</span></span> <span data-ttu-id="5a2fc-119">Z tego względu produkt `dotnet build` nie jest gotowy do przeniesienia na inną maszynę do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-119">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="5a2fc-120">Aby utworzyć wersję aplikacji, którą można wdrożyć, należy ją opublikować (na przykład przy użyciu polecenia [dotnet Publish](dotnet-publish.md) ).</span><span class="sxs-lookup"><span data-stu-id="5a2fc-120">To create a version of the application that can be deployed, you need to publish it (for example, with the [dotnet publish](dotnet-publish.md) command).</span></span> <span data-ttu-id="5a2fc-121">Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="5a2fc-121">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="5a2fc-122">W przypadku projektów wykonywalnych przeznaczonych dla platformy .NET Core 3,0 i nowszych zależności biblioteki są kopiowane do folderu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-122">For executable projects targeting .NET Core 3.0 and later, library dependencies are copied to the output folder.</span></span> <span data-ttu-id="5a2fc-123">Oznacza to, że jeśli nie ma żadnej innej logiki specyficznej dla publikacji (takiej jak projekty sieci Web), dane wyjściowe kompilacji powinny być możliwe do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-123">This means that if there isn't any other publish-specific logic (such as Web projects have), the build output should be deployable.</span></span>

<span data-ttu-id="5a2fc-124">Kompilowanie wymaga pliku *Project. assets. JSON* , który zawiera listę zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-124">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="5a2fc-125">Plik jest tworzony podczas wykonywania [`dotnet restore`](dotnet-restore.md) .</span><span class="sxs-lookup"><span data-stu-id="5a2fc-125">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="5a2fc-126">Bez pliku zasobów na miejscu narzędzia nie mogą rozpoznać zestawów referencyjnych, które powodują błędy.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-126">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="5a2fc-127">Przy użyciu zestawu SDK platformy .NET Core 1. x musisz jawnie uruchomić `dotnet restore` przed uruchomieniem `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-127">With .NET Core 1.x SDK, you needed to explicitly run `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="5a2fc-128">Począwszy od zestawu SDK programu .NET Core 2,0, `dotnet restore` uruchamiane niejawnie podczas uruchamiania `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-128">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="5a2fc-129">Aby wyłączyć niejawne przywracanie podczas wykonywania polecenia Build, można przekazać opcję `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-129">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="5a2fc-130">Czy projekt jest plikiem wykonywalnym, czy nie jest określony przez właściwość `<OutputType>` w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-130">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="5a2fc-131">W poniższym przykładzie przedstawiono projekt tworzący kod wykonywalny:</span><span class="sxs-lookup"><span data-stu-id="5a2fc-131">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="5a2fc-132">Aby utworzyć bibliotekę, Pomiń Właściwość `<OutputType>` lub zmień jej wartość na `Library`.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-132">To produce a library, omit the `<OutputType>` property or change its value to `Library`.</span></span> <span data-ttu-id="5a2fc-133">Biblioteka DLL IL dla biblioteki nie zawiera punktów wejścia i nie można jej wykonać.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-133">The IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="5a2fc-134">MSBuild</span><span class="sxs-lookup"><span data-stu-id="5a2fc-134">MSBuild</span></span>

<span data-ttu-id="5a2fc-135">`dotnet build` używa programu MSBuild do kompilowania projektu, aby obsługiwał kompilacje równoległe i przyrostowe.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-135">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="5a2fc-136">Aby uzyskać więcej informacji, Zobacz [Kompilacje przyrostowe](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="5a2fc-136">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="5a2fc-137">Oprócz opcji, polecenie `dotnet build` akceptuje Opcje programu MSBuild, takie jak `-p` do ustawiania właściwości lub `-l` w celu zdefiniowania rejestratora.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-137">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="5a2fc-138">Aby uzyskać więcej informacji na temat tych opcji, zobacz [informacje dotyczące wiersza polecenia programu MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="5a2fc-138">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="5a2fc-139">Lub można również użyć polecenia programu [dotnet MSBuild](dotnet-msbuild.md) .</span><span class="sxs-lookup"><span data-stu-id="5a2fc-139">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="5a2fc-140">Uruchamianie `dotnet build` jest równoważne działaniu `dotnet msbuild -restore`; jednak domyślny poziom szczegółowości danych wyjściowych jest inny.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-140">Running `dotnet build` is equivalent to running `dotnet msbuild -restore`; however, the default verbosity of the output is different.</span></span>

## <a name="arguments"></a><span data-ttu-id="5a2fc-141">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5a2fc-141">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="5a2fc-142">Plik projektu lub rozwiązania do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-142">The project or solution file to build.</span></span> <span data-ttu-id="5a2fc-143">Jeśli plik projektu lub rozwiązania nie zostanie określony, program MSBuild przeszukuje bieżący katalog roboczy dla pliku, który ma rozszerzenie pliku, które kończy się w *proj* lub *sln* i używa tego pliku.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-143">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="5a2fc-144">Opcje</span><span class="sxs-lookup"><span data-stu-id="5a2fc-144">Options</span></span>

- **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="5a2fc-145">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-145">Defines the build configuration.</span></span> <span data-ttu-id="5a2fc-146">Wartość domyślna dla większości projektów jest `Debug`, ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-146">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="5a2fc-147">Kompiluje dla określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="5a2fc-147">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="5a2fc-148">Struktura musi być zdefiniowana w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="5a2fc-148">The framework must be defined in the [project file](csproj.md).</span></span>

- **`--force`**

  <span data-ttu-id="5a2fc-149">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-149">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="5a2fc-150">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="5a2fc-150">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="5a2fc-151">Dostępne od wersji .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-151">Available since .NET Core 2.0 SDK.</span></span>

- **`-h|--help`**

  <span data-ttu-id="5a2fc-152">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-152">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="5a2fc-153">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-153">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="5a2fc-154">Na przykład, aby ukończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-154">For example, to complete authentication.</span></span> <span data-ttu-id="5a2fc-155">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="5a2fc-156">Ignoruje odwołania między projektami i projektami (P2P) i kompiluje tylko określony projekt główny.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-156">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

- **`--no-incremental`**

  <span data-ttu-id="5a2fc-157">Oznacza kompilację jako niebezpieczną dla kompilacji przyrostowej.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-157">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="5a2fc-158">Ta flaga powoduje wyłączenie kompilacji przyrostowej i wymuszenie czystej odbudowy wykresu zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-158">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

- **`--no-restore`**

  <span data-ttu-id="5a2fc-159">Nie wykonuje przywracania niejawnego podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-159">Doesn't execute an implicit restore during build.</span></span> <span data-ttu-id="5a2fc-160">Dostępne od wersji .NET Core 2,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-160">Available since .NET Core 2.0 SDK.</span></span>

- **`--nologo`**

  <span data-ttu-id="5a2fc-161">Nie wyświetla transparentu początkowego ani komunikatu o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-161">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="5a2fc-162">Dostępne od wersji .NET Core 3,0 SDK.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-162">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="5a2fc-163">Katalog, w którym mają zostać umieszczone skompilowane pliki binarne.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-163">Directory in which to place the built binaries.</span></span> <span data-ttu-id="5a2fc-164">Jeśli nie zostanie określony, domyślną ścieżką jest `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-164">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="5a2fc-165">W przypadku projektów z wieloma platformami docelowymi (za pomocą właściwości `TargetFrameworks`) należy również zdefiniować `--framework` po określeniu tej opcji.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-165">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="5a2fc-166">Określa docelowy środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-166">Specifies the target runtime.</span></span> <span data-ttu-id="5a2fc-167">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="5a2fc-167">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="5a2fc-168">Ustawia poziom szczegółowości programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-168">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="5a2fc-169">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="5a2fc-170">Wartość domyślna to `minimal`.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-170">The default is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="5a2fc-171">Ustawia wartość właściwości `$(VersionSuffix)`, która ma być używana podczas kompilowania projektu.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-171">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="5a2fc-172">Działa to tylko wtedy, gdy właściwość `$(Version)` nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-172">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="5a2fc-173">Następnie `$(Version)` jest ustawiony na `$(VersionPrefix)` połączony z `$(VersionSuffix)`rozdzielony kreską.</span><span class="sxs-lookup"><span data-stu-id="5a2fc-173">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="5a2fc-174">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5a2fc-174">Examples</span></span>

- <span data-ttu-id="5a2fc-175">Kompiluj projekt i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="5a2fc-175">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

- <span data-ttu-id="5a2fc-176">Kompilowanie projektu i jego zależności przy użyciu konfiguracji wydania:</span><span class="sxs-lookup"><span data-stu-id="5a2fc-176">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

- <span data-ttu-id="5a2fc-177">Kompiluj projekt i jego zależności dla określonego środowiska uruchomieniowego (w tym przykładzie Ubuntu 18,04):</span><span class="sxs-lookup"><span data-stu-id="5a2fc-177">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- <span data-ttu-id="5a2fc-178">Kompiluj projekt i Użyj określonego źródła pakietu NuGet podczas operacji przywracania (zestaw .NET Core 2,0 SDK i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="5a2fc-178">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- <span data-ttu-id="5a2fc-179">Skompiluj projekt i ustaw wersję 1.2.3.4 jako parametr kompilacji przy użyciu [opcji `-p` MSBuild](#msbuild):</span><span class="sxs-lookup"><span data-stu-id="5a2fc-179">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
