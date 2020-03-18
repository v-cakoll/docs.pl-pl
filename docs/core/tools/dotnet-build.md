---
title: polecenie dotnet build
description: Polecenie kompilacji dotnet tworzy projekt i wszystkie jego zależności.
ms.date: 02/14/2020
ms.openlocfilehash: 9f9a78ec0a6a25c54c8a727c05081ce6835514ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503765"
---
# <a name="dotnet-build"></a><span data-ttu-id="72c3f-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="72c3f-103">dotnet build</span></span>

<span data-ttu-id="72c3f-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="72c3f-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="72c3f-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="72c3f-105">Name</span></span>

<span data-ttu-id="72c3f-106">`dotnet build`- Buduje projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="72c3f-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="72c3f-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="72c3f-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force]
    [--interactive] [--no-dependencies] [--no-incremental] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="72c3f-108">Opis</span><span class="sxs-lookup"><span data-stu-id="72c3f-108">Description</span></span>

<span data-ttu-id="72c3f-109">Polecenie `dotnet build` tworzy projekt i jego zależności w zestaw plików binarnych.</span><span class="sxs-lookup"><span data-stu-id="72c3f-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="72c3f-110">Pliki binarne zawierają kod projektu w plikach il (Intermediate Language) z rozszerzeniem *dll.*</span><span class="sxs-lookup"><span data-stu-id="72c3f-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension.</span></span>  <span data-ttu-id="72c3f-111">W zależności od typu i ustawień projektu mogą być dołączone inne pliki, takie jak:</span><span class="sxs-lookup"><span data-stu-id="72c3f-111">Depending on the project type and settings, other files may be included, such as:</span></span>

- <span data-ttu-id="72c3f-112">Plik wykonywalny, który może służyć do uruchamiania aplikacji, jeśli typ projektu jest wykonywalnym kierowaniem .NET Core 3.0 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="72c3f-112">An executable that can be used to run the application, if the project type is an executable targeting .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="72c3f-113">Pliki symboli używane do debugowania z rozszerzeniem *pdb.*</span><span class="sxs-lookup"><span data-stu-id="72c3f-113">Symbol files used for debugging with a *.pdb* extension.</span></span>
- <span data-ttu-id="72c3f-114">Plik *.deps.json,* który zawiera listę zależności aplikacji lub biblioteki.</span><span class="sxs-lookup"><span data-stu-id="72c3f-114">A *.deps.json* file, which lists the dependencies of the application or library.</span></span>
- <span data-ttu-id="72c3f-115">Plik *.runtimeconfig.json,* który określa udostępniony czas wykonywania i jego wersję dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="72c3f-115">A *.runtimeconfig.json* file, which specifies the shared runtime and its version for an application.</span></span>
- <span data-ttu-id="72c3f-116">Inne biblioteki, od których zależy projekt (za pośrednictwem odwołań do projektu lub odwołań do pakietu NuGet).</span><span class="sxs-lookup"><span data-stu-id="72c3f-116">Other libraries that the project depends on (via project references or NuGet package references).</span></span>

<span data-ttu-id="72c3f-117">W przypadku projektów wykonywalnych przeznaczonych dla wersji wcześniejszych niż .NET Core 3.0 zależności biblioteki z NuGet zazwyczaj NIE są kopiowane do folderu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="72c3f-117">For executable projects targeting versions earlier than .NET Core 3.0, library dependencies from NuGet are typically NOT copied to the output folder.</span></span>  <span data-ttu-id="72c3f-118">Są one rozwiązywane z nuget folderu pakietów globalnych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="72c3f-118">They're resolved from the NuGet global packages folder at run time.</span></span> <span data-ttu-id="72c3f-119">Mając to na uwadze, `dotnet build` produkt nie jest gotowy do przeniesienia na inną maszynę do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="72c3f-119">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="72c3f-120">Aby utworzyć wersję aplikacji, która może być wdrożona, należy ją opublikować (na przykład [poleceniem publikowania dotnet).](dotnet-publish.md)</span><span class="sxs-lookup"><span data-stu-id="72c3f-120">To create a version of the application that can be deployed, you need to publish it (for example, with the [dotnet publish](dotnet-publish.md) command).</span></span> <span data-ttu-id="72c3f-121">Aby uzyskać więcej informacji, zobacz [.NET Core Application Deployment](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="72c3f-121">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="72c3f-122">W przypadku projektów wykonywalnych przeznaczonych na program .NET Core 3.0 i nowszych zależności biblioteki są kopiowane do folderu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="72c3f-122">For executable projects targeting .NET Core 3.0 and later, library dependencies are copied to the output folder.</span></span> <span data-ttu-id="72c3f-123">Oznacza to, że jeśli nie ma żadnej innej logiki specyficzne dla publikowania (takich jak projekty sieci Web mają), dane wyjściowe kompilacji powinny być wdrażalne.</span><span class="sxs-lookup"><span data-stu-id="72c3f-123">This means that if there isn't any other publish-specific logic (such as Web projects have), the build output should be deployable.</span></span>

