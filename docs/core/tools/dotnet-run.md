---
title: polecenia DotNet, uruchom polecenie — interfejs wiersza polecenia platformy .NET Core
description: Polecenia dotnet, uruchom polecenie zapewnia wygodny sposób, aby uruchomić aplikację z kodu źródłowego.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: f560e6f795f00488818647a4b5c711dcf9d59dcd
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46324533"
---
# <a name="dotnet-run"></a><span data-ttu-id="06efe-103">Uruchom polecenia DotNet</span><span class="sxs-lookup"><span data-stu-id="06efe-103">dotnet run</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="06efe-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="06efe-104">Name</span></span>

<span data-ttu-id="06efe-105">`dotnet run` — Przebiegi źródła kodu, bez jawnego kompilowania i uruchamiania poleceń.</span><span class="sxs-lookup"><span data-stu-id="06efe-105">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="06efe-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="06efe-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="06efe-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="06efe-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="06efe-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="06efe-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="06efe-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="06efe-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="06efe-110">Opis</span><span class="sxs-lookup"><span data-stu-id="06efe-110">Description</span></span>

<span data-ttu-id="06efe-111">`dotnet run` Polecenie zapewnia wygodny sposób, aby uruchomić aplikację z kodu źródłowego za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="06efe-111">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="06efe-112">Jest to przydatne w przypadku szybkiego iteracyjne projektowanie z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="06efe-112">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="06efe-113">Polecenie zależy od [ `dotnet build` ](dotnet-build.md) polecenie, aby skompilować kod.</span><span class="sxs-lookup"><span data-stu-id="06efe-113">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="06efe-114">Wszelkie wymagania dotyczące kompilacji, takie jak, projekt musi zostać przywrócona najpierw dotyczą `dotnet run` także.</span><span class="sxs-lookup"><span data-stu-id="06efe-114">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="06efe-115">Pliki wyjściowe są zapisywane w domyślnej lokalizacji, czyli `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="06efe-115">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="06efe-116">Na przykład jeśli masz `netcoreapp2.1` aplikacji i uruchom `dotnet run`, dane wyjściowe są umieszczane w `bin/Debug/netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="06efe-116">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="06efe-117">Pliki zostaną zastąpione, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="06efe-117">Files are overwritten as needed.</span></span> <span data-ttu-id="06efe-118">Pliki tymczasowe są umieszczane w `obj` katalogu.</span><span class="sxs-lookup"><span data-stu-id="06efe-118">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="06efe-119">Jeśli projekt określa wiele struktur, wykonywanie `dotnet run` powoduje błąd, chyba że `-f|--framework <FRAMEWORK>` opcja służy do określania platformę.</span><span class="sxs-lookup"><span data-stu-id="06efe-119">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="06efe-120">`dotnet run` Polecenie jest używane w kontekście projektów, nie skompilowanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="06efe-120">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="06efe-121">Jeśli próbujesz zamiast tego uruchomić program zależny od struktury biblioteki DLL, należy użyć [dotnet](dotnet.md) bez polecenia.</span><span class="sxs-lookup"><span data-stu-id="06efe-121">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="06efe-122">Na przykład, aby uruchomić `myapp.dll`, użyj:</span><span class="sxs-lookup"><span data-stu-id="06efe-122">For example, to run `myapp.dll`, use:</span></span>

```console
dotnet myapp.dll
```

