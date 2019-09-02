---
title: polecenie dotnet Run
description: Polecenie dotnet Run udostępnia wygodną opcję uruchamiania aplikacji z kodu źródłowego.
ms.date: 05/29/2018
ms.openlocfilehash: 0a6c1303bc12c256dd0a8923f9468620835ddabc
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202808"
---
# <a name="dotnet-run"></a><span data-ttu-id="47aec-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="47aec-103">dotnet run</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="47aec-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="47aec-104">Name</span></span>

<span data-ttu-id="47aec-105">`dotnet run`-Uruchamia kod źródłowy bez żadnych jawnych poleceń kompilacji lub uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="47aec-105">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="47aec-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="47aec-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="47aec-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="47aec-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="47aec-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="47aec-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="47aec-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="47aec-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="47aec-110">Opis</span><span class="sxs-lookup"><span data-stu-id="47aec-110">Description</span></span>

<span data-ttu-id="47aec-111">`dotnet run` Polecenie udostępnia wygodną opcję uruchamiania aplikacji z kodu źródłowego za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="47aec-111">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="47aec-112">Jest to przydatne w przypadku szybkiego iteracyjnego programowania z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="47aec-112">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="47aec-113">Polecenie jest zależne od [`dotnet build`](dotnet-build.md) polecenia do kompilowania kodu.</span><span class="sxs-lookup"><span data-stu-id="47aec-113">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="47aec-114">Wszelkie wymagania dotyczące kompilacji, takie jak najpierw należy przywrócić projekt, również zastosować do `dotnet run` .</span><span class="sxs-lookup"><span data-stu-id="47aec-114">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="47aec-115">Pliki wyjściowe są zapisywane w lokalizacji domyślnej, czyli `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="47aec-115">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="47aec-116">Na przykład jeśli masz `netcoreapp2.1` aplikację i uruchomisz `dotnet run`, dane wyjściowe są umieszczane w `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="47aec-116">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="47aec-117">Pliki są zastępowane w razie konieczności.</span><span class="sxs-lookup"><span data-stu-id="47aec-117">Files are overwritten as needed.</span></span> <span data-ttu-id="47aec-118">Pliki tymczasowe są umieszczane w `obj` katalogu.</span><span class="sxs-lookup"><span data-stu-id="47aec-118">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="47aec-119">Jeśli projekt określa wiele struktur, wykonanie `dotnet run` powoduje błąd, `-f|--framework <FRAMEWORK>` chyba że opcja jest używana do określenia struktury.</span><span class="sxs-lookup"><span data-stu-id="47aec-119">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="47aec-120">`dotnet run` Polecenie jest używane w kontekście projektów, nieskompilowanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="47aec-120">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="47aec-121">Jeśli próbujesz uruchomić bibliotekę DLL aplikacji zależnej od platformy, musisz użyć [dotnet](dotnet.md) bez polecenia.</span><span class="sxs-lookup"><span data-stu-id="47aec-121">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="47aec-122">Na przykład aby uruchomić `myapp.dll`polecenie, użyj:</span><span class="sxs-lookup"><span data-stu-id="47aec-122">For example, to run `myapp.dll`, use:</span></span>

```console
dotnet myapp.dll
```

