---
title: polecenie kompilacji dotnet
description: Polecenie kompilacji dotnet tworzy projekt i wszystkie jego zależności.
ms.date: 02/14/2020
ms.openlocfilehash: 1022df059493c7e045f81d4be93dff2fdab77eb1
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102843"
---
# <a name="dotnet-build"></a><span data-ttu-id="c874c-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="c874c-103">dotnet build</span></span>

<span data-ttu-id="c874c-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.x SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="c874c-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c874c-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c874c-105">Name</span></span>

<span data-ttu-id="c874c-106">`dotnet build`- Buduje projekt i wszystkie jego zależności.</span><span class="sxs-lookup"><span data-stu-id="c874c-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c874c-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="c874c-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet build -h|--help
```

## <a name="description"></a><span data-ttu-id="c874c-108">Opis</span><span class="sxs-lookup"><span data-stu-id="c874c-108">Description</span></span>

<span data-ttu-id="c874c-109">Polecenie `dotnet build` tworzy projekt i jego zależności do zestawu plików binarnych.</span><span class="sxs-lookup"><span data-stu-id="c874c-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="c874c-110">Pliki binarne zawierają kod projektu w plikach języka pośredniego (IL) z rozszerzeniem *.dll.*</span><span class="sxs-lookup"><span data-stu-id="c874c-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension.</span></span>  <span data-ttu-id="c874c-111">W zależności od typu projektu i ustawień mogą zostać dołączone inne pliki, takie jak:</span><span class="sxs-lookup"><span data-stu-id="c874c-111">Depending on the project type and settings, other files may be included, such as:</span></span>

- <span data-ttu-id="c874c-112">Plik wykonywalny, który może służyć do uruchamiania aplikacji, jeśli typ projektu jest wykonywalnym kierowaniem .NET Core 3.0 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="c874c-112">An executable that can be used to run the application, if the project type is an executable targeting .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="c874c-113">Pliki symboli używane do debugowania z rozszerzeniem *pdb.*</span><span class="sxs-lookup"><span data-stu-id="c874c-113">Symbol files used for debugging with a *.pdb* extension.</span></span>
- <span data-ttu-id="c874c-114">Plik *deps.json,* który wyświetla listę zależności aplikacji lub biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c874c-114">A *.deps.json* file, which lists the dependencies of the application or library.</span></span>
- <span data-ttu-id="c874c-115">Plik *.runtimeconfig.json,* który określa udostępnione środowisko uruchomieniowe i jego wersję dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c874c-115">A *.runtimeconfig.json* file, which specifies the shared runtime and its version for an application.</span></span>
- <span data-ttu-id="c874c-116">Inne biblioteki, od których zależy projekt (za pośrednictwem odwołań do projektu lub odwołań do pakietu NuGet).</span><span class="sxs-lookup"><span data-stu-id="c874c-116">Other libraries that the project depends on (via project references or NuGet package references).</span></span>

<span data-ttu-id="c874c-117">W przypadku projektów wykonywalnych przeznaczonych dla wersji wcześniejszych niż .NET Core 3.0 zależności biblioteki z NuGet zazwyczaj NIE są kopiowane do folderu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="c874c-117">For executable projects targeting versions earlier than .NET Core 3.0, library dependencies from NuGet are typically NOT copied to the output folder.</span></span>  <span data-ttu-id="c874c-118">Są one rozpoznawane z folderu pakietów globalnych NuGet w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c874c-118">They're resolved from the NuGet global packages folder at run time.</span></span> <span data-ttu-id="c874c-119">Mając to na uwadze, `dotnet build` produkt nie jest gotowy do przeniesienia na inną maszynę do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="c874c-119">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="c874c-120">Aby utworzyć wersję aplikacji, która może być wdrożona, należy ją opublikować (na przykład za pomocą polecenia [publikowania dotnet).](dotnet-publish.md)</span><span class="sxs-lookup"><span data-stu-id="c874c-120">To create a version of the application that can be deployed, you need to publish it (for example, with the [dotnet publish](dotnet-publish.md) command).</span></span> <span data-ttu-id="c874c-121">Aby uzyskać więcej informacji, zobacz [.NET Core Application Deployment](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="c874c-121">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="c874c-122">W przypadku projektów wykonywalnych przeznaczonych dla platformy .NET Core 3.0 lub nowszych zależności biblioteki są kopiowane do folderu wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="c874c-122">For executable projects targeting .NET Core 3.0 and later, library dependencies are copied to the output folder.</span></span> <span data-ttu-id="c874c-123">Oznacza to, że jeśli nie ma żadnej innej logiki specyficzne dla publikowania (takich jak projekty sieci Web), dane wyjściowe kompilacji powinny być wdrażalne.</span><span class="sxs-lookup"><span data-stu-id="c874c-123">This means that if there isn't any other publish-specific logic (such as Web projects have), the build output should be deployable.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="c874c-124">Niejawne przywracanie</span><span class="sxs-lookup"><span data-stu-id="c874c-124">Implicit restore</span></span>

<span data-ttu-id="c874c-125">Tworzenie wymaga pliku *project.assets.json,* który zawiera listę zależności aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c874c-125">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="c874c-126">Plik jest tworzony [`dotnet restore`](dotnet-restore.md) podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c874c-126">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="c874c-127">Bez pliku zasobów w miejscu narzędzia nie można rozpoznać zestawów odwołań, co powoduje błędy.</span><span class="sxs-lookup"><span data-stu-id="c874c-127">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

### <a name="executable-or-library-output"></a><span data-ttu-id="c874c-128">Dane wykonywalne lub dane wyjściowe biblioteki</span><span class="sxs-lookup"><span data-stu-id="c874c-128">Executable or library output</span></span>

<span data-ttu-id="c874c-129">Określana przez `<OutputType>` właściwość w pliku projektu, czy projekt jest wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="c874c-129">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="c874c-130">W poniższym przykładzie pokazano projekt, który tworzy kod wykonywalny:</span><span class="sxs-lookup"><span data-stu-id="c874c-130">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="c874c-131">Aby utworzyć bibliotekę, `<OutputType>` pomiń właściwość `Library`lub zmień jej wartość na .</span><span class="sxs-lookup"><span data-stu-id="c874c-131">To produce a library, omit the `<OutputType>` property or change its value to `Library`.</span></span> <span data-ttu-id="c874c-132">Biblioteka DLL IL dla biblioteki nie zawiera punktów wejścia i nie może być wykonana.</span><span class="sxs-lookup"><span data-stu-id="c874c-132">The IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="c874c-133">MSBuild</span><span class="sxs-lookup"><span data-stu-id="c874c-133">MSBuild</span></span>

<span data-ttu-id="c874c-134">`dotnet build`używa MSBuild do tworzenia projektu, więc obsługuje zarówno równoległe, jak i przyrostowe kompilacje.</span><span class="sxs-lookup"><span data-stu-id="c874c-134">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="c874c-135">Aby uzyskać więcej informacji, zobacz [Kompilacje przyrostowe](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="c874c-135">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="c874c-136">Oprócz opcji `dotnet build` polecenie akceptuje opcje MSBuild, takie `-p` jak ustawienie właściwości `-l` lub zdefiniowanie rejestratora.</span><span class="sxs-lookup"><span data-stu-id="c874c-136">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="c874c-137">Aby uzyskać więcej informacji na temat tych opcji, zobacz [odwołanie do wiersza polecenia MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="c874c-137">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="c874c-138">Można też użyć polecenia [dotnet msbuild.](dotnet-msbuild.md)</span><span class="sxs-lookup"><span data-stu-id="c874c-138">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="c874c-139">Bieganie `dotnet build` jest `dotnet msbuild -restore`równoznaczne z bieganiem; jednak domyślna szczegółowość danych wyjściowych jest inna.</span><span class="sxs-lookup"><span data-stu-id="c874c-139">Running `dotnet build` is equivalent to running `dotnet msbuild -restore`; however, the default verbosity of the output is different.</span></span>

## <a name="arguments"></a><span data-ttu-id="c874c-140">Argumenty</span><span class="sxs-lookup"><span data-stu-id="c874c-140">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="c874c-141">Plik projektu lub rozwiązania do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="c874c-141">The project or solution file to build.</span></span> <span data-ttu-id="c874c-142">Jeśli plik projektu lub rozwiązania nie jest określony, MSBuild przeszukuje bieżący katalog roboczy dla pliku, który ma rozszerzenie pliku, który kończy się *proj* lub *sln* i używa tego pliku.</span><span class="sxs-lookup"><span data-stu-id="c874c-142">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="c874c-143">Opcje</span><span class="sxs-lookup"><span data-stu-id="c874c-143">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="c874c-144">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c874c-144">Defines the build configuration.</span></span> <span data-ttu-id="c874c-145">Wartość domyślna dla `Debug`większości projektów to , ale można zastąpić ustawienia konfiguracji kompilacji w projekcie.</span><span class="sxs-lookup"><span data-stu-id="c874c-145">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="c874c-146">Kompiluje dla określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="c874c-146">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="c874c-147">Struktura musi być zdefiniowana w [pliku projektu](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="c874c-147">The framework must be defined in the [project file](csproj.md).</span></span>

- **`--force`**

  <span data-ttu-id="c874c-148">Wymusza wszystkie zależności do rozwiązania, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c874c-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="c874c-149">Określenie tej flagi jest takie samo jak usunięcie pliku *project.assets.json.*</span><span class="sxs-lookup"><span data-stu-id="c874c-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c874c-150">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="c874c-150">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="c874c-151">Umożliwia zatrzymywania polecenia i oczekiwania na dane wejściowe lub akcję użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c874c-151">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="c874c-152">Na przykład, aby zakończyć uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="c874c-152">For example, to complete authentication.</span></span> <span data-ttu-id="c874c-153">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c874c-153">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="c874c-154">Ignoruje odwołania do projektu do projektu (P2P) i tworzy tylko określony projekt główny.</span><span class="sxs-lookup"><span data-stu-id="c874c-154">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

- **`--no-incremental`**

  <span data-ttu-id="c874c-155">Oznacza kompilacji jako niebezpieczne dla kompilacji przyrostowej.</span><span class="sxs-lookup"><span data-stu-id="c874c-155">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="c874c-156">Ta flaga wyłącza kompilacji przyrostowej i wymusza czyste odbudowanie wykresu zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="c874c-156">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

- **`--no-restore`**

  <span data-ttu-id="c874c-157">Nie wykonuje niejawnego przywracania podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="c874c-157">Doesn't execute an implicit restore during build.</span></span>

- **`--nologo`**

  <span data-ttu-id="c874c-158">Nie wyświetla banera startowego ani wiadomości o prawach autorskich.</span><span class="sxs-lookup"><span data-stu-id="c874c-158">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="c874c-159">Dostępne od .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="c874c-159">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="c874c-160">Katalog, w którym można umieścić wbudowane pliki binarne.</span><span class="sxs-lookup"><span data-stu-id="c874c-160">Directory in which to place the built binaries.</span></span> <span data-ttu-id="c874c-161">Jeśli nie zostanie określona, domyślną ścieżką jest `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="c874c-161">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="c874c-162">W przypadku projektów z wieloma `TargetFrameworks` strukturami docelowymi (za pośrednictwem właściwości) należy również zdefiniować `--framework` podczas określania tej opcji.</span><span class="sxs-lookup"><span data-stu-id="c874c-162">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="c874c-163">Określa docelowy czas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c874c-163">Specifies the target runtime.</span></span> <span data-ttu-id="c874c-164">Aby uzyskać listę identyfikatorów środowiska wykonawczego (RID), zobacz [katalog RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="c874c-164">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="c874c-165">Ustawia poziom szczegółowości MSBuild.</span><span class="sxs-lookup"><span data-stu-id="c874c-165">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="c874c-166">Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .</span><span class="sxs-lookup"><span data-stu-id="c874c-166">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="c874c-167">Wartość domyślna to `minimal`.</span><span class="sxs-lookup"><span data-stu-id="c874c-167">The default is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="c874c-168">Ustawia wartość właściwości `$(VersionSuffix)` do użycia podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="c874c-168">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="c874c-169">To działa tylko `$(Version)` wtedy, gdy właściwość nie jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="c874c-169">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="c874c-170">Następnie `$(Version)` jest ustawiona `$(VersionPrefix)` na `$(VersionSuffix)`połączone z , oddzielone kreską.</span><span class="sxs-lookup"><span data-stu-id="c874c-170">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="c874c-171">Przykłady</span><span class="sxs-lookup"><span data-stu-id="c874c-171">Examples</span></span>

- <span data-ttu-id="c874c-172">Tworzenie projektu i jego zależności:</span><span class="sxs-lookup"><span data-stu-id="c874c-172">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

- <span data-ttu-id="c874c-173">Tworzenie projektu i jego zależności przy użyciu konfiguracji wydania:</span><span class="sxs-lookup"><span data-stu-id="c874c-173">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

- <span data-ttu-id="c874c-174">Tworzenie projektu i jego zależności dla określonego środowiska uruchomieniowego (w tym przykładzie Ubuntu 18.04):</span><span class="sxs-lookup"><span data-stu-id="c874c-174">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- <span data-ttu-id="c874c-175">Skompiluj projekt i użyj określonego źródła pakietu NuGet podczas operacji przywracania (.NET Core 2.0 SDK i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="c874c-175">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- <span data-ttu-id="c874c-176">Skompiluj projekt i ustaw wersję 1.2.3.4 jako parametr kompilacji przy użyciu `-p` opcji [MSBuild:](#msbuild)</span><span class="sxs-lookup"><span data-stu-id="c874c-176">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