<span data-ttu-id="06efe-123">Aby uzyskać więcej informacji na temat `dotnet` sterowników, zobacz [.NET Core wiersza polecenia narzędzia (CLI)](index.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="06efe-123">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="06efe-124">Aby uruchomić aplikację, `dotnet run` polecenie usuwa zależności aplikacji, które znajdują się poza udostępnionego środowiska uruchomieniowego z pamięcią podręczną programu NuGet.</span><span class="sxs-lookup"><span data-stu-id="06efe-124">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="06efe-125">Ponieważ używa ona zależności pamięci podręcznej, nie zaleca się używać `dotnet run` do uruchamiania aplikacji w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="06efe-125">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="06efe-126">Zamiast tego [Utwórz wdrożenie](../deploying/index.md) przy użyciu [ `dotnet publish` ](dotnet-publish.md) poleceń i wdrożyć opublikowane dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="06efe-126">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="06efe-127">Opcje</span><span class="sxs-lookup"><span data-stu-id="06efe-127">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="06efe-128">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="06efe-128">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="06efe-129">Argumenty rozgranicza `dotnet run` na podstawie argumentów dla aplikacji, są uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="06efe-129">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="06efe-130">Wszystkie argumenty po tym ogranicznikiem są przekazywane do aplikacji, uruchom.</span><span class="sxs-lookup"><span data-stu-id="06efe-130">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="06efe-131">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="06efe-131">Defines the build configuration.</span></span> <span data-ttu-id="06efe-132">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="06efe-132">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="06efe-133">Kompiluje i uruchamia aplikację przy użyciu określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="06efe-133">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="06efe-134">Struktura należy określić w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="06efe-134">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="06efe-135">Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="06efe-135">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="06efe-136">Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="06efe-136">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="06efe-137">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="06efe-137">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="06efe-138">Nazwa uruchomienia profilu (jeśli istnieje) do użycia podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06efe-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="06efe-139">Profile uruchamiania są zdefiniowane w *launchSettings.json* pliku i są zwykle nazywane `Development`, `Staging`, i `Production`.</span><span class="sxs-lookup"><span data-stu-id="06efe-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="06efe-140">Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="06efe-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="06efe-141">Nie da się skompilować projekt przed uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="06efe-141">Doesn't build the project before running.</span></span> <span data-ttu-id="06efe-142">Ustawia ona również niejawne `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="06efe-142">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="06efe-143">Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca projektu głównego, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="06efe-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="06efe-144">Nie próbuj używać *launchSettings.json* do konfigurowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06efe-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="06efe-145">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="06efe-145">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="06efe-146">Określa ścieżkę do pliku projektu do uruchomienia (nazwa folderu lub pełną ścieżkę).</span><span class="sxs-lookup"><span data-stu-id="06efe-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="06efe-147">Jeśli nie zostanie określony, jego wartość domyślna w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="06efe-147">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="06efe-148">Określa docelowe środowisko uruchomieniowe w celu przywrócenia pakietów dla.</span><span class="sxs-lookup"><span data-stu-id="06efe-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="06efe-149">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="06efe-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="06efe-150">Ustawia poziom szczegółowości polecenia.</span><span class="sxs-lookup"><span data-stu-id="06efe-150">Sets the verbosity level of the command.</span></span> <span data-ttu-id="06efe-151">Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, i `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="06efe-151">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="06efe-152">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="06efe-152">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="06efe-153">Argumenty rozgranicza `dotnet run` na podstawie argumentów dla aplikacji, są uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="06efe-153">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="06efe-154">Wszystkie argumenty po tym ogranicznikiem są przekazywane do aplikacji, uruchom.</span><span class="sxs-lookup"><span data-stu-id="06efe-154">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="06efe-155">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="06efe-155">Defines the build configuration.</span></span> <span data-ttu-id="06efe-156">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="06efe-156">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="06efe-157">Kompiluje i uruchamia aplikację przy użyciu określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="06efe-157">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="06efe-158">Struktura należy określić w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="06efe-158">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="06efe-159">Wymusza wszystkie zależności rozwiązany, nawet wtedy, gdy ostatnie przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="06efe-159">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="06efe-160">Określanie ta flaga jest taka sama jak usuwanie *project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="06efe-160">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="06efe-161">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="06efe-161">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="06efe-162">Nazwa uruchomienia profilu (jeśli istnieje) do użycia podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06efe-162">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="06efe-163">Profile uruchamiania są zdefiniowane w *launchSettings.json* pliku i są zwykle nazywane `Development`, `Staging`, i `Production`.</span><span class="sxs-lookup"><span data-stu-id="06efe-163">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="06efe-164">Aby uzyskać więcej informacji, zobacz [Praca z wieloma środowiskami](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="06efe-164">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="06efe-165">Nie da się skompilować projekt przed uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="06efe-165">Doesn't build the project before running.</span></span> <span data-ttu-id="06efe-166">Ustawia ona również niejawne `--no-restore` flagi.</span><span class="sxs-lookup"><span data-stu-id="06efe-166">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="06efe-167">Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca projektu głównego, a nie odwołania.</span><span class="sxs-lookup"><span data-stu-id="06efe-167">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="06efe-168">Nie próbuj używać *launchSettings.json* do konfigurowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="06efe-168">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="06efe-169">Przy uruchamianiu polecenia niejawne przywracania nie jest wykonywany.</span><span class="sxs-lookup"><span data-stu-id="06efe-169">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="06efe-170">Określa ścieżkę do pliku projektu do uruchomienia (nazwa folderu lub pełną ścieżkę).</span><span class="sxs-lookup"><span data-stu-id="06efe-170">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="06efe-171">Jeśli nie zostanie określony, jego wartość domyślna w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="06efe-171">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="06efe-172">Określa docelowe środowisko uruchomieniowe w celu przywrócenia pakietów dla.</span><span class="sxs-lookup"><span data-stu-id="06efe-172">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="06efe-173">Aby uzyskać listę identyfikatorów środowisk uruchomieniowych (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="06efe-173">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="06efe-174">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="06efe-174">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="06efe-175">Argumenty rozgranicza `dotnet run` na podstawie argumentów dla aplikacji, są uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="06efe-175">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="06efe-176">Wszystkie argumenty po tym ogranicznikiem są przekazywane do aplikacji, uruchom.</span><span class="sxs-lookup"><span data-stu-id="06efe-176">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="06efe-177">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="06efe-177">Defines the build configuration.</span></span> <span data-ttu-id="06efe-178">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="06efe-178">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="06efe-179">Kompiluje i uruchamia aplikację przy użyciu określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="06efe-179">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="06efe-180">Struktura należy określić w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="06efe-180">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="06efe-181">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="06efe-181">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="06efe-182">Określa ścieżkę i nazwę pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="06efe-182">Specifies the path and name of the project file.</span></span> <span data-ttu-id="06efe-183">(Zobacz Uwagi). Jeśli nie zostanie określony, jego wartość domyślna w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="06efe-183">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="06efe-184">Użyj ścieżkę i nazwę pliku projektu za pomocą `-p|--project` opcji.</span><span class="sxs-lookup"><span data-stu-id="06efe-184">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="06efe-185">Regresja w interfejsie wiersza polecenia platformy zapobiega, podając ścieżkę folderu przy użyciu zestawu SDK programu .NET Core 1.x.</span><span class="sxs-lookup"><span data-stu-id="06efe-185">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="06efe-186">Aby uzyskać więcej informacji na temat tego problemu, zobacz [dotnet, uruchom -p, nie można uruchomić projektu (/ interfejsu wiersza polecenia dotnet #5992)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="06efe-186">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="06efe-187">Przykłady</span><span class="sxs-lookup"><span data-stu-id="06efe-187">Examples</span></span>

<span data-ttu-id="06efe-188">Uruchom projekt w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="06efe-188">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="06efe-189">Uruchamia określony projekt:</span><span class="sxs-lookup"><span data-stu-id="06efe-189">Run the specified project:</span></span>

`dotnet run --project ./projects/proj1/proj1.csproj`

<span data-ttu-id="06efe-190">Uruchom projekt w bieżącym katalogu ( `--help` argument w tym przykładzie jest przekazywany do aplikacji, ponieważ pustą `--` jest używana opcja):</span><span class="sxs-lookup"><span data-stu-id="06efe-190">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="06efe-191">Przywracanie zależności i narzędzia dla projektów w bieżącym katalogu, tylko wyświetlanie minimalne dane wyjściowe, a następnie uruchomić projekt: (.NET Core SDK 2.0 i nowsze wersje):</span><span class="sxs-lookup"><span data-stu-id="06efe-191">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`