<span data-ttu-id="47aec-123">Aby uzyskać więcej informacji na `dotnet` temat sterownika, zobacz temat [narzędzia wiersza polecenia (CLI) platformy .NET Core](index.md) .</span><span class="sxs-lookup"><span data-stu-id="47aec-123">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="47aec-124">Aby uruchomić aplikację, `dotnet run` polecenie rozwiązuje zależności aplikacji, które są poza udostępnionym środowiskiem uruchomieniowym z pamięci podręcznej NuGet.</span><span class="sxs-lookup"><span data-stu-id="47aec-124">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="47aec-125">Ponieważ używa on buforowanych zależności, nie jest zalecane `dotnet run` do uruchamiania aplikacji w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="47aec-125">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="47aec-126">Zamiast tego [Utwórz wdrożenie](../deploying/index.md) przy użyciu [`dotnet publish`](dotnet-publish.md) polecenia i Wdróż opublikowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="47aec-126">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="47aec-127">Opcje</span><span class="sxs-lookup"><span data-stu-id="47aec-127">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="47aec-128">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="47aec-128">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="47aec-129">Ogranicza argumenty `dotnet run` od argumentów dla uruchamianej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="47aec-129">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="47aec-130">Wszystkie argumenty po tym ograniczniku są przesyłane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="47aec-130">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="47aec-131">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="47aec-131">Defines the build configuration.</span></span> <span data-ttu-id="47aec-132">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="47aec-132">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="47aec-133">Kompiluje i uruchamia aplikację przy użyciu określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="47aec-133">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="47aec-134">Struktura musi być określona w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="47aec-134">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="47aec-135">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="47aec-135">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="47aec-136">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="47aec-136">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="47aec-137">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="47aec-137">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="47aec-138">Nazwa profilu uruchamiania (jeśli istnieje) do użycia podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="47aec-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="47aec-139">Profile uruchamiania są zdefiniowane w pliku *profilu launchsettings. JSON* i są zwykle nazywane `Development`, `Staging`i `Production`.</span><span class="sxs-lookup"><span data-stu-id="47aec-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="47aec-140">Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="47aec-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="47aec-141">Nie kompiluje projektu przed uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="47aec-141">Doesn't build the project before running.</span></span> <span data-ttu-id="47aec-142">Również niejawne ustawia `--no-restore` flagę.</span><span class="sxs-lookup"><span data-stu-id="47aec-142">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="47aec-143">W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="47aec-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="47aec-144">Nie próbuje skonfigurować aplikacji przy użyciu pliku *profilu launchsettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="47aec-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="47aec-145">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="47aec-145">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="47aec-146">Określa ścieżkę do pliku projektu do uruchomienia (nazwa folderu lub pełna ścieżka).</span><span class="sxs-lookup"><span data-stu-id="47aec-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="47aec-147">Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="47aec-147">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="47aec-148">Określa docelowy środowisko uruchomieniowe, dla którego mają zostać przywrócone pakiety.</span><span class="sxs-lookup"><span data-stu-id="47aec-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="47aec-149">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="47aec-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="47aec-150">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="47aec-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="47aec-151">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`</span><span class="sxs-lookup"><span data-stu-id="47aec-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="47aec-152">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="47aec-152">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="47aec-153">Ogranicza argumenty `dotnet run` od argumentów dla uruchamianej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="47aec-153">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="47aec-154">Wszystkie argumenty po tym ograniczniku są przesyłane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="47aec-154">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="47aec-155">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="47aec-155">Defines the build configuration.</span></span> <span data-ttu-id="47aec-156">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="47aec-156">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="47aec-157">Kompiluje i uruchamia aplikację przy użyciu określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="47aec-157">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="47aec-158">Struktura musi być określona w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="47aec-158">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="47aec-159">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="47aec-159">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="47aec-160">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="47aec-160">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="47aec-161">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="47aec-161">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="47aec-162">Nazwa profilu uruchamiania (jeśli istnieje) do użycia podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="47aec-162">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="47aec-163">Profile uruchamiania są zdefiniowane w pliku *profilu launchsettings. JSON* i są zwykle nazywane `Development`, `Staging`i `Production`.</span><span class="sxs-lookup"><span data-stu-id="47aec-163">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="47aec-164">Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="47aec-164">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="47aec-165">Nie kompiluje projektu przed uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="47aec-165">Doesn't build the project before running.</span></span> <span data-ttu-id="47aec-166">Również niejawne ustawia `--no-restore` flagę.</span><span class="sxs-lookup"><span data-stu-id="47aec-166">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="47aec-167">W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="47aec-167">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="47aec-168">Nie próbuje skonfigurować aplikacji przy użyciu pliku *profilu launchsettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="47aec-168">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="47aec-169">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="47aec-169">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="47aec-170">Określa ścieżkę do pliku projektu do uruchomienia (nazwa folderu lub pełna ścieżka).</span><span class="sxs-lookup"><span data-stu-id="47aec-170">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="47aec-171">Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="47aec-171">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="47aec-172">Określa docelowy środowisko uruchomieniowe, dla którego mają zostać przywrócone pakiety.</span><span class="sxs-lookup"><span data-stu-id="47aec-172">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="47aec-173">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="47aec-173">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="47aec-174">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="47aec-174">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="47aec-175">Ogranicza argumenty `dotnet run` od argumentów dla uruchamianej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="47aec-175">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="47aec-176">Wszystkie argumenty po tym ograniczniku są przesyłane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="47aec-176">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="47aec-177">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="47aec-177">Defines the build configuration.</span></span> <span data-ttu-id="47aec-178">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="47aec-178">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="47aec-179">Kompiluje i uruchamia aplikację przy użyciu określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="47aec-179">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="47aec-180">Struktura musi być określona w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="47aec-180">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="47aec-181">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="47aec-181">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="47aec-182">Określa ścieżkę i nazwę pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="47aec-182">Specifies the path and name of the project file.</span></span> <span data-ttu-id="47aec-183">(Zobacz uwagi). Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="47aec-183">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="47aec-184">Użyj ścieżki i nazwy pliku projektu z `-p|--project` opcją.</span><span class="sxs-lookup"><span data-stu-id="47aec-184">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="47aec-185">Regresja w interfejsie wiersza polecenia uniemożliwia podanie ścieżki folderu z zestaw .NET Core SDK 1. x.</span><span class="sxs-lookup"><span data-stu-id="47aec-185">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="47aec-186">Aby uzyskać więcej informacji o tym problemie, zobacz polecenie [dotnet Run-p, nie można uruchomić projektu (#5992 dotnet/CLI)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="47aec-186">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="47aec-187">Przykłady</span><span class="sxs-lookup"><span data-stu-id="47aec-187">Examples</span></span>

<span data-ttu-id="47aec-188">Uruchom projekt w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="47aec-188">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="47aec-189">Uruchom określony projekt:</span><span class="sxs-lookup"><span data-stu-id="47aec-189">Run the specified project:</span></span>

`dotnet run --project ./projects/proj1/proj1.csproj`

<span data-ttu-id="47aec-190">Uruchom projekt w bieżącym katalogu ( `--help` argument w tym przykładzie jest przesyłany do aplikacji, ponieważ jest używana opcja pusta `--` ):</span><span class="sxs-lookup"><span data-stu-id="47aec-190">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="47aec-191">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu, wyświetlając tylko minimalne dane wyjściowe, a następnie Uruchom projekt: (zestaw .NET Core SDK 2,0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="47aec-191">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`
