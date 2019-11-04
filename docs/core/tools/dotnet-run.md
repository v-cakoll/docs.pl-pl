---
title: polecenie dotnet Run
description: Polecenie dotnet Run udostępnia wygodną opcję uruchamiania aplikacji z kodu źródłowego.
ms.date: 10/31/2019
ms.openlocfilehash: 87e9a57e874116533951a9c5eb676be76be2c98d
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454781"
---
# <a name="dotnet-run"></a><span data-ttu-id="e1810-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="e1810-103">dotnet run</span></span>

<span data-ttu-id="e1810-104">**Ten artykuł dotyczy: ✓** .NET Core 1. x SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="e1810-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="e1810-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e1810-105">Name</span></span>

<span data-ttu-id="e1810-106">`dotnet run` — uruchamia kod źródłowy bez żadnych jawnych poleceń kompilacji lub uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="e1810-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e1810-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="e1810-107">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="e1810-108">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e1810-108">.NET Core 3.0</span></span>](#tab/netcore30)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="e1810-109">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="e1810-109">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="e1810-110">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="e1810-110">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e1810-111">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="e1810-111">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="e1810-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e1810-112">Description</span></span>

<span data-ttu-id="e1810-113">Polecenie `dotnet run` udostępnia wygodną opcję uruchamiania aplikacji z kodu źródłowego za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1810-113">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="e1810-114">Jest to przydatne w przypadku szybkiego iteracyjnego programowania z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1810-114">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="e1810-115">Polecenie jest zależne od polecenia [`dotnet build`](dotnet-build.md) do kompilowania kodu.</span><span class="sxs-lookup"><span data-stu-id="e1810-115">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="e1810-116">Wszelkie wymagania dotyczące kompilacji, takie jak najpierw należy przywrócić projekt, należy zastosować również do `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="e1810-116">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="e1810-117">Pliki wyjściowe są zapisywane w domyślnej lokalizacji, która jest `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="e1810-117">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="e1810-118">Na przykład jeśli masz aplikację `netcoreapp2.1` i uruchomisz `dotnet run`, dane wyjściowe są umieszczane w `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="e1810-118">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="e1810-119">Pliki są zastępowane w razie konieczności.</span><span class="sxs-lookup"><span data-stu-id="e1810-119">Files are overwritten as needed.</span></span> <span data-ttu-id="e1810-120">Pliki tymczasowe są umieszczane w katalogu `obj`.</span><span class="sxs-lookup"><span data-stu-id="e1810-120">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="e1810-121">Jeśli projekt określa wiele struktur, wykonywanie `dotnet run` powoduje błąd, chyba że zostanie użyta opcja `-f|--framework <FRAMEWORK>` do określenia struktury.</span><span class="sxs-lookup"><span data-stu-id="e1810-121">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="e1810-122">Polecenie `dotnet run` jest używane w kontekście projektów, nieskompilowanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="e1810-122">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="e1810-123">Jeśli próbujesz uruchomić bibliotekę DLL aplikacji zależnej od platformy, musisz użyć [dotnet](dotnet.md) bez polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1810-123">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="e1810-124">Na przykład aby uruchomić `myapp.dll`, użyj:</span><span class="sxs-lookup"><span data-stu-id="e1810-124">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="e1810-125">Aby uzyskać więcej informacji na temat sterownika `dotnet`, zobacz temat [narzędzia wiersza polecenia (CLI) platformy .NET Core](index.md) .</span><span class="sxs-lookup"><span data-stu-id="e1810-125">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="e1810-126">Aby uruchomić aplikację, polecenie `dotnet run` rozwiązuje zależności aplikacji, które są poza udostępnionym środowiskiem uruchomieniowym z pamięci podręcznej NuGet.</span><span class="sxs-lookup"><span data-stu-id="e1810-126">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="e1810-127">Ponieważ używa ona zależności buforowanych, nie zaleca się używania `dotnet run` do uruchamiania aplikacji w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="e1810-127">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="e1810-128">Zamiast tego [Utwórz wdrożenie](../deploying/index.md) przy użyciu [`dotnet publish`](dotnet-publish.md) polecenia i Wdróż opublikowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="e1810-128">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="e1810-129">Opcje</span><span class="sxs-lookup"><span data-stu-id="e1810-129">Options</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="e1810-130">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e1810-130">.NET Core 3.0</span></span>](#tab/netcore30)

`--`

<span data-ttu-id="e1810-131">Ogranicza argumenty do `dotnet run` z argumentów dla uruchamianej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1810-131">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="e1810-132">Wszystkie argumenty po tym ograniczniku są przesyłane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1810-132">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="e1810-133">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e1810-133">Defines the build configuration.</span></span> <span data-ttu-id="e1810-134">Wartość domyślna dla większości projektów jest `Debug`.</span><span class="sxs-lookup"><span data-stu-id="e1810-134">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="e1810-135">Kompiluje i uruchamia aplikację przy użyciu określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e1810-135">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="e1810-136">Struktura musi być określona w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="e1810-136">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="e1810-137">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e1810-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="e1810-138">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="e1810-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="e1810-139">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1810-139">Prints out a short help for the command.</span></span>

`--interactive`

<span data-ttu-id="e1810-140">Zezwala na zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład w celu ukończenia uwierzytelniania).</span><span class="sxs-lookup"><span data-stu-id="e1810-140">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="e1810-141">Nazwa profilu uruchamiania (jeśli istnieje) do użycia podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1810-141">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="e1810-142">Profile uruchamiania są zdefiniowane w pliku *profilu launchsettings. JSON* i są zwykle nazywane `Development`, `Staging`i `Production`.</span><span class="sxs-lookup"><span data-stu-id="e1810-142">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="e1810-143">Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="e1810-143">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="e1810-144">Nie kompiluje projektu przed uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="e1810-144">Doesn't build the project before running.</span></span> <span data-ttu-id="e1810-145">Również niejawne ustawia flagę `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="e1810-145">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="e1810-146">W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="e1810-146">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="e1810-147">Nie próbuje skonfigurować aplikacji przy użyciu pliku *profilu launchsettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="e1810-147">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="e1810-148">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1810-148">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="e1810-149">Określa ścieżkę do pliku projektu do uruchomienia (nazwa folderu lub pełna ścieżka).</span><span class="sxs-lookup"><span data-stu-id="e1810-149">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="e1810-150">Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="e1810-150">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="e1810-151">Określa docelowy środowisko uruchomieniowe, dla którego mają zostać przywrócone pakiety.</span><span class="sxs-lookup"><span data-stu-id="e1810-151">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="e1810-152">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="e1810-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="e1810-153">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1810-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e1810-154">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e1810-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="e1810-155">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="e1810-155">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="e1810-156">Ogranicza argumenty do `dotnet run` z argumentów dla uruchamianej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1810-156">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="e1810-157">Wszystkie argumenty po tym ograniczniku są przesyłane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1810-157">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="e1810-158">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e1810-158">Defines the build configuration.</span></span> <span data-ttu-id="e1810-159">Wartość domyślna dla większości projektów jest `Debug`.</span><span class="sxs-lookup"><span data-stu-id="e1810-159">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="e1810-160">Kompiluje i uruchamia aplikację przy użyciu określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e1810-160">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="e1810-161">Struktura musi być określona w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="e1810-161">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="e1810-162">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e1810-162">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="e1810-163">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="e1810-163">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="e1810-164">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1810-164">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="e1810-165">Nazwa profilu uruchamiania (jeśli istnieje) do użycia podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1810-165">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="e1810-166">Profile uruchamiania są zdefiniowane w pliku *profilu launchsettings. JSON* i są zwykle nazywane `Development`, `Staging`i `Production`.</span><span class="sxs-lookup"><span data-stu-id="e1810-166">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="e1810-167">Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="e1810-167">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="e1810-168">Nie kompiluje projektu przed uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="e1810-168">Doesn't build the project before running.</span></span> <span data-ttu-id="e1810-169">Również niejawne ustawia flagę `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="e1810-169">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="e1810-170">W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="e1810-170">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="e1810-171">Nie próbuje skonfigurować aplikacji przy użyciu pliku *profilu launchsettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="e1810-171">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="e1810-172">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1810-172">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="e1810-173">Określa ścieżkę do pliku projektu do uruchomienia (nazwa folderu lub pełna ścieżka).</span><span class="sxs-lookup"><span data-stu-id="e1810-173">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="e1810-174">Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="e1810-174">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="e1810-175">Określa docelowy środowisko uruchomieniowe, dla którego mają zostać przywrócone pakiety.</span><span class="sxs-lookup"><span data-stu-id="e1810-175">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="e1810-176">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="e1810-176">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="e1810-177">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1810-177">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e1810-178">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e1810-178">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="e1810-179">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="e1810-179">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="e1810-180">Ogranicza argumenty do `dotnet run` z argumentów dla uruchamianej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1810-180">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="e1810-181">Wszystkie argumenty po tym ograniczniku są przesyłane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1810-181">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="e1810-182">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e1810-182">Defines the build configuration.</span></span> <span data-ttu-id="e1810-183">Wartość domyślna dla większości projektów jest `Debug`.</span><span class="sxs-lookup"><span data-stu-id="e1810-183">The default for most projects value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="e1810-184">Kompiluje i uruchamia aplikację przy użyciu określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e1810-184">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="e1810-185">Struktura musi być określona w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="e1810-185">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="e1810-186">Wymusza rozpoznanie wszystkich zależności, nawet jeśli ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="e1810-186">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="e1810-187">Określenie tej flagi jest takie samo jak usuwanie pliku *Project. assets. JSON* .</span><span class="sxs-lookup"><span data-stu-id="e1810-187">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="e1810-188">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1810-188">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="e1810-189">Nazwa profilu uruchamiania (jeśli istnieje) do użycia podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1810-189">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="e1810-190">Profile uruchamiania są zdefiniowane w pliku *profilu launchsettings. JSON* i są zwykle nazywane `Development`, `Staging`i `Production`.</span><span class="sxs-lookup"><span data-stu-id="e1810-190">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="e1810-191">Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="e1810-191">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="e1810-192">Nie kompiluje projektu przed uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="e1810-192">Doesn't build the project before running.</span></span> <span data-ttu-id="e1810-193">Również niejawne ustawia flagę `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="e1810-193">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="e1810-194">W przypadku przywracania projektu z odwołaniami do projektu (P2P) program przywraca projekt główny, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="e1810-194">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="e1810-195">Nie próbuje skonfigurować aplikacji przy użyciu pliku *profilu launchsettings. JSON* .</span><span class="sxs-lookup"><span data-stu-id="e1810-195">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="e1810-196">Nie wykonuje przywracania niejawnego podczas wykonywania polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1810-196">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="e1810-197">Określa ścieżkę do pliku projektu do uruchomienia (nazwa folderu lub pełna ścieżka).</span><span class="sxs-lookup"><span data-stu-id="e1810-197">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="e1810-198">Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="e1810-198">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="e1810-199">Określa docelowy środowisko uruchomieniowe, dla którego mają zostać przywrócone pakiety.</span><span class="sxs-lookup"><span data-stu-id="e1810-199">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="e1810-200">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [wykaz identyfikatorów RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="e1810-200">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e1810-201">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="e1810-201">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="e1810-202">Ogranicza argumenty do `dotnet run` z argumentów dla uruchamianej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1810-202">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="e1810-203">Wszystkie argumenty po tym ograniczniku są przesyłane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e1810-203">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="e1810-204">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e1810-204">Defines the build configuration.</span></span> <span data-ttu-id="e1810-205">Wartość domyślna dla większości projektów jest `Debug`.</span><span class="sxs-lookup"><span data-stu-id="e1810-205">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="e1810-206">Kompiluje i uruchamia aplikację przy użyciu określonej [struktury](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e1810-206">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="e1810-207">Struktura musi być określona w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="e1810-207">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="e1810-208">Drukuje krótką pomoc dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="e1810-208">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="e1810-209">Określa ścieżkę i nazwę pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="e1810-209">Specifies the path and name of the project file.</span></span> <span data-ttu-id="e1810-210">(Zobacz uwagi). Jeśli nie zostanie określony, domyślnie jest bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="e1810-210">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="e1810-211">Użyj ścieżki i nazwy pliku projektu z opcją `-p|--project`.</span><span class="sxs-lookup"><span data-stu-id="e1810-211">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="e1810-212">Regresja w interfejsie wiersza polecenia uniemożliwia podanie ścieżki folderu z zestaw .NET Core SDK 1. x.</span><span class="sxs-lookup"><span data-stu-id="e1810-212">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="e1810-213">Aby uzyskać więcej informacji o tym problemie, zobacz polecenie [dotnet Run-p, nie można uruchomić projektu (#5992 dotnet/CLI)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="e1810-213">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="e1810-214">Przykłady</span><span class="sxs-lookup"><span data-stu-id="e1810-214">Examples</span></span>

<span data-ttu-id="e1810-215">Uruchom projekt w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="e1810-215">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="e1810-216">Uruchom określony projekt:</span><span class="sxs-lookup"><span data-stu-id="e1810-216">Run the specified project:</span></span>

`dotnet run --project ./projects/proj1/proj1.csproj`

<span data-ttu-id="e1810-217">Uruchom projekt w bieżącym katalogu (`--help` argument w tym przykładzie jest przesyłany do aplikacji, ponieważ jest używana opcja pustej `--`):</span><span class="sxs-lookup"><span data-stu-id="e1810-217">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="e1810-218">Przywróć zależności i narzędzia dla projektu w bieżącym katalogu, wyświetlając tylko minimalne dane wyjściowe, a następnie Uruchom projekt: (zestaw .NET Core SDK 2,0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="e1810-218">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`