<span data-ttu-id="72c3f-124">Tworzenie wymaga pliku *project.assets.json,* który zawiera listę zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="72c3f-124">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="72c3f-125">Plik jest tworzony [`dotnet restore`](dotnet-restore.md) podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="72c3f-125">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="72c3f-126">Bez pliku zasobów w miejscu, narzędzia nie można rozwiązać zestawy odwołań, co powoduje błędy.</span><span class="sxs-lookup"><span data-stu-id="72c3f-126">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="72c3f-127">W przypadku sdk .NET Core 1.x `dotnet restore` należy `dotnet build`jawnie uruchomić przed uruchomieniem .</span><span class="sxs-lookup"><span data-stu-id="72c3f-127">With .NET Core 1.x SDK, you needed to explicitly run `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="72c3f-128">Począwszy od .NET Core 2.0 `dotnet restore` SDK, `dotnet build`jest uruchamiany niejawnie po uruchomieniu .</span><span class="sxs-lookup"><span data-stu-id="72c3f-128">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="72c3f-129">Jeśli chcesz wyłączyć przywracanie niejawne podczas uruchamiania `--no-restore` polecenia kompilacji, możesz przekazać tę opcję.</span><span class="sxs-lookup"><span data-stu-id="72c3f-129">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="72c3f-130">Określa, czy projekt jest wykonywalny, `<OutputType>` czy nie, jest określana przez właściwość w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="72c3f-130">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="72c3f-131">W poniższym przykładzie przedstawiono projekt, który tworzy kod wykonywalny:</span><span class="sxs-lookup"><span data-stu-id="72c3f-131">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="72c3f-132">Aby utworzyć bibliotekę, `<OutputType>` pomiń właściwość `Library`lub zmień jej wartość na .</span><span class="sxs-lookup"><span data-stu-id="72c3f-132">To produce a library, omit the `<OutputType>` property or change its value to `Library`.</span></span> <span data-ttu-id="72c3f-133">Biblioteka IL dla biblioteki nie zawiera punktów wejścia i nie można jej wykonać.</span><span class="sxs-lookup"><span data-stu-id="72c3f-133">The IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="72c3f-134">MSBuild</span><span class="sxs-lookup"><span data-stu-id="72c3f-134">MSBuild</span></span>

<span data-ttu-id="72c3f-135">`dotnet build`używa MSBuild do tworzenia projektu, więc obsługuje kompilacje równoległe i przyrostowe.</span><span class="sxs-lookup"><span data-stu-id="72c3f-135">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="72c3f-136">Aby uzyskać więcej informacji, zobacz [Kompilacje przyrostowe](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="72c3f-136">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="72c3f-137">Oprócz opcji `dotnet build` polecenie akceptuje opcje MSBuild, takie `-p` jak ustawianie `-l` właściwości lub definiowanie rejestratora.</span><span class="sxs-lookup"><span data-stu-id="72c3f-137">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="72c3f-138">Aby uzyskać więcej informacji na temat tych opcji, zobacz [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="72c3f-138">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="72c3f-139">Można też użyć polecenia [dotnet msbuild.](dotnet-msbuild.md)</span><span class="sxs-lookup"><span data-stu-id="72c3f-139">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="72c3f-140">Uruchamianie `dotnet build` jest `dotnet msbuild -restore`równoznaczne z bieganiem; jednak domyślna szczegółowość danych wyjściowych jest inna.</span><span class="sxs-lookup"><span data-stu-id="72c3f-140">Running `dotnet build` is equivalent to running `dotnet msbuild -restore`; however, the default verbosity of the output is different.</span></span>

## <a name="arguments"></a><span data-ttu-id="72c3f-141">Argumenty</span><span class="sxs-lookup"><span data-stu-id="72c3f-141">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="72c3f-142">Projekt lub plik rozwiązania do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="72c3f-142">The project or solution file to build.</span></span> <span data-ttu-id="72c3f-143">Jeśli plik projektu lub rozwiązania nie jest określony, MSBuild przeszukuje bieżący katalog roboczy dla pliku, który ma rozszerzenie pliku, który kończy się *proj* lub *sln* i używa tego pliku.</span><span class="sxs-lookup"><span data-stu-id="72c3f-143">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="72c3f-144">Opcje</span><span class="sxs-lookup"><span data-stu-id="72c3f-144">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="72c3f-145">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="72c3f-145">Defines the build configuration.</span></span> <span data-ttu-id="72c3f-146">Wartość domyślna dla `Debug`większości projektów jest , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="72c3f-146">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="72c3f-147">Kompiluje dla określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="72c3f-147">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="72c3f-148">Struktura musi być zdefiniowana w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="72c3f-148">The framework must be defined in the [project file](csproj.md).</span></span>

- **`--force`**

  <span data-ttu-id="72c3f-149">Wymusza rozwiązywanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="72c3f-149">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="72c3f-150">Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="72c3f-150">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="72c3f-151">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="72c3f-151">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="72c3f-152">Umożliwia zatrzymanie polecenia i oczekiwanie na wejście użytkownika lub akcję.</span><span class="sxs-lookup"><span data-stu-id="72c3f-152">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="72c3f-153">Na przykład, aby zakończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="72c3f-153">For example, to complete authentication.</span></span> <span data-ttu-id="72c3f-154">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="72c3f-154">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="72c3f-155">Ignoruje odwołania projektu do projektu (P2P) i tworzy tylko określony projekt główny.</span><span class="sxs-lookup"><span data-stu-id="72c3f-155">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

- **`--no-incremental`**

  <span data-ttu-id="72c3f-156">Oznacza kompilację jako niebezpieczną dla kompilacji przyrostowej.</span><span class="sxs-lookup"><span data-stu-id="72c3f-156">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="72c3f-157">Ta flaga wyłącza kompilację przyrostową i wymusza czystą odbudowę wykresu zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="72c3f-157">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

- **`--no-restore`**

  <span data-ttu-id="72c3f-158">Nie wykonuje przywracania niejawnego podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="72c3f-158">Doesn't execute an implicit restore during build.</span></span>

- **`--nologo`**

  <span data-ttu-id="72c3f-159">Nie wyświetla banera startowego ani wiadomości o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="72c3f-159">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="72c3f-160">Dostępne od sdk .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="72c3f-160">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="72c3f-161">Katalog, w którym mają być umieszczane wbudowane pliki binarne.</span><span class="sxs-lookup"><span data-stu-id="72c3f-161">Directory in which to place the built binaries.</span></span> <span data-ttu-id="72c3f-162">Jeśli nie zostanie określony, `./bin/<configuration>/<framework>/`ścieżka domyślna to .</span><span class="sxs-lookup"><span data-stu-id="72c3f-162">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="72c3f-163">W przypadku projektów z wieloma `TargetFrameworks` platformami docelowymi (za pośrednictwem właściwości) należy również zdefiniować `--framework` po określeniu tej opcji.</span><span class="sxs-lookup"><span data-stu-id="72c3f-163">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="72c3f-164">Określa docelowy czas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="72c3f-164">Specifies the target runtime.</span></span> <span data-ttu-id="72c3f-165">Aby uzyskać listę identyfikatorów runtime (RID), zobacz [katalog RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="72c3f-165">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="72c3f-166">Ustawia poziom szczegółowości MSBuild.</span><span class="sxs-lookup"><span data-stu-id="72c3f-166">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="72c3f-167">Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .</span><span class="sxs-lookup"><span data-stu-id="72c3f-167">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="72c3f-168">Wartość domyślna to `minimal`.</span><span class="sxs-lookup"><span data-stu-id="72c3f-168">The default is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="72c3f-169">Ustawia wartość właściwości `$(VersionSuffix)` do użycia podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="72c3f-169">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="72c3f-170">To działa tylko `$(Version)` wtedy, gdy właściwość nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="72c3f-170">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="72c3f-171">Następnie `$(Version)` jest ustawiony `$(VersionPrefix)` na połączone `$(VersionSuffix)`z , oddzielone kreską.</span><span class="sxs-lookup"><span data-stu-id="72c3f-171">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="72c3f-172">Przykłady</span><span class="sxs-lookup"><span data-stu-id="72c3f-172">Examples</span></span>

- <span data-ttu-id="72c3f-173">Tworzenie projektu i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="72c3f-173">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

- <span data-ttu-id="72c3f-174">Tworzenie projektu i jego zależności przy użyciu konfiguracji wersji:</span><span class="sxs-lookup"><span data-stu-id="72c3f-174">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

- <span data-ttu-id="72c3f-175">Tworzenie projektu i jego zależności dla określonego czasu wykonywania (w tym przykładzie Ubuntu 18.04):</span><span class="sxs-lookup"><span data-stu-id="72c3f-175">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- <span data-ttu-id="72c3f-176">Skompiluj projekt i użyj określonego źródła pakietu NuGet podczas operacji przywracania (.NET Core 2.0 SDK i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="72c3f-176">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- <span data-ttu-id="72c3f-177">Zbuduj projekt i ustaw wersję 1.2.3.4 jako parametr kompilacji przy użyciu `-p` opcji [MSBuild:](#msbuild)</span><span class="sxs-lookup"><span data-stu-id="72c3f-177">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
